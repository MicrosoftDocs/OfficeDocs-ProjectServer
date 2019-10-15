---
title: 'Connect to Project for the web data through Power BI Desktop'
description: 'Connect to Project for the web data through Power BI Desktop'
author: efrene
manager: pamgreen
ms.reviewer: 

---
# Connect to Project for the web data through Power BI Desktop
You can connect to data in Project Online through Power BI Desktop.

## Get started 
You first need to do the following:

- Download [Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662), then run the installer to get **Power BI Desktop** on your computer.
- Download the [Project for the web Power BI template]() to your computer.

## Launch and configure the Power BI Desktop template file
1. Click on the Project for the web Power BI template file to open it in Power BI Desktop.
2. In the ribbon, select **Edit Queries**, and then select **Edit Parameters**.
3. In the **Enter Parameters** screen, in the **CDS URL** field, type the URL of your Dynamics 365 Common Data Service (CDS) default instance you are using for Project for the web, and then click **OK**.
4.  Power BI Desktop will prompt you to authenticate with your Office 365 account. Select Organizational account and then enter your credentials.

From here, you can choose which tables you would like to connect to and build a query. 

### How to determine your **CDS URL**

 



 To determine the URL you need, see the **Web API URL and versions** section of [Compose HTTP requests and handle errors](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions).   

  






