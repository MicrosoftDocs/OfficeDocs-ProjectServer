---
title: "Assign an approval task in a workflow"
ms.author: kenwith
author: kenwith
ms.prod: scotv
ms.date: 8/30/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.assetid: 4735a010-84c3-44af-a2c7-c83bd0013cd9
description: "Summary: Learn how to add an approval task to a Project Web App workflow."
---

# Assign an approval task in a workflow
 
 **Summary:** Learn how to add an approval task to a Project Web App workflow.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
By including an approval task in your Project Web App workflow, you can ensure that your projects receive proper approval before they get underway. In this article, we'll look at an example of using an approval task in a workflow to allow selected users to approve or reject a project.
  
## Before you begin
<a name="begin"> </a>

Before starting, make sure:
  
- If you are using an on-premises deployment of Project Server, you have set up the [SharePoint 2013 workflow platform](http://technet.microsoft.com/library/145fc383-d584-487a-8738-8de15512ae26%28Office.14%29.aspx).
    
- You have created the sample workflow, stages, and enterprise project type as described in [Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md).
    
## Create a workflow with an approval task
<a name="proc1"> </a>

We'll be using the Sample Workflow that you created in [Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md) to build a workflow that looks like this:
  
![Screenshot of workflow in SharePoint Designer](images/WorkflowAssignAnApprovalTask.png)
  
If you've completed the procedures in other articles in this series, you may already have part of this workflow in place. The complete steps for creating this workflow are in the following procedure.
  
### To create a workflow

1. Start SharePoint Designer.
    
2. Connect to your Project Web App site.
    
3. On the left, click **Workflows**.
    
4. Click **Sample Workflow**.
    
5. Click **Edit workflow**.
    
6. On the ribbon, click **Stage**, and then click **1 - Propose idea**.
    
7. Place the orange cursor in the top section of **Stage 1** and, on the ribbon, click **Action**, and then, under **Project Web App Actions**, click **Wait for Project Event**.
    
8. Click **this project event**, and choose **Event: When a project is submitted** from the dropdown menu.
    
9. Place the orange cursor below Stage 1, click **Stage**, and then click **2 - Request idea**.
    
10. Place the orange cursor below Stage 2, click **Stage**, and then click **3 - Execute**.
    
11. Place the orange cursor below Stage 3, click **Stage**, and then click **4 - Cancelled**.
    
12. Place the orange cursor in the **Transition to stage** area of Stage 1, and then, on the ribbon, click **Action**, and then click **Go to a stage**.
    
13. Click the **a stage** link, and then choose **2 - Request review** from the dropdown list.
    
14. Place the orange cursor in the top half of Stage 2.
    
15. On the ribbon, click **Action**, and then, under **Task Actions**, click **Start a task process**.
    
16. Click the **these users** link.
    
17. On the Start a Task Process page:
    
1. Click the ellipsis ( **...**) for **Participants** and add the name of the user to whom you want to assign the project approval task.
    
2. For **Task Title**, click **fx**, choose a **Data source** of **Project Data**, a **Field from source** of **Project Name**, and click **OK**.
    
3. Click **OK**.
    
18. Place the orange cursor in the **Transition to stage** section of Stage 2.
    
19. Click **Condition** and select **If any value equals value**.
    
20. Click the first **value** link, and then click **fx**.
    
21. Choose a **Data source** of **Workflow Variables and Parameters** and a **Field from source** of **Variable: Outcome** and click **OK**.
    
22. Click the second **value** link and choose **Approved** from the dropdown list.
    
23. Place the orange cursor in the If branch of the If / Else statement.
    
24. On the ribbon, click **Action**, and then choose **Go to a stage**.
    
25. Click the **a stage** link, and then choose **3 - Execute**.
    
26. Place the orange cursor in the Else branch of the If / Else statement.
    
27. On the ribbon, click **Action**, and then choose **Go to a stage**.
    
28. Click **a stage**, and then choose **4 - Cancelled** from the dropdown menu.
    
29. Place the orange cursor in the **Transition to stage** area of Stage 3, and then, on the ribbon, click **Action**, and then click **Go to a stage**.
    
30. Click **a stage**, and then choose **End of Workflow** from the dropdown menu.
    
31. Place the orange cursor in the **Transition to stage** area of Stage 4, and then, on the ribbon, click **Action**, and then click **Go to a stage**.
    
32. Click **a stage**, and then choose **End of Workflow** from the dropdown menu.
    
33. On the ribbon, click **Publish**.
    
## Test it out
<a name="proc2"> </a>

With the workflow published, we can create a sample project to see how the approval task works.
  
### To create a project

1. In Project Web App, in the left navigation, click **Projects**.
    
2. On the ribbon, click the **Projects** tab.
    
3. Click **New**, and then click **Sample Project Type**.
    
4. Name the project **Assign an approval task**, and then click **Save**.
    
5. On the Workflow Status page, click **Submit**, and then click **OK** to confirm.
    
Once the project has been created and submitted, you'll notice that the Current Workflow Stage is **1 - Propose idea**. The workflow will pause here until the user to whom you assigned the approval task approves or rejects the project.
  
Let's take a look at what happens when the user approves the task.
  
### To approve a task

1. Log into Project Web App as the user to whom you assigned the task.
    
2. In Project Web App, in the left navigation, click **Approvals**.
    
3. On the ribbon, click **Workflow Approvals**.
    
4. On the Workflow Tasks list, click **All Tasks**.
    
5. Click **Assign an approval task**.
    
6. On the ribbon, click **Edit**.
    
7. Click **Approved**.
    
Notice that once the task has been approved, the Current Workflow Stage is **3 - Execute**. Try creating another project, and this time choose **Rejected** for the approval task. Note that the Current Workflow Stage is **4 - Cancelled**.
  
In the next article, we'll look at how to [add an additional approval option to the approval task](customize-approval-options-for-project-web-app-workflows.md).
  
## See also
<a name="proc2"> </a>

#### 

[Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md)
  
[Have a workflow wait for a Project Web App event](have-a-workflow-wait-for-a-project-web-app-event.md)
  
[Set the stage status in a Project Web App workflow](set-the-stage-status-in-a-project-web-app-workflow.md)
  
[Add a custom field to a project detail page](add-a-custom-field-to-a-project-detail-page.md)
  
[Customize approval options for Project Web App workflows](customize-approval-options-for-project-web-app-workflows.md)

