---
title: "Create backup copies of your Project Server 2010 farm databases for upgrade to Project Server 2013"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: a2570ae9-dfb4-43be-8ef4-940b2f9a072a
description: "Summary: Learn how to back up Project Server 2010 databases by using SQL Server 2005, SQL Server 2008 or SQL Server 2008 R2, or SQL Server 2012."
---

# Create backup copies of your Project Server 2010 farm databases for upgrade to Project Server 2013
 
 **Summary:** Learn how to back up Project Server 2010 databases by using SQL Server 2005, SQL Server 2008 or SQL Server 2008 R2, or SQL Server 2012.<br/>
**Applies to:** Project Server 2013
  
Upgrading to Project Server 2013 requires you to use the database-attach upgrade method. This method upgrades your Project Server 2010 databases and merges them in a single Project Web App database. It also restores the Project Web App content database to your Project Server 2013 farm. One of the first steps in upgrading from Project Server 2010 to Project Server 2013 is to create backup copies of your databases that you will need to upgrade from your Project Server 2010 farm deployment. These databases include the following:
  
- Project Server Draft
    
- Project Server Archived
    
- Project Server Published
    
- Project Server Reporting
    
- SharePoint content database (which contains your Project Web App site data)
    
The following sections describe how to create backup copies of these databases in SQL Server. These include procedures in each of the SQL Server versions that are supported for use with Project Server 2010:
  
- SQL Server 2005
    
- SQL Server 2008 or SQL Server 2008 R2
    
- SQL Server 2012
    
After you complete this procedure, you will have to restore your backup copies of your databases to the SQL Server instance that you are using to host your Project Server 2013 databases. For more information, see [Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)](./restore-your-project-server-2010-farm-databases-for-upgrade-project-server-2013.md).
  
## Create backup copies of your databases in SQL Server 2005

### To back up a database in SQL Server 2005

1. On the database server, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2005**, and then click **SQL Server Management Studio**.
    
2. In the **Connect to Server** dialog box, fill in the connection information, and then click **Connect**.
    
3. After you connect to the appropriate instance of the SQL Server 2005 Database Engine, in Object Explorer, expand the server tree by expanding the server name.
    
4. Expand **Databases**, right-click the database that you want to back up, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.
    
5. In the **Source** section, in the **Database** box, verify the database name.
    
6. In the **Backup type** box, select **Full**.
    
7. For the **Backup component**, select **Database**.
    
8. In the **Backup set** section, in the **Name** box, either accept the default backup set name that is suggested or type a different name for the backup set.
    
9. In the **Destination** section, specify the type of backup destination by selecting **Disk** or **Tape**, and then specify a destination. To create a different destination, click **Add**.
    
10. Click **OK** to start the backup process.
    
Repeat the previous procedure to back up the remaining required databases.
  
## Create backup copies of your databases in SQL Server 2008 and SQL Server 2008 R2

### To back up a database in SQL Server 2008 or SQL Server 2008 R2

1. On the database server, click **Start**, point to **All Programs**, point to **Microsoft SQL Server 2008**, and then click **SQL Server Management Studio**.
    
2. In the **Connect to Server** dialog box, fill in the connection information, and then click **Connect**.
    
3. After you connect to the appropriate instance of the SQL Server 2008 Database Engine, in Object Explorer, expand the server name.
    
4. Expand **Databases**, right-click the database that you want to back up, point to **Tasks**, and then click **Back Up**. The **Back Up Database** dialog box appears.
    
5. In the **Source** area, in the **Database** box, verify the database name.
    
6. In the **Backup type** box, select **Full**.
    
7. Under **Backup component**, select **Database**.
    
8. In the **Backup set** section, in the **Name** box, either accept the default backup set name or type a new name.
    
9. In the **Destination** section, specify the type of backup destination by selecting **Disk** or **Tape**, and then specify a destination. To create a different destination, click **Add**.
    
10. Click **OK** to start the backup process.
    
Repeat the previous procedure to back up the remaining required databases.
  
## Create backup copies of your databases in SQL Server 2012

### To back up a database in SQL Server 2012

1. Open SQL Server Management Studio and connect to the appropriate instance of the SQL Server 2012 Database Engine.
    
2. In the Object Explorer pane, expand **Databases**, right-click the database that you want to back up, click **Tasks**, and then click **Back Up**.
    
3. In the **Back Up Database** dialog box, on the General page, in the **Source** section, click the **Database** drop-down menu and select the database that you want to back up.
    
4. In the **Backup type** box, select **Full**.
    
5. For the **Backup component**, select **Database**.
    
6. In the **Backup set** section, in the **Name** box, either accept the default backup set name or type a new name.
    
7. In the **Destination** section, specify the type of backup destination by selecting **Disk** or **Tape**. Click **Add**. In the **Select Backup Destination** dialog box, click the **Browse** button. In the **Locate Database Files** dialog box, in the **File name** box, type a name for the backup file. Click **OK**. 
    
8. In the General page, click **OK** to start the backup process. The status of the backup process will appear in the **Progress** section. When the process has completed successfully, a dialog box appears that states that the backup has completed successfully. Click **OK**. The backup file can be found in the location noted in the **Destination** section.
    
Repeat the previous procedure to back up the remaining required databases.
  
## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also

[Plan for upgrade to Project Server 2013](plan-for-upgrade-to-project-server-2013.md)
  
[Upgrade to Project Server 2013](upgrade-to-project-server-2013.md)

[What's new for upgrade (Project Server 2013)](./what-s-new-in-project-server-2013-upgrade.md)
  
[Prepare your environment for upgrade (Project Server 2013)](./prepare-your-environment-for-an-upgrade-to-project-server-2013.md)
  
[Restore your Project Server 2010 farm databases for upgrade (Project Server 2013)](./restore-your-project-server-2010-farm-databases-for-upgrade-project-server-2013.md)