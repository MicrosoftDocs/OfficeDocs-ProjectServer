---
title: "Manage users, groups, and categories in Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/9/2015
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 8f290faa-8b71-4b98-9621-72e14551b784
description: "Summary: Manage users, groups, and categories in Project Server permission mode."
---

# Manage users, groups, and categories in Project Server
 
 **Summary:** Manage users, groups, and categories in Project Server permission mode.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server permission mode, Project Web App security is based on users, groups, and categories. Groups contain sets of users who need to access the same set of data in the same way. Categories provide access to projects and resources based on parameters that you define. For complete information about planning groups and categories, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md).
  
Define your groups by identifying common needs based on the areas of Project Web App to which users in your organization need access. After you define your groups, you can add users to the groups and grant permissions to the groups. Permissions assigned to groups apply to all of the users that the group contains. Using groups to control access to Project Web App simplifies security administration. 
  
Users can be automatically added or removed from groups based on Active Directory group membership. This can be configured in Project Web App through the Active Directory synchronization feature. For more information, see [Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md).
  
Users can belong to multiple groups according to their role in the organization and their access requirements. Several groups are created by default when a Project Web App instance is created, each of which is assigned a set of predefined categories and permissions. For more information, see [Manage security groups in Project Server](manage-security-groups-in-project-server.md).
  
Administrators usually assign permissions by adding a user account to one of the built-in groups or by creating a new group and assigning specific permissions to that group.
  
For complete lists of Project Web App permissions in Project Server 2013, see [Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md) and [Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md).
  
## Articles about Security settings for Project Server permission mode

The following are the tasks for managing security in Project Server permission mode:
  
|&nbsp;|**Content**|**Description**|
|:-----|:-----|:-----|
|![Building blocks.](images/mod_icon_buildingblock_M.png)|[Manage users in Project Server](manage-users-in-project-server.md) <br/> |Use the Manage Users page in Project Web App to add, modify, deactivate, and reactivate user accounts.  <br/> |
||[Manage security groups in Project Server](manage-security-groups-in-project-server.md) <br/> |Administrators can manage security permissions for groups by using the Manage Groups page in Project Web App Settings.  <br/> |
||[Manage categories in Project Server](manage-categories-in-project-server.md) <br/> |Administrators can organize a system of categories to manage user and group access to projects, resources, and views in Project Web App.  <br/> |
||[Manage security templates in Project Server](manage-security-templates-in-project-server.md) <br/> |Administrators can use security templates in Project Web App to standardize the granting of user permissions by role.  <br/> |
||[Manage Project Web App permissions (Project Server permission mode)](manage-project-web-app-permissions-project-server-permission-mode.md) <br/> |Project Web App global and category permissions can be disabled, but this action should be examined carefully before it is done.  <br/> |
||[Manage delegates in Project Server](manage-delegates-in-project-server.md) <br/> |Project Server 2016 enables user delegation throughout all of Project Web App.  <br/> |
||[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md) <br/> |Project Server security group synchronization controls Project Server security group membership by automatically adding and removing users from specified Project Server security groups based on group membership in the Active Directory directory service.  <br/> |
||[Plan users, groups, and catagories in Project Web App](plan-groups-categories-and-rbs-in-project-server.md) <br/> |This article addresses planning for groups and categories in a Project Server deployment.  <br/> |
   
## Videos about Security settings for Project Server

[Video series: How security permissions work in Project Server](https://support.office.com/article/Video-series-How-security-permissions-work-in-Project-Server-A19FB429-4F8F-4AA1-A186-8A33650C9801?ui=en-US&rs=en-US&ad=US)
  

   

