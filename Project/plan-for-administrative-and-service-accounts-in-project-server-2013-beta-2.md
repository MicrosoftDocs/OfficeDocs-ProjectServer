---
title: "Plan for administrative and service accounts in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/29/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: a2388ad0-a39b-486c-9cc9-2a352935a6b6

description: "Summary: Learn about the accounts that you must plan for and the deployment scenarios that affect account requirements in Project Server 2013."
---

# Plan for administrative and service accounts in Project Server 2013
 
 **Summary:** Learn about the accounts that you must plan for and the deployment scenarios that affect account requirements in Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
Use this article to plan for the account requirements and recommendations for accounts that are required to install, configure, and use Project Server 2013.
  
You must provide credentials for these accounts during Setup and configuration. This article does not discuss accounts that you do not have to configure or provide credentials for.
  
## Administrative and service accounts that are required by Project Server 2013

This section lists and describes the accounts that are required by Project Server 2013.
  
> [!NOTE]
> All Project Server 2013 and SharePoint Server 2013 service accounts must be granted interactive logon permissions for the computer where the service is running. By default, such permissions are normally granted when a new account is set up. However, you may have to make manual adjustments if your organization normally denies interactive logon permissions for service accounts. 
  
The following table describes the standard account requirements for Project Server 2013.
  
**Standard account requirements for Project Server 2013**

|**Account**|**Purpose**|**Required permissions**|
|:-----|:-----|:-----|
|Setup user account  <br/> | The user account that is used to run: <br/>  Setup on each server computer <br/>  SharePoint Products Configuration Wizard <br/>  The Psconfig command-line tool <br/>  Log in with this account when you install SharePoint Server 2013 and Project Server 2013. This must be a domain account. <br/> IMPORTANT - This account may already exist if you are deploying Project Server 2013 to an existing SharePoint Server 2013 farm.          | This account must be a member of the local Administrators group on each application server in the farm. <br/>  This account must be: <br/>  a member of the local Administrators group on each application server in the farm. <br/>  A member of the **sysadmin** Server Role in SQL Server. <br/>  If you run Windows PowerShell cmdlets that affect a database, this account must be a member of the **db_owner** fixed database role for the database. <br/> |
|Server farm account  <br/> | This account is also known as: <br/>  Farm administrator account <br/>  Database access account <br/>  This account servers as the following: <br/>  The application pool account for the SharePoint Central Administration Web site <br/>  The process account for the SharePoint 2013 Timer (SPTimerV4) service <br/> IMPORTANT - This account may already exist if you are deploying Project Server 2013 to an existing SharePoint Server 2013 farm.          | Additional permissions are automatically granted for this account when Project Server 2013 is installed and when additional application servers are added to the farm. <br/>  A logon is automatically created for this account in SQL Server, and that logon is automatically added to the following SQL Server Server Roles: <br/> **dbcreator** fixed server role <br/> **securityadmin** fixed server role <br/> **db_owner** fixed database role for all databases in the server farm <br/> |
|Application Pool  <br/> |Runs the application pool associated with the Project Server service application.  <br/> NOTE - This account may already exist if you are deploying Project Server 2013 to an existing SharePoint Server 2013 farm. However, we recommend that you create a separate account for the Project Server service application.           | The following SQL Server roles and permissions are automatically assigned to this account: <br/>  Database owner role for content databases associated with the Web application <br/>  Read/write access to the associated Service Application database <br/>  Read from the configuration database <br/>  Additional permissions for this account on front-end Web servers and application servers are automatically granted by Project Server 2013. <br/> |
|Workflow Proxy  <br/> |Runs Project Server workflow activities. This account makes the Project Server Interface (PSI) calls associated with each workflow.  <br/> NOTE - This account is only used for workflows that use the SharePoint Server 2010 workflow platform.  | This domain account must also be configured as a Project Server user account that has the following permissions: <br/>  Global permissions: <br/>  -Log On <br/>  -Manage Users and Groups <br/>  -Manage Workflow and Project Detail Pages <br/>  Category permissions: <br/>  -Open Project <br/>  -Save Project to Project Server <br/> NOTE - If you are using SharePoint Permission mode, add this account to the Administrators for Project Web App security group. |
   
## Accounts and groups for business intelligence

In addition to the accounts listed earlier in this article, the following accounts and Active Directory directory service groups are required when you configure reporting for Project Server 2013.
  
**Accounts and groups required for reporting in Project Server 2013**

|**Account**|**Purpose**|**Required permissions**|
|:-----|:-----|:-----|
|Report Authors Group  <br/> |Active Directory security group to which you add users who will create reports.  <br/> |This group requires **db_datareader** permissions on the Project Web App database. <br/> |
|Report Viewers Group  <br/> |Active Directory security group to which you add users who will view reports.  <br/> |None. (This group is used as part of Secure Store configuration.)  <br/> |
|External Report Viewers Group  <br/> |(Optional.) Active Directory security group for users who do not have a Project Web App user account but require access to the Project Server 2013 Business Intelligence Center to view reports.  <br/> |This group requires read permissions to the Business Intelligence Center site.  <br/> |
|Secure Store Target Application account  <br/> |This account provides the credentials necessary for report viewers to view reports generated from data in the Project Web App database. This account is used as part of Secure Store configuration.  <br/> |This account must have **db_datareader** permissions on the Project Web App database. We recommend that you add this account to the Report Authors Active Directory group described earlier in this section to give it the necessary permissions. <br/> |
   

