---
title: "Plan the application tier in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: f736c231-33a0-43b2-9091-ff947edbd704
description: "Summary: Learn what components of the application tier that you should plan for in a Project Server 2013 deployment."
---

# Plan the application tier in Project Server 2013
 
 **Summary:** Learn what components of the application tier that you should plan for in a Project Server 2013 deployment.<br/>
**Applies to:** Project Server 2013
  
The application tier in Project Server 2013 includes the following components:
  
- [SharePoint Server 2013](#SharePointServer)
    
- [Project Server 2013](#section1)
    
- [Project Server Interface](#section2)
    
- [Project Server 2013 Events service](#section3)
    
- [Project Server 2013 Queue service](#section4)
    
- [Exchange Server](#exchange)
    
- [Other applications](#section5) (described in this article)
    
## SharePoint Server 2013
<a name="SharePointServer"> </a>

The Enterprise edition of SharePoint Server 2013 is required for Project Server 2013. SharePoint Server 2013 has many features in its own right, and deployment of SharePoint Server 2013 should be carefully planned. For information about how to plan your SharePoint Server 2013 deployment, see [Planning and architecture for SharePoint Server 2013](http://technet.microsoft.com/library/0ed0b44c-d60d-4b85-87de-19065d968835.aspx).
  
## Project Server 2013
<a name="section1"> </a>

Project Server 2013 is a robust and highly scalable Web-based server application that is integrated with several client applications, the Windows Server platform, and SQL Server 2008 R2 or SQL Server 2012.
  
You can run the Project Server 2013 service on one or more application servers in a SharePoint Server 2013 farm.
  
## Project Server Interface
<a name="section2"> </a>

The Project Server Interface is the application programming interface (API) of Project Server 2013. The Project Server Interface object model exposes Project Server 2013 functionality to all external applications. Project Professional 2013, Project Web App, and line-of-business and other third-party applications use the Project Server Interface (PSI) to access Project Server 2013 data that is stored in a Project Web App database. The PSI is available through Web service calls by back-end line-of-business applications, or through a Project Server Interface proxy for client applications having a user interface.
  
## Project Server 2013 Events service
<a name="section3"> </a>

The system-level Project Server 2013 Events service manages the Project Server 2013 events. Other applications can subscribe to Project Server 2013 pre-events and post-events, and register event handler methods through Project Web App. Event handlers can check business rules and cancel an operation through a pre-event, or extend Project Server 2013 with additional processing such as workflow by using a post-event (for example, ProjectPublished).
  
## Project Server 2013 Queue service
<a name="section4"> </a>

The Save and Publish queue manages new and incremental saves of working projects and also manages publishing a project.
  
## Exchange Server
<a name="exchange"> </a>

Exchange Server 2013 integration with SharePoint Server 2013 allows for Project Web App users to view Project Server and SharePoint Server tasks in Microsoft Outlook and on devices that can access the user's Exchange Server account.
  
## Other applications
<a name="section5"> </a>

Third-party and line-of-business applications can be used with Project Server 2013. By using the Project Server Interface, you can address many project management needs with these applications. The following are some sample scenarios:
  
- **Project proposals** Create placeholder projects during project initiation and use project custom fields to tag the project with information needed for the initiation and approval process. Add tasks to identify project phases for key milestones or deliverables. When approved, project proposals can evolve into full-scale projects that are managed by using Project Professional 2013.
    
- **Maintenance projects** Create placeholder projects to use with resource plans. Reserve or book time against resources for maintenance work or base business. Maintenance projects generally do not have tasks.
    
- **Financial projects** Create projects for time capture through the timesheet for integration with a financial system. Create tasks for a hierarchy of financial codes that reflect the cost breakdown structure of the financial system. These projects do not require scheduling or status updates.
    
- **Integration with project accounting systems** Capture the resource costs and expenses associated with projects to feed financial and billing systems and for budget comparison purposes. Synchronize tasks, resources, and assignments between the systems. Capture timesheet data in one system to feed the other (which timesheet is used depends on the needs of the organization or of individual projects).
    
- **Integration with work or task management systems** Synchronize tasks and assignments between Project Server 2013 and systems such as Microsoft Visual Studio Team System. Microsoft Visual Studio Team System is integrated with Project Standard 2013 and Project Professional 2013, but integration with Project Server 2013 requires developing components by using the PSI.
    
- **Process updates from team members** For projects that are not actively managed, automatically update them on the server by using information from team members about progress and other changes. Projects can be updated and republished without a project manager reviewing the results or making adjustments to the plan.
    

