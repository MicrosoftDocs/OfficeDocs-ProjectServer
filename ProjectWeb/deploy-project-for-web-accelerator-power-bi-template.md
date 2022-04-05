---
title: Deploy the Project for the web Accelerator
description: Deploying the Accelerator to your Project for the web environment adds improved project management scenarios such as Project Requests, Changes, and Status.   
author: v-stthomas
ms.author: v-stthomas
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: admin
---

# Deploy the Project for the web Accelerator

Although people in your organization can start using Project for the web as soon as you subscribe to Microsoft 365, you'll probably want to customize the environment to meet your specific business needs. Save time with several common scenarios by deploying the Project for the web Accelerator.

## Prerequisites

- Admin rights in an environment with the [deployed Project for the web solution](https://docs.microsoft.com/project-for-the-web/deploying-project)
- Rights to create Power Automate flows using the [Common Data Service connector](/connectors/commondataserviceforapps/).

## Scenarios added by the Accelerator

💡 **Project Requests**. Create a list for project ideas that include a business case and expected impact. The included Power Automate flow creates a project when a request is set to *Approved*.

💼 **Programs**. Create a hierarchy of programs and projects see how work fits into the bigger picture.

🔥 **Risks and Issues**. Manage the surprises that accompany every project. Create and assign risks and issues to minimize impacts to a project's schedule.

🚧 **Changes**. Use change tracking processes to help understand the history of a project.

📝 **Status**. Centralize recording of project status to keep stakeholders up-to-date.

## Deploy the Accelerator

1. Download the [Accelerator](/OfficeDev/Project-Accelerator/blob/main/README#heres-the-latest-version-of-the-accelerator) and save it locally. Don't unpack it&mdash;the import process uses the zipped file.
1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Open the **Environment** menu and select your Project for the web environment.

   :::image type="content" source="media/environment_menu.png" alt-text="The Power Apps Portal Environment menu.":::

1. On the navigation pane, select **Solutions**.
1. On the command bar, select **Import**.
1. In the **Import a solution** dialog, select **Browse**, then find and select the Accelerator file you downloaded.
1. Select **Next**, then select an existing connection to a Power Automate flow, or create a new connection.
1. Select **Next** and then select **Import**.

When deployment succeeds, the Project Power App will resemble this:

:::image type="content" source="media/project-with-the-accelerator.png" alt-text="The Project Power App after the Project for the web Accelerator is deployed.":::

## Licensing

The Accelerator solution is distributed free of charge under the MIT license.
However, using them in your environments to work with Project for the web has certain licensing implications.

> [!NOTE]
> The [Project Service Description](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description) provides details about Project licensing.

Using the Accelerator requires a **Project Plan 1** license. This applies to your project managers who also need to do such things as organize programs, track issues and risks, manage the business caseS and finances, or edit the custom columns such as corporate sponsor of the project.

Users who only need to view projects (not add or change any data or components) need a **Microsoft 365 license**.

### Using the Accelerator without using Project for the web
<!-- Is this really practical? There seem to be a lot of hooks to Dynamics/Dataverse built-in. This heading suggests we're going to tell them how. -->
All the content on this site is completely free for you to reuse in your own applications. Refer to the [LICENSE](LICENSE) file for details. It is only when using the Accelerator with the Project Power App or when using the Project for the web tables that there are additional licensing implications.

## Support and Troubleshooting

For support of the Accelerator you can either raise an issue here in Github or open a new service request through the Microsoft 365 admin center Support tab. Microsoft fully support the deployment and use of the Accelerator with Project for the web, however we do not support any subsequent customizations that either you or a partner may have added on top of the Accelerator. We would of course still support the core functionality even if customizations have been added.

For best experience to avoid any issues with subsequent releases of the Accelerator always follow best practices of using managed solutions for any additional customization. [Learn about using solutions](https://docs.microsoft.com/powerapps/maker/data-platform/solutions-overview) and related documents for guidance on working with solutions and understanding correct use of solution layers.

### Errors about Dependencies
If you get an error (shown below) that you need a version of msdyn_ProjectServiceCore > 1.0.0.87, navigate to your list of solutions for your environment in [Power Apps](https://make.powerapps.com) and ensure that the latest version of the Project Service Core solution is installed. You'll see an "Update" option next to the solution name if there is an update available. After the update is complete, try installing the Accelerator package again.
![Power BI reports in the Project Power App](images/../dependency-error.png)

### Unable to turn on the flow for converting Project Requests into Projects

Some customers upgrading from an earlier version of the Accelerator may encounter one of these errors trying to turn on the flow.

![Failed to activate component(s). Flow save failed with code OpenApiOperationParameterValidationFailed and message Input parameter item' validation failed in workflow operation...](images/maker-flow-error.png)

or this error in flow.microsoft.com

![Flow save failed with code OpenApiOperationParameterValidationFailed and message Input parameter item validation failed in workflow operation Create_a_new_record: The API operation 'CreateRecord' is missing required property item/msdyn_schedulemode.](images/flow-error.png)

To resolve this, do the following.
1. In the Project Accelerator solution, open the flow by clicking on the label of the cloud flow _When a Request State is Updated..._. This will open the flow.microsoft.com editor.
![Solution explorer](images/open-the-flow.png)
1. Press the Edit flow button
![Edit flow button](images/edit-flow-button.png)
1. Click the _Condition_ step to expand it
![Condition step](images/flow-condition.png)
1. In the _If yes_ condition, expand the _Create a new record_ step.
1. Choose a value for the _Scheduling Mode_ field. Set it to _Fixed Duration_ if you're unsure of which scheduling mode you want. Don't leave it blank. [Learn more about scheduling modes](https://techcommunity.microsoft.com/t5/project-support-blog/schedule-modes-and-task-and-resource-usage-in-project-for-the/ba-p/2656738).
1. Press the save button to persist the changes
1. Press the back arrow at the top of the flow editor
![Back arrow](images/flow-back.png)
1. Press the _Turn On_ button to enable the flow
![Turn on](images/turn-on-flow.png)
1. Close the browser tab to return to the Accelerator solution in make.powerapps.com
1. Press the _Publish customizations_ button at the top to persist the changes.
1. The flow should now work! To try it out, open a Project Request to the _Approved_ state and a project will be created
Microsoft Open Source
Docs## Next Steps
