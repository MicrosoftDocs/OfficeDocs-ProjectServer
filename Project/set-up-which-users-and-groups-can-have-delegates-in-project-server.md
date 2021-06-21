---
title: "Set up which users and groups can have delegates in Project Server"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 6608aa2b-72a3-4af3-a015-6f6506f2d382
description: "Summary: How to set up who can have delegates assigned to them in Project Server."
---

# Set up which users and groups can have delegates in Project Server
 
 **Summary:** How to set up who can have delegates assigned to them in Project Server.<br/>
**Applies to:** Project Server 2013
  
Categories are used in Project Web App to determine which users or groups can have delegates do work on their behalf. In order for a delegation to work correctly, the user requesting the delegation must have the correct category permissions, and the user who will act as the delegate must have the correct individual user or group permissions.
  
### To set up who can have delegates assigned to them

1. On the PWA home page, click **Server Settings**.
    
2. In the **Security** section, click **Manage Categories**.
    
3. Click the name of the category that contains the user or group for which you want to enable user delegation.
    
4. In the **Users and Groups** section, click the name of group or a specific user in the **Users and Groups with Permissions** box.
    
5. In the permissions box that appears, scroll down to the **Resource** section, and select the check box for the **Manage Resource Delegates** permission to turn on the user delegation feature for that user or group.
    
6. Click **Save** to save the permissions on the server.
    
## See also

#### 

[Set up which users and groups can act as delegates in Project Server](set-up-which-users-and-groups-can-act-as-delegates-in-project-server.md)

