---
title: "Manage connected SharePoint sites in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: 6a50a06d-1fd3-49be-9940-f98c6601dd20
description: "Summary: The Connected SharePoint Sites page in Project Web App Settings lets you manage project sites in Project Server 2013."
---

# Manage connected SharePoint sites in Project Server 2013
 
 **Summary:** The Connected SharePoint Sites page in Project Web App Settings lets you manage project sites in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
The **Connected SharePoint Sites** setting is available through the Project Web App Server Settings page in the **Operational Policies** section. For more information about related administrative settings, see [Operational Policies in Project Server 2013](operational-policies-in-project-server-2013.md).
  
## Configure the Project Sites settings

You can do the following through the Connected Project Sites page:
  
- Create a new project site
    
- Edit a project site address
    
- Synchronize
    
- Delete a project site
    
- Go to Project Site Settings
    
### The Create Site settings
<a name="section1"> </a>

 **Create Site** lets you create a new project site for your project if you did not create one when the project was originally published to Project Server 2013. You can view the **Project Sites** list on the Connect SharePoint Sites page to determine whether a project has an existing site. A project without a project site does not have a corresponding URL next to it in the **Site Address** column.
  
### To create a project site

1. In Project Web App, click the Setting icon, and on the menu click **Project Web App Settings**. 
    
2. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.
    
3. On the Connected SharePoint Sites page, from the **Project Name** list, select a project for which you want to create the project site.
    
4. Click **Create Site**.
    
    The **Create Project Site** dialog box appears.
    
5. In the **Web Application** list, select the web application that you want for the project site.
    
6. In the **Site URL** field, verify the site URL for the project site. You can edit the site URL information, if necessary. The site URL is appended to the web application name to provide the destination URL (as seen in the **Destination URL** field).
    
7. Click **OK**. 
    
    The project site you created now appears next to the project name that you selected in step 2.
    
### The Edit Site Address settings
<a name="section2"> </a>

 **Edit Site Address** lets you edit the destination URL for a project site to point to a new site address. Changing the site address information breaks the existing link between the project and the existing project site. You can then enter the information for the new project site.
  
> [!NOTE]
> Before changing the project site URL for a project, be sure to provision a new project site with a new site template. 
  
### To edit a site address for a project site

1. In Project Web App, click the Setting icon, and on the menu click **Project Web App Settings**. 
    
2. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.
    
3. On the Connected SharePoint Sites page, from the **Project Name** list, select a project for which you want to edit the project site information.
    
4. Click **Edit Site Address**.
    
    The **Edit Site Address** dialog box appears.
    
5. To change the project site URL to the new URL, select **Type a new SharePoint site URL**. Select the Web Application in which the new site is located and enter the Site URL for the new site.
    
6. Click **Test URL** to verify whether the new project site URL can be opened.
    
7. You optionally can unlink the existing SharePoint site from the project through the Edit Site Address dialog box. To do this, **click Unlink the SharePoint site from the project**.
    
    > [!NOTE]
    > Unlinking a SharePoint Tasks List project from a project site enables the enterprise project feature for the project. 
  
8. Click **OK**. 
    
    The project site URL for the project you selected in step five is changed to the new URL.
    
### The Synchronize settings
<a name="section3"> </a>

> [!NOTE]
> The Synchronize setting is only available in Project Permission Mode. This setting is not available in SharePoint Permission Mode. 
  
 **Synchronize** lets you manually synchronize the project site's users, permissions, and other Project Server-related information between Project Server 2013 and the Web server that is running SharePoint Server 2013.
  
If you want to automatically run synchronization for your project sites, see the **Automatic Provisioning** option that is available in [Project Site Provisioning Settings (Project Server 2013 settings)](project-site-provisioning-settings-project-server-2013-settings.md).
  
### To synchronize your project site information between Project Server and SharePoint Foundation

1. In Project Web App, click the Setting icon, and on the menu click **Project Web App Settings**. 
    
2. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.
    
3. On the Connected SharePoint Sites page, from the **Project Name** list, select a project for which you want to synchronize your project site information between Project Server 2013 and SharePoint Server 2013.
    
4. Click **Synchronize**.
    
    > [!NOTE]
    > Synchronization will automatically recur at the default schedule of every one minute. You can choose to change the default schedule synchronization setting by configuring the **Project Server: Synchronization of SharePoint Server permission to Project Web App permissions** timer job in Central Administration.
  
### To change the synchronize schedule

1. In Central Administration, click **Monitoring**.
    
2. On the Monitoring page, in the Timer Job section, click **Review job definitions**.
    
3. On the Job Definitions page, find and click **Project Server: Synchronization of SharePoint Server permission to Project Web App permissions for job <PWAInstance>**. 
    
    For example: Project Server: Synchronization of SharePoint Server permission to Project Web App permissions job for http://contoso/pwa.
    
4. On the Edit Timer Job page for the job, in the Recurring Schedule section, you can specify when the synchronization will run on a recurring basis. Under **This timer job is scheduled to run**, you can select one of the following options, based on your company's requirements:
    
   - **Minutes**: Allows you to specify a frequency in which the job will run — **Every x minutes**. 
    
   - **Hourly**: Allows you to specify an interval in which the job will randomly run — **Starting every hour between x minutes past the hour and no later than y minutes past the hour**.
    
   - **Daily**: Allows you to specify an interval in which the job will randomly run — **Starting every day between <time of day> and no later than <time of day>**.
    
   - **Weekly**: Allows you to specify in which the job will randomly run — **Starting every week between <day of week and time of day> and no later than <day of week and time of day>**.
    
   - **Monthly**: Provides you two options:
    
   - Allows you to specify an interval in which the job will randomly run — **By date: starting every month between <time of day and day of month> and no later than <time of day and day of month>**.
    
   - Allows you to specify an exact time of the month in which the timer job will run — **By day: starting every month <time of day, day of the week, and week of the month**. For example, **12:00 AM on the first Sunday**.
    
5. Click **OK** to save your configuration changes.
    
    > [!NOTE]
    > You can click **Run Now** at any time to run the timer job immediately.
  
### The Delete Site settings
<a name="section4"> </a>

 **Delete Site** lets you permanently remove a project site and its content.
  
> [!IMPORTANT]
> Before you proceed, verify that you want to permanently remove a site and its content. Deleted project sites are not recoverable. 
  
> [!NOTE]
> When a project site is deleted for a SharePoint Tasks List project, the enterprise project feature is enabled for the project. 
  
### To delete a project site

1. In Project Web App, click the Setting icon, and on the menu click **Project Web App Settings**. 
    
2. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.
    
3. On the Connected SharePoint Sites page, from the **Project Name** list, select a project for which you want to delete a project site.
    
4. Click **Delete Site**.
    
    A message box appears that asks you to confirm whether you want to delete the project site. It also warns you that you will also be deleting all documents, issues, risks, and deliverables that are associated with the site. 
    
5. Click **OK** to proceed with deleting the site. Click **Cancel** if you no longer want to delete the site.
    
6. If you clicked **OK**, the project site is deleted and no longer appears next to the project it was associated with on the Project Sites page.
    
### Go to Project Site Settings
<a name="section5"> </a>

 **Go to Project Site Settings** lets you go directly to a project site's site settings page where the sites administration settings are located. From the Site Settings page, you can make changes to the site, such as add or remove users, add Web Parts to the site, customize the site's look and feel, and many others.
  
### To go to the Site Settings page for a project site

1. In Project Web App, click the Setting icon, and on the menu click **Project Web App Settings**. 
    
2. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.
    
3. On the Connected SharePoint Sites page, from the **Project Name** list, select a project for which you want to view the Project Site settings page.
    
4. Click **Go to Project Site Settings**.
    
5. The Site Settings page for the selected project site opens. You can make changes to the site settings from this page.
    

