---
title: 'Connect to Project data through Power BI Desktop'
description: 'Connect to Project for the web data through Power BI Desktop'
author: serdars
ms.author: serdars
manager: pamgreen
ms.date: 10/29/2019
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150
ms.localizationpriority: medium

---
# Connect to Project data through Power BI Desktop

You can use the Project Power BI template to import and analyze data from Project for the web and Project Online into Power BI. The template is designed to help you quickly connect to your Dataverse instance in Dynamics 365 where your Project for the web data is stored, as well as connect to your Project Web App tenant in Office 365.  You will be able to download a variety of data to visually explore and monitor all the key aspects of your PPM deployment. There are multiple visually rich report pages for the portfolio, resource, and project overview.

## Get started

You first need to do the following:

- Download [Power BI Desktop](https://go.microsoft.com/fwlink/?LinkID=521662), then run the installer to get **Power BI Desktop** on your computer.
- Download the [Project Power BI template](https://aka.ms/ProjectReports) to your computer. The file name of the template file is **Microsoft Project Power BI Template.pbit** for the *consolidated report*; **Microsoft Project Online Power BI Template.pbit** for *Project Online report*; and **Microsoft Project for the Web Power BI Template.pbit** for *Project for the Web report pack*.
 
To use the template, you need the following:

- A Project Plan 1 or Project Plan 3 (previously named Project Online Professional) or Project Plan 5 (previously named Project Online Premium) subscription.
- A Power BI Desktop or Power Bi Pro subscription.

## Launch and configure the Power BI Desktop template file

1. Click on the Project Power BI template file to open it in Power BI Desktop.

2. On the **Enter Parameters** screen, in the **Dataverse URL** field, type the URL of your Dynamics 365 Dataverse instance you are using for Project for the web.

3. In the **PWA URL** field, type the URL of your Project Online Project Web App site, for example, https://<spam><spam>contoso.sharepoint<spam><spam>.com/sites/PWA. Then click **Load**.

   ![Parameters.](media/MSPowerBIProject.png)

4.  Power BI Desktop will prompt you to authenticate with your Office 365 account. Select **Organizational account**, click **Sign In**, and enter your credentials.

    ![Dataverse environment.](media/OrgSignin.png)

A message will be displayed, telling you that your data is loading. Depending on the number of projects, tasks, and resources in your system, this may take some time. 

If you receive an error during the load process stating that access to a resource is forbidden, check your data source settings permissions by implementing the following steps:

1. In the ribbon, select **Edit queries**, and then select **Data source settings**.

2. Select **Global permissions**, select a data source URL, and then click the **Edit permissions** button at the bottom of the screen.

3. On the **Edit permissions** screen, verify that **Privacy level** is set to **Organizational**.

4. Also verify that for **Credentials**, the **Type** is set to **Organizational account**.  If it is not, click **Edit**, select **Organizational account** on the left pane, and log in with your credentials.  Click **Save**, and verify that the Credentials Type has changed.

5. Do this for each of the remaining data source URLs, and then click **Close**.

6. Try to load your data again.

> [!div class="mx-imgBorder"]
> ![Data source settings.](media/data-source-settings.png)

### How to determine your Dataverse URL

 Project for the web data is stored in the Dynamics 365 Dataverse. You need to enter the URL of your Dataverse instance that you are using, and it needs to be in the following format: 

https://(environment_name).(region).dynamics.com

For example:
https://orgde6d15d8.crm.dynamics.com

The following sections will tell you how to find the *environment_name* and the *region* values of the URL.

**To determine the Dataverse environment name value of the URL**:

1. Log on to Office: https://www.office.com.
2. On the office.com page, in the left pane, click **All apps**.
3. On the **All apps** page, click **Business Apps** tab and select the project application of the organization you want to build your reports on.
The Apps URL will give you the environment and region value. 

    ![Default Dataverse environment.](media/powerappsen.png)

**To determine the region value of the URL**:

The region value will usually be associated to the data center that is close to you geographically. The following list shows the region values associated with regional data centers.

| Region <br/> | Value <br/>|
|:-----|:-----|
|North America   <br/> |crm <br/> |
|South America <br/> |crm2  <br/> |
|Canada   <br/> |crm3 <br/> |
|Europe, Middle East and Africa (EMEA)  <br/> |crm4<br/> |
|Asia Pacific Area (APAC)  <br/> |crm5 <br/> |
|Oceania   <br/> |crm6 <br/> |
|Japan   <br/> |crm7 <br/> |
|India  <br/> |crm8 <br/> |
|North America 2   <br/> |crm9 <br/> |
|United Kingdom   <br/> |crm11 <br/> |
|France  <br/> |crm12 <br/> |

If you are not sure, check with your Office 365 administrator and have them check for the value in the [Power Platform Admin Center](https://docs.microsoft.com/power-platform/admin/admin-guide).

![PowerPlatform Admin Center.](media/PowerPlatformAdminCenter.png)

### How to determine your Project Web App (PWA) URL

You can go to your Project Online PWA site home page to find the PWA site URL.

You can get to your PWA site by implementing the following steps:

1. In Office 365, click the Apps icon in the top left corner, and then in **Apps**, select **Project**.

2. On your Project Home page, on the bottom of the page, click, **Go to Project Online**. This will take you to your PWA Home page.

3. Copy the URL in your browser and use this value for the **PWA URL** field in the Project template.

   ![Project Web App Site URL.](media/PWASiteURL.png) 

If you are still not sure, check with your Office 365 admin and have them check for the value in the SharePoint admin center.


## After connecting to your data

After Power BI Desktop retrieves the data, the visualizations in each report page will load and display the data.  

> [!Note]
> You need to have read permissions at the business-unit level to the Dataverse entities to which the report connects to have a portfolio-level view of the data.  


From the Power BI Desktop, we recommend [publishing the report to a shared workspace](https://docs.microsoft.com/power-bi/desktop-upload-desktop-files), and then [configure scheduled refresh of the data to keep your dataset up to date](https://docs.microsoft.com/power-bi/refresh-scheduled-refresh).

## Project reports

After connecting to your data, the following key "out-of-the-box" reports are available to you to view and analyze your project data.

### Portfolio Dashboard

The Portfolio Dashboard report gives you a roll-up of all projects, and lets you know the total number of projects, effort completed, and effort remaining. It lets you filter your project data by project progress or project manager.

![Portfolio Dashboard.](media/portfolio-dashboard.png) 

### Portfolio Timeline

The Portfolio Timeline reports shows visually where all projects fall on a timeline, including their duration and progress to date. 

![Portfolio Timeline.](media/portfolio-timeline.png) 

### Portfolio Milestones

The Portfolio Milestones report summarizes all milestones completed and are yet to complete in the past 30 days, as well as the milestones planned for the next 30 days.

![Portfolio Milestones.](media/portfolio-milestones.png) 

### Resource Dashboard
The Resource Dashboard gives a resource manager an overview of how his or her resources are allocated to projects, showing details about each resources total effort, tasks remaining, and task status.
 
![Resource Dashboard.](media/resource-dashboard.png) 

### Resource Assignments

The Resource Assignments report lets you focus on task and project data for your resources.  You can drill into a resources task progress, total effort, effort distribution across projects, and project and task details.

![Resource Assignments.](media/resource-assignments.png) 

### Task Overview

The Task Overview report looks at task details across projects.  

![Task Overview.](media/task-overview.png) 

### Project Timeline

The Project Timeline shows each project with details on its tasks and status.  

![Project Timeline.](media/project-timeline.png) 

### My Work

The My Work report lets an individual team member see a  detailed task list of all their work across projects, and gives others visibility into their work. 


![My Work.](media/my-work.png) 

### My Timeline

The My Timeline report lets team member see their personal timeline of work across and within projects.​
 

![My Timeline.](media/my-timeline.png) 

## See also

[Compose HTTP requests and handle errors](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions)
