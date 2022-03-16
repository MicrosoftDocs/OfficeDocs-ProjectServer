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

1. In the **Column properties** pane, set the [column properties](column-properties) as needed. Properties that require a value have an asterisk next to their name.

   :::image type="content" source="media/ColumnPropertyQuickInfo.png" alt-text="Get quick info about a property.":::

### Column properties

| **Property** | **Description** |
| --: | --: |
| **Display Name** | Text that appears next to and identifies the column in the user interface. |
| **Name** | Provides a unique name for the column across your environment. An automatically-generated name appears when you enter a display name, but you can edit the value before you save the column properties. After you save the column properties when you create the column, its name cannot be changed. The name always has the customization prefix for your Dataverse Default Publisher. |
| **Data type** | Controls how values are stored, and in some applications how they are formatted. After you save the column properties, you can't change the data type. Exception: you can convert text columns to autonumber columns. |
| **Required** | A row can't be saved without data in this column. For more information, see [Saving rows programmatically for required columns](/powerapps/maker/data-platform/create-edit-field-portal#saving-rows-programmatically-for-required-columns). |
| **Searchable** | Controls whether the column appears in Advanced Find and is available when customizing views. |
| **Calculated or Rollup** | Use to automate manual calculations. Use values, dates, or text. |
| **Advanced Options** | Add a description, and specify a maximum length and IME mode for the column. |

> [!NOTE]
> Other properties may become available when you set a value for **Data type**.
