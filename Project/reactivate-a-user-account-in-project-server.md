---
title: "Reactivate a user account in Project Server"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 10/10/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: c869cc96-a6c8-4131-8415-74b27dfa5efd
description: "Summary: Reactivate deactivated user accounts by using the Manage Users page in Project Web App Settings."
---

# Reactivate a user account in Project Server
 
 **Summary:** Reactivate deactivated user accounts by using the Manage Users page in Project Web App Settings.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
After you deactivate a user account, you may need to reactivate it at some later time. Because the user information still exists in the Project Server database, you simply need to change the account status from **Inactive** to **Active**.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](http://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
Before you begin this operation, review the following information about prerequisites: 
  
- Read [Manage users in Project Server](manage-users-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Reactivate a user account

Use this procedure to reactivate a deactivated Project Web App user account. After you have performed this procedure, the reactivated account is able to access Project Web App.
  
### To reactivate a user account

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Users**.
    
3. On the Manage Users page, in the **Users** list, find the user account you want to reactivate. (You can use the **Search** box to search for a specific user.) Click the user name of the account.
    
4. On the Edit User page for the selected user, in the **Identification Information** section, select **Active** from the **Account Status** drop-down list.
    
5. Click **Save**.
    
## See also

#### 

[Deactivate user accounts in Project Server](deactivate-user-accounts-in-project-server.md)
  
[Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md)

