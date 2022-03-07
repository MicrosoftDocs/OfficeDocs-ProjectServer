---
title: "Project Server 2016 knowledge articles for Systems Center Operations Manager"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 1362d492-f27c-4891-bc0d-1a494026c1b3
description: "Summary: Learn how to resolve alerts about Project Server in the SharePoint Server 2013 management pack for Systems Center Operations Manager (SCOM)."
---

# Project Server 2016 knowledge articles for Systems Center Operations Manager
 
 **Summary:** Learn how to resolve alerts about Project Server in the SharePoint Server 2013 management pack for Systems Center Operations Manager (SCOM).
  
The articles in this section are knowledge articles for Project Server 2013 that appear in the SharePoint Server 2016 management pack (MP). Typically, you would see these articles after clicking a link in an alert in the Operations Manager console. You can use these articles to help you troubleshoot and resolve problems in Project Server 2013.
  
New SCOM alerts in Project Server 2013:
  
- [Project WFE to application server connection failed (SharePoint 2013 monitoring rule)](#ProjectApp)
    
- [Project WFE to application server connection failed](#ProjectApp2)
    
Alerts for Project Server 2013 and Project Server 2010: 
  
- [Project Active Directory Connection Failed](/previous-versions/office/project-server-2010/ff678244(v=office.14))
    
- [Project Active Directory Exception Occurred During Synchronization](/previous-versions/office/project-server-2010/ff678246(v=office.14))
    
- [Project Active Directory Nested Foreign Security Principal Could Not Be Resolved](/previous-versions/office/project-server-2010/ff678245(v=office.14))
    
- [Project Active Directory Nested Object Could Not Be Resolved](/previous-versions/office/project-server-2010/ff678248(v=office.14))
    
- [Project Active Directory PWA Group Could Not Be Resolved](/previous-versions/office/project-server-2010/ff678243(v=office.14))
    
- [Project Active Directory Top Level Group Has No Members](/previous-versions/office/project-server-2010/ff730245(v=office.14))
    
- [Project Creating Report Center Web Failed](/previous-versions/office/project-server-2010/ff730237(v=office.14))
    
- [Project Cube Build Service Analysis Services Server Connection Failure](/previous-versions/office/project-server-2010/ff730236(v=office.14))
    
- [Project Cube Build Service Analysis Services Server Lock Time Out](/previous-versions/office/project-server-2010/ff730246(v=office.14))
    
- [Project Cube Build Service Attempt To Overwrite Failed](/previous-versions/office/project-server-2010/ff730251(v=office.14))
    
- [Project Cube Build Service Decision Support Object Is Not Installed](/previous-versions/office/project-server-2010/ff730231(v=office.14))
    
- [Project Cube Build Service OLAP Processing Failure](/previous-versions/office/project-server-2010/ff730240(v=office.14))
    
- [Project Failure Creating a Project Workspace](/previous-versions/office/project-server-2010/ff730239(v=office.14))
    
- [Project General Data Access Layer Error Connecting To Database](/previous-versions/office/project-server-2010/ff730253(v=office.14))
    
- [Project General Data Access Layer Error While Getting Connection Strings](/previous-versions/office/project-server-2010/ff730233(v=office.14))
    
- [Project Notification Email Delivery Failed](/previous-versions/office/project-server-2010/ff730235(v=office.14))
    
- [Project Notification XSLT Transformation Error](/previous-versions/office/project-server-2010/ff730240(v=office.14))
    
- [Project Queue General Percentage SQL Retries Per Day](/previous-versions/office/project-server-2010/ff730254(v=office.14))
    
- [Project Queue General Percentage SQL Retries Per Hour](/previous-versions/office/project-server-2010/ff730247(v=office.14))
    
- [Project Queue Jobs Average Wait Time Per Day](/previous-versions/office/project-server-2010/ff730230(v=office.14))
    
- [Project Queue Jobs Percentage Jobs Failed Per Day](/previous-versions/office/project-server-2010/ff730249(v=office.14))
    
- [Project Queue Jobs Percentage Jobs Failed Per Hour](/previous-versions/office/project-server-2010/ff730241(v=office.14))
    
- [Project Queue System Restarting Due to Unexpected Error](/previous-versions/office/project-server-2010/ff730248(v=office.14))
    
- [Project Reporting Server Side Event Has Failed](/previous-versions/office/project-server-2010/ff730255(v=office.14))
    
- [Project Server Side Event Handler Could Not Be Found](/previous-versions/office/project-server-2010/ff730250(v=office.14))
    
- [Project Server Event Service Could Not Be Found](/previous-versions/office/project-server-2010/ff730238(v=office.14))
    
- [Project SQL User View Refresh Message Was Not Queued](/previous-versions/office/project-server-2010/ff730232(v=office.14))
    
- [Project User View Was Truncated](/previous-versions/office/project-server-2010/ff730242(v=office.14))
    
- [Project Windows SharePoint Services Format Error](/previous-versions/office/project-server-2010/ff730243(v=office.14))
    
- [Project Winproj Average Time Taken For Project Open](/previous-versions/office/project-server-2010/ff730229(v=office.14))
    
- [Project Winproj Percentage Of Incremental Save To Full Save](/previous-versions/office/project-server-2010/ff730234(v=office.14))
    
- [Project Workspace User Synchronization Failed](/previous-versions/office/project-server-2010/ff730252(v=office.14))
    
## Project WFE to application server connection failed (SharePoint 2013 monitoring rule)
<a name="ProjectApp"> </a>

 <strong>Alert Name:</strong>Project WFE to application server connection failed
  
 **Summary:** This alert occurs when a Project Server front-end server cannot connect to a back-end server. Requests are no longer transferred from the front-end to the back-end.
  
### Cause

Potential root causes include: 
  
- Hardware issues
    
- Networking issues
    
- Permissions issues
    
### Resolution

Check standard connectivity on the faulty computers:
  
1. Ensure there are no hardware failures on any computer that reported the error.
    
2. Perform basic network connectivity checks between the front-end and back-end computers.
    
3. Check Project service accounts credentials and permissions.
    
## Project WFE to application server connection failed
<a name="ProjectApp2"> </a>

 <strong>Alert Name:</strong>Project WFE to application server connection failed
  
 **Summary:** This alert occurs when a Project Server front-end server cannot connect to a back-end server. Requests are no longer transferred from the front-end to the back-end.
  
### Cause

Potential root causes include: 
  
- Hardware issues
    
- Networking issues
    
- Permissions issues
    
### Resolution

Check standard connectivity on the faulty computers:
  
1. Ensure there are no hardware failures on any computer that reported the error.
    
2. Perform basic network connectivity checks between the front-end and back-end computers.
    
3. Check Project service accounts credentials and permissions.
    
## See also
<a name="ProjectApp2"> </a>

[Operations for Project Server 2016](operations-for-project-server-2016.md)

[Plan for monitoring in SharePoint 2013](/SharePoint/administration/monitoring-planning)
  
[Monitor health in SharePoint 2013](/SharePoint/administration/monitoring-overview)
  
[System Center Operations Manager knowledge articles (SharePoint 2016 Preview)](/SharePoint/technical-reference/system-center-operations-manager-knowledge-articles)