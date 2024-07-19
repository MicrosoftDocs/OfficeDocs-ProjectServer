---
title: Configure reporting for Project Web App (Project Server 2013)
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_OneDriveAdmin
ms.assetid: 400e26f1-b21d-489a-8c6e-a1bc30e6e0c7
description: Configure reporting for Project Web App and configure Secure Store and Excel Services settings to enable the Project Web App sample reports.
---

# Configure reporting for Project Web App (Project Server 2013)
 
 **Summary:** Configure reporting for Project Web App and configure Secure Store and Excel Services settings to enable the Project Web App sample reports.<br/>
**Applies to:** Project Server 2013
  
Project Server 2013 integrates the SharePoint Server 2013 Business Intelligence Center site template into each instance of Project Web App, which provides a central point for hosting the reports, dashboards, and report connections that can be auto-created or manually authored to provide access to reporting data in a given instance of Project Web App. The Business Intelligence Center can be used to host content created with Excel Services in SharePoint Server 2013, Visio Services in SharePoint, PerformancePoint Services in SharePoint, Power Pivot and SQL Server Reporting Services (SSRS).
  
To configure reporting, you must do the following steps:
  
- [Video demonstration](#VideoDemonstration)
    
- [Configure prerequisites](#ConfigurePrerequisites)
    
- [Add a login for the report authors group](#section1) in SQL Server
    
- [Install SQL Server 2008 Analysis Management Objects](#section2)
    
- [Configure Excel Services settings](#section3)
    
- [Configure Secure Store Service settings](#section4)
    
- [Populate the Report Authors and Report Viewers Active Directory groups](#PopulateADGroups)
    
## Video demonstration
<a name="VideoDemonstration"> </a>

This video shows the steps involved in configuring reporting in Project Web App, as described in this article. 
  
**Video: Configure reporting for Project Web App**

![Video (play button) icon.](images/mod_icon_video_M.png)
  
## Configure prerequisites
<a name="ConfigurePrerequisites"> </a>

The procedures in this article require Excel Services and Secure Store. If you have not already deployed these services on SharePoint Server 2013, you must do so before proceeding with the procedures in this article.
  
> [!NOTE]
> Both Excel Services and Secure Store run as service applications in SharePoint Server 2013. If you have already deployed these service applications in SharePoint Server 2013, you can use them with Project Server. There is no need to create new instances of these service applications for Project Server. 
  
For information about deploying Excel Services, see the following articles:
  
- [Excel Services overview](/SharePoint/administration/excel-services-overview)
    
- [Configure Excel Services in SharePoint](/officeonlineserver/configure-excel-online-administrative-settings)
    
> [!IMPORTANT]
> The Excel Services application pool account requires access to the SharePoint content database that is associated with Project Web App. If the content database was created after Excel Services was configured, you must follow the procedure in [Grant content database access to the managed account](/officeonlineserver/configure-excel-online-administrative-settings#GrantAccess) to grant the proper access.
  
For information about deploying Secure Store, see the following articles:
  
- [Plan the Secure Store Service (SharePoint Server 2013)](/SharePoint/administration/secure-store-service-planning)
    
- [Configure the Secure Store Service (SharePoint 2013)](/SharePoint/administration/configure-the-secure-store-service)
    
After both Excel Services and Secure Store have been configured on the farm, proceed with the procedures in the sections below.
  
## Accounts and security groups
<a name="AccountsAndSecurity"> </a>

The following table describes the accounts and security groups that you will need for the various procedures in this article.
  
**Accounts and security groups for configuring reporting for Project Web App**

|**Account**|**Description**|
|:-----|:-----|
|Report Authors group  <br/> |Active Directory security group to which you add users who will create reports, or any other users who need to access reports in Excel. This group is given read permissions to the Project Web App database via the PSDataAccess database role. Have your domain administrator create this group before proceeding with the procedures below.  <br/> NOTE - If you have multiple instances of Project Web App and you want to isolate reporting access for each, you will need a Report Authors group for each instance of Project Web App.           |
|Report Viewers group  <br/> |Active Directory security group to which you add users who will view reports. Have your domain administrator create this group before proceeding with the procedures below.  <br/> NOTE - If you have multiple instances of Project Web App and you want to isolate reporting access for each, you will need a Report Viewers group for each instance of Project Web App.           |
|Secure Store Target Application account  <br/> |This account provides the credentials necessary for report viewers to view reports generated from data in the Project Web App database. This account must have read permissions on the Project Web App database via the PSDataAccess database role.  <br/>TIP - We recommend that you add this account to the Report Authors Active Directory group described above to give it the necessary permissions.           |
   
## Add a login for the report authors group
<a name="section1"> </a>

In order for a report author to be able to access the Project Web App database from Excel, it is necessary to configure SQL Server access and add a SQL Server logon. The logon must allow specific access to the Project Web App database to get schema information and data. Use the domain group you created for report authors.
  
> [!IMPORTANT]
> Excel does not use the Secure Store Service for data access. Only Excel Services in SharePoint Server 2013 uses Secure Store. Users working with reports in Excel require direct database access. 
  
Perform the following procedure on the computer where your Project Web App database is located, or connect to the database engine remotely by using SQL Server Management Studio.
  
### To add a login for the report authors group

1. Click **Start**, **All Programs**, **Microsoft SQL Server** \<version>, **SQL Server Management Studio**.
    
2. Select the instance of the SQL Server database engine where your Project Server 2013 database resides, and then click **Connect**.
    
3. Expand **Security**, right-click **Logins**, and then click **New Login**.
    
4. On the **General** page, click **Search**.
    
5. Click **Object Types**, and select the **Groups** check box.
    
6. Click **OK**.
    
7. Type the name of the group you created for report authors.
    
8. Click **Check Names**.
    
9. Click **OK**.
    
10. Select the **User Mapping** page.
    
11. In the **Users mapped to this login** list box, select the row containing the Project Server 2013 Database.
    
12. Select the **Map** check box for the Project Server 2013 Database.
    
13. Select the **PSDataAccess** database role membership check box.
    
14. Click **OK**.
    
## Install SQL Server 2008 Analysis Management Objects
<a name="section2"> </a>

If you do not already have the SQL Server 2008 R2 Analysis Management Objects (AMO) installed, you must install them on each application server in the farm.
  
> [!NOTE]
> Use the SQL Server 2008 R2 version of AMO regardless of which version of SQL Server you are using to host your databases. 
  
Click to download the [SQL Server 2008 R2 Analysis Management Objects](https://www.microsoft.com/download/details.aspx?id=44277).
  
> [!NOTE]
> After installing the AMO objects, restart the **Project Application Service** on each application server in the farm where it is running. This service is configured in the SharePoint Central Administration website in the **System Settings** section, **Manage services on server**. 
  
## Configure Excel Services settings
<a name="section3"> </a>

You must configure trusted file locations for the Project Web App Sample Reports and Templates libraries.
  
Follow this procedure twice: once for each library.
  
### To configure a trusted file location

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Excel Services service application.
    
3. On the Manage Excel Services page, click **Trusted File Locations**.
    
4. Click **Add Trusted File Location**.
    
5. In the **Address** box, type:
    
    For the Templates library:
    
     `https://<servername>/<projectsitename>/ProjectBICenter/Templates/`
    
    or
    
    For the Sample Reports library:
    
     `https://<servername>/<projectsitename>/ProjectBICenter/Sample%20Reports/`
    
6. In the **Trust Children** section, confirm that the **Children trusted** check box is selected.
    
7. In the **External Data** section:
    
1. In the **Allow External Data** section, select the **Trusted data connection libraries and embedded** option.
    
2. In the **Warn on Refresh** section, clear the **Refresh warning enabled** check box.
    
8. Leave the remaining options at their default value, and then click **OK**.
    
You must configure trusted data connection libraries in order to give users access to the connectors that link the report spreadsheets to the data in the Project Server Database and OLAP databases. As part of this process, you will need the URL of the data connection library in Project Web App (PWA).
  
Use the following procedure to determine the URL of the data connection library in PWA.
  
### To determine the URL for the data connection library

1. On the Project Web App site, in the left navigation pane, click **Reports**.
    
2. In the left pane, click **Data Connections**.
    
3. On the Data Connections page, click the Open Menu button ( **...**) for the **English (United States)** line (or the appropriate language for your locale).
    
4. On the toolbar, click **View Properties**.
    
5. On the Data Connections properties page, right-click the **English (United States)** (or the appropriate language for your locale) link, and then choose ** Properties**.
    
6. Copy the URL in the **Location** text box.
    
### To set up trusted data connection libraries

1. In Central Administration, in the **Application Management**, click **Manage Service Applications**.
    
2. Click the Excel Services service application.
    
3. Click **Trusted Data Connection Libraries**.
    
4. Click **Add Trusted Data Connection Library**.
    
5. In the **Address** box, paste the URL for the data connection library that you copied in the previous procedure. It should be in the following format:
    
     `https://<ServerName>/<ProjectSiteName>/ProjectBICenter/Data%20Connections/English%20(United%20States)`
    
6. Click **OK**.
    
## Configure Secure Store Service settings
<a name="section4"> </a>

The sample reports included with each instance of Project Web App are configured to use a Secure Store target application called ProjectServerApplication. You must create this target application in order for the sample reports to work. Use the following procedure to create the target application.
  
### To create a Secure Store target application

1. On the SharePoint Central Administration website home page, in the **Application Management** section, click **Manage Services Applications**.
    
2. Click the Secure Store Service.
    
3. On the Secure Store Service page, select the **Edit** tab.
    
4. Click **New**.
    
5. On the Create New Secure Store Target Application page:
    
1. In the **Target Application ID** box, typeProjectServerApplication.
    
2. In the **Display Name** box, type a name for the Secure Store Target Application.
    
3. In the **Contact Email** box, type an email address.
    
4. From the **Target Application Type** drop-down list, select **Group**.
    
5. Click **Next**.
    
6. On the Specify the credential fields for your Secure Store Target Application page, click **Next**.
    
7. On the Specify the membership settings page:
    
1. In the **Target Application Administrators** box, type the name of the user who will administer this target application.
    
2. In the **Members** box, type the name of the domain group you created for report viewers.
    
3. Click **OK**.
    
8. On the Secure Store Service Application page, select the check box for the target application that you just created.
    
9. On the ribbon, in the **Credentials** section, click **Set**.
    
10. On the **Set Credentials for Secure Store Target Application (Group)** dialog box, type the user name and password of the account you created for the secure store target application.
    
    > [!IMPORTANT]
    > This account must have **PSDataAccess** permissions on the Project Web App database. We recommend that you add this account to the Report Authors Active Directory group to give it the required permissions.
  
11. Click **OK**.
    
## Populate the Report Authors and Report Viewers Active Directory groups
<a name="PopulateADGroups"> </a>

To provide your users with the needed access to the Business Intelligence Center in Project Web App and the reports within, you must populate the Report Authors and Report Viewers Active Directory groups as follows:
  
- Report Authors group: Add the Active Directory accounts of users who will be creating reports using Excel.
    
- Report Viewers: Add the Active Directory accounts of Project Web App users who will be viewing reports in the Business Intelligence Center.
    
    > [!NOTE]
    > If your report authors will also be viewing reports, you can add the Report Authors group to the Report Viewers group in Active Directory. 
  
## OLAP cube access
<a name="PopulateADGroups"> </a>

If you plan to use SQL Server Analysis Services OLAP cubes with Project Web App, then you must configure cube access for your users. For more information, see [Configure OLAP cubes for Project Web App](configure-olap-cubes-for-project-web-app.md).
  
## See also
<a name="PopulateADGroups"> </a>

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)