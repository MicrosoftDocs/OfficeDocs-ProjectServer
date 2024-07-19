---
title: "Enterprise custom fields and lookup tables in Project Web App"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 9/6/2017
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 16ceaa65-1f0a-480f-b924-171e8b08ac2b
description: "Summary: Use enterprise custom fields and lookup tables in Project Web App to customize Project Server data."
---

# Enterprise custom fields and lookup tables in Project Web App

**Summary:** Use enterprise custom fields and lookup tables in Project Web App to customize Project Server data.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
In Project Web App, you can use Enterprise Custom Fields to help establish consistency across all the organization's projects. That way that you can ensure that fields and associated lookup tables are used in the same manner for all projects, tasks, resources, and assignments in a given instance of Project Web App.
  
Enterprise Custom Fields can include custom formulas and can use lookup tables and graphical indicators. By using Enterprise Custom Fields effectively, you can help customize Project Web App to fit the unique needs of your organization. When you use Enterprise Custom Fields, all users in your organization have access to a standard set of fields, which enables operations to be applied in the same manner across whole sets of projects. For example:
  
- You can customize project management to reflect your organization's structure and processes. All users in your organization can have access to a standard set of fields, which enables the same operations to be completed across whole sets of projects.
    
- You can set Enterprise Custom Fields as required fields so that users are prompted to enter information in that field before they save.
    
- You can use Enterprise Custom Fields on a per-department basis.
    
Because creating Enterprise Custom Fields can range from being easy to being very complex and labor-intensive, it is important to correctly design your Enterprise Custom Fields. To determine the scope of Enterprise Custom Fields that your organization requires, consider the following questions:
  
- What words or phrases are used by stakeholders in your organization, such as return on investment (ROI), Key Performance Indicator (KPI), and so on? You might want to quantify and codify these concepts by using Enterprise Custom Fields. Also consider the concepts behind the common words and phrases used by stakeholders in your organization.
    
- What are the user requirements in your organization? User requirements are frequently based on reporting requirements.
    
- How will you sort and select data? How will you use graphical indicators?
    
## Enterprise Custom Fields

You can create Enterprise Custom Fields at the task, project, and resource level. It is important to determine which specific Enterprise Custom Fields your organization needs when you review your business requirements while planning your Project Server deployment. It is best to do this after you have performed a gap analysis by comparing the capabilities of Project Server against the business needs of your organization.
  
For example, a group of executives in an organization wants to be able to view project data by department. In order to achieve this business requirement, they have to define a consistent method for identifying departments within the organization. In addition, if each department has a different accounting method or funding process, the executives might have to determine a method for defining this, also. You can use the Project Departments or Resource Departments custom fields together with the Department custom lookup table, or any enterprise custom field that has the Department property set to do this.
  
The most important use for Enterprise Custom Fields is to enable organizations to enforce consistency across all projects. For example, if two project managers use different fields to specify a resource's location, then users are unable to determine when the same resource is assigned to projects managed by each project manager.
  
Note that using a lot of custom fields with formulas can have a performance impact on your system.
  
## Enterprise Custom lookup tables

Consider using custom lookup tables for any Enterprise Custom Field for which standardization of data is the most important factor. For example, it might not be a good practice to let users enter an arbitrary value in a custom Status field. One project manager might enter Started, and another might enter In-Progress, both indicating that the project has begun and is underway. Without using lookup tables, it is difficult to standardize terminology in your organization.
  
For example, you might create a custom text field that is associated with Resources. To do this, you click the **Resource** option, select **Text** from the list, and rename itManager. If you do not specify a lookup table for this custom text field, a user could enter any text value in the **Manager** field.
  
## See also

[Add or edit enterprise custom fields in Project Server](add-or-edit-enterprise-custom-fields-in-project-server.md)
  
[Add or edit enterprise custom lookup tables in Project Server](add-or-edit-enterprise-custom-lookup-tables-in-project-server.md)
