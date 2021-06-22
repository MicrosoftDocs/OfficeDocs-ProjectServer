---
title: "Resource Plan Work Day (Project Server 2013 settings)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 2c8989cd-6d94-49ec-b88b-6c763036f43e
description: "Summary: Use the Resource Plan Work Day settings in Central Administration to set full-time equivalency for resources in Project Server 2013."
---

# Resource Plan Work Day (Project Server 2013 settings)
 
 **Summary:** Use the Resource Plan Work Day settings in Central Administration to set full-time equivalency for resources in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Resource Plan Work Day** is a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Resource Plan Work Day

 **Resource Plan Work Day** lets you specify the length of a work day ("full-time equivalents" or FTE) for all resources in your resource plan. This value can be calculated from the resource's base calendar or can be manually entered as a value.
  
### To configure the Resource Plan Work Day setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Resource Plan Work Day setting.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Resource Plan Work Day setting, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
6. On the Additional Server Settings page, in the Resource Plan Work Day section, for **Calculate resource full-time equivalent from**, select one of the two options:
    
   - **Resource base calendars** Use this option if you want the full-time equivalents to be calculated from each resources base calendar. This is the default option.
    
   - **Hours per day** Use this option if you want to specify the full-time equivalents for your resources in the resource plan. After selecting this option, enter the value (in hours) of the standard work day for your organization. Note that this value is used for all resources in the resource plan.
    
7. Click **Save**.
    
## See also

#### 

[Additional Server Settings (Project Server 2013 settings)](additional-server-settings-project-server-2013-settings.md)

