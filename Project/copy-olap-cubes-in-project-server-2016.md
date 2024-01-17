---
title: "Copy OLAP cubes in Project Server 2016"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 3/28/2016
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: ddda61d3-25cf-4d37-9cc8-739b6a142bcc
description: "Summary: Copy Project Web App OLAP cube settings for use in creating a new cube."
---

# Copy OLAP cubes in Project Server 2016

**Summary:** Copy Project Web App OLAP cube settings for use in creating a new cube.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016
  
OLAP cubes are managed on the OLAP Database Management page in Server Settings in the SharePoint Central Administration website.
  
To copy an OLAP cube, you must be a Project Server service application administrator. Perform the following procedure to copy an existing OLAP Cube. Copying a cube creates a new cube with the same settings and configuration as the cube that you copied. Copying a cube does not copy the Analysis Services database, but instead copies all the cube settings from which you can build a new Analysis Services database.
  
> [!NOTE]
> You must specify a new name for the Analysis Services database after you copy the cube. 
  
Use the following procedure to copy an OLAP cube.
  
### To copy an OLAP cube by using Project Web App

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Point to the Project Web App instance where you want to build the cube, click the arrow that appears, and then click **Manage**.
    
4. On the Server Settings page, in the **Database Administration** section, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, select the cube that you want to copy, and then click **Copy**.
    
6. On the OLAP Database Build Settings page, type the name of the server and the database that you want created and adjust any other desired settings.
    
7. Click **Save**.
    
    > [!NOTE]
    > This procedure copies the cube configuration but does not build the cube. You can build the cube manually or wait for it to build on the schedule that you set. 
  
## See also

[Create OLAP cubes in Project Server 2016](create-olap-cubes-in-project-server-2016.md)
  
[Configure an OLAP cube in Project Server 2016](configure-an-olap-cube-in-project-server-2016.md)
  
[Delete OLAP cubes in Project Server 2016](delete-olap-cubes-in-project-server-2016.md)
  
[Build OLAP cubes in Project Server 2016](build-olap-cubes-in-project-server-2016.md)
