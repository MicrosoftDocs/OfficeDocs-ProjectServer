---
title: "Remove Project for the web or Roadmap from Office 365"
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: project-web
localization_priority: Normal
ms.custom: Adm_Project
search.appverid: PJO150
description: "Remove Roadmap from Office 365."
---

# Remove Project for the web or Roadmap from Office 365

You can turn Project for the web or Roadmap off in the Microsoft 365 admin center. This will prevent your users from using them, but will not remove any user data that currently exists. (Note that it may take a few minutes for functionality to be disabled while the setting synchronizes across your tenant.)

To turn off Project for the web:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Settings**, click **Settings**.
2. Click **Project**.
3. Uncheck **Turn Project for the web on for your entire organization**.
4. Click **Save**.

> [!Important!]
> Although this setting currently displays in your Project settings, it will not be enabled until a later date (see your Message Center). You can still turn off Project for the web for users in [this article](turn-project-for-the-web-off.md). </br> 

To turn off Roadmap:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Settings**, click **Settings**.
2. Click **Project**.
3. Uncheck **Turn Roadmap on or off for your entire organization**.
4. Click **Save**.

If your Project Online subscription ends, most of the associated data is deleted in conformance with the [Data Retention, Deletion, and Destruction in Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-data-retention-deletion-and-destruction-overview). Unlike other Project Online data, Project for the web and Roadmap data isn’t automatically deleted when your Project Online subscription ends.

You can remove all Project for the web and Roadmap data by removing the entire solution from Microsoft 365. This will delete all of the existing projects, roadmaps, and associated user data.

To remove Roadmap:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Admin centers**, click Dynamics 365.
2. In the Dynamics 365 Administration Center, select the default instance, and then click **Open**.
3. On the **Settings** menu, under **Customization**, click **Solutions**.
4. Select the **PortfolioService** solution, and then click **Delete**.
5. Select the **PortfolioService_Anchor** solution, and then click **Delete**.


> [!NOTE]
> Removing the Roadmap solution does not affect any of the projects or tasks that the roadmaps are connected to.


To remove Project for the web:

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Admin centers**, click Dynamics 365.
2. In the Dynamics 365 Administration Center, select the default instance, and then click **Open**.
3. On the **Settings** menu, under **Customization**, click **Solutions**.
4. Select the **msdyn_ProjectServiceCore** solution, and then click **Delete**.
5. Select the **MicrosoftDynamicsScheduling** solution, and then click **Delete**.
6. Select the **msdynce_SchedulingPatch** solution, and then click **Delete**.
7. Select the **msdynce_Scheduling** solution, and then click **Delete**.
## See Also

[Delete user data from Project for the web](delete-user-data-from-project-for-the-web.md)
