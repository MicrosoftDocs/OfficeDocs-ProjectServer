---
title: Plan the client tier in Project Server 2013
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: dee8ae00-1de3-456b-8148-fe07d59e2871
description: Plan for Project Professional, task synchronization, and browser support in Project Server 2013.
---

# Plan the client tier in Project Server 2013
 
 **Summary:** Plan for Project Professional, task synchronization, and browser support in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
This article identifies the key components of the client tier in a Project Server 2013 deployment.
  
The client tier includes Microsoft-based applications and any custom applications that are specific to your organization.
  
## Project Professional 2013 in a Project Server 2013 deployment

Project Professional 2013 is a desktop application that enables project managers to create, publish, and manage projects. In addition to scheduling and tracking tools, Project Professional 2013 provides project managers with enterprise resource and portfolio management capabilities.
  
For information about deploying Project Professional 2013 in an enterprise environment, see [Office 2013 Resource Kit](/deployoffice/).
  
## Outlook in a Project Server 2013 deployment

SharePoint Server 2013 integrates with Exchange Server 2013 to provide task synchronization between SharePoint Server and a user's Exchange Server account. Project Server can use this functionality to synchronize a user's Project Server tasks and make them available in Outlook or on devices that allow the user to connect to their Exchange Server account.
  
Users can also receive email reminder notifications for tasks that they are assigned in projects that are stored in the Project Web App database.
  
## Browser support in Project Server 2013

Project Server 2013 and Project Web App support the same browsers as SharePoint Server 2013. For information about which browsers are supported, see [Plan browser support (SharePoint 2013)](/sharepoint/install/browser-support-planning)
  
## Third-party and line of business applications in a Project Server 2013 deployment

Many organizations use line-of-business client applications or develop business-specific applications. These applications call Project Server 2013 by using the Project Server Interface — an extensible set of Web services — and must also be integrated with a Microsoft Windows-based platform.
  
Project Server 2013 provides a complete Software Development Kit (SDK). 
  
## See also


[Volume activation of Office 2013](/DeployOffice/vlactivation/plan-volume-activation-of-office)