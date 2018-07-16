---
title: "Deploy Project Web App with a new site collection"
ms.author: efrene
author: efrene
manager: pamgreen
ms.audience: ITPro
ms.topic: get-started-article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 1619f4b5-af74-41ee-8051-7eb99511d084
description: "Summary: Learn how to deploy an instance of Project Web App along with a Project Web App site in a new site collection."
---

# Deploy Project Web App with a new site collection (Project Server 2016)
 
 **Summary:** Learn how to deploy an instance of Project Web App along with a Project Web App site in a new site collection.<br/>
**Applies to:** Project Server 2016, Project Server 2019 Public Preview
  
## Create a top-level web site

If a top-level web site does not exist for the web application where you want to create a Project Web App site, you must first create one. Use the following procedure to create a top-level web site if needed.
  
### To create a top-level Web site

1. In the SharePoint Central Administration website, in the **Application Management** section, click **Create site collections**.
    
2. Choose a Web application from the **Web Application** drop-down menu.
    
3. Type a title for the site collection in the **Title** box.
    
4. In the **Template Selection** section, choose a template for the site.
    
    > [!NOTE]
    > Project Servers 2016 or 2019 Public Preview does not require a specific template. You can choose one appropriate for your organization. 
  
5. In the **Primary Site Collection Administrator** section, type the name of the account that you want to use for the site administrator.
    
6. Click **OK**.
    
After you have created the top-level web site, you must grant users access to the site. Use the following procedure to grant read access to the top-level site.
  
### To set Read permissions on the top-level Web site

1. Navigate to the root site (that is, http://<servername>).
    
2. At the top of the page, click **Share**.
    
3. On the Share dialog box, click **Show Options**.
    
4. From the Select a group or permission level, choose **<site> Visitors [Read]**.
    
5. In the **Enter names or email addresses** text box, typeEveryone.
    
6. Click **Share**.
    
## Create a Project Web App site

> [!IMPORTANT]
> When you create a new Project Web App site in conjunction with a new site collection, we recommend that you use a separate SharePoint Server 2016 or 2019 Public Preview content database for the Project Web App site and its associated project workspaces. To correctly isolate the Project Web App site in its own content database, you must deploy Project Web App at a time when other administrators are not creating new sites on the Web application where you are deploying Project Web App. 
  
By putting Project Web App and its associated project workspaces in a separate content database, you greatly simplify site migration and backup and restore procedures.
  
Creating a Project Web App site takes five basic steps:
  
1. Create a content database to host the Project Web App site and its associated project workspaces.
    
2. Create the Project Web App site itself.
    
3. Lock down the Project Web App content database to prevent additional site collections being added.
    
> [!IMPORTANT]
> Ensure that no other administrators are adding site collections to the Web application where you plan to deploy Project Web App while you are performing the procedures in this section. 
  
### To create a content database

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage content databases**.
    
2. Click **Add a content database**.
    
3. In the **Web Application** section, choose the Web application where you plan to deploy the Project Web App site.
    
4. In the **Database Name and Authentication** section, type the database server name where you plan to deploy your Project Web App databases, and type a name for the database.
    
5. Click **OK**.
    
After the content database has been created and configured, the next step is to create the Project Web App site itself.
  
To create a Project Web App site in a new site collection, you run the [New-SPSite](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/new-spsite?view=sharepoint-ps) Microsoft PowerShell cmdlet to create the site in the content database that you just created, and then run Enable-SPFeature to turn on the Project Web App site collection features. 

Verify that you have the following memberships:

    •securityadmin fixed server role on the SQL Server instance. 


    •db_owner fixed database role on all databases that are to be updated. 


    •local Administrators group on the server on which you are running the PowerShell cmdlets.

From the PowerShell command prompt, run the following commands to create the Project Web App site.
  
```
New-SPSite -ContentDatabase ContentDBName -URL SiteCollectionURL/PWASiteName -Template pwa#0
Enable-SPFeature pwasite -URL SiteCollectionURL/PWASiteName
```

For example:
  
```
New-SPSite -ContentDatabase PWA_Content -URL http://contoso-appsrv1/sites/PWA -Template pwa#0
Enable-SPFeature pwasite -URL http://contoso-appsrv1/sites/PWA

```

After the Project Web App site has been provisioned, verify that it was created in the content database that you created. Use the [Get-SPSite](https://docs.microsoft.com/en-us/powershell/module/sharepoint-server/get-spsite?view=sharepoint-ps) cmdlet, passing the new content database as a parameter:
  
### To verify the Project Web App site location

- From the PowerShell command prompt , type the following command and then press ENTER:
    
    **Get-SPSite -ContentDatabase** _<ContentDatabaseName>_
    
    The command should return the URL for your Project Web App site and no other URLs.
    
    > [!NOTE]
    > If additional URLs beyond that of the Project Web App site are listed in the content database, delete the Project Web App site and restart the procedure with a new content database. 
  
After the Project Web App site is in the desired content database, you must lock down the database to prevent SharePoint Server from adding additional site collections to the database. This is performed by configuring the maximum number of sites for the content database to one. 
  
> [!NOTE]
> Configuring this setting does not prevent new project workspace sites from being created. 
  
### To lock down the content database

1. In SharePoint Central Administration, in the **Application Management** section, click **Manage content databases**.
    
2. In the **Database Name** column, click the link for the content database that you created.
    
3. In the **Database Capacity Settings** section:
    
1. In the **Number of sites before a Warning event is generated** box, type0.
    
2. In the **Maximum number of sites that can be created in this database** box, type1.
    
4. Click **OK**.
    
You can now access the new Project Web App site.
  
## See also

#### 

[Deploy Project Web App in an existing site collection (Project Server 2016)](deploy-project-web-app-in-an-existing-site-collection-project-server-2016.md)
#### 

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

