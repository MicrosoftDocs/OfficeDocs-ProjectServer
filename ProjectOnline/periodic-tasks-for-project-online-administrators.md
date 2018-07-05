---
title: "Periodic tasks for Project Online administrators"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 9/8/2017
ms.audience: Admin
ms.topic: conceptual
ms.prod: office-online-server
localization_priority: Normal
ms.custom: IT_ProjectAdmin
search.appverid: PJO150
ms.assetid: f7de04cc-9850-466c-920a-dd1ab593154e

description: "Describes periodic checks Project Online admins should perform to maintain their environments."
---

# Periodic tasks for Project Online administrators

This article describes periodic checks Project Online admins should perform to maintain their environments.
  
Project Online administrators should perform the following periodic checks to their environment as an important part of their job:
  
|**Daily**|
|:-----|
|Check the queue for  *Failed and Blocking*  jobs.  <br/> |
|Review the errors related to  *Failed and Blocking*  jobs to troubleshoot.  <br/> |
|Cancel  *Failed and Blocking*  jobs.  <br/> |
   
|**Weekly**|
|:-----|
|Check Active Directory synchronization jobs to ensure they were successful.  <br/> |
|Update Resource Breakdown Structure (RBS) values for new users. Newly synched users won't have an RBS.  <br/> > [!NOTE]> This may be the job of the PMO.           |
|Clear any overly long delegation sessions in Server Settings | Delete Enterprise Objects | User Delegation.  <br/> |
|Maintain a valid enterprise resource pool by checking for users who haven't logged in for 60 days and find out why. For example, they may have left the company, are unaware of PWA, or could have been added mistakenly when someone else needed access.  <br/> |
|Check the ADMINISTRATORS group for admins that should be removed.  <br/> |
|Check with Office 365 Global admin for news on upcoming features or updates.  <br/> |
   
|**Monthly**|
|:-----|
|Provide timesheet training to new users.  <br/> |
|Provide project manager training to new project managers.  <br/> |
|Check with Office 365 Global admin on license usage. For example, use data to follow up with users on licenses that are not being used.  <br/> |
   
|**Quarterly**|
|:-----|
|Close timesheet periods for the previous quarter plus one or some similar period. For example, if you are in Q4, close the timesheet reporting periods for Q2. The interval will be based on business or reporting needs.  <br/> |
|Check with the project manager first, then close tasks to updates on projects that are complete or mostly compete or that have older tasks.  <br/> |
|Delete timesheets from the past. Again, this will be defined by a policy that is based on business needs for reporting timesheet data.  <br/> |
   
|**Yearly**|
|:-----|
|Create fiscal periods for the next calendar year.  <br/> |
|Create timesheet periods for the next calendar year. The prefix might equal "Week.", starting at 1, and the suffix might be the calendar year, such as ".2016". Week 1's period will show as "Week.1.2016".  <br/> |
|Consider deleting timesheets for long-ago periods.  <br/> |
   

