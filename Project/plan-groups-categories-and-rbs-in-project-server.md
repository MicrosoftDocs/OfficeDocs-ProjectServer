---
title: "Plan groups, categories, and RBS in Project Server"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/15/2017
audience: ITPro
ms.topic: conceptual
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 27c51b32-e99c-4d1c-a365-baf2d13c8ada
description: "Summary: In Project Server permission mode, Project Web App security is based on users, groups, and categories."
---

# Plan groups, categories, and RBS in Project Server
 
 **Summary:** In Project Server permission mode, Project Web App security is based on users, groups, and categories.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
This article addresses planning for groups and categories in a Project Server deployment. If you are using SharePoint permission mode as your security model, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md).
  
In this article:
  
- [Permissions in Project Web App](#section2)
    
- [Groups in Project Web App](#section1)
    
- [Categories in Project Web App](#section3)
    
- [Security templates in Project Web App](#section4)
    
- [Resource Breakdown Structure in Project Web App](#section5)
    
## Permissions in Project Web App
<a name="section2"> </a>

A permission is the authority to perform a specific action within the context of Project Server. You canAllow, Deny, or not configure each permission in Project Server. For example, the **Change Password** permission can be allowed or denied for any given user or group.
  
There are two types of permissions in Project Server:
  
- Global Permissions grant users and groups the ability to perform actions throughout an instance of Project Web App. Global Permissions are assigned on a user or group level.
    
- Category Permissions grant users and groups the ability to perform actions on specific projects and resources. Category Permissions are assigned on a category level.
    
Permissions can be set in a number of different places within Project Web App. You can allow or deny permissions by selecting the check boxes in the **Allow** and **Deny** columns. If neither the **Allow** nor the **Deny** check boxes are selected, the default state is Not Allow. The Not Allow state does not prevent users from accessing the feature associated with the permission if they are granted permission in some other way. For example, a user might belong to one group for which permission is not configured (Not Allowed), but might be granted permission by means of membership in a group for which the permission is allowed. However, if the permission is explicitly denied anywhere, permission is denied everywhere for a particular user or group.
  
You can configure all Project Server permissions by choosing **Project Web App Settings** from the Project Web App **Settings** menu. Permissions can be configured in the following ways:
  
- **Allow** Enables users or group members to perform the actions associated with the permission.
    
- **Deny** Prevents a user or group from performing the actions associated with the permission. Use caution when denying permissions. Note that if a user is denied a specific permission, the deny setting supersedes any Allow settings that might apply to other groups to which the user belongs. No permissions are set to Deny by default.
    
- **Not Allow** If you select neither **Allow** nor **Deny** for a permission, the default state is Not Allow. If a user belongs to more than one group, and a permission is set to Not Allow for one group and is set to **Allow** (but not **Deny**) for another group, then the user is allowed to perform the actions associated with the permission.
    
It is important to consider when you are configuring a permission to **Deny** that the **Deny** setting supersedes any **Allow** settings that apply to the user for that permission by means of other group memberships. Limiting your use of the **Deny** setting can simplify permissions management for large groups of users.
  
> [!NOTE]
> The **Deny** setting enables you to deny access to functionality, because this setting overrides the **Allow** setting. Therefore, use caution when selecting the **Deny** check box. Select the **Deny** check box to prevent a user from outside the organization from accessing Project Server security objects or to deny functionality to a user or group).
  
For organizations that include a large number of users, assigning and administering permissions on an individual basis can be an overwhelming task. You can use groups to assign permissions to multiple users with a single action. Create the groups and define the set of permissions to associate with the groups as part of your initial Project Server deployment planning process, before you assign users to groups and groups to categories. After you define groups, the permissions associated with the groups, and group memberships, the day-to-day administration of users, groups, and categories involves adding users to or removing users from security groups. This helps to reduce the volume of day-to-day administrative tasks required, and can simplify troubleshooting permissions issues. 
  
## Groups in Project Web App
<a name="section1"> </a>

Groups contain sets of users who have similar functionality needs. For example, every project manager in a particular division within your organization may need the same set of Project Server permissions, while executives or resource managers might have different needs. 
  
Define your groups by identifying common needs based on the areas of Project Web App to which users in your organization need access. After you define your groups, you can add users to the groups and grant permissions to the groups; permissions assigned to groups apply to all of the users that the group contains. Using groups to control Project Web App permissions simplifies security administration in Project Web App. Group memberships can change frequently, but the access requirements for groups change infrequently. 
  
> [!NOTE]
> Group membership consists of users only. Groups cannot contain other groups. 
  
Users can belong to multiple groups according to their role in the organization and their access requirements. The following default groups are available in each instance of Project Web App that is in Project Server permission mode. Each is assigned a set of predefined categories and permissions.
  
|**Group**|**Description**|
|:-----|:-----|
|Administrators  <br/> |Users have all global permissions as well as all category permissions via the My Organization category. This allows them complete access to everything on a given instance of Project Web App.  <br/> |
|Portfolio Viewers  <br/> |Users have permissions to view project and Project Web App data. This group is intended for high-level users who need visibility into projects but are not themselves assigned project tasks.  <br/> |
|Portfolio Managers  <br/> |Users have assorted project-creation and team-building permissions. This group is intended for high-level managers of groups of projects.  <br/> |
|Project Managers  <br/> |Users have most global and category-level project permissions and limited resource permissions. This group is intended for users who maintain project schedules on a daily basis.  <br/> |
|Resource Managers  <br/> |Users have most global and category-level resource permissions. This group is intended for users who manage and assign resources and edit resource data.  <br/> |
|Team Leads  <br/> |Users have limited permissions around task creation and status reports. This group is intended for people in a lead capacity who do not have regular assignments on a project.  <br/> |
|Team Members  <br/> |Users have general permissions for using Project Web App, but limited project-level permissions. This group is intended to give everyone basic access to Project Web App. All new users are added to the Team Members group automatically.  <br/> |
   
Administrators usually assign permissions by adding a user account to one of the built-in groups or by creating a new group and assigning specific permissions to that group.
  
## Categories in Project Web App
<a name="section3"> </a>

Categories are collections of projects, resources, and views. Categories define the scope of the information accessible to a given user. A category is similar to a group in that it provides permissions to users. Unlike Global Permissions, Category Permissions are related to specific projects and resources. Additionally, categories include project and resource filters that can be used to determine which projects and resources the specified permissions apply to.
  
Groups and Categories are associated with each other to provide a complete set of permissions for each user. Each Group can be associated with one or more Categories and each category can provide a different set of project- and resource-level permissions on the projects in that category for the members of that group.
  
Each Project Web App instance includes the following default categories:
  
|**Category**|**Description**|
|:-----|:-----|
|My Direct Reports  <br/> | Allows users permission to approve timesheets for their direct descendants in RBS. This category is intended for managers who need the ability to approve timesheets. <br/> |
|My Organization  <br/> | Contains all projects and resources and allows various levels of category permissions depending on associated group management. It also provides full access to all views. This category is intended to allow users to have visibility into everything on the Project Web App instance. <br/> |
|My Projects  <br/> |Filtered to allow category permissions to users who own projects or are status managers on a project, are assigned as a resource to a project, or whose descendants in RBS are assigned to a project. This category is intended to allow users to have visibility into all project with which they or their descendants in RBS are associated.  <br/> |
|My Resources  <br/> |Allows most resource-level category permissions, filtered on resources who are descendants of the user in RBS. This category is intended to allow users to manage their resources as delineated in the RBS structure.  <br/> |
|My Tasks  <br/> |Allows users to see projects to which they are assigned. This category is associated with the Team Members group and is intended for everyone to have visibility into the projects to which they are assigned.  <br/> |
   
You can create custom categories to provide new ways to access data for projects, resources, and views. A large number of categories can be complex to administer. We recommend that you use categories sparingly.
  
## Security templates in Project Web App
<a name="section4"> </a>

Security templates are predefined sets of permissions. Use security templates to simplify the process of granting permissions to groups of users who need access to the same data. Each Project Web App instance includes the following default security templates:
  
- Administrator 
    
- Portfolio Viewer 
    
- Portfolio Manager 
    
- Project Manager 
    
- Proposal Reviewer
    
- Resource Manager 
    
- Team Lead
    
- Team Member
    
Security templates provide a means for you to quickly apply or reset predefined permission profiles to new or existing users, groups, and categories. By applying security templates, you can easily standardize the permissions that you assign according to users' role in the organization. The default security templates align with the predefined groups in Project Web App. You can customize these security templates and create new security templates according to your needs. 
  
> [!NOTE]
> When you change the settings for a security template, the changes are not automatically applied to the users and groups that the template was applied to. 
  
Creating custom security templates requires planning. You must first identify the common Project Web App usage patterns in your organization that are not reflected in the default security templates. This helps you to identify your requirements for custom security templates. Then, determine the permissions that the users who share the common Project Web App usage patterns require. This defines the security template. Next, determine the set of projects, resources, views, and so on, that the users and groups require access to; this defines the security category. Create the custom security template and apply it to the group of users that share common usage patterns.
  
## Resource Breakdown Structure in Project Web App
<a name="section5"> </a>

The Resource Breakdown Structure (RBS) is a hierarchical security structure typically based on the management reporting structure of your organization, although it can also be structured in other ways. The RBS can be an important element in your Project Web App security model when it is used to define the reporting relationships among users and projects in your organization. When you specify an RBS value for each Project Web App user, you can take advantage of the dynamic security options that can be defined for each security category.
  
The RBS structure is defined by adding values to the RBS custom lookup table that is built in to Project Web App. Once you define the structure, you can assign RBS values to individual users by setting the RBS property in the user's account settings page.
  
Once the RBS is configured, Categories can use RBS codes to dynamically determine which projects and resources particular users can view or access. The following tables list the security options that use RBS that are available in each Category. 
  
**Security options for projects**

|**Option**|**Description**|
|:-----|:-----|
|**The user is the Project Owner or the User is the Status Manager on assignments within that project** <br/> |Users with permissions in the category where this option is selected can see projects on which they are a Project Owner or a Status Manager  <br/> |
|**The user is on that project's Project Team** <br/> |Users with permissions in the category where this option is selected can see projects on which they are a resource  <br/> |
|**The Project Owner is a descendant of the User via RBS** <br/> |Users with permissions in the category where this option is selected can see projects owned by their descendants in the RBS  <br/> |
|**A resource on the project's Project Team is a descendant of the User via RBS** <br/> |Users with permissions in the category where this option is selected can see projects on which their descendants in the RBS are a resource  <br/> |
|**The Project Owner has the same RBS value as the User** <br/> |Users with permissions in the category where this option is selected can see projects owned by other users with the same RBS value  <br/> |
   
> [!NOTE]
> The first two options ( **The user is the Project Owner or the User is the Status Manager on assignments within that project** and **The User is on that project's Project Team**) are not related to the RBS, but they do offer a similar method of filtering which projects are visible to a user. 
  
**Security options for resources**

|**Option**|**Description**|
|:-----|:-----|
|**The User is the resource** <br/> |Users with permissions in the category where this option is selected can see themselves as a resource  <br/> |
|**They are members of a Project Team on a project owned by the User** <br/> |Users with permissions in the category where this option is selected can see resources assigned to projects that they own  <br/> |
|**They are descendants of the User via RBS** <br/> |Users with permissions in the category where this option is selected can see their descendants in the RBS  <br/> |
|**They are direct descendants of the User via RBS** <br/> |Users with permissions in the category where this option is selected can see their direct descendants in the RBS  <br/> |
|**They have the same RBS value as the user** <br/> |Users with permissions in the category where this option is selected can see other users with the same RBS value  <br/> |
   
> [!NOTE]
> The first two options ( **The User is the resource** and **They are members of a Project Team on a project owned by the User**) are not related to the RBS, but they do offer a similar method of filtering which resources are visible to a user. 
  
The options in the tables above can be configured when you create or modify a Category.
  
## See also
<a name="section5"> </a>


[Video series: How security permissions work in Project Server](https://go.microsoft.com/fwlink/p/?LinkId=618509)

