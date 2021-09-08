---
title: "Scheduling modes"
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 09/08/2021
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150 
ms.localizationpriority: medium
description: "Learn about the various modes of scheduling in project operations."
---

# Scheduling Modes

Project for the web provides the ability for admininstrators to define how their organization manages key variables in project tasks. Based on the specific needs of the organization, administrators can make changes to the scheduling mode when a project is created.

The following three scheduling modes are available in project operations:

- Fixed duration (default)
- Fixed effort
- Fixed unit

The values impacted by the definition of a specific scheduling mode are determined by the following formula:

Effort = Duration x Units

When you define a project’s scheduling mode, you are setting one of these values, which then can't be changed. Holding this value as a constant places a priority on that value, which notifies the system not to change it when the other two values change. The following table provides information about the impacts of selecting a specific mode:


|In this task  |If you revise units  |If your revise duration  |If you revise effort  |
|---------|---------|---------|---------|
|Fixed units task     |    Duration is recalculated     |    Effort is recalculated     | Duration is recalculated        |
|Fixed effort task    |    Duration is recalculated     |  Units are recalculated       |    Duration is recalculated     |
|Fixed duration task    |    Effort is recalculated     |Effort is recalculated         |Units are recalculated         |

For more information about the implications of a given mode, see [Change the task type for more accurate scheduling](https://support.microsoft.com/office/change-the-task-type-for-more-accurate-scheduling-b0b969ad-45bc-4e9e-8967-435587548a72). 

> [!NOTE]
> In the topic, the term **Work** is used instead of **Effort**.





