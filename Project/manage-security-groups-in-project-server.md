---
title: "Manage security groups in Project Server"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/16/2014
audience: ITPro
ms.topic: article
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 0f38d5c3-b604-41b0-a1c8-7b1112672265
description: "Summary: Administrators can manage security permissions for groups by using the Manage Groups page in Project Web App Settings."
---

# Manage security groups in Project Server
 
 **Summary:** Administrators can manage security permissions for groups by using the Manage Groups page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
A group is a container for users that can be assigned permissions in Project Web App. Users automatically inherit the permissions of any group to which they belong. By adding users to groups, you can significantly reduce the amount of time spent managing user permissions. In Project Server permission mode, you can manage groups from the Project Web App Server Settings page.
  
> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.
  
Avoid creating unnecessary groups. Having lots of groups and categories in an organization can lead to additional management complexity. Additionally, having many groups and categories can stress the authorization system, which can affect performance.
  
You can modify the information associated with any security group in Project Web App. For example, you may have to modify the group for changes to users or categories, or for changes to the Active Directory group to which it is currently being synchronized.
  
We recommend not modifying the default Project Web App groups, but instead creating a new group that has the same permissions and modifying the new group.
  
By default, the following groups are available in a Project Web App running in Project Server permission mode:
  
- **Team Members** Users have general permissions for using Project Web App, but limited project-level permissions. This group is intended to give everyone basic access to Project Web App. All new users are added to the Team Members group automatically. This group is associated with the My Tasks category.
    
- **Project Managers** Users have most global and category-level project permissions and limited resource permissions. This group is intended for users who maintain project schedules daily. This group is associated with the My Organization and My Projects categories.
    
- **Resource Managers** Users have most global and category-level resource permissions. This group is intended for users who manage and assign resources and edit resource data. This group is associated with the My Direct Reports, My Organization, My Projects, and My Resources categories.
    
- **Portfolio Viewers** Users have permissions to view project and Project Web App data. This group is intended for high-level users who need visibility into projects but are not themselves assigned project tasks. This group is associated with the My Organization category.
    
- **Team Leads** Users have limited permissions around task creation and status reports. This group is intended for people in a lead capacity who do not have regular assignments on a project. This group is associated with the My Projects category.
    
- **Portfolio Managers** Users can create and edit data, but cannot perform Project Web App administrative tasks such as adding users or creating groups. Portfolio Managers are able to view and edit all projects and resources in the organization. This group is associated with the My Organization category.
    
- **Administrators** This group is granted all available Project Web App permissions. It is associated with the My Organization category.
    
These default groups should be used together with the five default categories.
  
## Task requirements

The following are required to perform the procedures for this task:
  
- Access to Project Web App
    
- The **Manage users and groups** global permission in Project Web App in order to add, modify, or delete a group
    
To manage groups in Project Web App, you can perform the following procedures:
  
- [Create security groups in Project Server](create-security-groups-in-project-server.md)
    
- [Modify security groups in Project Server](modify-security-groups-in-project-server.md)
    
- [Delete a security group (Project Server permission mode)](delete-a-security-group-project-server-permission-mode.md)
    
## See also


[Manage users, groups, and categories in Project Server](manage-users-groups-and-categories-in-project-server-2013.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

