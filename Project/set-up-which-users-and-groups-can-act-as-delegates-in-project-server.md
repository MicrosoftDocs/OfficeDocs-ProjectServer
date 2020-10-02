---
title: "Set up which users and groups can act as delegates in Project Server"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 6de83367-4ff3-4def-aac7-8fa7ecff9fab
description: "Summary: How to enable users or groups to act as delegates for other people in Project Server."
---

# Set up which users and groups can act as delegates in Project Server
 
 **Summary:** How to enable users or groups to act as delegates for other people in Project Server.<br/>
**Applies to:** Project Server 2013
  
In Project Web App, there are user- or group-level permissions that enable you to determine which users or groups can act as delegates for other people. By default, the only group that has these permissions turned on is the administrators group. Therefore, if you want users in your organization to be able to act as delegates, you have to set the appropriate permissions.
  
### To set permissions for a specific user

1. On the PWA home page, click **Server Settings**.
    
2. In the **Security** section, click **Manage Users**.
    
3. Click the name of the user for which you are setting permissions.
    
4. On the **Edit User** page, expand the **Global Permissions** section.
    
5. In the **Global Permissions** section, under **Resource**, choose the appropriate permissions for this user.
    
   - **Can be Delegate** Select the **Allow** check box for this permission to enable this user to become a delegate for another user.
    
   - **Manage My Delegations** Select the **Allow** check box for this permission to enable this user to create his or her own delegations.
    
   - **Manage My Resource Delegations** Select the **Allow** check box for this permission to enable this user to set up delegations for other users.
    
6. Click **Save** to save the permissions on the server.
    
### To set permissions for a group

1. On the PWA home page, click **Server Settings**.
    
2. In the **Security** section, click **Manage Groups**.
    
3. Click the name of the group for which you are setting permissions.
    
4. On the **Add or Edit Group** page, expand the **Global Permissions** section.
    
5. In the **Global Permissions** section, under **Resource**, choose the appropriate permissions for this group.
    
   - **Can be Delegate** Select the **Allow** check box for this permission to enable members of this group to become delegates for other users.
    
   - **Manage My Delegations** Select the **Allow** check box for this permission to enable members of this group to create their own delegations.
    
   - **Manage My Resource Delegations** Select the **Allow** check box for this permission to enable members of this group to set up delegations for other users.
    
6. Click **Save** to save the permissions on the server.
    
## See also

#### 

[Set up which users and groups can have delegates in Project Server](set-up-which-users-and-groups-can-have-delegates-in-project-server.md)

