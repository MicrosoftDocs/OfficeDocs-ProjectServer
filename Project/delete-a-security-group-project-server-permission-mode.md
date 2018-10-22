---
title: "Delete a security group (Project Server permission mode)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/27/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_OneDriveAdmin
ms.assetid: 1ff8d75f-637e-4474-acdc-f57b6390f59d
description: "Summary: Delete custom security groups by using the Manage Groups page in Project Web App Settings."
---

# Delete a security group (Project Server permission mode)
 
 **Summary:** Delete custom security groups by using the Manage Groups page in Project Web App Settings.<br/>
**Applies to:** Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Server permission mode, if you no longer need a security group in Project Web App, you can delete it. Before you delete a group, ensure that no other users or groups are dependent on it for required permissions. 
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](http://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
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

#### 

[Manage users in Project Server](manage-users-in-project-server.md)

