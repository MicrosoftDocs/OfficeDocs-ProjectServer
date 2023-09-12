---
title: Licenses for customizations of Project for the web
description: Custom solutions built on Project for the web require licenses when used with the Project solution. Your custom solution itself should also have some kind of license, but you might want to make it as freely-available as possible to encourage others to build on your work.  
author: v-stthomas
ms.author: serdars
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 04/15/2022
ms.custom: template-how-to
audience: admin
---

# Licenses for customizations of Project for the web

When you create custom solutions starting with Project for the web, some additional licenses may be required.

[!INCLUDE [p4w-licenses.md](includes/p4w-licenses.md)]

- [Simple customizations](#example-1-simple-customizations) typically require no additional licenses.
- [Extensive customizations](#example-2-extensive-customizations-and-power-bi) might require licenses.

Read the [Project Service Description](/office365/servicedescriptions/project-online-service-description/project-online-service-description) for comprehensive information about licensing Project.

## Examples

The following two examples illustrate licensing considerations for possible customizations.

### Example 1: Simple customizations

You add up to five tables in Dataverse and expose the new tables in the Project Power App:

- You create relationships between the new tables and existing Project tables.
- You create views and forms that use fields from the new tables.
- You add charts that use data from the new tables.

### Example 2: Extensive customizations and Power BI

You add at least six tables in Dataverse and expose the new tables in the Project Power App. This may require a P3 subscription for project managers.

- You create relationships, add view, forms, and charts exposing the new tables.
- You add Power Automate flows or the Project Scheduling API to automate data changes.

You built a Power BI report, publish it on powerbi.com, and integrate it into your custom solution.

- People who view the Power BI report (standalone or as a dashboard-embedded report) don't need additional licenses.
- People who modify the Power BI report need a Power BI Premium license.

## Next steps

- Consider subscribing to a [Developer plan](/power-apps/maker/developer-plan) so you can export your solutions to deploy them easily in other environments.
