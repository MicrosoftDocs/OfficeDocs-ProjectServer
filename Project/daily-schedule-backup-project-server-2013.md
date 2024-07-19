---
title: "Daily Schedule Backup (Project Server 2013)"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: db7da70b-5d6d-4e94-b15e-0922eecf93d0
description: "Summary: Use the Daily Schedule Backup settings page in SharePoint Central Administration to schedule daily backups of Project Server 2013 objects."
---

# Daily Schedule Backup (Project Server 2013)
 
 **Summary:** Use the Daily Schedule Backup settings page in SharePoint Central Administration to schedule daily backups of Project Server 2013 objects.<br/>
**Applies to:** Project Server 2013
  
This article describes how to use the Daily Schedule Backup settings page to select the Project Server 2013 objects that you would like to schedule for back up on a daily basis. This procedure does not back up the physical files of a database (.mdb), but creates backups of specific items in the database. These items are backed up from the Published section to the Archive section in the Project Web App database. 
  
In order to access and use settings on the Daily Schedule Backup page, you must be a farm administrator.
  
## Items you can schedule for backup

You can enable daily backup on the Daily Schedule Backup page for the following Project Server 2013 items:
  
|**Item**|**Description**|
|:-----|:-----|
|Project  <br/> |Includes project resources, assignments, tasks, custom field values, baseline data  <br/> |
|Enterprise resource pool and calendars  <br/> |Includes enterprise resources and enterprise calendars  <br/> |
|Enterprise custom field  <br/> |Includes enterprise custom field metadata, enterprise lookup table metadata, enterprise lookup table values  <br/> |
|Enterprise global template  <br/> |Includes all Project Professional table, macro, and view definitions  <br/> |
|View definition  <br/> |Includes statusing, Project Center, Portfolio Analyzer, and Resource Center view definitions  <br/> |
|Category and group settings  <br/> |Includes settings for all Project Server categories and groups.  <br/> |
   
> [!IMPORTANT]
> Item-level backup and restore of category and group settings apply only in Project Permission Mode. For more information about security modes in Project Server 2013, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
### To back up data automatically by using a daily schedule

1. In SharePoint Central Administration, click **Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Administrative Backup settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Daily Schedule Backup settings, and click **Manage**.
    
5. On the Project Web App Server Settings page, in the Queue and Database Administration section, click **Daily Schedule Backup**.
    
6. On the Daily Backup Schedule page, in the **Project Retention Policy** box, type the number of versions you want to retain for projects that you back up.
    
    > [!NOTE]
    > The Project Retention Policy only pertains to projects and not to other enterprise objects. Also note that increasing this setting affects the Archive table in the Project Server 2013 database (ProjectService). The more versions you keep, the more space is required. 
  
7. For each item in the **Item** section, select either **Schedule** or **Never** from the **Option** list to indicate whether you want to schedule a backup for that item.
    
8. Click **Save**.
    
By default, all items you selected on the Daily Backup Schedule page are backed daily, at a time between 12 AM and 3 AM. 
  
As noted in the procedure, the number of versions that are backed up for projects depend on the value you set for the Project Retention Policy. All other items are only backed up to the previous version.
  
> [!NOTE]
> If you do not want to schedule a daily backup, and need to make an immediate backup of these Project Server 2013 items, see [Back up item-level objects through Administrative Backup (Project Server 2013)](back-up-item-level-objects-through-administrative-backup-project-server-2013.md). 
  
## See also

[Back up item-level objects through Administrative Backup (Project Server 2013)](back-up-item-level-objects-through-administrative-backup-project-server-2013.md)
  
[Restore item-level objects through Administrative Restore (Project Server 2013)](restore-item-level-objects-through-administrative-restore-project-server-2013.md)

