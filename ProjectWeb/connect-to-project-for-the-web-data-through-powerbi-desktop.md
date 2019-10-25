---
title: 'Connect to Project for the web data through Power BI Desktop'
description: 'Connect to Project for the web data through Power BI Desktop'
author: efrene
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: PJO150
localization_priority: Normal

---
# Connect to Project for the web data through Power BI Desktop


## Get started 
You first need to do the following:

- Download [Power BI Desktop](http://go.microsoft.com/fwlink/?LinkID=521662), then run the installer to get **Power BI Desktop** on your computer.
- Download the [Project for the web Power BI template](https://aka.ms/ProjectReports) to your computer.

## Launch and configure the Power BI Desktop template file
1. Click on the Project for the web Power BI template file to open it in Power BI Desktop.
2. In the **Enter Parameters** screen, in the **CDS URL** field, type the URL of your Dynamics 365 Common Data Service (CDS) default instance you are using for Project for the web, and then click **OK**.<br/>
![Default CDS environment](media\Parameter.png)
3.  Power BI Desktop will prompt you to authenticate with your Office 365 account. Select Organizational account and then enter your credentials.

From here, you can choose which tables you would like to connect to and build a query. 

### How to determine your CDS URL

 Project for the web data is stored in the Dynamics 365 Common Data Service (CDS). For the parameter value needed to connect with the Power BI Desktop, you need to enter the URL of your default CDS instance that you are using, and it needs to be in the following format: 

https://<spam><spam>(environment_name).(region).dynamics<spam><spam>.com

For example:
https://<spam><spam>orgde6d15d8.crm.dynamics<spam><spam>.com

**To determine the Default CDS environment value of the URL**:

1. While logged into Office 365, go to this site:  https://web.powerapps.com
2. On the PowerApps page, note the value in the **Environments** section.  In the image below, the default CDS environment value is **orgde6d15d8**.

    ![Default CDS environment](media\PowerAppsPage.png)

**To determine the region value of the URL**:

The region value will usually be associated to the data center that is close to you geographically. The following list shows the region values associated with regional data centers.

|||
|:-----|:-----|
|**Region** <br/> |**Value** <br/> |
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

If you are not sure, check with your Office 365 administrator and have them check for the value in the [Power Platform Admin Center](https://docs.microsoft.com/en-us/power-platform/admin/admin-guide).

![PowerPlatform Admin Center](media\PowerPlatformAdminCenter.png)

## See also

[Compose HTTP requests and handle errors](https://docs.microsoft.com/powerapps/developer/common-data-service/webapi/compose-http-requests-handle-errors#web-api-url-and-versions).   

  






