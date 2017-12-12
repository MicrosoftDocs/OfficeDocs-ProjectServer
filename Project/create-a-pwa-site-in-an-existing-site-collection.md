---
title: "Create a PWA site in an existing site collection"
ms.author: efrene
author: efrene
manager: gailmc
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: project-server
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: bd4e7c9f-79f7-45c4-8cbe-8dbe75c72370
description: "Summary: Add a Project Web App site to an existing site collection."
---

# Create a PWA site in an existing site collection
 
 **Summary:** Add a Project Web App site to an existing site collection.
  
You can add a Project Web App site to an existing site collection. Doing so will allow you to take full advantage of Project Server 2016 and Project Web App functionality for the projects in that site collection.
  
In order for a Project Web App site to function properly, the Project Web App site collection features must be enabled. If you have not already done so, [enable the Project Web App site collection features](enable-the-project-web-app-site-collection-features-in-project-server-2016.md) on the site collection where you want to deploy the Project Web App site.
  
To create a Project Web App site in an existing site collection, you run the New-SPWeb Microsoft PowerShell cmdlet to create the site. Run the following script to create the Project Web App site.
  
```
New-SPweb -URL SiteCollectionURL/PWASiteName -Template pwa#0

```

For example:
  
```
New-SPweb -URL http://contoso-appsrv1/sites/ContosoProjects/PWA -Template pwa#0

```

The Project Web App site is now available at the URL that you specified.
  
## See also

#### 

[New-SPWeb](http://technet.microsoft.com/library/1ea28725-5b75-49f9-b69c-5ff0edf31459.aspx)
  
[Upgrade-SPProjectWebInstance](http://technet.microsoft.com/library/014804fa-0006-462d-9c40-70a487fd6819.aspx)
  
[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

