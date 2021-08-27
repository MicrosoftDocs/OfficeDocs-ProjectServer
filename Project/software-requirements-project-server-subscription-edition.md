---
title: "Software requirements for Project Server Subscription Edition"
ms.author: v-jmathew
author: serdars
manager: pamgreen
ms.date: 6/18/2021
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 32d82f51-546a-42a3-ade5-54cc4dfdcb87
description: "Summary: Learn about installation requirements for Project Server Subscription Edition."
---

# Software requirements for Project Server Subscription Edition

 **Summary:** Learn about installation requirements for Project Server Subscription Edition.<br/>
**Applies to:** Project Server Subscription Edition

## Key Requirements

Project Server Subscription Edition installation is now a part of the SharePoint Server Subscription Edition Enterprise installation process. The installation files for Project Server Subscription Edition are included in the SharePoint Server Subscription Edition Enterprise MSI file, and it is installed along with it.

> [!IMPORTANT]
> Project Server Subscription Edition can only be enabled on the Enterprise version of SharePoint Server Subscription Edition. You will not be able to enable Project Server Subscription Edition on SharePoint Server Subscription Edition with a Standard license.

Since Project Server Subscription Edition is part of the SharePoint Server Subscription Edition installation, requirements for Project Server Subscription Edition (including supported browsers, operating systems, and database servers) will be the ones specified for SharePoint Server Subscription Edition.

Some of the key software requirements for SharePoint Server Subscription Edition are:

|**Software**|**Software requirements**|
|:-----|:-----|
|**Supported Server Operating Systems:**  <br/> | Windows Server 2019 Standard or Datacenter <br/> Windows Server 2022 Standard or Datacenter <br/> |
|**Supported Database Server:**  <br/> | Microsoft SQL Server 2019 RTM for Windows Services<br/>  Note: SQL Analysis Services must also be installed if you are using the Cube Building Service in Project Server Subscription Edition. <br/> |
|**Supported browsers:**  <br/> | Microsoft Edge <br/>  Microsoft Internet Explorer 11 <br/> Google Chrome (latest released version) <br/>  Mozilla Firefox (latest released version plus immediate previous version) <br/>  Apple Safari (latest released version) <br/> |
    
> [!NOTE]
> For information about the hardware, software, and browser requirement for SharePoint Server Subscription Edition, see [System requirements for SharePoint Server Subscription Edition](/sharepoint/install/hardware-and-software-requirements-2019).

## Client Compatibility

You can connect to Project Server Subscription Edition with not only Project Professional 2021 and the Project Online Desktop Client, but also with Project Professional 2019.

|**Version**|**Compatible with**|
|:-----|:-----|
|Project Server Subscription Edition<br/> |Project Professional 2021 <br/> Project Professional 2019 <br/>  Project Online Desktop Client <br/> <br/> |
    

## Cube Building Service requirements

SQL Server 2019 Analysis Services must also be installed on your SQL Server 2019 database server for your SharePoint Server Subscription Edition Enterprise deployment if you plan to use the Cube Building Service in Project Server Subscription Edition. Additionally, SQL Server Analysis Services AMO 2019 Client must also be installed.

## Portfolio Analysis Requirements

For charts to render correctly in your browser when using Portfolio Analysis in Project Server Subscription Edition, the State Service needs to be running in your SharePoint farm.
  
## See also

[Deploy Project Servers 2016 or 2019](deploy-project-server-2016.md)

[Hardware and software requirements for SharePoint Server 2019](/sharepoint/install/system-requirements-for-sharepoint-server-2016)
  
[Plan browser support in SharePoint Server 2019](/sharepoint/install/browser-support-planning-0)
