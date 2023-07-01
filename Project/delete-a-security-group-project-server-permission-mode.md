---
title: Delete a security group (Project Server permission mode)
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_OneDriveAdmin
ms.assetid: 1ff8d75f-637e-4474-acdc-f57b6390f59d
description: Delete custom security groups by using the Manage Groups page in Project Web App Settings.
---

# Delete a security group (Project Server permission mode)
 
 **Summary:** Delete custom security groups by using the Manage Groups page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server permission mode, if you no longer need a security group in Project Web App, you can delete it. Before you delete a group, ensure that no other users or groups are dependent on it for required permissions. 
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage users in Project Server](manage-users-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Delete a security group

Perform the following procedure to delete a group in Project Web App.
  
> [!IMPORTANT]
> We highly recommend that you not delete the default Project Web App groups. The Team Members group cannot be deleted. 
  
### To delete a custom group

1. On the Project Web App home page, on the **Settings** menu, click **Server Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Groups**.
    
3. On the Manage Groups page, in the **Group Name** list, find the group you want to delete. Select the check box next to the group that you want to delete. Note that you can select multiple groups.
    
4. Click **Delete Group**. 
    
5. A message box appears, asking for confirmation and noting that the group will be permanently removed. Click **OK** to delete the group.
    
    > [!NOTE]
    > Security groups are permanently deleted, unlike deactivated user accounts (which can be reactivated). If you delete a security group and then find that you want to have it again, you must recreate it. 
  
## See also


[Manage users in Project Server](manage-users-in-project-server.md)