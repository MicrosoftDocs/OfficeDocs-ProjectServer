---
title: "Plan for upgrade to Project Server Subscription Edition"
ms.author: v-bshilpa
author: Benny-54
manager: serdars
ms.date: 6/17/2021
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 
description: "Summary: Learn about considerations you need to make in upgrading to Project Server Subscription Edition."
---

# Plan for upgrade to Project Server Subscription Edition
 
 **Summary:** Learn about considerations you need to make in upgrading to Project Server Subscription Edition.<br/>
**Applies to:** Project Server Subscription Edition
  
In this article:
  
- [Things you need to know about upgrading to Project Server Subscription Edition](plan-for-upgrade-to-project-server-2019.md#thingknow)
    
- [Upgrading from an earlier version of Project Server](plan-for-upgrade-to-project-server-2019.md#Upg)
    
- [Upgrading multiple Project Web App sites](plan-for-upgrade-to-project-server-2019.md#MultPWA)
    
> [!NOTE]
> <br/>For an overview of the steps in the upgrade process, see [Overview of the Project Server Subscription Edition upgrade process](overview-of-the-project-server-2019-upgrade-process.md).<br/> <br/>For details information about the upgrade process, see [Upgrading to Project Server Subscription Edition](upgrading-to-project-server-2019.md). 
  
## Things you need to know about upgrading to Project Server Subscription Edition
<a name="thingknow"> </a>

If you are planning to upgrade to Project Server Subscription Edition, it is important to know the following:
  
- **You can only upgrade to Project Server Subscription Edition through Project Server 2016 or 2019**. If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2016 or 2019 first in order to upgrade to Project Server Subscription Edition. 
   
- **No in-place upgrade**. You must first create a Project Server Subscription Edition installation, and then attach and upgrade your Project Server 2016 or 2019 databases to the new farm. In-place upgrade is not supported.
    
- **Upgrade through Microsoft PowerShell cmdlets**. Similar to the Project Server 2019 upgrade experience, upgrading to Project Server Subscription Edition will be by using PowerShell cmdlets. You can use the SharePoint Subscription Edition Management Shell to run the correct version of the cmdlets used for upgrade.
    
## Upgrading from an earlier version of Project Server
<a name="Upg"> </a>

Since upgrading to Project Server Subscription Edition from Project Server 2016 or 2019 is the only supported upgrade path, you will have to upgrade to Project Server 2016 or 2019 first if you are upgrading from an earlier version of Project Server.

|**Upgrading from**|**Upgrade path**|
|:-----|:-----|
|Project Server 2013 |1. Upgrade to Project Server 2016 <br/> 2. Upgrade to Project Server  Subscription Edition <br/>|
|Project Server 2016 |1. Upgrade to Project Server Subscription Edition <br/> or <br/> 1. Upgrade to Project Server 2019 <br/> 2. Upgrade to Project Server Subscription Edition <br/>|
|Project Server 2019 |1. Upgrade to Project Server Subscription Edition <br/>|


For more information, see:<br/>
[Upgrade to Project Server 2013](./upgrade-to-project-server-2016.md) <br/> 
[Upgrading to Project Server 2016](upgrading-to-project-server-2016.md) <br/> 
   
## Upgrading multiple Project Web App sites
<a name="MultPWA"> </a>

If you have multiple Project Web App sites using the same content database, and want the update the site collections in the content database or any of the PWA sites to Subscription Edition, all the sites in the content database and all three PWA sites must be upgraded at the same time.
  
In the following example, Contoso is using Project Server 2016 or 2019 and has three PWA sites that all use the same content database to store their data (ContentDB-A). When upgrading to Project Server Subscription Edition, attached to the content database and then begin the upgrade process.
  

| **PWA site**                         |  **Content database** |
|:-------------------------------------|:----------------------|
| <https://contoso/sites/PWA_A>  <br/> |  ContentDB-A  <br/>   |
| <https://contoso/sites/PWA_B>  <br/> |  ContentDB-A  <br/>   |
| <https://contoso/sites/PWA_C>  <br/> |  ContentDB-A  <br/>   |
