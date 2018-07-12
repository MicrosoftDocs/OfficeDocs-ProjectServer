---
title: "Grant reporting access in Project Online"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 2/25/2016
audience: admin
ms.topic: article
ms.service: project-online
localization_priority: Normal
search.appverid:
- PJO150
- PJO160
ms.assetid: 4f125cf5-a752-4ce6-b9e9-5a2eb6ace9e2
description: "If your Project Online reports connect to the OData feed, you'll need to grant the BI Azure Service access to Project Web App before you can refresh data in Excel Web App. This article explains how to grant this access."
---

# Grant reporting access in Project Online

 *[\< More Project help](project-help.md)* 
  
Before you can use Project Online reports in Excel Online, the tenant administrator needs to activate this feature for the Project Online site collection.
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your admin account. 
    
2. At the top of the page, select **Projects**. Or, select the app launcher ![Office 365 app launcher icon](media/0aaa6945-f9a4-4b13-bf5f-d5c5dbe978fb.png), and then select **Projects**.
    
3. Select **Settings**![Settings icon](media/22ecb306-849a-4d04-8885-fe49ec9df8ce.png)\> **Site Settings**.
    
4. Under **Site Collection Administration**, select **Site collection features**.
    
5. Scroll down in the list to **Project Web App Permission for Excel Web App Refresh**, and then select **Activate**.
    
    ![Project Web App Permission for Excel Online Refresh](media/3b65c380-44e9-4377-8746-a52ae7662965.png)
  
    > [!TIP]
    >  If you have more than one Project Online site collection, make a note about which one has **Project Web App Permission for Excel Online Refresh** activated. When you activate it on one site collection, it is activated for all site collections in your Office 365 tenant. However, if you ever want to deactivate it, you can only turn it off from the site collection where you activated it initially. 
  
You should now be able to refresh your Project Online reports in Excel Online.
  
> [!IMPORTANT]
>  Before using the default Project Online reports ( **Project Overview**, **Resource Overview**, and **Project Overview Dashboard**), you may need to open each report in Excel 2013, refresh the data, and then save the report back to Project Online. This will update the report so that it is supported by Excel Online. 
  

