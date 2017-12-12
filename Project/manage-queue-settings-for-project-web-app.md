---
title: "Manage Queue Settings for Project Web App"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: d24af5d0-8743-4436-acd4-bedab330648f
description: "Use the Manage Queue Settings for Project Web App page to configure Project Queue settings in Project Server 2013."
---

# Manage Queue Settings for Project Web App
 
Use the Manage Queue Settings for Project Web App page to configure Project Queue settings in Project Server 2013.
  
In Project Server 2013, Queue settings are no longer applicable to individual Project Web App instances, but now apply to all Project Web App instances that are created in the Project Service Application. Additionally, because the Queue is now located at the Project Service level, the Manage Queue Settings page can be accessed in the SharePoint Central Administration website instead of Project Web App.
  
> [!IMPORTANT]
> Project Server 2013 Queue performance has increased significantly from the previous version because of many changes that were implemented for this release. The default values are the recommended queue settings for optimal performance. 
  
## Before you begin

If you are sure you need to change the default Queue settings, you need to be at least a Service Application Administrator for the Project service application. This is the least privileged permission level required.
  
The Manage Queue Settings page can be accessed in the Project Service Application page in Central Administration. Use the following procedure to access the Manage Queue Setting page in the Project Service Application page:
  
### To access the Manage Queue Setting page

1. In Central Administration, in the Application Management section, under Service Applications, click **Manage service applications**.
    
2. On the Manage service application page, click the name of the Project service application.
    
3. On the Manage Project Web Apps page, click **Manage Queue Settings for Project Web App**.
    
> [!IMPORTANT]
> Verify with your Project Server Administrator before you make changes to your default Queue settings. Changes will affect the way that queue jobs are processed, and will affect all Project Web App instances that were created under the Project Service Application. 
  
## Queue settings

The Manage Queue Settings for Project Web App page allows you to change the following Queue settings:
  
- Maximum Degree of Concurrency
    
- Retry Interval
    
- Retry Limit
    
- SQL Timeout
    
- Cleanup Age Limit for Successful Jobs
    
- Cleanup Age Limit for Unsuccessful Jobs
    
- Bookkeeping Interval
    
- Queue Timeouts
    
> [!IMPORTANT]
> The **SQL Retry Interval** and **SQL Retry Limit** settings that display on this page are obsolete in Project Server 2013 and will be removed in a future update. Do not use these settings.
  
### Maximum Degree of Concurrency

Because the Queue is multithreaded, multiple jobs that are sent to the queue can be processed at the same time. The Maximum Degree of Concurrency setting limits the number of jobs that can be processed at the same time, by setting the maximum number of job processor threads that are available in the Queue. The valid range is 1 through 10, with a default value of 4. 
  
In Project Server 2013, the value for this setting acts as a multiplier of the number of cores on the application server. For example, if your application server is using a dual-core processor, and the Maximum Degree of Concurrency is set at the default value of 4, the maximum number of jobs that can be processed at the same time is 8. If you have multiple application servers, this setting applies to each server on which the Project Server application service is running. For example, if you have two application servers that have dual-core processors, and the Maximum Degree of Concurrency is set at the default value of 4, each server can process up to 8 jobs at the same time. 
  
### Retry Interval (in milliseconds)

The **Retry Interval** setting lets you set the length of time (in milliseconds) between retries for jobs that have failed because of transient issues, such as a SQL time-out. If the processing job fails, instead of failing the job, the Queue will wait for the time set by the Retry Interval value, and then will retry the job. The valid range is 0 (immediate retry) to 60000 (1 minute), with a default value of 1000 (1 second).
  
### Retry Limit

The **Retry limit** setting lets you set the maximum number of times a failed processing job will be retried. If the job does not process because of transient issues, such as a SQL time-out, instead of failing the job, the Queue will retry the job. The number of retries attempted is set by the value entered for this setting. Note that the amount of time between retries is set by the Retry Interval setting. The valid range is 0 (no retries) to 100. The default value is 5.
  
### SQL Timeout (in seconds)

The queue makes SQL calls for retrieving and executing jobs. This SQL Timeout setting lets you set the time-out value (in seconds) for these calls. If any job fails because of a SQL Timeout error, you can increase the value for this setting and retry the job. The valid range is 30 to 86400 (one day), with a default value of 1800 (30 minutes).
  
### Cleanup Age Limit for Successful Jobs

The **Cleanup Age Limit for Successful Jobs** setting lets you configure when a job that has been completed successfully is removed from the system. Successfully completed jobs can be removed from the system through the Queue Cleanup job, which can be configured so that it removes successfully completed jobs after they reach a certain age threshold. You can configure this setting by entering the value (in hours) in the **Cleanup Age Limit for Successful Job** field. The value that you enter configures the queue to delete the job when the Queue Cleanup job is scheduled to run, only if the age of the successfully created job is equal to or greater than that value. The valid range for this setting is 1 hour through 100,000 hours. The default value for this setting is 24 hours (one day).
  
### Cleanup Age Limit for Non-Successful Jobs

The **Cleanup Age Limit for Non-Successful Jobs** setting lets you configure when a job that has completed in an unsuccessful state is removed from the system. You can configure this setting by entering the value (in hours) in the **Cleanup Age Limit for Non-Successful Jobs** field. The value that you enter configures the Queue to delete the job during the cleanup interval, only if the age of the non-successful job is equal to or greater than that value. The method in which unsuccessful jobs are removed from the system is identical to the way successfully completed jobs are removed from the system.
  
> [!NOTE]
> Jobs that are in an **Unsuccessful and blocking correlation** state stay in the history until they are successfully retried or canceled. The cleanup for non-successful jobs does not affect jobs in this state.
  
The default value of this setting is 168 hours (7 days). Since job status information is important in helping to troubleshoot problems when a job has not completed successfully, we recommend not setting this value to less than the default setting.
  
### Bookkeeping Interval

There are a number of Bookkeeping tasks that are executed by the Queuing System. For example, these include awakening jobs in a "sleeping" state, updating the heartbeat timestamp, checking whether the Queue Cleanup job needs to be executed, etc. The **Bookkeeping Interval** setting controls the time interval (in milliseconds) in which these tasks are run.
  
The valid range is 500 (1/2 second) to 300000 (five minutes), with a default value of 10000 (ten seconds).
  
### Queue Timeout (in minutes)

In a farm that contains multiple Application servers that are running the Project Server Application Service, if the Queue Service fails on one of the servers, jobs are automatically distributed among the remaining Application servers on which the Queue Service is online. A Queue Service is considered to have timed out if it cannot be accessed from the Queue health timer job for longer than the **Queue Timeout** value (in minutes).
  
The valid range is 5 to 60 minutes, with a default value of 3 minutes. 
  
> [!NOTE]
> The **Queue Timeout** value cannot be less than four times the **Bookkeeping Interval** at any time. If this rule is violated, the **Queue Timeout** value will automatically be changed to four times the Bookkeeping value.
  

