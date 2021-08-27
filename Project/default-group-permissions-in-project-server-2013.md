---
title: "Default group permissions in Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: c5f826df-9b39-4494-8b5e-173e0cf9fdde
description: "Summary: Project Server 2013 default security groups have defined global permissions to allow you to access and use features and functionality."
---

# Default group permissions in Project Server 2013
 
 **Summary:** Project Server 2013 default security groups have defined global permissions to allow you to access and use features and functionality.
  
> [!IMPORTANT]
> The Project Server 2013 environment must be in Project Permission Mode in order to view categories, groups, and other security settings. For more information about Project Permission Mode, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
This article describes the global permissions that are given to the default templates and security groups in Project Server 2013.
  
Project Server 2013 creates seven default groups during installation:
  
- Administrators 
    
- Portfolio Managers
    
- Portfolio Viewers 
    
- Project Managers 
    
- Resource Managers 
    
- Team Leads 
    
- Team Members 
    
Each group is given a default set of global permissions. Templates are also included to allow these default permissions to be assigned to new groups created by the administrator. After you use the template to create a new group, you can then choose to customize the new group to better suit your users by editing the permission for the group. 
  
Global permissions differ from category permissions in that they apply to functionality that the user is allowed to do throughout Project Server 2013. In order to work with specific projects or resources, users must have access to them through a category to which the project or resource is added. The users are only allowed to do tasks with these specific projects and resources through the category permissions defined in the category. For more detailed information about groups and categories, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md).
  
> [!NOTE]
> For information about the default categories that are associated to default security groups, as well their corresponding category permissions, see [Default categories in Project Server 2013](default-categories-in-project-server-2013.md). 
  
## Security group default global permissions
<a name="section2"> </a>

The following table contains a list of the default global permissions for each of the default security groups. 
  
**Default global permissions for Project Server security groups**

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
   
## See also
<a name="section2"> </a>

#### 

[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Default categories in Project Server 2013](default-categories-in-project-server-2013.md)
  
[Plan user access in Project Server](plan-user-access-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

