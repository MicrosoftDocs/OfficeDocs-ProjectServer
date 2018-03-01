---
title: "Post-upgrade tasks (Project Server 2013)"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/22/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: b51169b0-3e7e-42e1-845e-db0b5bdaf331
description: "Summary: After you upgrade to Project Server 2013, you must address additional tasks."
---

# Post-upgrade tasks (Project Server 2013)
 
 **Summary:** After you upgrade to Project Server 2013, you must address additional tasks.<br/>
**Applies to:** Project Server 2013
  
After upgrading to Project Server 2013, you must address two post-upgrade tasks:
  
- Enable Issues and Risks links.
    
- Add the Project Server 2013 Enterprise Project Type (EPTs)
    
## Enable Issues and Risks links

After upgrading to Project Server 2013, Issues and Risk links in your upgraded project plans will not function and require the following in order for them to work properly: 
  
- **Bulk update of all project sites** - You will need to change the site path information for your upgraded project sites since they have been moved from one Web application to another. You can do this through the Bulk Update Project Sites page in the Project Web App settings located in SharePoint Central Administration. For more information about the Bulk Update Project Sites page, see [Bulk Update Project Sites (Project Server 2013 settings)](bulk-update-project-sites-project-server-2013-settings.md).
    
- **Publish all projects with associated project sites** - After updating your site path information for your project sites through the Bulk Update Project Sites page, you will need to publish each project that contains an associated project site. This is required so that the Project Server 2010 links for Issues and Risks are moved to Project Server 2013, which occurs when the project is published. If the project is not published, the link items will not display.
    
> [!IMPORTANT]
> Document library links to tasks in Project Server 2010 are not migrated to Project Server 2013 during the upgrade process. Although your Document library links may function in Project Server 2010, when they are upgraded to Project Server 2013, they will no longer display since they are not upgraded. However, new Document library links can be added in Project Server 2013. 
  
## Add the Project Server 2013 Enterprise Project Types

A known issue after you upgrade from Project Server 2010 to Project Server 2013 is that on the Project Center page, if you click **New** on the ribbon, you only see the **Basic Project** EPT that was migrated from Project Server 2010. You do not see the two default EPTs that are installed with Project Server 2013:
  
- Enterprise Project
    
- SharePoint Tasks List
    
The following procedures allow you to correct this problem so that you can access and use the default EPTs for Project Server 2013. This process requires two procedures:
  
- Add the SharePoint Tasks Lists EPT
    
- Rename the Basic Project EPT to "Enterprise Project"
    
After you complete the procedures, the Enterprise Project Types page displays the SharePoint Tasks Lists and Enterprise Project EPTs. 
  
### To add the SharePoint Tasks List as an Enterprise Project Type

1. In Project Web App, click the Settings icon, and then click **Project Web App Settings**.
    
2. On the Project Web App settings page, in the **Workflow and Project Details Pages** section, click **Enterprise Project Types**.
    
3. On the Enterprise Project Types page, click **New Enterprise Project Type**.
    
4. On the Add Enterprise Project Type page, enter the information needed for the SharePoint Tasks List enterprise project type:
    
  - For the **Name** field, typeSharePoint Tasks List.
    
  - For the **Description** field, typeUse this type to create a SharePoint Tasks List Project with some basic information (like name, start date, end date) and a schedule.
    
  - In the **SharePoint Tasks List Project** section, select **Create new projects as SharePoint Tasks List Projects**.
    
  - In the **New Project Page/Project Details Pages** section, in the **New Project Page** list, select **Project Details**. In the **Available Project Details Pages** list, move **Project Details** and **Schedule** to the box on the right. Use the Up/Down buttons to ensure that Project Details is listed first and Schedule is listed second.
    
  - In the **Defaults** section, select **Use this as the default Enterprise Project Type during Project Creation**.
    
  - In the **Image** section, in the **Type the URL** field, type/_layouts/15/inc/pwa/images/CenterNormalProject.png. This specifies the location of the default image for the SharePoint Tasks List EPT. Click **Click here to test** to verify that the image is found in the default location.
    
5. Leave each of the other options with the default value, and then click **Save**.
    
### To rename the Basic Project Enterprise Project Type

1. In Project Web App, click the Settings icon, and then click **Project Web App Settings**.
    
2. On the Project Web App settings page, in the **Workflow and Project Details Pages** section, click **Enterprise Project Types**.
    
3. On the Enterprise Project Types page, in the **Name** column, click **Basic Project**.
    
4. On the Basic Project page, in the **Name** field, change the text toEnterprise Project, and then click **OK**. 
    
5. Click **Save**. The Enterprise Project EPT now displays on the Enterprise Project Types page.
    
## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also

#### 

[Upgrade to Project Server 2013](upgrade-to-project-server-2013.md)

