---
title: Prevent deletes of projects in a Project environment by creating a Microsoft Dataverse Plugin
description: Create and register a plug-in Visual Studio using a modified class library that interrupts attempts to delete records from the Project table in Project for the web. Add a group whose members can delete. 
author: v-stthomas
ms.author: jenz
ms.service: project-web
manager: jtremper
ms.topic: how-to
ms.date: 05/02/2022
ms.custom: template-how-to
---

# Prevent deletes of projects in a Project environment by creating a Microsoft Dataverse Plugin

Project for the Web is collaborative by design and allows all licensed team members full access to the entire project. But sometimes, you want to keep some teammates from deleting projects. This article explains how to use [a Dataverse plug-in to block deletion of projects](https://github.com/OfficeDev/Project-Dataverse-Plugin-Sample), even in Dynamics 365 Project Operations.

You can modify this plugin to grant the delete permission solely to the project owner, manager, an Admin, or otherwise. Furthermore, Dataverse plug-ins can be used to validate or modify any other operation that is performed on Dataverse Entities (Projects, Tasks, Teams, etc.) and their relationship to other entities.

## Prerequisites

- Administrator level access to a Microsoft Dataverse environment
- A model-driven app that includes the account and task tables
     > [!TIP]
     > For help building such an app, go to [Build your first model-driven app from scratch](/power-apps/maker/model-driven-apps/build-first-model-driven-app).

- Visual Studio 2017 (or later version)
- Knowledge of the Visual C# programming language
- The [Plug-in Registration tool](https://www.nuget.org/packages/Microsoft.CrmSdk.XrmTooling.PluginRegistrationTool)
     > [!TIP]
     > Go to [Download tools from NuGet](/power-apps/developer/data-platform/download-tools-nuget) for steps to use a PowerShell script to download the latest tools from NuGet.

## Create a new Dataverse plug-in in Visual Studio

1. Launch Visual Studio.
1. Select **Create a new Project**.
1. Choose the **Class Library (.NET Framework)** templates and select **Next**.

     :::image type="content" source="media/csharp-dataverse-plugin-create.png" alt-text="Choose your class library template.":::

1. Name your Project, choose the **.NET Framework 4.6.2**, and select **Create**.

     :::image type="content" source="media/prevent-project-deletes-create-plugin-step-2.png" alt-text="Create your class library.":::

1. Name the class in your project solution *ProjectBlockDeletePlugin.cs*. This will make it easier to read in code and understand its purpose.

## Add a NuGet Package

1. In the top toolbar, select **Tools > NuGetPackageManager > Manage NuGet Packages for Solutions**.
1. On the **Browse** tab, search for *Microsoft.CrmSdk.CoreAssemblies*, and install the latest stable version for your project.

     :::image type="content" source="media/prevent-project-deletes-create-plugin-manage-packages.png" alt-text="Install Microsoft.CrmSdk.CoreAssemblies.":::

## Register your plug-in

> [!NOTE]
>
> - You’re creating a Pre-Validation plug-in. It runs when an operation (Delete) is called on the Dataverse Entity (Project).
> - When someone tries to delete a project, the plug-in checks the GUID of the user who is trying to delete a project in Project for the Web. It then checks Dataverse to see whether the user belongs to a Teams group that is allowed to delete projects. If not, the plug-in cancels the Delete operation.
> - For more context and documentation on what you can do with Dataverse Plug-ins, please [visit the Official Dataverse Plug-In Documentation](/power-apps/developer/data-platform/plug-ins).

1. Open your new class file (*ProjectBlockDeletePlugin.cs*), and paste in the following class code, but replace the GUID for the Team ID who gets delete privilege. You can find the GUID in PowerApps Data Explorer.

     ```csharp
      using System;
      using Microsoft.Xrm.Sdk;
      using Microsoft.Xrm.Sdk.Query;
      using System.ServiceModel;
      using Microsoft.Xrm.Sdk.Messages;
      namespace PluginTest.Plugins
     {
      public class ProjectBlockDeletePlugin : IPlugin
        {
          public void Execute(IServiceProvider serviceProvider)
          {
            // Obtain the tracing service
            ITracingService tracingService =
            (ITracingService)serviceProvider.GetService(typeof(ITracingService));

            // Obtain the execution context from the service provider.  
            IPluginExecutionContext context = (IPluginExecutionContext)
                serviceProvider.GetService(typeof(IPluginExecutionContext));

            // The InputParameters collection contains all the data passed in the message request.  
            if (context.InputParameters.Contains("Target") &&
                context.InputParameters["Target"] is EntityReference)
            {
                // Obtain the target entity from the input parameters.  
                EntityReference projectEntityRef = context.InputParameters["Target"] as EntityReference;

                // Obtain the organization service reference which you will need for  
                // web service calls.  
                IOrganizationServiceFactory serviceFactory = (IOrganizationServiceFactory)serviceProvider.GetService(typeof(IOrganizationServiceFactory));
                IOrganizationService service = serviceFactory.CreateOrganizationService(context.InitiatingUserId);

                try
                {
                    // TODO: Manually set which team has Delete privileges
                    Guid TeamWithDeletePrivilegeId = new Guid("0f96b130-c72c-ec11-b6e5-000d3a59eeac");

                    // Create the queryExpression for the team entity query
                    QueryExpression query = new QueryExpression("team");
                    query.ColumnSet = new ColumnSet("teamid");

                    // Create a Relationship collection query for the user <-> team relationship
                    Relationship teamMembershipRelationship = new Relationship("teammembership_association");
                    RelationshipQueryCollection relationshipCollectionQuery = new RelationshipQueryCollection();
                    relationshipCollectionQuery.Add(teamMembershipRelationship, query);

                    // Create a service RetrieveRequest with the system user - the user who launches the plugin - and all the teams the user is related to.
                    RetrieveRequest request = new RetrieveRequest();
                    request.RelatedEntitiesQuery = relationshipCollectionQuery;
                    request.Target = new EntityReference("systemuser", context.InitiatingUserId);
                    request.ColumnSet = new ColumnSet(true);

                    // Execute the RetrieveRequest
                    RetrieveResponse userWithTeamRelationships = (RetrieveResponse)service.Execute(request);

                    // Loop through all teams that the user is related to find if they belong the team with delete permissions
                    bool userCanDelete = false;
                    foreach (Entity entity in userWithTeamRelationships.Entity.RelatedEntities[teamMembershipRelationship].Entities)
                    {
                        if ((Guid)entity.Attributes["teamid"] == TeamWithDeletePrivilegeId)
                        {
                            userCanDelete = true;
                            break;
                        };
                    }

                    // Throw an exception if the user doesn't have permission to delete - aborting the Delete Operation.
                    if (!userCanDelete)
                    {

                        // Optional: retrieve the team name with delete privilege for error message,
                        string TeamWithDeletePrivilegeName = service.Retrieve("team", TeamWithDeletePrivilegeId, new ColumnSet("name")).Attributes["name"].ToString();

                        throw new InvalidPluginExecutionException("You do not have permission to delete projects. Delete permission is only granted to members of the \"" + TeamWithDeletePrivilegeName + "\" team.");
                    }

                }

                catch (FaultException<OrganizationServiceFault> ex)
                {
                    throw new InvalidPluginExecutionException("An error occurred in ProjectBlockDeletePlugin.", ex);
                }

                catch (Exception ex)
                {
                    tracingService.Trace("ProjectBlockDeletePlugin: {0}", ex.ToString());
                    throw;
                }
            }
          }
        }
     }

     ```

> [!IMPORTANT]
> Make sure that your class is public, and named *ProjectBlockDeletePlugin.cs*.

## Sign your assembly

1. In Solution Explorer, on the context menu for your new plug-in select **Properties**.
1. On the **Signing** tab, select **Sign the assembly**, then choose **New…** from the dropdown options.

      :::image type="content" source="media/prevent-project-deletes-sign-assembly-2.png" alt-text="{alt-text}":::

1. Complete the **Create Strong Name Key** dialog.
1. On your project's context menu, select **Build**.

## Register your Dataverse plug-in

1. Launch the Plugin Registration Tool.
1. Select **Create New Connection**, and then enter the account from which you want to register the plug-in to Dataverse.  

     :::image type="content" source="media/prevent-project-deletes-sign-assembly-3.png" alt-text="Create New Connection to Dataverse":::

1. Select **Register > Register New Assembly**.

     :::image type="content" source="media/prevent-project-deletes-register-assembly.png" alt-text="Register your`new assembly":::

1. Load the assembly from the .DLL file in your project’s **Debug** folder.
1. Select **Register Selected Plugins**.
1. In the list of Registered Plugins, select **Register New Step** from your plugin assembly’s context menu.

     :::image type="content" source="media/prevent-project-deletes-register-assembly-3.png" alt-text="Register an assembly step":::

1. Register the Pre-Validation Step to make the plug-in run when someone tries to run a Delete operation on an *msdyn_project* entity:
  
     :::image type="content" source="media/prevent-project-deletes-register-assembly-2.png" alt-text="Finish registration":::

## Test your new plug-in

1. Open Project for the web using an account that isn't in the group who can Delete (that you built into the plug-in).
1. In the *Project* table, attempt to delete a row.
1. If your plug-in is working, your attempt will fail with a warning ("*You do not have permission to delete projects. Delete permission is only...*").

## Next steps

- [Visit the official Dataverse Plug-in Documentation](/power-apps/developer/data-platform/plug-ins).
