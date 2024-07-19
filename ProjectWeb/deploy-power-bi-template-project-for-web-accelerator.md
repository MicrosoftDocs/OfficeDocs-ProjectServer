---
title: Add the Power BI template to the Project Management Office Accelerator
description: Deploy the Project Management Accelerator and the Power BI template into a development environment. Create, export, and deploy a managed solution that integrates the Power BI template into the PMO Accelerator.
author: jenzamora
ms.author: jenz
manager: jtremper
ms.service: project-web
ms.topic: how-to
ms.date: 04/04/2022
ms.custom: template-how-to
audience: admin
---

# Add the Power BI template to the Project Management Office Accelerator

The [Project Management Office Accelerator solution](deploy-project-for-web-accelerator-power-bi-template.md) gives you a head start customizing Project for the web to support common project management scenarios. It's a managed solution, making it easy to deploy new versions as updates.

We've prepared a Power BI template for the Project Management Office Accelerator (PMO Accelerator). To add the Power BI template, create a managed solution for it, then deploy that solution on top of the PMO Accelerator.

The process has four broad steps:

1. Open a development environment where you're an admin, with Project and the PMO Accelerator deployed already.
1. Download the Power BI template and deploy it to that development environment.
1. In that environment, create a managed solution that contains the steps to integrate the Power BI template.
1. Export the solution, and then import it into your production Project+Accelerator environment.

## Prerequisites

- Admin rights in a development environment [with the Project Management Office Accelerator deployed](deploy-project-for-web-accelerator-power-bi-template.md)
- Power BI Desktop and a Power BI Pro account
- Rights to use the Common Data Service connector
- An understanding of [managed solution layers](/power-platform/alm/solution-layers-alm#layering-within-a-managed-solution)
- (Optional, but recommended) A [Developer plan](/power-apps/maker/developer-plan) so you can export your solution to easily deploy in other environments

## Deploy the Power BI template

1. Download the Power BI template at [https://aka.ms/ProjectReports](https://aka.ms/ProjectReports). (See [Extend the Power BI template for Project for the web](https://support.microsoft.com/office/extend-the-power-bi-template-for-project-for-the-web-23fb86a7-e1b2-45fc-b82b-8f64ae44c51c).)
1. Open Power BI Desktop.
1. Select **File** > **Import**, then select the downloaded template.
1. When prompted for the environment url, use the base url of your development environment. For example: `https://mydevenvironment.crm.dynamics.com`
1. Note the workspace where you save the report.
1. To [ensure that your team will have access to the report, share it](/power-bi/collaborate-share/service-share-dashboards).

     - On the [Power BI portal](https://app.powerbi.com/), in the navigation pane select **Workplace** and then select the workspace where you put the report.
     - In the report's row select the three vertical dots to open the menu, and then select **Manage permissions**.
         :::image type="content" source="media/customize-project-accelerator-sharing-choose-pbi-rpt-1.png" alt-text="Open the Power BI template report menu":::

     - Under **Related content**, expand **Datasets**, and then select the report.
         :::image type="content" source="media/customize-project-accelerator-sharing-choose-pbi-rpt-2.png" alt-text="{alt-text}":::

     - In the **Grant people access** dialog, enter the email addresses of the Teams groups who need access, select the sharing options you want, and then select **Grant access**.
         :::image type="content" source="media/customize-project-accelerator-sharing-options-pbi-rpt.png" alt-text="Sharing options for granting access to the Power BI report":::

         > [!NOTE]
         > You might want to repeat this process for several different groups to control who can do what with the report in Project for the web.

## Create a managed solution for deploying the Power BI template

Like the Project Power App, the PMO Accelerator is a [managed solution](/power-platform/alm/solution-concepts-alm) so that Microsoft can make future improvements and fixes, and so customers can deploy such changes as upgrades to their environment. Although you can customize the environment after you deploy the Accelerator, this might cause issues if you then try to deploy an update.

To add the Power BI template, you should create a managed solution that contains the customizations required to integrate the template into the Project+Accelerator environment. 

> [!TIP]
> If you're a beginner to managed solutions, visit [Application lifecycle management (ALM) with Microsoft Power Platform](/power-platform/alm/) to prepare before your first try.

1. Open your development environment with Project for the web and the PMO Accelerator deployed.
1. In the navigation pane, select **Solutions**, and then on the command bar select **+ New Solution**.

    :::image type="content" source="media/customize-project-accelerator-new-solution.png" alt-text="Start a new solution.":::

1. Add a **Display Name**&mdash;the solution will bear this name in environments where it's deployed.
1. A value for **Name** will then appear. It's safe to accept this value, but you can change it provided you don't use any invalid characters.
1. If you already have a [solution publisher for your custom solutions](/power-apps/maker/data-platform/create-solution#create-a-solution-publisher), use it for **Publisher**. If not, create one to use:

    - In the **New Solution** dialog, under **Publisher** select **+ New publisher**, complete the dialog that opens and then select **Create**.

    :::image type="content" source="media/customize-project-accelerator-new-publisher.png" alt-text="Add a new publisher for your custom solutions.":::

1. Adjust the **Version** if you want, and then select **Create**. Your new solution opens.

> [!TIP]
> For more options when you create a custom solution, go to [Create a solution](/powerapps/maker/data-platform/create-solution).

## Modify the PMO Accelerator – Reports menu to include the deployed Power BI template

> [!IMPORTANT]
> You must first [deploy the Power BI report to PowerBI.com](#deploy-the-power-bi-template).

When you deploy the PMO Accelerator, the Reports menu points to a web resource file with instructions on how to get the Power BI Template with the Accelerator. Because the Accelerator is a managed solution, this web resource cannot be edited. There are two options to have the report bring up the report from the Power BI template.

### Option 1: Add a dashboard with the Power BI embedded report

1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Select the environment where you created your customized managed solution.
1. In the navigation pane, select **Solutions**.
1. Select your customized managed solution, and then on the command bar select **Edit**.

    :::image type="content" source="media/customize-project-accelerator-edit-solution.png" alt-text="Edit the selected solution.":::

1. In the navigation pane, select **Objects**.
1. On the command bar, select **New** > **Dashboard** > **Power BI embedded**.

    :::image type="content" source="media/add-embedded-report.png" alt-text="Add a Power BI embedded dashboard to your custom solution.":::

1. In the **New Power BI embedded Dashboard** dialog, enter a **Display Name**, then select a **Power BI workspace** and **Power BI report**, and then select **Save**.
1. Add the *Project* site map to your custom solution.

     - On the command bar, select **Add existing** > **More** > **Site Map**.
     - Select the item with the **Name** *msdyn_ProjectServiceCore*, and then at the bottom of the dialog select **Add**.

1. Select the **Project** site map, and then on the command bar select **Edit**.
1. Select **Reporting** > **Reports**.

     - Set **Type** to **Dashboard**.
     - For **Default Dashboard**, select the Power BI report, and then on the command bar select **Save and close**.

1. Select **Publish**.
1. Open Project for the web, and in the navigation pane select **Reports**.
1. The Power BI embedded dashboard now appears.

    :::image type="content" source="media/powerbi-in-app-dashboard.png" alt-text="The Power BI report for the Accelerator, displayed in Project for the web.":::

### Option 2: Add a Web resource that embeds the Power BI report (full frame)

The Accelerator includes a placeholder for the Power BI template. Once you've deployed the Accelerator and the Power BI template, follow these steps to have the Power BI report appear in the Accelerator.

1. Once you've deployed the Power BI template, open the report in [PowerBI.com](https://www.powerbi.com).
1. Select **File** > **Embed Report** > **Website or portal**.
1. Copy the link labeled **Here's a link you can use to embed content** and keep it handy.
1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Select the environment that contains the Accelerator.
1. In the navigation pane, select **Solutions**, then select your custom managed solution, and the on the command bar select **Edit**.
1. In the navigation pane, select **Objects**.
1. On the command bar, select **New > More > Web resource**.
1. Enter the following values:

     - **Display Name** = *Accelerator Power BI report*
     - **Name**: *Accelerator_report*
     - **Type**: *Webpage HTML*

1. Create a new HTML file to upload with the following text, but change the value of **src** to the powerbi.com link you copied in step 3 of this procedure. Give a short descriptive name, such as *PBI extra.html*

     ```html
     <html>
     <head>
     </head>
     <body onfocusout="parent.setEmailRange();" style="overflow-wrap: break-word;">
      <iframe width="100%" height="100%" src="REPLACE THIS" frameborder="0" allowfullscreen="true"></iframe>
     </body>
     </html>
     ```

1. Select **OK**.
1. If it's not already there, add the *Project* site map to your custom solution.

     - On the command bar, select **Add existing** > **More** > **Site Map**.
     - Select the item with the **Name** *msdyn_ProjectServiceCore*, and then at the bottom of the dialog select **Add**.

1. On the site map, under **Reporting** select **Reports** to open the control pane.

     :::image type="content" source="media/select-reports-subarea-of-site-map.png" alt-text="Select the Reports subarea":::

1. In the control pane, set Type to **Web Resource**, and then under URL, enter the name of the HTML file you created earlier in this process.
1. At the top right corner of the Site Map, select **Save**, and then select **Publish**. Close the site map.
1. On the command bar, select **Publish all Customizations**.
1. Open Project for the web, and in the navigation pane, select **Reports**.
1. The report now appears in Project for the web. Tp open it, on the navigation pane select **Reports > Report**.

    :::image type="content" source="media/powerbi-in-app.png" alt-text="Power BI Project Accelerator report.":::

     > [!NOTE]
     > The template includes numerous reports—use the tabs along the bottom to switch between them.

## Next steps

- [Basic concepts for designers in the Power BI service](/power-bi/fundamentals/service-basic-concepts)
- [Introduction to Power BI deployment pipelines](/power-bi/create-reports/deployment-pipelines-overview)
