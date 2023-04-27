---
title: "Manage security group synchronization with Active Directory in Project Server"
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/27/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 4d9fd5f9-669b-4b60-bc6f-1696ca4c15fe
description: "Summary: You can configure Project Server security groups in Project Web App to synchronize with security or distribution groups in Active Directory."
---

# Manage security group synchronization with Active Directory in Project Server
  **Summary:** You can configure Project Server security groups in Project Web App to synchronize with security or distribution groups in Active Directory.<br/>
**Applies to:** Project Server Subscription Edition, Project Server 2019, Project Server 2016, Project Server 2013
  
> [!NOTE]
> To configure Active Directory synchronization to Project Web App security groups, your Project Server instance must be in Project Server Permission Mode. The settings are not available in SharePoint Permission Mode. For more information about Project Server Permission Mode, see [Plan user access in Project Server](plan-user-access-in-project-server.md). 
  
Project Server security group synchronization controls Project Server security group membership by automatically adding and removing users from specified Project Server security groups based on group membership in the Active Directory directory service. Each Project Server security group can be mapped to a single Active Directory group. Additionally, an Active Directory group can contain nested groups whose members are also synchronized.
  
The following actions can occur during a Project Server security group synchronization process:
  
- A new Project Server user account can be created based on an Active Directory account.
    
- An existing Project Server user can be removed from a Project Server security group.
    
- An existing Project Server user can be added to a Project Server security group.
    
- An existing Project Server user account's metadata (name, e-mail address, and so on) can be updated if it has changed in Active Directory.
    
Before you perform this procedure, confirm the following:
  
- The account with which you are accessing Project Server through Project Web App (PWA) has both the **Manage Active Directory Settings** and the **Manage users and groups** global permissions enabled.
    
- The Service Application service account for the Project Server instance has Read access to all Active Directory groups and user accounts involved in the synchronization. You can verify this account on the Service Application page on the SharePoint Central Administration website. 
    
## Security group synchronization scenarios

The following are possible scenarios and corresponding actions that occur when security group synchronization takes place:
  
|**Scenario**|**Action**|
|:-----|:-----|
|The user exists in Active Directory and is a member of the Active Directory group mapped to the current Project Server security group. The user does not exist in Project Server.  <br/> |A new corresponding user account is created in Project Server and is granted membership to the current Project Server security group.  <br/> |
|The user is not a member of the Active Directory group mapped to the current Project Server security group. The user also exists in Project Server and is a member of the current Project Server security group.  <br/> |The existing Project Server user is removed as a member of the current Project Server security group.  <br/> |
|The user exists in Active Directory and is a member of the Active Directory group mapped to the current Project Server security group. The user also exists in Project Server, but is not a member of the current Project Server security group.  <br/> |The existing Project Server user is given membership to the current Project Server security group.  <br/> |
|The user exists in Active Directory and is a member of the Active Directory group mapped to the current Project Server security group. The user also exists in Project Server and is a member of the current Project Server security group. User information has been updated in Active Directory.  <br/> |The corresponding Project Server user information is updated (if applicable).  <br/> |
|The user exists in Active Directory and is a member of the Active Directory group mapped to the current Project Server security group. The user also exists in Project Server, but as an inactive account.  <br/> |If the **Automatically reactivate currently inactive users if found in Active Directory during synchronization** option is selected in Project Server, the account is reactivated and is added to the current Project Server security group. If the option is not selected, the account remains inactive in Project Server. <br/> |
   
## Configure security group synchronization with Active Directory groups

Project Web App security group synchronization with Active Directory groups is done through the Manage Groups page of your Project Web App Server Settings.
  
### To configure security group synchronization

1. On the Project Web App Server Settings page, in the **Security** section, click **Manage Groups**.
    
2. On the Manage Groups page, in the **Group Name** column, click the name of the security group that you want to synchronize.
    
3. On the Add or Edit page for the group that you selected, in the **Active Directory Group** section, type the name or SAM account of the Active Directory group to which you want to synchronize with this PWA group. As you type the group name, Active Directory groups that contain the text string will appear in the results. Select the Active Directory group that you want to synchronize from the results.
    
    To select a group from a remote forest, type the fully qualified domain name of the group (for example, group@corp.contoso.com). 
    
    > [!NOTE]
    > You can synchronize to a security or distribution group of any scope (Local, Global, or Universal). 
  
4. Click **Save** to save the settings.
    
5. On the Manage Groups page, click **Active Directory Group Sync Options**.
    
6. On the Sync Project Web App security groups with Active Directory dialog page, you can enable inactive user accounts to be reactivated if they are found in the Active Directory group during synchronization. To do so, select **Automatically reactivate currently inactive users if found in Active Directory during sync**. For example, if you enabled this option, it would ensure that if an employee were rehired, the employee's user account would be reactivated.
    
7. Click **Save** to save the settings. Click **Save and Synchronize Now** if you want to synchronize your Project Server security groups immediately. The Status section describes the last time Project Web App groups were synchronized with Active Directory.
    
    > [!NOTE]
    > Clicking the **Save and Synchronize Now** button will synchronize all security groups to configured Active Directory groups. Do not select individual security groups at the manage groups page before clicking **Active Directory Group Sync Options**, as this does not affect which groups are synchronized. 
  
You can view the Manage Groups page to see which PWA security groups are synchronized to Active Directory groups and the last time synchronization occurred for each security group. 
  
- The Active Directory Group column shows which Active Directory groups are configured to synchronize with a PWA security group.
    
- The Last Sync column shows the last time synchronization occurred successfully for each group.
    
## Schedule Active Directory synchronization to PWA security groups

You can schedule the frequency that Active Directory synchronization to PWA security groups occurs by using the **Project Server: Synchronization of AD with security groups** timer job configuration settings in Central Administration. This can be scheduled over a defined period of minutes, days, weeks, or months. The following procedure shows you how to access the **Project Server: Synchronization of AD with security groups** timer job configuration settings in Central Administration and describes the scheduling options that are available.
  
### To schedule Active Directory synchronization to PWA security groups

1. In Central Administration, click **Monitoring**.
    
2. On the Monitoring page, in the **Timer Job** section, click **Review job definitions**.
    
3. On the Job Definitions page, find and click **Project Server: Synchronization of AD with security groups for PWAIntanceName**. 
    
    For example: Project Server: Synchronization of AD with security groups for https://contoso/pwa.
    
4. On the Edit Timer Job page for the job, in the **Recurring Schedule** section, you can configure when the synchronization will run on a recurring basis. In the **This timer job is scheduled to run** section, you can select one of the following options, based on your organization's requirements:
    
   - **Minutes**: Allows you to specify a frequency in which the job will run — **Every x minutes**. 
    
   - **Hourly**: Allows you to specify an interval in which the job will randomly run — **Starting every hour between x minutes past the hour and no later than y minutes past the hour**.
    
   - **Daily**: Allows you to specify an interval in which the job will randomly run — **Starting every day between x time of day and no later than y time of day**.
    
   - **Weekly**: Allows you to specify in which the job will randomly run — **Starting every week between x day of week and x time of day and no later than y day of week and y time of day**.
    
   - **Monthly**: Provides two options:
    
   - Allows you to specify an interval in which the job will randomly run — **By date: starting every month between x time of day and x day of month and no later than y time of day and y day of month**.
    
   - Allows you to specify an exact time of the month in which the timer job will run — **By day: starting every month x time of day, y day of the week, and z week of the month**. For example, **12:00AM on the first Sunday**.
    
5. Click **OK** to save your configuration changes.
    
    > [!NOTE]
    > You can click **Run Now** at any time to run the timer job immediately.
  
Notice that several options provide you a period of execution time to run the job instead of an exact time or frequency. Selecting an option that provides a period of execution time allows the timer service to select a random time within the parameters specified in order to run the job on each application server. Using an option with a period of execution time is appropriate for high-load jobs that run on multiple servers in the farm. Running this type of job on all servers of the servers simultaneously might place an unreasonable load on the farm.
  
Various factors may help you determine the frequency in which you choose to run the **Project Server: Synchronization of AD with security groups** timer job. You may want to choose to run this timer job more frequently if, in your environment, users frequently move to different groups, or if your company frequently hires or releases employees. You may also want to choose to run the job more frequently if your Project Server users are working with sensitive data.
  
## See also

[Manage Active Directory Resource Pool synchronization in Project Server 2013](manage-active-directory-resource-pool-synchronization-in-project-server-2013.md)
  
[Manage security groups in Project Server](manage-security-groups-in-project-server.md)
  
[Best practices to configure Active Directory groups for Enterprise Resource Pool synchronization in Project Server 2013](best-practices-to-configure-active-directory-groups-for-enterprise-resource-pool.md)

