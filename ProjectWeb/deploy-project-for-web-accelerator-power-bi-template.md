---
title: Deploy the Project Management Office Accelerator
description: Deploying the Accelerator to your Project for the web environment adds improved project management scenarios such as Project Requests, Changes, and Status.   
author: v-stthomas
ms.author: v-stthomas
manager: deniseb
ms.service: project-web
ms.topic: how-to
ms.date: 3/21/2022
ms.custom: template-how-to
audience: admin
---

# Deploy the Project Management Office Accelerator

Although people in your organization can start using Project for the web as soon as you subscribe to Microsoft 365, you'll probably want to customize the environment to meet your specific business needs. Save time with several common scenarios by deploying the Project Management Office Accelerator (PMO Accelerator).

## Prerequisites

- Admin rights in an environment with the [deployed Project for the web solution](/project-for-the-web/deploying-project).
- Rights to create Power Automate flows using the [Common Data Service connector](/connectors/commondataserviceforapps/).

## Deploy the Accelerator

1. Download the [Accelerator](/OfficeDev/Project-Accelerator/blob/main/README#heres-the-latest-version-of-the-accelerator) and save it locally. Don't unpack it&mdash;the import process uses the zipped file.
1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Open the **Environment** menu and select your Project for the web environment.

    :::image type="content" source="media/environment-menu.png" alt-text="The Power Apps Portal Environment menu.":::

1. In the navigation pane, select **Solutions**.
1. On the command bar, select **Import**.
1. In the **Import a solution** dialog, select **Browse**, then find and select the Accelerator file you downloaded.
1. Select **Next**, then select an existing connection to a Power Automate flow, or create a new connection.
1. Select **Next** and then select **Import**.

When deployment succeeds, the Project Power App will resemble this:

:::image type="content" source="media/project-with-the-accelerator.png" alt-text="The Project Power App after the PMO Accelerator is deployed.":::

## Use the Accelerator components without Project for the web

You may reuse the Accelerator components in your own applications, per the [LICENSE](/OfficeDev/Project-Accelerator/blob/main/LICENSE). Using the Accelerator with the Project Power App or using the Project for the web tables employed by the Accelerator is only permitted according the to terms of your Project plan and subscriptions.

## Resolve error messages that appear during deployment

The following table lists known errors that sometimes appear while you are deploying the Accelerator solution, and provides steps to resolve them. If the steps don't resolve the error, you can [get support from Microsoft](#accelerator-support-options).

| Error message | Fix |
| :-- | :-- |
| **There are missing dependencies. Install the following solutions before installing this one: "msdyn_ProjectServiceCore (1.0.0.87)".** | In the environment where you're deploying the Accelerator, select **Solutions** in the navigation pane. Find the *Project Service Core* solution, and then select **Update** next to the solution name. After the update is complete, deploy the Accelerator solution. |
| **Failed to activate component(s). Flow save failed with code OpenApiOperationParameterValidationFailed and message Input parameter item validation failed in workflow operation...** | [Resolve flow errors](#resolve-flow-errors). |
| **Flow save failed with code OpenApiOperationParameterValidationFailed and message Input parameter item validation failed in workflow operation Create_a_new_record: The API operation 'CreateRecord' is missing required property item/msdyn_schedulemode.** | [Resolve flow errors](#resolve-flow-errors). |

### Resolve flow errors

1. Open the [Power Apps Portal](https://make.powerapps.com).
1. Open the **Environment** menu and select your Project for the web environment.

    :::image type="content" source="media/environment-menu.png" alt-text="The Power Apps Portal Environment menu.":::

1. In the navigation pane, select **Solutions**.
1. Open the Project Accelerator solution, and then in the navigation pane select **Cloud flows**.
1. Select **When a Request State is Updated...**.
1. On the command bar, select **Edit**.
1. Select the **Condition** step.
1. In the **If yes** condition, select **Create a new record**.

    :::image type="content" source="media/deploy-project-accelerator-if-yes-create-record.png" alt-text="Select the action to edit it.":::

1. Set **Scheduling Mode** to **Fixed Duration**.
1. On the command bar, select **Save**, and then select the back arrow on the far left.

    :::image type="content" source="media/deploy-project-accelerator-back-arrow.png" alt-text="Select the back arrow after you're done editing.":::

1. Select **When a Request State is Updated...**.
1. On the command bar, select **Turn On**, and then select the back arrow on the far left.
1. On the command bar, select **Publish all customizations**.

## Support and Troubleshooting

Microsoft fully supports the deployment and use of the Accelerator with Project for the web. Although we don't support any customizations added on top of the Accelerator, we do support the core functionality in such circumstances.

### Accelerator support options

- Open a new service request through the Microsoft 365 admin center Support tab.
- Raise an [issue in Github](https://github.com/OfficeDev/Project-Accelerator/issues).

## Next Steps

- [Create a managed solution to add the Power BI template to the Project Management Office Accelerator](deploy-power-bi-template-project-for-web-accelerator.md).
- [Learn more about scheduling modes](https://techcommunity.microsoft.com/t5/project-support-blog/schedule-modes-and-task-and-resource-usage-in-project-for-the/ba-p/2656738).
