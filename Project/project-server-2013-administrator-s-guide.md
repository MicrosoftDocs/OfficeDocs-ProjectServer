---
title: "Project Server 2013 Administrator's Guide"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 9/6/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server
localization_priority: Normal
ms.assetid: 409b5511-24a2-482e-a62c-896256be58fd
description: "Summary: Download and use the Microsoft Project Server 2013 Administrator's Guide to manage and administer Project Server 2013 in your organization."
---

# Project Server 2013 Administrator's Guide
 
 **Summary:** Download and use the Microsoft Project Server 2013 Administrator's Guide to manage and administer Project Server 2013 in your organization.
  
Project Server 2013 administrators must manage many tasks in the Project Web App (PWA) Server Settings page for users to access and interact effectively with data. Farm administrators must also understand the tasks in the PWA Server Settings that they might be responsible for, such as OLAP database management, queue settings management, or project site provisioning settings. The  *Microsoft Project Server 2013 Administrator's Guide*  helps your organization understand these tasks that are involved with administering Project Server 2013. It includes many step-by-step procedures and accompanying user-interface screen shots of Project Web App.
  
File size: approximately 7.1 MB
  
- [Download the guide as a .docx file](https://go.microsoft.com/fwlink/p/?LinkId=299886)
    
## Changes in Project Server 2013 that affect administration

Before reading through this guide, it is important to know of several key changes in Project Server 2013 that make administration different from the previous versions. These changes include the following:
  
- **Some server settings moved to Central Administration**: A few Project Web App Server Settings that have previously been located in Project Web App in Project Server 2010 were moved to Central Administration in Project Server 2013. The reason for this change was that these settings were tasks that were more typically done by a farm administrator, instead of a PMO manager or Project Server 2013 administrator.
    
- **SharePoint Permissions Mode**: By default, Project Server 2013 security will be in SharePoint Permissions Mode. This mode uses Project Server 2013 SharePoint Security groups as containers in which Project Server 2013 can be added as members. Project Server 2013 permissions are assigned to these group, and they are not editable. If you must have more control, you can change to the traditional Project Server Permissions Mode. It is important to understand security modes when you are viewing the "Security" chapter.
    
- **Project Online**: Project Online is a hosted version of Project Server 2013 in which the service is hosted in the cloud. Administration will be different for Project Online and Project Server 2013, because many administrative tasks are performed for you and are inaccessible to users. The tasks documented in this guide are intended for Project Server 2013 users, and not for Project Online users. A Project Online Administrators Guide will be available to you at a later date.
    
## Book structure

This guide is divided into two sections, because Project Server 2013 administrative settings are now located in Project Web App and in Central Administration. The "Project Web App Settings in Project Server 2013" section contains eight chapters and is targeted to the Project Server Administrator or PMO. The "Project Web App Settings in SharePoint Central Administration" section is made up of four chapters and contains information that is of more interest to your farm administrator. Both sections are organized in the same manner in this book as they are organized in Project Web App and in Central Administration. This guide also contains appendix data, which is primarily reference data and lists.
  
Note that all of the chapters in the "Project Web App Settings in SharePoint Central Administration" section will also have similar chapter titles as the chapters located in the "Project Web App Settings in Project Server 2013" section of the book. This is because tasks associated with the chapter title are located in the PWA Settings page of both Project Server 2013 and Central Administration. For example, all "Operational Policies" tasks that typically are performed by a farm administrator are located in Central Administration, and all "Operational Policies" tasks that are typically done by a Project Server 2013 administrator are located in Project Server 2013.
  
The Microsoft Project Server 2013 Administrator's Guide contains the following chapters and appendices:
  
> Introduction
    
> Part 1: Project Web App Settings in Project Server 2013
    
    - Chapter 1, "Personal Settings"
    
    - Chapter 2, "Enterprise Data"
    
    - Chapter 3, "Queue and Database Administration"
    
    - Chapter 4, "Look and Feel"
    
    - Chapter 5, "Time and Task Management"
    
    - Chapter 6, "Operational Policies"
    
    - Chapter 7, "Workflow and Project Detail Pages"
    
    - Chapter 8, "Security"

    
> Part 2: Project Web App Settings in SharePoint Central Administration
    
    - - Chapter 9, "Queue and Database Administration"
    
    - Chapter 10, "Operational Policies"
    
    - Chapter 11, "Workflow and Project Detail Pages"
    
    - Chapter 12, "Manage Queue Settings"
    
> Appendices

    - Appendix A, "Project Server 2013 Category Permissions"
    
    - Appendix B, "Project Server 2013 Global Permissions"
    
    - Appendix C, "Project Server 2013 Default Security Groups"
    
    - Appendix D, "Project Server 2013 Default Categories"
    
    - Appendix E, "SharePoint Permission Mode Default Permissions for Project Server 2013 SharePoint groups"
    
 
    

