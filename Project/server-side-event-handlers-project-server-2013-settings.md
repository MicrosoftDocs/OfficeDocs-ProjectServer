---
title: "Server Side Event Handlers (Project Server 2013 settings)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 5bba1a62-424d-4369-bade-d9b042e84d62
description: "Summary: Use the Server Side Event Handler page in SharePoint Central Administration to associate event handlers with Project Server 2013 server side events."
---

# Server Side Event Handlers (Project Server 2013 settings)
 
 **Summary:** Use the Server Side Event Handler page in SharePoint Central Administration to associate event handlers with Project Server 2013 server side events.
  
The **Server Side Event Handler** settings are available through the Project Server 2013 Server Settings page in the **Operational Policies** section. In Project Server 2013, these settings are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Configure Server Side Event Handlers

Project Server 2013 provides public events that enable development of custom processes such as adding and enforcing business rules, validation, data processing, notification services, and workflow. These custom processes are written as server-side event handlers by developers in an organization and can be associated to Project Server 2013 events through the Server Side Event Handlers page in Project Web App Server Settings. For example, developers in your organization can create an event handler that starts a custom workflow. Through the Server Side Event Handlers page, you can associate that event handler with the Project Published event so that a workflow starts when the event occurs.
  
For more information about Project Server event handlers, see the MSDN article, [How to: Create a Project Server Event Handler and Log an Event](https://msdn.microsoft.com/en-us/library/gg615466.aspx)
  
### To associate an event handler with a server-side event

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Server Side Event handler settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Server Side Event handler settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Server Side Event Handlers**.
    
6. On the Server Side Event Handlers page, in the **Events** list, find the event that you want to associate your new event handler with, and then click the **Event Source** listed next to the **Event Name** (for example, click the **Project** event source for the **Published** event name).
    
    In the **Event Handlers** section, the **Event Source** and **Event Name** should be populated with the event that you selected. Any event handlers that are currently associated with the event appear in the **Event Handlers** list.
    
7. Click **New Event Handler**. 
    
8. In the New Event Handler page, enter the following information for the event handler that you want to associate with the selected event:
    
1. In the **Display Information** section, enter the event handler name. You can also optionally enter a description of the event handler.
    
2. In the **System Information** section, in the **Assembly Name** field, enter the full name of the strongly named event handler assembly. For example:
    
  ```
  TestCreatingProject, Version=1.0.0.0, Culture=neutral, PublicKeyToken=92978aaaab03ff98

  ```

3. In the **Class Name** field, enter the fully qualified name of the class that implements the event handler functionality. For example: Microsoft.SDK.Project.Samples.TestCreatingProject.CheckProjectDepartment.
    
4. In the **Order** field, provide the order number of the event handler. If it is the only event handler associated with the event, enter1. If there are multiple event handlers associated with the event, enter the order number in which this event handler will be executed. 
    
9. In the **Endpoint URL** field, enter the Windows Communication Foundation (WCF) Endpoint URL. If you are adding a legacy on-premises event handler, you can leave this field blank.
    
10. Click **Save**.
    

