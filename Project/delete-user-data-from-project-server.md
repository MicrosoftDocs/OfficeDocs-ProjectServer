---
title: Delete user data from Project Server
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 1ec9b8c4-0dfe-477d-b131-e446eef7f928
description: Learn how an Farm admin can delete a specific user's data from a Project Server environment. This information applies to Project Server 2016, Project Server 2013, and Project Server 2010.
ms.date: 04/26/2018
---

# Delete user data from Project Server

Learn how an Farm admin can delete a specific user's data from a Project Server environment. This information applies to Project Server 2016, Project Server 2013, and Project Server 2010. To learn how to delete user data from Project Server 2019 Public Preview, see [Delete user data in Project Server 2019 Public Preview](delete-user-data-in-project-server-2019.md).

- [Step 1 - Find the Project Web App instances in your SharePoint Server farm](delete-user-data-from-project-server.md#FindPWA)

- [Step 2 - Find the user's Resource ID or Claims Account on each PWA site](delete-user-data-from-project-server.md#FindResID)

- [Step 3 - Close all the user's projects](delete-user-data-from-project-server.md#Step4)

- [Step 4 - Export the users data](delete-user-data-from-project-server.md#Step3)

- [Step 5 - Delete workspace items](delete-user-data-from-project-server.md#DeletePersonalData)

- [Step 6 - Sync workspace items into Project Server](delete-user-data-from-project-server.md#SyncWorkspaceItems)

- [Step 7 - Open the resources calendar and clear out the exception reason for the user](delete-user-data-from-project-server.md#Calendar)

- [Step 8 - Delete the user's personal information from the Resource and Project Resources tables](delete-user-data-from-project-server.md#step5)

- [Step 9 - Redact resource information from archived objects](delete-user-data-from-project-server.md#RedactArchive)

- [Step 10 - Clear the cache for Project Professional users connecting to the Project Online instance.](delete-user-data-from-project-server.md#step6)

> [!NOTE]
> Issues and Risks are stored in Project Sites, which are part of SharePoint Server. When deleting user information, the best practice is to [delete the user's SharePoint Server information first](/office365/enterprise/gdpr-for-sharepoint-server), followed by deleting their Project Server information. 

Be sure you have deployed the latest updates to your farm and Project Professional clients before you run the scripts in this article.

## What user information is deleted?
<a name="Whatdata"> </a>

In Project Server, admins can use the steps detailed in this article to delete a user's personal data and personal identifying data (data that can be used to identify the user), such as:

- **Display name, phonetic name, GUIDs** - You can choose to delete or rename the user Display Name (details in how to run the script). 

- **Users specific view settings** - For example, if the user has customizations on their view settings (views, filters, groups, tables, maps, drawing, reports) ﻿on top of grid pages with views (such as the Resource Center, Project Center, Schedule webpart, etc.), these are deleted. 

- **Calendar exception details** - For example, if the user was out for a week in January because he or she was sick or on vacation, the name of the exception needs to be manually deleted. The dates will remain the same. 

- **User Permissions** - For example, if user ﻿is ﻿associated with project server categories, groups/ has been granted individual global permissions, we will go ahead and remove ﻿all the associations. The user will also be set as inactive. 

> [!NOTE]
> Project Author is not deleted as part of the procedures in this article. 

User personal information contained in Project sites, issues, and risks are stored in SharePoint and are not deleted through this process. You will need to [delete this data directly from SharePoint Server](/office365/enterprise/gdpr-for-sharepoint-server).

> [!IMPORTANT]
> We recommend running the SharePoint Server user information delete process before deleting the same user's information from Project Server. This will prevent user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, should they still exist. 

## Delete scenarios
<a name="scenarios"> </a>

Depending on your needs, this process allows you to delete your user's personal information listed above, but also allows some control of in regards to deleting the users display name in shared items, such as timesheets, projects, and assignments. There are three delete scenarios that you can do:

### Scenario 1: Delete user's information from a Project Web App instance except for the display name

In this scenario, all of the user's personal information is deleted, but the user's display name will remain intact.

You might choose this scenario if you need to do further review of shared items (such as timesheets and projects) in which the user was active.

### Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere

In this scenario, all of the user's personal information is deleted. In all locations where the user's display name was shown, it is replaced with a string of your choosing, such as "Deleted User." The resource ID for the user remains.

You might choose this scenario if there is no business need to retain the user display name, even in shared records such as timesheets and projects.

### Scenario 3: Delete user's information from a Project Web App instance, but change the display name everywhere except for timesheet records

In this scenario, all of the user's personal information is deleted, except in timesheet records. You can choose to replace the user's display name with another string, such as "Deleted User." However, this will not affect timesheet records, where the user name still remains. The updated display name is unlinked from its timesheets records and a new Resource ID is generated so that the updated user name cannot be identified through data in timesheet records.

You might choose this scenario if you need to do further review of timesheet records in which the user appears as either a submitter or approver.

## Process Overview
<a name="Overview"> </a>

The following is an overview of the process to delete a specific user's information in Project Web App:

1. Download the delete and export scripts from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=871966).

2. **Find the PWA sites in your environment**: Find a listing of Project Web App instances in your Project Server farm.

3. **Find the user's resource ID**: On each Project Web App instance, find the unique Resource ID for the user by specifying the user's claims account.

4. **Perform an export of the user's data**: This procedures is described in [Export user data from Project Server](export-user-data-from-project-server.md).

5. **In Project Professional, close all projects in which the user was involved**: This ensures that changes will be made to all projects in which the user has information.

6. **Run the RedactProjectUser PowerShell script**: Run the script to delete the user's information from each PWA site.

    Through the script, you can choose to change the user's display name to something different (for example, "Deleted User"). This is useful when the user's data is shared and you don't want to delete it, such as the owner of an assignment in a project, or part of a project schedule.

7. **Delete the cache for Project Professional users**: After the script has completed successfully, you must delete the cache on each device in which Project Professional was used to open the project while connected to the Project Web App instance. Clearing the cache prevents the user info from being re-added to the project if it is cached on the device.

   > [!IMPORTANT]
   > We recommend running the SharePoint Server user information delete process before deleting the same user's information from Project Server. This will prevent user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, should they still exist. 

### Using scripts for different versions of Project Server

This article applies to Project Server 2016, Project Server 2013 and Project Server 2010. While the general process applies to all three versions, there are specifics that may apply to the different versions, especially when running the SQL scripts. These are noted in the directions.

## Step 1 - Find the Project Web App instances in your SharePoint Server farm
<a name="FindPWA"> </a>

Use the Get-SPProjectWebInstance cmdlet with the following filters to get the URL, site ID, and database name for the PWA sites that exist in the SharePoint Server farm:

```powershell
 Get-SPProjectWebInstance | ft -a Url,SiteId,DatabaseName,DatabaseServer
```

You will need the information for each site when you delete the user's personal data in a later step.

For example, running the cmdlet on our sample Contoso Project Server farm might return the following three PWA sites:


| **URL**                      | **SiteID**                             | **Database**       |
|:-----------------------------|:---------------------------------------|:-------------------|
| `https://contoso/pwa1`  <br/> | 63ed0197-3647-4279-ed5e80855fc7  <br/> | WSS_Content  <br/> |
| `https://contoso/pwa2`  <br/> | 67fd0727-5279-3321-ef4e90956fc8  <br/> | WSS_Content  <br/> |
| `https://contoso/pwa3`  <br/> | 63ed0197-3647-4279-eg7e20233fg9  <br/> | WSS_Content  <br/> |

### Find the Project Web App instances in a SharePoint Server 2010 farm

For Project Server 2010, you also need to find the Service Application ID of the  *Project Server PSI Service Application*  . Run the **Get-ServiceApplication** PowerShell cmdlet with the following parameters to do this: 

```powershell
Get-SPServiceApplication | ? { $_.TypeName -eq "Project Server PSI Service Application" } | ft -a
```

This will also return the name of the Project Server service application. You can then use the Get-SPProjectWebInstance cmdlet to return the names of the four Project Server databases by specifying the service application name with the -ServiceApplication parameter:

```powershell
Get-SPProjectWebInstance -ServiceApplication "Project Server"  | ft -a Url,PrimaryServer,PublishedDatabase,DraftDatabase,ArchiveDatabase,ReportingServer,ReportingDatabase
```

You need to be able to reference the database names for each database.

> [!NOTE]
> The Project Server 2010 Reporting database can be located on a different instance of SQL Server than the other three databases. 

## Step 2 - Find the user's Resource ID or Claims Account on each PWA site
<a name="FindResID"> </a>

After getting information all PWA sites on your Project Server farm, next you need to find the Resource ID (ResID) or Claims account of the user whose personal data you want to delete. Do this on each of the PWA sites your discovered in Step 1 (since ResIDs differ in each PWA instance). You need either the user's Resource ID or Claims account when you delete the user's personal data in a later step.

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

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @searchName nvarchar(255) = 'Adam Barr'
```

The script returns the Resource Name, Resource ID, email address, and Claims Account values for the user.

In Project Server 2010, the script also generates a timesheet GUID that you will need if you want to delete the user's information from a Project Web App instance, but change the display name everywhere except for timesheet records. Make a note of this GUID for use in the reporting and delete scripts.

## Step 3 - Close all the user's projects
<a name="Step4"> </a>

Before running the delete script in the next step, you need to ensure that all of the user's projects are closed in your Project Server environment. This will ensure that changes made by the delete script are not overwritten.

If needed, a PWA admin can force-checkin the project through the PWA Server Settings. 

1. On the **Server Settings** page, in the **Queue and Database Administration** section, click **Force Check-in Enterprise Objects**. 

2. ﻿On the **Force Check-in Enterprise Objects** page, from the project list, select the checkbox next to the project that needs to be checked, and then click **Check-In**. 

3. ﻿A message will display asking if you are sure you want to force-checkin. Click **OK.**

## Step 4 - Export the users data
<a name="Step3"> </a>

Before deleting your user's personal data, you should know all projects the user was a part of. This will allow you to later verify if the user's data was removed and that you have the correct user to delete. Exporting user data is covered in detail in [Export user data from Project Server](export-user-data-from-project-server.md). Note that you will need the ExportWorkspaceItemsByDisplayName201x.sql script for Step 6, below.

## Step 5 - Delete workspace items
<a name="DeletePersonalData"> </a>

Workspace items are stored in Project Sites, which are part of SharePoint Server. You must delete a user's SharePoint Server information before deleting their Project Server information. This will prevent user personal information in workspace items from being updated by corresponding SharePoint Server data, should they still exist.

Workspace items include:
- Issues
- Risks
- Deliverables
- Linked documents

## Step 6 - Sync workspace items into Project Server
<a name="SyncWorkspaceItems"> </a>

The Sync-ProjectWorkspace201x.ps1 script creates a queue job in Project Server to do a project workspace full sync. Run this script for each project that contains the user that you're looking for. (You will need the Project ID for each project. You can use the ExportWorkspaceItemsByDisplayName201x.sql script to retrieve this.) [Confirm that the queue jobs have completed](./manage-queue-jobs-project-server-2013.md) before proceeding with additional steps. 

## Step 7 - Open the resources calendar and clear out the exception reason for the user
<a name="Calendar"> </a>

To remove the user's personal data from the resources calendar in Project Server, the Project admin will need to manually open it and clear out any calendar exception reasons that are included.

1. In Project Web App, navigate to the Resource Center.

2. In the Resource Center, select the user that you want to update.

3. On the **Resources** tab, in the **Resources** section, click **Open**. If prompted, confirm that you want to open Project Professional.

4. In Project Professional, double-click the user that you want to update.

5. On the Resource Information dialog box, click **Change Working Time**.

6. On the **Change Working Time** dialog box, on the **Exceptions** tab, select any exceptions that you want to delete, and then click **Delete**.

7. Click **OK**.

8. On the **Resource Information** dialog box, click **OK**.

9. On the **File** tab click **Save**.

## Step 8 - Delete the user's personal information from the Resource and Project Resources tables
<a name="step5"> </a>

Because Project Server 2010 has a different database structure than later versions, the procedures and scripts are different. See the appropriate section below for your version.

> [!IMPORTANT]
> Make sure to backup your Project Server databases prior to running this script. After you are sure you successfully completed deleting your user's data, you can delete the backup file. 

### Project Server 2016

Running the RedactUser2016.sql SQL script removes personal data of a user from the Project Web App instance and can optionally update the display name of the user.

Run RedactUser2016.sql using the following parameters:

|**Parameter**|**Description**|**Note**|
|:-----|:-----|:-----|
|@siteID  <br/> |The site ID of the PWA instance  <br/> |Required  <br/> |
|@resUID  <br/> |The resource ID of the user for which you want to delete personal data  <br/> |Either resUID or res_claims_account is required.  <br/> |
|@res_claims_account  <br/> |The claims account for the user for which you want to delete personal data  <br/> |Either resUID or res_claims_account is required.  <br/> |
|@res_new_name  <br/> |When provided, the username of the resource will be updated with this string.  <br/> Important: This value should be NULL unless you are doing Scenario 2 or 3 above.           |Optional  <br/> |
|@update_timesheet_names  <br/> |When enabled (value of "1"), username in timesheet records will be replaced with the @res_new_name string provided  <br/> When not enabled (value of "0"), username will remain in timesheet records, but the username will be assigned a new resource ID in timesheets to make the username untrackable.  <br/> |Enabled by default.  <br/> |

#### Example script configuration of Scenario 1: Delete user's information from a Project Web App instance, but leave the display name

This scenario removes the personal data of a user from the Project Web App instance, but will leave the user's display name intact. You may want to leave the user's display name for review in case it in a shared item, like as task owner in a project or an entry in a timesheet.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2, as well as the PWA site IDs we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = NULL
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data except for his display name from the https://contoso.sharepoint.com/sites/pwa site.

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2, as well as the PWA site ID we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) = NULL
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data except for his display name from the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name everywhere including timesheets to what you choose (for example, "Deleted User"). Use this method to change the user's display name to something that will make the user's identity anonymous.

After successfully running the script, you can re-run the FindUser201x.sql script you used in Step 2 to verify if the display name for the user has changed.

You can specify the user either by claims account or Resource ID.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2, as well as the PWA site IDs we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = 'Deleted User'
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data and changes his display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site.

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2, as well as the PWA site IDs we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data and changes his display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 3: Delete user's information from a Project Online instance, but change the display name everywhere except for timesheet records

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name to what you choose (for example, "Deleted User"), except where it appears in timesheet records.

After running the script, you can re-run the FindUser201x.sql script you used in Step 2 to see verify if the display name for the user has changed.

Note that you can specify the user either by claims account or Resource ID.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2, as well as the PWA site IDs we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = 'Deleted User'
DECLARE @update_timesheet_names bit = 0
```

The script removes all Adam Barr's personal data from the https://contoso.sharepoint.com/sites/pwa site and changes his display name to "Deleted User" except in timesheet records. A new Resource ID is generated for the user in timesheet records to unlink them from the records associated with "Deleted Uer."

Because the account is deleted, it is not possible to rerun the script using the user's claims account.

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2, as well as the PWA site IDs we retrieved in Step 1, and configure the parameters in the script as follows:

```sql
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 0
```

The script removes all Adam Barr's personal data from the https://contoso.sharepoint.com/sites/pwa site and changes his display name to "Deleted User" except in timesheet records. A new Resource ID is generated for the user in timesheet records to unlink them from the records associated with "Deleted Uer."

### Project Server 2013

Running the RedactUser2013.sql SQL script removes personal data of a user from the Project Web App instance and can optionally update the display name of the user.

Run RedactUser2013.sql using the following parameters:

|**Parameter**|**Description**|**Note**|
|:-----|:-----|:-----|
|@resUID|The resource ID of the user for which you want to delete personal data|Either resUID or res_claims_account is required.|
|@res_claims_account|The claims account for the user for which you want to delete personal data|Either resUID or res_claims_account is required.|
|@res_new_name|When provided, the username of the resource will be updated with this string.> [!IMPORTANT]> This value should be NULL unless you are doing Scenario 2 or 3 above.           |Optional|
|@update_timesheet_names|When enabled (value of "1"), username in timesheet records will be replaced with the @res_new_name string providedWhen not enabled (value of "0"), username will remain in timesheet records, but the username will be assigned a new resource ID in timesheets to make the username untrackable.|Enabled by default.|

#### Example script configuration of Scenario 1: Delete user's information from a Project Web App instance, but leave the display name

This scenario removes the personal data of a user from the Project Web App instance, but will leave the user's display name intact. You may want to leave the user's display name for review in case it in a shared item, like as task owner in a project or an entry in a timesheet.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = NULL
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data except for his display name from the https://contoso.sharepoint.com/sites/pwa site.

Because the account is deleted, it is not possible to rerun the script using the user's claims account.

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) = NULL
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data except for his display name from the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name everywhere including timesheets to what you choose (for example, "Deleted User"). Use this method to change the user's display name to something that will make the user's identity anonymous.

After successfully running the script, you can re-run the FindUser201x.sql script you used in Step 2 to verify if the display name for the user has changed.

You can specify the user either by claims account or Resource ID.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = 'Deleted User'
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data and changes his display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site.

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 1
```

The script removes all Adam Barr's personal data and changes his display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 3: Delete user's information from a Project Online instance, but change the display name everywhere except for timesheet records

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name to what you choose (for example, "Deleted User"), except where it appears in timesheet records.

After running the script, you can re-run the FindUser201x.sql script you used in Step 2 to see verify if the display name for the user has changed.

Note that you can specify the user either by claims account or Resource ID.

 **Use the user's claims account**

In this example, we use Adam Barr's claims account we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = NULL
DECLARE @res_claims_account nvarchar(255) = 'i:0#.w|contoso\adamb'
DECLARE @res_new_name nvarchar(255) = 'Deleted User'
DECLARE @update_timesheet_names bit = 0
```

The script removes all Adam Barr's personal data from the https://contoso.sharepoint.com/sites/pwa site and changes his display name to "Deleted User" except in timesheet records. A new Resource ID is generated for the user in timesheet records to unlink them from the records associated with "Deleted Uer."

 **Use the user's Resource ID**

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_claims_account nvarchar(255) = NULL
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 0
```

The script removes all Adam Barr's personal data from the https://contoso.sharepoint.com/sites/pwa site and changes his display name to "Deleted User" except in timesheet records. A new Resource ID is generated for the user in timesheet records to unlink them from the records associated with "Deleted Uer."

### Project Server 2010

Running the RedactUser-PrimaryDB2010.sql and RedactUser-ReportingDB2010.sql SQL scripts remove personal data of a user from the Project Web App instance and can optionally update the display name of the user.

Run both of these scripts for each user, using the following parameters:

|**Parameter**|**Description**|**Note**|
|:-----|:-----|:-----|
|@resUID|The resource ID of the user for which you want to delete personal data|Either resUID or res_claims_account is required.|
|@res_new_name|When provided, the username of the resource will be updated with this string.> [!IMPORTANT]> This value should be NULL unless you are doing Scenario 2 or 3 above.           |Optional|
|@update_timesheet_names|When enabled (value of "1"), username in timesheet records will be replaced with the @res_new_name string providedWhen not enabled (value of "0"), username will remain in timesheet records, but the username will be assigned a new resource ID in timesheets to make the username untrackable.|Enabled by default.|
|@timesheet_new_res_uid|Use when @update_timesheet_names=0. Use the value from FindUser201x.sql. Be sure to use the same value for both the primary and reporting scripts.||

#### Example script configuration of Scenario 1: Delete user's information from a Project Web App instance, but leave the display name

This scenario removes the personal data of a user from the Project Web App instance, but will leave the user's display name intact. You may want to leave the user's display name for review in case it in a shared item, like as task owner in a project or an entry in a timesheet.

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_new_name nvarchar(255) = NULL
DECLARE @update_timesheet_names bit = 1
DECLARE @timesheet_new_res_uid uniqueidentifier = NULL
```

The script removes all Adam Barr's personal data except for his display name from the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name everywhere including timesheets to what you choose (for example, "Deleted User"). Use this method to change the user's display name to something that will make the user's identity anonymous.

After successfully running the script, you can re-run the FindUser201x.sql script you used in Step 2 to verify if the display name for the user has changed.

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 1
DECLARE @timesheet_new_res_uid uniqueidentifier = NULL
```

The script removes all Adam Barr's personal data and changes his display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site.

#### Example script configuration of Scenario 3: Delete user's information from a Project Online instance, but change the display name everywhere except for timesheet records

This scenario removes the personal data of a user from the Project Web App instance, and changes the user's display name to what you choose (for example, "Deleted User"), except where it appears in timesheet records.

After running the script, you can re-run the FindUser script you used in Step 2 to see verify if the display name for the user has changed.

In this example, we use Adam Barr's Resource ID we retrieved in Step 2 and configure the parameters in the script as follows:

```sql
DECLARE @res_uid uniqueidentifier = '19004637-C518-E811-80E0-001DD8C187B9'
DECLARE @res_new_name nvarchar(255) =  'Deleted User'
DECLARE @update_timesheet_names bit = 0
DECLARE @timesheet_new_res_uid uniqueidentifier = 'delete-user-data-from-project-server'
```

The script removes all Adam Barr's personal data from the https://contoso.sharepoint.com/sites/pwa site and changes his display name to "Deleted User" except in timesheet records. The new Resource ID is added to the timesheet records to unlink them from the records associated with "Deleted Uer."

## Step 9 - Redact resource information from archived objects
<a name="RedactArchive"> </a>

**Archived project data**

For projects where the resource was redacted:
1. In Project Web App settings, choose **Delete enterprise objects**.
2. Choose **Delete archived projects**.
3. Delete the required archived projects.

**Archived non-project data**

Project Server only keeps a single version of the following archived items:
- Enterprise Resource Pool and Calendars
- Enterprise Custom Fields
- Enterprise Global

Take a new [administrative backup](/Project/back-up-item-level-objects-through-administrative-backup-project-server-2013) ([2010](/previous-versions/office/project-server-2010/dd207304(v%3doffice.14))). This will overwrite the previous version with the version where the resource’s personal data has been redacted.

## Step 10 - Clear the cache for Project Professional users connecting to the Project Online instance
<a name="step6"> </a>

On all devices on which Project Professional or the Project Online Desktop Client connected to Project Web App, you need to clear the cache. Clearing the cache will prevent projects in which user information was deleted from being updated from cached data that remains on the system.

To clear the cache in Project Professional:

1. Select the **File** menu, and then click **Options**.

2. On the **Project Options** page, select **Save**.

3. In the **Cache** section, select **Clean Up Cache**.

## See also

[Export user data from Project Server](export-user-data-from-project-server.md)