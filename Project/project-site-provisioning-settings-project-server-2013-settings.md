---
title: "Project Site Provisioning Settings (Project Server 2013 settings)"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 0bac34fa-d058-413c-a8ad-e0cec58d8946
description: "Summary: Use the Project Site Provisioning Settings in Central Administration to configure the automatic creation of project sites for projects in Project Server 2013."
---

# Project Site Provisioning Settings (Project Server 2013 settings)
 
 **Summary:** Use the Project Site Provisioning Settings in Central Administration to configure the automatic creation of project sites for projects in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Project Site Provisioning Settings** are part of the Operational Policies section of Project Server 2013 Server Settings. In Project Server 2013, these settings are available in SharePoint Central Administration. To access this setting, you must be a farm administrator.
  
## Configure Project Site Provisioning Settings

The Project Site Provisioning Settings page let you configure settings for the project sites that are created for projects. You can configure the following settings:
  
- [Site URL](project-site-provisioning-settings-project-server-2013-settings.md#section1)
    
- [Default Site Properties](project-site-provisioning-settings-project-server-2013-settings.md#section2)
    
- [Site creation settings](project-site-provisioning-settings-project-server-2013-settings.md#section3)
    
### Site URL
<a name="section1"> </a>

The **Site URL** settings let you set the default Web application in which your project sites are created. The default site URL information on this page is based on the information that is provided during the provisioning of the Project Web App instance.
  
### To specify site URL information

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Site Provisioning settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Site Provisioning settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Project Site Provisioning Settings**.
    
6. On the Project Site Provisioning Settings page, in the **Site URL** section, specify a default Web application that your project sites will be created from. Select the Web application from the **Default Web application** menu.
    
7. In the **Site URL** field, type the URL path (for example,PWA).
    
8. Select **Restrict Project site creation to the default site collection** if you only want project sites to be created in the site URL settings you specify.
    
9. Click **Save**.
    
### Default Site Properties
<a name="section2"> </a>

The **Default Site Properties** settings let you select the default site template language that will be used to create your project sites.
  
### To configure default site properties for your Project Sites

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Site Provisioning settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Site Provisioning settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Project Site Provisioning Settings**.
    
6. On the Project Site Provisioning Settings page, in the **Default Site Properties** section, select the default language for your project sites from the **Default site template language** drop-down list.
    
    > [!NOTE]
    >  The languages available to you in the Default site template language drop-down list are:>  The language of your base-installation of Project Server 2013.>  The language of any installed Project Server 2013 language packs.>  For example, if you install the Project Server 2013 Spanish language pack on a Project Server 2013 English base installation, you can choose English or Spanish from the Default site template language drop-down menu. Selecting one or the other will determine the default language the Project Web App user interface will display in for newly provisioned instances of Project Web App.
  
7. Click **Save**.
    
### Site creation settings
<a name="section3"> </a>

The **Site creation settings** lets you indicate whether you want to have Project Server 2013 create project sites for projects when the projects are newly published to the server. The settings can be configured to not create a project site. Additionally, you could provide users the option select either option.
  
> [!NOTE]
> If you choose not to create a site, you can create a site for your project later through the Project Sites page in the Project Web App Server Settings page. For more information, see [Manage connected SharePoint sites in Project Server 2013](manage-connected-sharepoint-sites-in-project-server-2013.md). 
  
### To configure the site creation setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Site Provisioning settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Site Provisioning settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Project Site Provisioning Settings**.
    
6. On the Project Site Provisioning Settings page, in the **Site creation settings** section, select one of the three **Provisioning mode** options:
    
   - **Automatically create a project site on first publish**
    
   - **Allow users to choose**
    
   - **Do not create a site**
    
7. Click **Save**.
    
    
## See also

[Manage connected SharePoint sites in Project Server 2013](manage-connected-sharepoint-sites-in-project-server-2013.md)

