---
title: "Add a custom column to the Project Power App"
ms.author: v-stthomas
author: v-stthomas
manager: alexla
ms.date: 3/15/2022
audience: admin
ms.service: project-web
ms.topic: how-to
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

- The [Power Apps portal](https://make.powerapps.com/) has a nice, friendly UI. This article provides steps to use the Power Apps portal to add a custom column to a Dataverse table for Project Power App. It's convenient and suitable most of the time, but a few options aren't available.
- The [Power Apps solution explorer](/powerapps/maker/data-platform/create-edit-field-solution-explorer) provides advanced options that aren't available on the Power Apps portal.

> [!NOTE]
> Don't add a custom column to the Task table in Dataverse. Columns added to the Task table in Dataverse aren't available in the Tasks tab of the Project Power App.

## Add a custom column using the Power App portal

1. Open the [Power Apps portal](https://make.powerapps.com/).
1. In the navigation pane, select **Dataverse** > **Tables**.
1. Find and select the table that needs a custom column.

   > [!TIP]
   > The table you want might not be listed by default. Use the item filter on the command bar to choose the type of items Power Apps lists.

   :::image type="content" source="media/add-custom-column-project-power-app-06.png" alt-text="Use the item filter on the command bar to choose the type of items Power Apps lists.":::

1. On the command bar, select **+ Add column**.
1. In the **Column properties** pane, set the [column properties](#column-properties) as needed. Properties that require a value have an asterisk next to their name.

   :::image type="content" source="media/add-custom-column-project-power-app-03.png" alt-text="For a quick reminder of a property’s effect, select the info icon beside its name.":::

1. After you set all the properties you need, select **Done** at the bottom of the **Column properties** pane to save the new column.

### Column properties

| **Property** | **Description** |
| --: | --: |
| **Display Name** | Text that appears next to and identifies the column in the user interface. |
| **Name** | Provides a unique name for the column across your environment. An automatically generated name appears when you enter a display name, but you can edit the value before you save the column properties. After you save the column properties when you create the column, its name can’t be changed. The name always has the customization prefix for your Dataverse Default Publisher. |
| **Data type** | Controls how values are stored, and in some applications how they're formatted. After you save the column properties, you can't change the data type. Exception: you can convert text columns to autonumber columns. |
| **Required** | A row can't be saved without data in this column. For more information, see [Saving rows programmatically for required columns](/powerapps/maker/data-platform/create-edit-field-portal#saving-rows-programmatically-for-required-columns). |
| **Searchable** | Controls whether the column appears in Advanced Find and is available when customizing views. |
| **Calculated or Rollup** | Use to automate manual calculations. Use values, dates, or text. |
| **Advanced Options** | Add a description, and specify a maximum length and IME mode for the column. |

> [!NOTE]
> Other properties may become available when you set a value for **Data type**.

## Example: Add a *Budget* column to the *Project* table

Anita Montero has determined that her business has grown complex enough to require more granular accounting. She needs to start allocating funds at the Project level. There's no built-in column that works for her, so she's adding a custom column to the Project Power App using the [Power Apps portal](https://make.powerapps.com/).

She opens the *Project* table and verifies it's not a Managed or a System table, so it's safe to change.

:::image type="content" source="media/add-custom-column-project-power-app-04.png" alt-text="Make changes in your Development environment first, so you can ensure they work as expected before you deploy them in your Production environment. Make sure that a table isn’t a Managed or System table before you try to make arbitrary changes to it.":::

She adds the new column, names it *Budget*, and sets **Data type** to *Currency*.

:::image type="content" source="media/add-custom-column-project-power-app-05.png" alt-text="The Currency data type supports financial calculations.":::

Because there are already some projects underway, she sets **Required** to *Recommended*. She leaves **Searchable** selected so she can easily find projects that don't have a value for *Budget* yet, and so people can use the column in Advanced Find operations.

Ready to start allocating funds, at the bottom of the pane, Anita selects **Done**.

:::image type="content" source="media/add-custom-column-project-power-app-08.png" alt-text="Select Save Table after adding a column.":::

The *Budget* column is now visible in the *Project* table. Anita selects **Save Table**.

After saving, Anita notices there's another new column, right under *Budget*: *Budget (Base)*. It's an automatic column that shows the value of *Budget* in terms of the base currency defined for her app. Power Platform adds one when you [add a column with the Currency data type](/powerapps/maker/data-platform/types-of-fields#using-currency-columns).

:::image type="content" source="media/add-custom-column-project-power-app-09.png" alt-text="When you add a column with the Currency data type, Power Platform adds another column that calculates the column’s values in the base currency for your app.":::

## Add a form field to the *Information* form

After you add a custom column to the Project Power App, you should add it the *Information* form as a field. Most people won't be using the tables directly&mdash;they'll use the *Information* form to work with project data.

1. After you save the table, select the **Forms** area.
1. Select the *Information* form. You might have to adjust the view's filter to find it.

   :::image type="content" source="media/add-custom-column-project-power-app-10.png" alt-text="Switch to the Forms area after you add a custom column. Select the form where you want to make the column available.":::

1. On the command bar, select **+ Form field**.

   :::image type="content" source="media/add-custom-column-project-power-app-11.png" alt-text="When you select + Form field, the Table columns pane opens. By default, only unused columns appear in the Table columns pane.":::

1. Because you haven't added the column to a form yet, it's listed in the **Table columns** pane. Drag it from the pane onto the form to add it as a field in the **General** section. If you want it in a specific place, drop it where you want it to appear. You can adjust the size and position of the new filed as needed.

   :::image type="content" source="media/add-custom-column-project-power-app-12.png" alt-text="When you drag a field onto a form, it’s added to the General section unless you drop it somewhere else.":::

1. On the command bar, select **Save**.
1. When you're ready to roll out your changes to the environment you're in, on the command bar, select **Publish**.

   :::image type="content" source="media/add-custom-column-project-power-app-13.png" alt-text="After you publish your changes, the new field appears in every project in the same environment.":::

## Next Steps

- Consider whether you should create or adjust any [business process flows](/power-automate/business-process-flows-overview) for your new column.
- If the new form field requires it, add or change [business rules](/powerapps/maker/model-driven-apps/create-business-rules-recommendations-apply-logic-form).
- If the new column will require associated Dataverse actions when its values change, implement them using [Power Automate](/power-automate/connection-cds).
- Consider [adding the new column to your Power BI template for Project](https://support.microsoft.com/office/extend-the-power-bi-template-for-project-for-the-web-23fb86a7-e1b2-45fc-b82b-8f64ae44c51c). Adding it to your Power BI template makes it part of reports that use the template.
