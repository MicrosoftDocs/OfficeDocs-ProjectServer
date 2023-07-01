---
title: "Plan SharePoint groups in Project Server"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 7/31/2017
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 324bb8cc-6ffc-4598-8b41-ea9980487dbe
description: "Summary: Plan users and groups for Project Server in SharePoint permission mode."
---

# Plan SharePoint groups in Project Server

**Summary:** Plan users and groups for Project Server in SharePoint permission mode.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
SharePoint permissions mode creates SharePoint groups that directly correspond to the default security groups found in Project Server permission mode.
  
The following table describes the Project Server SharePoint groups and what user functionality they enable in Project Web App.
  
|**SharePoint group**|**Function**|
|:-----|:-----|
|Administrators  <br/> |Users have all global permissions as well as category permissions through the My Organization category. This allows them complete access to everything in Project Web App.  <br/> |
|Portfolio Viewers  <br/> |Users have permissions to view Project and Project Web App data. This group is intended for high-level users who need visibility into projects but are not themselves assigned project tasks.  <br/> |
|Project Managers  <br/> |Users have permissions to create and manage projects. This group is intended for project owners who assign tasks to resources.  <br/> |
|Portfolio Managers  <br/> |Users have assorted project-creation and team-building permissions. This group is intended for high-level managers of groups of projects.  <br/> |
|Resource Managers  <br/> |Users have most global and category-level resource permissions. This group is intended for users who manage and assign resources and edit resource data.  <br/> |
|Team Leads  <br/> |Users have limited permissions around task creation and status reports. This group is intended for persons in a lead capacity that do not have regular assignments on a project.  <br/> |
|Team Members  <br/> |Users have general permissions for using Project Web App, but limited project-level permissions. This group is intended to give everyone basic access to Project Web App.  <br/> |
   
These Project Server SharePoint groups have the same global and category permissions that are assigned to them in Project Server permission mode. In SharePoint permissions mode, you cannot create additional custom groups, categories, Resource Breakdown Structure (RBS) nodes, or edit the default permissions assigned to any of these objects.
  
## Adding users to Project Web App in SharePoint permission mode

There are two methods of adding users to the SharePoint groups:
  
- Add user accounts individually
    
- Add one or more Active Directory groups
    
You can use one or both of these methods for each group.
  
For information on how to add users and Active Directory groups to SharePoint groups, see [Share a site](https://office.microsoft.com/en-us/sharepoint-help/share-a-site-HA103456668.aspx).
  
### Adding individual users to SharePoint groups

When you add individual users to one of the SharePoint groups, that user is synchronized to Project Web App automatically. User synchronization runs on a SharePoint timer job, by default every ten minutes.
  
### Using Active Directory groups to add users to SharePoint groups

When you add Active Directory groups to one of the Project Server-specific SharePoint security groups, the users are not automatically added to the list of users in Project Web App. Each user is individually added to Project Web App the first time she or he accesses the Project Web App site. 
  
Because users in Active Directory groups do not appear on the list of Project Web App resources until they have accessed the Project Web App site, we recommend that you configure Active Directory synchronization in Project Web App to prepopulate your resource list. This allows you to have a complete resource list and to assign work to resources before they have accessed the Project Web App site.
  
## See also

[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
