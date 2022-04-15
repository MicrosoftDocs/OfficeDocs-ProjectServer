---
title: Customize the Project Management Office Accelerator
description: Deploying the Accelerator to your Project for the web environment adds improved project management scenarios such as Project Requests, Changes, and Status.   
author: v-stthomas
ms.author: v-stthomas
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 4/15/2022
ms.custom: template-how-to
audience: admin
---

# Customize the Project Management Office Accelerator

After you [deploy the PMO Accelerator](deploy-project-for-web-accelerator-power-bi-template.md), consider creating a custom managed solution to add any extra functionality you want. The [Power BI template](deploy-power-bi-template-project-for-web-accelerator.md) is a great example: it adds significant reporting features to the PMO Accelerator, but merely deploying the template won't integrate the reports&mdash;you need to change some components to enable it, and a managed solution that you deploy on top of the Accelerator is the best way to make such changes.

## Prerequisites

- Admin rights in a development environment [with the Project Management Office Accelerator deployed](deploy-project-for-web-accelerator-power-bi-template.md)
- Rights to use the Common Data Service connector
- An understanding of [managed solution layers](/power-platform/alm/solution-layers-alm#layering-within-a-managed-solution)
- (Optional, but recommended) A [Developer plan](/power-apps/maker/developer-plan) so you can export your solution to easily deploy in other environments

## Create a managed solution to layer over the PMO Accelerator

> [!IMPORTANT]
> The order of events in this process is critical:
>
>  1. Select (or create) a development environment where you're an admin, and where Project for the web and the Accelerator solution are deployed&mdash;or deploy them, if they aren't there yet.
>  1. In that environment, create a managed solution that contains your customizations.
>  1. Export the solution, and then import it into your production Project+Accelerator environment.

## Example customization: add an action to send email when a Project Request is approved

The cloud flow included with the *Project Requests* scenario is very simple; it creates a project from a request when *Request State* is set to *Approved*. By adding an action to the cloud flow, you can make it also send an email notification.

1. Open the [Power Apps Portal](https://make.powerapps.com) and select your development environment.
1. In the list of solutions, select **Project Management Office Accelerator**.
1. In the navigation pane, select **Cloud Flows**.
1. Select **When the request state is updated to Approved** to open it.
1. On the command bar, select **Edit**.
1. Select **+ New step**.
1. Under **Choose an operation**, enter *Out* and then select **Office 365 Outlook**.

    :::image type="content" source="media/customize-project-accelerator-add-ol-connector.png" alt-text="Add the Outlook connector to your new flow step.":::

1. Select fields inside the connector to add content. Power Apps offers suggestions depending on the field you select. For example, when you select the **Subject** field you see attributes you can add. When the flow runs, the value of the attribute appears in the generated email.

    :::image type="content" source="media/customize-project-accelerator-ol-action-subject.png" alt-text="Power Apps suggesting attributes for the email Subject line.":::

1. Your Outlook step should look something like this example:

    :::image type="content" source="media/customize-project-accelerator-ol-action-ready.png" alt-text="Example Outlook step in a customized cloud flow.":::

1. Save and close the flow.
1. On the command bar, select **Publish all customizations**.

## Disable the flow

1. Open the [Power Apps Portal](https://make.powerapps.com).
1. In the navigation pane, select **Solutions**, and then select **Project Management Office Accelerator**.
1. In the navigation pane, select **Cloud Flows**.
1. Select the **When the request state is updated to Approved** flow. Then, on the command bar select the ellipses (**...**) and then select **Turn Off**.

    :::image type="content" source="media/customize-project-accelerator-turn-off-flow.png" alt-text="Turn off the flow":::

1. On the command bar, select **Publish all customizations**.

## Next Steps

- Learn more about [Solution layers](/power-apps/maker/data-platform/solution-layers).
- Understand [application lifecycle management (ALM) with Micrfosoft Power Platform](/power-platform/alm/overview-alm)
