---
title: "Project for the Web Security Roles"
ms.author: namerali
author: namerali
manager: hocull
ms.date: 01/07/2021
audience: admin
ms.topic: article
ms.service: project-web
localization_priority: Normal
description: "Learn about the security roles in Project for the web."
---
# Project for the Web Security Roles

Project for the web includes several security roles that enable users to work with Project. Some of these security roles can also be customized by Administrators to control access of data. [Learn more about security roles and priveleges](https://docs.microsoft.com/en-us/power-platform/admin/security-roles-privileges).

## Behavior with AAD Groups
When a project is shared with an AAD Office Group, the Microsoft Project Application user will
1. Create a Team that is backed by the AAD Group.  The name of the team will be the same as the AAD Office group when possible.
2. The team is given the following security roles
   * Project Team Member 
   * Project Common 

> [!Note] Today, in the Default org, the team is given Project User role but this is being changed to the above

3. Ownership of the project and related tables is changed from the current owning user to the newly created team.
Project for the web only supports adding additional security roles to the Microsoft Project Application user. Other changes/modification are not supported and can cause the service not to function. The Project Common role can modify to support least privilege and customization

## Project Common
- Customizable
- Provides non-project related permissions to give a user access to the environment including the ability to log in. 
- It is a copy of the Common Data Service User role but can diverge in future releases.
- The AAD Office Group team that is created when a project is shared is given this role so that members have enough permissions to log into and interact with the environment

## Project User
- Cannot be customized
- Provides user scoped permissions to create, read, update, and delete project and related entities. 

## Portfolio User
- Deprecated as of 0.8.7.59
- Internal use by Project for the web.  Provides user scoped permissions to create, read, update, and delete portfolio and related entities.

## Project System
- Internal use by Project for the web
- Provides all organization scoped permissions to create, read, update, and delete project and related entities. 

## Project Team Member
- Provides user scoped permissions to read, update and delete project and related entities.
- The AAD Office Group team that is created when a project is shared is given this role so that member can interact with the project

## Roadmap System 
Internal use by Project for the web. Provides all organization scoped permissions to create, read, update, and delete portfolio and related entities. 

## Roadmap User
Provides user scoped permissions to create, read, update, and delete portfolio and related entities. 