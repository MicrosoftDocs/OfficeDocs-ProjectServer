---
title: "Plan reporting and business intelligence in Project Web App"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/29/2017
ms.audience: ITPro
ms.topic: concetpual
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: df0a0c09-ed30-42b9-ba6c-08b6de9370e5
description: "Summary: Plan reporting on Project Web App data by using business intelligence tools in SharePoint Server 2013."
---

# Plan reporting and business intelligence in Project Web App
 
 **Summary:** Plan reporting on Project Web App data by using business intelligence tools in SharePoint Server 2013.<br/>
**Applies to:** Project Server 2013
  
In Project Server 2013 project information is stored in the SharePoint content database where the Project Web App site resides. This information can be queried by any reporting tool that can connect to a SQL Server database, provided you have no more than one instance of Project Web App for each content database. The data is also available through an OData feed. (OData is the recommended reporting method.)
  
> [!IMPORTANT]
> Directly querying Project Server data in a content database containing more than one instance of Project Web App is not supported. You must use the OData feed in this case. 
  
The data available for reporting includes timesheet custom fields, project properties, and portfolio planner and optimizer data. Project Server can also generate online analytical processing (OLAP) cubes containing this information.
  
Each instance of Project Web App includes a set of sample reports that use the OData feed. These reports are contained within Excel 2013 workbooks and can be rendered in a browser window if you have [Office Online Server configured to work with your SharePoint farm](http://technet.microsoft.com/library/a5276781-133b-413c-beca-b851e17c2081%28Office.14%29.aspx).
  
## Reports in Project Web App that use Excel

Excel reports are data-connected spreadsheets that you use to visualize the data retrieved from Project Web App or the associated OLAP cubes. In Excel 2013, you can present data in Pivot Tables, or Pivot Charts, and have access to additional visualization features.
  
## Security and access for the PWA Reports library in Project Web App

The PWA Reports library is a subsite of the Project Web App site and inherits permissions from the main Project Web App site. If you have users in your organization who are not Project Web App users, but who require access to Project Web App reports, you can do one of the following:
  
- You can break the permission inheritance between the PWA Reports library and the main Project Web App site. This allows you to add users to the PWA Reports library without giving them access to the Project Web App site. However, you will need to manually manage users who require access to both sites.
    
- You can create a site in the same site collection as Project Web App, but with different permissions, and deploy one or more dashboard pages to that site to make the needed reports available.
    
The following SharePoint Server 2013 site permission levels are available:
  
**SharePoint Server 2013 site permission levels**

|**Group**|**Permission level**|**Access to OData feed**|
|:-----|:-----|:-----|
|Administrators for Project Web App  <br/> |Full Control  <br/> |Yes  <br/> |
|Portfolio Managers for Project Web App  <br/> |Design  <br/> |Yes  <br/> |
|Portfolio Viewers for Project Web App  <br/> |Design  <br/> |Yes  <br/> |
|Project Managers for Project Web App  <br/> |Read  <br/> |No  <br/> |
|Resource Managers for Project Web App  <br/> |Read  <br/> |No  <br/> |
|Team Leads for Project Web App  <br/> |No access  <br/> |No  <br/> |
|Team Members for Project Web App  <br/> |No access  <br/> |No  <br/> |
   
These roles give the user access permissions to the reports within the site.
  
If you must secure access to specific items within the site, such as restricting access to report folders, specific reports or Office Data Connections, you can customize security permissions on an exception basis by either creating a specific security group that helps secure these items or by editing the security permissions for each item. All of this is accomplished by using SharePoint Server 2013 security.
  
We recommend that you do not rename or delete the default sample reports or their containing folders. When patches and service packs are released in the future, these reports and templates may be recreated.
  
## Reporting in Project Online

In Project Online, Project Web App data for reporting is only available through the OData feed. The OData feed must be accessed through Excel. OData reports can be published to the PWA Reports library and displayed using Excel Services.
  
## See also

#### 



