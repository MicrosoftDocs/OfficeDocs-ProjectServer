---
title: "Global permissions in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: b1a7f8a5-1530-4a57-b061-3fdd914bb6b5

description: "Summary: Project Server 2013 users are allowed access to features and functionality through global permissions."
---

# Global permissions in Project Server 2013
 
 **Summary:** Project Server 2013 users are allowed access to features and functionality through global permissions.
  
> [!IMPORTANT]
> The Project Server 2013 environment must be in Project Permission Mode in order for you to view global permissions and other security settings. For more information about Project Permission Mode, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
The following is a list of global permissions for Project Server 2013. The columns in the table include the following:
  
- **Description** Describes what the permission enables you to do.
    
- **Dependencies** Lists any other permissions (global or category) or requirements necessary for the permission to function.
    
- **New for Project Server 2013** Displays an × symbol if the permission is new for Project Server 2013.
    
> [!NOTE]
> For more information about how global permission work in the Project Server 2013 security model, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md). 
  
|**Permission**|**Description**|**Dependencies**|**New for Project Server 2013**|
|:-----|:-----|:-----|:-----|
|Access Project Server Reporting Service  <br/> |Allows a user to access the OData web service for retrieving data from Project Server.  <br/> ||×  <br/> |
|Build Team On New Project  <br/> |Allows a user to add resources to a project that has not been saved to Project Server. Grant this permission to project managers who want to use the Build Team feature in Project Professional 2013 to staff their projects before they save (and publish) them to Project Server.  <br/> |User has to be granted the **Assign Resources** and **View Enterprise Resource Data** category permissions in order to see resources that are part of the Enterprise Resource Pool in the Build Team feature in Project Professional. <br/> ||
|Can be Delegate  <br/> |Specifies whether a user can be a delegate.  <br/> |||
|Change Workflow  <br/> |Allows a user to change a project's Enterprise Project type. (Change Project Type).  <br/> |||
|Clean up Project Server database  <br/> |Allows a user to access the Delete Enterprise Objects page available through the Server Settings page in Project Web App. Grant this permission to users who have to delete timesheets, status reports responses, projects, resources, users, and user delegates from Project Server.  <br/> |||
|Contribute to Project Web App  <br/> |Allows users to edit items within lists in Project Web App project sites.  <br/> |||
|Edit Status Report Requests  <br/> |Allows a user to access the Request a status report link on the Project Web App Status Reports center and to view team reports. Grant this permission to any member of your organization who has to create status report requests and view team reports, usually project managers, resource managers, team leads, and members of your organization's PMO.  <br/> |||
|Log on  <br/> |Allows a user to connect to Project Server from Project Professional or to log on to Project Web App. Grant this permission to any user who is authorized to connect to Project Server from Project Professional or log on to Project Web App.  <br/> |||
|Log on to Project Server from Project Professional  <br/> |Allows a user to load the Enterprise Global Template when he or she connects Project Professional to Project Server. Grant this permission to all users in your organization who will be using Project Professional to connect to Project Server.  <br/> |||
|Manage Active Directory Settings  <br/> | Allows users to modify any Active Directory Synchronization settings within the Project Web App Project Server Settings. If the user is denied this permission then they cannot modify settings for any of the following: <br/>  Enterprise Resource Pool synchronization settings. <br/>  Project Web App Security Groups synchronization settings. <br/>  Choose an Active Directory Group to synchronize against a specific Security Group within the Add or Edit Group page. <br/> |||
|Manage Check-Ins  <br/> |Allows a user to access the Forced Check-in Enterprise Objects page in Project Web App. This page lets users force check-in projects, resources, custom fields, calendars, lookup tables and resource plans.  <br/> |||
|Manage Cube Building Service  <br/> |Allows a user to the set and modify the settings for OLAP cube creation.  <br/> |||
|Manage Drivers  <br/> |Allows a user to access the drivers.aspx page and manage business drivers for project portfolio analysis.  <br/> |||
|Manage Enterprise Calendars  <br/> |Allows a user to create, modify, and delete Enterprise Calendars within Project Web App.  <br/> |||
|Manage Enterprise Custom Fields  <br/> |Allows a user to modify the definitions of Enterprise Custom Fields and lookup table from Project Web App.  <br/> |||
|Manage Exchange Integration  <br/> |Allows administrators to enable the synchronization of project tasks with Exchange Server.  <br/> |||
|Manage Gantt Chart and Grouping Formats  <br/> |Allows a user to access the Gantt chart and grouping formats customization options in the Project Server Administration page for Project Web App views.  <br/> |||
|Manage Lists in Project Web App  <br/> |Allows a user to create, modify, and delete lists within the Project Web App project site. This permission is used when you synchronize a user against the Project Web App project site.  <br/> |||
|Manage Notification and Reminders  <br/> |Allows a user to manage the Notification and Reminders settings.  <br/> |||
|Manage My Delegates  <br/> |Allows users to see the "Manage Delegates" link and to set a delegate on the "Add/Modify Delegation" page.  <br/> |||
|Manage My Resource Delegates  <br/> |Allows users to set a user who requires a substitute on the Add/Modify Delegation page.  <br/> |||
|Manage Personal Notifications  <br/> |Allows a user to access the Manage My Alerts and Reminders page in Project Web App. Grant this permission to any user that you want to be able to sign up for e-mail notifications and reminders related to tasks and status reports.  <br/> |||
|Manage Portfolio Analyses  <br/> |Allows a user to create, read, update, and delete Portfolio analyses.  <br/> |||
|Manage Prioritizations  <br/> |Allows a user to create, read, update, and delete driver prioritizations.  <br/> |||
|Manage Project Web App Views  <br/> |Allows a user to access the Manage Views page in the Server Settings page in Project Web App. Users with permission to access this page are able to add, modify, or delete Project, Project Center, Resource Center, Assignment, or Portfolio Analyzer views, and they are able to modify Timesheet views. Grant this permission to project managers, resource managers, and members of your organization's PMO so that they can create project data views for users to access in Project Web App and Project Professional. It is important to remember that if your organization is allowing project managers to create custom fields at the project level, then each project may require its own unique view. The number of projects in this kind of environment may be too many for the IT administrator team. Offloading this work to the people in your organization that work at the project level on a day-to-day basis is one way to distribute the workload of managing views.  <br/> |||
|Manage Queue  <br/> |Allows the user to read or set queue configuration settings and retry, cancel, and unblock jobs in the queue.  <br/> |||
|Manage Resource Notifications  <br/> |Allows a user to access the "Alert me about my resources on tasks and status reports" link on the Project Web App home page. Grant this permission to any resource manager or project manager that you want to be able to sign up for email notifications and reminders related to their resources' tasks and status reports.  <br/> |||
|Manage Rules  <br/> |Allows a user to access the Rules page from the Approval Center in Project Web App and set rules on how update transactions will be automatically processed. Grant this permission to project managers, resource managers, or members of your organization's PMO so that they can define how they will automatically receive and accept changes to transactions by their resources.  <br/> |||
|Manage security  <br/> |Allows a user to access the Manage security page in Project Web App to define security categories, security templates, and user authentication settings. Grant this permission to Project Server administrators or a very small and closely managed group of people. This page lets users change Project Server security settings, and create security categories and security templates. Changes to settings on this page, after you have begun using Project Server in your organization, should be carefully managed and (ideally) infrequent.  <br/> |||
|Manage Server Events  <br/> |Allows a user to register event handlers for specific Project Server server-side events. The Manager Server Events page requires the event handler to be registered by the server as defined in the Project Server SDK.  <br/> |||
|Manage Server Configuration  <br/> |Allows a user to access the Project Web App Permissions page in Project Web App. Users with permission to access the Project Web App Permissions page can enable or disable enterprise features, manage organizational permissions, and create custom menus (both top-level and side-pane) in Project Web App. Grant this permission to Project Server administrators or a very small and closely managed group of people.  <br/> |||
|Manage SharePoint Foundation  <br/> |Allows a user to create and delete project sites, configure automatic project site creation for newly published projects, configure permission synchronization settings, and update site path. Grant this permission to members of your organization who are administrators for Project Web App or administrators for the servers that are running SharePoint Server 2013.  <br/> |Users with this permission should be granted administrative privileges to all of the servers that are running Project Server 2013 and SharePoint Server 2013  <br/> ||
|Manage Time Reporting and Financial Periods  <br/> |Allows a user to create and modify Timesheet and Fiscal period definitions.  <br/> |||
|Manage Time Tracking  <br/> | Allows a user to be forwarded timesheets for review. After reviewing the timesheet, the user must be granted the following permissions to accept and approve the timesheet: <br/>  Accept Timesheet <br/>  Approve Timesheet <br/> |||
|Manage Users and Groups  <br/> |Allows a user to access the Manage Users and Groups page in the Server Settings page in Project Web App. Users with this permission will be able to add, modify, or delete Project Server users and manage Project Server security groups. Grant this permission to members of your organization who are Project Server administrators. Only a small group of people should have permission to access this set of pages.  <br/> |||
|Manage Workflow and Project Detail Pages  <br/> |Allows a user to manage and view workflow and Project Detail Pages (PDPs).  <br/> |||
|New Project  <br/> |Allows a user to add a new project to Project Server using Project Professional, Project Web App, or the Project Server Interface (PSI). New functionality in Project Server 2013 for this permission: If you do not also have the Open Project permission, after you create a project, you are taken back to the Project Center.  <br/> |||
|New Resource  <br/> |Allows a project manager to add new resources to the Enterprise Resource Pool using Project Professional, the Project Web App Resource Center, or the Project Server Interface (PSI). Grant this permission to any member of your organization who has to create new enterprise resources in Project Server.  <br/> > [!NOTE]> If your organization is using the Active Directory synchronization feature, you may want to consider denying this permission to all non-IT administrators in your organization.           |||
|New Task Assignment  <br/> |Allows users to access the Create a New Task and Add Yourself to a Task links from the Insert Row button found on the Tasks page of Project Web App. Grant this permission to any member of your organization who has to create new assignments on existing tasks in projects that have been published to Project Server. Users with this permission will also be able to use the Create a New Task link to create new tasks in Project Web App for any project to which the user has access. The list of available projects for a user to create new tasks is determined by the Create New Tasks or Assignment category permission. A user who has the New Task Assignment permission must also have access to the projects to which they want to assign themselves to a task.  <br/> |||
|Open Project Template  <br/> |Allows a user to open an Enterprise Project Template from Project Server by using Project Professional. Grant this permission to all users in your organization who will use Project Professional to create and manage projects that are based on Enterprise Project Templates.  <br/> |User must be granted the **New Project** global permission in order to save the project to the Project Server database as an actual project. <br/> ||
|Reassign Task  <br/> |Allows a user to delegate an assigned task to another (existing) user. Grant this permission to members of your organization who need the ability to delegate task assignments to other resources. For example, a large project may be run by a single project manager, but actually implemented by several teams, each with its own team lead. A project manager could assign the team leads in the project plan, and then the team leads could in turn delegate each task to individual members of the teams. This example creates an additional layer of task management within the larger organization, but it can also simplify resource allocation within projects themselves and make it easier for a project manager to manage large projects. Or, if you have a resource that is about to leave on a three-week vacation, and this resource had this permission, that person would be able to assign his or her tasks directly to other resources instead of having the project manager check out the project and reassign resources.  <br/> |||
|Save Enterprise Global  <br/> |Allows a user to check out, modify, and save the Enterprise Global Template to the Project Server database from Project Professional. This permission should only be granted to a small group of people in your organization; either project managers, members of your organization's PMO, or Project Server administrators.  <br/> |||
|Save Project Template  <br/> |Allows a user to create and save a project as an Enterprise Project Template from Project Professional to the Project Server database. Grant this permission to members of your organization who are tasked with creating Enterprise Project Templates. When a user saves a project to Project Server for the first time, the option to select Template (as opposed to Project) from the Type drop-down list in the **Save to Project Server** dialog box is enabled. <br/> |User needs to be granted the **Assign Resources** and **View Enterprise Resource Data** category permissions in addition to this permission if they are also responsible for adding Generic resources to the Enterprise Project Template. <br/> ||
|Save Unprotected Baseline  <br/> |Allows a user to save a non-protected baseline or clear a non-protected baseline associated with an enterprise project published to the Project Server database. Baselines are saved by using the Set Baseline functionality accessed from the Project Professional ribbon on the **Project** tab in the **Schedule** group. Click the **Set Baseline** button and then select **Save Baseline** or **Clear Baseline**. Unprotected Baselines are in the range of Baseline 6-10 inclusive.  <br/> |User needs to be granted the **Save Project** category permission. <br/> ||
|Self-Assign Team Tasks  <br/> |Resources can be members of a Team Assignment Pool. With this permission, it is possible for users to assign tasks, which have been assigned to their Team Assignment Pool, to themselves through the Team Tasks page in Project Web App.  <br/> |||
|Status Broker Permission  <br/> |Allows API updates to occur for a user from places like Exchange Server.  <br/> |||
|View Approvals  <br/> |Allows a user to view the Approval Center.  <br/> | Users have access to the Approval Center if they have either the Accept Timesheets or the View Approvals permission. <br/> ||
|View Business Intelligence Link  <br/> |Allows a user to see the Business Intelligence link in Quick Launch. However, it has no effect on Report Center Security.  <br/> |||
|View OLAP Data  <br/> |Allows a user to read from the output for the OLAP cube. This permission is only checked when the OLAP cube is built.  <br/> |||
|View Project Center  <br/> |Allows users to access the Project Center from Project Web App or Project Professional.  <br/> |User needs to be granted the **View Project Summary in Project Center** category permission. <br/> ||
|View Project Schedule Views  <br/> |Allows a user to see the link in the Quick Launch. However, it has no effect on Report Center Security.  <br/> |||
|View Project Timesheet Line Approvals  <br/> |Allows a user to approve timesheets on a line-by-line basis.  <br/> |||
|View Resource Availability  <br/> |Allows a user to access the View Resource Availability page to view resource allocation data in Project Web App. Grant this permission to users in your organization who need to view resource availability in Project Web App.  <br/> |||
|View Resource Center  <br/> |Allows users to access the Resource Center from Project Web App or Project Professional and view resource allocation data. Grant this permission to users who need to view the Resource Center in Project Web App by clicking the Resources link in the top-level navigation, or in Project Professional by selecting Resource Center on the Collaborate menu.  <br/> |User needs to be granted the **View Enterprise Resource Data** category permission. <br/> ||
|View Resource Plan  <br/> |Allows a user to access the Resource Plan page within Project Web App.  <br/> |||
|View Resource Timesheet  <br/> |Allows users to view the timesheets, regardless of their state or ownership, for resources identified in the category selection criteria.  <br/> |Users must be granted the **Accept Timesheet** global permission to use this permission. <br/> ||
|View Task Center  <br/> |This permission when denied prevents users from seeing the Task Center link on the Project Web App Quick Launch menu  <br/> > [!NOTE]> This permission does not lock down access to the Task Center page. It is still possible for users to navigate to this page.           |||
|View Team Builder  <br/> |Allows a user to use Build Team in Project Web App and Project Professional, as well as determine the list of available resources. Grant this permission to resource managers to allow them to use Build Team in Project Web App to add resources to projects that have been saved to the Project Server database. Project Managers can also use this permission to allow them to use Build Team in Project Professional to add resources to projects.  <br/> | User needs to be granted the **Assign Resources** category permission in addition to the **View Team Builder** global permission. The Assign Resources category permission determines the list of resources available in Build Team in both Project Professional and Project Web App. <br/>  User needs to be granted the **Build Team on Project** category permission. The Build Team on Project permission determines with which projects Build Team can be used. This applies to using Build Team in both Project Professional and Project Web App. <br/> ||
|View Timesheets  <br/> |When this permission is denied, it prevents users from seeing the Timesheet Center link on the Project Web App Quick Launch menu.  <br/> > [!NOTE]> This permission does not lock down access to the Timesheet page. It is still possible for users to navigate to this page.           |||
   
## Project Server 2010 Global Permissions no longer available

The following are global permissions that were available in Project Server 2010 but are no longer available in Project Server 2013:
  
- About Project Server
    
- Approve Timesheets
    
- Close Tasks to Update
    
- Manage Site Services
    
- View Project View
    
- Edit Status Report Responses
    
## See also

#### 

[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Default categories in Project Server 2013](default-categories-in-project-server-2013.md)
  
[Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md)
  
[Plan user access in Project Server](plan-user-access-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

