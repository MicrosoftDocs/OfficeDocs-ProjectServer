---
title: "Set up policies for capturing time and task progress"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 7/11/2017
audience: admin
ms.topic: article
ms.service: project-online
ms.localizationpriority: medium
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- PJU150
- PJO160
- PJU160
- MET150
ms.assetid: c1da8a04-d5d7-4965-bb43-48f1c50bef1b
description: "In addition to some of the standard settings available for time and task progress in Project Web App, there are also some more granular policies that let you fine-tune how your organization will work."
---

# Set up policies for capturing time and task progress

In addition to some of the standard settings available for time and task progress in Project Web App, there are also some more granular policies that let you fine-tune how your organization will work.
  
When choosing the right settings for your organization, there are two different spots where you'll need to make changes. Start by going to **Settings**![Settings icon.](media/22ecb306-849a-4d04-8885-fe49ec9df8ce.png) \> **PWA Settings**.
  
From there, some of the settings will be under **Timesheet Settings and Defaults**.
  
![Timesheet Settings and Defaults.](media/4b39ea36-c7ed-4dd4-aece-56f4e959af2a.png)
  
Other settings will be under **Task Settings and Display**.
  
![Task Settings and Display.](media/5306f2b4-bfa5-4c30-a91f-c785d5e90157.png)
  
|**Policies**|**Where to set them**|**What to set**|
|:-----|:-----|:-----|
|**Can team members submit overtime and non-billable time?** <br/> |Timesheet Settings and Defaults  <br/> |Under **Project Web App Display**, select the **The timesheet will use standard Overtime and Non-Billable time tracking** check box.  <br/> ![The timesheet will use standard Overtime and Non-Billable time tracking.](media/7de8e96c-ff3c-40a1-8551-1a6437de0270.png)|
|**Got limits on how much time can be reported?** <br/> |Timesheet Settings and Defaults  <br/> |Accounting systems, customers, or other internal factors may require that you have policies around how much time can be reported.  <br/> Under **Hourly Reporting Limits**, you can set **Maximum Hours per Timesheet**, **Minimum Hours per Timesheet**, and **Maximum Hours per Day**.  <br/> ![Time tracking data entry limits.](media/3e6aa8b1-768f-4241-bf0b-803e3554f7fe.png)|
|**Can team members report work ahead of time?** <br/> |Timesheet Settings and Defaults  <br/> |By default, team members can't submit actual work for future time periods. If your organization is okay with reporting hours before they actually happen, select the **Allow future time reporting** check box, under **Timesheet Policies**.  <br/> ![Allow future time reporting.](media/1c0a7492-78ff-4636-ada4-8eff602d02e6.png)|
|**Can team members report time against top-level summary tasks?** <br/> |Timesheet Settings and Defaults  <br/> | In Project Web App, tasks can be indented below other tasks, and the work done on the indented tasks will roll up to the top-level task to summarize all of the work done in that area. For example, your task list might look like this:  <br/>  Produce white paper  <br/>  Research subject  <br/>  Write content  <br/>  Review content  <br/>  Incorporate feedback  <br/>  Publish content  <br/>  Typically, team members report work on the indented tasks, and those hours roll up to the top-level summary task ("Produce white paper"). However, in some organizations, it might make sense to allow team members to report time spent on the summary task, too.  <br/>  If you want team members to be able to report time spent on summary tasks, select the **Allow top-level time reporting** check box, under **Timesheet Policies**.  <br/> ![Allow top-level time reporting.](media/01640bc6-1975-4698-9fe2-68674415d7a9.png)|
|**Don't want project managers changing actual hours?** <br/> |Task Settings and Display  <br/> |Under **Protect User Updates**, choose **Only allow task updates via Tasks and Timesheets**.  <br/> ![Only allow task updates via Tasks and Timesheets.](media/6c1194ca-3336-4720-860a-aff05307a839.png)|
|**Want all types of work copied from timesheets to task progress?** <br/> |Task Settings and Display  <br/> |Team members can import their timesheet hours into their task progress, to get a jump on filling out how much work they've finished. By default, only work that uses the [standard line classification](set-up-categories-for-timesheet-rows.md) (in the **Billing Category** column of a timesheet) will be imported.  <br/> If you want all work across all categories to be copied to task progress when a team member imports a timesheet, select the **Import all timesheet line classifications** check box, under **Protect User Updates**.  <br/> ![Import all timesheet line classifications.](media/257545a0-3b09-4f17-a011-44947b6c665e.png)|
|**Can team members set the time frame for a task progress report?** <br/> |Task Settings and Display  <br/> |Task progress is different from timesheets, in that it doesn't necessarily need to reflect a specific accounting period. If you want team members to be able to choose what dates they're reporting task progress for, select the **Allow users to define custom periods for task updates** check box, under **Protect User Updates**.  <br/> ![Allow users to define custom periods for task updates.](media/d40ec644-2c60-4254-88ce-2964c3bf3bef.png)|
   

