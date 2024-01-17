---
title: "Bulk Update Project Sites (Project Server 2013 settings)"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/16/2014
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: f7887c71-2339-4584-987e-23db26cd5b04
description: "Summary: Use the Bulk Update Project Sites settings in SharePoint Central Administration to change site path information for project sites in Project Server 2013."
---

# Bulk Update Project Sites (Project Server 2013 settings)
 
 **Summary:** Use the Bulk Update Project Sites settings in SharePoint Central Administration to change site path information for project sites in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
  
 **Bulk Update Project Sites** are part of the Operational Policies section of Project Server 2016 Server Settings. In Project Server 2016, these settings are available in SharePoint Central Administration. To access this setting, you must be a farm administrator.
  
## Configure the Bulk Update Project Sites Setting

The Bulk Update Project Sites page allows you to change site path information for project sites in one Web application to a different one (for example, when migrating). It allows you to break the original links between projects and their corresponding project sites in one site collection and then relink to the new project sites in the new site collection.
  
- [Update Site Paths](#section1)
    
- [Update Content Types](#section2)
    
- [Project Site Permissions](#section3)
    
### Update Site Paths
<a name="section1"> </a>

The **Update Site Paths** setting lets you break links between projects and project sites that are contained in one site collection and relink with the new project sites in a different site collection.
  
### To update project site paths to a new site collection

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Bulk Update Project Sites settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Bulk Update Project Sites settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Bulk Update Project Sites**.
    
6. On the Bulk Update Project Sites page, in the **Update Site Paths** section, for **Previous Site Path**:
    
1. Select the Web application for your project sites that you want to break the link to. If you are migrating project sites on the same server, the Web application that you need to select may appear as a URL. If you are migrating projects sites from a different server, the Web application you need to select may appear as a globally unique identifier (GUID).
    
2. In the **Site URL** field, type the site URL information (for example, PWA).
    
7. For **New Site Path**:
    
1. Select the Web application that contains the project sites that you want to link to (for example, https://hr1.contoso.com).
    
2. In the **Site URL** field, type the site URL information (for example, PWA).
    
8. Click **Save**.
    
### Update Content Types
<a name="section2"> </a>

The **Update Content Types** setting allows you to ensure that when you migrate content from one farm to another, the content types of Project Issues, Risks, and Documents are updated in the new location so that item links remain functional.
  
### To enable the Update Content Types setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Bulk Update Project Sites settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Bulk Update Project Sites settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Bulk Update Project Sites**.
    
6. On the Bulk Update Project Sites page, in the **Update Content Types** section, select **Update Content Types**.
    
7. Click **Save**.
    
### Project Site Permissions
<a name="section3"> </a>

The **Project Site Permissions** setting allows you to synchronize permissions to the Project Sites while updating the site paths. This allows users to immediately access their project sites.
  
> [!NOTE]
> For the Project Site Permissions setting to be enabled, the Project Site Permissions setting must also be enabled on the Project Site Provisioning page. 
  
### To enable the Synchronize site permissions setting

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Bulk Update Project Sites settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Bulk Update Project Sites settings, and click **Manage**.
    
5. On the Server Settings page, in the **Operational Policies** section, click **Bulk Update Project Sites**.
    
6. On the Bulk Update Project Sites page, in the **Project Site Permissions** section, click **Synchronize site permissions**.
    
7. Click **Save**.
    
## See also

[Operational Policies (Project Server 2013)](./project-server-2013-and-2016.md)