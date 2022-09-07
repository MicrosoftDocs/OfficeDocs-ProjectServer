---
title: "Delete a category (Project Server permission mode)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: ba624d09-892e-459b-abe6-50718e6520c9
description: "Summary: Delete custom security categories by using the Manage Categories page in Project Web App Settings."
---

# Delete a category (Project Server permission mode)
 
 **Summary:** Delete custom security categories by using the Manage Categories page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Web App, you can delete any existing custom category from the Manage Categories page in Project Web App.
  
> [!NOTE]
> Default Project Server categories cannot be deleted. 
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites: 
  
- Read [Manage categories in Project Server](manage-categories-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Delete a category

Perform the following procedure to delete an existing category in Project Web App.
  
### To delete a category

1. On the Project Web App home page, on the **Settings** menu, click **Server Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Categories**.
    
3. On the Manage Categories page, in the **Category Name** list, find the category that you want to delete. Select the check box next to the category that you want to delete. Note that you can select multiple categories.
    
4. Click **Delete Categories**.
    
    A warning message appears, noting that the category will be permanently removed. 
    
    > [!CAUTION]
    > Verify that the category you are deleting is the one you intend to delete. If you accidentally delete the wrong category, it is permanently deleted and will need to be recreated. 
  
5. Click **OK**.
    
## See also


[Manage categories in Project Server](manage-categories-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Create security categories in Project Server](create-security-categories-in-project-server.md)
  
[Modify categories in Project Server](modify-categories-in-project-server.md)