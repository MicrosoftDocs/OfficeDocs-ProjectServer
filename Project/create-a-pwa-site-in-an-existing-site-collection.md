---
title: "How to create a PWA site in an existing site collection"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 7/24/2018
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: bd4e7c9f-79f7-45c4-8cbe-8dbe75c72370
description: "Add a Project Web App site to an existing site collection."
---

# How to create a PWA site in an existing site collection

 **Summary:** Add a Project Web App site to an existing site collection.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016

You can add a Project Web App site to an existing site collection. Doing so will allow you to take full advantage of Project Server and Project Web App functionality for the projects in that site collection.

In order for a Project Web App site to function properly, the Project Web App site collection features must be enabled. If you have not already done so, [enable the Project Web App site collection features](enable-the-project-web-app-site-collection-features-in-project-server-2016.md) on the site collection where you want to deploy the Project Web App site.

To create a Project Web App site in an existing site collection, you run the [New-SPWeb](/powershell/module/sharepoint-server/new-spweb) Microsoft PowerShell cmdlet to create the site.

From the PowerShell command prompt, type the following syntax to create the Project Web App site.

```
New-SPweb -URL SiteCollectionURL/PWASiteName -Template pwa#0
```

For example:

```
New-SPweb -URL https://contoso-appsrv1/sites/ContosoProjects/PWA -Template pwa#0
```

The Project Web App site is now available at the URL that you specified.

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)