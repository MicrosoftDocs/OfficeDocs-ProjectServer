---
title: "Software requirements for Project Server 2019 Public Preview"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 7/24/2018
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 32d82f51-546a-42a3-ade5-54cc4dfdcb87
description: "Summary: Learn about installation requirements for Project Server 2019 Public Preview."
---

# Software requirements for Project Server 2019 Public Preview
 
 **Summary:** Learn about installation requirements for Project Server 2019 Public Preview.<br/>
**Applies to:** Project Server 2019 Public Preview
  
## Key Requirements

In previous versions of Project Server, Project Server was installed separately after you installed SharePoint Server, as SharePoint Server was a requirement. Project Server 2019 Public Preview installation is now a part of the SharePoint Server 2019 Public Preview Enterprise installation process. The installation files for Project Server 2019 Public Preview are included in the SharePoint Server 2019 Public Preview Enterprise MSI file, and it is installed along with it. 
  
> [!IMPORTANT]
> Project Server 2019 Public Preview can only be enabled on the Enterprise version of SharePoint Server 2019 Public Preview. You will not be able to enable Project Server 2019 Public Preview on SharePoint Server 2019 Public Preview with a Standard license. 
  
Since Project Server 2019 Public Preview is part of the SharePoint Server 2019 Public Preview installation, requirements for Project Server 2019 Public Preview (including supported browsers, operating systems, and database servers) will be the ones specified for SharePoint Server 2019 Public Preview. 
  
Some of the key software requirements for SharePoint Server 2019 Public Preview are:
  
|||
|:-----|:-----|
|**Supported Server Operating Systems** **:** <br/> | Windows Server 2016 Standard or Datacenter <br/>  Windows Server 2019 Standard or Datacenter <br/> |
|**Supported Database Server** **:** <br/> | Microsoft SQL Server 2017 RTM for Windows <br/> •Microsoft SQL Server 2016 Service Pack 1 (SP1) <br/>  SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server 2016. <br/> |
|**Supported browsers** **:** <br/> | Microsoft Edge <br/>  Microsoft Internet Explorer 11 <br/> Google Chrome (latest released version) <br/>  Mozilla Firefox (latest released version plus immediate previous version) <br/>  Apple Safari (latest released version) <br/> |
   
> [!NOTE]
> For information about the hardware, software, and browser requirement for SharePoint Server 2019 Public Preview, see [System requirements for SharePoint Server 2019 Preview](https://docs.microsoft.com/en-us/sharepoint/install/hardware-and-software-requirements-2019). 
  
## Client Compatibility

You can connect to Project Server 2019 Public Preview with not only Project Professional 2019 Public Preview and the Project Online Desktop Client, but also with Project Professional 2016.
  
 
|||
|:-----|:-----|
|**Version** <br/> |**Compatible with** <br/> |
|Project Server 2019 Public Preview <br/> |<br/> Project Professional 2016 <br/>  Project Online Desktop Client <br/> <br/> |


   

## Cube Building Service requirements

SQL Server 2016 Analysis Services must also be installed on your SQL Server 2016 database server for your SharePoint Server 2019 Enterprise deployment if you plan to use the Cube Building Service in Project Server 2019 Public Preview.
  

  
## Portfolio Analysis Requirements

For charts to render correctly in your browser when using Portfolio Analysis in Project Server 2019 Public Preview, the State Service needs to be running in your SharePoint farm. 
  
## See also

#### 

[Deploy Project Servers 2016 or 2019 Public Preview](deploy-project-server-2016.md)

[Hardware and software requirements for SharePoint Server 2019 Preview](https://docs.microsoft.com/en-us/sharepoint/install/system-requirements-for-sharepoint-server-2016)
  
[Plan browser support in SharePoint Server 2019 Preview](https://docs.microsoft.com/en-us/sharepoint/install/browser-support-planning-0)

