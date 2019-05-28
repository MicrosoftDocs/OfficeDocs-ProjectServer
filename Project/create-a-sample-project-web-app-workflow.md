---
title: "Create a sample Project Web App workflow"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 8/30/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: b857e56c-9964-4fc4-9da6-125736e8f7a4
description: "Summary: Create sample workflow components to use in learning about Project Web App workflows."
---

# Create a sample Project Web App workflow
 
 **Summary:** Create sample workflow components to use in learning about Project Web App workflows.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
In this article, we're going to set up some basic workflow infrastructure that we can use to demonstrate workflow functionality. We'll be creating some sample workflow stages, an empty workflow that we can build on later, and a sample enterprise project type. We can then use these items in the articles that follow to demonstrate some of the workflow capabilities available for Project Web App.
  
## Create sample workflow stages

First, we'll create some Project Web App workflow stages for use in the workflow demonstration articles that follow.
  
We'll create the following stages:
  
|**Stage name**|**Phase**|
|:-----|:-----|
|1 - Propose idea  <br/> |Create  <br/> |
|2 - Request review  <br/> |Select  <br/> |
|3 - Execute  <br/> |Manage  <br/> |
|4 - Cancelled  <br/> |Finished  <br/> |
   
Use the following procedure to create each of the stages in the table above. Follow the procedure once for each stage.
  
### To create a stage

1. In Project Web App, click **Settings** > **PWA Settings**.
    
2. Under **Workflow and Project Detail Pages**, click **Workflow Stages**.
    
3. Click **New Workflow Stage**.
    
4. In the **Name** box, type a name for the stage as shown in the table above.
    
5. Choose a phase from the **Workflow Phase** dropdown list as shown in the table above.
    
6. In the **Visible Project Detail Pages** section, select **Project Information** and click **>** to add it to the **Selected Project Details Pages** list.
    
7. Leave the other options at their default values and click **Save**.
    
## Publish an empty workflow to Project Web App

Next, we'll create an empty workflow. We'll be adding to the workflow later, but right now we need the empty container to hook up to the enterprise project type that we'll create next.
  
### To create and publish a workflow

1. Start SharePoint Designer.
    
2. Click **Open Site**.
    
3. Type the URL of your Project Web App site, and then click **Open**.
    
4. On the left, click **Workflows**.
    
5. On the ribbon, click **Site Workflow**.
    
6. Type Sample Workflow for the name.
    
7. Ensure that **SharePoint 2013 Workflow - Project Server** is selected as the **Platform Type**.
    
8. Click **OK**.
    
9. On the ribbon, click **Publish**.
    
10. Close SharePoint Designer.
    
## Create an enterprise project type

With the workflow published, we can create a sample enterprise project type.
  
### To create a sample enterprise project type

1. In Project Web App, click **Settings** > **PWA Settings**.
    
2. Under **Workflow and Project Detail Pages**, click **Enterprise Project Types**.
    
3. Click **New Enterprise Project Type**.
    
4. Type Sample Project Type for the name.
    
5. Choose **Sample Workflow** (the workflow that we just created) from the **Site Workflow Association** dropdown list.
    
6. Choose **Project Information** from the **New Project Page** dropdown list.
    
7. Click **Save**.
    
## Explore workflow functionality

With the sample stages and workflow in place, we can take a closer look at workflow functionality in Project Web App. See the following articles to try out some of the Project Web App features:
  
1. [Have a workflow wait for a Project Web App event](have-a-workflow-wait-for-a-project-web-app-event.md)
    
2. [Set the stage status in a Project Web App workflow](set-the-stage-status-in-a-project-web-app-workflow.md)
    
3. [Add a custom field to a project detail page](add-a-custom-field-to-a-project-detail-page.md)
    
4. [Assign an approval task in a workflow](assign-an-approval-task-in-a-workflow.md)
    
5. [Customize approval options for Project Web App workflows](customize-approval-options-for-project-web-app-workflows.md)
    
You can read these articles in any order, but the order listed above represents simplest to most complex.
  

