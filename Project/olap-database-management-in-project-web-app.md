---
title: "OLAP database management in Project Web App"
ms.author: efrene
author: efrene
manager: gailmc
ms.date: 3/28/2016
ms.audience: ITPro
ms.topic: overview
ms.prod: project-server
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 3f3dabda-bb01-4af0-a18a-3d4563176651
description: "Summary: Use Project Web App to create OLAP databases containing the specific resources, projects, and custom fields that you need for reporting."
---

# OLAP database management in Project Web App
 
 **Summary:** Use Project Web App to create OLAP databases containing the specific resources, projects, and custom fields that you need for reporting.
  
Through Project Web App, multiple OLAP databases can be delivered that contain the specific resources, projects, and custom fields that each group within your organization requires for its particular group reporting needs.
  
In Project Web App, you can create multiple OLAP databases that have the following characteristics:
  
- They only contain data for projects and resources that they administer.
    
- They only contain facts and dimensions that they select from the new integrated OLAP database management user interface.
    
- They support departmental filtering to restrict which projects, custom fields, and resources are loaded into the OLAP database.
    
- They support selection of intrinsic measures for inclusion/exclusion. For example, you can remove fields that you may not use, such as baseline cost 7, to reduce data clutter.
    
- They include data for Inactive Tasks and User Scheduled Tasks.
    
- They let you choose whether to add Timephased/NonTimephased data.
    
- They have support for Multiple Measure groups in a single OLAP database.
    
- They contain field names in multiple languages to enable multi-language report creation.
    
Also, when a new OLAP database is created, the necessary Office Data Connections and Excel Reporting templates are created in the Business Intelligence Center in the Reports folder. This data-connected blank template will help you quickly create new reports that are based on the new OLAP database.
  
## Project Web App departments for filtering in project and resources

Both projects and resources can have departments. The main purpose of departments is to act as a filter for what custom fields are displayed to users within given areas of Project Professional 2016 and Project Web App. Departments allow for different business units to define and make visible their own set of custom fields. Departments are also used to filter OLAP databases so that only the data for that department is loaded.
  
When you configure a cube, you can specify both the project and resource departments so that the database data is filtered based on these criteria. These values are specified in the OLAP Database Build Settings page.
  
Also, within the OLAP database configuration, you can add the Project department field as a dimension to the Project and Tasks cubes. And you can add the Resource department field as a dimension to the Resource cube as long as the department field has not been converted to a multi-value field.
  
With Project Web App, departmental custom fields help relieve the problem of too much information and too many choices. Departments help you manage the custom field list, and help you define, at a resource, task, or project level, which fields are required or not required.
  
In Project Web App, fields can be globally scoped or they can be scoped to a specific department.
  
Departmental fields enable two primary functions:
  
- Filtering custom fields so that a user sees, by default, only those fields that are either global to the system or in the department that the user belongs to.
    
- Controlling which fields require input.
    
**Example of departments in use**

|**Field**|**Scope**|**Department**|**Required?**|
|:-----|:-----|:-----|:-----|
|ProjectCustomText1  <br/> |Global  <br/> |-  <br/> |No  <br/> |
|ProjectCustomText2  <br/> |Global  <br/> |-  <br/> |Yes  <br/> |
|ProjectCustomText3  <br/> |Department  <br/> |Marketing  <br/> |No  <br/> |
|ProjectCustomText4  <br/> |Department  <br/> |Marketing  <br/> |Yes  <br/> |
|ProjectCustomText5  <br/> |Department  <br/> |Development  <br/> |Yes  <br/> |
|ProjectCustomText6  <br/> |Department  <br/> |Development  <br/> |No  <br/> |
   
If John Woods belongs to the Development department, then when he views areas of the product that have departmental custom fields enabled, he sees the following:
  
- ProjectCustomText1
    
- ProjectCustomText2
    
- ProjectCustomText5
    
- ProjectCustomText6
    
John will be required to enter data into ProjectCustomText2 and ProjectCustomText5.
  
Cindy White belongs to the Marketing department. When she views areas of the product that have departmental custom fields enabled, she sees the following:
  
- ProjectCustomText1
    
- ProjectCustomText2
    
- ProjectCustomText3
    
- ProjectCustomText4
    
Cindy will be required to enter data into ProjectCustomText2 and ProjectCustomText4.
  
By default, departments filter the list of custom fields that John Woods and Cindy White see. But the filter does not prevent them from viewing custom fields assigned to the other departments.
  
Departmental fields are not tied into security. You cannot use them with security categories and groups to enable or disable fields and their functions. Instead, their main purpose is to filter out fields which are not useful for the target user.
  
**Department considerations for cubes**

|**Which cubes are filtered by which value**|**No project department specified**|**Project department specified**|
|:-----|:-----|:-----|
|No resource department specified  <br/> |All data is loaded for all cubes  <br/> |Project non-timephased cube  <br/> Task non-timephased cube  <br/> Issues cube  <br/> Risks cube  <br/> Deliverables cube  <br/> MSP_Project_WSS virtual cube  <br/> MSP_Project_Timesheet virtual cube  <br/> MSP_Portfolio_Analyzer virtual cube  <br/> Assignment non-timephased cube  <br/> Assignment timephased cube  <br/> EPM timesheet cube  <br/> |
|Resource department specified  <br/> |Assignment non-timephased cube  <br/> Assignment timephased cube  <br/> Resource non-timephased cube  <br/> Resource timephased cube  <br/> Timesheet cube  <br/> MSP_Project_Timesheet virtual cube  <br/> MSP_Portfolio_Analyzer virtual cube  <br/> | Filtered by Project Department: <br/>  Project non-timephased cube <br/>  Task non-timephased cube <br/>  Issues cube <br/>  Risks cube <br/>  Deliverables cube <br/>  MSP_Project_WSS virtual cube <br/>  Filtered by Resource &amp; Project Department: <br/>  Assignment non-timephased cube <br/>  Assignment timephased cube <br/>  EPM timesheet cube <br/>  MSP_Project_Timesheet virtual cube <br/>  MSP_Portfolio_Analyzer virtual cube <br/>  Filtered by Resource Department: <br/>  Resource no- timephased cube <br/>  Resource timephased cube <br/>  Timesheet cube <br/> |
   
Cubes include assignments for resources in projects that belong to other departments or to no department. This ensures that all data is present when examining data such as a department's resources full calendar capacity.
  
The subset of projects and resources will be used to filter at the project and timesheet level as follows:
  
Project non-timephased:
  
- The data in this cube will be filtered by the departmental project list.
    
- Projects with assignments to the department's resources will be included.
    
Task non-timephased:
  
- Non-departmental tasks with assignments to the department's resources will be included. The full non-departmental project will not be included.
    
- All tasks for departmental projects will be included.
    
Assignment non-timephased:
  
- Non-departmental project assignments for the department's resources will be included.
    
- All assignments for departmental projects will be included.
    
Assignment timephased:
  
- Non-departmental project assignments for the department's resources will be included.
    
- All assignments for departmental projects will be included.
    
Deliverables:
  
- All deliverables owned by the filtered list of projects will be included.
    
- All deliverables to which the filtered list subscribes and the projects/tasks that subscribe to the filtered list's deliverables will be included.
    
- All deliverables offered by non-departmental projects that are subscribed to by departmental projects will be included.
    
Issues:
  
- Issues connected to the filtered list of projects and tasks will be included.
    
Risks:
  
- Risks connected to the filtered list of projects and tasks will be included.
    
Resource non-timephased:
  
- Resources in the departmental list will be included.
    
Resource timephased:
  
- Resources in the departmental list will be included.
    
Timesheet:
  
- Timesheets for departmental list resources will be included.
    
EPM Timesheet:
  
- Timesheets for departmental list resources will be included.
    
- Task assignments from projects outside the department will be included.
    
Resources are described in three ways in the OLAP databases:
  
- Fact focus (timesheets, capacity)
    
- Associated with Facts (project task assignments)
    
- Owning Facts (project owner, issue owner, assignment owner)
    
The departmental resource list is used to filter facts with focus (Timesheets). Consequently, a non-departmental resource will never have any timesheets or capacity in the OLAP database if the database has a resource filter. However the non-departmental resource will be in the Resource List dimension if it has association with a departmental project, and will only have the relevant assignment facts.
  
Resources who own things that have separate dimensions (that is, Assignment Owner) do not have to be in the resource list. The Resource List dimension for a specific OLAP database contains:
  
- The departmental resources
    
- All resources with assignments to departmental projects
    
## See also

#### 

[Create OLAP cubes in Project Server 2016](create-olap-cubes-in-project-server-2016.md)
  
[Configure an OLAP cube in Project Server 2016](configure-an-olap-cube-in-project-server-2016.md)
  
[Copy OLAP cubes in Project Server 2016](copy-olap-cubes-in-project-server-2016.md)
  
[Delete OLAP cubes in Project Server 2016](delete-olap-cubes-in-project-server-2016.md)
  
[Build OLAP cubes in Project Server 2016](build-olap-cubes-in-project-server-2016.md)

