---
title: "Default categories in Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 85b4f0f9-b310-4169-87aa-3da6312c8dd9
description: "Summary: Project Server 2013 default security categories are associated to default security groups, providing a different set of category permissions to each group."
---

# Default categories in Project Server 2013
 
 **Summary:** Project Server 2013 default security categories are associated to default security groups, providing a different set of category permissions to each group.
  
> [!IMPORTANT]
> The Project Server 2013 environment must be in Project Permission Mode in order to view categories, groups, and other security settings. For more information about Project Permission Mode, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
Project Server 2013 creates five default security categories during installation. Each of the categories is associated to default security groups. Some security groups are associated to multiple categories. Each category provides the associated security group category permissions that allow it to perform certain tasks with projects and resources for that category. This article describes the default settings for each category for Project Server 2013, including the following:
  
- [Category association to default security groups](#section1) Lists the default categories that are associated with each default security group.
    
- [Category permissions](#section2) Lists each category permission that is allowed for each security group, as defined by the default category that is associated with that group.
    
## Category association to default security groups
<a name="section1"> </a>

Specific default groups are already associated with each of the default categories. This means that users who are added to a specific default security group will automatically be allowed a specific set of permissions to work with the projects and resources that are associated with the category. 
  
> [!NOTE]
> For more information about the relationship between groups and categories, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md). 
  
**Categories associated with default security groups**

|**Category Name**|**Administrators**|**Portfolio Managers**|**Portfolio Viewers**|**Project Managers**|**Resource Managers**|**Team Leads**|**Team Members**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|My Direct Reports  <br/> ||||||||
|My Organization  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |×  <br/> |||
|My Projects  <br/> ||||×  <br/> |×  <br/> |×  <br/> ||
|My Resources  <br/> |||||×  <br/> |×  <br/> ||
|My Tasks  <br/> |||||||×  <br/> |
   
## Category permissions
<a name="section2"> </a>

The following table describes the default category permissions for each default group. For example, a user in the default Administrators group (who is associated to the My Organization category by default) has the permissions allowed in the Administrators column in the table. These category permissions only apply to all projects, resources, and views selected for the My Organization category. However, a user in the default Project Managers group (who is associated to the My Organization and My Projects categories) has a different set of category permissions for the objects in the My Organization category. This allows you to conveniently set a more or less restrictive set of permissions for different types of users to a group of projects, resources, and views. 
  
> [!NOTE]
> For more information about category permissions, see [Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md). For more information about how categories relate to groups, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md). 
  
Use the following legend for the table below.
  
- My Org = My Organization
    
- My Dir = My Direct Reports
    
- My Proj = My Projects
    
- My Res = My Resources
    
- My Tsks = My Tasks
    
**Category permissions for default categories**

|**Permission Name**|**Administrators**|**Portfolio Managers**|**Portfolio Viewers**|**Project Managers**|**Resource Managers**|**Team Leads**|**Team Members**|
|:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
|Accept Task Update Requests  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|Adjust Timesheet  <br/> |My Org  <br/> ||||My Org  <br/> |||
|Approve Timesheets  <br/> |My Org  <br/> |My Org  <br/> |||My Org, My Res  <br/> |||
|Assign Resource  <br/> |My Org  <br/> |My Org  <br/> ||My Org  <br/> |My Res  <br/> |||
|Build Team On Project  <br/> |My Org  <br/> |||My Proj  <br/> |My Org  <br/> |||
|Create Deliverable and Legacy Item Links  <br/> |My Org  <br/> |My Org  <br/> |My Org  <br/> |My Proj  <br/> |My Org, My Proj, My Res  <br/> |My Proj  <br/> |My Tsks  <br/> |
|Create New Task or Assignment  <br/> |My Org  <br/> |||My Proj  <br/> |My Proj  <br/> |My Proj  <br/> |My Tsks  <br/> |
|Delete Project  <br/> |My Org  <br/> |My Org  <br/> ||My Proj  <br/> ||||
|Edit Enterprise Resource Data  <br/> |My Org  <br/> |My Org  <br/> |||My Res  <br/> |||
|Edit Project Summary Fields  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|Manage Basic Project Security  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|Manage Resource Delegates  <br/> |My Org  <br/> ||||My Res  <br/> |||
|Manage Resource Plan  <br/> |My Org  <br/> |||My Org  <br/> |My Res  <br/> |||
|Open Project  <br/> |My Org  <br/> ||My Org  <br/> |My Proj  <br/> ||||
|Publish Project  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|Save Project to Project Server  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|Save Protected Baseline  <br/> |My Org  <br/> |||My Proj  <br/> ||||
|View Enterprise Resource Data  <br/> |My Org  <br/> |My Org  <br/> |My Org  <br/> |My Org, My Proj  <br/> |My Res  <br/> |||
|View Project Schedule in Project Web App  <br/> |My Or  <br/> |My Org  <br/> |My Org  <br/> |My Proj  <br/> ||My Proj  <br/> |My Tsks  <br/> |
|View Project Site  <br/> |My Org  <br/> |My Org  <br/> |My Org  <br/> |My Proj  <br/> |My Proj  <br/> |My Proj  <br/> |My Tsks  <br/> |
|View Project Summary in Project Center  <br/> |My Org  <br/> |My Org  <br/> |My Org  <br/> |My Proj  <br/> |My Proj  <br/> |My Proj  <br/> |My Tsks  <br/> |
|View Resource Assignments in Assignment Views  <br/> |My Org  <br/> |My Org  <br/> |My Org  <br/> |My Proj  <br/> |My Res  <br/> |My Proj  <br/> |My Tsks  <br/> |
   
## See also
<a name="section2"> </a>

#### 

[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md)
  
[Plan user access in Project Server](plan-user-access-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

