---
title: "Software requirements for Project Server 2019"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 7/24/2018
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 32d82f51-546a-42a3-ade5-54cc4dfdcb87
description: "Summary: Learn about installation requirements for Project Server 2019."
---

# Software requirements for Project Server 2019
 
 **Summary:** Learn about installation requirements for Project Server 2019.<br/>
**Applies to:** Project Server 2019 
  
## Key Requirements

In previous versions of Project Server, Project Server was installed separately after you installed SharePoint Server, as SharePoint Server was a requirement. Project Server 2019 installation is now a part of the SharePoint Server 2019 Enterprise installation process. The installation files for Project Server 2019 are included in the SharePoint Server 2019 Enterprise MSI file, and it is installed along with it. 
  
> [!IMPORTANT]
> Project Server 2019 can only be enabled on the Enterprise version of SharePoint Server 2019. You will not be able to enable Project Server 2019 on SharePoint Server 2019 with a Standard license. 
  
Since Project Server 2019 is part of the SharePoint Server 2019  installation, requirements for Project Server 2019 (including supported browsers, operating systems, and database servers) will be the ones specified for SharePoint Server 2019. 
  
Some of the key software requirements for SharePoint Server 2019 are:
  
|||
|:-----|:-----|
|**Supported Server Operating Systems:**  <br/> | Windows Server 2016 Standard or Datacenter <br/>  Windows Server 2019 Standard or Datacenter <br/> |
|**Supported Database Server:**  <br/> | Microsoft SQL Server 2017 RTM for Windows Services<br/> Microsoft SQL Server 2016 with Service Pack 1 <br/>  Note: SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server 2019. <br/> |
|**Supported browsers:**  <br/> | Microsoft Edge <br/>  Microsoft Internet Explorer 11 <br/> Google Chrome (latest released version) <br/>  Mozilla Firefox (latest released version plus immediate previous version) <br/>  Apple Safari (latest released version) <br/> |
   
> [!NOTE]
> For information about the hardware, software, and browser requirement for SharePoint Server 2019, see [System requirements for SharePoint Server 2019](https://docs.microsoft.com/sharepoint/install/hardware-and-software-requirements-2019). 
  
## Client Compatibility

You can connect to Project Server 2019 with not only Project Professional 2019 and the Project Online Desktop Client, but also with Project Professional 2016.
  
 
|||
|:-----|:-----|
|**Version** <br/> |**Compatible with** <br/> |
|Project Server 2019<br/> |Project Professional 2019 <br/> Project Professional 2016 <br/>  Project Online Desktop Client <br/> <br/> |


   

## Cube Building Service requirements

SQL Server 2016 Analysis Services must also be installed on your SQL Server 2016 database server for your SharePoint Server 2019 Enterprise deployment if you plan to use the Cube Building Service in Project Server 2019.
  

  
## Portfolio Analysis Requirements

For charts to render correctly in your browser when using Portfolio Analysis in Project Server 2019, the State Service needs to be running in your SharePoint farm. 
  
## See also

#### 

[Deploy Project Servers 2016 or 2019](deploy-project-server-2016.md)

[Hardware and software requirements for SharePoint Server 2019](https://docs.microsoft.com/sharepoint/install/system-requirements-for-sharepoint-server-2016)
  
[Plan browser support in SharePoint Server 2019](https://docs.microsoft.com/sharepoint/install/browser-support-planning-0)

