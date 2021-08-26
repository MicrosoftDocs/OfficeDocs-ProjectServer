---
title: "Add or edit enterprise custom lookup tables in Project Server"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 9/6/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: a7fafc9e-abb0-4318-a3ce-0ba8b296f1d8
description: "Summary: Use the New Custom Field page in Project Web App settings to specify the options for a custom lookup table."
---

# Add or edit enterprise custom lookup tables in Project Server
 
 **Summary:** Use the New Custom Field page in Project Web App settings to specify the options for a custom lookup table.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
Use the following procedure to create or edit an enterprise custom lookup table.
  
### To create or edit Enterprise Custom Lookup Tables

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Project Web App Server Settings page, click **Enterprise Custom fields and Lookup Tables**.
    
3. In the **Lookup Tables for Custom Fields** section, click **New Lookup Table** to create a new lookup table, or click the lookup table that you want to edit.
    
4. For a new table, type a name for the lookup table in the **Name** box.
    
5. Fill out the Custom Lookup Table page by specifying the options that you want to use. See the descriptions for each field in the following sections.
    
6. Click **Save**.
    
## Type

For a new lookup table, you must specify a data type for the table. It is not possible to mix field types in a table.
  
The following table describes the options for data types in a custom lookup table.
  
**Data types for custom lookup tables in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Cost** <br/> |Each field in the table is a cost value.  <br/> |
|**Date** <br/> |Each field in the table is a date value.  <br/> |
|**Duration** <br/> |Each value in the table is treated as a duration.  <br/> |
|**Number** <br/> |Each value in the table is a number.  <br/> |
|**Text** <br/> |Each value in the table is text. Choosing **Text** also allows a hierarchy of values to be specified if you want. <br/> |
   
## Code mask

The **code mask** option only appears when a field type of **Text** has been selected.
  
The code mask lets you specify what types of text characters appear in the lookup table, the length of the string, and what characters to use to separate levels in a hierarchy. If you are creating a hierarchical lookup table, you must specify a code mask for each level of the hierarchy.
  
The following table describes the options available for configuring code masks.
  
**Code mask settings for a custom lookup table in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Code preview** <br/> |Displays a preview of the code mask for the table.  <br/> |
|**Sequence** <br/> |Specify the type of text characters to allow. Choose **Numbers**, **Uppercase characters**, **Lowercase characters**, or **Characters**.  <br/> |
|**Length** <br/> |Specify the maximum length of the string. Choose a number from 1 to 255 or **Any**.  <br/> |
|**Separator** <br/> |Specify from one to three characters to use as a separator between levels of the table hierarchy.  <br/> |
   
## Lookup Table

Use the **Lookup Table** section of the New Lookup table page to specify the values in the lookup table.
  
Type each value that you want in the lookup table in the **Value** column. Create as many rows as needed to accommodate the values that you want to include. Optionally, include a description for the value in the **Description** column.
  
The following table describes the options for creating lookup table values.
  
**Lookup table values in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Level** <br/> |Denotes the level in the hierarchy. This is a read-only field. Select the row and use the Indent and Outdent buttons to change levels.  <br/> |
|**Value** <br/> |Specify the value of the field.  <br/> |
|**Description** <br/> |Describes what the field represents. (Optional)  <br/> |
|**Move** <br/> |Use the Move buttons to change the position of rows in the table. Select a row and then click the Up or Down Move button to move a row.  <br/> |
|**Display order for lookup table** <br/> |Specifies how to sort the lookup table. If you select **By row number**, the table remains sorted as you specify it. If you choose to sort ascending or descending, the table is sorted based on the values in the **Value** column. <br/> |
   
## See also

#### 

[Add or edit enterprise custom fields in Project Server](add-or-edit-enterprise-custom-fields-in-project-server.md)

