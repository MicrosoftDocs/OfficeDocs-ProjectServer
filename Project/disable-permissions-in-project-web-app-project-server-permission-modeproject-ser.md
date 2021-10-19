---
title: "Disable permissions in Project Web App (Project Server permission mode) (Project Server 2013)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 4916dd91-cc55-4a08-a882-83ea0a166d66
description: "Summary: Project Web App global and category permissions can be disabled, but this action should be examined carefully before it is done."
---

# Disable permissions in Project Web App (Project Server permission mode) (Project Server 2013)

**Summary:** Project Web App global and category permissions can be disabled, but this action should be examined carefully before it is done.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server permission mode, you can disable individual permissions in Project Web App.
  
> [!IMPORTANT]
> In Project Web App, thoroughly consider the effects on your organization of disabling permissions before making such a change. If the removal of the permission does not need to be applied to all users, then verify whether another approach could be used. For example, could you create a custom group and deny the permission you want to restrict instead of disabling the permission throughout the organization? 
  
For information about how permissions work, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md).
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage Project Web App permissions (Project Server permission mode)](manage-project-web-app-permissions-project-server-permission-mode.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Disable a Project Web App organizational permission

Perform the following procedure to disable a Project Web App permission.
  
### To disable a Project Web App permission

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Project Web App Permissions**.
    
3. On the Project Web App Permissions page, in the **Available Project Web App Permissions** list, clear the **Enable** check box next to the permission that you no longer want to make available to Project Web App users. (All Project Web App permissions are enabled by default.)
    
4. Click **Save**.
    
    > [!NOTE]
    > Enabling a previously disabled permission is simply done by selecting the **Enable** check box next to the permission that has been disabled.
  
## See also

#### 

[Manage Project Web App permissions (Project Server permission mode)](manage-project-web-app-permissions-project-server-permission-mode.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)