---
title: Customization Best Practices and Limitations for Project for the web
description: Customize Project for the web through managed solution layers using at least two environments. Use Teams Groups security roles, and avoid restricting access to the Project entities.  
author: v-stthomas
ms.author: v-stthomas
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 04/15/2022
ms.custom: template-how-to
audience: admin
---

# Customization Best Practices and Limitations for Project for the web

[!INCLUDE [p4w-required-roles.md](includes/p4w-required-roles.md)]

[!INCLUDE [p4w-solution-layers.md](includes/p4w-solution-layers.md)]

## Prerequisites

- Admin rights in a development environment with Project for the web
- An understanding of [managed solution layers](/power-platform/alm/solution-layers-alm#layering-within-a-managed-solution)
- (Optional, but recommended) A [Developer plan](/power-apps/maker/developer-plan) so you can export your solution to easily deploy in other environments

## Options for creating customizations

You have two options for creating customizations:

- The [Power Apps portal](https://make.powerapps.com/) has a nice, friendly UI. It's convenient and suitable most of the time, but a few options aren't available.
- The [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer) provides advanced options that aren't available on the Power Apps portal.

## Use Teams Group and roles to implement security and access

Although you can as an admin create users and assign security roles in the Microsoft Power Platform, when you want to customize the Project solution, you should avoid this practice. Project for the web security leverages Teams Groups, so you should instead [manage group teams](/power-platform/admin/manage-group-teams) and assign security roles to teams whenever you can, instead of granting individual users security roles.

## Don't restrict access to existing Project entities using Dataverse security

You might be tempted to create restrictions on tables that are part of the Project solution using Dataverse security. This is a bad idea, as the components of the Project solution require access to the Project entities and use Teams Groups security roles to control access.

However, you might want to restrict access to new tables and columns that are part of your custom solution. Although it's best to use Teams Groups Security to control access to tables, column security for new columns is most easily done by setting a column property. In new columns, [Dataverse column security](/power-platform/admin/field-level-security) may be appropriate.

## Next Steps

- [Upgrade or update a solution](/power-apps/maker/data-platform/update-solutions)
- [Licenses for customizations of Project for the web](licensing-custom-solutions-layered-on-project-for-the-web.md)
