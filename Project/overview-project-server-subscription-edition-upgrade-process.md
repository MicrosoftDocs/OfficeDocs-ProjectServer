---
title: "Overview of the Project Server Subscription Edition upgrade process"
ms.author: serdars
author: Benny-54
manager: serdars
ms.date: 6/17/2021
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 
description: "Summary: View a high-level overview of the steps required to upgrade to Project Server Subscription Edition from Project Server 2016 or 2019."
---

# Overview of the Project Server Subscription Edition upgrade process
 
 **Summary:** View a high-level overview of the steps required to upgrade to Project Server Subscription Edition from Project Server 2016 or 2019.<br/>
<br/>**Applies to:** Project Server Subscription Edition
  
> [!NOTE]
> For information about planning consideration when upgrading to Project Server Subscription Edition, see [Plan for upgrade to Project Server Subscription Edition](plan-for-upgrade-to-project-server-2019.md). 
  
## Overview of the Project Server Subscription Edition upgrade steps

![Project Server Subscription Edition upgrade steps.](images/Update-for---Create-a-SharePoint-Server.png)
  
Upgrading to Project Server Subscription Edition can be broken up into four steps. These include:
  
1. Create the SharePoint Server Subscription Edition farm installation and enable Project Server Subscription Edition. Project Server Subscription Edition installs with SharePoint Server Subscription Edition and the Project Server service application needs to be started.
    
    > [!IMPORTANT]
    > Project Server Subscription Edition can only be enabled on the Enterprise version of SharePoint Server Subscription Edition. Project Server Subscription Edition cannot be enabled on SharePoint Server Subscription Edition with a Standard license. 
  
2. Copy and move your database from your Project Server 2016 or 2019 database server to the database server that hosts your Project Server Subscription Edition installation. This database is SharePoint 2016 or 2019 content database that contains your project site collections.
    
3. Use the [Mount-SPContentDatabase](/powershell/module/sharepoint-server/mount-spcontentdatabase?) PowerShell cmdlet to attach and upgrade the SharePoint 2016 or 2019 content database containing your Project site data to the Project Server Subscription Edition.
    
4. Use the [Test-SPContentDatabase](/powershell/module/sharepoint-server/test-spcontentdatabase?) PowerShell cmdlet to check your upgraded SharePoint content databases.
    
