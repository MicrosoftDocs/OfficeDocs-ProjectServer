---
title: "Overview of Universal Resource Scheduling in Project for the web"
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 09/06/2021
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150 
ms.localizationpriority: medium
description: "Provides an overview of the Universal Resource Scheduling in Project for the web, and its prerequisites."
---

# Overview of Universal Resource Scheduling in Project for the web

The **Universal Resource Scheduling** option in the **Resource Scheduling** app enables booking of resources to projects. A booked resource is ensured of a balanced workload, with its **booked** status indicating that it won't be used for too much work from projects.

## Prerequisites

Before you can use the **Universal Resource Scheduling** option, ensure you have:

- Project for the web. For information on specific licensing needs, see [service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).
    - User credentials with the necessary permissions. See below for more information.

### Update your environment

Before you can use Bookings with Project for the web, we recommend some updates to the Project Power App. You will need the [Environment Maker role](/power-platform/admin/database-security) on the environment to make these updates.
If you want to be able to search for resources based off skills or roles, you will need to show these fields on the resource form so the information can be entered.

See [this](/dynamics365/project-operations/resource-management/skills-proficiency-models) article for more information on how to set up skills and proficiency models although note the experience within Project for the web will be a bit different. Once you have created skills and ensured the proficiency model meets your needs, you need to update your resources with the skills they have. Therefore, when trying to find a resource that meets a requirement, you can ensure you are staffing the correct person for the work.

You can also use roles to help further define your resource needs. Roles can be defined through the the **Settings** option in the **Resource Scheduling**. You can use roles in addition to skills (for example, have a developer role and then skills based off more specific coding needs) or just use roles or skills for resource searching. Once roles are defined, you will then need to update resources similar to skills.

1. Go to [https://make.powerapps.com](https://make.powerapps.com/).
1. Ensure that you have set the precise environment in which you want to make edits, and that which is assigned to a project.
1. On the left navigation pane, click **Apps**.
1. Select the radio button of the project that you want to edit, and click **Edit**.
> [!NOTE]
> Refer to [these](/powerapps/maker/model-driven-apps/) documents for more information on working with Power App model-driven apps. This article just covers the basic changes needed for bookings. We do recommend putting these changes in a new layer.
1. Click **Forms** in the **Bookable Resource** row. This action sets the right pane to **Bookable Resource** and results in display of the forms.
1. Click the **pencil** icon which is at the right of **Information**. This action results in a pop up of the Power Apps form editor.
1. In the tree view, scroll to **Project Service** and un-hide it.
> [!NOTE]
> You can also rename the section, if you wish.
1. Make any additional changes of choice to the form.
1. Click **Save** in the top-right corner.
1. Click **Publish** in the top-right corner.
1. Click **X** on the top-right corner to exit the window.

It is also recommended to turn on the **Team** tab, too, for projects. This action enables your project managers to understand their resource needs and compare those to the bookings so that they can stay within their resource budgets.

1. Execute Steps 1-4 from the previous section.
1. Click **Forms** in the **Project** row. This action sets the right pane to **Project** and results in the display of the forms. 
1. Click the **pencil** icon to the right of **Information**. This action results in a pop up of the Power Apps form editor.
1. In the tree view, scroll to **Team** and un-hide it.
> [!NOTE]
> If you are using the Project Accelerator, the **Team** view has already been un-hidden and is called **Resources**.
1. Click **Save** in the top-right corner.
1. Click **Publish** in the top-right corner.
1. Click **X** on the top-right corner to exit the window.
1. Click **Views** in the **Project Team Members** row.
1. Click the **pencil** icon to the right of **Team Members** (or whatever view you want to edit).
1. Click **Column Attributes Primary Entity**.
1. Drag the columns that you want to add to the table. We recommend **Hard Booked Hours** but you may also want to add Soft Booked Hours.
1. Click **Save** in the top-right corner.
1. Click **Publish** in the top-right corner.

### Update permissions/privileges

You will need to update permissions for people who need to use the schedule board. For an overview of how permissions work and how to update them, see [this](/dynamics365/customerengagement/on-premises/admin/security-roles-privileges) article.

To create a resource requirement, a user may need the following privileges:
> [!IMPORTANT]
> The exact needs depend on which fields you decide to use around resource requests and your processes. A user may also need additional privileges if you have edited other security roles.

- Custom Entities
    - Requirement characteristic
    - Requirement Group
    - Requirement Organization Unit
    - Requirement Relationship
    - Requirement Resource Category
    - Requirement Resource Preference
    - Requirement Status
    - Resource Request
    - Resource Requirement
    - Resource Requirement Detail

To accept a booking proposal, the user will additionally need:

- Service
    - Booking Status

To use the schedule board and manage resource properties, the user will additionally need:

- Service
    - Bookable Resource Booking
    - Bookable Resource Booking Header
    - Bookable Resource Category
    - Bookable Resource Category Association
    - Bookable Resource
    - Bookable Resource Characteristic
    - Bookable Resource Group
    - Booking Status
- Custom Entities
    - Booking Alert Status
    - Booking Change
    - Booking Rule
    - Booking Setup Metadata
    - Fulfillment Preference
    - Schedule Board Setting
    - System User Scheduler Setting





