---
title: "Overview of Universal Resource Scheduling in Project for the web"
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 12/10/2021
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150 
ms.localizationpriority: medium
description: "This article provides an overview of the Universal Resource Scheduling in Project for the web, and its prerequisites."
---

# Overview of Universal Resource Scheduling in Project for the web

The **Universal Resource Scheduling** option in the **Resource Scheduling** app enables booking of resources to projects that helps ensure that resources are not overloaded with too much work from too many projects.

## Prerequisites

Before you can use the **Universal Resource Scheduling** option, ensure you have:

- Project for the web. For information on specific licensing needs, see [service description](/office365/servicedescriptions/project-online-service-description/project-online-service-description).
- User credentials with the necessary permissions.

## Book a resource to a project

The process of booking a resource to a project comprises the following tasks:

- [Create a resource requirement](#create-a-resource-requirement)
- [Schedule the booking requirement](#schedule-the-booking-requirement)

### Create a resource requirement

> [!IMPORTANT]
> Before you create a resource requirement, ensure you devise a project schedule that clearly presents your resource needs.

1. Launch the **Resource Scheduling** app.
   > [!NOTE]
   > To find Resource Scheduling app, launch [https://make.powerapps.com](https://make.preview.powerapps.com/). In the top-right corner, ensure that the desired environment is listed.
   > The desired environment is referred to one in which you can create the chosen resource requirement.
1. Select **Apps** in the left navigation pane.
1. Select **Resource Scheduling**.
1. In the left navigation pane, select **Resource Requirements**.
1. Select **New** in the toolbar on top of the screen. The **New Resource Requirement** screen appears.
1. Use the tooltips to fill in the required information. For more information, see [Allocation Method](/dynamics365/project-operations/resource-management/booking-allocation-methods).
1. Select **Save**. 

### Schedule the booking requirement

You can schedule a booking requirement in the following ways:

- [Select an unscheduled booking and find available resources](#select-an-unscheduled-booking-and-find-available-resources)
- [Drag an unscheduled booking requirement from the List view to the Schedule Board](#drag-an-unscheduled-booking-requirement-from-the-list-view-to-the-schedule-board)

#### Select an unscheduled booking and find available resources

1. From the **Resource Scheduling** home screen, select **Schedule Board**.
1. From the **Booking Requirement** list, select on an unscheduled booking.
1. From the list of resources on the Schedule Board, select **Find availability**. This option enables you to find the list of resources that are available and those resources that fit your requirement from the list.
   > [!NOTE]
   > When you use the **Find availability** option, you are presented with a list of options related to the chosen booking requirement. If the options are not displayed, try adjusting the filters.
1. When you find an apt available time slot for your booking requirement, right-click on it and choose **Book Here**. Alternatively, you can drag unscheduled booking requirement to an available resource/time slot on the Schedule Board.

#### Drag an unscheduled booking requirement from the List view to the Schedule Board

1. From the **Resource Scheduling** home screen, select **Schedule Board**.
1. Select an unscheduled booking requirement from the booking requirement list at the bottom of the screen.
1. Drag the unscheduled booking requirement to an available resource/time slot on the Schedule Board.

If the resource was soft booked or proposed, the resources availability won’t be affected. Find more information [here](/dynamics365/field-service/schedule-board-utilization). The project manager can accept a resource booking proposal or change a booking status through the Bookings table at **Resource Scheduling > Bookings**.

Once the resource is booked to the project, the resource shows up in the resource list and can be assigned to tasks. To ensure the project manager doesn’t use the resource more than its booking  limit, we recommend you create a report to review the booking versus total assignments.

## Update your environment

Before you can use Bookings with Project for the web, we recommend some updates to the Project Power App. To make these updates in the environment, you need [Environment Maker role](/power-platform/admin/database-security).
If you want to be able to search for resources based off skills or roles, you will need to show these fields on the resource form so the information can be entered.

See [this](/dynamics365/project-operations/resource-management/skills-proficiency-models) article for more information on how to set up skills and proficiency models although the experience within Project for the web will be a bit different. Once you have created skills and ensured the proficiency model meets your needs, you need to update your resources with the skills they have. Therefore, when trying to find a resource that meets a requirement, you can ensure you are staffing the correct person for the work.

You can also use roles to help further define your resource needs. Roles can be defined through the **Settings** option in the **Resource Scheduling**. You can use roles in addition to skills (for example, have a developer role and then skills based off more specific coding needs) or just use roles or skills for resource searching. Once roles are defined, you will then need to update resources similar to skills.

1. Go to [https://make.powerapps.com](https://make.powerapps.com/).
2. Ensure that you have set the precise environment in which you want to make edits, and that which is assigned to a project.
3. In the left navigation pane, select **Apps**.
4. Select the radio button of the project that you want to edit, and select **Edit**.
    > [!NOTE]
    > See [these](/powerapps/maker/model-driven-apps/) documents for more information on working with Power App model-driven apps. This article just covers the basic changes needed for bookings. We do recommend putting these changes in a new layer.
5. Select **Forms** in the **Bookable Resource** row. This action sets the right pane to **Bookable Resource** and results in display of the forms.
6. Select the **pencil** icon that is at the right of **Information**. This action results in a pop up of the Power Apps form editor.
7. In the tree view, scroll to **Project Service** and unhide it.
    > [!NOTE]
    > You can also rename the section, if you wish.
8. Make more changes of choice to the form.
9. Select **Save** in the top-right corner.
10. Select **Publish** in the top-right corner.
11. Select **X** on the top-right corner to exit the window.

It is also recommended to turn on the **Team** tab, too, for projects. This action enables your project managers to understand their resource needs and compare those needs to the bookings so that they can stay within their resource budgets.

1. Execute Steps 1-4 from the previous section.
2. Select **Forms** in the **Project** row. This action sets the right pane to **Project** and results in the display of the forms. 
3. Select the **pencil** icon to the right of **Information**. This action results in a pop up of the Power Apps form editor.
4. In the tree view, scroll to **Team** and unhide it.
   > [!NOTE]
   > If you are using the Project Accelerator, the **Team** view has already been un-hidden and is called **Resources**.
5. Select **Save** in the top-right corner.
6. Select **Publish** in the top-right corner.
7. Select **X** on the top-right corner to exit the window.
8. Select **Views** in the **Project Team Members** row.
9. Select the **pencil** icon to the right of **Team Members** (or whatever view you want to edit).
10. Select **Column Attributes Primary Entity**.
11. Drag the columns that you want to add to the table. We recommend the **Hard Booked Hours** column but you may also want to add the **Soft Booked Hours** column.
12. Select **Save** in the top-right corner.
13. Select **Publish** in the top-right corner.

### Update permissions/privileges

You will need to update permissions for people who need to use the Schedule Board. For an overview of how permissions work and how to update them, see [Security roles and privileges](/dynamics365/customerengagement/on-premises/admin/security-roles-privileges)    article.

To create a resource requirement, a user may need the following privileges:
> [!IMPORTANT]
> The exact needs depend on which fields you decide to use around resource requests and on your processes. A user may also need additional privileges if you have edited other security roles.

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

To use the Schedule Board and manage resource properties, the user will additionally need to have the Environment maker role in addition to the following roles:

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
