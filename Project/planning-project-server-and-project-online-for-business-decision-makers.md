---
title: "Planning Project Server and Project Online for business decision makers"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/20/2016
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: e59c8461-d915-4db7-8950-b0dd42389ecf
description: "Summary: Learn about the business planning decisions you have to make when you deploy Project Server or Project Online."
---

# Planning Project Server and Project Online for business decision makers
 
 **Summary:** Learn about the business planning decisions you have to make when you deploy Project Server or Project Online.<br/>
**Applies to:** Project Server 2016
  
Project Web App is the primary interface you use to manage projects and resources in Project Online and Project Server. Project Web App in Project Server 2016 and Project Web App in Project Online are very similar, but there are some key differences that you should be aware of when you decide whether to use Project Server or Project Online.
  
Read this article for an overview of these differences and the factors to consider when you decide which option to choose. We'll also cover key configuration decisions that you'll have to make when you set up Project Web App.
  
In this article, we'll look at business decisions. Also look at the [technical decisions](planning-project-server-and-project-online-for-technical-decision-makers.md) you'll need to make.
  
For a feature-by-feature comparison of Project Server and Project Online, see [A feature/function comparison of Project Online and Project Server 2013](./project-server-2013-and-2016.md).
  
## User access in Project Server and Project Online

Project Web App offers two methods of user access:
  
- **SharePoint permission mode** This mode uses SharePoint security to provide access to Project Server or Project Online. This mode is simple to use and allows you to provide different levels of access to people with different roles, such as project managers, resource managers, and team members.
    
- **Project permission mode** This mode uses a complex security model that provides very precise control of user access, including customization of permissions for each role and custom roles. This mode takes careful planning to set up and maintain. It's not recommended unless you have a very mature project management office and need to customize user access at a very detailed level.
    
Whereas you can switch between the two modes, doing so requires that you reconfigure all of your permissions. We recommend that you choose the mode that's best for your organization before you configure Project Web App.
  
Generally, unless you have a large and highly complex organization with specific business requirements to fine-tune what users have access to, we highly recommend that you use SharePoint permission mode. This mode is much easier to set up and maintain.
  
For more information about the two modes and which features are supported in each, see [Plan user access in Project Server](plan-user-access-in-project-server.md).
  
## Business intelligence in Project Server and Project Online

Getting information out of Project Web App is as important as getting information into it. Business intelligence, or reporting, is a big reason why many customers choose Project Web App.
  
There are some important differences between how Project Server and Project Online handle reporting. With Project Server, you can build customized online analytical processing (OLAP) cubes using the data in the Project Web App database. OLAP cubes are not currently available in Project Online.
  
If you're willing to do some additional integration, you can build a hybrid business intelligence solution. You can use Project Online and have your data copied to a data warehouse on-premises or to Microsoft Azure for reporting with on-premises reporting tools. Or you can use Project Server on-premises and use Power BI Desktop to access your Project Web App data and publish reports to the cloud.
  
The following table compares how you can use on-premises and online business intelligence services with Project Server and Project Online.
  
||**Project Server**|**Project Online**|
|:-----|:-----|:-----|
|Cloud business intelligence  <br/> |Use Power BI Desktop to access your on-premises Project Server data.  <br/> This requires Power BI and may require some configuration by your IT department.  <br/> |Use OData in Excel or a custom application to access your Project Online data for general reporting. Add Power BI for Office 365 for scheduled data refresh, [Power BI Q&amp;A](/power-bi/consumer/end-user-q-and-a), and other advanced features.  <br/> |
|On-premises business intelligence  <br/> |Use SQL Server Reporting Services or PerformancePoint Services for your corporate reporting needs. Use Excel for self-service business intelligence and ad-hoc reporting.  <br/> Both work without additional configuration needed beyond writing the report.  <br/> |Bring your Project Online data into a data warehouse on-premises or in Microsoft Azure where you can use standard corporate business intelligence reporting tools, such as SQL Server Reporting Services.  <br/> This requires configuration and customization by your IT department.  <br/> |
   
 **Keeping it simple**
  
Project Online is designed to use Excel as the primary reporting tool. From Excel, you can connect to the Project Online OData feeds and create PivotTables, PivotCharts, and other reports. You can also use Power BI to easily create reports and visualizations on your Project Web App data.
  
If you have a relatively small organization, and basic reports in Excel or Power BI fit your needs, Project Online is your best choice.
  
 **Advanced reporting needs**
  
If you require advanced reporting tools such as OLAP cubes, PerformancePoint Services, or SQL Server Reporting Services, consider one of the following options:
  
- **Project Server** - With Project Server, you have direct access to the data that you need for advanced reporting. This includes the Project Web App OData feeds and OLAP cubes.
    
- **Project Online** - With Project Online, you can use SQL Server Integration Services to connect to the Project Online OData feed and copy your data into an on-premises data warehouse. From there, you can access the data with PerformancePoint Services or SQL Server Reporting Services.
    
## Custom fields and lookup tables in Project Server and Project Online

By using Project Web App, you can create custom fields to collect metadata associated with your projects. For example, you can create a field where you store the estimated cost of the project. You can create custom fields for projects, tasks, and resources, and users can input values or choose values from lookup tables that you define.
  
Custom fields are available in the OData feeds in Project Web App, and you can include them in reports that you run on Project Web App data.
  
As you plan your deployment, review your business and reporting requirements, and think about what information you want to capture as part of each project. Your implementation team can set up custom fields to capture this data.
  
Custom fields and lookup tables work exactly the same in Project Server and Project Online.
  
## Number of Project Web App instances

With both Project Server and Project Online, you can create as many instances of Project Web App as you need.
  
A single instance of Project Web App can host many projects across different departments in your organization.
  
Having multiple instances of Project Web App is useful if you need any of the following:
  
- Security isolation for governance or other reasons
    
- Different sets of users or groups
    
- Different calendars
    
- Different timesheet standards
    
If you don't need more than seven instances of Project Web App, consider using Project Online.
  
## See also

#### 

[IT Pro Planning for Project Server](it-pro-planning-for-project-server-2016.md)

[Project Online Service Description](/office365/servicedescriptions/project-online-service-description/project-online-service-description)