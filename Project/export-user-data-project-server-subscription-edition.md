---
title: "Export user data from Project Server Subscription Edition"
ms.author: v-benzyd
author: benzicald
manager: serdars
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
description: "Learn how your organization can export a specific user's content from your Project Server Subscription Edition environment."
---

# Export user data from Project Server Subscription Edition

> [!Important] 
> The process to export user data from Project Server Subscription Edition is different from previous Project Server releases. To learn how to export user data from previous versions, see <br/>1. [Export user data from Project Server 2019](Export-user-data-in-Project-Server-2019.md) <br/>2. [Export user data from Project Server 2016/2013/2010](export-user-data-from-project-server.md)

## Process Overview

<span id="Overview" class="anchor"></span>The following is an overview of the process to export a specific user's information from a Project Web App site in Project Server Subscription Edition:

| Steps | Process | Description|
|-------|---------|------------|
|1.|Download the export scripts|Download the `.sql` and Microsoft PowerShell scripts for exporting user data.|
|2.|Find the PWA sites in your environment|Find a listing of Project Web App instances in your Project Server farm.|
|3.|Export workspace items for the user|Look for user data in project sites.|
|4.|Find the user's resource ID|On each Project Web App instance, find the unique Resource ID for the user. You can also choose to specify the user claim.|
|5.|Perform an export of the user's data|Export the information that you want to review by using the scripts.|
|6.|Review your exported content|Look through the exported data for information about your user.|
|7.|Timephased Data|Export timephased reporting data for a user's tasks &amp; assignments.|
|8.|Archived items|Look for data about your user in the Archived database.|
|9.|Find and save custom views, custom filters, attachments, and macros|Locate custom items.|
|10.|Data you need to manually export|Look for user data not included in the export.|

## Step 1 - Download the export script files

<span id="DownloadScripts" class="anchor"></span>Download the export scripts from the [Microsoft Download Center](https://go.microsoft.com/fwlink/?linkid=871966).

The download contains a zip file with separate folder for each version. Use scripts from ***Subscription Edition*** folder to export data from Project Server Subscription Edition.

Important notes about running the export scripts:

-   Run the `.sql` script in the context of the database where the information resides. You must have `db\_datareader` permissions on the database.

-   You may need to "unblock" the zip file because by default, executing scripts downloaded from the Internet is not allowed. Do the following to unblock your files:

    1.  In File Explorer, go to the location where you saved the zip file.

    2.  Right click on the zip file, and click **Properties**.

    3.  On the **General** tab, select **Unblock**.

    4.  Click **OK**.

All files contained in the zip file should now be Unblocked. You can verify this in the individual files by checking to see if the **Unblocked** checkbox option no longer appears in the **General** tab of the file's **Properties** page.

> [!Note] 
>If you only have access to unzipped files, you can also unblock each file individually.

<span id="bkmk_lookuptheusersresourceid" class="anchor"></span>

## Step 2 - Find the Project Web App instances in your SharePoint Server farm

<span id="FindPWA" class="anchor"></span>Use the **Get-SPProjectWebInstance** cmdlet with the following filters to get the URL, site ID, and database name for the PWA sites that exist in the SharePoint Server farm:

```powershell
Get-SPProjectWebInstance | ft -a Url,SiteId,DatabaseName,DatabaseServer
```

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

## Step 3 - Export workspace items for the user

Run the `ExportWorkspaceItemsByDisplayName.sql` script and search for data using possible display names of the user (partial name searches).

> [!Note] 
> Run the `ExportWorkspaceItemsByDisplayName.sql` script in SQL Server Management Studio and must have farm admin permissions to have access to the appropriate database.

Run the script on the database for the related PWA site. In the example results provided in Step 1, the database for all three Project Web App instances is *WSS\_Content*.

Provide values for the following parameters in the script:

| Parameter | Description |
|-----------|-------------|
|`@siteID`|The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1.|
|`@searchName` |The display name of the Project Server user.|

## Step 4 - Find the user's Resource ID or Claims Account on each PWA site

<span id="FindResID" class="anchor"></span>After getting information all PWA sites on your Project Server farm, next you need to find the Resource ID (ResID) or Claims account of the user whose personal data you want to delete. Do this on each of the PWA sites your discovered in Step 1 (since ResIDs differ in each PWA instance).

Run the `FindUser.sql` script to find the user's Resource ID or claims account.

Provide values for the following parameters in the script:

| Parameter | Description |
|-----------|-------------|
|`@siteID`|The PWA site ID for the site in which you want to find the user's Resource ID. You found the PWA site ID values for your PWA sites in Step 1.|
|`@searchName` |The display name of the Project Server user.|

For example, if you want to find the userID for Adam Barr on the Contoso PWA1 site you found in the example in Step 1, you would edit the values for the parameters in the script like this:

```powershell

DECLARE @siteId uniqueidentifier = '63ed0197-3647-4279-ed5e80855fc7'

DECLARE @searchName nvarchar(255) = 'Adam Barr'
```

The script returns the Resource Name, Resource ID, email address, and Claims Account values for the user.

## Step 5 - Export your user's data from the PWA site

Next, you will need to run the **ExportProjectUserContent** PowerShell script to export your user's data from each PWA site in your Project Server environment. To run the script, ensure you and your environment meet the prerequisites.

### Prerequisites

-   **Project Online Desktop Client or Project Professional 2021/2019**: You will need the Project Online Desktop Client or Project Professional 2021/2019 and be connected to the Project PWA instance.

    To connect your Project client to your Project PWA instance:

    1.  Click the **File** tab to open the Backstage view. Click **Info**, and then click **Manage** Accounts.
    
    2.  In the **Project Web App Accounts** dialog box, click **Add**.
    
    3.  In the **Account Properties** dialog box, type a name for this account in the **Account Name** box.
    
    4.  Enter the URL of the PWA site you are connecting to in the **Project Server URL** box.
    
    5.  Click **OK**.
    
    6.  In the **Project Web App Accounts** dialog box, select **Set as Default,** and then click **OK**.
    
    7.  Restart Project, and log on to the PWA site.

-   **Permissions:**  To have the required permissions to run the script, add yourself as a site collection admin to the PWA Site for which you are running the script.

### Run the `ExportProjectUserContent` script

Use the `ExportProjectUserContent.ps1` PowerShell script to export your user's data.

You will need to configure four parameters when running the script.

|Parameter |Description|
|----------|-----------|
|`-URL` |URL of the PWA site|
|`-ResourceID` |Resource ID of the user.|
|`-ClaimsAccount` |Claims account of the user|
|`-OutputDirectory` |Location to store the export files.|

You will also need to choose the authentication method.

|Authentication Parameter |Description|
|-------------------------|-----------|
|[nothing passed in] |Authenticate using NTLM and the Kerberos protocol as the current user.|
|`-PromptForCredential` |Authenticate using Basic or digest protocol or using NTLM and/or Kerberos with a different user.|
|`-UseWebLogin` |Authenticate using Forms and ADFS/SAML protocol.|

You can choose to run the script either by specifying the user's Resource ID or login Name.

#### **To run the `ExportProjectUser` script using the users Resource ID**

You would use the following command in PowerShell with the parameters listed above:

```powershell

 .\\ExportProjectUserContent.ps1 -Url \<PwaSiteURL\> -ResourceUid \<UsersResourceID\> -OutputDirectory \<LocationToStoreOutput\>

```

For example, if you want to export user data from the Costoso PWA1 site (site URL of https://contoso/sites/pwa1) for a user with a Resource ID of cb5c91cf-fd6b-e711-80d0-00155da4a406, and have the export files save to `c:\\pwa1siteOutput`, you would enter:

```powershell

 .\\ExportProjectUserContent.ps1 -Url https://contoso/sites/pwa1 -ResourceUid cb5c91cf-fd6b-e711-80d0-00155da4a406 -OutputDirectory c:\\pwa1siteOutput

 ```

#### **To run the `ExportProjectUser` script using the users Claim Account**

You would use the following command in PowerShell with the parameters listed above:

```powershell

 .\\ExportProjectUserContent.ps1 -Url \<PwaSiteURL\> -ClaimAccount \<UsersClaimAccount\> -OutputDirectory \<LocationToStoreOutput\>

```

For example, if you want to export user data from the Costoso PWA1 site (site URL of https://contoso/sites/pwa1) for a user with a Login Name of AdamB@contoso.onmicrosoft.com, and have the export files save to `c:\\pwa1siteOutput`, you would enter:

```powershell
.\\ExportProjectUserContent.ps1 -Url https://contoso/sites/pwa1 -LoginName AdamB@contoso.onmicrosoft.com -OutputDirectory c:\\pwa1siteOutput
```

After the script runs successfully, all exported data will be stored in the `-OutputDirectory` you specified.

### Select specific feature-related user data files to export

Some of the exported user content you receive will include a number of json formatted files that includes feature-specific user information. For example, the `Security.json` file contains data about the user's security groups, categories, and permissions settings. These [*feature-related json files*](https://support.office.com/en-us/article/export-user-data-from-project-online-27f3838d-3dbe-4b98-80dc-df55f851154d) are described in more detail in the next section. By default, you will receive all 27 feature-related json files when you run the `ExportProjectUserContent` script. However, you can use the `-Options` parameter to select specific json files to download. These include the following:

<table>
<thead>
<tr class="header">
<th align="left">-Options values</th>
<th align="left">Json files you receive</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">All</td>
<td align="left">All feature-related json files, all project-specific json files, and all project-list files.</td>
</tr>
<tr class="even">
<td align="left">Engagements</td>
<td align="left">Engagements_page#.json</td>
</tr>
<tr class="odd">
<td align="left">Resources</td>
<td align="left">Resource.json, ReportingResource.json</td>
</tr>
<tr class="even">
<td align="left">Portfolio</td>
<td align="left">BusinessDrivers.json, DriverPrioritizations.json, PortfolioAnalyses.json</td>
</tr>
<tr class="odd">
<td align="left">Projects</td>
<td align="left"><p>DraftProjectList.xml, PublishedProjectList.xml. ReportingProjectList</p>
<p>You will also receive one of each of the following for each project that the user was a part of:</p>
<p>Project_projName_draft.json, Project_projName_draft.mpp, Project_projName_draft.xml,</p>
<p>Project_projName_published.json, Project_projName_ published.mpp, Project_projName_ published.xml,</p>
<p>Project_projName_reporting.json, Project_projName_reporting_Tasks, Project_projName_reporting_Assignments, Project_projName_reporting_Resources, Project_projName_reporting_Baselines</p></td>
</tr>
<tr class="even">
<td align="left">ResourcePlans</td>
<td align="left">ResourcePlans_page#.json, ReportingResourcePlans.json</td>
</tr>
<tr class="odd">
<td align="left">Security</td>
<td align="left">Security.json</td>
</tr>
<tr class="even">
<td align="left">ServerSettings</td>
<td align="left">CustomFields.json, LookupTables.json, Calendars.json, Delegations.json, QueueJobs.json, SubscribedReminders.json, UnsubscribedAlerts.json, ReminderEmails.json, AdminAudit.json</td>
</tr>
<tr class="odd">
<td align="left">Timesheets</td>
<td align="left"><p>Timesheets_Reporting.json, Timesheets_page#.json</p>
<p>For the Timesheets_page#.json, you will get file per page.</p></td>
</tr>
<tr class="even">
<td align="left">TaskStatus</td>
<td align="left">Rules.json, TaskStatus_AssignmentsHistory_page#.json, TaskStatus_AssignmentsSaved.json, TaskStatus_AssignmentsSubmitted.json</td>
</tr>
<tr class="odd">
<td align="left">StatusReports</td>
<td align="left">StatusReports.json</td>
</tr>
<tr class="even">
<td align="left">Workflow</td>
<td align="left">Workflow.json</td>
</tr>
<tr class="odd">
<td align="left">WorkspaceItems</td>
<td align="left">WorkspaceItems.json</td>
</tr>
<tr class="even">
<td align="left">UserViewSettings</td>
<td align="left">UserViewSettings.json</td>
</tr>
</tbody>
</table>

Using the `-Options` parameter can be helpful if you want to export user data from the PWA site for specific features. For example, if you are only concerned with your user's data in the Portfolio Analysis feature, you can run the `-Options` parameter with the value of *Portfolio*:

```powershell

.\\ExportProjectUserContent.ps1 -Url https://contoso/sites/pwa1 -ResourceUid cb5c91cf-fd6b-e711-80d0-00155da4a406 -OutputDirectory c:\\pwa1siteOutput -Options Portfolio

```

This will allow you to export the three json files that contain your user's data that pertains to the Portfolio Analysis feature (`BusinessDrivers.json`, `DriverPrioritizations.json`, `PortfolioAnalyses.json`).

## Step 6 - Review your exported content

After you run the `ExportProjectUserContent` PowerShell script successfully, you will have the following output in the output directory you specified when running the command:

-   **Project list files** - You will receive the following three `.xml` files that provide a list of projects contained in the Project Draft and Published schemas of which the user was a part of.
    
    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">DraftProjectList.xml</td>
    <td align="left">List of projects from the Draft schema that corresponds to the conditions above.</td>
    </tr>
    <tr class="even">
    <td align="left">PublishedProjectList.xml</td>
    <td align="left">List of projects from the Published schema that corresponds to the conditions above.</td>
    </tr>
    <tr class="odd">
    <td align="left">ReportingProjectList.xml</td>
    <td align="left">List of projects from the Reporting schema that corresponds to the conditions above.</td>
    </tr>
    </tbody>
    </table>

    This means the user was involved in the project as at least one of the following:
    
    - Was the project owner.

    - Has a task assigned to him or her in the project.

    - Is an assignment owner of a task in the project.

    - Is the status manager of a task in the project.

    The list of projects may differ slightly for each of the three `.xml` files. For example, a user can save the project but not publish, meaning that it will appear in the` DraftProjectList.xml` file, but not the `PublishedProjectList.xml` or `ReportingProjectList.xml` files.

    A project admin can use the Project list .xml files to give them information about which project-specific export files they be interested in analyzing to decide how much of the exported content should be shared with the user.

    All three of the `ProjectList.xml` files will have the following properties for each project listed:

    <table>
    <thead>
    <tr class="header">
    <th align="left">Property</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">SiteId</td>
    <td align="left">The unique identifier for the PWA site in which the project exists.</td>
    </tr>
    <tr class="even">
    <td align="left">Proj_UID</td>
    <td align="left">The unique identifier for the project.</td>
    </tr>
    <tr class="odd">
    <td align="left">Proj_Name</td>
    <td align="left">Name of the project.</td>
    </tr>
    </tbody>
    </table>

-  **Feature-related files** - For each PWA site that the user is part of, the following feature-specific `.json` files will be exported to the specified output directory. The feature-specific files will contain user data as it pertains to the feature use throughout the PWA site. For example, the `Drivers.json` file will include data about Portfolio Analysis business drivers the user created or owned. If the user has no data relating to the feature on the specific PWA site, the file will contain no data.

    The feature-specific `.json` files include:
    
    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/adminaudit-ce5faeae-9af4-4696-b847-a1f4f20327c7#adminaudit"><em>AdminAudit</em></a></td>
    <td align="left">Project Web App server settings change data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/businessdrivers-ce5faeae-9af4-4696-b847-a1f4f20327c7#drivers"><em>BusinessDrivers</em></a></td>
    <td align="left">Portfolio analysis business drivers data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/calendars-ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars"><em>Calendars</em></a></td>
    <td align="left">Enterprise calendar data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/customfields-ce5faeae-9af4-4696-b847-a1f4f20327c7#customfields"><em>CustomFields</em></a></td>
    <td align="left">Custom field data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/delegations-ce5faeae-9af4-4696-b847-a1f4f20327c7#delegations"><em>Delegations</em></a></td>
    <td align="left">Delegation data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/driverprioritizations-ce5faeae-9af4-4696-b847-a1f4f20327c7#prioritizations"><em>DriverPrioritizations</em></a></td>
    <td align="left">Business driver prioritizations data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/engagements-ce5faeae-9af4-4696-b847-a1f4f20327c7#engagements"><em>Engagements</em></a></td>
    <td align="left">Resource engagement data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/lookuptables-ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables"><em>LookupTables</em></a></td>
    <td align="left">Lookup table data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/portfolioanalysis-ce5faeae-9af4-4696-b847-a1f4f20327c7#analyses"><em>PortfolioAnalysis</em></a></td>
    <td align="left">Portfolio analyses data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/queuejobs-ce5faeae-9af4-4696-b847-a1f4f20327c7#queuejobs"><em>QueueJobs</em></a></td>
    <td align="left">Data about user jobs process through the Queue Service.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/reminderemails-ce5faeae-9af4-4696-b847-a1f4f20327c7#reminderemails"><em>ReminderEmails</em></a></td>
    <td align="left">Reminder email data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/reportingresourceplans-ce5faeae-9af4-4696-b847-a1f4f20327c7#reportingresource"><em>ReportingResourcePlans</em></a></td>
    <td align="left">Resource reporting data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/resource-ce5faeae-9af4-4696-b847-a1f4f20327c7#resource"><em>Resource</em></a></td>
    <td align="left">Resource data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/resourceplans-ce5faeae-9af4-4696-b847-a1f4f20327c7#resourceplan"><em>ResourcePlans</em></a></td>
    <td align="left">Resource plan data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/rules-ce5faeae-9af4-4696-b847-a1f4f20327c7#rules"><em>Rules</em></a></td>
    <td align="left">Rules data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/security-ce5faeae-9af4-4696-b847-a1f4f20327c7#security"><em>Security</em></a></td>
    <td align="left">Data about security groups, categories, and permissions.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/statusreports-ce5faeae-9af4-4696-b847-a1f4f20327c7#statusreports"><em>StatusReports</em></a></td>
    <td align="left">Status report data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/subscribedreminders-ce5faeae-9af4-4696-b847-a1f4f20327c7#subscribedreminders"><em>SubscribedReminders</em></a></td>
    <td align="left">Subscribed reminders data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/taskstatusassignmentshistory-ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignhis"><em>TaskStatus_AssignmentsHistory</em></a></td>
    <td align="left">Statusing assignments history data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/taskstatusassignmentssaved-ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignsaved"><em>TaskStatus_AssignmentsSaved</em></a></td>
    <td align="left">Statusing assignments save data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/taskstatusassignmentssubmitted-ce5faeae-9af4-4696-b847-a1f4f20327c7#statusassignsub"><em>TaskStatus_AssignmentsSubmitted</em></a></td>
    <td align="left">Statusing assignments submit data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/timesheets-ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets"><em>Timesheets</em></a></td>
    <td align="left">Data about timesheets.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/timesheetsreporting-ce5faeae-9af4-4696-b847-a1f4f20327c7#timesheets_reporting"><em>Timesheets_Reporting</em></a></td>
    <td align="left">Reporting data about timesheets.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/unsubscribedalerts-ce5faeae-9af4-4696-b847-a1f4f20327c7#unsubscribedalerts"><em>UnsubscribedAlerts</em></a></td>
    <td align="left">Unsubscribed alerts data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/userviewsettings-ce5faeae-9af4-4696-b847-a1f4f20327c7#userprop"><em>UserViewSettings</em></a></td>
    <td align="left">User view settings data.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/workflow-ce5faeae-9af4-4696-b847-a1f4f20327c7#workflow"><em>Workflow</em></a></td>
    <td align="left">Project workflow data.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/workspaceitems-ce5faeae-9af4-4696-b847-a1f4f20327c7#wss"><em>WorkspaceItems</em></a></td>
    <td align="left">Data about SharePoint items from project sites.</td>
    </tr>
    </tbody>
    </table>

    Certain feature-specific json files have the possibility of being large, so to improve performance, the following json files will spawn across multiple files:
   
    - `Engagements.json`

    - `ResourcePlans.json`

    - `Timesheets.json`

    - `TaskStatus\_AssignmentHistory.json`

    > [!Note] 
    > To learn more about the objects contained in each of the feature-specific `.json` files, see the [Feature-specific data](https://support.office.com/en-us/article/featurespecific-data-ce5faeae-9af4-4696-b847-a1f4f20327c7) section of [Project Online and Project Server export data definitions](https://support.office.com/en-us/article/project-online-export-json-object-definitions-ce5faeae-9af4-4696-b847-a1f4f20327c7).

-   **Project-specific files** - If the user is part of any project, then for each of those projects, several individual files will be exported to the output directory. This will happen if the user is part of the specific project as one of the following:

    -   The project owner

    -   Has a task assigned to him or her in the project

    -   Is an assignment owner of a task in the project

    -   Is the status manager of a task in the project

    Project-specific data differs from the Feature-related data in that the data is specific to a single project. Feature-related data can include user data across many projects in the PWA site that the user was a part of, but pertaining to a single feature.  

    > [!Note] 
    > For all project-specific files you receive, they will be prefixed with the specific project's **Project Name**. For example, if a project has a Project Name of **Project1**, all project-specific files we describe in this section will be prefixed with **Project1**.

    For each project the user is a part of, you will received the following three sets of files:

    - An `.xml` file for the project from the draft and published databases:

    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">&lt;projectName&gt;_draft.xml</td>
    <td align="left">The project file from the draft schema saved as .xml format.</td>
    </tr>
    <tr class="even">
    <td align="left">&lt;projectName&gt;_published.xml</td>
    <td align="left">The project file from the published schema saved as .xml format.</td>
    </tr>
    </tbody>
    </table>

    > [!Note] 
    > See the [Project XML Data Interchange Scheme Reference](/office-project/xml-data-interchange/project-xml-data-interchange-schema-reference) to understand the Project XML data contained in these files.

    <br>

    - An .mpp file for the project from the draft and published databases:

    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">&lt;projectName&gt;_draft.mpp</td>
    <td align="left">The project file from the draft schema saved as a Project .mpp file.</td>
    </tr>
    <tr class="even">
    <td align="left">&lt;projectName&gt;_published.mpp</td>
    <td align="left">The project file from the published schema saved as a Project .mpp file.</td>
    </tr>
    </tbody>
    </table>

    > [!Note]
    > You can open the .mpp file with Project Professional 2021, Project Professional 2019, or the Project Online Desktop client.

    <br>

    - Four `.json` files for the project from the reporting schema:

    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/projectprojectnamereportingprojectbaselinejson-ce5faeae-9af4-4696-b847-a1f4f20327c7#projectbaseline">Project_&lt;projectName&gt;_reporting_ProjectBaseline.json</a></td>
    <td align="left">Project Baseline data for the project from the reporting schema.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/projectprojectnamereportingtasksjson-ce5faeae-9af4-4696-b847-a1f4f20327c7#projecttasks">Project_&lt;projectName&gt;_reporting_Tasks.json</a></td>
    <td align="left">Project tasks data for the project from the reporting schema.</td>
    </tr>
    <tr class="odd">
    <td align="left"><a href="https://support.office.com/en-us/article/projectprojectnamereportingassignmentsjson-ce5faeae-9af4-4696-b847-a1f4f20327c7#assignments">Project_&lt;projectName&gt;_reporting_Assignments.json</a></td>
    <td align="left">Assignment resources data for the project from the reporting schema.</td>
    </tr>
    <tr class="even">
    <td align="left"><a href="https://support.office.com/en-us/article/projectprojectnamereportingresourcesjson-ce5faeae-9af4-4696-b847-a1f4f20327c7#reporting_resources">Project_&lt;projectName&gt;_reporting_Resources.json</a></td>
    <td align="left">Resources data for the project from the reporting schema.</td>
    </tr>
    </tbody>
    </table>

    > [!Note] 
    > To learn more about the objects contained in each of the `.json` files, see the [Project-specific data files](https://support.office.com/en-us/article/projectspecific-data-files-ce5faeae-9af4-4696-b847-a1f4f20327c7)section of [Project Online export json object definitions](https://support.office.com/en-us/article/project-online-export-json-object-definitions-ce5faeae-9af4-4696-b847-a1f4f20327c7).

    Three `.json` files with the project's metadata from the draft, published, and reporting schemas:

    <table>
    <thead>
    <tr class="header">
    <th align="left">Name</th>
    <th align="left">Description</th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td align="left">&lt;projectName&gt;_draft.json</td>
    <td align="left">Project metadata file from the Draft schema</td>
    </tr>
    <tr class="even">
    <td align="left">&lt;projectName&gt;_published.json</td>
    <td align="left">Project metadata file from the Published schema</td>
    </tr>
    <tr class="odd">
    <td align="left">&lt;projectName&gt;_reporting.json</td>
    <td align="left">Project metadata file from the Reporting schema</td>
    </tr>
    </tbody>
    </table>

    <span id="findviews" class="anchor"></span>

    > [!Note] To learn more about the objects contained in each of the `.json` files, see the [Project-specific Metadata files](https://support.office.com/en-us/article/project-online-and-project-server-export-data-definitions-ce5faeae-9af4-4696-b847-a1f4f20327c7?ui=en-US&rs=en-US&ad=US#projspecmeta) section of [Project Online and Project Server export data definitions](https://support.office.com/en-us/article/project-online-export-json-object-definitions-ce5faeae-9af4-4696-b847-a1f4f20327c7).

## Step 7 - Timephased Data

Run the `ExportReportingTimephasedData.sql` script to export timephased data stored in reporting schema that is related to the resource. The script exports the following timephased information:

1. [TaskTimephased](/ProjectOnline/project-online-and-project-server-export-data-definitions#tasktimephaseddataset)
2. [TaskBaselineTimephased](/ProjectOnline/project-online-and-project-server-export-data-definitions#taskbaselinetimephaseddataset)
3. [AssignmentTimephased](/ProjectOnline/project-online-and-project-server-export-data-definitions#assignmenttimephaseddataset)
4. [AssignmentBaselineTimephased](/ProjectOnline/project-online-and-project-server-export-data-definitions#assignmentbaselinetimephaseddataset)

## Step 8 - Archived items

<span id="ArchivedItems" class="anchor"></span>

`ExportArchievdData.sql` will return the following data that is stored in the archived database that is related to the resource.

<table>
<thead>
<tr class="header">
<th align="left">Export option</th>
<th align="left">Output definitions</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td align="left">Archived items - Calendar</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#calendars">Calendars</a></td>
</tr>
<tr class="even">
<td align="left">Archived items - Custom fields</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#customFields">CustomFields</a></td>
</tr>
<tr class="odd">
<td align="left">Archived items - Lookup tables</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#lookuptables">Lookup Table</a></td>
</tr>
<tr class="even">
<td align="left">Archived items - Projects</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#projlist">Project List</a><br />ProjectVersionId (Archive version ID)<br />ProjectVersionDescription (Date and time of the backup)<br />ProjectVersionDate (The date of the backup)</td>
</tr>
<tr class="odd">
<td align="left">Archived items - Resource</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#resource">Resource</a></td>
</tr>
<tr class="even">
<td align="left">Archived items - Resource custom fields</td>
<td align="left"><a href="https://support.office.com/article/ce5faeae-9af4-4696-b847-a1f4f20327c7#rescustfields">Resource - custom fields</a></td>
</tr>
</tbody>
</table>

Archived Project Data: To export archived projects:

1.  [Archive the current project](./back-up-item-level-objects-through-administrative-backup-project-server-2013.md).

2.  [Restore the archived version](./restore-item-level-objects-through-administrative-restore-project-server-2013.md).

3.  Export the user related data.

4.  Restore the project from archive.

Archived Non-Project Data:

1.  Use [SharePoint backup and recovery](/sharepoint/administration/backup-and-recovery-overview) to create a clone of the current farm.

2.  Restore the archived items from Administrative backup and restore (see previous procedure).

3.  Export the user related data.

## Step 9 - Find and save custom views, custom filters, attachments, and macros

After receiving the exported user content, you can use your data to find the user's custom views, custom filters, custom tables, attachments, and macros. To find these, you will need to have the MPP and XML file for each project in which you want to search. For more information on how to do this, see [*Find customized user items in Project Online and Project Server user export data*](https://support.office.com/en-us/article/find-customized-user-items-in-project-online-and-project-server-user-export-data-d40ede2b-22e5-4fa4-b789-007c9a36d5f1).

### Considerations for master and inserted projects

As noted earlier, the export script will only export projects that the user was a part of as an owner, has an assigned task, is an assignment owner of a task, or is the status manager of a task. When the user is part of an inserted project, but not the master project, only the inserted project will be exported. Similarly, if the user is only part of a master project and not any of the inserted projects, only the master project will be exported.

When saving a master project that a user was a part of, you will not need to save any associated inserted projects if you are prompted.

## Step 10 – Data you need to manually export

### Project Author

The author of the project is not exported using the above steps. You can run `ExportProjectAuthor.sql` to get the list of projects whose author matches the user display name or the users claims.

|Parameter |Description|
|----------|-----------|
|`@siteID` |The PWA site ID for the site in which you want to find if the user is author of a project.|
|`@searchName` |The display name or claims of the Project Server user. |
