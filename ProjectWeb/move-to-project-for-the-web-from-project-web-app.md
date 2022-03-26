---
title: Start using Project for the web while supporting Project Web App
description: Understand how Project for the web differs from Project Web App. Learn to administer and customize the Project Power App to control projects in Project for the web. Start supporting Project for the web for new projects.
author: v-stthomas
ms.author: v-stthomas
manager: alexla
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: admin
---

# Start using Project for the web while supporting Project Web App

Project for the web is the interface for projects that are based on the Project Power App. This article explains how projects in Project for the web differ from projects in the Project Web App, and provides links to help you decide which projects will work better in Project for the web.

## Prerequisites

- Ensure you have [appropriate licenses](/power-platform/admin/powerapps-flow-licensing-faq).
- Understand [the basics of the Power Apps portal](/learn/paths/get-started-power-apps-portals).
- See the [FAQ about supporting projects in Project Web App and Project for the web](https://support.microsoft.com/office/project-for-the-web-and-project-online-6569170c-5c8e-474e-a7f0-642872f62f8a).

## Differences between Project Web App and Project for the web

Project for the web offers some substantial benefits over Project Web App, but it doesn't yet offer full feature parity. For a detailed list of project for the web features, see [What is Project for the web?](https://support.microsoft.com/office/what-is-project-for-the-web-c19b2421-3c9d-4037-97c6-f66b6e1d2eb5).

The following table summarizes the differences between Project Web App and Project for the web. The exact functionality of each depends on your plan and subscription. For a full comparison of all available Project plans and subscriptions, see the [Microsoft Project service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

| Component (links to sections, below) | In Project Web App | In Project for the web |
| :-- | :-- | :-- |
|[Data](#data-components) | SharePoint lists | [Dataverse](/powerapps/maker/model-driven-apps/define-data-model-driven-app) |
|[UI](#ui-components) | Project Detail Pages | Views and Forms |
|[Logic](#logic-components) | SharePoint workflows | Power Automate |
|[Security](#security) | [SharePoint permissions or Project Online permissions](/projectonline/change-permission-management-in-project-online) | [Security roles](project-for-the-web-security-roles.md) |
|[Visualizations](#visualizations) | [Various options based on your plan/subscription](/projectonline/what-reporting-tools-can-i-use-with-project-data) | [Charts, Dashboards, and Power BI](/powerapps/maker/model-driven-apps/model-driven-app-components#visualizations) |

## Data components

Project data for Project Web App is stored in SharePoint lists. Project for the web data is stored in Dataverse tables. While suitable for many scenarios, SharePoint lists do have some limitations compared to Dataverse tables. For a comparison, see [Handling data for Project](/project-for-the-web/handling-data-for-project-for-the-web-and-roadmap).

### Dataverse in the Project Power App

The Project Power App stores data in your environment's Dataverse, in three classes of tables.

1. Core scenario tables hold data used for projects in Project for the web. You can modify these tables if needed to support special functionality in your environment, with some caveats. For example, you can [add a custom column](add-custom-column-project-power-app.md) to make it available to all projects in your environment.

   | Table name | What it stores | Caveats |
   | :-- | :-- | :-- |
   | *Project* | Summary project information. | None. |
   | *Task* | Tasks that can be assigned. | Modification not recommended. Changes won't display correctly in Project for the web. |
   | *Bookable Resource* |  |  |
   | *Project Team* |  |  |
   | *Bucket* |  |  |
   | *Task Assignment* |  |  |
   | *Checklist* |  |  |
   | *Label* |  |  |
   | *Task Attachment* |  |  |
   | *Task Conversation* |  |  |
   | *Work template* |  |  |
   | *Task Dependency* |  |  |
   | *Resource Requirement* |  |  |
   | *Resource Requirement Detail* |  |  |
   | *Role Competency requirement* |  |  |
   | *Requirement Resource Category* |  |  |
   | *Project Import Staging* |  |  |
   | *Project Parameter* |  |  |
   | *User* |  |  |

1. Project Accelerator tables support the Project for the web Power App Accelerator. These tables only exist if you've deployed the Project Accelerator in your environment. You can customize them to change the implementation of the scenarios the Project Accelerator provides. Be sure you know what you're doing and have a plan before you make changes. The Risks and Issues tables are part of the same scenario and shouldn't be changed separately. Other scenario components rely on these tables, such as Power Automate flows.

   | Table name | Scenario it supports |
   | :-- | :-- |
   | *Project Requests* | Create a list of ideas for Projects that include a business case and expected impact. The included Power Automate flow will create projects whenever the state of requests is set to Approved. |
   | *Programs*  | Create a hierarchy of programs and projects to see how work fits into the bigger picture. |
   | *Risks*  | Manage the surprises that accompany every project. Create and assign risks to minimize impacts to a project's schedule. Works in conjunction with the Issues table. |
   | *Issues*  | Manage the surprises that accompany every project. Create and assign issues to minimize impacts to a project's schedule. Works in conjunction with the Risks table. |
   | *Changes*  | Use change tracking processes to help understand the history of a project. |
   | *Status Report* | Centralize recording of project status to keep stakeholders up-to-date. |

1. System tables provide the basic framework of the Project Power App. Some can be safely customized, some can't.

   | Table name | What it stores | Safe to change |
   | :-- | :-- | :-- |
   | *Document Header* |  | Yes |
   | *Document Section*  |  | Yes |
   | *Long Running Job Status*  |  | No |
   | *OperationSet* |  | No |
   | *OperationSet Detail*  |  | No |

## UI components

Both Project Web App and Project for the web provide a UI for data entry using instances of project templates that you customize. Both UIs use a web browser. But the specifics are different. For a comparison of the design experiences, see [Edit project details in Project Online](https://support.microsoft.com/office/edit-project-details-in-project-online-9ea8d54f-d46e-4de7-a503-93095d83095d) and [Customizing the Project Power App](/project-for-the-web/faq#customization).

To customize the Project for the web UI, you modify or create views and forms in the Project Power App. Views define how to display a list of rows for a specific table in your application. Each view definition contains which columns to display, the width of each column, and default row sorting behavior and filters. Forms present a set of data-entry columns for a given table, and provide the interface for people working with projects.

### Views in the Project Power App

To customize Project Power App views, use the [Power Apps Portal](https://make.powerapps.com). You use a view to customize the display of data from a table (such as the Project table, the main table used in Project for the web). To work with views, you first select a table, then you select the **Views** tab.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-02.png" alt-text="The Views tab for the Project table in the Project Power app.":::

For more information about Power Apps views, see [Understand model-driven app views](/powerapps/maker/model-driven-apps/create-edit-views).

### Forms in the Project Power App

When users open a project in Project for the web, the browser displays the default Main form&mdash;the *Information* form in Project for the web, unless you select a different default for your environment. All projects created in Project for the web in the same environment display the same Main form.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-03.png" alt-text="The Information form of a project opened in Project for the web.":::

When you open the Project Power App in an environment, you can set a different default Main form, and you can also edit forms. Both changes affect all projects in that environment, providing centralized control over the functionality of projects.
  
   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-04-closeup.png" alt-text="The Information form of the Project Power App." lightbox="media/move-to-project-for-the-web-from-project-web-app-04.png":::

For more information about Power Apps forms, see [Create and design model-driven app forms](/powerapps/maker/model-driven-apps/create-design-forms).

## Logic components

Project Web App uses SharePoint workflows to control the logical flow of projects. In Project for the web, you use Power Automate. For a comparison, see [Classic SharePoint workflows and Power Automate](/sharepoint/dev/business-apps/power-automate/guidance/migrate-from-classic-workflows-to-power-automate-flows).

### Control logical flow of projects using Power Automate

Project for the web projects use Power Automate flows. You create these flows on the Power Apps portal. It's a good idea to follow a design and deploy process with the following broad steps.

1. [Plan](/power-automate/guidance/planning/planning-phase): Identify the who, what, when, and why.
1. [Design](/power-automate/guidance/planning/process-design): Design your new automated process "on paper," and consider various methods of automation.
1. [Make](/power-automate/guidance/planning/making-phase): Create the Power Automate flows.
1. [Test](/power-automate/guidance/planning/testing-strategy): Try out the automation you created.
1. [Deploy and refine](/power-automate/guidance/planning/deploy-to-production): Start using the automation in production, identify processes that can be refined, and decide what to change or add.

## Security

Project Web App uses SharePoint-based security by default, but you can configure Project Online security separately. The two security models are different, but are based on groups and permissions. Project for the web uses Dataverse security based on roles, and can use Dataverse column security to provide more granular control by letting you control who can edit specific fields.

### Set up security roles in Project for the web

To control user access to projects in Project for the web, you use Power Platform security roles. This lets you allow some users to work with existing projects, some to create new projects, and some to make design changes to the Project Power App.

1. Review the [predefined security roles](/power-platform/admin/database-security#environments-with-a-dataverse-database). In most cases, you can meet all of your users' access needs by assigning them to one or more of these roles.
1. If needed, [create custom security roles](/power-platform/admin/database-security#create-or-configure-a-custom-security-role).
1. [Assign security roles to users](/power-platform/admin/database-security#assign-security-roles-to-users-in-an-environment-that-has-a-dataverse-database).
1. If needed, [restrict access to specific fields](/power-platform/admin/set-up-security-permissions-field).

## Visualizations

## Next steps

- If you’re looking for portfolio management, consider deploying the free, [Project for the Web Accelerator solution](https://aka.ms/projaccelerator) in any environment that has Project for the web.
- To learn more about Power App development, see [Understand model-driven app components](/powerapps/maker/model-driven-apps/model-driven-app-components).
