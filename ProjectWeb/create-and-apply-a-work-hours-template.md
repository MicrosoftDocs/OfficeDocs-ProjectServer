---
title: "Create and apply a work hours template in Project for the web"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: 
search.appverid: PJO150
localization_priority: Normal
m
description: "Learn how to create a work hours template and apply it to resources in Project for the web."
---

# Create and apply work calendars in Project for the web

Project for the web is built on the [Microsoft Power Platform](https://powerplatform.microsoft.com/en-us/), and some aspects of resource setup for Project for the web is done in Dynamics 365, including how to create a work hours template and apply it to resources.

Before you can create project schedules, you need to set up a project calendar that defines the number of working hours to accommodate per day in the schedule and any business closures. You do this with a work hours template, which contains details about work hours per day, days off, and any other business closures.

You associate a work template to the project calendar to apply the schedule for the project.

There are two ways you can create a work hours template:
- Create a work hours template based on a resource’s calendar.
- Create a new work hours template.
 
Both methods are done on the PowerApps Project Resources page in Dynamics 365. To go there, do the following:
1. While logged into Office 365, open a browser window and go to **https://web.powerapps.com**.
2. On the PowerApps page, select **Apps**.
3. On the Apps page, in the Org Apps tab, select **Project**.
4. On the Project page, in the left pane, select **Resources**.
 

## Create a work hours template based on a resource’s calendar

1. On the Resources page, select the resource you want to base your work hours on.
2. Click **Save Calendar As**, enter a name for the work hours template, and then click **Save**.
3. When you’re done changing options, click **Save and Close**.


## Create a new work hours template

1. On the Resources page, click the **Projects** menu on the bottom of the left pane, and then select **Settings**.
2. On the Project Settings Parameters page, click **Calendar Templates**.
3. On the **Active Work Hour Templates** page, click **New**.
4. ON the New Work Templates page, give it a name.
5. In the Template Resource field, type the name of a resource to base the work hours on.
6. Click **Save and Close**.
7. Your new work hours template will display on the **Active Work Hour Templates** page.

## Apply a calendar to a resource

Once you’ve created a work hours template, you can assign it to resources so their calendars reflect the working hours specified in the template.

1. On the Resources page, select the resources that you want to apply set the calendar for. You can select more than one resource.
2. Click **Set Calendar**.
3. In the **Work Template** window, click in the **Work Template** box to see the work templates that are available, and then select the one you want to apply.
4. Click **Apply**.


 
## See Also


  
  



