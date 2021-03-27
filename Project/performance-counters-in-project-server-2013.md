---
title: "Performance counters in Project Server 2013"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: c28280ca-a2d6-4474-a267-3ffeb73f1e69
description: "Summary: Use performance counters to monitor the health of a Project Server 2013 farm."
---

# Performance counters in Project Server 2013
 
 **Summary:** Use performance counters to monitor the health of a Project Server 2013 farm.<br/>
**Applies to:** Project Server 2013
  
To help you determine when you have to scale up or scale out your Project Server 2013 farm, use performance counters cited in this article to monitor the health of the system. The information in the following tables can be used to determine which performance counters to monitor, and to which process the performance counters should be applied:
  
- Web servers
    
- Database servers
    
- Project Application Server performance counters
    
## 

The following table shows performance counters and processes to monitor for Web servers in your Project Server 2013 farm.
  
**Performance counters and processes to monitor for Web servers**

|**Performance counter**|**Apply to object**|**Notes**|
|:-----|:-----|:-----|
|Processor Time  <br/> |Total  <br/> |Shows the percentage of elapsed time that this thread used the processor to execute instructions.  <br/> |
|Memory Utilization  <br/> |Application Pool  <br/> |Shows the average utilization of system memory for the application pool. You must specify the correct application pool to monitor.  <br/> The basic guideline is to determine peak memory utilization for a given Web application, and assign that number plus 10 MB to the associated application pool.  <br/> |
   
The following table shows performance counters and processes to monitor for database servers in your farm.
  
**Performance counters and processes to monitor for database servers**

|**Performance counter**|**Apply to object**|**Notes**|
|:-----|:-----|:-----|
|Average disk queue length  <br/> |Hard disk that contains SharedServices.mdf  <br/> |Average values larger than 1.5 per spindle indicate that the write times for that hard disk are insufficient.  <br/> |
|Processor time  <br/> |SQL Server process  <br/> |Average values larger than 80 percent indicate that processor capacity on the database server is insufficient.  <br/> |
|Processor time  <br/> |Total  <br/> |Shows the percentage of elapsed time that this thread used the processor to execute instructions.  <br/> |
|Memory utilization  <br/> |Total  <br/> |Shows the average utilization of system memory.  <br/> |
   
The following table shows performance counters and processes to monitor for your Application server.
  
**Performance counters and processes to monitor for your Application server**

|**Performance counter**|**Apply to object**|
|:-----|:-----|
|% Sql Retries / Day  <br/> |ProjectServer:QueueGeneral  <br/> |
|Active Job Processing Threads  <br/> |ProjectServer:QueueGeneral  <br/> |
|Active Job Processing Threads  <br/> |ProjectServer:QueueGeneral  <br/> |
|Average Unprocessed Jobs / Day  <br/> |ProjectServer:QueueGeneral  <br/> |
|Current Unprocessed Jobs  <br/> |ProjectServer:QueueGeneral  <br/> |
|New Jobs / Minute  <br/> |ProjectServer:QueueGeneral  <br/> |
|Sql Calls / Hour/Day  <br/> |ProjectServer:QueueGeneral  <br/> |
|Sql Calls / Minute  <br/> |ProjectServer:QueueGeneral  <br/> |
|Sql Retries / Minute  <br/> |ProjectServer:QueueGeneral  <br/> |
|% Jobs Failed / Day  <br/> |ProjectServer:QueueJobs  <br/> |
|% Jobs Failed / Hour  <br/> |ProjectServer:QueueJobs  <br/> |
|% Jobs Retried / Day  <br/> |ProjectServer:QueueJobs  <br/> |
|% Jobs Retried / Hour  <br/> |ProjectServer:QueueJobs  <br/> |
|Average Processing Time / Day  <br/> |ProjectServer:QueueJobs  <br/> |
|Average Processing Time / Minute  <br/> |ProjectServer:QueueJobs  <br/> |
|Average Wait Time / Day  <br/> |ProjectServer:QueueJobs  <br/> |
|Average Wait Time / Minute  <br/> |ProjectServer:QueueJobs  <br/> |
|Jobs Failed / Minute  <br/> |ProjectServer:QueueJobs  <br/> |
|Jobs Processed / Hour/Day  <br/> |ProjectServer:QueueJobs  <br/> |
|Jobs Processed / Minute  <br/> |ProjectServer:QueueJobs  <br/> |
|Jobs Retried / Minute  <br/> |ProjectServer:QueueJobs  <br/> |
|Average time taken for Project Open  <br/> |ProjectServer:Winproj  <br/> |
|Percentage of incremental save to full save  <br/> |ProjectServer:Winproj  <br/> |
|Winproj full open count in the last hour  <br/> |ProjectServer:Winproj  <br/> |
|Winproj full save count in the last hour  <br/> |ProjectServer:Winproj  <br/> |
|Winproj incremental open count in the last hour  <br/> |ProjectServer:Winproj  <br/> |
|Winproj incremental save count in the last hour  <br/> |ProjectServer:Winproj  <br/> |
   
## See also

#### 

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)