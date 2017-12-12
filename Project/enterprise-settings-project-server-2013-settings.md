---
title: "Enterprise Settings (Project Server 2013 settings)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 111f7f1a-60f5-450c-910a-e99a03485cf3
description: "Summary: Learn to use the Enterprise Settings options in SharePoint Central Administration to provide additional flexibility for your Project Server 2013 projects."
---

# Enterprise Settings (Project Server 2013 settings)
 
 **Summary:** Learn to use the Enterprise Settings options in SharePoint Central Administration to provide additional flexibility for your Project Server 2013 projects.
  
 **Enterprise Settings** options are a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Enterprise Settings

 Enterprise Settings lets you determine whether Project Server 2013 allows for projects to have the following capabilities:
  
- **Allow master projects to be saved and published** (By default, this option is enabled.) Enabling this setting enables master projects to be used in Project Server 2013. Master projects are projects that contain sub-projects, and they usually contain tasks that are dependent on one another. Check with your Project Management Office to determine whether your organization prohibits the use of master projects.
    
- **Allow projects to use local base calendars** Enabling this settings lets users not only use enterprise base calendars that are on the system for their enterprise projects, but to also use local base calendars that users create. Having this setting disabled (which is the default) restricts users to using only enterprise base calendars that are on the system for their projects. Restricting the users to enterprise calendars gives you more control by preventing problems that can occur when projects use local base calendars that contain conflicting data. For example, a project that uses a local base calendar that differs from an enterprise calendar (for example, July 4 as a work day versus a holiday) can lead to faulty calculations and other issues.
    
### To configure the Enterprise Settings

1. In SharePoint Central Administration, click **Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Enterprise Settings options.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Enterprise Settings options, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
6. On the Additional Server Settings page, in the **Enterprise Settings** section:
    
1. Select **Allow master projects to be saved and published to Microsoft Project Server 2010** if you want to enable this setting. (By default, it is enabled.)
    
2. Select **Allow projects to use local base calendars** if you want to enable this setting (By default, this option is cleared.)
    
7. Click **Save**.
    

