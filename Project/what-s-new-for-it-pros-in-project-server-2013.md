---
title: "What's new for IT pros in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/15/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 27a47c38-12b8-45f1-9e2a-a12e5e76a5af
description: "Summary: Learn about new features and capabilities in Project Server 2013."
---

# What's new for IT pros in Project Server 2013
 **Summary:** Learn about new features and capabilities in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
This article provides a brief overview of new and significantly updated functionality in Project Server 2013, with a particular emphasis on the areas of interest to IT pros. These areas include the following:
  
- [Project Online in Office 365](#section1)
    
- [Project Server 2013 architecture changes](#section2)
    
- [Multi-tenancy support](#section3)
    
- [Database consolidation](#section4)
    
- [Project site availability in SharePoint Server 2013](#section5)
    
- [Project mobile availability](#section6)
    
- [Demand Management improvements](#section7)
    
- [OData service for better reporting](#section8)
    
- [Improvements in Exchange integration with Project Server](#section9)
    
- [SharePoint task-list projects and enterprise projects](#section10)
    
- [My Tasks: All tasks in one location](#section11)
    
- [Administrative Settings user interface changes](#section12)
    
- [SharePoint Permission Mode](#section13)
    
- [Project site permissions](#section14)
    
- [Active Directory synchronization improvements](#section15)
    
- [Better logging and monitoring](#section16)
    
- [Project Server 2013 upgrade changes](#section17)
    
> [!NOTE]
> Project Server 2013 is built on SharePoint Server 2013, so Project Server users should read about its new features and functionality. For information about new features and functionality in SharePoint Server 2013, see [Explore SharePoint 2013](http://technet.microsoft.com/library/1a20e357-a21f-4409-9a99-6b8263ab30c5.aspx). 
  
## Project Online in Office 365
<a name="section1"> </a>

The release of Project Server 2013 is paired with the release of a new service in Office 365 for enterprises, Project Online. With Project Online, all operational maintenance is handled through an online service that is hosted in Microsoft datacenters, which allows you to focus on core project management tasks. Project Online in Office 365 delivers full Project Portfolio Management (PPM) capabilities (Demand Management, Portfolio Management, Resource Management, Reporting, and so on). Portfolio managers, project managers, and team members can access Project Online from anywhere with an Internet connection. 
  
The Project Online offering provides the following benefits:
  
- **IT Pro administration** All operational maintenance is handled through the Project Online service. You no longer have to commit IT resources to tasks such as updates, disaster recovery, and maintenance. Also, preventive maintenance scripts are run on your databases to prevent problems before they happen.
    
- **Easy startup** There are no up-front infrastructure costs and users are on a simple per user licensing basis.
    
- **Security** Office 365 employs robust disaster recovery capability, globally-redundant back-ups, and extensive privacy features. Filters help protect users against spam and viruses.
    
- **Guaranteed uptimes** Microsoft offers guaranteed, financially-backed up times and phone support 24 hours a day, seven days a week.
    
> [!NOTE]
> For more information about how to use Project Online, see [Getting started with Project Online](https://support.office.com/article/Get-started-with-Project-Online-E3E5F64F-ADA5-4F9D-A578-130B2D4E5F11). 
  
## Project Server 2013 architecture changes
<a name="section2"> </a>

Project Server 2013 is a multi-tiered system that extends the architecture introduced in Office Project Server 2007. The front-end tier includes Project Professional 2013, Project Web App, and third-party applications. Client applications communicate with the middle tier through the Project Server Interface (PSI) or through the client-side object model (CSOM) endpoints, which in turn communicate with the PSI and the business object layer. Database access is integrated in the business objects. The Project Server Eventing System can access both local and remote event handlers. The Project Calculation Service duplicates the Project Professional scheduling engine. Client applications do not (or should not) directly access the Project Web App database; Project Server hides business objects from clients.
  
At a high-level, some key architecture changes for Project Server 2013 include the following:
  
- **Database consolidation**: Driven by an effort to reduce total cost of ownership (TCO), Project Server 2013 data is consolidated into a single Project Web App database. The benefits of a single database are described in the [Database consolidation](#section4) section of this document.
    
- **Azure Workflow**: Declarative workflows (workflows that are defined in SharePoint Designer 2013) are offloaded to Azure Workflow for processing. Azure Workflow can run on a separate server in the SharePoint farm, on Azure in the cloud, or on a single Project Server computer for testing or demonstrations. Coded workflows that are developed with Visual Studio 11 Beta are processed in the workflow runtime within SharePoint Server, as in Project Server 2010.
    
- **OData services for reporting**: Project Online users and users of Project Server 2013 on-premises can both access their reports through the OData service. Open Data (OData) is an industry standard web protocol used to access data from external systems. The OData service internally runs SQL queries on the Reporting tables and views. This is especially helpful for Project Online users, because the Project Web App database cannot be directly accessed in Azure. Project Server 2013 users will still be able to directly access the Reporting table and views through SQL Server in order to create reports. For more information, see[Introducing OData: Data Access for the web, the cloud, mobile devices and more](http://go.microsoft.com/fwlink/p/?LinkId=780783&amp;clcid=0x409) in the MSDN Library.
    
- **Project Server Queuing system**: In Project Server 2013, timesheet jobs do not use the queue system (no Timesheets queue). All sites served by the same application service share the same queue service. Several key changes have greatly improved queue performances. When a job is posted to the queue table, the system will be notified that a job is available, instead of periodically having to poll for queue jobs.
    
- **Azure cloud services for Project Online**: For Project Online users in Office 365, data is stored in the Azure cloud services operating system.
    
    > [!NOTE]
    > For more information about Project Server 2013 architecture, see [Project Server 2013 architecture overview](https://msdn.microsoft.com/en-us/library/office/ee767687.aspx). 
  
## Multi-tenancy support
<a name="section3"> </a>

Unlike Project Server 2010, Project Server 2013 supports the ability to accommodate multiple tenants when used in conjunction with the SharePoint Server 2013 multi-tenancy feature. This gives you the ability to have multiple customers, business units, or departments on the same SharePoint Server and Project Server farm and infrastructure. For example, in a hosted environment you can have separate Project Server 2013 instances for two separate companies. Or in a company, you can have your legal department using a Project Server 2013 instance that is completely independent of other instances used by other departments. Each Project Server 2013 tenant shares use of the Project Application Service, but it runs independent of, and isolated from, the other.
  
## Database consolidation
<a name="section4"> </a>

In Project Server 2013, the Project Service provides project management functionality not only to Project Web App (PWA) but also throughout the SharePoint Server 2013 farm in which it resides. One major change is the use of a single Project Web App database for Project Server 2013.
  
In Project Server 2010, each Project Server 2010 instance was supported by a set of four Project Server databases (Draft, Publish, Reporting, and Archive). For Project Server 2013, all four Project Server 2013 databases are consolidated into a single database, the Project Web App database (default name: ProjectWebApp). The Reporting tables retain their previous names, and the Draft, Published, and Archived table names have the prefixes **draft.**, **pub.**, and **ver.** Direct access is not supported for the Draft, Published, and Archive tables and views. Reports should only use the Reporting tables and views.
  
These changes are driven by the need to reduce total cost of ownership (TCO) for using Project Server 2013, especially when you are implementing an environment in which you may have multiple PWA instances in your environment. A reduction in the number of databases required to use Project Server 2013 reduces the costs associated to maintain the data (update, backup, disaster recovery, and so on). 
  
## Project site availability in SharePoint Server 2013
<a name="section5"> </a>

The project site feature provides basic project management functionality in all SharePoint Server 2013 versions. The project site feature provides SharePoint Server 2013 users a team collaboration site in order to manage projects.
  
Project sites in SharePoint Server 2013 enable people in an organization to effectively collaborate on lightweight projects. Project managers can quickly get a sense of what is going on in a project, and team members can quickly see how their work fits into the overall context. Project sites also enable teams to access and share relevant data, documents, and communication.
  
A project site provides the following:
  
- Project Summary Web Part
    
- Visual timeline of the project's tasks
    
- Complete task schedule for a project
    
- Library for storing relevant project documents
    
- Notebook for quickly capturing and organizing information about the project
    
- Shared calendar for team events
    
- Ability to connect to the Project 2013 client application
    
When SharePoint Server 2013 is connected to Exchange Server, a project site can also include a team mailbox for unified communication about the project as it progresses. When a project site is part of a site collection that is associated with Project Server 2013, it can also be used to capture issues, risks, and deliverables, and it can be switched to full control (versus managed mode) for more robust Project Server 2013 functionality.
  
Although project sites offer the SharePoint Server user lightweight project management capabilities, eventually your environment might evolve to a point where you require additional features. For example, you might have numerous project sites and require a collective view of the information. When you need added project management functionality, a structured method allows you to easily migrate your project site data to Project Server 2013. 
  
For more detailed information about how to use project sites in SharePoint Server 2013, see [Getting started with a project site](https://go.microsoft.com/fwlink/p/?LinkId=255326).
  
## Project mobile availability
<a name="section6"> </a>

A new addition in Project Server 2013 is support for mobile access to your project data. A web-based mobile site is now included, which enables team members and project managers to view project status at a glance on a mobile device. By using the touch-enabled mobile site, you can access and edit relevant project documents and do lightweight editing of project plans from your Windows Phone 7.5 (using the Internet Explorer 9 browser), Apple iPhone, or Android device.
  
Mobile features are used primarily by two types of Project Server users:
  
- Team members
    
  - Check tasks assignments in a Project site
    
  - Interact with documents, tasks, and other information kept on a Project site
    
  - View the roll-up of project status for Project Server and lightweight projects.
    
- Project managers
    
  - Manage projects by using project sites
    
  - View up-to-date status information from resources assigned to their projects wherever they are
    
  - View project status information at a glance in a format that can be carried anywhere they need to go
    
  - Make minor changes to the project plan on the fly
    
Team members are also able to edit and submit task status through the Microsoft Exchange client on their telephones. Task synchronization between Exchange Server and SharePoint Server 2013 (the My Tasks page) is done through the Work Management Service.
  
For information about mobile availability in SharePoint Server 2013, [What's new in mobile devices (SharePoint 2013)](http://technet.microsoft.com/library/64d0b7b1-0b1d-43f3-88b0-7a15055f2a90.aspx).
  
## Demand Management improvements
<a name="section7"> </a>

Demand Management is the area of collecting "demand" for project ideas and proposals, and gathering information on those proposals. Proposals are then managed through portfolio management with triage and selection workflow, and then selected projects are executed and tracked by using Project Professional 2013 and Project Server 2013Project Server 2016. In Project Server 2010, workflows can be created and edited in Visual Studio. A key improvement in Project Server 2013 is the ability to use SharePoint Designer and the workflow engine in SharePoint Server 2013 to create Project workflows for Demand Management.
  
Demand Management in Project Server 2013 provides the following:
  
- A new proposal can be created and managed in SharePoint Server (say, with a SharePoint list) — and seamlessly integrated with Project Server. 
    
1. The project manager creates a SharePoint list for ideas and sets it up however she or he wants to. There are no requirements about how the list is set up for PPM Online to be able to work with it. 
    
2. Once the PM decides that they want the list to be able to migrate items into Project Server, they can add the Manage Projects App to the list to expose that functionality.
    
3. (Optional) The user goes to the Project Server settings page in List Settings and sets up the mapping from the columns in the list to fields in Project Server. 
    
4. The user promotes items in one of two ways: 
    
  - **Manually**, by selecting one or more items in a list view and clicking the **Create Projects** button on the **Items** tab of the ribbon. This opens a dialog box that allows the user to specify the column-field mapping (defaulted to the mappings set up in step 3) and the EPT to use, after which the projects are created for the selected items.
    
  - **Automatically**, through a workflow action. The user sets up a regular SharePoint workflow on the list and uses the Project action ( **Create Project from List Item**) as part of that workflow. The action takes an EPT as a parameter and, when executed, uses the mapping set up in the earlier step to create a project from the current list item context. 
    
5. In either case, the project is created in Project Server, and is created between the list item and the project (only new list items can be imported).
    
- In the case when users use the rich Demand Management platform with PDPs and EPTs (this was available in Project 2010), they can see a rich visualization of Project workflow status on the proposal (instead of a text table). 
    
## OData service for better reporting
<a name="section8"> </a>

A key change in Project Server 2013 reporting is the use of the OData service to access the Project Web App database. The use of OData was driven by the move to create a Project Online offering. In Office 365, the Project Web App database for Project Online cannot be accessed directly, so an OData service is available. For online customers, Reporting tables and views are exposed only by the OData interface. Project Online is designed to provide a separate database for each instance of Project Web App. That is, multiple instances of Project Web App each have their own Project Web App database. The OData service internally runs SQL queries on the Reporting tables and views in the Project Web App database associated with the specific instance of Project Web App. In Project Server 2013, users can also access the on-premises Reporting tables through the OData interface.
  
Users of Project Server 2013 on-premises who have the correct permissions can directly access the Reporting tables and views through SQL Server to create reports just as they do in Project Server 2010. For example, the dbo.MSP_PROJECT table and the dbo.MSP_EpmProject_UserView view can be used for reports. Any tables or views that have a "draft.", "pub.", or "ver." prefix are for internal use by Project Server only, and are not for reporting use. For example, the draft.MSP_TASKS table and the pub.MSP_PROJECTS_WORKING_VIEW view are not documented and are not for third-party use.
  
The Reporting tables, views, and fields in the Project Web App database are documented in an HTML Help file in the Project 2013 SDK. The OData XML schema for the Reporting data will also be documented online on MSDN, in an update of the SDK. Queries of the Reporting tables and views that were created for Project Server 2010 will, in most cases, work with the Project Web App database in Project Server 2013. Users of Project Server 2013 on-premises can access the Project Server OLAP cubes in SQL Server Analysis Services, as they currently do. In Project Online, OLAP cubes are not available.
  
An additional change to reporting in Project Server 2013 is that Basic Power Pivot technology is integrated into the latest version of Excel. Project Server 2013 and Project Online both take advantage of this technology to design rich reports.
  
> [!NOTE]
> For Project Server 2016, reports can be designed and viewed only in the Excel client. 
  
For information about how to configure reporting in SharePoint Server 2013, see [Configure reporting for Project Web App (Project Server 2013)](http://technet.microsoft.com/library/1882695e-50f4-4bc7-9f15-18365f96caf5.aspx).
  
## Improvements in Exchange integration with Project Server
<a name="section9"> </a>

Exchange integration with Project Server was introduced in Project Server 2010. It provides the ability for team members or resources on a project to view, update, delete, and report status on their published tasks in Microsoft Outlook, Outlook Web App (OWA), or any other application that is capable of syncing tasks from Exchange Server.
  
The Exchange integration feature in Project Server 2013 allows you integrate project task management by using SharePoint Server 2013 with Exchange Server 2013. This allows team members anywhere that have access to Exchange Server to interact with task management data in Microsoft Outlook or Outlook Web App and even using an Exchange-connected mobile device (by using either Windows Phone 7.5 or Apple IOS v5).
  
Project Server 2013 with Exchange Server 2013 provides the following:
  
- Server to Server Open Authorization (OAuth) standard
    
- Connections between SharePoint Server 2013, Exchange Server 2013, and Lync Server
    
- Task synchronization with SharePoint and Outlook tasks.
    
> [!NOTE]
> For more information about configuring task synchronization, see [Configure Exchange task synchronization in SharePoint Server 2013](http://technet.microsoft.com/library/2a83671c-29c5-41af-a15c-54a573a05d99.aspx). 
  
### Exchange calendar out-of-office integration

In Project Server 2013, we introduce the ability to synchronize a Project Server resource's calendar to their Microsoft Exchange calendar in order to retrieve and synchronize their out-of-office (administrative) time. This new functionality allows your resources to report their out-of-office time in a single location (Microsoft Exchange), and have it automatically synchronize to their Project Web App resource calendar. 
  
This feature is disabled by default, and is enabled in the Exchange Server Details section of the Additional Server Settings page of your Project Web App server settings.
  
## SharePoint task-list projects and enterprise projects
<a name="section10"> </a>

The Project Application Service in Project Server 2013 can be associated with a SharePoint site collection in which the project sites are SharePoint task-list projects. When the project site is a SharePoint task-list project, SharePoint maintains the project site in a site collection. Project Professional can synchronize with and update the task lists. A project site can include an independent SharePoint task list or a task list that is synchronized with an .MPP file; the .MPP file can be stored locally or in a SharePoint library. 
  
SharePoint task list projects can be converted so that Project Server maintains them as enterprise projects. In this case, Project Professional saves data directly to Project Server. The feature comparison table below compares the behavior of task lists, the Schedule Web Part, and other functionality for SharePoint task list projects and enterprise projects. The Schedule Web Part contains the grid on the Project Web App page where you can edit a project schedule. 
  
The following table provides a comparison of how various features work in visibility mode and full control:
  
**Comparison of SharePoint task list projects and enterprise projects**

|**Feature**|**SharePoint task list project**|**Enterprise project**|
|:-----|:-----|:-----|
|Task list in SharePoint  <br/> |Read-only  <br/> |Read/write  <br/> |
|Schedule Web Part  <br/> |Read-only  <br/> |Read/write  <br/> |
|Reporting  <br/> |Rich reporting through Project Server  <br/> |Rich reporting through Project Server  <br/> |
|Other Project Server functionality  <br/> | Blocked functionality: <br/>  Server-side project edits, with Project Web App or custom client applications <br/>  Statusing <br/>  Tasks are not visible <br/> |Full functionality is enabled  <br/> |
   
> [!NOTE]
> For more information about SharePoint task lists, see [Overview: View a SharePoint task list in Project Web App](https://go.microsoft.com/fwlink/p/?LinkId=259495). 
  
## My Tasks: All tasks in one location
<a name="section11"> </a>

The My Tasks feature allows users to see an aggregation of their SharePoint, Project Server, and Microsoft Outlook/Exchange tasks in a single location — the My Tasks page in a user's personal site. Instead of navigating to different lists, sites, and site collections to view and edit both SharePoint Server and Project Server tasks, users simply have to go to their My Tasks page to see a single collection of all the things they need to do. 
  
The My Tasks page allows you to update existing Project Server assignments, and the results are synchronized to Project Server 2013. For example, if you change the assignment status of an active Project Server 2013 task to **Complete**, the change is forwarded to Project Server 2013. 
  
The Work Management Shared Service in SharePoint Server 2013 provides the functionality for the My Tasks page. The Work Management Service is responsible for aggregating SharePoint tasks through Enterprise Search and Project Server task assignments through the Project application service. Tasks are not only collected to the My Tasks page, but they are also pushed to other applications in which they are configured to be viewed, such as Microsoft Outlook, or by mobile devices that synchronize to Exchange Server.
  
You can synchronize tasks from SharePoint Server, your My Site, and Project Server into your Exchange Server mailbox and your Windows Phone tasks hub. Additionally, Exchange Server tasks can be synchronized into your My Tasks page.
  
The Tasks section of the My Tasks page has various features to better organize your tasks. These include the following:
  
- **Timeline**: The timeline provides a visual representation of your recent and upcoming tasks relative to the current date. It can be configured through the Task settings page, but it provides a default view of all tasks one week into the past, and three weeks into the future. 
    
- **Filters**: Tasks can be filtered by a number of different settings, including by project, flagged and upcoming tasks, active tasks, new tasks, completed tasks, timesheet tasks, and task status reporting. Additionally, tasks can also be filtered by keyword search.
    
- **Important tasks**: You can use the "Important" flag to specify tasks that have special significance to you and make them viewable through the main view. Flags automatically expire over time to keep your list of important tasks current.
    
## Administrative Settings user interface changes
<a name="section12"> </a>

In Project Server 2013, Administrative controls that are more IT-related were moved from the Project Web App Server Settings page to the SharePoint Central Administration site. The goal is to make the Server Settings page more suitable for PMO Administration and to move settings related to administering the farm to the Central Administration site. 
  
In Central Administration in SharePoint Server 2013, you can find the Manage Project Server Settings page in the **General Application Settings** section. This page contains the following configuration pages:
  
**Configuration pages for General Application Settings in SharePoint Server 2013**

|**Queue and Database Administration**|**Operational Policies**|**Workflow and Project Details Pages**|
|:-----|:-----|:-----|
|Manage Queue Jobs  <br/> |Additional Server Settings  <br/> |Project Workflow Settings  <br/> |
|Daily Schedule Backup  <br/> |Server Side Event Handlers  <br/> ||
|Administrative Backup  <br/> |Project Site Provisioning Settings  <br/> ||
|Administrative Restore  <br/> |Bulk Update Project Sites  <br/> ||
|OLAP Database Management  <br/> |||
   
The Project Queue settings have been relocated to the Manage Project Web Apps page in Central Administration. You can access this page by clicking the Project Service Application in the Service Application page in Central Administration. You can then view the queue settings by clicking the Manage Queue Settings for Project Web App link on the Manage Project Web App Sites page.
  
## SharePoint Permission Mode
<a name="section13"> </a>

To both simplify Project Server permissions and more closely align the permissions configuration with SharePoint Server, the new default SharePoint Permission Mode has been created in Project Server 2013. It provides users an alternative to the "classic" Project Server permissions model (Project Permission Mode). A new installation of Project Server 2013 automatically starts you in SharePoint Permission Mode. If you require more detail in managing permissions, you can easily switch to the Project Permission Mode by using a Window PowerShell command. 
  
The following table illustrates the features available in each security mode.
  
**Comparison of security modes in Project Server 2013**

|**Feature**|**Permission mode**|
|:-----|:-----|
|**SharePoint** <br/> |**Project** <br/> |
|Unified security management through SharePoint Server  <br/> |×  <br/> ||
|Permissions inheritance for PWA and Workspaces  <br/> |×  <br/> ||
|Direct authorization against Active Directory security groups  <br/> |×  <br/> ||
|Claims-based authorization  <br/> |×  <br/> ||
|Manage authorization by role-based groups  <br/> |×  <br/> |×  <br/> |
|Extensible and customizable  <br/> |×  <br/> |×  <br/> |
|User delegation  <br/> ||×  <br/> |
|Ability to secure work resources  <br/> ||×  <br/> |
|Impersonation  <br/> ||×  <br/> |
|Security filtering using the Resource Breakdown Structure  <br/> ||×  <br/> |
|Custom Security Categories  <br/> ||×  <br/> |
   
Because SharePoint Permission Mode does not require synchronization between Project Server users and SharePoint sites, SharePoint Permission Mode uses fewer system resources and allows for greater scalability.
  
> [!IMPORTANT]
> Switching between SharePoint Permission Mode and Project Permission Mode deletes all security-related settings. If you switch from SharePoint Permission Mode to Project Permission Mode, you have to manually configure your security permissions structure in Project Server 2013. Switching from Project Permission Mode back to SharePoint Permission Mode deletes your security permissions information from Project Server 2013. 
  
One of the benefits of using SharePoint Permission Mode is that it attempts to separate IT and PMO roles. Site collection administrators are granted less control of PMO settings and pages, and they are granted more control over all aspects of the site collection.
  
SharePoint Permission Mode creates SharePoint groups that directly correspond to the Project Server 2010 default Security Groups. SharePoint groups are created during the post-provisioning process and after transition to SharePoint Permission Mode. 
  
These Project Server 2013 SharePoint groups have the same global and category permissions that were typically assigned to them in Project Server 2010. In SharePoint Permission Mode, you cannot create additional custom groups, categories, Resource Breakdown Structure (RBS) nodes, or edit the default permissions assigned to any of these objects. The following table describes the Project Server 2013 SharePoint groups and what they are allowed to do within EPM:
  
**Project Server 2013 SharePoint groups**

|**SharePoint group**|**EPM/PPM function**|
|:-----|:-----|
|Administrators  <br/> |Users have all global permissions and also category permissions through the My Organization category. This allows them complete access to everything in Project Server 2013.  <br/> |
|Portfolio Viewers  <br/> |Users have permissions to view Project and Project Server data. This group is intended for high-level users who need visibility into projects but are not themselves assigned project tasks.  <br/> |
|Project Managers  <br/> |Users have permissions to create and manage projects. This group is intended for project owners who assign tasks to resources.  <br/> |
|Portfolio Managers  <br/> |Users have assorted project-creation and team-building permissions. This group is intended for high-level managers of groups of projects.  <br/> |
|Resource Managers  <br/> |Users have most global and category-level resource permissions. This group is intended for users who manage and assign resources and edit resource data.  <br/> |
|Team Leads  <br/> |Users have limited permissions around task creation and status reports. This group is intended for persons in a lead capacity that do not have regular assignments on a project.  <br/> |
|Team Members  <br/> |Users have general permissions for using PWA, but limited project-level permissions. This group is intended to give everyone basic access to PWA. All new users are added to the Team Members group automatically.  <br/> |
   
To switch from SharePoint Permission Mode to Project Permission mode, run the following Microsoft PowerShell cmdlet:
  
```
Set-SPProjectPermissionMode -url <url> -mode ProjectServer
```

To switch from Project Permission Mode to SharePoint Permission Mode, run the following Microsoft PowerShell cmdlet:
  
```
Set-SPProjectPermissionMode -url<url > -mode SharePoint
```

## Project site permissions
<a name="section14"> </a>

For project sites that are managed through SharePoint (in visibility mode), users of the site are assigned to one of three SharePoint groups with the following SharePoint Permission levels:
  
|**Group name**|**SharePoint Permission level**|
|:-----|:-----|
|ProjectNameOwner  <br/> |Full Control  <br/> |
|ProjectNameMember  <br/> |Contribute  <br/> |
|ProjectNameVisitor  <br/> |Read  <br/> |
   
If the project site is then switched from a SharePoint tasks list project to an enterprise project (where Project Server maintains the project site), the groups are then given Project Server global and category permissions, based on the group they are in:
  
|**Group name**|**Project Server permission level**|
|:-----|:-----|
|ProjectNameOwner  <br/> |Full Permissions  <br/> |
|ProjectNameMember  <br/> |Basic Permissions  <br/> |
|ProjectNameVisitor  <br/> |Limited Permissions  <br/> |
   
Project site users must be in at least one of the three SharePoint groups for them to be recognized when the project site is in full control. Users created at the root of the SharePoint site will not be recognized by Project Server, although they will have access to the site.
  
> [!NOTE]
> For more information about SharePoint Permission Mode in Project Server 2013, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md). 
  
## Active Directory synchronization improvements
<a name="section15"> </a>

In Project Server 2013, big improvements have been made to synchronization and timer job performance. Changes were made to improve the time required for synchronization of users in the Active Directory directory service with Project Server Enterprise Resource Pools (ERPs) and to Project Server security groups. These changes include the following: 
  
- **Introduced smarter scheduling**: Synchronization jobs now run more during low usage times. Active Directory sync timer jobs can be scheduled through the Central Administration site.
    
- **Reduced the number of RDB updates**: Reporting synchronization jobs are more expensive to run than other job types. Reductions have been made in the number of jobs being run, and also in the types of jobs that are run. 
    
The result of these changes is marked improvements in the time required for synchronization jobs to run. The following table compares recent test results for Active Directory synchronization job times for a large group of users between Project Server 2010 SP1 and Project Server 2013:
  
||**Project Server 2010 SP1 Sync Job time**|**Project Server 2013 Sync Job time**|
|:-----|:-----|:-----|
|Initial Synchronization  <br/> |20:01  <br/> |7:43  <br/> |
|Recurring Synchronization  <br/> |14:07  <br/> |00:24  <br/> |
   
> [!NOTE]
> For the above test scenario, there were 6100+ users in 12+ nested groups. 
  
## Better logging and monitoring
<a name="section16"> </a>

Project Server Log Level Manager is a feature in Project Server 2013 that allows administrators to throttle the logs for a specific entity (for example, a project, resource, job, and so on). When activated, all the logs about a specified entity are written to ULS even if the server is set to a higher level. The entity that you want to track is specified through its GUID through Log Level Manager. Whenever ULS notices a trace with that GUID, it adds it to logging. Although we do not recommend verbose logging for the entire farm, logging for the specific entity is verbose. The following entities can be tracked through Log Level Manager:
  
- Assignments
    
- Calendars
    
- Queue jobs
    
- Objects
    
- Projects
    
- TS periods
    
- Resources 
    
- Tasks
    
- Templates
    
- timesheets
    
Log Level Manager is configured through the following Microsoft PowerShell cmdlets:
  
- **Add-SPProjectLogLevelManager**: Run this cmdlet to add a new entity to watch. Just running this cmdlet would prompt the user to provide all the relevant parameters, including the PWA url, the type and GUID of the entity to watch, and the level of logging desired.
    
- **Set-SPProjectLogLevelManager**: Run this cmdlet to update an entry already added to the log watch list. With this cmdlet, for example, you can update the LogLevel. (By default it is Verbose.)
    
- **Get-SPProjectLogLevelManager**: Run this cmdlet to list all the entities added or entities belonging to a certain criteria. For example, you can list all the entities for a given entitytype or with an entityuid starting with a partial guid string.
    
- **Clear-SPProjectLogLevelManager**: Run this cmdlet to clear all the entities being watched.
    
- **Remove-SPProjectLogLevelManager**: Run this cmdlet to delete a specific entity represented by an Entityuid.
    
- **Set-SPProjectLogLevelManagerRefresh**: You must run this cmdlet after making LogLevelManager changes to update the cached list of entities to watch. For performance reasons, the process in charge of writing to the ULS logs does not query the database to look for changes in the list of entities to watch. It works off of a copy of this table in memory instead. This command is required to refresh that list in memory.
    
## Project Server 2013 upgrade changes
<a name="section17"> </a>

The following are important things to note for upgrading to Project Server 2013:
  
- Full database-attach upgrade is the only available upgrade method when you upgrade to Project Server 2013Project Server 2016. In-place upgrade is not supported for upgrading to Project Server 2013. 
    
- Backwards compatibility is not supported for Project Server 2013. If you want to connect to Project Server 2013 with a Project client, Project Professional 2013 is required. Project Professional 2010 does not connect to Project Server 2013.
    
- There is no direct upgrade path from Project Server 2007 to Project Server 2013. You must first upgrade to Project Server 2010 before upgrading your data to Project Server 2013. For information about how to upgrade from Project Server 2007 to Project Server 2010, see the [Project Server 2010 Upgrade Overview](https://go.microsoft.com/fwlink/?LinkId=780784) on Microsoft TechNet.
    
- Because in-place upgrade is not supported, you must plan to have a Project Server 2013 environment to which you can migrate your Project Server 2010 data. 
    
For information about how to upgrade to Project Server 2013, see [Upgrade to Project Server 2016](upgrade-to-project-server-2016.md).
  

