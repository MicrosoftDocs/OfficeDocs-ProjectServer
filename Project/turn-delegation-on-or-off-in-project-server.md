---
title: "Turn delegation on or off in Project Server"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/16/2014
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: eafbf21a-a6eb-4855-afbc-255ecb870142
description: "Summary: The user delegation feature in Project Web App can be enabled or disabled globally, for all users and groups."
---

# Turn delegation on or off in Project Server
 
 **Summary:** The user delegation feature in Project Web App can be enabled or disabled globally, for all users and groups.<br/>
**Applies to:** Project Server 2013
  
When user delegation is turned on, you can set permissions to control the specific behavior of the feature in Project Web App.
  
### To turn delegation on or off

1. On the PWA home page, click **Server Settings**.
    
2. On the **Server Settings** page, in the **Security** section, click **Project Web App Permissions**.
    
3. In the **Resource** section, select the check box for the **Manage Resource Delegates** permission to turn on the user delegation feature within Project Web App.
    
4. Choose any additional delegation permissions that meet your organization's needs:
    
   - **Manage My Resource Delegations** Select this check box to enable users to set up delegations for other users.
    
   - **Manage My Delegations** Select this check box to enable users to create delegations for themselves.
    
   - **Can be Delegate** Select this check box to enable a user to become a delegate for another user, after a delegation has been created.
    
5. Click **Save** to save the permissions on the server.
    
## See also


[Create delegations in Project Server](create-delegations-in-project-server.md)

