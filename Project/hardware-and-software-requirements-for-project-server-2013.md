---
title: "Hardware and software requirements for Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/14/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: bde05c8a-0312-4f46-ace9-ade6ba1edd3c

description: "Summary: Verify that your computer meets the hardware and software requirements that are listed in this article when you try to install Project Server 2013."
---

# Hardware and software requirements for Project Server 2013
 
 **Summary:** Verify that your computer meets the hardware and software requirements that are listed in this article when you try to install Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
This article describes the following requirements:
  
- Hardware requirements:
    
  - Small dataset hardware recommendations
    
  - Medium dataset hardware recommendations
    
  - Large dataset hardware recommendations
    
- Software requirements:
    
  - Operating system
    
  - SharePoint Server 2013
    
  - SQL Server
    
  - Requirements for Project Server 2013 features
    
- Client requirements:
    
  - Project Professional client compatibility
    
  - Project Professional 2013installation requirements
    
  - Project Professional 2013 through Office 365 ProPlus
    
  - Project Web App requirements
    
- Project Server 2013 with the Microsoft Azure platform
    
## Hardware requirements for Project Server 2013
<a name="section1"> </a>

When you plan for the hardware that is required for a Project Server 2013 deployment, as a starting point, you should determine the usage requirements for your Project Server 2013 environment. These variables include the number of projects, tasks, users, average tasks per project, and so on. By using the [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md) tables, you can compare the numbers from your environment to the data for small, medium, and large datasets defined in their corresponding table. By selecting the dataset that most resembles the usage requirements in your environment, you can use the recommended topology and associated hardware requirements for your topology as a starting point when you plan for hardware for your Project Server 2013 deployment.
  
This section specifies the hardware requirements for a Project Server 2013 deployment based on the datasets defined in [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md).
  
> [!NOTE]
> The minimum hardware requirements in this section are recommended in which only the required services to run Project Server 2013 are enabled. Be aware that enabling additional SharePoint Server 2013 features in the farm may require more resources. For more information about hardware and software requirements for SharePoint Server 2013, see [Hardware and software requirements for SharePoint 2013](http://technet.microsoft.com/library/4d88c402-24f2-449b-86a6-6e7afcfec0cd.aspx). 
  
### Small dataset hardware recommendations for Project Server 2013

The following are the recommended hardware requirements for a Project Server 2013 small dataset scenario. See [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md) for more information about how the small dataset size is defined.
  
#### Minimum requirements for hardware for small datasets in Project Server 2013

The minimum hardware topology for a small dataset scenario is a single-server deployment that contains the following three tiers:
  
- SQL Server
    
- Application server
    
- Front-end web server
    
The minimum recommended hardware requirements for the servers in this dataset are as follows:
  
**Minimum hardware requirements for a small dataset in Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |24 GB for developer and evaluation use  <br/> |
|Hard disk  <br/> |80 GB for installation  <br/> For production use, you need additional free disk space for day-to-day operations. Add two times as much free space as you have RAM for production environments.  <br/> |
   
#### Recommended hardware for Project Server 2013 for a small dataset

Project Server 2013 runs as a service application on SharePoint Server 2013, and usage by other service applications generates additional resource usage (processor, RAM, and hard disk). While the minimum recommended requirements are suitable for a small dataset with light usage, more substantial datasets and usage patterns may require additional hardware resources. For a single-server deployment with a small dataset, we advise 16 GB of RAM to assure a high level of perceived performance.
  
We recommend that, if possible, you separate your SQL Server tier from the Application and front-end web tiers by placing your databases onto a dedicated computer that is running SQL Server.
  
- Server 1: Application and front-end web
    
- Server 2: SQL Server
    
For a two-tiered deployment supporting a small dataset, we recommend the following hardware requirements:
  
**Front-end web and Application server hardware recommendations for Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**SQL Server hardware recommendations for Project Server 2013 for a small dataset**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core (If your dataset size is significantly larger than the medium dataset, we recommend 8 cores.)  <br/> |
|RAM  <br/> |16 GB  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
### Medium dataset hardware recommendations for Project Server 2013

The following are the recommended hardware requirements for a Project Server 2013 medium dataset scenario. See [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md) for more information about how the medium dataset size is defined.
  
#### Minimum requirements for hardware for medium datasets for Project Server 2013

The minimum recommended hardware topology for a medium dataset scenario is a three-tier deployment that contains a dedicated server for each of the following:
  
- Server 1: Front-end web server
    
- Server 2: Application server
    
- Server 3: SQL Server 
    
    
For a three-tier deployment supporting a medium dataset, the following are the hardware minimum requirements:
  
**Minimum hardware requirements for a Front-end web server for a medium dataset deployment of Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single server and multiple server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**Minimum hardware requirements for an Application server for a medium dataset deployment of Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core  <br/> |
|RAM  <br/> |8 GB for developer or evaluation use  <br/> 16 GB for single-server and multiple-server farm installation for production use  <br/> |
|Hard disk  <br/> |80 GB  <br/> |
   
**Minimum hardware requirements for the SQL Server tier for a medium dataset deployment of Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, four-core, 2.5 GHz minimum per core (If your dataset size is significantly larger than the medium dataset, we recommend 8 cores.)  <br/> |
|RAM  <br/> |16 GB  <br/> |
|Hard disk  <br/> |100 GB  <br/> |
   
#### Recommended hardware for Project Server 2013 for a medium dataset

As a general prescription, you should prepare to handle additional user load and data load by having sufficient computers to add more front-end web servers and Application servers to your topology. The hardware specifications of your front-end web servers and Application servers can remain largely the same. A 4x2x1 topology (four front-end web servers, two Application servers, and one computer that is running SQL Server) should be sufficient for handling the needs of most medium data sets and usage patterns. However, scaling out your Application and front-end web servers will add more load to the SQL Server tier, which you will have to compensate for by adding more memory and CPU resources. The following SQL Server specification should be able to handle the performance needs of most medium datasets.
  
**SQL Server hardware recommendations for Project Server 2013 for a medium dataset**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor  <br/> |64-bit, eight-core, 2.5 GHz minimum per core (If your dataset size is significantly larger than the medium dataset, we recommend 8 cores.)  <br/> |
|RAM  <br/> |32 GB  <br/> |
|Hard disk  <br/> |160 GB  <br/> NOTE - Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks. <br/> NOTE - RAID 5 should provide a good compromise between reliability, and throughput.           |
   
Additionally, if the SharePoint Server 2013 instance on which Project Server 2013 is coexisting with also experiences heavy usage (for example, you are not using the instance specifically for Project Server 2013 functionality), we recommend a separation of the ProjectService database and the SharePoint Server 2013SharePoint Server 2016 content databases. This requires you to place them on two dedicated computers that are running SQL Server.
  
### Large dataset hardware recommendations in Project Server 2013

The following are the recommended hardware requirements for a Project Server 2013 large dataset scenario. See [How datasets affect performance and capacity in Project Server 2013](how-datasets-affect-performance-and-capacity-in-project-server-2013.md) for more information about how the large dataset size is defined.
  
For large datasets, data load is the biggest concern. At a minimum, for large datasets you will want a 4×2×1 topology. The hardware characteristics of the front-end web and Application servers can generally remain the same as those recommended for the small and medium datasets. However, because the SQL Server tier will be the bottleneck, you may find that this constrains your ability to scale out to additional front-end web and Application servers. If data load is the bottleneck, you may find that additional front-end web and Application servers do not produce an improvement in throughput. 
  
For a large data set, we recommend that you invest in additional resources on the SQL Server tier of your topology. You can "scale-up" your SQL Server by adding additional RAM, CPU and hard disk resources.
  
The following are the minimum and recommended specifications for the SQL Server tier of a large dataset topology. 
  
#### Minimum requirements for hardware for large datasets in Project Server 2013

**Minimum hardware requirements for the SQL Server tier for a large dataset deployment of Project Server 2013**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor |64-bit, four-core, 2.5 GHz minimum per core (If your dataset size is significantly larger than the medium dataset, we recommend 8 cores.)|
|RAM|32 GB |
|Hard disk|250 GB <br/> NOTE - Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks. <br/> NOTE - RAID 5 should provide a good compromise between reliability, and throughput.           |
   
#### Recommended hardware for Project Server 2013 for a large dataset

**SQL Server hardware recommendations for Project Server 2013 for a large dataset**

|**Component**|**Minimum requirement**|
|:-----|:-----|
|Processor |64-bit, eight-core, 2.5 GHz minimum per core (If your dataset size is significantly larger than the medium dataset, we recommend 8 cores.)|
|RAM|64 GB |
|Hard disk|300 GB or more <br/>NOTE - Ideally, you should separate and prioritize data among disks. Place your data files and your SQL Server transaction logs on separate physical hard disks. <br/>NOTE - RAID 5 should provide a good compromise between reliability, and throughput.           |
   
## Software requirements for Project Server 2013
<a name="section8"> </a>

This section describes the software requirements for Project Server 2013. This includes the following: 
  
- Operating system
    
- Database server (SQL Server)
    
- SharePoint Server 2013
    
- Software requirements for Project Server 2013 feature usage
    
### Operating system

Project Server 2013 runs on the following server operating systems:
  
- Windows Server 2012(64-bit)
- Windows Server 2008 R2(64-bit) with a minimum service-pack level of Service pack 1. 
    
**Supported Windows Server 2012 editions**

- Windows Server 2012, Standard Edition (64-bit)  
- Windows Server 2012, Datacenter Edition (64-bit) 

**Supported Windows Server 2008 R2 editions**

- Windows Server 2008 R2 SP1, Standard Edition (64-bit)
- Windows Server 2008 R2 SP1, Enterprise Edition (64-bit)
- Windows Server 2008 R2 SP1, Datacenter Edition (64-bit)
   
> [!NOTE]
> Server Core installations of Windows Server 2008 R2 are not supported. 
  
> [!IMPORTANT]
> SharePoint Server 2013 and Project Server 2013 are available only in 64-bit editions, and they require 64-bit editions of Windows Server 2008 R2 or Windows Server 2012. 
  
#### Windows Server server roles

Project Server 2013 requires the following Windows Server server roles on each Application server in the farm:
  
**Required server roles for Application servers**

- Application server role
- Web Server role with Internet Information Services (IIS) 6 Management Compatibility enabled
   
In addition to these server roles, Project Server 2013 also requires that Microsoft PowerShell be enabled.
  
> [!NOTE]
> Both the server roles and Microsoft PowerShell are configured automatically by the SharePoint Server 2013 prerequisite installation tool if they are not already enabled. 
  
> [!NOTE]
> For more information about Windows Server 2008 R2, see the [Windows Server 2008 R2](https://go.microsoft.com/fwlink/p/?LinkId=780779) on Microsoft TechNet.
  
### SharePoint Server 2013

Project Server 2013 runs as a SharePoint Server 2013 service application. Therefore, SharePoint Server 2013 Enterprise is a prerequisite for Project Server 2013 installation. Prior versions of SharePoint Server and SharePoint Foundation 2013 are not supported. 
  
> [!NOTE]
> For more information about SharePoint Server 2013 hardware and software requirements, see [Hardware and software requirements (SharePoint 2013)](http://technet.microsoft.com/library/4d88c402-24f2-449b-86a6-6e7afcfec0cd.aspx). 
  
### Requirements for the database server (SQL Server)

For database servers, Project Server 2013 (and SharePoint Server 2013) supports use with the following versions of SQL Server:
  
**SQL Server versions supported for Project Server 2013**

- SQL Server 2012 (64-bit)
- SQL Server 2008 R2 with Service Pack 1 (SP1) (64-bit)  
- SQL Server 2014 (64-bit)   
> NOTE - SQL Server 2014 support requires Project Server 2013 with Service Pack 1.           
   
The following components of SQL Server are required:
  
- Database Engine
    
- Analysis Services
    
- Management tools
    
- Connectivity components
    
The SQL Server Agent service must be running.
  
If you plan to upgrade from a Project Server 2010 environment, be aware that Project Server 2013 does not support SQL Server 2005.
  
> [!NOTE]
>  For more information about SQL Server, see the following Microsoft TechNet Home pages:> [SQL Server 2008 R2](https://go.microsoft.com/fwlink/p/?LinkId=780780)> [SQL Server 2012](https://go.microsoft.com/fwlink/p/?LinkId=780781)
  
### Software requirements for Project Server 2013 feature usage

The following table describes software requirements for use of specific Project Server 2013 features that you may want to use.
  
|**Feature**|**Required software**|**Configuration notes**|
|:-----|:-----|:-----|
|My Tasks (task synchronization with Exchange Server 2013, Project Server 2013, and SharePoint Server 2013)  <br/> | Server requirements: Exchange Server 2013 <br/>  Desktop requirements (supported Outlook versions): <br/>  Outlook 2013 <br/>  Outlook 2010 <br/>  Microsoft Office Outlook 2007 <br/>  Microsoft Office Outlook 2003 <br/>  Mobile requirements (supported mobile operating system versions): <br/>  Windows Phone 7.5 or newer <br/>  iApple: OS 5 or newer <br/>  Android 2.3 or newer <br/> |The Work Management Application service must be enabled.  <br/> Exchange Server 2013 and SharePoint Server 2013 have to be on the same domain together with the Auto Discover server configured and functional.  <br/> IMPORTANT - For Exchange Server 2013 integration with Project Server 2013, hybrid deployment is not supported. Exchange Server 2013 must be integrated either in an on-premises environment or online. An on-premises integration of Exchange Server 2013 will not support Project Online users.           |
|Active Directory Synchronization (Resources and security groups)  <br/> | The domain controller must be one of the following operating systems: <br/>  Windows Server 2012 R2 <br/>  Windows Server 2012 <br/>  Windows Server 2008 R2 <br/>  Windows Server 2008 <br/>  Windows Server 2003 <br/> ||
|Reporting  <br/> | On premises (supported versions): <br/>  Excel 2013 <br/>  Excel 2010 <br/>  Project Online: <br/>  Excel 2013 only <br/> |Reporting through the OData service (for both Project Server 2013 on-premises and Project Online) requires Excel 2013.  <br/> For more information about Reporting in Project Server 2013, see [Plan reporting and business intelligence in Project Web App](plan-reporting-and-business-intelligence-in-project-web-app.md).  <br/> For more information about software requirements for using business intelligence for your reports, see [Software Requirements for business intelligence](http://technet.microsoft.com/library/6824b3bf-9046-4d43-b266-de463d0007e5.aspx).  <br/> |
|Lync presence in Project Web App or Project Professional  <br/> | One of the following: <br/>  Lync 2013 with Internet Explorer 10, Internet Explorer 9, Internet Explorer 8, Mozilla Firefox (latest released version), or Google Chrome (latest released version). <br/>  Lync 2010 with Internet Explorer 10, Internet Explorer 9 or Internet Explorer 8. <br/>  Internet Explorer 9, Internet Explorer 8, Mozilla Firefox (latest released version), and Google Chrome (latest released version) with any Office 2013 application will provide the user a contact card, but no Skype for Business presence. <br/> NOTE - Skype for Business presence and contact card do not work in the new Internet Explorer interface in Windows 8.x, but do work on the traditional Desktop Internet Explorer 10.          ||
|Workflow editing  <br/> | Requires both of the following: <br/>  SharePoint Designer 2013 <br/>  Microsoft Visio 2013 <br/> ||
   
## Client requirements for Project Server 2013
<a name="section8"> </a>

When you are planning system requirements for Project Server 2013, you must also consider hardware and software requirements for the client users who need to connect to the server. These client users include the following:
  
- Project Professional 2013 users
    
- Project Web App users
    
### Project Professional client compatibility with Project Server 2013

If you plan to upgrade from an earlier version of Project Server, you must consider whether your current Project Professional clients will be compatible with Project Server 2013.
  
|**Project Server version**|**Supported Project Professional version**|**Note**|
|:-----|:-----|:-----|
|Project Server 2013  <br/> | Project Professional 2016 <br/>  Project Professional 2013 <br/>  Project Online Desktop Client <br/> |Note that the same clients are supported to connect to Project Server 2016. For more information, see [Software requirements for Project Server 2016](https://go.microsoft.com/fwlink/p/?LinkId=722930).  <br/> |
|Project Server 2010  <br/> | Project Professional 2010 <br/>  Office Project Professional 2007 with Service Pack 2 <br/> |Project Professional 2007 with Service Pack 2 can only connect to Project Server 2010 when backward compatibility mode is enabled on the server.  <br/> |
|Project Server 2007  <br/> |Office Project Professional 2007  <br/> ||
   
Plan for these two considerations when planning for Project Professional client connectivity:
  
- Project Server 2013 does not provide a "backward compatibility" connectivity feature for any previous Project Professional client versions. 
    
- Project Professional 2013 does not connect to Project Server 2010.
    
### Project Professional 2013 installation requirements

Project Professional 2013 has the following installation requirements:
  
**Project Professional 2013 installation requirements**

|||
|:-----|:-----|
|Computer and Processor  <br/> |1 GHz or faster x86/x64 processor with SSE2 instruction set  <br/> |
|Memory  <br/> | 1 GB RAM (32-bit) <br/>  2 GB RAM (64-bit) <br/> |
|Hard disk  <br/> |2 GB available  <br/> |
|Operating system  <br/> | Supported versions: <br/>  Windows 7 <br/>  Windows 8 <br/>  Windows 8.1 <br/>  Windows 10 <br/>  Windows Server 2008 Release 2 <br/> NOTE -  With .NET Framework version 3.5 or 4.0          |
|Graphics  <br/> |Graphics hardware acceleration requires DirectX10 graphics card  <br/> 1024×576 resolution  <br/> |
|Browser requirements  <br/> | Supported versions: <br/>  Internet Explorer 11 <br/>  Internet Explorer 10 <br/>  Internet Explorer 9 <br/>  Internet Explorer 8 <br/>  Mozilla Firefox (latest released version) <br/>  Apple Safari (latest released version) <br/>  Google Chrome (latest released version) <br/> |
|Visual Reports requirements  <br/> | Office Excel 2007, Excel 2010, or Excel 2013 <br/>  Office Visio 2007, Visio 2010, or Visio 2013 <br/> |
   
> [!NOTE]
> For more information about Project Professional 2013 requirements, see [Microsoft Project Professional 2013](http://technet.microsoft.com/library/399026a3-007c-405a-a377-da7b0f7bf9de.aspx#section12). 
  
### Project for Office 365 requirements

Project for Office 365 is a subscription-based online offering of Project Professional through Office 365. Project for Office 365 has the same system installation requirements as Project Professional. 
  
### Project Web App requirements for Project Server 2013

For Project Web App in Project Server 2013, you can use any of the following supported web browsers:
  
**Supported web browsers for Project Web App**

- Internet Explorer 11 
- Internet Explorer 10
- Internet Explorer 9
- Internet Explorer 8
- Mozilla Firefox (latest released version)
- Apple Safari (latest released version)
- Google Chrome (latest released version)
   
> [!IMPORTANT]
> Project Web App in Project Server 2013 supports the same web browsers that are supported for SharePoint Server 2013. For more information about supported browsers for SharePoint Server 2013, see [Plan browser support (SharePoint 2013)](http://technet.microsoft.com/library/ff6c5b8c-59bd-4079-8f0b-de4f8b4e0a86.aspx). 
  
> [!NOTE]
> Project Web App in Office 365 requires the same supported browsers. 
  
## Project Server 2013 with the Azure platform
<a name="section8"> </a>

You can install Project Server 2013 and SharePoint Server 2013 on the Azure platform. For more information, see [SharePoint on Azure Infrastructure Services](http://go.microsoft.com/fwlink/p/?LinkId=780782&amp;clcid=0x409) in the Azure library.
  
## See also
<a name="section8"> </a>

#### 

[Support and licensing for Azure in SharePoint 2013](http://technet.microsoft.com/library/1157a2c0-133d-45fa-b0bf-14015fb00885.aspx)

