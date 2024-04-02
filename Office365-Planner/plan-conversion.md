---
title: "Plan Downgrade"
ms.author: namerali
author: NadinMerali
manager: dellerderick
ms.date: 03/29/2024
audience: Admin,user
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
description: "This article explains how to convert a basic plan into a premium plan in Microsoft Planner."
---

# Converting basic plans to premium plans

There are several capabilities that are available in premium plans that do not exist in basic plans.  For example, premium users can create dependencies between tasks in a premium plan such that when one task is moved out (by any user), dependent tasks also move out.  More details on the differences between basic and premium plans can be found [here](https://support.microsoft.com/office/comparing-basic-vs-premium-plans-5e351170-4ed5-43dc-bf30-d6762f5a6968).

The following plans are eligible to be converted into premium plans:
- Basic plans that are shared with a O365 group.
- Basic plans which are not yet shared (coming soon)
Plans that have been created outside of Planner core application or have business rules cannot be converted.  Examples include:
- Published Plans
- Loop task list plans

Any member of an eligible basic plan can convert it to a premium plan.  Premium plans that were converted can be downgraded back to basic plans.  Details about downgrading plans can be found **here**.

Users with a Planner premium license can convert a basic plan to a premium plan.  In scenarios where an M365 user is viewing a basic eligible plan and starting a Planner premium trial, the basic plan will be converted into a premium plan.

## What to know before downgrading

- A new premium plan is created with all the data from the basic plan.  
- The plan is upgraded in-place.  Users who have access to the basic plan will have access to the premium plan once the conversion is complete.  
  - Users and guest who have M365 licenses will be able to continue to work in premium plans as before.  See M365 User access and guest access for more information
  - Users accessing plans from places that do not support premium plans will either be automatically directed to a location that supports premium plans or will be given instructions on how to access premium plans.  See redirection below

- The basic plan becomes read-only and achieved for 90 days and cannot be accessed.  Users in the premium plan have 90 days to downgrade back to their basic plan.  After 90 days the basic plan is removed.  Details about why and how to downgrade back to a basic plan can be found here.
- If there is data incompatibility between the basic and premium plan the conversion logic will fall back to an import flow:
  - The basic plan is not modified and access to the members remains the same.  The team can continue to work on the basic plan without being affected.
  - A new premium plan will be created with a copy of the compatible data and will understand what was incompatible.   The user who initiated conversion will have access to the premium plan copy.
  - Possible next steps:
    - Modify the basic plan and remove compatibility issues and attempt to convert again.
    - Review the premium plan copy and share with the team if it meets your requirements.
Please review [Import a plan](https://prod.support.services.microsoft.com/office/import-a-plan-into-a-project-for-the-web-016f9e4d-28c6-4f61-a1b1-82187185977d) to understand scenarios and limits where the system will fall back to the import flow.
- Power Automate workflows and 3rd party applications will need to be modified to work with premium plans.  Please see [Use V2 Project schedule APIs with Power Automate](https://learn.microsoft.com/dynamics365/project-operations/project-management/scheduling-apis-powerautomate-v2)  and [Project schedule API](https://learn.microsoft.com/en-us/dynamics365/project-operations/project-management/schedule-api-preview) for more information.

## Converting to a premium plan

Note: Premium users can convert basic plans into premium plans

1. Open the basic plan in the new Planner Application.
2.	Click on the …
3.	Choose a premium view.
4.	Click “Convert to premium for everyone”.
5.	Once completed, everyone will be working on the premium plan. 

The process can take a few minutes to complete. Once it is done, the user and their team will be redirect to the premium plan.

## Redirection to premium plans


Certainly! Here's a simple markdown table for you:

| **Entry Point 1** | **Outcome 2** |
|--------------|--------------|--------------|
| Item 1       | Value 1      | Result 1     |
| Item 2       | Value 2      | Result 2     |
| Item 3       | Value 3      | Result 3     |

Feel free to customize the content as needed! 😊
