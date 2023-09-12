---
title: "Scheduling modes"
ms.author: serdars
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

# Scheduling modes

Project for the web enables administrators to define how their organization manages key variables in project tasks. Based on the specific needs of the organization, administrators can make changes to the scheduling mode when a project is created.

## Change your organization’s scheduling mode

Project for the web sets **Fixed duration** as the out-of-the-box default scheduling mode for all organizations. However, administrators can choose a different default scheduling mode at the organizational level.

To change the scheduling mode for your organization, perform the following steps:

1. Launch the **Power Apps** portal.
1. On the bottom-left corner in the navigation pane, click **Projects**.

   :::image type="content" source="media/project-power-apps-screen.png" alt-text="The Power Apps screen":::

1. Navigate to **Settings > General > Parameters**, and then select the project parameter. The **Project Parameters** page appears.

   :::image type="content" source="media/parameter-screen.png" alt-text="The Project Parameters screen":::

1. Choose the scheduling mode that you want to apply from the **Schedule Mode** field, to make it the default one.

## Enable project managers to override default scheduling mode

Administrators can determine if project managers can override the default scheduling mode on their projects. To enable the override, perform the following steps:

1. Choose **Settings > General > Parameters**, and then select the project parameter. The **Project Parameters** page appears.
1. Set **Project Level Schedule Mode Override Permitted** to **Yes**.

> [!NOTE]
> If this setting is set to **No**, all projects in the organization will have the organization’s default scheduling mode.
> 
> If this setting is set to **Yes**, project managers can override the default scheduling mode setting & set a custom scheduling mode on their projects.

## Project Manager

A project manager creates a project and is, therefore, entitled to change the default scheduling mode for that project.

### Changing the scheduling mode setting on a project

To change a project's default scheduling mode, perform the following steps:

1. Create a new project in the Project Power app. Once the project is created, its summary page appears.
1. Navigate to the **Schedule Mode** setting.
1. Change the scheduling mode to your desired mode.
1. Save the changes.

> [!NOTE]
> The scheduling mode can only be edited while a project is being created. After your project has been saved, you cannot edit the scheduling mode.
> 
> Even when this parameter is set to **Yes**, you can only change the scheduling mode for the project; you cannot change the scheduling mode of individual tasks.

### Copy projects

A project manager has the privilege to create projects by cloning from an existing project.  If the newly created project is a cloned one, the project manager can't set the scheduling mode. The destination project will always default to the mode defined at the organizational level.

### Copy tasks

A project manager has the privilege to copy a task from one project to another. Such cloned tasks inherit the scheduling mode of the destination project.

The following three scheduling modes are available in a project:

- Fixed duration (default)
- Fixed effort
- Fixed unit

The values affected by the definition of a specific scheduling mode are determined by the following formula:

Effort = Duration x Units

When you define a project’s scheduling mode, you are setting one of these values to remain unchanged. Holding this value as a constant places a priority on that value, which notifies the system not to change it when the other two values change. The following table provides information about the impacts of selecting a specific mode:


|In this task  |If you revise units  |If your revise duration  |If you revise effort  |
|---------|---------|---------|---------|
|Fixed units task     |    Duration is recalculated     |    Effort is recalculated     | Duration is recalculated        |
|Fixed effort task    |    Duration is recalculated     |  Units are recalculated       |    Duration is recalculated     |
|Fixed duration task    |    Effort is recalculated     |Effort is recalculated         |Units are recalculated         |

For more information about the implications of a given mode, see [Change the task type for more accurate scheduling](https://support.microsoft.com/office/change-the-task-type-for-more-accurate-scheduling-b0b969ad-45bc-4e9e-8967-435587548a72). 

> [!NOTE]
> In the topic, the term **Work** is used instead of **Effort**.





