---
title: "Small dataset hardware recommendations for Project Server 2013"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/29/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: aadb7d9f-ddfd-4a80-8658-ed92891903c6
description: "Summary Here are the hardware recommendations for a small deployment of Project Server 2013."
---

# Small dataset hardware recommendations for Project Server 2013
 
 **Summary** Here are the hardware recommendations for a small deployment of Project Server 2013.
  
## Minimum requirements for hardware for Project Server 2013

A single server that acts in all three roles: Application Server, Web Front End, and Database (SQL) Server. This server contains the SharePoint Content database and the four Project Server databases.
  
**Minimum requirements for hardware components for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single-server and multiple-server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB for installation  <br/> For production use, you need additional free disk space for day-to-day operations. Add twice as much free space as you have RAM for production environments.  <br/> |
   
## Recommendations based on coexistence with SharePoint Server 2013

Because Project Server 2013 coexists with SharePoint Server 2013, it generates additional resource usage (processor, RAM, and hard disk). The guideline requirements for SharePoint Server 2013 are also valid for a Project Server 2013 installation with a small data set and light usage. However, for more substantial data sets and usage patterns, additional hardware resources will be required. For a single-box deployment, with a small data set, we advise 16 GB of RAM to assure a high level of perceived performance. Beyond this, if possible, we recommend that you separate your SQL Server from the Application and front-end Web tiers by placing your databases onto a dedicated computer that is running SQL Server.
  
**Web Front End and Application Server recommendations for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single-server and multiple-server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**SQL Server database recommendations for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core(if your dataset size is considerably larger than the medium dataset, 8 cores are recommended)  <br/> |
|RAM  <br/> |16 GB  <br/> 8 GB for single-server and multiple-server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
## See also

#### 

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)
#### 

[Typical Datasets (Project Server 2013)](http://technet.microsoft.com/library/e2a0a4b6-0bda-468e-aeca-00f2807bf644.aspx)

