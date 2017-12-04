---
title: "Create security templates in Project Server"
ms.author: efrene
author: efrene
manager: laurawi
ms.date: 11/27/2017
ms.audience: ITPro
ms.topic: article
ms.prod: office-online-server
localization_priority: Normal
ms.collection: IT_OneDriveAdmin
ms.assetid: d10da3ff-4b2b-499a-8c2c-b990cc1fd167
description: "Summary: Create Project Web App security templates by using the Manage Templates page in Project Web App Settings."
---

# Create security templates in Project Server
 **We are in the process of combining the Project Server 2013 and Project Server 2016 content into a single content set. We appreciate your patience while we reorganize things. See the Applies To tag at the top of each article to find out which version of Project Server an article applies to.**
 **Summary:** Create Project Web App security templates by using the Manage Templates page in Project Web App Settings.
  
See [To create a template](#proc) later in this article.
  
In Project Server permission mode, you can group commonly used permissions into a security template and then use it to assign permissions to users, groups, and categories.
  
## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:> [Plan browser support](https://go.microsoft.com/fwlink/p/?LinkId=246502)> [Accessibility for SharePoint Products](http://technet.microsoft.com/library/94ad4316-1077-400a-b17e-a2085a5a7312.aspx)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://go.microsoft.com/fwlink/p/?LinkID=246504)> [Touch](https://go.microsoft.com/fwlink/p/?LinkId=246506)
  
Before you begin this operation, review the following information about prerequisites:
  
- Read [Manage security templates in Project Server](manage-security-templates-in-project-server.md).
    
- You must have access to Project Web App.
    
    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.
  
## Create a template

Perform the following procedure to create a template in Project Web App.
  
### To create a template

1. On the PWA home page, on the **Settings** menu, click **Project Web App Settings**.
    
2. On the Server Settings page, in the **Security** section, click **Manage Security Templates**.
    
3. On the Manage Templates page, click **New Template**.
    
4. On the Add or Edit Template page, in the **Name** section, do the following:
    
1. In the **Template Name** box, type a name for the template.
    
2. In the **Description** box, type a short description of the template.
    
3. Optionally, you can base the new template on an existing template, and then make any required changes. To do this, select an existing template from the **Copy Template** list. The new template will be populated with the security permissions from the template you selected.
    
5. In the **Category Permissions** section, select the permissions in the **Allow** or **Deny** column that you want to apply towards projects and resources whenever this template is used to set permissions.
    
    For more information about specific category permissions, see [Category permissions in Project Server 2013](category-permissions-in-project-server-2013.md).
    
6. In the **Global Permissions** section, select the permissions in the **Allow** or **Deny** columns that you want to apply across this instance of Project Web App whenever this template is used to set permissions.
    
    For more information about specific global permissions, see [Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md).
    
7. Click **Save**.
    
## See also

#### 

[Manage security templates in Project Server](manage-security-templates-in-project-server.md)
  
[Modify security templates in Project Server](modify-security-templates-in-project-server.md)
  
[Delete a security template (Project Server permission mode)](delete-a-security-template-project-server-permission-mode.md)
  
[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)
  
[Plan groups, categories, and RBS in Project Server](plan-groups-categories-and-rbs-in-project-server.md)

