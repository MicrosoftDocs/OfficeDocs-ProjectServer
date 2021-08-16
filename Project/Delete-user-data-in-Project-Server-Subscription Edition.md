---
title: "Delete user data from Project Server Subscription Edition Public Preview"
ms.author: v-bshilpa
author: Benny-54
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal

description: "Learn how an Farm admin can delete a specific user's data from a Project Server Subscription Edition Public Preview environment."
---
# Delete user data from Project Server Subscription Edition Public Preview

> **Important!**: The process to delete user data from Project Server 2019 Public Preview is very different from the process used for Project Server 2016, Project Server 2013, and Project Server 2010. To learn how to delete user data from previous versions of Project Server, see [Delete user data from Project Server](delete-user-data-from-project-server.md).

Learn how a Farm admin can delete a specific user's data from a Project Server environment. 

This article describes:

-   What user information is deleted?

-   Delete scenarios

-   Process Overview

-   Step 1 - Find the Project Web App instances in your SharePoint Server farm

-   Step 2 - Find the user's Resource ID or Claims Account on each PWA site

-   Step 3 - Close all the user's projects

-   Step 4 - Sync workspace items into Project Server

-   Step 5 - Export the users data

-   Step 6 - Delete user personal data for Issues and Risks

-   Step 7 - Open the resources calendar and clear out the exception reason for the user

-   Step 8 - Delete the user's personal information from the Resource and Project Resources tables

-   Step 9 - Clear the cache for Project Professional users connecting to the Project Server instance.

## What user information is deleted?

<span id="user-content-Whatdata" class="anchor"></span>In Project Server, admins can use the steps detailed in this article to delete a user's personal data and personal identifying data (data that can be used to identify the user), such as:

-   **Display name, phonetic name, GUIDs** - You can choose to delete or rename the user Display Name (details in how to run the script).

-   **Users specific view settings** - For example, if the user has customizations on their view settings (views, filters, groups, tables, maps, drawing, reports) ﻿on top of grid pages with views (such as the Resource Center, Project Center, Schedule webpart, etc.), these are deleted.

-   **Calendar exception details** - For example, if the user was out for a week in January because he or she was sick or on vacation, the name of the exception needs to be manually deleted. The dates will remain the same.

-   **User Permissions -** For example, if user ﻿is ﻿associated with project server categories, groups/ has been granted individual global permissions, we will go ahead and remove ﻿all the associations. The user will also be set as inactive.

User personal information contained in Project sites, issues, and risks are stored in SharePoint and are not deleted through this process. You will need to delete this data directly from SharePoint Server.

**IMPORTANT:** We recommend running the SharePoint Server user information delete process before deleting the same user's information from Project Server. This will prevent user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, should they still exist.

## Delete scenarios  

Depending on your needs, this process allows you to delete your user's personal information listed above, but also allows some control of in regards to deleting the users display name in shared items, such as timesheets, projects, and assignments. There are three delete scenarios that you can do:


### **Scenario 1: Delete user's information from a Project Web App instance except for the display name**

In this scenario, all of the user's personal information is deleted, but the user's display name will remain intact.

You might choose this scenario if you need to do further review of shared items (such as timesheets and projects) in which the user was active.

### **Scenario 2: Delete user's information from a Project Web App instance, but update the display name everywhere**

In this scenario, all of the user's personal information is deleted. In all locations where the user's display name was shown, it is replaced with a string of your choosing, such as "Deleted User." The resource ID for the user remains.

You might choose this scenario if there is no business need to retain the user display name, even in shared records such as timesheets and projects.

### **Scenario 3: Delete user's information from a Project Web App instance, but change the display name everywhere except for timesheet records**

In this scenario, all of the user's personal information is deleted, except in timesheet records. You can choose to replace the user's display name with another string, such as "Deleted User." However, this will not affect timesheet records, where the user name still remains. The updated display name is unlinked from its timesheets records and a new Resource ID is generated so that the updated user name cannot be identified through data in timesheet records.

You might choose this scenario if you need to do further review of timesheet records in which the user appears as either a submitter or approver.

## Process Overview

<span id="user-content-Overview" class="anchor"></span>The following is an overview of the process to delete a specific user's information in Project Web App:

1.  **Download** the export scripts from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=871966).

2.  **Find the PWA sites in your environment**: Find a listing of Project Web App instances in your Project Server farm.

3.  **Find the user's resource ID**: On each Project Web App instance, find the unique Resource ID for the user by specifying the user's claims account.

4.  **Close all the user’s projects**: This ensures that changes will be made to all projects in which the user has information.

5.  **Sync workspace items into Project Server**:

6.  **Perform an export of the user's data**: This procedures is described in [Export user data in Project Server 2019 Public Preview](export-user-data-in-project-server-2019.md).

7.  **Delete user personal data from Issues and Risks**:

8.  **Delete your user’s data from the PWA site:** Run the script to delete the user's information from each PWA site.

9.  **Redact resource information from archived objects:**

10. **Clear the cache for Project client users connecting to the PWA site**:

## Step 1 - Download the export script files

<span id="DownloadScripts" class="anchor"></span>Click [here](https://go.microsoft.com/fwlink/?linkid=871966) to download the export scripts.

Important notes about running the export scripts:

-   Run the .sql script in the context of the database where the information resides. You must have db\_datareader permissions on the database.

-   You may need to "unblock" the zip file because by default, executing scripts downloaded from the Internet is not allowed. Do the following to unblock your files:

1.  In File Explorer, go to the location where you saved the zip file.

2.  Right click on the zip file, and click **Properties**.

3.  On the **General** tab, select **Unblock**. 

4.  Click **OK.**

All files contained in the zip file should now be Unblocked. You can verify this in the individual files by checking to see if the **Unblocked** checkbox option no longer appears in the **General** tab of the file's **Properties** page.

**Note**: If you only have access to unzipped files, you can also unblock each file individually.

## Step 2 - Find the Project Web App instances in your SharePoint Server farm

<span id="FindPWA" class="anchor"></span>Use the Get-SPProjectWebInstance cmdlet with the following filters to get the URL, site ID, and database name for the PWA sites that exist in the SharePoint Server farm:

> *Get-SPProjectWebInstance | ft -a Url,SiteId,DatabaseName,DatabaseServer*

You will need the information for each site when you delete the user's personal data in a later step.

For example, running the cmdlet on our sample Contoso Project Server farm might return the following three PWA sites:

<table>
<thead>
<tr class="header">
<th align="left">URL</th>
<th align="left">SiteID</th>
<th align="left">Database</th>
<th align="left">DatabaseServer</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left"><a href="https://contoso/pwa1" class="uri">https://contoso/pwa1</a> </td>
<td align="left">63ed0197-3647-4279-ed5e80855fc7 </td>
<td align="left">WSS_Content </td>
<td align="left">SQL01 </td>
</tr>
<tr class="even">
<td align="left"><a href="https://contoso/pwa2" class="uri">https://contoso/pwa2</a> </td>
<td align="left">67fd0727-5279-3321-ef4e90956fc8 </td>
<td align="left">WSS_Content </td>
<td align="left">SQL01 </td>
</tr>
<tr class="odd">
<td align="left"><a href="https://contoso/pwa3" class="uri">https://contoso/pwa3</a> </td>
<td align="left">63ed0197-3647-4279-eg7e20233fg9 </td>
<td align="left">WSS_Content </td>
<td align="left">SQL02 </td>
</tr>
</tbody>
</table>

<span id="bkmk_runtheexportpowershellscript" class="anchor"></span>

## Step 3 - Find the user's Resource ID or Claims Account on each PWA site

<span id="FindResID" class="anchor"></span>After getting information all PWA sites on your Project Server farm, next you need to find the Resource ID (ResID) or Claims account of the user whose personal data you want to delete. Do this on each of the PWA sites your discovered in Step 1 (since ResIDs differ in each PWA instance).

Run the FindUser2019.sql SQL script to find the user's Resource ID or claims account.  
  
**Note**: You need to run the FindUser2019.sql SQL script in SQL Server Management Studio and must have farm admin permissions to have access to the appropriate database.

Run the script on the database for the related PWA site. In the example results provided in Step 1, the database for all three Project Web App instances is *WSS\_Content* .

Provide values for the following parameters in the script:

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Description</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">@siteID</td>
<td align="left">The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1. </td>
</tr>
<tr class="even">
<td align="left">@searchName </td>
<td align="left">The display name of the Project Server user. </td>
</tr>
</tbody>
</table>

For example, if you want to find the userID for Adam Barr on the Contoso PWA1 site you found in the example in Step 1, you would edit the values for the parameters in the script like this:

> *DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'*
>
> *DECLARE @searchName nvarchar(255) = 'Adam Barr'*

The script returns the Resource Name, Resource ID, email address, and Claims Account values for the user.

## Step 4 - Close all the user's projects

<span id="user-content-Step4" class="anchor"></span>You need to ensure that all of the user's projects are closed in your Project Server environment. This will ensure that changes made by the delete script are not overwritten.

If needed, a PWA admin can force-checkin the project through the PWA Server Settings.

1.  On the **Server Settings** page, in the **Queue and Database Administration** section, click **Force Check-in Enterprise Objects**.

2.  On the **Force Check-in Enterprise Objects** page, from the project list, select the checkbox next to the project that needs to be checked, and then click **Check-In**.

3.  A message will display asking if you are sure you want to force-checkin. Click **OK.**

## Step 5 - Sync workspace items into Project Server  

<span id="user-content-SyncWorkspaceItems" class="anchor"></span>The Sync-ProjectWorkspace2019.ps1 script creates a queue job in Project Server to do a project workspace full sync. Run this script for each project that contains the user that you're looking for. (You will need the Project ID for each project. You can find out the projects relating to the user by doing an export of the WorkspaceItems [Export user data from Project Server 2019 Public Preview](export-user-data-from-project-server-2019 Public Preview.md). [Confirm that the queue jobs have completed](manage-queue-jobs-project-server-2013.md) before proceeding with additional steps.

  
## Step 6 - Export the users data

<span id="user-content-Step3" class="anchor"></span>Before deleting your user's personal data, you should know all projects the user was a part of. This will allow you to later verify if the user's data was removed and that you have the correct user to delete. Exporting user data is covered in detail in Export user data from Project Server 2019 Public Preview.

## Step 7- Delete user personal data for Issues and Risks

<span id="user-content-DeletePersonalData" class="anchor"></span>Issues and Risks are stored in Project Sites, which are part of SharePoint Server. We recommend deleting a user's SharePoint Server information before deleting their Project Server information. This will prevent user personal information in Project Server issues and risks from being updated by corresponding SharePoint Server data, should they still exist.

If you delete user information from a Project Site after they have already been deleted from Project Server (or for users who never had a Project Server account), you must use their claims account because Resource ID isn't available once they've been deleted from Project Server.

You can use the FindUserClaims2019.sql script to find claims accounts for all issues risks in the reporting database.

## Step 8 - Delete your user's data from the PWA site

On the Project Server, as a SharePoint farm admin, execute the Invoke-SPProjectRedactUser cmdlet to remove user data from the PWA site and to optionally update the display name of the user.

The **Invoke** cmdlet uses the following paramaters:

<table>
<thead>
<tr class="header">
<th align="left">Parameter</th>
<th align="left">Description</th>
<th align="left">Note</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">-URL</td>
<td align="left">URL of the Project Online instance.</td>
<td align="left">Required</td>
</tr>
<tr class="even">
<td align="left">-ClaimsAccount</td>
<td align="left">ClaimsAccount of the user.</td>
<td align="left">Either Claims Account or ResourceID is required.</td>
</tr>
<tr class="odd">
<td align="left">-ResourceId</td>
<td align="left">Resource GUID of the user.</td>
<td align="left">Either Claims Account or ResourceID is required.</td>
</tr>
<tr class="even">
<td align="left">-UpdateDisplayName</td>
<td align="left">New display name for the user</td>
<td align="left">If used, RedactTimesheet is also required.</td>
</tr>
<tr class="odd">
<td align="left">-RedactTimesheet</td>
<td align="left">Apply changes to timesheets? (<em>$true</em> or <em>$false</em>)</td>
<td align="left"></td>
</tr>
</tbody>
</table>

You can use the Invoke cmdlet and parameters in the following ways:

### **Scenario 1: Delete user's information from a Project Online instance except for the display name**

Using this command will remove the user's data from the PWA site, except for the display name. Your organization may want to leave the user's display name for a later review in case it's in a shared item, like a task owner in a project or an entry in a timesheet.

Note that you can specify the user either by claims account or Resource ID.

#### Use the Claims Account  
Use the cmdlet the following way if you are specifying the user by Claims Account
> *Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\>*

For example, the following remove all data for the user with the claim :0\#.w|*contoso/bob* throughout the *https://contoso.sharepoint.com/sites/pwa* site, except for the user's display name.

> *Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac”  
> *

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's display name\> has been removed, except the name of the resource.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

> *Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\>*

For example, the following removes all user data for the user with a resource ID of *0c7cd3fb-a0be-e111-9fte-00155d022d022681* throughout the *https://contoso.sharepoint.com/sites/pwa site*, except for the user's display name

> *Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681*

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's resource ID\> has been removed, except the name of the resource.

### **Scenario 2: Delete user's information from a Project Server instance, but update the display name everywhere**

Using this command will remove the user data of a user from the Project Online instance, and will change the user's display name to something of their choosing, and this will also occur in timesheet records. Your organization may want to change the user's display name to something that will make the user's identity anonymous, such as "Deleted User".

Note that you can specify the user either by Claims Account or Resource ID.

#### Use the Claims Account

Use the cmdlet the following way if you are specifying the user by logon name:

> Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $true

For example, the following will remove all user data for *evac@contoso.onmicrosoft.com* and will change his display name to "*Deleted User*" throughout the *https://contoso.sharepoint.com/sites/pwa* site.

Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac” -UpdateDisplayName "Deleted User" -RedactTimesheet $true

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

> Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $true

For example, the following will remove all user data for the user with a resource ID of *0c7cd3fb-a0be-e111-9fte-00155d022d022681* and will change the display name to "*Deleted User*" throughout the *https://contoso.sharepoint.com/sites/pwa* site.

> Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $true

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's Resource ID\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.

### **Scenario 3: Delete user's information from a Project Web App site, but change the display name everywhere except for timesheet records**

Using this command will remove the user's data from the Project Web App site, and will change the user's display name to something you specify, **but this will not occur in timesheet records**. Your organization may want to later analyze if they have a business reason to retain the users display name in their timesheet records.

Note that you can specify the user either by Claims Account or Resource ID.

#### Use the Claims Account

Use the cmdlet the following way if you are specifying the user by Claims Account:

> *Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ClaimsAccount \<ClaimsAccount\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $false*

For example, the following will remove all data for *evac@contoso.onmicrosoft.com* and will change his display name to "*Deleted User*" throughout the *https://contoso.sharepoint.com/sites/pwa* site, except in timesheet records.

> *Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ClaimsAccount “i:0\#.w|contoso\\evac” -UpdateDisplayName "Deleted User" -RedactTimesheet $false*

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.

#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:

> *Invoke-SPProjectRedactUser  -Url \<PWASiteURL\> -ResourceID \<ResourceID\> -UpdateDisplayName "\<newDisplayName\>" -RedactTimesheet $false*

For example, the following will remove all personal data for the user with a resource ID of 0c7cd3fb-a0be-e111-9fte-00155d022d022681 and will change the display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site, except in timesheet records.

> *Invoke-SPProjectRedactUser  -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $false*

When running this command, a message will display asking you to confirm if you want to proceed.

After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.

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

Take a new [administrative backup](https://review.docs.microsoft.com/Project/back-up-item-level-objects-through-administrative-backup-project-server-2013). This will overwrite the previous version with the version where the resource’s personal data has been redacted.

## Step 10 - Clear the cache for Project client users connecting to the PWA site

On all devices on which Project Professional or the Project Online Desktop Client connected to the Project Online instance, an IT admin needs to clear the cache. Clearing the cache will prevent projects in which user information was deleted from being updated from cached data that remains on the system. You also need to make sure that none of the user's projects are open on the client before clearing the cache.

To clear the cache in Project Professional 2016 and the Project Online Desktop Client:

1.  Select the **File** menu, and then click **Options**.

2.  On the **Project Options** page, select **Save**.

3.  In the **Cache** section, select **Clean Up Cache**.
