---
title: "Restore Project Server 2013 by using built-in tools"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: c6f6d098-0400-446e-9e15-bf5557b4a77c
description: "Summary: You can do specific restores of Project Server 2013 in multiple ways, whether through a planned event, or as a result of Project Server having real issues that can only be addressed by a restore of a previously known good backup."
---

# Restore Project Server 2013 by using built-in tools
 
 **Summary:** You can do specific restores of Project Server 2013 in multiple ways, whether through a planned event, or as a result of Project Server having real issues that can only be addressed by a restore of a previously known good backup.<br/>
**Applies to:** Project Server 2013
  
Sometimes you must do a restore of your Project Server 2013 components, either into a new SharePoint Server 2013 environment or your existing SharePoint Server 2013 environment. If this is the case, your options depend on the SQL Server or SharePoint backups available to you. This article describes scenarios for the restore process for the built-in restore options recommended by Microsoft.
  
Before restoring your Project Server components to a SharePoint farm, make sure that you have reviewed the requirements for SharePoint restoration at [Restore farms in SharePoint 2013](https://technet.microsoft.com/library/7942ef65-c309-402d-b4bb-d54e686fc5d9.aspx). 
  
Some of the decisions which must be made when you are prepared to restore are as follows:
  
- Will you restore Project Server into a new environment, or an environment where those components already exist? 
    
    A new environment may be one that you are moving the Project Server components to, whereas an existing environment may be necessary to restore functionality, and will require overwriting in-place components.
    
- What type of backup do you have? 
    
    If this restore is unplanned, you must confirm what backups options are available for restoring. Do you only have a SQL Server backup? Do you have a SharePoint backup? 
    
    If this is a planned restore, you can decide what type of backup is most helpful to you by reviewing [Back up Project Server 2013 by using built-in tools](back-up-project-server-2013-by-using-built-in-tools.md).
    
    You may have several options, which will let you choose the scenario best suited to your needs. In some cases, only one type of backup may be available to you (such as SQL Server backups).
    
Consider the following before you try to restore your Project Server 2013 sites and components:
  
- When considering a Project Server 2013 component restore, you'll be restoring at least one Project Server service application (or at least its database) and one or more content databases that contain Project Web Access sites. If you want to restore additional SharePoint components, you can review the SharePoint articles at [Backup solutions in SharePoint 2013](https://technet.microsoft.com/library/79d47308-a90a-4c51-a1ae-93567e978236.aspx).
    
## Scenario one: You have SQL Server database backups

You have to restore your Project Server environment to a new farm, and you only have SQL Server backups available. The following steps allow you to restore both your PWA database and your SharePoint content database to a new farm. This exercise assumes that you have one PWA database and one content database that has Project sites in it to restore, and you are restoring to an environment that has Project Server 2013 installed, but not yet configured. It also assumes any custom elements, site definitions, features in the original farm are already installed in the new environment.
  
> [!NOTE]
> If you have multiple PWA sites or multiple content databases, or both, you must repeat the steps for each database. Organize in advance to avoid confusion over which content databases are used with which service application. 
  
### To restore SQL Server databases

1. On the server that is hosting the SQL Server installation being used by the SharePoint farm, open Start -> All Programs -> Microsoft SQL Server 2008/2012 -> SQL Server Management Studio.
    
2. Connect to the server hosting the SQL Server instance that you want to work with by clicking the **Connect** button.
    
3. Under your SQL Server instance on the left-hand side, right-click the **Databases** option, and choose **Restore Database** from the drop-down menu that appears.
    
4. In the **Restore Database** window, select the **Device** radio button for your **Source**, on the **General** page.
    
5. Click the **Build** button (three … dots to the right of the **Device** text box), and you will be able to open the **Select backup devices** window.
    
6. Click the **Add** button, and browse to the location of your SQL Server backups.
    
7. Choose the first database backup that you want to restore (in this scenario it's the PWA database), and then click **OK**. It should now be listed in the **Backup media** pane. If so, click **OK** to return to the **Restore Database** window.
    
8. The **Files** page should not require changes; it will create MDF and LDF files for the database being restored at the default SQL Server location. Change it only if you must. (In a production environment a DBA should make that determination with space and permission issues being considered.)
    
9. The **Options** page should not require changes, as this is a new farm, there should be no existing database that has this name. If there is a database that uses the name already present, choose a new name under the **General** and **Files** pages for this database.
    
10. Once you are ready, click **OK** on the **Restore Database** page to restore this database. Repeat steps 3 through 10 for the content database that you want to restore to this environment.
    
### To restore content databases in Central Administration

1. After restoring both databases, you next have to connect to a server on your SharePoint farm and open Start -> All Programs -> Microsoft SharePoint 2013 Products -> SharePoint 2013 Central Administration.
    
2. Select **Application Management** on the left-hand navigation.
    
3. Choose **Manage Web Applications**, under the **Web Application** heading.
    
4. On the following page, under the **Web Applications** tab, select **New**.
    
5. **Create an IIS web site** is the option button that should be selected.
    
6. You must use a unique IIS port or configure it with a Host Header as per your organization's needs and requirements.
    
7. Authentication and SSL should be similarly configured.
    
8. We recommend a new application pool, running under a suitable managed account.
    
9. The database name that you choose should be unique. However, this is a temporary database. Click **OK** to create this web application.
    
10. Once the web application is created, select **Application Management** on the left-hand navigation.
    
11. Click the **Manage content databases** link under **Databases**.
    
12. From the **Web Application** drop-down on the upper-right, choose **Change Web Application** if your newly-created web application is not listed. If it is listed, continue to step 14.
    
13. Select your newly-created web application from the list, and you should be returned to the previous page.
    
14. The database that you created as part of the web application creation should be listed. Click its name.
    
15. On the **Manage Content Database Settings** page, scroll to the bottom and select the **Remove content database** check box. Click **OK** to drop this content database from the SharePoint web application.
    
16. Back on the **Content Databases** page (which should now have no database names listing), click the **Add a content database** link.
    
17. The database server that contains your restored content database should be listed. Add the restored content database name to the **Database Name** field.
    
18. You may set the **Number of sites before a warning event is generated** and the **Maximum number of sites that can be created in this database** as per your organization's recommendations, but ideally you will set them to be greater than the number of sites existing in the database (if you are unsure how many sites are in the database, leave the numbers at the default settings and adjust later, as needed). Click **OK** when ready.
    
19. Now the content database is restored, and the site or sites contained in it should be capable of being browsed.
    
### To restore Project Server service application databases in Central Administration

1. In Central Administration, select **Application Management** on the left-hand navigation.
    
2. Click the **Manage Service Applications** link, in the **Service Applications**.
    
3. Select **New** from the **Service Applications** tab, and then choose **Project Server service application** from the list.
    
4. You must give your Project Server service application name, and we recommend that you also make a new application pool, running with a managed account. Leave the **Create a proxy** option selected, and then click **OK** to create the service application.
    
5. Once the service application has finished being created, you should be able to click the name link on the main service application page to open it.
    
6. Once the service application is open, you must click the **Create Project Web App Instance**.
    
7. Choose the web applications that you finished restoring in the previous section.
    
8. For a database, choose the restored Project Server database, and then click **OK**.
    
9. You will return to the main Project Server page, and the provisioning steps continue. Once the process has finished, your Project database is synched up to your PWA content, and your data should be restored into this new environment.
    
    > [!NOTE]
    > This becomes more complex with multiple Project Server service applications, as you will want to associate them with the correct content databases. Consult your organization's planning and build documentation or disaster-recovery documentation if you are unsure what your previous configuration may have been. 
  
## Scenario two: You have Central Administration farm backups

You have to restore a backup of your Project Server service application to a last known good configuration, and there is a SharePoint farm backup of this environment. In this scenario, the restore is put into the same environment that the backup was taken from, and you restore only Project Server components from a Full farm backup.
  
### To restore a Project Server service application by using SharePoint Central Administration

1. On a server in your SharePoint farm, open Start -> All Programs -> Microsoft SharePoint 2013 Products -> SharePoint 2013 Central Administration.
    
2. Select **Backup and Restore** from the left-hand navigation.
    
3. Click the **Restore from a backup** link, in the **Farm Backup and Restore** section.
    
4. If your job is not listed here, you must enter (in the **Backup Directory Location** text box) the directory where the farm backup was put.
    
5. Once you have the correct directory, select the date and time of the backup that you want to restore, and then click the **Next** button.
    
6. On the following page, scroll down to the **Shared Services Applications** listing and expand it.
    
7. Select the check box for the Project Server Shared Service you want to restore. It will auto-select that service application's components underneath.
    
8. Click **Next** at the bottom of the page to continue.
    
9. The following page will have an option button selection. Choose the **Same configuration** option, as you are restoring into the same farm. Click **OK** on the warning box that appears.
    
    > [!NOTE]
    > If you were restoring to a new farm, you would want the **New configuration** option to be selected.
  
10. Provide an appropriate password for the account in the **Login Names and Passwords** section.
    
11. Click the **Start Restore** button, and monitor the status on the following page until the restore is finished.
    
    If you receive any errors, you can review them in the **Failure Message** column of the **Backup and Restore Job Status** page. You can also find more details in the Sprestore.log file at the UNC path that you specified in step 2.
    
## Scenario three: You have a Project Server component backup

You have to restore a backup of your SharePoint farm to a last known good configuration, and there is a Project Server component backup of this environment. In this scenario, the restore occurs in a new environment that was built for the restore to match the old environment, excluding these missing components. You are restoring from a Project Server component backup by using Windows PowerShell.
  
### To restore Project Server components by using Windows PowerShell

1. On a server in your SharePoint farm, open Start -> All Programs -> Microsoft SharePoint 2013 Products -> SharePoint 2013 Management Shell, right-clicking the SharePoint 2013 Management Shell and selecting **Run as administrator** on the menu.
    
2. If the **User Account Control** box opens asking whether you want to allow the following program to make changes to this computer, and the program is Microsoft PowerShell, click the **Yes** button to continue.
    
3. To do a restore, some information is needed. The first thing that you have to type is this:
    
    **Get-SPBackupHistory -Directory** *<BackupShare>* **-ShowBackup**
    
    Where  *<BackupShare>* is the location of the backup. This enables you to see the GUID entry for the backup or backups at that location after you click the Enter key.
    
    > [!NOTE]
    > If you have multiple backups in the same location and are unsure of which GUID might be the one that you want, browse to the backup folder location and open the folder of that backup, and then open the spbackup.xml file in Notepad. The GUID that you must have for the following step will be four lines down, contained in the  `<SPID> </SPID>` tags.
  
4. After you identify the GUID of the backup that you want to restore, use the following command to restore to the SharePoint farm.
    
    **Restore-SPFarm -Directory** <BackupShare> **-BackupID** <GUID> **-RestoreMethod** New
    
    Where  *<BackupShare>* is the location of the backup and *<GUID>* is the GUID of the backup. The **RestoreMethod** refers to the fact that this is a new farm. A restore to the original farm for these components would require the **Overwrite** value. Click Enter to run.
    
5. You may be prompted whether you are sure you want to perform this action. Y is for **Yes** andA is **Yes to All**.
    
    > [!NOTE]
    > If you were restoring to an existing farm, you would also receive a prompt warning you that existing items will be overwritten, and a Y response here would allow the restore to continue.
  
6. The restore should continue until it is completed. If there are errors, you can review the restore log located at the backup path. If there are no errors, you should be able to confirm that your Project Server components are now in the restore farm.
    
For more information, see [Restore-SPFarm](https://technet.microsoft.com/library/8e18ea80-0830-4ffa-b6b6-ad18a5a7ab3e.aspx).
> [!NOTE]
> We recommend that you use Windows PowerShell when performing command-line administrative tasks. The Stsadm command-line tool has been deprecated, but is included to support compatibility with previous product versions. 
  
## See also

#### 

[Back up Project Server 2013 by using built-in tools](back-up-project-server-2013-by-using-built-in-tools.md)

