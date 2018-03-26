---
title: "Resource Capacity Settings (Project Server 2013 settings)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 6fdff6fe-13d9-44ce-823f-8767cf0c164e
description: "Summary: Use the Resource Capacity Settings in Central Administration to help you calculate resource availability in Project Server 2013."
---

# Resource Capacity Settings (Project Server 2013 settings)
 
 **Summary:** Use the Resource Capacity Settings in Central Administration to help you calculate resource availability in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
The **Resource Capacity Settings** are a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Resource Capacity Settings

Resource Capacity Settings are used to calculate your resources' availability for work over a specified time range. Your resources' capacity data for the specified time range is stored on the Reporting database, and it is updated daily through a processing job that is run at a time that you specify in the settings. You are able to set the Active capacity view by entering a time range in relative terms — months in the past, and months in the future — where the current date is a relative starting point. You can view your resources' availability for work through the Resource Center in Project Web App.
  
The default **Active capacity view** settings are "1" month behind and "12" months ahead. This means that in the Resource Center you can view a resource's future availability for up to 12 months from the current date, and you can view utilization over the last month. By increasing the **Month ahead** setting, you get more capacity computed for future periods. For example, imagine that a company plans for new projects later in the year and wants to forecast the capacity for resources from 12 months to 24 months. Some customers might want to increase the **Months behind** value to get an accurate report of work completed in the past (for example, to account for any users who might report time long after the work is completed).
  
Note that increasing either value also increases the time it takes for the daily processing job to run.
  
### To configure Resource Capacity Settings

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Resource Capacity settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Resource Capacity settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
6. On the Additional Server Settings page, in the **Resource Capacity Settings** section, for **Active capacity view**, enter the following:
    
1. In the **Months behind** field, enter the number of months in the past that you want resource data to be calculated from.
    
2. In the **Months ahead** field, enter the number of months in the future that you want resource data to be calculated from.
    
7. Click **Save**.
    
Resource Capacity information will be processed daily at 1:00 AM by default.
  
## See also

#### 

[Additional Server Settings (Project Server 2013 settings)](additional-server-settings-project-server-2013-settings.md)

