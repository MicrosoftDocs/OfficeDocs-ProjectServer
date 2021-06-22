---
title: "Modify security groups in Project Server"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 30267248-e652-4fba-bb36-5ecdb2981132
description: "Summary: Change settings for security groups by using the Manage Groups page in Project Web App Settings."
---

# Modify security groups in Project Server
 
 **Summary:** Change settings for security groups by using the Manage Groups page in Project Web App Settings.<br/>
**Applies to:** Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server permission mode, you can modify the information associated with any security group in Project Web App. For example, you may have to modify the group for changes to users or categories, or for changes to the Active Directory group to which it is currently being synchronized.
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage security groups in Project Server](manage-security-groups-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Modify a security group

Perform the following procedure to modify an existing group in Project Web App.
  
### To modify a group

1. On the Project Web App home page, on the **Settings** menu, click **Server Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Groups**.
    
3. On the Manage Groups page, in the **Group Name** list, click the name of the group that you want to modify.
    
4. On the Add or Edit Group page for the selected group, make your changes to the group information. For information about each option on the page, see [Create security groups in Project Server](create-security-groups-in-project-server.md).
    
5. Click **Save**.
    
## See also

#### 

[Manage security groups in Project Server](manage-security-groups-in-project-server.md)