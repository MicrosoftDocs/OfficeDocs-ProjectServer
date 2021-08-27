---
title: "Periodic tasks for Project Server administrators"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 5/16/2017
audience: Admin
ms.topic: get-started-article
ms.prod: project-server-itpro
ms.localizationpriority: medium
search.appverid: MET150
ms.collection: IT_ProjectAdmin
ms.assetid: 6f4a1de6-878d-49cf-b759-352b717ddde2

description: "This article describes periodic checks Project Server admins should perform to maintain their environments. It was contributed by Microsoft Senior Premier Field Engineer Brooks White."
---

# Periodic tasks for Project Server administrators
 

**Applies to:** Project Server 2016, Project Server 2013 <br/>

This article describes periodic checks Project Server admins should perform to maintain their environments. It was contributed by Microsoft Senior Premier Field Engineer [Brooks White](https://go.microsoft.com/fwlink/p/?linkid=848903). (To access this link you will need a LinkedIn account)
  
## 

Project Server administrators should perform the following periodic checks to their environment as an important part of their job:
  
|**Daily**|
|:-----|
|Check the queue for  *Failed and Blocking*  jobs. <br/> |
|Review the errors related to  *Failed and Blocking*  jobs to troubleshoot. <br/> |
|Check for nightly cube build failures.  <br/> |
|Cancel  *Failed and Blocking*  jobs. <br/> |
   
| **Weekly**                                                                                                                                                                                                                                                       |
|:-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Review application and event logs on web front end (WFE) servers, APP servers and the SQL Server.  <br/>                                                                                                                                                         |
| Use the Unified Logging Service (ULS logs) as needed, based on the finding in the application and system event logs. Use the [Merge-SPLogFile](/powershell/module/sharepoint-server/Merge-SPLogFile) PowerShell cmdlet to filter output from all servers. <br/>        |
| Check Active Directory synchronization jobs to ensure they were successful.  <br/>                                                                                                                                                                               |
| Update Resource Breakdown Structure (RBS) values for new users. Newly synched users won't have an RBS.  <br/>NOTE - This may be the job of the PMO.                                                                                                              |
| Clear any overly long delegation sessions in Server Settings                                                                                                                                                                                                     |
| Maintain a valid enterprise resource pool by checking for users who haven't logged in for 60 days and find out why. For example, they may have left the company, are unaware of PWA, or could have been added mistakenly when someone else needed access.  <br/> |
| Check the ADMINISTRATORS group for admins that should be removed.  <br/>                                                                                                                                                                                         |
   
|**Monthly**|
|:-----|
|Provide timesheet training to new users.  <br/> |
|Provide project manager training to new project managers.  <br/> |
   
| **Quarterly**                                                                                                                                                                                                                     |
|:----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Close timesheet periods for the previous quarter plus one or some similar period. For example, if you are in Q4, close the timesheet reporting periods for Q2. The interval will be based on business or reporting needs.  <br/>  |
| Check with the project manager first, then close tasks to updates on projects that are complete or mostly compete or that have older tasks.  <br/>                                                                                |
| Archive and delete projects/sites for old completed project plans. But first create an archive plan that is documented and adhered to.  <br/> > [!NOTE]> Generally speaking, don't ever delete any resources from Server Settings |
| Delete timesheets from the past. Again, this will be defined by a policy that is based on business needs for reporting timesheet data.  <br/>                                                                                     |
   
|**Yearly**|
|:-----|
|Create fiscal periods for the next calendar year.  <br/> |
|Create timesheet periods for the next calendar year. The prefix might equal "Week.", starting at 1, and the suffix might be the calendar year, such as ".2016". Week 1's period will show as "Week.1.2016".  <br/> |
|Consider deleting timesheets for long-ago periods.  <br/> |
