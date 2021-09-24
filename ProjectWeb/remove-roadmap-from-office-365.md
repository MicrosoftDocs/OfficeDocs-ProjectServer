---
title: "Remove Project from Microsoft 365"
ms.author: serdars
author: serdars
manager: serdars
audience: admin
ms.topic: article
ms.service: project-web
ms.localizationpriority: medium
ms.custom: Adm_Project
search.appverid: 
- PJO150
- MET150
description: "Remove Roadmap from Microsoft 365."
---

# Remove Project for the web or Roadmap from Microsoft 365

You can turn Project for the web or Roadmap off in the Microsoft 365 admin center. This setting prevents your users from using them, but will not remove any user data that currently exists. 

> [!NOTE]
> It may take a few minutes for functionality to be disabled while the setting synchronizes across your tenant.

**To turn off Project for the web:**

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Settings**, click **Org settings**.
2. Click **Project**.
3. Uncheck **Turn on Project for the web**.
4. Click **Save**.

> [!NOTE]
> Although this setting currently displays in your Project settings, it will not be enabled until a later date (see your Message Center). You can still [turn off Project for the web for individual users](turn-project-for-the-web-off.md). 

**To turn off Roadmap:**

1. In the [Microsoft 365 admin center](https://admin.microsoft.com), under **Settings**, click **Org settings**.
2. Click **Project**.
3. Uncheck **Turn on Roadmap for your organization**.
4. Click **Save**.

If your Project Online subscription ends, most of the associated data is deleted in conformance with the [Data retention, deletion, and destruction in Microsoft 365](/compliance/assurance/assurance-data-retention-deletion-and-destruction-overview). Unlike other Project Online data, Project for the web and Roadmap data isn’t automatically deleted when your Project Online subscription ends.

## Remove Project for the web and Roadmap data

You can remove all Project for the web and Roadmap data by removing the entire solution from Microsoft 365. This removal deletes all of the existing projects, roadmaps, and associated user data.

**To remove Roadmap:** (Only applies to the default org as Roadmap can only be installed on the default org)

1. In the [Microsoft 365 App Launcher](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a), click **Power Apps** (or as an alternative, you can go to [https://make.powerapps.com/](https://make.powerapps.com/)).

   > [!TIP]
   > If you're looking up a named organization, ensure that you pick the correct **named organization**.

2. Click on the settings icon on the top right of the page and go to **Advanced Settings**.
3. On the **Settings** menu, under **Customization**, click **Solutions**.
4. Select the **PortfolioService** solution, and then click **Delete**.
5. Select the **PortfolioService_Anchor** solution, and then click **Delete**.
6. Select any solutions with a naming format of **PortfolioService_Patch_(number)**, (for example, PortfolioService_Patch_1 or PortfolioService_Patch_2), and then click **Delete**.

> [!NOTE]
> Removing the Roadmap solution does not affect any of the projects or tasks that the roadmaps are connected to.


**To remove Project for the web:**

1. In the [Microsoft 365 App Launcher](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a), click **Power Apps** or you can browse directly to it by going to: [https://make.powerapps.com/](https://make.powerapps.com/).
2. Ensure that the correct org where you want to remove Project for the web is displayed at the top of the page. In most cases, it will be the default org if you have an out-of-box installation. 
3. Click on the settings icon on the top right of the page and go to **Advanced Settings**.
4. On the **Settings** menu, under **Customization**, click **Solutions**.
5. Select the **msdyn_ProjectServiceCore** solution, and then click **Delete**.
6. Select the **msdyn_ProjectServiceCore_Anchor** solution, and then click **Delete**.
7. Select the **MicrosoftDynamicsScheduling** solution, and then click **Delete**.
8. Select any solutions with a naming format of **msdyn_ProjectServiceCore_Patch_(number)**, (for example, msdyn_ProjectServiceCore_Patch_1 or msdyn_ProjectServiceCore_Patch_2), and then click **Delete**.
## See Also

[Delete user data from Project for the web](delete-user-data-from-project-for-the-web.md)
