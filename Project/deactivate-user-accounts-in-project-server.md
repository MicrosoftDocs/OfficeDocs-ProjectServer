---
title: "Deactivate user accounts in Project Server"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 10/10/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: 02858e0a-08ab-4216-b0b7-395bd19f12b2
description: "Summary: Deactivate user accounts by using the Manage Users page in Project Web App Settings."
---

# Deactivate user accounts in Project Server
 
 **Summary:** Deactivate user accounts by using the Manage Users page in Project Web App Settings.<br/>
**Applies to:** Project Server 2019, Project Server 2016, Project Server 2013
  
At times, you may have to make Project Web App user accounts unavailable. In Project Server permission mode, when you deactivate a user account, that user's information and data remains in the database, but the user is unavailable for new assignments. The user account is inactive until it is reactivated.
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
Deactivating a user account means that it can no longer be used to log on to Project Web App. Users cannot use this account to send assignment updates, request status reports, or delegate tasks. 
  
Once a user is deactivated, the Project Manager is prompted to reassign the user's work. This prompt occurs when the Project Manager opens the project in Project Professional.
  
User accounts, when deactivated, are not actually deleted from the Project Web App database. This is to ensure that any relationships that resource might have with project data can be preserved in case the account is reactivated later. The option to delete a user is available in the **Database Administration** section in Project Web App Settings. However, deactivating a user to preserve data is recommended.
  
After an account is deactivated, the account cannot access Project Web App until it has been reactivated. The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
When you are using Active Directory synchronization, Project Web App users not found in the Active Directory group being synchronized will be deactivated.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](https://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage users in Project Server](manage-users-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Deactivate a user account

Use this procedure to deactivate an active Project Web App user account. After this procedure has been performed, the account will be unable to access Project Web App until it has been reactivated.
  
### To deactivate a user account

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Users**.
    
3. On the Manage Users page, in the **Users** list, find the user account that you want to deactivate. (You can use the **Search** box to search for a specific user.) Click the check box next to the user name of the account that you want to deactivate. Note that you can select multiple user accounts.
    
4. Click **Deactivate Users**.
    
5. A message box appears and asks for confirmation. Click **OK** to deactivate the user account or user accounts.
    
## See also

#### 

[Reactivate a user account in Project Server](reactivate-a-user-account-in-project-server.md)
  
[Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md)

