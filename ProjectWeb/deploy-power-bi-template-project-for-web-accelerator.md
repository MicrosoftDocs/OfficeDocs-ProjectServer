---
title: Create a solution to deploy the Power BI template for the Project for the web Accelerator
description: analytics! visualize whirled peas 
author: v-stthomas
ms.author: v-stthomas
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 04/04/2022
ms.custom: template-how-to
audience: admin
---

# Create a managed solution to add the Power BI template to the Project for the web Accelerator

The Project for the web Accelerator solution gives you a head start customizing Project for the web to support common project management scenarios. It's a managed solution, making it easy to deploy new versions as updates.

We encourage you to further customize Project for the web to better meet your specific business needs, and we advise that you do so by creating your own solution to layer on top of the deployed Accelerator. One enhancement that's ready to go is the Power BI template for the Project for the web Accelerator. This article provides guidance for adding the Power BI template to your managed solution to deploy on top of the Accelerator.

> [!IMPORTANT]
> The order of events in this process is critical:
>
>  1. Select (or create) a development environment where you're an admin, and where Project for the web and the Accelerator solution are deployed&mdash;or deploy them, if they aren't there yet.
>  2. Download the Power BI template and deploy it to that development environment.
>  3. In that environment, create a managed solution that contains the steps to integrate the Power BI template (along with any other customizations you might want.).
>  4. Export the solution, and then import it into your production Project+Accelerator environment.

## Prerequisites

- Admin rights in an development environment with the Project for the web Accelerator deployed
- Power BI Desktop and a Power BI Pro account
- Rights to use the Common Data Service connector
- An understanding of [managed solution layers](/power-platform/alm/solution-layers-alm#layering-within-a-managed-solution)
- (Optional, but recommended) A [Developer plan](/power-apps/maker/developer-plan) so you can export your solution to easily deploy in other environments.

## Create a managed solution for customizing Project for the web and the Accelerator

To customize the Project Power App after deploying the Accelerator, create a new managed solution that contains the customizations, and then layer that solution over the Accelerator.

Like the Project Power App, the Accelerator is a [managed solution](/power-platform/alm/solution-concepts-alm) so that Microsoft can make future improvements and fixes, and so customers can deploy such changes as upgrades to their environment. Although you can customize the environment after you deploy the Accelerator, this might cause issues if you then try to deploy an update. 

> [!TIP]
> If you're a beginner to managed solutions, visit [Application lifecycle management (ALM) with Microsoft Power Platform](/power-platform/alm/) to prepare before your first try.

1. Select or create a development environment with Project for the web and the Accelerator deployed.
1. In the navigation pane of that environment, select **Solutions**, and then on the command bar select **+ New Solution**.

   :::image type="content" source="media/customize-project-accelerator-new-solution.png" alt-text="Start a new solution.":::

1. Add a **Display Name**&mdash;the solution will bear this name in environments where it's deployed.
1. A value for **Name** will then appear. It's safe to accept this value, but you can change it provided you don't use any invalid characters.
1. If you already have a [solution publisher for your custom solutions](/power-apps/maker/data-platform/create-solution#create-a-solution-publisher), use it for **Publisher**. If not, create one to use:

   - In the **New Solution** dialog, under **Publisher** select **+ New publisher**, complete the dialog that opens and then select **Create**.

   :::image type="content" source="media/customize-project-accelerator-new-publisher.png" alt-text="Add a new publisher for your custom solutions.":::

1. Adjust the **Version** if you want, and then select **Create**. Your new solution opens.

For additional options to create a custom solution, see [Create a solution](/powerapps/maker/data-platform/create-solution).

### Example customization: add an action to send email when a Project Request is approved

The cloud flow included with the *Project Requests* scenario is very simple: it creates a project from a request when *Request State* is set to *Approved*. By adding an action to the cloud flow, you can make it also send an email notification.

1. Open the [Power Apps Portal](https://make.powerapps.com) and select your development environment.
1. In the list of solutions, select **Project for the Web Accelerator**.
1. In the navigation pane, select **Cloud Flows**.

   :::image type="content" source="media/cloud-flow-in-solution.png" alt-text="{alt-text}":::

1. Select **When the request state is updated to Approved** to open it.
1. On the command bar, select **Edit**.
1. Select **+ New step**.
1. Under **Choose an operation**, enter *Out* and then select **Office 365 Outlook**.

   :::image type="content" source="media/customize-project-accelerator-add-ol-connector.png" alt-text="Add the Outlook connector to your new flow step.":::
<!-- Resume here -->
1. Save and close the flow.
1. On the command bar, select **Publish all customizations**.

   :::image type="content" source="media/publish-customizations.png" alt-text="Publish your changes to the flow to make them functional":::

### Disabling the flow

1. Open the [Power Apps Portal](https://make.powerapps.com).
1. In the navigation pane, select **Solutions**, and then select **Project for the Web Accelerator**.
1. In the navigation pane, select **Cloud Flows**, and then select **When the request state is updated to Approved**.
1. Select **...** to open the flow menu, then select **Turn Off**.
1. On the command bar, select **Publish all customizations**.

  :::image type="content" source="media/disabling-the-flow.png" alt-text="Turn off the flow":::


## Deploy the Power BI template

1. Download the [Power BI template](/OfficeDev/Project-Accelerator#heres-the-latest-version-of-the-power-bi-template-for-the-accelerator).
1. Open Power BI Desktop.
1. When prompted for the environment url, use the base url of your development environment. For example: `https://mydevenvironment.crm.dynamics.com`

When you deploy the report, ensure that your team will have access to it. [Learn more about sharing in Power BI](https://docs.microsoft.com/power-bi/collaborate-share/service-share-dashboards).

### Modify the Project Accelerator – Reports menu to use the deployed template or any Power BI report

> [!IMPORTANT]
> You must first deploy the Power BI report to PowerBI.com
> To preserve your ability to upgrade the Accelerator, [create a solution](/powerapps/maker/data-platform/create-solution) to contain your customizations.

The Report menu currently points to a web resource file with instructions on how to get the Power BI Template with the Accelerator. Because the Accelerator is a managed solution, this web resource cannot be edited. There are two options to have the report bring up the Power BI report:

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

## Next steps

- [Write how-to guides](contribute-how-to-write-howto.md)
- [Links](links-how-to.md)
