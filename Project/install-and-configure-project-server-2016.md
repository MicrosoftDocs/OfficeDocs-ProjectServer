---
title: "Install and configure Project Server 2016"
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
ms.assetid: 54bd9a14-ede6-445e-9b44-a03798b6d1b0
description: "Summary: Configure Project Server 2016 on a SharePoint Server 2016 farm."
---

# Install and configure Project Server 2016
 
 **Summary:** Configure Project Server 2016 on a SharePoint Server 2016 farm.<br/>
**Applies to:** Project Server 2016
  
Project Server 2016 runs as a service application under SharePoint Server 2016. It is included as part of the SharePoint Server 2016 Enterprise installation, though it is licensed separately. This article describes configuring Project Server 2016, including provisioning the Project Server Service Application. Project Server 2016 is only available on SharePoint Server 2016 Enterprise.
  
Be sure you have [installed SharePoint Server 2016](http://technet.microsoft.com/library/8a911115-de8a-4cf3-9701-f5ba78fa8bfc%28Office.14%29.aspx) before starting the procedures in this article. Also, be sure that the State Service is running on your SharePoint farm.
  
## Configure Project Server 2016

Project Server 2016 requires a license in order to operate, and you must enable Project Server 2016 by using your license key before you can create a Project Web App site. 
  
(If you're not sure if Project Server 2016 has already been enabled, use the Get-ProjectServerLicense cmdlet to check.)
  
### To activate Project Server 2016

1. Open the SharePoint 2016 Management Shell as Administrator.
    
2. Type the following to enable Project Server 2016:
    
  ```
  Enable-ProjectServerLicense -Key <LicenseKey>
  ```

 **Creating a service application**
  
Project Server 2016 runs as a service application in SharePoint Server 2016, so the first thing to do is check to see if you already have a Project Server Service Application configured.
  
### Check for a Project Server Service Application

1. In the SharePoint Central Administration website, under **Application Management**, click **Manage service applications**.
    
2. Check the service applications list for a Project Server Service Application.
    
If you already have a Project Server Service Application, you can go ahead and [configure a Project Web App site](deploy-project-web-app.md). Otherwise, the first step in creating a Project Server Service Application is to register a managed account. For this, you'll need a domain account that you can use to run the application pool for the Project Server Service Application.
  
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

