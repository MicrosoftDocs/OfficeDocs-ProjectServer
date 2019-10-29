---
title: "Project for the web setup requirements for Dynamics 365 business units"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: project-web
search.appverid: PJO150
localization_priority: Normal
description: "Learn how to assign the Project User role to a Dynamics 365 business unit's team."
---

# Project for the web setup requirements for Dynamics 365 business units

In Dynamics 365, you can create additional [business units](https://docs.microsoft.com/power-platform/admin/create-edit-business-units) in your Common Data Service (CDS) instance.  If you want Project for the web users in the business unit to be able to access and use it, you need to made sure that the associated team in which your users are members have the **Common Data Service User** and **Project User** roles applied to it.

> [!NOTE]
> You only need to do this if you add a new business unit to your default CDS instance. This will automatically be applied to your root business unit's team settings.

## To apply the Project User role to a business unit

> [!NOTE]
> You must be a Global Admin to do this.

1. In the Dynamics 365 Administration Center, for your default instance, click **Open**.
2. On the PowerApps Settings Apps page, click **Project**.
3. On the Project page, click the gear icon in the toolbar and click **Advanced Settings**.
4. On the Dynamics 365 Settings page, click the **Settings** menu in the toolbar, and in the **Systems** section, select **Security**.
5. On the Security page, select **Teams**.
6. Select the team for your business unit from the **Team Name** column, and then click **Manage Roles** in the toolbar.
7. In the Manage Team Roles screen, select **Project User** and **Common Data Service User**, and then click **OK**.<br/>

   


## See Also

[Create or edit business units](https://docs.microsoft.com/power-platform/admin/create-edit-business-units)
  
  



