# Task History Definition

This article describes the definition of the task history record that is stored in Dataverse in the Project History table. A task history record represents a change to a task.

The type of history record is defined by the "Edit Type".

| Syntax      | Description |
| ----------- | ----------- |
|TaskCreated|represents when the task is created.|
|TaskEdited | represents when the task is edited.|
|TaskDeleted | represents when the task is deleted. |
| Undo | represents when a change has been undone.|
| Redo | represents when a change has been redone.|
|DependentEdit | represents when a task modified because of an change to another task|


## History Records

All history records share a common set of fields include:

| Field      | Description |
| ----------- | ----------- |
|Project | the project the history is related to.|
|Project Task | the task the history is related to. It is blank if the task is deleted.|
|XrmUserId | the Xrm User that made the change to the task.|
|Timestamp | the datetime the history record was generated..|
|Edit Type | the type of history record.|
|Details | containing the history data.|

The following will describe what the Details payload field contains depending on the type of history record and what was edited

### TaskCreated details

The record is created when the task is created. The payload will be empty.

### TaskDeleted details

Single property "name" which is the name of the task when it was deleted.

Example:

```
{"name":"Pour concrete"}
```

### Undo/Redo details

A "revisions" property with an array value holding all the revision numbers that were undone or redone.  The revision that was undone/redone will be in the revision property

Example:

```
{"revisions":[11,12]}
```

Will match to the history record with revision

```
msxrm\_orgxxxyyyy.crm.dynamics.com\_ff69bc0e-3f66-41c3-b40c-aa3035517e38\_00000000*11*
```

### TaskEdited details

TaskEdited represents direct property edits on a task as well as creates, deletes, and edits to any task child items (e.g. check list Items, attachments, assignments, links, etc.).

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

For large properties (e.g. notes assignment "totalWorkContour"), an empty JSON is emitted and not the previous/updated values.

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

These are similar to field edits but the key is the navigation property name and value is an array. The items in the array can be creates (has a "created":true property), deletes ("deleted":true property), or edits (no created or deleted, but list of edited properties). Created or deleted child elements have a set of minimum properties needed to render the item with values directly set on the property. Edits have the same format as field edits on the task with the previous and updated values.

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

For simple task child elements (like check list Items, attachments) for creates and deletes, all properties required to render that item are included. Checklist items include the name and attachments include name, uri, and type.

Any child elements which are a relationship between other entities will include the id of the other entity. For example, assignments include the resourceId and links include the predecessorId.

### DependentEdit details

Dependent editrecords are generated for a task if a change to another task causes the current task to be modified. The history record will include the changes to the current task as well as a sourceEdit property indicating the changes to the source task that caused the current task to be modified.

Example: When a link is added to another task (source) to the current task and the current task start date is moved out one day:

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

Bulk operations can change multiple tasks at once and can lead to multiple dependance changes. In that scenario, the tasks in the bulk operation are included in the sourceEdit with a CompoundEdit record type. Examples of these scenarios include deleting multiple tasks, linking multiple tasks, indenting multiple tasks. A CompoundEdit record includes the count of edits and the first 3 edits.

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

Certain operations like deleting a task or indenting a task can generate multiple records if the edited task is a summary task since those edits also apply to the task's children. All dependent records will only include the summary task as the sourceEdit.

### Record size

Details field has a maximum size of 1000 characters. If the initial change record exceeds 1000 characters, the history record will be trimmed down. All string changes will be limited to 100 characters and the number of changed fields will be limited to 6. A "truncated" property will indicate how many direct fields were not included. A "truncatedElements" property will indicate the number of child elements that were not written out.

If the size of the record with the above restrictions will still exceed 1000 characters, the entire record is not generated.

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
