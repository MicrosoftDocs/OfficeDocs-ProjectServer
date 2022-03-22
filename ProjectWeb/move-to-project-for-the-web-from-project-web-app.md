---
title: Move to Project for the web from Project Web App
description: Understand the differences between Project for the web and the Project Web App. Learn about security roles in Project for the web. Move projects from the Project Web App to Project for the web.
author: v-stthomas
ms.author: v-stthomas
manager: alexla
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: ITPro
---

# Move to Project for the web from Project Web App

Project for the web is the interface for people who work with projects created using the Project Power App. This article explains how projects in Project for the web differ from projects in the Project Web App, and how to move projects from the Project Web App to Project for the web.

The following table lists the main components in the two products, and a summary of the differences between them.

| Functionality | Project Web App component | Project for the web component | Summary of differences |
| :-- | :-- | :-- | :-- |
| Storing project data | SharePoint tables | Dataverse tables and columns |  |
| Presentation of project data | Project Detail Pages | Views and Forms |  |
| Logical flow of projects | SharePoint workflows | Power Automate |  |

## Prerequisites

- Make sure you have the [appropriate licenses](/power-platform/admin/powerapps-flow-licensing-faq).
- Check your [security role](project-for-the-web-security-roles.md).
- [Learn the basics of the Power Apps portal](/learn/paths/get-started-power-apps-portals).

## Move data from SharePoint to Dataverse

1. Open the [Power Apps portal](https://make.powerapps.com).
1. In the navigation pane, select **Data** > **Entities**.
1. Select **Get data**.
1. Select **OData**.
1. Enter your information into the dialog.
1. When your data appears, select **Next**.
1. Specify whether to use the existing entity or create a new one.
1. Complete the remaining fields and finish the import process.

## Views and forms in Project for the web

:::image type="content" source="media/move-to-project-for-the-web-from-project-web-app-02.png" alt-text="The Views tab in the Project Power app.":::

### The Information form

:::image type="content" source="{source}" alt-text="{alt-text}":::

1. <!-- Step 1 -->
1. <!-- Step 2 -->
1. <!-- Step n -->

## [Section n heading]
<!-- Introduction paragraph -->
1. <!-- Step 1 -->
1. <!-- Step 2 -->
1. <!-- Step n -->

<!-- 5. Next steps
Required. Provide at least one next step and no more than three. Include some 
context so the customer can determine why they would click the link.
-->

## Next steps
<!-- Add a context sentence for the following links -->
- [Write how-to guides](contribute-how-to-write-howto.md)
- [Links](links-how-to.md)

<!--
Remove all the comments in this template before you sign-off or merge to the 
main branch.
-->
