---
title: What's new for IT pros in Project Server Subscription Edition
ms.author: v-bshilpa
author: Benny-54
manager: serdars
ms.date: 6/18/2021
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 
description: Learn about Project Server Subscription Edition. Find information on the latest features and capabilities and get an overview of its new and updated functionality.
---

# What's new for IT pros in Project Server Subscription Edition 
  **Summary:** Learn about Project Server Subscription Edition. Find information on the latest features and capabilities and get an overview of its new and updated functionality.<br/>
**Applies to:** Project Server Subscription Edition 
  
This article provides a brief overview of new and significantly updated functionality in Project Server Subscription Edition, with a particular emphasis on the areas of interest to IT professionals. These include the following:
    
- [Base installation languages and language packs](new-features-capabilities-project-server-subscription-edition.md#Lang)
    
- [Hardware and software requirements](new-features-capabilities-project-server-subscription-edition.md#Req)
    
- [Upgrading to Project Server Subscription Edition Public Preview](new-features-capabilities-project-server-subscription-edition.md#Upgra)
    
- [Project Web App changes](new-features-capabilities-project-server-subscription-edition.md#PWAChanges)
    
   
## Base installation languages and language packs
<a name="Lang"> </a>

Now that both the Project Server Subscription Edition and SharePoint Server Subscription Edition are installed through a single installation, the base language is automatically matched for both. For example, when you install SharePoint Server Subscription Edition (English - US), the base installation language for both Project Server Subscription Edition and SharePoint Server Subscription Edition will be English - US. 
  
There is a special case in which the base installation language for SharePoint Server Subscription Edition and Project Server Subscription Edition does not match:
  
|**SharePoint Server Subscription Edition** <br/> |**Project Server Subscription Edition** <br/> |
|:-----|:-----|
|Thai  <br/> |English  <br/> |
   
**Language packs**
  
SharePoint Server Subscription Edition language packs will also match languages for both Project Server Subscription Edition and SharePoint Server Subscription Edition. Individual language packs for Project Server Subscription Edition are not available. 
  
Since Project Server Subscription Edition does not provide a matching language for all available SharePoint Server Subscription Edition language packs, an alternate language is provided. The following table lists SharePoint Server Subscription Edition language packs in which an alternate Project Server Subscription Edition language is provided.
  
|**SharePoint Server Subscription Edition language pack** <br/> |**Project Server Subscription Edition language** <br/> |
|:-----|:-----|
|Azeri (Latin)  <br/> |English  <br/> |
|Basque  <br/> |Spanish  <br/> |
|Bosnian  <br/> |English  <br/> |
|Bulgarian  <br/> |English  <br/> |
|Catalan  <br/> |Spanish  <br/> |
|Croatian  <br/> |English  <br/> |
|Estonian  <br/> |English  <br/> |
|Gaelic Irish  <br/> |English  <br/> |
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

Since Project Server Subscription Edition is now a service application in SharePoint Server Subscription Edition, the hardware, software, and browser requirements for Project Server Subscription Edition will be the ones specified for SharePoint Server Subscription Edition. Some notable requirements for this version are:
  
|**Software**|**Software requirements**|
|:-----|:-----|
|**Supported Server Operating Systems** **:** <br/> | Windows Server 2019 Standard or Datacenter <br/>Windows Server 2022 Standard or Datacenter <br/> |
|**Supported Database Server:** <br/> | Microsoft SQL Server 2019 RTM <br/>  SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server Subscription Edition. <br/> |
|**Supported browser's:** <br/> | Microsoft Edge <br/>  Microsoft Internet Explorer 11 <br/>Google Chrome (latest released version) <br/>  Mozilla Firefox (latest released version plus immediate previous version) <br/>  Apple Safari (latest released version) <br/> |
   
 **Project client compatibility**
You can connect to Project Server Subscription Edition with not only Project Professional 2021 and the Project Online Desktop Client, but also with Project Professional 2019. 
  
|**Version** <br/> |**Compatible with** <br/> |
|:-----|:-----|
|Project Server Subscription Edition  <br/> | Project Professional 2021  <br/>Project Professional 2019 <br/>  Project Online Desktop Client <br/> |
|Project Server 2019  <br/> | Project Professional 2019  <br/> Project Professional 2016 <br/> Project Online Desktop Client <br/> |
|Project Server 2016  <br/> | Project Professional 2019  <br/> Project Professional 2016 <br/> Project Online Desktop Client <br/>  Project Professional 2013 <br/> |
|Project Server 2013  <br/> | Project Professional 2016  <br/> Project Professional 2013 <br/> |
| |
   
> [!NOTE]
> Project Online Desktop Client connectivity to Project Server 2016 will no longer be supported after January 13, 2022. 
  
> [!NOTE]
> For more information about the hardware and software requirements for SharePoint Server Subscription Edition, see [Hardware and software requirements for SharePoint Server Subscription Edition](/sharepoint/install/hardware-and-software-requirements-2019). 
> For more information about supported browsers for SharePoint Server Subscription Edition, see [Plan browser support in SharePoint Server Subscription Edition](/sharepoint/install/browser-support-planning-2016-2019). 
  
## Upgrading to Project Server Subscription Edition 
<a name="Upgra"> </a>

When planning to upgrade to Project Server Subscription Edition take note of the following: 
  
- **Upgrade only through Project Server 2016 or 2019** - If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2016 or 2019 first in order to upgrade to Project Server Subscription Edition. There is no direct upgrade path from Project Server 2013 to Project Server Subscription Edition.
    
- **Project Web App site collection upgrade** - The SharePoint 2016 or 2019 content database that contains your PWA site collection needs to be upgraded as well during the upgrade process.
    
- **No in-place upgrade** - You must first create a Project Server Subscription Edition farm, and then attach and upgrade your Project Server 2016 or 2019 databases to the new farm. In-place upgrade is not supported.
    
- **Upgrade through Microsoft PowerShell** - Similar to the Project Server 2016 or 2019 upgrade experience, upgrading to Project Server Subscription Edition will be by using PowerShell cmdlets.
    
- **Migrate your Project Server Resource Plans** -  You can migrate your Project Server Resource Plans data to Resource Engagements in Project Server Subscription Edition. 
    
For more detailed information about the upgrade process, see [Upgrading to Project Server Subscription Edition](how-to-upgrade-project-server-subscription-edition.md).
     
## Project Web App changes
<a name="PWAChanges"> </a>
  
In Project Server Subscription Edition, there are no major features or enhancements. Note that there is a change to one feature used in Project Web App. This includes:
  
|**What's new**|**How do I do this?**|
|:-----|:-----|
|**Building cubes** - New software requirement <br/> | Use SQL Server Analysis Services AMO Client - 2019 <br/> |

## Known Issues
<a name="Issues"> </a>

There is a known issue in the Project Web App in RTM release. Users who aren't site admins can't attach issues, risks, or deliverables to tasks. Use the [SharePoint CSOM RelatedItemManager](/dotnet/api/microsoft.sharepoint.client.relateditemmanager) library as a workaround. The sample snippet below is an example.

```csharp
// Starting with ClientContext, the constructor requires a URL to the
// server running SharePoint.
ClientContext context = new ClientContext("https://{pwa_site_url}");

// Add credentials
string userName, passWord;
Console.WriteLine("Please enter your username for PWA");
userName = Console.ReadLine();
Console.WriteLine("Please enter your password for PWA");
passWord = Console.ReadLine();
context.Credentials = new NetworkCredential(userName, passWord);

// Add RelatedItem Issue/Risk to a task. Add the target item (issue/risk/etc) url to the pwa_connected_site url to create doc url of related item you want to add.
// For eg : Lists/Issues/1_.000 corresponds to the url for the first issue in Issues list.
// See <https://learn.microsoft.com/previous-versions/office/sharepoint-server/jj169493(v=office.15)> for AddSingleLinkToUrl method details.
RelatedItemManager.AddSingleLinkToUrl(context,"Tasks", 1, "<pwa_connected_site_relative_url>/Lists/Issues/1_.000", true);

// Execute the query to the server.
context.ExecuteQuery();
```

## See also
<a name="PWAChanges"> </a>

[New and improved features in SharePoint Server Subscription Edition](/sharepoint/what-s-new/new-and-improved-features-in-sharepoint-server-subscription-edition)
