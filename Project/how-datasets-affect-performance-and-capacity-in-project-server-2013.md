---
title: "How datasets affect performance and capacity in Project Server 2013"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 5dbcb4c9-9837-4508-907a-78e4b07eef81
description: "Summary: As you plan performance and capacity of a Project Server 2013 deployment, consider the set of variables that affect your plans."
---

# How datasets affect performance and capacity in Project Server 2013
 
 **Summary:** As you plan performance and capacity of a Project Server 2013 deployment, consider the set of variables that affect your plans.<br/>
**Applies to:** Project Server 2013
  
## Typical datasets in Project Server 2013

The datasets described in this article are characterized by the variables listed and explained in the table below. These variables may not capture all of the factors that affect the performance of Project Server. (That is, they do not capture the mix of features you tend to use in your deployment.) However, they do capture much of the information that is significant in determining appropriate capacity.
  
**Factors that affect performance in Project Server 2013**

|**Entity**|**Description/Notes**|**Small**|**Medium**|**Large**|
|:-----|:-----|:-----|:-----|:-----|
|Projects  <br/> ||20  <br/> |100  <br/> |5000  <br/> |
|Project Sites  <br/> ||20  <br/> |100  <br/> |5000  <br/> |
|% Projects in Managed Mode  <br/> ||0%  <br/> |10%  <br/> |80%  <br/> |
|Tasks  <br/> ||1250  <br/> |25000  <br/> |1250000  <br/> |
|Average Tasks Per Project  <br/> ||62.5  <br/> |250  <br/> |250  <br/> |
|Task Transaction History  <br/> |The number of times status tends to be submitted and approved for any given task  <br/> |10  <br/> |10  <br/> |100  <br/> |
|Assignments  <br/> ||1625  <br/> |32500  <br/> |1625000  <br/> |
|Average Assignments Per Task  <br/> ||1.3  <br/> |1.3  <br/> |1.3  <br/> |
|Average Tasks per My Site User  <br/> ||50  <br/> |250  <br/> |5000  <br/> |
|Approvals  <br/> |Pending updates per manager  <br/> |5  <br/> |50  <br/> |600  <br/> |
|Resources  <br/> ||50  <br/> |1000  <br/> |10000  <br/> |
|Average Resources Per Project  <br/> ||2.5  <br/> |10  <br/> |20  <br/> |
|Average Assignments Per Resource  <br/> ||32.5  <br/> |32.5  <br/> |162.5  <br/> |
|Users  <br/> ||50  <br/> |1000  <br/> |10000  <br/> |
|Calendars  <br/> ||3  <br/> |26  <br/> |100  <br/> |
|Issues  <br/> ||20  <br/> |400  <br/> |20000  <br/> |
|Risks  <br/> ||20  <br/> |400  <br/> |20000  <br/> |
|Deliverables  <br/> ||20  <br/> |800  <br/> |40000  <br/> |
|Enterprise Project Types  <br/> |||5  <br/> |50  <br/> |
|Workflows  <br/> |||2  <br/> |30  <br/> |
|Average Projects Per Workflow  <br/> |||50  <br/> |167  <br/> |
|Phases  <br/> |||5  <br/> |50  <br/> |
|Phases Per Enterprise Project Type  <br/> |||20  <br/> |20  <br/> |
|Stages  <br/> |||15  <br/> |150  <br/> |
|Stages Per Workflow  <br/> |||20  <br/> |40  <br/> |
|PDPs  <br/> |||10  <br/> |100  <br/> |
|Custom Fields Per PDP  <br/> |||10  <br/> |10  <br/> |
|Number of Departments  <br/> ||||100  <br/> |
|Average Projects Per Department  <br/> ||||50  <br/> |
|Average Resources Per Department  <br/> ||||100  <br/> |
|Timesheets Per Year  <br/> |The more you utilize timesheets, the more resource demands will be placed on SQL Server.  <br/> |2600  <br/> |52000  <br/> |780000  <br/> |
|Status Reports Per Year  <br/> |||26000  <br/> |260000  <br/> |
   
> [!NOTE]
> In our dataset size descriptions, the number of custom fields includes only the enterprise custom fields, not department custom fields. Department custom fields have essentially the same effect on the performance of Project Server 2013 as enterprise custom fields do. Therefore, if you have a large number of departmental custom fields (especially at the task level) you will require additional resources to support this. The prescriptions that are made regarding custom fields throughout this document apply to both enterprise custom fields and department custom fields. 
  
## Other performance and capacity variables to consider in Project Server 2013

Concurrency of users: 
  
- Concurrent user load is often a significant factor in setting capacity requirements. You may have fewer users in the system, but they may all transact with the server simultaneously during your "peak" traffic periods. For example, an organization that has its users all submit status/timesheet updates at the same time of the week will likely notice a substantial decrease in performance during those periods. If you have heavy peak usage periods, you should add more resources to the topology recommended for your dataset.
    
Split of user roles:
  
- The distribution of your users between Administrators, Portfolio Administrators, Project Managers, and Team Members will affect the performance of your deployment insofar as each type of user has access to a varying amount of data. Users in different security categories may vary with regard to how many projects and resources they may be able to see. Administrators, for example, will be able to see all projects on the server when loading Project Center, and all resources when they load Resource Center. In comparison, a Project Manager may be able to see only his or her own projects. The result is that these users may be subject to a diminished perceived performance. Where possible, we suggest you limit the number of projects, tasks, or resources shown in a given view by defining appropriate filters in the views that you define in the >Manage Views section of Server Settings.
    
Issues, risks, and deliverables:
  
- Having larger numbers of these entities may place additional load on SQL Server. In particular, it is the act of viewing and interacting with these entities in the project site that is likely to create the additional load. If you use these features heavily, you may want to allocate additional resources to SQL Server to maintain a high level of performance. These artifacts and the project site functionality are SharePoint sites and lists, so for scaling these aspects of Project Server 2013, consult documentation around scaling SharePoint sites and lists.
    
Custom Calendars:
  
- Custom calendars can be defined for projects, tasks and resources. These largely impact the scheduling engine, causing higher processor usage on the Application and Database servers.
    
## See also

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)