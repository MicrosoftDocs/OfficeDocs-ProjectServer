---
title: "Manage categories in Project Server"
ms.author: efrene
author: efrene
ms.prod: scotv
ms.date: 3/9/2015
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_OneDriveAdmin
ms.assetid: 89cf59e5-e06b-4f02-93a9-bc1ee4679789
description: "Summary: Administrators can organize a system of categories to manage user and group access to projects, resources, and views in Project Web App."
---

# Manage categories in Project Server
 
 **Summary:** Administrators can organize a system of categories to manage user and group access to projects, resources, and views in Project Web App.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
In Project Server permission mode, Categories are the collections of projects, resources, and views to which users and groups in Project Server are granted access. Categories define which collections of specific data (projects, resources, and views) that these users and groups have access to. Categories also allow the administrator to filter data using security rules, like Resource Breakdown Structure (RBS), that can help organize and display data in specific ways.
  
> [!NOTE]
> Categories are only available in Project Server permission mode. If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
You can add projects and resources to categories manually by choosing them from lists, or you can use dynamic filters to automatically add them to categories. Any user associated with a category can be granted permission to the projects and resources in that category.
  
- You must have the **Manage users and groups** global permission to add, modify, or delete a category.
    
- Avoid creating unnecessary categories. Having a large number of groups and categories within an organization can stress the authorization system, which can affect performance.
    
Project Web App provides five default categories in Project Server permission mode. These default categories are designed to enable Project Web App to provide the most common layer of security for a hierarchical organization or matrix organization. 
  
|**Default category**|**Default groups in the category**|**Description**|
|:-----|:-----|:-----|
|My Tasks  <br/> |Team Members  <br/> |Primarily used by project resources who have assigned tasks.  <br/> |
|My Projects  <br/> |Project Managers  <br/> Resource Managers  <br/> Team Leads  <br/> |Provides access to all projects that a user owns.  <br/> |
|My Resources  <br/> |Resource Managers  <br/> |Intended for resource managers and is useful only after the Resource Breakdown Structure (RBS) is defined.  <br/> |
|My Direct Reports  <br/> |Resource Managers  <br/> |Intended for users who need to be able to approve timesheets.  <br/> |
|My Organization  <br/> |Portfolio Viewers  <br/> Portfolio Managers  <br/> Project Managers  <br/> Resource Managers  <br/> Administrators  <br/> |Used to grant access to all information in the organization. This category is intended for members of a Project Management Office (PMO), executives in an organization, and other key users who require the ability to view projects and resources across the entire organization.  <br/> |
   
## Task requirements

The following are required to perform the procedures for this task:
  
- Access to Project Web App
    
- The **Manage users and groups** global permission in Project Web App in order to create, modify, or delete a category
    
To manage categories in Project Web App, you can perform the following procedures:
  
- [Create security categories in Project Server](create-security-categories-in-project-server.md)
    
- [Modify categories in Project Server](modify-categories-in-project-server.md)
    
- [Delete a category (Project Server permission mode)](delete-a-category-project-server-permission-mode.md)
    
## See also

#### 

[Plan user access in Project Server](plan-user-access-in-project-server.md)
  
[Manage users, groups, and categories in Project Server](manage-users-groups-and-categories-in-project-server-2013.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Default categories in Project Server 2013](default-categories-in-project-server-2013.md)

