---
title: "Add or edit enterprise custom fields in Project Server"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 9/6/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.assetid: 19ad76d0-3d4f-41a3-a726-869c371e66ff
description: "Summary: Use the New Custom Field page in Project Web App settings to specify the options for a custom field."
---

# Add or edit enterprise custom fields in Project Server
 
 **Summary:** Use the New Custom Field page in Project Web App settings to specify the options for a custom field.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
Use the following procedure to create a new enterprise custom field or edit an existing one.
  
### To create or edit Enterprise Custom Fields

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Project Web App Server Settings page, click **Enterprise Custom fields and Lookup Tables**.
    
3. In the **Enterprise Custom Fields** section, click the field that you want to edit, or click **New Field** to create a new field.
    
4. Fill out the Custom Field page by specifying the custom field options that you want to use. See the descriptions for each field in the following sections.
    
5. Click **Save**.
    
## Name and Description

Use the **Name** and **Description** areas to specify a name and description for the custom field. The following table describes the name and description fields.
  
> [!NOTE]
> If you plan to use custom fields in your OLAP cubes, avoid using non-alphanumeric characters in the name. 
  
**Name and Description attributes for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Name** <br/> |The name of the custom field.  <br/> |
|**Description** <br/> |A description of the custom field.  <br/> |
   
## Entity and Type

Use the **Entity** and **Type** areas to specify whether you want a Project, Resource, or Task custom field, and what data type the field should be. Note that Entity and Type cannot be edited after the custom field has been saved.
  
The following table describes each available entity.
  
**Entity options for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Project** <br/> |Select to create Enterprise Custom Fields that are applied at the project level.  <br/> |
|**Resource** <br/> |Select to create Enterprise Custom Fields that are applied at the resource level.  <br/> |
|**Task** <br/> |Select to create Enterprise Custom Fields that are applied at the task level.  <br/> |
   
The **Type** selection defines the data type of the custom field. The value that you choose here affects which options are available in the Custom Attributes, Calculation for Summary Rows, and Behavior sections. The following table describes the available custom field types.
  
**Type attributes for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Cost** <br/> |Use custom cost fields to define currency data. For example, you can use a custom cost field to define a project's Approved Budget.  <br/> |
|**Date** <br/> |Use custom date fields to specify date-driven data. For example, you can create an Enterprise Custom Field called Project Approval Date and use it to record the date on which a project is approved.  <br/> |
|**Duration** <br/> |Use custom duration fields to define a duration. These are frequently defined as calculations that use custom formulas. For example, a custom duration field can enable your organization to define a way for a project manager to show and store the difference between a project's original schedule and the actual schedule.  <br/> |
|**Flag** <br/> |Use custom flag fields to define anything that can have only two choices for defining the data. For example, you might use a flag field to determine whether to display a field or to enable a macro that controls whether a particular set of data is available in the project.  <br/> |
|**Number** <br/> |Use custom number fields to define any numeric set of data or to perform a custom calculation by using a custom formula. For example, you might use a task-level field to record the estimated lines of code in a software development project or to compare a project's actual cost to its proposed cost.  <br/> |
|**Text** <br/> |Use custom text fields to define simple, non-hierarchical, alphanumeric data. For example, you can create a custom text field that is named Project Status that includes options such as Initiated, Approved, In-Progress, Suspended, Cancelled, and Closed.  <br/> |
   
## Custom attributes

When you select a Project Text custom field, you have the option of specifying one or multiple lines of text for the custom field.
  
The following table describes the custom text options.
  
**Custom text attributes for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Single line of text** <br/> |Select if you want the custom field to be a single line of text. This option is available only for Project Text fields.  <br/> |
|**Multiple lines of text** <br/> |Select if you want the custom field to be multiple lines of text. This option is available only for Project Text fields. The project field created by using this option is not visible in the project information tab in Project Professional. However, this field can be exposed by using a Web-based Project Detail Page.  <br/> |
   
You can choose to have a custom lookup table supply the values for a custom field. This lets you control the values selected for the custom field. You can do the following:
  
- Choose whether to have a default value if no other value is selected
    
- Choose whether to allow multiple values to be selected from the lookup table
    
- Choose to restrict available values to those values in the table that have no subordinates
    
The lookup table option is available when you have selected Text as the field type.
  
The following table describes the lookup table options for custom fields.
  
**Lookup table attributes for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Lookup Table** <br/> |The name of the Enterprise Custom Lookup Table that you want to associate with this custom field. Once you have associated a lookup table with a field and have saved it, you cannot remove the lookup table relationship. Therefore, make sure that you need the lookup table before you make this association.  <br/> |
|**Choose a value to use as a default when adding new items** <br/> |If you want to have a default value included in this custom field in cases where the user does not specify one, select this check box, and then select the default value.  <br/> |
|**Default value** <br/> |The default value to be used in this field when users do not specify a value. To set the value, click the browse button and select the desired value.  <br/> |
|**Only allow codes with no subordinate values** <br/> |Select this option if you want to allow only values in the lookup table that have no subordinate values (that is, values at the lowest level of each branch).  <br/> |
|**Allow multiple values to be selected from lookup table** <br/> |Select this option if you want to allow users to select more than one value from the lookup table. Once this selection has been made and saved, it cannot be removed. This option is not compatible with OLAP cubes.  <br/> |
   
> [!NOTE]
> If you plan to create a custom field that refers to a lookup table, create the lookup table before creating the custom field. 
  
You can use formulas to define your own parameters for how your Enterprise Custom Fields measure data or present information when they are used in a project. Formulas cannot be used with all types of Enterprise Custom Fields.
  
The formula option is available with all field types.
  
> [!NOTE]
> Once a formula is associated with a custom field, it can be edited but it cannot be removed. 
  
- To use a known formula, type the formula in the **Edit formula** box.
    
- To add a field to the formula, click **Pick field**, point to a field type, and then click the name of the field that you want to reference. To reference an existing Enterprise Custom Field, point to a field type, point again to a custom field type (such as Custom Date or Custom Finish), and then click the Enterprise Custom Field that you want.
    
- To use a function in the formula, click **Pick function**, click a function type, and then click the function that you want. Each function includes placeholder arguments that you can replace with the fields and values that you want to use.
    
- To build a formula by using a standard set of operators, click **Pick operator** and choose the operator that you need. The formula can operate by using referenced fields, functions, or literal data.
    
The following table describes the formula options.
  
**Formula attributes for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Enter formula** <br/> |The formula you want to use.  <br/> |
|**Insert field** <br/> |Inserts a field (cost, date, duration, flag, number, or text) into the formula.  <br/> |
|**Insert function** <br/> |Inserts a function (conversion, date/time, general, math, Microsoft Project, or text) into the formula.  <br/> |
|**Insert operator** <br/> |Inserts an operator (mathematical or Boolean) into the formula.  <br/> |
   
## Department

You can select a department to be associated with a custom field. Selecting a department allows you to limit a user's ability to see the custom field if that person is not a member of that department. If you do not specify a department, then all users are able to see the custom field.
  
The values available for **Department** are specified in the Department custom lookup table.
  
## Calculation for summary rows

For entity types of Resource and Task, you can select options for the calculation of summary rows.
  
Note that summary row calculation is not available with a field type of Text.
  
The following table describes the options for summary task calculation.
  
**Summary task calculation options for custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**None** <br/> |Choose **None** if you do not want the custom field to be applied to summary and group summary rows. <br/> |
|**Rollup** <br/> |Choose **Rollup** to roll up the individual rows for the summary row. <br/> |
|**Use formula** <br/> |Choose **Use formula** to use a specific formula to calculate the summary row. You must specify the formula to use under **Custom Attributes**.  <br/> |
   
## Calculation for assignment rows

For resource types of Resource and Task, you choose to use a roll down calculation for assignment rows.
  
The following table describes the options for calculating assignment rows.
  
**Assignment row calculation options in custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**None** <br/> |Choose **None** if you do not want to roll down assignment rows. <br/> |
|**Roll down, unless manually specified** <br/> |Choose **Roll down** if you want data that is entered at the task or resource level to be rolled down and copied to each assignment with the same value. <br/> |
   
## Values to display

You can choose to display raw data or to have the data represented graphically.
  
If you select **Graphical indicators**, you can select different criteria for Non-summary rows, Summary rows, and, if you are using an entity type of Project, Project summary.
  
When you select an option, further configurable parameters specific to that option are displayed.
  
The following table describes the options for graphical indicators.
  
**Graphical indicator options in custom fields in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Non-summary rows** <br/> |Choose **Non-summary rows** to specify criteria for graphical representation of data rows that are not summary rows. <br/> |
|**Summary rows** <br/> |Choose **Summary rows** to specify criteria for graphical representation of summary rows. <br/> |
|**Project summary** <br/> |Choose **Project summary** to specify criteria for graphical representation of the project summary. <br/> |
   
When you configure graphical indicators, you can specify the exact value and comparison parameters that determine when a particular graphic is used. The available comparison (test) parameters are as follows:
  
- Equals
    
- Does not equal
    
- Is greater than
    
- Is greater than or equal to
    
- Is less than
    
- Is less than or equal to
    
- Is within
    
- Is not within
    
- Contains
    
- Does not contain
    
- Contains exactly
    
- Is any value
    
These are used to compare the data value with a threshold value that you specify to determine which graphic to display. For example, you can configure values greater than or equal to 50 to display a green indicator and values less than 50 to display a red indicator.
  
You can specify as many images for different values as required. Add a new row to the table for each test/value comparison. Rows in the table are evaluated from top to bottom and the image associated with the first row where the test/value combination is true is displayed.
  
The following table describes the graphical indicator options for non-summary rows.
  
**Graphical indicator attributes for non-summary rows in custom fields for Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Test** <br/> |Choose the operator (equals, less than, and so on) to apply to the field value to determine the image to use.  <br/> |
|**Values** <br/> |Type the field value or a field reference (for example, [cost]) that, combined with the operator in the test column, determines when to use the image in the Image column.  <br/> |
|**Images** <br/> |Choose the image to display when the test/value combination is true.  <br/> |
|**Move** <br/> |Use the move buttons to move a row up or down in the table.  <br/> |
|**Show data values in ToolTips** <br/> |Select this attribute to show the field value in the tool tip associated with the image.  <br/> |
   
When you use graphical indicators for summary rows, you can choose to inherit the graphical indicator settings that you have defined for non-summary rows.
  
If you select the **Inherit criteria from non-summary rows** check box when you configure graphical indicators for summary rows, the graphical indicator parameters that you configured for the non-summary rows are used.
  
If you select the **Inherit criteria from summary rows** check box when you configure graphical indicators for project summary, the graphical indicator parameters that you configured for the summary rows will be used.
  
## Behavior

You can configure a custom field to be controlled by workflow or to require a value.
  
If you choose to have the custom field controlled by a workflow, the required field option is not available because that behavior is controlled by workflow.
  
The following table describes the options for configuring custom field behavior.
  
**Custom field behavior options in Project Web App**

|**Attribute**|**Description**|
|:-----|:-----|
|**Behavior controlled by workflow** <br/> |Select this check box if you want the custom field behavior to be controlled by workflow.  <br/> |
|**Allow editing on Project Detail pages for SharePoint Task List Projects** <br/> |Select this option if you want this custom field to be available to users editing SharePoint task list projects.  <br/> |
|**Require that this field has information** <br/> |Choose whether you want this to be a required field (that is, the field cannot be left blank). This option is not available if the **Behavior controlled by workflow** option is selected. <br/> |
   
## See also

#### 

[Add or edit enterprise custom lookup tables in Project Server](add-or-edit-enterprise-custom-lookup-tables-in-project-server.md)

