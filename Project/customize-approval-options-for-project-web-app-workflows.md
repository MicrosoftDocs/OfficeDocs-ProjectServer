---
title: "Customize approval options for Project Web App workflows"
ms.author: kenwith
author: kenwith
ms.prod: scotv
ms.date: 8/30/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.assetid: 0cf2625c-858d-4f98-a77a-3e566cb63a22
description: "Summary: Learn how to add additional approval options to a Project Web App workflow approval task."
---

# Customize approval options for Project Web App workflows
 
 **Summary:** Learn how to add additional approval options to a Project Web App workflow approval task.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
When using approval tasks in your workflows, it is often desirable to have additional options beyond Approved and Rejected. For example, you may want those submitting the proposal to do some additional groundwork on the project and then resubmit before you make the final Approved or Rejected decision.
  
In this article, we'll look at how to add a third option — we'll call it  *Revise and Resubmit*  — to the list of options in the workflow approval task.
  
## Before you begin
<a name="begin"> </a>

Before starting, make sure:
  
- If you are using an on-premises deployment of Project Server, you have set up the [SharePoint 2013 workflow platform](http://technet.microsoft.com/library/145fc383-d584-487a-8738-8de15512ae26%28Office.14%29.aspx).
    
- You have created the sample workflow, stages, and enterprise project type as described in [Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md).
    
## Add a new task approval option
<a name="proc1"> </a>

The first thing that we need to do is to add the new Revise and Resubmit option to the existing list of approval options. This is done in the site settings for the Project Web App site.
  
### To modify the task approval options

1. In Project Web App, click **Settings**, and then click **Site settings**.
    
2. Under **Web Designer Galleries**, click **Site content types**.
    
3. Under **List Content Types**, click **Workflow Task (SharePoint 2013)**.
    
4. Under **Columns**, click **Task Outcome**.
    
5. Click the **Edit site column** link.
    
6. In the **Type each choice on a separate line** box, addRevise and Resubmit on a separate line between **Approved** and **Rejected**.
    
7. Click **OK**.
    
## Create the workflow
<a name="proc2"> </a>

We'll be using the Sample Workflow that you created in [Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md) to build a workflow that looks like this:
  
![Screenshot of workflow in SharePoint Designer](images/WorkflowCustomizeApprovalOptions.png)
  
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
    
27. Click **Condition** and select **If any value equals value**.
    
28. Click the first **value** link, and then click **fx**.
    
29. Choose a **Data source** of **Workflow Variables and Parameters** and a **Field from source** of **Variable: Outcome** and click **OK**.
    
30. Click the second **value** link and choose **Revise and Resubmit** from the dropdown list.
    
31. Place the orange cursor in the If branch of the second If / Else statement.
    
32. On the ribbon, click **Action**, and then choose **Go to a stage**.
    
33. Click the **a stage** link, and then choose **1 - Propose idea**.
    
34. Place the orange cursor in the Else branch of the If / Else statement.
    
35. On the ribbon, click **Action**, and then choose **Go to a stage**.
    
36. Click **a stage**, and then choose **4 - Cancelled** from the dropdown menu.
    
37. Place the orange cursor in the **Transition to stage** area of Stage 3, and then, on the ribbon, click **Action**, and then click **Go to a stage**.
    
38. Click **a stage**, and then choose **End of Workflow** from the dropdown menu.
    
39. Place the orange cursor in the **Transition to stage** area of Stage 4, and then, on the ribbon, click **Action**, and then click **Go to a stage**.
    
40. Click **a stage**, and then choose **End of Workflow** from the dropdown menu.
    
41. On the ribbon, click **Publish**.
    
## Test it out
<a name="proc2"> </a>

### To create a project

1. In Project Web App, in the left navigation, click **Projects**.
    
2. On the ribbon, click the **Projects** tab.
    
3. Click **New**, and then click **Sample Project Type**.
    
4. Name the project **Customize approval options**, and then click **Save**.
    
5. On the Workflow Status page, click **Submit**, and then click **OK**.
    
Submitting the project will move the workflow to Stage 2, triggering our approval task. (Note that the Current Workflow Stage on the Workflow Status page is **2 - Request review**.) The next step is to select an outcome for the task.
  
### To choose an outcome for a task

1. Log into Project Web App as the user to whom you assigned the task.
    
2. In Project Web App, in the left navigation, click **Approvals**.
    
3. On the ribbon, click **Workflow Approvals**.
    
4. On the Workflow Tasks list, click **All Tasks**.
    
5. Click **Customize approval options**.
    
6. On the ribbon, click **Edit**.
    
7. Click **Revise and Resubmit**.
    
On the Workflow Status page, note that the Current Workflow Stage has returned to **1 - Propose idea**. (You can also [use the Stage Status to leave a message for your users](set-the-stage-status-in-a-project-web-app-workflow.md) about the need to revise their proposal.) Users can now update the project proposal materials and resubmit the project again to create another approval task.
  
Try creating another project and choosing **Approved** or **Rejected** for the task. You'll notice that the workflow stage moves to **3 - Execute** or **4 - Cancelled** respectively.
  
In this case, we added a single additional option — Revise and Resubmit — to the approval task. You can add additional options depending on your needs, and configure the workflow to react differently to each one.
  
## See also
<a name="proc2"> </a>

#### 

[Create a sample Project Web App workflow](create-a-sample-project-web-app-workflow.md)
  
[Have a workflow wait for a Project Web App event](have-a-workflow-wait-for-a-project-web-app-event.md)
  
[Set the stage status in a Project Web App workflow](set-the-stage-status-in-a-project-web-app-workflow.md)
  
[Add a custom field to a project detail page](add-a-custom-field-to-a-project-detail-page.md)
  
[Assign an approval task in a workflow](assign-an-approval-task-in-a-workflow.md)

