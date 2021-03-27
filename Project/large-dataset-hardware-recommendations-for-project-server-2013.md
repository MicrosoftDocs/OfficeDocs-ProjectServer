---
title: "Large dataset hardware recommendations for Project Server 2013"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: af00720c-08ba-458c-a45b-706ad1c71a87

description: "Summary Here are the hardware recommendations for a large deployment of Project Server 2013."
---

# Large dataset hardware recommendations for Project Server 2013
 
 **Summary** Here are the hardware recommendations for a large deployment of Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
For large datasets, the data load will be the most substantial performance bottleneck. Generally, at a minimum for large datasets you will want a 4×2×1 topology. The hardware characteristics of the front-end Web and Application servers can generally remain the same as those recommended for the small and medium datasets. However, given that the SQL Server tier will be the bottleneck, you may find that this constrains your ability to scale out to additional front-end Web and Application servers. If data load is your bottleneck, you may find that additional front-end Web and Application servers do not produce an improvement in throughput. 
  
For large datasets, it is possible that the SharePoint Server 2013 instance that Project Server 2013 is coexisting with is also getting heavy usage (that is, you are not using that SharePoint Server 2013 deployment specifically for Project Server 2013 functionality). In this case we recommend that you separate the Project Server 2013 ProjectService database from the SharePoint Server 2013 content databases, placing it on its own dedicated computer that is running SQL Server. 
  
Given that the SQL Server tier will be your bottleneck, you will want to invest in additional resources on the SQL Server tier of your topology. You can "scale-up" your SQL Server by adding additional RAM, CPU, and hard disk resources.
  
The tables that follow give the minimum and recommended specifications for the SQL Server tier of a large dataset topology. 
  
## Minimum requirements for hardware for Project Server 2013

**SQL Server database minimum requirements for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> If your dataset size is considerably larger than the medium dataset, 8 cores are recommended.  <br/> |
|RAM  <br/> |32 GB  <br/> |
|Hard disk  <br/> |250 GB  <br/> NOTE - Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks.<br/> NOTE - RAID 5 should provide a good compromise between reliability, and throughput.           |
   
## Recommended hardware for Project Server 2013

**SQL Server database recommendations for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor |64-bit, eight-core, 2.5 GHz minimum per coreIf your dataset size is considerably larger than the medium dataset, 8 cores are recommended.|
|RAM|64 GB |
|Hard disk|300 GB or more <br/> NOTE - Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks. <br/> NOTE - RAID 5 should provide a good compromise between reliability and throughput.           |
   
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

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)