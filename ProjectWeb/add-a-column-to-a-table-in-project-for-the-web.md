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
description: "Learn how to add a custom column to a table in the Project Power App and make it available on the associated form to people in your environment using Project for the web."
---

# Add a custom column to Project for the web

When you need all the projects created in your Dataverse environment to accommodate a new piece of information, add a column to the appropriate table in Project Power App. After you make the new column available on the associated form, people using Project for the web will be able to use the column in their projects.

If possible, [use an available built-in column](/powerapps/maker/model-driven-apps/add-move-or-delete-fields-on-form#create-a-new-column-on-the-table-when-editing-a-form). This article provides steps to add a column that isn't built-in: a custom column.

[!INCLUDE [p4w-required-roles.md](includes/p4w-required-roles.md)]

[!INCLUDE [p4w-solution-layers.md](includes/p4w-solution-layers.md)]

To create a custom table column in Project Power App, you have two choices:

- The Convenient method: Use the Power Apps portal, which has a nice, friendly UI. This article provides steps to use the Power Apps portal to add a custom column to a Dataverse table for Project Power App. It's convenient and suitable most of the time, but a few options aren't available.
- The Full Control method: If you need an option that's not available with the Power Apps portal, use the [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer).

> [!NOTE]
> Don't add a custom column to the Task table in Dataverse. Columns added to the Task table in Dataverse aren't available in Project for the web.

## Add a custom column to a table in Project Power App

1. Open the [Power Apps portal](https://make.powerapps.com/).
1. In the navigation pane, select **Dataverse** > **Tables**.
1. Find and select the table that needs a custom column.

   > [!TIP]
   > You might not see the table you want by default. Use the item filter on the command bar to choose the type of items you see.

   :::image type="content" source="media/CommandBar-ItemFilter.png" alt-text="Choose the type of items you see.":::

1. On the command bar, select **+ Add column**.
1. In the **Column properties** pane, set the [column properties](column-properties) as needed. Properties that require a value have an asterisk next to their name.

   :::image type="content" source="media/ColumnPropertyQuickInfo.png" alt-text="Get quick info about a property.":::

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

Anita Montero has determined that her business has grown complex enough to require more granular accounting. She needs to start allocating funds at the Project level. She checked and didn't see a built-in column for this, so she's changing the Project Power App in the Power Apps portal.

She opens the Project table and verifies it's not a Managed or a System table. If it were, she'd have to reconsider her plan.

:::image type="content" source="media/AddColumn-BudgetExample.png" alt-text="The Project table isn't Managed or a System table.":::

She adds the new column, names it *Budget*, and sets **Data type** to *Currency*.

:::image type="content" source="media/AddColumn-ExampleCurrencyDataType.png" alt-text="The Currency data type supports calculations.":::

Because there are already some projects underway, she sets **Required** to *Recommended*. She leaves **Searchable** selected so she can easily find projects that don't have a value for *Budget* yet, and so people can use the column in Advanced Find operations. Although calculations will be done using the value of *Budget*, the column itself isn't calculated or a roll-up: Anita will use it to set the total amount of funds allocated to a project. She's planning to add other fields that will use *Budget* in calculations.

Anita selects **Advanced Options**, considers the choices, and sets them accordingly.

:::image type="content" source="media/AdvancedOptions-BudgetColumnExample.png" alt-text="Advanced Options for a column with the Currency data type.":::

Ready to start allocating funds, at the bottom of the pane, Anita selects **Done**.

:::image type="content" source="media/AddColumn-SaveTable.png" alt-text="Select Save Table after adding a column.":::

The *Budget* column is now visible in the *Project* table. Anita selects **Save Table**.

After saving, Anita notices there's another new column, right under *Budget*: *Budget (Base)*. It's an automatic column that shows the value of *Budget* in terms of the base currency defined for her app. Power Platform adds one when you [add a column with the Currency data type](/powerapps/maker/data-platform/types-of-fields#using-currency-columns).

:::image type="content" source="media/AddColumn-CurrencyAutoBase.png" alt-text="Automatic new column showing the Budget in terms of the app's base currency.":::

## Add a new column to its table's forms

After you add a custom column to a table in Project Power App, you probably want to make it available to people who use Project for the web in your environment. Most people won't be using the tables directly&mdash;they'll use forms to work with their projects. Here's how to add your new column to a Project Power App form using the Power App portal.

1. After you save the table, select the Forms area.
1. Select the form where you want to make the new column available. You might have to adjust the view's filter to see the form you want.

   :::image type="content" source="media/AddColumn-PutItOnAForm.png" alt-text="Select a form for making the new column available.":::

1. On the command bar, select **+ Form field**.
1. Drag the new field from the **Table columns** pane onto the form. If you want it in a specific place, drop it there&mdash;otherwise it appears in the **General** section.

   :::image type="content" source="media/AddColumn-DragFieldToForm.png" alt-text="Drag a field onto the form.":::
