---
title: "Add non-user resources in Project for the web"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: 
- PJO150
- MET150 
ms.localizationpriority: medium
description: "Learn how to add a non-user resource and make it available to assign to tasks in Project for the web."
---

# Add non-user resources in Project for the web

Project for the web is built on the [Microsoft Power Platform](https://powerplatform.microsoft.com/en-us/), and some aspects of resource setup for Project for the web is done in Dynamics 365, such as how to add resources that aren’t users in your organization (for example, contacts or equipment) and making them available to assign to tasks.

While users in Azure Active Directory (Azure AD) are available to assign to project tasks in Project for the web, you need to manually add non-user resources.

> [!Note]
> Guest users accounts in AAD are not  supported to be available to directly assign  to tasks in Project for the web.

## Types of non-user resources

Some of the more commonly used non-user resources you’ll be able to add include:

|||
|:-----|:-----|
|**Name** <br/> |**Description** <br/> |
|Contact or Account   <br/> |The resource isn’t directly a part of your organization, but needs to be scheduled. A common example is subcontractors.  <br/> |
|Equipment <br/> |The resource is a piece of equipment, tool, or machine that must be scheduled.  <br/> |

> [!Note]
> You will only be able to assign user, contact, account, or equipment resource types to project tasks in Project for the web.

For more information about non-user resources, see [Set up a bookable resource](https://docs.microsoft.com/dynamics365/field-service/set-up-bookable-resources#add-work-hours).

## Create a non-user resource

You first need to go to the Dynamics 365 Project Resources page:

1. While logged into Office 365, open a browser window and go to **https://<spam><spam>make.powerapps<spam><spam>.com**.
2. On the PowerApps page, select **Apps**.
3. On the Apps page, in the Org Apps tab, select **Project**.
4. On the Project page, in the left pane, select **Resources**.

When you get to the resources page, perform the following steps:

1. On the Resources page, select **New**.
2. On the New Bookable Resource page, select in the **Resource Type** field, and select the resource type you need to create.
![Resource types.](media/resourcetypes.png)
3. Provide the information needed for the resource type you selected.
4. In the **Name** field, type the name you want to give the resource.
5. When you’re done, select **Save and Close**.

The new resource will display in the Bookable Resources page and can be assigned to tasks in Project for the web.

## See Also

[Set up a bookable resource](https://docs.microsoft.com/dynamics365/field-service/set-up-bookable-resources#add-work-hours)
