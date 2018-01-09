---
title: "Configure OLAP cubes for Project Web App"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/21/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: f64d7cd6-8795-4c79-baec-eefdb5be1a61
description: "Summary: Set up OLAP cubes for Project Web App."
---

# Configure OLAP cubes for Project Web App
 
 **Summary:** Set up OLAP cubes for Project Web App.<br/>
**Applies to:** Project Server 2013
  
> [!IMPORTANT]
> This scenario applies only to Project Server 2013. 
  
In this article:
    
- Before you begin
- Configure the Analysis Services service account    
- Build an OLAP cube in Project Web App    
- Grant access to the Project Web App OLAP cube
    
## Overview
<a name="overview"> </a>

This article describes how to configure a SQL Server Analysis Services cube for Project Web App. You must follow the procedures in this article for each instance of Project Web App that you create.
  
> [!NOTE]
> Due to changes in the security infrastructure in Project Server 2013, the View OLAP Data permission that existed in earlier versions of Project Server no longer exists in Project Server 2013. Cube access is now configured using the procedures in this article. 
  
## Before you begin
<a name="begin"> </a>

This article assumes that you have completed all of the steps in [Configure reporting for Project Web App (Project Server 2013)](http://technet.microsoft.com/library/1882695e-50f4-4bc7-9f15-18365f96caf5.aspx). The procedures in this article make use of the Active Directory groups and accounts that you created in the reporting configuration article.
  
Before you begin, make sure you have the following:
  
- An instance of SQL Server Analysis Services where you can build an OLAP cube.
    
- The name of the account that is running the SQL Server Analysis Services service.
    
- The name of the Report Authors group that you created when you configured reporting for Project Web App
    
- The name of the Secure Store Target Application account that you created when you configured reporting for Project Web App.
    
    > [!NOTE]
    > If this account is a member of the Report Authors group, then you will not need it for the procedures below. 
  
## Configure the Analysis Services service account
<a name="proc1"> </a>

To build OLAP cubes, the account running the Analysis Services service must have read access to the Project Web App database. This access is granted using the PSDataAccess database role in SQL Server.
  
The first step is to create a SQL Server login for the account running the SQL Server Analysis Services service.
  
Use the following procedure to create a login for the SQL Server Analysis Services service account.
  
> [!NOTE]
> If a login already exists for the SQL Server Analysis Services service account, you can skip this procedure. 
  
### To create a login for the Analysis Services service account

1. In SQL Server Management Studio, connect to the instance of the database engine where your Project Web App is located.
    
2. In Object Explorer, expand **Security**.
    
3. Right-click **Logins**, and then click **New Login**.
    
4. In the **Login name** box, type the name of the Active Directory account that is running the Analysis Services service.
    
5. Click **OK**.
    
Once the login has been created, you must grant the login access to the Project Web App database. Use the following procedure to configure database access.
  
### To grant database access to the Analysis Services service account

1. In SQL Server Management Studio, connect to the database engine.
    
2. In Object Explorer, expand **Security**.
    
3. Double-click the login for the Analysis Services service.
    
4. In the **Select a page** section, click **User Mapping**.
    
5. Select the **Map** check box for the Project Web App database that you want to provide access to, and then, in the **Database role membership for: <database>** section, select the **PSDataAccess** check box.
    
6. Click **OK**.
    
The next step is to build an OLAP cube.
  
## Build an OLAP cube
<a name="proc2"> </a>

In order to configure the needed permissions in SQL Server Analysis Services, the OLAP cube must be created. Even if you do not plan to use the cube right away, you will need to build one now in order to configure the needed user access requirements.
  
Use the following procedure to build an OLAP cube.
  
### To build an OLAP cube

1. In Central Administration, under **Application Management**, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Hover over the instance of Project Web App for which you want to build a cube, click the arrow that appears, and then click **Manage**.
    
4. On the Project Web App settings page, under **Queue and Database Administration**, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, in the **OLAP Database Name** column, click the **DatabaseName** link.
    
6. On the OLAP Database Build Settings page:
    
1. In the **Analysis Services Server** box, type the name of the instance of Analysis Services where you want to build the cube.
    
2. In the **Analysis Services Database to be created** box, type a name for the OLAP database.
    
3. Click **Save**.
    
7. On the OLAP Database Management page, select the row in the table for the cube that you just configured, and then click **Build Now**.
    
8. Monitor the **Status** field on the OLAP Database Management page until the status is **Build Success!**
    
After you have built the cube, you can grant users access to it.
  
## Grant access to the OLAP cube
<a name="proc3"> </a>

To grant users access to the cube, you must add the following groups and accounts to the default ProjectServerViewOlapDataRole role in the cube:
  
- The Report Authors Active Directory group that you created when you configured reporting for Project Web App. This group should contain the users who you expect to be working with OLAP cube data in Excel.
    
- The Secure Store Target Application account that you created when you configured reporting for Project Web App. This account will allow users viewing OLAP cube reports in Excel Services to refresh the data. If you added this account to the Report Authors group when you configured reporting for Project Web App, there's no need to add it separately here.
    
If you have additional users beyond those in the Report Authors group who will be accessing the cube from Excel, you must grant them access to the cube as well. Consider using the same groups that you use for Active Directory synchronization to grant cube access to your users. For example, if you want all Project Managers to have access to the OLAP cube in Excel, add the Active Directory group that you're synchronizing with the Project Managers group to the ProjectServerViewOlapDataRole role in the cube.
  
Use the following procedure to grant users access to the OLAP cube.
  
### To grant user access to the OLAP cube

1. In SQL Server Management Studio, connect to Analysis Services.
    
2. In Object Explorer, expand **Databases**.
    
3. Expand the cube that you just created.
    
4. Double-click the **ProjectServerViewOlapDataRole** role.
    
5. In the left pane, select the **Membership** page.
    
6. On the Membership page, click **Add**.
    
7. On the **Select Users or Groups** dialog box, click **Object Types**.
    
8. On the **Object Types** dialog box, select the **Groups** check box, and then click **OK**.
    
9. On the **Select Users or Groups** dialog box, type the name of the Report Authors Active Directory group and the name of the data access account for the ProjectServerApplication Secure Store target application. Also type the name of any additional users or groups to which you want to grant cube access.
    
10. Click **OK**.
    
11. Click **OK**.
    
## See also
<a name="proc3"> </a>

#### 

[Active Directory Resource Pool Synchronization for Project Server 2013](active-directory-resource-pool-synchronization-for-project-server-2013.md)
#### 

[Configure reporting for Project Web App (Project Server 2013)](http://technet.microsoft.com/library/1882695e-50f4-4bc7-9f15-18365f96caf5.aspx)
  
[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

