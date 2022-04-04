---
title: "Add SharePoint task list data to Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: d6109d43-8ede-465c-bb18-31a01fbfd039
description: "Summary: You must ensure that all SharePoint Tasks list data is added to Project Server after importing it to Project Web App."
---

# Add SharePoint task list data to Project Server 2013
 
 **Summary:** You must ensure that all SharePoint Tasks list data is added to Project Server after importing it to Project Web App.<br/>
**Applies to:** Project Server 2013
  
  
In SharePoint Server 2013, when a SharePoint Tasks list on a project site has been added to Project Web App, the task data is imported to Project Server 2013. If the SharePoint task list had been opened and saved in Project Professional 2013, a Project Professional MPP file will be associated with this task list, and it will be stored in the site's asset library. The MPP file contains additional data not stored in the task list that must be saved to Project Server 2013 manually. This includes data such as baselines, custom fields, and views.
  
If you attempt to open the MPP file for the task list in Project Professional 2013, a warning message will appear that says:  *The SharePoint Task List for this project is now connected to Project Server, but additional steps are required to complete the connection*  . Clicking the **Follow these steps** button will open this TechNet article.
  
If you add a SharePoint Tasks list to Project Server 2013 that has an associated MPP file, you must follow the procedure in this article to overwrite the project file in Project Server 2013 with the MPP file. This ensures that all of the task list data is imported into Project Server 2013. 
  
> [!NOTE]
> If the SharePoint Tasks list had never been opened and saved in Project Professional 2013, no action is required to add the additional task list data into Project Server 2013. If this is the case, an MPP file will not exist in the site's asset library. 
  
## Overwriting the project file in Project Server

> [!NOTE]
> Before you start this procedure, verify that Project Professional 2013 is closed on your desktop. 
  
### To overwrite the project file in Project Server

1. Open the SharePoint site that contains your SharePoint Tasks list.
    
2. In the List ribbon, click **Open with Project**. 
    
    This action opens the SharePoint Tasks list in Project Professional 2013.
    
    > [!IMPORTANT]
    > We recommend that you use the **Open with Project** button on the ribbon to open the task list in Project Professional 2013. This opens Project Professional 2013 with a configured connection to the project in Project Server 2013. If you open the task list in Project Professional 2013 by using the "most recently used" or the site asset library, you would need to manually configure the connection to Project Server 2013.
  
3. In Project Professional 2013, click **File**, click **Save As**, and then click **Save to Project Web App**. In the **Save to Project Web App** dialog box, click **Save**. This overwrites the current file that is saved to Project Server. The Name field is automatically configured with the correct project name and is not editable, ensuring that the correct file is overwritten on the server. Verify that the save job completes successfully, and then close Project Professional 2013.
    
4. To verify whether the project file in Project Server 2013 has been overwritten successfully, go back to the SharePoint Tasks list on the site and click **Open with Project**. You will no longer see the warning message if the file has been overwritten successfully. This is because Project Professional 2013 will now be connecting to the project file in Project Server 2013. It will no longer have a connection to the MPP file in the site asset library.
    
> [!IMPORTANT]
> The MPP file will be completely disconnected from Project Server, but will still exist in the site asset library or might still be viewed in Project Professional 2013 as a recently accessed project. You can choose to delete or rename the MPP file to avoid confusion. 
  
## See also

[Work with a task list](https://go.microsoft.com/fwlink/p/?LinkId=255328)
  
[Getting started with a project site](https://go.microsoft.com/fwlink/p/?LinkId=255326)

