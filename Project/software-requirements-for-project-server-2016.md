---
title: Software requirements for Project Server 2016
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/7/2016
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 32d82f51-546a-42a3-ade5-54cc4dfdcb87
description: Learn about installation requirements for Project Server 2016.
---

# Software requirements for Project Server 2016
 
 **Summary:** Learn about installation requirements for Project Server 2016.<br/>
**Applies to:** Project Server 2016
  
## Key Requirements

In previous versions of Project Server, Project Server was installed separately after you installed SharePoint Server, as SharePoint Server was a requirement. Project Server 2016 installation is now a part of the SharePoint Server 2016 Enterprise installation process. The installation files for Project Server 2016 are included in the SharePoint Server 2016 Enterprise MSI file, and it is installed along with it. 
  
> [!IMPORTANT]
> Project Server 2016 can only be enabled on the Enterprise version of SharePoint Server 2016. You will not be able to enable Project Server 2016 on SharePoint Server 2016 with a Standard license. 
  
Since Project Server 2016 is part of the SharePoint Server 2016 installation, requirements for Project Server 2016 (including supported browsers, operating systems, and database servers) will be the ones specified for SharePoint Server 2016. 
  
Some of the key software requirements for SharePoint Server 2016 are:
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Supported Server Operating Systems** **:** <br/> | Windows Server 2019 Standard or Datacenter <br/> Windows Server 2016 Standard or Datacenter <br/> Windows Server 2012 R2 <br/> |
|**Supported Database Server** **:** <br/> | Microsoft SQL Server 2017 RTM for Windows <br/> Microsoft SQL Server 2016 RTM <br/> The 64-bit edition of SQL Server 2014 with Service Pack 1 (SP1) <br/> SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server 2016. <br/> |
|**Supported browsers** **:** <br/> | Microsoft Edge <br/> Microsoft Internet Explorer 11 <br/> Microsoft Internet Explorer 10 <br/> Google Chrome (latest released version) <br/> Mozilla Firefox (latest released version plus immediate previous version) <br/> Apple Safari (latest released version) <br/> |
   
> [!NOTE]
> For information about the hardware, software, and browser requirement for SharePoint Server 2016, see [System requirements for SharePoint Server 2016 IT Preview](/SharePoint/install/system-requirements-for-sharepoint-server-2016). 
  
## Client Compatibility

You can connect to Project Server 2016 with not only Project Professional 2016 and the Project Online Desktop Client, but also with Project Professional 2013.
  
Also note that you will be able to use Project Professional 2016 and the Project Online Desktop Client, as well as Project Professional 2013, to connect to Project Server 2013
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Version** <br/> |**Compatible with** <br/> |
|Project Server 2016  <br/> | Project Professional 2019 <br/> Project Professional 2016 <br/>  Project Online Desktop Client <br/>  Project Professional 2013 <br/> |
|Project Server 2013  <br/> | Project Professional 2016 <br/>   Project Professional 2013 <br/> |
|Project Server 2010  <br/> | Project Professional 2010 <br/>  Project Professional 2007 with Service Pack 2 <br/>  Project Professional 2007 with Service Pack 2 can only connect if Backwards Compatibility is enabled on Project Server 2010 <br/> |
   
> [!NOTE]
>Project Online Desktop Client connectivity to Project Server 2013 will expire and no longer be supported after January 13, 2020.  

> [!NOTE]
> If you are using Resource Engagements in Project Server 2016, the new Resource Plan view for Resource Engagements is not available in Project Professional 2013. You must use Project Professional 2016 to use the Resource Plan view. 
  
## Cube Building Service requirements

SQL Server 2014 Analysis Services must also be installed on your SQL Server 2014 database server for your SharePoint Server 2016 Enterprise deployment if you plan to use the Cube Building Service in Project Server 2016.
  

  
## Portfolio Analysis Requirements

For charts to render correctly in your browser when using Portfolio Analysis in Project Server 2016, the State Service needs to be running in your SharePoint farm. 
  
## See also


[Deploy Project Server 2016](deploy-project-server-2016.md)

[Hardware and software requirements for SharePoint Server 2016](/SharePoint/install/hardware-and-software-requirements)
  
[Plan browser support in SharePoint Server 2016](/sharepoint/install/browser-support-planning-2016-2019)