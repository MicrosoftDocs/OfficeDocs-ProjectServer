---
title: Integrate Project for the web into your project management processes  
description: Learn how Project for the web differs from Project Web App. Decide which projects can use default Project for the web features, and how to customize the Project Power App to conform Project. Deploy the Project for the web Accelerator and Power BI template to get a head start with pre-built customizations.
author: v-stthomas
ms.author: v-stthomas
manager: alexla
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: admin
---

# Integrate Project for the web into your project management processes

This article compares Project for the web and the Project Web App to help you support Project for the web adoption. It explains how to customize the Project Power App to support processes you've implemented in Project Online, and introduces the Project for the web Accelerator&mdash;a free solution that adds numerous project management scenarios to the Project Power App, saving you time on customizing the Project Power App to help Project for the web meet your business process requirements.

> [!NOTE]
> To customize Project for the web, you need an account with [the right security role](/powerapps/maker/model-driven-apps/privileges-required-customization#system-administrator-and-system-customizer-security-roles).

Project for the web is for projects based on the Project Power App. It's easy to quickly get started creating projects, assigning tasks, and tracking progress. It uses familiar components available with Microsoft 365 subscriptions, such as Teams and SharePoint. And it's built on the Power Platform, with scalable, secure components that support [solutions](/power-platform/alm/solution-concepts-alm).

Project for the web's simplicity relative to Project Online will encourage some people to use it in lieu of Planner. Meanwhile, you can customize the Project Power App to support your management processes, and your teams will become comfortable using Project for the web to track progress for more of their efforts.

## Prerequisites

- Ensure you have [appropriate licenses](/power-platform/admin/powerapps-flow-licensing-faq).
- Understand [the basics of the Power Apps portal](/learn/paths/get-started-power-apps-portals).

## Compare Project Web App and Project for the web

- For a basic comparison of the two products, see the [FAQ about supporting projects in Project Web App and Project for the web](https://support.microsoft.com/office/project-for-the-web-and-project-online-6569170c-5c8e-474e-a7f0-642872f62f8a).
- For a detailed list of Project for the web features, see [What is Project for the web?](https://support.microsoft.com/office/what-is-project-for-the-web-c19b2421-3c9d-4037-97c6-f66b6e1d2eb5).
- The exact differences between Project Web App and Project for the web depend on your plan and subscription. For a full comparison of all Project plans and subscriptions, see the [Microsoft Project service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

### Table of architectural differences

The following table provides a comparison between the components of Project Web App and Project for the web.

| Component (links to sections, below) | In Project Web App | In Project for the web |
| :-- | :-- | :-- |
|[Data](#data-components) and [Logic](#logic-components) | SharePoint lists and workflows | [Dataverse](/powerapps/maker/model-driven-apps/define-data-model-driven-app) and Power Automate |
|[Security](#security) | [SharePoint permissions or Project Online permissions](/projectonline/change-permission-management-in-project-online) | [Security roles](project-for-the-web-security-roles.md) |
|[UI](#ui-components) and [Visualizations](#visualizations) | Project Detail Pages and [Options based on your plan/subscription](/projectonline/what-reporting-tools-can-i-use-with-project-data) | [Views, Forms](/powerapps/maker/model-driven-apps/model-driven-app-components#ui-components), [Charts, and Dashboards](/powerapps/maker/model-driven-apps/model-driven-app-components#visualizations) |

## Data components

Project data for Project Web App is stored in SharePoint lists. Project for the web data is stored in Dataverse tables. While suitable for many scenarios, SharePoint lists do have some limitations compared to Dataverse tables. For a comparison, see [Handling data for Project](/project-for-the-web/handling-data-for-project-for-the-web-and-roadmap).

### Dataverse in the Project Power App

The Project Power App stores data in your environment's Dataverse, in three classes of tables.

1. Core scenario tables hold data used for projects in Project for the web. You can modify some of these tables if needed to support special functionality in your environment. For example, you can [add a custom column](add-custom-column-project-power-app.md) to the *Project* table to make it available to all projects in your environment.

   To review these tables, search on the Power App portal using the search term *Project*. Then, select each table to review the existing columns and app components for the selected table.

  :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-06.png" alt-text="In the navigation pane, under Dataverse select Tables. Set the view filter to All, then search using the term Project.":::

1. Project Accelerator tables support the [Project for the web Power App Accelerator](https://aka.ms/projaccelerator). These tables only exist if you've deployed the Project Accelerator in your environment. You can customize them to change the implementation of the scenarios the Project Accelerator provides. Be sure you know what you're doing and have a plan before you make changes. Other scenario components rely on these tables, such as Power Automate flows.

   > [!NOTE]
   > The Risks and Issues tables are part of the same scenario and shouldn't be changed separately.

   - *Project Requests*
   - *Programs*
   - *Risks*
   - *Issues*
   - *Changes*
   - *Status Report*

1. System tables provide the basic framework of the Project Power App. Don't try to change them if you're not a Power Platform expert.

   - *Document Header*
   - *Document Section*
   - *Long Running Job Status*
   - *OperationSet*
   - *OperationSet Detail*

## UI components

Both Project Web App and Project for the web provide a UI for data entry using instances of project templates that you customize. Both UIs use a web browser, but differ in the details. For a comparison of the design experiences, see [Edit project details in Project Online](https://support.microsoft.com/office/edit-project-details-in-project-online-9ea8d54f-d46e-4de7-a503-93095d83095d) and [Customizing the Project Power App](/project-for-the-web/faq#customization).

To customize the Project for the web UI, you modify or create views and forms in the Project Power App. Views define how to display a list of rows for a specific table in your application. Each view definition contains which columns to display, the width of each column, and default row sorting behavior and filters. Forms present a set of data-entry columns for a given table, and provide the interface for people working with projects.

### Views in the Project Power App

To customize Project Power App views, use the [Power Apps Portal](https://make.powerapps.com). Create a view to customize the display of data from a single table.

#### Create a view

1. Open the [Power App Portal](https://make.powerapps.com), then on the navigation pane select **Data** > **Tables**.
1. In the view selector on the command bar, select **All**, then search for *Project*.
1. In the search results, sort **Customizable** by **True then False** to list customizable tables first.
1. Find the table you want, select its name to open it, and then select the **Views** tab.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-02.png" alt-text="The Views tab for the Project table in the Project Power app.":::

1. On the command bar, select **+Add view**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-10.png" alt-text="The Add view command for a single Project Power App table.":::

1. Follow the steps in the **Create a view** dialog.

For more information about Power Apps views, see [Understand model-driven app views](/powerapps/maker/model-driven-apps/create-edit-views).

### Forms in the Project Power App

When users open a project in Project for the web, the browser displays the default Main form&mdash;the *Information* form in Project for the web, unless you select a different default for your environment. All projects created in Project for the web in the same environment display the same Main form.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-03.png" alt-text="The Information form of a project opened in Project for the web.":::

When you open the Project Power App in an environment, you can set a different default Main form, and you can also edit forms. Both changes affect all projects in that environment, providing centralized control over the functionality of projects.
  
   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-04-closeup.png" alt-text="The Information form of the Project Power App." lightbox="media/move-to-project-for-the-web-from-project-web-app-04.png":::

For more information about Power Apps forms, see [Create and design model-driven app forms](/powerapps/maker/model-driven-apps/create-design-forms).

## Logic components

Project Web App uses SharePoint workflows to control the logical flow of projects. In Project for the web, you use Power Automate. For a comparison, see [Classic SharePoint workflows and Power Automate](/sharepoint/dev/business-apps/power-automate/guidance/migrate-from-classic-workflows-to-power-automate-flows).

### Control the logical flow of projects using Power Automate

Power Automate provides logical flows for projects in  Project for the web. You create Power Automate flows on the Power Apps portal, using the following design and deploy process.

1. [Plan](/power-automate/guidance/planning/planning-phase): Identify the who, what, when, and why.
1. [Design](/power-automate/guidance/planning/process-design): Design your new automated process "on paper," and consider various methods of automation.
1. [Make](/power-automate/guidance/planning/making-phase): Create the Power Automate flows.
1. [Test](/power-automate/guidance/planning/testing-strategy): Try out the automation you created.
1. [Deploy and refine](/power-automate/guidance/planning/deploy-to-production): Start using the automation in production, identify processes that can be refined, and decide what to change or add.

## Security

Project Web App uses SharePoint-based security by default, but you can configure Project Online security separately. The two security models are different, but are based on groups and permissions.

Project for the web uses [Teams Groups](/microsoftteams/office-365-groups) and [policies](/microsoftteams/policy-assignment-overview) to determine which users in your organization can create or work on projects.

The Project Power App lets you use Dataverse security roles to control access to specific tables, and Dataverse column security to restrict access for specific fields.

### Set up Project for the web security

1. If you haven't already, [set up Teams Groups](/microsoftteams/office-365-groups#how-microsoft-365-groups-work-with-teams) for people in your organization.
1. [Assign policies to groups](/microsoftteams/assign-policies-users-and-groups#assign-a-policy-to-a-group) to establish things all group members can do.
1. If needed, [assign policies to individual users](/microsoftteams/assign-policies-users-and-groups#assign-a-policy-to-individual-users) to grant them specific privileges.
1. If needed, set up [external access](/microsoftteams/manage-external-access) to let people outside your organization work on projects.

### Add Dataverse security in the Project Power App

1. Review the [predefined security roles](/power-platform/admin/database-security#environments-with-a-dataverse-database). In most cases, you can meet all of your users' access needs by assigning them to one or more of these roles.
1. If needed, [create custom security roles](/power-platform/admin/database-security#create-or-configure-a-custom-security-role).
1. [Assign security roles to users](/power-platform/admin/database-security#assign-security-roles-to-users-in-an-environment-that-has-a-dataverse-database).
1. If needed, [restrict access to specific fields](/power-platform/admin/set-up-security-permissions-field).

## Visualizations

Stakeholders need a way to check the status and results of projects. Project Web App comes with some built-in reports, and you can create your own visualizations using SharePoint, Excel, and Power BI (depending on your plan and subscriptions). Project for the web uses the Power Platform visualization components: charts and dashboards.

### Customize charts and dashboards in Project for the web

Project for the web includes built-in visualizations that you can customize. You can also create new visualizations.

To create and customize charts and dashboards for Project for the web, you add or modify them in the Project Power App. To customize reports, you work in [Power BI](/powerapps/maker/model-driven-apps/use-power-bi). As with other components, visualizations you create or customize in the Project Power App affect all projects using Project for the web in your environment.

To use Power BI reports on Project for the web data, you need to be a licensed user of Power BI Desktop or Power BI Pro. See [Power BI Pricing](https://powerbi.microsoft.com/en-us/pricing/) for more information.

> [!NOTE]
> 

#### Use charts to summarize data

Charts show summary column data for a table. For example, the *Project* table comes with the *Project by Estimated Vs Actual hours* chart that summarizes data from the *Effort (hours)* and *Effort Completed (hours)*.

In Project for the web, when you select **Projects** in the navigation pane, you can select **Show Charts** on the command bar to display charts that summarize projects.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-07.png" alt-text="Use the controls above the chart to change the view (which projects to list), and to select a chart.  To choose which project the chart summarizes, select the table name in the list.":::

   1. Use the controls above the chart to change the view (which projects to list), and to select a chart.
   1. To expand the chart, select the vertical dots next to the chart title.
   1. To choose which project the chart summarizes, select the table name in the list.

To create or customize a chart, open the Power App portal, select the table you want to summarize, then select the Charts area, and then do one of the following:

- To create a new chart based on the table, on the command bar select **Add chart**.
- To customize an existing chart, select the name of the chart.

A new browser tab opens where you can work on charts that summarize the table's data.

:::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-09.png" alt-text="The design surface for a new chart based on the Project table.":::

The types of chart you can create change when you add series (aggregated column data) and categories (horizontal axis labels). For example, here's the same *Project by Estimated Vs Actual hours* chart opened in the Project Power App.

:::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-08.png" alt-text="The existing series only support ":::

For help customizing charts in the Project Power App, see [Create a new chart](/powerapps/maker/model-driven-apps/create-edit-system-chart#create-a-new-chart).

#### Create a dashboard in the Project Power App

Dashboards contain other components to help you provide a role-specific interface. For example, you might create one dashboard for project users and another one for organization managers. Project for the web doesn't have any pre-built dashboards, but you can create them for your environment in the Project Power App. However, the [Project for the web Power App Accelerator](https://aka.ms/projaccelerator) includes a pre-built dashboard that you can use as-is or customize as needed.

> [!IMPORTANT]
> Create or customize the components you want to include on your dashboard first. Otherwise, they won't be available when you design your dashboard.

1. Open the Power Apps Portal.
1. In the navigation pane, select **Apps**.
1. Select the Project Power App, and then on the command bar select **Edit**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-12.png" alt-text="Select the Project app to edit it.":::

1. In the App Designer, on the **Components** tab select **Dashboards**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-13.png" alt-text="Add a dashboard to the Project app using the App Designer.":::

1. Select **Create New**, and then select **Classic Dashboards**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-14.png" alt-text="Choose a classic dashboard.":::

   > [!NOTE]
   > Classic dashboards display visualizations and other components to provide a bigger picture of projects.Interactive dashboards let users edit data directly in the dashboard, and require significant expertise to create. For more information, see [Create and configure model-driven app interactive experience dashboards](/powerapps/maker/model-driven-apps/configure-interactive-experience-dashboards).

1. Choose the layout you want and then select **Create**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-15.png" alt-text="Choosing a layout for a Classic Dashboard.":::

1. The new dashboard opens in a new window. Enter a value for **Name**, then add components by selecting the icons in each tile.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-16.png" alt-text="Add components to a Classic dashboards":::

1. Make any other changes you want. Then on the ribbon select **Save** and then **Close**.

#### Create and customize reports

> [!TIP]
> The [Project for the web Power App Accelerator](https://aka.ms/projaccelerator) includes reports that use the Power BI Service.

You can use Power BI Desktop to [create reports using your Project for the web data](https://support.microsoft.com/en-us/office/use-power-bi-desktop-to-connect-with-your-project-data-df4ccca1-68e9-418c-9d0f-022ac05249a). 

## Next steps

- [Create and apply work calendars in Project for the web](create-and-apply-a-work-calendar.md)
- [Add non-user resources in Project for the web](create-nonuser-resources-in-project-for-the-web.md)
- [Book a resource to a project](overview-universal-resource-scheduling.md#book-a-resource-to-a-project)
- To learn more about Power App development, see [Understand model-driven app components](/powerapps/maker/model-driven-apps/model-driven-app-components).
