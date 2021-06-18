---
title: "Install and configure Project Servers 2016 or 2019"
ms.author: serdars
author: serdars
manager: pamgreen
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 54bd9a14-ede6-445e-9b44-a03798b6d1b0
description: "Summary: Configure Project Servers 2016 or 2019 on a SharePoint Server farm."
---

# Install and configure Project Servers 2016 or 2019
 
 **Summary:** Configure Project Servers 2016 or 2019 or Subscription Edition on a SharePoint Server 2016 or SharePoint Server 2019 farm or SharePoint Server Subscription Edition farm.<br/>
**Applies to:** Project Server 2016, Project Server 2019, Project Server Subscription Edition
  
Project Server runs as a service application under SharePoint Server. It is included as part of the SharePoint Server 2016 or SharePoint Server 2019 or SharePoint Server Subscription Edition Enterprise installation, though it is licensed separately. This article describes configuring Project Servers 2016 or 2019 or Subscription Edition, including provisioning the Project Server Service Application. Project Servers 2016 or 2019 or Subscription Edition are only available on SharePoint Servers 2016 or 2019 or Subscription Edition Public Preview Enterprise.
  
Be sure you have [installed SharePoint Server 2016 or 2019 or Subscription Edition](/sharepoint/install/install-for-sharepoint-server-2016) before starting the procedures in this article. Also, be sure that the State Service is running on your SharePoint farm.
  
## Configure Project Servers 2016 or 2019 or Subscription Edition

Project Servers 2016 or 2019 or Subscription Edition requires a license in order to operate, and you must enable Project Servers 2016 or 2019 or Subscription Edition by using your license key before you can create a Project Web App site.

> [!NOTE]
> To enable the license key is only available by using a Microsoft Powershell cmdlet. 
  
If you're not sure if Project Server 2016 or 2019 or Subscription Edition has already been enabled, use the [Get-ProjectServerLicense](/powershell/module/sharepoint-server/get-projectserverlicense?view=sharepoint-ps) cmdlet to check.
  
### To activate Project Servers 2016 or 2019 or Subscription Edition

1. Open the SharePoint Management Shell as Administrator.

2. Verify that you have the following memberships:

    •securityadmin fixed server role on the SQL Server instance.
    
    •db_owner fixed database role on all databases that are to be updated.
    
    •Local Administrators group on the server on which you are running the PowerShell cmdlets.

    An administrator can use the [Add-SPShellAdmin](/powershell/module/sharepoint-server/Add-SPShellAdmin?view=sharepoint-ps) cmdlet to grant permissions to use Project Server cmdlets. 


    
3. From the PowerShell command prompt, type the following syntax to enable Project Server 2016 or 2019 or Subscription Edition:
    
   ```
   Enable-ProjectServerLicense -Key <LicenseKey>
   ```

### Check for a Project Server Service Application

Project Server runs as a service application in SharePoint Server, so the first thing to do is check to see if you already have a Project Server Service Application configured.

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