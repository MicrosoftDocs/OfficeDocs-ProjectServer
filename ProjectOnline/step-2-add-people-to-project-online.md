---
title: "Step 2 Add people to Project Online"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 12/14/2017
ms.audience: End User
ms.topic: overview
ms.service: project-online
localization_priority: Normal
search.appverid:
- PJO150
- PJO160
ms.assetid: e65c6c3b-68af-4d13-9504-5626b73e54ce

description: "The second step in getting started with Project Online is adding the people who will use it."
---

# Step 2: Add people to Project Online

|||
|:-----|:-----|
|![Get set up](media/6b503a9c-4ef0-409b-ab56-09e804cfe0c3.png)           <br/> |[![Step 1: Sign up for Project Online](media/f82f0100-dc58-47d6-960a-28db901de6d8.png)](step-1-sign-up-for-project-online.md)          ![Step 2: Add people to Project Online](media/1e3028cb-08d7-482c-b57c-c2f24a4951a0.png)          [![Step 3: Set up shop in Project Online](media/e27ceef5-1c39-43e4-92ac-300d58fb65c8.png)](step-3-set-up-shop-in-project-online.md) <br/> |
   
## 1. First, add people to Office 365
<a name="__top"> </a>

|||
|:-----|:-----|
|![Add user](media/adf53af3-c248-4fd8-95fd-26c2a7cdb3e4.png)           <br/> |
|||
|:-----|:-----|
|Start by adding users in the Office 365 admin center. If you are adding Project Online to an existing Office 365 subscription, you may have already added all the users you need and can skip this step.  <br/> > [!IMPORTANT]> **Planning to use your own domain (like contoso.com)?**[Add a domain to Office 365](https://support.office.com/article/6383f56d-3d09-4dcb-9b41-b5f5a5efd611), before adding your Project Online users. **Changing domains after you've added users is not supported!**         ||
   
|||
|:-----|:-----|
|![Arrow](media/2005a697-28c3-44a3-9194-3a1e2af483ac.png)           <br/> |**When you're ready to add someone to Project Online, start by adding users:** <br/> Choose Users \> Active Users from the left menu on the Office 365 admin center. At the top of the list of users, choose + Add a user. Fill out the account information. Under Product licenses, make sure a Project Online license is assigned, and then choose Add. Choose whether to send the new user's password in email, and then add another user. For more information, see [Add users individually or in bulk to Office 365 - Admin Help](https://support.office.com/article/1970f7d6-03b5-442f-b385-5880b9c256ec) <br/> |
   
|
   
## 2. Next, group people by what they'll be doing with Project Online
<a name="__top"> </a>

|||
|:-----|:-----|
|![Share](media/94aea025-98ff-4a16-af99-3f91e31ed1e9.png)           <br/> |
||
|:-----|
|Now that you've added people to Project Online, the next step is to divide them into groups by how they'll be using it.  <br/> **Not everyone needs access to everything** available in Project Online. Usually, your organization can be sorted into the following roles:  <br/> ||||
|:-----|:-----|:-----|
|Role  <br/> |Description  <br/> |Permission name  <br/> |
|Admins  <br/> |People who need full control over your Project Online subscription. Admins manage your user list, who gets what level of access, and also manage all the main project settings.  <br/> |**Administrators for Project Web App [Full Control]** <br/> |
|Project managers  <br/> |People who will create and manage project files. Project managers will create projects and tasks, assign resources, manage timesheets, and otherwise be in charge of projects and project files.  <br/> |**Project Managers for Project Web App [Design, Manage Subsites]** <br/> |
|Team members:  <br/> |People who perform project tasks. Team members receive assignments and fill out progress and timesheets.  <br/> |**Team Members for Project Web App [Read]** <br/> |
   
For the full list of permissions available with Project Online, see [Plan SharePoint groups in Project Online](plan-sharepoint-groups-in-project-online.md).  <br/> |
   
|||
|:-----|:-----|
|![Arrow](media/2005a697-28c3-44a3-9194-3a1e2af483ac.png)           <br/> |**To more easily manage people in Project Online, create a security group for each of the roles you need:** <br/> Choose Groups \> Groups from the left menu on the Office 365 admin center. At the top of the list of groups, choose + Add a group. For type, choose Security group. There are other group types in Office 365, but this is the one that can most easily manage your Project Online users. For more information on different types of groups, see Compare groups. Type a name for your group. It might be easiest to pick a name that refers to the permission level. For an organization named Contoso, you could name your group "Contoso admins" or "Contoso team members". Choose Add. |
   
|||
|:-----|:-----|
|![Arrow](media/2005a697-28c3-44a3-9194-3a1e2af483ac.png)           <br/> |Then, add users to groups.  <br/> To add users to groups:  <br/> Choose Users \> Active users. Select the check box for each user you want to add to your first security group, and choose + Add to group in the Bulk actions pane. Choose a group from the Group memberships list, and then choose Save \> Close. |
   
|
   
## 3. Then, add people as resources
<a name="__top"> </a>

|||
|:-----|:-----|
|![Add user](media/adf53af3-c248-4fd8-95fd-26c2a7cdb3e4.png)           <br/> |
|||
|:-----|:-----|
|**Not every user needs to be a resource.** Sometimes, people like higher-level executives only need access to Project Online to keep an eye on how projects are going across the organization.  <br/> |![Users and resources](media/2cc5476a-68eb-4f42-8ca4-6e1c672f2c0c.png)           <br/> |
   
|||
|:-----|:-----|
|||
|![Arrow](media/2005a697-28c3-44a3-9194-3a1e2af483ac.png)           <br/> |**If you know a person will work on projects and tasks, make that user a resource:** <br/> On the Office 365 app launcher , choose Project.  Choose Resources on the left menu. You can either:   Add many resources at a time: If you haven't added any resources yet, you can synchronize with an existing group.   On the Resource Center page, choose click here in the first sentence: "To add resources, click here to synchronize with an existing group."   On the Active Directory Enterprise Resource Pool Synchronization page, type the name of a security group in the Active Directory Group box.   Choose Save.   Repeat for any other security groups you want to create resources for. When you've added all the security groups you want, choose Save and Synchronize Now.   Add resources one at a time:   On the Resource Center page, choose Resources \> New.   There are a lot of things you can fill out here, but only two things are really important right now:   Under Identification Information, choose Associate resource with a user account.   Under User Authentication, in the User logon account box, type the name of the user you want working on projects and tasks.   Choose Save when you're done.  |
   
|
   
## 4. Finally, share Project Online with the people you added
<a name="__top"> </a>

|||
|:-----|:-----|
|![Share](media/94aea025-98ff-4a16-af99-3f91e31ed1e9.png)           <br/> |Now that you've added people to Project Online, the next step is to share the site with them so they can actually get in!  <br/> **When you share the Project Online site with a user, you also decide what they can do in Project Online:** <br/> In Project Online, choose Share, just below your name in the top-right portion of the page. You can share with individuals or security groups. Share by security group if you've created security groups for each permission level you want to use. Type either the name of the security group or the name of the individual user in the top box, and then choose Show Options. Under Select a group or permission level, choose the permission level that matches what the security group or person's role is in your organization. For example, for the Contoso admins security group, choose Administrators for Project Web App [Full Control]. Choose Share. Repeat this process for all additional groups or individuals you want to use Project Online. |
   
## NEXT STEP...
<a name="__top"> </a>

Next, learn about [Step 3: Set up shop in Project Online](step-3-set-up-shop-in-project-online.md).
  
[![Step 1: Sign up for Project Online](media/f82f0100-dc58-47d6-960a-28db901de6d8.png)](step-1-sign-up-for-project-online.md)![Step 2: Add people to Project Online](media/be1ca863-defe-4156-a5b1-68cea288476f.png)[![Step 3: Set up shop in Project Online](media/e002dacf-722f-4af8-9d22-b606d22a8051.png)](step-3-set-up-shop-in-project-online.md)
  
||
|:-----|
|[Top of Page](step-1-sign-up-for-project-online.md#__top)|
   

