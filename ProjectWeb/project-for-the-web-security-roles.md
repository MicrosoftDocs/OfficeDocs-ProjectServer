---
title: "Project for the Web Security Roles"
ms.author: namerali
author: NadinMerali
manager: hocull
ms.date: 01/07/2021
audience: admin
ms.topic: article
ms.service: project-web
ms.localizationpriority: medium
description: "Learn about the security roles in Project for the web."
---
# Project for the Web Security Roles

Project for the web includes several security roles that enable users to work with Project. Some of these security roles can also be customized by Administrators to control access of data. For more information, see [Security roles and privileges](/power-platform/admin/security-roles-privileges).

Project Common and Project User roles need to be assigned to each user to create/manage projects within a non-default environment. These roles are needed in addition to roles required to sign in and access a Dataverse environment. For more information, see [Security roles and privileges](/power-platform/admin/assign-security-roles).

**Microsoft Project** (also maybe shown as **Microsoft Portfolios**) is an application user that is provisioned in the environments that is used by Project for the web to interact with Dataverse. The **Microsoft Project** application user must be assigned to the following roles for the service to function correctly:
   * Portfolio User (deprecated) 
   * Project Common
   * Project System
   * Roadmap System (Default Dataverse organization only)
   * Roadmap user (Default Dataverse organization only)


<a name='behavior-with-microsoft-azure-active-directory-azure-ad-groups'></a>

## Behavior with Microsoft Entra groups

When a project is shared with a Microsoft Entra Office Group, the Microsoft Project Application user will:

1. Create a Team that is backed by the Microsoft Entra group (if a team with the Microsoft Entra group doesn’t already exist). The name of the team will be the same as the Microsoft Entra Office Group when possible.

> [!Note] 
> Changes to the name of the O365 group will not update the name of the Dataverse team.

2. The team is given the following security roles:

* Project Team Member
* Project Common

> [!Note] 
> In the Default org, the team was given Project User role for older project.

3.	Ownership of the project and related tables is changed from the current owning user to the newly created team. Project for the web only supports adding more security roles to the Microsoft Project Application user. Other changes/modification aren’t supported and can cause the service not to function. The Project Common role can modify to support least privilege and customization.

## Project Common

* Can be customized and used to support extensibility, see [Behavior with Microsoft Entra groups](#behavior-with-microsoft-azure-active-directory-azure-ad-groups) to understand how this permission is assigned to Microsoft Entra groups.
* Default org: Users are automatically given this role.
* Non-default: Administrators need to assign to users to support the creation of projects when the environment has been customized.
* The Microsoft Entra Office Group team created at the project-sharing stage is given this role so that members have enough permissions to log into and interact with the environment.

## Portfolio User
* Deprecated as of 0.8.7.59
* Internal use by Project for the web. Provides user-scoped permissions to create, read, update, and delete portfolio and related entities.
* Users shouldn’t be assigned this role.

## Project System
* Internal use by Project for the web
* Provides all organization scoped permissions to create, read, update, and delete project and related entities.
* Users shouldn’t be assigned this role.

## Project Team Member
* Provides user-scoped permissions to read, update, and delete project and related entities.
* The Microsoft Entra Office Group team created at the project-sharing stage is given this role so that member can interact with the project.
* Users shouldn’t be assigned this role.

## Project User
* Provides user-scoped permissions to create, read, update, and delete project and related entities.
* Default org: Users are automatically given this role
* Non-default: Administrators need to assign to users to support the creation of projects.

## Roadmap System 
* Internal use by Project for the web. Provides all organization scoped permissions to create, read, update, and delete portfolio and related entities.
* Exists in the default organization only
* Users shouldn’t be assigned this role.

## Roadmap User
* Provides user-scoped permissions to create, read, update, and delete portfolio and related entities.
* Exists in the default organization only
* Users in the default organization are automatically given this role.
