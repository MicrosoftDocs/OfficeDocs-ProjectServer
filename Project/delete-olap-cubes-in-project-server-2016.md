---
title: "Delete OLAP cubes in Project Server 2016"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 12/20/2016
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 455e2d63-120c-46ea-bc90-e0fa5a45d34d
description: "Summary: Delete an OLAP cube by using the OLAP Database Management page in Central Administration."
---

# Delete OLAP cubes in Project Server 2016
 
 **Summary:** Delete an OLAP cube by using the OLAP Database Management page in Central Administration.<br/>
**Applies to:** Project Server 2016
  
To delete an OLAP cube, you must be a Project Server service application administrator. Perform the following procedure to delete an OLAP Cube.
  
### To delete an OLAP cube by using Project Web App

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Point to the Project Web App instance where you want to build the cube, click the arrow that appears, and then click **Manage**.
    
4. On the Server Settings page, in the **Database Administration** section, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, select the cube that you want to delete, and then click **Delete**.
    
    > [!NOTE]
    > This procedure deletes the cube and its associated configuration from Project Web App. The actual OLAP database is not deleted from SQL Server Analysis Services (SSAS). For information about deleting the OLAP database from Analysis Services, see [How to: Delete an Analysis Services Database or Cube](https://go.microsoft.com/fwlink/p/?LinkId=212797). 
  
## See also

#### 

[Create OLAP cubes in Project Server 2016](create-olap-cubes-in-project-server-2016.md)
  
[Configure an OLAP cube in Project Server 2016](configure-an-olap-cube-in-project-server-2016.md)
  
[Build OLAP cubes in Project Server 2016](build-olap-cubes-in-project-server-2016.md)

