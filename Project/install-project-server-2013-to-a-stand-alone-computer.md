---
title: Install Project Server 2013 to a stand-alone computer
ms.author: jenz
author: jenzamora
manager: jtremper
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.assetid: f5e0717d-e473-4371-9e94-994eb84f7913
description: Summary - Set up a simple Project Server 2013 installation for demonstration purposes.
ms.date: 12/04/2017
---

# Install Project Server 2013 to a stand-alone computer
 
 **Summary:** Set up a simple Project Server 2013 installation for demonstration purposes.<br/>
**Applies to:** Project Server 2013
  
Project Server 2013 can be installed in a stand-alone configuration that uses SQL Server 2008 R2 Express Edition with SP1. This configuration is useful for demonstration, but should not be used for a production environment.

The stand-alone configuration has fewer features than a full farm installation. SQL Server Analysis Services (SSAS) and OLAP are not present in the stand-alone configurations. (Analysis Services and OLAP functionality can be configured to use a different instance of SQL Server if you want.)

> [!IMPORTANT]
> We recommend installing the standalone configuration on a computer that has at least 24GB of RAM. 

To install Project Server 2013 in stand-alone mode, you must first install SharePoint Server 2013 in stand-alone mode. This includes installing the prerequisites for SharePoint Server 2013.


## To install SharePoint Server 2013 prerequisites

1. On the SharePoint Server 2013 DVD, run **default.hta**.
2. On the SharePoint Server 2013 first page, click **Install software prerequisites**.
3. Follow the wizard to complete the installation.</br>
   NOTE - Depending on your configuration, you may have to restart your computer during this process.
4. When the wizard has finished, click **Finish**.
5. After you complete the Microsoft SharePoint Products Preparation Tool, you must also install the following hotfixes:
    - [KB 2554876](https://go.microsoft.com/fwlink/p/?LinkId=254221)
    - [KB 2708075](https://go.microsoft.com/fwlink/p/?LinkID=254222)
    - KB 2759112
    - KB 2765317

Once the software prerequisites have been installed, restart the computer before installing SharePoint Server 2013.

After you have restarted the computer, use the following procedure to install SharePoint Server 2013 in stand-alone mode. 

## To install SharePoint Server 2013

1. On the SharePoint Server 2013 DVD, run **default.hta**.
2. ON the SharePoint Server 2013 first page, click **Install SharePoint Server**.
3. On the **Enter your Product Key** page, type your product key, and then click **Continue**.
4. On the **Read the Microsoft Software License Terms** page, read the license agreement and accept the terms by selecting the **I accept the terms of this agreement** check box.
5. Click **Continue**.
6. On the Choose the installation you want page, select the Stand-alone option, and then click **Install Now**.  SharePoint Server 2013 will install.
7. When the installation is complete, click **Close**.  The SharePoint Products Configuration Wizard starts.
8. On the **Welcome to SharePoint Products** page, click **Next**.
9. On the warning dialog box, click **Yes**.
10. On the **Configuration Successful** page, click **Finish**.
11. On the **Template Selection** page, select one of the following options, and then click **OK**:
    - In the **Template Selection** section, click a predefined template.
    - In the **Solutions Gallery** section, click **Solutions Gallery**, and customize your own site template.
12. On the **Set Up Groups for this Site** page, specify who should have access to your site, and then either create a new group or use an existing group for these users by doing one of the following: 
    - To create a new group, click **Create a new group**, and then type the name of the group and the members that you want to be part of this group.
    - To use an existing group, click **Use an existing group**, and then select the user group in the **Item** list.
13. Click **OK**.
 
Once SharePoint Server 2013 is installed, the next step is to install Project Server 2013 and run the SharePoint Products Configuration Wizard.

## To install Project Server 2013

1. On the SharePoint Server 2013 DVD, run **default.hta**.  The Setup menu opens.
   > [!NOTE]
   > default.hta may run automatically when you insert the disk.
2. On the Start page, click **Install Project Server**.
3. On the **Enter your Product Key** page, type your product key, and then click **Continue**.
4. In the **End User License Agreement** page, review the terms of the agreement. To accept the agreement, select the **I accept the terms of this agreement** check box.
5. Click **Continue**.
6. On the **Choose a file location** page, click **Install Now**.
7. When the installation is complete, click **Close**. The SharePoint Products Configuration Wizard starts.
8. On the **Welcome to SharePoint Products** page, click **Next**.
9. On the warning dialog box, click **Yes**.
10. On the **Configuration Successful** page, click **Finish**.
 
    When the SharePoint Products Configuration Wizard finishes, the system will automatically create a PWA site. This may take several minutes. When the site has been created, it can be accessed at https://\<servername>/pwa.

> [!NOTE]
> The account that you used to install Project Server is automatically added to the Project Server Administrators group.

## See also


[Install SharePoint 2013 on a single server with a built-in database](/SharePoint/install/single-server-with-a-built-in-database)
  
[Deploy Project Server 2013 to a server farm environment](deploy-project-server-2013-to-a-server-farm-environment.md)

[Hardware and software requirements for Project Server 2013](hardware-and-software-requirements-for-project-server-2013.md)
