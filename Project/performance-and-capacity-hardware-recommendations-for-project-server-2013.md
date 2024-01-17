---
title: "Performance and capacity hardware recommendations for Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 207dc8bd-b5d9-42db-a340-40dce88eb180
description: "Summary: Use these hardware recommendations regarding performance and capacity for Project Server 2013 to identify a suitable starting topology for your requirements."
---

# Performance and capacity hardware recommendations for Project Server 2013
 
 **Summary:** Use these hardware recommendations regarding performance and capacity for Project Server 2013 to identify a suitable starting topology for your requirements.<br/>
**Applies to:** Project Server 2013
  
They will also help you decide whether you have to scale out or scale up the starting topology.
  
Throughout this set of articles we refer to three different server roles: the Web Front End Server role, Application Server role, and Database (SQL) Server role. These are all components of a complete Project Server 2013 deployment. The front-end Web servers act as the interface for users accessing Project Server. The Application server handles the requests to the data tier of Project Server, and implements the business logic of Project Server 2013. Lastly, the database tier is the data source, housing the Project Server 2013 database. For small deployments, the Web Front End Server, Application Server, and Database Server roles may be combined on the same physical computer. For larger deployments it may be necessary to separate these onto separate computers, even having multiple physical computers acting in the same role.
  
## Hardware requirements and recommendations for Project Server 2013

This section suggests a minimum requirement and a recommended topology for each of the small, medium, and large dataset sizes characterized in [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md). The minimum requirement is a topology that will be functional with the given data set, but may suffer from substantially decreased perceived performance. The recommended topologies for each dataset should be sufficient for obtaining reasonable performance with most usage patterns on those dataset sizes. However, we encourage you to take into account the specific recommendations given throughout the rest of this document for determining if you will need to expand beyond the topology that is recommended for your approximate dataset. In general, you should monitor the performance metrics of your topology, and scale it accordingly if you are unsatisfied with the performance characteristics. 
  
[Small dataset hardware recommendations for Project Server 2013](small-dataset-hardware-recommendations-for-project-server-2013.md)
  
[Medium dataset hardware recommendations for Project Server 2013](medium-dataset-hardware-recommendations-for-project-server-2013.md)
  
[Large dataset hardware recommendations for Project Server 2013](large-dataset-hardware-recommendations-for-project-server-2013.md)
  
## Virtualization recommendations for Project Server 2013

Project Server 2013 supports running on virtual machines. Most of the advice given for virtualization of SharePoint Server 2013 also applies to Project Server 2013. However, as in any situation where virtualization is employed, it is important to consider contention for the physical machine's resources between virtualized machines running on the same physical instance.
  
We do not recommend running SQL Server on a virtualized machine. The competition for resources on a virtualized machine can substantially decrease the performance of SQL Server. If you must run SQL Server in a virtual environment, we recommend that you use the following settings:
  
- Network Adapter:
    
  - If you are using Hyper-V virtualization, you should utilize the virtual network adapter rather than the legacy network adapter.
    
- Virtual Disk: 
    
  - For the virtual machine that you are running SQL Server on, we recommend that you select the "pass through" option for the disk type (rather than dynamic, or fixed). If this is not an option, you should utilize a fixed disk size rather than a dynamically sized virtual disk.
    
  - We recommend that you select IDE over SCSI for your boot drive.
    
  - Allocate sufficient hard disk space to handle the expected maximum size of your dataset and ULS logging demands.
    
- Memory:
    
  - You should allocate as much memory to the virtual machine that is running SQL Server as can feasibly be allocated. This should be comparable to the amount of memory required/recommended for physical boxes serving the same function.
    
  - You need to also account that some memory needs to be reserved for the host operating system. At least 2 GB of memory should be reserved for the host operating system. 
    
Running the Web Front End or Application Servers in virtualized environments tends to not be as detrimental to the performance of running SQL Server in a virtual environment. 
  
## Network requirements for Project Server 2013 deployments

For most Project Server deployments, network bandwidth tends to not be the bottleneck on performance. The table below lists the recommended specifications of network components.
  
|**Component**|**Small and medium**|**Large**|
|:-----|:-----|:-----|
|# of NICs  <br/> |1  <br/> |2  <br/> |
|# NIC Speed (Network)  <br/> |Any speed greater than 100mbps should be fine  <br/> |1 Gb/s  <br/> |
|Load Balancer Type  <br/> |NLB or hardware, both are acceptable  <br/> |NLB or hardware, both are acceptable  <br/> |
   
A general aim should be to maintain low latency between the Application and SQL Server tiers.
  
## See also

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)