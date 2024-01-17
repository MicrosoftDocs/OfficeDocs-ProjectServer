---
title: "Capacity planning strategy for Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: e594b254-aee8-4ec3-801c-d2948cf3e42a
description: "Summary: Performance and capacity planning strategy is a vital part of planning a Project Server deployment."
---

# Capacity planning strategy for Project Server 2013
 
 **Summary:** Performance and capacity planning strategy is a vital part of planning a Project Server deployment.<br/>
**Applies to:** Project Server 2013
  
This article and related articles contain information and recommendations for how to determine the hardware requirements for a Project Server farm.
  
The performance and capacity planning strategies outlined provide guidance on the footprint that the usage of Project Server 2013 has on topologies running SharePoint Server 2013. 
  
## Estimating throughput targets in Project Server

Many factors can affect throughput. These factors include the number of users; the type, complexity, and frequency of user operations; the number of postbacks in an operation; and the performance of data connections. Each of these factors can have a major impact on farm throughput. You should carefully consider the factors discussed in this section when you plan your deployment.
  
Project Server 2013 can be deployed and configured in a wide variety of ways. As a result, there is no simple way to estimate how many users can be supported by a given number of servers. Therefore, make sure that you conduct testing in your own environment before you deploy Project Server 2013 in a production environment.
  
In many cases, the topology that meets an organization's minimum availability requirements is used as a starting point and server computers are added or scaled up to meet capacity and performance goals. When you undertake your capacity planning for Project Server 2013, you need to be aware of the variables that can affect the performance of a Project Server deployment.
  
Because of the rich functionality set that Project Server provides, deployments that seem similar when described at a high level can differ substantially in their actual performance characteristics. It's not enough to characterize your demands by just the number of projects, or the number of users you will have in the system. Thinking about the performance of your Project Server deployment requires a more nuanced and holistic approach. For example, workloads, and subsequently your hardware needs, will differ in relation to the following variables:
  
1. Projects:
    
   - Number of projects
    
   - Typical project sizes in terms of tasks
    
   - Number of project level custom fields
    
   - Level of linking (dependencies) between tasks
    
2. Users:
    
   - Concurrency of users. How many users will be hitting the system at the same time? What is the average load, what are the spikes in traffic?
    
   - What security permissions do users have? This affects both the amount of data the server needs to present to the user at a given time, along with the complexity of the security checks the server has to do.
    
   - Geographic distribution of users. When users are spread over large geographical areas there can be detrimental performance effects due to network latency. This also impacts usage patterns insofar as users are likely to hit servers at different times during the day, making it harder to find low-traffic periods in which to run maintenance tasks such as backups, reporting, or Active Directory sync.
    
3. Usage patterns:
    
   - Workload conditions. Which set of features are being commonly utilized? For example, a deployment that uses time-sheeting heavily will have different characteristics than one that does not use time-sheeting.Number of projects
    
   - Average time between page requests.
    
   - Average session time.
    
   - Payload of Pages (How many Web Parts do you have on a given page? How much data do they contain?)
    
To help you in your capacity planning, we define three data sets, which we have found to characterize small, medium, and large Project Server deployments. For each of these data sets, we then recommend one of three "rule-of-thumb" hardware topologies that should approximately satisfy the needs of similar datasets. With these starting point topologies in mind, we highlight factors that may require you to adjust these hardware topologies, outlining how you should evaluate if you need to decrease or increase the allocated resources to scale to your particular needs. 
  
The approach you should take in your capacity planning is as follows:
  
1. Determine which of the datasets (small, medium, or large), is the closest match to your expected dataset. This is covered in [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md).
    
2. Use the hardware topology we recommend for that dataset size as a starting point approximation for what your needs will be. 
    
    > [!NOTE]
    > It is important to realize that the needs of your particular dataset and usage patterns may require either fewer or more hardware resources than that approximate topology. [Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md) goes into depth about how you can assess whether you should add more resources to the topology, and where to add them.
  
3. Monitor your application's performance by using the guidelines we outline in the [Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md) topic. In those topics we specify the key metrics you will want to track to determine when and how you need to scale your topology.
    
4. Optimize your deployment according to the suggestions provided in [Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md). 
    
5. Depending on your chosen topology, your dataset, your usage patterns, and the performance metrics you observe, follow the recommendations on scaling given in the following articles:
    
   - [Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md) : This article gives advice regarding the type of strategy you should pursue when scaling depending on your current needs. Should you purchase additional servers, or should you purchase additional resource capacity (memory, CPU, disk) for the servers you already have?
    
   - Common Project Server 2013 Bottlenecks and their Causes: This section in the [Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md) topic describes the likely source of bottlenecks in your system, how you might spot them through monitoring, and how issues related to these bottlenecks can commonly be resolved.
    
## See also

[Overview of performance and capacity planning in Project Server 2013](overview-of-performance-and-capacity-planning-in-project-server-2013.md)
  
[Capacity planning strategy for Project Server 2013](capacity-planning-strategy-for-project-server-2013.md)
  
[Performance and capacity hardware recommendations for Project Server 2013](performance-and-capacity-hardware-recommendations-for-project-server-2013.md)
  
[Scaled-up and scaled-out topologies in Project Server 2013](scaled-up-and-scaled-out-topologies-in-project-server-2013.md)
  
[Optimize performance in Project Server 2013](optimize-performance-in-project-server-2013.md)
  
[Performance counters in Project Server 2013](performance-counters-in-project-server-2013.md)
  
[Performance troubleshooting in Project Server 2013](performance-troubleshooting-in-project-server-2013.md)

[Typical Datasets (Project Server 2013)](./project-server-2013-and-2016.md)