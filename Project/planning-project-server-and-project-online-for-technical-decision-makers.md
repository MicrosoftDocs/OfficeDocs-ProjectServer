---
title: "Planning Project Server and Project Online for technical decision makers"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 12/20/2016
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 8529f4fb-9c72-41ac-9bf8-6c8f02395e5e
description: "Summary: Learn about the technical planning decisions you have to make when deploying Project Server or Project Online."
---

# Planning Project Server and Project Online for technical decision makers
 
 **Summary:** Learn about the technical planning decisions you have to make when deploying Project Server or Project Online.<br/>
**Applies to:** Project Server 2016
  
Project Web App in Project Server 2016 and Project Web App in Project Online are very similar, but there are some key differences that you should think about when deciding whether to use Project Server or Project Online.
  
Read this article for an overview of the technical differences and what to consider when deciding on which option to choose. We'll also cover key configuration decisions that you'll have to make when setting up Project Web App.
  
In this article, we'll look at technical decisions. Also look at the [business decisions](planning-project-server-and-project-online-for-business-decision-makers.md) you'll need to make.
  
For a feature-by-feature comparison of Project Server and Project Online, see [A feature/function comparison of Project Online and Project Server 2013](https://technet.microsoft.com/library/f86ebfbb-0e55-420a-8718-66c27467eeb0.aspx).
  
## User access in Project Server and Project Online

The biggest decision that you'll have to make about security in Project Server or Project Online is which security mode to use.
  
### Security modes

Project Web App offers two security modes:
  
- **SharePoint permission mode** This mode uses SharePoint security to provide access to Project Server or Project Online. This mode is simple, and you can use it to provide different levels of access to different groups of people.
    
- **Project permission mode** This mode uses a complex security model that provides very precise control of user access. This mode takes careful planning to set up and maintain.
    
For each Project Web App site that you have, you need to decide which of the two security modes you want to use. For more information about the two modes and which features are supported in each, see [Plan user access in Project Server](plan-user-access-in-project-server.md).
  
### Security groups

In both security modes, you give your users access to features by adding them to groups. In both modes, Project Web App creates the following seven default groups:
  
- Administrators
    
- Portfolio Managers
    
- Portfolio Viewers
    
- Project Managers
    
- Resource Managers
    
- Team Leads
    
- Team Members
    
In SharePoint permission mode, these are created as SharePoint security groups in the Project Web App site collection. In Project permission mode, a separate security user interface is added to the PWA Settings page, containing these groups and other security settings.
  
As part of your planning process, you should decide which users to add to each group and how you want to manage those groups.
  
[Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md) lists the permissions that users in each group have. In SharePoint permission mode, these permissions are static and can't be changed. In Project permission mode, they're fully customizable.
  
In both modes, you can synchronize the groups with Active Directory groups. You do this by using [Active Directory Synchronization](manage-security-group-synchronization-with-active-directory-in-project-server.md) in Project permission mode, and by simply adding the Active Directory group you want to the SharePoint group in SharePoint permission mode.
  
## Business intelligence in Project Server and Project Online

There are some important differences between how Project Server and Project Online handle reporting:
  
- **Project Server** - In Project Server, you have direct access to Project Web App data in the content database (if your Project Web App site has its own content database), and you can query the reporting schema using Excel or more advanced reporting tools such as SQL Server Reporting Services or PerformancePoint Services in SharePoint Server 2016.
    
    With Project Server, you can also build customized OLAP cubes using the data in the Project Web App database. 
    
- **Project Online** - Direct database access is not possible because Project Online is hosted in a Microsoft datacenter. You must access your Project Web App data using one of the provided OData feeds. OLAP cubes are not currently available in Project Online.
    
Beyond this, you can combine cloud and on-premises BI solutions by copying your Project Online data into a data warehouse on-premises or in Microsoft Azure, or by accessing your on-premises Project Server data from Power BI and publishing reports to the cloud.
  
The following table shows a high-level comparison of how on-premises and online BI services can be used with Project Server and Project Online.
  
||**Project Server**|**Project Online**|
|:-----|:-----|:-----|
|Cloud BI  <br/> |Use Power BI Desktop to write reports by accessing Project Web App data in the content database or using the OData feed. These reports can be shared by publishing them to the cloud.  <br/> |Use Excel to access the Project Online OData feeds. Save reports for your users to your Project Online reporting library.  <br/> Optionally, use Power BI reports and data visualizations.  <br/> |
|On-premises BI  <br/> |For corporate BI, use SQL Server Reporting Services or PerformancePoint Services to report directly on the reporting data in the content database or online analytical processing (OLAP) cubes. (Requires no more than one instance of Project Web App per content database.)  <br/> For self-service BI, use Excel to access the Project Server OData feeds or OLAP cubes.  <br/> |Use SQL Server Integration Services to [create a data warehouse on-premises or in Microsoft Azure](https://go.microsoft.com/fwlink/p/?LinkId=511997). Use SQL Server Reporting Services or PerformancePoint Services to report from that.  <br/> |
   
Setting up reporting in Project Online is the easiest option to configure. The OData feeds for Project Web App work as soon as you set up Project Web App. 
  
Setting up reporting in an on-premises environment is more involved. If you want to access the Project Web App in the content database, you need to follow a series of steps that includes [setting up Office Web Apps Server](https://technet.microsoft.com/library/e4d51dc4-6460-437d-aa8e-0ae4d3aa8cc5%28Office.14%29.aspx) and [Secure Store](https://technet.microsoft.com/library/29c0bc76-d835-401b-a2fb-abb069e84125%28Office.14%29.aspx).
  
If you want to copy Project Online data into an on-premises data warehouse, you need to use SQL Server Integration Services and create a custom solution. Of all the reporting options for Project Web App this requires the most up-front work from your IT department or BI specialists. However, it does allow you to use Project Online even if you have business requirements for advanced reporting in an on-premises database.
  
Because pretty much any reporting need can be met using Project Online, either by itself or with a custom data warehouse using SQL Server Integration Services, we recommend Project Online as your first choice unless you have other business needs that require Project Server on-premises.
  
## Workflows in Project Server and Project Online

Workflows enforce your business processes and provide a structured way for projects to move through the various steps dictated by those processes. You can set up a workflow to do a variety of actions based on the user input, including sending emails, assigning tasks, and waiting for specific project actions.
  
While you can use Project Server or Project Online without using workflows, by using workflows, you can provide a basic structure to how projects are managed and how your project team interacts with them. As part of your planning process for Project Web App, be sure to plan how you want to use workflows to help you manage your projects.
  
## Custom fields in Project Server and Project Online
<a name="CustomFields"> </a>

By using Project Web App, you can create custom fields that you can use to collect metadata associated with your projects. Custom fields are available in the OData feeds in Project Web App and can be included in reports that you run on Project Web App data.
  
Custom fields work the same in Project Server and Project Online.
  
There are two types of custom fields: local andenterprise. Local custom fields are created and maintained in Project Professional. They are specific to a particular project. Enterprise custom fields are created and maintained in Project Web App and are available to all projects in Project Web App. You can create enterprise custom fields that are optional or required.
  
 **Local custom fields**
  
The main thing to consider when you use local custom fields is a naming convention. If you plan to use fields for the same purpose across multiple projects, be sure to give them the same name. By using the same name, you can use the fields consistently in reports among subprojects within a master project.
  
 **Enterprise custom fields**
  
Consider the following when you plan your enterprise custom fields:
  
- You can configure enterprises custom fields to be controlled by workflow.
    
- You can make enterprise custom fields optional or required. So if you want to be sure that you collect certain information at different stages of your workflow, for example, you can create custom fields that are required, and the user will have to fill them in before they can advance the workflow.
    
- While local custom fields are specific to a project, it's important to realize that enterprise custom fields are available in all projects in Project Web App. So when you create a custom field, consider how many projects you'll use it in to determine if you should make it a local or enterprise custom field.
    
  **Custom fields and system performance**
  
There are some circumstances where using custom fields can cause a noticeable reduction in performance, both in Project Server and in Project Online. Keep these in mind when you plan your custom fields.
  
Formulas in custom fields use system resources for their calculations. With local custom fields, this occurs in Project Professional. With enterprise custom fields, this occurs in Project Server or Project Online. Normally, these calculations happen in the background and aren't noticeable to the user, but with many custom fields with complex formulas, you might start to see a reduction in performance.
  
Similarly, lookup tables with large numbers of values can have a noticeable performance impact. Lookup tables with dozens or hundreds of options can cause a lag in performance.
  
## See also
<a name="CustomFields"> </a>

#### 

[IT Pro Planning for Project Server](it-pro-planning-for-project-server-2016.md)

