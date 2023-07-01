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

Project Online and Project Server use key SharePoint features such as web parts, collaborative sites, and SharePoint security groups. If you administer either product, you've spent time customizing them to control access and ensure that projects meet your organization's standards.

Project for the web uses the Microsoft Power Platform: [PowerApps](/powerapps/powerapps-overview), [Power Automate](/power-automate/getting-started), [Power BI](/power-bi/fundamentals/power-bi-overview), and [Dataverse](/powerapps/maker/common-data-service/data-platform-intro).

The following diagram shows how the two apps fit into the overall Project architecture.

:::image type="content" source="media/projarchoverview.png" alt-text="Project architecture":::

This article helps you customize the Project Power App to meet the standards that you've implemented in Project Online or Project Server. Like the Project Web App, users access Project for the web from [Project Home](https://project.microsoft.com/). They can begin working on projects in Project for the web, and you can easily introduce customizations via Power Platform [solutions](/power-platform/alm/solution-concepts-alm).

## Table that compares components

| Components | Project Web App | Project for the web |
| :-- | :-- | :-- |
|[Permissions and security](#permissions-and-security) | [SharePoint permissions or Project Online permissions](/projectonline/change-permission-management-in-project-online) | [Security roles](project-for-the-web-security-roles.md) |
|[Data](#data-in-project-for-the-web) and [Logic](#logic) | SharePoint lists and workflows | [Dataverse](/powerapps/maker/model-driven-apps/define-data-model-driven-app) and Power Automate |
|[UI](#ui-components) and [Visualizations](#visualizations) | Project Detail Pages and [Options based on your plan/subscription](/projectonline/what-reporting-tools-can-i-use-with-project-data) | [Views, Forms](/powerapps/maker/model-driven-apps/model-driven-app-components#ui-components), [Charts, and Dashboards](/powerapps/maker/model-driven-apps/model-driven-app-components#visualizations) |

> [!TIP]
> Want a head start? [Deploy the Project for the web Accelerator and Power BI template](https://github.com/OfficeDev/Project-Accelerator#heres-the-latest-version-of-the-accelerator), a free solution that adds numerous project management scenarios and visualizations to the Project Power App.

> [!IMPORTANT]
> To customize the Project Power App, you need an account with [the right security role](/powerapps/maker/model-driven-apps/privileges-required-customization#system-administrator-and-system-customizer-security-roles).

## Prerequisites

- Ensure you have [appropriate licenses](/power-platform/admin/powerapps-flow-licensing-faq).
- Understand [the basics of the Power Apps portal](/training/paths/get-started-power-apps-portals).

## Permissions and security

Project for the web uses [Teams Groups](/microsoftteams/office-365-groups) and [policies](/microsoftteams/policy-assignment-overview) to determine who has permissions required for various activities.

### Set up Project for the web security

1. If you haven't already, [set up Teams Groups](/microsoftteams/office-365-groups#how-microsoft-365-groups-work-with-teams) for people in your organization.
1. [Assign policies to groups](/microsoftteams/assign-policies-users-and-groups#assign-a-policy-to-a-group) to establish things all group members can do.
1. If needed, set up [external access](/microsoftteams/manage-external-access) to let people outside your organization work on projects.

## Data in Project for the web

The Project Power App stores data in Dataverse tables for three purposes.

- *Core scenario* tables hold data used for projects in Project for the web. You can modify some of these tables if needed to support special functionality in your environment. For example, you can [add a custom column](add-custom-column-project-power-app.md) to the *Project* table to make it available to all projects in your environment.

   To review these tables, search on the Power App portal using the search term *Project*. Then, select each table to review the existing columns and app components for the selected table.

- *Project Accelerator* tables support the Project for the web Power App Accelerator. These tables are customized when you deploy the Accelerator in your environment. You can customize them yourself if you don't deploy the Accelerator.

  It's possible to customize them after you deploy the Accelerator, but you should do so in a [new solution](/power-platform/alm/use-solutions-for-your-customizations), and then [deploy the new solution on top](/power-platform/alm/solution-layers-alm#layering-within-a-managed-solution) of the Accelerator&mdash;it's a managed solution, so if you customize the environment directly after you deploy it, you'll be unable to deploy updates of the Accelerator solution.

  - *Project Requests*
  - *Programs*
  - *Risks*
  - *Issues*
  - *Changes*
  - *Status Report*

- System tables provide the basic framework of the Project Power App. Don't customize them.

  - *Document Header*
  - *Document Section*
  - *Long Running Job Status*
  - *OperationSet*
  - *OperationSet Detail*

## Logic

Power Automate provides logical flows for data in Project for the web. To automate the logical flow of Project data, use Power Automate with the Dataverse connector. For example, suppose you want a record created in the *Project* table when a value in a row of another table changes.

### Add a record to the Project table using Power Automate

1. In the navigation pane, select **Flows**.
1. On the command bar, select **+ New flow**.
1. On the menu that appears, select **Automated cloud flow**.
1. In the dialog that opens, optionally add a name.
1. For **Choose your flow's trigger**, enter *Dataverse* to filter the list, then select **When a row is added, modified, or deleted. Microsoft Dataverse**, and then select **Create**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-choose-flow-trigger.png" alt-text="Choose a Dataverse trigger for Project data flows.":::

1. The trigger you chose appears in your new flow. Next steps depend on exactly what you want to automate - which data is involved, etc.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-edit-flow-trigger.png" alt-text="Dataverse trigger in a new Project Power App flow.":::

1. After you add a trigger, select **New** below the trigger to set up the automated data change.

For more information about using flows with Project data, see [Overview of how to integrate Power Automate flows with Dataverse](/power-automate/dataverse/overview).

However, the Dataverse connector can only edit data or create rows in the *Project* table itself. To change any other data, you must use the [Project Scheduling API](/dynamics365/project-operations/project-management/schedule-api-preview).

## UI components

To customize the Project for the web UI, you modify or create views and forms in the Project Power App.

- Views define how to display a list of rows for a specific table in your application. Each view definition contains which columns to display, the width of each column, and default row sorting behavior and filters. For example, **My Active Projects** only displays projects for the current user where the project's *State* is *Active*.
- Forms present a set of data-entry columns for a given table, and provide the interface for people working with projects. For example, the *Information* form is the default main form&mdash;it displays details about a project. A form can have tabs to help organize the data into subjects, such as Tasks or Resources.

### Create a view in the Project Power App

Create a view to customize the display of data from a single table.

1. Open the [Power App Portal](https://make.powerapps.com), then on the navigation pane select **Data** > **Tables**.
1. In the view selector on the command bar, select **All**, then search for *Project*.
1. In the search results, sort **Customizable** by **True then False** to list customizable tables first.
1. Find the table you want, select its name to open it, and then select the **Views** tab.
1. On the command bar, select **+Add view**.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-10.png" alt-text="The Add view command for a single Project Power App table.":::

1. Follow the steps in the **Create a view** dialog.

For more information about Power Apps views, see [Understand model-driven app views](/powerapps/maker/model-driven-apps/create-edit-views).

### Forms in the Project Power App

When users open a project in Project for the web, the browser displays the default Main form&mdash;the *Information* form in Project for the web, unless you select a different default for your environment. All projects created in Project for the web in the same environment display the same Main form.

When you open the Project Power App in an environment, you can set a different default Main form, and you can also edit forms. Both changes affect all projects in that environment, providing centralized control over the functionality of projects.

For more information about Power Apps forms, see [Create and design model-driven app forms](/powerapps/maker/model-driven-apps/create-design-forms).

## Visualizations

Stakeholders need a way to check the status and results of projects. Project for the web uses the Power Platform visualization components: charts and dashboards.

Project for the web includes built-in visualizations that you can customize in the Project Power App. You can also create new visualizations. As with other components, visualizations you create or customize in the Project Power App affect all projects in Project for the web in your environment.

### Use charts to summarize data

Charts show summary column data for a table. For example, the *Project* table comes with the *Project by Estimated Vs Actual hours* chart that summarizes data from the *Effort (hours)* and *Effort Completed (hours)*.

In Project for the web, when you select **Projects** in the navigation pane, you can select **Show Charts** on the command bar to display charts that summarize projects.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-07.png" alt-text="Use the controls above the chart to change the view (which projects to list), and to select a chart.  To choose which project the chart summarizes, select the table name in the list.":::

   1. Use the controls above the chart to change the view (which projects to list), and to select a chart.
   1. To expand the chart, select the vertical dots next to the chart title.
   1. To choose which project the chart summarizes, select the table name in the list.

To create or customize a chart, open the Power App portal, select the table you want to summarize, then select the Charts area, and then do one of the following:

- To create a new chart based on the table, on the command bar select **Add chart**.
- To customize an existing chart, select the name of the chart.

A new browser tab opens where you can work on charts that summarize the table's data. The types of chart you can create change when you add series (aggregated column data) and categories (horizontal axis labels).

For help customizing charts in the Project Power App, see [Create a new chart](/powerapps/maker/model-driven-apps/create-edit-system-chart#create-a-new-chart).

### Create a dashboard in the Project Power App

Dashboards contain other components to provide a role-specific big picture. For example, you might create one dashboard for project users that summarizes progress on their projects and another dashboard for organization managers that shows per-project and per-user information.

> [!TIP]
> The Project for the web Power App Accelerator includes a dashboard that you can use and customize as needed.

> [!IMPORTANT]
> Create or customize the components you want to include on your dashboard first. Otherwise, they won't be available when you design your dashboard.

1. Open the [Power Apps Portal](https://make.powerapps.com).
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

1. Make any other changes you want. Then, on the ribbon, select **Save** and then **Close**.

## Next steps

- To learn more about Power App development, see [Understand model-driven app components](/powerapps/maker/model-driven-apps/model-driven-app-components).
- For a detailed list of Project for the web features, see [What is Project for the web?](https://support.microsoft.com/office/what-is-project-for-the-web-c19b2421-3c9d-4037-97c6-f66b6e1d2eb5).
- For a full comparison of all Project plans and subscriptions, see the [Microsoft Project service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).
- Consider using the [AI](/ai-builder/) to help you refine and automate business processes, glean insights from project data, and predict outcomes based on historical examples.
