---
title: "Overview of the upgrade process to Project Server 2013"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_OneDriveAdmin
ms.assetid: 0e896c78-7e9e-4e24-a398-0319873b15ef
description: "Summary: Upgrade from Project Server 2010 to Project Server 2013."
---

# Overview of the upgrade process to Project Server 2013
 
 **Summary:** Upgrade from Project Server 2010 to Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
This article contains an overview of the procedures required to upgrade to Project Server 2013 from Project Server 2010.
  
> [!NOTE]
> If you are upgrading to Project Server 2013 from Office Project Server 2007, you must first upgrade to Project Server 2010. There is no direct upgrade path from Office Project Server 2007 to Project Server 2013. For more information, see [What's new for upgrade (Project Server 2013)](./what-s-new-in-project-server-2013-upgrade.md). 
  
## Upgrade process overview

Upgrading to Project Server 2013 from Project Server 2010 can be separated into the following sequential phases:
  
1. Create the Project Server 2013 farm
    
2. Copy the required databases from the Project Server 2010 farm
    
3. Restore the databases to the computer that is running SQL Server that is hosting your Project Server 2013 databases
    
4. Upgrade the databases
    
5. Upgrade the Project Web App site collection
    
### Create the Project Server 2013 farm

The first stage in upgrading to Project Server 2013 is to create the new Project Server 2013 destination farm.
  
1. The server farm administrator installs SharePoint Server 2013 to a new farm.
    
    > [!NOTE]
    > SharePoint Server 2013 is a prerequisite for installing Project Server 2013. 
  
2. The server farm administrator installs Project Server 2013 to the farm.
    
### Copy the required databases from the Project Server 2013 farm

1. The farm administrator sets the Project Web App (PWA) site collection in the Project Server 2010 farm to read-only so that users can continue to access the old farm while the upgrade is in progress on the new farm. This ensures that no jobs are processed during the upgrade process. 
    
2. With the PWA site collection set to read-only mode on the Project Server 2010 farm, the database administrator creates backup copies of the databases required for upgrade. These include the following:
    
   - Project Server 2010 Archive
    
   - Project Server 2010 Draft
    
   - Project Server 2010 Published
    
   - Project Server 2010 Reporting
    
   - SharePoint content database that contains the Project Web App site data
    
> [!NOTE]
> For more information about copying your Project Server 2010 farm databases for upgrade, see [Create backup copies of your Project Server 2010 farm databases for upgrade to Project Server 2013](./create-backup-copies-of-your-project-server-2010-farm-databases-for-upgrade-to-p.md). 
  
### Restore the databases to the computer that is running SQL Server that is hosting your Project Server 2013 farm databases

The farm administrator restores the Project Server 2010 databases to the computer that is running SQL Server that is hosting your Project Server 2013 farm databases.
  
> [!NOTE]
> For more information about restoring your databases, see [Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)](./restore-your-project-server-2010-farm-databases-for-upgrade-project-server-2013.md). 
  
### Upgrade the databases

1. The server farm administrator attaches and upgrades the SharePoint Content database to the Project Server 2013 farm.
    
2. The server farm administrator consolidates the four Project Server 2010 database to a single Project Services database.
    
3. The new Project Services database is attached and then upgraded to the Project Server 2013 farm.
    
### Upgrade the Project Web App site collection

1. The farm administrator tests and then upgrades the Project Web App (PWA) site collection.
    
2. The farm administrator enables PWA features for the site. 
    
> [!NOTE]
> For detailed procedures about upgrading your databases and the PWA site collection, see [Upgrade your databases and Project Web App site collections to Project Server 2016](upgrade-your-databases-and-project-web-app-site-collections-project-server-2013.md). 
  
## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also

[Plan for upgrade to Project Server 2016](plan-for-upgrade-to-project-server-2016.md)

[What's new for upgrade (Project Server 2013)](./what-s-new-in-project-server-2013-upgrade.md)
  
[Prepare your environment for upgrade (Project Server 2013)](./prepare-your-environment-for-an-upgrade-to-project-server-2013.md)
  
[Plan for upgrade (SharePoint 2013 Products)](/SharePoint/upgrade-and-update/plan-for-upgrade)