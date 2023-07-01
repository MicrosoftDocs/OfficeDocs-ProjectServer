---
title: Delete a security template (Project Server permission mode)
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_OneDriveAdmin
ms.assetid: cb63b6ca-2af4-4c80-bb61-17e3a9d76d34
description: Learn how to delete Project Web App security templates by using the Manage Templates page in Project Web App Settings.
---

# Delete a security template (Project Server permission mode)
 
 **Summary:** Learn how to delete Project Web App security templates by using the Manage Templates page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server security mode, you can delete any existing security templates from the Manage Templates page in Project Web App Settings.
  
> [!IMPORTANT]
> As a best practice, do not delete any of the default Project Web App templates. 
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage security templates in Project Server](manage-security-templates-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Delete a template

Perform the following procedure to delete an existing template in Project Web App.
  
### To delete a template

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Security Templates**.
    
3. On the Manage Templates page, in the **Template Name** list, select the check box next to the templates that you want to delete.
    
4. Click **Delete Template**. 
    
    A warning message appears, noting that the template will be permanently removed. 
    
5. Click **OK**.
    
## See also


[Manage security templates in Project Server](manage-security-templates-in-project-server.md)
  
[Create security templates in Project Server](create-security-templates-in-project-server.md)
  
[Modify security templates in Project Server](modify-security-templates-in-project-server.md)
  
[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)