---
title: "Manage Project Web App permissions (Project Server permission mode)"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/27/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 81ead545-11ef-4a45-b15c-c9835a6c05b0
description: "Summary: Project Web App global and category permissions can be disabled, but this action should be examined carefully before it is done."
---

# Manage Project Web App permissions (Project Server permission mode)
 
 **Summary:** Project Web App global and category permissions can be disabled, but this action should be examined carefully before it is done.
  
In Project Server permission mode, you can use the Project Web App Permissions page to control which global and category permissions are enabled on a given Project Web App instance. An administrator can use the Project Web App Permissions page to deny access to all Project Web App users for a particular feature in Project Professional or a Project Web App instance. If a Project Web App permission is disabled on this page, the equivalent global or category permission is disabled for users throughout Project Web App. All permissions on this page are enabled by default.
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
For example, if you deny the **Delete project** permission, users throughout Project Web App cannot delete projects, regardless of whether they have the Delete project category permission.
  
> [!IMPORTANT]
> Before disabling a Project Web App permission, thoroughly consider the effects on your organization of doing so. If you want to turn off a permission for only some Project Web App users, verify whether you can do it by creating a custom group and denying the permissions you want to restrict. 
  
## Task requirements

The following are required to perform the procedures for this task:
  
- Access to Project Web App
    
- The **Manage users and groups** global permission in Project Web App to manage Project Web App organizational permissions
    
To manage Project Web App organizational permissions in Project Web App, you can perform the following procedure:
  
- [Disable permissions in Project Web App (Project Server permission mode) (Project Server 2013)](disable-permissions-in-project-web-app-project-server-permission-modeproject-ser.md)
    
## See also

#### 

[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Manage users, groups, and categories in Project Server 2013](manage-users-groups-and-categories-in-project-server-2013.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
#### 

[Permissions in Project Web App](plan-groups-categories-and-rbs-in-project-server.md#section2)

