---
title: "Manage Active Directory Resource Pool synchronization in Project Server 2013"
ms.author: efrene
author: efrene
manager: scotv
ms.date: 11/30/2017
ms.audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection: IT_ProjectAdmin
ms.assetid: 8f7ef435-af46-4575-baef-4f36d7debf24

description: "Summary: Use the Active Directory Resource Pool Synchronization settings in Project Server 2013 to quickly add Active Directory users as enterprise resources."
---

# Manage Active Directory Resource Pool synchronization in Project Server 2013
 
 **Summary:** Use the Active Directory Resource Pool Synchronization settings in Project Server 2013 to quickly add Active Directory users as enterprise resources.<br/>
**Applies to:** Project Server 2013
  
The **Active Directory Resource Pool Synchronization** settings are available through the Project Server 2013 Server Settings page in the **Operational Policies** section. For more information about related administrative settings, see [Operational Policies in Project Server 2013](operational-policies-in-project-server-2013.md).
  
In this article:
  
- [Changes in Active Directory Resource Pool synchronization for Project Server 2013](#changes)
    
- [User synchronization scenarios](#section1)
    
- [Requirements for Enterprise Resource Pool synchronization](#req)
    
- [Configure Enterprise Resource Pool synchronization](#section_configsynchro)
    
- [Schedule Enterprise Resource Pool synchronization](#section_schedsyncro)
    
- [Requirements for synchronizing the Enterprise Resource Pool with Active Directory users in a different domain](#section3)
    
- [SharePoint 2013 People Picker](#PP)
    
Keeping your Project Server 2013 resources synchronized with Active Directory is a good way to ensure that your resources are always current, and to automatically add the newest group's members to your list of resources.
  
Project Server 2013 Active Directory Enterprise Resource Pool synchronization is used to create or update multiple Project Server enterprise resources at the same time. For example, new employees in your department can automatically be added as Project Server enterprise resources as long as they are in the Active Directory group selected for synchronization.
  
Enterprise Resource Pool synchronization also updates enterprise resource properties with the most current data from Active Directory. For example, an employee's name and email address may change because of marriage. As long as the change is made in Active Directory and the user is in the linked group, the change occurs in the user's Enterprise Resource properties when synchronization occurs. 
  
The Enterprise Resource Pool can be mapped with up to five Active Directory groups for synchronization. These Active Directory groups can contain nested groups whose members are also synchronized.
  
## Changes in Active Directory Resource Pool synchronization for Project Server 2013
<a name="changes"> </a>

It is important to note the following changes in Active Directory Resource Pool synchronization in Project Server 2013:
  
- No Project Server user accounts will be automatically created for resources that are added to the Enterprise Resource Pool through Active Directory synchronization.
    
- You can synchronize up to five Active Directory groups with the Enterprise Resource Pool in Project Server 2013.
    
## User synchronization scenarios
<a name="section1"> </a>

The following are the two most common actions that occur during the Enterprise Resource Pool synchronization process:
  
- **A new Project Server enterprise resource can be created based on Active Directory membership** By adding a new member to the Active Directory group that is being used for your Enterprise Resource Pool synchronization, you automatically also create a resource for this user in Project Server..
    
- **An existing Project Server user account's metadata (for example, name, email address, and so on) can be updated if it has changed in Active Directory** For example, if a resource's last name was changed in Active Directory, the Project Server 2013 Enterprise Resource Pool synchronization makes sure that the resource name is also changed in the Project Server Enterprise Resource Pool.
    
The following table describes all Active Directory to Project Server 2013 Enterprise Resource Pool synchronization scenarios, as well as their corresponding actions:
  
|**Scenario**|**Action**|
|:-----|:-----|
|User exists in Active Directory and is a member of the Active Directory group mapped to the Enterprise Resource Pool. The user does not exist in Project Server  <br/> |A new Project Server resource is created for this user.  <br/> NOTE - A Project Server User Account is not created based on this synchronization. The Active Directory user needs to be added to a Project Server security group to create a user account. For more information, see [Best practices to configure Active Directory groups for Enterprise Resource Pool synchronization in Project Server 2013](best-practices-to-configure-active-directory-groups-for-enterprise-resource-pool.md).           |
|User exists in Active Directory and is a member of the Active Directory group mapped to the Enterprise Resource Pool. The user exists in Project Server as a user, but not as a resource.  <br/> |A new Project Server resource is created for this user, and is linked to the existing Project Server user account.  <br/> |
|User exists in Active Directory and is a member of the Active Directory group mapped to the Enterprise Resource Pool. The corresponding resource already exists in Project Server.  <br/> |The corresponding Project Server enterprise resource and user information is updated, if any updates were made to the user properties in Active Directory.  <br/> |
|User exists in Active Directory, but is removed from the Active Directory group mapped to the Enterprise Resource Pool.  <br/> |The resource is not inactivated in Enterprise Resource Pool.  <br/> |
|A user is marked as inactive in Active Directory.  <br/> |The resource is not inactivated in the Enterprise Resource Pool. The corresponding Project Server User is not deactivated based on this synchronization. For more information, see [Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md).  <br/> |
   
## Requirements for Enterprise Resource Pool synchronization
<a name="req"> </a>

Before you perform this procedure, confirm the following:
  
- You have access to Project Server through Project Web App with an account that has the **Manage Active Directory Settings** and the **Manage users and groups** global settings enabled.
    
- The Service Application (SA) service account for the Project Server instance has Read access to all Active Directory groups and user accounts involved in the synchronization. 
    
    You can verify this account in the Service Application properties on the Service Application Administration page on the SharePoint Central Administration website.
    
- The identity under which the Queue service runs needs to have access to all the forest and domains in which it is expected to find users.
    
- The SharePoint 2013 People Picker must be able to resolve groups and access user information from Active Directory in order for Project Server 2013 Active Directory ERP synchronization to work. The People Picker allows you to search for Active Directory groups to which you want to synchronize to the ERP. The SharePoint 2013 People Picker is described in more detail later in this article.
    
## Configure Enterprise Resource Pool synchronization
<a name="section_configsynchro"> </a>

In the Project Web App Server Settings, you access the Active Directory Enterprise Resource Pool Synchronization page in which you can configure your settings.
  
### To configure Enterprise Resource Pool synchronization

1. In Project Web App, click the **Settings** icon, and then click **Project Web App Settings**.
    
2. On the Project Web App Server Settings page, in the Operational Policies section, click **Active Directory Resource Pool Synchronization**.
    
3. On the Active Directory Enterprise Resource Pool Synchronization page, in the **Active Directory Group** section, type the name or Service Account Manager (SAM) account of the active directory group or groups you want to synchronize with the Enterprise Resource Pool. If you are unsure of the group name, you can type part of the group name to display groups in Active Directory that contain the text string. The SharePoint 2013 People Picker provides the search functionality that displays the Active Directory groups you are looking for. To select a group from a remote forest, type the fully qualified domain name of the group (for example, group@corp.contoso.com).
    
    > [!NOTE]
    > You can synchronize to a security or distribution group of any scope (Local, Global, or Universal). 
  
4. You can enable inactive accounts to be reactivated if they are found in the Active Directory group during synchronization. To do so, in **Sync options**, select **Automatically reactivate currently inactive users if found in Active Directory during sync**. 
    
    For example, an employee moves to a different role within their company and their Project Server user account is inactivated (they are removed from the Enterprise Resource Pool Active Directory group). The user later decides to go back to their old job, and they are added back to the Enterprise Resource Pool Active Directory group. If **Automatically reactivate currently inactive users if found in Active Directory during sync** is enabled, the user's account would be automatically reactivated upon synchronization.
    
    > [!NOTE]
    > For this option to be available, it requires the October 2014 Cumulative Update for Project Server 2013. For more information about this update, see this [Microsoft Project Support Blog post.](https://go.microsoft.com/fwlink/?LinkId=534101)
  
5. Click **Save** to save the settings and have synchronization scheduled to recur at the default setting (once a day at 12:00 AM). Click **Save and Synchronize Now** if you want to synchronize your Enterprise Resource Pool immediately, save your settings, and have synchronization scheduled to recur at the default setting.
    
You can check the status of the Enterprise Resource Pool synchronization by returning to the Active Directory Enterprise Resource Pool Synchronization page and reviewing the information in the **Synchronization Status** section. It contains information such as when the last successful synchronization occurred. If last synchronization failed for any reason, it will also post a timestamp of when it occurred if you wanted to search for more information in the ULS logs.
## Schedule Enterprise Resource Pool synchronization
<a name="section_schedsyncro"> </a>

In Project Server 2013, scheduling synchronization of your enterprise resource pool with Active Directory groups is done through the Timer Job Status page in Central Administration. 
  
### To schedule Enterprise Resource Pool synchronization

1. In Central Administration, click **Monitoring**.
    
2. On the Monitoring page, in the Timer Job section, click Check job status.
    
3. On the Timer Job Status page, find and then click **Project Web App: Synchronization of AD with the Enterprise Resource Pool job for <PWA site name>**. 
    
    For example: Project Web App: Synchronization of AD with the Enterprise Resource Pool job for http://contoso/pwa.
    
4. On the Edit Timer Job page, in the **Recurring Schedule** section, you can configure when the synchronization will run on a recurring basis. Under **This timer job is scheduled to run**, you can select one of the following options, based on your company's requirements:
    
   - **Minutes**: Allows you to specify a frequency in which the job will run — **Every x minutes**. 
    
   - **Hourly**: Allows you to specify an interval in which the job will randomly run — **Starting every hour between x minutes past the hour and no later than y minutes past the hour**.
    
   - **Daily**: Allows you to specify an interval in which the job will randomly run — **Starting every day between <time of day> and no later than <time of day>**.
    
   - **Weekly**: Allows you to specify in which the job will randomly run — **Starting every week between <day of week and time of day> and no later than <day of week and time of day>**.
    
   - **Monthly**: Provides two options:
    
   - Allows you to specify an interval in which the job will randomly run — **By date: starting every month between <time of day and day of month> and no later than <time of day and day of month>**.
    
   - Allows you to specify an exact time of the month in which the timer job will run — **By day: starting every month <time of day, day of the week, and week of the month**. For example, "12:00 AM on the first Sunday".
    
5. Click **OK** to save your configuration changes.
    
    > [!NOTE]
    > You can click **Run Now** at any time to run the timer job immediately.
  
Note that several options provide a period of execution time to run the job instead of an exact time or frequency. Selecting an option that provides a period of execution time allows the timer service to select a random time within the parameters specified in order to run the job on each application server. Using an option with a period of execution time is appropriate for high-load jobs which run on multiple servers in the farm. Running this type of job on all servers of the servers simultaneously might place an unreasonable load on the farm.
  
## Requirements for synchronizing the Enterprise Resource Pool with Active Directory users in a different domain
<a name="section3"> </a>

Imagine that you need to synchronize your Enterprise Resource Pool with Active Directory users that exist in a domain other than the one that Project Server 2013 is installed on. For example, your organization may acquire a new company, or your branch may need to add users from a different branch within your organization. In this scenario, a two-way trust relationship must exist between the domains in order for Active Directory users in one domain to synchronize with the Enterprise Resource Pool in a Project Server 2013 installation that exists on a different domain.
  
> [!NOTE]
> Project Server 2013 does not support synchronizing your Enterprise Resource Pool or security groups with Active Directory users across different domains in which only a one-way trust relationship exists between domains. 
  
## SharePoint 2013 People Picker
<a name="PP"> </a>

As mentioned earlier in this article, Project Server 2013 can synchronize a user from Active Directory only if this user can first be found by the People Picker.
  
People Picker will only be able to return users, groups, and claims in the following topologies: 
  
- The domain in which your SharePoint Server 2013/Project Server 2013 farm is currently installed.
    
- A domain that has a two-way trust relationship with the domain in which your SharePoint Server 2013/Project Server 2013 farm is currently installed. 
    
By default, People Picker only returns users, groups, and claims from the domain on which SharePoint Server 2013 is installed. If you want People Picker to return query results from more than one forest or domain, you can create a two-way trust between the forests or domains. For both these cases, People Picker functions automatically, and no additional configuration is necessary. When two-way trusts are established, the People Picker automatically returns results found in the trusted domains. 
  
For example, the Contoso.com domain has a two-way trust with Litware.com and Fabrikam.com. The Project Server 2013 ERP synchronization defined in the Contoso.com domain in which the Project Server 2013 farm resides is configured to include Bob (from the Fabrikam.com domain) and Mindy (from the Litware.com domain). People Picker finds both groups in which both Bob and Mindy reside in their domain's Active Directory, the Project Server 2013 ERP synchronization will synchronize the group and both users successfully. If no trust or a one-way trust existed between the Contoso.com domain and the other domains, the users would not be able to synchronize to the Project Server 2013 ERP.
  
![People Picker - Domains with Two-Way Trust](images/ADSyncPeoplePickerTrustDomain.jpg)
  
## See also
<a name="PP"> </a>

#### 

[Best practices to configure Active Directory groups for Enterprise Resource Pool synchronization in Project Server 2013](best-practices-to-configure-active-directory-groups-for-enterprise-resource-pool.md)
  
[Supported Active Directory topologies for Project Server 2013 Enterprise Resource Pool synchronization](supported-active-directory-topologies-for-project-server-2013-enterprise-resourc.md)
  
[Manage security group synchronization with Active Directory in Project Server](manage-security-group-synchronization-with-active-directory-in-project-server.md)

[People Picker and claims providers overview (SharePoint 2013)](http://technet.microsoft.com/library/bf8717c2-463d-4e8d-acaf-f186b5907df1.aspx)
  
[Plan for People Picker in SharePoint 2013](http://technet.microsoft.com/library/2093c146-c880-48c6-9526-24cdf80969ba.aspx)

