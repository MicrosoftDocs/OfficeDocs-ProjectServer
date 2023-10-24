---
title: "Export user data from Project for the Web"
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 10/29/2019
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150
ms.localizationpriority: medium
ms.assetid: 27f3838d-3dbe-4b98-80dc-df55f851154d
description: "Learn how your organization can export a specific user's content from your Project for the web environment."
---

# Export user data from Project for the web

This article describes how a Microsoft 365 tenant admin can export a specific user’s data from Project for the web. The admin can then choose to view the user’s data and decide what data they want to make available to the user.

Project for the web data is stored in [Dataverse](/powerapps/maker/common-data-service/data-platform-intro) in Microsoft PowerApps. This article describes how you can:  

- View a specific user’s Project for the web data by using the Advanced Find function in Dynamics 365.  
- Use a PowerShell script to export data about specific projects that your user was a part of.

## Requirements
  
You’ll need the following in order to look for data on a specific user through the Advanced Find search feature:

- You need the Microsoft Entra Object ID (Microsoft Entra ID) of the user. You can find it in the Microsoft Entra Admin Center.  
- You need to be a global admin in your Microsoft 365 tenant. You need this to access the Dynamics 365 Admin Center.  

If you also want to export and view information on specific projects:

- You need to be a tenant admin.
- You need to have a Project Plan 1, Project Plan 3, or Project Plan 5 license.


## Methods for finding your user's data

Depending on the type of user data you need to find, there are two paths you can take in searching for and exporting your user's data.

- **Find data about your user's project and roadmap objects in Dataverse** - Use the Advanced Find feature in the Dynamics 365 Admin Center to find all the user's data that is contained in Dataverse (for example, objects related to their projects and roadmaps).
- **Find data about specific projects that your user was associated with** - Use the project export PowerShell script to get details about specific projects the user was associated with.

## Find user data in Dataverse with the Advanced Find search feature

Project for the web user information that resides in Dataverse - such as roadmap and project objects and properties - are located in specific Dynamics 365 solutions.  The Advanced Find search feature in the Dynamics 365 Admin center can query across entities in these solutions to find the information you need.

### Understand Project for the web Dataverse data and where it resides

When looking for a specific user's Project for the web data in Dynamics 365 Dataverse, it’s located in these five Dynamics 365 solutions:

|Name|Display Name|
|:-----|:-----|
|PortfolioService  <br/> |Portfolio Service  <br/> |
|msdyn_ProjectServiceCore <br/> |Project <br/> |
|MicrosoftDynamicsScheduling  <br/> |Universal Resource Scheduling <br/> |
|msdynce_SchedulingPatch  <br/> |Scheduling Patch <br/> |
|mydynce_Scheduling <br/> | Scheduling <br/> |

You can look specifically at any of these Dynamics 365 solutions to get an idea of the entities that exist for it. Understanding the entities that exist for a specific solution can help you with understanding what to look for in your query.

To view entities for a Dynamics 365 solution:

1. In the Microsoft 365 Admin center, under **Admin centers**, select **Dynamics 365**.

1. In the Dynamics 365 Administration Center, select the default instance, and then select **Open**.

   ![Screenshot of Dataverse instance Open button.](media/CDSInstance.png) 

1. On the Dynamics 365 Settings page, select the **Settings** menu, and in the **Customization** section, select **Solutions**.

1. On the All Solutions page, select the Display Name of the solution that you’re interested in.

    ![Dataverse solutions.](media/CDSsolutions.png) 

1. On the solution information page, expand **Entities** to view them.

   ![Screenshot of Dataverse solutions entities.](media/CDSSolutionEntities.png)
   
1. Under each entity, you can select specific objects to get more details about its properties.

   ![Solutions entities descriptions.](media/CDSEntitiesDesc.png)

### Use Advanced Find to search for user data

Use [Dynamics 365 Advanced Find search](/dynamics365/customer-engagement/basics/save-advanced-find-search) to look for  Project for the web data for your user. Advanced Find will search across all solutions in your Dataverse instance. You can then download the results directly to an Excel spreadsheet and determine what to provide to your user.

1. In the Dynamics 365 Administration Center, select the default instance, and then select **Open**.

2. On the Dynamics 365 Settings page, select the **Settings** menu, and in the **Customization** section, select **Solutions**.

3. Select the **Advance Find** button.

    ![Screenshot of the Advanced Find button.](media/AdvancedFind.png)

4. In Advanced Find, in the **Look for** menu, select the objects that you want to search for, such as your user's projects or roadmaps.

    For example, if you want to view all roadmaps your user was a part of, select **Roadmaps**.

    ![Advanced Find results menu.](media/AdvancedFindLookForRoadmap1.png)

5. To begin building your query, select **Select**, and then select the fields you need to start searching for projects or roadmaps your user was a part of. You’ll need the users Microsoft Entra ID or account name.  

   For example:
   - To find all roadmaps owned by the user, select the Owner field, and then select Equals, and then enter the account name for the user.
   - To find all roadmaps created by the user, select the Created By field, and then select Equals, and then enter the account name for the user.
     ![Create query in Advanced Find.](media/AdvancedFindBuildQueryRM.png)

6. When you’re done with selecting your search criteria, in the ribbon, select **Edit Columns**.

7. On the Edit columns page, select **Add columns**, and then select the columns you want to include in the query.  When done, select **OK**.

8. Select **Results** to run your query.

9. After you receive your results, you can export them to Excel.  To do this, select **Export**, and then select **Static Worksheet**.  

You can then review the results to determine what data you'd like to provide to the user.

## Use the export script to see details on specific projects

If you need to look for more details that are contained in specific projects that the user was associated with, you can use the ExportProjectContent  PowerShell script to get more information on each project. With the script, you can get the following files for a specific project:

- Project files (.MPP) for the project. Add the parameter **-mppexport $true** to the cmdlet to generate .mpp files of the project plans.
- An XML file that contains project details and settings.

### Get the Project IDs of the projects you’re interested in

Before you run the script, you need to get the Project IDs of the projects you’re interested in.

Assuming you've used Advanced Find search to query for the user's projects and have downloaded them to an Excel file, the Project ID column is the first column of the Excel spreadsheet, but it’s hidden by default. Unhiding the first column can be a bit tricky, so if you need help, see [Unhide the first row or column in a worksheet](https://support.office.com/article/unhide-the-first-column-or-row-in-a-worksheet-d6b47608-80ee-4021-9b51-6a1f57269ec9#ID0EAABAAA=Windows).

After you unhide the columns in the spreadsheet, look for the name of the project, and then look for the corresponding value in the Project column to find the Project ID for the project.

![Dataverse Instance.](media/projectIDs.png)

### Run the Export script

Now that you have the Project IDs of the projects you’re interested in looking at, use the **ExportProjectContent** Windows PowerShell function to get more information. The ExportProjectUserContent function is included in the ProjectExport Windows PowerShell module.

[Download the Project Export Windows PowerShell module](https://go.microsoft.com/fwlink/?linkid=2106330) and first unblock the zip file and then unzip the files.

> [!NOTE]
> After you unzip the script, run the following in Windows PowerShell to import the modules:
>
> Import-Module -Name ./projectexport

To run the ExportProjectContent function:

1. In Windows PowerShell, where you’ve imported the module, run the following cmdlet:

   `ExportProjectContent -ProjectId (ProjectID of the project) -OutputDirectory (Location to put files) -InstanceId "(Dataverse instance name)"`

   You’ll need to configure the following parameters when running the script:

   |Parameter|Description|
   |:-----|:-----|
   |ProjectId   <br/> |GUID of the project within Dataverse.  You learned how to find this in the previous section.   <br/> |
   |OutputDirectory  <br/> |Location where the export files are put.   <br/> |
   |InstanceId   <br/> |The identifier of the Dynamics 365 instance you’re using. <br/> |

   To find your Instance ID:

   1. In the Dynamics 365 Administration Center, select the default instance, and then select **Open**.

      ![Screenshot of Open button for Dataverse instance.](media/CDSInstance.png) </br>

   1. On the PowerApps setting page, look at the first part of the URL to determine your Instance ID value. In the graphic below, the Instance ID value would be `https://orgde6d15d8.crm.dynamics.com`.

      ![Screenshot of Find the instance Unique Name.](media/DynamicsOrgid.png)</br>

   As an example of how to run the script, if the Project ID of the project is dd065460-02b8-e911-a989-000d3a170e10, you want the output files to go to C:\User1Project1, and the instance name of the Dataverse org is 
   `https://orgde6d15d8.crm.dynamics.com`, you would run the script like this:
      
   `ExportProjectContent -ProjectID dd065460-02b8-e911-a989-000d3a170e10 -OutputDirectory C:\User1Project1 -InstanceId `https://orgde6d15d8.crm.dynamics.com`"`

1. When the script completes, go to the OutputDirectory location you specified to find the .json files for the project.

   > 3a215ea2-c650-49db-8200-47bd4a7e2278_2023-02-13T21-29-13Z.json

If you have multiple projects, run the script again for each project, using its corresponding ProjectID value.

Note that you may receive multiple versions of your .json file, known as snapshots. These are versions of your project file prior to changes being made to it. Snapshot files will include a timestamp to let you know when they were taken. The **current** version of the file is the one with the **earliest** timestamp, which would be the project creation date.

All snapshots currently stored for the project are exported. Snapshots can be periodically cleared out depending on how active the project is.

The field definitions are at [Export Content Definition](export-project-content-definition.md).

## View and export Project History

Open the **Advanced Find** tool. In the **Look for** menu, select the **Project History object**.

If you want to filter on a particular project, choose **Select**, select the **Project** option from the drop down dialog, and then add the project for which you’d like to see Project History items.

When you’re done with selecting your search criteria, in the ribbon, select **Edit Columns**.

On the **Edit columns** page, select **Add columns**, and then select the columns you want to include in the query. When done, select **OK**.

Select **Results** to run your query.

After you receive your results, you can export them to Excel. To do this, select **Export**, and then select **Static Worksheet**.

Use the [Power Apps portal](https://make.powerapps.com) to view the descriptions of the different fields that are stored with the Project History data. Open the **Project History** table within the **msdyn_ProjectServiceCore_Patch** solution. The **msdyn_project** field is a reference to the related project. **msdyn_projecttask** is a reference to the associated task (if applicable). The **msdyn_details** field is a JSON object that describes the details of the history record. More information on what is contained in msdyn_details can be found in the [Task History Definition](export-task-history-definition.md).

## See Also

[Create, edit, or save an Advanced Find search](/dynamics365/customer-engagement/basics/save-advanced-find-search)

[Delete user data from Project for the web](delete-user-data-from-project-for-the-web.md)

[Export user data from Project Online](/projectonline/export-user-data-from-project-online)

[Export Content Definition](export-project-content-definition.md)

[Task History Definition](export-task-history-definition.md)
