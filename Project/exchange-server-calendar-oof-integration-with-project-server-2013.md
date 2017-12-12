---
title: "Exchange Server calendar OOF integration with Project Server 2013"
ms.author: efrene
author: efrene
ms.prod: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 0bef7c78-4864-4775-8b44-d96bcf82fdae
description: "Summary: In Project Server 2013, you can synchronize Project Resource Calendars to Exchange Server calendars to retrieve and synchronize users' out-of-office time. Then, when users update this information in Exchange, Project is aware of it."
---

# Exchange Server calendar OOF integration with Project Server 2013
 
 **Summary:** In Project Server 2013, you can synchronize Project Resource Calendars to Exchange Server calendars to retrieve and synchronize users' out-of-office time. Then, when users update this information in Exchange, Project is aware of it.<br/>
**Applies to:** Project Server 2013
  
This is an on-premises feature for Project Server 2013. It is not supported on Office 365. 
  
## Enable Project Server 2013 and Exchange Server OOF calendar integration

By default, this feature is disabled and must be enabled in your SharePoint Server 2013 environment by someone with Farm Administrator privileges.
  
> [!NOTE]
> Time reporting periods must be configured for Exchange Server OOF calendar integration to work. 
  
### To enable this feature in Central Administration

1. Using an account that has farm administrator credentials, log on to an instance of SharePoint Server in your farm that is running Central Administration.
    
2. Go to **Start > Run > All Programs > SharePoint Products and Technologies > SharePoint 2016 Central Administration**, and choose this option to open Central Administration.
    
3. On the main Central Administration page, click **General Application Settings** on the left side.
    
4. On the General Application Settings page, click the **Manage** link in the **PWA Settings** section.
    
5. If you have more than one PWA instance, make sure that the correct **Project Web Application Instance** is displayed on the upper-right side of the page. If it is not, select the drop-down arrow and then click **Change Project Web App Instance** to allow you to select the correct instance.
    
6. With the correct instance selected, click the **Additional Server Settings** link in the **Operational Policies** section.
    
7. On the following page, scroll down to the **Exchange Server Details** section, near the bottom of the page. This section contains a single check box for **Synchronize Out of Office calendars**. Select that check box, and then click **Save**.
    
Once this feature is enabled at the Central Administration level, a Project Web Access administrator must enable it for individual resources at the PWA level.
  
### To enable Project Server 2013 and Exchange Server OOF calendar integration for individual resources

1. Log on to a computer as the PWA Administrator, and then browse to the PWA site that has Exchange Server synchronization enabled on it.
    
2. Click the **Resources** link on the left-hand side of the main page.
    
3. Once the resources are displayed, you can select a resource with a valid Exchange Server email address and then click the **Edit** button from the **Resources** tab.
    
4. On the Edit Resource: [USER] page, scroll down and locate the **Exchange Server Details** section, which has a **Synchronize Out of Office calendars** check box, similar to the Central Administration section discussed earlier.
    
5. As in Central Administration, this check box must be checked for the user, and then the **Save** button at the bottom of the page should be clicked.
    
> [!NOTE]
> Repeat this procedure for each resource in your PWA resource list that should have this functionality. Bulk edit does not give you this option to select for multiple users at the same time. 
  
You can adjust the Exchange sync timer job. By default, it will run once per day, and be scheduled for off-peak hours during the night. A farm administrator can change the frequency or time by modifying this job.
  
### To change the Exchange sync timer job

1. Log on to an instance of SharePoint Server in your farm that is running Central Administration by using an account that has farm administrator credentials.
    
2. Go to **Start > Run > All Programs > SharePoint Products and Technologies > SharePoint 2013 Central Administration**, and choose this option to open Central Administration.
    
3. On the main Central Administration page, click the **Monitoring** link on the left side.
    
4. On the Monitoring page, click the **Review job definitions** link in the **Timer Jobs** section.
    
5. You must locate the **Project Web App: Exchange Calendar Out of Office synchronization job for [PWA URL]** timer job, where _[PWA-URL]_ is the URL of the PWA site you've enabled the feature on. Click this timer job link.
    
6. On the Edit Timer Job page, you can make the changes that you must have, such as running the job at a time other than the early morning hours, or changing to be more frequent, such as hourly. For more information on timer jobs, see [Timer job reference](http://technet.microsoft.com/library/b23e4fb4-6ee1-451e-92b3-7c90be5dc7e7.aspx).
    
## Effect of OOF integration for users and project managers

With this feature enabled, users will be able to enter their OOF time in Exchange via Outlook or Outlook Web Access and that information will then become visible in their Project Server timesheet. All scheduled out-of-office time, whether a complete day or partial day, is displayed as unavailable on a resource calendar for a Project Manager.
  
From the Project Manager's perspective, no work has to be done. Users who submit their out-of-office time in Exchange Server are now accounted for. This enables Project planning to be more accurate.
  
## How Exchange Server OOF calendar integration with Project Server 2013 works

- The synchronization between Project Server and Exchange Server is triggered from Project Server. This happens when a user account is enabled or through scheduled timer jobs.
    
- After the procedure starts, Exchange Server is contacted for free/busy information for the user or users specified.
    
- If a resource is unavailable for editing because it has been checked out, that user is bypassed as part of the sync operation and will be synchronized the next time that the timer job is run.
    
- Although users may not want to enter their vacation and out-of-office time in multiple places, this calendar integration feature is probably not going to replace timesheets, because they are necessary for billing and other line-of-business purposes.
    
    To support this scenario, OOF time synchronized from Exchange Server is displayed as non-working time in the user's timesheet, consistent with how non-working time is currently shown in the user's timesheet. This indicates to the user that the time is already blocked off from another source, but it does not prevent him or her from entering time for that day.
    
- A new addition to Exchange Server 2013 and Outlook 2013 is the 'working from elsewhere' time scheduling option. This option should not be reflected in imports, as the decision was made to respect traditional out-of-office/nonworking options for backward compatibility with product versions that do not have that enum type.
    
- Time data is imported from Exchange Server at 15-minute intervals and aggregated to determine the total effect that the imported OOF time should have on the resource calendar. If the total out-of-office hours for a given day are less than four hours, then the out-of-office time is not reflected on Resource calendars. Amounts of four hours or more will be reflected.
    
- As both a user's Exchange Server and Project Server resource calendars have working hours and non-working hours defined. Therefore, out of hours from the Exchange Server calendar that are within the Exchange Server working time period will count toward the number of hours taken from working time in Project Server. If the whole day is defined as non-working in Exchange Server, the whole day will also be specified as non-working in Project Server.
    

