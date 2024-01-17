---
title: "Manage Queue Jobs (Project Server 2013)"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 72e5adfd-2d41-4589-a3c0-1e2855b6db50
description: "Summary: Learn how to manage jobs submitted in Project Server 2013 through the Manage Queue Jobs settings."
---

# Manage Queue Jobs (Project Server 2013)
 
 **Summary:** Learn how to manage jobs submitted in Project Server 2013 through the Manage Queue Jobs settings.<br/>
**Applies to:** Project Server 2013
  
The Manage Queue Jobs page lets you view Project Server 2013 operations ("jobs") that have been processed by the queue system. You can use the configuration options to filter jobs and only see the jobs that you are interested in viewing. You can also retry or cancel jobs through this page. 
  
The Project Server 2013 Manage Queue Jobs settings are available through SharePoint Central Administration page in the General Application Settings. These settings were previously located in the Project Web App (PWA) Server Settings page in Project Server 2010, but were moved to SharePoint Central Administration with other PWA settings that had more to do with server operations and maintenance.
  
For more information about related administrative settings, see [Queue and Database Administration (Project Server 2013)](queue-and-database-administration-project-server-2013.md).
  
## Requirements to access the Manage Queue Job settings in SharePoint Central Administration

To access the Manage Queue Job settings in SharePoint Central Administration, you must be a farm administrator.
  
## Accessing the Manage Queue Job settings

In Project Server 2013, the Manage Queue Job settings are now accessible through the SharePoint Central Administration site.
  
### To access the Manage Queue Job settings

1. In SharePoint Central Administration, click **Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Manage Queue Jobs settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Manage Queue Jobs settings, and click **Manage**.
    
5. On the Project Server Settings page, in the Queue and Database Administration page, click **Manage Queue Jobs**.
    
## Use the Manage Queue Jobs settings

The Manage Queue Jobs page lets you view, retry, or cancel jobs in the queue through the Jobs Grid. Viewable jobs are displayed according to the settings you select in the Manage Queue Jobs page. The configuration settings on the Manage Queue Job page include the following:
  
- Filter Type
    
- Job Types
    
- Job Completion States
    
- Columns
    
- Advanced Options
    
### Filter Type
<a name="section1"> </a>

The **Filter Type** configuration option lets you select filters to query for specific types of jobs that will appear in the Jobs Grid. The filters available in the **Filter Type** drop-down list are as follows:
  
- **By Status** Displays jobs in the queue in order by status. This is the default setting.
    
- **My Jobs** Displays only the jobs initiated by you.
    
- **By Project** Displays jobs in the queue in order by project.
    
- **By ID** Displays jobs in the queue in order by Job ID.
    
- **Active** Displays all jobs that have a status of **Active**.
    
- **Blocked** Displays all jobs that have a status of **Blocked**.
    
### To select a filter

1. On the Manage Queue Jobs page, in the **Filter Type** section, click the **Filter Type** drop-down list and select the type of filter that you want to use to determine which jobs appear in the Jobs Grid.
    
2. In the Jobs Grid, click **Refresh Status**.
    
    Jobs in the Jobs Grid appear according to the filter type that you select. For example, if you select the **By Status** filter, jobs are listed alphabetically by status.
    
### Job History
<a name="section2"> </a>

This configuration option enables you to select the date range of jobs that appear in the Jobs Grid. Use the **From** and **To** fields to select a beginning and end data. The default selection is to select the one-day date range for the present date.
  
You can use the **Maximum Number of Jobs** field to limit the number of jobs that appear for a given date range. If the selected date range contains a very large number of jobs that have to appear in the Jobs Grid, the load time for the Manage Queue Jobs page can be very long. The **Maximum Number of Jobs** field lets you limit the jobs that appear. The default setting is 500.
  
### To configure the Job History setting

1. On the Manage Queue Jobs page, in the **Job History** section, specify the following values:
    
   - In the **From** field, specify the start date for which you want jobs to appear in the Jobs Grid. You can also click the calendar icon to select a start date.
    
   - In the **To** field, specify the end date for which you want jobs to appear in the Jobs Grid. You can also click the calendar icon to select an end date.
    
2. In the **Maximum number of jobs per queue** box, you can specify the maximum number of jobs that you want to display. The default value is 500.
    
3. In the Jobs Grid, click **Refresh Status**.
    
### Job Types
<a name="section3"> </a>

The **Job Types** configuration option lets you select the type of job (for example, **Project Create**, **Timesheet Submit**, **Notifications**, and so on) that you want to appear in the Jobs Grid. By default, all job types are listed in the **Selected Jobs** list.
  
### To configure the Job Types setting

1. On the Manage Queue Jobs page, in the **Job Types** section:
    
   - If you want to keep certain job types from appearing in the Jobs Grid, from the **Selected Jobs** list, select the job types that you do not want to appear in the Jobs Grid, and then click **Remove**. (This action moves the selected job types to the **Available Jobs** list.) Click **Remove All** if you want to remove all job types from the **Selected Jobs** list.
    
   - If you want to add jobs types to the Jobs Grid, from the **Available Jobs** list, select the job types that you want to appear in the Jobs Grid, and then click **Add**. This action moves the selected job types to the **Selected Jobs** list. Click **Add All** if you want to add all job types to the **Selected Jobs** list.
    
2. In the Jobs Grid, click **Refresh Status**.
    
### Job Completion States
<a name="section4"> </a>

The **Job Completion States** configuration option lets you select the job states (for example, **Success**, **Blocked Due to a Failed Job**, **Processing**, and so on) of the jobs that you want to appear in the Jobs Grid. By default, all job types except **Success** are listed in the **Selected Jobs** list, since Project administrators would be more interested in job types that signify a failure or blocking issue.
  
You can add or remove different job states to and from the Selected Job States list and the Available Job States list. The Jobs Grid will query for jobs in the job stats listed in the Selected Job States list.
  
This setting can be helpful for troubleshooting jobs that are not completing successfully in the queue. For example, some users might have experienced problems over the past several days. You can see specifically which jobs are not completing successfully by going to the **Job Completion States** setting and adding all job states except **Success**. You can also select a Job History date range that begins shortly before the problems occurred (for example, seven days). In this scenario, the Jobs Grid should display information about all jobs that are in a non-successful job status that have occurred over the past week.
  
The **Job Completion** states that you can select for this setting are as follows:
  
- **Blocked Due to a Failed Job**
    
- **Cancelled**
    
- **Failed and Blocking Correlation**
    
- **Failed but not Blocking Correlation**
    
- **Getting Queued**
    
- **Processing**
    
- **Skipped for Optimization**
    
- **Success**
    
- **Waiting to be Processed**
    
- **Waiting to be Processed (On Hold)**
    
- **Waiting to be Processed (Ready for Launch)**
    
- **Waiting to be Processed (Sleeping)**
    
### To configure the Job Completion States setting

1. On the Manage Queue Jobs page, in the **Job Completion States** section, add all job states that you want to display in the Jobs Grid to the **Selected Job States** list. Job states that are shown in the **Available Job States** list will not appear in the Job Grid.
    
   - To move an available job state in the **Available Job States** list to the **Selected Job States** list, select the job and then click **Add**.
    
   - To remove a job state from the **Selected Job States** list, select the job and then click **Remove**. To select multiple job states press the Ctrl key while making your selections.
    
2. In the Jobs Grid, click **Refresh Status**.
    
### Columns
<a name="section5"> </a>

The **Columns** configuration option lets you select the columns that appear in the Jobs Grid. It also lets you configure the order of the columns in the Jobs Grid.
  
The column options available to you are as follows:
  
- **% Complete**
    
- **Completed Time**
    
- **Correlation ID**
    
- **Correlation Priority**
    
- **Entry Time**
    
- **Error**
    
- **Job ID**
    
- **JobGroup ID**
    
- **JobInfo ID**
    
- **Job State**
    
- **Job Type**
    
- **Last Admin Action**
    
- **Owner**
    
- **Position**
    
- **Priority**
    
- **Project Name**
    
- **Queue Type**
    
- **Wait Time (secs)**
    
- **Wakeup Time**
    
### To configure the Columns setting

1. On the Manage Queue Jobs page, in the **Columns** section, add all columns that you want to display in the Jobs Grid to the **Selected Columns** list. Columns that are shown in the **Available Columns** list will not appear in the Job Grid.
    
   - To move a column in the **Available Columns** list to the **Selected Columns** list, select the column name and then click the **Add** button (">").
    
   - To remove a column from the **Selected Columns** list, select the column and then click the **Remove** button ("<"). To select multiple columns, press the Ctrl key while making your selections. You can also move all columns from one list to another by using the **Add All** (">>") or the **Remove All** ("<<") buttons.
    
2. In the Jobs Grid, click **Refresh Status**.
    
Note that you can change the order of the columns as they display in the Job Grid by selecting a column name in the Selected Columns list and using the **Up** or **Down** button to move the column to a different position.
  
### Advanced Options
<a name="section6"> </a>

The **Advanced Options** queue setting applies to the way that jobs in the queue are canceled.
  
The **Cancel jobs getting enqueued** option allows you to cancel all jobs that remain in a "getting enqueued" state for a prolonged time. When a job is in this state, it means that the queue has been told to start to receive a job that will be processed later. But it has not received a tag telling it that all the data for the job has been received. Until the full job has been received, the job will remain in the getting enqueued state. If a job remains in the getting enqueued state for a prolonged time, it is likely that something is preventing the job from finishing. If the job continues to remain in this state after you re-run it, review your ULS logs to troubleshoot why they problem is occurring.
  
Saving a project from Project Professional to Project Server is a job that typically enqueues. When you save a project from Project Professional to the Project Server, the job synchronizes with the server. If the synchronization is not completed, then the job remains in the enqueued state.
  
By default, this setting is enabled.
  
Make sure to click **Refresh Status** in the Jobs Grid after you make any changes.
  
> [!NOTE]
> In Project Server 2010, the Advanced Options page also contained an option to **Cancel Subsequent Jobs in Correlation**. This option is not available in Project Server 2013. 
  
## Jobs Grid

The Jobs Grid provides a view of the jobs that meet the criteria listed in the Manage Queue Jobs page. Options within this section let you select a job or group of jobs and to apply the following options to them, if applicable:
  
- **Retry Job** Allows you to rerun selected jobs in the queue that were not completed successfully.
    
- **Cancel Job** Allows you to cancel selected jobs in the queue that were not completed successfully.
    
- **View Related Jobs** Allows you to view jobs that have a dependency relationship (for example, jobs in the same correlation) with a selected job in the queue.
    
- **Refresh Status** Allows you to update the jobs in your job grid with the latest status.
    
### To retry a job

1. In the Jobs Grid, find the job that you want to retry, and then select the check box in the far left column of this job.
    
2. Click **Retry Job**. Recheck the status of the job in the Jobs Grid to verify the results of retrying the job.
    
### To cancel a job

1. In the Jobs Grid, find the job that you want to cancel, and then select the check box in the far left column of this job. Note that a job that has already completed successfully cannot be canceled.
    
2. Click **Cancel Job**.
    
### To view related jobs

1. In the Jobs Grid, find the job for which you want to find related jobs, and then select the check box in the far left column of this job.
    
2. Click **View All Jobs**. All jobs that have a dependency relationship with this job appear in the Jobs Grid.
    

