---
title: "Configure an OLAP cube in Project Server 2016"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/20/2016
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 6e92d2c8-ea5c-4534-9bad-9e99eb5235c8

description: "Summary: Configure OLAP cube settings by using the OLAP Database Management page in Central Administration."
---

# Configure an OLAP cube in Project Server 2016
 
 **Summary:** Configure OLAP cube settings by using the OLAP Database Management page in Central Administration.<br/>
**Applies to:** Project Server 2016
  
You can configure OLAP cube dimensions and measures, or you can configure the build settings of a cube.
  
To configure an OLAP cube, you must be a Project Server service application administrator.
  
There are two sets of parameters that can be configured on an existing OLAP cube:
  
- Dimensions and measures
    
- Cube build settings
    
Perform the following procedure to configure the dimensions and measures of an existing OLAP cube.
  
### To configure OLAP cube dimensions and measures

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Point to the Project Web App instance where you want to build the cube, click the arrow that appears, and then click **Manage**.
    
4. On the Server Settings page, in the **Database Administration** section, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, select an OLAP database from the list, and then click **Configuration**.
    
6. Configure the settings on the Database Configuration page:
    
|**Setting**|**Description**|
|:-----|:-----|
|**Cube Dimensions** <br/> | Use the Cube dimensions area to specify the custom fields that you want to add to the OLAP cube as dimensions. <br/>  Select a cube from the drop-down list to display the available and selected dimensions. <br/>  Select the dimensions that you want to include in that cube in the **Available fields** list and click **Add** to include them in the cube. Do this for each cube in the **Cube** drop-down list. <br/> |
|**Cube Measures** <br/> | Use the Cube measures area to specify the custom fields that you want to add to the OLAP cube as measures. <br/>  Select a cube from the drop-down list to display the available and selected measures. <br/>  Choose the measures that you want to include in that cube in the **Available fields** list and click **Add** to include them in the cube. Do this for each cube in the **Cube** drop-down list. <br/> |
|**Built-in Measures** <br/> |Select the built-in measures that you want to include in the cube.  <br/> The fields that you select are added to the Project, Task, and Assignment cubes as measures.  <br/> |
|**Inactive Tasks** <br/> |If you want the cube to include inactive tasks, select the **Include Inactive Tasks** check box. <br/> |
|**Calculated Measures** <br/> |Select the cube that you want to define an expression for from the **Cube** drop-down list, and then click **Insert** to add a custom MDX expression. <br/> For more information about MDX expressions, see [Multidimensional Expressions (MDX) Reference](/sql/mdx/multidimensional-expressions-mdx-reference) (https://go.microsoft.com/fwlink/p/?LinkID=186166). <br/> |
   
7. Click **Save**.
    
Perform the following procedure to configure the build settings of an existing OLAP cube.
  
### To configure OLAP cube build settings

1. In Central Administration, in the **Application Management** section, click **Manage service applications**.
    
2. Click the Project Server service application.
    
3. Point to the Project Web App instance where you want to build the cube, click the arrow that appears, and then click **Manage**.
    
4. On the Server Settings page, in the **Database Administration** section, click **OLAP Database Management**.
    
5. On the OLAP Database Management page, in the **OLAP Database Name** column, click the database that you want to configure.
    
6. Configure the settings on the OLAP Database Build Settings page:
    
|**Setting**|**Description**|
|:-----|:-----|
|**Analysis Services Server** <br/> |The name of the instance of SQL Server Analysis Services (SSAS) where you want to build the cube.  <br/> |
|**Analysis Services Database to be created** <br/> |The name of the database that you want to create.  <br/> |
|**Extranet URL** <br/> |The URL for the extranet site.  <br/> |
|**Description** <br/> |A description of this OLAP cube.  <br/> |
|**Project Departments** <br/> |If you have projects assigned to departments, you have the option of selecting the departments that you want to have included in the cube. If no department is selected, then no departmental filtering occurs.  <br/> The selection of departments available is controlled by the Department custom lookup table. To allow multiple selections, modify the Project Departments custom field and select the **Allow multiple values to be selected from lookup table** check box. <br/> > [!NOTE]> To cancel the selection of a department after it is selected, click the department again.           |
|**Resource Departments** <br/> |If you have resources assigned to departments, you have the option of selecting the departments that you want to have included in the cube. If no department is selected, then no departmental filtering occurs.  <br/> The selection of departments available is controlled by the Department custom lookup table. To allow multiple selections, modify the Resource Departments custom field and select the **Allow multiple values to be selected from lookup table** check box. <br/> > [!NOTE]> To cancel the selection of a department after it is selected, click the department again.           |
|**Use the earliest project start date and the latest project finish date** <br/> |Select this option if you want to base the date range of the cube on the earliest start date of any project and the latest finish date of any project.  <br/> |
|**Use the following last and next time units to calculate the date range at the time that the OLAP database is built** <br/> |Select this option if you want the date range to be configured automatically based on a delta from the date on which the cube is built. In the **Last** and **Next** boxes, type the number of days, weeks, or months that you want to use for the delta. <br/> |
|**Use the fixed date range specified below** <br/> |Select this option if you want to use a fixed date range. In the **From** and **To** boxes, type the dates that you want to use. <br/> |
|**Update periodically** <br/> |Select this option if you want to schedule an update frequency. If this option is not selected, the cube will not be updated automatically.  <br/> |
|**Immediately retry the OLAP database update if scheduled time fails because of queue down time** <br/> |If the scheduled cube build fails because the queue is not available, selecting this option will cause the build job to start automatically when the queue becomes available instead of waiting for the next scheduled time.  <br/> |
|**Update every** <br/> |Select the number of hours, days, weeks, or months for the cube to be rebuilt.  <br/> |
|**Start date** <br/> |Select the start date for the first automated cube build.  <br/> |
|**Start time** <br/> |Select the start time for each automated cube build.  <br/> |
   
7. Click **Save**.
    
## See also

#### 

[Create OLAP cubes in Project Server 2016](create-olap-cubes-in-project-server-2016.md)
  
[Delete OLAP cubes in Project Server 2016](delete-olap-cubes-in-project-server-2016.md)
  
[Build OLAP cubes in Project Server 2016](build-olap-cubes-in-project-server-2016.md)