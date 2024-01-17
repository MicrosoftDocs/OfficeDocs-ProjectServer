---
title: "Enable the Project Web App site collection features in Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 41b5c036-6647-4daf-89cb-e56d6c2300ff
description: "Summary: Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App."
---

# Enable the Project Web App site collection features in Project Server 2013

 **Summary:** Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App.<br/>
**Applies to:** Project Server 2013

Enabling the Project Web App site collection features adds additional functionality to the site collection that allows you to import SharePoint list projects into Project Web App.

Enabling the Project Web App site collection features consists of two steps:

- Create a Project Web App database

- Enable the Project Web App site collection features

## Video demonstration

This video shows the steps involved in enabling the Project Web App site collection features, as described in this article.

**Video: Enable the Project Web App site collection features in Project Server 2013**

![Video (play button) icon.](images/mod_icon_video_M.png)

## Create a Project Web App database
<a name="CreateAProjectWebAppDatabase"> </a>

A Project Web App database is created using the **New-SPProjectDatabase** Microsoft PowerShell cmdlet. In order for the new database to be properly associated with the site collection where you want enable the Project Web App site collection features, you must use the **Tag** parameter to associate a unique string with this database. That string will be used later when you enable the site collection features.

Run the following cmdlet to create a new Project Web App database.

```
New-SPProjectDatabase -Name DatabaseName -ServiceApplication "ServiceApplicationName" -DatabaseServer SQLServerInstance -Tag String
```

For example:

```
New-SPProjectDatabase -Name ProjectWebApp1 -ServiceApplication "Project Service Application" -DatabaseServer Contoso-SQL -Tag "ProjectWebApp1DB"
```

> [!NOTE]
> You can find the name of the Project Server service application in Central Administration by clicking **Manage service applications** under **Application Management**. 

Once you have created the new Project Web App database, the next step is to enable the Project Web App site collection features. Doing so will associate the database that you just created with the site collection.

## Enable the Project Web App site collection features
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

The Project Web App site collection features are enabled by using the **Enable-SPFeature** PowerShell cmdlet. Prior to running this cmdlet, you must set the **PWA_TAG** parameter of the site collection to match the **Tag** parameter that you set when you created the database. Use the following PowerShell script to set the **PWA_TAG** parameter and then enable the Project Web App site collection features.

```
$web=Get-SPWeb SiteCollectionURL
$web.Properties["PWA_TAG"]="String"
$web.Properties.Update()
Enable-SPFeature pwasite -URL SiteCollectionURL
```

For example:

```
$web=Get-SPWeb https://contoso-appsrv1/sites/ContosoProjects
$web.Properties["PWA_TAG"]="ProjectWebApp1DB"
$web.Properties.Update()
Enable-SPFeature pwasite -URL https://contoso-appsrv1/sites/ContosoProjects
```

After the Project Web App site collection features have been activated for the site collection, you can add a Project Center web part and begin importing SharePoint list projects into Project Web App.

If you want to add a Project Web App site to the site collection, see [Create a PWA site in an existing site collection](create-a-pwa-site-in-an-existing-site-collection.md).

## See also
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

[New-SPProjectDatabase](/powershell/module/sharepoint-server/)

[Enable-SPFeature](/powershell/module/sharepoint-server/Enable-SPFeature)

[Get-SPWeb](/powershell/module/sharepoint-server/Get-SPWeb)

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)