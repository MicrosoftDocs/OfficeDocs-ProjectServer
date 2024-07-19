---
title: "SharePoint Permissions Mode default permissions for Project Server 2013 SharePoint groups"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: a267cbc9-16ad-4102-979d-8cb5291ec3a3
description: "Summary: Learn about the corresponding Project Server permissions that SharePoint groups receive in SharePoint Permission Mode in Project Server 2013."
---

# SharePoint Permissions Mode default permissions for Project Server 2013 SharePoint groups
 
 **Summary:** Learn about the corresponding Project Server permissions that SharePoint groups receive in SharePoint Permission Mode in Project Server 2013.
  
SharePoint Permission Mode creates SharePoint groups that directly correspond to the default security groups found in Project Permission Mode. These default security groups include the following: 
  
- Administrator
    
- Portfolio Managers
    
- Portfolio Viewers
    
- Project Managers
    
- Resource Managers
    
- Team Leads
    
- Team Members
    
Users in these SharePoint groups have the same global and category permissions that are assigned to them in Project Permission Mode in Project Server 2013 For example, the Project Managers SharePoint group in SharePoint Permission Mode receive all allowed global and category permissions that the Project Managers default security group has in Project Server 2013 in Project Permission Mode.
  
> [!IMPORTANT]
> In SharePoint Permission Mode, you cannot edit the default permissions assigned to any of these SharePoint groups. Also, you cannot create additional custom groups, categories, Resource Breakdown Structure (RBS) nodes, or edit the default permissions assigned to any of these objects. If you need more management of your user permissions in Project Server 2013, you can change to Project Permission Mode. For more information about the differences between the two security modes available to you in Project Server 2013, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
> [!NOTE]
> For more information about SharePoint groups in SharePoint Permission Mode for Project Server 2013, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md). 
  
## Permissions for SharePoint groups in Project Server 2013

This section provides a list of permissions allowed for each SharePoint group in SharePoint Permission Mode in Project Server 2013. Note that there are two different types of permissions for Project Server 2013 users.
  
- **Global permissions**: Allow users to use and access sites and features in Project Server 2013.
    
- **Category permissions**: Allows users to do tasks with project, resources, and views in Project Server 2013.
    
> [!NOTE]
>  For descriptions of Project Server 2013 global and category permissions, see the following articles:> [Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)> [Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
**Global permissions for SharePoint groups in SharePoint Permission Mode**

|**Permission Name**|**Administrators**|**Portfolio Managers**|**Portfolio Viewers**|**Project Managers**|**Resource Managers**|**Team Leads**|**Team Members**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Access Project Server Reporting Service  <br/> |×  <br/> |×  <br/> |×  <br/> |||||
|Build Team On New Project  <br/> |×  <br/> |×  <br/> ||×  <br/> |×  <br/> |||
|Can Be Delegate  <br/> |×  <br/> |||||||
|Change Workflow  <br/> |×  <br/> |||||||
|Clean Up Project Server Database  <br/> |×  <br/> |||||||
|Contribute to Project Web App  <br/> |×  <br/> ||||×  <br/> |×  <br/> |×  <br/> |
|Edit Status Report Requests  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||
|Log On  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|Log on to Project Server from Project Professional  <br/> |×  <br/> |×  <br/> ||×  <br/> |×  <br/> |||
|Manage Active Directory Settings  <br/> |×  <br/> |||||||
|Manage Check-Ins  <br/> |×  <br/> |×  <br/> ||||||
|Manage Cube Building Service  <br/> |×  <br/> |×  <br/> ||||||
|Manage Drivers  <br/> |×  <br/> |×  <br/> |×  <br/> |||||
|Manage Enterprise Calendars  <br/> |×  <br/> |×  <br/> ||||||
|Manage Enterprise Custom Fields  <br/> |×  <br/> |×  <br/> ||||||
|Manage Exchange Integration  <br/> |×  <br/> |||||||
|Manage Gantt Chart and Grouping Formats  <br/> |×  <br/> |||||||
|Manage Lists in Project Web App  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||||
|Manage My Delegates  <br/> |×  <br/> ||||×  <br/> |||
|Manage My Resource Delegates  <br/> |×  <br/> ||||×  <br/> |||
|Manage Notification and Reminders  <br/> |×  <br/> |||||||
|Manage Personal Notifications  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|Manage Portfolio Analyses  <br/> |×  <br/> |×  <br/> |×  <br/> |||||
|Manage Prioritizations  <br/> |×  <br/> |×  <br/> |×  <br/> |||||
|Manage Project Server Backup  <br/> |×  <br/> |||||||
|Manage Project Server Restore  <br/> |×  <br/> |||||||
|Manage Project Web App Views  <br/> |×  <br/> |×  <br/> ||||||
|Manage Queue  <br/> |×  <br/> |||||||
|Manage Resource Notifications  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||
|Manage Rules  <br/> |×  <br/> |||×  <br/> ||||
|Manage Security  <br/> |×  <br/> |||||||
|Manage Server Configuration  <br/> |×  <br/> |||||||
|Manage Server Events  <br/> |×  <br/> |||||||
|Manage SharePoint Foundation  <br/> |×  <br/> |||||||
|Manage Time Reporting and Financial Periods  <br/> |×  <br/> |||||||
|Manage Time Tracking  <br/> |×  <br/> |||||||
|Manage Users and Groups  <br/> |×  <br/> |||||||
|Manage Workflow Project Detail Pages  <br/> |×  <br/> |||||||
|New Project  <br/> |×  <br/> |×  <br/> ||×  <br/> ||||
|New Resource  <br/> |×  <br/> |×  <br/> |||×  <br/> |||
|New Task Assignment  <br/> |×  <br/> |||×  <br/> ||×  <br/> |×  <br/> |
|Open Project Template  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||||
|Reassign Task  <br/> |×  <br/> |||×  <br/> |||×  <br/> |
|Save Enterprise Global  <br/> |×  <br/> |×  <br/> |×  <br/> |||||
|Save Project Template  <br/> |×  <br/> |×  <br/> ||×  <br/> ||||
|Save Unprotected Baseline  <br/> |×  <br/> |||×  <br/> ||||
|Self-assign Team Tasks  <br/> |×  <br/> |||×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|Status Broker Permission  <br/> |×  <br/> |||||||
|View Approvals  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Business Intelligence Link  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||||
|View OLAP Data  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||||
|View Project Center  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Project Schedule Views  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Project Timesheet Line Approvals  <br/> |×  <br/> |||×  <br/> ||||
|View Resource Availability  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |||
|View Resource Center  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |||
|View Resource Plan  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |||
|View Resource Timesheet  <br/> |×  <br/> |||||||
|View Task Center  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Team Builder  <br/> |×  <br/> |×  <br/> ||×  <br/> |×  <br/> |||
|View Timesheets  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
   
**Category permissions for SharePoint groups in SharePoint Permission Mode**

|**Permission Name**|**Administrators**|**Portfolio Managers**|**Portfolio Viewers**|**Project Managers**|**Resource Managers**|**Team Leads**|**Team Members**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Accept Task Update Requests  <br/> |×  <br/> |||×  <br/> ||||
|Adjust Timesheet  <br/> |×  <br/> ||||×  <br/> |||
|Approve Timesheets  <br/> |×  <br/> |×  <br/> |||×  <br/> |||
|Assign Resource  <br/> |×  <br/> |×  <br/> ||×  <br/> |×  <br/> |||
|Build Team On Project  <br/> |×  <br/> |||×  <br/> |×  <br/> |||
|Create Deliverable and Legacy Item Links  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|Create New Task or Assignment  <br/> |×  <br/> |||×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|Delete Project  <br/> |×  <br/> |×  <br/> ||×  <br/> ||||
|Edit Enterprise Resource Data  <br/> |×  <br/> |×  <br/> |||×  <br/> |||
|Edit Project Summary Fields  <br/> |×  <br/> |||×  <br/> ||||
|Manage Basic Project Security  <br/> |×  <br/> |||×  <br/> ||||
|Manage Resource Delegates  <br/> |×  <br/> ||||×  <br/> |||
|Manage Resource Plan  <br/> |×  <br/> |||×  <br/> |×  <br/> |||
|Open Project  <br/> |×  <br/> ||×  <br/> |×  <br/> ||||
|Publish Project  <br/> |×  <br/> |||×  <br/> ||||
|Save Project to Project Server  <br/> |×  <br/> |||×  <br/> ||||
|Save Protected Baseline  <br/> |×  <br/> |||×  <br/> ||||
|View Enterprise Resource Data  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |||
|View Project Schedule in Project Web App  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> ||×  <br/> |×  <br/> |
|View Project Site  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Project Summary in Project Center  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
|View Resource Assignments in Assignment Views  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |
   

