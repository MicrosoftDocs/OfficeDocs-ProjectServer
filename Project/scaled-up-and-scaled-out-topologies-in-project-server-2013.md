---
title: "Scaled-up and scaled-out topologies in Project Server 2013"
ms.author: efrene
author: efrene
ms.prod: scotv
ms.date: 11/29/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: f26b7a86-d834-4c45-a079-df4f71bf8580
description: "Summary: Learn how to increase the capacity of existing servers or add more servers to the topology of your Project Server 2013 installation."
---

# Scaled-up and scaled-out topologies in Project Server 2013
 
 **Summary:** Learn how to increase the capacity of existing servers or add more servers to the topology of your Project Server 2013 installation.<br/>
**Applies to:** Project Server 2013
  
This article covers performance and capacity planning scaled-up and scaled-out topologies for a Project Server deployment. This document and related content contains information and recommendations for how to scale-up or scale-out a Project Server 2013 farm.
  
## Scaled-up and scaled-out topologies for Project Server 2013 deployments

To increase the capacity and performance of your topology you can do two things. You can scale up by increasing the capacity of your existing server computers and scale out by adding additional servers to the topology.
  
Monitoring resource usage on your Project Server 2013 deployment servers can give insights into which strategy you will want to pursue: scaling-up versus scaling-out. The performance metrics that can help inform your decisions are discussed in [Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md).
  
The physical servers that you deploy Project Server 2013 on will play the following server roles: 
  
- Web Front End
    
- Application Server
    
- Database (SQL) Server
    
In a single-machine deployment, one physical server plays all three of these roles. You can scale out by dividing ownership of these roles amongst different physical machines (optionally, they could also be virtual machines. Read the "Virtualization" section of [Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md) for additional guidelines about virtualization). The first step you should take when starting to scale out is to separate the Database (SQL) Server role onto its physical machine, while having the other physical machine act as the Web Front End and Application Server.
  
> [!NOTE]
> Project Server 2013 only provides limited scale-out capabilities. While additional servers can be added to act as front-end web servers and Application servers, on the back end the computer that is running SQL Server has limited scale-out possibilities. 
  
### To provide for more user load

- Scale-out by adding more web servers to serve as dedicated Application and front-end web servers.
    
- Note that as you add more front-end web servers and Application servers, the load on computer that is running SQL Server will increase, and your SQL Server could in turn become your bottleneck.
    
- You may also scale up any front-end web or Application server to improve performance by increasing the hardware capacity of those servers.
    
### To provide for more data load

- To provide for more data load, add capacity to the database server by increasing the capacity of that single server.
    
- Separate the Project Database from the SharePoint Databases by moving the Project database onto its own dedicated database server.
    
    > [!NOTE]
    > Project Server 2013 does not support scaling out the Database component through SQL replication. While it is possible to perform SQL mirroring on a Project SQL Server for the purposes of backing up data, Project Server 2013 is unable to take advantage of SQL replication to reduce read loads on the SQL Server. 
  
 **Recommended server role ratio:**
  
- As a general rule, a recommended ratio for maintaining a manageable load on the SQL Server is:
    
  - 2 Web Front Ends : 1 Application Server : 1 SQL Server
    
    > [!NOTE]
    > This recommended ratio might not apply for deployments utilizing more robust hardware, especially for the database server. 
  
    > [!NOTE]
    > The recommended ratio also varies based on the data set size, and the usage patterns. For example, larger data sets would constrain the ability to fan-out, requiring a smaller ratio of Web Front Ends and Application Server to the SQL Server. 
  
 **Isolate the Project Server database from SharePoint Server:**
  
- As previously mentioned, it is possible to separate the Project Server database from the SharePoint databases, by placing it on its own dedicated database server.
    
- We also recommend that you separate at the application tier level. While Project Server is a SharePoint service, we recommend that you have that application instance run on a dedicated server.
    
 **How to spend money on scaling up and out:**
  
- As a general rule, in the early stages of scaling your Project Server deployment, you will want to invest primarily in purchasing additional memory. Most often, the subsequent areas you would want to invest in are disk spindles, and then network resources.
    
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

