---
title: "Plan for upgrade to Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: cc10a269-8dde-4d1c-b879-5c4cccf0a5bd

description: "Summary: When you upgrade to Project Server 2013, primary things to consider include system requirements and your current environment."
---

# Plan for upgrade to Project Server 2013
 
 **Summary:** When you upgrade to Project Server 2013, primary things to consider include system requirements and your current environment.<br/>
**Applies to:** Project Server 2013
  
When you plan to upgrade to Project Server 2013 from a previous version of Project Server, it is important to consider the following planning areas that are key in ensuring a successful upgrade of your environment:
  
- Review system requirements for upgrade to Project Server 2013
    
- Plan for clients
    
- Gather information about your current environment
    
- Plan for upgrading customizations
    
- Create an upgrade communications plan 
    
## Review system requirements for upgrade to Project Server 2013

When you plan for upgrade, it is important to plan for the following system requirements:
  
- **Upgrading to Project Server 2013 does not support an in-place upgrade option (where the Project Server files are upgraded on the same hardware)** Project Server 2013 will need to be installed in its own environment, to which your Project Server 2010 databases and the SharePoint content database containing your Project Web App site data will be upgraded. You will need to plan for additional hardware and software for the Project Server 2013 "destination environment."
    
- **Review your Project Server 2013 hardware and software requirements** As noted above, upgrading to Project Server 2013 is only through the database attach method, which requires to you install a Project Server 2013 "destination environment." You should review the Project Server 2013 hardware and software requirements to plan for deploying your Project Server 2013 environment. For more information about Project Server 2013 hardware and software requirements, see[Hardware and software requirements for Project Server 2013](hardware-and-software-requirements-for-project-server-2013.md).
    
    > [!NOTE]
    > Verify that you are installing SharePoint Server 2013 and Project Server 2013 on a clean server farm instance that has not previously hosted SharePoint Server 2010. Uninstalling SharePoint Server 2010 does not completely remove all installed files, folders, registry entries and other components. Installing SharePoint Server 2013 and Project Server 2013 on such a server will likely cause issues. It is recommended that you reformat the hard drive and reinstall Windows Server if you do chose to use such a server. 
  
- **Prepare to upgrade your Project Professional client users for the upgrade to Project Server 2013** Project Server 2013 supports client connectivity from Project Professional 2016 and Project Professional 2013. Your Project Professional 2010 users will not be able to connect to Project Server 2013. Project Server 2013 does not provide a backward compatibility feature that allows Project Professional 2010 users to connect. To see Project Professional 2013 installation requirements, see the "Plan for clients" section of this article.
    
## Plan for clients

When you plan to upgrade to Project Server 2013, you must take into account that you may also need to upgrade your clients that you plan on connecting to Project Server 2013. Clients who are connecting through Project Professional or Project Web App may no longer be able to connect with their existing client software or web browser after upgrading to Project Server 2013. 
  
The following client connectivity table describes which versions of Project Professional and Web browsers for Project Web App are supported for use with different versions of Project Server:
  
|**Project Server version**|**Supported Project Professional versions**|**Supported Web browsers for Project Web App**|
|:-----|:-----|:-----|
|Project Server 2013  <br/> | Project Professional 2013 <br/>  Project Professional 2016 <br/>  Project Online Desktop Client <br/> | Internet Explorer 11 <br/>  Internet Explorer 10 <br/>  Internet Explorer 9 <br/>  Internet Explorer 8 <br/>  Mozilla FireFox (latest released version) <br/>  Apple Safari (latest released version) <br/>  Google Chrome (latest released version) <br/> > [!NOTE]>  Project Server 2013 Project Web App supports the same web browsers that SharePoint Server 2013 does.          |
|Project Server 2010  <br/> | Project Professional 2010 <br/>  Project Professional 2007 with Service Pack 2 (only when Backward Compatibility Mode is enabled on Project Server 2010) <br/> | Internet Explorer 11 <br/>  Internet Explorer 10 <br/>  Internet Explorer 9 <br/>  Internet Explorer 8 <br/>  Internet Explorer 7 <br/> > [!NOTE]>  Project Server 2010 Service Pack 1 provides support for the following web browsers for certain team member pages:>  Mozilla FireFox 3.6.8>  Google Chrome 6.0 on Windows 7>  Apple Safari 5 on Mac OS X v10.6>  For more information, see[Plan browser support (Project Server 2010)](/previous-versions/office/project-server-2010/ff631137(v=office.14)).           |
|Project Server 2007  <br/> |Project Professional 2007  <br/> | Internet Explorer 9 <br/>  Internet Explorer 8 <br/>  Internet Explorer 7 <br/>  Internet Explorer 6 <br/> |
   
### Project Professional requirements

Project Server 2013 only accepts connections from Project Professional 2016 and Project Professional 2013. You must upgrade your Project Professional 2010 clients in order to connect to Project Server 2013.
  
The following table shows you the versions of Project Professional that are supported for use with Project Server 2013, Project Server 2010, and Office Project Server 2007.
  
|**Project Server version**|**Supported client version**|**Note**|
|:-----|:-----|:-----|
|Project Server 2013  <br/> | Project Professional 2013 <br/>  Project Professional 2016 <br/>   ||
|Project Server 2010  <br/> | Project Professional 2010 <br/>  Project Professional 2007 with Service Pack 2 (only in backward compatibility mode) <br/> |Will only accept connections from Project Professional 2007 with Service Pack 2 when backward compatibility mode is enabled in Project Server 2010.  <br/> |
   
> [!IMPORTANT]
> Project Server 2013 does not have a backward compatibility feature that enables earlier versions of Project Professional to connect to the server. 

> [!Note]
> Project Online Desktop Client connectivity to Project Server 2013 will expire and no longer be supported after January 13, 2020. 
  
Project Professional 2013 has the following installation requirements:
  
**Project Professional 2013 Installation requirements**

|||
|:-----|:-----|
|Computer and processor  <br/> |1 GHz or faster x86/x64 processor with SSE2 instruction set  <br/> |
|Memory  <br/> | 1 GB RAM (32-bit) <br/>  2 GB RAM (64-bit) <br/> |
|Operating system  <br/> | Windows 7 <br/>  Windows 8 <br/>  Windows 2008 R2 <br/> > [!NOTE]>  Requires .NET 3.5 Framework or greater          |
|Graphics  <br/> |Graphics hardware acceleration requires a DirectX10 graphics card 1024x576 resolution  <br/> |
|Browser  <br/> | Internet Explorer 10 <br/>  Internet Explorer 9 <br/>  Internet Explorer 8 <br/>  FireFox 10 <br/>  Mac Safari 5 <br/>  Google Chrome 17 <br/> |
|Visual reports  <br/> | Excel 2007, Excel 2010, or Excel 2013 <br/>  Microsoft Office Visio 2007, Visio 2010, or Visio 2013 <br/> |
   
> [!NOTE]
> For more information about Project Professional 2013 and other Office 2013 client installation requirements, see [System requirements for Office 2013](/previous-versions/office/office-2013-resource-kit/ee624351(v=office.15)). 
  
### Supported browsers for Project Web App

 The following web browsers are supported for using Project Web App:
  
- Internet Explorer 10
    
- Internet Explorer 9
    
- Internet Explorer 8
    
- FireFox 10
    
- Mac Safari 5
    
- Google Chrome 17
    
> [!IMPORTANT]
> The web browsers in this list are the same that are supported for SharePoint Server 2013. 
  
## Gather information about your Project Server 2010 environment

You should gather current configuration information about your Project Server 2010 environment so that you can recreate it on your new system (the Project Server 2013 destination environment). This can include the following:
  
- Alternate access mappings
    
- Authentication providers and authentication modes in use
    
- Quota templates
    
- Customizations
    
- Managed Paths
    
- Self-service site management settings
    
- Incoming and out-going email settings
    
## Plan to upgrade customizations

Before you upgrade, you must identify and then evaluate the customizations in your Project Server 2010 environment and determine whether you will upgrade them, and how. After you upgrade to your Project Server 2013 test environment, check to see if the customizations you want to migrate can be reapplied. 
  
> [!NOTE]
> For detailed information about how to plan for upgrading customizations, see [Create plan to upgrade customizations (SharePoint 2013)](/SharePoint/upgrade-and-update/create-a-communication-plan-for-the-upgrade-to-sharepoint-2013). 
  
During the upgrade process, several Microsoft PowerShell "test" cmdlets can be run on your databases to verify if specific customizations in your Project Server 2010 environment can cause issues with the upgrade process. In most cases, customizations will not cause the actual upgrade process to fail. 
  
> [!NOTE]
> For more information about Microsoft PowerShell "test" cmdlets and other cmdlets used in the upgrade process, see [Upgrading to Project Server 2016](upgrading-to-project-server-2016.md). 
  
## Create an upgrade communications plan

It is important that you communicate with users during the upgrade process to Project Server 2013. Project Web App users need to know what to expect when they visit the site again after upgrade, and Project Server client (Project Web App and Project Professional) users need to know how they can help prepare for upgrade and what they will have to do after upgrade. All users who access Project Server need to know when the upgrade will occur. As part of the planning process, determine the following:
  
- Who are the members of the upgrade team, what other stakeholders are involved, and who will be affected by the upgrade
    
- What information must the upgrade team have, and when
    
- What information must users and other stakeholders have, and when
    
### Create an upgrade team

For small deployments, the upgrade team might consist of only one person. For larger deployments, on the other hand, several people with different roles can be required, as described in the following list: 
  
- **Server administrators** The server administrator performs most of the upgrade tasks. There must be at least one server administrator on the upgrade team because running the Setup wizard requires someone who is a member of the local Administrators group on each front-end Web server.
    
    > [!NOTE]
    > Farm administrators might not be local administrators for the server. 
  
- **Project Server administrators** Project Server administrators are trained to use the various Project Web App configuration and control features. They are responsible for modifying and maintaining general settings of the EPM application such as enterprise global codes, Project Web App views, Project Professional global settings, and so on.
    
- **SharePoint Server administrator** It is essential to get assistance from a SharePoint administrator. A SharePoint administrator can help you upgrade the SharePoint content database with your Project site data, deal with SharePoint customizations, and make sure that SharePoint Server 2013 is installed and configured properly in your "destination" environment. Many Project Server 2013 features are closely tied with SharePoint Server 2013 (such as My tasks and reporting), and it is important that a SharePoint Server 2013 expert is available after upgrade to test the environment to ensure the upgraded data can accessed and used in it.
    
- **Database administrators** If you have a separate database administration team, you must coordinate with it to schedule the upgrade and perform the upgrade.
    
- **Server security teams** You must coordinate with your security teams, such as the Active Directory directory services team, to verify accounts and permissions or to take advantage of the new policy settings that you can apply for Project Server 2013.
    
- **Client deployment team** Communicate with client deployment teams to coordinate deployments of the new Project Professional client and server applications. The client deployment team also has to verify that all Project Web App users support the new browser requirements (Internet Explorer 7.0 or newer). Backwards compatibility mode (BCM) allows you some flexibility in scheduling your Project Professional client upgrade. This team should also contain a representative for the Project Management Office (PMO).
    
- **Developer staff** If you have custom templates, Web Parts, Web services, or other custom elements associated with your Project Web App sites, you must work with the people responsible for developing or customizing those elements to ensure that you can create new versions of these custom elements or verify that these elements have been upgraded correctly. You must also ensure that custom applications developed to work with Project Server are still functional. This is especially true when you are doing a database-attach upgrade where many of the customizations will have to be redeployed manually to the new environment..
    
- **Project Server users** This group can include general Project Web App users, team members, Project Managers, Timesheet managers, and all other people who access data in Project Server. You must communicate to both Project Professional and Project Web App users about when the upgrade will occur and what they should expect with regard to changes. If you have existing Project Professional 2010 users, you must work with them to upgrade to Project Professional 2013, since backward compatibility mode is not available for clients who connect to Project Server 2013. Prior to the upgrade process, you must inform users of tasks that they should do to ensure that the project data that they work with is in an upgradeable state. Communicating pre-upgrade tasks to end-users (for example, "ensure that all projects are checked in") helps prevent problems during the upgrade.
    
- **Network engineers** Network engineers must work with server administrator to do tasks such as creating new DNS entries, and so on.
    
- **Sponsors and other stakeholders** You might have other people in your organization involved in the upgrade planning process. Make sure that you include them in your communication plan appropriately.
    
    > [!NOTE]
    > An upgrade team can include one or more members in each role, depending on your organization. 
  
### What and when to communicate to the upgrade team

In general, the farm administrators and service application administrators set the timeline for upgrade, and site owners are notified only when the process is about to begin. However, because team members have their own tasks to perform at particular points in the overall upgrade process, make sure that you have a solid plan to communicate the progress of the upgrade to all team members so that everyone knows when it is time to perform their particular tasks. 
  
The whole upgrade team must work together to determine the following:
  
- **Dates and times to perform the upgrade** We recommend that you upgrade when site usage is low. For small single-server deployments, upgrade may be completed in less than a day. For larger deployments, such as server farms with large amounts of data, it can take much longer. There is no way to determine the precise length of time that will be required to upgrade. Because of this, it is very important to communicate with other team members involved in the upgrade process in addition to end-users. The day or days that you choose for upgrading should be far enough in the future that the upgrade team has enough time to complete all of the preliminary steps. When you plan the timeline, make sure that you schedule time to validate the upgraded Project Web App site and project data and also schedule time to implement any changes. Also note that you may need to upgrade Project Server client to access Project Server 2013. This can include upgrading Project Professional and Internet Explorer 6.0 users. For more information, see the Plan for Clients section of this article.
    
- **The upgrade approach to use**
    
It is important to communicate with site owners, designers, and developers at the following points during the upgrade process:
  
- Before the process starts, so that they know the general timeline and what their roles in the process will be.
    
- After the upgrade, so that they can validate their upgraded data and the Project Web App site, and can make any changes that are needed. 
    
### What and when to communicate to users

It is equally important to communicate with the Project Server users about the following issues: 
  
- **When their sites will be upgraded** Users must be informed that they will be unable to access data during the upgrade (for example, over the weekend). You must also inform users to leave the data in a state that is ready for migration. (For example, all projects should be checked in, and pending timesheet and status updates should be approved or denied.) This helps eliminate problems that might occur during the upgrade.
    
- **When to expect Project Server 2013 to be ready to access** "Ready to access" means that the upgrade team has not only upgraded but also verified the functionality after the upgrade. You must also prepare information that is required for users to connect to the upgraded version such as a new URL for the Project Web App site.
    
- **How the upgrade might affect them and what they should know about the new environment** For example, the Project Web App site will look different and function slightly differently in the new user interface. You can prepare training materials, such as quick reference sheets, to prepare users for any changes that might have occurred in the processes they do in Project Server. You can also point them to available content, such as "What's New" articles, to learn about the new version.
    
- **How to get help** If users find an issue with the data after the upgrade, where can they go for information or help?
    
### Microsoft Gold Certified Partners

Microsoft has certified several partner companies as experts for EPM deployments and system migrations. You can find partners on the Microsoft Web site by searching for EPM solution providers at [Microsoft Solution Marketplace](https://go.microsoft.com/fwlink/p/?LinkId=187521) (https://go.microsoft.com/fwlink/p/?LinkId=187521).
  
## Project Server forums and documentation feedback

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.
  
If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.
  
![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)
  
## See also

#### 

[Overview of the Project Server 2013 upgrade process](overview-of-the-upgrade-process-to-project-server-2013.md)
#### 

[Prepare your environment for upgrade (Project Server 2013)](./prepare-your-environment-for-an-upgrade-to-project-server-2013.md)