---
title: "Book a resource to a project"
ms.author: v-smandalika
author: v-smandalika
manager: dansimp
ms.date: 09/03/2021
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150 
ms.localizationpriority: medium
description: "Learn how to add a resource to a project."
---

# Book a resource to a project

The process of booking a resource to a project comprises the following tasks:

- [Create a resource requirement](#create-a-resource-requirement)
- [Schedule the booking requirement](#schedule-the-booking-requirement)

## Create a resource requirement

> [!IMPORTANT]
> Before you create a resource requirement, ensure you devise a project schedule that clearly presents your resource needs.

1. Launch the Resource Scheduling app by:
    1. Launching [https://make.powerapps.com](https://make.preview.powerapps.com/).
    1. Selecting the environment in which the resource requirement is to be created, on the top-right corner of the **Power Apps** home screen.
    1. Clicking **Apps** in the left navigation pane.
    1. Clicking on **Resource Scheduling**.
1. On the left navigation pane, click **Resource Requirements**.
1. Click **New** in the toolbar on top of the screen. The **New Resource Requirement** screen appears.
1. Use the tooltips to fill in the required information.
> [!NOTE]
> Creation of a resource to a project involves an important role played by booking allocation methods, one of which is used in creation of a resource to a project. For more information, see [Allocation Method](/dynamics365/project-operations/resource-management/booking-allocation-methods).

1. Click **Save**. 

## Schedule the booking requirement

You can schedule a booking requirement in the following ways:

- [Click on an unscheduled booking and find available resources](#click-on-an-unscheduled-booking-and-find-available-resources)
- [Drag an unscheduled booking requirement from the **List** view to the schedule board](#drag-an-unscheduled-booking-requirement-from-the-list-view-to-the-schedule-board)

### Click on an unscheduled booking and find available resources

1. From the **Resource Scheduling** home screen, click **Schedule Board**.
1. From the **Booking Requirement** list, click on an unscheduled booking.
1. Click **Find availability** to find available resources that meet the requirement from the list of resources on the schedule board.
> [!NOTE]
> When you do this, the filters will show the options for the selected booking requirement. If you can't find an available resource for the booking, try adjusting the filters.
1. When you see the available slot, right-click on the time slot on the schedule board and click **Book Here**, Or, drag and drop the booking requirement to the available time slot.

### Drag an unscheduled booking requirement from the List view to the schedule board

1. From the **Resource Scheduling** home screen, click **Schedule Board**.
1. Select an unscheduled booking requirement from the list at the bottom of the screen.
1. Drag the unscheduled booking requirement to an available resource/time slot on the schedule board.

If the resource was soft booked or proposed, the resources availability won’t be affected. Find more information [here](/dynamics365/field-service/schedule-board-utilization). The project manager can then accept a resource booking proposal or change a booking status through the **Bookings** table at Resource **Scheduling > Bookings**.

Once the resource is booked to the project, the resource shows up in the resource list and can be assigned to tasks. To ensure the project manager doesn’t use the resource more than its booking  limit, we recommend you create a report to review the booking versus total assignments.




