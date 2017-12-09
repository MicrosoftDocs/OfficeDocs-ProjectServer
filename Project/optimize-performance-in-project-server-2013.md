---
title: "Optimize performance in Project Server 2013"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/29/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 67cb4e6b-6140-438c-bb0e-f5100a1e6902
description: "Summary: Read guidelines for optimizing performance for a Project Server 2013 deployment."
---

# Optimize performance in Project Server 2013
 
 **Summary:** Read guidelines for optimizing performance for a Project Server 2013 deployment.
  
## Optimizations

This document and related content contains information and recommendations for tuning a Project Server 2013 farm for optimized performance.
  
### Baselining

Generally, we recommend that you limit the number of baselines that you have saved at any given time. There is a hard limit of only 11 baselines supported at a given time. 
    
### Database server optimizations

Given that Project Server 2013 is a data intensive application, optimizing your database tier can add considerable gains to performance. Please refer to SQL Server Storage Capacity Planning and Configuration topics for broad guidelines on optimizing your SQL Server settings. Some of the recommendations here highlight those made in the SQL Server topics:

- Separate the database files and the transaction log files away from the OS drives—preferably each to their own partition. This helps by reducing IO contention between the host operating system and SQL Server, and then also between SQL database files and log files, which tend to have different update patterns depending on what recovery strategy is used.

- Separate the TempDB onto its own partition. Split the database into several physical files—ideally, splitting it into as many files as you have processors on your database server.
            
Consider utilizing a RAID subsystem for your data needs.
> [!NOTE] RAID 5 is acceptable for medium and large dataset sizes, but RAID 10 is ideal.   
> [!NOTE] Move indexes onto their own partition. 
  
### Optimizing master projects

When you use the Master Projects functionality in Project Server, note that changes in the Master Project schedule will have an impact on the schedules of subprojects within the Master Projects. Therefore, schedule changes for very large Master Projects may execute slowly, because their subproject plans may need to be updated.
    
### Security setting optimizations

> [!NOTE] Optimizations are unnecessary if you are using SharePoint Permission Mode. 

In Project Permissions Mode, the security settings you select for your users can have a significant effect on performance characteristics. This is because they determine both the amount of data that users load when they view projects, and also the complexity of the security checks that are performed to determine which sets of data users have permissions on. 
   
For example, Administrators will have access to all of the projects that you have stored in Project Server, and they are therefore required to load all of the data when interacting with them. Team members may not need access to all the data, so we can limit the amount of data that is sent to them by using security categories:

- Use groups and categories where possible rather than more granular permissions that require additional complexity in the security checks.
- Try to restrain users' security permissions to the projects they need to have access to. That way, they load only the data they need to when interacting with Project Server.

### Views optimizations

- One should attempt to limit the data that is presented to users by restricting the number of columns in a given view to only the columns that users with permission on that view need to see. Also, note that adding Custom Field columns will have a more detrimental effect on view performance.
    
- You may also use filters to limit the amount of data that must be loaded when you are loading a particular view. Be aware, however, that filters with complex logic require additional computation, and may as a result slow down performance.
    
### Custom field optimizations

The performance impact of custom field usage depends on several aspects of the custom fields that are used (both Department and Enterprise custom fields). The following are some considerations and suggestions regarding the performance aspects of custom fields.

- The performance impact of your custom fields will depend on the following:
    
    - The performance impact of your custom fields will depend on the following:
        - The quantity of data stored in the custom fields you use. (Are they generally sparse, or are there large quantities of data in a given custom field column?)
        - For formula fields, the more complex the formulas employed, the more substantial the negative impact on performance will be.
        - The level the custom fields occur at:
    
  - The quantity of data stored in the custom fields you use. (Are they generally sparse, or are there large quantities of data in a given custom field column?)
    
  - For formula fields, the more complex the formulas employed, the more substantial the negative impact on performance will be.
    
  - The level the custom fields occur at. There are usually far more tasks than projects in a dataset and, therefore, custom fields applied at the task level will have a more substantial negative impact on performance than project level custom fields.
    
- Generally, the prescription is to try to limit the number of custom fields used, especially at the task level. As a general rule, try to use less than 10-15 task level Enterprise Custom Fields.
- Task and assignment custom fields are the primary bottleneck in saving from Project Professional to the server in most observed customer data sets.
  
    
### Local custom field optimizations

In accord with the recommendations about optimizing custom field use, optimize local formula field use by limiting the number of local formula fields used in the Project client.

The performance impact of your custom fields depends particularly on limiting the use of formula fields where possible, as they require additional data transfer that increase the time required for saving to the server.     
    
### Page payload optimizations

One of the most important factors in determining a given page's load time is the amount of data that needs to be accessed on a given page request. This is largely determined by the number of Web Parts and the types of Web Parts and how much data they present on a given page. The following are some general recommendations on limiting the payloads of your Project Server pages:    
   
  - Limit the amount of data that these Web Parts load to only the data that they need to be loading.
    
  - Payload considerations are particularly important for Project Detail Pages (PDPs), where there tend to be a larger number of Web Parts on a given page, and more customization occurs.
    
### Queue optimizations

> Project Server 2013 utilizes a queuing system to handle how it services requests, enabling it to serve a greater number of requests overall. Certain settings related to how the queue operates can be altered through the Queue Settings page. This section gives a brief explanation of the settings you can modify, and how to optimize them for your needs.
Max Number of Threads (1-20, default 4): This determines how many jobs the queue can process in parallel at any given time. Note that this applies to all machines in the farm—if you have three Application servers, and you set this value to 4 for the project queue, you can process up to 12 independent project jobs at a time.

Max Number of Threads (1-20, default 4): This determines how many jobs the queue can process in parallel at any given time. Note that this applies to all machines in the farm—if you have three Application servers, and you set this value to 4 for the project queue, you can process up to 12 independent project jobs at a time.
    
If you find that queued jobs are taking an excessive amount of resources away from a synchronous workload, you can try the following: 
    
If you have a large number of jobs that are processed in parallel (that is, you see multiple jobs in the "processing" state at the same time when you check the queue status), you can try reducing the thread count.
    
### Workload process optimizations

Certain aspects of how you operate and maintain your Project Sever deployment can help improve the perceived performance of Project Server. This section covers a list of Business- or IT-related process modifications that can help to improve the perceived performance of your Project Server during periods when your users are most likely to interact with the system.

- Timesheeting and status submissions:
    - If possible, try to stagger the times when users submit status updates and timesheets. This will act to reduce the strain on the system during peak periods by distributing the load over larger time intervals.
- Backups:
    - If possible, you should try to run backup processes during non-peak periods, as these are resource intensive processes that will diminish perceived performance for users attempting to use the system while they are running.
- Reporting:
    - As with backup processes, you should try to run the building of OLAP cubes for reporting during non-peak periods, as these are resource intensive processes that will diminish perceived performance for users attempting to use the system while they are running.
- SharePoint Permissions mode:
    - If SharePoint Permissions mode is enabled "SharePoint User Sync" is not required thus allowing better performance.   
    
### Workflow optimizations

When you are using the Workflows functionality, be aware of the following actions that will take a toll on the performance of your deployment:
- It can take a long time to load the "Change or Restart Workflows" page in Server Settings when you have a large number of projects stored in the database.
- Restarting or changing the EPT for a large number of projects from Change or Restart Workflows page in Server Settings.
- Having an approval process with a very large number of users.
- Having projects submitted at the same time from a workflow stage without check-in required.
    
Generally, we recommend minimizing these actions, or executing them at low-traffic periods to optimize perceived performance.
    
### Custom solution (programmability) optimizations

When you develop custom solutions that interact with the Project Server Programmable Interfaces, take into account the following performance recommendations:

- If you are deploying event handlers, be aware that the event handlers are synchronous. You should be careful when employing event handlers in your custom solutions, as if utilized ineffectively they can substantially increase the performance of Project Server.
    > [!NOTE]
    > Event handlers can be run off on another machine.
- Your custom solution should try to throttle calls it makes to queuing operations in the Project Server to prevent overloading the queue. 
- For Line of Business (LOB) Applications, when you automate data movement between Project Server and other applications, if you notice that syncs with these types of applications are substantially degrading performance, it is advised to run them during non-peak usage periods. 
    - We highly recommend that customers test and monitor their LOB application performance, in addition to their user-facing performance.
    - Where possible, try to utilize intrinsic Project Server fields rather than custom fields to achieve the sync that you desire between Project Server and the LOB applications.
    - Try to minimize the data you are moving between LOB applications and Project Server to the smallest subset you need for achieving the desired functionality.


 The Project Server 2013 SDK and related articles make further recommendations about maintaining high performance when developing custom solutions.
    
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

