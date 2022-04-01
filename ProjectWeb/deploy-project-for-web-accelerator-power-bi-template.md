---
title: Deploy the Project for the web Accelerator and Power BI template
description: Deploying the Accelerator to your Project for the web environment adds project management scenarios such as Project Requests, Changes, and Status. Add a Power BI template for extra reporting options. Customize the Accelerator to use the Power BI template.   
author: v-stthomas
ms.author: v-stthomas
manager: alexla
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: admin
---

# Deploy the Project for the web Accelerator and Power BI template

Although people in your organization can start using Project for the web as soon as you subscribe to Microsoft 365, you'll probably want to customize the environment to meet your specific business needs. Save time with several common scenarios by deploying the Project for the web Accelerator and Power BI template.

## Prerequisites

- Admin rights in an environment with the [deployed Project for the web solution](https://docs.microsoft.com/project-for-the-web/deploying-project)
- Rights to create Power Automate flows using the [Common Data Service connector](/connectors/commondataserviceforapps/).
- The appropriate privileges to deploy the Power BI content pack to powerbi.com.
<!-- Rights, permissions, and privileges? Three different things? -->
## Scenarios added by the Accelerator

💡 **Project Requests**. Create a list for project ideas that include a business case and expected impact. The included Power Automate flow creates a project when a request is set to *Approved*.

💼 **Programs**. Create a hierarchy of programs and projects see how work fits into the bigger picture.

🔥 **Risks and Issues**. Manage the surprises that accompany every project. Create and assign risks and issues to minimize impacts to a project's schedule.

🚧 **Changes**. Use change tracking processes to help understand the history of a project.
<!-- Does this scenario enable rollbacks? -->

📝 **Status**. Centralize recording of project status to keep stakeholders up-to-date.

## Deploy the Accelerator

1. Download the [Accelerator](/OfficeDev/Project-Accelerator/blob/main/README#heres-the-latest-version-of-the-accelerator) and save it locally. Don't unpack it&mdash;the import process uses the zipped file.
1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Open the **Environment** menu and select your Project for the web environment.

   :::image type="content" source="media/environment_menu.png" alt-text="The Power Apps Portal Environment menu.":::

1. On the navigation pane, select **Solutions**.
1. On the command bar, select **Import**.
1. In the **Import a solution** dialog, select **Browse**, then find and select the Accelerator file you downloaded.
1. Select **Next**, then select an existing connection to a Power Automate flow or create a new one.
1. Select **Next** and then select **Import**.

When deployment succeeds, the Project Power App will look like this:

:::image type="content" source="media/project-with-the-accelerator.png" alt-text="The Project Power App after the Project for the web Accelerator is deployed.":::

## Create a custom solution to add to the Accelerator

Like the Project Power App, the Accelerator is a [managed solution](https://docs.microsoft.com/en-us/power-platform/alm/solution-concepts-alm) so that Microsoft can make future improvements and fixes, and so customers can deploy such changes as upgrades to their environment. Although you can customize the environment after you deploy the Accelerator, this might cause issues if you then try to deploy an update.

To customize the Project Power App after deploying the Accelerator, create a separate solution that contains the customizations and deploy it to the environment where you deployed the Accelerator. Your custom solution is deployable in other environments that have the Project Power App and the Accelerator.

For more information about managed solutions, see [Application lifecycle management (ALM) with Microsoft Power Platform](https://docs.microsoft.com/en-us/power-platform/alm/). For steps to create a custom solution, see [Create a solution](https://docs.microsoft.com/en-us/powerapps/maker/data-platform/create-solution).

## Scenario: Project Requests

The Accelerator includes a Project Request table that your teams can use to propose projects, and a Power Automate flow to create a project when a proposal is approved.
<!-- Resume here. -->
To get started, create a new Project Request. All requests start of in a _New_ state. 

![Project request in a new state](images/new-state.png)

To create a project, change the state to _Approved_ and press the _Save_ button to save the record. In a few moments, a new project will appear in the list of projects.

### Customizing the flow

The flow included with the Accelerator is very simple: it creates a project from a request in an _Approved_ state. This can be customized to support scenarios such as including steps to send a notification to Teams. Customizing the flow starts in the Power Platform makers portal.

1. Open the Project for the Web Accelerator solution in [Power Apps](https://make.powerapps.com)
1. Look for the _When the request state is updated to Approved_ cloud flow
![Cloud Flow in the solution](images/cloud-flow-in-solution.png) 
1. Click on the label to open the flow in flow.microsoft.com
1. Edit the flow to support the workflows of your team
1. Save the Flow and close the browser tab
1. In the Power Apps makers portal, press the _Publish all customizations- button to persist changes to the flow
![Publish customizations button](images/publish-customizations.png)

### Disabling the flow
The flow can be disabled from within the solution explorer.
Open the Project for the Web Accelerator solution in [Power Apps](https://make.powerapps.com)
1. Look for the _When the request state is updated to Approved_ cloud flow 
1. Press the "..." to open the menu for the flow
1. Select the _Turn Off_ menu option
1. At the top of the window, press the _Publish all customizations- button to persist changes to the flow
![Turn off flow](images/disabling-the-flow.png)

## Using the Power BI template

### Prerequisites

- An environment with Project for the web and the Project Accelerator in it.
- Admin rights to the environment

## Deploy the Power BI template

1. Download the [Power BI template](https://github.com/OfficeDev/Project-Accelerator/blob/main/releases/Project_for_the_Web_Accelerator_report_v1.1.pbit?raw=true) for the Accelerator.
2. Deploy it using Power BI Desktop or in the [PowerBI.com service](https://www.powerbi.com).
3. When prompted for the environment url, use the base url of your environment. For example: `https://myenvironment.crm.dynamics.com`

When you deploy the report, ensure that your team will have access to it. [Learn more about sharing in Power BI](https://docs.microsoft.com/power-bi/collaborate-share/service-share-dashboards).

### Modify the Project Accelerator – Reports menu to use the deployed template or any Power BI report

#### Prerequisites

1.	Power BI report has been deployed to PowerBI.com
2.	A customized solution has been created to include the changes. To create a solution please review [Create a solution](https://docs.microsoft.com/en-us/powerapps/maker/data-platform/create-solution).

The Report menu currently points at a web resource file containing HTML with instructions on how to get the Power BI Template with the Accelerator. Since the Accelerator is managed, the web resource cannot be edited. There are two options to have the report bring up the Power BI report:

#### Updating the report menu via Power BI embedded report

1.	Sign into [powerapps.com](https://make.powerapps.com)
2.	Select the environment containing the Accelerator
3.	Select solutions -> the customized solution -> Edit
4.	Select the Objects option
5.	New -> Dashboard -> Power BI embedded

![Add embedded report to solution](images/add-embedded-report.png)

6.	Give the report a name and choose the workspace/report and save

![Choose Power BI Report](images/choose_report.png)

7.	If not already added, add the site map to the custom solution
* Add existing -> more-> Site Map
* Choose Project – msdyn_ProjectServiceCore 
* Click add
10.	Select the site map and click edit
11.	Select the Reports option under Reporting
* Select Type = Dashboard
* Default Dashboard = choose the report from the drop down
* Save and close

![Set Sitemap embedded report](images/new-embedded-report-site-map.png)

10.	Click Publish
11.	Go back to the Project app and click Report
12.	The report will now show up along other reports in the environment

![Power BI reports in the Project Power App](images/powerbi-in-app-dashboard.png)

#### Updating the report menu via Web resource (full frame)

The Accelerator already contains a placeholder for the Power BI template. Once you've deployed the Accelerator and the Power BI template, follow these steps to have the Power BI report appear in the Accelerator.

1. Once you've deployed the Power BI template, open the report in [PowerBI.com](https://www.powerbi.com).
2. Press the file -> Embed Report -> Website or portal

![The website or portal menu option under the share button](images/share-powerbi-report.png)

3.	Copy the link in the top box ("Here's a link you can use to embed content") and keep it handy.

![Embed link](images/reports-link-code.png)

4.	Sign into [Power Apps](https://make.powerapps.com)
5.	Select the environment containing the Accelerator
6.	Select solutions -> the customized solution -> Edit
7.	Select the Objects option
8.	New -> more -> Web resource 
9.	Set
*	Display Name: Accelerator Power BI report
* Name: Accelerator_report
* Type: Webpage HTML



10.	Create a new html file to upload with the follow text. Update the “REPLACE THIS” with the embedded string copied earlie

```
  <html>
  <head>
    </head>
    <body onfocusout="parent.setEmailRange();" style="overflow-wrap: break-word;">
      <iframe width="100%" height="100%" src="REPLACE THIS" frameborder="0" allowfullscreen="true"></iframe>
    </body>
  </html>
```

11.	Press OK to save the changes and close the dialog.
12.	If not already added, add the site map to the custom solution
* Add existing -> more-> Site Map
* Choose Project – msdyn_ProjectServiceCore 
* Click add
13.	Select the site map and click edit
14.	Select the Reports option under Reporting
* Select Type = Web Resource
* URL = Accelerator Power BI report

![Set Sitemap web resource](images/set-report-web-resource-site-map.png)

* Save and close
15.	Click Publish
16.	Go back to the Project app and click Report
17.	The report will now show up taking up the entire section

![Power BI reports in the Project Power App](images/powerbi-in-app.png)

## Licensing

The Accelerator solution and Power BI template are distributed free of charge under the MIT license.
However, using them in your environments to work with _Project for the web_ has certain licensing implications.

Refer to the [Project Service Description](https://docs.microsoft.com/office365/servicedescriptions/project-online-service-description/project-online-service-description) for details about Project licensing.

### Using the Accelerator without the Power BI content pack

Using all the customizations -except the reports- requires a **Project Plan 1** license. This applies to your project managers who also need to do things like organize programs, track issues and risks, manage the business case and financials, or edit the custom columns such as corporate sponsor of the project.

Users who don't need to make any changes to the project and only need to view things like risks and issues need a **Microsoft 365 license**.

### Using the Accelerator with the Power BI content pack

Users who need to view the Power BI reports in the Project Accelerator need the following
1.  an M365 or Project Plan 1 license
2.  a Power BI license

### Using the Accelerator without using Project for the web

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
