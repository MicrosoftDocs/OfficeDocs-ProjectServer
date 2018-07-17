---
title: "Upgrading to Project Server 2019 Public Preview"
ms.author: efrene
author: efrene
manager: pamgreen
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 03e9ea52-f4a6-4709-b8c3-41acf4484251
description: "Summary: Learn how to upgrade to Project Server 2019 Public Preview."
---

# Upgrading to Project Server 2019 Public Preview
 
 **Summary:** Learn how to upgrade to Project Server 2019 Public Preview.<br/>
**Applies to:** Project Server 2019 Public Preview
  
This article describes the steps required to upgrade to Project Server 2019 Public Preview. 
  
> [!NOTE]
> Prior to reading this article, please see [Plan for upgrade to Project Server 2019 Public Preview](plan-for-upgrade-to-project-server-2019.md) for more information about upgrade and the upgrade process.
  
## Upgrade requirements

Note the following requirements for upgrading to Project Server 2019 Public Preview:
  
-  You can only upgrade from Project Server 2016. If you are upgrading from earlier versions of Project Server, you must upgrade your databases to Project Server 2016 first in order to upgrade to Project Server 2019 Public Preview.
    
    > [!NOTE]
    > For information about upgrading to Project Server 2019 Public Preview from Project Server 2013, see [Upgrade from SharePoint 2013 to SharePoint Server 2019 Public Preview](https://docs.microsoft.com/en-us/SharePoint/upgrade-and-update/upgrade-from-sharepoint2013-to-sharepointserver-2019). 
  
-  The upgrade process requires you to run Microsoft PowerShell cmdlets in the SharePoint Server 2019 Public Preview Management Shell. Verify that you have the following minimum permissions to run them:

    - securityadmin fixed server role on the SQL Server instance. 


    - db_owner fixed database role on all databases that are to be updated. 


    - Administrators group on the server on which you are running the PowerShell cmdlets.

An administrator can use the **Add-SPShellAdmin** cmdlet to grant permissions to use SharePoint Server cmdlets. 

[!NOTE]If you do not have permissions, contact your Setup administrator or SQL Server administrator to request permissions. For additional information about PowerShell permissions, see [Add-SPShellAdmin](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/add-spshelladmin?view=sharepoint-ps)

    
- If you are migrating your Project Server 2016 Resource Plans to use as Resource Engagements in Project Server 2019 Public Preview:
    
  - They must be published.
    
  - They must have associated time phased data (it must contain work, not just resources).
    
    > [!NOTE]
    > For more information about Resource Engagements, see this blog post: [Resource Engagements](http://go.microsoft.com/fwlink/p/?LinkID=620823&amp;clcid=0x409). 
  
## Project Server 2019 Public Preview upgrade steps

Upgrading to Project Server 2019 public Preview can be broken up into 4 steps. These include:
  
1. Create a Project Server 2019 Public Preview farm 
    
2. Copy and move your databases
    
3. Attach and upgrade your SharePoint Server 2016 content database
    
4. Test your SharePoint Content database
    
  
The following provides more detail about the upgrade steps mentioned in the upgrade overview.
  
### Create your Project Server 2019 Public Preview farm
<a name="farm"> </a>

The first step in the upgrade process is to create the Project Server 2019 Public Preview farm. Since database attach is the supported method for upgrade, you will be attaching and upgrading your Project Server 2016 databases to this farm in the steps that follow.
  
Note that a key difference in installing Project Server 2019 Public Preview versus the way it was installed in previous versions is that the Project Server 2019 Public Preview installation is now a part of the SharePoint Server 2019 Public Preview installation. Project Server 2019 Public Preview now runs as a service application in SharePoint Server 2019 Public Preview, and does not require a separate installation. 
  
> [!IMPORTANT]
> Project Server 2019 Public Preview can only be enabled on the Enterprise version of SharePoint Server 2019 Public Preview. Project Server 2019 Public Preview cannot be enabled on SharePoint Server 2019 Public Preview with a Standard license. 
  
> [!NOTE]
> For more information about how to install a new Project Server 2019 Public Preview farm, see [Deploy Project Servers 2016 or 2019 Public Preview](deploy-project-server-2016.md). 
  
### Copy and move your databases
<a name="copy"> </a>

The second step in the upgrade process copies your databases required for your Project Server 2016 environment to your new Project Server 2019 Public Preview environment. This is a two-step process:
  
1. With the SharePoint Server 2016 farm in read-only mode, the server farm administrator backs up the following two databases from the SQL Server instance:
    
  - SharePoint Server 2016 content database that contains your project data
    
  - Project Server 2016 database
    
2. The server farm administrator restores a backup copy of the databases to the SQL Server 2016 or 2017 instance being used to host the Project Server 2019 Public Preview farm databases.
    
You can use SQL Server Management Studio to copy and the restore of the databases.
  
### Attach and upgrade your SharePoint Server 2016 content database
<a name="attachSP"> </a>

The third step in the upgrade process attaches and upgrades your SharePoint Server 2016 content database that contains your Project site data to your new Project Server 2019 Public Preview farm. 
  
You will need to run the [Mount -SPContentDatabase](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/mount-spcontentdatabase?view=sharepoint-ps) PowerShell cmdlet in the SharePoint 2019 Management Shell in order to do this.
  
1. Open the SharePoint 2019 Management Shell as an Administrator.
    
2. At the Powershell command prompt, type:
    
     `Mount-SPContentDatabase -Name <database name> -WebApplication <Web application name>`
    
    For example:
    
     `Mount-SPContentDatabase -Name WSSContentContosoPWA -WebApplication "SharePoint 80"`
    
### Test your content database
<a name="test"> </a>

The fourth step in the upgrade is to test your newly attached and upgraded content database. You will use the [Test-SPContentDatabase](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/test-spcontentdatabase?view=sharepoint-ps) PowerShell cmdlet to test against the Web application you specified to verify all customizations referenced within the content database are also installed in the web application in the new SharePoint Server 2019 Public Preview environment. This cmdlet will not update your data in anyway.
  
1. Open the SharePoint 2019 Management Shell as an Administrator.
    
2. At the PowerShell command prompt, type:
    
     `Test-SPContentDatabase -Name <database name> -WebApplication <Web application name>`
    
    For example:
    
     `Test-SPContentDatabase -Name WSSContentContosoPWA -WebApplication "SharePoint 80"`
    
    This will check the SharePoint - 80 Web application against the customizations referenced in the WSSContentContosoPWA database, and will post the results.
    
The results of the Test-SPContentDatabase cmdlet will note inconsistencies it will find in your upgraded SharePoint Web application in its new SharePoint Server 2019 Public Preview environment. The results do not imply that the upgrade of the SharePoint 2016 content database has failed, but will only note things you need to look into in your new environment. 
  
 
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
  
To get the SiteID value for your PWA site, run the following PowerShell command in the SharePoint Server 2019 Management Shell:
  
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
    

