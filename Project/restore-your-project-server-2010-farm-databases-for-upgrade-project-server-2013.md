---
title: "Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/22/2017
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: e79d3ca4-7f2d-4c94-be68-a408fd3de65d
description: "Summary: Restore your Project Server 2010 databases to the SQL Server instance that is hosting your Project Server 2013 data."
---

# Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** Restore your Project Server 2010 databases to the SQL Server instance that is hosting your Project Server 2013 data.
  
This is one of the required steps when you upgrade from Project Server 2010 to Project Server 2013 through the database-attach upgrade method.
  
After you have configured the Project Server 2013 destination environment, you can restore the backup copies of the Project Server 2010 databases on the SQL Server instance that you are using to host your Project Server 2013 databases. This requires you to have backup copies of your Project Server 2010 databases and the SharePoint content database used to host your Project Web App site data. For information about how to create backup copies of these databases, see [Create backup copies of your Project Server 2010 farm databases for upgrade (Project Server 2013)](http://technet.microsoft.com/library/028f9509-0cfb-4f7e-b102-e19f36d8f014.aspx). 
  
The Project Server 2010 databases that are required for upgrading to Project Server 2013 include the following:
  
- Project Server Draft
    
- Project Server Archived
    
- Project Server Published
    
- Project Server Reporting
    
- SharePoint content database that contains your Project Web App site data
    
The following sections describe how to restore the backup copies of these databases on the SQL Server instance that you are using to host your Project Server 2013 databases. These include procedures in each of the SQL Server versions that are supported for use with Project Server 2010:
  
- SQL Server 2008 or SQL Server 2008 R2
    
- SQL Server 2012
    
After you have restored the backup copies of the Project Server 2010 databases, you can upgrade the databases and the Project Web App site collection. For more information, see [Upgrading to Project Server 2016](upgrading-to-project-server-2016.md).
  
## Restore your Project Server 2010 databases in SQL Server 2008 or SQL Server 2008 Release 2

### To restore a backup copy of a database in SQL Server 2008 Enterprise

1. After you connect to the appropriate instance of the SQL Server 2008 Database Engine, in Object Explorer, expand the server name.
    
2. In Object Explorer, right-click **Databases**, and then click **Restore Database**. 
    
    The **Restore Database** dialog box appears.
    
3. In the **Restore Database** dialog box, on the **General** page, type the name of the database to be restored in the **To database** list.
    
4. In the **To a point in time** box, keep the default ( **Most recent possible**).
    
5. To specify the source and location of the backup sets to restore, click **From device**, and then click **Browse** to select the backup file.
    
6. In the **Specify Backup** dialog box, in the **Backup media** box, be sure that **File** is selected.
    
7. In the **Backup location** area, click **Add**.
    
8. In the **Locate Backup File** dialog box, select the file that you want to restore, click **OK**, and then, in the **Specify Backup** dialog box, click **OK**.
    
9. In the **Restore Database** dialog box, under the **Select the backup sets to restore** grid, select the **Restore** check box next to the most recent full backup.
    
10. In the **Restore Database** dialog box, on the **Options** page, under **Restore options**, select the **Overwrite the existing database** check box.
    
11. Click **OK** to start the recovery process.
    
Repeat the previous procedure to restore the remaining required databases.
### To restore a backup copy of a database in SQL Server 2012

1. Open SQL Server Management Studio, and connect to the appropriate instance of the SQL Server 2012 Database Engine.
    
2. In the Object Explorer pane, right-click **Databases**, and then click **Restore Database**. 
    
    The **Restore Database** dialog box appears.
    
3. In the **Restore Database** dialog box, select the **General** page. In the **Source** section, select **Device** and then click the **Browse** button.
    
4. In the **Select backup devices** dialog box, click **Add**.
    
5. In the **Locate Backup File** dialog box, locate and select the database that you want to restore. Click **OK**.
    
6. In the **Select backup devices** dialog box, click **OK**.
    
7. On the General page, in the **Restore plan** section, in the **Backup sets to restore** list, verify that the **Restore** check box is selected for the database that you are restoring.
    
8. In the **Destination** section, in the **Database** field, you can type a new database name if you want to change it from the previous name.
    
9. Click **OK** to start the restore process. The status will appear in the status bar on the top of the page.
    
10. When the restore process is complete, a dialog box is displayed that states that the database was restored successfully. Click **OK**.
    
Repeat the previous procedure to restore the remaining required databases.
## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also

#### 

[Plan for upgrade to Project Server 2016](plan-for-upgrade-to-project-server-2016.md)
  
[Upgrading to Project Server 2016](upgrading-to-project-server-2016.md)
#### 

[What's new for upgrade (Project Server 2013)](http://technet.microsoft.com/library/d42b8778-87ee-4e09-8b9e-cb2d1d800db9.aspx)
  
[Prepare your environment for upgrade (Project Server 2013)](http://technet.microsoft.com/library/587325fd-c15f-4347-a247-92abbf23fb76.aspx)
  
[Create backup copies of your Project Server 2010 farm databases for upgrade (Project Server 2013)](http://technet.microsoft.com/library/028f9509-0cfb-4f7e-b102-e19f36d8f014.aspx)

