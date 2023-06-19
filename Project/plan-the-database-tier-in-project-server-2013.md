---
title: "Plan the database tier in Project Server 2013"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 77a2f176-c824-4159-8e13-cf64d57c0dfc
description: "Summary: Learn how data is partitioned within a Project Web App database and which tables are available for use externally."
---

# Plan the database tier in Project Server 2013
 
 **Summary:** Learn how data is partitioned within a Project Web App database and which tables are available for use externally.<br/>
**Applies to:** Project Server 2013
  
This article identifies the key components of the database tier.
  
The data access layer is internal to Project Server 2013 and is not exposed to external applications. The data access layer translates between the logical business entity representation of the data and the physical database tables. Each logical entity is stored in a number of different tables. The data access layer encapsulates the work required to manage connections, execute queries, and begin, commit, and roll back transactions. Project Server 2013 data is contained in a single database for each instance of Project Web App, partitioned into four table schemas:
  
- The Draft tables contain unpublished projects from Project Professional 2013. Project data in these tables is not accessible by using Project Web App.
    
- The Published tables contain all of the published projects as well as tables that are specific to Project Web App (timesheets, models, views, and so on), and global data tables (outline codes, security, and metadata). Published projects are visible in Project Web App. 
    
- The Archive tables contain backed-up and older versions of projects.
    
- The Reporting tables are the staging area for generating reports and online analytical processing (OLAP) cubes. Data in the Reporting tables is updated nearly in real-time, is comprehensive, and is optimized for read-only report generation.
    
Only the Reporting table schema is documented. You should access the Drafts, Published, and Archive tables only through the Project Server Interface.
  
> [!NOTE]
> Access to the Reporting tables is not supported in Project Online. You must use the Project Web App OData feed to access the data in the Reporting tables. 
  
You can add data tables, fields (properties), and entities that are not defined in the Project Server 2013 database schema. If you do, you must also provide the full stack of a custom assembly, Web service, business objects, and data access.
  
> [!NOTE]
> These additions will not be automatically upgraded to future versions of Project Server. 
  

