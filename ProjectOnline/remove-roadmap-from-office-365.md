---
title: "Remove Roadmap from Office 365"
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: project-online
localization_priority: Normal
ms.custom: Adm_Project
search.appverid: PJO150
description: "Remove Roadmap from Office 365."
---

# Remove Roadmap from Office 365

You can turn Roadmap off in the Microsoft 365 admin center. This will prevent your users from using Roadmap, but will not remove any user data that currently exists. (Note that it may take a few minutes for roadmap functionality to be disabled while the setting synchronizes across your tenant.)

1. In the [Microsoft 365 amin center](https://admin.microsoft.com), under **Settings**, click **Services & add-ins**.
2. Click **Project Online**.
3. Set **Turn Roadmap on or off for your entire organization** to **Off**.

If your Project Online subscription ends, most of the associated data is deleted in conformance with the [Data Retention, Deletion, and Destruction in Office 365](https://docs.microsoft.com/office365/securitycompliance/office-365-data-retention-deletion-and-destruction-overview). Unlike other Project Online data, Roadmap data isn’t automatically deleted when your Project Online subscription ends.

You can remove all roadmap data by removing the entire Roadmap solution from Microsoft 365. This will delete all of the existing roadmaps and associated user data.

1. In the [Microsoft 365 amin center](https://admin.microsoft.com), under **Admin centers**, click Dynamics 365.
2. In the Dynamics 365 Administraton Center, select the default instance, and then click **Open**.
3. On the **Settings** menu, under **Customization**, click **Solutions**.
4. Select the **PortfolioService** solution, and then click **Delete**.
5. Select the **PortfolioService_Anchor** solution, and then click **Delete**.

> [!NOTE]
> Removing the Roadmap solution does not affect any of the projects or tasks that the roadmaps are connected to.

## See Also

[Delete user data from Roadmap](delete-user-data-from-roadmap.md)
