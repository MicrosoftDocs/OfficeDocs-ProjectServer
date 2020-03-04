---
title: "Overview of performance and capacity planning in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: 97cfb11d-5ba3-469c-a52b-f8b4d014b8e8
description: "Summary: Performance and capacity planning concepts are a vital part of planning a Project Server deployment."
---

# Overview of performance and capacity planning in Project Server 2013
 
 **Summary:** Performance and capacity planning concepts are a vital part of planning a Project Server deployment.<br/>
**Applies to:** Project Server 2013
  
This document and related content contain information and recommendations for how to determine the hardware requirements for a Project Server 2013 farm.
  
This article identifies the characteristics that affect your capacity requirements, and it provides recommendations for the following:
  
- Number of server computers in the server farm
    
- Configuration of application server roles in the server farm
    
- Hardware requirements for specific server roles in the server farm
    
## Planning for capacity vs. availability in Project Server 2013 deployments

This chapter assumes that you have already planned for availability requirements by using the [IT Pro Planning for Project Server 2016](it-pro-planning-for-project-server-2016.md) articles. As a result of using those articles, you will start the capacity planning exercise with a topology that meets your organization's minimum availability requirements. Given the topology you have selected, this chapter helps you determine the following:
  
- Whether you have to add more servers to meet your goals for capacity and performance
    
- Whether you have to adjust the configuration of application server roles to optimize capacity and performance of the server farm
    
- Whether you have to plan for more than one server farm based on your capacity requirements
    
In some cases, an organization's requirements for availability can result in a server farm size that provides much larger capacity or performance than is otherwise required. If this is the case, capacity planning can focus on sizing the server hardware economically, instead of adding additional server computers or scaling up with higher-performing hardware.
  
In many cases, the topology that meets an organization's minimum availability requirements is used as a starting point and server computers are added or scaled up to meet capacity and performance goals.
  
## Capacity planning approach for Project Server 2013

There are many variables that affect capacity planning. For this reason, it can be difficult to receive a crisp answer to a straightforward question. Consequently, the most common answer to a capacity-related question is, "It depends … ." 
  
The capacity planning exercise provided in this documentation set is designed to reduce the number of variables in consideration so that straightforward answers can be provided based on common scenarios. However, this chapter also includes the guidance for calculating your capacity and performance requirements based on your individual solution characteristics. This chapter includes two kinds of capacity planning guidance:
  
- **Recommendations for estimating capacity requirements** A series of articles is provided, based on targeted scenarios. Each article defines a typical usage profile and identifies the key characteristics that will affect capacity and performance for the scenario. Based on the profile and key characteristics, predefined data lets you estimate capacity requirements for your solution.
    
- **Formulas and guidance for calculating specific capacity requirements** Using this guidance, you can develop your own usage profile (or modify one of the scenario profiles) and calculate all of the variables that affect the capacity and performance of your solution.
    
## Capacity planning process for Project Server 2013 deployments

Capacity planning focuses on three aspects of sizing your solution:
  
- **Capacity boundaries of the software** Each of the features that can be implemented and the objects that can be created have scale limitations. Planning for capacity boundaries ensures that your solution design fits within the scale recommendations of the software.
    
- **Throughput targets** Each kind of action that is performed by a server farm introduces a performance load on the server hardware. Primary actions include user operations, indexing of content, and operations tasks (such as backing up the databases). The use of specific features, such as Excel Calculation Services, although necessary for cube building, also adds a performance load. Developing throughput targets involves estimating or calculating the number of operations per second that a server farm must process in order to support the expected throughput load.
    
- **Data capacity** Data capacity includes the expected volume of content databases and the configuration database. Each server role also has unique data requirements based on the solution, such as disk space for content indexes or for cached content.
    
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

[Typical Datasets (Project Server 2013)](https://technet.microsoft.com/library/e2a0a4b6-0bda-468e-aeca-00f2807bf644.aspx)

