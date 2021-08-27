---
title: "Exchange Server Details (Project Server 2013 settings)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: a42377f2-5f83-41b7-a05b-df1db3b49411
description: "Summary: Use the Exchange Server Details setting in SharePoint Central Administration to enable or disable Microsoft Exchange Server integration with Project Server 2013."
---

# Exchange Server Details (Project Server 2013 settings)
 
 **Summary:** Use the Exchange Server Details setting in SharePoint Central Administration to enable or disable Microsoft Exchange Server integration with Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Exchange Server Details** is a part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration.
  
To access and configure this setting, you must be a farm administrator.
  
An additional requirement for this feature is that the Project queue is required to run under a mail-enabled user account.
  
## Exchange Server Details

The Exchange Server Details page allows you to enable or disable Microsoft Exchange Server integration with Project Server 2013. When enabled, it allows you to synchronize your resources out-of-office time between Exchange Server and Project Server 2013. This is done at an individual resource level in the resource properties page. 
  
Disabling the setting will disable Microsoft Exchange integration with Project Server. This setting is disabled by default.
  
### To configure the Exchange Server Details setting

1. In SharePoint Central Administration, click **General Application Settings**.
    
2. On the General Application Settings page, in the Project Web App settings section, click **Manage**.
    
3. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Project Professional Versions setting, and click **Manage**.
    
4. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
5. On the Additional Server Settings page, in the **Exchange Server Details** section, click **Synchronize Out of Office calendars** if you want to automatically synchronize out-of-office time in resource calendars between Project Server 2013 and Exchange Server 2007 with Service Pack 1, Exchange Server 2010, or Exchange Server 2013.
    
6. Click **Save**.
    
## See also

#### 

[Additional Server Settings (Project Server 2013 settings)](additional-server-settings-project-server-2013-settings.md)

