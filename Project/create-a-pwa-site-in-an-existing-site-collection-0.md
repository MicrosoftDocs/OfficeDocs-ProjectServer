---
title: "Create a PWA site in an existing site collection"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: e0f8249e-5eae-4dee-ba36-d6d57f1080ae
description: "Summary: Add a Project Web App site to an existing site collection."
---

# Create a PWA site in an existing site collection
 
 **Summary:** Add a Project Web App site to an existing site collection.<br/>
**Applies to:** Project Server 2013
  
You can add a Project Web App site to an existing site collection. Doing so will allow you to take full advantage of Project Server 2013 and Project Web App functionality for the projects in that site collection.
  
In order for a Project Web App site to function properly, the site collection must have a Project Web App database associated with it and the Project Web App site collection features must be enabled. If you have not already done so, create a Project Web App database and enable the Project Web App site collection features on the site collection where you want to deploy the Project Web App site. For more information, see [Enable the Project Web App site collection features in Project Server 2013](enable-the-project-web-app-site-collection-features-in-project-server-2013.md).
  
To create a Project Web App site in an existing site collection, you run the New-SPWeb Microsoft PowerShell cmdlet to create the site and then run the **Upgrade-SPProjectWebInstance** to perform post-provisioning actions, including creating a Business Intelligence Center.
  
Run the following script to create the Project Web App site.
  
```
New-SPweb -URL SiteCollectionURL/PWASiteName -Template pwa#0
Upgrade-SPProjectWebInstance -Identity SiteCollectionURL -Confirm:$False
```

For example:
  
```
New-SPweb -URL https://contoso-appsrv1/sites/ContosoProjects/PWA -Template pwa#0
Upgrade-SPProjectWebInstance -Identity https://contoso-appsrv1/sites/ContosoProjects -Confirm:$False
```

After you have created the Project Web App site and run **Upgrade-SPProjectWebInstance**, you must run iisreset on each application server in the farm. To run iisreset, open a command window, and type:
  
```
iisreset /noforce
```

The Project Web App site is now available at the URL that you specified.
  
## See also

[New-SPWeb](/powershell/module/sharepoint-server/New-SPWeb)
  
[Upgrade-SPProjectWebInstance](/powershell/module/sharepoint-server/)
  
[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)