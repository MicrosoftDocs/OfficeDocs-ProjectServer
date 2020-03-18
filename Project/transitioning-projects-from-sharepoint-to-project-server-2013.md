---
title: "Transitioning projects from SharePoint to Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 8/30/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: d24d3ade-4970-4407-a7d8-fb3931cd5651
description: "Summary: Learn how to increase the Project Web App functionality level for a project as project management needs become more complex."
---

# Transitioning projects from SharePoint to Project Server 2013

 **Summary:** Learn how to increase the Project Web App functionality level for a project as project management needs become more complex.<br/>
**Applies to:** Project Server 2013

SharePoint Server and Project Server 2013 provide the ability to incrementally increase the project management capabilities and features for a project as the project grows and becomes more complex. Projects can start as a simple SharePoint task list and gradually grow into a full enterprise project using all the features available in Project Server.

> [!IMPORTANT]
> This scenario applies only to Project Server 2013. 

In this article:

- [Scenario overview](transitioning-projects-from-sharepoint-to-project-server-2013.md#overview)

- [Before you begin](transitioning-projects-from-sharepoint-to-project-server-2013.md#begin)

- [Create SharePoint task list projects](transitioning-projects-from-sharepoint-to-project-server-2013.md#proc1)

- [Enable the Project Web App site collection features](transitioning-projects-from-sharepoint-to-project-server-2013.md#EnablePWAFeatures)

- [Add a Project Center web part](transitioning-projects-from-sharepoint-to-project-server-2013.md#AddProjectCenterWebPart)

- [Import a project](transitioning-projects-from-sharepoint-to-project-server-2013.md#ImportProject)

- [Activate enterprise project features for a project](transitioning-projects-from-sharepoint-to-project-server-2013.md#ActivateEnterpriseFeatures)

- [Add a Project Web App site](transitioning-projects-from-sharepoint-to-project-server-2013.md#AddProjectWebAppSite)

## Scenario overview
<a name="overview"> </a>

This scenario walks through the progression of steps that you can take to transition a SharePoint task list project to a full enterprise project in Project Web App for Project Server. These are steps that you would normally take over some period of time as your project management requirements increase for a particular project. The purpose of this article is to show what those steps are and the order in which they are done.

The basic progression is:

1. Create a site and add a SharePoint task list to that site.

2. Update the task list project using Project Server if needed.

3. Enable the Project Web App site collection features for the site collection where your task list project is located.

4. Add a Project Center web part and import the task list project into the Project Web App database.

5. Activate the enterprise project features for the task list project.

6. Add a Project Web App site to the site collection.

Each of the above steps adds new functionality that you can use to manage the project.

When planning your project sites, it's important to plan your site collections carefully if you want to keep related projects together.You can create multiple site collections, each with their own projects, but each site collection is distinct and projects cannot be shared between site collections. When you deploy a Project Web App site to a given site collection, it can only be used to manage projects in that site collection.

## Before you begin
<a name="begin"> </a>

Before starting, read the following information about permissions and software requirements. Follow the specified steps to install or configure prerequisite software or to modify settings. For example:

- For the procedures in this article that use the SharePoint Central Administration website, you must use an account that is a farm administrator or a Project Server service application administrator.

- For the procedure in this article that use Project Server, you must be logged into a computer running a Windows client operating system such as Windows 7 and you must have Project Server installed.

## Create SharePoint task list projects
<a name="proc1"> </a>

You can create task lists on team sites or project sites using SharePoint Server without the need of having Project Server 2016 installed on the farm. You can accomplish many basic project management tasks by using a SharePoint task list, including editing these projects in Project Server.

While you can create a task list on a team or project site in any site collection, for easiest long term management, we recommend creating a new site collection to use for project sites.

When planning your project sites, it's important to plan your site collections carefully. You can create multiple site collections, each with their own projects, but each site collection is distinct and projects cannot be shared between site collections. When you deploy a Project Web App site to a given site collection, it can only be used to manage projects in that site collection.

Use the following procedure to create a site collection.

### To create a site collection

1. On the SharePoint Central Administration website, under **Application Management**, click **Create site collections**.

2. In the **Web Application** section, choose the web application where you want to create the site collection.

3. In the **Title** text box, type a title for the site.

4. In the **Web Site Address** section, type the URL where you want the site to be created.

5. In the **Template Selection** section, choose **Team Site**.

6. In the **Primary Site Collection Administrator** section, type the name of the primary site collection administrator.

7. Optionally, specify a secondary site collection administrator and a quota template.

8. Click **OK**.

Once the site collection has been created, you must grant access to it for your users. Users will need Edit access in order to work with SharePoint task list projects.

Use the following procedure to grant access to your users.

### To grant access to a site collection

1. Navigate to the root of the site collection that you created.

2. In the ribbon, click **Share**.

3. Type the names of the users or groups to whom you want to grant access, and then click **Share**.

While you can create a project site directly on the root of the site collection, we recommend creating a subsite for each project that you plan to manage.

Use the following procedure to create a subsite.

### To create a subsite

1. Navigate to the root of the site collection that you created.

2. On the **Settings** menu, click **Site Settings**.

3. On the Site Settings page, under **Site Administration**, click **Sites and workspaces**.

4. On the Sites and Workspaces page, click **Create**.

5. In the **Title** text box, type a title for the site.

6. In the **Web Site Address** section, type the URL where you want the site to be created.

7. In the **Template Selection** section, choose **Team Site**.

8. Click **Create**.

Once you have created a subsite, you can add the Tasks and Calendar apps to it. This essentially converts a team site to a project site.

> [!NOTE]
> You can choose the **Project Site** template and the Tasks and Calendar apps will be included. In this case, we chose **Team Site** to illustrate how to add the Tasks and Calendar apps to an existing team site.

Use the following procedure to add the Tasks and Calendar apps to the site.

### To add the Tasks and Calendar apps to a site

1. Navigate to the subsite that you created.

2. Click the **Working on a deadline?** tile.

3. On the **Working on a deadline?** dialog box, click **Add Them**.

Once you have added the Tasks and Calendar apps, you can create a SharePoint list project.

Use the following procedure to create a project.

### To create a SharePoint list project

1. On the subsite, click **Edit the task list**.

2. Add one or more tasks to the task list and assign people and due dates to them.

For greater versatility in managing your project, you can open it in Project Server directly from the SharePoint list.

Use the following procedure to open the project in Project Professional. You must do this on a client computer that is running Project Professional.

### To open a task list in Project Professional

1. On the subsite, in the left pane, click **Tasks**.

2. In the ribbon, on the **List** tab, click **Open with Project**.

3. Add one or more tasks to the task list and assign people and due dates to them.

4. Click **File**, and then click **Save**.

5. Close Project Professional.

6. Refresh the Tasks page to see your changes.

You can continue to use the SharePoint task list and Project Professional to manage your project for as long as that meets your needs.

## Enable the Project Web App site collection features
<a name="EnablePWAFeatures"> </a>

Enabling the Project Web App site collection features adds additional functionality to the site collection, including:

- The ability to import SharePoint task list projects into Project Web App.

- The ability to create reports using data from multiple imported projects.

- New SharePoint security groups specific to Project Web App to help you manage access to your projects.

Enabling the Project Web App site collection features requires that you have Project Server 2016 deployed on the farm.

Enabling the Project Web App site collection features consists of two steps:

- Create a Project Web App database

- Enable the Project Web App site collection features

A Project Web App database is created using the **New-SPProjectDatabase** Microsoft PowerShell cmdlet. In order for the new database to be properly associated with the site collection where you want enable the Project Web App site collection features, you must use the **Tag** parameter to associate a unique string with this database. That string will be used later when you enable the site collection features.

Run the following cmdlet to create a new Project Web App database.

```
New-SPProjectDatabase -Name DatabaseName -ServiceApplication "ServiceApplicationName" -DatabaseServer SQLServerInstance -Tag String
```

For example:

```
New-SPProjectDatabase -Name ProjectWebApp1 -ServiceApplication "Project Service Application" -DatabaseServer Contoso-SQL -Tag "ProjectWebApp1DB"
```

> [!NOTE]
> You can find the name of the Project Server service application in Central Administration by clicking **Manage service applications** under **Application Management**. 

Once you have created the new Project Web App database, the next step is to enable the Project Web App site collection features. Doing so will associate the database that you just created with the site collection.

The Project Web App site collection features are enabled by using the **Enable-SPFeature** PowerShell cmdlet. Prior to running this cmdlet, you must set the **PWA_TAG** parameter of the site collection to match the **Tag** parameter that you set when you created the database. Use the following PowerShell script to set the **PWA_TAG** parameter and then enable the Project Web App site collection features.

```
$web=Get-SPWeb SiteCollectionURL
$web.Properties["PWA_TAG"]="String"
$web.Properties.Update()
Enable-SPFeature pwasite -URL SiteCollectionURL
```

For example:

```
$web=Get-SPWeb https://contoso-appsrv1/sites/ContosoProjects
$web.Properties["PWA_TAG"]="ProjectWebApp1DB"
$web.Properties.Update()
Enable-SPFeature pwasite -URL https://contoso-appsrv1/sites/ContosoProjects
```

After the Project Web App site collection features have been activated for the site collection, the next step depends on the needs of your organization. You can do one of the following:

- **Add a Project Center web part to the site collection** - this allows you to import SharePoint list projects into SharePoint list projects into Project Web App. Adding the web part can be done by anyone with Design permissions on the site. If you do not yet require the full functionality of a Project Web App site, this is an easy way to enable importing projects without the need to involve a system administrator.

- **Add a Project Web App site to the site collection** - this gives you full Project Web App functionality. If you choose this option, there is no need to add a separate Project Center web part, as one is included as part of the Project Web App site.

In the next section, we will walk through the more gradual approach of adding the Project Center web part first. In your environment, consider which approach is best for you.

## Add a Project Center web part
<a name="AddProjectCenterWebPart"> </a>

The Project Center web part provides the necessary functionality for importing SharePoint list projects into Project Web App. This web part can be added to any site in the site collection. In this example, we assume that you are adding it to the root of the site collection.

Use the following procedure to add a Project Center web part.

> [!NOTE]
> You must have Design permissions on the site to perform this procedure. 

### To add a Project Center web part

1. Navigate to the root of the site collection that you created.

2. In the ribbon, on the **Page** tab, click **Edit**.

3. Place your cursor below the Documents web part (or wherever you want to add the Project Center web part).

4. In the ribbon, on the **Insert** tab, click **Web Part**.

5. In the **Categories** list, click **Project Web App**.

6. In the **Parts** list, click **Project Center**.

7. Click **Add**.

8. Click the Project Center web part, and then in the ribbon, on the **Web Part** tab, click **Web Part Properties**.

9. In the web part properties pane, expand **Project Web App**.

10. Type the URL of the root of the site collection that you created.

11. Click **OK**.

12. In the ribbon, on the **Page** tab, click **Save**.

To view projects in the Project Center web part, you must be a member of one of the Project Web App security groups on the site collection. Use the following procedure to add one or more users to a Project Web App security group.

### To add a user to a Project Web App security group

1. Navigate to the root of the site collection that you created.

2. On the Settings menu, choose **Site Settings**.

3. On the Site Settings page, under **Users and Permissions**, choose **People and groups**.

4. On the People and Groups page, in the left pane, click **More...**.

5. Click the Project Web App group to which you want to add users.

    > [!NOTE]
    > **Team Members for Project Web App** is sufficient to see projects in the Project Center web part.

6. Click **New**.

7. Type the users that you want to add to the group, and then choose **Share**.

## Import a project
<a name="ImportProject"> </a>

You must be a member of the **Project Managers for Project Web App** or **Administrators for Project Web App** security groups in the site collection in order to import a project.

### To import a project

1. Navigate to the root of the site collection that you created.

2. On the **Projects** tab, click **Add SharePoint Sites**.

3. On the **Add SharePoint Sites to Project Web App** dialog box, select the check box for the projects that you want to import, and then click **Add**.

The project import process is processed by the Project Server queue. You can check the queue to confirm that the import process has completed successfully. Use the following procedure to check the status of the import job.

> [!NOTE]
> You must be a farm administrator or Project Server service application administrator to perform this task. 

### To check the status of the project import queue job

1. In Central Administration, under **Application Management**, choose **Manage service applications**.

2. Choose the Project Server service application.

3. Hover over the instance of Project Web App where you want to check the queue, click the arrow that appears, and then click **Manage**.

4. Under **Queue and Database Administration**, click **Manage Queue Jobs**.

5. Expand **Job Completion States** and add all job states to the **Selected Job States** box.

6. In the **Job Grid**, click **Refresh**.

7. Check the **Job Type** column for **Project Import Task List** and then check the **Job State** column for the state of that job. The **Job State** will be **Success** when the project import task has completed successfully.

After a project has been imported, you must be a member of the **Project Managers for Project Web App** security group in the site collection to open a project in Project Professional.

If you edited the task list in Project Professional prior to importing it, then you must reconcile the project and enterprise resources using Project Professional after the import has completed.

> [!NOTE]
> If resource reconciliation is required, you will see the following warning when you open the project in Project Professional: **The SharePoint List for this project is now connected to Project Web App, but additional steps are required to complete the connection.**

Use the following procedure to reconcile project and enterprise resources.

> [!NOTE]
> You must be a member of the **Administrators for Project Web App** security group in the site collection in order to perform this task.

### To reconcile project and enterprise resources

1. Navigate to the subsite.

2. In the left navigation, click **Tasks**.

3. In the ribbon, on the List tab, click **Open with Project**.

4. In Project Professional, on the **Resource** tab, click **Add Resources**, and then click **Build Team from Enterprise**.

5. On the **Build Team** dialog box:

1. For each enterprise resource, select the resource in the **Enterprise Resource** list, select the resource with the same name in the **Project Resources** list, and then click **Replace**.

    > [!NOTE]
    > Project resources for which there is no enterprise resource equivalent will be imported in the next step. 

2. Click **OK**.

6. On the **Resource** tab, click **Add Resources**, and then click **Import Resources to Enterprise**.

7. In the left pane, click **Continue to Step 2**.

    Any resources available for import will appear in the center pane.

8. Click **Save and Finish**.

9. On the **File** tab, click **Save As**.

10. Under **Project Web App**, click **Save**.

11. On the **Save to Project Web App** dialog box, click **Save**.

12. Close Project Professional. When prompted to check the project in, click **Yes**.

## Activate enterprise project features for a project
<a name="ActivateEnterpriseFeatures"> </a>

As your project management needs grow for a project, you can convert an imported SharePoint task list project into an enterprise project. Doing so provides additional features, such as timesheets and workflow. Once the project becomes an enterprise project, the SharePoint task list becomes read-only and the project must be edited in Project Professional or Project Web App.

Use the following procedure to activate the enterprise features for the project that you imported.

> [!NOTE]
> You must be a member of the **Administrators for Project Web App** security group in the site collection in order to perform this task.

### To activate enterprise features for an imported project

1. Navigate to the site collection where the project is located.

2. On the Settings menu, choose **Project Web App Settings**.

3. On the Project Server Settings page, in the **Operational Policies** section, click **Connected SharePoint Sites**.

4. On the Connected SharePoint Sites page, in the **Enterprise Project Features** column, click **Activate** for the project where you want to activate the enterprise features.

## Add a Project Web App site
<a name="AddProjectWebAppSite"> </a>

You can add a Project Web App site to the site collection where you have created the SharePoint list projects. Doing so will allow you to take full advantage of Project Server 2013 and Project Web App functionality for the projects in that site collection.

To create a Project Web App site in an existing site collection, you run the New-SPweb Microsoft PowerShell cmdlet to create the site and then run the **Upgrade-SPProjectWebInstance** to perform post-provisioning actions, including creating a Business Intelligence Center.

Run the following script to create the Project Web App site.

```
New-SPweb -URL SiteCollectionURL/PWASiteName -Template pwa#0
Upgrade-SPProjectWebInstance -Identity SiteCollectionURL -Confirm:$False
```

For example:

```
New-SPweb -URL https://contoso-appsrv1/sites/ContosoProjects/PWA -Template pwa#0
Upgrade-SPProjectWebInstance -Identity https://contoso-appsrv1/sites/ContosoProjects -Confirm:$False
```

After you have created the Project Web App site and run **Upgrade-SPProjectWebInstance**, you must run iisreset on each application server in the farm. To run iisreset, open a command window, and type:

```
iisreset /noforce
```

The Project Web App site is now available at the URL that you specified.

## See also
<a name="AddProjectWebAppSite"> </a>

#### 

[Create a PWA site in an existing site collection](create-a-pwa-site-in-an-existing-site-collection.md)

[Enable the Project Web App site collection features in Project Server 2016](enable-the-project-web-app-site-collection-features-in-project-server-2016.md)

[Add SharePoint task list data to Project Server 2013](add-sharepoint-task-list-data-to-project-server-2013.md)

