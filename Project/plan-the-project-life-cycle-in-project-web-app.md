---
title: "Plan the project life cycle in Project Web App"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/29/2017
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: ae466c4f-b311-4471-9ee0-2ff5641722cb
description: "Summary: Learn how to plan projects, resources, and custom fields for new projects, and how to archive completed projects in Project Web App."
---

# Plan the project life cycle in Project Web App
 
 **Summary:** Learn how to plan projects, resources, and custom fields for new projects, and how to archive completed projects in Project Web App.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
There are many methodologies and systems that effectively manage a project life cycle. This article does not advocate for any one of these over another. This article is written for Project Server administrators, and it provides a list of project creation, maintenance, and archival activities. These tasks are general and will be the same, or at least similar, regardless of the methodology being used by your organization. Planning these activities can help ensure that projects are being managed in a way that is consistent with the purpose of your organization and can foster a satisfactory experience for the end user. This article alerts those who are responsible for planning the deployment and configuration of Project Server that some choices will have to be made that relate to these features.
  
Projects have many ways of moving from concept to reality. Sometimes the process is informal and may be the result of a brainstorm on a whiteboard that happened in under an hour. Other times a project is created after years of study and careful analysis. If it is not planned and managed, this creation process can become chaotic. This chaos can cost your organization in many ways: reduced efficiency, misallocated resources, misaligned priorities, duplication of effort, conflicting approaches, and missed opportunities, to name a few. What follows are some key things to consider when you are using Project to create projects for your organization.
  
## Plan to migrate task list projects into Project Web App

Project Server provides the ability to import projects that were created by using SharePoint lists into an instance of Project Web App. This functionality allows you to quickly start projects and manage them simply while they remain small. As they grow in scope, you can gradually migrate them to become full Project Server projects.
  
Project Server supports only a single instance of Project Web App per site collection. As you plan SharePoint task list projects, consider which site collection that you want to create them in so that projects that are related to each other can be imported into the same instance of Project Web App.
  
We also recommend that you develop guidelines for your organization for how long you want to manage projects in a SharePoint list before you import them into Project Web App.
  
## Plan resources in Project Web App

Enterprise resources are the people, equipment, and materials that are used to complete tasks in an enterprise project. Enterprise resources are part of your organization's pool of resources and are stored centrally in each instance of Project Web App. You can create the Enterprise Resource Pool that project managers will use when assigning resources to tasks in projects by adding resources to the Enterprise Resource Pool or by importing resources. You should define the contents of the Enterprise Global Template before you add resources to the Enterprise Resource Pool.
  
Before you can properly create and maintain the Enterprise Resource Pool for your organization, you must carefully define and document your Enterprise Resource custom fields and create them. In addition, for large organizations, initially populating the Enterprise Resource Pool is just as important as the process of keeping the Enterprise Resource Pool accurate and up-to-date. Tracking significant changes to the resource information that is stored and managed in the Enterprise Resource Pool can be a full-time activity
  
Before you create your Enterprise Resource Pool for Project Web App, you must determine your starting point. The process of adding resources to the Enterprise Resource Pool varies according to whether you are:
  
- **Starting with new projects** Minimal preparation is necessary for this scenario. The process is simplified if you can gather all required resource information in a single document. You could make a list on paper. Then you would import your identified resources from Active Directory, or from a membership store if you were using forms authentication. Alternatively, you can gather this information by using Excel. Then you would import the resulting spreadsheet into Project Professional and save it to Project Web App.
    
- **Creating the enterprise resource pool** In this scenario, you are creating the Enterprise Resource Pool in Project Professional. Using Project Professional, connect to Project Web App and check out the Enterprise Resource Pool. Enter the resources and save the Enterprise Resource Pool.
    
## Plan custom fields in Project Web App

Project Web App includes lookup tables and fields that you can customize. A custom field can contain information about a task, resource, or assignment. In Project Web App, fields that can contain customized data are text, flags, numbers, dates, cost, start and finish dates, and durations. You can customize these fields to obtain the information you want using formulas, specific value calculations, or graphical indicators.
  
You can write your own formulas, including references to other fields, to be calculated in a custom field. You can create a list of values for a custom field to ensure fast and accurate data entry. You can display a graphical indicator in a custom field instead of the actual data. That way, you can quickly see when the data in that field meets certain criteria, such as when the data exceeds a specified range or when resources are over-allocated. You can also create a hierarchical structure of custom fields for information in your project. For instance, you might want to associate your company's cost codes with your project data. After you create this structure and apply these custom fields to your data, you can easily use them to filter, sort, and group project data.
  
In Project Web App there are two types of custom fields — local and enterprise. Local custom fields are used by the project manager within the scope of a particular project. Enterprise custom fields are used by the Project Management Office (PMO) to collect data for rollup reporting across the organization. For enterprise task and project custom fields, Project Web App supports the notion of scoping to a specific program (collection of projects). In this way, an enterprise custom field can be defined that applies to a subset of projects.
  
(More information on [Custom fields in Project Server and Project Online](planning-project-server-and-project-online-for-technical-decision-makers.md#CustomFields).)
  
## Retire projects from Project Web App

There are certain activities that you should consider when retiring projects. Doing some basic clean-up when a project is retired can help to improve Project Server performance. Also, you can secure projects to ensure that only those who need the information — for example, for historical purposes — can see the projects. Deleting other enterprise objects that are not being used, such as resources and assignments, can help to prevent degradation of server performance. 
  
## Plan archiving in Project Web App

A number of enterprise objects can be backed up in Project Web App:
  
- Projects
    
- Enterprise Resource Pool and Calendars
    
- Enterprise Custom Fields
    
- Enterprise Global
    
- View Definitions
    
- System Settings
    
- Category and Group Settings
    
Backing up these objects allows you to selectively restore specific items, and you can retain multiple versions of these items.
  
Backups are done on the Project Server Settings page in Project Web App. There are two methods available:
  
- Schedule Backup
    
- Administrative Backup
    
Administrative Backup allows you to back up enterprise objects at any time. Schedule Backup, as the name implies, allows you to back up enterprise objects daily at a scheduled time. We recommend that you back up your enterprise objects regularly and, if scheduled, at a time when server utilization is low.
  
When an object is backed up, it is saved to an archive area in the SharePoint content database where the Project Web App resides.
  
When a project is complete, there are a few options available for retiring the project.
  
- Delete the enterprise objects from Project Web App but retain the archived copy.
    
- Delete enterprise objects completely and rely upon database backups for archival.
    
- Place the project in a special Project Web App category that denies access to all but a few users.
    
### Placing projects in a special Project Server category

To allow only certain users to view a retired project, you can create a special Project Web App category for that purpose. Add the project and all users whom you do not want to have access to the project and set all of their permissions to deny. For more information about Users, Groups, and Categories, see [Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md).
  
> [!NOTE]
> To create a category, Project Web App must be in Project Server permission mode. 
  
## Plan cleanup in Project Web App

Deleting unused enterprise objects when a project is completed can help to prevent degradation of server performance. It is particularly beneficial for long term server performance to delete assignments. It is also a good idea to delete resources if they are no longer being used in the enterprise. Deleting unused enterprise objects when a project is completed also saves disk space on your database server.
  
