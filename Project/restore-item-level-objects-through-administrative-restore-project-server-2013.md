---
title: "Restore item-level objects through Administrative Restore (Project Server 2013)"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: c88cb008-35e3-4634-b7ff-cbd44b8725bd
description: "Summary: Use the Administrative Restore page in Central Administration to restore Project Server 2013 objects."
---

# Restore item-level objects through Administrative Restore (Project Server 2013)
 
 **Summary:** Use the Administrative Restore page in Central Administration to restore Project Server 2013 objects.<br/>
**Applies to:** Project Server 2013
  
This article describes how to restore specific project items in Project Web App. This procedure does not restore the physical files of a database (.mdb), but restores backups of specific items in the database. These items were backed up to the Archive section of the Project Web App database through the Administrative Backup page in SharePoint Central Administration. For more information about item level-backup in Project Server 2013, see [Back up item-level objects through Administrative Backup (Project Server 2013)](back-up-item-level-objects-through-administrative-backup-project-server-2013.md). 
  
Before you perform this procedure, confirm that project items have been backed up.
  
In order to perform these procedures, you must be a farm administrator.
  
## Restoring item-level objects

Use the procedure to restore the following project items:
  
|**Item**|**Description**|
|:-----|:-----|
|Project  <br/> |Includes project resources, assignments, tasks, custom field values, baseline data  <br/> |
|Enterprise resource pool and calendar  <br/> |Includes enterprise resources and enterprise calendars  <br/> |
|Enterprise custom field  <br/> |Includes enterprise custom field metadata, enterprise lookup table metadata, enterprise lookup table values  <br/> |
|Enterprise global template  <br/> |Includes all Project Professional table, macro, and view definitions  <br/> |
|View definition  <br/> |Includes statusing, Project Center, Portfolio Analyzer and Resource Center view definitions  <br/> |
|Category and group settings  <br/> |Includes settings for all Project Server categories and groups.  <br/> |
   
> [!IMPORTANT]
> Item-level backup and restore of category and group settings are non-operational if you are using SharePoint Permission Mode. For more information about security modes in Project Server 2013, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
### To restore project items by using Project Web App

1. In SharePoint Central Administration, click **Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Administrative Backup settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Administrative Restore settings, and click **Manage**.
    
5. On the Project Web App Server Settings page, in the Queue and Database Administration section, click **Administrative Restore**.
    
6. In the **Item** list, select the item that you want to restore.
    
7. If you selected **Projects** from the **Item** list, select the version of the project that you want to restore as the current working version of the project.
    
    > [!NOTE]
    > The versions that are available for you to restore depend upon the number of backups that have been completed and the total number of backups that you have chosen to retain. 
  
8. Click **Restore**.
    
9. Any changes that were made between when the item was deleted and when the item was most recently backed up cannot be restored.
    
## See also

#### 

[Back up item-level objects through Administrative Backup (Project Server 2013)](back-up-item-level-objects-through-administrative-backup-project-server-2013.md)
  
[Queue and Database Administration (Project Server 2013)](queue-and-database-administration-project-server-2013.md)

