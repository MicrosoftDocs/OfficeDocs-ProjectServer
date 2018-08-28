---
title: "Back up Project Server 2013 by using built-in tools"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: d016e0f7-3c61-4862-9fac-37696cfdefbe
description: "Summary: Learn how to implement a backup strategy for Project Server farm components by using SharePoint Server 2013 and SQL Server tools."
---

# Back up Project Server 2013 by using built-in tools
 
 **Summary:** Learn how to implement a backup strategy for Project Server farm components by using SharePoint Server 2013 and SQL Server tools.<br/>
**Applies to:** Project Server 2013
  
There are three ways to back up Project Server 2013 components located in a SharePoint Server 2013 farm.
  
- You can use SQL Server tools to back up the relevant Project Server 2013 databases.
    
- You can use the SharePoint Central Administration website to back up the relevant Project Server databases.
    
- You can use Microsoft PowerShell to back up the relevant Project Server databases.
    
We recommend a backup for any production environment, or any environment where data loss would be unacceptable. In a SharePoint farm, the ideal method is to back up all content and configuration databases so that you can perform a complete restore, if necessary. Monitor farm resources when backups are taken for performance issues, and if desirable, take your backups during low-usage times.
  
> [!NOTE]
> To review the backup documentation for a SharePoint Server 2013 farm, see [Back up farms in SharePoint 2013](http://technet.microsoft.com/library/8daa31a5-0f8c-4bd6-84c9-ee1f5074594d.aspx). 
  
For Project Server 2013, there are two core components for backing up, unique to Project Server: a Project Server service application database for each Project Server service application in the farm, and at least one, but possibly more than one, content database that contains Project sites. The methods outlined below show you how to back up these elements.
  
## Use SQL Server tools to take Project Server database backups

> [!IMPORTANT]
> This process can also be automated by your database administrator and may already be in place. Discuss backups with your database administrator as needed. 
  
### To identify Project Server databases in a SharePoint farm

1. Identify the relevant Project Server 2013 databases to be backed up. Go to Start -> All Programs -> Microsoft SharePoint 2013 Products -> SharePoint 2013 Central Administration.
    
2. Select **Application Management** from the left-hand navigation.
    
3. Click **Manage service applications**, under the **Service Applications** heading on the following page.
    
4. On this page, you must select each service application of Type: **Project Application Services**. Depending on your organizational needs, you may have more than one service application configured. Click the name of the first service application found.
    
5. On the following page, you may see one or more URLs listed with Project Web App sites created for them. For each one listed, rest your mouse on the URL and then click the drop-down arrow to the right when it appears.
    
6. Select **View** from the drop-down menu.
    
7. This page gives you the web application for the Project Web App site, which you can use to determine the content database or databases to back up, and the Project Web App path. Make a note of these.
    
    The **Database Settings** section gives you the Project Web App database name. You should also note this name.
    
8. To determine the content database name, click **Application Management** on the left-hand navigation again.
    
9. Click **View all site collections**, in the **Site Collections** section.
    
10. Here you are able to go to the **Web Application:** drop-down on the upper-right-hand side of the page. Select the drop-down arrow and choose **Change Web Application**.
    
11. Choose the web application identified in step 7.
    
12. You should now see a list of site collections for this web application. Identify the Project Web App path, from step 7.
    
13. Once you have selected that site collection, the database that it is located in should be listed in the table to the right. Make note of that name.
    
14. Repeat this process for each URL listed in your Project Server service application, and for each Project Server service application you have. At this point, you should have the minimum database requirements for a SQL backup listed.
    
### To back up Project Server databases from a SharePoint farm by using SQL Server tools

1. On the server hosting the SQL Server installation being used by the SharePoint farm, open Start -> All Programs -> Microsoft SQL Server 2008/2012 -> SQL Server Management Studio.
    
2. Connect to the server hosting the SQL instance you want to work with by clicking the **Connect** button.
    
3. Under your SQL instance on the left-hand side, expand the **Databases** option.
    
4. You should now see which databases are listed for this instance. Retrieve the list you completed in step 14 of the previous section.
    
5. For each database in this list, right-click the database name, and choose **Tasks** and then **Backup** on the submenu.
    
6. Once the Backup window opens, under the **General Page**, select the **Backup Type** to be **Full** ( **Differential** can be done later, the first backup must be full). Choose a name if the default name is insufficient, and ensure that the destination folder is appropriate and has sufficient space. If not, choose a suitable location.
    
7. Click **OK** to perform the backup.
    
8. Repeat this process for each database in the list.
    
### To schedule the backup

1.	Go to Start -> All Programs -> Microsoft SQL Server 2008/2012 -> SQL Server Management Studio.

2.	Connect to the server hosting the SQL instance you want to work with by clicking the **Connect** button.

3.	Expand the server where you want to create your management plan.

4.	Right-click Maintenance Plans and then click Maintenance Plan Wizard.

5.	The wizard builds the maintenance plans that will run per your instructions set via the wizard.

## Use Central Administration to take Project Server component backups

If you are using this method, discuss it with your database administrator before implementation. SharePoint Server 2013 backups involve using SQL backup methods, and this may be disruptive to a SQL backup schedule.
  
### To back up Project Server components by using Central Administration

1. Go to Start -> All Programs -> Microsoft SharePoint 2013 Products -> SharePoint 2013 Central Administration.
    
2. Select **Backup and Restore** from the left-hand navigation.
    
3. Select **Perform a backup** under **Farm Backup and Restore**.
    
4. In the **Select component to back up** section, scroll down to the **Shared Services** section in the tree view of the page.
    
5. In the **Shared Services** section, expand **Shared Services Applications**.
    
6. You must select the check box for the Project Server Shared Service in your Shared Services Applications list that you want to back up. The content that relates to each service application should be listed immediately underneath the service application name, and also be auto-checked. 
    
    > [!NOTE]
    > If you have multiple Project Server Service Applications, each must be backed up separately. 
  
7. Scroll to the bottom of the page and select **Next** in order to proceed to the **Step 2: Select Backup Options** page.
    
8. If this is the first time that you have performed a backup, you must leave the option button for **Backup Type** to **Full**. Subsequent backup types may be set to **Differential**, being aware that the Full backup must be restored before the Differential backup(s).
    
9. You must have a UNC path, a share, in the \\\\server\\share format, for your backup location. We recommend against using use a share on the same server that the current installation of SharePoint Server is running on, in the event of a critical issue occurring on that server.
    
    > [!NOTE]
    > The account running your SharePoint installation's MSSQLSERVER service must have explicit write permissions to the UNC folder, as this is the account which backs up the databases. 
  
10. Click **Start Backup**, and monitor progress on the **Backup and Restore status page** until completed.
    
11. If issues are encountered, review the information found on the Backup and Restore status page, or the backup log located at the path that was specified in step 9. Otherwise the backup should be at the location that was specified in step 9.
    
## Use Windows PowerShell to take Project Server component backups

You can use Microsoft PowerShell to back up your Project Server 2013 farm manually or as part of a script that can be run at scheduled intervals.
  
### To back up Project Server components by using Windows PowerShell

1. On a server in the SharePoint farm, open Start > All Programs -> SharePoint 2016 -> SharePoint 2016 Management Shell.
    
2. Right-click the **SharePoint 2013 Management Shell** and choose **Run as administrator** from the menu to open the application in administration mode. If UAC prompts you to allow the program to make changes to this computer, and Microsoft PowerShell is listed as the application, select **Yes**.
    
3. At the prompt, type the following command:
    
    **Backup-SPFarm -ShowTree -Directory** _<BackupShare>_ **-BackupMethod** [ **full/incremental** ] -Path _<Project Server Web Application Name>_
    
4. This allows you to determine the elements that you will backup, without actually performing the backup, thanks to the **-ShowTree** parameter. If your service application name is not unique, this should provide you with the full path to enter for **-Path** instead (if there are spaces, enclose the path with double quotation marks).
    
5. Once you have identified the Project Server service application to back up, and confirmed with the **-ShowTree** command , you can remove the **-ShowTree** command to perform the backup.
    
    **Backup-SPFarm -Directory** _<BackupShare>_ **-BackupMethod** [ **full/incremental** ] -Path _<Project Server Web Application Name>_
    
6. Click **Enter**. If you add the **-Verbose** parameter, detailed information is provided about the backup status. If you do not, then a "successful" or error message appears at the end of the backup process.
    
7. If issues are encountered, review the backup log located at the path that was specified in step 8. Otherwise, the backup will be at the location that was specified at the **-Directory** parameter.
    
For more information, see [Backup-SPFarm](http://technet.microsoft.com/library/c37704b5-5361-4090-a84d-fcdd17bbe345.aspx).
> [!NOTE]
> We recommend that you use Windows PowerShell when performing command-line administrative tasks. The Stsadm command-line tool has been deprecated, but is included to support compatibility with previous product versions. 
  
## See also

#### 

[Restore Project Server 2013 by using built-in tools](restore-project-server-2013-by-using-built-in-tools.md)

