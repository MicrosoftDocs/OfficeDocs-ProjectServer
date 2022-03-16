---
title: "Add a custom column to Project for the web"
ms.author: v-stthomas
author: v-stthomas
manager: alexla
ms.date: 3/15/2022
audience: admin
ms.service: project-web
ms.localizationpriority: medium
search.appverid: 
- PJO150
- PJO160
- MET150
description: "Learn how to add a custom column to a table in Project for the web and make it available on the associated form."
---

# Add a custom column to a table in Project for the web

When you need all the projects created in your Dataverse environment to accommodate a new piece of information, add a column to the appropriate table in Project Power App. If possible, [use an available built-in column](/powerapps/maker/model-driven-apps/add-move-or-delete-fields-on-form#create-a-new-column-on-the-table-when-editing-a-form). This article provides steps to add a column that isn't built-in: a custom column.

[!INCLUDE [p4w-required-roles.md](includes/p4w-required-roles.md)]

[!INCLUDE [p4w-solution-layers.md](includes/p4w-solution-layers.md)]

To create a custom table column for Project Power App, you have two choices:

- The Easy Way: Use the Power Apps portal, which has a nice, friendly UI. This article provides steps to use the Power Apps portal to add a custom column to a Dataverse table for Project Power App. However, some options aren't available.
- The Hard Way: If you need to use an option that's not available using the Power Apps portal, use the [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer).

> [!NOTE]
> Don't add a custom column to the Task table in Dataverse. Columns added to the Task table in Dataverse aren't available in Project for the web.

## Add a column to a table in Project Power App

1. Open the [Power Apps portal](https://make.powerapps.com/).
1. In the navigation pane, select **Dataverse** > **Tables**.
1. Find and select the table that needs a custom column.
1. On the command bar, select **+ Add column**.

   :::image type="content" source="media/AddColumn-OpenDialog.png" alt-text="Choose a table to add a column.":::

1. In the Set [column properties](column-properties) as needed. Properties that require a value have an asterisk next to their name.

   :::image type="content" source="media/ColumnPropertyQuickInfo.png" alt-text="Get quick info about a property.":::

### Column properties

| Area | Property | Description |
| --: | --: | --: |
| yada | bada | Bing |
