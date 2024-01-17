---
title: "Prepare for a deployment of Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/20/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.assetid: ba9b8053-1658-42eb-a767-cf84b80539e9
description: "Summary: Ensure that you have access to the necessary accounts and permissions to install Project Server 2013."
---

# Prepare for a deployment of Project Server 2013
 
 **Summary:** Ensure that you have access to the necessary accounts and permissions to install Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
To successfully complete a deployment of Project Server 2013, the following permissions are required:
  
- **Domain Administrator** Required to set up two domain groups for report authors and report viewers.
    
- **SQL Server Administrator** Required for various SQL Server and SQL Server Analysis Services (SSAS) configuration tasks as denoted in [Configure SQL Server and Analysis Services in Project Server 2013](configure-sql-server-and-analysis-services-in-project-server-2013-0.md).
    
- **Setup User Account** Required to install Project Server 2013. This account is created when you install SharePoint Server 2013.
    
- **Farm Administrator** Required to configure a Project Web App site. This account is created when you install SharePoint Server 2013.
    
> [!IMPORTANT]
> Verify that you are installing SharePoint Server 2013 and Project Server 2013 on a clean instance of Windows Server that has not previously hosted SharePoint Server 2010. Uninstalling SharePoint Server 2010 does not completely clean all installed files, folders, registry entries and other components. Installing SharePoint Server 2013 and Project Server 2013 on such a server will likely cause issues. It is recommended that you reformat the hard drive and reinstall Windows Server if you do chose to use such a server. 
  
## Creating users and groups in the Active Directory directory service

Deploying Project Server 2013 requires that you have certain Active Directory users and groups available. The deployment instructions assume that the necessary groups already exist. If you have not yet created the necessary users and groups, do so now before deploying Project Server. For detailed information about the users and groups required for Project Server deployment, see [Plan for administrative and service accounts in Project Server 2013](plan-for-administrative-and-service-accounts-in-project-server-2013-beta-2.md).
  
## Configuring SQL Server and Analysis Services

Before deploying your farm, you must configure SQL Server and SQL Server Analysis Services. If you are installing Project Server 2013 to an existing SharePoint Server farm, some of these steps may already be completed. We recommend that you confirm these settings before installing Project Server.
  
To configure SQL Server and Analysis Services, follow the procedures in [Configure SQL Server and Analysis Services in Project Server 2013](configure-sql-server-and-analysis-services-in-project-server-2013-0.md).
  
## See also

[IT Pro Planning for Project Server](it-pro-planning-for-project-server-2016.md)

[Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project)

