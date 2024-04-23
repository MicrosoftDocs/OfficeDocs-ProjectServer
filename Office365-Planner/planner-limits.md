---
title: "Microsoft Planner limits"
description: Learn about limits that apply to Microsoft Planner.
ms.author: v-mscharlock
author: mscharlo
manager: jtremper
ms.date: 04/19/2024
audience: Admin
ms.topic: article
ms.service: office-perpetual-itpro
ms.subservice: planner
ms.localization_priority: medium
---
# Microsoft Planner limits

> [!IMPORTANT]
>
> This article applies to:
>
> - Basic plans in the Planner app in Teams
> - All plans in other Planner endpoints (including Planner web, Planner mobile, and Planner connectors)
>
> It doesn't apply to To Do lists or premium plans in the Planner app in Teams. [Learn more about the Planner app in Teams](/microsoftteams/manage-planner-app)

This article describes the current limits that apply to Microsoft Planner.

## Plan limits

|Field  |Limit  |
|---------|---------|
|Maximum active tasks in a plan    |2400|
|Maximum buckets in a plan    |200|
|Maximum plans owned by a group or user     |200|
|Maximum plans that a user can subscribe to delta-sync for    |300|
|Maximum tasks in a plan    |9000|
|Maximum users that can subscribe to delta-sync for a plan    |100|
|Maximum contexts on a plan    |10|
|Maximum favorite plans for a user     |30|

> [!NOTE]
> - An active task is a task that is not completed.
> - Delta sync lets users passively receive updates in real-time while the app is open. Users beyond the delta-sync limits will not see updates in real-time.
> - Most Planner plans are owned by a group. Plans created by other apps, and shown in Planner, may be owned by a user.
> - A context is the association between a plan and a host container like a Teams tab. The limit on contexts is a limit on how many associations a plan can have.

## Task limits

|Field  |Limit  |
|---------|---------|
|Maximum assignees in a task     |20|
|Maximum checklist items in a task     |20|
|Maximum references on a task     |10|
|Maximum tasks assigned to a user     |3000|
|Maximum tasks created by a user     |20000|
|Maximum user-data count in user details   |10|

> [!NOTE]
> These limitations can be raised or lowered from time-to-time without a prior notice. Refer to this article for updated information on Planner limits.
