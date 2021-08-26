---
title: "Troubleshoot Project Online workflows"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 1/3/2018
audience: admin
ms.topic: article
ms.service: project-online
ms.localizationpriority: medium
ms.custom: IT_ProjectAdmin
search.appverid: 
- PJO150
- MET150
ms.assetid: fd893a1f-26c3-48c0-a854-4aa12fd808b1

description: "It is common as a Project Web App admin to have to troubleshoot Project workflows. Depending on how the workflow process has been defined for the organization, there may be instances where an admin needs to act for the workflow instance to progress. There are fields that a user can add to the Project Center, query OData or the Project Online Rest endpoint to better understand the state of each Project workflow. With the information provided in these fields, a Project Web App admin can take the appropriate corrective action to unblock the progression of the Project workflow."
---

# Troubleshoot Project Online workflows

It is common as a Project Web App admin to have to troubleshoot Project workflows. Depending on how the workflow process has been defined for the organization, there may be instances where an admin needs to act for the workflow instance to progress. There are fields that a user can add to the Project Center, query OData or the Project Online Rest endpoint to better understand the state of each Project workflow. With the information provided in these fields, a Project Web App admin can take the appropriate corrective action to unblock the progression of the Project workflow.
  
There are three steps on troubleshooting Project Online workflows:
  
1. [Setting up views and reports to see the errors](troubleshoot-project-online-workflows.md#settingupviews)
    
2. [Reviewing the errors](troubleshoot-project-online-workflows.md#reverrors)
    
3. [Acting on the errors and taking additional steps](troubleshoot-project-online-workflows.md#ActingonErrors)
    
## Setting up views and reports to see the errors
<a name="settingupviews"> </a>

An admin can see Project workflow errors in two ways:
  
- Create a Project Center View to see workflow state
    
- Query Project OData Service or the Project REST API
    
### Create a Project Center View to see workflow state

We recommend creating a new Project Center view to troubleshoot Project workflows. To create the view or edit a Project Center view, the user will need to have the Global permission to Manage Project Web App Views
  
> [!NOTE]
> For more information on how to manage security, please see [Video series: How security permissions work in Project Server](https://support.office.com/article/a19fb429-4f8f-4aa1-a186-8a33650c9801)
  
 **To create the view**
  
1. From Project Web App, click on the gear icon then ** PWA Settings **.
    
2. On the settings page, click **Manage Views**. A list of views will appear.
    
3. Click ** New View **.
    
4. In the Name and Type section, in the ** View Type ** list, select **Project Center**.
    
5. In the **Name** box, type the name of the new view. For example, "  *Project Workflows*  ". 
    
6. In the **Description** box, type a description of the new view. 
    
7. In the **Table and Fields** section, from the **Displayed Fields** list, remove the default **Start and Finish** fields. Add the following fields from the **Available fields** list: 
    
  - Workflow Error Code
    
  - Workflow Error
    
  - Workflow Created
    
  - Workflow ID
    
  - Workflow Last Run
    
  - Workflow Owner
    
  - Workflow Phase Name
    
  - Workflow Stage Name
    
  - Workflow State
    
  - Checked Out
    
  - Checked Out By﻿
    
8. Scroll to the bottom of the page and click **Filter﻿﻿**. 
    
9. Add the filter using the field " **Workflow Error Code**is greater than 1" and click **OK** ﻿. 
    
10. Click **Save**.
    
    > [!NOTE]
    > After clicking **Save**, you will receive the following message: " *You have not assigned a security category to this view. Failure to do so will prevent anyone from seeing the view in the dropdown or from using the view. Do you want to save anyway?*  " Click **OK**, because only members of the PWA Administrators group will be able to view the Project Workflows Project Center view. 
  
### Query Project OData Service or the Project REST API

Optionally users can query for this information from the Project OData Service or programmatically through the Project REST API.
  
Project OData Service
  
|**Project Center Field**|**Entity**|**Property**|
|:-----|:-----|:-----|
|Workflow Error Code  <br/> |Projects  <br/> |WorkflowErrorResponseCode  <br/> |
|Workflow Error  <br/> |Projects  <br/> |WorkflowError  <br/> |
|Workflow Created  <br/> |Projects  <br/> |WorkflowCreatedDate  <br/> |
|Workflow ID  <br/> |Projects  <br/> |WorkflowInstanceId  <br/> |
|Workflow Last Run  <br/> |ProjectWorkflowStageData  <br/> |StageLastSubmittedDate  <br/> |
|Workflow Owner  <br/> |Projects  <br/> |WorkflowOwnerName  <br/> |
|Workflow Phase Name  <br/> |ProjectWorkflowStageData  <br/> |PhaseName  <br/> |
|Workflow Stage Name  <br/> |ProjectWorkflowStageData  <br/> |StageName  <br/> |
|Workflow State  <br/> |ProjectWorkflowStageData  <br/> |StageStatus  <br/> |
   
> [!NOTE]
> For more information about the Project OData service, see [ProjectData-Project OData service reference](/previous-versions/office/project-odata/jj163015(v=office.15)). 
  
Project REST API
  
|**Project Center Field**|**Entity**|**Property**|
|:-----|:-----|:-----|
|Workflow Error Code  <br/> |ProjectWorkflowInstance  <br/> |WorkflowErrorResponseCode  <br/> |
|Workflow Error  <br/> |ProjectWorkflowInstance  <br/> |WorkflowError  <br/> |
|Workflow Created  <br/> |ProjectWorkflowInstance  <br/> |WorkflowCreatedDate  <br/> |
|Workflow ID  <br/> |ProjectWorkflowInstance  <br/> |Id  <br/> |
|Workflow Last Run  <br/> |ProjectWorkflowInstance  <br/> |LastSubmittedDate  <br/> |
|Workflow Owner  <br/> |Projects  <br/> |ProjectOwnerName  <br/> |
|Workflow Phase Name  <br/> |ProjectWorkflowStageData  <br/> |PhaseName  <br/> |
|Workflow Stage Name  <br/> |ProjectWorkflowStageData  <br/> |StageName  <br/> |
|Workflow State  <br/> |ProjectWorkflowInstance  <br/> |WorkflowState  <br/> |
   
### Code Examples

Read a filtered set of projects and retrieve the project workflow instances. If the request includes more then 20 projects, you will need to add additional filtering otherwise the request will fail:
  
```
GET https://CONTOSO.sharepoint.com/teams/project/PWA/_api/projectserver/projects?$Filter=startswith(Name,'Budget')&amp;$Expand=ProjectWorkflowInstance,ProjectWorkflowInstance/WorkflowInstance
```

Read all workflows with error response codes greater than or equal to 400, including the owner and minimal details about the project:
  
```
GET https://CONTOSO.sharepoint.com/teams/project/PWA/_api/projectserver/projectworkflowinstances?$FILTER=WorkflowErrorResponseCode ge 400&amp;$SELECT=Id,WorkflowError,WorkflowErrorResponseCode,WorkflowState,Project/Id,Project/Name&amp;$EXPAND=WorkflowInstanceOwner,Project
```

> [!NOTE]
> For more information about developing against Project Online, please visit the [Project Dev Center](https://go.microsoft.com/fwlink/?linkid=863964). 
  
## Reviewing the errors
<a name="reverrors"> </a>

If the admin created a Project Center view as described above, the view can be accessed following these steps:
  
1. From Project Web App, navigate to Project center by clicking **Projects** from the Quick Launch. 
    
2. Click on **Projects** in the ribbon. 
    
3. Select the view that was created following the steps above from the **View:** dropdown. 
    
    This will provide the user with a list of all the projects and the current status of each project's workflow, including errors.
    
Optionally the user can review the errors through a custom report or programmatically as described above.
  
> [!NOTE]
> The Workflow Created and Workflow Last Run display date and time in UTC. ﻿ 
  
> [!NOTE]
> After acting on the errors it will take up to 24 hours for the status to be updated in Project Center, Project Service OData and through the Project REST AP. 
  
## Acting on the errors and taking additional steps
<a name="ActingonErrors"> </a>

The following errors may happen with a Project workflow:
  
|**Error**|**Action**|
|:-----|:-----|
|We were not able to update the status for project PROJECT_GUID  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF).  <br/> |
|We were not able to update the status for stage STAGE_GUID on project PROJECT_GUID  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF).  <br/> |
|Stage STAGE_GUID is not the current stage for project PROJECT_GUID  <br/> |This error happens when attempting to set workflow stage status for a workflow stage that is not in valid. In this situation, you need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Custom field CUSTOM_FIELD_GUID does not have a value set for project PROJECT_GUID  <br/> |A custom field is not correctly set and the workflow is unable to progress until the custom field value is updated. To determine the name of the custom field that needs to be updated, see the section titled [How to get a Custom Field from a Custom Field GUID](troubleshoot-project-online-workflows.md#custfieldGuid). After updating the custom field, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF).  <br/> > [!NOTE]> As a best practice, it is recommended for true/false custom fields involved in a workflow to use a lookup table opposed to a flag custom field to prevent this issue for custom fields of this type.           |
|The custom field CUSTOM_FIELD_GUID does not exist.  <br/> |This happens when the workflow attempts to read or write the value for a custom field which has been removed from PWA. You will need to edit the workflow and ensure proper custom field is associated with the workflow.  <br/> |
|Failure submitting Check-in job for project PROJECT_GUID  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Failure submitting Publish job for project PROJECT_GUID  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Failure submitting Publish Summary job for project PROJECT_GUID  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Failed to create a project from list item  <br/> |This is an error that is impacting the CreateProjectFromListItem activity. First, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue persists, review the PWA queue to see if there is a failed queue job for the project creation.  <br/> |
|Could not find list item to create a project for web WEB_ID list LIST_ID item LIST_ITEM_ID  <br/> |The list item does not exist anymore. You can check the Recycle Bin to see if you can restore the list item.  <br/> |
|Could not find an idea associated with project PROJECT_GUID while trying to update status  <br/> |This happens when the idea that was initially used for project creation is deleted. You can check the Recycle Bin to see if you can restore the list item.  <br/> |
|Job id JOB_GUID is invalid  <br/> |Contact Microsoft Support if you get this error message.  <br/> |
|Workflow owner does not have permission to check-in project PROJECT_GUID  <br/> |Admin needs to grant check-in permissions to the workflow owner. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Workflow owner does not have Edit Project Summary Fields or Save Project to Project Server or Publish Project category permission on project PROJECT_GUID  <br/> |Admin needs to grant appropriate permission to the workflow owner. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Workflow owner does not have New Project global permission  <br/> |This happens when attempting to create a project from a SharePoint list item and the user that starts the workflow instance cannot create new projects in PWA.  <br/> Admin needs grant appropriate permission to the user. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Workflow owner does not have Open and Save Project To Project Server category permissions on project PROJECT_GUID  <br/> |Admin needs to either grant appropriate permission to the user. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Workflow owner does not have Open Project category permission on project PROJECT_GUID  <br/> |Admin needs to either grant appropriate permission to the user. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Workflow owner does not have Publish Project category permission on project PROJECT_GUID  <br/> |Admin needs to either grant appropriate permission to the user. After granting permissions, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|The project workflow cannot have multiple stages in progress  <br/> |This error shows up if the workflow instance attempts to enter a stage without closing previous stage. Contact Microsoft Support for more help with this error.  <br/> |
|The project workflow must have one stage in progress  <br/> |This error shows up if the workflow instance attempts to leave a stage without setting the next stage in progress. Contact Microsoft Support for more help with this error.  <br/> |
|Project PROJECT_GUID cannot have a workflow  <br/> |This error occurs when trying to start a workflow instance on an unsupported project type. Contact Microsoft Support for more help with this error.  <br/> |
|Project PROJECT_GUID has failed to check-in  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|Project {0} has failed to check-in after the custom field {1} value was updated  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|Project PROJECT_GUID has failed to check-in after the property PROPERTY value was updated  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|Project PROJECT_GUID is checked out in another session  <br/> |Admin needs to either force check-in the project or ask the user to check the project in. After the project is checked-in, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Project PROJECT_GUID is checked out to another user  <br/> |Admin needs to either force check-in the project or ask the user to check the project in. After the project is checked-in, try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF). If the issue continues to persist, you will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|Project PROJECT_GUID does not have a workflow  <br/> |Contact Microsoft Support if you get this error message.  <br/> |
|Project PROJECT_GUID is not checked out  <br/> |The admin will need to review the workflow definition and verify no project updates are attempted before the project is checked-out.  <br/> |
|Project PROJECT_GUID does not exist  <br/> |Contact Microsoft Support if you get this error message.  <br/> |
|Project PROJECT_GUID cannot be published because the PROJ_PWA_SHORT_NAME is in Read Only mode  <br/> |Typically this error will be resolved if no action is taken for a period of time. If you need the error to be resolved immediately, verify that the PWA site is not in read only mode by navigating to the site and seeing if there is a notification across the top of the page. If there is no notification, then try [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF).  <br/> |
|Failed to update project PROJECT_GUID  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|Property PROPERTY does not have a value set for project PROJECT_GUID  <br/> |The admin will need to review the workflow definition and verify properties are being set correctly.  <br/> |
|Property PROPRERTY does not exist  <br/> |Contact Microsoft Support if you get this error message.  <br/> |
|Failed performing a Publish operation on project PROJECT_GUID  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|Failed performing a Publish Summary operation on project PROJECT_GUID  <br/> |A PWA queue job has failed preventing the workflow from progressing. Review the failed queue job from the Manage Queue job page within PWA.  <br/> |
|401 User not found/user is inactive  <br/> |You will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
|System.InvalidOperationException: Incomplete closure detected while loading subroutines for workflow WORKFLOW_GUID in scope.  <br/> |You will need to [How to Restart a Project Workflow](troubleshoot-project-online-workflows.md#restartSPWF).  <br/> |
   
If your error is not listed or you want further details about the error you are getting, see the section [How to get the detailed error message for a SharePoint Workflow](troubleshoot-project-online-workflows.md#detailederror).
  
If you find any other errors that are not listed above, please let us know. There are two ways to contact us, either through our [User Voice forum](https://go.microsoft.com/fwlink/?linkid=863965) or by contacting Microsoft support. Please provide us with the following details. 
  
- Project Name
    
- Workflow Error Code
    
- Workflow Error
    
- Workflow Created
    
- Workflow ID
    
- Workflow Last Run
    
- Workflow Owner
    
- Failed queue message and timestamp if applicable
    
## How to Resume a SharePoint Workflow
<a name="resumeSPWF"> </a>

In some cases a workflow may need to be resumed to retry the current step of the workflow.
  
 **To resume a SharePoint workflow**
  
1. From Project Web App, navigate to Project center by clicking **Projects** from the Quick Launch. 
    
2. Click on the project name.
    
3. Click on the project name from the Quick Launch.
    
4. Expand the **All Workflow Stages** section. 
    
5. Click the **Additional Workflow Data** link. 
    
6. Click the "i" icon beside the **Internal Status**. 
    
7. Click the **Resume this workflow** link. 
    
## How to Restart a Project Workflow
<a name="restartSPWF"> </a>

Restarting a Project workflow will put it back to the start of the workflow. Users will need to advance the workflow back to it's current stage. Before restarting the Project workflow, you may want to first try resuming the workflow to retry the current steps. See [How to Resume a SharePoint Workflow](troubleshoot-project-online-workflows.md#resumeSPWF) for steps on how to resume a workflow. 
  
 **To restart a project workflow**
  
1. From Project Web App, navigate to Project center by clicking **Projects** from the Quick Launch. 
    
2. Click on the project name.
    
3. From the **Project** tab, click on **Options**, then **Restart Workflow**.
    
    > [!NOTE]
    > The project needs to be checked-in before the workflow can be restarted. For more information about checking in a project, please see [Manually check in projects and resources that are checked out by another user](https://support.office.com/article/914852de-7b1d-43f4-8edd-8306d51bd22e). 
  
4. Click **OK**
    
 **To restart project workflows for a set of projects**
  
1. From Project Web App, click on the gear icon then **PWA Settings**.
    
2. Click on **Change or Restart Workflows**.
    
3. Choose the **Enterprise Project Type** from the list for the projects. 
    
4. Select the set of projects that need to have their workflows restarted.
    
    > [!NOTE]
    > Projects need to be checked-in for them to show up in the list. For more information about checking in a project, please see [Manually check in projects and resources that are checked out by another user](https://support.office.com/article/914852de-7b1d-43f4-8edd-8306d51bd22e). 
  
5. Select **Restart current workflow** for the selected projects. 
    
6. Click **OK**.
    
Optionally Project workflows can be programmatically restarted. ProjectWorkflowInstance has two methods to restart Project Workflows:
  
- RestartWorkflow()
  
POST https://CONTOSO.sharepoint.com/teams/project/PWA/_api/projectserver/projects('PROJECT_GUID')/ProjectWorkflowInstance/RestartWorkflow()
    
- RestartWorkflowSkipToStage(stageId)
  
POST https://CONTOSO.sharepoint.com/teams/project/PWA/_api/projectserver/projectworkflowinstances('WORKFLOW_INSTANCE_GUID')/RestartWorkflowSkipToStage('STAGE_GUID')
    
> [!NOTE]
> Restarting Project workflows in bulk may cause throttling to occur. To learn more, please see [SharePoint 2013 workflow throttling and performance in SharePoint Online and Project Online](https://go.microsoft.com/fwlink/?linkid=862660). 
  
## How to get the detailed error message for a SharePoint Workflow
<a name="detailederror"> </a>

If the error message provided in the Project Center does not provide enough details for you to troubleshoot the issue, you may want to review the detailed SharePoint Workflow error message.
  
 **To get the detailed error message for a SharePoint Workflow**
  
1. From Project Web App, navigate to Project center by clicking **Projects** from the Quick Launch. 
    
2. Click on the project name.
    
3. Click on the project name from the Quick Launch.
    
4. Expand the **All Workflow Stages** section. 
    
5. Click the **Additional Workflow Data** link. 
    
6. Click the "i" icon beside the **Internal Status** to see the detailed error message. 
    
## How to get a Custom Field from a Custom Field GUID
<a name="custfieldGuid"> </a>

1. From Project Web App, click on the gear icon then PWA Settings.
    
2. Click **Enterprise Custom Fields and Lookup Tables**. 
    
3. Click on a custom field﻿.
    
4. Scroll to the bottom of the page.
    
5. Expand the **System Identification Data** section to review the Custom Field GUID. 
    
## How to Review PWA Queue Jobs
<a name="custfieldGuid"> </a>

In some cases an error will be a result of a failed PWA queue job. ﻿PWA provides detailed error messages for failed queue jobs.
  
 **To review PWA queue Jobs**
  
1. From Project Web App, click on the gear icon then PWA Settings.
    
2. Click **Manage Queue Jobs**. 
    
3. Find the failed queue job related to the workflow error and click on the error for more details.﻿
    
> [!NOTE]
> You will need to change the **Job History** if the workflow error is older then a week for it to show up in the list. 
  
## Additional Steps
<a name="custfieldGuid"> </a>

 **Workflow Last Run Date is far in the past for an active project**
  
The project may be checked out in another session and the workflow is unable to progress until the project is checked in. The admin may want to consider force checking in the project to allow the workflow to progress. For more information about checking in a project, please see [Manually check in projects and resources that are checked out by another user](https://support.office.com/article/914852de-7b1d-43f4-8edd-8306d51bd22e).
  
> [!NOTE]
> Workflow Last Run Date is referred to Last Submitted Date in the Project Service OData and Project Service REST API. 
