---
title: "Upgrade your databases and Project Web App site collections (Project Server 2013)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 94b48cf9-dc40-4c8e-afd8-39e2fbd125a4

description: "Summary: How to upgrade your required Project Server 2010 databases and your Project Web App site collection to Project Server 2013."
---

# Upgrade your databases and Project Web App site collections (Project Server 2013)

 **Summary:** How to upgrade your required Project Server 2010 databases and your Project Web App site collection to Project Server 2013.<br/>
**Applies to:** Project Server 2013

This article is one is a series of articles for upgrade to Project Server 2013. We recommend that you read the following articles before you try any procedures in this article:

- [Plan for upgrade to Project Server 2013](plan-for-upgrade-to-project-server-2013.md)

- [Prepare your environment for upgrade (Project Server 2013)](./prepare-your-environment-for-an-upgrade-to-project-server-2013.md)

- [Create backup copies of your Project Server 2010 farm databases for upgrade (Project Server 2013)](./create-backup-copies-of-your-project-server-2010-farm-databases-for-upgrade-to-p.md)

- [Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)](./restore-your-project-server-2010-farm-databases-for-upgrade-project-server-2013.md)

- [What's new for upgrade (Project Server 2013)](./what-s-new-in-project-server-2013-upgrade.md)

After restoring your Project Server 2010 databases and the SharePoint content database that contains your Project Web App site data, you can then run the steps necessary to upgrade the data and the Project Web App site collection to Project Server 2013. The actual upgrade process can be divided into two separate phases:

- SharePoint upgrade phase:

  - Check the SharePoint content database that contains your Project Site data for errors that can cause upgrade to fail.

  - Attach and upgrade the SharePoint content database.

  - Take ownership of the site collection you want to upgrade.

  - Migrate users from Windows Classic authentication to claims-based authentication (optional).

  - Check the SharePoint site for issues that can cause upgrade to fail.

  - Upgrade the SharePoint Site.

- Project Server upgrade phase: 

  - Consolidate your Project Server 2010 databases to a Project Web App database.

  - Attach your Project Web App database to the web application.

  - Upgrade your Project Web App database.

  - Mount your Project Web App Instance.

  - Upgrade your Project Web App Instance.

  - Enable the PWA feature.

## SharePoint upgrade phase

||**Steps**|**Required Microsoft PowerShell cmdlet**|
|:-----|:-----|:-----|
|1  <br/> |Check the SharePoint content database that contains your Project Site data for errors that can cause upgrade to fail.  <br/> |[Test-SPContentDatabase](/powershell/module/sharepoint-server/Test-SPContentDatabase) <br/> |
|2  <br/> |Attach and upgrade the SharePoint content database.  <br/> |[Mount-SPContentDatabase](/powershell/module/sharepoint-server/Mount-SPContentDatabase) <br/> |
|3  <br/> |Take ownership of the site collection you want to upgrade.  <br/> |[Set-SPSite](/powershell/module/sharepoint-server/Set-SPSite) <br/> |
|4  <br/> |Migrate users from Windows Classic authentication to claims-based authentication (optional).  <br/> > [!NOTE]> This step is only required if your Project Server 2010 web application is using Classic Windows authentication, and your Project Server 2013 web application is using claims-based authentication.           |([Get-SPWebApplication](/powershell/module/sharepoint-server/Get-SPWebApplication) <SPWebAppPipeBind>).MigrateUsers($true) <br/> |
|5  <br/> |Check the SharePoint site collection for issues that can cause upgrade to fail.  <br/> |[Test-SPSite](/powershell/module/sharepoint-server/Test-SPSite) <br/> |
|6  <br/> |Upgrade the SharePoint site.  <br/> |[Upgrade-SPSite](/powershell/module/sharepoint-server/Upgrade-SPSite)Upgrade-SPSite  <br/> |

### 1. Check the SharePoint Content database for errors that can cause upgrade to fail

Run the **Test-SPContentDatabase** cmdlet to check the SharePoint Server 2010 content database prior to running the **Mount-SPContentDatabase** cmdlet to connect the SharePoint 2010 database to the farm. The **Test-SPContentDatabase** cmdlet is a non-destructive test operation that checks the database and post errors that prevent upgrade of the database.

```
Test-SPContentDatabase -Name <contentdbName> -WebApplication <URL> 
-ServerInstance <servername>
```

For example:

```
Test-SPContentDatabase -Name PWA_ContentDB -WebApplication https://Contoso:80  -ServerInstance SQLServer1
```


| **Required parameters** |
|:------------------------|
| -Name  <br/>            |
| -WebApplication  <br/>  |
| -ServerInstance  <br/>  |

Running the **Test-SPContentDatabase** cmdlet checks the SharePoint Server 2010 content database and posts any possible errors in the data. It provides a description of the error, possible remedy, and an **UpgradeBlocking** flag to note if the error will prevent an upgrade of the database. It is important to address any errors in which the **UpgradeBlocking** flag is set to a value of **True**.

### 2. Attach and Upgrade the SharePoint Content Database

Run the **Mount-SPContentDatabase** Microsoft PowerShell cmdlet to connect the SharePoint Server 2010 database to the specified Web Application and also upgrade the database. Ensure that the account that you use to attach the databases is a member of the **db_owner** fixed database role for the content databases that you want to upgrade.

> [!NOTE]
> Using the SharePoint Central Administration pages to attach a content database is not supported for upgrading. 

```
Mount-SPContentDatabase -Name <contentdbName> -WebApplication <URL> -DatabaseServer <servername> -NoB2BSiteUpgrade
```

For example:

```
Mount-SPContentDatabase -Name PWA_ContentDB -WebApplication https://Contoso:80 -DatabaseServer SQLServer1 -NoB2BSiteUpgrade
```


| **Required parameters**  |
|:-------------------------|
| -Name  <br/>             |
| -WebApplication  <br/>   |
| -DatabaseServer  <br/>   |
| -NoB2BSiteUpgrade  <br/> |

### 3. Add your account as a secondary owner of the PWA site collection that you want to upgrade

You must add yourself as an owner of the PWA site collection. This is required for the proceeding steps in which you have to verify and then upgrade the site collection. 

```
Set-SPSite  -Identity <sitecollectionName> -SecondaryOwnerAlias <account>
```

For example:

```
Set-SPSite -Identity https://contoso/pwa -SecondaryOwnerAlias "contoso\\FarmAdmin"
```


| **Required Parameters**     |
|:----------------------------|
| -Identity  <br/>            |
| -SecondaryOwnerAlias  <br/> |

### 4. Migrate users who are using Windows Classic authentication mode to claims based authentication (optional)

If you are migrating Project Server 2010 users who were using Windows Classic authentication over to claims-based authentication when upgrading to Project Server 2013, you will need to run the following Windows PowerShell cmdlet. If this is not done, your users will not be able to log on to Project Web App after upgrade.

```
(Get-SPWebApplication <webappURL>).migrateUsers($true)
```

For example:

```
(Get-SPWebApplication https://contoso:80).migrateUsers($true)
```

For more information about this method, see [SPWebApplication.MigrateUsers Method](/previous-versions/office/sharepoint-server/ee554321(v=office.15)).

### 5. Check your PWA Site collection for issues that can cause upgrade of the site to fail

The Project Web App site does not support SharePoint Server 2010 version mode. The site collection for PWA must be upgraded in order to work in Project Server 2013. It is important to note that this requirements in only for PWA, and that core SharePoint site collections do not require this.

Prior to upgrading the site collection, we recommend that you run the **Test-SPSite** cmdlet to verify if the site collection has any issues that can cause upgrade of the site collection to fail. You can review the results and fix any upgrade blocking issues.

```
Test-SPSite -Identity <URL>
```

For example:

```
Test-SPSite -Identity https://contoso/pwa
```


| **Required Parameters** |
|:------------------------|
| -Identity  <br/>        |

The results display the number of "FailedWarningCounts" that it discovered through the test, but will not display information about the failure. To find more information about the failure, you can navigate to the PWA Site Settings page and run a health check on the site collection by doing the following:

### To run a health check on the PWA site collection to view upgrade warning information

1. In a browser window, enter the URL for the site (for example, https://contoso/pwa). At the end of the URL, type the following: /_layouts/15/settings.aspx. In this example, the complete URL would be https://contoso/pwa/_layouts/15/settings.aspx. This gives you a direct link to the Site Setting page. You cannot display the PWA site page because it has not been upgraded and is still in SharePoint Server 2010 mode.

2. On the PWA Site Settings page, in the **Site Collection Administration** section, click **Site Collection Health Checks**.

    > [!NOTE]
    > Notice that a message displays at the top of the page stating that the page is in SharePoint 2010 mode, because the site collection has not been upgraded yet. 

3. On the Run Site Collection Health Checks page, click **Run checks** to start a health check on the site collection.

4. The results of the health check will display verbose information about any warnings that were found by the **Test-SPSite** cmdlet. For example, it will tell you if any pages may have been customized and may cause unexpected behavior after upgrade. It will provide the page URL and an option to reset the page to default.
   > [!CAUTION]
   > Before using the option to reset the page to default, make sure that you track the customization that were implemented on the page so that you can manually re-create them after upgrade. Resetting the page to default will return the page to the default template, and will remove your customizations that were implemented on the page. 

### 6. Upgrade the Project Web App site from SharePoint 2010 mode

After checking the PWA site collection and correcting any issues that can cause upgrade to fail, you can run the Upgrade-SPSite Microsoft PowerShell cmdlet to upgrade the PWA site to SharePoint 2013.

```
Upgrade-SPSite -Identity <URL> -versionupgrade
```

For example

```
Upgrade-SPSite -Identity https://contoso/pwa -versionupgrade
```


| **Required parameters** |
|:------------------------|
| -Identity  <br/>        |
| -versionupgrade  <br/>  |

## Project Server upgrade phase

After you complete the SharePoint Upgrade phase, you will be able to connect to the PWA site, but will be unable to view any project data because the Project Server 2010 database have not been connected and upgraded yet. Use the following steps in the Project Server upgrade phase to complete the upgrade.

||**Steps**|**Required Microsoft PowerShell cmdlet**|
|:-----|:-----|:-----|
|1  <br/> |Consolidate your Project Server 2010 databases to a Project Project Web App database  <br/> |Convertto-SPProjectDatabase  <br/> |
|2  <br/> |Attach your Project Web App database to the web application.  <br/> |Mount-SPProjectDatabase  <br/> |
|3  <br/> |Check your Project Web App database for errors  <br/> |Test-SPProjectDatabase  <br/> |
|4  <br/> |Upgrade your Project Web App database  <br/> |Upgrade-SPProjectDatabase  <br/> |
|5  <br/> |Mount your Project Web App Instance  <br/> |Mount-SPProjectWebInstance  <br/> |
|6  <br/> |Check your Project Web App instance for errors  <br/> |Test-SPProjectWebInstance  <br/> |
|7  <br/> |Upgrade your Project Web App Instance  <br/> |Upgrade-SPProjectWebInstance  <br/> |
|8  <br/> |Enable PWA features  <br/> |Enable-SPfeature  <br/> |

### 1. Consolidate your Project Server 2010 databases to a Project Web App database

Run the **Convertto-SPProjectDatabase** Microsoft PowerShell cmdlet to consolidate your restored Project Server 2010 databases to a single Project Server 2013 Project Web App database. This cmdlet also connects the new Project Server 2013 Project Web App database to the Project Server 2013 web application.

```
Convertto-SPProjectDatabase -WebApplication <URL> -Dbserver <databaseServerName> -ArchiveDbname<ArchivedbName> -DraftDbname<DraftdbName> -PublishedDbname<PublisheddbName> -ReportingDbname<ReportingdbName> -ProjectServiceDbname<ProjectWebAppdbName> 
```

For example:

```
Convertto-SPProjectDatabase -WebApplication https://contoso:80 -Dbserver SQLServer1 -ArchiveDbname ContosoProjectArchived -DraftDbname ContosoProjectDraft -PublishedDbname ContosoProjectPublished -ReportingDbname ContosoProjectReporting -ProjectServiceDbname ContosoProjectWebApp1 
```


| **Required Parameters**      |
|:-----------------------------|
| -WebApplication  <br/>       |
| -Dbserver  <br/>             |
| -ArchiveDbname  <br/>        |
| -DraftDbname  <br/>          |
| -PublishedDbname  <br/>      |
| -ReportingDbname  <br/>      |
| -ProjectServiceDbname  <br/> |

When you run the cmdlet, you are prompted for a confirmation that you want to continue. Type Y to continue.

After running this cmdlet successfully, you will see a confirmation message of "Conversion of Project Databases complete." You will also see the new Project Web App database on the computer that is running SQL Server.

### 2. Attach the Project Services database to the web application

Run the **Mount-SPProjectDatabase** Microsoft PowerShell cmdlet to attach your new Project Web App database to the web application that you had created earlier in your Project Server 2013 environment.

```
Mount-SPProjectDatabase -Name <ProjectWebAppdbName> -WebApplication<URL> -DatabaseServer <databaseServerName>
```

For example:

```
Mount-SPProjectDatabase -Name ContosoProjectWebApp1 -WebApplication https://contoso:80 -DatabaseServer SQLServer1
```


| **Required parameters** |
|:------------------------|
| -Name  <br/>            |
| -WebApplication  <br/>  |
| -DatabaseServer  <br/>  |

When the **Mount-SPProjectDatabase** cmdlet is finished, it will return you to the Microsoft PowerShell command prompt. Currently, you will not see a confirmation message upon successful completion.

### 3. Check your Project Web App database for errors that can cause upgrade to fail

Run the **Test-SPProjectDatabase** cmdlet to check your Project Web App database for issues that can cause upgrade of this database to fail. The **Test-SPProjectDatabase** cmdlet is a non-destructive test operation that will check the database and will post error that will prevent upgrade of the database.

```
Test-SPProjectDatabase -Name <contentdbName> -DatabaseServer <DBServerName>
```

For example:

```
Test-SPProjectDatabase -Name ContosoProjectWebApp1 -DatabaseServer SQLServer1
```

|||
|:-----|:-----|
|-Name  <br/> |Specifies the name of your Project Web App database.  <br/> |
|-Databaseserver  <br/> |Specifies the instance of the database service on which the Project Web App database is located.  <br/> The type must be a valid GUID, such as 12345678-90ab-cdef-1234-567890bcdefgh; a valid name of a SQL Server instance (for example, DBSvrInstance1); or an instance of a valid SPDatabaseServiceInstance object.  <br/> |

Running the **Test-SPProjectDatabase** cmdlet will check your Project Web App database and will post any possible errors in the data. It provides a description of the error, possible remedy, and an **UpgradeBlocking** flag to note if the error will prevent an upgrade of the database. It is important to address any errors in which the **UpgradeBlocking** flag is set to a value of True.

### 4. Upgrade the Project Web App database

Run the **Upgrade-SPProjectDatabase** Microsoft PowerShell cmdlet to upgrade your new Project Web App database to Project Server 2013. The four Project Server 2010 databases were merged to the Project Web App database by the **Convertto-SPProjectDatabase** in step 1.

```
Upgrade-SPProjectDatabase -Name <ProjectWebAppdbName> -WebApplication <URL> -DatabaseServer <databaseServerName>
```

For example:

```
Upgrade-SPProjectDatabase -Name ContosoProjectWebApp1 -WebApplication https://contoso:80 -DatabaseServer SQLServer1
```


| **Required Parameters** |
|:------------------------|
| -Name  <br/>            |
| -WebApplication  <br/>  |
| -DatabaseServer  <br/>  |

When you run the cmdlet, you are prompted for a confirmation that you want to continue. Type Y to continue.

When the **Upgrade-SPProjectDatabase** cmdlet is finished, it will return you to the Microsoft PowerShell command prompt. Currently, you will not see a confirmation message upon successful completion.

### 5. Mount the Project Web App instance

Run the **Mount-SPProjectWebInstance** Microsoft PowerShell cmdlet to connect your new Project Web App database to a Project Web App instance in Project Server 2013.

```
Mount-SPProjectWebInstance -DatabaseName <ProjectWebAppdbName> -SiteCollection<URL> -DatabaseServer <databaseServerName>
```

For example:

```
Mount-SPProjectWebInstance -DatabaseName ContosoProjectWebApp1 -SiteCollection https://contoso/pwa -DatabaseServer SQLServer1 
```


| **Required parameters** |
|:------------------------|
| -DatabaseName  <br/>    |
| -SiteCollection  <br/>  |
| -DatabaseServer  <br/>  |

When you run the cmdlet, you are prompted for a confirmation that you want to continue. Type Y to continue.

### 6. Check the Project Web App instance for issues that can cause upgrade to fail

Prior to trying to upgrade the Project Web App instance, run the **Test-SPProjectWebInstance** Microsoft PowerShell cmdlet to check the Project Web App instance for issues that can cause upgrade to fail.

This cmdlet checks for issues such as if the Project Business Intelligence (BI) Center exists for all project sites, or if there are unprocessed jobs in the queue and also queue status, and for issues with project workspaces. The result of the test appears in Microsoft PowerShell, but the information is more readable if you export the results to a text file. Use the results to address any issues with a "FailedWarning" status.

```
Test-SPProjectWebInstance -Identity <URL or Site ID>
```

For example:

```
Test-SPProjectWebInstance -Identity https://contoso/pwa
```


| **Required parameters** |
|:------------------------|
| -Identity  <br/>        |

### 7. Upgrade the Project Web App instance

Run the **Upgrade-SPProjectWebInstance** Microsoft PowerShell cmdlet to upgrade the Project Web App instance to Project Server 2013.

This cmdlet checks for issues such as if the Project Business Intelligence (BI) Center exists for all project sites, or if there are unprocessed jobs in the queue and also queue status, and for issues with project workspaces. The results of the test will display in Microsoft PowerShell, but the information will be more readable if you export the results to a text file. Use the results to address any issues with a "FailedWarning" status.

```
Upgrade-SPProjectWebInstance -Identity <URL or site ID>
```

For example:

```
Upgrade-SPProjectWebInstance -Identity https://contoso/pwa
```


| **Required parameter** |
|:-----------------------|
| -Identity  <br/>       |

When you run the cmdlet, you are prompted for a confirmation that you want to continue. Type Y to continue.

After you run this cmdlet successfully, you see a confirmation message of "Upgrade of single project site completed."

### 8. Enable Project Web App features

Run the **Enable-SPFeature** Microsoft PowerShell cmdlet to enable the PWA site feature on the site collection.

```
Enable-SPFeature -Identity pwasite -URL <ProjectSiteCollection>
```

For example:

```
Enable-SPFeature -Identity pwasite -URL https://contoso/PWA
```


| **Required parameter** |
|:-----------------------|
| -Identity  <br/>       |
| -URL  <br/>            |

When the **Enable-SPFeature** cmdlet finishes, it returns you to the Microsoft PowerShell command prompt. Currently, you will not see a confirmation message upon successful completion.

Open your Project Web App site URL to view your upgraded site and data.

## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.

If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.

![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)

## See also

#### 

[Plan for upgrade to Project Server 2013](plan-for-upgrade-to-project-server-2013.md)

[What's new for upgrade (Project Server 2013)](./what-s-new-in-project-server-2013-upgrade.md)

[Prepare your environment for upgrade (Project Server 2013)](./prepare-your-environment-for-an-upgrade-to-project-server-2013.md)

[Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)](./restore-your-project-server-2010-farm-databases-for-upgrade-project-server-2013.md)

[Create backup copies of your Project Server 2010 farm databases for upgrade (Project Server 2013)](./create-backup-copies-of-your-project-server-2010-farm-databases-for-upgrade-to-p.md)