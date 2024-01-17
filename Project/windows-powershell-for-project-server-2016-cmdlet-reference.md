---
title: "Microsoft PowerShell for Project Server cmdlet reference"
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 2/16/2016
audience: ITPro
ms.topic: hub-page
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 4d9b6f33-5c78-496b-a25c-753ce45f58f5
description: "Summary: A list of Windows PowerShell cmdlets for Project Server."
---

# Microsoft PowerShell for Project Server cmdlet reference

**Summary:** A list of Microsoft PowerShell cmdlets for Project Server 2016.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016
  
The following table describes the PowerShell cmdlets available in Project Server.
  
|**Cmdlet name**|**Description**|
|:-----|:-----|
|[Disable-ProjectServerLicense](/powershell/module/sharepoint-server/disable-projectserverlicense) <br/> |Disables the Project Server functionality across the farm.  <br/> |
|[Disable-SPProjectActiveDirectoryEnterpriseResourcePoolSync](/powershell/module/sharepoint-server/disable-spprojectactivedirectoryenterpriseresourcepoolsync) <br/> |Disables Timer Job execution of the Active Directory Enterprise Resource Pool synchronization.  <br/> |
|[Disable-SPProjectEmailNotification](/powershell/module/sharepoint-server/disable-spprojectemailnotification) <br/> |Turns off the Project Web App site level setting for email notifications.  <br/> |
|[Disable-SPProjectEnterpriseProjectTaskSync](/powershell/module/sharepoint-server/disable-spprojectenterpriseprojecttasksync) <br/> |Disables project task sync between Project Web App and project sites.  <br/> |
|[Enable-ProjectServerLicense](/powershell/module/sharepoint-server/enable-projectserverlicense) <br/> |Enables Project Server functionality in the farm.  <br/> |
|[Enable-SPProjectActiveDirectoryEnterpriseResourcePoolSync](/powershell/module/sharepoint-server/enable-spprojectactivedirectoryenterpriseresourcepoolsync) <br/> |Enables Timer Job execution of the Active Directory Enterprise Resource Pool synchronization.  <br/> |
|[Enable-SPProjectEmailNotification](/powershell/module/sharepoint-server/enable-spprojectemailnotification) <br/> |Enables Project Server functionality in the farm.  <br/> |
|[Enable-SPProjectEnterpriseProjectTaskSync](/powershell/module/sharepoint-server/enable-spprojectenterpriseprojecttasksync) <br/> |Enables project task sync between Project Web App and project sites.  <br/> |
|[Get-SPProjectEventServiceSettings](/powershell/module/sharepoint-server/enable-spprojectenterpriseprojecttasksync) <br/> |Returns the settings for the Microsoft Project Server Events Service 2016.  <br/> |
|[Get-ProjectServerLicense](/powershell/module/sharepoint-server/get-projectserverlicense) <br/> |Retrieves the status of the license for Project Server.  <br/> |
|[Get-SPProjectDatabaseUsage](/powershell/module/sharepoint-server/get-spprojectdatabaseusage) <br/> |Returns an approximate size, in megabytes (MB) of the Project Web App data used in the content database.  <br/> |
|[Get-SPProjectEnterpriseProjectTaskSync](/powershell/module/sharepoint-server/get-spprojectenterpriseprojecttasksync) <br/> |Gets the status of project task sync between Project Web App and project sites.  <br/> |
|[Get-SPProjectIsEmailNotificationEnabled](/powershell/module/sharepoint-server/get-spprojectisemailnotificationenabled) <br/> |Returns the Project Web App site level setting for email notifications.  <br/> |
|[Get-SPProjectOdataConfiguration](/powershell/module/sharepoint-server/get-spprojectodataconfiguration) <br/> |Returns the settings for how the OData service is configured for an instance of Project Web App.  <br/> |
|[Get-SPProjectPCSSettings](/powershell/module/sharepoint-server/get-spprojectodataconfiguration) <br/> |Gets the settings for the Project Calculation Engine on the Project Server 2016.  <br/> |
|[Get-SPProjectPermissionMode](/powershell/module/sharepoint-server/get-spprojectpermissionmode) <br/> |Returns the permission mode for a Project Web App instance.  <br/> |
|[Get-SPProjectQueueSettings](/powershell/module/sharepoint-server/get-spprojectqueuesettings) <br/> |Returns a list of all Project Server 2016 Queue settings and their current values for the specified Project Server service application.  <br/> |
|[Get-SPProjectWebInstance](/powershell/module/sharepoint-server/get-spprojectwebinstance) <br/> |Returns an instance of a Project Web App site.  <br/> |
|[Invoke-SPProjectActiveDirectoryEnterpriseResourcePoolSync](/powershell/module/sharepoint-server/invoke-spprojectactivedirectoryenterpriseresourcepoolsync) <br/> |Triggers Active Directory Enterprise Resource Pool synchronization on the specified instance of Project Web App.  <br/> |
|[Invoke-SPProjectActiveDirectoryGroupSync](/powershell/module/sharepoint-server/invoke-spprojectactivedirectorygroupsync) <br/> |Manually starts the synchronization job to synchronize Project Server 2016 group membership with the specified Active Directory groups.  <br/> |
|[Migrate-SPProjectDatabase](/powershell/module/sharepoint-server/migrate-spprojectdatabase) <br/> |Copies the data from the Project Server 2013 database into the corresponding SharePoint Server 2016 content database containing the migrated site collection.  <br/> |
|[Migrate-SPProjectResourcePlans](/powershell/module/sharepoint-server/migrate-spprojectresourceplans) <br/> |Migrates the published resource plan assignment data to engagements. Run after data migration has been completed from Project Server 2013 to Project Server 2016.  <br/> |
|[New-SPProjectServiceApplication](/powershell/module/sharepoint-server/new-spprojectserviceapplication) <br/> |Creates a new Project Server service application.  <br/> |
|[New-SPProjectServiceApplicationProxy](/powershell/module/sharepoint-server/new-spprojectserviceapplicationproxy) <br/> |Creates a proxy for a Project Server service application.  <br/> |
|[Pause-SPProjectWebInstance](/powershell/module/sharepoint-server/pause-spprojectwebinstance) <br/> |Switches the specified instance of Project Web App to read-only, preventing any changes from being made through the Project Server 2016 PSI or CSOM.  <br/> |
|[Repair-SPProjectWebInstance](/powershell/module/sharepoint-server/repair-spprojectwebinstance) <br/> |Re-queues specific Project Server 2016 queue items that may have fallen out of the queue.  <br/> |
|[Reset-SPProjectEventServiceSettings](/powershell/module/sharepoint-server/reset-spprojecteventservicesettings) <br/> |Resets the Microsoft Project Server Events Service 2016 settings to the default values.  <br/> |
|[Reset-SPProjectPCSSettings](/powershell/module/sharepoint-server/reset-spprojectpcssettings) <br/> |Resets the settings for the Project Calculation Engine on Project Server 2016.  <br/> |
|[Reset-SPProjectQueueSettings](/powershell/module/sharepoint-server/reset-spprojectqueuesettings) <br/> |Resets all Project Server Queue settings to their default values for a specific Project Server service application.  <br/> |
|[Resume-SPProjectWebInstance](/powershell/module/sharepoint-server/resume-spprojectwebinstance) <br/> |Switches the specified instance of Project Web App to read-write mode, allowing users to change data again.  <br/> |
|[Set-SPProjectEventServiceSettings](/powershell/module/sharepoint-server/set-spprojecteventservicesettings) <br/> |Allows you to change the Microsoft Project Server Events Service 2016 TCP port settings.  <br/> |
|[Set-SPProjectOdataConfiguration](/powershell/module/sharepoint-server/set-spprojectodataconfiguration) <br/> |Sets the properties for how the OData service is configured for an instance of Project Web App.  <br/> |
|[Set-SPProjectPCSSettings](/powershell/module/sharepoint-server/set-spprojectpcssettings) <br/> |Sets the settings for the Project Calculation Engine on Project Server 2016.  <br/> |
|[Set-SPProjectPermissionMode](/powershell/module/sharepoint-server/set-spprojectpermissionmode) <br/> |Changes the permission mode for a Project Web App instance. Running this cmdlet deletes all security settings and reverts to the default settings for the specified mode.  <br/> |
|[Set-SPProjectQueueSettings](/powershell/module/sharepoint-server/set-spprojectqueuesettings) <br/> |Sets the value of one or multiple Project Server 2016 Queue settings for a specific Project Server service application.  <br/> |
|[Set-SPProjectServiceApplication](/powershell/module/sharepoint-server/set-spprojectserviceapplication) <br/> |Sets the properties of a Project Server service application.  <br/> |
|[Set-SPProjectUserSync](/powershell/module/sharepoint-server/set-spprojectusersync) <br/> |Controls the behavior of WSS user sync.  <br/> |
|[Set-SPProjectUserSyncDisabledSyncThreshold](/powershell/module/sharepoint-server/set-spprojectusersyncdisabledsyncthreshold) <br/> |Defines the threshold over which a user sync job will not be executed but instead will be deleted. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Set-SPProjectUserSyncFullSyncThreshold](/powershell/module/sharepoint-server/set-spprojectusersyncfullsyncthreshold) <br/> |Defines the threshold over which a delta user sync job will be executed as a complete user sync. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Set-SPProjectUserSyncOffPeakSyncThreshold](/powershell/module/sharepoint-server/set-spprojectusersyncoffpeaksyncthreshold) <br/> |Defines the threshold over which a full user sync job will be executed during off peak hours instead of immediately. This threshold is the product of the number of projects multiplied by the number of users.  <br/> |
|[Sync-SPProjectPermissions](/powershell/module/sharepoint-server/sync-spprojectpermissions) <br/> |Manually synchronizes permissions between a Project Web App instance and its associated project sites.  <br/> |
|[Test-SPProjectServiceApplication](/powershell/module/sharepoint-server/test-spprojectserviceapplication) <br/> |Runs a serious of health checks against the Project Service Application.  <br/> |
|[Test-SPProjectWebInstance](/powershell/module/sharepoint-server/sync-spprojectpermissions) <br/> |Runs a suite of tests on an existing Project Web Instance.  <br/> |
   
## See also

[Microsoft PowerShell for SharePoint 2013 reference](/powershell/module/sharepoint-server/)
