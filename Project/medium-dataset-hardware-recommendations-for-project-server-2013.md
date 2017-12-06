---
title: "Medium dataset hardware recommendations for Project Server 2013"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/29/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: d25851d2-708a-4ba9-961a-21d8231a4f30

description: "Summary: Learn the system requirements such as RAM, disk space, processor speed for server hardware for Project Server 2013."
---

# Medium dataset hardware recommendations for Project Server 2013
 
 **Summary:** Learn the system requirements such as RAM, disk space, processor speed for server hardware for Project Server 2013.
  
## Minimum requirements for hardware for Project Server 2013

For a medium dataset, we suggest that as a minimum you have a dedicated Web server, Application server and computer that is running SQL Server. This is what is referred to as a 1×1×1 topology. The recommended hardware specifications for each of the servers are stated following the diagram. [Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md) gives more instructions on how to achieve this separation of the tiers across multiple servers.
  
**Minimum requirements for a front-end Web server**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single server and multiple server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**Minimum requirements for an Application server**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single server and multiple server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**Minimum requirements for a computer running SQL Server**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core(if your dataset size is considerably larger than the medium dataset, 8 cores are recommended)  <br/> |
|RAM  <br/> |16 GB  <br/> |
|Hard disk  <br/> |100 GB  <br/> |
   
In some cases people use the SharePoint Server 2013 instance that Project Server is installed on top of as their primary SharePoint Server deployment. For small databases this may be a feasible approach, but we recommend against it for medium and large databases. If the SharePoint Server 2013 instance that Project Server 2013 is coexisting with also gets heavy usage (that is, you are not using it specifically for Project Server 2013 functionality), then you can separate the Project Server 2013 ProjectService database from the SharePoint Server 2013 content databases. You can do this by placing the Project Server 2013 ProjectService database on its own dedicated instance of SQL Server. 
  
## Recommended hardware for Project Server 2013

The minimum requirements specified for medium sets can be scaled-out and scaled-up to handle additional load. [Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md) discusses considerations about how to handle increased user load and increased data load. If your dataset is substantially larger than the medium dataset or you heavily use some of the features that generate additional data load, such as timesheets, then we advise you to take some of the measures described in[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md) to handle your additional user and data load.
  
As a general prescription, you should prepare for additional user load and data load by having sufficient computers to add additional front-end Web servers and Application servers to your topology. The hardware specifications of your front-end Web servers and Application servers can remain largely the same. A 4 x 2 x 1 topology should be sufficient for handling the needs of most medium datasets and usage patterns. 
  
Note that scaling out your Application and front-end Web servers adds more load to SQL Server, which you will have to compensate for by adding more memory and CPU resources. The following SQL Server specification should be able to handle the performance needs of most medium datasets.
  
**SQL Server database recommendations for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, eight-core, 2.5 GHz minimum per core (If your dataset size is considerably larger than the medium dataset, 8 cores are recommended.)  <br/> |
|RAM  <br/> |32 GB  <br/> |
|Hard disk  <br/> |160 GB  <br/> > [!NOTE]> Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks.           > [!NOTE]> RAID 5 should provide a good compromise between reliability, and throughput           |
   
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

