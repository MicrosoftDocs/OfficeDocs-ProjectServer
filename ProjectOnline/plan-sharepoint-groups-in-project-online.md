---
title: "Plan SharePoint groups in Project Online"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 2/25/2016
audience: admin
ms.topic: conceptual
ms.service: project-online
ms.collection: M365-subscription-management
localization_priority: Normal
search.appverid:
- PJO150
- PJO160
- MET150
ms.assetid: 212275d0-a32b-4560-97c5-1499616b8787
description: "Plan users and groups for Project Online in SharePoint Permission Mode."
---

# Plan SharePoint groups in Project Online

  
In Project Online, SharePoint Permission Mode creates SharePoint groups that directly correspond to the default security groups found in Project Permission Mode.
  
> [!TIP]
>  Need to switch between security modes? Take a look at [Change permission management in Project Online](change-permission-management-in-project-online.md). 
  
## What groups are available?
<a name="__top"> </a>

The following list describes the SharePoint groups and what they'll allow users to do in Project Online.
  
- **Administrators** Users have all global permissions as well as category permissions through the **My Organization** category. This allows them complete access to everything in Project Online. 
    
- **Portfolio Viewers** Users have permissions to view Project Online data. This group is intended for high-level users who need visibility into projects but are not themselves assigned project tasks. 
    
- **Project Managers** Users have permissions to create and manage projects. This group is intended for project owners who assign tasks to resources. 
    
- **Portfolio Managers** Users have assorted project-creation and team-building permissions. This group is intended for high-level managers of groups of projects. 
    
- **Resource Managers** Users have most global and category-level resource permissions. This group is intended for users who manage and assign resources and edit resource data. 
    
- **Team Leads** Users have limited permissions around task creation and status reports. This group is intended for persons in a lead capacity that do not have regular assignments on a project. 
    
- **Team Members** Users have general permissions for using Project Online, but limited project-level permissions. This group is intended to give everyone basic access to Project Online. 
    
These SharePoint groups have the same global and category permissions that are assigned to them in Project Permission Mode. In SharePoint Permission Mode, you cannot create additional custom groups, categories, Resource Breakdown Structure (RBS) nodes, or edit the default permissions assigned to any of these objects.
  
There are two methods of adding users to the SharePoint groups: adding individual users, or using Active Directory groups to add users. You can use one or both of these methods for each group.
  
## Adding individual users to SharePoint groups
<a name="__top"> </a>

When you add individual users to one of the SharePoint groups, that user is synchronized to Project Online automatically. User synchronization runs every ten minutes.
  
## Using Active Directory groups to add users to SharePoint groups
<a name="__top"> </a>

When you add Active Directory groups to one of the SharePoint security groups, the users are not automatically added to the list of users in Project Online. Each user is individually added the first time she or he accesses Project Online. 
  
Because users in Active Directory groups do not appear on the list of resources until they have accessed Project Online, we recommend that you [configure Active Directory synchronization](configure-the-resource-center.md) in Project Online to prepopulate your resource list. This allows you to have a complete resource list and to assign work to resources before they have accessed Project Online. 
  

