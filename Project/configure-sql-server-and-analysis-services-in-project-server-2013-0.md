---
title: "Configure SQL Server and Analysis Services in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 3d90a60f-b4a4-4119-acd1-5925e54ce856
description: "Summary: Configure SQL Server and SQL Server Analysis Services (SSAS) settings prior to installing Project Server 2013."
---

# Configure SQL Server and Analysis Services in Project Server 2013
 
 **Summary:** Configure SQL Server and SQL Server Analysis Services (SSAS) settings prior to installing Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
Before you install SharePoint Server 2013 and Project Server 2013, you must first configure SQL Server and, if you're planning to use Project Server OLAP cubes, SQL Server Analysis Services. SQL Server Analysis Services must be deployed in Multidimensional mode.
  
> [!NOTE]
> If you are installing Project Server 2013 to an existing SharePoint Server 2013 farm, some of these steps may already be completed. 
  
Complete the procedures in each section below:
  
- [Configure SQL Server network settings](#section1)
    
- [Configure Analysis Services for building Project Server OLAP cubes](#section4)
    
Additionally, depending on the needs of your organization, you may want to do the following:
  
- Create a Project Web App database
    
- Create additional TempDB files
    
We also recommend that you start the SQLSERVERAGENT service on the instance of SQL Server where your SharePoint Server databases are located. SharePoint Server and Project Server 2013 use the SQL Server Agent service to perform various database cleanup activities.
  
When you have finished configuring SQL Server and Analysis Services, go to the next article, [Install SharePoint Server 2013 (Project Server 2013)](install-sharepoint-server-2013-project-server-2013.md).
  
## Configure SQL Server network settings
<a name="section1"> </a>

For SharePoint Server and Project Server to work correctly, the associated instance of SQL Server must be configured to enable remote connections using TCP/IP. Use the following procedure to confirm that your instance of SQL Server is configured to allow remote TCP/IP connections.
  
### To configure SQL Server 2008 R2 or SQL Server 2012 network settings

1. Click **Start**, click **All Programs**, click **Microsoft SQL Server 2008 R2** or **Microsoft SQL Server 2012**, click **Configuration Tools**, and then click **SQL Server Configuration Manager**.
    
2. In the left pane, expand **SQL Server Network Configuration**, and then select the instance of SQL Server where you will be installing Project Server 2013 databases.
    
3. In the right pane, ensure the Status for TCP/IP is Enabled.
    
## Configure Analysis Services for building Project Server OLAP cubes
<a name="section4"> </a>

Project Server 2013 can build OLAP cubes in SQL Server Analysis Services (SSAS) for use in reporting. If you plan to use the Project Server 2013 cube building feature, you must configure the Farm Administrator account to have administrative permissions in SQL Server Analysis Services for the instance of Analysis Services that you will be using with Project Server 2013.
  
### To add the Farm Administrator as an Analysis Services server administrator

1. Open SQL Server Management Studio. In the **Connect to Server** window, connect to the instance of Analysis Services that you are using with Project Server 2013.
    
2. In SQL Server Management Studio, in Object Explorer, right-click your Analysis Services instance name, and then click **Properties**.
    
3. On the Analysis Services Properties page, in the **Select a page** pane, click **Security**.
    
4. Click **Add**.
    
5. On the Select Users, Computers, or Groups page, type the name of the Farm Administrator account.
    
6. Click **OK**. The Farm Administrator account appears in the Members list.
    
7. Click **OK**.
    
> [!NOTE]
> For information about configuring user access for OLAP cubes, see [Configure OLAP cubes for Project Web App](configure-olap-cubes-for-project-web-app.md). For information about managing OLAP databases in Project Server 2013, see [OLAP database management in Project Web App](olap-database-management-in-project-web-app.md). 
  
## Create additional TempDB files
<a name="section4"> </a>

Both Project Server 2013 and SharePoint Server 2013 make extensive use of TempDB during SQL transactions. To optimize performance, create additional TempDB files.
  
As a rule, create an additional TempDB file for each processor (core) in the computer that is running SQL Server. Create the files on a separate partition from other database files.
  
## Project Server forums and documentation feedback
<a name="section4"> </a>

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also
<a name="section4"> </a>

#### 

[Install SharePoint Server 2016 (Project Server 2016)](install-sharepoint-server-2016-project-server-2016.md)

