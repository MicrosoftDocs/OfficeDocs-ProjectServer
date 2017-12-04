---
title: "What's new in Project Server 2013 upgrade"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/21/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 1722bfce-85a3-477a-8d13-680f22284671
description: "Summary: Learn about key changes and considerations when you upgrade to Project Server 2013."
---

# What's new in Project Server 2013 upgrade
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** Learn about key changes and considerations when you upgrade to Project Server 2013.
  
Upgrading to Project Server 2013 differs in many ways from upgrading to previous versions of Project Server. When you upgrade to Project Server 2013, it is important to consider the following:
  
- [Database-attach is the supported method for upgrading to Project Server 2013](#section1)
    
- [Upgrade from Project Server 2010 to Project Server 2013 includes database consolidation to a single database](#section2)
    
- [Upgrade from Office Project Server 2007 to Project Server 2013 involves two major steps](#section3)
    
- [ Client compatibility with Project Server 2013](#section4)
    
- [Upgrade from Project Server 2010 to Project Online](http://technet.microsoft.com/library/d42b8778-87ee-4e09-8b9e-cb2d1d800db9.aspx#Online)
    
- [Known issues when you upgrade to Project Server 2013](#section5)
    
## Database-attach is the supported method for upgrading to Project Server 2013
<a name="section1"> </a>

When you upgrade to Project Server 2013, database-attach upgrade is the only supported method. Database-attach upgrade lets you attach your required databases to your Project Server 2013 farm, and then upgrade the databases. Database-attach upgrade requires you to install a "destination environment"—a Project Server 2013 farm.
  
> [!NOTE]
> In-place upgrade (where the Project Server binary files are upgraded on the same hardware) is not a supported method for upgrading to Project Server 2013. 
  
When you upgrade to Project Server 2013, you are required to use the following databases from your Project Server 2010 environment:
  
- Project Server 2010 Archive
    
- Project Server 2010 Draft
    
- Project Server 2010 Published
    
- Project Server 2010 Reporting
    
- SharePoint Content database containing the Project Web App site data
    
> [!IMPORTANT]
> When you upgrade to Project Server 2013, full database-attach upgrade (sometimes referred to as "five database-attach") is used. This means that the SharePoint Content database that contains the Project Web App site data, and the Project Server 2010 databases, is required for upgrade. The SharePoint Content database must be used, or else project details pages and workflows will not function. Also, all project workspaces will not be available, along with associated documents, lists, risks, issues, and deliverables. 
  
## Upgrade from Project Server 2010 to Project Server 2013 includes database consolidation to a single database
<a name="section2"> </a>

Project Server 2013 architecture has been improved to reduce total cost of ownership (TCO) for database maintenance. In Project Server 2010 and Office Project Server 2007, each PWA instance hosted a majority of its project data on the four Project Server databases (Draft, Publish, Reporting, and Archive). When you upgrade to Project Server 2013, your four Project Server 2010 databases are merged into a single Project Web App database (default name: ProjectWebApp). The reduction in the number of databases required to run Project Server 2013 equates to a reduction in the costs to maintain, update, back up, and plan for disaster recovery for your Project Server 2013 data. 
  
> [!NOTE]
> For information about recommended hardware requirements for your database tier in Project Server 2013, see [Software requirements for Project Server 2016](software-requirements-for-project-server-2016.md). 
  
## Upgrade from Office Project Server 2007 to Project Server 2013 involves two major steps
<a name="section3"> </a>

There is no direct upgrade path from Office Project Server 2007 to Project Server 2013. When you upgrade from Office Project Server 2007, you must first upgrade to Project Server 2010, then upgrade the required databases to Project Server 2013.
  
For information about how to upgrade from Office Project Server 2007 to Project Server 2010, see the following resources:
  
- [Upgrade and Migration for Project Server 2010 TechNet Resource Center](https://technet.microsoft.com/en-us/projectserver/ee691958.aspx): This site contains links to all Project Server 2010 upgrade technical content on Microsoft TechNet. 
    
- [Microsoft Project Server 2010 Upgrade SuperFlow](https://go.microsoft.com/fwlink/p/?LinkId=253657): An interactive Help file that you can download and install on your local computer. It contains the Project Server 2010 TechNet upgrade content set, made viewable to the user through logically organized category tabs and sequential data flow objects. 
    
## Client compatibility with Project Server 2013
<a name="section4"> </a>

Note the following in regards to Project Professional and Project Web App client compatibility to Project Server 2013:
  
- Project Server 2013 will only accept connections from Project Professional 2013.
    
- Project Web App users in Project Server 2013 will be able to use the all browsers that are supported for use with SharePoint Server 2013. These include the following:
    
  - Internet Explorer 10
    
  - Internet Explorer 9
    
  - Internet Explorer 8
    
  - FireFox 10
    
  - Mac Safari 5
    
  - Google Chrome 17
    
> [!NOTE]
> For more information about client connectivity, see [Plan for upgrade to Project Server 2016](plan-for-upgrade-to-project-server-2016.md). 
  
## Upgrade from Project Server 2010 to Project Online
<a name="Online"> </a>

The release of Project Server 2013 is also paired with the release of a new service in Office 365 for enterprises, Project Online. With Project Online in Office 365, all operational maintenance is handled through an online service that is hosted in Microsoft datacenters. Project Online in Office 365 delivers full Project Portfolio Management (PPM) capabilities (Demand Management, Portfolio Management, Resource Management, Reporting, and so on). Portfolio managers, project managers, and team members can access Project Online from anywhere with an Internet connection.
  
Project Server 2010 customers may want to upgrade from their on-premises environment to Project Online in Office 365. Upgrading your on-premises environment to Project Online in Office 365 is done through 3rd party tools. For more information about available 3rd party tools, see the MSDN blog post [Want to test-drive Project Online? How to migrate data from on-premises to Online](https://blogs.msdn.com/b/jkalis/archive/2012/09/30/evaluating-project-online-need-data-how-about-your-data.aspx). 
  
## Known issues when you upgrade to Project Server 2013
<a name="section5"> </a>

The following are current known issues that occur when you upgrade to Project Server 2013: 
  
- Upon completing the upgrade from Project Server 2010 to Project Server 2013, if you click **New** in the PWA ribbon, you only see the Basic Project Plan Enterprise Project Type (EPT). You do not see other project types that are available in Project Server 2013. The workaround for this issue is to manually add the Project Server 2013 EPTs. For more information about this workaround, see[Post-upgrade tasks: Address known issue with Enterprise Project Types (Project Server 2013)](http://technet.microsoft.com/library/2d27658e-cf30-4f9f-8768-39de5a41e22f.aspx). 
    
- When you upgrade your Project Server 2010 databases to Project Server 2013, your Project Server 2010 databases must be in native mode (not backward compatibility mode). If your Project Server 2010 databases are in backward compatibility mode (BCM) when you upgrade, you may experience some issues (such as missing pages) with your sites after upgrade, because BCM is not a supported feature in Project Server 2013. For more information about this issue, see [Prepare your environment for an upgrade to Project Server 2013](http://technet.microsoft.com/library/587325fd-c15f-4347-a247-92abbf23fb76.aspx)
    
    > [!NOTE]
    > For more information about backward compatibility mode, see [Project Server 2010 backward compatibility mode](https://technet.microsoft.com/en-us/library/gg502585%28v=office.14%29.aspx). 
  
- If your Project Server 2010 Published database contains resource accounts in which the  `WRES_Account` field contains an empty string (expected value is NULL), upgrade of this database will fail. We recommend that you check for this condition before attempting an upgrade, especially if you had upgraded resource accounts from Office Project Server 2007 to Project Server 2010 in the past. If your upgrade to Project Server 2013 fails because of this condition, you cannot use the same copies of your Project Server 2010 databases to fix the issue and retry upgrade. You must restore the original Project Server 2010 databases to the SQL Server, fix the condition, and then retry the upgrade.
    
    To check for this condition, run the following SQL script on the backup copy of your Project Server 2010 Published database:
    
  ```
  Use ProjectServer_Published
select RES_Name, RES_TYPE, RES_ID from MSP_RESOURCES where WRES_ACCOUNT =''

  ```

    If accounts with this condition are found, run the following SQL script on the same database to fix the accounts:
    
  ```
  Use ProjectServer_Published
Update MSP_RESOURCES set WRES_ACCOUNT = null where WRES_ACCOUNT =''

  ```

## Project Server forums and documentation feedback
<a name="section5"> </a>

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also
<a name="section5"> </a>

#### 

[Plan for upgrade to Project Server 2016](plan-for-upgrade-to-project-server-2016.md)
  
[Overview of the Project Server 2016 upgrade process](overview-of-the-project-server-2016-upgrade-process.md)
#### 

[Prepare your environment for upgrade (Project Server 2013)](http://technet.microsoft.com/library/587325fd-c15f-4347-a247-92abbf23fb76.aspx)

