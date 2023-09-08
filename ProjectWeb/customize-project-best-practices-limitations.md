---
title: Customization Best Practices and Limitations for Project for the web
description: Customize Project for the web through managed solution layers using at least two environments. Use Teams Groups security roles, and avoid restricting access to the Project entities.  
author: alexla
ms.author: alexla
manager: anavs
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

## General best practices

- Always create a managed solution that contains your customizations, so you can layer them on top of the Project solution.
- Use the [Power Apps portal](https://make.powerapps.com/) to make easy changes. If you find you need to do something and can't find a way in the Power Apps portal, use the [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer), which provides more advanced options.

## General limitations

- Except for creating a new project, creating records and editing fields in the project tables requires the [Project scheduling API](/dynamics365/project-operations/project-management/schedule-api-preview).
- If you decide to duplicate and modify Project security roles, you'll need to update those roles whenever new features are released for the Project solution. For example, the Task History feature added new tables to the Project solution. Your custom security roles must have the same permissions to those tables as the Project security roles, otherwise users with your custom security roles won't be able to use the Task History feature.

## Use Teams Group and roles to implement security and access

Although you can as an admin create users and assign security roles in the Microsoft Power Platform, when you want to customize the Project solution, you should avoid this practice. Project for the web security leverages Teams Groups, so you should instead [manage group teams](/power-platform/admin/manage-group-teams) and assign security roles to teams whenever you can, instead of granting individual users security roles.

### Examples of what is and isn't supported

✅ *Supported*: Customizing security roles so that users can't edit specific custom columns added to tables in the Project solution.

❌ *Not supported*: Customizing security roles so that users can edit projects, but not create new projects.

## Don't restrict access to existing Project entities using Dataverse security

You might be tempted to create restrictions on tables that are part of the Project solution using Dataverse security. This is a bad idea, as the components of the Project solution require access to the Project entities and use Teams Groups security roles to control access.

However, you might want to restrict access to new tables and columns that are part of your custom solution. Although it's best to use Teams Groups Security to control access to tables, column security for new columns is most easily done by setting a column property. In new columns, [Dataverse column security](/power-platform/admin/field-level-security) may be appropriate.

## Next Steps

- [Upgrade or update a solution](/power-apps/maker/data-platform/update-solutions)
