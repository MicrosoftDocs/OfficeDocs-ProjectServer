---
title: "Category permissions in Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.assetid: a9089d58-e1cd-4a86-b4dc-1575dc7988eb

description: "Summary: Project Server 2013 security categories have various permissions that allow or deny users the ability to do certain tasks with projects and resources."
---

# Category permissions in Project Server 2013
 
 **Summary:** Project Server 2013 security categories have various permissions that allow or deny users the ability to do certain tasks with projects and resources.
  
> [!IMPORTANT]
> The Project Server 2013 environment must be in Project Permission Mode in order to view category permissions and other security settings. For more information about Project Permission Mode, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
The following tables contain descriptions of all category permissions for Project Server 2013. The category permission descriptions are provided in two tables (Project and Resources), because category permissions apply to either projects or resources that are associated to a specific category. 
  
> [!NOTE]
> For information about different default security categories and their associated category permissions, see [Default categories in Project Server 2013](default-categories-in-project-server-2013.md). For more information about security categories and how they are used in the Project Server 2013 security model, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md). 
  
The table includes columns with the following information:
  
- **Description** Describes what the permission lets you do.
    
- **Dependencies** Lists any other permissions (global or category) or requirements to allow the permission to function.
    
- **New for Project Server 2013** Displays an **×** symbol if the permission is new for Project Server 2013.
    
**Category Permissions — Project**

|**Name**|**Description**|**Dependencies**|**New for Project Server 2013**|
|:-----|:-----|:-----|:-----|
|Accept Task Update Requests  <br/> |Allows a user to accept updates on projects without requiring that the user have the Save Project to Project Server permission.  <br/> |||
|Build Team On Project  <br/> |Allows a user to add resources to a project that has already been saved to the Project Server database. Grant this permission to project managers who want to use the Build Team feature in Project Professional to staff their projects before they save (and publish) them to the Project Server database. Or grant this permission to resource managers who want to use the Build Team feature in the Project Center of Project Web App to add resources to a project that has already been saved to the Project Server database.  <br/> | User must have the **View Enterprise Resource Data and Assign Resources** category permissions in order to see resources that are part of the Enterprise Resource Pool in the Build Team feature in Project Professional and Project Web App. <br/>  User must have permission (at the category level) to access the specific projects and resources that have to be accessed to build the project team or assign resources. <br/> ||
|Create Deliverable and Legacy Item Links  <br/> |Allows a user to create, modify, or delete links between Project tasks and items in the project site (documents, issues, deliverables, and risks).  <br/> ||X  <br/> |
|Create New Task or Assignment  <br/> |Determines which projects are available when you are creating new tasks. Grant this permission to any group of projects that individual users will be able to create new tasks in by using the Create a new task page in Project Web App.  <br/> |User must be granted the **New Task Assignment** global permission in order to access the New task page in Project Web App. <br/> ||
|Delete Project  <br/> |Allows users of Project Professional to delete a project saved to the Project Server database from the **Open from Microsoft Project Server** dialog box in Project Professional. Grant this permission to members of your organization to enable them to more closely manage the projects he or she has saved to the Project Server database from Project Professional or by using the "Delete Enterprise Objects" link in Project Web App. Before letting users delete projects, you should consider how your organization will recover those projects, if you have to do so. <br/> |||
|Edit Project Summary Fields  <br/> |Allows a user to edit only the enterprise project fields shown in the new project fields Web Part. If you do not have this permission, but have "Save Project to Project Server" you can still edit project-level fields/custom fields in the project field Web Part.  <br/> |||
|Manage Basic Project Security  <br/> |Controls whether a specific Project Permission can be set on a single project through the new Project Permissions feature.  <br/> |||
|Manage Resource Plan  <br/> |Allows a user to edit a resource plan.  <br/> |||
|Open Project  <br/> |Allows a user to open a project from the Project Server database in read-only mode by using Project Professional. Grant this permission to any member of your organization who has to use the **Open from Microsoft Project Server** dialog box in Project Professional or in the Project Center in Project Web App to open projects that have been saved to the Project Server database. If users are not assigned the **Save Project to Project Server** permission, then the project will only be open in read-only mode. <br/> |||
|Publish Project  <br/> |Allows a user to Publish projects to the ProjectServices database by using Project Professional and Project Web App. Grant this permission to all members of your organization who will be publishing projects.  <br/> |User must be granted the **Open Project** category permission on any project that has to be checked out from the Project Server database. If the project has changed since opening, the user will be required to have the **Save Project to Project Server** permission on that project. If not, when a publish occurs, it will only publish the outdated version. <br/> ||
|Save Project to Project Server  <br/> |Allows a user to save projects to the Project Server database by using Project Professional. Also gives Project Web App users the permission to save schedules and strategic impact data. Grant this permission to all members of your organization who will be saving projects from Project Professional to the Project Server database by using the **Save to Project Server** dialog box or through Server-side projects. <br/> | User must be granted the **New Project** permission in order to create the project. <br/>  User must be granted the **Open Project** category permission on any project that has to be checked out from the Project Server database. <br/> ||
|Save Protected Baseline  <br/> |Allows a user to save a protected baseline or clear a protected baseline associated with an enterprise project published to the Project Server database. Grant this permission to project managers who have to save baselines in their projects. Baselines are saved by using the Set Baseline functionality accessed from the Project Professional ribbon on the **Project** tab in the **Schedule** group. Click the **Set Baseline** button and then select **Save Baseline** or **Clear Baseline**. Protected Baselines are in the range of Baseline 0-5 inclusive. Only users who have Save Unprotected Baseline, Open Project and Save Project Category permissions are able to save Baselines in Baseline 6-10.  <br/> |User must be granted the **Save Project to Project Server** category permission. <br/> ||
|View Project Schedule in Project Web App  <br/> |Allows a user to view project information for a specific project from the Project Center in Project Web App. Grant this permission to users who have to view project details in the Project Center.  <br/> |||
|View Project Site  <br/> |Allows users to view Risks, Issues, and Documents areas in Project Web App and Project Professional. Grant this permission to any user of Project Professional who has to select Project site, Documents, Issues, or Risks from the Info page in the Backstage or any user of Project Web App who has to access the Project site, Documents, Issues, or Risks top-level navigation links.  <br/> |||
|View Project Summary in Project Center  <br/> |Allows a user to access a specific project in the Project Center from Project Web App. Grant this permission to any member of your organization who has to view projects summaries in the Project Center.  <br/> |||
   
**Category Permissions — Resource**

|**Name**|**Description**|**Dependencies**|**New for Project Server 2013**|
|:-----|:-----|:-----|:-----|
|Adjust Timesheet  <br/> |Allows a Project Web App user to adjust a team member's submitted timesheet entries. Grant this permission to any member of your organization who requires the ability to adjust a resource's timesheet entry after that resource has submitted the entry.  <br/> |User must have the **View Resource Timesheet** permission to use this permission. <br/> ||
|Approve Timesheets  <br/> |Allows a user to approve a team member's submitted timesheet entries. Grant this permission to any member of your organization who requires the ability to approve a resource's timesheet.  <br/> | User must have the **Approve Timesheets** permission through a category which contains the resources which they want to approve timesheets on. <br/> ||
|Assign Resources  <br/> |Allows a user to assign or allocate a given resource to projects. This permission controls the list of available resources in Team Builder in both Project Web App and Project Professional. Grant this permission to all project managers and resource managers who have to assign, manage, or allocate resources. For example, if you want to add resource R to project P, then you must have permission to assign resource R (Assign Resources) plus permission to build the team on Project P (Build Team on Project). In addition, you must have access to the Team Builder page through either Project Web App or Project Professional (Assign Resources to Project Team).  <br/> | User must have the **View Team Builder** global permission in order to use the Build Team page in Project Web App or Project Professional. <br/>  User must have the **Build Team on Project** category permission in order to assign a resource in an existing enterprise project. <br/>  User must have the **Build Team on New Project** global permission in order to assign a resource in a new enterprise project. <br/> ||
|Edit Enterprise Resource Data  <br/> |Allows a project manager to edit enterprise resource data by using Project Professional (checked-out Enterprise Resource Pool) or a resource manager to edit enterprise resources using Project Web App (Resource Center). Grant this permission to project managers and resource managers who have to make updates to resources that belong to the Enterprise Resource Pool. Resource managers with this permission are able to edit enterprise resource data in the Resource Center in Project Web App, and they can make updates to cost data, custom outline code data, custom field data, and other static information related to resources. Resource managers cannot add or delete resources from the Enterprise Resource Pool in Project Web App. Project managers can add or delete resources from the Enterprise Resource Pool in Project Professional if they have the **New Resource** global permission (to add resources) or the **Clean Up Project Server Database global** permission (to delete resources). These permissions are required in addition to the **Edit Enterprise Resource Data** category permission. <br/> > [!NOTE]> The Project Server Interface (PSI) can also be used to create or delete resources in the Enterprise Resource Pool and to edit enterprise resource data.           |User must be granted the **View Enterprise Resource Data** category permission. <br/> ||
|Manage Resource Delegates  <br/> |Allows a user to see other users whom he or she manages and to set delegates for them.  <br/> |||
|View Enterprise Resource Data  <br/> |Allows a user to view resources and resource data that is stored in the Enterprise Resource Pool. Grant this permission to any user who has to view resources and resource data that is stored in the Enterprise Resource Pool.  <br/> |||
|View Resource Assignments in Assignment Views  <br/> |Allows a user to view assignment details using assignment views in the Resource Center. Grant this permission to project managers and resource managers who have to view resource assignment details in the Resource Center from Project Professional or Project Web App.  <br/> |||
   
> [!NOTE]
> The "Create Object Link" permission is available in Project Server 2010, but is removed from Project Server 2013. 
  
## See also

[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Default categories in Project Server 2013](default-categories-in-project-server-2013.md)
  
[Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md)
  
[Plan user access in Project Server](plan-user-access-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

