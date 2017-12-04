---
title: "Add an application server to a farm in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/21/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: ab894aca-5ae4-48af-8109-2cedb3f96df0
description: "Summary: Add a new SharePoint Server 2013 application server with Project Server 2013 to an existing farm."
---

# Add an application server to a farm in Project Server 2013
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** Add a new SharePoint Server 2013 application server with Project Server 2013 to an existing farm.
  
To add a Project Server 2013 application server to an existing farm, you must do the following:
  
- Install SharePoint Server 2013 prerequisites
    
- Install SharePoint Server 2013
    
- Install Project Server 2013
    
- Install required updates
    
- Add the server to the farm by running the SharePoint Products and Technologies Configuration Wizard
    
## Video demonstration

This video shows the steps involved in adding an application server to an existing Project Server 2013 farm, as described in this article.
  
**Video: Add an application server to a Project Server farm**

![Video (play button) icon](images/mod_icon_video_M.png)
  
## Configure the application server

Use the following procedures to configure the application server and add it to the farm.
  
> [!NOTE]
> For these procedures, we recommend that you use the Farm Install account that you originally created to install SharePoint Server 2013. 
  
### To install prerequisites for SharePoint Server 2013 Preview

1. On the SharePoint Server DVD, run default.hta.
    
2. Click **Install software prerequisites**.
    
    > [!NOTE]
    > You must be connected to the Internet to perform this step. If you are not connected to the Internet, you must install the prerequisites manually. 
  
3. On the Welcome page, click **Next**.
    
4. Read the license agreement, and if you accept, then select the **I accept the terms of the License Agreement(s)** check box.
    
5. Click **Next**.
    
    > [!NOTE]
    > Depending on your configuration, you may be required to restart the server during this process. 
  
Once the prerequisites have been installed, the next step is to install SharePoint Server 2013.
  
### To install SharePoint Server 2013 Preview

1. On the SharePoint Server DVD, run default.hta.
    
2. Click **Install SharePoint Server**.
    
3. On the Enter your Product Key page, type your product key, and then click **Continue**.
    
4. Read the license agreement, and if you accept, then select the **I accept the terms of this agreement** check box, and then click **Continue**.
    
5. On the Choose the installation you want page, click **Server Farm**.
    
6. On the Server type page, click **Complete**.
    
7. If desired, select the **File Location** tab and change the installation location.
    
8. Click **Install Now**.
    
9. When installation has finished, clear the **Run the SharePoint Products and Technologies Configuration Wizard now** check box, and then click **Close**.
    
Once SharePoint Server 2013 has been installed, the next step is to install Project Server 2013.
  
### To install Project Server 2013 Preview

1. On the Project Server DVD, run default.hta.
    
2. Click **Install Project Server**.
    
3. On the Enter your Product Key page, type your product key, and then click **Continue**.
    
4. Read the license agreement, and if you accept, then select the **I accept the terms of this agreement** check box.
    
5. Click **Continue**.
    
6. On the Choose a file location page, click **Install Now**.
    
7. When installation has finished, clear the **Run the SharePoint Products and Technologies Configuration Wizard now** check box, and then click **Close**.
    
Once SharePoint Server 2013 and Project Server 2013 are installed on the computer, you must install any required updates so that the updates on the new application server match those currently on the farm. Note that this includes Project Server 2013 and SharePoint Server 2013 updates (such as service packs and cumulative updates), but does not include updates for other products, such as Windows Server or SQL Server.
  
### To add the server to the farm

1. Click **Start**, **All Programs**, **Microsoft SharePoint 2013 Products**, **SharePoint 2013 Products Configuration Wizard**.
    
2. On the Welcome page, click **Next**.
    
3. On the warning dialog box, click **Yes**.
    
4. On the Connect to a server farm page, select the **Connect to an existing server farm** option.
    
5. Click **Next**.
    
6. On the Specify Configuration Database Settings page, type the name of the instance of SQL Server where the SharePoint Server 2013 configuration database is located, and then click **Retrieve Database Names**.
    
7. Select the configuration database for the farm you want to join from the **Database name** drop-down box, and then click **Next**.
    
8. On the Specify Farm Security Settings page, type the farm pass phrase, and then click **Next**.
    
9. On the Completing the SharePoint Products Configuration Wizard page, click **Next**.
    
10. When the wizard has finished, click **Finish**.
    
## See also

#### 

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

