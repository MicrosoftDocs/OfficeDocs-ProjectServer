---
title: "Enable the Project Web App site collection features in Project Servers 2016 or 2019"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 7/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: b9c4dff2-4812-4131-8b20-4b7766d93233
description: "Summary: Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App."
---

# Enable the Project Web App site collection features in Project Servers 2016 or 2019
 
 **Summary:** Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App.<br/>
**Applies to:** Project Server 2016, Project Server 2019
  
Enabling the Project Web App site collection features adds additional functionality to the site collection that allows you to import SharePoint list projects into Project Web App.
  
## Enable the Project Web App site collection features
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

The Project Web App site collection features are enabled by using the [Enable-SPFeature](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/enable-spfeature?view=sharepoint-ps) PowerShell cmdlet. 

From the PowerShell command prompt, type the followoing syntax to enable the Project Web App site collection features.
  
```
Enable-SPFeature pwasite -URL SiteCollectionURL
```

For example:
  
```
Enable-SPFeature pwasite -URL http://contoso-appsrv1/sites/ContosoProjects

```

After the Project Web App site collection features have been activated for the site collection, you can add a Project Center web part and begin importing SharePoint list projects into Project Web App.
  
If you want to add a Project Web App site to the site collection, see [Create a PWA site in an existing site collection](create-a-pwa-site-in-an-existing-site-collection.md).
  
## See also
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

#### 


[Enable-SPFeature](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/enable-spfeature?view=sharepoint-ps)
  
[Get-SPWeb](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/get-spweb?view=sharepoint-ps)
  
[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

