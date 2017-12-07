---
title: "Enable the Project Web App site collection features in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/20/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 41b5c036-6647-4daf-89cb-e56d6c2300ff
description: "Summary: Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App."
---

# Enable the Project Web App site collection features in Project Server 2013
 
 **Summary:** Enable the Project Web App site collection features to allow the import of SharePoint list projects into Project Web App.
  
Enabling the Project Web App site collection features adds additional functionality to the site collection that allows you to import SharePoint list projects into Project Web App.
  
Enabling the Project Web App site collection features consists of two steps:
  
- [](enable-the-project-web-app-site-collection-features-in-project-server-2016.md#CreateAProjectWebAppDatabase)
    
- [Enable the Project Web App site collection features](enable-the-project-web-app-site-collection-features-in-project-server-2016.md#EnableTheProjectWebAppSiteCollectionFeatures)
    
## Video demonstration

This video shows the steps involved in enabling the Project Web App site collection features, as described in this article.
  
**Video: Enable the Project Web App site collection features in Project Server 2013**

![Video (play button) icon](images/mod_icon_video_M.png)
  
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
$web=Get-SPWeb http://contoso-appsrv1/sites/ContosoProjects
$web.Properties["PWA_TAG"]="ProjectWebApp1DB"
$web.Properties.Update()
Enable-SPFeature pwasite -URL http://contoso-appsrv1/sites/ContosoProjects

```

After the Project Web App site collection features have been activated for the site collection, you can add a Project Center web part and begin importing SharePoint list projects into Project Web App.
  
If you want to add a Project Web App site to the site collection, see [Create a PWA site in an existing site collection](create-a-pwa-site-in-an-existing-site-collection.md).
  
## See also
<a name="EnableTheProjectWebAppSiteCollectionFeatures"> </a>

#### 

[New-SPProjectDatabase](http://technet.microsoft.com/library/6eca666c-cbe8-41aa-94c5-4a8a3419fc96.aspx)
  
[Enable-SPFeature](http://technet.microsoft.com/library/9b68c192-b640-4cb8-8a92-a98008169b27.aspx)
  
[Get-SPWeb](http://technet.microsoft.com/library/9bf9284f-e3b9-439d-8a5f-74020e1eccaf.aspx)
  
[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

