---
title: "Deploy Project Web App with a new site collection (Project Server 2013)"
ms.author: serdars
author: serdars
manager: scotv
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: f7b97b0f-d7f9-42ef-bbee-e220daedd06e
description: "Summary: Learn how to deploy an instance of Project Web App along with a Project Web App site in a new site collection."
---

# Deploy Project Web App with a new site collection (Project Server 2013)
 
 **Summary:** Learn how to deploy an instance of Project Web App along with a Project Web App site in a new site collection.<br/>
**Applies to:** Project Server 2013
  
Creating a Project Web App site with a new site collection creates a Project Web App database on the specified instance of SQL Server.
  
> [!NOTE]
> If your organization requires databases to be created manually by a database administrator, have your database administrator see [New-SPProjectDatabase](https://technet.microsoft.com/library/6eca666c-cbe8-41aa-94c5-4a8a3419fc96.aspx) and create the Project Web App database before you proceed with the procedures in this article.
  
## Video demonstration
<iframe src="//videoplayercdn.osi.office.net/hub/?csid=ux-cms-en-us-msoffice&uuid=e37c691c-1696-40b6-a6c9-30b51b3588eb&AutoPlayVideo=false&height=415&width=740" frameborder= "0" marginwidth= "0" marginheight= "0" scrolling= "no" allowfullscreen= "" style="width: 740px; height: 415px;"></iframe>

This video shows the steps involved in creating a Project Web App site with a new site collection in a Project Server 2013 farm, as described in this article.
  
**Video: Deploy Project Web App with a new site collection**
 
## Create a top-level web site
<a name="VideoDemo"> </a>

If a top-level web site does not exist for the web application where you want to create a Project Web App site, you must first create one. Use the following procedure to create a top-level web site if needed.
  
### To create a top-level Web site

1. Start SharePoint 2013 Central Administration.
    
   - For Windows Server 2008 R2:
    
   - Click **Start**, click **Microsoft SharePoint 2013 Products**, and then click **SharePoint 2013 Central Administration**.
    
   - For Windows Server 2012:
    
   - On the **Start** screen, click **SharePoint 2013 Central Administration**.
    
     If **SharePoint 2013 Central Administration** is not on the **Start** screen:
    
   - Right-click **Computer**, click **All apps**, and then click **SharePoint 2013 Central Administration**.
    
2. In Central Administration, in the **Application Management** section, click **Create site collections**.
    
3. Choose a Web application from the **Web Application** drop-down menu.
    
    > [!NOTE]
    > If no Web application is available, you must create one. For more information, see [Create a Web application (SharePoint Server 2013)](https://technet.microsoft.com/library/cc261875.aspx). 
  
4. Type a title for the site collection in the **Title** box.
    
5. In the **Template Selection** section, choose a template for the site.
    
    > [!NOTE]
    > Project Server 2013 does not require a specific template. You can choose one appropriate for your organization. 
  
6. In the **Primary Site Collection Administrator** section, type the name of the account that you want to use for the site administrator.
    
7. Click **OK**.
    
After you have created the top-level web site, you must grant users access to the site. Use the following procedure to grant read access to the top-level site.
  
### To set Read permissions on the top-level Web site

1. Navigate to the root site (that is, https://<servername>).
    
2. At the top of the page, click **Share**.
    
3. On the Share dialog box, click **Show Options**.
    
4. From the Select a group or permission level, choose **<site> Visitors [Read]**.
    
5. In the **Enter names or email addresses** text box, type **Everyone**.
    
6. Click **Share**.
    
## Create a Project Web App site
<a name="VideoDemo"> </a>

> [!IMPORTANT]
> When you create a new Project Web App site in conjunction with a new site collection, we recommend that you use a separate SharePoint Server 2013 content database for the Project Web App site and its associated project workspaces. To correctly isolate the Project Web App site in its own content database, you must deploy Project Web App at a time when other administrators are not creating new sites on the Web application where you are deploying Project Web App. 
  
By putting Project Web App and its associated project workspaces in a separate content database, you greatly simplify site migration and backup and restore procedures.
  
Creating a Project Web App site takes five basic steps:
  
1. Temporarily lock down existing content databases.
    
2. Create a content database to host the Project Web App site and its associated project workspaces.
    
3. Create the Project Web App site itself.
    
4. Lock down the Project Web App content database to prevent additional site collections being added.
    
5. Unlock existing content databases.
    
SharePoint Server 2013 uses a round-robin algorithm to determine the distribution of site collections across content databases. In order to deploy the Project Web App site to a specific content database, you have to lock down any existing content databases in the farm. The process does not affect user access; it only affects the distribution of new site collections.
  
> [!NOTE]
> If you are deploying Project Web App to a new web application that will be dedicated to PWA, you can use the default content database created with that web application for Project Web App. In this case, there is no need to follow the following lockdown procedures. However, we do recommend that you set the **Maximum number of sites that can be created in this database** setting to1 for that content database after you deploy Project Web App. This helps avoid having additional site collections beyond Project Web App being created in that database in the future.
  
To lock down your content databases, follow these steps for each content database associated with the Web application where you plan to deploy your Project Web App site.
  
> [!IMPORTANT]
> Ensure that no other administrators are adding site collections to the Web application where you plan to deploy Project Web App while you are performing the procedures in this section. 
  
### To lock down a content database

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage content databases**.
    
2. In the **Current Number of Site Collections** column, note the number of site collections for the database that you plan to lock down.
    
3. In the **Database Name** column, click the link for the content database that you want to lock down.
    
4. In the **Database Capacity Settings** section:
    
1. In the **Maximum number of sites that can be created in this database** box, type the existing number of site collections for this database (as noted in the **Current Number of Site Collections** column, earlier in this procedure).
    
    > [!NOTE]
    > Take note of the current value for this parameter. You will have to change it back to this value after the PWA site has been created. 
  
2. In the **Number of sites before a Warning event is generated** box, type a lower number than the value that is used for **Maximum number of sites that can be created in this database**.
    
    > [!NOTE]
    > Take note of the current value for this parameter. You will have to change it back to this value after the Project Web App site has been created. 
  
5. Click **OK**.
    
### To create a content database

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage content databases**.
    
2. Click **Add a content database**.
    
3. In the **Web Application** section, choose the Web application where you plan to deploy the Project Web App site.
    
4. In the **Database Name and Authentication** section, type the database server name where you plan to deploy your Project Web App databases, and type a name for the database.
    
5. Click **OK**.
    
After the content database has been created and configured, the next step is to create the Project Web App site itself.
  
### To create a Project Web App site

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. On the Manage Service Applications page, click the Project Server Service Application.
    
3. On the Manage Project Web App Sites page, click **Create Project Web App Instance**.
    
4. Complete the Create Project Web App Instance page as designated in the following table:
    
|**Option**|**Description**|
|:-----|:-----|
|Web Application  <br/> |The Web application for the Project Web App site.  <br/> |
|Project Web App path  <br/> |The path from the root site for this Project Web App site.  <br/> |
|Select a language  <br/> |The user interface language for this Project Web App site.  <br/> |
|Use Public URL  <br/> |Use this option if you want to host the Project Web App site on a root URL (for example, https://www.contoso.com).  <br/> |
|Administrator Account  <br/> |The user account that will be added to the Administrators for Project Web App security group in this instance of Project Web App. You must use this account the first time that you access the Project Web App site.  <br/> |
|Database server  <br/> |The instance of SQL Server where you want to host the Project Web App database. If your database administrator has already created a Project Web App database, specify the names of that database in the **Project Web App database name** text box. If the database was not previously created, it will be created automatically. <br/> |
|Quota for SharePoint content in this site  <br/> |The maximum site storage, in megabytes, for the Project Web App site.  <br/> |
|Quota Warning for SharePoint content in this site  <br/> |The site storage level, in megabytes, at which a warning e-mail message will be sent to the site administrator.  <br/> |
   
5. Click **OK**.
    
Project Server starts the Project Web App site creation process. This may take some time. When the site creation process is complete, the status shown on the Project Web App site list is **Provisioned**.
  
After the Project Web App site has been provisioned, verify that it was created in the content database that you created. Use the **Get-SPSite** Microsoft PowerShell command, passing the new content database as a parameter:
  
### To verify the Project Web App site location

1. Verify that you meet the following minimum requirements: See [Add-SPShellAdmin](https://docs.microsoft.com/powershell/module/sharepoint-server/Add-SPShellAdmin?view=sharepoint-ps).
    
2. On the **Start** menu, click **All Programs**.
    
3. Click **Microsoft SharePoint 2013 Products**.
    
4. Click **SharePoint 2013 Management Shell**.
    
5. From the Microsoft PowerShell command prompt (that is, PS C:\\>), type the following command and then press ENTER:
    
    **Get-SPSite -ContentDatabase** *<ContentDatabaseName>*
    
    The command should return the URL for your Project Web App site and no other URLs.
    
    > [!NOTE]
    > If additional URLs beyond that of the Project Web App site are listed in the content database, delete the Project Web App site and restart the procedure with a new content database. 
  
After the Project Web App site is in the desired content database, you must lock down the database to prevent SharePoint Server 2013 from adding additional site collections to the database. This is performed by configuring the maximum number of sites for the content database to one. 
  
> [!NOTE]
> Configuring this setting does not prevent new project workspace sites from being created. 
  
### To lock down the content database

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage content databases**.
    
2. In the **Database Name** column, click the link for the content database that you created.
    
3. In the **Database Capacity Settings** section:
    
1. In the **Number of sites before a Warning event is generated** box, type **0**.
    
2. In the **Maximum number of sites that can be created in this database** box, type **1**.
    
4. Click **OK**.
    
After you have locked down your Project Web App content database, you can return any other content databases to their original values for **Maximum number of sites that can be created in this database** and **Number of sites before a Warning event is generated**.
  
You can now access the new Project Web App site.
  
## See also
<a name="VideoDemo"> </a>

#### 

[Deploy Project Web App in an existing site collection (Project Server 2016)](deploy-project-web-app-in-an-existing-site-collection-project-server-2016.md)
#### 

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

