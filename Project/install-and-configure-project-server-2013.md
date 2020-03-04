---
title: "Install and configure Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 6a279309-9a6f-4b46-b56f-076b59403345
description: "Summary: Install Project Server 2013 on a SharePoint Server 2013 farm and create a Project Server service application."
---

# Install and configure Project Server 2013
 
 **Summary:** Install Project Server 2013 on a SharePoint Server 2013 farm and create a Project Server service application.<br/>
**Applies to:** Project Server 2013
  
Project Server 2013 runs as a service application under SharePoint Server 2013. This article describes installing and configuring Project Server 2013, including provisioning the Project Server Service Application.
  
Use the procedures that follow to install Project Server 2013. The Project Server 2013 software must be installed on each application server in the farm before you can run the SharePoint Products Configuration Wizard to integrate Project Server with SharePoint Server 2013. 
    
> [!IMPORTANT]
> If you plan to use workflows with Project Server, you must install and configure the SharePoint 2013 Workflow platform in SharePoint Server 2013. For more information, see [Installing and configuring workflow for SharePoint Server 2013](https://technet.microsoft.com/library/b37c1d36-5bfe-4f76-bb03-2c5436c043a2.aspx) and the[Workflow in SharePoint 2013 resource center](https://technet.microsoft.com/sharepoint/jj556245.aspx). 
  
> [!IMPORTANT]
> After you install Project Server 2013, it cannot be uninstalled from the farm. If you want to remove Project Server 2013 functionality, you can turn off the Project Application Service and delete the Project Server 2013 Service Application. 
  
## Video demonstration

This video shows the steps involved in installing Project Server 2013 and configuring a Project Server 2013 service application, as described in this article.
  
**Video: Install and configure Project Server 2013**

![Video (play button) icon](images/mod_icon_video_M.png)
  
## Install and configure Project Server 2013

This section describes how to install Project Server 2013. The basic procedure is as follows:
  
- Install Project Server 2013 on each application server and Web server in the farm
    
- Run the SharePoint Products Configuration Wizard
    
- Refresh the installed products on the farm
    
> [!NOTE]
> If you encounter an error during the installation process, check the log files that are located at \\Program Files\\Common Files\\Microsoft shared\\Web server extensions\\15\\logs and consult the [Project Forums](https://go.microsoft.com/fwlink/p/?LinkId=169001) (https://go.microsoft.com/fwlink/p/?LinkId=169001).
  
Complete the following procedure on each application server in the farm.
  
### To install Project Server 2013

1. On the Project Server 2013 DVD, run default.hta. The Setup menu appears.
    
    > [!NOTE]
    > Default.hta may run automatically when you insert the disk. 
  
2. On the Start page, click **Install Project Server**.
    
3. On the Enter your Product Key page, type your product key, and then click **Continue**.
    
4. In the End User License Agreement page, review the terms of the agreement. To accept the agreement, select the **I accept the terms of this agreement** check box.
    
5. Click **Continue**.
    
6. On the Choose a file location page, click **Install Now**.
    
7. When the installation is complete, clear the **Run the SharePoint Products and Technologies Configuration Wizard now** check box.
    
8. Click **Close**.
    
After the Project Server 2013 software has been installed on each web server and application server in the farm, you must run the SharePoint Products Configuration Wizard to integrate Project Server with SharePoint Server 2013. You must run this wizard on each web server and application server in the farm before you can start using Project Server.
  
Complete the following procedure on each web server and application server in the farm.
  
> [!NOTE]
> Run the SharePoint Products Configuration Wizard on one server at a time. Do not run it on multiple servers at the same time. 
  
### To run the SharePoint Products and Technologies Configuration Wizard

1. Click **Start**, **All Programs**, **Microsoft SharePoint 2013 Products**, **SharePoint 2013 Products Configuration Wizard**.
    
2. At the Welcome to SharePoint Products and Technologies page, click **Next**.
    
3. A confirmation dialog message appears that displays a list of services that may have to be restarted. Click **Yes**.
    
4. On the Modify server farm Settings page, select the **Do not disconnect from this server farm option**, and then click **Next**.
    
    > [!NOTE]
    > Depending on your configuration, this option may not appear. 
  
5. If the server is hosting the SharePoint Central Administration website, the Modify SharePoint Central Administration Web Application Settings page appears. Select the **No, this machine will continue to host the web site** option, and then click **Next**.
    
    > [!NOTE]
    > Depending on your configuration, this option may not appear. 
  
6. On the Completing the SharePoint Products Configuration Wizard page, click **Next**.
    
7. On the Configuration Successful page, click **Finish**.
    
## Configure services

After Project Server 2013 is installed, the following configuration steps are required before creating a Project Web App site and using Project Server:
  
- Start the Project Server Application Service
    
- Create a Project Server service application
    
Before you create a Project Server service application, you must start the Project Server Application Service on at least one application server in the farm.
  
### To start the Project Server Application Service

1. On the Central Administration home page, in the **System Settings** section, click **Manage services on server**.
    
2. On the Services on Server page, select the server where you want to run the Project Application Service from the **Server** drop-down list.
    
3. On the **Service** list, click **Start** next to **Project Server Application Service**.
    
After you have started the Project Server service on the desired application servers in the farm, you must create a Project Server service application.
  
> [!NOTE]
> While you can create more than one Project Server service application, doing so consumes additional system resources. We recommend that you create only one Project Server service application. A single service application supports multiple instances of Project Web App. 
  
The account that you plan to use for the application pool for the Project Server service application must be a registered account in SharePoint Server. If you have not already registered this account in SharePoint Server, use the following procedure to do so.
  
### To register a managed account

1. On the Central Administration home page, in the left navigation, click **Security**.
    
2. On the Security page, in the **General Security** section, click **Configure managed accounts**.
    
3. On the Managed Accounts page, click **Register Managed Account**.
    
4. Type the user name and password of the domain account that you are registering.
    
5. Optionally, select the **Enable automatic password change** check box if you want SharePoint Server to manage password changes for this account.
    
6. Click **OK**.
    
After the application pool account has been registered with SharePoint Server, the next step is to create the Project Server service application. Use the following procedure to create the service application.
  
### To create a Project Server service application

1. On the Central Administration home page, in the **Application Management** section, click **Manage service applications**.
    
2. On the Manage Service Applications page, on the ribbon, click **New**, and then click **Project Server Service Application**.
    
3. On the Create Project Web App service application page:
    
1. Type a name for the service application in the **Project Web App service application name** box.
    
2. In the **Application Pool** section, type the name of the application pool you want to create in the **Application pool name** box.
    
3. Select the **Configurable** option, and choose the managed account that you want to use to run the application pool.
    
4. Click **OK**.
    
The next step is to determine how you want to deploy Project Web App. Go to the next article, [Deploy Project Web App](deploy-project-web-app.md).
  
## See also

#### 

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

