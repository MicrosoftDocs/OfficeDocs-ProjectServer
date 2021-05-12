---
title: "Project Online and Project Server export data definitions"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 7/3/2018
audience: admin
ms.topic: article
ms.service: project-online
localization_priority: Normal
ms.custom: IT_ProjectAdmin_Top
search.appverid:
- PJU140
- PJO150
- PJU150
- PJU160
- MET150
ms.assetid: ce5faeae-9af4-4696-b847-a1f4f20327c7
description: "This technical reference article describes the data objects and properties contained in the output files you receive when using the user data export method described in Export user data from Project Online and in Export user data from Project Server . This article will include short descriptions of the objects and properties you will find in the output data."
---

# Project Online and Project Server export data definitions

This technical reference article describes the data objects and properties contained in the output files you receive when using the user data export method described in [Export user data from Project Online](export-user-data-from-project-online.md) and in [Export user data from Project Server](/Project/export-user-data-from-project-server) . This article will include short descriptions of the objects and properties you will find in the output data. 
  
We can group the user data output your receive from both Project Online and Project Server into the following:
  
- [Project lists](project-online-and-project-server-export-data-definitions.md#project-lists): A list of projects that the user was a part of in the Project Web App (PWA) site.
    
- [Feature-specific data](project-online-and-project-server-export-data-definitions.md#featurespec): Feature in the PWA site in which the user might have data.
    
- [Project-specific user data from the reporting data](project-online-and-project-server-export-data-definitions.md#projectspec): Detailed data about a user's project in the PWA site.
    
- [Project-specific Metadata files](project-online-and-project-server-export-data-definitions.md#ProjSpecMeta): Project metadata about a user's project in the PWA site.
    
## Project lists


You will receive three lists of projects contained in the Project Draft, Published, and Reporting schemas. All the projects in the lists were projects the user was a part of. This means the user was involved in the project as at least one of the following:
  
- Was the project owner.
    
- Has a task assigned to him or her in the project.
    
- Is an assignment owner of a task in the project.
    
- Is the status manager of a task in the project.
    
This data includes:
  
- List of projects from the Draft schema that corresponds to the conditions above.
- List of projects from the Published schema that corresponds to the conditions above.
- List of projects from the Reporting schema that corresponds to the conditions above. 
   
The list of projects may differ slightly for each of the three files. For example, a user can save the project and not publish, meaning that it will appear in the Draft projects list, but not the Published or Reporting projects lists.
  
A project admin can use the Project list files to give them information about which project-specific export files they may be interested in analyzing to decide how much of the exported content should be shared with the user.
  
All three of the ProjectList files will have the following properties for each project listed:
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |The unique identifier for the PWA site in which the project exists.  <br/> |
|Proj_UID  <br/> |The unique identifier for the project.  <br/> |
|Proj_Name  <br/> |Name of the project.  <br/> |
   
## Feature-specific data
<a name="featurespec"> </a>

The export method defined in [Export user data from Project Online](export-user-data-from-project-online.md) creates the following feature-related .json files that checks for a specific user's data in features used in Project Online. If no data is found for the user in that feature, the corresponding .json file will be empty. 
  
The export method defined in [Export user data from Project Server](https://support.office.com/article/c85c548f-4406-4663-8487-192ee065a803) queries for feature-related data through SQL scripts run against the Project Server databases. 
  
The feature areas for both Project Online and Project Server include the following. Click on the feature name in the table to see brief definitions of the objects and properties you may see in the data you export data you receive about the user.
  
|**Name**|**Description**|
|:-----|:-----|
|[AdminAudit](#adminaudit) <br/> |Project Web App server settings change data.  <br/> |
|[BusinessDrivers](project-online-and-project-server-export-data-definitions.md#Drivers) <br/> |Portfolio analysis business drivers data.  <br/> |
|[PortfolioAnalysis](project-online-and-project-server-export-data-definitions.md#Analyses) <br/> |Portfolio analyses data.  <br/> |
|[Calendars](project-online-and-project-server-export-data-definitions.md#Calendars) <br/> |Enterprise calendar data.  <br/> |
|[CustomFields](project-online-and-project-server-export-data-definitions.md#CustomFields) <br/> |Custom field data.  <br/> |
|[Delegations](project-online-and-project-server-export-data-definitions.md#Delegations) <br/> |Delegation data.  <br/> |
|[DriverPrioritizations](project-online-and-project-server-export-data-definitions.md#Prioritizations) <br/> |Business driver prioritizations data.  <br/> |
|[Engagements](project-online-and-project-server-export-data-definitions.md#Engagements) <br/> |Resource engagement data.  <br/> |
|[LookupTables](project-online-and-project-server-export-data-definitions.md#LookupTables) <br/> |Lookup table data.  <br/> |
|[PortfolioAnalysis](project-online-and-project-server-export-data-definitions.md#Analyses) <br/> |Portfolio analyses data.  <br/> |
|[QueueJobs](project-online-and-project-server-export-data-definitions.md#QueueJobs) <br/> |Data about user jobs process through the Queue Service.  <br/> |
|[ReminderEmails](project-online-and-project-server-export-data-definitions.md#ReminderEmails) <br/> |Reminder email data.  <br/> |
|[ReportingResource](project-online-and-project-server-export-data-definitions.md#ReportingResource) <br/> |Resource reporting data.  <br/> |
|[ReportingResourcePlan](project-online-and-project-server-export-data-definitions.md#RepResPlan2) <br/> |Resource plan reporting data.  <br/> |
|[Resource](project-online-and-project-server-export-data-definitions.md#Resource) <br/> |Resource data.  <br/> |
|[ResourcePlans](project-online-and-project-server-export-data-definitions.md#ResourcePlan) <br/> |Resource plan data.  <br/> |
|[Rules](project-online-and-project-server-export-data-definitions.md#rules) <br/> |Rules data.  <br/> |
|[Security](project-online-and-project-server-export-data-definitions.md#Security) <br/> |Data about security groups, categories, and permissions.  <br/> |
|[StatusReports](project-online-and-project-server-export-data-definitions.md#StatusReports) <br/> |Status report data.  <br/> |
|[SubscribedReminders](project-online-and-project-server-export-data-definitions.md#SubscribedReminders) <br/> |Subscribed reminders data.  <br/> |
|[TaskStatus_AssignmentsHistory](project-online-and-project-server-export-data-definitions.md#StatusAssignHis) <br/> |Statusing assignments history data.  <br/> |
|[TaskStatus_AssignmentsSaved](project-online-and-project-server-export-data-definitions.md#StatusAssignSaved) <br/> |Statusing assignments save data.  <br/> |
|[TaskStatus_AssignmentsSubmitted](project-online-and-project-server-export-data-definitions.md#StatusAssignsub) <br/> |Statusing assignments submit data.  <br/> |
|[Timesheets](project-online-and-project-server-export-data-definitions.md#Timesheets) <br/> |Data about timesheets.  <br/> |
|[Timesheets_Reporting](project-online-and-project-server-export-data-definitions.md#Timesheets_Reporting) <br/> |Reporting data about timesheets.  <br/> |
|[UnsubscribedAlerts](project-online-and-project-server-export-data-definitions.md#UnsubscribedAlerts) <br/> |Unsubscribed alerts data.  <br/> |
|[UserViewSettings](project-online-and-project-server-export-data-definitions.md#UserProp) <br/> |User view settings data.  <br/> |
|[Workflow](project-online-and-project-server-export-data-definitions.md#Workflow) <br/> |Project workflow data.  <br/> |
|[WorkspaceItems](project-online-and-project-server-export-data-definitions.md#WSS) <br/> |Data about SharePoint items from project sites.  <br/> |
   
### AdminAudit
<a name="AdminAudit"> </a>

AdminAudit contains data about Project Web App server settings that the user changed. Each **AdminAuditData** object will have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|ServerSettingName  <br/> |Name of the PWA server setting.  <br/> |
|SettingOldValue  <br/> |Previous value for the setting.  <br/> |
|SettingNewValue  <br/> |New value for the setting.  <br/> |
|ChangedDate  <br/> |Time and date the setting was changed.  <br/> |
|ResourceUid  <br/> |Unique identifier for the resource that made the setting change.  <br/> |
|ResourceName  <br/> |Name for the resource that made the setting change.  <br/> |
   
### BusinessDrivers
<a name="Drivers"> </a>

BusinessDrivers contains data about Portfolio Analysis business drivers that the user created or modified. Each **Drivers** object will have the following properties: 
  
|****Property****|****Description****|
|:-----|:-----|
|DriverID  <br/> |Unique identifier of the business driver.  <br/> |
|DriverDescription  <br/> |Description of the business driver.  <br/> |
|BusinessDriverIsActive  <br/> |Is the business driver active (true/false).  <br/> |
|CreatedByResourceID  <br/> |Unique identifier of the resource that created the driver.  <br/> |
|CreatedByResourceName  <br/> |Display name of the resource that created the driver.  <br/> |
|ModifiedByResourceID  <br/> |Unique identifier of the resource that modified the driver.  <br/> |
|ModifiedByResourceName  <br/> |Display name of the resource that modified the driver.  <br/> |
|ImpactDescriptionNone  <br/> |Description of what is considered to be no impact for the driver.  <br/> |
|ImpactDescriptionLow  <br/> |Description of what is considered to be low impact for the driver.  <br/> |
|ImpactDescriptionModerate  <br/> |Description of what is considered to be moderate impact for the driver.  <br/> |
|ImpactDescriptionStrong  <br/> |Description of what is considered to be strong impact for the driver.  <br/> |
|ImpactDescriptionExtreme  <br/> |Description of what is considered to be extreme impact for the driver.  <br/> |
|CreatedDate  <br/> |Date and timestamp of when the driver was created.  <br/> |
|ModifiedDate  <br/> |Date and timestamp of when the driver was last modified.  <br/> |
   
Each **Drivers** object can have **Department** objects, which have the following properties. 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|DriverId  <br/> |Unique identifier for the business driver.  <br/> |
|DepartmentId  <br/> |Unique identifier for the department.  <br/> |
|DepartmentName  <br/> |Name of the department.  <br/> |
   
### Calendars
<a name="Calendars"> </a>

Calendars contains data about enterprise calendars that are currently checked out by the user. Each **CalendarData** object will have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|Id  <br/> |Unique identifier for the calendar.  <br/> |
|Name  <br/> |Name of the calendar.  <br/> |
|CheckedOutDate  <br/> |Date and time the calendar was checked out.  <br/> |
   
### CustomFields
<a name="CustomFields"> </a>

CustomFields contains data about custom fields that are currently checked out by the user. Each **CustomFieldData** object will have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ID  <br/> |Unique identifier for the custom field.  <br/> |
|Name  <br/> |Name of the custom field.  <br/> |
|CheckOutDate  <br/> |Time and date the custom field was last checked out.  <br/> |
   
### Delegations
<a name="Delegations"> </a>

Delegations contains data about delegations that the user is involved in. The user can either be the delegate or the person who requests for the delegation. Each **DelegationData** object will have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|Id  <br/> |Unique identifier for the delegation.  <br/> |
|ResourceId  <br/> |Unique identifier for the resource that requested the delegation.  <br/> |
|ResourceName  <br/> |Name of the resource that requested the delegation.  <br/> |
|DelegateResourceId  <br/> |Unique identifier for the delegate.  <br/> |
|DelegateName  <br/> |Name of the delegate.  <br/> |
|StartDate  <br/> |Start date for the delegation period.  <br/> |
|FinishDate  <br/> |End date for the delegation period.  <br/> |
   
### DriverPrioritizations
<a name="Prioritizations"> </a>

DriverPrioritizations contains data about business driver prioritizations that the user created or modified. Each **Prioritizations** object may have the following properties: 
  
|****Property****|****Description****|
|:-----|:-----|
|PrioritizationId  <br/> |Unique identifier of the portfolio analysis prioritization.  <br/> |
|PrioritizationName  <br/> |Name of the portfolio analysis prioritization.  <br/> |
|PrioritizationDescription  <br/> |Description of the portfolio analysis prioritization.  <br/> |
|ConsistencyRatio  <br/> |The prioritization consistency ratio.  <br/> |
|PrioritizationIsManual  <br/> |True if a portfolio analysis prioritization is manual. If False, it is calculated.  <br/> |
|DepartmentId  <br/> |Unique identifier for the department.  <br/> |
|DepartmentName  <br/> |Name of the department.  <br/> |
|CreatedByResourceId  <br/> |Unique identifier of the resource that created the prioritization.  <br/> |
|CreatedByResourceName  <br/> |Name of the resource that created the prioritization.  <br/> |
|ModifiedByResourceID  <br/> |Unique identifier of the resource that last updated the prioritization.  <br/> |
|ModifiedByResourceName  <br/> |Display name of the resource that last updated the prioritization.  <br/> |
|CreatedDate  <br/> |Date and time when the prioritization was created.  <br/> |
|ModifiedDate  <br/> |Date and time when the prioritization was last updated.  <br/> |
   
For **BusinessDrivers**, you will see the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PrioritizationId  <br/> |Unique identifier for the prioritization.  <br/> |
|BusinessDriverId  <br/> |Unique identifier for the business driver.  <br/> |
|BusinessDriverName  <br/> |Name of the business driver.  <br/> |
|BusinessDriverPriorityPercentage  <br/> |Priority percentage assigned to the business driver.  <br/> |
   
For the **DriverRankings**, you will see the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PrioritizationId  <br/> |Unique identifier for the prioritization.  <br/> |
|BusinessDriver1Id  <br/> |Unique identifier for the first business driver in the prioritization.  <br/> |
|BusinessDriver1Name  <br/> |Name of the first business driver in the prioritization.  <br/> |
|RelationValue  <br/> |Relationship value assigned to this business driver in comparison to another business driver.  <br/> |
|BusinessDriver2Id  <br/> |Unique identifier for the second business driver in the prioritization.  <br/> |
|BusinessDriver2Name  <br/> |Name of the second business driver in the prioritization.  <br/> |
   
### Engagements
<a name="Engagements"> </a>

Engagements contains data about resource engagements that the user created or modified, or was requested as a resource. Each **Engagement** object will have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|EngagementUID  <br/> |Unique identifier for the engagement.  <br/> |
|ProjectID  <br/> |Unique identifier for the project for which the engagement was requested.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource requested.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|EngagementName  <br/> |Name of the engagement.  <br/> |
|CreatedDate  <br/> |Date the engagement was created.  <br/> |
|SubmittedDate  <br/> |Date the engagement was submitted for approval.  <br/> |
|ReviewedDate  <br/> |Date the engagement was reviewed.  <br/> |
|LastModifiedDate  <br/> |Date the engagement was last modified.  <br/> |
|SubmitterResourceUID  <br/> |Unique identifier for the resource that submitted the engagement.  <br/> |
|SumitterResourceName  <br/> |Resource name of the submitter.  <br/> |
|ReviewerResourceUID  <br/> |Unique identifier for the resource that reviewed the engagement.  <br/> |
|ReviewerResourceName  <br/> |Display name of the resource that reviewed the engagement request.  <br/> |
|LastModifiedByResourceUID  <br/> |Unique identifier of the resource that last modified the engagement request.  <br/> |
|LastModifiedByResourceName  <br/> |Display name of the resource that last modified the engagement request.  <br/> |
|EngagementStatus  <br/> | Status of the engagement request:  <br/>  0- Committed  <br/>  1- Proposed  <br/>  2- Draft  <br/>  3- Rejected  <br/> |

   
Each **Engagements** object can contain multiple **EngagementSegments**, which may have the following properties:
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|EngagementUID  <br/> |Unique identifier for the engagement that contains the EngagementSegment.  <br/> |
|SegmentType  <br/> | 0- Committed  <br/>  1- Proposed  <br/>  2- Draft  <br/>  3- Rejected  <br/> |
|SegmentStartDate  <br/> |The proposed start date. Depending on the SegmentType, this is proposed/draft/committed start date for the segment.  <br/> |
|SegmentFinishDate  <br/> |The proposed end date. Depending on the SegmentType, this is proposed/draft/committed end date for the segment.  <br/> |
|SegmentMaxUnits  <br/> |Maximum number of units representing capacity.  <br/> |
|SegmentWork  <br/> |Number of work units for a work day.  <br/> |
   
Each **Engagements** object can contain **EngagementComments**, which may have the following properties:

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CommentUID  <br/> |Unique identifier for the comment.  <br/> |
|EngagementUID  <br/> |Unique identifier for the engagement that contains the EngagementSegment.  <br/> |
|CommentCreatedDate  <br/> |Date the comment was created.  <br/> |
|CommentMessage  <br/> |Comment details.  <br/> |
|CommentAuthorResourceUID  <br/> |Resource UID of the author of the comment.  <br/> |
|CommentAuthorResourceName  <br/> |Resource name of the author of the comment.  <br/> |
   
### LookupTables
<a name="LookupTables"> </a>

LookupTables contains data about lookup tables that are currently checked out by the user. Each **LookupTableData** object may have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ID  <br/> |Unique identifier for the lookup table.  <br/> |
|Name  <br/> |Name of the lookup table.  <br/> |
|CheckOutDate  <br/> |Time and date the lookup table was last checked out.  <br/> |
   
### PortfolioAnalysis
<a name="Analyses"> </a>

PortfolioAnalysis contains data about Portfolio Analyses that the user created or modified. Each **Analyses** object will have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|AnalysisDescription  <br/> |Description of the analysis.  <br/> |
|AnalysisType  <br/> |Type of analysis.  <br/> |
|PrioritizationType  <br/> |Prioritization type for the analysis (Business driver or Custom fields).  <br/> |
|PrioritizationID  <br/> |Unique identifier for the prioritization.  <br/> |
|PrioritizationName  <br/> |Name of the prioritization.  <br/> |
|HardConstraintCustomFieldID  <br/> |Unique identifier for the custom field selected as the primary cost constraint.  <br/> |
|HardConstraintCustomFieldName  <br/> |Name of the custom field selected as the primary cost constraint.  <br/> |
|TimeScale  <br/> | The time scale selected for the analysis:  <br/>  0- Days  <br/>  1- Weeks  <br/>  2- Months  <br/>  3- Quarters  <br/>  4- Years  <br/> |
|BookingType  <br/> |Specifies whether a resource is considered committed or proposed.  <br/> |
|ModifiedByResourceID  <br/> |Unique identifier for the resource that last modified the analysis.  <br/> |
|ModifiedByResourceName  <br/> |Name of the resource that last modified the analysis.  <br/> |
|CreatedByResourceId  <br/> |Unique identifier for the resource that created the analysis.  <br/> |
|CreatedByResourceName  <br/> |Name of the resource that created the analysis.  <br/> |
|DepartmentId  <br/> |Unique identifier for the department.  <br/> |
|DepartmentName  <br/> |Name of the department.  <br/> |
|FilterResourcesByDepartment  <br/> |True if resources are filtered by department.  <br/> |
|FilterResourcesByRBS  <br/> |True if are resources filtered by resource breakdown structure.  <br/> |
|FilterResourcesByRBSValueId  <br/> |The identifier of the RBS value being used for filtering.  <br/> |
|FilterResourcesByRBSValueText  <br/> |The actual text of the RBS value being used for filtering.  <br/> |
|UseAlternateProjectDatesForResourcePlans  <br/> |True if alternate project dates are used for resource plans.  <br/> |
|AlternateProjectStartDateCustomFieldId  <br/> |The GUID for a custom field that contains an alternate start date for a portfolio analysis.  <br/> |
|AlternateProjectStartDateCustomFieldName  <br/> |The name of a custom field that contains an alternate start date for a portfolio analysis.  <br/> |
|AlternateProjectEndDateCustomFieldId  <br/> |The GUID for a custom field that contains an alternate end date and time for a portfolio analysis.  <br/> |
|AlternateProjectEndDateCustomFieldName  <br/> |The name of a custom field that contains an alternate end date and time for a portfolio analysis.  <br/> |
|ForcedInAliasLookupTableId  <br/> |Identifier of the internal lookup table used for forcing in projects.  <br/> |
|ForcedInAliasLookupTableName  <br/> |Name of the internal lookup table used for forcing in projects  <br/> |
|ForcedOutAliasLookupTableId  <br/> |Identifier of the internal lookup table used for forcing out projects.  <br/> |
|ForcedOutAliasLookupTableName  <br/> |Name of the internal lookup table used for forcing out projects  <br/> |
|CreatedDate  <br/> |Date the analysis was created.  <br/> |
|ModifiedDate  <br/> |Date the analysis was last modified.  <br/> |
|ProjectData  <br/> |Dataset link for more information about the project on which the analysis was done.  <br/> |
   
Each **Analyses** object can have **ProjectData** properties, which include: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|AnalysisPriority  <br/> |Project priority.  <br/> |
|AbsolutePriority  <br/> |Normalized project priority.  <br/> |
|OriginalStartDate  <br/> |Original start date of the project.  <br/> |
|OriginalEndDate  <br/> |Original end date of the project.  <br/> |
|StartDate  <br/> |Start date of the project.  <br/> |
|Duration  <br/> |Duration of the project.  <br/> |
|StartNoEarlierThan  <br/> |Project starts no earlier than specified date.  <br/> |
|FinishNoLaterThan  <br/> |Project starts no later than specified date.  <br/> |
|Locked  <br/> |True if project is locked.  <br/> |
   
For Optimizer Solutions, **CostConstraintProject** objects can have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ScenarioId  <br/> |Identifier of the cost constraint scenario.  <br/> |
|ScenarioName  <br/> |Name of the cost constraint scenario.  <br/> |
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|ProjectId  <br/> |Identifier of the project included in the cost constraint scenario.  <br/> |
|ProjectName  <br/> |Name of the project included in the cost constraint scenario.  <br/> |
|ProjectStatus  <br/> |Status of the project.  <br/> |
|ForceStatus  <br/> |Force status of the project (whether it is forced in or forced out).  <br/> |
|ForceAliasLookupTableId  <br/> |Identifier of the internal lookup table used for forcing in projects.  <br/> |
|ForceAliasLookupTableName  <br/> |Name of the internal lookup table used for forcing in projects.  <br/> |
|ProjectPriority  <br/> |Priority of the project.  <br/> |
|AbsolutePriority  <br/> |Normalized project priority.  <br/> |
|HardConstraintValue  <br/> |Value of the project for the custom field select as a hard constraint.  <br/> |
   
For Optimizer Solutions, **CostConstraintScenario** objects can have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|ScenarioId  <br/> |Identifier of the cost constraint scenario.  <br/> |
|ScenarioName  <br/> |Name of the cost constraint scenario.  <br/> |
|ScenarioDescription  <br/> |Description of the cost constraint scenario.  <br/> |
|UseDependencies  <br/> |Specify whether or not the cost constraint scenario uses dependencies.  <br/> |
|CreatedByResourceId  <br/> |Identifier for the resource that created the cost constraint scenario.  <br/> |
|CreatedByResourceName  <br/> |Name for the resource that created the cost constraint scenario.  <br/> |
|ModifiedByResourceId  <br/> |Identifier for the resource that modified the cost constraint scenario.  <br/> |
|ModifiedByResourceName  <br/> |Name of the resource that modified the cost constraint scenario.  <br/> |
|CreatedDate  <br/> |Date when cost constraint scenario was created.  <br/> |
|ModifiedDate  <br/> |Date when cost constraint scenario was last modified.  <br/> |
|SelectedProjectsCost  <br/> |Cost of the selected project.  <br/> |
|SelectedProjectsPriority  <br/> |Priority of the selected project.  <br/> |
|UnselectedProjectsCost  <br/> |Cost of the unselected project.  <br/> |
|UnselectedProjectsPriority  <br/> |Priority of the unselected project.  <br/> |
   
For Planner Solutions, **ResourceConstraintProject** objects can have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ScenarioId  <br/> |Identifier of the cost constraint scenario.  <br/> |
|ScenarioName  <br/> |Name of the cost constraint scenario.  <br/> |
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|CostConstraintScenarioId  <br/> |Unique identifier for the portfolio analysis cost constraint scenario.  <br/> |
|CostConstraintScenarioName  <br/> |The name of a portfolio analysis cost constraint scenario.  <br/> |
|ProjectId  <br/> |Identifier of the project included in the cost constraint scenario.  <br/> |
|ProjectName  <br/> |Name of the project included in the cost constraint scenario.  <br/> |
|NewStartDate  <br/> |The new start date of the project.  <br/> |
|ForceStatus  <br/> |Force status of the project (whether it is forced in or forced out).  <br/> |
|ProjectStatus  <br/> |The status of the project.  <br/> |
|ResourceWork  <br/> |The amount of work that is performed by a resource on a project.  <br/> |
|ResourceCost  <br/> |The cost of a resource on a project.  <br/> |
|ForceAliasLookupTableId  <br/> |Identifier of the internal lookup table used for forcing in projects.  <br/> |
|ForceAliasLookupTableName  <br/> |Name of the internal lookup table used for forcing in projects.  <br/> |
|ProjectPriority  <br/> |Priority of the project.  <br/> |
|AbsolutePriority  <br/> |Normalized project priority.  <br/> |
|HardConstraintValue  <br/> |Value of the project for the custom field select as a hard constraint.  <br/> |
   
For Planner Solutions, **ResourceConstraintScenario** objects can have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ScenarioId  <br/> |Identifier of the cost constraint scenario.  <br/> |
|ScenarioName  <br/> |Name of the cost constraint scenario.  <br/> |
|ScenarioDescription  <br/> |Description of the cost constraint scenario.  <br/> |
|AnalysisID  <br/> |Unique identifier for the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|CostConstraintScenarioId  <br/> |Unique identifier for the portfolio analysis cost constraint scenario.  <br/> |
|CostConstraintScenarioName  <br/> |The name of a portfolio analysis cost constraint scenario.  <br/> |
|ConstraintType  <br/> |The type of restriction or constraint.  <br/> |
|ConstraintValue  <br/> |A value that indicates the limit of a constraint.  <br/> |
|AllocationThreshold  <br/> |The percentage number between 0 and 100 that specifies the minimum threshold that is required for a resource to be allocated to a project.  <br/> |
|RateTable  <br/> |The cost rate table used for the resource.  <br/> |
|EnforceProjectDependencies  <br/> |A flag that indicates whether project dependencies are enforced.  <br/> |
|EnforceSchedulingConstraints  <br/> |A flag that indicates whether scheduling constraints are enforced.  <br/> |
|HiringType  <br/> |The internal or external hiring type.  <br/> |
|CreatedByResourceId  <br/> |Identifier for the resource that created the cost constraint scenario.  <br/> |
|CreatedByResourceName  <br/> |Name for the resource that created the cost constraint scenario.  <br/> |
|ModifiedByResourceId  <br/> |Identifier for the resource that modified the cost constraint scenario.  <br/> |
|ModifiedByResourceName  <br/> |Name of the resource that modified the cost constraint scenario.  <br/> |
|CreatedDate  <br/> |Date when cost constraint scenario was created.  <br/> |
|ModifiedDate  <br/> |Date when cost constraint scenario was last modified.  <br/> |
   
### QueueJobs
<a name="QueueJobs"> </a>

QueueJobs contains data about jobs that were created by the user through the Queuing service. Each **QueueData** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CorrelationId  <br/> |Unique identifier for jobs that are part of a correlation with other jobs.  <br/> |
|QueueState  <br/> | Queue state the job is currently in:  <br/>  0- Unknown  <br/>  1- ReadyForProcessing  <br/>  2- SendIncomplete  <br/>  3- Processing  <br/>  4- Success  <br/>  5- Failed  <br/>  6- FailedNotBlocking  <br/>  7-ProcessingDeferred  <br/>  8- CorrelationBlocked  <br/>  9- Cancelled  <br/>  10- OnHold  <br/>  11- Sleeping  <br/>  12- ReadyForLaunch  <br/> |
|MessageType  <br/> |Queue job type (see the corresponding QueueStateLabel value).  <br/> |
|ErrorInfo  <br/> |Error details about the queue job.  <br/> |
|JobId  <br/> |Unique identifier for the queue job.  <br/> |
|PercentComplete  <br/> |Current percentage completed of processing the job through the Queue service.  <br/> |
|CreatedDate  <br/> |Date and time the queue job was created.  <br/> |
|ProcessingDate  <br/> |Date and time the queue job began processing through the Queue service.  <br/> |
|CompletedDate  <br/> |Date and time the queue job was processed through the Queue service.  <br/> |
|ReadyForProcessingDate  <br/> |Date and time the queue job was ready to be picked up for processed through the Queue service.  <br/> |
|MessageTypeLabel  <br/> |Job type (associated with the MessageType value).  <br/> |
|QueueStateLabel  <br/> |Current queue state of the job (see the corresponding QueueStateValue).  <br/> |
   
### ReminderEmails
<a name="ReminderEmails"> </a>

ReminderEmails contains data about email reminder notifications for the user. Each **ReminderEmailData** object will have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|SessionId  <br/> |The unique identifier for the reminder emails.  <br/> |
|EmailType  <br/> |The type of emails: Task, StatusReport, Timesheet, or Engagement.  <br/> |
|RowIsReady  <br/> |If the email is ready to be sent out.  <br/> |
   
### ReportingResource
<a name="ReportingResource"> </a>

ReportingResource contains data about reporting resources. Each **ReportingResourceData** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|ResourceNTAccount  <br/> |The Windows account name for a resource.  <br/> |
|UserClaimsAccount  <br/> |Login name for the user.  <br/> |
|ResourceEmailAddress  <br/> |The email address of a resource.  <br/> |
|ResourceCanLevel  <br/> |True if resource leveling can be done.  <br/> |
|ResourceEarliestAvailableFrom  <br/> |The earliest date that a resource is available for work on a particular task.  <br/> |
|ResourceLatestAvailableTo  <br/> |The last date that a resource is available.  <br/> |
|ResourceStandardRate  <br/> |The standard rate of pay for a resource.  <br/> |
|ResourceOvertimeRate  <br/> |The rate of overtime pay for a resource.  <br/> |
|ResourceMaxUnits  <br/> |The maximum capacity (percentage or units) that a resource is available to accomplish tasks during the current time period.  <br/> |
|ResourceBaseCalendar  <br/> |The base calendar for a resource.  <br/> |
|ResourceHyperlinkFriendlyName  <br/> |Shows the title or explanatory text for a hyperlink associated with a resource.  <br/> |
|ResourceHyperlinkHref  <br/> |The text that is displayed for a resource hyperlink, as specified in the Edit User page of Project Web Access.  <br/> |
|ResourceInitials  <br/> |The initials of a resource.  <br/> |
|ResourceType  <br/> |The type of a resource (for example, Enterprise, Local, Project Server, Material, or Generic). See [ResourceType Enumerations](/previous-versions/office/project-class/jj232846(v=office.15)) for values.  <br/> |
|ResourceBookingType  <br/> |The resource booking type: proposed or committed.  <br/> |
|ResourceCostPerUse  <br/> |The cost that accrues each time a work resource is used.  <br/> |
|ResourceGroup  <br/> |The group to which resource belongs.  <br/> |
|ResourceCode  <br/> |Contains any code, abbreviation, or number you want to enter as part of a resource's information.  <br/> |
|ResourceTimesheetManagerUID  <br/> |The unique identifier of a timesheet manager.  <br/> |
|ResourceName(OR ResourceName1)  <br/> |Display name of the resource.  <br/> |
|ResourceWorkgroup  <br/> |A number value that represents a team collaboration method for a resource.  <br/> |
|ResourceCostCenter  <br/> |A user-defined code for resource cost accounting.  <br/> |
|ResourceIsTeam  <br/> |True if a resource is a team resource.  <br/> |
|ResourceRequiresEngagements  <br/> |True if the resource can only be requested through an engagement request.  <br/> |
|ResourceCreatedDate  <br/> |The date and time that a resource was created in the project.  <br/> |
|ResourceModifiedDate  <br/> |The date that information about a resource was last modified.  <br/> |
   
Each **Customfields** object may have the following properties: 
  
|**Property**|**Description**|
|:-----|:-----|
|CustomFieldValueUID  <br/> |Unique identifier for the custom field value.  <br/> |
|CustomFieldTypeUID  <br/> |Unique identifier for the custom field type.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|EntityUID(OR ResourceUID)  <br/> |Unique identifier for the resource.  <br/> |
|CFValue  <br/> |Custom field value.  <br/> |
   
Each **ResourceCapacityData** object may have the following properties: 
  
|**Property**|**Description**|
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|TimeByDay  <br/> |A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
|BaseCapacity  <br/> |The maximum work capacity that is determined by the resource calendar. Also known as baseline capacity.  <br/> |
|Capacity  <br/> |The amount of work that can be done by a resource.  <br/> |
   
### ReportingResourcePlan
<a name="RepResPlan2"> </a>

ReportingResourcePlan contains data about reporting resource plans. It may have the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|AssignmentId  <br/> |Unique identifier for the assignment.  <br/> |
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|TaskId  <br/> |Unique identifier for the task.  <br/> |
|ResourceOwnerId  <br/> |Resource ID of the resource owner.  <br/> |
|AssignmentCost  <br/> |The total scheduled (or projected) cost for an assignment.  <br/> |
|AssignmentOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the assignment.  <br/> |
|AssignmentActualCost  <br/> |The costs incurred for work that has already been performed on an assignment, along with any other associated costs.  <br/> |
|AssignmentActualOvertimeCost  <br/> |The costs incurred for overtime work that has already been performed on an assignment.  <br/> |
|AssignmentWork  <br/> |The total amount of time, such as person-hours or days, that is scheduled for an assignment.  <br/> |
|AssignmentOvertimeWork  <br/> |The total overtime work for an assignment, including overtime work that has already been performed, in addition to remaining overtime work.  <br/> |
|AssignmentActualWork  <br/> |The amount of work that has already been performed on an assignment.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work that has already been performed on an assignment.  <br/> |
|AssignmentMaterialWork  <br/> |The total work time scheduled for a material resource.  <br/> |
|AssignmentMaterialActualWork  <br/> |The actual amount of work that has already been performed with the use of a material resource, usually expressed as a percentage of the scheduled amount of material resource work.  <br/> |
|AssignmentPercentWorkCompleted  <br/> |Percentage of work that has been completed.  <br/> |
|AssignmentStartDate  <br/> |Date a resource is scheduled to begin an assignment.  <br/> |
|AssignmentFinishDate  <br/> |Assignment finish date.  <br/> |
|AssignmentDelay  <br/> |Amount of time a resource is to wait before starting to work on an assignment.  <br/> |
|AssignmentStartVariance  <br/> |Variance at the start of the assignment.  <br/> |
|AssignmentFinishVariance  <br/> |Variance at the assignment finish.  <br/> |
|AssignmentACWP  <br/> |Actual cost of work performed for the assignment.  <br/> |
|AssignmentBCWP  <br/> |Budgeted cost of work performed for the assignment (earned value).  <br/> |
|AssignmentBCWS  <br/> |Budgeted cost of work scheduled for the assignment (planned value).  <br/> |
|AssignmentBookingID  <br/> |Assignment booking GUID.  <br/> |
|AssignmentType  <br/> |Type of assignment. NormalAssignment=0, WorkOnlyAssignment=1, FixedCostAssignment=2, FixedCostWorkOnlyAssignment=3, EmptyAssignment=4, FixedCostGeneratedAssignment=100 (generated during RDS transfer), ResourcePlanAssignment=101.  <br/> |
|AssignmentResourceType  <br/> |The type of resource that is associated with an assignment. See [Type enumeration](/previous-versions/office/project-class/gg223589(v=office.15)).  <br/> |
|IsPublic  <br/> |True if the item was published, so a team member can see it.  <br/> |
|AssignmentIsPublished  <br/> |True if assignment is published.  <br/> |
|AssignmentWorkVariance  <br/> |The variance of assignment work from the baseline work as minutes x 1000.  <br/> |
|AssignmentCostVariance  <br/> |The difference between the cost and baseline cost for a resource.  <br/> |
|AssignmentCV  <br/> |Earned value cost variance.  <br/> |
|AssignmentSV  <br/> |Earned value schedule variance.  <br/> |
|AssignmentIsOverallocated  <br/> |True if any assigned resources are overallocated.  <br/> |
|AssignmentPeakUnits  <br/> |Maximum number of units that a resource is assignmed for a task.  <br/> |
|AssignmentCreatedDate  <br/> |Date and time the assignment was created.  <br/> |
|AssignmentModifiedDate  <br/> |Date and time the assignment was last updated.  <br/> |
|AssignmentBudgetCost  <br/> |The total projected cost of an assignment.  <br/> |
|AssignmentBudgetWork  <br/> |The total projected amount of work that is planned for an assignment.  <br/> |
|AssignmentBudgetMaterialsWork  <br/> |The total projected amount of use on the assignment of material resources.  <br/> |
|AssignmentResourcePlanWork  <br/> |The total time that is scheduled for an assignment in the resource plan.  <br/> |
|TaskIsActive  <br/> |True if the task for the assignment timephased data is active.  <br/> |
|TimesheetClassUid  <br/> |GUID of the timesheet class.  <br/> |
   
### Resource
<a name="Resource"> </a>

Resource contains data about the resource. Each **ResourceData** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceID  <br/> |ID of the resource within the list of resources.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|ResourceAccount  <br/> |User's account.  <br/> |
|UserClaimsAccount  <br/> |User's claims account (same as the Office 365 account when using Project Online).  <br/> |
|ResourceEmailAddress  <br/> |The email address of a resource.  <br/> |
|ResourceEmailLanguage  <br/> |Language code used for the resources email.  <br/> |
|ResourceIsOffline  <br/> |True if the resource is offline. This feature is deprecated.  <br/> |
|ResourceLastConnectDate  <br/> |The last time the resource connected. This feature is deprecated.  <br/> |
|ResourcePhonetics  <br/> |The phonetic spelling of the resource name. For use with Japanese only.  <br/> |
|ResourceHasNotes  <br/> |Whether the resource has notes (value of 2)  <br/> |
|ResourceCanBeLeveled  <br/> |True if resource leveling can be done.  <br/> |
|ResourceAccrueAt  <br/> |How cost is accrued against the resource. (1=Start, 2=End, 3=Prorated, 4=Invalid).  <br/> |
|ResourceAvailableFrom  <br/> |The starting date that a resource is available for work at the units specified for the current time period.  <br/> |
|ResourceAvailableTo  <br/> |The end date that a resource is available for work at the units specified for the current time period.  <br/> |
|ResourceStandardRate  <br/> |The standard rate of pay for a resource.  <br/> |
|ResourceOvertimeRate  <br/> |The rate of overtime pay for a resource.  <br/> |
|ResourceMaxUnits  <br/> |The maximum capacity (percentage or units) that a resource is available to accomplish tasks during the current time period.  <br/> |
|ResourceBaseCalendar  <br/> |The base calendar for a resource.  <br/> |
|ResourceHyperlinkFriendlyName  <br/> |Shows the title or explanatory text for a hyperlink associated with a resource.  <br/> |
|ResourceHyperlinkHref  <br/> |Contains the combination, or concatenation, of the Hyperlink Address and Hyperlink SubAddress fields associated with a resource..  <br/> |
|ResourceInitials  <br/> |The initials of a resource.  <br/> |
|ResourceType  <br/> |The type of a resource. See [ResourceType Enumerations](/previous-versions/office/project-class/jj232846(v=office.15)) for values.  <br/> |
|ResourceBookingType  <br/> |The resource booking type: proposed or committed.  <br/> |
|ResourceGroup  <br/> |The name of the group that a resource belongs to.  <br/> |
|ResourceCode  <br/> |Contains any code, abbreviation, or number you want to enter as part of a resource's information.  <br/> |
|ResourceCostPerUse  <br/> |The cost that accrues each time a work resource is used.  <br/> |
|DefaultAssignmentOwner  <br/> |Default assignment owner for the resource.  <br/> |
|DefaultAssignmentOwnerDisplayName  <br/> |Display name of the default assignment owner.  <br/> |
|ResourceTimesheetManagerUID  <br/> |Timesheet manager for the given resource.  <br/> |
|ResourceTimesheetManagerDisplayName  <br/> |Display name of the timesheet manager.  <br/> |
|ResourceCostCenter  <br/> |The cost center for the resource.  <br/> |
|ResourceIsTeam  <br/> |True if a resource is a team resource.  <br/> |
|ResourceRequiresEngagements  <br/> |True if the resource can only be requested through an engagement request.  <br/> |
|ResourceCreatedDate  <br/> |The date and time that a resource was created.  <br/> |
|ResourceModifiedDate  <br/> |The date that information about a resource was last modified.  <br/> |
|CheckedOutDate  <br/> |Time and date the resource was last checked out.  <br/> |
|CheckedOutBy  <br/> |The user that checked out the resource.  <br/> |
|DefaultAssignmentOwnerResources  <br/> |Resources for which the resource is the default assignment owner.  <br/> |
   
Each **ResourceData** object may have a collection of **DefaultAssignmentOwnerResources**. Each **DefaultAssignmentOwnerResources** object may have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceID  <br/> |The ID of the resource within the list of resources.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource for which the user is the default assignment owner.  <br/> |
|ResourceName  <br/> |Name of the resource.  <br/> |
|ResourceType  <br/> |The type of a resource (for example, Enterprise, Local, Project Server, Material, or Generic). See [ResourceType Enumerations](/previous-versions/office/project-class/jj232846(v=office.15)) for values.  <br/> |
|DefaultAssignmentOwner  <br/> |Default assignment owner for the resource.  <br/> |
   
Each **ResourceData** object may also have a collection of **CustomFields**. Each **CustomFields** object may contain the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|CustomFieldUid  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|CustomFieldValue  <br/> |Value properties for the custom field.  <br/> |
   
### ResourcePlans
<a name="ResourcePlan"> </a>

ResourcePlans contains data about resource plans the user created, modified, or was a part. For each **ResourcePlans** object, you will see the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|ResourcePlanUtilizationType  <br/> |Value that represents the utilization type of a resource plan.  <br/> |
|ResourcePlanUtilizationDate  <br/> |The start date and time for use of the resource plan.  <br/> |
|ResourceId  <br/> |Unique identifier of the resource.  <br/> |
|ResourceName  <br/> |Name of the resource.  <br/> |
|ResourcePlanCheckedOutById  <br/> |Resource ID of the user that checked out the resource plan.  <br/> |
|ResourcePlanCheckedOutByName  <br/> |Name of the user that checked out the resource plan.  <br/> |
|ResourcePlanCheckedOutDate  <br/> |Date the resource plan was checked out.  <br/> |
|ResourcePlanPublishStatus  <br/> |Internal property describing publish status.  <br/> |
|ProjectCurrentRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ProjectCurrentRevRank  <br/> |Internal property describing number of revisions.  <br/> |
|ResourcePlanCreationDate  <br/> |Date and time the resource plan was created.  <br/> |
|ResourcePlanModDate  <br/> |Date and time the resource plan was last updated.  <br/> |
|ResourcePlanCreatedRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ResourcePlanModRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ResourcePlanStartDate  <br/> |Date and time the resource plan began.  <br/> |
|ResourcePlanFinishDate  <br/> |Date and time the resource plan ended.  <br/> |
|ResourcePlanModRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ResourcePlanCreatedRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ResourcePlanAssignments  <br/> |Assignments associated with the resource plan.  <br/> |
   
A **ResourcePlan** object can have a collection of **ResourcePlanAssignments**. Each **ResourcePlanAssignments** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|AssignmentId  <br/> |Unique identifier for the assignment.  <br/> |
|ReservedData  <br/> |Used to temporarily store calculated values.  <br/> |
|AssignmentActualFinish  <br/> |The actual finish date of the assignment.  <br/> |
|AssignmentActualStart  <br/> |The actual start date of the assignment.  <br/> |
|AssignmentResourceType  <br/> |The type of resource that is associated with an assignment. See [Type enumeration](/previous-versions/office/project-class/gg223589(v=office.15)).  <br/> |
|AssignmentIsOverAllocated  <br/> |Indicates whether a resource is assigned to more work on a specific task than can be done within the resource's normal working capacity.  <br/> |
|AssignmentWorkContour  <br/> |The work contour of the assignment. Values are: 0=Flat, 1=Back Loaded, 2=Front Loaded, 3=Double Peak, 4=Early Peak, 5=Late Peak, 6=Bell, 7=Turtle, 8=Contoured.  <br/> |
|AssignmentStartVariance  <br/> |The variance of the assignment start date from the baseline start date.  <br/> |
|AssignmentFinishVariance  <br/> |The variance of the assignment finish date from the baseline finish date.  <br/> |
|AssignmentUpdateNeeded  <br/> |Indicates whether a TeamUpdate message should be sent to the resource assigned to a task because of changes to the start date, finish date, or resource reassignments.  <br/> |
|AssignmentHasLinkedFields  <br/> |Indicates that the assignment has linked fields.  <br/> |
|AssignmentIsConfirmed  <br/> |Indicates whether a resource assigned to a task has accepted or rejected the task assignment.  <br/> |
|AssignmentResponsePending  <br/> |Indicates whether an answer has been received from a message sent to a resource assigned to a task notifying the resource of the assignment.  <br/> |
|AssignmentHasNotes  <br/> |There are notes about the assignment.  <br/> |
|AssignmentTeamStatusPending  <br/> |Indicates whether a status message has been received in response to a TeamStatus message sent to a resource assigned to a task.  <br/> |
|ResourceId  <br/> |Unique identifier of the resource.  <br/> |
|ResourceName  <br/> |Name of the resource.  <br/> |
|AssignmentStartDate  <br/> |The date and time that an assigned resource is scheduled to begin working on a task.  <br/> |
|AssignmentFinishDate  <br/> |The date and time that an assigned resource is scheduled to stop working on a task.  <br/> |
|AssignmentDelay  <br/> |The amount of time a resource is to wait after the task start date before starting work on an assignment.  <br/> |
|AssignmentDelayFMT  <br/> |The format for expressing the duration of the delay. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|AssignmentLevelingDelay  <br/> |The amount of time that an assignment is to be delayed from the scheduled start date as a result of resource leveling.  <br/> |
|AssignmentCostRateTable  <br/> |Indicates which cost rate table to use for a resource on an assignment.  <br/> |
|AssignmentMaterialRateFMT  <br/> |Indicates the units in which the bid is expressed in the project.  <br/> |
|AssignmentUnits  <br/> |The number of units for which a resource is assigned to a task, expressed as a percentage.  <br/> |
|AssignmentWork  <br/> |The total amount of work scheduled to be performed by a resource on a task.  <br/> |
|AssignmentActualWork  <br/> |The amount of work that has already been done by a resource on a task.  <br/> |
|AssignmentRegularWork  <br/> |The total amount of non-overtime work scheduled to be performed by a resource assigned to a task.  <br/> |
|AssignmentRemainingWork  <br/> |The amount of time required by a resource assigned to a task to complete an assignment.  <br/> |
|AssignmentCost  <br/> |The total scheduled (or projected) cost for an assignment.  <br/> |
|AssignmentActualCost  <br/> |The cost incurred for work already performed by a resource on a task.  <br/> |
|AssignmentRemainingCost  <br/> |The costs associated with completing all remaining scheduled work by any resources on a specific task.  <br/> |
|AssignmentOvertimeWork  <br/> |The amount of overtime to be performed by a resource on a task; charged at the resource's overtime rate.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work already performed by a resource on an assigned task.  <br/> |
|AssignmentRemainingOvertimeWork  <br/> |The amount of overtime work that remains on an assignment.  <br/> |
|AssignmentActualOvertimeCost  <br/> |The cost incurred for overtime work already performed by a resource on a task.  <br/> |
|AssignmentRTFNotes  <br/> |Notes that are associated with the specified assignment, and that are stored in Rich Text Format.  <br/> |
|AssignmentRemainingOvertimeCost  <br/> |The remaining scheduled overtime expense for an assignment.  <br/> |
|AssignmentBookingType  <br/> |Specifies the booking type of the assignment (committed or proposed).  <br/> |
|AssignmentTDModeDate  <br/> |Internal property describing last modified date on timephased data.  <br/> |
|AssignmentTDModCounter  <br/> |Internal property describing number of revisions.  <br/> |
|AssignmentOvertimeCost  <br/> |The total overtime cost for a resource assignment.  <br/> |
|AssignmentStopDate  <br/> |The date the assignment was stopped.  <br/> |
|AssignmentResumeDate  <br/> |The date the assignment was resumed.  <br/> |
|CreatedDate  <br/> |The date that the assignment was created.  <br/> |
|ModDate  <br/> |The date that the assignment was last updated.  <br/> |
|CreatedRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
|ModRevCounter  <br/> |Internal property describing number of revisions.  <br/> |
   
A **ResourcePlanAssignments** object can have a collection of **Assignments**. Each **Assignments** object may contain the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier for the resource for the assignment.  <br/> |
|ProjectId  <br/> |Unique identifier for the project for the assignment.  <br/> |
|AssignmentId  <br/> |Unique identifier for the assignment.  <br/> |
|MDProjectUID  <br/> |Internal user only.  <br/> |
|CustomFieldName  <br/> |Name of the resource.  <br/> |
|CustomFieldValue  <br/> |Values for the custom field.  <br/> |
|CreationDate  <br/> |Date the custom field was created.  <br/> |
|ModDate  <br/> |Date the custom field was last updated.  <br/> |
|ResourceName  <br/> |Name of the resource for the assignment.  <br/> |
|Start  <br/> |Date and time the assignment work began.  <br/> |
|End  <br/> |Date and time the assignment work ended.  <br/> |
|Work  <br/> |The total amount of work scheduled to be performed by a resource on a task.  <br/> |
   
### Rules
<a name="rules"> </a>

Rules contains data about approval rules defined by status manager to approve certain task updates. Each **RulesData** object can have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|RuleUid  <br/> |Unique identifier for the rule.  <br/> |
|RuleManagerUid  <br/> |Unique identifier for the Status Manager Owner of the rule.  <br/> |
|RuleManagerName  <br/> |The name of the Status Manager Owner.  <br/> |
|RuleName  <br/> |Name of the rule.  <br/> |
|IsAutomatic  <br/> |True if status updates are automatically approved if they meet criteria defined in this rule, false otherwise.  <br/> |
|AutoPublish  <br/> |True if projects are published after the updates are automatically applied.  <br/> |
|RuleTypeNewTaskAndAssignments  <br/> |True if this rule is applying to updates of type new task or new assignments, false otherwise.  <br/> |
|RuleTypeDelegations  <br/> |True if this this rule is applying to updates of type Delegation(Reassign), false otherwise.  <br/> |
|RuleTypeUpdateTasks  <br/> |True if this rule is applying to updates made to the task assignments, false otherwise.  <br/> |
|RuleTypeDeletes  <br/> |True if this rule is applying to updates of type delete assignment, false otherwise.  <br/> |
|RuleConditionType  <br/> |If extra filtering is done in this rule this filed will have one of the values: None, Compare with fix string, or Compare with Database Column.  <br/> |
|Field1  <br/> |The left side of the filter  <br/> |
|Field2  <br/> |The right side of the filter  <br/> |
|Operator  <br/> |Operator (can be Equal, Not Equal, Less Than, Greater Than, Less Than or Equal, Greater Than, or Equal).  <br/> |
|ValueType  <br/> |Type of right side of the filter (can be string, int, double, date, bool).  <br/> |
|IntValue  <br/> |Value to compare with if ValueType is  *Int*  .  <br/> |
|DateValue  <br/> |Value to compare with if ValueType is  *Date*  .  <br/> |
|DecimalValue  <br/> |Value to compare with if ValueType is  *Decimal*  .  <br/> |
|StringValue  <br/> |Value to compare with if ValueType is  *String*  .  <br/> |
|IncludesAllProjects  <br/> |True if this rule applies to updates made in all projects, false otherwise.  <br/> |
|IncludesAllResources  <br/> |True if this rule applies to updates made by all resources, false otherwise.  <br/> |
|IncludesAllDelegatee  <br/> |True if this rule applies to updates of type delegation regardless of delegatee, false otherwise.  <br/> |
|RuleDescription  <br/> |Description for the rule.  <br/> |
|CreatedDate  <br/> |Date the rule was created.  <br/> |
|ModifiedDate  <br/> |Date the rule was last updated.  <br/> |
|RuleDetailsData  <br/> |Object with details about projects/resources this rule will applied for. This object will be populated with data only if IncludesAllProjects or IncludesAllResources or IncludesAllDelegatee is false.  <br/> |
   
Each **RulesDetailsData** object will have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|RuleUid  <br/> |Unique identifier for the rule.  <br/> |
|RuleListItemUid  <br/> |Unique identifier for project/resource/delagatee.  <br/> |
|RuleListItemType  <br/> |Type of the item, can be project, resource or delegate.  <br/> |
|RuleListItemName  <br/> |RuleListItemName Name of the item (can be name of the project/ resource/delegatee depending on the ruleListItemType).  <br/> |
|CreatedDate  <br/> |Date the rule was created.  <br/> |
|ModDate  <br/> |Date the rule was last updated.  <br/> |
   
### Security
<a name="Security"> </a>

Security provides security data about your user. It will only include data about your user if the PWA site is using Project Server permissions mode.
  
It includes:
  
- **SecurityData**: Account information about the user.
    
- **GroupData**: Project security groups in that the user was associated with.
    
- **CategoryData**: Security categories that the user was associated with.
    
- **PermissionData**: Global permission settings for your user.
    
A **ResourceData** object may have the following properties: 
  

|**Properties** <br/> |**Description** <br/> |
|:-----|:-----|
|EncodedClaim  <br/> |Claims account of the resource.  <br/> |
|ResourceUID  <br/> |Unique identifier of resource.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|GroupData  <br/> |Security group objects data.  <br/> |
|CategoryData  <br/> |Security category objects data.  <br/> |
   
Under **ResourceData**, a **GroupData** object may have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier of resource.  <br/> |
|GroupUID  <br/> |Unique identifier of the security group.  <br/> |
|GroupName  <br/> |Name of the security group.  <br/> |
|GroupDecription  <br/> |Description of the security group.  <br/> |
   
Under **ResourceData**, a **CategoryData** object may have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier of resource.  <br/> |
|CategoryUID  <br/> |Unique identifier of the category.  <br/> |
|CategoryName  <br/> |Name of the category.  <br/> |
|CategoryDescription  <br/> |Description of the category.  <br/> |
   
Under **ResourceData**, a **ParentPermissionData** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier of resource.  <br/> |
|PermissionUID  <br/> |Unique identifier of the parent permission.  <br/> |
|PermissionName  <br/> |Name of the parent permission.  <br/> |
|PermissionData  <br/> |Permission objects under the parent permission.  <br/> |
   
Under **ParentPermissionData**, a **PermissionData** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier of resource.  <br/> |
|PermissionUID  <br/> |Unique identifier of the permission.  <br/> |
|PermissionParentUID  <br/> |Internal unique identifier of the parent permission name.  <br/> |
|AllowOption  <br/> |If True, Allow was selected for permission for the user.  <br/> |
|DenyOption  <br/> |If True, Deny was selected for permission for the user.  <br/> |
|PermissionName  <br/> |Name of the permission.  <br/> |
   
### StatusReports
<a name="StatusReports"> </a>

StatusReports contains data about status reports that the user created or received as a status report manager. For each **StatusReports** object, you will see the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|StatusReportName  <br/> |Name of the status report.  <br/> |
|ManagerId  <br/> |Unique identifier of the status report manager.  <br/> |
|ManagerName  <br/> |Name of the status report manager.  <br/> |
|IsEnabled  <br/> |Indicates whether it's a active or archived status report.  <br/> |
|IsRequested  <br/> |Indicates whether it's a Requested or Misc status report.  <br/> |
|Sections  <br/> |Sections of the status report.  <br/> |
|CreatedDate  <br/> |Date the status report was created.  <br/> |
|ModifiedDate  <br/> |Date the status report was last updated.  <br/> |
   
Each **StatusReportRequests** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|RequesterId  <br/> |Unique identifier of the requestor.  <br/> |
|RequesterName  <br/> |Name of the requestor.  <br/> |
|DueDate  <br/> |Date when the status report is due  <br/> |
|IsNewRequest  <br/> |Indicates whether it's a active or archived status report.  <br/> |
|IsEnabled  <br/> |Indicates whether it's a Requested or Misc status report.  <br/> |
|CreatedDate  <br/> |Date and time when the request was created.  <br/> |
|ModifiedDate  <br/> |Date and time when the request was last updated.  <br/> |
   
Each **StatusReportResponses** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|ResponseId  <br/> |Unique identifier of the response.  <br/> |
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|ResponderId  <br/> |Unique identifier of the responder.  <br/> |
|ResponderName  <br/> |Name of the responder.  <br/> |
|ResponsePeriodStartDate  <br/> |Start date of the response period.  <br/> |
|ResponsePeriodFinishDate  <br/> |End date of the response period.  <br/> |
|ResponseSubmittedStatus  <br/> |The status of the submitted response.  <br/> |
|ResponseSubmittedDate  <br/> |Date the response was submitted.  <br/> |
|ResponseSectionsCount  <br/> |The number of sections included in the status response.  <br/> |
|IsMatchingResponse  <br/> |True if the response matches the status report period.  <br/> |
|IsNewResponse  <br/> |True if the response is new versus updated.  <br/> |
|ResponseSendId  <br/> |Identifier of the status report response.  <br/> |
|CreatedDate  <br/> |Date and time when the response was created.  <br/> |
|ModifiedDate  <br/> |Date and time when the response was last updated.  <br/> |
   
Each **StatusReportSections** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|SectionId  <br/> |Unique identifier of the section.  <br/> |
|ResponseId  <br/> |Unique identifier of the response.  <br/> |
|SectionText  <br/> |Actual text of a status report section.  <br/> |
|SectionIndex  <br/> |Identifier of the status report section.  <br/> |
|SectionName  <br/> |Name of the section.  <br/> |
|SectionDescription  <br/> |Description of the section.  <br/> |
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|CreatedDate  <br/> |Date the section was created.  <br/> |
|ModifiedDate  <br/> |Date the section was last updated.  <br/> |
   
Each **StatusReportFrequencies** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|StatusReportName  <br/> |Name of the status report.  <br/> |
|ResponseId  <br/> |Unique identifier of the response.  <br/> |
|FrequencyType  <br/> |Indicates the status report is due by week,month, or year.  <br/> |
|FrequencyPart1  <br/> |Due weeks for the status report.  <br/> |
|FrequencyPart2  <br/> |Due days or day of the month, or day of the week, or week of the month for the status report.  <br/> |
|FrequencyPart3  <br/> |Due month or day of the week for the status report.  <br/> |
|FrequencyPart4  <br/> |Due week of the month for the status report.  <br/> |
|FrequencyPart5  <br/> |Due day of the week for the status report.  <br/> |
|FrequencyPart6  <br/> |Due month of the status report.  <br/> |
|FrequencyYearlyDate  <br/> |Date of yearly frequency for the status report.  <br/> |
|CreatedDate  <br/> |Date the frequency was created.  <br/> |
|ModifiedDate  <br/> |Date the frequency was last updated.  <br/> |
   
Each **StatusReportDistribution** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|ResponderId  <br/> |Unique identifier of the responder.  <br/> |
|ResponderName  <br/> |Name of the responder.  <br/> |
|ResponseId  <br/> |Unique identifier of the response.  <br/> |
|CreatedDate  <br/> |Date the distribution was created.  <br/> |
|ModifiedDate  <br/> |Date the distribution was last updated.  <br/> |
   
Each **WorkDetails** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|StatusReportId  <br/> |Unique identifier of the status report.  <br/> |
|StatusReportName  <br/> |Name of the status report.  <br/> |
|StartDate  <br/> |Start date of the status report.  <br/> |
|CreatedDate  <br/> |Date and time when the request was created.  <br/> |
|ModifiedDate  <br/> |Date and time when the request was last updated.  <br/> |
|DueWeek  <br/> |Indicates the Due week number of the status report.  <br/> |
|DueDays  <br/> |Due date of the status report.  <br/> |
   
### SubscribedReminders
<a name="SubscribedReminders"> </a>

SubscribedReminders contains data about reminders subscribed to by the user. For each **SubscribedReminderData** object, you will see the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|Id  <br/> |The unique identifier of the reminder.  <br/> |
|ReminderName  <br/> |The name of the reminder.  <br/> |
|RecipientType  <br/> |Can be either: OnlyToManager, OnlyToTeamMember, or ToBothManagerAndTeamMember.  <br/> |
|FrequencyPeriod  <br/> |Can be: Daily, Weekly, or Monthly.  <br/> |
|FrequencyValue  <br/> |The value of the frequency to send the reminder, combined with the frequency period. For example, the value is "2" and the FrequencyPeriod is "Monthly", so the reminder will be sent every 2 months.  <br/> |
|NextRun  <br/> |The time the next reminder will be sent.  <br/> |
   
### TaskStatus_AssignmentsHistory
<a name="StatusAssignHis"> </a>

TaskStatus_AssignmentsHistory contains data about status updates where user is the submitter, assignment owner, status manager or delagatee. Each **Transactions** object, you may see the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|TransactionUid  <br/> |Unique identifier of the transaction.  <br/> |
|State  <br/> |State of the transaction.  <br/> |
|UpdateType  <br/> |Type of update: new assignment, status update, delete assignment, reassignment, or new task.  <br/> |
|ApprovalType  <br/> |The action taken by the status manager regarding the status update: Approve or Reject.  <br/> |
|ErrorStatus  <br/> |In case the status update couldn't be applied to the plan this will tell you the error encountered.  <br/> |
|DelegateeUid  <br/> |Unique identifier of the delegatee.  <br/> |
|DelegateeName  <br/> |Name of the delegatee.  <br/> |
|SubmitterUid  <br/> |Unique identifier of the submitter.  <br/> |
|SubmitterName  <br/> |Name of the submitter.  <br/> |
|ApproverUid  <br/> |Unique identifier of the approver.  <br/> |
|ApproverName  <br/> |Name of the approver.  <br/> |
|UpdateDate  <br/> |Date the status update last modified by the submitter or approver.  <br/> |
|SubmittedDate  <br/> |When this status update was submitted.  <br/> |
|CreatedDate  <br/> |Creation date for the status update.  <br/> |
|ModifiedDate  <br/> |Last modified date for the status update.  <br/> |
|AssignmentUid  <br/> |Unique identifier of the assignment.  <br/> |
|StatusAssignmentTaskUid  <br/> |Unique identifier of the status assignment task.  <br/> |
|ProjectUid  <br/> |Unique identifier of the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|TaskUid  <br/> |Unique identifier of the task.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|Changes  <br/> |The object containing the changes made by the submitter in the status update.  <br/> |
   
Each **Changes** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|TransactionUid  <br/> |Unique identifier of the transaction.  <br/> |
|EntityUid  <br/> |Task UID or Assignment UID depending if the change was made for the task or for the assignment.  <br/> |
|PropertyName  <br/> |Name of the property that was changed.  <br/> |
|PeriodStart  <br/> |The start of the period.  <br/> |
|PeriodEnd  <br/> |The end of the period.  <br/> |
|Value  <br/> |Value the property was changed to.  <br/> |
   
Each **TransactionsComments** object may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|CommentUid  <br/> |Unique identifier of the comment.  <br/> |
|TransactionUid  <br/> |Unique identifier of the transaction.  <br/> |
|CommentType  <br/> |Type of comment (Submitted or Approved).  <br/> |
|AuthorUid  <br/> |Unique identifier of the comment author.  <br/> |
|AuthorName  <br/> |Name of the comment author.  <br/> |
|Comment  <br/> |Comment details.  <br/> |
|DateEntered  <br/> |Date and time the comment was created.  <br/> |
|CommentCreatedDate  <br/> |Date and time the comment was created.  <br/> |
|CommentModifiedDate  <br/> |Date and time the comment was last updated.  <br/> |
   
### TaskStatus_AssignmentsSaved
<a name="StatusAssignSaved"> </a>

TaskStatus_AssignmentsSaved contains data about status reports that the user created or received as a status report manager. This file will contain a collection of **Tasks** objects, which may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|TaskUid  <br/> |Unique identifier of the task.  <br/> |
|TaskPublishedUid  <br/> |Name of the status report.  <br/> |
|ProjectUid  <br/> |Unique identifier of the project in which the task exists.  <br/> |
|ProjectName  <br/> |Name of the project in which the task exists.  <br/> |
|TaskParentUid  <br/> |Unique identifier of the parent task.  <br/> |
|TaskACWP  <br/> |The actual cost of work performed on the task to date.  <br/> |
|TaskBCWP  <br/> |The budgeted cost of work performed on the task to date.  <br/> |
|TaskBCWS  <br/> |The budgeted cost of work scheduled for the task.  <br/> |
|TaskDurationVariance  <br/> |The difference between the baseline duration of a task and the total duration.  <br/> |
|TaskFinishVariance  <br/> |The variance of the task finish date from the baseline finish date as minutes x 1000.  <br/> |
|TaskOutlineNumber  <br/> |The outline number of the task.  <br/> |
|TaskStartVariance  <br/> |The difference between the baseline start and the actual start.  <br/> |
|TaskIsOverallocated  <br/> |True if the task is overallocated.  <br/> |
|TaskOvertimeWork  <br/> |The amount of overtime work scheduled for the task  <br/> |
|TaskVAC  <br/> |The task variance at completion of the task.  <br/> |
|TaskRegularWork  <br/> |The amount of time scheduled for a task that is charged at the resource's standard rate.  <br/> |
|TaskTotalSlack  <br/> |The amount of total slack.  <br/> |
|TaskId  <br/> |Unique identifier for the task.  <br/> |
|TaskHasLinkedFields  <br/> |True if the task has linked fields.  <br/> |
|TaskIsMilestone  <br/> |True if the task is a milestone.  <br/> |
|TaskIsCritical  <br/> |True if the task is in the critical chain.  <br/> |
|TaskIsSummary  <br/> |True if the task is a summary task.  <br/> |
|TaskIsSubproject  <br/> |True if the task is an inserted project.  <br/> |
|TaskIsMarked  <br/> |Indicates whether a task is marked for further action or identification of some kind.  <br/> |
|TaskIgnoresResourceCalendar  <br/> |True if the task ignores the resource calendar.  <br/> |
|TaskIsRolledUp  <br/> |True if the task is rolled up  <br/> |
|TaskIsSubprojectScheduledFromFinish  <br/> |Gets a value that indicates whether a subproject for this task is set to schedule from finish.  <br/> |
|TaskBarIsHidden  <br/> |True if the GANTT bar of the task is hidden when displayed in Microsoft Office Project.  <br/> |
|TaskIsRecurring  <br/> |True if the task is recurring.  <br/> |
|TaskIsRecurringSummary  <br/> |True if the task is a recurring summary task.  <br/> |
|TaskIsExternal  <br/> |True if the task is external.  <br/> |
|TaskIsEffortDriven  <br/> |True if the task is effort driven.  <br/> |
|TaskIsCollapsed  <br/> |True if task is displayed collapsed in Project client.  <br/> |
|TaskHasNotes  <br/> |True if text notes are associated with the task.  <br/> |
|TaskIsSubprojectReadOnly  <br/> |Gets a value that indicates whether a subproject for this task is read-only.  <br/> |
|TaskLevelingCanSplit  <br/> |True if leveling can split the task.  <br/> |
|TaskCanSplit  <br/> |Indicates whether the resource leveling function can cause splits on remaining work on this task. If this field is set to Yes, then leveling can interrupt this task. If this field is set to No, leveling cannot split the task.  <br/> |
|TaskDurationIsEstimated  <br/> |Indicates whether the task's duration is flagged as an estimate.  <br/> |
|TaskEarlyFinish  <br/> |The early finish date of the task.  <br/> |
|TaskLateStart  <br/> |The late start date of the task.  <br/> |
|TaskStopDate  <br/> |The date that the task was stopped.  <br/> |
|TaskFreeSlack  <br/> |The amount of free slack.  <br/> |
|TaskResumeDate  <br/> |The date that the task was resumed.  <br/> |
|TaskCompletedDate  <br/> |The date argument for the task constraint type.  <br/> |
|TaskOutlineLevel  <br/> |The outline level of the task.  <br/> |
|TaskScheduledDuration  <br/> |The scheduled duration of the task.  <br/> |
|TaskScheduledDurationFormat  <br/> |Gets the total span of active working time for the task as entered or as calculated based on the start date, the finish date, calendars, and other scheduling factors.  <br/> |
|TaskActualDuration  <br/> |The actual duration of the task.  <br/> |
|TaskRemainingDuration  <br/> |The amount of time required to complete the unfinished portion of the task.  <br/> |
|TaskConstraintType  <br/> |The constraint on the start or finish date of the task. Values are: 0=As Soon As Possible, 1=As Late As Possible, 2=Must Start On, 3=Must Finish On, 4=Start No Earlier Than, 5=Start No Later Than, 6=Finish No Earlier Than and 7=Finish No Later Than.  <br/> |
|TaskLevelingDelay  <br/> |The delay caused by leveling the task.  <br/> |
|TaskLevelingDelayFormat  <br/> |The format for expressing the duration of the delay. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|TaskScheduledStart  <br/> |The scheduled start date of the task.  <br/> |
|TaskScheduledFinish  <br/> |The scheduled finish date of the task.  <br/> |
|TaskActualStart  <br/> |The actual start date of the task.  <br/> |
|TaskActualFinish  <br/> |The actual finish date of the task.  <br/> |
|TaskConstraintDate  <br/> |The date associated with the constraint type.  <br/> |
|TaskPriority  <br/> |The priority of the task from 0 to 1000.  <br/> |
|TaskPercentComplete  <br/> |The percentage of the task duration completed.  <br/> |
|TaskWorkPercentComplete  <br/> |The percentage of the task work completed.  <br/> |
|TaskType  <br/> |The type of task. Values are: 0=Fixed Units, 1=Fixed Duration, 2=Fixed Work.  <br/> |
|TaskFixedCostAccrual  <br/> |How the fixed cost is accrued against the task. Values are: 1=Start, 2=Prorated and 3=End.  <br/> |
|TaskPreleveledStart  <br/> |Contains the start date of a task as it was before resource leveling was done.  <br/> |
|TaskPreleveledFinish  <br/> |Contains the end date of a task as it was before resource leveling was done.  <br/> |
|TaskEarlyStart  <br/> |The early start date of the task.  <br/> |
|TaskLateFinish  <br/> |The late finish date of the task.  <br/> |
|TaskCalendarUid  <br/> |The unique identifier of the calendar associated with a task.  <br/> |
|TaskDeadline  <br/> | The final desired point in a task's time length that the task must be completed by.  <br/> |
|TaskWork  <br/> |The amount of scheduled work for the task.  <br/> |
|TaskActualWork  <br/> |The actual work for the task.  <br/> |
|TaskRemainingWork  <br/> |The remaining work scheduled to complete the task  <br/> |
|TaskCost  <br/> |The projected or scheduled cost of the task.  <br/> |
|TaskFixedCost  <br/> |The fixed cost of the task.  <br/> |
|TaskActualCost  <br/> |The actual cost of the task.  <br/> |
|TaskRemainingCost  <br/> |The remaining projected cost of completing the task.  <br/> |
|TaskActualOvertimeWork  <br/> |The actual overtime work for the task.  <br/> |
|TaskRemainingOvertimeWork  <br/> |The remaining overtime work scheduled to finish the task.  <br/> |
|TaskOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the task.  <br/> |
|TaskActualOvertimeCost  <br/> |The actual overtime cost of the task.  <br/> |
|TaskRemainingOvertimeCost  <br/> |The remaining overtime cost projected to finish the task.  <br/> |
|TaskWBS  <br/> |The work breakdown structure (WBS) code of the task.  <br/> |
|TaskName  <br/> |The name of the task.  <br/> |
|TaskHierarchy  <br/> |The hierarchy of the task.  <br/> |
|TaskRightMostLevel  <br/> |Used in leveling.  <br/> |
|TaskRTFNotes  <br/> |Notes that are associated with the specified task, and that are stored in Rich Text Format.  <br/> |
|TaskPhysicalPercentCompleted  <br/> |The percentage complete value entered by the Project Manager.  <br/> |
|TaskEAC  <br/> |The EAC (estimate at completion) field shows theexpected total cost of a task based on performance up to the status date. EAC is also called forecast at completion (FAC).  <br/> |
|TaskEarnedValueMethod  <br/> |The method for calculating earned value. Values are: 0=Percent Complete, 1=Physical Percent Complete.  <br/> |
|TaskTDModifyDate  <br/> |Last datetime when task's timephased data was modified.  <br/> |
|TaskOptIndex  <br/> |Gets the Item ID of the task in the task list.  <br/> |
|TaskIsNull  <br/> |Specifies whether the task has no values set.  <br/> |
|TaskIsDeletedInProject  <br/> |Indicates if the task was deleted from the project.  <br/> |
|TaskCostIsValid  <br/> |Gets or sets a Boolean value that indicates whether the current field is the associated cost for the task.  <br/> |
|TaskDeletedFlag  <br/> |Indicates if the task was deleted.  <br/> |
|TaskUpdatesConflict  <br/> |True if the Project Manager updated this task and the updates might conflict with updates made by a team member.  <br/> |
|TASK_IS_ROLLUP_ASSN  <br/> |Indicates whether the task has rollup data for the assignment.  <br/> |
|TASK_LOCKDOWN_BY_MANAGER  <br/> |True if this task will not accept updates from team members.  <br/> |
|TASK_EXT_TASK_UID  <br/> | Specifies cross project tasks links.  <br/> |
|TASK_EXT_PROJ_UID  <br/> |Specifies cross project links.  <br/> |
|TaskContact  <br/> |Contact information for the task.  <br/> |
|TaskCPI  <br/> |The CPI (cost performance index) fields show the ratio of budgeted (or baseline) costs of work performed to actual costs of work performed.  <br/> |
|TaskCV  <br/> |Task cost variance.  <br/> |
|TaskHyperLinkFriendlyName  <br/> |Shows the title or explanatory text for a hyperlink associated with a task.  <br/> |
|TaskHyperLinkAddress  <br/> |The URL or UNC path of a document.  <br/> |
|TaskHyperLinkSubAddress  <br/> |Contains the specific location in a document within a hyperlink associated with a task.  <br/> |
|TaskNotes  <br/> |Notes for the task.  <br/> |
|TaskSPI  <br/> |Often used to estimate the project completion date.  <br/> |
|TaskSV  <br/> |The cost difference between the current progress and the baseline plan of a task.  <br/> |
|TaskTCPI  <br/> |The TCPI (to complete performance index) field shows the ratio of the work remaining to be done to funds remaining to be spent, as of the status date.  <br/> |
|TaskWorkVariance  <br/> |The variance of task work from the baseline task work as minutes x 1000.  <br/> |
|TaskCostVariance  <br/> |Gets the difference in cost terms between the current progress and the baseline planned progress for a resource on the task.  <br/> |
|TaskFinishSlack  <br/> |Amount of finish slack.  <br/> |
|TaskBudgetWork  <br/> |The scheduled work for a task.  <br/> |
|TaskBudgetCost  <br/> |Gets the budget costs for budget cost resources.  <br/> |
|TaskWinprojUniqueId  <br/> |Indicates the unique identifier for the task used in Project client.  <br/> |
|TaskStartSlack  <br/> |Amount of start slack.  <br/> |
|TaskCommitmentType  <br/> |Specifies whether the task has an associated deliverable or a dependency on an associated deliverable. Values are: 0=The task has no deliverable or dependency on a deliverable, 1=The task has an associated deliverable, 2=The task has a dependency on an associated deliverable.  <br/> |
|TaskCommitmentUid  <br/> |Unique identifier for the commitment.  <br/> |
|TaskCommitmentStart  <br/> |Start date for the commitment.  <br/> |
|TaskCommitmentFinish  <br/> |End date for the commitment.  <br/> |
|TaskIsActive  <br/> |True if the task is active.  <br/> |
|TaskDispSumary  <br/> |The value of the property should be **false**. Reserved for future use.  <br/> |
|TaskIsManual  <br/> |True if the task is manual.  <br/> |
|TaskDuration  <br/> |The planned duration of the task  <br/> |
|TaskDurationFormat  <br/> |The format for expressing the duration of the task. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|TaskStartDate  <br/> |The scheduled start date of the task.  <br/> |
|TaskFinishDate  <br/> |The scheduled finish date of the task.  <br/> |
|TaskDurationString  <br/> |String used for task duration.  <br/> |
|TaskStartString  <br/> |String used for task finish.  <br/> |
|TaskFinishString  <br/> |String used for task start.  <br/> |
|TaskCreatedDate  <br/> |Date the task was created.  <br/> |
|TaskModifiedDate  <br/> |The date the task was last updated.  <br/> |
|Assignments  <br/> |The collection of assignments that make up the project.  <br/> |
   
Each **Tasks** object may have a collection of **Assignments** objects, which may have the following properties: 
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|AssignmentUID  <br/> |Unique identifier of the assignment.  <br/> |
|TaskUID  <br/> |Unique identifier of the task for the assignment.  <br/> |
|TaskName  <br/> |Name of the task for the assignment.  <br/> |
|ProjectUid  <br/> |Unique identifier of the project for the the task.  <br/> |
|ResourceUid  <br/> |Unique identifier of the resource assigned to the assignment.  <br/> |
|ResourceName  <br/> |Name of the resource assigned to the assignment.  <br/> |
|AssignmentActualFinish  <br/> |The actual finish date of the assignment.  <br/> |
|AssignmentActualStart  <br/> |The actual start date of the assignment.  <br/> |
|AssignmentActualCostOfWorkPerformed  <br/> |Gets the actual cost of work performed (ACWP) for the assignment to date.  <br/> |
|AssignmentEarnedValue  <br/> |Specifies the assignment's budgeted cost of work performed (BCWP).  <br/> |
|AssignmentBCWS  <br/> |The budgeted cost of work on the assignment.  <br/> |
|AssignmentResourceType  <br/> |The type of resource that is associated with an assignment. See [Type enumeration](/previous-versions/office/project-class/gg223589(v=office.15)).  <br/> |
|AssignmentIsOverallocated  <br/> |Whether the assignment is overallocated.  <br/> |
|AssignmentWorkContour  <br/> |The work contour of the assignment. Values are: 0=Flat, 1=Back Loaded, 2=Front Loaded, 3=Double Peak, 4=Early Peak, 5=Late Peak, 6=Bell, 7=Turtle, 8=Contoured.  <br/> |
|AssignmentStartVariance  <br/> |The variance of the assignment start date from the baseline start date.  <br/> |
|AssignmentFinishVariance  <br/> |The variance of the assignment finish date from the baseline finish date.  <br/> |
|AssignmentUpdateNeeded  <br/> |True if the resource assigned to a task needs to be updated as to the status of the task.  <br/> |
|AssignmentHasLinkedFields  <br/> |Whether the project is linked to another OLE object.  <br/> |
|AssignmentIsPendingResponse  <br/> |True if a response has not been received for a TeamAssign message.  <br/> |
|AssignmentHasNotes  <br/> |Has text notes associated with the assignment.  <br/> |
|AssignmentTeamStatusPending  <br/> |Indicates whether a status message has been received in response to a TeamStatus message sent to a resource assigned to a task.  <br/> |
|AssignmentsStartDate  <br/> |The scheduled start date of the assignment.  <br/> |
|AssignmentFinishDate  <br/> |The scheduled finish date of the assignment.  <br/> |
|AssignmentDelay  <br/> |The amount that the assignment is delayed  <br/> |
|AssignmentDelayFormat  <br/> |The format for expressing the duration of the delay. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|AssignmentLevelingDelay  <br/> |The delay caused by leveling.  <br/> |
|AssignmentCostRateTable  <br/> |The cost rate table used for the assignment.  <br/> |
|AssignmentMaterialRateFormat  <br/> |Indicates the units in which the bid is expressed in the project.  <br/> |
|AssignmentUnits  <br/> |The number of units for the assignment.  <br/> |
|AssignmentWork  <br/> |The amount of scheduled work for the assignment.  <br/> |
|AssignmentActualWork  <br/> |The actual amount of work incurred on the assignment.  <br/> |
|AssignmentRegularWork  <br/> |The amount of non-overtime work scheduled for the assignment.  <br/> |
|AssignmentRemainingWork  <br/> |The remaining work scheduled to complete the assignment.  <br/> |
|AssignmentCost  <br/> |The projected or scheduled cost of the assignment.  <br/> |
|AssignmentActualCost  <br/> |The actual cost incurred on the assignment.  <br/> |
|AssignmentRemainingCost  <br/> |The remaining projected cost of completing the assignment.  <br/> |
|AssignmentOvertimeWork  <br/> |The scheduled overtime work for the assignment.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work incurred on the assignment.  <br/> |
|AssignmentRemainingOvertimeWork  <br/> |The remaining overtime work scheduled to complete the assignment.  <br/> |
|AssignmentOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the assignment.  <br/> |
|AssignmentRemainingOvertimeCost  <br/> |The remaining projected overtime cost of completing the assignment.  <br/> |
|AssignmentRTFNotes  <br/> |Represents notes that are associated with the specified assignment, and that are stored in Rich Text Format.  <br/> |
|AssignmentBookingType  <br/> |Specifies the booking type of the assignment. 1=Commited, 2=Proposed.  <br/> |
|AssignmentParentId  <br/> |Unique identifier of the primary assignment.  <br/> |
|AssignmentRemovedByResource  <br/> |True if team member removed this resource.  <br/> |
|StatusManagerUid  <br/> |Unique identifier for the status manager.  <br/> |
|StatusManagerName  <br/> |Name of the status manager.  <br/> |
|DefaultAssignmentOwnerUid  <br/> |Unique identifier for the default assignment owner.  <br/> |
|DefaultAssignmentOwnerName  <br/> |Name of the default assignment owner.  <br/> |
|AssignmentLastWork  <br/> |The scheduled work from the last update from Project.  <br/> |
|AssignmentsComments  <br/> |The user's comments about the assignment.  <br/> |
|AssignmentNoteStatus  <br/> |Indicates whether a note has been entered for the assignment.  <br/> |
|TaskIsSummary  <br/> |Specifies whether the task is a summary task.  <br/> |
|AssignmentIsConfirmed  <br/> |Whether the Resource has accepted all of his or her assignments.  <br/> |
|AssignmentUpdatedByManager  <br/> |True if the assignment was updated by Project Manager.  <br/> |
|AssignmentLockeByManager  <br/> |True if this assignment doesn't accept update from team member anymore.  <br/> |
|AssignmentCreatedByResourceId  <br/> |Resource ID of the assignment creator.  <br/> |
|CreatorName  <br/> |Name of the assignment creator.  <br/> |
|AssignmentCurrentTrackingMode  <br/> | Indicates the current method used to track projects.  <br/>  0 - None (default)  <br/>  1 - Timephased actuals  <br/>  2 - Percent complete tracking  <br/>  3 - Total actual work and remaining work tracking  <br/> |
|AssignmentUpdatedTrackingMode  <br/> | Indicates the updated method used to track projects:  <br/>  0 - None (default)  <br/>  1 - Timephased actuals  <br/>  2 - Percent complete tracking  <br/>  3 - Total actual work and remaining work tracking  <br/> |
|AssignmentNeedUpdatesSubmitted  <br/> |True if there are saved update from team members for assignment.  <br/> |
|AssignmentDeletedInProject  <br/> |True if assignment was deleted from project.  <br/> |
|AssignmentUpdatesByResource  <br/> |True if the assignment was updated by team member.  <br/> |
|AssignmentRequestsUpdates  <br/> |Indicates whether a team resource has submitted actuals.  <br/> |
|AssignmentUpdatesAccepted  <br/> |True is status updates made for assignment where accepted.  <br/> |
|AssignmentActualsPending  <br/> |True if accepted updates are pending to be applied to the plan.  <br/> ||
|AssignmentIsDelegated  <br/> |True if assignment was created by a reassign operation.  <br/> |
|AssignmentIsNew  <br/> |True if assignment is newly created for team member.  <br/> |
|AssignmentUpdateStatus  <br/> | Indicates the status of an assignment.  <br/>  0 - Not edited by resource.  <br/>  1 - Edited by resource but not updated to the project manager yet.  <br/> |
|AssignmentPercentWorkCompleted  <br/> |The amount of work completed on the assignment.  <br/> |
|AssignmentActualOvertimeCost  <br/> |The costs incurred for overtime work that has already been performed on an assignment.  <br/> |
|AssignmentAssignedToExisting  <br/> |Indicates whether a new assignment has been created by a resource using the assign self to task feature.  <br/> |
|AssignmentTDModifyDate  <br/> |Last modified date for assignment timephased data  <br/> |
|AssignmentResumeDate  <br/> |The date that the assignment resumed.  <br/> |
|AssignmentStopDate  <br/> |The date that the assignment was stopped.  <br/> |
|AssignmentIsPublished  <br/> |True if assignment was published.  <br/> |
|AssignmentDemandRequire  <br/> |Indicates how to assign resources when using the resource substitution wizard.  <br/> |
|AssignmentIsCostValid  <br/> |Indicates whether or not the cost associated with the assignment has been approved.  <br/> |
|AssignmentCostIsEdited  <br/> |Indicates if the cost associated with this assignment was edited.  <br/> |
|AssignmentOtherType  <br/> | Indicates the type of assignment:  <br/>  0 - Regular  <br/>  1 - TaskOnlyWork  <br/>  2 - FixedCosts  <br/>  3 - FixedCostsAndTaskOnly  <br/>  4 - RegularUnassigned  <br/> |
|AssignmentUpdatesConflict  <br/> |True if there are conflicting updates for assignment  <br/> |
|DeletedFlag  <br/> |Indicates if the assignment was deleted.  <br/> |
|AssignmentVAC  <br/> |The difference between baseline cost and total cost.  <br/> |
|AssignmentSV  <br/> |Earned value schedule variance, through the project status date.  <br/> |
|AssignmentWorkVariance  <br/> |The variance of assignment work from the baseline work as minutes x 1000.  <br/> |
|AssignmentCostVariance  <br/> |The difference between the cost and baseline cost for a resource.  <br/> |
|AssignmentBudgetWork  <br/> |The budgeted work amount for work or material resources on this assignment.  <br/> |
|AssignmentBudgetCost  <br/> |The budgeted amount for cost resources on this assignment.  <br/> |
|AssignmentTaskManagementFlags  <br/> |Internal use only.  <br/> |
|AssignmentIgnoreResourceCalendar  <br/> |Indicates whether the resource calendar intersects with the task calendar.  <br/> |
|AssignmentWinProjUniqueId  <br/> |Indicates a unique identifier for the assignment used in Project client.  <br/> |
|AssignmentRemovedFromTS  <br/> |Indicates if the assignment was removed from the timesheet.  <br/> |
|AssignmentCreatedDate  <br/> |The date that the assignment was created.  <br/> |
|AssignmentModifiedDate  <br/> |The date that the assignment was last updated.  <br/> |
|AssignmentSendUpdatesDate  <br/> |The date and time that an assignment update was sent by the resource to a manager.  <br/> |
|AssignmentSummaryProgress  <br/> |Shows progress on a summary task based on progress on its subtasks and where these subtasks have been scheduled.  <br/> |
|TeamLeadUid  <br/> |Unique identifier for the team lead.  <br/> |
| TeamLeadName  <br/> |Name of the team lead.  <br/> |
|ReservedData1  <br/> |Used to temporarily store calculated values.  <br/> |
|ReservedData2  <br/> |Used to temporarily store calculated values.  <br/> |
|ReservedData3  <br/> |Used to temporarily store calculated values.  <br/> |
|AssignmentHyperlinkFriendlyName  <br/> |The title or explanatory text for a hyperlink associated with an assignment.  <br/> |
|AssignmentHyperlinkAddress  <br/> |The URL or UNC path of a document.  <br/> |
|AssignmentHyperlinkSubAddress  <br/> |The specific location in a document within a hyperlink associated with a assignment.  <br/> |
|AssignmentNotes  <br/> |The notes that are entered in the assignment details dialog box.  <br/> |
|AssignmentVAC  <br/> |The difference between baseline cost and total cost.  <br/> |
   
Each **Assignments** object may have a collection of **Timephased** objects, which may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|AssignmentUID  <br/> |Unique identifier for the assignement.  <br/> |
|Date  <br/> |Date the work started.  <br/> |
|Work  <br/> |Units of work scheduled for the assignment.  <br/> |
|OvertimeWork  <br/> |Units of overtime work scheduled for the assignment.  <br/> |
|ActualWork  <br/> |Actual units of work completed for the assignment.  <br/> |
|ActualOvertimeWork  <br/> |Actual units of overtime work completed for the assignment.  <br/> |
   
Each **Assignments** object may have a collection of **CustomFields** objects, which may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldUid  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|AssignmentUid  <br/> |Unique identifier for the assignment.  <br/> |
|Type  <br/> |Type of the custom field (can be number, text, cost, duration, date, fals, finish date, start date, etc.).  <br/> |
|CustomFieldValue  <br/> |Value properties for the custom field.  <br/> |
|DurationFormat  <br/> |Specifies the display format for the value if type is "duration".  <br/> |
|LookupTableUid  <br/> |Unique identifier for the lookup table.  <br/> |
|IndicatorValue  <br/> |Specifies the value of the custom field if the type of custom field is "indicator".  <br/> |
   
### TaskStatus_AssignmentsSubmitted
<a name="StatusAssignsub"> </a>

TaskStatus_AssignmentsSubmitted contains data about status reports that the user. This file will contain a collection of **Tasks** objects, which may have the following properties: 
  
|****Properties****|****Description****|
|:-----|:-----|
|TaskUid  <br/> |Unique identifier of the task.  <br/> |
|TaskPublishedUid  <br/> |Name of the status report.  <br/> |
|ProjectUid  <br/> |Unique identifier of the project in which the task exists.  <br/> |
|ProjectName  <br/> |Name of the project in which the task exists.  <br/> |
|TaskParentUid  <br/> |Unique identifier of the parent task.  <br/> |
|TaskACWP  <br/> |The actual cost of work performed on the task to date.  <br/> |
|TaskBCWP  <br/> |The budgeted cost of work performed on the task to date.  <br/> |
|TaskBCWS  <br/> |The budgeted cost of work scheduled for the task.  <br/> |
|TaskDurationVariance  <br/> |Difference between the baseline duration and the total duration (current estimate) of a task.  <br/> |
|TaskFinishVariance  <br/> |The variance of the task finish date from the baseline finish date as minutes x 1000.  <br/> |
|TaskOutlineNumber  <br/> |The outline number of the task.  <br/> |
|TaskStartVariance  <br/> |Task start variance is the difference between a baseline start date and the currently scheduled start date.  <br/> |
|TaskIsOverallocated  <br/> |True if the task is overallocated.  <br/> |
|TaskOvertimeWork  <br/> |The amount of overtime work scheduled for the task  <br/> |
|TaskVAC  <br/> |Variance at completion.  <br/> |
|TaskRegularWork  <br/> |Total amount of non-overtime work scheduled for a task.  <br/> |
|TaskTotalSlack  <br/> |The amount of total slack.  <br/> |
|TaskId  <br/> |Unique identifier for the task.  <br/> |
|TaskHasLinkedFields  <br/> |True if the task has linked fields.  <br/> |
|TaskIsMilestone  <br/> |True if the task is a milestone.  <br/> |
|TaskIsCritical  <br/> |True if the task is in the critical chain.  <br/> |
|TaskIsSummary  <br/> |True if the task is a summary task.  <br/> |
|TaskIsSubproject  <br/> |True if the task is an inserted project.  <br/> |
|TaskIsMarked  <br/> |Indicates whether a task is marked for further action or identification of some kind.  <br/> |
|TaskIgnoresResourceCalendar  <br/> |True if the task ignores the resource calendar.  <br/> |
|TaskIsRolledUp  <br/> |True if the task is rolled up  <br/> |
|TaskIsSubprojectScheduledFromFinish  <br/> |Gets a value that indicates whether a subproject for this task is set to schedule from finish.  <br/> |
|TaskBarIsHidden  <br/> |True if the GANTT bar of the task is hidden when displayed in Microsoft Office Project.  <br/> |
|TaskIsRecurring  <br/> |True if the task is recurring.  <br/> |
|TaskIsRecurringSummary  <br/> |True if the task is a recurring summary task.  <br/> |
|TaskIsExternal  <br/> |True if the task is external.  <br/> |
|TaskIsEffortDriven  <br/> |True if the task is effort driven.  <br/> |
|TaskIsCollapsed  <br/> |True if task is displayed collapsed in Project client.  <br/> |
|TaskHasNotes  <br/> |True if text notes are associated with the task.  <br/> |
|TaskIsSubprojectReadOnly  <br/> |Gets a value that indicates whether a subproject for this task is read-only.  <br/> |
|TaskLevelingCanSplit  <br/> |True if leveling can split the task.  <br/> |
|TaskCanSplit  <br/> |Indicates whether the resource leveling function can cause splits on remaining work on this task. If this field is set to Yes, then leveling can interrupt this task. If this field is set to No, leveling cannot split the task .  <br/> |
|TaskDurationIsEstimated  <br/> |Indicates whether the task's duration is flagged as an estimate.  <br/> |
|TaskEarlyFinish  <br/> |The early finish date of the task.  <br/> |
|TaskLateStart  <br/> |The late start date of the task.  <br/> |
|TaskStopDate  <br/> |The date that the task was stopped.  <br/> |
|TaskResumeDate  <br/> |The date that the task was resumed.  <br/> |
|TaskCompletedDate  <br/> |The date argument for the task constraint type.  <br/> |
|TaskFreeSlack  <br/> |The amount of free slack.  <br/> |
|TaskOutlineLevel  <br/> |The outline level of the task.  <br/> |
|TaskScheduledDuration  <br/> |The scheduled duration of the task.  <br/> |
|TaskScheduledDurationFormat  <br/> |Gets the total span of active working time for the task as entered or as calculated based on the start date, the finish date, calendars, and other scheduling factors.  <br/> |
|TaskActualDuration  <br/> |The actual duration of the task.  <br/> |
|TaskRemainingDuration  <br/> |The amount of time required to complete the unfinished portion of the task.  <br/> |
|TaskConstraintType  <br/> |The constraint on the start or finish date of the task. Values are: 0=As Soon As Possible, 1=As Late As Possible, 2=Must Start On, 3=Must Finish On, 4=Start No Earlier Than, 5=Start No Later Than, 6=Finish No Earlier Than and 7=Finish No Later Than.  <br/> |
|TaskLevelingDelay  <br/> |The delay caused by leveling the task.  <br/> |
|TaskLevelingDelayFormat  <br/> |The format for expressing the duration of the delay. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|TaskScheduledStart  <br/> |The scheduled start date of the task.  <br/> |
|TaskScheduledFinish  <br/> |The scheduled finish date of the task.  <br/> |
|TaskActualStart  <br/> |The actual start date of the task.  <br/> |
|TaskActualFinish  <br/> |The actual finish date of the task.  <br/> |
|TaskConstraintDate  <br/> |The date associated with the constraint type.  <br/> |
|TaskPriority  <br/> |The priority of the task from 0 to 1000.  <br/> |
|TaskPercentComplete  <br/> |The percentage of the task duration completed.  <br/> |
|TaskWorkPercentComplete  <br/> |The percentage of the task work completed.  <br/> |
|TaskType  <br/> |The type of task. Values are: 0=Fixed Units, 1=Fixed Duration, 2=Fixed Work.  <br/> |
|TaskFixedCostAccrual  <br/> |How the fixed cost is accrued against the task. Values are: 1=Start, 2=Prorated and 3=End.  <br/> |
|TaskPreleveledStart  <br/> |Contains the start date of a task as it was before resource leveling was done.  <br/> |
|TaskPreleveledFinish  <br/> |Contains the end date of a task as it was before resource leveling was done.  <br/> |
|TaskEarlyStart  <br/> |The early start date of the task.  <br/> |
|TaskLateFinish  <br/> |The late finish date of the task.  <br/> |
|TaskCalendarUid  <br/> |The unique identifier of the calendar associated with a task.  <br/> |
|TaskDeadline  <br/> | The final desired point in a task's time length that the task must be completed by.  <br/> |
|TaskWork  <br/> |The amount of scheduled work for the task.  <br/> |
|TaskActualWork  <br/> |The actual work for the task.  <br/> |
|TaskRemainingWork  <br/> |The remaining work scheduled to complete the task  <br/> |
|TaskCost  <br/> |The projected or scheduled cost of the task.  <br/> |
|TaskFixedCost  <br/> |The fixed cost of the task.  <br/> |
|TaskActualCost  <br/> |The actual cost of the task.  <br/> |
|TaskRemainingCost  <br/> |The remaining projected cost of completing the task.  <br/> |
|TaskActualOvertimeWork  <br/> |The actual overtime work for the task.  <br/> |
|TaskRemainingOvertimeWork  <br/> |The remaining overtime work scheduled to finish the task.  <br/> |
|TaskOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the task.  <br/> |
|TaskActualOvertimeCost  <br/> |The actual overtime cost of the task.  <br/> |
|TaskRemainifOvertimeCost  <br/> |The remaining overtime cost projected to finish the task.  <br/> |
|TaskWBS  <br/> |The work breakdown structure (WBS) code of the task.  <br/> |
|TaskName  <br/> |The name of the task.  <br/> |
|TaskHierarchy  <br/> |The hierarchy of the task.  <br/> |
|TaskRightMostLevel  <br/> |Used in leveling.  <br/> |
|TaskRTFNotes  <br/> |Notes that are associated with the specified task, and that are stored in Rich Text Format.  <br/> |
|TaskPhysicalPercentCompleted  <br/> |The percentage complete value entered by the Project Manager.  <br/> |
|TaskEAC  <br/> |Shows the expected total cost of a task based on performance up to the status date. EAC is also called forecast at completion (FAC).  <br/> |
|TaskEarnedValueMethod  <br/> |The method for calculating earned value. Values are: 0=Percent Complete, 1=Physical Percent Complete.  <br/> |
|TaskTDModifyDate  <br/> |Last datetime when task's timephased data was modified.  <br/> |
|TaskTDModifyCounter  <br/> |Counter for modifying timephased data.  <br/> |
|TaskStartOffset  <br/> |Offset for the task start.  <br/> |
|TaskReservedData  <br/> |Used to temporarily store calculated values.  <br/> |
|TaskOptIndex  <br/> |Gets the Item ID of the task in the task list.  <br/> |
|TaskSummaryProgressDate  <br/> |Internal user only.  <br/> |
|TaskIsNull  <br/> |Specifies whether the task has no values set.  <br/> |
|TaskIsDeletedInProject  <br/> |Indicates if the task was deleted from the project.  <br/> |
|TaskCostIsValid  <br/> |Gets or sets a Boolean value that indicates whether the current field is the associated cost for the task.  <br/> |
|TaskDeletedFlag  <br/> |Indicates if the task was deleted.  <br/> |
|TaskUpdatesConflict  <br/> |True if the ProjectManager updated this task and the updates might conflict with updates made by a team member.  <br/> |
|TASK_IS_ROLLUP_ASSN  <br/> |Indicates whether the task has rollup data for the assignment.  <br/> |
|TASK_LOCKDOWN_BY_MANAGER  <br/> |True if this task will not accept updates from team members.  <br/> |
|TASK_EXT_TASK_UID  <br/> | Specifies cross project tasks links.  <br/> |
|TASK_EXT_PROJ_UID  <br/> |Specifies cross project links.  <br/> |
|TaskContact  <br/> |Contact for the task.  <br/> |
|TaskCPI  <br/> |The CPI (cost performance index) fields show the ratio of budgeted (or baseline) costs of work performed to actual costs of work performed.  <br/> |
|TaskCV  <br/> |Task cost variance.  <br/> |
|TaskHyperLinkFriendlyName  <br/> |Shows the title or explanatory text for a hyperlink associated with a task.  <br/> |
|TaskHyperLinkAddress  <br/> |The URL or UNC path of a document.  <br/> |
|TaskHyperLinkSubAddress  <br/> |Contains the specific location in a document within a hyperlink associated with a task.  <br/> |
|TaskNotes  <br/> |Notes for the task.  <br/> |
|TaskSPI  <br/> |SPI is often used to estimate the project completion date.  <br/> |
|TaskSV  <br/> |The cost difference between the current progress and the baseline plan of a task.  <br/> |
|TaskTCPI  <br/> |The TCPI (to complete performance index) field shows the ratio of the work remaining to be done to funds remaining to be spent, as of the status date.  <br/> |
|TaskWorkVariance  <br/> |The variance of task work from the baseline task work as minutes x 1000.  <br/> |
|TaskCostVariance  <br/> |Gets the difference in cost terms between the current progress and the baseline planned progress for a resource on the task.  <br/> |
|TaskFinishSlack  <br/> |Amount of finish slack.  <br/> |
|TaskBudgetWork  <br/> |The scheduled work.  <br/> |
|TaskBudgetCost  <br/> |Gets the budget costs for budget cost resources.  <br/> |
|TaskWinprojUniqueId  <br/> |Indicates the unique identifier for the task used in Project client.  <br/> |
|TaskStartSlack  <br/> |Amount of start slack.  <br/> |
|TaskCommitmentType  <br/> |Specifies whether the task has an associated deliverable or a dependency on an associated deliverable. Values are: 0=The task has no deliverable or dependency on a deliverable, 1=The task has an associated deliverable, 2=The task has a dependency on an associated deliverable.  <br/> |
|TaskCommitmentUid  <br/> |Unique identifier for the commitment.  <br/> |
|TaskCommitmentStart  <br/> |Start date for the commitment.  <br/> |
|TaskCommitmentFinish  <br/> |End date for the commitment.  <br/> |
|TaskIsActive  <br/> |True if the task is active.  <br/> |
|TaskDispSumary  <br/> |The value of the property should be **false**. Reserved for future use.  <br/> |
|TaskIsManual  <br/> |True if the task is manual.  <br/> |
|TaskDuration  <br/> |The planned duration of the task  <br/> |
|TaskDurationFormat  <br/> |The format for expressing the duration of the task. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|TaskStartDate  <br/> |The scheduled start date of the task.  <br/> |
|TaskFinishDate  <br/> |The scheduled finish date of the task.  <br/> |
|TaskDurationString  <br/> |String used for task duration.  <br/> |
|TaskStartString  <br/> |String used for task finish.  <br/> |
|TaskFinishString  <br/> |String used for task start.  <br/> |
|TaskCreatedDate  <br/> |The date the task was created.  <br/> |
|TaskModifiedDate  <br/> |The date the task was last updated.  <br/> |
|Assignments  <br/> |The collection of assignments that make up the project.  <br/> |
   
Each **Tasks** object may have a collection of **Assignments** objects, which may have the following properties: 
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|AssignmentUID  <br/> |Unique identifier of the assignment.  <br/> |
|TaskUID  <br/> |Unique identifier of the task for the assignment.  <br/> |
|TaskName  <br/> |Name of the task for the assignment.  <br/> |
|ProjectUid  <br/> |Unique identifier of the project for the task.  <br/> |
|ResourceUid  <br/> |Unique identifier of the resource assigned to the assignment.  <br/> |
|ResourceName  <br/> |Name of the resource assigned to the assignment.  <br/> |
|ReservedData  <br/> |Used to temporarily store calculated values.  <br/> |
|ProjectSummaryAssignmentID  <br/> |Unique identifier of the project summary assignment.  <br/> |
|AssignmentActualFinish  <br/> |The actual finish date of the assignment.  <br/> |
|AssignmentActualStart  <br/> |The actual start date of the assignment.  <br/> |
|AssignmentActualCostOfWorkPerformed  <br/> |Gets the actual cost of work performed (ACWP) for the assignment to date.  <br/> |
|AssignmentEarnedValue  <br/> |Specifies the assignment's budgeted cost of work performed (BCWP).  <br/> |
|AssignmentBCWS  <br/> |The budgeted cost of work on the assignment.  <br/> |
|AssignmentResourceType  <br/> |The type of resource that is associated with an assignment. See [Type enumeration](/previous-versions/office/project-class/gg223589(v=office.15)).  <br/> |
|AssignmentIsOverallocated  <br/> |Whether the assignment is overallocated.  <br/> |
|AssignmentWorkContour  <br/> |The work contour of the assignment. Values are: 0=Flat, 1=Back Loaded, 2=Front Loaded, 3=Double Peak, 4=Early Peak, 5=Late Peak, 6=Bell, 7=Turtle, 8=Contoured.  <br/> |
|AssignmentStartVariance  <br/> |The variance of the assignment start date from the baseline start date.  <br/> |
|AssignmentFinishVariance  <br/> |The variance of the assignment finish date from the baseline finish date.  <br/> |
|AssignmentUpdateNeeded  <br/> |True if the resource assigned to a task needs to be updated as to the status of the task.  <br/> |
|AssignmentHasLinkedFields  <br/> |Whether the project is linked to another OLE object.  <br/> |
|AssignmentIsConfirmed  <br/> |Indicates whether this resource has accepted or rejected the task assignment.  <br/> |
|AssignmentIsPendingResponse  <br/> |True if a response has not been received for a TeamAssign message.  <br/> |
|AssignmentHasNotes  <br/> |Has text notes associated with the assignment.  <br/> |
|AssignmentTeamStatusPending  <br/> |Indicates whether a status message has been received in response to a TeamStatus message sent to a resource assigned to a task.  <br/> |
|AssignmentsStartDate  <br/> |The scheduled start date of the assignment.  <br/> |
|AssignmentFinishDate  <br/> |The scheduled finish date of the assignment.  <br/> |
|AssignmentDelay  <br/> |The amount that the assignment is delayed  <br/> |
|AssignmentDelayFormat  <br/> |The format for expressing the duration of the delay. Values are: 3=m, 4=em, 5=h, 6=eh, 7=d, 8=ed, 9=w, 10=ew, 11=mo, 12=emo, 19=%, 20=e%, 21=null, 35=m, 36=em, 37=h, 38=eh, 39=d, 40=ed, 41=w, 42=ew, 43=mo, 44=emo, 51=%, 52=e% and 53=null.  <br/> |
|AssignmentLevelingDelay  <br/> |The delay caused by leveling.  <br/> |
|AssignmentCostRateTable  <br/> |The cost rate table used for the assignment.  <br/> |
|AssignmentMaterialRateFormat  <br/> |Indicates the units in which the bid was expressed in the project.  <br/> |
|AssignmentUnits  <br/> |The number of units for the assignment.  <br/> |
|AssignmentWork  <br/> |The amount of scheduled work for the assignment.  <br/> |
|AssignmentActualWork  <br/> |The actual amount of work incurred on the assignment.  <br/> |
|AssignmentRegularWork  <br/> |The amount of non-overtime work scheduled for the assignment.  <br/> |
|AssignmentRemainingWork  <br/> |The remaining work scheduled to complete the assignment.  <br/> |
|AssignmentCost  <br/> |The projected or scheduled cost of the assignment.  <br/> |
|AssignmentActualCost  <br/> |The actual cost incurred on the assignment.  <br/> |
|AssignmentRemainingCost  <br/> |The remaining projected cost of completing the assignment.  <br/> |
|AssignmentOvertimeWork  <br/> |The scheduled overtime work for the assignment.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work incurred on the assignment.  <br/> |
|AssignmentRemainingOvertimeWork  <br/> |The remaining overtime work scheduled to complete the assignment.  <br/> |
|AssignmentOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the assignment.  <br/> |
|AssignmentRemainingOvertimeCost  <br/> |The remaining projected overtime cost of completing the assignment.  <br/> |
|AssignmentRTFNotes  <br/> |Represents notes that are associated with the specified assignment, and that are stored in Rich Text Format.  <br/> |
|AssignmentBookingType  <br/> |Specifies the booking type of the assignment. 1=Commited, 2=Proposed.  <br/> |
|AssignmentParentId  <br/> |Unique identifier of the primary assignment.  <br/> |
|AssignmentRemovedByResource  <br/> |True if team member removed this resource.  <br/> |
|StatusManagerUid  <br/> |Unique identifier for the status manager.  <br/> |
|StatusManagerName  <br/> |Name of the status manager.  <br/> |
|DefaultAssignmentOwnerUid  <br/> |Unique identifier for the default assignment owner.  <br/> |
|DefaultAssignmentOwnerName  <br/> |Name of the default assignment owner.  <br/> |
|AssignmentLastWork  <br/> |The scheduled work from the last update from Project.  <br/> |
|AssignmentsComments  <br/> |The user's comments about the assignment.  <br/> |
|HistoryNotes  <br/> ||
|AssignmentNoteStatus  <br/> |Indicates whether a note has been entered for the assignment.  <br/> |
|TaskIsSummary  <br/> |Specifies whether the task is a summary task.  <br/> |
|AssignmentIsConfirmed  <br/> |Whether the Resource has accepted all of his or her assignments.  <br/> |
|AssignmentUpdatedByManager  <br/> |True if the assignment was updated by Project Manager.  <br/> |
|AssignmentLockeByManager  <br/> |True if this assignment doesn't accept update from team member anymore.  <br/> |
|AssignmentCreatedByResourceId  <br/> |Resource ID of the assignment creator.  <br/> |
|CreatorName  <br/> |Name of the assignment creator.  <br/> |
|AssignmentCurrentTrackingMode  <br/> | Indicates the current method used to track projects:  <br/>  0 - None (default)  <br/>  1 - Timephased actuals  <br/>  2 - Percent complete tracking  <br/>  3 - Total actual work and remaining work tracking  <br/> |
|AssignmentUpdatedTrackingMode  <br/> | Indicates the updated method used to track projects:  <br/>  0 - None (default)  <br/>  1 - Timephased actuals  <br/>  2 - Percent complete tracking  <br/>  3 - Total actual work and remaining work tracking  <br/> |
|AssignmentNeedUpdatesSubmitted  <br/> |True if there are saved update from team members for this assignment.  <br/> |
|AssignmentDeletedInProject  <br/> |True if assignment was deleted from project.  <br/> |
|AssignmentUpdatesByResource  <br/> |True if the assignment was updated by team member.  <br/> |
|AssignmentRequestsUpdates  <br/> |Indicates whether a team resource has submitted actuals.  <br/> |
|AssignmentUpdatesAccepted  <br/> |True is status updates made for assignment where accepted.  <br/> |
|AssignmentActualsPending  <br/> |True if accepted updates are pending to be applied to the plan.  <br/> |
|AssignmentDeletePending  <br/> |True if delete for assignment is pending to be applied.  <br/> |
|AssignmentIsDelegated  <br/> |True if assignment was created by a reassign operation.  <br/> |
|AssignmentIsNew  <br/> |True if assignment is newly created for team member.  <br/> |
|AssignmentUpdateStatus  <br/> |Indicates the status of an assignment: 0 - Not edited by resource. 1 - Edited by resource but not updated to the project manager yet.  <br/> |
|AssignmentLastDelegationId  <br/> |The last delegation performed on this assignment.  <br/> |
|AssignmentPercentWorkCompleted  <br/> |The amount of work completed on the assignment.  <br/> |
|AssignmentSendUpdatesDate  <br/> |The date and time that an assignment update was sent by the resource to a manager.  <br/> |
|AssignmentSummaryProgress  <br/> |Shows progress on a summary task based on progress on its subtasks and where these subtasks have been scheduled.  <br/> |
|TeamLeadUid  <br/> |Unique identifier of the team lead.  <br/> |
|TeamLeadName  <br/> |Name of the team lead.  <br/> |
|WNWRK_UID  <br/> |Internal use only.  <br/> |
|WNWORK_ENTRY_UID  <br/> |Internal use only.  <br/> |
|AssignmentAssignedToExisting  <br/> |Indicates whether a new assignment has been created by a resource using the assign self to task feature.  <br/> |
|ReservedData1  <br/> |Used to temporarily store calculated values.  <br/> |
|ReservedData2  <br/> |Used to temporarily store calculated values.  <br/> |
|ReservedData3  <br/> |Used to temporarily store calculated values.  <br/> |
|AssignmentTDModifyDate  <br/> |Last modified date for assignment timephased data.  <br/> |
|AssignmentResumeDate  <br/> |The date that the assignment resumed.  <br/> |
|AssignmentStopDate  <br/> |The date that the assignment was stopped.  <br/> |
|AssignmentIsPublished  <br/> |True if assignment is published.  <br/> |
|AssignmentDemandRequire  <br/> |Indicates how to assign resources when using the resource substitution wizard.  <br/> |
|AssignmentIsCostValid  <br/> |Indicates whether or not the cost associated with the assignment has been approved.  <br/> |
|AssignmentCostIsEdited  <br/> |Indicates if the cost associated with this assignment was edited.  <br/> |
|AssignmentOtherType  <br/> | Indicates the type of assignment:  <br/>  0 - Regular  <br/>  1 - TaskOnlyWork  <br/>  2 - FixedCosts  <br/>  3 - FixedCostsAndTaskOnly  <br/>  4 - RegularUnassigned  <br/> |
|AssignmentUpdatesConflict  <br/> |True if there are conflicting updates for assignment  <br/> |
|DeletedFlag  <br/> |Indicates if the assignment was deleted.  <br/> |
|AssignmentCV  <br/> |Earned value cost variance.  <br/> |
|AssignmentHyperlinkFriendlyName  <br/> |The title or explanatory text for a hyperlink associated with an assignment.  <br/> |
|AssignmentHyperlinkAddress  <br/> |The URL or UNC path of a document.  <br/> |
|AssignmentHyperlinkSubAddress  <br/> |The specific location in a document within a hyperlink associated with a assignment.  <br/> |
|AssignmentNotes  <br/> |The notes that are entered in the assignment details dialog box.  <br/> |
|AssignmentVAC  <br/> |The difference between baseline cost and total cost.  <br/> |
|AssignmentSV  <br/> |Earned value schedule variance, through the project status date.  <br/> |
|AssignmentWorkVariance  <br/> |The variance of assignment work from the baseline work as minutes x 1000.  <br/> |
|AssignmentCostVariance  <br/> |The difference between the cost and baseline cost for a resource.  <br/> |
|AssignmentBudgetWork  <br/> |The budgeted work amount for work or material resources on this assignment.  <br/> |
|AssignmentBudgetCost  <br/> |The budgeted amount for cost resources on this assignment.  <br/> |
|AssignmentTaskManagementFlags  <br/> |Internal use only.  <br/> |
|AssignmentIgnoreResourceCalendar  <br/> |Indicates whether the resource calendar intersects with the task calendar.  <br/> |
|AssignmentWinProjUniqueId  <br/> |Indicates a unique identifier for the assignment used in Project client.  <br/> |
|AssignmentRemovedFromTS  <br/> |Indicates if the assignment was removed from the timesheet.  <br/> |
|AssignmentCreatedDate  <br/> |The date that the assignment was created.  <br/> |
|AssignmentModifiedDate  <br/> |The date that the assignment was last updated.  <br/> |

   
Each **Assignments** object may have a collection of **CustomFields** objects, which may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldUid  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|AssignmentUid  <br/> |Unique identifier for the assignment.  <br/> |
|Type  <br/> |Type of the custom field (can be number, text, cost, duration, date, fals, finish date, start date, etc.).  <br/> |
|CustomFieldValue  <br/> |Value properties for the custom field.  <br/> |
|DurationFormat  <br/> |Specifies the display format for the value if type is "duration".  <br/> |
|LookupTableUid  <br/> |Unique identifier for the lookup table.  <br/> |
|IndicatorValue  <br/> |Specifies the value of the custom field if the type of custom field is "indicator".  <br/> |
   
### Timesheets
<a name="Timesheets"> </a>

Timesheets contains data about timesheets the user owns or is a part of. For each timesheet, you will see the following objects:
  
|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetName  <br/> |Name of the timesheet.  <br/> |
|TimesheetOwnerID  <br/> |The unique identifier for the owner of the timesheet.  <br/> |
|TimesheetOwner  <br/> |The owner of the timesheet.  <br/> |
|StatusID  <br/> |The value associated with the timesheet status (see Status).  <br/> |
|Status  <br/> |The status of the timesheet.  <br/> |
|PeriodName  <br/> |The name of the timesheet period.  <br/> |
|StartDate  <br/> |The start date and time of the timesheet.  <br/> |
|EndDate  <br/> |The end date and time for the timesheet.  <br/> |
|PeriodUID  <br/> |The unique identifier for the timesheet period.  <br/> |
|PeriodStatusID  <br/> |The status identifier of the timesheet period (open, closed, or all periods).  <br/> |
|PeriodStatus  <br/> |The status of the timesheet period.  <br/> |
|Comment  <br/> |Comment details.  <br/> |
|ModifiedDate  <br/> |The date and time that the timesheet was last modified.  <br/> |
|CreatedDate  <br/> |The date and time that the timesheet was created.  <br/> |
   
A **Timesheets** object can have a collection of **Lines** objects, which may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetLineId  <br/> |Unique identifier for the timesheet line item.  <br/> |
|AssignmentUID  <br/> |Unique identifier for the assignment.  <br/> |
|LastSavedWork  <br/> |Amount of Actual Work for the timesheet line item.  <br/> |
|CreatedDate  <br/> |Time and date of when the line item was created.  <br/> |
|ModifiedDate  <br/> |Time and date of when the line item was last modified.  <br/> |
|ProjectId  <br/> |Unique identifier of the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|TaskId  <br/> |Unique identifier for the task.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|TimesheetApproverResourceID  <br/> |Name of the Timesheet Approver.  <br/> |
|TimesheetApproverResourceName  <br/> |Resource ID of the Timesheet Approver.  <br/> |
|TimesheetClassDescription  <br/> |The description of the timesheet class (for example, to describe its purpose as the recording of sick time or vacation time).  <br/> |
|TimesheetClassId  <br/> |Unique identifier of the timesheet line class.  <br/> |
|TimesheetClassName  <br/> |The name of the timesheet line class.  <br/> |
|TimesheetClassType  <br/> |The type of the timesheet class (for example, sick time or vacation time).  <br/> |
|TimesheetLineComment  <br/> |The text comment for the timesheet line.  <br/> |
|TimesheetLineStatus  <br/> |The status of the timesheet line.  <br/> |
|TimesheetLineStatusId  <br/> |Unique identifier for the timesheet line status (see the corresponding TimesheetLineStatus value).  <br/> |
   
Each **Lines** object can have a collection of **Actuals** objects. Each **Actuals** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetLineId  <br/> |Unique identifier for the timesheet line.  <br/> |
|ActualOvertimeWorkBillable  <br/> |The actual billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualOvertimeWorkNonBillable  <br/> |The actual non-billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkBillable  <br/> |The actual billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkNonBillable  <br/> |The actual non-billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|Comment  <br/> |Comment details.  <br/> |
|CreatedDate  <br/> |The date and time that the timesheet actual was created.  <br/> |
|PlannedWork  <br/> |The estimated amount of work.  <br/> |
|StartDate  <br/> |Start date of the period.  <br/> |
|EndDate  <br/> |End date of the period.  <br/> |
|TimesheetLineModifiedDate  <br/> |Time and date the line was last updated.  <br/> |
   
A **Lines** object can have a collection of **CustomFields** objects, which may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimeSheetLineID  <br/> |Unique identifier for the timesheet line.  <br/> |
|CustomFieldUID  <br/> |Unique identifier for the custom field value.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|CustomFieldValue <br/> |Value properties for the custom field.|

   
### Timesheets_Reporting
<a name="Timesheets_Reporting"> </a>

Timesheets_Reporting contains timesheet data for the user from the reporting schema. For each **Timesheets** object, you will see the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetName  <br/> |Name of the timesheet.  <br/> |
|TimesheetOwnerId  <br/> |Unique identifier for the timesheet owner.  <br/> |
|TimesheetOwner  <br/> |Name of the timesheet owner.  <br/> |
|StatusDescription  <br/> |Status of the timesheet.  <br/> |
|PeriodName  <br/> |Name of the period.  <br/> |
|StartDate  <br/> |Start date of the period.  <br/> |
|EndDate  <br/> |End date of the period.  <br/> |
|PeriodUID  <br/> |Unique identifier for the period.  <br/> |
|PeriodStatusID  <br/> |Unique identifier for the period status.  <br/> |
|PeriodStatus  <br/> |The status of the timesheet period.  <br/> |
|Comment  <br/> |Comment details.  <br/> |
|ModifiedDate  <br/> |Time and date the timesheet was last modified.  <br/> |
   
Each **Timesheets** object can have a collection of **Line** objects. Each **Line** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetLineId  <br/> |Unique identifier for the timesheet line item.  <br/> |
|ActualOvertimeWorkBillable  <br/> |The actual billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualOvertimeWorkNonBillable  <br/> |The actual non-billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkBillable  <br/> |The actual billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkNonBillable  <br/> |The actual non-billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|PlannedWork  <br/> |The estimated amount of work.  <br/> |
|AssignmentUID  <br/> |Unique identifier for the assignment.  <br/> |
|LastSavedWork  <br/> |Unique identifier for the workflow stage.  <br/> |
|CreatedDate  <br/> |Time and date of when the line item was created.  <br/> |
|ModifiedDate  <br/> |Time and date of when the line item was last modified.  <br/> |
|ProjectId  <br/> |Unique identifier of the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|TaskId  <br/> |Unique identifier for the task.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|TaskHierarchy  <br/> |The hierarchical list of tasks for a project.  <br/> |
|TimesheetApproverResourceId  <br/> |Resource ID of the timesheet approver.  <br/> |
|TimesheetApproverResourceName  <br/> |Name of the timesheet approver.  <br/> |
|TimesheetClassDescription  <br/> |The description of the timesheet class (for example, to describe its purpose as the recording of sick time or vacation time).  <br/> |
|TimesheetClassId  <br/> |Unique identifier of the timesheet class.  <br/> |
|TimesheetClassName  <br/> |The name of the timesheet class.  <br/> |
|TimesheetClassType  <br/> |The type of the timesheet class (for example, sick time or vacation time).  <br/> |
|TimesheetLineComment  <br/> |The text comment for the timesheet line.  <br/> |
|TimesheetLineStatus  <br/> |The status of the timesheet line.  <br/> |
|TimesheetLineStatusId  <br/> |Unique identifier for the timesheet line status (see the corresponding TimesheetLineStatus value).  <br/> |
   
Each **Timesheets** object can have a collection of **Actuals** objects. Each **Actuals** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TimesheetLineId  <br/> |Unique identifier for the timesheet line.  <br/> |
|ActualOvertimeWorkBillable  <br/> |The actual billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualOvertimeWorkNonBillable  <br/> |The actual non-billable overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkBillable  <br/> |The actual billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|ActualWorkNonBillable  <br/> |The actual non-billable amount of regular, non-overtime work that has already been performed by resources assigned to tasks.  <br/> |
|AdjustmentIndex  <br/> |The timesheet actual adjustment index.  <br/> |
|Comment  <br/> |Comment details.  <br/> |
|CreatedDate  <br/> |The date and time that the timesheet line was created.  <br/> |
|LastChangedResourceName  <br/> |Name of the resource that last modified the line.  <br/> |
|PlannedWork  <br/> |The estimated amount of work.  <br/> |
|TimeByDay  <br/> |Date and time for the data, for example, 2013-03-29 00:00:00.000.  <br/> |
|TimeByDay_DayOfMonth  <br/> |Day of the month (1 - 31) for time by day calculation.  <br/> |
|TimeByDay_DayOfWeek  <br/> |Day of the week (1 - 7) for time by day calculation.  <br/> |
|TimesheetLineModifiedDate  <br/> |Time and date the line was last updated.  <br/> |
   
Each **Actuals** object can have a collection of **CustomFields** objects. Each **CustomFields** object may have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldId  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the resource.  <br/> |
|TimesheetUID  <br/> |Unique identifier for the timesheet.  <br/> |
|TimesheetLineId  <br/> |Unique identifier for the timesheet line item.  <br/> |
|CustomFieldValue  <br/> |Values for the custom field.  <br/> |
   
### UnsubscribedAlerts
<a name="UnsubscribedAlerts"> </a>

UnsubscribedAlerts contains data about alert notifications unsubscribed by the user. For each **UnsubscribedAlertData** object, you will see the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|Id  <br/> |Unique identifier for the alert.  <br/> |
|AlertName  <br/> |Name of the alert.  <br/> |
   
### UserViewSettings
<a name="UserProp"> </a>

> [!NOTE]
> The information in this section applies to Project Server 2016, Project Server 2013, and Project Online. For Project Server 2010, see the [UserViewSettings for Project Server 2010](project-online-and-project-server-export-data-definitions.md#UserView2010). 
  
UserViewSettings contains data about custom view settings that the user created. You can see properties for the following objects:
  
- **WebControlSettings**: User settings for web controls in different pages. 
    
- **WebControlResourcePlanEngagementSettings:**: User settings for web controls in the resource plan engagement pages. 
    
- **ViewSettings**: User settings in different views across the product. 
    
- **LastPDPViewed**: Information about the last Project Detail Page that was viewed for a particular project. 
    
- **UserSettings**: Settings customized by the user. 
    
- **OptimizerPlannerPlannerReqPages**: Settings customized on the Optimizer, Planner and Planner Request pages. 
    
- **PlannerDefPlannerResPlannerAvailPages**: Settings customized on the Planner Deficit, Planner Resource, Planner Availability pages. 
    
- **PortfolioAnalysisGridSettings**: Settings customized on the Portfolio Analysis Grid. 
    
- **OtherWebSettings**: Other settings customized on web pages. 
    
 **WebControlSettings** objects can have the following following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|WebControl  <br/> |Web control type (for example, resourcecenter).  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **WebControlResourcePlanEngagementSettings** objects can have the following properties: 

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|WebControl  <br/> |Web control type (for example, resourcecenter).  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **ViewSettings** objects can have following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ViewId  <br/> |The unique identifier for the view.  <br/> |
|ViewName  <br/> |Name of the view.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **LastPDPViewed** objects can have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |The unique identifier for the project.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyString  <br/> |String representing value of the property  <br/> |
|PropertyData  <br/> |The binary representation of the property string  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **UserSettings** objects can have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |The unique identifier for the project.  <br/> |
|SettingKey  <br/> |Key of the user setting stored in the database.  <br/> |
|PropertyString  <br/> |String representing value of the property  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
|PropertyData  <br/> |The binary representation of the property string  <br/> |
   
 **OptimizerPlannerPlannerReqPages** objects can have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PageName  <br/> |Name of the page.  <br/> |
|AnalysisUid  <br/> |Unique identifier of the analysis.  <br/> |
|AnalysisName  <br/> |Name of the analysis.  <br/> |
|ViewUid  <br/> |Unique identifier of the view  <br/> |
|ViewName  <br/> |Name of the view.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
For each **PlannerDefPlannerResPlannerAvailPages** object, you will see the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PageName  <br/> |Name of the page.  <br/> |
|AnalysisUid  <br/> |Unique identifier of the analysis.  <br/> |
|AnalysisName  <br/> |The name of the analysis.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **PortfolioAnalysisGridSettings** objects can have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PageUrl  <br/> |URL of the page.  <br/> |
|AnalysisId  <br/> |The unique identifier of the analysis.  <br/> |
|AnalysisName  <br/> |The name of the analysis.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
 **OtherWebSettings** objects can have the following properties: 
  
|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|SettingKey  <br/> |Unique key that describes the user setting data being stored.  <br/> |
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
|PropertyData  <br/> |The binary representation of the property string  <br/> |
   
 **PropertyName and PropertyValue properties**
  
You may see the following properties for the above objects for the **PropertyName** and corresponding **PropertyValue** properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ViewUid  <br/> |Unique identifier of the view  <br/> |
|JSGridWidth  <br/> |Width of the displayed grid (value in pixels).  <br/> |
|SelectedResourceIds  <br/> |Unique identifiers of resources selected last on the grid.  <br/> |
|SelectedResources  <br/> |Unique identifiers of resources selected last on the grid.  <br/> |
|TimeStampUID  <br/> |A sequential guid that updates every time the view is initialized.  <br/> |
|Duration  <br/> |Selected value of duration for display on the grid. Values are:  <br/> -1 -Invalid, -2 -The duration is an estimate, 1 -Seconds, 2 -Elapsed seconds, 3 -Minutes, 4 -Elapsed minutes, 5 -Hours, 6 -Elapsed Hours, 7 -Days, 8 -Elapsed days, 9 -Weeks, 10 -Elapsed Weeks, 11 -Months, 12 -Elapsed Months, 13 -Quarters, 14 -Elapsed Quarters, 15 -Years, 16 -Elapsed Years, 17 -Decades, 18 -Elapsed Decades, 19 -Percent, 20 -Elapsed Percent, 21 -No Units, 22 -Material Usage  <br/> |
|Date  <br/> |The date format used. Values are:  <br/> 1 - ShortDate, 2 - ShortTime, 3 - ShortDateTime, 4 - LongDate, 5 - LongDateTime, 6 - WeekDayMonth, 7 - MonthDay, 8 - YearMonth, 9 - Sortable, 10 - SmartShortDateTime, 10 - GeneralLongDateTime  <br/> |
|ProjectTeamJsGridFields  <br/> |Contains key value pairs of the fields on the grid.  <br/> |
|ExpandSubProjects  <br/> |If true, subprojects are expanded in the UI.  <br/> |
|GanttZoomLevel  <br/> |Level to which Gantt is zoomed in for display. Goes from most zoomed in to most zoomed out: 0 - Minute, 1 - Hour longdate, 2 - Hour shortdate, 3 - Day with the shortest day name, 4 - Day with the day Year Month listed, 5 - Day with the day year month listed, 6 - Month, 7 - Month, 8 - Quarter, 9 - Half year  <br/> |
|PredefinedFilter  <br/> |Value of current filtering. Values are: 0 - All, 1 - Overdue, 2 - Newly Assigned, 3- Completed, 4 - Incomplete, 5 - Custom  <br/> |
|DefaultLayout  <br/> |Default layout of the page. Values are: 0- None, 1- Gantt, 2- Timephased  <br/> |
|ZoomLevel  <br/> |Zoom level from most zoomed in to most zoomed out : 0- Minute, 1 - Hour longdate, 2- Hour shortdate, 3 - Day with the shortest day name, 4 - Day with the day Year Month listed, 5 - Day with the day year month listed, 6 - Month, 7 - Month, 8 - Quarter, 9 - Half year  <br/> |
|DividerPosition  <br/> |Position of JsGrid splitter in pixels.  <br/> |
|GroupBy0  <br/> |Field to group by.  <br/> |
|GroupBy1  <br/> |Field to group by.  <br/> |
|GroupBy2  <br/> |Field to group by.  <br/> |
|SortBy  <br/> |Field to sort by.  <br/> |
|SortByOrder  <br/> |0 - Ascending, 1 - Descending  <br/> |
|ViewOutlineLevel  <br/> |If value is -1, expand all, except for subprojects. If value is any other number, set that outline level expanded.  <br/> |
|FilterBy  <br/> |Column to filter by.  <br/> |
|SelectedFilterId  <br/> |Field selected to filter.  <br/> |
|JSGridFields  <br/> |Contains key-value pairs describing the settings used to display the Grid in the user interface.  <br/> |
|ShowTimeWithDates  <br/> |If true, time is displayed with dates. If false, they are not.  <br/> |
|PrincipalColumnWidth  <br/> |Width of principal column in pixels.  <br/> |
|CategoryColumnWidth  <br/> |Width of category column in pixels.  <br/> |
|IsSidebarHidden  <br/> |Set to true if sidebar is hidden, false if not.  <br/> |
|IsViewBubbleChart  <br/> |If true, cost constraint analysis chart is displayed. If false, the grid is displayed.  <br/> |
|IsViewSBAChart  <br/> |If true, Strategic Business Alignment Chart is displayed. If false, Efficient Frontier chart is displayed.  <br/> |
|IsHighlightDeficit  <br/> |If true, the Highlight Deficit option is checked. If false, it is not.  <br/> |
|ProjUid  <br/> |Unique identifier of project.  <br/> |
|IncludeProposedBookings  <br/> |True to include proposed bookings in the data displayed on grid, false otherwise.  <br/> |
|WorkUnits  <br/> |Determine work units for the grid. Values are: 0- Hours, 1 - Days, 2- Full Time Equivalent  <br/> |
|TimeScale  <br/> |Determines time scale for the grid. Values are: 3 - Days, 4- Weeks, 5- Months, 6- Quarters, 7 - Years  <br/> |
|SelectedViewType  <br/> |Determines the view type. Values are: 0 - AssignmentsByResource, 1 - AssignmentsByProject, 2- Availability, 3 - Work, 4 - HeatMapCapacityEngagement  <br/> |
|DateEarliestSerialized  <br/> |Represents start date of the view on Capacity Planning page.  <br/> |
|DateLatestSerialized  <br/> |Represents the end date of the view on Capacity Planning page.  <br/> |
|UpperThreshold  <br/> |Value of upper threshold on Capacity Planning page.  <br/> |
|LowerThreshold  <br/> |Value of lower threshold on Capacity Planning page.  <br/> |
|FromDate  <br/> |Start date of the view in the grid.  <br/> |
|ToDate  <br/> |End date of the view in grid.  <br/> |
|IncludeProposed  <br/> |If true, Include Proposed booking is checked. If false, it is not.  <br/> |
|TabExpanded  <br/> |If true, the filter tab is expanded on the Timesheet History page.  <br/> |
|DateFilterChecked  <br/> |If true, the date filter is checked on the Timesheet page.  <br/> |
|ResourceFilterChecked  <br/> |If true, the Resource Filter option is checked on the Timesheet page.  <br/> |
|StartDate  <br/> |Date when view starts.  <br/> |
|FinishDate  <br/> |Date when view ends.  <br/> |
|FilterMode  <br/> |Determines which timesheets are displayed. Values are: 1 - Show unsubmitted timesheets, 2- Show approved timesheets, 3- Show all timesheets  <br/> |
|CustomFilterSelected  <br/> |If true, a custom filter is selected.  <br/> |
|SelectedResource  <br/> |Numeric identifier of the resource selected last on the grid.  <br/> |
|SelectedFiscalPeriod  <br/> |Index of the fiscal period selected from the Fiscal Period dropdown menu.  <br/> |
|ShowTimeWithDate  <br/> |If true, time is displayed with dates.  <br/> |
|ShowInsertedProjects  <br/> |If true, inserted projects will display.  <br/> |
|ShowRollups  <br/> |If true, rollups will display.  <br/> |
|ShowGanttChart  <br/> |If true, Gantt chart will display.  <br/> |
|ShowProjectSummaryTask  <br/> |If true, project summary task will display on grid.  <br/> |
|ViewSelection  <br/> |Whether the view displays  *InProgressAndFailedJobsInThePastWeek/AllInProgressAndFailedJobs/SuccessfulJobsInThePastWeek/AllSuccessfulJobs/AllJobsInThePastWeek/AllJobs TimePhasedPane.*  .  <br/> |
|TimePhasedPane  <br/> |If true, the Timephased pane will display.  <br/> |
|IncludeSummaryTasks  <br/> |If true, summary tasks will display.  <br/> |
|ShowOvertimeWork  <br/> |If true, overtime work will display.  <br/> |
|ShowScheduledWork  <br/> |If true, scheduled work will display.  <br/> |
|ShowSelectedList  <br/> |If true, selected resources list will display.  <br/> |
|Timephased  <br/> |If true, the Timephased grid will be visible.  <br/> |
|Proposed  <br/> |If true, the proposed values will display.  <br/> |
|Planned  <br/> |If true, planned work will display.  <br/> |
|Overtime  <br/> |If true, overtime work will display.  <br/> |
|NonBillable  <br/> |If true, non-billable work will display.  <br/> |
|CommentOnSubmit  <br/> |If true, comment dialog will display on submit of timesheet.  <br/> |
|ShowTotals  <br/> |If true, total work will display.  <br/> |
|TimephasedStart  <br/> |ECMA Date representation of the start date of timephased data.  <br/> |
|TimephasedEnd  <br/> |ECMA Date representation of the end date of timephased data.  <br/> |
|showPlanned  <br/> |If true, planned work will display.  <br/> |
|showOvt  <br/> |If true, overtime work will display.  <br/> |
|showNonBill  <br/> |If true, non-billable work will display.  <br/> |
|dateFormat  <br/> |The format of date values: 1 - ShortDate, 2 - ShortTime, 3 - ShortDateTime, 4 -LongDate, 5 - LongDateTime, 6 - WeekdayDayMonth, 7 - MonthDay, 8 - YearMonth, 9 - Sortable, 10 - SmartShortDateTime, 11 - General LongDateTime  <br/> |
|durationFormat  <br/> |-1 - Invalid, -2 - SwitchToEstimatedDuration , 1 - Seconds, 2 - ElapsedSeconds, 3 - Minutes, 4 - ElapsedMinutes, 5 - Hours, 6 - ElapsedHours, 7 - Days, 8 - ElapsedDays, 9 - Weeks, 10 - ElapsedWeeks, 11 - Months, 12 - ElapsedMonths, 13 - Quarters, 14 - ElapsedQuarters, 15 - Years, 16 - ElapsedYears, 17 - Decades, 18 - ElapsedDecades, 19 - Percent, 20 - ElapsedPercent, 21 - None, 22 - Material  <br/> |
|workFormat  <br/> |-1 - Invalid, -2 - None , 0 - Seconds, 1 - Minutes, 2 - Hours, 3 - Days, 4 - Weeks, 5 - Months, 6 - Quarters, 7 - Years, 8 - Decades, 9 - Material  <br/> |
|filterType  <br/> |0 - All, Overdue - 1, NewlyAssigned - 2, Completed - 3, Incomplete - 4  <br/> |
|projUids  <br/> |List of projects selected for the resource constraint filter.  <br/> |
|roleUids  <br/> |List of roles selected for the resource constraint filter.  <br/> |
|UseDate  <br/> |If true, the  *Filter By Date*  checkbox is checked on the Manage Delegations page.  <br/> |
|UseResource  <br/> |If true, the  *Filter By Users*  checkbox is checked on the Manage Delegations page.  <br/> |
|UseWeek  <br/> |If true, the  *Only show delegates covering this week*  option is checked.  <br/> |
|UseSelfDelegates  <br/> |If true, the  *Only show delegates acting on my behalf*  checkbox is checked.  <br/> |
|UseNamedDelegate  <br/> |If true, the  *Delegate name*  checkbox is checked.  <br/> |
|UseActingFor  <br/> |If true, the  *Delegate name who is acting for*  option is checked.  <br/> |
|UseDateRange  <br/> |If true, the  *Date range*  checkbox is checked.  <br/> |
|DelegateUid  <br/> |Unique identifier that represents the currently filtered delegate.  <br/> |
|ActingForUid  <br/> |Unique identifier of the user that the delegation is on behalf of.  <br/> |
|DelegateName  <br/> |Name of the delegate.  <br/> |
|ActingForName  <br/> |Name of delegatee.  <br/> |
|FilterVisible  <br/> |If true, the filter options will display.  <br/> |
|GridTimeScaleUnits  <br/> |0- Hours, 1 - Days, 2- Full Time Equivalent  <br/> |
|DateRangeFrom  <br/> |Start date of data displayed in the view.  <br/> |
|DateRangeTo  <br/> |End date of data displayed in the view.  <br/> |
|DateRangeUnits  <br/> |Units used for date range display on grid. Values are: 0- seconds, 1- minutes, 2- hours, 3- days, 4- weeks, 5 - months, 6- quarters, 7 - years  <br/> |
   
#### UserViewSettings for Project Server 2010
<a name="UserView2010"> </a>

> [!NOTE]
> This section include information about UserViewSettings data in Project Server 2010. For information about Project Server 2016, Project Server 2013, or Project Online, see the previous section ([UserViewSettings](project-online-and-project-server-export-data-definitions.md#UserProp)). 
  
UserViewSettings contains data about custom view settings that the user created. Objects can have the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|PropertyName  <br/> |Name of the property.  <br/> |
|PropertyValue  <br/> |Value of the property.  <br/> |
   
The custom view objects include the following:
  
- **WebControlSettings**: These are user settings for web controls in different pages. These web controls include the following: 
    
|**Name**|**Web Control**|
|:-----|:-----|
|teambuilderhometab  <br/> |Team Builder  <br/> |
|teambuilderjsgridcontrol  <br/> |Team Builder  <br/> |
|effectiverightsgrid  <br/> |Effective Rights  <br/> |
|eptjsgridcontrol  <br/> |Enterprise Project Types  <br/> |
|projectcenterjsgridcontrol  <br/> |Project Center  <br/> |
|projectdrilldownjsgridcontrol  <br/> |Schedule Page  <br/> |
|resourceassignmentsjsgridcontrol  <br/> |Resource Assignments  <br/> |
|resourcecenterjsgridcontrol  <br/> |Resource Center  <br/> |
|resourcerequestsjsgridcontrol  <br/> |Resource Requests  <br/> |
|reviewtsdetailpartjsgridcontrol  <br/> |Review Timesheet  <br/> |
|selecttasksfortlgrid  <br/> |Select tasks for Timeline  <br/> |
|statusapprovalshistorypage  <br/> |Status Approval History  <br/> |
|approvalcenterjsgridcontrol  <br/> |Approvals  <br/> |
|statusapprovalspreviewjsgridcontrol  <br/> |Status Approvals Review  <br/> |
|mytasksjsgridcontrol  <br/> |My Tasks  <br/> |
|teamtasksjsgridcontrol  <br/> |Team Assignments  <br/> |
|timesheetpartjsgridcontrol  <br/> |Timesheets  <br/> |
   
   In the export data for Project Server 2010, WebControlSettings data will display the name of the web control after the actual property for the control. For example, the following is a **Date** property for the **MyTasksJSGridControl**, which has a value of **1**. 
    
  ```
   	{
   	        "PropertyName":  "DateMyTasksJSGridControl",
   	        "PropertyValue":  "1"
   	    },
  
  ```

- **WebControlResourcePlanEngagementSettings:**: These are user settings for web controls in the resource plan engagement pages. If the PropertyName contains ResPlanGrid or ProjectEngagementsGrid, then the GUID in the PropertyName is the Project Unique Identifier (PROJ_UID). You can retrieve the corresponding project name from the MSP_PROJECTS table in the Project Server 2010 Published database. 
    
- **ViewSettings**: These are user settings in different views across the product. If the PropertyName looks like it contains just one GUID, then that GUID is the View Identifier (WVIEW_UID) from the MSP_WEB_VIEW_REPORTS table in the Project Server 2010 Published database, and the corresponding view name is stored in the WVIEW_NAME. 
    
    The actual property name will display before the GUID value.
    
    In the following example, the View unique identifier is  *000010fc-7b06-45a9-9bd2-1cbfc2f64ce4*  and the property name is  *DividerPosition*  . 
    
  ```
   	{
   	        "PropertyName":  "DividerPosition000010fc-7b06-45a9-9bd2-1cbfc2f64ce4",
   	        "PropertyValue":  "0"
   	    },
  
  ```

- **LastPDPViewed**: This provides information about the last Project Detail Page that was viewed for a particular project. The unique identifier of the corresponding project (PROJ_UID) is displayed after the string  *PDPPages_LastViewed_PDP_For*  . Also, the project name (PROJ_NAME) can be obtained from the MSP_PROJECTS table in the Project Server 2010 Published database. In the following example, the project has a unique identifier of  *051f3a1e-02f5-4e45-bea7-30bfbf8df67f*  , and the last viewed Project Detail Page has unique identifier  *1e26f08d-2757-46d9-b726-16cae3614c56*  . You could find the project name by checking the MSP_PROJECTS table for the PROJ_NAME associated with  *051f3a1e-02f5-4e45-bea7-30bfbf8df67f.* 
    
  ```
   	{
   	        "PropertyName":  "PDPPages_LastViewed_PDP_For_051f3a1e-02f5-4e45-bea7-30bfbf8df67f",
   	        "PropertyValue":  "1e26f08d-2757-46d9-b726-16cae3614c56"
   	    },
  
  ```

- **OptimizerPlannerPlannerReqPages**: This provides settings the user customized on the Optimizer, Planner and Planner Request pages. If the PropertyName contains  *{Optimizer}*  ,  *{Planner*  } or  *{PlannerReq}*  , two unique identifiers will follow it. The first is the unique identifier of the view, and the second is the unique identifier for the analysis. You can find the corresponding view name (WVIEW_NAME) in the MSP_WEB_VIEW_REPORTS table from the view id (WVIEW_UID) in the Project Server 2010 Published database. The corresponding analysis name (ANALYSIS_NAME) can be obtained from the MSP_ANALYSIS table from the view ID(ANALYSIS_UID) column in the Project Server 2010 Published database. 
    
- **PlannerDefPlannerResPlannerAvailPages**: This provides settings the user customized on the Planner Deficit, Planner Resource, Planner Availability pages. If the PropertyName contains  *{PlannerDef}*  ,  *{PlannerRes}*  or  *{PlannerAvail}*  , then the GUID that follows it is the unique identifier of the analysis. The corresponding analysis name (ANALYSIS_NAME) can be obtained from the MSP_ANALYSIS table from the view ID (ANALYSIS_UID) in the Project Server 2010 Published database. 
    
 **PropertyName and PropertyValue properties**
  
You may see the following properties for the above objects for the **PropertyName** and corresponding **PropertyValue** properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ViewUid  <br/> |Unique identifier of the view  <br/> |
|JSGridWidth  <br/> |Width of the displayed grid (value in pixels).  <br/> |
|SelectedResourceIds  <br/> |Unique identifiers of resources selected last on the grid.  <br/> |
|SelectedResources  <br/> |Unique identifiers of resources selected last on the grid.  <br/> |
|TimeStampUID  <br/> |A sequential guid that updates every time the view is initialized.  <br/> |
|Duration  <br/> |Selected value of duration for display on the grid. Values are:  <br/> -1 -Invalid, -2 -The duration is an estimate, 1 -Seconds, 2 -Elapsed seconds, 3 -Minutes, 4 -Elapsed minutes, 5 -Hours, 6 -Elapsed Hours, 7 -Days, 8 -Elapsed days, 9 -Weeks, 10 -Elapsed Weeks, 11 -Months, 12 -Elapsed Months, 13 -Quarters, 14 -Elapsed Quarters, 15 -Years, 16 -Elapsed Years, 17 -Decades, 18 -Elapsed Decades, 19 -Percent, 20 -Elapsed Percent, 21 -No Units, 22 -Material Usage  <br/> |
|Date  <br/> |The date format used. Values are:  <br/> 1 - ShortDate, 2 - ShortTime, 3 - ShortDateTime, 4 - LongDate, 5 - LongDateTime, 6 - WeekDayMonth, 7 - MonthDay, 8 - YearMonth, 9 - Sortable, 10 - SmartShortDateTime, 10 - GeneralLongDateTime  <br/> |
|ProjectTeamJsGridFields  <br/> |Contains key value pairs of the fields on the grid.  <br/> |
|ExpandSubProjects  <br/> |If true, subprojects are expanded in the UI.  <br/> |
|GanttZoomLevel  <br/> |Level to which Gantt is zoomed in for display. Goes from most zoomed in to most zoomed out: 0 - Minute, 1 - Hour longdate, 2 - Hour shortdate, 3 - Day with the shortest day name, 4 - Day with the day Year Month listed, 5 - Day with the day year month listed, 6 - Month, 7 - Month, 8 - Quarter, 9 - Half year  <br/> |
|PredefinedFilter  <br/> |Value of current filtering. Values are: 0 - All, 1 - Overdue, 2 - Newly Assigned, 3- Completed, 4 - Incomplete, 5 - Custom  <br/> |
|DefaultLayout  <br/> |Default layout of the page. Values are: 0- None, 1- Gantt, 2- Timephased  <br/> |
|ZoomLevel  <br/> |Zoom level from most zoomed in to most zoomed out : 0- Minute, 1 - Hour longdate, 2- Hour shortdate, 3 - Day with the shortest day name, 4 - Day with the day Year Month listed, 5 - Day with the day year month listed, 6 - Month, 7 - Month, 8 - Quarter, 9 - Half year  <br/> |
|DividerPosition  <br/> |Position of JsGrid splitter in pixels.  <br/> |
|GroupBy0  <br/> |Field to group by.  <br/> |
|GroupBy1  <br/> |Field to group by.  <br/> |
|GroupBy2  <br/> |Field to group by.  <br/> |
|SortBy  <br/> |Field to sort by.  <br/> |
|SortByOrder  <br/> |0 - Ascending, 1 - Descending  <br/> |
|ViewOutlineLevel  <br/> |If value is -1, expand all, except for subprojects. If value is any other number, set that outline level expanded.  <br/> |
|FilterBy  <br/> |Column to filter by.  <br/> |
|SelectedFilterId  <br/> |Field selected to filter.  <br/> |
|JSGridFields  <br/> |Contains key-value pairs describing the settings used to display the Grid in the user interface.  <br/> |
|ShowTimeWithDates  <br/> |If true, time is displayed with dates. If false, they are not.  <br/> |
|PrincipalColumnWidth  <br/> |Width of principal column in pixels.  <br/> |
|CategoryColumnWidth  <br/> |Width of category column in pixels.  <br/> |
|IsSidebarHidden  <br/> |Set to true if sidebar is hidden, false if not.  <br/> |
|IsViewBubbleChart  <br/> |If true, cost constraint analysis chart is displayed. If false, the grid is displayed.  <br/> |
|IsViewSBAChart  <br/> |If true, Strategic Business Alignment Chart is displayed. If false, Efficient Frontier chart is displayed.  <br/> |
|IsHighlightDeficit  <br/> |If true, the Highlight Deficit option is checked. If false, it is not.  <br/> |
|ProjUid  <br/> |Unique identifier of project.  <br/> |
|IncludeProposedBookings  <br/> |True to include proposed bookings in the data displayed on grid, false otherwise.  <br/> |
|WorkUnits  <br/> |Determine work units for the grid. Values are: 0- Hours, 1 - Days, 2- Full Time Equivalent  <br/> |
|TimeScale  <br/> |Determines time scale for the grid. Values are: 3 - Days, 4- Weeks, 5- Months, 6- Quarters, 7 - Years  <br/> |
|SelectedViewType  <br/> |Determines the view type. Values are: 0 - AssignmentsByResource, 1 - AssignmentsByProject, 2- Availability, 3 - Work, 4 - HeatMapCapacityEngagement  <br/> |
|DateEarliestSerialized  <br/> |Represents start date of the view on Capacity Planning page.  <br/> |
|DateLatestSerialized  <br/> |Represents the end date of the view on Capacity Planning page.  <br/> |
|UpperThreshold  <br/> |Value of upper threshold on Capacity Planning page.  <br/> |
|LowerThreshold  <br/> |Value of lower threshold on Capacity Planning page.  <br/> |
|FromDate  <br/> |Start date of the view in the grid.  <br/> |
|ToDate  <br/> |End date of the view in grid.  <br/> |
|IncludeProposed  <br/> |If true, Include Proposed booking is checked. If false, it is not.  <br/> |
|TabExpanded  <br/> |If true, the filter tab is expanded on the Timesheet History page.  <br/> |
|DateFilterChecked  <br/> |If true, the date filter is checked on the Timesheet page.  <br/> |
|ResourceFilterChecked  <br/> |If true, the Resource Filter option is checked on the Timesheet page.  <br/> |
|StartDate  <br/> |Date when view starts.  <br/> |
|FinishDate  <br/> |Date when view ends.  <br/> |
|FilterMode  <br/> |Determines which timesheets are displayed. Values are: 1 - Show unsubmitted timesheets, 2- Show approved timesheets, 3- Show all timesheets  <br/> |
|CustomFilterSelected  <br/> |If true, a custom filter is selected.  <br/> |
|SelectedResource  <br/> |Numeric identifier of the resource selected last on the grid.  <br/> |
|SelectedFiscalPeriod  <br/> |Index of the fiscal period selected from the Fiscal Period dropdown menu.  <br/> |
|ShowTimeWithDate  <br/> |If true, time is displayed with dates.  <br/> |
|ShowInsertedProjects  <br/> |If true, inserted projects will display.  <br/> |
|ShowRollups  <br/> |If true, rollups will display.  <br/> |
|ShowGanttChart  <br/> |If true, Gantt chart will display.  <br/> |
|ShowProjectSummaryTask  <br/> |If true, project summary task will display on grid.  <br/> |
|ViewSelection  <br/> |Whether the view displays  *InProgressAndFailedJobsInThePastWeek/AllInProgressAndFailedJobs/SuccessfulJobsInThePastWeek/AllSuccessfulJobs/AllJobsInThePastWeek/AllJobs TimePhasedPane.*  .  <br/> |
|TimePhasedPane  <br/> |If true, the Timephased pane will display.  <br/> |
|IncludeSummaryTasks  <br/> |If true, summary tasks will display.  <br/> |
|ShowOvertimeWork  <br/> |If true, overtime work will display.  <br/> |
|ShowScheduledWork  <br/> |If true, scheduled work will display.  <br/> |
|ShowSelectedList  <br/> |If true, selected resources list will display.  <br/> |
|Timephased  <br/> |If true, the Timephased grid will be visible.  <br/> |
|Proposed  <br/> |If true, the proposed values will display.  <br/> |
|Planned  <br/> |If true, planned work will display.  <br/> |
|Overtime  <br/> |If true, overtime work will display.  <br/> |
|NonBillable  <br/> |If true, non-billable work will display.  <br/> |
|CommentOnSubmit  <br/> |If true, comment dialog will display on submit of timesheet.  <br/> |
|ShowTotals  <br/> |If true, total work will display.  <br/> |
|TimephasedStart  <br/> |ECMA Date representation of the start date of timephased data.  <br/> |
|TimephasedEnd  <br/> |ECMA Date representation of the end date of timephased data.  <br/> |
|showPlanned  <br/> |If true, planned work will display.  <br/> |
|showOvt  <br/> |If true, overtime work will display.  <br/> |
|showNonBill  <br/> |If true, non-billable work will display.  <br/> |
|dateFormat  <br/> |The format of date values: 1 - ShortDate, 2 - ShortTime, 3 - ShortDateTime, 4 -LongDate, 5 - LongDateTime, 6 - WeekdayDayMonth, 7 - MonthDay, 8 - YearMonth, 9 - Sortable, 10 - SmartShortDateTime, 11 - General LongDateTime  <br/> |
|durationFormat  <br/> |-1 - Invalid, -2 - SwitchToEstimatedDuration , 1 - Seconds, 2 - ElapsedSeconds, 3 - Minutes, 4 - ElapsedMinutes, 5 - Hours, 6 - ElapsedHours, 7 - Days, 8 - ElapsedDays, 9 - Weeks, 10 - ElapsedWeeks, 11 - Months, 12 - ElapsedMonths, 13 - Quarters, 14 - ElapsedQuarters, 15 - Years, 16 - ElapsedYears, 17 - Decades, 18 - ElapsedDecades, 19 - Percent, 20 - ElapsedPercent, 21 - None, 22 - Material  <br/> |
|workFormat  <br/> |-1 - Invalid, -2 - None , 0 - Seconds, 1 - Minutes, 2 - Hours, 3 - Days, 4 - Weeks, 5 - Months, 6 - Quarters, 7 - Years, 8 - Decades, 9 - Material  <br/> |
|filterType  <br/> |0 - All, Overdue - 1, NewlyAssigned - 2, Completed - 3, Incomplete - 4  <br/> |
|projUids  <br/> |List of projects selected for the resource constraint filter.  <br/> |
|roleUids  <br/> |List of roles selected for the resource constraint filter.  <br/> |
|UseDate  <br/> |If true, the  *Filter By Date*  checkbox is checked on the Manage Delegations page.  <br/> |
|UseResource  <br/> |If true, the  *Filter By Users*  checkbox is checked on the Manage Delegations page.  <br/> |
|UseWeek  <br/> |If true, the  *Only show delegates covering this week*  option is checked.  <br/> |
|UseSelfDelegates  <br/> |If true, the  *Only show delegates acting on my behalf*  checkbox is checked.  <br/> |
|UseNamedDelegate  <br/> |If true, the  *Delegate name*  checkbox is checked.  <br/> |
|UseActingFor  <br/> |If true, the  *Delegate name who is acting for*  option is checked.  <br/> |
|UseDateRange  <br/> |If true, the  *Date range*  checkbox is checked.  <br/> |
|DelegateUid  <br/> |Unique identifier that represents the currently filtered delegate.  <br/> |
|ActingForUid  <br/> |Unique identifier of the user that the delegation is on behalf of.  <br/> |
|DelegateName  <br/> |Name of the delegate.  <br/> |
|ActingForName  <br/> |Name of delegatee.  <br/> |
|FilterVisible  <br/> |If true, the filter options will display.  <br/> |
|GridTimeScaleUnits  <br/> |0- Hours, 1 - Days, 2- Full Time Equivalent  <br/> |
|DateRangeFrom  <br/> |Start date of data displayed in the view.  <br/> |
|DateRangeTo  <br/> |End date of data displayed in the view.  <br/> |
|DateRangeUnits  <br/> |Units used for date range display on grid. Values are: 0- seconds, 1- minutes, 2- hours, 3- days, 4- weeks, 5 - months, 6- quarters, 7 - years  <br/> |
   
### Workflow
<a name="Workflow"> </a>

This file contains data about Project workflows in which the user was an owner. For each **WorkflowInstances** object, you may see the following objects: 
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteID  <br/> |Unique identifier for the PWA site in which the workflow is used.  <br/> |
|ProjectID  <br/> |Unique identifier of the project utilizing the workflow.  <br/> |
|ProjectName  <br/> |Name of the project utilizing the workflow.  <br/> |
|WorkflowInstanceId  <br/> |Unique identifier of the workflow instance.  <br/> |
|WorkflowError  <br/> |Instance failed with this error string.  <br/> |
|WorkflowErrorResponseCode  <br/> |Instance failed with this error code.  <br/> |
|WorkflowCreatedDate  <br/> |Date the workflow instance for the project was created.  <br/> |
|EnterpriseProjectTypeUid  <br/> |Unique identifier for the enterprise project type using the workflow.  <br/> |
|EnterpriseProjectTypeName  <br/> |Name the enterprise project type using the workflow.  <br/> |
|WorkflowStatus  <br/> |Status of the workflow.  <br/> |
   
For each **WorkflowStatus** object, you may see the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|WorkflowInstanceId  <br/> |Unique identifier for the workflow instance.  <br/> |
|PhaseId  <br/> |Unique identifier for the workflow phase.  <br/> |
|PhaseName  <br/> |Name of the workflow phase.  <br/> |
|PhaseDescription  <br/> |Description of the workflow phase.  <br/> |
|StageId  <br/> |Unique identifier for the workflow stage.  <br/> |
|StageName  <br/> |Name of the workflow stage.  <br/> |
|StageDescription  <br/> |Description of the workflow stage.  <br/> |
|StageInformation  <br/> |Actual stage information that was updated through the workflow.  <br/> |
|StageOrder  <br/> |The order of a stage in a workflow.  <br/> |
|StageStatus  <br/> |The status of a workflow stage.  <br/> |
|StageStateDescription  <br/> |The description of the state of a workflow stage.  <br/> |
|StageEntryDate  <br/> |The date and time that a workflow stage begins.  <br/> |
|StageLastSubmitted  <br/> |Date when project was last submitted.  <br/> |
|StageCompletionDate  <br/> |Date the stage was completed.  <br/> |
|LastModifiedDate  <br/> |Time/Date the workflow instance was last modified.  <br/> |
   
## WorkspaceItems
<a name="WSS"> </a>

WorkspaceItems described data about SharePoint items that are used in Project Server and Project Online, such as Issues, Risks, and deliverables. This can include collections of:
  
- Issues
    
- Risks
    
- Deliverable
    
- ListItemAssociations
    
There can be a collection of **Issues** objects that have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|IssueUniqueId  <br/> |Unique identifier for the issue.  <br/> |
|IssueId  <br/> |The ID of the issue.  <br/> |
|Title  <br/> |The title or name of the issue.  <br/> |
|AssignedToResource  <br/> |WSS item assigned to field.  <br/> |
|AssignedToUserClaimsAccount  <br/> |WSS item assigned to claims field.  <br/> |
|NumberOfAttachments  <br/> |The number of attachments for the issue.  <br/> |
|DueDate  <br/> |Date the issue is due to complete.  <br/> |
|Category  <br/> |The category of the issue.  <br/> |
|Status  <br/> |The status of the issue.  <br/> |
|Priority  <br/> |The priority of the issue.  <br/> |
|Owner  <br/> |Name of the issue owner.  <br/> |
|OwnerUserClaimsAccount  <br/> |Claims account of the owner.  <br/> |
|Discussion  <br/> |The text field for the issue discussion.  <br/> |
|Resolution  <br/> |The resolution of the issue.  <br/> |
|IsFolder  <br/> |True if the issue is a folder in the SharePoint list.  <br/> |
|ItemRelativeUrlPath  <br/> |The relative URL of the issue.  <br/> |
|CreatedByResource  <br/> |The resource that created the issue.  <br/> |
|CreatedByUserClaimsAccount  <br/> |Claims account of the user that created the issue.  <br/> |
|CreatedDate  <br/> |The date and time the issue was created.  <br/> |
|ModifiedByResource  <br/> |The user who last modified the issue.  <br/> |
|ModifiedByUserClaimsAccount  <br/> |Claims account of the user that last modified the issue.  <br/> |
|ModifiedDate  <br/> |The date and time that the issue was last updated.  <br/> |
   
There can be a collection of **Risk** objects that have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project with the risk.  <br/> |
|ProjectName  <br/> |Name of the project with the risk.  <br/> |
|RiskUniqueId  <br/> |The unique identifier of the risk.  <br/> |
|RiskId  <br/> |The ID of a risk.  <br/> |
|Title  <br/> |The title or name of a risk.  <br/> |
|AssignedToResource  <br/> |WSS item assigned to field.  <br/> |
|AssignedToUserClaimsAccount  <br/> |WSS item assigned to claims field.  <br/> |
|NumberOfAttachments  <br/> |The number of attachments for a risk.  <br/> |
|DueDate  <br/> |Date the risk is due.  <br/> |
|Probability  <br/> |The percent probability that a risk will happen.  <br/> |
|Impact  <br/> |The magnitude of the impact if a risk happens.  <br/> |
|Exposure  <br/> |The overall threat of a risk, calculated by multiplying the risk probability by the impact.  <br/> |
|Cost  <br/> |The total projected cost for a risk.  <br/> |
|CostExposure  <br/> |The overall threat of risk, calculated by multiplying the cost by the risk probability.  <br/> |
|Category  <br/> |The risk category.  <br/> |
|Status  <br/> |The status of a risk.  <br/> |
|Owner  <br/> |Name of the risk owner.  <br/> |
|R.OwnerUserClaimsAccount  <br/> |Claims account of the risk owner.  <br/> |
|Description  <br/> |The text field for a risk description.  <br/> |
|MitigationPlan  <br/> |A plan for handling problems that are related to risk factors.  <br/> |
|ContingencyPlan  <br/> |The contingency plan for a risk.  <br/> |
|TriggerTask  <br/> |The condition that triggers the contingency plan (for example, date, exposure over threshold, tasks not completed, or other user-assigned values).  <br/> |
|TriggerDescription  <br/> |The description of the trigger that causes a risk.  <br/> |
|NumberOfAttachments  <br/> |The number of attachments for the risk.  <br/> |
|IsFolder  <br/> |True if the risk is a folder in the SharePoint list.  <br/> |
|ItemRelativeUrlPath  <br/> |The relative URL of the risk.  <br/> |
|CreatedByResource  <br/> |The resource that created a risk.  <br/> |
|CreatedByUserClaimsAccount  <br/> |Claims account of the user that created the risk.  <br/> |
|CreatedDate  <br/> |The date and time when a risk was created.  <br/> |
|ModifiedByResource  <br/> |The user who modified a risk.  <br/> |
|ModifiedByUserClaimsAccount  <br/> |Claims account of the user that last modified the risk.  <br/> |
|ModifiedDate  <br/> |The date and time when a risk was modified.  <br/> |
   
There can be a collection of **Deliverables** objects that have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project for the deliverable.  <br/> |
|ProjectName  <br/> |Name of the project for the deliverable.  <br/> |
|DeliverableUniqueId  <br/> |Unique identifier for the deliverable.  <br/> |
|DeliverableId  <br/> |The ID of the deliverable.  <br/> |
|Title  <br/> |The title of the deliverable.  <br/> |
|Description  <br/> |Description of the deliverable.  <br/> |
|StartDate  <br/> |The start date and time of the deliverable.  <br/> |
|FinishDate  <br/> |The finish date of the deliverable.  <br/> |
|IsFolder  <br/> |True if the deliverable is a folder in the SharePoint list.  <br/> |
|ItemRelativeUrlPath  <br/> |The relative URL of the deliverable.  <br/> |
|CreatedByResource  <br/> |The resource that created the deliverable.  <br/> |
|CreatedByUserClaimsAccount  <br/> |The Claims account of the user who created the deliverable  <br/> |
|CreatedDate  <br/> |The date and time that the deliverable was created.  <br/> |
|ModifiedByResource  <br/> |The resource that last changed the deliverable.  <br/> |
|ModifiedByUserClaimsAccount  <br/> |The Claims account of the user who last modified the deliverable.  <br/> |
|ModifiedDate  <br/> |The date and time that the deliverable was modified.  <br/> |
   
There can be a collection of **ListItemAssociations** objects that have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectId  <br/> |Unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|ListItemId  <br/> |Unique identifier for the list item.  <br/> |
|ListItemName  <br/> |Name of the list item.  <br/> |
|RelatedProjectId  <br/> |Unique identifier for the related project.  <br/> |
|RelatedProjectName  <br/> |Name of the related project.  <br/> |
|RelatedItemId  <br/> |Name of the item that is related to the list item  <br/> |
|RelatedItemTitle  <br/> |Title of the item that is related to the list item  <br/> |
|RelationshipTypeId  <br/> |Identifier of the relationship type  <br/> |
|RelationshipDescription  <br/> |Description of the relationship between list item and related item.  <br/> |
   
## Project-specific user data from the reporting data
<a name="projectspec"> </a>

The export method defined in [Export user data from Project Online](export-user-data-from-project-online.md) will also create eight files for each project in which the user was a part from the Reporting schema. 
  
Similarly, the queries for project-specific reporting data defined in [Export user data from Project Server](https://support.office.com/article/c85c548f-4406-4663-8487-192ee065a803) will provide you similar output. 
  
This data includes:
  
|**Name**|**Description**|
|:-----|:-----|
|[Reporting_AssignmentBaselineTimephased](project-online-and-project-server-export-data-definitions.md#AssignmentBaselineTimephased) <br/> |Assignment Baseline Timephased data for the project from the reporting schema.  <br/> |
|[Reporting_AssignmentTimephased](project-online-and-project-server-export-data-definitions.md#AssignmentTimephased) <br/> |Assignment Timephased data for the project from the reporting schema.  <br/> |
|[Reporting_ProjectBaseline](project-online-and-project-server-export-data-definitions.md#ProjectBaseline) <br/> |Project Baseline data for the project from the reporting schema.  <br/> |
|[Reporting_Tasks](project-online-and-project-server-export-data-definitions.md#ProjectTasks) <br/> |Project tasks data for the project from the reporting schema.  <br/> |
|[Reporting_Assignments](project-online-and-project-server-export-data-definitions.md#Assignments) <br/> |Assignment resources data for the project from the reporting schema.  <br/> |
|[Reporting_Resources](project-online-and-project-server-export-data-definitions.md#reporting_Resources) <br/> |Resources data for the project from the reporting schema.  <br/> |
|[Reporting_TaskBaselineTimephased](project-online-and-project-server-export-data-definitions.md#TaskBaselineTimephased) <br/> |Task baseline timephased data for the project from the reporting schema.  <br/> |
|[Reporting_TaskTimephased](project-online-and-project-server-export-data-definitions.md#TaskTimephased) <br/> |Task timephased data for the project from the reporting schema.  <br/> |
   
When you are exporting from Project Online, your will receive the information in json file format. The name for each file will be prefixed with the project name and project ID for the specific project. For example, if a project has the project name of *Project1*  and a project ID of  *fffa21a1-baac-e711-9ee6-00166dac9e0b*  , the first file in the table above will be named  *Project1_fffa21a1-baac-e711-9ee6-00166dac9e0b_draft.xml*  . 
  
### Reporting_AssignmentBaselineTimephased
<a name="AssignmentBaselineTimephased"> </a>

Reporting_AssignmentBaselineTimephased contains the properties that define the reporting data for assignment baseline timephased data in the ProjectData service. It has the following properties:
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|BaselineNumber  <br/> |An integer number that identifies a baseline in a project.  <br/> |
|AssignmentUID  <br/> |Unique identifier of the assignment.  <br/> |
|TimeByDay  <br/> |A primary key that identifies a day along a timeline. The granularity is in days only.  <br/> |
|ProjectUID  <br/> |The GUID of the project that is associated with the assignment baseline timephased data.  <br/> |
|TaskUID  <br/> |The GUID of the task that is associated with the assignment baseline timephased data.  <br/> |
|AssignmentBaselineCost  <br/> |The planned cost of the assignment.  <br/> |
|AssignmentBaselineWork  <br/> |The total planned person-hours scheduled for an assignment.  <br/> |
|AssignmentBaselineMaterialWork  <br/> |The planned number of units of supplies or other consumable items that are to be used to complete an assignment.  <br/> |
|AssignmentBaselineBudgetCost  <br/> |The planned cost of an assignment.  <br/> |
|AssignmentBaselineBudgetWork  <br/> |The planned total amount of time that is needed to complete an assignment.  <br/> |
|AssignmentBaselineBudgetMaterialWork  <br/> |The planned number of units of the supplies or other consumable items that are to be used to complete an assignment.  <br/> |
|AssignmentBaselineModifiedDate  <br/> |Date and time the assignment baseline was last modified.  <br/> |
|FiscalPeriodUID  <br/> |Unique identifier for the fiscal period.  <br/> |
|ResourceId  <br/> |Unique identifier for the resource.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
   
### Reporting_AssignmentTimephased
<a name="AssignmentTimephased"> </a>

Reporting_AssignmentTimephased contains the properties that define the reporting data for assignment timephased data in the ProjectData service. It has the following properties:
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|AssignmentUID  <br/> |Unique identifier for the assignment.  <br/> |
|TimeByDay  <br/> |A primary key that identifies a day along a timeline. The granularity is in days only.  <br/> |
|ProjectUID  <br/> |Unique identifier for the project for the assignment timephased data.  <br/> |
|TaskUID  <br/> |Unique identifier for the task for the assignment timephased data.  <br/> |
|FiscalPeriodUID  <br/> |Unique identifier for the fiscal period.  <br/> |
|ResourceId  <br/> |Unique identifier for the resource.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|AssignmentRegularCost  <br/> |The total cost for regular, nonovertime assignment work that has already been performed, in addition to remaining nonovertime work.  <br/> |
|AssignmentRegularWork  <br/> |The total amount of non-overtime work scheduled to be performed by a resource assigned to a task.  <br/> |
|AssignmentRemainingCost  <br/> |The costs associated with completing all remaining scheduled work by any resources on a specific task.  <br/> |
|AssignmentRemainingOvertimeCost  <br/> |The remaining scheduled overtime expense for an assignment.  <br/> |
|AssignmentRemainingOvertimeWork  <br/> |The amount of overtime work that remains on an assignment.  <br/> |
|AssignmentRemainingRegularCost  <br/> |The expense that will be incurred by completing the remaining regular, nonovertime work for an assignment.  <br/> |
|AssignmentRemainingRegularWork  <br/> |The amount of time, such as person-hours or days, that is still required to complete the regular, nonovertime work for an assignment.  <br/> |
|AssignmentRemainingWork  <br/> |The amount of time required by a resource assigned to a task to complete an assignment.  <br/> |
|AssignmentCombinedWork  <br/> |The work for the assignment, from both the project plan and the resource plan.  <br/> |
|AssignmentActualRegularCost  <br/> |The cost of the nonovertime work that has already been performed on an assignment.  <br/> |
|AssignmentActualRegularWork  <br/> |The actual amount of regular, nonovertime work that has already been performed on an assignment.  <br/> |
|AssignmentCost  <br/> |The total cost for an assignment, based on costs already incurred, in addition to costs that are planned for the remaining work.  <br/> |
|AssignmentOvertimeCost  <br/> |The total overtime cost for an assignment, including costs for overtime work that has already been performed, in addition to remaining overtime costs.  <br/> |
|AssignmentActualCost  <br/> |The costs incurred for work that has already been performed on an assignment, along with any other associated costs.  <br/> |
|AssignmentActualOvertimeCost  <br/> |The costs incurred for overtime work that has already been performed on an assignment.  <br/> |
|AssignmentWork  <br/> |The total amount of time, such as person-hours or days, that is scheduled for an assignment.  <br/> |
|AssignmentOvertimeWork  <br/> |The total overtime work for an assignment, including overtime work that has already been performed, in addition to remaining overtime work.  <br/> |
|AssignmentActualWork  <br/> |The amount of work that has already been performed on an assignment.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work that has already been performed on an assignment.  <br/> |
|AssignmentMaterialWork  <br/> |The total work time scheduled for a material resource.  <br/> |
|AssignmentMaterialActualWork  <br/> |The actual amount of work that has already been performed with the use of a material resource, usually expressed as a percentage of the scheduled amount of material resource work.  <br/> |
|AssignmentBudgetCost  <br/> |The total projected cost of an assignment.  <br/> |
|AssignmentBudgetWork  <br/> |The total projected amount of work that is planned for an assignment.  <br/> |
|AssignmentBudgetMaterialWork  <br/> |The total projected amount of use on the assignment of material resources.  <br/> |
|AssignmentResourcePlanWork  <br/> |The total time that is scheduled for an assignment in the resource plan.  <br/> |
|TaskIsActive  <br/> |True if the task for the assignment timephased data is active.  <br/> |
|AssignmentModifiedDate  <br/> |Date and time the assignment was last updated.  <br/> |
   
### Reporting_ProjectBaseline
<a name="ProjectBaseline"> </a>

Reporting_ProjectBaseline contains the properties that define the reporting data for project baseline data in the ProjectData service. It has the following properties:
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|BaselineNumber  <br/> |A number that identifies a project baseline.  <br/> |
|ProjectUID  <br/> |Unique identifier for the project.  <br/> |
|TaskUID  <br/> |Unique identifier for the task.  <br/> |
|TaskBaselineCost  <br/> |The total planned cost for the task.  <br/> |
|TaskBaselineFixedCost  <br/> |A set task cost that is projected in the baseline and that remains constant regardless of the task duration or the work performed by a resource.  <br/> |
|TaskBaselineWork  <br/> |The total hours that are scheduled in the baseline projection for a task.  <br/> |
|TaskBaselineBudgetCost  <br/> |The cost of the budgeted amount of work as projected in the baseline.  <br/> |
|TaskBaselineBudgetWork  <br/> |The budgeted amount of work as projected in the baseline.  <br/> |
|TaskBaselineStartDate  <br/> |The projected task start date and time.  <br/> |
|TaskBaselineFinishDate  <br/> |The projected completion date of a task.  <br/> |
|TaskBaselineDeliverableStartDate  <br/> |The published deliverable start date and time for a task.  <br/> |
|TaskBaselineDeliverableFinishDate  <br/> |The published deliverable finish date and time for a task as projected in the baseline.  <br/> |
|TaskBaselineDuration  <br/> |The amount of time estimated to complete a task.  <br/> |
|TaskBaselineStartDateString  <br/> |A string that contains the projected task start date and time.  <br/> |
|TaskBaselineFinishDateString  <br/> |A string that contains the projected task finish date and time.  <br/> |
|TaskBaselineDurationString  <br/> |A string that contains the projected task duration.  <br/> |
|TaskBaselineModifiedDate  <br/> |The date and time the task was last updated.  <br/> |
   
### Reporting_Tasks
<a name="ProjectTasks"> </a>

Reporting_ProjectTasks contains the properties that define the reporting data for project tasks data in the ProjectData service. It has the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|TaskUID  <br/> |The unique identifier of the task.  <br/> |
|TaskParentUID  <br/> |The unique identifier of the parent task.  <br/> |
|ProjectUID  <br/> |The unique identifier of the project to which the task belongs.  <br/> |
|FixedCostAssignmentUID  <br/> |The PWA instance site ID.  <br/> |
|TaskName  <br/> |The unique identifier of the task.  <br/> |
|TaskOutlineLevel  <br/> |The outline level of the task.  <br/> |
|TaskOutlineNumber  <br/> |The outline number of the task.  <br/> |
|TaskIndex  <br/> |Number of the task in the local project.  <br/> |
|TaskIsProjectSummary  <br/> |Whether the task is a project summary task.  <br/> |
|TaskIsOverallocated  <br/> |Gets a value that indicates whether the task is overallocated.  <br/> |
|TaskIsMilestone  <br/> |Whether the task is a milestone.  <br/> |
|TaskIsCritical  <br/> |Gets a value that indicates whether the timing for the task is critical or whether there can be any slack in the timing.  <br/> |
|TaskIsSummary  <br/> |Whether the task is a summary task.  <br/> |
|TaskStatusManagerUID  <br/> |The unique identifier of the task status manager.  <br/> |
|TaskFixedCost  <br/> |The fixed cost of the task.  <br/> |
|TaskActualFixedCost  <br/> |The actual fixed cost of the task.  <br/> |
|TaskCost  <br/> |The projected or scheduled cost of the task.  <br/> |
|TaskOvertimeCost  <br/> |The sum of the actual and remaining overtime cost of the task.  <br/> |
|TaskActualCost  <br/> |The actual cost of the task.  <br/> |
|TaskActualOvertimeCost  <br/> |The actual overtime cost of the task.  <br/> |
|TaskWork  <br/> |The amount of scheduled work for the task.  <br/> |
|TaskOvertimeWork  <br/> |The amount of overtime work scheduled for the task.  <br/> |
|TaskActualWork  <br/> |The actual work for the task.  <br/> |
|TaskActualOvertimeWork  <br/> |The actual overtime work for the task.  <br/> |
|TaskDurationVariance  <br/> |The difference between the baseline duration of the task and the total duration, or current estimated duration, of the task.  <br/> |
|TaskStartVariance  <br/> |The variance of the task start date from the baseline start date as minutes x 1000.  <br/> |
|TaskFinishVariance  <br/> |The variance of the task finish date from the baseline finish date as minutes x 1000.  <br/> |
|TaskTotalSlack  <br/> |The amount of total slack.  <br/> |
|TaskFreeSlack  <br/> |The amount of free slack.  <br/> |
|TaskDuration  <br/> |The planned duration of the task.  <br/> |
|TaskActualDuration  <br/> |The actual duration of the task.  <br/> |
|TaskStartDate  <br/> |The scheduled start date of the task.  <br/> |
|TaskFinishDate  <br/> |The scheduled finish date of the task.  <br/> |
|TaskDeliverableStartDate  <br/> |The published deliverable start date and time for a task.  <br/> |
|TaskDeliverableFinishDate  <br/> |The published deliverable finish date and time for a task.  <br/> |
|TaskActualStartDate  <br/> |The date the task was started.  <br/> |
|TaskActualFinishDate  <br/> |The date the task was completed.  <br/> |
|TaskPercentCompleted  <br/> |The percentage of the task duration completed.  <br/> |
|TaskPercentWorkCompleted  <br/> |The percentage of the task work completed.  <br/> |
|TaskPhysicalPercentCompleted  <br/> |The percentage complete value entered by the Project Manager. This can be used as an alternative for calculating the budgeted cost of work performed (BCWP).  <br/> |
|TaskACWP  <br/> |The actual cost of work performed on the task to date.  <br/> |
|TaskBCWP  <br/> |The budgeted cost of work performed on the task to date.  <br/> |
|TaskBCWS  <br/> |The budgeted cost of work scheduled for the task.  <br/> |
|TaskLevelingDelay  <br/> |The delay caused by leveling the task.  <br/> |
|TaskPriority  <br/> |The priority of the task from 0 to 1000.  <br/> |
|TaskSPI  <br/> |Shows the ratio of the budgeted cost of work performed to the budgeted cost of work scheduled (BCWP/BCWS).  <br/> |
|TaskTCPI  <br/> |Ratio of the work remaining to be done to funds remaining to be spent, as of the task status date (to complete performance index).  <br/> |
|TaskVAC  <br/> |Variance at completion.  <br/> |
|TaskDeadline  <br/> |The target date and time for when a task should be completed.  <br/> |
|TaskDurationIsEstimated  <br/> |Whether the baseline duration of the task was estimated.  <br/> |
|TaskEAC  <br/> |Task estimate at completion is the expected total cost of a task based on performance up to the status date.  <br/> |
|TaskIsEffortDriven  <br/> |Whether the task is effort-driven.  <br/> |
|TaskIsExternal  <br/> |Whether the task is external.  <br/> |
|TaskIsRecurring  <br/> |Whether the task is a recurring task.  <br/> |
|TaskCostVariance  <br/> |Gets the difference in cost terms between the current progress and the baseline planned progress for a resource on the task.  <br/> |
|TaskCV  <br/> |Earned value cost variance - show the difference between how much it should have cost and how much it has actually cost to achieve the current level of completion up to the status date.  <br/> |
|TaskCPI  <br/> |Show the ratio of budgeted (or baseline) costs of work performed to actual costs of work performed, up to the project status date.  <br/> |
|TaskEarlyFinish  <br/> |The early finish date of the task.  <br/> |
|TaskEarlyStart  <br/> |The early start date of the task.  <br/> |
|TaskLateFinish  <br/> |The late finish date of the task.  <br/> |
|TaskLateStart  <br/> |The late start date of the task.  <br/> |
|TaskSV  <br/> |The cost difference between the current progress and the baseline plan of a task.  <br/> |
|TaskWorkVariance  <br/> |The variance of task work from the baseline task work as minutes x 1000.  <br/> |
|TaskIgnoresResourceCalendar  <br/> |Whether the task ignores the resource calendar.  <br/> |
|TaskClientUniqueId  <br/> |Unique ID of the task as shown in Project Professional.  <br/> |
|TaskIsMarked  <br/> |True if task is marked for identification or further action.  <br/> |
|TaskWBS  <br/> |The work breakdown structure (WBS) code of the task.  <br/> |
|TaskCreatedDate  <br/> |The date that the task was created.  <br/> |
|TaskModifiedDate  <br/> |The date that the task was last updated.  <br/> |
|TaskBudgetCost  <br/> |Used to compare budgeted costs with the planned or actual costs.  <br/> |
|TaskBudgetWork  <br/> |The scheduled work for a task.  <br/> |
|TaskResourcePlanWork  <br/> |Time scheduled on a task for all resouces in the resource plan. This field is used to avoid double-counting if the scheduled work is from a resource plan.  <br/> |
|TaskHyperLinkFriendlyName  <br/> |Shows the title or explanatory text for a hyperlink associated with a task.  <br/> |
|TaskHyperLinkAddress  <br/> |A hyperlink that is associated with a task.  <br/> |
|TaskHyperLinkSubAddress  <br/> |The subaddress of a task hyperlink.  <br/> |
|TaskStartDateString  <br/> |The string value for a task start date and time.  <br/> |
|TaskFinishDateString  <br/> |The string value of the task finish date and time.  <br/> |
|TaskDurationString  <br/> |The string value for the duration of a task.  <br/> |
|TaskIsManuallyScheduled  <br/> |The unique identifier of the project to which the task belongs.  <br/> |
|TaskIsActive  <br/> |If the task is currently active.  <br/> |
|CustomFields  <br/> |Custom fields used in the task.  <br/> |
   
If the task contains a **CustomField** object, it will have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldId  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the resource.  <br/> |
|TaskId  <br/> |Unique identifier for the task in which the customer field is used.  <br/> |
|CustomFieldValue  <br/> |Values for the custom field.  <br/> |
   
### Reporting_Assignments
<a name="Assignments"> </a>

Reporting_Assignments contains the properties that define the reporting data for assignments in the ProjectData service. It has the following properties:
  

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|AssignmentUID  <br/> |Unique identifier for the assignment.  <br/> |
|ProjectUID  <br/> |Unique identifier for the project for the assignment.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource for the assignment.  <br/> |
|TaskUID  <br/> |Unique identifier for the task for the assignment.  <br/> |
|ResourceOwnerUID  <br/> |Unique identifier for the resource owner.  <br/> |
|AssignmentCost  <br/> |The total cost for an assignment, based on costs already incurred, in addition to costs that are planned for the remaining work.  <br/> |
|AssignmentOvertimeCost  <br/> |The total overtime cost for an assignment, including costs for overtime work that has already been performed, in addition to remaining overtime costs.  <br/> |
|AssignmentActualCost  <br/> |The costs incurred for work that has already been performed on an assignment, along with any other associated costs.  <br/> |
|AssignmentActualOvertimeCost  <br/> |The costs incurred for overtime work that has already been performed on an assignment.  <br/> |
|AssignmentWork  <br/> |The total amount of time, such as person-hours or days, that is scheduled for an assignment.  <br/> |
|AssignmentOvertimeWork  <br/> |The total overtime work for an assignment, including overtime work that has already been performed, in addition to remaining overtime work.  <br/> |
|AssignmentActualWork  <br/> |The amount of work that has already been performed on an assignment.  <br/> |
|AssignmentActualOvertimeWork  <br/> |The actual amount of overtime work that has already been performed on an assignment.  <br/> |
|AssignmentMaterialWork  <br/> |The total work time scheduled for a material resource.  <br/> |
|AssignmentMaterialActualWork  <br/> |The actual amount of work that has already been performed with the use of a material resource, usually expressed as a percentage of the scheduled amount of material resource work.  <br/> |
|AssignmentPercentWorkCompleted  <br/> |Percentage of work that has been completed.  <br/> |
|AssignmentStartDate  <br/> |Date a resource is scheduled to begin an assignment.  <br/> |
|AssignmentFinishDate  <br/> |Date a resource is scheduled to complete assignment.  <br/> |
|AssignmentActualStartDate  <br/> |Date a resource is begins an assignment.  <br/> |
|AssignmentActualFinishDate  <br/> |Date a resource is completes an assignment.  <br/> |
|AssignmentDelay  <br/> |Amount of time a resource is to wait before starting to work on an assignment.  <br/> |
|AssignmentStartVariance  <br/> |Variance at the start of the assignment.  <br/> |
|AssignmentFinishVariance  <br/> |Variance at the assignment finish.  <br/> |
|AssignmentACWP  <br/> |Actual cost of work performed for the assignment.  <br/> |
|AssignmentBCWP  <br/> |Budgeted cost of work performed for the assignment (earned value).  <br/> |
|AssignmentBCWS  <br/> |Budgeted cost of work scheduled for the assignment (planned value).  <br/> |
|AssignmentBookingID  <br/> |Assignment booking GUID.  <br/> |
|AssignmentBookingName  <br/> |Assignment booking name (committed or proposed).  <br/> |
|AssignmentType  <br/> |Type of assignment. NormalAssignment=0, WorkOnlyAssignment=1, FixedCostAssignment=2, FixedCostWorkOnlyAssignment=3, EmptyAssignment=4, FixedCostGeneratedAssignment=100 (generated during RDS transfer), ResourcePlanAssignment=101.  <br/> |
|TypeName  <br/> |Name of the assignment type.  <br/> |
|AssignmentResourceType  <br/> |The type of resource that is associated with an assignment. See [Type enumeration](/previous-versions/office/project-class/gg223589(v=office.15)).  <br/> |
|R.TypeName  <br/> ||
|IsPublic  <br/> |True if the item was published, so a team member can see it.  <br/> |
|AssignmentIsPublished  <br/> |True if assignment is published.  <br/> |
|AssignmentCostVariance  <br/> |Difference between baseline cost and total cost.  <br/> |
|AssignmentWorkVariance  <br/> |Difference between baseline work and currently scheduled work.  <br/> |
|AssignmentCV  <br/> |Earned value cost variance.  <br/> |
|AssignmentSV  <br/> |Earned value schedule variance.  <br/> |
|AssignmentVAC  <br/> |Variance at completion.  <br/> |
|AssignmentIsOverallocated  <br/> |True if any assigned resources are overallocated.  <br/> |
|AssignmentPeakUnits  <br/> |Maximum number of units that a resource is assignmed for a task.  <br/> |
|AssignmentCreatedDate  <br/> |Date and time the assignment was created.  <br/> |
|AssignmentModifiedDate  <br/> |Date and time the assignment was last updated.  <br/> |
|AssignmentBudgetCost  <br/> |The total projected cost of an assignment.  <br/> |
|AssignmentBudgetWork  <br/> |The total projected amount of work that is planned for an assignment.  <br/> |
|AssignmentBudgetMaterialWork  <br/> |The total projected amount of use on the assignment of material resources.  <br/> |
|AssignmentResourcePlanWork  <br/> |The total time that is scheduled for an assignment in the resource plan.  <br/> |
|TaskIsActive  <br/> |True if the task for the assignment timephased data is active.  <br/> |
|TimesheetClassUID  <br/> |GUID of the timesheet class.  <br/> |
   
If the task contains a **CustomField** object, it will have the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldId  <br/> |Unique identifier for the custom field.  <br/> |
|CustomFieldName  <br/> |Name of the resource.  <br/> |
|PrimaryCustomFieldId  <br/> |The ID of the primary custom field (either a Task or a Resource type) that this custom field is a child of.  <br/> |
|PrimaryCustomFieldName  <br/> |The name of the primary custom field (either a Task or a Resource type) that this custom field is a child of.  <br/> |
|AssignmentRolldown  <br/> |Does the value of this assignment rolls down from the primary custom field. If it does,the value is the same os the value of the corresponding primary custom field unless ovverriden in the assignment custom field  <br/> |
|AssignmentId  <br/> |The assignment id that this custom field belong to.  <br/> |
|CustomFieldValue  <br/> |Values for the custom field.  <br/> |
   
### Reporting_Resources
<a name="reporting_Resources"> </a>

Reporting_Resources contains the properties that define the reporting data for resources in the ProjectData service. It has the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|ResourceName  <br/> |Display name of the resource.  <br/> |
|ResourceStandardRate  <br/> |The standard rate of pay for a resource.  <br/> |
|ResourceOvertimeRate  <br/> |The rate of overtime pay for a resource.  <br/> |
|ResourceStatusUID  <br/> |GUID of the resource status.  <br/> |
|ResourceStatusName  <br/> |Localized name of the resource status. Status includes Unassigned Resource, Local Resource, Unknown Resource, and Enterprise Resource. Most resources on a project have the Enterprise Active status value.  <br/> |
|ResourceCode  <br/> |Contains any code, abbreviation, or number you want to enter as part of a resource's information.  <br/> |
|ResourceCostPerUse  <br/> |The cost that accrues each time a work resource is used.  <br/> |
|ResourceEmailAddress  <br/> |The email address of a resource.  <br/> |
|ResourceInitials  <br/> |Initials of the resource.  <br/> |
|ResourceMaterialLabel  <br/> |The Material Label field contains the unit of measurement you enter for a material resource, for example, tons, boxes, or cubic yards. This label is then used in conjunction with the material resource's assignment units, for example, eight tons or 22 boxes.  <br/> |
|ResourceType  <br/> |The type of a resource (for example, Enterprise, Local, Project Server, Material, or Generic). See [ResourceType Enumerations](/previous-versions/office/project-class/jj232846(v=office.15)) for values.  <br/> |
|TypeName  <br/> |Name of the resource type.  <br/> |
|ResourceGroup  <br/> |The Group field contains the name of the group that a resource belongs to.  <br/> |
|ResourceMaxUnits  <br/> |The maximum capacity (percentage or units) that a resource is available to accomplish tasks during the current time period.  <br/> |
|ResourceBookingType  <br/> |The resource booking type: proposed or committed.  <br/> |
|ResourceTimesheetManagerUID  <br/> |Timesheet manager for the given resource.  <br/> |
|ResourceEarliestAvailableFrom  <br/> |The earliest date that a resource is available for work on a particular task.  <br/> |
|ResourceLatestAvailableTo  <br/> |The last date that a resource is available.  <br/> |
|ResourceCanLevel  <br/> |True if resource leveling can be done.  <br/> |
|ResourceHyperlink  <br/> |The URL that is specified for a resource in the Edit User page of Project Web Access.  <br/> |
|ResourceHyperlinkHref  <br/> |The text that is displayed for a resource hyperlink, as specified in the Edit User page of Project Web Access.  <br/> |
|ResourceNTAccount  <br/> |The Windows account name for a resource.  <br/> |
|ResourceIsActive  <br/> |Specifies the project version that was active when the resource was created. This field is for internal use by the Project cache.  <br/> |
|ResourceIsGeneric  <br/> |True if the resource is generic.  <br/> |
|ResourceIsTeam  <br/> |True if a resource is a team resource.  <br/> |
|ResourceBaseCalendar  <br/> |The base calendar for a resource.  <br/> |
|ResourceWorkgroup  <br/> |A number value that represents a team collaboration method for a resource.  <br/> |
|ResourceClientUniqueId  <br/> |Unique ID of the resource from a local project when opened in Project Professional.  <br/> |
|ResourceCostCenter  <br/> |A user-defined code for resource cost accounting.  <br/> |
|ResourceCreatedRevisionCounter  <br/> |Specifies the project version that was active when the resource was created. This field is for internal use by the Project cache.  <br/> |
|ResourceModifiedRevisionCounter  <br/> |Count of how many times resource was modified.  <br/> |
|ResourceCreatedDate  <br/> |The date and time that a resource was created in the project.  <br/> |
|ResourceModifiedDate  <br/> |The date that information about a resource was last modified.  <br/> |
|ResourceRequiresEngagement  <br/> |True if the resource can only be requested through an engagement request.  <br/> |
|LCID  <br/> |Resource's Language Code ID.  <br/> |
|UserClaimsAccount  <br/> |Login name for the user.  <br/> |
   
### Reporting_TaskBaselineTimephased
<a name="TaskBaselineTimephased"> </a>

Reporting_TaskBaselineTimephased contains the properties that define the reporting data for task baseline timephased data in the ProjectData service. It has the following properties:

|**Object** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|BaselineNumber  <br/> |A number that identifies a project baseline.  <br/> |
|ProjectUID  <br/> |Unique identifier for the project.  <br/> |
|TaskUID  <br/> |Unique identifier for the task.  <br/> |
|TimeByDay  <br/> |A primary key that identifies the day along a timeline. The granularity is in days only.  <br/> |
|TaskBaselineCost  <br/> |The total planned cost for a task. The baseline cost is also known as budget at completion (BAC) for earned value.  <br/> |
|TaskBaselineFixedCost  <br/> |A set task cost that is projected in the baseline and that remains constant regardless of the task duration or the work performed by a resource.  <br/> |
|TaskBaselineWork  <br/> |The total planned hours that are scheduled for a task in the baseline projection.  <br/> |
|TaskBaselineBudgetCost  <br/> |The cost of the planned, budgeted amount of work on a task.  <br/> |
|TaskBaselineBudgetWork  <br/> |The planned, budgeted amount of work on a task.  <br/> |
|TaskBaselineModifiedDate  <br/> |The date and time the task was last updated.  <br/> |
|FiscalPeriodUID  <br/> |Unique identifier for the fiscal period.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
   
### Reporting_TaskTimephased
<a name="TaskTimephased"> </a>

Reporting_TaskTimephased contains the properties that define the reporting data for task timephased data in the ProjectData service. It has the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|SiteId  <br/> |Unique identifier for the PWA site.  <br/> |
|TaskUID  <br/> |Unique identifier for the task.  <br/> |
|TimeByDay  <br/> |A primary key that identifies a day along a timeline. The granularity is in days only.  <br/> |
|T.FiscalPeriodUID  <br/> |The identifier of the fiscal period.  <br/> |
|ProjectUID  <br/> |Unique identifier for the project.  <br/> |
|TaskIsActive  <br/> |True if the task is active.  <br/> |
|TaskIsProjectSummary  <br/> |True if the task is a project summary task.  <br/> |
|TaskCost  <br/> |The total scheduled or projected cost for a task.  <br/> |
|TaskActualCost  <br/> |The costs incurred for work that is already performed by all resources on a task, along with any other recorded costs.  <br/> |
|TaskWork  <br/> |The total time that is scheduled for a task for all assigned resources.  <br/> |
|TaskOvertimeWork  <br/> |The amount of overtime work that is scheduled to be performed by all resources that are assigned to a task.  <br/> |
|TaskActualWork  <br/> |The actual work that is already performed by resources on a task, usually expressed as percent complete.  <br/> |
|TaskBudgetCost  <br/> |The scheduled costs for a task.  <br/> |
|TaskBudgetWork  <br/> |The scheduled work for a task.  <br/> |
|TaskResourcePlanWork  <br/> |The total time that is scheduled for the task in the resource plan.  <br/> |
|TaskModifiedDate  <br/> |Date and time the task was last modified.  <br/> |
|TaskName  <br/> |Name of the task.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
   
## Project XML files
<a name="projectspec"> </a>

The method defined in [Export user data from Project Online](export-user-data-from-project-online.md) will give you two project-specific files for the each user project, but saved to .xml format. You get two .xml files for each project: 
  
- **\<ProjectName\>_\<ProjectID\>_draft.xml**: The project file from the Draft schema saved in .XML format. 
    
- **\<ProjectName\>_\<ProjectID\>_published.xml**: The project file from the Published schema saved in .XML format. 
    
See the [Project XML Data Interchange Schema Reference](/office-project/xml-data-interchange/project-xml-data-interchange-schema-reference) to understand the Project XML data contained in these files. 
  
## Project-specific Metadata files
<a name="ProjSpecMeta"> </a>

The method defined in [Export user data from Project Online](export-user-data-from-project-online.md) will also provide you three project-specific files that give metadata about each individual project. You receive one from each of the following schemas: 
  
- [Project metadata file from the Reporting schema](project-online-and-project-server-export-data-definitions.md#MetaRep)
    
- [Project metadata file from the Draft schema](project-online-and-project-server-export-data-definitions.md#Metadraft)
    
- [Project metadata file from the Published schema](project-online-and-project-server-export-data-definitions.md#MetaPub)
    
### Project metadata file from the Reporting schema
<a name="MetaRep"> </a>

The Project metadata file for a project will have the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectUID  <br/> |The unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|ProjectAuthorName  <br/> |The name of the author of the project.  <br/> |
|ProjectOwnerResourceUID  <br/> |Resource GUID of the project owner.  <br/> |
|ProjectManagerName  <br/> |Name of the project manager.  <br/> |
|ProjectType  <br/> |The enumerated value that represents the type of a project.  <br/> |
|ProjectStartDate  <br/> |The project start date and time.  <br/> |
|ProjectFinishDate  <br/> |The scheduled finish date and time of a project.  <br/> |
|ProjectStatusDate  <br/> |The status date and time of a project.  <br/> |
|ProjectWorkspaceInternalHRef  <br/> |The URL of the project site.  <br/> |
|ProjectWbsIsStale  <br/> |True if the work breakdown structure (task outline hierarchy) is not up to date.  <br/> |
|ProjectEarnedValueIsStale  <br/> |True if earned value fields are out of date.  <br/> |
|ProjectRollupsAreStale  <br/> |True if the summary task data is out of date.  <br/> |
|ProjectHierarchyNotSynchronized  <br/> |The master - subproject hierarchy is not synchronized.  <br/> |
|ProjectCalculationsAreStale  <br/> |True if project schedule calculations are not up to date.  <br/> |
|ProjectGhostTaskAreStale  <br/> |True if ghost tasks are out of date. Ghost tasks are placeholders for cross-project links.  <br/> |
|ProjectCurrency  <br/> |The project currency character code.  <br/> |
|ProjectCategoryName  <br/> |The name of a project category.  <br/> |
|ProjectCompanyName  <br/> |The name of the company for a project.  <br/> |
|ProjectKeywords  <br/> |The keywords for a project.  <br/> |
|ProjectSubject  <br/> |The subject of a project.  <br/> |
|ProjectTitle  <br/> |Name of the project.  <br/> |
|ProjectVisibilityMode  <br/> |Is this created from SharePoint task list.  <br/> |
|ResourcePlanUtilizationType  <br/> |Value that represents the utilization type of a resource plan.  <br/> |
|ResourcePlanUtilizationDate  <br/> |The start date and time for use of the resource plan.  <br/> |
|ProjectDescription  <br/> |Description of the project.  <br/> |
|EnterpriseProjectTypeName  <br/> |The name of an enterprise project type.  <br/> |
|ProjectCreatedDate  <br/> |The date that a project was created.  <br/> |
|ProjectModifiedDate  <br/> |The date and time that a project was last modified.  <br/> |
|ProjectCalendarDuration  <br/> |The total span of active working time for all tasks in a project, based on the project calendar that is specified in the Project Information dialog box.  <br/> |
|ProjectIdentifier  <br/> |Human readable identifier for the project. This identifier is configured in the EPT.  <br/> |
|ProjectLastPublishedDate  <br/> |The date of last publish  <br/> |
   
The project can have a collection of **CustomFields** objects, with the following properties: 
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|CustomFieldValueUID  <br/> |Unique identifier for the custom field value.  <br/> |
|CustomFieldTypeUID  <br/> |Unique identifier for the custom field type.  <br/> |
|CustomFieldName  <br/> |Name of the custom field.  <br/> |
|ResourceUID  <br/> |Unique identifier for the resource.  <br/> |
|CFValue  <br/> |Custom field value.  <br/> |
   
### Project metadata file from the Draft schema
<a name="Metadraft"> </a>

The Project metadata file for a project in the Draft schema will have the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectUID  <br/> |The unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|ProjectAuthorName  <br/> |The name of the author of the project.  <br/> |
|ProjectActualCost  <br/> |The costs incurred for work that has already been performed on a project.  <br/> |
|ProjectCategoryName  <br/> |The name of a project category.  <br/> |
|ProjectCompanyName  <br/> |The name of the company for a project.  <br/> |
|ProjectCritcalSlackLimit  <br/> |The number of days past its end date that a task can go before Project marks that task as a critical task.  <br/> |
|ProjectCurrencyDigits  <br/> |The number of decimal digits in currency values.  <br/> |
|ProjectCurrencyPosition  <br/> |The placement of the currency symbol in relation to the currency value.  <br/> |
|ProjectCurrencySymbol  <br/> |The project currency symbol.  <br/> |
|ProjectCurrencyCode  <br/> |The currency code of the project, as defined in ISO 4217.  <br/> |
|ProjectIsNewTasksEffortDriven  <br/> |Specifies whether new tasks are effort driven.  <br/> |
|ProjectCurrentDate  <br/> |The current date for the project.  <br/> |
|ProjectDefaultFinishTime  <br/> |The default finish time for all new tasks.  <br/> |
|ProjectDefaultFixedCostAccrual  <br/> |A value that indicates which default fixed cost accrual method to use on new tasks.  <br/> |
|ProjectMinutesPerDay  <br/> |The default number of minutes per day.  <br/> |
|ProjectMinutesPerWeek  <br/> |The default number of minutes per week.  <br/> |
|ProjectDefaultOvertimeRate  <br/> |Default overtime rate for local resources.  <br/> |
|ProjectDefaultStandardRate  <br/> |Default standard rate for local resources.  <br/> |
|ProjectDefaultStartTime  <br/> |The default start time for all new tasks.  <br/> |
|ProjectDefaultTaskType  <br/> |The default type for all tasks in the project.  <br/> |
|ProjectDurationFormat  <br/> |The default format for work duration.  <br/> |
|ProjectFinishDate  <br/> |The scheduled finish date and time of a project.  <br/> |
|ProjectTasksHonorConstraints  <br/> |Indicates whether Project schedules tasks according to their constraint date.  <br/> |
|ProjectKeywords  <br/> |The keywords for a project.  <br/> |
|ProjectLastSavedDate  <br/> |The date the project was last saved.  <br/> |
|ProjectManagerName  <br/> |The name of a project manager.  <br/> |
|ProjectMultipleCriticalPaths  <br/> |Indicates whether Project calculates and displays a critical path for each independent network of tasks within a project.  <br/> |
|ProjectPoolAttachedTo  <br/> |The name of the project that shares resources with this project.  <br/> |
|ProjectCreatedDate  <br/> |The date that a project was created.  <br/> |
|ProjectIsResourcePool  <br/> |Indicates if the project is being used as resource pool.  <br/> |
|ProjectScheduledFromStart  <br/> |Indicates whether a project is scheduled from Start Date or Finish Date.  <br/> |
|ProjectSplitTasksInProgress  <br/> |Indicated whether to Allow rescheding of remaining duration and work when a task slips or reports progress ahead of schedule.  <br/> |
|ProjectSpreadActualCostsToStatusDate  <br/> |Indicates whether actual costs are spread to the status date.  <br/> |
|ProjectSpreadPercentCompleteToStatus  <br/> |Indicates whether percent complete is spread to the status date.  <br/> |
|ProjectStartDate  <br/> |The project start date and time.  <br/> |
|ProjectStatusDate  <br/> |The status date and time of a project.  <br/> |
|ProjectSubject  <br/> |The subject of a project.  <br/> |
|ProjectTitle  <br/> |The title of a project.  <br/> |
|ProjectCalculateActualCosts  <br/> |Indicates whether Project should automatically calculate actual costs.  <br/> |
|ProjectWorkEntryFormat  <br/> |The default format for all work durations in the project.  <br/> |
|ProjectCalculatesSubTasksAsSummary  <br/> |Indicates whether Project calculates sub-tasks as summary tasks.  <br/> |
|ProjectDaysPerMonth  <br/> |The default number of working days per month.  <br/> |
|ProjectDefaultEstimatedDuration  <br/> |A value that indicates whether new tasks have estimated durations.  <br/> |
|ProjectShowEstimatedDurations  <br/> |A value that indicates whether a question mark is displayed after an estimated duration for a task.  <br/> |
|ProjectExpandTimephased  <br/> |Indicates whether Project saves timephased data in a readable or binary format when saved to a database.  <br/> |
|ProjectExternalEdited  <br/> |Indicates whether the project was edited externally.  <br/> |
|ProjectReadCount  <br/> |Indicates the number of users who have one or more tables open as read-only.  <br/> |
|ProjectType  <br/> |The enumerated value that represents the type of a project.  <br/> |
|ProjectCheckedOutBy  <br/> |Name of the user who checked out the project.  <br/> |
|ProjectCheckOutDate  <br/> |The project checked out date.  <br/> |
|ProjectPath  <br/> |The project path.  <br/> |
|ProjectActualsSyncProtectedActuals  <br/> |A value that indicates whether the project actuals are synchronized with the protected actuals.  <br/> |
|ProjectIsAdministrative  <br/> |Indicates whether the project is an administrative project.  <br/> |
|ProjectTimestamp  <br/> |The timestamp on the project.  <br/> |
|ProjectDescription  <br/> |Description of the project.  <br/> |
|ProjectLocalPath  <br/> |The project local path.  <br/> |
|ProjectWebPath  <br/> |The project web path.  <br/> |
|ProjectOwnerUID  <br/> |The GUID of a project owner.  <br/> |
|ProjectDataSourceNameID  <br/> |The identifier of the project data source name.  <br/> |
|ProjectDelegateAllowed  <br/> |Indicates if project delegate is allowed.  <br/> |
|ProjectIsNonWorking  <br/> |Indicates if project is non working.  <br/> |
|ProjectScope  <br/> |The project scope.  <br/> |
|ProjectIsConsolidatedProject  <br/> |Indicates if it's a consolidated project.  <br/> |
|ProjectResourceCanDecline  <br/> |Indicates if resource can decline.  <br/> |
|ProjectTrackingMode  <br/> |The default tracking method for all assignments in the project.  <br/> |
|ProjectLastPublishedDate  <br/> |The date of last project publish.  <br/> |
|LegacyProjectType  <br/> |The legacy project type.  <br/> |
|ProjectOptionDefaultStartTime  <br/> |Default start time of a working day.  <br/> |
|ProjectOptionDefaultFinishTime  <br/> |Default end time of a working day.  <br/> |
|ProjectSiteName  <br/> |The name of the project site.  <br/> |
|ProjectSiteServerUID  <br/> |The server ID of the project site..  <br/> |
|IssueListName  <br/> |The name of the project issue list.  <br/> |
|RiskListName  <br/> |The name of the project risk list.  <br/> |
|TotalDocumentCount  <br/> |Count of documents for the project.  <br/> |
|ProjectActiveIssueCount  <br/> |Count of active issues for the project.  <br/> |
|ProjectActiveRiskCount  <br/> |Count of active risks for the project.  <br/> |
|ProjectAdminRoleId  <br/> |The identifier for the project admin role.  <br/> |
|ProjectManagerRoleId  <br/> |The identifier for the project manager role.  <br/> |
|ProjectTeamMemberRoleId  <br/> |The identifier for the project team member role.  <br/> |
|ProjectReaderRoleId  <br/> |The identifier for the project reader role.  <br/> |
|ProjectProposalWorkflowInstanceId  <br/> |The identifier of the project workflow instance.  <br/> |
|ProjectIsAdminProjectLegacy  <br/> |Indicates whether the project is an administrative project.  <br/> |
|ProjectCalendarId  <br/> |The ID for the calendar used by the project.  <br/> |
|ProjectClientVersionNumber  <br/> |The client version for the project.  <br/> |
|ProjectVersion  <br/> |The version of the project.  <br/> |
|ProjectProgramUID  <br/> |The identifier for the project program.  <br/> |
|ProjectSessionUID  <br/> |The identifier for the project session.  <br/> |
|ProjectSessionDescription  <br/> |The project session descriptor.  <br/> |
|ProjectIsDeleted  <br/> |Indicates whether the project is deleted.  <br/> |
|ProjectBaselineCalendarId  <br/> |The identifier of the project baseline calendar.  <br/> |
|ProjectWBSPrefix  <br/> |The work breakdown structure prefix.  <br/> |
|ProjectNewTasksStartOnCurrentDate  <br/> |A value that indicates whether new tasks start on current date.  <br/> |
|ProjectIsNewTasksManual  <br/> |A value that indicates whether new tasks are manually scheduled.  <br/> |
|ProjectSummaryTaskId  <br/> |The task Id of the project summary task.  <br/> |
|ProjectModifiedDate  <br/> |The date and time that a project was last modified.  <br/> |
|SharepointIdeaListWebId  <br/> |The Ideas List SharePoint Web ID.  <br/> |
|SharepointIdeaListId  <br/> |The Ideas List SharePoint List ID.  <br/> |
|SharepointIdeaItemId  <br/> |The Ideas List SharePoint List Item ID.  <br/> |
|ProjectVisibilityMode  <br/> |Specifies whether the project site was created from SharePoint task list.  <br/> |
|ProjectIsProjectSiteRemoved  <br/> |Specifies whether the project site was removed.  <br/> |
|ProjectUtilizationType  <br/> |Value that represents the utilization type of a project.  <br/> |
|ProjectUtilizationDate  <br/> |The start date and time for use of the project.  <br/> |
|ProjectIdentifier  <br/> |Human readable identifier for the project. This identifier is configured in the EPT.  <br/> |
   
### Project metadata file from the Published schema
<a name="MetaPub"> </a>

The Project metadata file for a project in the Published schema will have the following properties:
  

|**Property** <br/> |**Description** <br/> |
|:-----|:-----|
|ProjectUID  <br/> |The unique identifier for the project.  <br/> |
|ProjectName  <br/> |Name of the project.  <br/> |
|ProjectAuthorName  <br/> |The name of the author of the project.  <br/> |
|ProjectActualCost  <br/> |The costs incurred for work that has already been performed on a project.  <br/> |
|ProjectCategoryName  <br/> |The name of a project category.  <br/> |
|ProjectCompanyName  <br/> |The name of the company for a project.  <br/> |
|ProjectCritcalSlackLimit  <br/> |The number of days past its end date that a task can go before Project marks that task as a critical task.  <br/> |
|ProjectCurrencyDigits  <br/> |The number of decimal digits in currency values.  <br/> |
|ProjectCurrencyPosition  <br/> |The placement of the currency symbol in relation to the currency value.  <br/> |
|ProjectCurrencySymbol  <br/> |The project currency symbol.  <br/> |
|ProjectCurrencyCode  <br/> |The currency code of the project, as defined in ISO 4217.  <br/> |
|ProjectIsNewTasksEffortDriven  <br/> |Specifies whether new tasks are effort driven.  <br/> |
|ProjectCurrentDate  <br/> |The current date for the project.  <br/> |
|ProjectDefaultFinishTime  <br/> |The default finish time for all new tasks.  <br/> |
|ProjectDefaultFixedCostAccrual  <br/> |A value that indicates which default fixed cost accrual method to use on new tasks.  <br/> |
|ProjectMinutesPerDay  <br/> |The default number of minutes per day.  <br/> |
|ProjectMinutesPerWeek  <br/> |The default number of minutes per week.  <br/> |
|ProjectDefaultOvertimeRate  <br/> |Default overtime rate for local resources.  <br/> |
|ProjectDefaultStandardRate  <br/> |Default standard rate for local resources.  <br/> |
|ProjectDefaultStartTime  <br/> |The default start time for all new tasks.  <br/> |
|ProjectDefaultTaskType  <br/> |The default type for all tasks in the project.  <br/> |
|ProjectDurationFormat  <br/> |The default format for work duration.  <br/> |
|ProjectFinishDate  <br/> |The scheduled finish date and time of a project.  <br/> |
|ProjectTasksHonorConstraints  <br/> |Indicates whether Project schedules tasks according to their constraint date.  <br/> |
|ProjectKeywords  <br/> |The keywords for a project.  <br/> |
|ProjectLastSavedDate  <br/> |The date the project was last saved.  <br/> |
|ProjectManagerName  <br/> |The name of a project manager.  <br/> |
|ProjectMultipleCriticalPaths  <br/> |Indicates whether Project calculates and displays a critical path for each independent network of tasks within a project.  <br/> |
|ProjectPoolAttachedTo  <br/> |The name of the project that shares resources with this project.  <br/> |
|ProjectCreatedDate  <br/> |The date that a project was created.  <br/> |
|ProjectIsResourcePool  <br/> |Indicates if the project is being used as resource pool.  <br/> |
|ProjectScheduledFromStart  <br/> |Indicates whether a project is scheduled from Start Date or Finish Date.  <br/> |
|ProjectSplitTasksInProgress  <br/> |Indicated whether to Allow rescheding of remaining duration and work when a task slips or reports progress ahead of schedule.  <br/> |
|ProjectSpreadActualCostsToStatusDate  <br/> |Indicates whether actual costs are spread to the status date.  <br/> |
|ProjectSpreadPercentCompleteToStatus  <br/> |Indicates whether percent complete is spread to the status date.  <br/> |
|ProjectStartDate  <br/> |The project start date and time.  <br/> |
|ProjectStatusDate  <br/> |The status date and time of a project.  <br/> |
|ProjectSubject  <br/> |The subject of a project.  <br/> |
|ProjectTitle  <br/> |The title of a project.  <br/> |
|ProjectCalculateActualCosts  <br/> |Indicates whether Project should automatically calculate actual costs.  <br/> |
|ProjectWorkEntryFormat  <br/> |The default format for all work durations in the project.  <br/> |
|ProjectCalculatesSubTasksAsSummary  <br/> |Indicates whether Project calculates sub-tasks as summary tasks.  <br/> |
|ProjectDaysPerMonth  <br/> |The default number of working days per month.  <br/> |
|ProjectDefaultEstimatedDuration  <br/> |A value that indicates whether new tasks have estimated durations.  <br/> |
|ProjectShowEstimatedDurations  <br/> |A value that indicates whether a question mark is displayed after an estimated duration for a task.  <br/> |
|ProjectExpandTimephased  <br/> |Indicates whether Project saves timephased data in a readable or binary format when saved to a database.  <br/> |
|ProjectExternalEdited  <br/> |Indicates whether the project was edited externally.  <br/> |
|ProjectReadCount  <br/> |Indicates the number of users who have one or more tables open as read-only.  <br/> |
|ProjectType  <br/> |The enumerated value that represents the type of a project.  <br/> |
|ProjectCheckedOutBy  <br/> |Name of the user who checked out the project.  <br/> |
|ProjectCheckOutDate  <br/> |The project checked out date.  <br/> |
|ProjectPath  <br/> |The project path.  <br/> |
|ProjectActualsSyncProtectedActuals  <br/> |A value that indicates whether the project actuals are synchronized with the protected actuals.  <br/> |
|ProjectIsAdministrative  <br/> |Indicates whether the project is an administrative project.  <br/> |
|ProjectTimestamp  <br/> |The timestamp on the project.  <br/> |
|ProjectDescription  <br/> |Description of the project.  <br/> |
|ProjectLocalPath  <br/> |The project local path.  <br/> |
|ProjectWebPath  <br/> |The project web path.  <br/> |
|ProjectOwnerUID  <br/> |The GUID of a project owner.  <br/> |
|ProjectDataSourceNameID  <br/> |The identifier of the project data source name.  <br/> |
|ProjectDelegateAllowed  <br/> |Indicates if project delegate is allowed.  <br/> |
|ProjectIsNonWorking  <br/> |Indicates if project is non working.  <br/> |
|ProjectScope  <br/> |The project scope.  <br/> |
|ProjectIsConsolidatedProject  <br/> |Indicates if it's a consolidated project.  <br/> |
|ProjectResourceCanDecline  <br/> |Indicates if resource can decline.  <br/> |
|ProjectTrackingMode  <br/> |The default tracking method for all assignments in the project.  <br/> |
|ProjectLastPublishedDate  <br/> |The date of last project publish.  <br/> |
|LegacyProjectType  <br/> |The legacy project type.  <br/> |
|ProjectOptionDefaultStartTime  <br/> |Default start time of a working day.  <br/> |
|ProjectOptionDefaultFinishTime  <br/> |Default end time of a working day.  <br/> |
|ProjectSiteName  <br/> |The name of the project site.  <br/> |
|ProjectSiteServerUID  <br/> |The server ID of the project site..  <br/> |
|IssueListName  <br/> |The name of the project issue list.  <br/> |
|RiskListName  <br/> |The name of the project risk list.  <br/> |
|TotalDocumentCount  <br/> |Count of documents for the project.  <br/> |
|ProjectActiveIssueCount  <br/> |Count of active issues for the project.  <br/> |
|ProjectActiveRiskCount  <br/> |Count of active risks for the project.  <br/> |
|ProjectAdminRoleId  <br/> |The identifier for the project admin role.  <br/> |
|ProjectManagerRoleId  <br/> |The identifier for the project manager role.  <br/> |
|ProjectTeamMemberRoleId  <br/> |The identifier for the project team member role.  <br/> |
|ProjectReaderRoleId  <br/> |The identifier for the project reader role.  <br/> |
|ProjectProposalWorkflowInstanceId  <br/> |The identifier of the project workflow instance.  <br/> |
|ProjectIsAdminProjectLegacy  <br/> |Indicates whether the project is an administrative project.  <br/> |
|ProjectCalendarId  <br/> |The ID for the calendar used by the project.  <br/> |
|ProjectClientVersionNumber  <br/> |The client version for the project.  <br/> |
|ProjectVersion  <br/> |The version of the project.  <br/> |
|ProjectProgramUID  <br/> |The identifier for the project program.  <br/> |
|ProjectSessionUID  <br/> |The identifier for the project session.  <br/> |
|ProjectSessionDescription  <br/> |The project session descriptor.  <br/> |
|ProjectIsDeleted  <br/> |Indicates whether the project is deleted.  <br/> |
|ProjectBaselineCalendarId  <br/> |The identifier of the project baseline calendar.  <br/> |
|ProjectWBSPrefix  <br/> |The project work breakdown prefix.  <br/> |
|ProjectNewTasksStartOnCurrentDate  <br/> |A value that indicates whether new tasks start on current date.  <br/> |
|ProjectIsNewTasksManual  <br/> |A value that indicates whether new tasks are manually scheduled.  <br/> |
|ProjectSummaryTaskId  <br/> |The task Id of the project summary task.  <br/> |
|ProjectModifiedDate  <br/> |The date and time that a project was last modified.  <br/> |
|SharepointIdeaListWebId  <br/> |The Ideas List SharePoint Web ID.  <br/> |
|SharepointIdeaListId  <br/> |The Ideas List SharePoint List ID.  <br/> |
|SharepointIdeaItemId  <br/> |The Ideas List SharePoint List Item ID.  <br/> |
|ProjectVisibilityMode  <br/> |Specifies whether the project site was created from SharePoint task list.  <br/> |
|ProjectIsProjectSiteRemoved  <br/> |Specifies whether the project site was removed.  <br/> |
|ProjectUtilizationType  <br/> |Value that represents the utilization type of a resource plan.  <br/> |
|ProjectUtilizationDate  <br/> |The start date and time for use of the project.  <br/> |
|ProjectIdentifier  <br/> |Human readable identifier for the project. This identifier is configured in the EPT.  <br/> |
|ProjectPublishedReportingTimephasedMode  <br/> |The sync mode for timephased data in reporting.  <br/> |
|ProjectPublishedReportingTimephasedFirstDayOfWeek  <br/> |The first day of the week for timephased reporting.  <br/> |
|ProjectPublishedReportingTimephasedFirstWeekOfYear  <br/> |The first week of the year for timephased reporting.  <br/> |
|ProjectFiscalPeriodMaxModDate  <br/> |The fiscal period max modified date.  <br/> |
