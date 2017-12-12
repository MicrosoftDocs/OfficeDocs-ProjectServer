---
title: "Windows PowerShell for Project Server 2016 cmdlet reference"
ms.author: efrene
author: efrene
manager: gailmc
ms.date: 2/16/2016
ms.audience: ITPro
ms.topic: hub-page
ms.prod: office-online-server
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 4d9b6f33-5c78-496b-a25c-753ce45f58f5
description: "Summary: A list of Windows PowerShell cmdlets for Project Server 2016."
---

# Windows PowerShell for Project Server 2016 cmdlet reference
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** A list of Windows PowerShell cmdlets for Project Server 2016.
  
The following table describes the Microsoft PowerShell cmdlets available in Project Server 2016.
  
|**Cmdlet name**|**Description**|
|:-----|:-----|
|[Disable-ProjectServerLicense](disable-projectserverlicense.md) <br/> |Disables the Project Server functionality across the farm.  <br/> |
|[Disable-SPProjectActiveDirectoryEnterpriseResourcePoolSync](disable-spprojectactivedirectoryenterpriseresourcepoolsync.md) <br/> |Disables Timer Job execution of the Active Directory Enterprise Resource Pool synchronization.  <br/> |
|[Disable-SPProjectEmailNotification](disable-spprojectemailnotification.md) <br/> |Turns off the Project Web App site level setting for email notifications.  <br/> |
|[Disable-SPProjectEnterpriseProjectTaskSync](disable-spprojectenterpriseprojecttasksync.md) <br/> |Disables project task sync between Project Web App and project sites.  <br/> |
|[Enable-ProjectServerLicense](enable-projectserverlicense.md) <br/> |Enables Project Server functionality in the farm.  <br/> |
|[Enable-SPProjectActiveDirectoryEnterpriseResourcePoolSync](enable-spprojectactivedirectoryenterpriseresourcepoolsync.md) <br/> |Enables Timer Job execution of the Active Directory Enterprise Resource Pool synchronization.  <br/> |
|[Enable-SPProjectEmailNotification](enable-spprojectemailnotification.md) <br/> |Enables Project Server functionality in the farm.  <br/> |
|[Enable-SPProjectEnterpriseProjectTaskSync](enable-spprojectenterpriseprojecttasksync.md) <br/> |Enables project task sync between Project Web App and project sites.  <br/> |
|[Get-SPProjectEventServiceSettings](get-spprojecteventservicesettings.md) <br/> |Returns the settings for the Microsoft Project Server Events Service 2016.  <br/> |
|[Get-ProjectServerLicense](get-projectserverlicense.md) <br/> |Retrieves the status of the license for Project Server.  <br/> |
|[Get-SPProjectDatabaseUsage](get-spprojectdatabaseusage.md) <br/> |Returns an approximate size, in megabytes (MB) of the Project Web App data used in the content database.  <br/> |
|[Get-SPProjectEnterpriseProjectTaskSync](get-spprojectenterpriseprojecttasksync.md) <br/> |Gets the status of project task sync between Project Web App and project sites.  <br/> |
|[Get-SPProjectIsEmailNotificationEnabled](get-spprojectisemailnotificationenabled.md) <br/> |Returns the Project Web App site level setting for email notifications.  <br/> |
|[Get-SPProjectOdataConfiguration](get-spprojectodataconfiguration.md) <br/> |Returns the settings for how the OData service is configured for an instance of Project Web App.  <br/> |
|[Get-SPProjectPCSSettings](get-spprojectpcssettings.md) <br/> |Gets the settings for the Project Calculation Engine on the Project Server 2016.  <br/> |
|[Get-SPProjectPermissionMode](get-spprojectpermissionmode.md) <br/> |Returns the permission mode for a Project Web App instance.  <br/> |
|[Get-SPProjectQueueSettings](get-spprojectqueuesettings.md) <br/> |Returns a list of all Project Server 2016 Queue settings and their current values for the specified Project Server service application.  <br/> |
|[Get-SPProjectWebInstance](get-spprojectwebinstance.md) <br/> |Returns an instance of a Project Web App site.  <br/> |
|[Invoke-SPProjectActiveDirectoryEnterpriseResourcePoolSync](invoke-spprojectactivedirectoryenterpriseresourcepoolsync.md) <br/> |Triggers Active Directory Enterprise Resource Pool synchronization on the specified instance of Project Web App.  <br/> |
|[Invoke-SPProjectActiveDirectoryGroupSync](invoke-spprojectactivedirectorygroupsync.md) <br/> |Manually starts the synchronization job to synchronize Project Server 2016 group membership with the specified Active Directory groups.  <br/> |
|[Migrate-SPProjectDatabase](migrate-spprojectdatabase.md) <br/> |Copies the data from the Project Server 2013 database into the corresponding SharePoint Server 2016 content database containing the migrated site collection.  <br/> |
|[Migrate-SPProjectResourcePlans](migrate-spprojectresourceplans.md) <br/> |Migrates the published resource plan assignment data to engagements. Run after data migration has been completed from Project Server 2013 to Project Server 2016.  <br/> |
|[New-SPProjectServiceApplication](new-spprojectserviceapplication.md) <br/> |Creates a new Project Server service application.  <br/> |
|[New-SPProjectServiceApplicationProxy](new-spprojectserviceapplicationproxy.md) <br/> |Creates a proxy for a Project Server service application.  <br/> |
|[Pause-SPProjectWebInstance](pause-spprojectwebinstance.md) <br/> |Switches the specified instance of Project Web App to read-only, preventing any changes from being made through the Project Server 2016 PSI or CSOM.  <br/> |
|[Repair-SPProjectWebInstance](repair-spprojectwebinstance.md) <br/> |Re-queues specific Project Server 2016 queue items that may have fallen out of the queue.  <br/> |
|[Reset-SPProjectEventServiceSettings](reset-spprojecteventservicesettings.md) <br/> |Resets the Microsoft Project Server Events Service 2016 settings to the default values.  <br/> |
|[Reset-SPProjectPCSSettings](reset-spprojectpcssettings.md) <br/> |Resets the settings for the Project Calculation Engine on Project Server 2016.  <br/> |
|[Reset-SPProjectQueueSettings](reset-spprojectqueuesettings.md) <br/> |Resets all Project Server Queue settings to their default values for a specific Project Server service application.  <br/> |
|[Resume-SPProjectWebInstance](resume-spprojectwebinstance.md) <br/> |Switches the specified instance of Project Web App to read-write mode, allowing users to change data again.  <br/> |
|[Set-SPProjectEventServiceSettings](set-spprojecteventservicesettings.md) <br/> |Allows you to change the Microsoft Project Server Events Service 2016 TCP port settings.  <br/> |
|[Set-SPProjectOdataConfiguration](set-spprojectodataconfiguration.md) <br/> |Sets the properties for how the OData service is configured for an instance of Project Web App.  <br/> |
|[Set-SPProjectPCSSettings](set-spprojectpcssettings.md) <br/> |Sets the settings for the Project Calculation Engine on Project Server 2016.  <br/> |
|[Set-SPProjectPermissionMode](set-spprojectpermissionmode.md) <br/> |Changes the permission mode for a Project Web App instance. Running this cmdlet deletes all security settings and reverts to the default settings for the specified mode.  <br/> |
|[Set-SPProjectQueueSettings](set-spprojectqueuesettings.md) <br/> |Sets the value of one or multiple Project Server 2016 Queue settings for a specific Project Server service application.  <br/> |
|[Set-SPProjectServiceApplication](set-spprojectserviceapplication.md) <br/> |Sets the properties of a Project Server service application.  <br/> |
|[Set-SPProjectUserSync](set-spprojectusersync.md) <br/> |Controls the behavior of WSS user sync.  <br/> |
|[Set-SPProjectUserSyncDisabledSyncThreshold](set-spprojectusersyncdisabledsyncthreshold.md) <br/> |Defines the threshold over which a user sync job will not be executed but instead will be deleted. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Set-SPProjectUserSyncFullSyncThreshold](set-spprojectusersyncfullsyncthreshold.md) <br/> |Defines the threshold over which a delta user sync job will be executed as a complete user sync. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Set-SPProjectUserSyncOffPeakSyncThreshold](set-spprojectusersyncoffpeaksyncthreshold.md) <br/> |Defines the threshold over which a full user sync job will be executed during off peak hours instead of immediately. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Sync-SPProjectPermissions](sync-spprojectpermissions.md) <br/> |Manually synchronizes permissions between a Project Web App instance and its associated project sites.  <br/> |
|[Test-SPProjectServiceApplication](test-spprojectserviceapplication.md) <br/> |Runs a serious of health checks against the Project Service Application.  <br/> |
|[Test-SPProjectWebInstance](test-spprojectwebinstance.md) <br/> |Runs a suite of tests on an existing Project Web Instance.  <br/> |
   
## See also

#### 

[Windows PowerShell for SharePoint 2013 reference](http://technet.microsoft.com/library/24f40b8f-58e2-4ed8-948c-51c08073997d.aspx)

