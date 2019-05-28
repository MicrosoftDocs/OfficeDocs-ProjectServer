---
title: "Create security groups in Project Server"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: f3aa46e3-c36e-4ea2-be2f-2269896d914c
description: "Summary: Create custom security groups by using the Manage Groups page in Project Web App Settings."
---

# Create security groups in Project Server
 
 **Summary:** Create custom security groups by using the Manage Groups page in Project Web App Settings.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
Seven default security groups are available in Project Web App in Project Server permission mode. To better meet the security requirements of your own organization, you can also create custom groups by using the Manage Groups page on the Project Web App Server Settings page. 
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](http://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage security groups in Project Server](manage-security-groups-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
Perform the following procedure to create a custom group in Project Web App.
  
### To create a security group

1. On the Server Settings page, in the **Security** section, click **Manage Groups**.
    
2. On the Manage Groups page, click **New Group**.
    
3. Complete the required fields on the Add or Edit Group page. See the following sections for information about each area.
    
4. Click **Save**.
    
## Group information

Use the **Group Information** section to specify a name and description for the group.
  
The following table describes the group information options.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Group Name** <br/> |The name of the group  <br/> |
|**Description** <br/> |A description of the group  <br/> |
   
## Active Directory Group

If you want to synchronize the membership of this group with an Active Directory group, type the name of the Active Directory group in the format domain\\group. To stop synchronizing an existing group, click the **X** next to the group.
  
## Users

Use the **Users** section to specify which Project Web App users are members of this group.
  
To add users to the group, select the users in the **Available Users** list, and then click **Add**. To remove users from the group, select the users in the **Selected Users** list, and then click **Remove**.
  
If you have configured Active Directory synchronization for this group, the group membership is maintained by that mechanism. Any changes that you make manually may be overwritten the next time that the group is synchronized with the Active Directory directory service.
  
The following table describes the options for users in the group.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Available Users** <br/> |The users in Project Web App that are not members of this group  <br/> |
|**Selected Users** <br/> |The users in Project Web App that are members of this group  <br/> |
   
## Categories

Use the **Categories** section to define which security categories area associated with this group.
  
To associate a category with this group, select the category in the **Available Categories** list, and then click **Add**.
  
To set the category-level permissions for a particular category, select the category in the **Selected Categories** list, and then click **Allow** for the permissions that you want to enable for this category/group combination.
  
The following table describes the categories options for a group.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Available Categories** <br/> |The categories that are not associated with this group.  <br/> |
|**Selected Categories** <br/> |The categories that are associated with this group.  <br/> |
|**Permissions for** <category> <br/> |The permissions that members of this group have within the selected category. This option appears when you select a category in the **Available Categories** list. <br/> |
|**Set permissions with Template** <br/> |To set the category permissions for the selected category from a template — such as Project Manager or Team Member — select the desired template from the list, and then click **Apply**.  <br/> |
   
## Global permissions

Use the **Global Permissions** section to configure global permissions for this group.
  
To allow a permission for the group, select the **Allow** check box for that permission.
  
To deny a permission for the group, select the **Deny** check box for that permission.
  
To set the global permissions from a template, select the template from the **Set permissions with Template** dropdown list, and then click **Apply**.
  
For a complete list of global permissions in Project Server 2013, see [Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md).
  
> [!NOTE]
> If neither check box is selected for a permission, the user is not allowed the permission unless it is allowed in another group that the user is a member of, or it is allowed at the user level. If the **Deny** check box is selected for a permission, that permission is denied for all users in the group and cannot be enabled through other group or user settings.
  
## See also

#### 

[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Manage security groups in Project Server](manage-security-groups-in-project-server.md)

