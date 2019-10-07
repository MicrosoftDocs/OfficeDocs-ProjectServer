---
title: 'Connect to Project for the web data through Power BI Desktop'
description: 'Connect to Project for the web data through Power BI Desktop'
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: 
localization_priority: Normal
ms.custom: Adm_Project
search.appverid: 
description: "Learn how an Office 365 global administrator can delete a user's information from Project for the Web."
---
# Connect to Project for the web data through Power BI Desktop
You can connect to data in Project Online through Power BI Desktop.

## Step 1: Download Power BI Desktop
1. [Download Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662), then run the installer to get **Power BI Desktop** on your computer.

## Step 2: Connect to Project for the web with OData
1. Open **Power BI Desktop**.
2. On the *Welcome* screen, select **Get Data**.
3. Choose **OData feed** and select **Connect**.
4. Enter the address for your OData feed in the URL box, and then click **OK**.

    For example: <spam><spam>https://contoso.crm.dynamics.com/api/data/<spam><spam>

    To determine the URL you need, see the **Web API URL and versions** section of [Compose HTTP requests and handle errors](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions).   
    
5. Power BI Desktop will prompt you to authenticate with your Office 365 account. Select Organizational account and then enter your credentials.
   
   ![](media/desktop-project-online-connect-to-data/image.png)

From here, you can choose which tables you would like to connect to and build a query.  






