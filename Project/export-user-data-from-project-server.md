---
title: "Export user data from Project Server"
ms.author: efrene
author: efrene
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: c85c548f-4406-4663-8487-192ee065a803
description: "Your organization can export a specific user's content from your Project Server environment. To export this content, a Project Server farm administrator can follow these steps:"
---
# Export user data from Project Server

> **Important!**: This article describes how to export user data from Project Server 2016, Project Server 2013, or Project Server 2010. The process to export user data from Project Server 2019 is very different from the previous version, and is not contained in this article. To learn how to export user data from previous versions of Project Server 2019 Public Preview, see [Export user data in Project Server 2019 Public Preview](export-user-data-in-project-server-2019.md).

Your organization can export a specific user's content from your Project Server environment. To export this content, a Project Server farm administrator can follow these steps:

[Step 1 - Download the export script files](export-user-data-from-project-server.md#DownloadScripts)

[Step 2- Find the Project Web App instances in your SharePoint Server farm](export-user-data-from-project-server.md#FindPWA)

[Step 3- Export workspace items for the user](export-user-data-from-project-server.md#FindWSItem)

[Step 4 - Find the user's Resource ID or Claims Account on each PWA site](export-user-data-from-project-server.md#FindResID)

[Step 5 - Find projects that contain the user you're looking for](export-user-data-from-project-server.md#FindProjects)

[Step 6 - Additional queries to export data](export-user-data-from-project-server.md#RunQueries)

[Step 7 - Archived items](export-user-data-from-project-server.md#ArchivedItems)

[Step 8 - Find and save attachments, views, and VBA files](export-user-data-from-project-server.md#FindViews)

## Process Overview
<a name="Overview"> </a>

The following is an overview of the process to export a specific user's information from Project Web App:

1. **Download the export scripts**: Download the .sql and Microsoft PowerShell scripts for exporting user data.

2. **Find the PWA sites in your environment**: Find a listing of Project Web App instances in your Project Server farm.

3. **Find the user's resource ID**: On each Project Web App instance, find the unique Resource ID for the user. You can also choose to specify the user claim.

4. **Perform an export of the user's data**: Export the information that you want to review by using the scipts.

   **Using scripts for different versions of Project Server**

This article applies to Project Server 2016, Project Server 2013 and Project Server 2010. While the general process applies to all three versions, there are specifics that may apply to the different versions, especially when running the SQL scripts. These are noted in the sections below. Be sure you have deployed the latest updates to your farm and Project Professional clients.

> [!NOTE]
> Project Author is not exported as part of the procedures in this article. 


## Step 1 - Download the export script files
<a name="DownloadScripts"> </a>

Download the export scripts from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=871966).

The download contains a ZIP file with separate folders for each version of Project Server. Use the scripts for your version or Project Server as described in Step 5, below.

Important notes about running the export scripts:

- The script folder contains several .wsdl files. These are required by the PowerShell scripts. Be sure they are in the same directory as the PowerShell scripts when you run them.

- The SetupReportingProcedures201x.sql script temporarily creates some global stored procedures in memory that are available within the sql session. These stored procedures are required by the following scripts:

    - ExportReportingProject201x.sql 

    - ExportReportingResource201x.sql 

    - ExportTimesheetReporting201x.sql 

> [!NOTE]
> Run SetupReportingProcedures201x.sql before running any of these scripts. 

- Each script has one or more variables that must be defined - such as UserID or database name - before you run it. Check the description section in the script itself for any needed parameters.

- Run each .sql script in the context of the database where the information resides. You must have db_datareader permissions on the database.

- You may need to "unblock" the zip file because by default, executing scripts downloaded from the Internet is not allowed. Do the following to unblock your files:

1. In File Explorer, go to the location where you saved the zip file.

2. Right click on the zip file, and click **Properties**. 

3. On the **General** tab, select **Unblock**. 
    ![Unblocking the file](images/845d5e02-d062-4806-8fdb-c8c0cdd0aa08.png)

4. Click **OK.**

    All files contained in the zip file should now be Unblocked. You can verify this in the individual files by checking to see if the **Unblocked** checkbox option no longer appears in the **General** tab of the file's **Properties** page. 

    > [!NOTE]
    > If you only have access to unzipped files, you can also unblock each file individually. 

## Step 2- Find the Project Web App instances in your SharePoint Server farm
<a name="FindPWA"> </a>

Use the Get-SPProjectWebInstance cmdlet with the following filters to get the URL, site ID, and database name for the PWA sites that exist in the SharePoint Server farm:

```
 Get-SPProjectWebInstance | ft -a Url,SiteId,DatabaseName,DatabaseServer
```

You will need the information for each site when you delete the user's personal data in a later step.

For example, running the cmdlet on our sample Contoso Project Server farm might return the following three PWA sites:


| **URL**                      | **SiteID**                             | **Database**       | **DatabaseServer** |
|:-----------------------------|:---------------------------------------|:-------------------|:-------------------|
| <http://contoso/pwa1>  <br/> | 63ed0197-3647-4279-ed5e80855fc7  <br/> | WSS_Content  <br/> | SQL01  <br/>       |
| <http://contoso/pwa2>  <br/> | 67fd0727-5279-3321-ef4e90956fc8  <br/> | WSS_Content  <br/> | SQL01  <br/>       |
| <http://contoso/pwa3>  <br/> | 63ed0197-3647-4279-eg7e20233fg9  <br/> | WSS_Content  <br/> | SQL02  <br/>       |

### Find the Project Web App instances in a SharePoint Server 2010 farm

For Project Server 2010, you also need to find the Service Application ID of the  *Project Server PSI Service Application*  . Run the **Get-ServiceApplication** PowerShell cmdlet with the following parameters to do this: 

```
Get-SPServiceApplication | ? { $_.TypeName -eq "Project Server PSI Service Application" } | ft -a
```

This will also return the name of the Project Server service application. You can then use the Get-SPProjectWebInstance cmdlet to return the names of the four Project Server databases by specifying the service application name with the -ServiceApplication parameter:

```
Get-SPProjectWebInstance -ServiceApplication "Project Server"  | ft -a Url,PrimaryServer,PublishedDatabase,DraftDatabase,ArchiveDatabase,ReportingServer,ReportingDatabase
```

You need to be able to reference the database names for each database.

> [!NOTE]
> The Project Server 2010 Reporting database can be located on a different instance of SQL Server than the other three databases. 

## Step 3 - Export workspace items for the user
<a name="FindWSItem"> </a>

Run the ExportWorkspaceItemsByDisplayName201x.sql script and search for data using possible display names of the user (partial name searches).

Run the script on the Reporting database for Project Server 2010, or on the database for the related PWA site for later versions. In the example results provided in Step 1, the database for all three Project Web App instances is  *WSS_Content*  . 

Provide values for the following parameters in the script:

|**Parameter**|**Description**|
|:-----|:-----|
|@siteID (Project Server 2016 only)  <br/> |The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1.  <br/> |
|@resDisplayName  <br/> |The display name, or partial display name, of the Project Server user.  <br/> |



## Step 4 - Find the user's Resource ID or Claims Account on each PWA site
<a name="FindResID"> </a>

After getting information all PWA sites on your Project Server farm, next you need to find the Resource ID (ResID) or Claims account of the user whose personal data you want to delete. Do this on each of the PWA sites your discovered in Step 1 (since ResIDs differ in each PWA instance).

Run the FindUser201x.sql SQL script to find the user's Resource ID or claims account. 

> [!NOTE]
> You need to run the FindUser201x.sql SQL script in SQL Server Management Studio and must have farm admin permissions to have access to the appropriate database. 

Run the script on the Published database for Project Server 2010, or on the database for the related PWA site for later versions. In the example results provided in Step 1, the database for all three Project Web App instances is  *WSS_Content*  . 

Provide values for the following parameters in the script:

|**Parameter**|**Description**|
|:-----|:-----|
|@siteID (Project Server 2016 only)  <br/> |The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1.  <br/> |
|@searchName  <br/> |The display name of the Project Server user.  <br/> |

For example, if you want to find the userID for Adam Barr on the Contoso PWA1 site you found in the example in Step 1, you would edit the values for the parameters in the script like this:

```
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @searchName nvarchar(255) = 'Adam Barr'
```

The script returns the Resource Name, Resource ID, email address, and Claims Account values for the user.

## Step 5 - Find projects that contain the user you're looking for
<a name="FindProjects"> </a>

You can use the Resource ID that you found in Step 4 to locate the projects that the user was involved with. This is done by using SQL scripts to query the Project data stored for a list of projects.

There are separate scripts for each of the data stores in Project Server. Results from the scripts are likely to be similar, though you may see some differences if you have draft projects that haven't been published.

Before you run the scripts, update them with the Resource ID that you're looking for.

**For Project Server 2010**, run these scripts:

(Be sure to read the description at the top of each script. Some scripts require you to add the database name or update other parameters.)

- ExportDraftProjectList2010.sql

- ExportPublishedProjectList2010.sql

- ExportReportingProjectList2010.sql

**For Project Server 2013**, run these scripts:

- ExportDraftProjectList2013.sql

- ExportPublishedProjectList2013.sql

- ExportReportingProjectList2013.sql

**For Project Server 2016**, run these scripts:

- ExportDraftProjectList2016.sql

- ExportPublishedProjectList2016.sql

- ExportReportingProjectList2016.sql

Examine the output of the queries and determine the projects where you want to find specific user data. You may want to export the list from SQL Server to a CSV file for convenience.

When you have determined which projects you want to search for user information, run the following scripts for each project, using the ProjectUID returned by the scripts above:

**For Project Server 2010**, run these scripts:

(Be sure to read the description at the top of each script. Some scripts require you to add the database name or update other parameters.)

- ExportDraftProject2010.sql

- ExportPublishedProject2010.sql

- ExportReportingProjects2010.sql

- ExportReportingProjectTimephasedData2010.sql

**For Project Server 2013**, run these scripts:

- ExportDraftProject2013.sql

- ExportPublishedProject2013.sql

- ExportReportingProjects2013.sql

- ExportReportingProjectTimephasedData2013.sql

**For Project Server 2016**, run these scripts:

- ExportDraftProject2016.sql

- ExportPublishedProject2016.sql

- ExportReportingProjects2016.sql

- ExportReportingProjectsTimephased2016.sql

For information about the output values of these queries, see [Project-specific user data from the reporting data](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#projectspec).

If you need additional user information, see Step 6 for scripts to retrieve information about resources, timesheets, statusing, etc.

## Step 6 - Additional queries to export data
<a name="RunQueries"> </a>

Run these additional queries to find additional information about resources, timesheets, statusing, etc.

See [Running the PowerShell scripts](export-user-data-from-project-server.md#RunScripts) below for information about how to run the PowerShell scripts.

### Export data from Project Server 2010

To export data from Project Server 2010, use the .sql scripts and Microsoft PowerShell scripts as noted in the following table. For details about each of the fields in the output, see the link in the  *Output definitions*  column. 

(Be sure to read the description at the top of each script. Some scripts require you to add the database name or update other parameters.)

|**Export option**|**Run these scripts:**|**Output definitions**|
|:-----|:-----|:-----|
|Portfolio  <br/> |ExportPortfolioModels2010.sql  <br/> |[Drivers](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#drivers) <br/> [Prioritizations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#prioritizations) <br/> [Analyses](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#analyses) <br/> |
|Resource plans  <br/> |Export-ResourcePlanTimephasedData2010.ps1  <br/> ExportResourcePlans2010.sql  <br/> ExportReportingResourcePlans2010.sql |[ResourcePlan](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resourceplan) <br/> |
|Resources  <br/> |ExportResource2010.sql  <br/> ExportReportingResource2010.sql  <br/> |[Resources](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resource) <br/> [ReportingResource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reportingresource) <br/> |
|Security  <br/> |ExportSecurity2010.sql  <br/> |[Security](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#security) <br/> |
|Service Settings  <br/> |ExportServerSettings2010.sql  <br/> |[QueueJobs](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#queuejobs) <br/> [CustomFields](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#customfields) <br/> [LookupTables](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables) <br/> [Calendars](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars) <br/> [UnsubscribedAlerts](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#unsubscribedalerts) <br/> [SubscribedReminders](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#subscribedreminders) <br/> [ReminderEmails](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reminderemails) <br/> [Delegations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#delegations) <br/> |
|Status reports  <br/> |ExportStatusReports2010.sql  <br/> |[StatusReports](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusReports) <br/> |
|TaskStatus  <br/> |ExportAssignmentsSavedData2010.sql  <br/> ExportSubmittedTaskStatusUpdates2010.sql  <br/> ExportAssignmentTransactionHistory2010.sql  <br/> ExportAssignmentHistoryData2010.ps1  <br/>ExportSavedTaskStatusUpdates2010.sql<br/>Export-SavedTaskStatusUpdates2010.ps1 ([Note](export-user-data-from-project-server.md#RunStatusScripts)) |[StatusAssignSaved](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignSaved) <br/> [StatusAssignHistory](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignHis) <br/> |
|Timesheets  <br/> |ExportTimesheets2010.sql  <br/> ExportReportingTimesheets2010.sql  <br/> |[Timesheets](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets) <br/> [Timesheets_Reporting](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets_reporting) <br/> |
|User view settings  <br/> |Export-UserViewSettings2010.ps1  <br/> |[UserViewSettings](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#userprop) <br/> |
|Workflow  <br/> |ExportWorkflow2010.sql  <br/> |[Workflow](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#workflow) <br/> |
|Workspace items  <br/> |ExportWorkspaceItemsByDisplayName2010.sql  <br/> |[WorkspaceItems](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#UserView2010) <br/> |

### Export data from Project Server 2013

To export data from Project Server 2013, use the .sql scripts and Microsoft PowerShell scripts as noted in the following table. For details about each of the fields in the output, see the link in the  *Output definitions*  column. 

|**Export option**|**Run these scripts:**|**Output definitions**|
|:-----|:-----|:-----|
|Portfolio  <br/> |ExportPortfolioModels2013.sql  <br/> |[Drivers](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#drivers) <br/> [Prioritizations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#prioritizations) <br/> [Analyses](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#analyses) <br/> |
|Resource plans  <br/> |ExportResourcePlanTimephasedData2013.ps1  <br/> ExportResourcePlans2013.sql  <br/> |[ResourcePlan](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resourceplan) <br/> |
|Resources  <br/> |ExportResource2013.sql  <br/> ExportReportingResource2013.sql  <br/> |[Resource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resource) <br/> [ReportingResource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reportingresource) <br/> |
|Security  <br/> |ExportSecurity2013.sql  <br/> |[Security](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#security) <br/> |
|Service Settings  <br/> |ExportServerSettings2013.sql  <br/> |[QueueJobs](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#queuejobs) <br/> [CustomFields](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#customfields) <br/> [LookupTables](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables) <br/> [Calendars](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars) <br/> [UnsubscribedAlerts](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#unsubscribedalerts) <br/> [SubscribedReminders](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#subscribedreminders) <br/> [ReminderEmails](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reminderemails) <br/> [Delegations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#delegations) <br/> |
|Status reports  <br/> |ExportStatusReports2013.sql  <br/> |[StatusReports](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusreports) <br/> |
|TaskStatus  <br/> |ExportAssignmentsSavedData2013.sql  <br/> ExportSubmittedTaskStatusUpdates2013.sql  <br/> ExportAssignmentTransactionHistory2013.sql  <br/> ExportAssignmentHistoryData2013.ps1  <br/>ExportSavedTaskStatusUpdates2013.sql<br/>Export-SavedTaskStatusUpdates2013.ps1 ([Note](export-user-data-from-project-server.md#RunStatusScripts))|[StatusAssignSaved](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusAssignsaved) <br/> [StatusAssignHistory](https://support.office.com/article/statusingassignmentshistory-ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignhis) <br/> |
|Timesheets  <br/> |ExportTimesheets2013.sql  <br/> ExportReportingTimesheets2013.sql  <br/> |[Timesheets](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets) <br/> [Timesheets_Reporting](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets_reporting) <br/> |
|User view settings  <br/> |Export-UserViewSettings2013.ps1  <br/> |[UserViewSettings](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#userprop) <br/> |
|Workflow  <br/> |ExportWorkflow2013.sql  <br/> |[Workflow](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#workflow) <br/> |
|Workspace items  <br/> |ExportWorkspaceItemsByDisplayName2013.sql  <br/> |[WorkspaceItems](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#wss) <br/> |

### Export data from Project Server 2016

To export data from Project Server 2016, use the .sql scripts and Microsoft PowerShell scripts as noted in the following table. For details about each of the fields in the output, see the link in the  *Output definitions*  column. 

|**Export option**|**Run these scripts:**|**Output definitions**|
|:-----|:-----|:-----|
|Engagements  <br/> |ExportEngagementScripts2016.sql  <br/> |[Engagements](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#engagements) <br/> |
|Portfolio  <br/> |ExportPortfolioModels2016.sql  <br/> |[Drivers](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#drivers) <br/> [Prioritizations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#prioritizations) <br/> [Analyses](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#analyses) <br/> |
|Resource plans  <br/> | ExportResourcePlans2016.sql  <br/> |[ResourcePlan](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resourcePlan) <br/> |
|Resources  <br/> |ExportResource2016.sql  <br/> ExportReportingResource.sql  <br/> |[Resource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resource) <br/> [ReportingResource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reportingresource) <br/> |
|Security  <br/> |ExportSecurity2016.sql  <br/> |[Security](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#security) <br/> |
|Service Settings  <br/> |ExportServerSettings2016.sql  <br/> |[QueueJobs](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#queuejobs) <br/> [CustomFields](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#customFields) <br/> [LookupTables](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables) <br/> [Calendars](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars) <br/> [UnsubscribedAlerts](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#unsubscribedalerts) <br/> [SubscribedReminders](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#subscribedreminders) <br/> [ReminderEmails](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#reminderemails) <br/> [Delegations](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#delegations) <br/> |
|Status reports  <br/> |ExportStatusReports2016.sql  <br/> |[StatusReports](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusreports) <br/> |
|TaskStatus  <br/> |ExportAssignmentsSavedData2016.sql  <br/> ExportSubmittedTaskStatusUpdates2016.sql  <br/> ExportAssignmentTransactionHistory2016.sql  <br/> ExportAssignmentHistoryData.ps1  <br/> ExportSavedTaskStatusUpdates2016.sql<br/> Export-SavedTaskStatusUpdates2016.ps1|[StatusAssignSaved](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignsaved) <br/> [StatusAssignHistory](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignhis) <br/> |
|Timesheets  <br/> |ExportTimesheets2016.sql  <br/> ExportReportingTimesheets2016.sql  <br/> |[Timesheets](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets) <br/> [Timesheets_Reporting](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets_reporting) <br/> |
|User view settings  <br/> |Export-UserViewSettings2016.ps1  <br/> |[UserViewSettings](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#userprop) <br/> |
|Workflow  <br/> |ExportWorkflow2016.sql  <br/> |[Workflow](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#workflow) <br/> |
|Workspace items  <br/> |ExportWorkspaceItemsByDisplayName2016.sql  <br/> |[WorkspaceItems](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#wss) <br/> |

## Step 7 - Archived items
<a name="ArchivedItems"> </a>

ExportArchievdData201x.sql will return the following data that is stored in the archived database that is related to the resource.

|Export option|Output definitions|
|:-----|:-----|
|Archived items - Calendar|[Calendars](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars)|
|Archived items - Custom fields|[CustomFields](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#customFields)|
|Archived items - Lookup tables|[Lookup Table](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables)|
|Archived items - Projects|[Project List](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#projlist)<br>ProjectVersionId (Archive version ID)<br>ProjectVersionDescription (Date and time of the backup)<br>ProjectVersionDate (The date of the backup)|
|Archived items - Resource|[Resource](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resource)|
|Archived items - Resource custom fields|[Resource - custom fields](https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#rescustfields)|

Archived Project Data: To export archived projects:
1.  [Archive the current project](https://docs.microsoft.com/project/back-up-item-level-objects-through-administrative-backup-project-server-2013). ([2010](https://docs.microsoft.com/previous-versions/office/project-server-2010/dd207304(v%3doffice.14)))
2.  [Restore the archived version](https://docs.microsoft.com/en-us/project/restore-item-level-objects-through-administrative-restore-project-server-2013). ([2010](https://docs.microsoft.com/previous-versions/office/project-server-2010/dd207306(v%3doffice.14)))
3.  Export the user related data.
4.  Restore the project from archive.

Archived Non-Project Data: 
1.  Use [SharePoint backup and recovery](https://docs.microsoft.com/en-us/sharepoint/administration/backup-and-recovery-overview) ([2010](https://technet.microsoft.com/EN-US/library/ee662536(v=office.14).aspx)) to create a clone of the current farm.
2.  Restore the archived items from Administrative backup and restore (see previous procedure).
3.  Export the user related data.


## Step 8 - Find and save attachments, views, and VBA files
<a name="FindViews"> </a>

To find attachments and views, we recommend that you export a given project to XML. To do this, open it in Project Professional, and then save it as an XML file. Once you have XML files for the Projects that you want to review, see [Find customized user items in Project Online and Project Server user export data](https://support.office.com/article/d40ede2b-22e5-4fa4-b789-007c9a36d5f1).

## Running the PowerShell scripts
<a name="RunScripts"> </a>


The table below shows the parameters required for a given script. Run each script in a SharePoint Management Shell as a farm administrator.

|Script|Parameters|
|:-----|:-----|
|ResourcePlanTimephasedData201x.ps1 <br>Export-SavedTaskStatusUpdates201x.ps1 <br> ExportTaskStatusUpdateHistory201x.ps1|ProjectServerURL<br>ResId<br>OutputPath<br>PromptForCredential<br>UseWebLogin|
|Sync-ProjectWorkspace201x.ps1|ProjectServerURL<br>ProjectId<br>PromptForCredential<br>UseWebLogin|
|Export-UserViewSettings201x.ps1|ProjectServerURL<br>ResId<br>OutputPath|


These parameters are described in the following table.

|Parameter|Description|
|:-----|:-----|
|ProjectServerURL|URL of the PWA site|
|ResId|Resource Id of the user|
|OutputPath|Location to store the export files.|
|ProjectId|Project workspace to synchronize|

Also include one of the following authorization parameters each time you run a script:

|Auth Parameter|Description|
|:-----|:-----|
|[nothing passed in]|Authenticate using NTLM and the Kerberos protocol as the current user.|
|PromptForCredential|Authenticate using Basic or digest protocol or using NTLM and/or Kerberos with a different user.|
|UseWebLogin|Authenticate using Forms and ADFS/SAML protocol.|

For example:

```powershell
.\Export-UserViewSettings2016.ps1 -ProjectServerURL "https://pwa" -resId "55efd6ff-853c-4fec-8abd-6df2c90b94e5" -OutputPath "C:\"
```
See each PowerShell script file for further examples and information about the parameters.

### Running Export-SavedTaskStatusUpdates201x.ps1 (2010 and 2013 only)
<a name="RunStatusScripts"> </a>

To run the Export-SavedTaskStatusUpdates201x.ps1 script, you must run as a delegate of the user being exported in order to view the saved assignment. Use the following procedure:

1.  [Turn delegation on in Project Server](turn-delegation-on-or-off-in-project-server.md)
2.  [Enable delegation permissions on the user being exported](set-up-which-users-and-groups-can-act-as-delegates-in-project-server.md) 
3.  Enable delegation permissions on yourself to delegate as that user. (As an admin you may already have permissions.)
4.  [Configure yourself as a delegate of the user being exported](create-delegations-in-project-server.md)
5.  Log in to Project Web App.
6.  Click the gear icon, and then click **Act as a delegate**.
8.  Start a delegate session.
9.  Run the Export-SavedTaskStatusUpdates201x.ps1 PowerShell script.
10. Stop the delegate session.

## See also

[Delete user data from Project Server](delete-user-data-from-project-server.md)
