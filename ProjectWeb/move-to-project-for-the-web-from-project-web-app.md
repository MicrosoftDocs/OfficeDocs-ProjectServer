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

# Begin using Project for the web while supporting Project Web App

Project for the web is the interface for projects that are based on the Project Power App. This article explains how projects in Project for the web differ from projects in the Project Web App, and provides links to help you decide which projects will work better in Project for the web.

## Prerequisites

- Ensure you have [appropriate licenses](/power-platform/admin/powerapps-flow-licensing-faq).
- Understand [the basics of the Power Apps portal](/learn/paths/get-started-power-apps-portals).

## Differences between Project Web App and Project for the web

Project for the web offers some substantial benefits over Project Web App, but it doesn't yet offer full feature parity. For a detailed list of project for the web features, see [What is Project for the web?](https://support.microsoft.com/office/what-is-project-for-the-web-c19b2421-3c9d-4037-97c6-f66b6e1d2eb5).

The following table summarizes the differences between Project Web App and Project for the web. The exact functionality of each depends on your plan and subscription. For a full comparison of all available Project plans and subscriptions, see the [Microsoft Project service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).

| Functionality | In Project Web App | In Project for the web | Links to more information |
| :-- | :-- | :-- | :-- |
| [Storing project data](#storing-project-data) | SharePoint | Dataverse |  |
| [Project data presentation](#project-data-presentation) | Project Detail Pages | Views and Forms |  |
| [Logical flow of projects](#logical-flow-of-projects) | SharePoint workflows | Power Automate |  |
| [Securing access to project](#securing-access-to-projects) |  | [Security roles](project-for-the-web-security-roles.md) |  |

## Storing project data

Project data for Project Web App is stored in SharePoint lists. Project for the web data is stored in Dataverse tables. While suitable for many scenarios, SharePoint lists do have some limitations compared to Dataverse tables.

## Project data presentation

Both Project Web App and Project for the web projects present data using instances of project templates that you customize. People working on projects use a browser-based interface. But the interfaces and the design experience are different.

### Project Detail Pages in Project Web App

For Project Web App projects, you control and customize data presentation with Project Detail Pages by using Project Online or the Project Online Desktop client. Changes you make to Project Detail Pages affect all the projects in the same tenant.

### Views and forms in Project for the web

For projects in Project for the web, you use the Power Apps Portal to edit the Project Power App
:::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-02.png" alt-text="The Views tab in the Project Power app.":::

### The Information form: the default Main form of the Project Power App

When you open a project in Project for the web, the browser displays the Main form&mdash;typically the *Information* form, which is the default in Project for the web. All projects created in Project for the web in the same environment display the same Main form.

   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-03.png" alt-text="The Information form of a project opened in Project for the web.":::

When you open the Project Power App in an environment, you can set a different default Main form, and you can also edit forms. Both changes affect all projects in that environment, providing centralized control over the functionality of projects.
  
   :::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-04.png" alt-text="The Information form of the Project Power App.":::

## Logical flow of projects

## Securing access to projects

### Set up security roles in Project for the web

To control user access to projects in Project for the web, you use Power Platform security roles. This lets you allow some users to work with existing projects, some to create new projects, and some to make design changes to the Project Power App.

1. Review the [predefined security roles](/power-platform/admin/database-security#environments-with-a-dataverse-database). In most cases, you can meet all of your users' access needs by assigning them to one or more of these roles.
1. If needed, you can [create custom security roles](/power-platform/admin/database-security#create-or-configure-a-custom-security-role).
1. [Assign security roles to users](/power-platform/admin/database-security#assign-security-roles-to-users-in-an-environment-that-has-a-dataverse-database).
(/power-platform/admin/set-up-security-permissions-field).

## Next steps

- If you’re looking for portfolio management, consider deploying the free, [Project for the Web Accelerator solution](https://aka.ms/projaccelerator) in any environment with Project for the web in it.
