---
title: "Enable the Project Web App site collection features in Project Servers Subscription Edition, 2019, or 2016"
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 7/24/2018
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: b9c4dff2-4812-4131-8b20-4b7766d93233
description: "Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App."
---

# Enable the Project Web App site collection features in Project Servers Subscription Edition, 2019, or 2016

 **Summary:** Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016

Enabling the Project Web App site collection features adds additional functionality to the site collection that allows you to import SharePoint list projects into Project Web App.

## Enable the Project Web App site collection features
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

The Project Web App site collection features are enabled by using the [Enable-SPFeature](/powershell/module/sharepoint-server/enable-spfeature) PowerShell cmdlet.

From the PowerShell command prompt, type the following syntax to enable the Project Web App site collection features.

```
Enable-SPFeature pwasite -URL SiteCollectionURL
```

For example:

```
Enable-SPFeature pwasite -URL https://contoso-appsrv1/sites/ContosoProjects
```

After the Project Web App site collection features have been activated for the site collection, you can add a Project Center web part and begin importing SharePoint list projects into Project Web App.

If you want to add a Project Web App site to the site collection, see [Create a PWA site in an existing site collection](create-a-pwa-site-in-an-existing-site-collection.md).

## See also
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

[Enable-SPFeature](/powershell/module/sharepoint-server/enable-spfeature)

[Get-SPWeb](/powershell/module/sharepoint-server/get-spweb)

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)