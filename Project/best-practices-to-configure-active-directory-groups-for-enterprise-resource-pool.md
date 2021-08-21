---
title: "Best practices to configure Active Directory groups for Enterprise Resource Pool synchronization in Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 4ceccb50-f36d-4d1c-8a32-42c7e5b62b91
description: "Summary: This article describes the prescribed method to configure your Active Directory groups for synchronization with Project Server 2013 to add resources to the Enterprise Resource Pool."
---

# Best practices to configure Active Directory groups for Enterprise Resource Pool synchronization in Project Server 2013
 
 **Summary:** This article describes the prescribed method to configure your Active Directory groups for synchronization with Project Server 2013 to add resources to the Enterprise Resource Pool.<br/>
**Applies to:** Project Server 2013
  
When configuring synchronization between the Enterprise Resource Pool (ERP) and Active directory groups in Project Server 2013, a key consideration is that after being added as a resource to Project Server, you still need to add the resource as a user in order for the resource to use Project Web App. Unlike the previous version, in Project Server 2013 users accounts are not automatically created for resources that are added to the Enterprise Resource Pool through Active Directory synchronization. This article describes a best practice in which you can configure your Active Directory groups for security group synchronization as well as ERP synchronization in order to add user accounts for your resources.
  
## Active Directory group configuration for ERP and security group synchronization

It is important to note the following when planning to configure your active directory groups for synchronization with the ERP and with security groups in Project Server 2013:
  
- You can synchronize up to five Active Directory groups with the Enterprise Resource Pool.
    
- You can only synchronize one Active Directory group with each security group. For example, only one Active Directory group can be configured to synchronize with the default Project Managers security group.
    
The following graphic displays the method we suggest to configure your Active Directory groups to add your Project Server 2013 users both as resources and as users to their appropriate security groups.
  
![Active Directory group configuration.](images/ActiveDirectorygroupconfigurationforsynchronizatino.jpg)
  
In the graphic above, Active Directory is configured to contain a single "ERP Group" that also contains nested Active Directory groups for Team Members, Project Managers, and Resource Managers. Although you can synchronize up to five Active Directory Groups with the Enterprise Resource Pool, we synchronize only the single ERP group, which would include all users contained in the subgroups. User 1, User 2, User 3, User 4, User 5, and User 6 would all be synchronized to the Enterprise Resource Pool in Project Server 2013.
  
> [!NOTE]
> You can configure Active Directory synchronization to the Project Server 2013 ERP through the Active Directory Resource Pool Synchronization page in the Operational Policies section of Project Web App Server Settings. For more information, see [Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md). 
  
In order to add the resources as users in Project Server 2013 to give them Project Server user accounts, we also need to synchronize them from Active Directory to their appropriate security group in Project Server 2013. In the graphic above, each of the nested sub-groups in the ERP Group are synchronized with their appropriate security group in Project Server 2013. For example:
  
- The Team Member group in Active Directory is synchronized with the Team Members security group in Project Server 2013.
    
- The Project Managers group in Active Directory is synchronized with the Project Managers security group in Project Server 2013.
    
- The Resource Managers group in Active Directory is synchronized with the Resource Managers security group in Project Server 2013.
    
> [!NOTE]
> You can configure Active Directory synchronization to Project Server 2013 security groups through the Manage Groups page in the Security section of Project Web App Server Settings. For more information, see [Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md). 
  
A benefit of this configuration is that any changes to Active Directory can be made in a single location, and will be reflected in both the Enterprise Resource Pool and in security group. For example, if the Team Member "User 1" gets married and her last name is updated in Active Directory, the change in user properties will be reflected in both the Enterprise Resource Pool and the Project User Account when both groups are synchronized with the Active Directory group. Another benefit is that it prevents confusion that can be associated if a user is in two or more active directory groups that are synchronized with the ERP. 
  
## See also

#### 

[Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md)
  
[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)
  
[Supported Active Directory topologies for Project Server 2013 Enterprise Resource Pool synchronization](supported-active-directory-topologies-for-project-server-2013-enterprise-resourc.md)

