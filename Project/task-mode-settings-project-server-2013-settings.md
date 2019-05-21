---
title: "Task Mode Settings (Project Server 2013 settings)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 5bfb8b64-dcbf-4ba4-b5cf-30042dcc301c
description: "Summary: Use the Task Mode Setting in SharePoint Central Administration to define the default task mode used to schedule tasks in Project Server 2013."
---

# Task Mode Settings (Project Server 2013 settings)
 
 **Summary:** Use the Task Mode Setting in SharePoint Central Administration to define the default task mode used to schedule tasks in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Task Mode Settings** is a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Task Mode Settings

 **Task Mode Settings** let you select the default mode in which tasks are scheduled: manually or automatically. Additionally, if you select the default setting ( **Manually Scheduled**), you can also configure if you want task to be published to team members.
  
Manually scheduled tasks (also known as "User-Controlled Scheduling") were introduced in previously in Project Server 2010. In this mode, when a new task is created, the scheduling engine is ignored and Project Server 2013 creates the task without a duration, start date, or finish date. (These values can be entered manually.) It can be useful for scheduling tasks with hard dates that are difficult to move (for example, training).
  
### To configure the Task Mode setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Task Mode setting.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Task Mode setting, and click **Manage**.
    
5. On the Server Settings page, in the Operational Policies section, click **Additional Server Settings**.
    
6. In the Task Mode Settings section:
    
7. Select **Manually Scheduled tasks can be published to team members** (which is enabled by default) if you want to allows project managers to publish their manually scheduled task to team members.
    
8. For **Default task mode in new projects**, select one of the two following settings:
    
   - **Manually Scheduled** You have to enter duration, start, and finish dates for your tasks. By default, this option is selected.
    
   - **Automatically Scheduled** The scheduling engine automatically calculates durations and start dates and finish dates for your tasks.
    
9. Select **Users can override default in Project Professional** (which is enabled by default) if you want to enable your Project Professional 2013 users to override the default task mode settings that you selected.
    
10. Click **Save**.
    
## See also

#### 

[Additional Server Settings (Project Server 2013 settings)](additional-server-settings-project-server-2013-settings.md)

