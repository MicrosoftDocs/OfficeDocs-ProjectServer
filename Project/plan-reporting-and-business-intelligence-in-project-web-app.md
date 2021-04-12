---
title: "Plan reporting and business intelligence in Project Web App"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 11/29/2017
audience: ITPro
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
  
In Project Server 2013, project information is stored in the Project Web App database. This information can be queried by any reporting tool that can connect to a SQL Server database. The data is also available through an OData feed.

The data available for reporting includes timesheet custom fields, project properties, and portfolio planner and optimizer data. Project Server can also generate online analytical processing (OLAP) cubes containing this information.
Each instance of Project Web App includes a set of sample reports and templates. These reports are contained within Excel 2013 workbooks and are designed to be used with Excel Services in SharePoint Server 2013. 
  
## Reports in Project Web App that use Excel

Excel reports are data-connected spreadsheets that you use to visualize the data retrieved from the Project Web App database or the associated OLAP databases. In Excel 2013, you can present data in Pivot Tables, or Pivot Charts, and have access to additional visualization features. The sample reports included with Project Web App use Office Data Connections to access and retrieve data from the Project Web App database and OLAP databases.

## Dashboards in the Project Web App Business Intelligence Center

You can build dashboard pages in the Project Web App Business Intelligence Center by using Web Parts to display Project Web App data. Using Web Parts, you can present Project Web App data by using several different options:
- Excel Services
- SQL Server 2012 Power Pivot for SharePoint Server 2013
- Power View for SharePoint 2013
- SQL Server Reporting Services (SSRS) 2005 or 2008
- PerformancePoint Services in SharePoint Server 2013
- SharePoint Server 2013 Business Connectivity Services functionality

Each of the six methods listed can be added to a dashboard page by using the relevant Web Part for the reporting function. For example, in order to put an Excel Report on a dashboard page, you would add an Excel Web Access Web Part to the dashboard page and link the Web Part to the specific Excel .xlsx file to show in the Web Part.

Dashboard pages have built in page filters which can be linked to Report Web Parts to filter the contents by user or other information. Reporting Web Parts can also be linked to one another so that when you select a value in one report, the other connected reports are filtered by the current selection.


## Security and access for the Business Intelligence Center in Project Web App

The Business Intelligence Center is a subsite of the Project Web App site and inherits permissions from the main Project Web App site. If you have users in your organization who require access to Project Web App reports, you can do one of the following:
  
- You can break the permission inheritance between the Business Intelligence Center and the main Project Web App site. This allows you to add users to the Business Intelligence Center without giving them access to the Project Web App site. However, you will need to manually manage users who require access to both sites.
    
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
   
These roles give the user access permissions to a set of items within the site. These items can be Reports, Report Templates, and Office Data Connections. For items that are Office Data Connections, the Secure Store Service credentials that are used for a given ODC provide access to data within the Project Web App and OLAP databases.
  
If you must secure access to specific items within the site, such as restricting access to report folders, specific reports or Office Data Connections, you can customize security permissions on an exception basis by either creating a specific security group that helps secure these items or by editing the security permissions for each item. All of this is accomplished by using SharePoint Server 2013 security.
  
We recommend that you do not rename or delete the default sample reports or template, or their containing folders. When patches and service packs are released in the future, these reports and templates may be recreated.

## Office Data Connections

Office Data Connections are external files that can be used by multiple Excel reports. These files contain:

1. The connection information that is needed to connect and access the correct target database or OData feed.
2. The security credentials or authentication information needed to read data from the target data source.
3. The specific description of what data will be retrieved from the target database. This can include a SQL select query.

Access to these files can be secured by using SharePoint Server 2013 security. You can also secure access to reporting data by creating separate Secure Store target applications for each account.
  
## Reporting in Project Online

In Project Online, Project Web App data for reporting is only available through the Project Online Reporting OData feed. The OData feed can be accessed through Excel 2013 or later. OData reports can be published to the Project Online Project Web App and displayed using Excel. Providing the Excel file is using the legacy OData import wizard for the Project Online Reporting OData feed, Excel will be able to refresh the Project Online data in the Excel file. For details on enabling the legacy data import wizards in Excel see this article: [Data import and analysis options](https://support.office.com/en-us/article/data-import-and-analysis-options-3ea52160-08bc-45ac-acd9-bc4a11bcc2a2)
  
## See also
[Overview of Excel Services in SharePoint Server 2013](/SharePoint/administration/excel-services-overview)
####