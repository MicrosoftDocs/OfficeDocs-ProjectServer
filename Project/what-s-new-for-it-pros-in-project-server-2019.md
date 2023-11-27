---
title: What's new for IT pros in Project Server 2019
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 7/24/2018
audience: ITPro
ms.topic: overview
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: c400e683-d9a0-4865-8859-0f566292af17
description: Learn about Project Server 2019. Find information on the latest features and capabilities and get an overview of its new and updated functionality.
---

# What's new for IT pros in Project Server 2019 
  **Summary:** Learn about Project Server 2019. Find information on the latest features and capabilities and get an overview of its new and updated functionality.<br/>
**Applies to:** Project Server 2019 
  
This article provides a brief overview of new and significantly updated functionality in Project Server 2019, with a particular emphasis on the areas of interest to IT professionals. These include the following:
  

    
- [Base installation languages and language packs](what-s-new-for-it-pros-in-project-server-2019.md#Lang)
    
- [Hardware and software requirements](what-s-new-for-it-pros-in-project-server-2019.md#Req)
    
- [Upgrading to Project Server 2019 Public Prevew ](what-s-new-for-it-pros-in-project-server-2019.md#Upgra)
    
- [Project Web App changes](what-s-new-for-it-pros-in-project-server-2019.md#PWAChanges)
    
   
## Base installation languages and language packs
<a name="Lang"> </a>

 Now that both the Project Server 2019 and SharePoint Server 2019 are installed through a single installation, the base language is automatically matched for both. For example, when you install SharePoint Server 2019 (English - US), the base installation language for both Project Server 2019 and SharePoint Server 2019 will be English - US. 
  
There is a special case in which the base installation language for SharePoint Server 2019 and Project Server 2019 do not match:
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**SharePoint Server 2019** <br/> |**Project Server 2019** <br/> |
|Thai  <br/> |English  <br/> |
   
 **Language packs**
  
SharePoint Server 2019 language packs will also match languages for both Project Server 2019 and SharePoint Server 2019. Individual language packs for Project Server 2019 are not available. 
  
Since Project Server 2019 does not provide a matching language for all available SharePoint Server 2019 language packs, an alternate language is provided. The following table lists SharePoint Server 2019 language packs in which an alternate Project Server 2019 language is provided.
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**SharePoint Server 2019 language pack** <br/> |**Project Server 2019 language** <br/> |
|Azerbaijani  <br/> |English  <br/> |
|Basque  <br/> |Spanish  <br/> |
|Bosnian  <br/> |English  <br/> |
|Bulgarian  <br/> |English  <br/> |
|Catalan  <br/> |Spanish  <br/> |
|Croatian  <br/> |English  <br/> |
|Dari  <br/> |English  <br/> |
|Estonian  <br/> |English  <br/> |
|Irish  <br/> |English  <br/> |
|Galician  <br/> |Spanish  <br/> |
|Hindi  <br/> |English  <br/> |
|Indonesian  <br/> |English  <br/> |
|Kazakh  <br/> |Russian  <br/> |
|Latvian  <br/> |English  <br/> |
|Lithuanian  <br/> |English  <br/> |
|Macedonian  <br/> |English  <br/> |
|Malay  <br/> |English  <br/> |
|Serbian (Latin)  <br/> |English  <br/> |
|Thai  <br/> |English  <br/> |
|Vietnamese  <br/> |English  <br/> |
|Welsh  <br/> |English  <br/> |
   
> [!NOTE]
> For more information about Project Online supported languages, see [Supported languages for Project Online](/ProjectOnline/supported-languages-for-project-online). 
  
## Hardware and software requirements
<a name="Req"> </a>

Since Project Server 2019 is now a service application in SharePoint Server 2019, the hardware, software, and browser requirements for Project Server 2019 will be the ones specified for SharePoint Server 2019. Some notable requirements for this version are:
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Supported Server Operating Systems** **:** <br/> | Windows Server 2016 Standard or Datacenter <br/>  Windows Server 2019 Standard or Datacenter <br/> |
|**Supported Database Server** **:** <br/> | Microsoft SQL Server 2016 Service Pack 1 (SP1) <br/>  Microsoft SQL Server 2017 RTM <br/>  SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server 2019 . <br/> |
|**Supported browser** **s:** <br/> | Microsoft Edge <br/>  Microsoft Internet Explorer 11 <br/>Google Chrome (latest released version) <br/>  Mozilla Firefox (latest released version plus immediate previous version) <br/>  Apple Safari (latest released version) <br/> |
   
 **Project client compatibility**
You can connect to Project Server 2019 with not only Project Professional 2019 and the Project Online Desktop Client, but also with Project Professional 2016. 
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Version** <br/> |**Compatible with** <br/> |
|Project Server 2019  <br/> | Project Professional 2019  <br/>Project Professional 2016 <br/>  Project Online Desktop Client <br/> |
|Project Server 2016  <br/> | Project Professional 2019  <br/>Project Professional 2016 <br/>  Project Online Desktop Client <br/>  Project Professional 2013 <br/> |
|Project Server 2013  <br/> | Project Professional 2016 <br/>  Project Professional 2013 <br/> |
| |
   
> [!NOTE]
> Project Online Desktop Client connectivity to Project Server 2013 will no longer be supported after January 13, 2020. 

  
> [!NOTE]
> For more information about the hardware and software requirements for SharePoint Server 2019, see [Hardware and software requirements for SharePoint Server 2019](/sharepoint/install/hardware-and-software-requirements-2019). > For more information about supported browsers for SharePoint Server 2019, see [Plan browser support in SharePoint Server 2019 ](/sharepoint/install/browser-support-planning-2016-2019). 
  
## Upgrading to Project Server 2019 
<a name="Upgra"> </a>

When planning to upgrade to Project Server 2019 take note of the following: 
  
- **Upgrade only through Project Server 2016** - If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2016 first in order to upgrade to Project Server 2019. There is no direct upgrade path from Project Server 2013 to Project Server 2019.
    
- **Project Web App site collection upgrade** - The SharePoint 2016 content database that contains your PWA site collection needs to be upgraded as well during the upgrade process.
    
- **No in-place upgrade** - You must first create a Project Server 2019 farm, and then attach and upgrade your Project Server 2016 databases to the new farm. In-place upgrade is not supported.
    
- **Upgrade through Microsoft PowerShell** - Similar to the Project Server 2016 upgrade experience, upgrading to Project Server 2019 will be through the use of PowerShell cmdlets.
    
- **Migrate your Project Server 2016 Resource Plans** -  You can migrate your Project Server 2016 Resource Plans to Resource Engagements in Project Server 2019. 
    
For more detailed information about the upgrade process, see [Upgrading to Project Server 2019](upgrading-to-project-server-2019.md).
  
  
   
## Project Web App changes
<a name="PWAChanges"> </a>

Administrators should know of a couple of big changes in Project Web App that affects your users:
  
 **New Timeline options**
  
In Project Server 2019, in addition to performance improvements as well as accessibility improvements, note that there are several changes to the different features used in Project Web App. These include:
  
|**What's new**|**How do I do this?**|
|:-----|:-----|
|**Team task enhancements** - New way of working with task assignments <br/> |[New ways to work with Team Assignments](https://blogs.technet.microsoft.com/projectsupport/2016/12/02/project-online-new-ways-to-work-with-team-assignments/) <br/> |
|**Timephased reporting data** - Project admins can configure to roll up timephased reporting data to different levels of granularity. <br/> |[Configure rollup of timephased reporting data ](https://support.office.com/en-us/article/Configure-rollup-of-timephased-reporting-data-in-Project-Online-da8487fe-899e-4510-a264-e2ebc948928c?ui=en-US&rs=en-US&ad=US) <br/> |
|**Email notifications** - Project admins have more options on how they want to receive email. <br/> |[Email notifications ](https://www.microsoft.com/en-us/microsoft-365/blog/2015/12/03/3-new-enhancements-to-project-online/?eu=true) <br/> |
|**Project IDs** - Creates unique Project IDs on project creation. <br/> |[Project IDs ](https://www.microsoft.com/en-us/microsoft-365/blog/2015/12/03/3-new-enhancements-to-project-online/?eu=true) <br/> |
|**Increasing custom field limits for reporting** <br/> |[Increasing custom field limits for reporting ](https://www.microsoft.com/en-us/microsoft-365/blog/2015/12/03/3-new-enhancements-to-project-online/?eu=true) <br/> |
|**Resource Engagement API’s** - Able to take advantage of the API for Resource Engagment <br/> |[Resource Engagement API’s](https://blogs.msdn.microsoft.com/brismith/2016/07/13/resource-engagement-apis-coming-to-a-project-online-near-you/) <br/> |

   
  
## See also
<a name="PWAChanges"> </a>

[New and improved features in SharePoint Server 2019 ](/SharePoint/what-s-new/new-and-improved-features-in-sharepoint-server-2019)
