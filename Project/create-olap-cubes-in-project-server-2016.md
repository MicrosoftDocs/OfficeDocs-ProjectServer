---
title: "Create OLAP cubes in Project Server 2016"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 69efbd37-9b58-43f5-9e6b-93bc2cfbdbc6
description: "Summary: Manage OLAP cubes by using the OLAP Database Management page in Central Administration."
---

# Create OLAP cubes in Project Server 2016
 
 **Summary:** Manage OLAP cubes by using the OLAP Database Management page in Central Administration.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016
  
To create an OLAP cube, you must be a Project Server service application administrator. Perform the following procedure to create a new OLAP cube.
  
### To create an OLAP cube by using Project Web App

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Point to the Project Web App instance where you want to build the cube, click the arrow that appears, and then click **Manage**.
    
4. On the Server Settings page, in the **Queue and Database Administration** section, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, click **New**.
    
6. Configure the settings on the OLAP Database Build Settings page:
    
|**Setting**|**Description**|
|:-----|:-----|
|**Analysis Services Server** <br/> |The name of the instance of SQL Server Analysis Services (SSAS) where you want to build the cube.  <br/> |
|**Analysis Services Database to be created** <br/> |The name of the database that you want to create.  <br/> |
|**Extranet URL** <br/> |The URL for the extranet site.  <br/> |
|**Description** <br/> |A description of this OLAP cube.  <br/> |
|**Project Departments** <br/> |If you have projects assigned to departments, you have the option of selecting the departments that you want to have included in the cube. If no department is selected, then no departmental filtering occurs.  <br/> The selection of departments available is controlled by the Department custom lookup table.  <br/> |
|**Resource Departments** <br/> |If you have resources assigned to departments, you have the option of selecting the departments that you want to have included in the cube. If no department is selected, then no departmental filtering occurs.  <br/> The selection of departments available is controlled by the Department custom lookup table.  <br/> |
|**Use the earliest project start date and the latest project finish date** <br/> |Select this option if you want to base the date range of the cube on the earliest start date of any project and the latest finish date of any project.  <br/> |
|**Use the following last and next time units to calculate the date range at the time that the OLAP database is built** <br/> |Select this option if you want the date range to be configured automatically based on a delta from the date on which the cube is built. In the **Last** and **Next** boxes, type the number of days, weeks, or months that you want to use for the delta. <br/> |
|**Use the fixed date range specified below** <br/> |Select this option if you want to use a fixed date range. In the **From** and **To** boxes, type the dates that you want to use. <br/> |
|**Update periodically** <br/> |Select this option if you want to schedule an update frequency. If this option is not selected, the cube is not updated automatically.  <br/> |
|**Immediately retry the OLAP database update if scheduled time fails because of queue down time** <br/> |If the scheduled cube build fails because the queue is not available, selecting this option causes the build job to start automatically when the queue becomes available instead of waiting for the next scheduled time.  <br/> |
|**Update every** <br/> |Select the number of hours, days, weeks, or months for the cube to be rebuilt.  <br/> |
|**Start date** <br/> |Select the start date for the first automated cube build.  <br/> |
|**Start time** <br/> |Select the start time for each automated cube build.  <br/> |
   
7. Click **Save**.
    
## See also

[Configure an OLAP cube in Project Server 2016](configure-an-olap-cube-in-project-server-2016.md)
  
[Delete OLAP cubes in Project Server 2016](delete-olap-cubes-in-project-server-2016.md)
  
[Build OLAP cubes in Project Server 2016](build-olap-cubes-in-project-server-2016.md)

