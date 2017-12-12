---
title: "Plan for upgrade to Project Server 2016"
ms.author: efrene
author: efrene
ms.prod: scotv
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 9b863614-a41e-4ee4-89bb-7f4efea886b3
description: "Summary: Learn about considerations you need to make in upgrading to Project Server 2016."
---

# Plan for upgrade to Project Server 2016
 
 **Summary:** Learn about considerations you need to make in upgrading to Project Server 2016.<br/>
**Applies to:** Project Server 2016
  
In this article:
  
- [Things you need to know about upgrading to Project Server 2016](plan-for-upgrade-to-project-server-2016.md#thingknow)
    
- [ Upgrading from an earlier version of Project Server](plan-for-upgrade-to-project-server-2016.md#Upg)
    
- [ Upgrading multiple Project Web App sites](plan-for-upgrade-to-project-server-2016.md#MultPWA)
    
> [!NOTE]
> For an overview of the steps in the upgrade process, see [Overview of the Project Server 2016 upgrade process](overview-of-the-project-server-2016-upgrade-process.md). > For details information about the upgrade process, see [Upgrading to Project Server 2016](upgrading-to-project-server-2016.md). 
  
## Things you need to know about upgrading to Project Server 2016
<a name="thingknow"> </a>

If you are planning to upgrade to Project Server 2016, it is important to know the following:
  
- **You can only upgrade to Project Server 2016 through Project Server 2013** If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2013 first in order to upgrade to Project Server 2016. There is no direct upgrade path from Project Server 2010 to Project Server 2016.
    
- **No in-place upgrade** You must first create a Project Server 2016 installation, and then attach and upgrade your Project Server 2013 databases to the new farm. In-place upgrade is not supported.
    
- **Upgrade through Windows PowerShell cmdlets** Similar to the Project Server 2013 upgrade experience, upgrading to Project Server 2016 will be through the use of Windows PowerShell cmdlets. You can use the SharePoint 2016 Management Shell to run the correct version of the cmdlets used for upgrade.
    
- **Upgrade your Project Server 2013 Resource Plans to Resource Engagements** Resource Engagements is a new feature in Project Server 2016 that helps project managers and resource managers to align with each other on the specific amount of work and time periods for specific resources associated with a project. Resource Engagements replaces the Resource Plans feature, as they will no longer be available in Project Server 2016. You can choose to migrate your existing Project Server 2013 Resources Plans to use as Resource Engagements in Project Server 2016 as part of the upgrade process. Note that for your Project Server 2013 Resource Plans to migrate correctly to Resource Engagements, they must contain time phased data and must be published.
    
    > [!NOTE]
    > For more information about Resource Engagements, see this blog post: [Resource Engagements](http://go.microsoft.com/fwlink/?LinkID=620823&amp;amp;clcid=0x409). 
  
## Upgrading from an earlier version of Project Server
<a name="Upg"> </a>

Since upgrading to Project Server 2016 from Project Server 2013 is the only supported upgrade path, you will have to upgrade to Project Server 2013 first if you are upgrading from an earlier version of Project Server.
  
|||
|**Upgrading from**|**Upgrade path**|
|:-----|:-----|
|Project Server 2010  <br/> |
1.Upgrade to Project Server 2013 <br/> 2.Upgrade to Project Server 2016 |
|Project Server 2007  <br/> |
1.Upgrade to Project Server 2010 <br/> 2.Upgrade to Project Server 2013 <br/> 3.Upgrade to Project Server 2016 |

For more informations:
[Upgrade to Project Server 2010](https://go.microsoft.com/fwlink/?LinkId=747042) <br/> 
[Upgrade to Project Server 2013](https://go.microsoft.com/fwlink/?LinkId=747043) <br/> 
[Upgrading to Project Server 2016](upgrading-to-project-server-2016.md) <br/> 
   
## Upgrading multiple Project Web App sites
<a name="MultPWA"> </a>

If you have multiple Project Web App sites using the same content database, and want the update the site collections in the content database or any of the PWA sites to 2016, all the sites in the content database and all three PWA sites must be upgraded at the same time.
  
In the following example, Contoso is using Project Server 2013 and has three PWA sites that all use the same content database to store their data (ContentDB-A). When upgrading to Project Server 2016, the content database and all three associated Project databases need to be copied to the Project Server 2016 database server, and then attached and upgraded in the upgrade process.
  
|**PWA site**|**Project database**|**Content database**|
|:-----|:-----|:-----|
|https://contoso/sites/PWA_A  <br/> |ProjectDB-A  <br/> |ContentDB-A  <br/> |
|https://contoso/sites/PWA_B  <br/> |ProjectDB-B  <br/> |ContentDB-A  <br/> |
|https://contoso/sites/PWA_C  <br/> |ProjectDB-C  <br/> |ContentDB-A  <br/> |
   

