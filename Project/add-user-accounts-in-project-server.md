---
title: Add user accounts in Project Server
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 9/8/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.assetid: 1fc96ddf-f44c-4b90-be39-ae4cdaa91af9
description: Add user accounts by using the Manage Users page in Project Web App Settings.
---

# Add user accounts in Project Server

 **Summary:** Add user accounts by using the Manage Users page in Project Web App Settings.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013

Every Project Web App user must have a user account before he or she can log on to Project Web App and interact with Project Server data. In Project Server permission mode, user accounts can be added through the Manage Users page in Project Web App Settings. 

> [!NOTE]
> Windows users can also be added to Project Web App from the Active Directory directory service through Active Directory Synchronization. For more information, see [Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md). 

> [!NOTE]
> If you are using SharePoint permission mode, see [Plan SharePoint groups in Project Server](plan-sharepoint-groups-in-project-server.md) for information about managing users in Project Web App.

## Before you begin

> [!NOTE]
>  Because SharePoint Server runs as websites in Internet Information Services (IIS), administrators and users depend on the accessibility features that browsers provide. SharePoint Server supports the accessibility features of supported browsers. For more information, see the following resources:>  For SharePoint Server 2013:> [Plan browser support](/SharePoint/install/browser-support-planning)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Accessibility features in SharePoint 2013 Products](https://go.microsoft.com/fwlink/p/?LinkId=246501)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)>  For SharePoint Server 2016:> [Software requirements for Project Server 2016](software-requirements-for-project-server-2016.md)> [Accessibility for SharePoint Products](/SharePoint/accessibility-guidelines)> [Keyboard shortcuts](https://support.microsoft.com/office/keyboard-shortcuts-in-sharepoint-online-466e33ee-613b-4f47-96bb-1c20f20b1015)> [Touch](/windows/win32/wintouch/windows-touch-gestures-overview)

Before you begin this operation, review the following information about prerequisites:

- Read [Manage users in Project Server](manage-users-in-project-server.md).

- You must have access to the Project Web App instance where you want to add a user.

- The user accounts that you are adding are configured properly in either Active Directory or the forms-based membership provider so that their information is available to Project Web App. Project Server 2016 supports two authentication methods for its users (Windows authentication and claims authentication).

    > [!IMPORTANT]
    > The **Manage users and groups** global permission in Project Web App is required to complete this procedure.

To add a new user account, perform the following procedure.

### To add a user

1. On the Server Settings page, in the **Security** section, click **Manage Users**.

2. On the Manage Users page, click **New User**.

3. On the New User page, fill out the required information for the user. See the following sections for more information about each option.

4. Click **Save**.

## Identification Information

Use the **Identification Information** section to specify user information such as name, e-mail address, and account status.

The following table describes the user identification options.

|**Attribute**|**Description**|
|:-----|:-----|
|**User can be assigned as a resource** <br/> |The status of the user as an Enterprise Resource. Select **User can be assigned as a resource** to enable this user account to be assigned tasks as a resource. Selecting this entry makes the user an Enterprise Resource. This setting is the default selection. Once a user account becomes an Enterprise Resource it cannot be changed back to a non-Enterprise Resource even if the check box is cleared. <br/> |
|**Display Name** <br/> |The name for the user account. This is a required field.  <br/> |
|**E-mail address** <br/> |The e-mail address for the user. This field is required to synchronize tasks with Exchange Server.  <br/> |
|**RBS** <br/> |The user's position in the Resource Breakdown Structure hierarchy.  <br/> |
|**Initials** <br/> |The user's initials.  <br/> |
|**Hyperlink Name** <br/> |The name of the user's web site (for example, a team web site) if applicable.  <br/> |
|**Account Status** <br/> |Can be set to **Active** or **Inactive**. If the value is set to Active, the user account functions normally. If the value is set to **Inactive**, the user is unable to access the account and they are no longer available for adding to teams or being assigned to work, but their existing assignments remain in Project Web App.  <br/> |

## User Authentication

Use the **User Authentication** section to specify the user's logon account.

The following table describes the user account options.


| **Attribute**                | **Description**                                                                                                                                                                                                                                                                                                                                                               |
|:-----------------------------|:------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **User logon account** <br/> | If you are using Integrated Windows authentication, type the user's account name in the form of DomainName\\UserAccountName.  <br/> If you are using Project Online, type the user's account name in the form of username@domain.com  <br/> If you are using forms-based authentication, type the user account name in the form of MembershipProviderName:UserAccount.  <br/> |

## Assignment Attributes

Use the **Assignment Attributes** section to define information associated with the user's assignment to tasks. This includes calendar, booking type, timesheet manager, assignment owner, and cost and availability information.

> [!NOTE]
> If you have not selected the **User can be assigned as a resource** check box, these options are not available.

The following table describes the Project Web App user assignment attribute options.

|**Attribute**|**Description**|
|:-----|:-----|
|**Resource can be leveled** <br/> |Indicates whether the resource can be leveled. Leveling is the process that is used to resolve resource conflicts or over-allocations by delaying or splitting certain tasks. When Project Web App levels a resource, its selected assignments are distributed and rescheduled.  <br/> |
|**Base Calendar** <br/> |The base calendar for this resource. A base calendar is a calendar that can be used as a project and task calendar that specifies default working and non-working time for a set of resources.  <br/> |
|**Default Booking Type** <br/> |The configuration of a user's booking type as either Committed or Proposed. A committed resource is formally allocated to any task assignment in a project. A proposed resource has a pending resource allocation to a task assignment that has not yet been authorized. This resource assignment does not detract from the availability of the resource to work on other projects.  <br/> |
|**Timesheet manager** <br/> |The timesheet manager, if there is one, for the user.  <br/> If you set this value to this user, all submitted timesheets will be automatically approved.  <br/> |
|**Default Assignment Owner** <br/> |The enterprise resource who is responsible for entering progress information in Project Web App. This person can differ from the person first assigned to the task. For example, a material resource cannot log on to Project Web App but the assignment owner field allows an enterprise resource to enter progress for the resource within Project Web App.  <br/> |
|**Earliest Available** <br/> |The earliest date that the user is available as a resource. This date corresponds to the resource availability dates for a resource that can be seen in Project Professional 2016.  <br/> |
|**Latest Available** <br/> |The latest date that the user is available as a resource. This date corresponds to the resource availability dates for a resource that can be seen in Project Professional 2016.  <br/> |
|**Standard Rate** <br/> |The rate for the work on an assignment that is scheduled during the regular working hours of an assigned resource. To establish variable rates, open the enterprise resource in Project Professional 2016 and set this information in the Cost Rate tables.  <br/> |
|**Overtime Rate** <br/> |The rate for the work on an assignment that is scheduled beyond the regular working hours of an assigned resource. To establish variable rates, open the enterprise resource in Project Professional 2016 and set this information in the Cost Rate tables.  <br/> |
|**Current Max. Units (%)** <br/> |The percentage of time that the resource is available for assignments. The current max units is tied to the early and late availability dates, if set. For example, if today is 1/1/2012 and the earliest available date is 1/2/2012 then the max units value is 0% and text next to the field says "Custom availability detected, edit in Project Professional 2016."  <br/> |
|**Cost/Use** <br/> |The per-use cost of the resource if applicable. For work resources, a per-use cost accrues every time that the resource is used. For material resources, a per-use cost is accrued only one time.  <br/> |

## Exchange Server Details

Use the **Exchange Server Details** section to specify Exchange Server settings for the user.

Select the **Synchronize Tasks** check box if you want to enable task synchronization by using Microsoft Exchange Server for this user. Exchange integration must be configured for task synchronization to function.

Select the **Synchronize Out of Office Events** check box if you want to enable synchronization of the user's out of office information from Exchange Server to their Project Web App resource calendar as non-working time.

## Departments

Use the **Departments** section to define whether the user is a member of a particular department. (You define departments for your organization by populating the Departments custom lookup table.)

If the user is a member of a department, click the expand button ( **…**) and select the department from the displayed hierarchy.

## Security Groups

Use the **Security Groups** section to specify the user's membership in security groups.

To add the user to a security group, select the group in the **Available Groups** list, and then click **Add**.

The following table describes the security group configuration options for a user.

|**Attribute**|**Description**|
|:-----|:-----|
|**Available Groups** <br/> |The **Available Groups** list contains the groups that the user is currently not a member of. <br/> |
|**Groups that contain this user** <br/> |The **Groups that contain this user** list contains the groups that the user is currently a member of. <br/> |

## Security Categories

Use the **Security Categories** section to specify the user's membership in security categories.

To add the user to a category, select the category in the **Available Categories** list, and then click **Add**. To modify the category permissions for this user in a category, select the category in the **Selected Categories** list, and then select **Allow** for the permissions that you want to enable.

> [!IMPORTANT]
> We recommend that you do not set category permissions for a single user. Instead, assign the user to a group and set category permission for the group. This allows for easier maintenance. 

The following table describes the security category configuration options for a user.


| **Attribute**                           | **Description**                                                                                                                                                                                               |
|:----------------------------------------|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Available Categories** <br/>          | The **Available Categories** list contains the categories that the user is not a member of. <br/>                                                                                                             |
| **Selected Categories** <br/>           | The **Selected Categories** list contains the categories that the user is a member of. <br/>                                                                                                                  |
| **Permissions for \<category>** <br/>    | The **Permissions for \<category>** area lets you configure category permissions for this user for the selected category. <br/>                                                                                |
| **Set permissions with Template** <br/> | The **Set permissions with Template** option can be used to prepopulate a set of category permissions based on a predefined template for the user's role (such as Portfolio Viewer or Project Manager). <br/> |

## Global Permissions

Use the **Global Permissions** section to configure global permissions for the user.

To allow or deny a global permission for the user, select the **Allow** or **Deny** check box for the permission.

We recommend that you do not configure global permission for a single user. Instead, configure permissions at the group level and add users to the appropriate group. Doing this allows for much easier administration and helps in troubleshooting permissions issues.

For a complete list of global permissions for Project Server 2013, see [Global permissions in Project Server 2013](global-permissions-in-project-server-2013.md).

## Group Fields

Use the **Group Fields** section to define group and cost information for the user. Group fields are not tied to Project Web App security, but are a way to specify that a user belongs to a particular group in your organization. These fields appear in the Project Web App database and can be used for reporting. Cost Type can be added to the resource and assignment OLAP cubes.

If your organization uses group names, codes, or cost center information for people, type the information in the **Group Fields** area. The values available for Cost Type are those that are defined in the **Cost Type** custom lookup table. By default, the **Group** field is synchronized with Active Directory if you use Active Directory synchronization.

## Team Details

Use the **Team Details** section to define a team association for the user. To use teams, you must first do the following:

1. Create a custom lookup table and populate it with the team names that you want to use.

2. Edit the **Team Name** custom field to use the new lookup table.

You can use teams to pool assignments under a single resource where they can be later reassigned to other resources. For example, you could create a team resource named "Development" to which you assign software development tasks. By assigning this resource to the Development team and selecting the **Team Assignment Pool** check box, you enable other users on the Development team to see any tasks assigned to the Development resource and to accept the assignments in Project Web App. You could also select **Team Assignment Pool** for a team lead and have all assignments go through that person for distribution to team members.

## System Identification Data

The **System Identification Data** section displays user metadata, such as when the account was created, updated, or checked out.

In the **System Identification Data** section, type additional identifying information for the user in the **External ID** box. This information can be used to link the person to corresponding information elsewhere in the organization, or to facilitate the consolidation of reporting of resource use beyond what Project Server provides.

The following table describes the system identification data fields.

|**Attribute**|**Description**|
|:-----|:-----|
|**GUID** <br/> |The unique ID associated with this user.  <br/> |
|**External ID** <br/> |An identifier that can be used to link this user to external data.  <br/> |
|**Active Directory GUID** <br/> |The unique ID for this user's Active Directory account.  <br/> |
|**Date Created** <br/> |The date this user account was created.  <br/> |
|**Date last updated** <br/> |The date this user account was last updated.  <br/> |
|**Checked out by** <br/> |The user who currently has this user account checked out.  <br/> |
|**Checkout date** <br/> |The date this user account was checked out.  <br/> |

## See also


[Manage users in Project Server](manage-users-in-project-server.md)

[Modify user accounts in Project Server](modify-user-accounts-in-project-server.md)

[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)