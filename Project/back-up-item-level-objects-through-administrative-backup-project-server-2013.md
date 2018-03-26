---
title: "Back up item-level objects through Administrative Backup (Project Server 2013)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 98a1fbd1-b630-4d45-8bd3-93bcfad9d27c
description: "Summary: Use the Administrative Backup page in SharePoint Central Administration to back up Project Server 2013 objects."
---

# Back up item-level objects through Administrative Backup (Project Server 2013)
 
 **Summary:** Use the Administrative Backup page in SharePoint Central Administration to back up Project Server 2013 objects.<br/>
**Applies to:** Project Server 2013
  
This article describes how to back up specific project items in Project Web App. This procedure does not back up the physical files of a database (.mdb), but creates backups of specific items in the database. These items are backed up from the Published section to the Archive section in the Project Web App database. 
  
In order to perform these procedures, you must be a farm administrator.
  
## Backing up item-level objects

You can use the procedures in this article to back up the following project items:
  
|**Item**|**Description**|
|:-----|:-----|
|Project  <br/> |Includes project resources, assignments, tasks, custom field values, baseline data  <br/> |
|Enterprise resource pool and calendars  <br/> |Includes enterprise resources and enterprise calendars  <br/> |
|Enterprise custom field  <br/> |Includes enterprise custom field metadata, enterprise lookup table metadata, enterprise lookup table values  <br/> |
|Enterprise global template  <br/> |Includes all Project Professional table, macro, and view definitions  <br/> |
|View definition  <br/> |Includes statusing, Project Center, Portfolio Analyzer, and Resource Center view definitions  <br/> |
|Category and group settings  <br/> |Includes settings for all Project Server categories and groups.  <br/> |
   
> [!IMPORTANT]
> Item-level backup and restore of category and group settings only applies to Project Permission Mode. For more information about security modes in Project Server 2013, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
The following procedure allows you to select the Project Server 2013 items you would like to backup. When the procedure is completed, the backup job is immediately sent to the queue for processing. If you would like to schedule a daily backup of these items, this is done through the Daily Backup Schedule settings page. For more information on scheduling daily backups of Project Server 2013 items, see [Daily Schedule Backup (Project Server 2013)](daily-schedule-backup-project-server-2013.md).
  
### To back up items manually

1. In SharePoint Central Administration, click **Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Administrative Backup settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Administrative Backup settings, and click **Manage**.
    
5. On the Project Web App Server Settings page, in the Queue and Database Administration section, click **Administrative Backup**.
    
6. In the **Select Items** section, select the check box next to each project item that you want to back up.
    
7. Click **Backup**. A message box will display telling you that the selected items will be queued for backup. Click **OK** to back up the selected items.
    
When you backup projects for the first time, all projects are backed up. After the initial project backup, all subsequent project backups will only backup projects that have been updated since the last backup. This ensures that the latest version of the project is backed up for all projects. Note that you can configure the number of versions of a project that you would like to back up through the Project Retention Policy setting that is available in the Daily Schedule Backup page. The Project Retention policy pertains to both scheduled and manual administrative backups of projects. For more information about the Project Retention Policy setting, see [Daily Schedule Backup (Project Server 2013)](daily-schedule-backup-project-server-2013.md).
  
All Project Server 2013 items backed up through the Administrative Backup page can be restored through the Administrative Restore page. For more information about restoring backed up Project Server 2013 items, see [Restore item-level objects through Administrative Restore (Project Server 2013)](restore-item-level-objects-through-administrative-restore-project-server-2013.md).
  
## See also

#### 

[Restore item-level objects through Administrative Restore (Project Server 2013)](restore-item-level-objects-through-administrative-restore-project-server-2013.md)
  
[Daily Schedule Backup (Project Server 2013)](daily-schedule-backup-project-server-2013.md)

