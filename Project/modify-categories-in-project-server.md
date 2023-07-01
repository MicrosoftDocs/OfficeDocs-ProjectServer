---
title: Modify categories in Project Server
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: d9c8a396-e2de-443c-8046-8e6bc20d087f
description: Edit security categories by using the Manage Categories page in Project Web App Settings.
---

# Modify categories in Project Server
 
 **Summary:** Edit security categories by using the Manage Categories page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Web App, you can modify an existing category from the Manage Categories page on the Project Web App Server Settings page. You might want to do this, for example, if an existing category has to be updated for new projects and resources.
  
> [!NOTE]
> Categories are only available in Project Server permission mode. If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage categories in Project Server](manage-categories-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Modify a category

Perform the following procedure to modify an existing category in Project Web App.
  
### To modify a category

1. On the PWA home page, on the **Settings** menu, click **Server Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Categories**.
    
3. On the Manage Categories page, in the **Category Name** list, click the name of the category that you want to edit.
    
4. On the Add or Edit Category page, make your changes to the category information. For information about the options on the page, see [Create security categories in Project Server](create-security-categories-in-project-server.md).
    
5. Click **Save**.
    
## See also


[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Create security categories in Project Server](create-security-categories-in-project-server.md)
  
[Delete a category (Project Server permission mode)](delete-a-category-project-server-permission-mode.md)
  
[Manage categories in Project Server](manage-categories-in-project-server.md)