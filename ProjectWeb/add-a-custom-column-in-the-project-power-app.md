---
title: "Add a custom column to the Project Power App"
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
description: "Learn how to add a custom column in the Project Power App that can be used across all your projects."
---

# Add a custom column to the Project Power App

When you need to add a column to use in your projects but none of the [available built-in columns](/powerapps/maker/model-driven-apps/add-move-or-delete-fields-on-form#create-a-new-column-on-the-table-when-editing-a-form) meet your need, create a custom column.

[!INCLUDE [p4w-required-roles.md](includes/p4w-required-roles.md)]

[!INCLUDE [p4w-solution-layers.md](includes/p4w-solution-layers.md)]

To create a custom table column in Project Power App, you have two choices:

- The Convenient method: Use the Power Apps portal, which has a nice, friendly UI. This article provides steps to use the Power Apps portal to add a custom column to a Dataverse table for Project Power App. It's convenient and suitable most of the time, but a few options aren't available.
- The Full Control method: If you need an option that's not available with the Power Apps portal, use the [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer).

> [!NOTE]
> Don't add a custom column to the Task table in Dataverse. Columns added to the Task table in Dataverse aren't available in the Tasks tab of the Project Power App.

## Add a custom column using the Power App portal

1. Open the [Power Apps portal](https://make.powerapps.com/).
1. In the navigation pane, select **Dataverse** > **Tables**.
1. Find and select the table that needs a custom column.

   > [!TIP]
   > The table you want might not be listed by default. Use the item filter on the command bar to choose the type of items Power Apps lists.

   :::image type="content" source="media/add-a-custom-column-in-the-project-power-app-06.png" alt-text="Use the item filter on the command bar to choose the type of items Power Apps lists.":::

1. On the command bar, select **+ Add column**.
1. In the **Column properties** pane, set the [column properties](column-properties) as needed. Properties that require a value have an asterisk next to their name.

   :::image type="content" source="media/add-a-custom-column-in-the-project-power-app-03.png" alt-text="For a quick reminder of a property’s effect, select the info icon beside its name.":::

1. After you set all the properties you need, select **Done** at the bottom of the **Column properties** pane to save the new column.

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

## Example: Add a *Budget* column to the *Project* table

Anita Montero has determined that her business has grown complex enough to require more granular accounting. She needs to start allocating funds at the Project level. She checked and didn't see a built-in column for this, so she's changing the Project Power App using the [Power Apps portal](https://make.powerapps.com/).

She opens the Project table and verifies it's not a Managed or a System table. If it were, she'd have to reconsider her plan.

:::image type="content" source="media/add-a-custom-column-in-the-project-power-app-04.png" alt-text="Make changes in your Development environment first, so you can ensure they work as expected before you deploy them in your Production environment. Make sure that a table isn’t a Managed or System table before you try to make arbitrary changes to it.":::

She adds the new column, names it *Budget*, and sets **Data type** to *Currency*.

:::image type="content" source="media/add-a-custom-column-in-the-project-power-app-05.png" alt-text="The Currency data type supports financial calculations.":::

Because there are already some projects underway, she sets **Required** to *Recommended*. She leaves **Searchable** selected so she can easily find projects that don't have a value for *Budget* yet, and so people can use the column in Advanced Find operations.

Ready to start allocating funds, at the bottom of the pane, Anita selects **Done**.

:::image type="content" source="media/add-a-custom-column-in-the-project-power-app-08.png" alt-text="Select Save Table after adding a column.":::

The *Budget* column is now visible in the *Project* table. Anita selects **Save Table**.

After saving, Anita notices there's another new column, right under *Budget*: *Budget (Base)*. It's an automatic column that shows the value of *Budget* in terms of the base currency defined for her app. Power Platform adds one when you [add a column with the Currency data type](/powerapps/maker/data-platform/types-of-fields#using-currency-columns).

:::image type="content" source="media/add-a-custom-column-in-the-project-power-app-09.png" alt-text="When you add a column with the Currency data type, Power Platform adds another column that holds the calculation of the value in the column you added, in terms of the base currency for your app.":::

## Add a form field for a new column

After you add a custom column to the Project Power App, you should add it to a form as a field. Most people won't be using the tables directly&mdash;they'll use form fields to work with project data.

1. After you save the table, select the **Forms** area.
1. Select the form where you want to make the new column available. You might have to adjust the view's filter to find the form you want.

   :::image type="content" source="media/add-a-custom-column-in-the-project-power-app-10.png" alt-text="Switch to the Forms area after you add a custom column. Select the form where you want to make the column available.":::

1. On the command bar, select **+ Form field**.
1. Drag the new field from the **Table columns** pane onto the form. If you want it in a specific place, drop it there&mdash;otherwise it appears in the **General** section.

   :::image type="content" source="media/add-a-custom-column-in-the-project-power-app-11.png" alt-text="When you select + Form field, the Table columns pane opens. By default, unused columns appear in the Table columns pane.":::

   :::image type="content" source="media/add-a-custom-column-in-the-project-power-app-12.png" alt-text="When you drag a field onto a form, it’s added to the General section unless you drop it somewhere else.":::
