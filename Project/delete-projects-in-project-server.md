---
title: "Delete projects in Project Server"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 9/6/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: fa652c02-f1d0-4d4e-90e1-5f5e79dd44d4
description: "Summary: When a project is no longer needed, you can delete it from Project Web App using the Delete Enterprise Objects option."
---

# Delete projects in Project Server
 
 **Summary:** When a project is no longer needed, you can delete it from Project Web App using the Delete Enterprise Objects option.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
Use the following procedure to delete a project from Project Web App.
  
> [!IMPORTANT]
> The project is permanently deleted from Project Web App and it cannot be retrieved. 
  
### To delete a project

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Queue and Database Administration** section, click **Delete Enterprise Objects**.
    
3. On the Delete Enterprise Objects page, select the **Projects** option.
    
4. Select one of the following options:
    
   - **Delete draft and published projects** to display a list of both Draft and Published projects.
    
   - **Delete only published projects** to display a list of Published projects.
    
   - **Delete archived projects** to display a list of Archived projects.
    
5. To delete the associated SharePoint site, select the **Delete the connected SharePoint sites** check box.
    
    > [!NOTE]
    > If you do not delete the associated SharePoint site and you save and publish a new project with the same name as the deleted project, the SharePoint site publishing process will fail. 
  
6. Select the project that you want to delete.
    
7. Click **Delete**.
    

