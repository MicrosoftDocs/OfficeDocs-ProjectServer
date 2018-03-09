---
title: "Configure OLAP cubes for Project Web App"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: b66a49cd-9086-424f-8915-6fd3a4b002b0
description: "Summary: Set up OLAP cubes for Project Web App in Project Server 2016."
---

# Configure OLAP cubes for Project Web App
 
 **Summary:** Set up OLAP cubes for Project Web App in Project Server 2016.<br/>
**Applies to:** Project Server 2016
  
This article describes how to configure a SQL Server Analysis Services cube for Project Web App. You must follow the procedures in this article for each instance of Project Web App that you create.
  
In this article:
  
- [Before you begin](configure-olap-cubes-for-project-web-app.md#begin)
    
- [Configure the Analysis Services service account](configure-olap-cubes-for-project-web-app.md#proc1)
    
- [Build an OLAP cube in Project Web App](configure-olap-cubes-for-project-web-app.md#proc2)
    
- [Grant access to the Project Web App OLAP cube](configure-olap-cubes-for-project-web-app.md#proc3)
    
## Before you begin
<a name="begin"> </a>

Before you begin:
  
- You need an instance of SQL Server Analysis Services where you can build an OLAP cube You also need the name of the account that is running the SQL Server Analysis Services service for one of the procedures in this article.
    
- Ensure that the SharePoint system account is an [OLAP Administrator](https://go.microsoft.com/fwlink/p/?LinkID=717498) on that instance of SQL Server Analysis Services.
    
- You must have installed the SQL Server 2014 Analysis Management Objects (AMO) on each Application and Front-end role servers in the farm. ([Download the SQL Server 2014 Analysis Management Objects](https://go.microsoft.com/fwlink/?LinkId=722556).)
    
## Configure the Analysis Services service account
<a name="proc1"> </a>

To build OLAP cubes, the account running the Analysis Services service must have read access to the Project Web App in the SharePoint Content database. This access is granted using the PSDataAccess database role in SQL Server.
  
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
    
Once the login has been created, you must grant the login access to the SharePoint content database where your Project Web App site is located. Use the following procedure to configure database access.
  
### To grant database access to the Analysis Services service account

1. In SQL Server Management Studio, connect to the database engine.
    
2. In Object Explorer, expand **Security**.
    
3. Double-click the login for the Analysis Services service.
    
4. In the **Select a page** section, click **User Mapping**.
    
5. Select the **Map** check box for the SharePoint content database where your Project Web App site is located, and then, in the **Database role membership for: <database>** section, select the **PSDataAccess** check box.
    
6. Click **OK**.
    
The next step is to build an OLAP cube.
  
## Build an OLAP cube in Project Web App
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
  
## Grant access to the Project Web App OLAP cube
<a name="proc3"> </a>

To grant users access to the cube, you must add the following groups and accounts to the default ProjectServerViewOlapDataRole role in the cube:
  
- If you're accessing the cube using Windows authentication, such as through Excel, your user account must be a member of the ProjectServerViewOlapDataRole role in the cube. Consider using Active Directory Directory Services groups to manage user access to the cube. If you're using Active Directory synchronization with Project Server, those groups may contain the users to whom you want to grant cube access.
    
- If you're accessing the cube using Secure Store, such as when using Excel Online, the credentials of the Secure Store target application must be a member of the ProjectServerViewOlapDataRole role in the cube.
    
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

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

