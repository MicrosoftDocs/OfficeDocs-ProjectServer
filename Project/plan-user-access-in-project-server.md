---
title: Plan user access in Project Server
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 8/1/2017
audience: ITPro
ms.topic: conceptual
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 5228e0a7-3d7b-4cd9-8fc8-756caedce06d
description: Learn about the user access permission modes available in Project Web App.
---

# Plan user access in Project Server
 
 **Summary:** Learn about the user access permission modes available in Project Web App.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
Project Server offers two security modes for controlling the kind of access that users have to sites and projects:
  
- **SharePoint permission mode** In this mode, a special set of SharePoint security groups are created in sites associated with Project Server. These groups give users varying levels of access to projects and Project Server functionality.
    
- **Project permission mode** In this mode, Project Server provides customizable security groups and other functionality that is distinct from SharePoint groups.
    
In both security modes, the SharePoint site administrator for the Project Web App site is also a Project Web App administrator.
  
## What features are available in each Project Web App permission mode?

Use this table to compare the features available in each security mode.
  
**Comparison of features for security modes in Project Server**

|**Feature**|**SharePoint permission mode**|**Project Server permission mode**|
|:-----|:-----|:-----|
|Use a single set of security groups across Project Web App and SharePoint Server.  <br/> |×  <br/> ||
|Permissions inheritance for PWA and Project Sites  <br/> |×  <br/> ||
|Direct authorization against Active Directory security groups  <br/> |×  <br/> ||
|Claims-based authorization  <br/> |×  <br/> |×  <br/> |
|Manage authorization by role-based groups  <br/> |×  <br/> |×  <br/> |
|Extensible and customizable  <br/> |×  <br/> |×  <br/> |
|User delegation  <br/> ||×  <br/> |
|Ability to secure work resources  <br/> ||×  <br/> |
|Impersonation  <br/> ||×  <br/> |
|Security filtering using the Resource Breakdown Structure  <br/> ||×  <br/> |
|Custom Security Categories  <br/> ||×  <br/> |
   
When you've determined which permission mode you want to use, more information is available:
  
- For information about SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md).
    
- For information about Project Server permission mode, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md).
    
New Project Web App instances use the SharePoint permission mode by default. If you have more than one instance of Project Web App, each site can use a different permission mode.
  
## Changing Project Web App permission modes

In an on-premises installation of Project Server, the permission mode can be changed for a given instance of Project Web App by using the **Set-SPProjectPermissionMode** Microsoft PowerShell cmdlet. For more information, see [Set-SPProjectPermissionMode](/powershell/module/sharepoint-server/set-spprojectpermissionmode).
  
In Project Online, the mode can be changed in the Microsoft Office 365 portal site. For more information, see [Change permission management in Project Online](/projectonline/change-permission-management-in-project-online).
  
> [!CAUTION]
> Switching between SharePoint permission mode and Project Server permission mode deletes all security-related settings. If you switch from SharePoint permission mode to classic Project Server permission mode, you have to manually configure your security permissions structure in Project Server. Switching from Project Server permission mode back to SharePoint permission mode deletes your security permissions information from Project Server. 
