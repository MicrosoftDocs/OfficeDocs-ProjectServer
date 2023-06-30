---

title: "Task History Definition"
ms.author: namerali
author: nadinmerali
manager: pamgreen
ms.date: 6/30/2023
audience: admin
ms.topic: article
ms.service: project-web

ms.localizationpriority: medium
ms.assetid: 27f3838d-3dbe-4b98-80dc-df55f851154d
description: "Understand the Project task history in Dataverse."

---

# Task History Definition

This article describes the definition of the task history record that is stored in Dataverse in the Project History table. A task history record represents a change to a task.

"Edit Type" defines the type of history record.

| Syntax      | Description |
| ----------- | ----------- |
|[TaskCreated](#taskcreated-details)|represents when the task is created|
|[TaskEdited](#taskedited-details) |represents when the task is edited|
|[TaskDeleted](#taskdeleted-details) |represents when the task is deleted|
|[Undo](#undoredo-details) | represents when a change has been undone|
|[Redo](#undoredo-details) | represents when a change has been redone|
|[DependentEdit](#dependentedit-details) | represents when a task modified because of a change to another task|



## History Records

All history records share a common set of fields include:

| Field      | Description |
| ----------- | ----------- |
|Project | the project the history is related to|
|Project Task | the task the history is related to. It's blank if the task is deleted|
|XrmUserId | the Xrm User that made the change to the task|
|Timestamp | the date and time the change was generated|
|Edit Type | the type of history record|
|Details | containing the history data in a JSON format|

The following sections describe what the Details payload field contains depending on the type of history record and what was edited.  For the descriptions of the columns within the Details, review [Export Project Content Definition](export-project-content-definition.md)  

### TaskCreated details

The record is created when the task is created. The payload is empty.

### TaskDeleted details

Contains a single property "name", which is the name of the task when it was deleted.

Example:

```json
{"name":"Pour concrete"}
```

### Undo/Redo details

A "revisions" property with an array value holding all the revision numbers that were undone or redone.  The number corresponds to the suffix in the revision property of the history record.

Example:

```json
{"revisions":[11,12]}
```

Which matches to the history record with revision record suffix (00000000*11*) in:

```
msxrm\_orgxxxyyyy.crm.dynamics.com\_ff69bc0e-3f66-41c3-b40c-aa3035517e38\_0000000011
```

### TaskEdited details

TaskEdited represents direct property edits on a task and creates, deletes, and edits to any task child items, for example, checklist items, attachments, assignments, links, and so on.

#### Direct task field edits

The details have a "field" property with a JSON object value. That object has the changed property names as keys (there can be multiple task properties edited in a single user action), with an object as the value. That property object has a "previous" and "updated" keys with the values having the old and new values of the property.

Example:

```json
{
  "fields": {
    "name": {
      "previous": "Pour concrete",
      "updated": "Eat donuts"
    }
  }
}
```

For large properties (for example notes assignment "totalWorkContour"), an empty JSON is emitted and not the previous/updated values.

Example:

```json
 {
  "fields": {
    "notes": {}
  }
}
```

#### Task edits that complete a task

Any property edit that completes a task also adds a completed boolean property.

Example:
```json
{
  "fields": {
    "percentComplete": {
      "previous": 75,
      "updated": 100
    }
  },
  "completed": true
}
```
#### Task child element edits

Child elements are similar to field edits but the key is the navigation property name and value is an array. The items in the array can be creates (has a "created":true property), deletes ("deleted":true property), or edits (no created or deleted, but list of edited properties). Created or deleted child elements have a set of minimum properties needed to render the item with values directly set on the property. Edits have the same format as field edits on the task with the previous and updated values.

Example create:
```json
{
  "fields": {
    "checklistItems": [
      {
        "id": "f4be3c03-bc04-ee11-83c4-e04f43e61e09",
        "created": true,
        "name": "checklistItem1"
      }
    ]
  }
}
```
Example edit:

```json
{
  "fields": {
    "checklistItems": [
      {
        "id": "54219e93-bd04-ee11-83c4-e04f43e61e09",
        "completed": {
          "previous": false,
          "updated": true
        }
      }
    ]
  }
}
```

#### Included properties for creates and deletes

For simple task child elements (like check list Items, attachments) when being created and deleted, all properties required to render that item are included. Checklist items include the name and attachments include name, uri, and type.

Any child elements which are a relationship between other entities include the ID of the other entity. For example, assignments include the resourceId and links include the predecessorId.

### DependentEdit details

Dependent edit records are generated for a task if a change to another task causes the current task to be modified. The history record includes the changes to the current task and a sourceEdit property indicating the changes to the source task that caused the current task to be modified.

Example: A link is added to another task (source) to the current task and the current task start date is moved out one day:

```json
{
  "fields": {
    "start": {
      "previous": "2015-11-17T08:00:00Z",
      "updated": "2015-11-18T08:00:00Z"
    }
  },
  "sourceEdit": {
    "type": "TaskEdited",
    "taskId": "a6f33356-cd04-ee11-83c4-e04f43e61e09",
    "fields": {
      "predecessors": [
        {
          "id": "abf33356-cd04-ee11-83c4-e04f43e61e09",
          "created": true,
          "predecessorId": "a4f33356-cd04-ee11-83c4-e04f43e61e09"
        }
      ]
    }
  }
}
```


#### Multiple source edits

Bulk operations can change multiple tasks at once and can lead to multiple dependant changes. In that scenario, the tasks in the bulk operation are included in the sourceEdit with a CompoundEdit record type. Examples of these scenarios include deleting multiple tasks, linking multiple tasks, indenting multiple tasks. A CompoundEdit record includes the count of edits and the first three edits.

Example

```json
{
  "fields": {
    "start": {
      "previous": "2015-11-17T08:00:00Z",
      "updated": "2015-11-16T08:00:00Z"
    }
  },
  "sourceEdit": {
    "type": "CompoundEdit",
    "count": 2,
    "edits": [
      {
        "type": "TaskDeleted",
        "taskId": "f3233655-ce04-ee11-83c4-e04f43e61e09",
        "name": "Task A"
      },
      {
        "type": "TaskDeleted",
        "taskId": "f1233655-ce04-ee11-83c4-e04f43e61e09",
        "name": "Task B"
      }
    ]
  }
}
```

#### Edits to summary tasks

Certain operations, like deleting a task or indenting a task, can generate multiple records if the edited task is a summary task because those edits also apply to the task's children. All dependent records include the summary task as the sourceEdit.

### Record size

Details field has a maximum size of 1000 characters. If the initial change record exceeds 1000 characters, the history record is trimmed down. All string changes are limited to 100 characters and the number of changed fields are limited to 6. A "truncated" property indicates how many direct fields weren't included. A "truncatedElements" property indicates the number of child elements that weren't written out.

If the size of the record with the above restrictions exceeds 1000 characters, the entire record is not generated.

Example

```json
{
  "fields": {
    "start": {
      "previous": "2015-11-17T08:00:00Z",
      "updated": "2015-11-10T08:00:00Z"
    }
  },
  "sourceEdit": {
    "type": "CompoundEdit",
    "count": 2,
    "edits": [
      {
        "type": "TaskEdited",
        "taskld": "225a7a3b-a916-ee11-a35f-480fcf4e7967",
        "fields": {
          "name": {
            "previous": "Prepare Preliminary Project Scope Statement",
            "updated": "Summarize Project Results and Lessons Learned"
          },
          "start": {
            "previous": "2015-11-16T08:00:00Z",
            "updated": "2017-11-16T08:00: 00Z"
          },
          "truncated": 5
        }
      },
      {
        "type": "TaskEdited",
        "taskld": "245a7a3b-a916-ee11-a35f-480fcf4e7967",
        "fields": {
          "name": {
            "previous": "Prepare Preliminary Project Scope Statement",
            "updated": "Develop High Level Work Breakdown Structure"
          },
          "start": {
            "previous": "2015-11-16T08:00:00Z",
            "updated": "2017-11-16T08:00:00Z"
          },
          "truncated": 5
        }
      }
    ]
  }
}
```
