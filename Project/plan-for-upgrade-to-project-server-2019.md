---
title: "Plan for upgrade to Project Server 2019"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 7/24/2018
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 9b863614-a41e-4ee4-89bb-7f4efea886b3
description: "Summary: Learn about considerations you need to make in upgrading to Project Server 2019."
---

# Plan for upgrade to Project Server 2019
 
 **Summary:** Learn about considerations you need to make in upgrading to Project Server 2019 .<br/>
**Applies to:** Project Server 2019
  
In this article:
  
- [Things you need to know about upgrading to Project Server 2019](plan-for-upgrade-to-project-server-2019.md#thingknow)
    
- [ Upgrading from an earlier version of Project Server](plan-for-upgrade-to-project-server-2019.md#Upg)
    
- [ Upgrading multiple Project Web App sites](plan-for-upgrade-to-project-server-2019.md#MultPWA)
    
> [!NOTE]
> <br/>For an overview of the steps in the upgrade process, see [Overview of the Project Server 2019 upgrade process](overview-of-the-project-server-2019-upgrade-process.md).<br/> <br/>For details information about the upgrade process, see [Upgrading to Project Server 2019](upgrading-to-project-server-2019.md). 
  
## Things you need to know about upgrading to Project Server 2019
<a name="thingknow"> </a>

If you are planning to upgrade to Project Server 2019, it is important to know the following:
  
- **You can only upgrade to Project Server 2019 through Project Server 2016** If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2016 first in order to upgrade to Project Server 2019. 

- **There is no direct upgrade path from Project Server 2013 to Project Server 2019.**  For additional information about how to upgrade from Project Server 2013 to 2019 Public Preview, see [High Level Overview to upgrade SharePoint 2013 to SharePoint Server 2019](https://docs.microsoft.com/sharepoint/upgrade-and-update/upgrade-from-sharepoint2013-to-sharepointserver-2019)

    
- **No in-place upgrade** You must first create a Project Server 2019 installation, and then attach and upgrade your Project Server 2016 databases to the new farm. In-place upgrade is not supported.
    
- **Upgrade through Microsoft PowerShell cmdlets** Similar to the Project Server 2016 upgrade experience, upgrading to Project Server 2019 will be through the use of PowerShell cmdlets. You can use the SharePoint 2019 Management Shell to run the correct version of the cmdlets used for upgrade.
    
    
## Upgrading from an earlier version of Project Server
<a name="Upg"> </a>

Since upgrading to Project Server 2019 from Project Server 2016 is the only supported upgrade path, you will have to upgrade to Project Server 2016 first if you are upgrading from an earlier version of Project Server.
  

|**Upgrading from**|**Upgrade path**|
|:---|:---|
|Project Server 2013 |1. Upgrade to Project Server 2016 <br/> 2. Upgrade to Project Server  2019 <br/>|


For more informations:<br/>
[Upgrade to Project Server 2013](https://go.microsoft.com/fwlink/?LinkId=747043) <br/> 
[Upgrading to Project Server 2016](upgrading-to-project-server-2016.md) <br/> 
   
## Upgrading multiple Project Web App sites
<a name="MultPWA"> </a>

If you have multiple Project Web App sites using the same content database, and want the update the site collections in the content database or any of the PWA sites to 2019, all the sites in the content database and all three PWA sites must be upgraded at the same time.
  
In the following example, Contoso is using Project Server 2016 and has three PWA sites that all use the same content database to store their data (ContentDB-A). When upgrading to Project Server 2019, attached to the content database and then begin the upgrade process.
  

| **PWA site**                         | **Project database** | **Content database** |
|:-------------------------------------|:---------------------|:---------------------|
| <https://contoso/sites/PWA_A>  <br/> | ProjectDB-A  <br/>   | ContentDB-A  <br/>   |
| <https://contoso/sites/PWA_B>  <br/> | ProjectDB-B  <br/>   | ContentDB-A  <br/>   |
| <https://contoso/sites/PWA_C>  <br/> | ProjectDB-C  <br/>   | ContentDB-A  <br/>   |

