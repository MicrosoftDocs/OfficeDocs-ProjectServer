---
title: "Project Professional Versions (Project Server 2013 settings)"
ms.author: efrene
author: efrene
ms.prod: scotv
ms.date: 12/01/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 4b04ada0-efbd-4fb2-a690-0ced8dd2a32d
description: "Summary: Use the Project Professional Versions setting to define which builds of Project Professional 2013 can connect to Project Server 2013."
---

# Project Professional Versions (Project Server 2013 settings)
 
 **Summary:** Use the Project Professional Versions setting to define which builds of Project Professional 2013 can connect to Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Project Professional Versions** is a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Project Professional Versions

 **Project Professional Versions** lets you specify which versions (build numbers) of the Project Professional client will be able to connect to your Project Server 2013 environment. This setting lets you ensure that Project Professional client connections to the server are all at a required base level. For example, if you recently updated both Project Server 2013 and Project Professional 2013 to the same cumulative update, you can verify that all clients that connect to the server are at least at this level by entering the build number. All Project Professional 2013 clients that have not been updated to the specified cumulative update or a newer version will be unable to connect.
  
> [!NOTE]
> Project Professional 2013 is the only Project Professional client that can connect to Project Server 2013. 
  
### To configure the Project Professional Versioning setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Project Professional Versions setting.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Project Professional Versions setting, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
6. On the Additional Server Settings page, in the **Project Professional Versions** section, type the build number of each Project Professional version that you want to connect to Project Server 2013. Use a comma as a separator between multiple version numbers.
    
    Versions older than the lowest build number that you enter will be unable to connect to your Project Server 2013 environment.
    
7. Click **Save**.
    
### To find your Project Professional 2013 build number

1. In Project Professional 2013, click the File tab.
    
2. On the left pane, click **Account**.
    
3. On the Account page, in the Product Information section, click **About Microsoft Project**.
    
4. On the About Microsoft Project page, the build number is located at the top of the page (for example, 15.0.4312.1000).
    

