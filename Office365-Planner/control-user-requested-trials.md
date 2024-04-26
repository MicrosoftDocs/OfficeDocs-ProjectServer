---
title: "Control user-requested trials and licenses for Planner"
description: "Learn how to administer 30-day trials and licenses of Planner to your users."
author: mscharlo 
ms.author: v-mscharlock 
manager: jtremper
ms.service: office-perpetual-itpro
ms.subservice: planner 
ms.topic: how-to 
ms.date: 04/30/2024
ms.localization_priority: medium
audience: Admin
---
MICHELLE TODO: This still has (picture) in it

# Control user-requested trials and licenses for Planner
Planner allows users to request trials of the Project Plan 3 capabilities free for 30 days and request licenses for this plan from Microsoft 365 administrators.  

As an admin, you can use the Microsoft Admin Center (MAC) to enable or disable the ability for users to opt in to a trial and request a license after the trial. You can also control whether a self-service purchase option is available to users after they complete the trial.  

> [!NOTE]
> [Want to know more about Planner?](https://support.microsoft.com/planner) Planner is included in most Microsoft 365 Enterprise level licenses and unites To Do, Project, and Copilot into Teams as a lightweight solution for project management. [See this Planner FAQ about recent updates](https://cdn.techcommunity.microsoft.com/assets/Planner/Microsoft_Planner_FAQ_April_2024.pdf).

## Control access to 30-day trials

As an admin there are several ways to grant access to trials and deny them.  

## Process Planner trial requests individually

When users request a trial of Planner, you receive a notification in the Microsoft Admin Center. You can either [accept or deny these individually](https://learn.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users#assign-licenses-by-using-the-licenses-page) using the **Licenses** tab in the menu.  

(Picture)

Or you can opt to assign Planner licenses you already have through your Microsoft 365 subscription to users. Assigning a license gives users access to the product right away and eliminates the step accepting their post-trial request for a license. [You can assign 25 licenses per organization for 30-day trials as needed through the Microsoft Admin Center using these instructions](https://learn.microsoft.com/microsoft-365/admin/manage/assign-licenses-to-users#assign-licenses-by-using-the-licenses-page).  

## Process Planner trial requests in bulk  

You can administer trials to users in bulk using [PowerShell commands](https://learn.microsoft.com/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell) or [by group membership in Microsoft Entra ID](https://learn.microsoft.com/entra/identity/users/licensing-groups-assign).  

## Determine your organization's product usage

After accepting a user’s request for a trial, you can view information on product usage that may help you assign licenses to users that most need them. Within the Microsoft 365 Admin Center, you can monitor metrics like active users and project and task activity.

(Picture)

## Process post-trial requests for Planner

After initiating the trial, a user can request a license for Planner. This license request shows up as a request for Project Plan 3, as this plan is what users are offered in the trial period.

>[!TIP]
> Learn more about the [overall changes to Planner and Project product and plan names](https://techcommunity.microsoft.com/t5/planner-blog/the-new-planner-in-teams-is-now-in-public-preview/ba-p/4072525).  

You can control the subscription requests individually using these steps:  

1. Navigate to **Licenses** within the Microsoft 365 Admin Center.  

2. Within the **Licenses** tab, select **Requests**. You'll see a list of user-requested licenses by name and username.  

3. After selecting the requests you want to update, you'll be prompted to enter information about what Project Plan licenses you can grant. You can also approve and deny license requests, and send messages to the users to update them on the status of their request.

>[!NOTE]
> It is also possible to use your own license assignment process and this option can be found under the **Licenses** tab, then select **Requests**.  

## Enable or disable self-service purchases

Sometimes users decide they need a license for Planner and opt to purchase this license themselves, outside of your organizational subscription to Microsoft 365.  

As an admin, you can't assign or unassign licenses for a self-service purchase subscription bought by a user in your organization. You can [take over a purchase or trial subscription, and then assign or unassign licenses](https://learn.microsoft.com/microsoft-365/commerce/subscriptions/manage-self-service-purchases-admins?view=o365-worldwide#take-over-a-self-service-purchase-or-trial-subscription).
