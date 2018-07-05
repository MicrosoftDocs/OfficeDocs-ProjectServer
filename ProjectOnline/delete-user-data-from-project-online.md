---
title: "Delete user data from Project Online"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 5/25/2018
ms.audience: Admin
ms.topic: article
ms.service: project-online
localization_priority: Normal
ms.custom: Adm_Project
search.appverid: PJO150
ms.assetid: 252fa593-9c25-47ed-b861-643fe8bf1cb7
description: "Learn how an Office 365 global administrator can delete a user's information from a Project Online environment."
---

# Delete user data from Project Online

Learn how an Office 365 global administrator can delete a user's information from a Project Online environment.
  
- [What user data is deleted?](delete-user-data-from-project-online.md#Whatdata)
    
- [Delete scenarios](delete-user-data-from-project-online.md#scenarios)
    
- [Process Overview](delete-user-data-from-project-online.md#Overview)
    
- [Step 1 - Download the delete script files](delete-user-data-from-project-online.md#script)
    
- [Step 2 - Find the Project Web App sites in your Office 365 environment](delete-user-data-from-project-online.md#Step1)
    
- [Step 3 - Find the user's Resource ID on each PWA site (optional)](delete-user-data-from-project-online.md#Step2)
    
- [Step 4 - Close and check in all of the user's projects](delete-user-data-from-project-online.md#CloseCheckIn)
    
- [Step 5 - Export the users data (optional)](delete-user-data-from-project-online.md#Step3)
    
- [Step 6 - Delete user account information added through SharePoint Online](delete-user-data-from-project-online.md#claims)
    
- [Step 7 - Delete your user's data from the PWA site](delete-user-data-from-project-online.md#step5)
    
- [Step 8 - Clear the cache for Project client users connecting to the PWA site](delete-user-data-from-project-online.md#step6)
    
## What user data is deleted?
<a name="Whatdata"> </a>

In Project Online, admins can use the steps detailed in this article to delete user data and identifying data (data that can be used to identify a user), such as:
  
- **Display name, phonetic name, GUIDs** - You can choose to delete or rename the user's display name. 
    
- **Users specific view settings** - For example, if the user has customizations on their view settings (views, filters, groups, tables, maps, drawing, reports) ﻿on top of grid pages with views (such as the Resource Center, Project Center, Schedule webpart, etc.), these are deleted. 
    
- **Calendar exception details** - For example, if the user was out for a week in January because he or she was sick or on vacation, the name of the exception is removed. Dates for the exception will remain. 
    
- **User Permissions** - For example, if user ﻿is ﻿associated with categories, groups or has been granted individual global permissions, we will remove ﻿all the associations. The user will also be set as inactive. 
    
User information contained in Project sites - such as issues, risks, deliverables, and documents - that are stored in SharePoint Online might not be deleted through the Project Online user data delete process because some of these users are given access to the project site but aren't PWA users. You will need to delete this data through the process found in the [Step 6 - Delete user account information added through SharePoint Online](delete-user-data-from-project-online.md#claims) section of this article. 
  
> [!IMPORTANT]
> We recommend running the SharePoint Online user data delete process before deleting the same user's information from Project Online. This will prevent issues in which syncing with certain SharePoint Online items (such as Issues or Risks) will overwrite user data in Project Online that has been deleted. 
  
### How does this differ from deleting a user through Enterprise Object Delete?

The user data delete process described in this article is different from deleting a PWA user through the Enterprise Object Delete page in PWA Server Settings in several ways:
  
- Enterprise Object Delete will delete the user as an enterprise resource. However, deletion is blocked if the user/resource is any one of the following:
    
  - A project owner
    
  - A timesheet manager
    
  - On timesheet manager list
    
  - An assignment owner
    
  - In a resource plan
    
  - A workflow proxy user
    
- Deleting user data through the steps in this article does not delete the enterprise resource. It changes the user account to inactivate, removes the user data, and can optionally change the name of the resource to something you choose (such as "Deleted User") .
    
## Delete scenarios
<a name="scenarios_1"> </a>

Depending on your needs, this process allows you to delete your user data listed above, but also allows some control of in regards to deleting the users display name in shared items, such as timesheets, projects, and assignments. There are three delete scenarios that you can do:
  
### Scenario 1: Delete user's information from Project Online except for the display name

In this scenario, all of the user's data is deleted, except for the user's display name.
  
You might choose this scenario if you want to know the work the user has done, such as through their timesheets and tasks. 
  
### Scenario 2: Delete user's information from Project Online, but update the display name everywhere

In this scenario, all of the user's information is deleted. In all locations where the user's display name was shown, it will be replaced with something of your choosing, such as "Deleted User". The resource ID for the user will remain.
  
You might choose this scenario if there is no business need to retain the user display name, even in shared records such as timesheets and projects.
  
### Scenario 3: Delete user's information from Project Online, but update the display name everywhere except for timesheet records

In this scenario, all of the user's information is deleted, except in timesheet records. You can choose to replace the user's display name with something your choose, such as "Deleted User". However, this will not affect timesheet records, where the user name will still remain. The display name in the timesheets records is generated a new Resource ID so that the updated user name cannot be identified through data in timesheet records.
  
You might choose this scenario you need to do further review of timesheet records in which the user appears.
  
## Process Overview
<a name="Overview"> </a>

The following is an overview of the process that admins need to do to delete a specific user's information in their Project Online environment:
  
1. **Download your PowerShell scripts**: You need to download and unzip the PowerShell script files needed in this article. 
    
2. **Find the PWA sites that contain the user's data**: Find a listing of Project Web App sites in your environment.
    
3. **Find the user's resource ID on each PWA site (optional)**: On each Project Web App site, find the unique Resource ID for the user. You can also choose to specify the user by login account (for example, adambarr@contoso.onmicrosoft..com).
    
4. **Close and check in all of the user's projects**: This needs to happen before running the export scripts to ensure that your changes aren't overwritten. 
    
5. **Perform an export of the user's data**: This optional step is described in [Export user information from Project Online ](export-user-data-from-project-online.md). 
    
6. **Delete user account information added through SharePoint Online (optional)**: This step is only required if you need to delete a non-PWA users account information, such as a user who might have been given access to a project site. 
    
7. **Delete your user's data from the PWA site**: Run the script to delete the user's information from each PWA site.
    
    Through the script, you can choose to change the user's display name to something different (for example, "Deleted User"). This is allows you to make the user anonymous, while keeping the item in which the user information appears relatively unchanged.
    
8. **Delete the cache for Project Professional users**: After the script is completed successfully, PWA admins need to delete the cache on each device in which Project Professional was used to open the project while connected to the Project Online site. Clearing the cache prevents the user info from being readded to the project if it is cached on the device.
    
 **Work with your Project Admins**
  
Depending on your company, your Office 365 global admin might be knowledgeable about managing Office 365 administrative tasks, but may know little about Project Online administration. If this is the case, we recommend that the Office 365 global admin work collaboratively with their PWA site admins to accomplish these tasks. For example, a global admin would probably be best suited to run the PowerShell script to find all PWA sites, but would probably need to work collaboratively with the PWA admin to accomplish the remaining steps and for help regarding business rules and configuration of each PWA site.
  
> [!IMPORTANT]
> As a best practice, make sure to backup your Project databases before deleting user data from your site. You can delete your backup once you are sure you were successful. 
  
## Step 1 - Download the delete script files
<a name="script"> </a>

You will need the use of several prepare PowerShell script files for the procedures in this article. The script files referenced in this article are contained in the [Project Online User Content Export and Delete script package](https://go.microsoft.com/fwlink/?linkid=871953). Download and upzip the files to a location you can reference.
  
## Step 2 - Find the Project Web App sites in your Office 365 environment
<a name="Step1"> </a>

Global admins will need to use the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/?linkid=867805) to connect to their SharePoint Online Admin Center and run the **[Get-SPOSite](https://go.microsoft.com/fwlink/?linkid=873061)** PowerShell cmdlet to get a listing of URLs for each PWA site in their Office 365 environment. 
  
> [!NOTE]
> To run the Get-SPOSite PowerShell cmdlet, you need to be either in a Global admin or SharePoint admin role. 
  
1. In the SharePoint Online Management Shell module, connect to your SharePoint Online Admin Center with the **[Connect-SPOService](https://go.microsoft.com/fwlink/?linkid=873059)** cmdlet: 
    
  ```
  Connect-SPOService -URL <AdminSiteURL> 
  ```

    For example:
    
  ```
  Connect-SPOService -URL http://contoso-admin.sharepoint.com 
  ```

    After connecting to your SharePoint Online Admin Center, use the Get-SPOSites PowerShell cmdlet to find all PWA sites in your Office 365 environment:
    
2. 2. After connecting to your SharePoint Online Admin Center, use the [Get-SPOSite](https://go.microsoft.com/fwlink/?linkid=873061) PowerShell cmdlet to find all PWA sites in your Office 365 environment: 
    
  ```
  Get-SPOSite | ?{$_.PWAEnabled -eq "Enabled"} | ft -a Url,Owner
  ```

    After successfully running, a list of all PWA sites and site owners in your Office 365 environment will display.
    
## Step 3 - Find the user's Resource ID on each PWA site (optional)
<a name="Step2"> </a>

> [!IMPORTANT]
> If you have the user's login account, this step is optional. You will need either the user's **login account** or **Resource ID** for each PWA site in order to run the delete script. 
  
If you want to find the user's resource ID, PWA admins need to do the following on each PWA site that you found in the previous step:
  
1. In the Project Online **Server Settings**, in the **Enterprise Data** section, click **Resource Center**.
    
2. On the **Resource Center** page, in the ** Resource Name ** column, locate the user's name then look in that row to see if you can find a value in the **Unique ID** column. This value is the user's Resource ID. For example, in the graphic below, you can see Aaron Painter's Resource ID value listed in the Unique ID column. 
    
    ![User's Resource ID in the Unique ID column](media/1dee114a-2efc-4368-9e7c-6ecd614f1409.png)
  
    In some cases, your table may be customized so that the Unique ID column is not available. If so, select the checkbox to the left of the user name and then click **Edit** located in the **Resources** tab in the ribbon, and then go to the next step. 
    
3. On the **Edit Resource** page for the specific user, go to the **System Identification Data** section and find the value listed for the **GUID**. The GUID is the users resource ID for this PWA site.
    
    ![Finding a users Resource ID](media/5d716343-d912-46f8-a5b1-42e994644fbb.png)
  
> [!NOTE]
> If you have multiple PWA sites, each PWA site will have a different Resource ID for the same user. Make sure to pair the Resource ID your find for the user with the specific PWA site URL. 
  
## Step 4 - Close and check in all of the user's projects
<a name="CloseCheckIn"> </a>

Before running the export script., you need to ensure that all of the user's projects are closed and checked in by users on your PWA site. This will ensure that changes made by the delete script are not overwritten. 
  
If needed, a PWA admin can force-checkin the project through the PWA Server Settings.
  
1. On the **Server Settings** page, in the Queue and Database Administration section, click **Force Check-in Enterprise Objects**. 
    
2. On the **Force Check-in Enterprise Objects** page, from the project list, select the checkbox next to the project that needs to be checked, and then click ** Check-In **. 
    
3. A message will display asking if you are sure you want to force-checkin. Click **OK**. 
    
> [!NOTE]
> Forcing a check-in of a project that is being modified by a user may result in the loss of those changes. We highly recommend that users check in projects in the typical manner and that you use force check-in only when it is absolutely necessary. 
  
## Step 5 - Export the users data (optional)
<a name="Step3"> </a>

Before deleting your user's data, you should know all projects in which the user was a part of. This will allow you to later verify if the user's data was removed, since some issue might have prevented deletion from happening (for example, the project was checked out. You can see these projects through exporting the user's data. To learn how to do this, see [Export user information from Project Online (GDPR)](export-user-data-from-project-online.md).
  
The export script will also tell you if any of the user's projects are current checked out, since they need to be checked in prior to running the RedactProjectUser script in the next step.
  
If needed, a PWA admin can force a checkin of the project through the PWA Server Settings. 
  
1. On the **Server Settings** page, in the **Queue and Database Administration** section, click **Force Check-in Enterprise Objects**. 
    
2. ﻿On the **Force Check-in Enterprise Objects** page, from the project list, select the checkbox next to the project that needs to be checked, and then click **Check-In**. 
    
3. ﻿A message will display asking if you are sure you want to force-checkin. Click **OK.**
    
> [!IMPORTANT]
> If you force check-in an project that a user is modifying, the modifications may be lost. 
  
## Step 6 - Delete user account information added through SharePoint Online
<a name="claims"> </a>

> [!NOTE]
> If you are deleting user data from SharePoint Online as well, we recommend deleting the SharePoint Online user data before deleting the Project Online user data to prevent sync issues that can overwrite deleted content. 
  
Users in your Office 365 environment who do not have Project Web App (PWA) accounts can also have their name and account information in Project Online, and may want to delete it. This can happen if the user added certain SharePoint objects to a project site. A project site is a SharePoint collaboration site that that can be created when a project is created. SharePoint users who are not PWA users can be granted access to these collaboration sites. When this happens, their account information is saved can be saved to PWA.. If an admin is deleting user data in SharePoint Online, they should also look to see if they need to delete the users data in Project Online as well if they notice any of the following in the SharePoint Online export data:
  
- Issues associated with a project site
    
- Risks associated with a project site
    
- Documents associated with a project site
    
- Deliverables associated with a project site
    
If the SharePoint Online user data shows any of the above, you can also delete the users account information from the Project Online site by running the RedactProjectUser PowerShell script specifying the login account information (since the user won't have a resource ID):
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -LoginName <logonName> -UpdateDisplayName "<newDisplayName>" -RedactTimesheet $true

```

For example, from the SharePoint Online export data, you discovered that Eva Corets (account name of evac@contoso.com), added issues and risks to a project site that was part of a specific PWA site (https://contoso.sharepoint.com/sites/pwa1). Running the following will update all instance of her account name to "Deleted User" on the specific PWA site.
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -LoginName evac@contoso.onmicrosoft.com -UpdateDisplayName "Deleted User" -RedactTimesheet $true
```

## Step 7 - Delete your user's data from the PWA site
<a name="step5"> </a>

Run the **RedactProjectUser** PowerShell script in the [SharePoint Online Management Shell](https://go.microsoft.com/fwlink/?linkid=867805) to remove user data from the PWA site and to optionally update the display name of the user. 
  
The RedactProjectUser PowerShell script is included with the [Project Online User Content Export and Delete script package](https://go.microsoft.com/fwlink/?linkid=871953).
  
> [!NOTE]
>  In order to run the RedactProjectUser script, you need be at least one of the following: >  A site collection admin to the PWA Site for which you are running the script. >  If you are in Project permission mode, be assigned Manage Users and Groups permissions on the Project Online instance. If you are in SharePoint permission mode, be in the Global admin or SharePoint admin role. 
  
In the SharePoint Online Management Shell, you will be using the **Invoke** cmdlet to run the RedactProjectUser script: 
  
```
Invoke-RedactProjectUser  
```

The **Invoke** cmdlet uses the following paramaters: 
  
|**Parameter**|**Description**|**Note**|
|:-----|:-----|:-----|
|-URL  <br/> |URL of the Project Online instance.  <br/> |Required  <br/> |
|-LoginName  <br/> |Login name of the user.  <br/> |Either LoginName or ResourceID is required.  <br/> |
|-ResourceId  <br/> |Resource GUID of the user.  <br/> |Either LoginName or ResourceID is required.  <br/> |
|-UpdateDisplayName  <br/> |New display name for the user  <br/> |If used, RedactTimesheet is also required.  <br/> |
|-RedactTimesheet  <br/> |Apply changes to timesheets? ( *$true*  or  *$false*  )  <br/> ||
|-Region  <br/> | This optional parameter specifies the Office 365 environment you are using. The values you can use for this parameter include:  <br/> **Default** - Project Public Cloud.  <br/> **China** - Gallatin.  <br/> **Germany** - BlackForest .  <br/> **ITAR** - Office 365 United States Government.  <br/>  If the parameter is not used, the default value is used (  *Default*  ).  <br/> ||
   
You can use the Invoke cmdlet and parameters in the following ways:
  
### Scenario 1: Delete user's information from a Project Online instance except for the display name

Using this command will remove the user's data from the PWA site, except for the display name. Your organization may want to leave the user's display name for a later review in case it's in a shared item, like a task owner in a project or an entry in a timesheet.
  
Note that you can specify the user either by logon name or Resource ID.
  
#### Use the logon name

Use the cmdlet the following way if you are specifying the user by logon name:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -LoginName <loginName>
```

For example, the following remove all data for the user * evac@@contoso.onmicrosoft.com *  throughout the  *https://contoso.sharepoint.com/sites/pwa*  site, except for the user's display name 
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -LoginName evac@@contoso.onmicrosoft.com
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating:  *All data for resource \<user's display name\> has been removed, except the name of the resource.* 
  
#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -ResourceID <ResourceID>
```

For example, the following removes all user data for the user with a resource ID of  *0c7cd3fb-a0be-e111-9fte-00155d022d022681*  throughout the  *https://contoso.sharepoint.com/sites/pwa site*  , except for the user's display name 
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating:  *All data for resource \<user's resource ID\> has been removed, except the name of the resource.* 
  
### Scenario 2: Delete user's information from a Project Online instance, but update the display name everywhere

Using this command will remove the user data of a user from the Project Online instance, and will change the user's display name to something of their choosing, and this will also occur in timesheet records. Your organization may want to change the user's display name to something that will make the user's identity anonymous, such as "Deleted User".
  
Note that you can specify the user either by logon name or Resource ID.
  
#### Use the logon name

Use the cmdlet the following way if you are specifying the user by logon name:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -LoginName <logonName> -UpdateDisplayName "<newDisplayName>" -RedactTimesheet $true
```

For example, the following will remove all user data for  *evac@contoso.onmicrosoft.com*  and will change his display name to "  *Deleted User*  " throughout the  *https://contoso.sharepoint.com/sites/pwa*  site. 
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -LoginName evac@contoso.onmicrosoft.com -UpdateDisplayName "Deleted User" -RedactTimesheet $true
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating:  *All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.* 
  
#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -ResourceID <ResourceID> -UpdateDisplayName "<newDisplayName>" -RedactTimesheet $true
```

For example, the following will remove all user data for the user with a resource ID of  *0c7cd3fb-a0be-e111-9fte-00155d022d022681*  and will change the display name to "  *Deleted User*  " throughout the  *https://contoso.sharepoint.com/sites/pwa*  site. 
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $true
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating:  *All data for resource \<user's Resource ID\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere including timesheet records.* 
  
### Scenario 3: Delete user's information from a Project Web App site, but change the display name everywhere except for timesheet records

Using this command will remove the user's data from the Project Web App site, and will change the user's display name to something you specify, **but this will not occur in timesheet records**. Your organization may want to later analyze if they have a business reason to retain the users display name in their timesheet records. 
  
Note that you can specify the user either by logon name or Resource ID.
  
#### Use the logon name

Use the cmdlet the following way if you are specifying the user by logon name:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -LoginName <logonName> -UpdateDisplayName "<newDisplayName>" -RedactTimesheet $false
```

For example, the following will remove all data for  *evac@contoso.onmicrosoft.com*  and will change his display name to "  *Deleted User*  " throughout the  *https://contoso.sharepoint.com/sites/pwa*  site, except in timesheet records. 
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -LoginName evac@contoso.onmicrosoft.com -UpdateDisplayName "Deleted User" -RedactTimesheet $false
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating:  *After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's Resource ID\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.* 
  
#### Use the Resource ID

Use the cmdlet the following way if you are specifying the user by Resource ID:
  
```
.\Invoke-RedactProjectUser.ps1 -Url <PWASiteURL> -ResourceID <ResourceID> -UpdateDisplayName "<newDisplayName>" -RedactTimesheet $false
```

For example, the following will remove all personal data for the user with a resource ID of 0c7cd3fb-a0be-e111-9fte-00155d022d022681 and will change the display name to "Deleted User" throughout the https://contoso.sharepoint.com/sites/pwa site, except in timesheet records.
  
```
.\Invoke-RedactProjectUser.ps1 -Url https://contoso.sharepoint.com/sites/pwa -ResourceId 0c7cd3fb-a0be-e111-9fte-00155d022d022681 -UpdateDisplayName "Deleted User" -RedactTimesheet $false
```

When running this command, a message will display asking you to confirm if you want to proceed.
  
After you confirm and the script successfully completes, a message will display stating: All data for resource \<user's login name\> has been removed and the name of the resource has been changed to \<updated display name\> everywhere except for timesheet records.
  
## Step 8 - Clear the cache for Project client users connecting to the PWA site
<a name="step6"> </a>

On all devices on which Project Professional or the Project Online Desktop Client connected to the Project Online instance, an IT admin needs to clear the cache. Clearing the cache will prevent projects in which user information was deleted from being updated from cached data that remains on the system. You also need to make sure that none of the user's projects are open on the client before clearing the cache.
  
To clear the cache in Project Professional 2016 and the Project Online Desktop Client:
  
1. Select the **File** menu, and then click **Options**.
    
2. On the **Project Options** page, select **Save**.
    
3. In the **Cache** section, select **Clean Up Cache**.
    
## See Also
<a name="step6"> </a>

[Export user data from Project Online](export-user-data-from-project-online.md)
  
[Project Online export json object definitions](project-online-and-project-server-export-data-definitions.md)
  

