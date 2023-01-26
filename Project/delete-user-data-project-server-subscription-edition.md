---
title: "Delete user data from Project Server Subscription Edition"
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
description: "Learn how a Farm admin can delete a specific user's data from a Project Server Subscription Edition environment."
ms.date: 09/08/2021
---

# Delete user data from Project Server Subscription Edition 

> [!Important] 
> The process to delete user data from Project Server Subscription Edition is different from previous Project Server releases. To learn how to delete user data from previous versions, see: <br/>1. [Delete user data from Project Server 2019](Delete-user-data-in-Project-Server-2019.md) <br/>2. [Delete user data from Project Server 2016/2013/2010](delete-user-data-from-project-server.md).

Learn how a Farm admin can delete a specific user's data from a Project Server environment. 

This article describes:

-   [What user information is deleted?](delete-user-data-project-server-subscription-edition.md#info)

-   [Delete scenarios](delete-user-data-project-server-subscription-edition.md#delete)

-   [Process Overview](delete-user-data-project-server-subscription-edition.md#process)

-   [Step 1 - Download the export script files](delete-user-data-project-server-subscription-edition.md#files)

-   [Step 2 - Find the Project Web App instances in your SharePoint Server farm](delete-user-data-project-server-subscription-edition.md#farm)

-   [Step 3 - Find the user's Resource ID or Claims Account on each PWA site](delete-user-data-project-server-subscription-edition.md#site)

-   [Step 4 - Close all the user's projects](delete-user-data-project-server-subscription-edition.md#projects)

-   [Step 5 - Sync workspace items into Project Server](delete-user-data-project-server-subscription-edition.md#server)

-   [Step 6 - Export the user's data](delete-user-data-project-server-subscription-edition.md#data)

-   [Step 7 - Delete user personal data for issues and risks](delete-user-data-project-server-subscription-edition.md#risks)

-   [Step 8 - Delete your user's data from the PWA site](delete-user-data-project-server-subscription-edition.md#pwa)

-   [Step 9 - Redact resource information from archived objects](delete-user-data-project-server-subscription-edition.md#objects)

-   [Step 10 - Clear the cache for Project client users connecting to the PWA site](delete-user-data-project-server-subscription-edition.md#users)


## What user information is deleted?
<a name="info"> </a>

In Project Server, admins can use the steps detailed in this article to delete a user's personal data and personal identifying data (data that can be used to identify the user), such as:

-   **Display name, phonetic name, GUIDs** - You can choose to delete or rename the user Display Name (details in how to run the script).

-   **Users specific view settings** - For example, customized view settings (views, filters, groups, tables, maps, drawing, reports) on top of grid pages with views (such as the Resource Center, Project Center, Schedule web part, etc.) are deleted.

-   **Calendar exception details** - For example, if the user was out for a week in January because they were sick or on vacation, the name of the exception needs to be manually deleted. The dates will remain the same.

-   **User Permissions -** For example, if a user is associated with project server categories, groups or has been granted individual global permissions, all associations are deleted, and the user is set as Inactive.

User personal information contained in Project sites, issues, and risks are stored in SharePoint and are not deleted through this process. You will need to delete this data directly from SharePoint Server.

> [!Important] 
> We recommend running the SharePoint Server user information delete process before deleting the same user's information from Project Server. This prevents user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, if they exist.

<a name="delete"> </a>
## Delete scenarios  

Depending on your needs, this process allows you to delete your user's personal information listed above, but also allows some control regarding deletion of user's display name in shared items, such as timesheets, projects, and assignments. There are three delete scenarios that you can do:

### **Scenario 1: Delete user's information from a Project Web App instance except for the display name**

In this scenario, all of the user's personal information is deleted, but the user's display name remains intact.

You might choose this scenario if you need to do further review of shared items (such as timesheets and projects) in which the user was active.

### **Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere**

In this scenario, all of the user's personal information is deleted. In all locations, where the user's display name was shown, it is replaced with a string of your choosing, such as "Deleted User." The resource ID for the user remains.

You might choose this scenario if there is no business need to retain the user display name, even in shared records such as timesheets and projects.

### **Scenario 3: Delete user's information from a Project Web App instance, but change the display name everywhere except for timesheet records**

In this scenario, all of the user's personal information is deleted, except in timesheet records. You can choose to replace the user's display name with another string, such as "Deleted User." However, this won't affect timesheet records, where the user name still remains. The updated display name is unlinked from its timesheets records and a new Resource ID is generated so that the updated user name cannot be identified through data in timesheet records.

You might choose this scenario if you need to do further review of timesheet records in which the user appears as either a submitter or approver.

<a name="process"> </a>
## Process Overview

The following is an overview of the process to delete a specific user's information in Project Web App:

1.  **Download** the export scripts from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=871966).

2.  **Find the PWA sites in your environment**: Find a listing of Project Web App instances in your Project Server farm.

3.  **Find the user's resource ID**: On each Project Web App instance, find the unique Resource ID for the user by specifying the user's claims account.

4.  **Close all the user’s projects**: This ensures that changes are made to all the projects in which the user has information.

5.  **Sync workspace items into Project Server**.

6.  **Perform an export of the user's data**: This procedure is described in [Export user data from Project Server Subscription Edition](export-user-data-project-server-subscription-edition.md).

7.  **Delete user personal data from Issues and Risks**.

8.  **Delete your user’s data from the PWA site:** Run the script to delete the user's information from each PWA site.

9.  **Redact resource information from archived objects**.

10. **Clear the cache for Project client users connecting to the PWA site**.

<a name="files"> </a>
## Step 1 - Download the export script files

Click [here](https://go.microsoft.com/fwlink/?linkid=871966) to download the export scripts.

Important notes about running the export scripts:

-   Run the `.sql` script in the context of the database where the information resides. You must have db\_datareader permissions on the database.

-   You need to "unblock" the zip file because by default, executing scripts downloaded from the Internet is not allowed. Do the following to unblock your files:

    1.  In File Explorer, go to the location where you saved the zip file.

    2.  Right click on the zip file, and click **Properties**.

    3.  On the **General** tab, select **Unblock**. 

    4.  Click **OK.**

    All files contained in the zip file should now be Unblocked. You can verify this in the individual files by checking to see if the **Unblocked** checkbox option no longer appears in the **General** tab of the file's **Properties** page.

    > [!Note] 
    > If you only have access to unzipped files, you can also unblock each file individually.

<a name="farm"> </a>
## Step 2 - Find the Project Web App instances in your SharePoint Server farm

Use the `Get-SPProjectWebInstance` cmdlet with the following filters to get the URL, site ID, and database name for the PWA sites that exist in the SharePoint Server farm:

```PowerShell
Get-SPProjectWebInstance | ft -a Url,SiteId,DatabaseName,DatabaseServer
```

You need the information for each site when you delete the user's personal data in a later step.

For example, running the cmdlet on our sample Contoso Project Server farm returns the following three PWA sites:

|URL|SiteID|Database|DatabaseServer|
|:-----|:-----|:-----|:-----|
|`https://contoso/pwa1`|63ed0197-3647-4279-ed5e80855fc7|WSS_Content|SQL01|
|`https://contoso/pwa2`|67fd0727-5279-3321-ef4e90956fc8|WSS_Content|SQL01|
|`https://contoso/pwa3`|63ed0197-3647-4279-eg7e20233fg9|WSS_Content|SQL02|

<a name="site"> </a>
## Step 3 - Find the user's Resource ID or Claims Account on each PWA site

After getting information all PWA sites on your Project Server farm, next you need to find the Resource ID (ResID) or Claims account of the user whose personal data you want to delete. Do this on each of the PWA sites you discovered in Step 1 (since ResIDs differ in each PWA instance).

Run the `FindUser.sql` SQL script to find the user's Resource ID or claims account.  
  
> [!Note] 
> You need to run the `FindUser.sql` SQL script in SQL Server Management Studio and must have farm admin permissions to have access to the appropriate database.

Run the script on the database for the related PWA site. In the example results provided in Step 1, the database for all three Project Web App instances is WSS\_Content.

Provide values for the following parameters in the script:

|Parameter|Description|
|:-----|:-----|
|`@siteID`|The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1.|
|`@searchName`|The display name of the Project Server user.|

For example, if you want to find the userID for Adam Barr on the Contoso PWA1 site you found in the example in Step 1, you would edit the values for the parameters in the script like this:

```PowerShell
DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'

DECLARE @searchName nvarchar(255) = 'Adam Barr'
```

The script returns the Resource Name, Resource ID, email address, and Claims Account values for the user.

<a name="projects"> </a>
## Step 4 - Close all the user's projects

You need to ensure that all of the user's projects are closed in your Project Server environment. This ensures that changes made by the delete script are not overwritten.

If needed, a PWA admin can force-checkin the project through the PWA Server Settings.

1.  On the **Server Settings** page, in the **Queue and Database Administration** section, click **Force Check-in Enterprise Objects**.

2.  On the **Force Check-in Enterprise Objects** page, from the project list, select the checkbox next to the project that needs to be checked, and then click **Check-In**.

3.  A message displays asking if you are sure you want to force-checkin. Click **OK.**

<a name="server"> </a>
## Step 5 - Sync workspace items into Project Server  

The `Sync-ProjectWorkspace.ps1` script creates a queue job in Project Server to do a project workspace full sync. Run this script for each project that contains the user that you're looking for. (You need the Project ID for each project. You can find out the projects relating to the user by doing an export of the WorkspaceItems [Export user data from Project Server Subscription Edition](export-user-data-project-server-subscription-edition.md). Confirm that the queue jobs have completed from **Manage Queue Jobs** in **Project Web App Settings Page** before proceeding with additional steps.

<a name="data"> </a>
## Step 6 - Export the user's data

Before deleting your user's personal data, you should know all projects the user was a part of. This allows you to later verify if the user's data was removed and that you have the correct user to delete. Exporting user data is covered in detail in [Export user data from Project Server Subscription Edition](export-user-data-project-server-subscription-edition.md).

<a name="risks"> </a>
## Step 7- Delete user personal data for issues and risks

Issues and risks are stored in Project Sites, which are part of SharePoint Server. We recommend deleting a user's SharePoint Server information before deleting their Project Server information. This prevents user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, if they exist.

If you delete user information from a Project Site after they have already been deleted from Project Server (or for users who never had a Project Server account), you must use their claims account because Resource ID isn't available once they've been deleted from Project Server.

You can use the `FindUserClaims.sql` script to find claims accounts for all issues risks in the reporting database.

<a name="pwa"> </a>
## Step 8 - Delete your user's data from the PWA site

On the Project Server, as a SharePoint farm admin, run the `Invoke-SPProjectRedactUser` cmdlet to remove user data from the PWA site and to optionally update the display name of the user.

The `Invoke` cmdlet uses the following parameters:

|Parameter|Description|Note|
|:-----|:-----|:-----|
|`-URL`|URL of the Project Web App instance.|Required|
|`-ClaimsAccount`|ClaimsAccount of the user.|Either Claims Account or ResourceID is required.|
|`-ResourceId`|Resource GUID of the user.|Either Claims Account or ResourceID is required.|
|`-UpdateDisplayName`|New display name for the user|If used, RedactTimesheet is also required.|
|`-RedactTimesheet`|Apply changes to timesheets? ($true or $false)||

You can use the `Invoke` cmdlet and parameters in the following ways:

### **Scenario 1: Delete user's information from a Project Web App site except for the display name**

Use this command to remove the user's data from the PWA site, except for the display name. Your organization may want to leave the user's display name for a later review in case it's in a shared item, like a task owner in a project or an entry in a timesheet.

> [!Note] 
> You can specify the user either by claims account or Resource ID.

#### Use the Claims Account  

Use the cmdlet the following way if you are specifying the user by Claims Account

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\>
```

For example, the following removes all data for the user with the claim: 0\#.w|*contoso/bob* throughout the `https://contoso.sharepoint.com/sites/pwa` site, except for the user's display name.

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac”  
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message displays stating: All data for resource \<user's display name\> has been removed, except the name of the resource.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\>
```

For example, the following removes all user data for the user with a resource ID of *0c7cd3fb-a0be-e111-9fte-00155d022d022681* throughout the `https://contoso.sharepoint.com/sites/pwa` site, except for the user's display name

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's resource ID\> has been removed, except the name of the resource.

### **Scenario 2: Delete user's information from a Project Web App site, but update the display name everywhere**

Use this command to remove the user data of a user from the Project Web App site, and change the user's display name to something of your choice, and this occurs in timesheet records. Your organization may want to change the user's display name to something that ensures the user's identity as anonymous, such as "Deleted User".

> [!Note] 
> You can specify the user either by Claims Account or Resource ID.

#### Use the Claims Account

Use the cmdlet the following way if you are specifying the user by logon name:

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $true
```

For example, the following removes all user data for *evac@contoso.onmicrosoft.com* and change the display name to "*Deleted User*" throughout the `https://contoso.sharepoint.com/sites/pwa` site.

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac” -UpdateDisplayName "Deleted User" -RedactTimesheet $true
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message displays stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $true
```

For example, the following removes all user data for the user with a resource ID of *0c7cd3fb-a0be-e111-9fte-00155d022d022681* and changes the display name to "*Deleted User*" throughout the `https://contoso.sharepoint.com/sites/pwa` site.

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $true
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message displays stating: All data for resource \<user's Resource ID\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.

### **Scenario 3: Delete user's information from a Project Web App site, but change the display name everywhere except for timesheet records**

Use this command to remove the user's data from the Project Web App site, and change the user's display name to something you specify, **but this won't occur in timesheet records**. Your organization may want to later analyze if they have a business reason to retain the users display name in their timesheet records.

> [!Note] 
> You can specify the user either by Claims Account or Resource ID.

#### Use the Claims Account

Use the cmdlet the following way if you are specifying the user by Claims Account:

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $false*
```

For example, the following removes all data for *evac@contoso.onmicrosoft.com* and changes the display name to "*Deleted User*" throughout the `https://contoso.sharepoint.com/sites/pwa` site, except in timesheet records.

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac” -UpdateDisplayName "Deleted User" -RedactTimesheet $false*
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message displays stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

```PowerShell
Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $false*
```

For example, the following removes all personal data for the user with a resource ID of 0c7cd3fb-a0be-e111-9fte-00155d022d022681 and changes the display name to "Deleted User" throughout the `https://contoso.sharepoint.com/sites/pwa` site, except in timesheet records.

```PowerShell
Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $false
```

When running this command, a message displays asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message displays stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.

<a name="objects"> </a>
## Step 9 - Redact resource information from archived objects  

### **Archived project data**

For projects where the resource was redacted:

1.  In Project Web App settings, choose **Delete enterprise objects**.

2.  Choose **Delete archived projects**.

3.  Delete the required archived projects.

### **Archived non-project data**

Project Server only keeps a single version of the following archived items:

-   Enterprise Resource Pool and Calendars

-   Enterprise Custom Fields

-   Enterprise Global

Take a new [administrative backup](/Project/back-up-item-level-objects-through-administrative-backup-project-server-2013). This overwrites the previous version with the version where the resource’s personal data has been redacted.

<a name="users"> </a>
## Step 10 - Clear the cache for Project client users connecting to the PWA site

On all devices on which Project Professional or the Project Online Desktop Client connected to the Project Web App site, an IT admin needs to clear the cache. Clearing the cache prevents the projects in which user information was deleted from being updated from cached data that remains on the system. You also need to make sure that none of the user's projects are open on the client before clearing the cache.

To clear the cache in Project Professional 2019/2021 and the Project Online Desktop Client:

1.  Select the **File** menu, and then click **Options**.

2.  On the **Project Options** page, select **Save**.

3.  In the **Cache** section, select **Clean Up Cache**.
