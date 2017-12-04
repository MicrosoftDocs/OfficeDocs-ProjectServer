---
title: "Create security categories in Project Server"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/27/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_OneDriveAdmin
ms.assetid: cf1a1f91-83c7-4166-8e69-52e07a9ffeb5
description: "Summary: Add custom security categories by using the Manage Categories page in Project Web App Settings."
---

# Create security categories in Project Server
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** Add custom security categories by using the Manage Categories page in Project Web App Settings.
  
In Project Web App, you can add custom security categories as necessary to create a security model that meets the specific needs of users and groups in your organization. See [To create a category](#CreateACategory).
  
> [!NOTE]
> Categories are only available in Project Server permission mode. If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
Avoid creating unnecessary categories. Having lots of groups and categories in an organization can lead to greater administrative complexity. Additionally, having many groups and categories can stress the authorization system, which can affect performance.
  
If there are many users at the highest level of the Resource Breakdown Structure (RBS), consider adding them to a custom category that enables them to view all projects (avoiding dynamic rules). Top-level RBS users probably have access to all projects, so assigning them to this category avoids unnecessary work by the authorization system.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](http://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage categories in Project Server](manage-categories-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
To create a new category, perform the following procedure.
  
### To create a category

1. On the Project Web App home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Categories**.
    
3. On the Manage Categories page, click **New Category**.
    
4. Complete the Add or Edit Category page. See the following sections for information about each setting.
    
5. Click **Save**.
    
## Name and Description

Use the **Name and Description** section to specify a name and description for the category.
  
The following table describes the name and description options for a category.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Category Name** <br/> |The name of the category. This name must different be than that of other categories.  <br/> |
|**Description** <br/> |Description of the category.  <br/> |
   
## Projects

Use the **Projects** section to specify the projects that users associated with this category can view.
  
Users access to projects in this category are governed by the defined group and category permissions. You can also use one of the dynamic security options to have projects made available to users based on their relationship to the project or their RBS value.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Include all current and future projects** <br/> |When this option is selected, users in this category can see all projects in this instance of Project Web App.  <br/> |
|**Only include the selected projects** <br/> |When this option is selected, users in this category can view the projects in the **Selected Projects** list and any projects from the **Available Projects** list that the user has permissions to see with the dynamic permissions options. The dynamic permissions features only work when this option is selected. <br/> |
|**Available projects** <br/> |Projects that are not explicitly part of this category. Users may still be able to view these projects if any of the dynamic permissions options are configured to enable it.  <br/> |
|**Selected projects** <br/> |Projects that users in this category can view.  <br/> |
|**The User is the Project Owner or the User is the Status Manager on assignments within that Project** <br/> |Gives users permissions on any project they own. Also gives Status Managers permissions on projects that contain assignments that they manage.  <br/> |
|**The User is on that project's Project Team** <br/> |Gives users permissions on any project where they are on the project team. Users do not need to have assignments on the project.  <br/> |
|**The Project Owner is a descendant of the User via RBS** <br/> |Gives users permissions on any project that is managed by resources subordinate to them in the RBS hierarchy.  <br/> |
|**A resource on the project's Project Team is a descendant of the User via RBS** <br/> |Allows a user to view any project where a resource subordinate to the user in the RBS is a member of the project team.  <br/> Avoid using this rule for users who have many resources under them in the RBS. If the resources under them are on many projects involving many categories, this stress on the authorization system can affect performance (for example, delay the loading of the Project Center page).  <br/> |
|**The Project Owner has the same RBS value as the User** <br/> |Allows a user to view projects managed by persons that have the same RBS value that the user has.  <br/> |
   
## Resources

Use the **Resources** section to specify which resources the users associated with this category can view.
  
Users access to resources in this category are governed by the defined group and category permissions. You can also use one of the dynamic security options to have resources made available to users based on their relationship to the resource or their RBS value.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Include all current and future resources** <br/> |When this option is selected, users in this category can see all resources in this instance of Project Web App.  <br/> |
|**Only include the selected resources** <br/> |When this option is selected, users in this category can view the resources in the **Selected Resources** list and any resources from the **Available Resources** list that the user has permissions to see with the dynamic permissions options. <br/> |
|**Available Resources** <br/> |Resources that are not explicitly part of this category. Users may still be able to view these resources if any of the dynamic permissions options are configured to enable it.  <br/> |
|**Selected Resources** <br/> |Resources that users in this category can view.  <br/> |
|**The User is the resource** <br/> |Gives users permissions to view information about themselves (such as assignments).  <br/> |
|**They are members of a Project Team on a project owned by the User** <br/> |Gives users permissions to view information for all resources in projects they own.  <br/> |
|**They are descendants of the User via RBS** <br/> |Gives users permissions to view information for all resources under them in the RBS.  <br/> |
|**They are direct descendants of the User via RBS** <br/> |Gives users permissions to view information about resources that are directly under them in the RBS.  <br/> |
|**They have the same RBS value as the User** <br/> |Gives user permissions to view information about resources that have the same RBS value.  <br/> |
   
## Views

Use the **Views** section to specify views that users associated with this category can see.
  
To add a view to the category, select the **Add** check box for that view. To remove a view, clear the **Add** check box for that view.
  
## Permissions

Use the **Permissions** section to specify which users and groups are associated with this category.
  
To associate a user or group with this category, select the user or group in the **Available Users and Groups** list, and then click **Add**.
  
To remove the association between a user or group and this category, select the user or group in the **Users and Groups with Permissions** list and then click **Remove**.
  
For easiest administration, only associate groups with categories.
  
|**Attribute**|**Description**|
|:-----|:-----|
|**Available Users and Groups** <br/> |Users and groups that are not associated with this category.  <br/> |
|**Users and Groups with Permissions** <br/> |Users and groups that are associated with this category.  <br/> |
   
To select the category permissions for each user or group, select the user or group in the **Users and Groups with Permissions** list. This action enables the category permissions list for the selected group in this category.
  
Each user or group can be assigned distinct permission in a category.
  
For a complete list of category permissions, see [Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md).
  
## See also

#### 

[Manage categories in Project Server](manage-categories-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Modify categories in Project Server](modify-categories-in-project-server.md)
  
[Delete a category (Project Server permission mode)](delete-a-category-project-server-permission-mode.md)

