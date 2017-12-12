---
title: "Currency Settings (Project Server 2013 settings)"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 12/1/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: a00072bd-2cb1-4156-a674-8966ad1c2adf
description: "Summary: Use the Currency Settings in Project Server 2013 to set the default currency for projects."
---

# Currency Settings (Project Server 2013 settings)
 
 **Summary:** Use the Currency Settings in Project Server 2013 to set the default currency for projects.
  
The **Currency Settings** are part of the Additional Server Settings in the **Operational Policies** section of Project Server 2013 Server Settings. In Project Server 2013, these setting are available in SharePoint Central Administration. To access and configure this setting, you must be a farm administrator.
  
## Currency Settings

Through the currency setting, you can select the default currency setting for projects that are published to the server. (This is used for reports and the default view for new projects.) The default value is based on the default currency of the language that is used for the Project Web App instance. 
  
You can also select the currency settings for publishing:
  
- **Allow projects to be published in various currencies** Select this option if your organization uses multiple currencies for costs within projects. (This is the default setting).
    
- **Enforce that projects are published in the server currency** Select this option if your organization only uses a single currency for costs within projects. The currency that is used is the one selected as the default server currency.
    
### To configure the Currency Settings

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Project Professional Versions setting.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Project Professional Versions setting, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Additional Server Settings**.
    
6. On the Additional Server Settings page, in the **Currency Settings** section, select one of the following currency options:
    
  - **Allow projects to be published in various currencies** (Selected by default).
    
  - **Enforce that projects are published in the server currency**
    
    If you select **Enforce that projects are published in the server currency**, you see a message. This message box warns you that the change is only be enforced on all successive projects that are published to the server. All projects that are not using the default server currency must be changed to the default currency and republished. 
    
7. Click **OK**.
    
    All projects published to the server that are using a currency that conflicts with the server currency will be displayed in the Currency Settings section of the page in the **Project in conflict with the server currency** list. You can use this as a reference to note which projects have to have their currency changed to the server currency.
    
8. Click **Save**.
    
### Change currency option for a project

Use the following procedure in Project Professional 2013 to change the currency settings for a project. You can use this procedure to do the following:
  
- Select the currency for a specific project if the currency setting lets you use multiple currencies.
    
- Change the currency setting on a project to the server currency if the currency setting only lets you use the server currency.
    
### To change the currency for a project in Project Professional 2013

1. Open Project Professional 2013 and log on to Project Server 2013.
    
2. Check out and open a project from Project Server 2013.
    
3. Click **File**, and then click **Options**.
    
4. On the Project Options page, click **Display**.
    
5. On the Display page, in the **Currency options for this project** section, select the currency and then the currency format (symbol, placement, and decimal digits) that you want to use for this project.
    
6. Click **OK**.
    
7. Click **File**, and then click **Save** to save the project.
    
8. Click **File**, and then click **Publish** to publish the project.
    
## See also

#### 

[Additional Server Settings (Project Server 2013 settings)](additional-server-settings-project-server-2013-settings.md)

