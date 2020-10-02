---
title: "Plan the client tier in Project Server 2013"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: dee8ae00-1de3-456b-8148-fe07d59e2871
description: "Summary: Plan for Project Professional, task synchronization, and browser support in Project Server 2013."
---

# Plan the client tier in Project Server 2013
 
 **Summary:** Plan for Project Professional, task synchronization, and browser support in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
This article identifies the key components of the client tier in a Project Server 2013 deployment.
  
The client tier includes Microsoft-based applications and any custom applications that are specific to your organization.
  
## Project Professional 2013 in a Project Server 2013 deployment

Project Professional 2013 is a desktop application that enables project managers to create, publish, and manage projects. In addition to scheduling and tracking tools, Project Professional 2013 provides project managers with enterprise resource and portfolio management capabilities.
  
For information about deploying Project Professional 2013 in an enterprise environment, see [Office 2013 Resource Kit](https://technet.microsoft.com/library/9df1c7d2-30a9-47bb-a3b2-5166b394fbf5.aspx).
  
## Outlook in a Project Server 2013 deployment

SharePoint Server 2013 integrates with Exchange Server 2013 to provide task synchronization between SharePoint Server and a user's Exchange Server account. Project Server can use this functionality to synchronize a user's Project Server tasks and make them available in Outlook or on devices that allow the user to connect to their Exchange Server account.
  
Users can also receive email reminder notifications for tasks that they are assigned in projects that are stored in the Project Web App database.
  
## Browser support in Project Server 2013

Project Server 2013 and Project Web App support the same browsers as SharePoint Server 2013. For information about which browsers are supported, see [Plan browser support (SharePoint 2013)](https://technet.microsoft.com/library/ff6c5b8c-59bd-4079-8f0b-de4f8b4e0a86.aspx)
  
## Third-party and line of business applications in a Project Server 2013 deployment

Many organizations use line-of-business client applications or develop business-specific applications. These applications call Project Server 2013 by using the Project Server Interface — an extensible set of Web services — and must also be integrated with a Microsoft Windows-based platform.
  
Project Server 2013 provides a complete Software Development Kit (SDK). 
  
## See also

#### 

[Volume activation of Office 2013](https://technet.microsoft.com/library/b41f7bc2-b7fa-43a3-963a-cf1c1ef8f331.aspx)

