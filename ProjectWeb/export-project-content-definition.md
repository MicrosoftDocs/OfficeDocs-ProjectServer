---

title: "Export Content Definition"
ms.author: nadinmerali
author: nadinmerali
manager: pamgreen
ms.date: 2/17/2023
audience: admin
ms.topic: article
ms.service: project-web

ms.localizationpriority: medium
ms.assetid: 27f3838d-3dbe-4b98-80dc-df55f851154d
description: "Understand the Project export file structure."

---

# Export Project Content Definition

Page describes the output format and definition of JSON when using the ExportProjectContent tool.

| Property name                                                                     | Type       | Description                                         |
| --------------------------------------------------------------------------------- | ---------- | --------------------------------------------------- |
| /project                                                                          | JSONObject | Project level values                                |
| [/project/fields](#project-level-properties)                                      | JSONArray  | Definition of project level properties              |
| /project/assignments                                                              | JSONArray  | List of assignments and their values                |
| [/project/assignments/fields](#assignment-properties)                             | JSONArray  | Definition of assignment properties                 |
| /project/attachments                                                              | JSONArray  | List of attachments and their values                |
| [/project/attachments/fields](#attachment-properties)                             | JSONArray  | Definition of attachment properties                 |
| /project/buckets                                                                  | JSONArray  | List of buckets and their values                    |
| [/project/buckets/fields](#bucket-properties)                                     | JSONArray  | Definition of bucket properties                     |
| /project/calendars                                                                | JSONArray  | List of calendar and their values                   |
| [/project/calendars/fields](#calendar-properties)                                 | JSONArray  | Definition of calendar properties                   |
| /project/checklistItems                                                           | JSONArray  | List of checklist items and their values            |
| [/project/checklistItems/fields](#checklist-properties)                           | JSONArray  | Definition of checklist item properties             |
| /project/conditionalColoringRules                                                 | JSONArray  | List of conditional coloring rules and their values |
| [/project/conditionalColoringRules/fields](#conditional-coloring-rule-properties) | JSONArray  | Definition of conditional coloring rule properties  |
| /project/conversations                                                            | JSONArray  | List of conversation and their values               |
| [/project/conversations/fields](#conversations-properties)                        | JSONArray  | Definition of conversation properties               |
| /project/goalAssociations                                                         | JSONArray  | List of goal asociations and their values              |
| [/project/goalAssociations/fields](#goal-associations-properties)                 | JSONArray  | Definition of goal asociations          |
| /project/goals                                                                    | JSONArray  | List of goals and their values               |
| [/project/goals/fields](#goals-properties)                                        | JSONArray  | Definition of goal properties               |
| /project/labelassociations                                                        | JSONArray  | List of label associations and their values         |
| [/project/labelassociations/fields](#label-association-properties)                | JSONArray  | Definition of label association properties          |
| /project/labels                                                                   | JSONArray  | List of labels and their values                     |
| [/project/labels/fields](#label-properties)                                       | JSONArray  | Definition of label properties                      |
| /project/links                                                                    | JSONArray  | List of links and their values                      |
| [/project/links/fields](#links-properties)                                        | JSONArray  | Definition of link properties                       |
| /project/resources                                                                | JSONArray  | List of resources and their values                  |
| [/project/resources/fields](#resource-properties)                                 | JSONArray  | Definition of resource properties                   |
| /project/sprints                                                                  | JSONArray  | List of sprints and their values                    |
| [/project/sprints/fields](#sprint-properties)                                     | JSONArray  | Definition of sprint properties                     |
| /project/tasks                                                                    | JSONArray  | List of tasks and their values                      |
| [/project/tasks/fields](#task-properties)                                         | JSONArray  | Definition of task properties                       |
| /project/views/grid                                                               | JSONArray  | List of grid view properties                        |
| [/project/views/grid/fields](#view-properties)                                    | JSONArray  | Definition of grid view and their values            |


## Project Level Properties

Reference /project/fields

| Property name            | Type           | Description                                                          | Enumeration Values |
| ------------------------ | -------------- | -------------------------------------------------------------------- | ------------------ |
| projectStart             | datetime       | The start date of the project.                                       |                    |
| name                     | string         | Name of the project.                                                 |                    |
| calendarId               | guid           | Dataverse Calendar Id used for the project.                          |                    |
| durationInDays           | double         | The duration of the project (days).                                  |                    |
| projectManagerId         | guid           | Dataverse Project Team Member Id of the project manager.             |                    |
| workTemplateId           | guid           | Dataverse Work Template Id used to create the project calendar.      |                    |
| timezoneOffset           | timezoneOffset | Project's timezone offset in +/-HH:MM:SS format.                     |                    |
| timezoneName             | string         | Project's timezone name.                                             |                    |
| projectManagerResourceId | guid           | Dataverse Bookable Resource Id of the project manager.               |                    |
| officeGroupId            | guid           | Azure Active Directory Microsoft 365 Group Id linked to the project. |                    |
| projectState             | enum           | State of the project.                                                | Active, Inactive    |
| projectManagerAadId      | guid           | Azure Active Directory user Id of the project manager.               |                    |
| hasCustomCalendar        | bool           | Indicates if the project has a custom calendar.                      |                    |
| defaultSprintCreated     | bool           | Has the default sprint been created.                                 |                    |
| ignoreResourceCalendars  | bool           | Scheduling uses the project calendar over resource calendars.        |                    |
| work                     | double         | Total work for the project in seconds.                               |                    |
| actualWork               | double         | Completed work for the project in seconds.                           |                    |
| remainingWork            | double         | Remaining work for the project in seconds.                           |                    |
| duration                 | duration       | The duration of the project in seconds.                              |                    |
| percentComplete          | percent        | The percentage of the project duration completed.                    |                    |
| percentWorkComplete      | percent        | The percentage of the project work completed.                        |                    |
| earliestTaskStart        | datetime       | Earliest task start date.                                            |                    |
| latestTaskFinish         | datetime       | Latest task finish date.                                             |                    |

## Assignment Properties

Reference /project/assignments/fields.
They're part of a task record.

| Property name        | Type     | Description                                                                                                                                                                                                                           |
| -------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| units                | double   | The number of units for which a resource is assigned to a task, expressed as a percentage, assuming a resource's MaxUnits value is 100%.                                                                                              |
| work                 | double   | The total amount of work scheduled to be performed by a resource on a task in seconds.                                                                                                                                                |
| actualWork           | double   | Amount of work that has already been done by a resource on a task in seconds.                                                                                                                                                         |
| remainingWork        | double   | The amount of time required by a resource assigned to a task to complete an assignment in seconds.                                                                                                                                    |
| start                | datetime | The date and time that an assigned resource is scheduled to begin working on a task.                                                                                                                                                  |
| finish               | datetime | The date and time this assignment is scheduled to be completed.                                                                                                                                                                       |
| actualStart          | datetime | Date and time that an assignment actually began.                                                                                                                                                                                      |
| actualFinish         | datetime | Date and time when an assignment was actually completed.                                                                                                                                                                              |
| resume               | datetime | The date that the assignment was resumed.                                                                                                                                                                                             |
| delay                | duration | The amount of time a resource is to wait after the task start date before starting work on an assignment in seconds.                                                                                                                  |
| percentWorkComplete  | percent  | Current status of an assignment, expressed as the percentage of the assignment's work that has been completed.                                                                                                                        |
| remainingWorkContour | [contour](#contour-structure)  | Indicates how remaining work is to be distributed across the duration of the assignment. Represented as a start date and arrays of offset, duration, and work for each segment. Please see for more information on Contour structure. |
| actualWorkContour    | [contour](#contour-structure)  | Indicates how actual work is to be distributed across the duration of the assignment. Represented as a start date and arrays of offset, duration, and work for each segment. Please see for more information on Contour structure.    |
| overallocated        | bool     | Indicates whether a resource is assigned to more work on a specific task than can be done within the resource's normal working capacity.                                                                                              |
| stop                 | datetime | The date the assignment was stopped.                                                                                                                                                                                                  |
| taskId               | guid     | Dataverse Project Task Id for this assignment.                                                                                                                                                                                        |
| resourceId           | guid     | Dataverse Project Team Member Id.                                                                                                                                                                                                     |
| totalWorkContour     | [contour](#contour-structure)  | Indicates how total work is to be distributed across the duration of the assignment. Represented as a start date and arrays of offset, duration, and work for each segment. Please see for more information on Contour structure.     |

## Contour Structure

| Property name | Type      | Description                                                                                    |
| ------------- | --------- | ---------------------------------------------------------------------------------------------- |
| start         | datetime  | Start date of the contour.                                                                     |
| offsets       | JSONArray | The number of seconds to add to the start of the contour to indicate the start of the segment. |
| durations     | JSONArray | Duration in seconds of each segment.                                                           |
| work          | JSONArray | Work in seconds of each segment.                                                               |

Example

```json
        "remainingWorkContour": {
            "start": "2022-12-08T09:00:00Z",
            "offsets": [ 0, 54000 ],
            "durations": [ 54000, 3600 ],
            "work": [ 27000.0, 1800.0 ]
			}
```

Segment X  
- Start = "start" + X offset in seconds  
- Duration = duration of segment X in seconds  
- Work = work of segment X in seconds

The contour starts on 2023-02-13T09:00:00Z  
- Segment 1:  
	- Start = 2022-12-08T09:00:00Z + 0 seconds -> 2022-12-08T09:00:00Z  
	- Duration = 54000 seconds -> 900 Minutes -> 15 hours is the length of the segment  
	- Work = 27000 second -> 450 Minutes -> 7.5 hours fow of in the segment  
- Segment 2:  
	- Start = 2023-02-13T18:00:00Z + 54000 seconds (15 hours) -> 2022-12-09T00:00:00Z  
	- Duration = 3600 seconds -> 60 Minutes -> 1 hours is the length of the segment  
	- Work = 1800 seconds -> 30 Minutes -> 0.5 hours of work in the segment

## Attachment Properties

Reference /project/attachments/fields.

| Property name | Type   | Description                                               | Enumeration Values                                                  |
| ------------- | ------ | --------------------------------------------------------- | ------------------------------------------------------------------- |
| taskId        | guid   | Dataverse Project Task Id.                                |                                                                     |
| name          | string | Alias for the attachment.                                 |                                                                     |
| uri           | string | Location where attachment is stored.                      |                                                                     |
| type          | enum   | Type of the link.                                         | Word, Excel, PowerPoint, OneNote, Project, Visio, Pdf, ExternalLink, Other |
| showOnCard    | bool   | Indicates if the link is shown on the card in board view. |                                                                     |

## Bucket Properties

Reference /project/buckets/fields

| Property name | Type    | Description                         |
| ------------- | ------- | ----------------------------------- |
| order         | integer | Display order of bucket in Project. |
| name          | string  | Name of the bucket.                 |
| color         | integer | Color index assigned to the bucket. |

## Calendar Properties

Reference /project/calendar/fields

| Property name  | Type           | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| -------------- | -------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| name           | string         | Name of the calendar.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| data           | calendarData   | Describes a calendar by defining the times when a resource can work. defaultWorkWeek has the default working times for each day of the week. overrideWorkWeeks is a collection of workweek definitions which override defaultWorkWeek along with when that override is effective. exceptions is an array of day level overrides along with when that exception is effective. exceptions take priority over overrideWorkWeeks, which take priority over defaultWorkWeek. |
| baseCalendarId | guid           | Dataverse Calendar Id for the base calendar. Empty guid means there is no base calendar.                                                                                                                                                                                                                                                                                                                                                                                |
| timezoneOffset | timezoneOffset | Offset of the timezone in +/-HH:MM:SS format.                                                                                                                                                                                                                                                                                                                                                                                                                           |
| timezoneName   | string         | Name of the timezone.                                                                                                                                                                                                                                                                                                                                                                                                                                                   |

## Checklist Properties

Reference /project/checklistItems/fields

| Property name | Type   | Description                                               |
| ------------- | ------ | --------------------------------------------------------- |
| taskId        | guid   | Dataverse Project Task Id.                                |
| name          | string | Name of the checklist item.                               |
| completed     | bool   | Indicates if the item is checked off.                     |
| order         | double | Display order of the checklist item within the name task. |

## Conditional Coloring Rule Properties

Reference /project/conditionalColoringRules/fields

| Property name | Type             | Description                                                                               |
| ------------- | ---------------- | ----------------------------------------------------------------------------------------- |
| order         | integer          | Rule order.                                                                               |
| expression    | conditionalRules | A formal description of the rule used to color field cells.                               |
| color         | integer          | Color index set on this field on tasks gridColor property if this rule evaluates to true. |
| columnId      | column           | The column the color will be applied to when the expression is true.                      |

## Conversations Properties

Reference /project/conversations/fields

| Property name       | Type   | Description                                   |
| ------------------- | ------ | --------------------------------------------- |
| teamsChannelId      | string | Teams Channel Id containing the conversation. |
| teamsConversationId | string | Teams Conversation Id.                        |

## Goal Association Properties

Reference /project/goalAssociations/fields

| Property name       | Type   | Description                                   |
| ------------------- | ------ | --------------------------------------------- |
| taskId      | guid | Project Task Id. |
| goalId      | guid | Project Goal Id. |
| taskOrder      | string | Goal association order for ordering tasks |

## Goals Properties

Reference /project/goals/fields

| Property name       | Type   | Description                                   |
| ------------------- | ------ | --------------------------------------------- |
| name      | string | The name of the project goal. |
| color      | integer | Color index of the goal. |
| priority      | integer | Priority of the goal. |
| status      | integer | Status of the goal. |
| startDate      | datetime | Start date of the goal.|
| finishDate      | datetime | Finish date of the goal. |
| notes      | HTML | Goal notes formatted in HTML. |
| unformattednotes      | HTML | Goal notes with all HTML stripped out. |
| order      | string | Goal order |


## Label Association Properties

Reference /project/labelassociations/fields

| Property name | Type | Description                 |
| ------------- | ---- | --------------------------- |
| taskId        | guid | Dataverse Project Task Id.  |
| labelId       | guid | Dataverse Project Label Id. |

## Label Properties

Reference /project/labels/fields

| Property name | Type    | Description                    |
| ------------- | ------- | ------------------------------ |
| text          | string  | The name of the project label. |
| index         | integer | Color index of the label.      |

## Links Properties

Reference /project/links/fields

| Property name | Type     | Description                                        | Enumeration Values                                         |
| ------------- | -------- | -------------------------------------------------- | ---------------------------------------------------------- |
| linkType      | enum     | The type of the dependency.                        | FinishToFinish, FinishToStart, StartToFinish, StartToStart |
| delay         | duration | How long before the task should start.             |                                                            |
| delayUnits    | enum     | The unit the delay is in.                          | Minutes, Hours, Days, Weeks, Months                        |
| predecessorId | guid     | Dataverse Project Task Id of the predecessor task. |                                                            |
| successorId   | guid     | Dataverse Project Task Id of the successor task.   |                                                            |
| driver        | bool     | Indicates if the link drives the critical path.    |                                                            |

## Resource Properties

Reference /project/resources/fields

| Property name      | Type   | Description                                                            | Enumeration Values                                                                                                          |
| ------------------ | ------ | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| name               | string | Name of the team member.                                               |                                                                                                                             |
| overallocated      | bool   | If the team member is overallocated on this project.                   |                                                                                                                             |
| userPrincipalName  | string | Azure Active Directory User Principal Name for the user.               |                                                                                                                             |
| bookableResourceId | guid   | Bookable Resource Id for this team member.                             |                                                                                                                             |
| aadId              | guid   | Azure Active Directory user id of the Bookable Resource.               |                                                                                                                             |
| generic            | bool   | Indicates that this is a generic resource.                             |                                                                                                                             |
| type               | enum   | Bookable resource type.                                                | XrmUser, XrmContact, XrmAccount, XrmEquipment, XrmGeneric, AadUser, AadUserTypeNull, AadUserTypeMember, XrmBookableResource |
| jobTitle           | string | Job title of the bookable resource.                                    |                                                                                                                             |
| aadUserType        | enum   | If the bookable resource is an Azure Active Directory member or guest. | Member, Guest                                                                                                               |

## Sprint Properties

Reference /project/sprints/fields

| Property name | Type     | Description              |
| ------------- | -------- | ------------------------ |
| name          | string   | Name of the sprint.      |
| start         | datetime | Date when sprint starts. |
| finish        | datetime | Date when sprint ends.   |

## Task Properties

Reference /project/tasks/fields

| Property name               | Type        | Description                                                                                                                                                                                                                               | Enumeration Values                                                                                                                   |
| --------------------------- | ----------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ |
| work                        | double      | The total amount of work scheduled to be performed on a task by all assigned resources.                                                                                                                                                   |                                                                                                                                      |
| actualWork                  | double      | The amount of work that has already been done by the resources assigned to a task.                                                                                                                                                        |                                                                                                                                      |
| remainingWork               | double      | The total amount of non-overtime work scheduled to be performed by all resources assigned to a task.                                                                                                                                      |                                                                                                                                      |
| name                        | string      | Name of the task.                                                                                                                                                                                                                         |                                                                                                                                      |
| constraintType              | enum        | The constraint on the start or finish date of the task.                                                                                                                                                                                   | AsSoonAsPossible, AsLateAsPossible, MustStartOn, MustFinishOn, StartNoEarlierThan, StartNoLaterThan, FinishNoEarlierThan, FinishNoLaterThan |
| constraintDate              | datetime    | Indicates the constrained start or finish date as defined in the task ConstraintType. Required unless the constraint type is set to As late as possible or As soon as possible.                                                          |                                                                                                                                      |
| critical                    | bool        | Indicates whether a task has room in the schedule to slip, or if it is on the critical path.                                                                                                                                              |                                                                                                                                      |
| freeSlack                   | duration    | The actual amount of time that a task can be delayed without delaying any successor tasks. If a task has zero successor tasks, free slack is the amount of time a task can be delayed without delaying the entire project.                |                                                                                                                                      |
| totalSlack                  | duration    | The amount of time a task can be delayed without delaying a project's finish date.                                                                                                                                                        |                                                                                                                                      |
| index                       | integer     | Integer order of the task.                                                                                                                                                                                                                |                                                                                                                                      |
| milestone                   | bool        | Indicates whether a task is a milestone.                                                                                                                                                                                                  |                                                                                                                                      |
| actualDuration              | duration    | The span of actual working time for a task so far, based on the scheduled duration and current remaining work or percent complete. Actual duration can be calculated in two ways, either based on percent complete or remaining duration. |                                                                                                                                      |
| scheduledDuration           | duration    | The total span of active working time.                                                                                                                                                                                                    |                                                                                                                                      |
| remainingDuration           | duration    | The amount of time required to complete the unfinished portion of a task.                                                                                                                                                                 |                                                                                                                                      |
| percentComplete             | percent     | The percentage of the task duration completed.                                                                                                                                                                                            |                                                                                                                                      |
| scheduledStart              | datetime    | Start date and time as calculated by Project.                                                                                                                                                                                             |                                                                                                                                      |
| scheduledFinish             | datetime    | Finish date and time as calculated by Project.                                                                                                                                                                                            |                                                                                                                                      |
| earlyStart                  | datetime    | The earliest date that a task can begin, based on the early start dates of predecessor and successor tasks and other constraints.                                                                                                         |                                                                                                                                      |
| earlyFinish                 | datetime    | The earliest date that a task can finish, based on early finish dates of predecessor and successor tasks, other constraints, and any leveling delay.                                                                                      |                                                                                                                                      |
| lateStart                   | datetime    | The latest date that a task can start without delaying the finish of the project.                                                                                                                                                         |                                                                                                                                      |
| lateFinish                  | datetime    | The latest date that a task can finish without delaying the finish of the project.                                                                                                                                                        |                                                                                                                                      |
| actualStart                 | datetime    | The date and time that a task actually began.                                                                                                                                                                                             |                                                                                                                                      |
| actualFinish                | datetime    | The date and time that a task actually finished.                                                                                                                                                                                          |                                                                                                                                      |
| outlineLevel                | integer     | The number that indicates the level of a task in the project outline hierarchy.                                                                                                                                                           |                                                                                                                                      |
| cdsEffortCompleted          | double      | Amount of work done on this task as reported in Project Operations timesheets.                                                                                                                                                            |                                                                                                                                      |
| cdsEffortRemaining          | double      | Amount of work remaining on this task as reported in Project Operations timesheets.                                                                                                                                                       |                                                                                                                                      |
| cdsEffortEstimateAtComplete | double      | Forecast of total effort to complete the task as reported in Project Operations timesheets.                                                                                                                                               |                                                                                                                                      |
| cdsPercentComplete          | double      | Percentage of work completed as reported in Project Operations timesheets.                                                                                                                                                                |                                                                                                                                      |
| cdsScheduleVariance         | double      | Variance between the estimated work and the forecasted work based on the estimate at completion as reported in Project Operations timesheets.                                                                                             |                                                                                                                                      |
| summary                     | bool        | Indicates whether the task is a summary task.                                                                                                                                                                                             |                                                                                                                                      |
| resume                      | datetime    | The date the remaining portion of a task is scheduled to resume.                                                                                                                                                                          |                                                                                                                                      |
| stop                        | datetime    | The date that represents the end of the actual portion of a task.                                                                                                                                                                         |                                                                                                                                      |
| outlineNumber               | string      | Indicates the exact position of a task in the outline. For example, "7.2" indicates that a task is the second subtask under the seventh top-level summary task.                                                                           |                                                                                                                                      |
| completeThrough             | datetime    | The date and time for end of actual duration.                                                                                                                                                                                             |                                                                                                                                      |
| type                        | enum        | Type of task.                                                                                                                                                                                                                             | FixedUnits, FixedDuration, FixedWork                                                                                                   |
| durationDisplayFormat       | enum        | The display format the duration is displayed in.                                                                                                                                                                                          | Minutes, Hours, Days, Weeks, Months                                                                                                      |
| collapsed                   | bool        | Indicates whether the task is collapsed in the view.                                                                                                                                                                                      |                                                                                                                                      |
| deadline                    | datetime    | The date entered as a deadline for the task.                                                                                                                                                                                              |                                                                                                                                      |
| startSlack                  | duration    | Difference between earlyStart and lateStart dates.                                                                                                                                                                                        |                                                                                                                                      |
| finishSlack                 | duration    | Difference between earlyFinish and lateFinish dates.                                                                                                                                                                                      |                                                                                                                                      |
| order                       | double      | Order of the task represented as a double.                                                                                                                                                                                                |                                                                                                                                      |
| parentId                    | guid        | Dataverse Project Task Id of the parent task.                                                                                                                                                                                             |                                                                                                                                      |
| scheduleDrivers             | stringArray | Describes why a task is scheduled to start on it's start date. Can contain any of Actual, LevelingDelay, Constraint, Predecessor, ProjectStart, Calendar, Child, Parent, Deadline, Link.                                                  |                                                                                                                                      |
| start                       | datetime    | Date and time that a task is scheduled to begin.                                                                                                                                                                                          |                                                                                                                                      |
| finish                      | datetime    | The date and time that a task is scheduled to be completed.                                                                                                                                                                               |                                                                                                                                      |
| duration                    | duration    | The total span of active working time.                                                                                                                                                                                                    |                                                                                                                                      |
| bucketId                    | guid        | Dataverse Project Bucket Id the task is part of.                                                                                                                                                                                          |                                                                                                                                      |
| bucketOrder                 | string      | The order of the task within the bucket.                                                                                                                                                                                                  |                                                                                                                                      |
| sprintOrder                 | string      | The order of the task within the sprint.                                                                                                                                                                                                  |                                                                                                                                      |
| notes                       | HTML        | Notes entered about a task formatted in HTML.                                                                                                                                                                                             |                                                                                                                                      |
| unformattednotes            | HTML        | Notes with all HTML stripped out.                                                                                                                                                                                                         |                                                                                                                                      |
| manual                      | bool        | Whether this task is blank or has dates.                                                                                                                                                                                                  |                                                                                                                                      |
| showNotesOnCard             | bool        | Indicates if the note will be shown on the card in the board view.                                                                                                                                                                        |                                                                                                                                      |
| showChecklistOnCard         | bool        | Indicates if the checklist items will be shown on the card in the board view.                                                                                                                                                             |                                                                                                                                      |
| priority                    | integer     | Indicates the level of importance assigned to a task, with 5 being standard priority; the lower the number, the more urgent the task.                                                                                                     |                                                                                                                                      |
| sprintId                    | guid        | Property name of the sprint the task is assigned to.                                                                                                                                                                                      |                                                                                                                                      |
| gridColor                   | gridColor   | Color indexes for each field on this task where a conditionalColoringRule has evaluated to true. Please see for the color index mapping.                                                                                                  |                                                                                                                                      |
| [guid]                      | enum        | Task custom field definition. See below for definition.                                                                                                                                                                                   | stringOption, datetime, double, bool, string                                                                                             |

### Task Custom Field Properties

| Property name | Type      | Description                             | Enumeration Values                       |
| ------------- | --------- | --------------------------------------- | ---------------------------------------- |
| id            | guid      | Unique Id for the task custom field.    |                                          |
| type          | enum      | Type of Custom Field                    | stringOption,datetime,double,bool,string |
| custom        | bool      | true if it is custom field              |                                          |
| name          | string    | name of the custom field                |                                          |
| rollup        | enum      | Rollup type if type=double              | max,min,sum,average                      |
| values        | JSONArray | Values for options if type=stringOption. see [Choice Type](#choice-type) |                                          |

### Custom Field Types

| Custom Field Type | Enum Type    |
| ----------------- | ------------ |
| Text              | string       |
| Date              | datetime     |
| Number            | double       |
| Yes/No            | bool         |
| Choice            | stringOption |

### Choice Type

For Custom Fields of type 'stringOption'

| Property name | Type    | Description                        |
| ------------- | ------- | ---------------------------------- |
| Id            | guid    | Unique Id for choice               |
| value         | string  | Display value of the choice        |
| order         | double  | Display order of choices           |
| color         | integer | Color index assigned to the value. |

## View Properties

Reference /project/views/grid/fields

| Property name | Type    | Description                                         |
| ------------- | ------- | --------------------------------------------------- |
| name          | string  | Name of the grid view.                              |
| columns       | columns | Array of columns shown in the view and their width. |
