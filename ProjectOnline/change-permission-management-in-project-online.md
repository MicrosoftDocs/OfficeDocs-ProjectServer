---
title: "Change permission management in Project Online"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 6/15/2018
ms.audience: End User
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
search.appverid:
- PJO150
- PJO160
ms.assetid: 3537c79a-1a5f-4b1e-9de0-c437673352c6
description: "Project Web App for Project Online offers two security management options for controlling the kind of access that users have to sites and projects: SharePoint Permission Management and Classic Permission Management. This article describes how to switch between these options."
---

# Change permission management in Project Online

 *[\< More Project help](project-help.md)* 
  
Project Online offers two security management options for controlling the kind of access that users have to sites and projects:
  
- **SharePointPermission Mode** With this option selected, a special set of SharePoint security groups are created in sites associated with Project Online. These groups are used to grant users varying levels of access to projects and Project Online functionality. 
    
    > [!TIP]
    > To learn more about the permissions included in the security groups used with SharePoint Permission Mode, see [SharePoint Permissions Mode default permissions for Project Server 2013 SharePoint groups](https://technet.microsoft.com/en-us/library/jj219510%28v=office.15%29.aspx). While this article is written with Project Server 2013 in mind, the information also applies to Project Online. 
  
- **Project Permission Mode** With this option selected, Project Online provides a set of customizable security groups and other functionality that is distinct from SharePoint groups. 
    
Project Online uses SharePoint Permission Mode, by default. This mode is more streamlined, enabling you to implement security quickly and consistently across SharePoint Online and Project Online. However, there may be situations where it makes more sense to use Project Permission Mode. For example, if you think your organization needs to manage access based on the RBS structure, you'll need to use Project Permission Mode. This mode offers greater control, because you can customize and change individual permissions for each security group and typically intended for larger PMO organizations with a requirement to have more granular access control and has in-house expertise (or has engaged with a partner) to help with the implementation.
  
 **Site collection administrators have administrative permissions to the Project Online site.** These permissions allow the site collection administrator to bypass any Project Online security permissions set in SharePointPermission Mode or Project Permission Mode. This way, someone always has access to Project Online. [What should I do if my Project Online administrator gets locked out?](what-should-i-do-if-my-project-online-administrator-gets-locked-out.md)
  
> [!CAUTION]
> Switching between SharePoint Permission Mode and Project Permission Mode deletes all security-related settings. If you switch from SharePoint Permission Mode to Project Permission Mode, you have to manually configure your security permissions structure in Project Online. Switching from Project Permission Mode back to SharePoint Permission Mode deletes your security permissions information from Project Online. 
  
To change between permission modes:
  
1. [Where to sign in to Office 365 for business](https://support.office.com/article/e9eb7d51-5430-4929-91ab-6157c5a050b4) with your admin account and go to Project Online. 
    
2. In Project Online, click the **Settings** icon, and select **PWA Settings**.
    
3. On the **PWA Settings** page, in the **Operational Policies** section, select **Additional Server Settings**. 
    
4. In the **Permissions Management** section, choose the permission mode you want to use for your Project Web App site: **SharePoint Permission Mode** or **Project Permission Mode**.
    
5. Select **OK**.
    
> [!NOTE]
> You need to be a Site Collection Admin for the PWA site in order to view the PWA site usage settings on the Additional Server Settings page. 
  

