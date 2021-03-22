---
title: "Upgrading to Project Server 2016"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 4/21/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 03e9ea52-f4a6-4709-b8c3-41acf4484251
description: "Summary: Learn how to upgrade to Project Server 2016."
---

# Upgrading to Project Server 2016

 **Summary:** Learn how to upgrade to Project Server 2016.<br/>
**Applies to:** Project Server 2016

This article describes the steps required to upgrade to Project Server 2016. 

> [!NOTE]
> Prior to reading this article, please see [Plan for upgrade to Project Server 2016](plan-for-upgrade-to-project-server-2016.md) for more information about upgrade and the upgrade process.

## Upgrade requirements

Note the following requirements for upgrading to Project Server 2016:

-  You can only upgrade from Project Server 2013. If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2013 first in order to upgrade to Project Server 2016.

    > [!NOTE]
    > For information about upgrading to Project Server 2013 from Project Server 2010, see [Upgrade to Project Server 2013](./upgrade-to-project-server-2016.md). 

-  The upgrade process requires you to run Windows PowerShell cmdlets in the SharePoint Server 2016 Management Console. Verify that you have the required permissions to run them

- If you are migrating your Project Server 2013 Resource Plans to use as Resource Engagements in Project Server 2016:

  - They must be published.

  - They must have associated time phased data (it must contain work, not just resources).

    > [!NOTE]
    > For more information about Resource Engagements, see this blog post: [Resource Engagements](https://go.microsoft.com/fwlink/p/?LinkID=620823&amp;clcid=0x409). 

## Project Server 2016 upgrade steps

Upgrading to Project Server 2016 can be broken up into six steps. These include:

1. Create a Project Server 2016 farm 

2. Copy and move your databases

3. Attach and upgrade your SharePoint 2013 content database

4. Test your SharePoint Content database

5. Attach and upgrade your Project Server 2013 databases

6. Disable database quota limits for your PWA site

7. Migrate your Project Server 2013 resource plans (optional) 

The following provides more detail about the upgrade steps mentioned in the upgrade overview.

### Create your Project Server 2016 farm
<a name="farm"> </a>

The first step in the upgrade process is to create the Project Server 2016 farm. Since database attach is the supported method for upgrade, you will be attaching and upgrading your Project Server 2013 databases to this farm in the steps that follow.

Note that a key difference in installing Project Server 2016 versus the way it was installed in previous versions is that the Project Server 2016 installation is now a part of the SharePoint Server 2016 installation. Project Server 2016 now runs as a service application in SharePoint Server 2016, and does not require a separate installation. 

> [!IMPORTANT]
> Project Server 2016 can only be enabled on the Enterprise version of SharePoint Server 2016. Project Server 2016 cannot be enabled on SharePoint Server 2016 with a Standard license. 

> [!NOTE]
> For more information about how to install a new Project Server 2016 farm, see [Deploy Project Server 2016](deploy-project-server-2016.md). 

### Copy and move your databases
<a name="copy"> </a>

The second step in the upgrade process copies your databases required for your Project Server 2013 environment to your new Project Server 2016 environment. This is a two-step process:

1. With the SharePoint Server 2013 farm in read-only mode, the server farm administrator backs up the following two databases from the SQL Server instance:

   - SharePoint 2013 content database that contains your project data

   - Project Server 2013 database

2. The server farm administrator restores a backup copy of the databases to the SQL Server 2014 instance being used to host the Project Server 2016 farm databases.

You can use SQL Server Management Studio to copy and the restore of the databases.

### Attach and upgrade your SharePoint 2013 content database
<a name="attachSP"> </a>

The second step in the upgrade process attaches and upgrades your SharePoint 2013 content database that contains your Project site data to your new Project Server 2016 farm. 

You will need to run the **Mount -SPContentDatabase** PowerShell cmdlet in the SharePoint 2016 Management Shell in order to do this.

1. Open the SharePoint 2016 Management Shell as an Administrator.

2. At the prompt, enter:

     `Mount-SPContentDatabase -Name <database name> -WebApplication <Web application name>`

    For example:

     `Mount-SPContentDatabase -Name WSSContentContosoPWA -WebApplication "SharePoint 80"`

### Test your content database
<a name="test"> </a>

The next step in the upgrade is to test your newly attached and upgraded content database. You will use the **Test-SPContentDatabase** PowerShell cmdlet to test against the Web application you specified to verify all customizations referenced within the content database are also installed in the web application in the new SharePoint Server 2016 environment. This cmdlet will not update your data in anyway.

1. Open the SharePoint 2016 Management Shell as an Administrator.

2. At the prompt, enter:

     `Test-SPContentDatabase -Name <database name> -WebApplication <Web application name>`

    For example:

     `Test-SPContentDatabase -Name WSSContentContosoPWA -WebApplication "SharePoint 80"`

    This will check the SharePoint - 80 Web application against the customizations referenced in the WSSContentContosoPWA database, and will post the results.

The results of the Test-SPContentDatabase cmdlet will note inconsistencies it will find in your upgraded SharePoint Web application in its new SharePoint Server 2016 environment. The results do not imply that the upgrade of the SharePoint 2013 content database has failed, but will only note things you need to look into in your new environment. For example, you might see the following result:

 `Category: MissingWebPart`

 `Error: True`

 `UpgradeBlocking : False`

 `Message: WebPart class [e6002ce8-69ee-168a-8f7c-a1d98d51da29] (class [Microsoft.Office.Excel.WebUI.ExcelWebRenderer] from assembly [Microsoft.Office.Excel.WebUI, Version=15.0.0.0, Culture=neutral, PublicKeyToken=71e9bce111e9429c]) is referenced [1] times in the database [WSSContentContosoPWA], but is not installed on the current farm. Please install any feature/solution which contains this web part.`

 `Remedy: One or more web parts are referenced in the database [WSSContentContosoPWA], but are not installed on the current farm. Please install any feature or solution which contains these web parts.`

This message notes that the Excel Services Web Part that is referenced in the upgraded content database is not found on the SharePoint Server 2016 farm. You might need to install Office Online Server on your SharePoint Server 2016 farm for you to use it.

> [!NOTE]
> Office Online Server is supported for use with Project Server 2016. 

### Attach and upgrade your Project Server 2013 database
<a name="attach"> </a>

After attaching, upgrading, and testing your SharePoint 2013 content database, the next step is to attach and upgrade your Project Server 2013 database to the Project Server 2016 farm. You will need to run the **Migrate -SPProjectDatabase** PowerShell cmdlet in the SharePoint 2016 Management Shell in order to do this.

1. Open the SharePoint 2016 Management Shell as an Administrator.

2. At the prompt, enter:

     `Migrate-SPProjectDatabase -DatabaseName <database name> -SiteCollection <PWA site URL>`

    For example:

     `Migrate-SPProjectDatabase -DatabaseName ProjectDB1 -SiteCollection "https://contoso1/sites/PWA"`

    When the cmdlet completes successfully, verify that you can open the Project site you specified in Project Server 2016.

> [!NOTE]
> If you have multiple PWA sites that you want to upgrade, all the sites in the content DB and all the PWA sites must be upgraded at the same time. This means that the content database containing the project site data as well as any associated Project databases for each PWA site must be upgraded. 

### Disable database quota limits for your PWA site
<a name="quota"> </a>

You will need to run the following Windows PowerShell cmdlet to disable a database quota limit restriction that is set by default in Project Server 2016:

 `Set-SPProjectDatabaseQuota -URL <https://servername/sites/pwa> -Enabled:$false -ReadOnlyLimit 10200 -ReadOnlyWarningThreshold 90 -MaxDbSize 10240`

For example: 

 `Set-SPProjectDatabaseQuota -URL https://contoso/sites/pwa -Enabled:$false -ReadOnlyLimit 10200 -ReadOnlyWarningThreshold 90 -MaxDbSize 10240`

> [!NOTE]
>  If the database quota limit restriction is not disabled, you will run into the following issues:>  If you are upgrading to Project Server 2016 and your Project database you are upgrading is larger than 10 Gigs, your PWA site will immediately be set to Read-Only.>  If you deploy Project Server 2016, configure a PWA site, and through daily product use, the data for the site eventually goes over the 10 Gig limit, your PWA site will be set to Read-Only.>  If you are using multiple PWA sites, the cmdlet must be run for each PWA site.

> [!NOTE]
> For more information about this issue, see [Project Support Blog: If your PWA site goes read-only](https://go.microsoft.com/fwlink/p/?linkid=847696)

### Upgrade your Resource Plans to Resource Engagements
<a name="rp"> </a>

If you want to use the Resource Engagements feature in Project Server 2016, you can choose to upgrade your existing Project Server 2013 Resource Plans for use as Resource Engagements. To do this, after upgrading your Project Server 2013 database to Project Server 2016, you will also need to run the **Migrate-SPProjectResourcePlans** PowerShell cmdlet in the SharePoint 2016 Management Shell.

1. Open the SharePoint 2016 Management Shell as an Administrator.

2. At the prompt, enter:

     `Migrate-SPProjectResourcePlans -URL <PWA site URL>`

    For example:

     `Migrate-SPProjectResourcePlans -URL "https://contoso1/sites/PWA"`

After running the cmdlet, you should receive one of the following confirmation messages:

|**Message**|**What this means**|
|:-----|:-----|
|All Project Resource Plans successfully migrated  <br/> |All resource plans were found and all were migrated  <br/> |
|Migrated {0} of {1} Project Resource Plans. Check the logs for more details.  <br/> |Resource plans were found but some fail to migrate.  <br/> |
|There are no more project resource plans to migrate. Either all resource plans were migrated or exceeded the maximum retry count. Please check table MSP_RESOURCE_PLANS in the published store and verify RESPLAN_IS_MIGRATED is set for all projects  <br/> |No resource plans were found to migrate or the maximum number of attempts have passed.  <br/> |

If your resource plans did not migrate successfully (you received either of the last two messages), you can use the following troubleshooting steps to find more information.

#### Check your SharePoint Server 2016 content database for resource plan migration information

Check the MSP_RESOURCE_PLANS table for the following columns:

|**Column**|**Values**|
|:-----|:-----|
|RESPLAN_IS_MIGRATED  <br/> | "0" not migrated <br/>  "1" migrated <br/> |
|MIGRATED_REV_COUNTER  <br/> |The value shown is the number of attempts it took to migrate this resource plan. If the command is run repeatedly, this value is incremented each time, with a maximum value of 50.  <br/> |
|MIGRATION_ERROR_INFO  <br/> | Provides additional information about migration: <br/>  MissingResources=1, followed by a list of missing resources <br/>  AccessDenied=2, followed by any additional information <br/>  DatabaseError=3, followed by any additional information <br/>  Unknown=4, followed by any additional information <br/> |

#### Check your SharePoint Server 2016 content database for resource plan migration information

You can check to see if a specific PWA site you are migrating has an associated resource plan. You use the following SQL query to do this:

```
SELECT *
  FROM [DBName].[pjpub].[MSP_RESOURCE_PLANS] where SiteId = <SiteId>
```

There is a row in this table for each resource plan for the site (A project can have 0 or 1 resource plan).

To get the SiteID value for your PWA site, run the following PowerShell cmdlet in the SharePoint Server 2016 Management Console:

```
$site = get-spsite <SiteUrl>
$site.ID
```

#### Check your ULS logs for more information

The following tags in **category:Engagements (PWA)** may have useful information to help troubleshoot any problems associated with your resource plan migration:

- tag_a5h65

- tag_a5h66

- tag_a1kg8

- tag_a3qj3

- tag_a1khb

- tag_a5h67

- tag_a1khf

- tag_a2ifm

- tag_a4bic

- tag_a1khh

- tag_a2ifo