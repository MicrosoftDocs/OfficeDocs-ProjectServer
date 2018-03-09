---
title: "Manage security templates in Project Server"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/16/2014
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-2016
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 27f4504f-954f-4e41-bb33-f0bb395926a5
description: "Summary: Administrators can use security templates in Project Web App to standardize the granting of user permissions by role."
---

# Manage security templates in Project Server
 
 **Summary:** Administrators can use security templates in Project Web App to standardize the granting of user permissions by role.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
Security templates provide a means for you to quickly apply or reset predefined permission profiles to new or existing users, groups, and categories. By applying security templates, you can easily standardize the permissions that you assign according to user's role in the organization. A number of predefined security templates are available in each Project Web App instance. These align with the predefined groups. You can customize these security templates or create new security templates according to your needs.
  
Creating custom templates requires planning. You must first identify the common Project Server usage patterns in your organization that are not reflected in the default Project Server security templates. This helps you identify your requirements for custom security templates. Then, determine the permissions that the users who share the common Project Server usage patterns require. This defines the security template. Next, determine the set of projects, resources, views, and so on, that the users and groups require access to. This defines the security category. Create the custom security template and apply it to the group of users who share the common usage pattern. The permissions that you define in the custom security template will enable users to access the Project Server security objects that they require.
  
Security templates are available in Project Server permission mode. There are eight default security templates available in Project Web App:
  
- Administrators
    
- Portfolio Viewers
    
- Portfolio Managers
    
- Project Managers
    
- Proposal Reviewers
    
- Resource Managers
    
- Team Leads
    
- Team Members
    
Each security template is given a set of default category and global permissions, based on the functions that each group typically does in an organization. As mentioned previously, when you create new security templates, you are allowed to copy the permissions for a default security template and then customize it to suit your needs.
  
> [!NOTE]
> For information about the permissions assigned to default security templates in Project Server 2013, see [Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md). 
  
## Task requirements

The following are required to perform the procedures for this task:
  
- Access to Project Web App
    
- The **Manage users and groups** global permission in Project Web App to create, change, or delete a security template
    
To manage security templates in Project Web App, you can perform the following procedures:
  
- [Create security templates in Project Server](create-security-templates-in-project-server.md)
    
- [Modify security templates in Project Server](modify-security-templates-in-project-server.md)
    
- [Delete a security template (Project Server permission mode)](delete-a-security-template-project-server-permission-mode.md)
    
## See also

#### 

[Manage users, groups, and categories in Project Server](manage-users-groups-and-categories-in-project-server-2013.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)
  
[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)
  
[Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md)
  
[Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md)
  
[Default group permissions in Project Server 2013](default-group-permissions-in-project-server-2013.md)

