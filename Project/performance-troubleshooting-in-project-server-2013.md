---
title: "Performance troubleshooting in Project Server 2013"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 1223bffd-7e67-48cb-aee7-b6c5027ace16
description: "Summary: Read troubleshooting information for common bottlenecks and their causes in Project Server 2013."
---

# Performance troubleshooting in Project Server 2013
 
 **Summary:** Read troubleshooting information for common bottlenecks and their causes in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
During performance testing, several different common bottlenecks can be revealed. A bottleneck is a condition in which the capacity of a particular constituent of a farm is reached. This causes a plateau or decrease in farm throughput.
  
By monitoring your performance using the guidelines specified in the Performance Monitoring section, you may be able to better identify which bottlenecks are impacting the perceived performance of your Project Server deployment. 
  
## Common bottlenecks, causes, and resolutions

The following table lists some common bottlenecks and describes their causes and possible resolutions:
  
|**Bottleneck**|**Cause**|**Resolution**|
|:-----|:-----|:-----|
|Database contention (locks)  <br/> |Database locks prevent multiple users from making conflicting modifications to a set of data. When a set of data is locked by a user or process, no other user or process can modify that same set of data until the first user or process finishes modifying the data and relinquishes the lock.  <br/> | To help reduce the incidence of database lock contention you can: <br/>  Scale up the database server. <br/>  Tune the database server hard disk for read/write. <br/> |
|Database server disk I/O  <br/> |When the number of I/O requests to a hard disk exceeds the disk's I/O capacity, the requests will be queued. As a result, the time to complete each request increases.  <br/> |Distributing data files across multiple physical drives allows for parallel I/O.  <br/> Limit the number of projects and fields shown in a given view, so that limit the amount of data requested from the Database server.  <br/> Try to limit the number of custom fields you utilize, especially at the task level. Formula fields at the task level are particularly costly in terms of database server disk I/O when performing save operations from Project Professional.  <br/> |
|Front-end web CPU utilization  <br/> |When a WFE is overloaded with user requests, average CPU utilization will approach 100 percent. This prevents the WFE from responding to requests quickly and can cause timeouts and error messages on client computers.  <br/> |This issue can be resolved in one of two ways. You can add additional WFE servers to the farm to distribute user load, or you can scale up the Web server or servers by adding higher-speed processors.  <br/> |
|Server Memory Utilization  <br/> |When you have a substantial number of large queue jobs executing, the server memory utilization can spike.  <br/> More complex server side scheduling calculations, or evaluation of formula custom fields, can also consume substantial memory resources.  <br/> As a result, the time to complete each request increases.  <br/> | Monitor at which tier memory usage is a bottleneck:that is, is the memory scarcity happening on the Application server, the front-end web server, or the database server. <br/>  To resolve the lack of memory there are two options: <br/>  Purchase and install additional memory for that tier. <br/>  Purchase additional application servers to handle the load. <br/> |
|Active Directory Sync  <br/> |Project Server users and resources can be synchronized with the users of the service across multiple domains and forests. This feature helps administrators with tedious tasks, such as manually adding large numbers of users, updating user metadata such as email addresses, and deactivating users who no longer require system access. Active Directory synchronization can be done manually or on an automated schedule. The process of synchronization is resource intensive  <br/> |It is best to run Active Directory Sync during non-peak user usage periods. That way, Active Directory Sync will not degrade the perceived performance of users.  <br/> In addition, try to avoid heavily nested groups, as they increase the complexity of the sync that must be performed, and result in longer sync processes.  <br/> |
|Application Server CPU  <br/> | Application Server CPU can be hit hard when: <br/>  Scheduling complex projects. <br/>  Evaluating formulas on complex projects/ <br/>  Running portfolio analyses on a large number of projects with Time-phased Resource Planning analysis turned on. <br/> |Monitor the Application Server's CPU usage, and if it seems that it is utilizing a high percentage of its CPU resources, then add an additional Application Server to your topology to distribute the load.  <br/> Note that adding an additional Application Server will add additional threads that could cause increased load on the Database Server. This could create a new bottleneck on the database server, which may be resolved by allowing fewer Job Processor Threads in the Queue Settings.  <br/> |
|Database Server CPU  <br/> |Usually, database server CPU spikes when try to load views that comprise of a large number of projects, and a large number of fields shown. This will reduce the perceived user response time when that view is applied.  <br/> |Limit the number of projects and the number of fields shown in a given view.  <br/> |
   
## See also

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)