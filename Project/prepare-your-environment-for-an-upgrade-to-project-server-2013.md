---
title: "Prepare your environment for an upgrade to Project Server 2013"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/22/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: 31299399-5d52-4e1b-81cf-fd85de478095
description: "Summary: After you create a plan to upgrade your environment to Project Server 2013, you must prepare you environment before you can start the actual upgrade process."
---

# Prepare your environment for an upgrade to Project Server 2013

 **Summary:** After you create a plan to upgrade your environment to Project Server 2013, you must prepare you environment before you can start the actual upgrade process.<br/>
**Applies to:** Project Server 2013

This article describes these tasks that must be done prior to upgrading from your current Project Server environment.

Prior to upgrading your Project Server 2010 data to Project Server 2013, you must prepare your upgrade environment by doing the following:

- [Deploy your Project Server 2013 destination environment](#section1)

- [Prepare your Windows PowerShell environment](#section2)

- [Disable backward compatibility mode in your Project Server 2010 environment](#section3)

- [Check your Project Server 2010 data for issues that can cause the upgrade to fail](#section4)

## Deploy your Project Server 2013 destination environment
<a name="section1"> </a>

Because in-place upgrade is not supported for upgrading to Project Server 2013, the database-attach upgrade method requires you to install Project Server 2013 so that you have an environment to which you can migrate your Project Server 2010 data.

For a Project Server 2013 installation, the minimum operating system supported is the 64-bit version of Windows Server 2008 R2 Service Pack 1 (SP1). The minimum SQL Server version supported is the 64-bit version of SQL Server 2008 R2 with Service Pack 1 (SP1). For additional Project Server 2013 system requirements for installation, see [Hardware and software requirements for Project Server 2013](hardware-and-software-requirements-for-project-server-2013.md). For information about installing Project Server 2013, see [Deploy Project Server 2013](deploy-project-server-2013.md).

> [!NOTE]
> We recommend that you first upgrade the Project Server 2010 data to a Project Server 2013 test environment before you attempt to upgrade to your production environment. 

## Prepare your Windows PowerShell environment
<a name="section2"> </a>

You use Microsoft PowerShell commands to execute many of the procedures required to upgrade to Project Server 2013. On the computer on which you installed Project Server 2013, it is important to verify that you have the ability to open the SharePoint 2016 Management Shell, and that you are able to access the PowerShell cmdlets for Project Server 2013.

### To open the SharePoint 2013 Management Shell and verify that you can access the Project Server 2013 cmdlets

1. Click **Start**, click **All Programs**, click **Microsoft SharePoint 2013 Products**, and then click **SharePoint 2013 Management Shell**. 

    This opens the SharePoint 2013 Management Shell.

2. In the SharePoint 2013 Management Shell, enter the following at the PS> prompt, and then press Enter:

   ```
   Get-Command *SPProject*
   ```

    This command provides a list of Project Server 2013 cmdlets that you are able to run.

    If you do not see any of the Project Server 2013 cmdlets in the results, verify that you had launched the SharePoint 2016 Management Shell and that Project Server 2013 has been installed. If you just installed Project Server 2013, close and reopen your SharePoint 2016 Management Shell and try this procedure again.

## Disable backward compatibility mode in your Project Server 2010 environment
<a name="section3"> </a>

When you upgrade your Project Server 2010 databases to Project Server 2013, your Project Server 2010 databases must be in native mode (not backward compatibility mode). If your Project Server 2010 databases are in backward compatibility mode (BCM) when you upgrade, you may experience some issues with your sites after upgrade (for example, missing pages), because BCM is not a supported feature in Project Server 2013. Also, if you turn off BCM in Project Server 2010 in order to meet this upgrade requirement, you must also check-out, open and save the Enterprise Global Template file in Project Professional 2010, and then check the file back in. After these requirements are met, you can then create backup copies of the Project Server 2010 databases in order to upgrade to Project Server 2013. Once you disable BCM in the Project Server 2010 environment, BCM cannot be re-enabled. If you do not want to switch the Project Server 2010 farm to native mode, you can create an intermediate Project Server 2010 farm on which to restore the original Project Server 2010 databases. You can then switch from BCM to native mode on the intermediate farm, and then use these databases to upgrade to Project Server 2013.

> [!IMPORTANT]
> It is critical that you check-out, open, save, and check-in the Enterprise Global Template file in Project Professional 2010 after you disable BCM. If this is not done, new projects created in your upgraded environment may be corrupted. 

> [!NOTE]
> For more information about backward compatibility mode, see [Project Server 2010 backward compatibility mode (BCM)](/previous-versions/office/project-server-2010/gg502585(v=office.14)). 

## Check your Project Server 2010 data for issues that can cause the upgrade to fail
<a name="section4"> </a>

The following are current known issues that occur when upgrading to Project Server 2013: 

- Upon completing the upgrade from Project Server 2010 to Project Server 2013, if you click **New** in the Project Web App ribbon, you only see the Basic Project Plan and the Sample Proposal. You do not see other project types that are available in Project Server 2013. After upgrading to Project Server 2013, you can correct this known issue with a simple workaround that is described in[Post-upgrade tasks (Project Server 2013)](./post-upgrade-tasks-project-server-2013.md).

- In Project Server 2010, the **Prevent Active Directory synchronization for this user** option is available for each user in the user's property page. Selecting this option will allow you to manually specify the security group membership for the user and prevent the user's memberships from being altered when synchronizing security groups with Active Directory. When upgrading from Project Server 2010 to Project Server 2013, this option is no longer available.

    The **Prevent Active Directory synchronization for this user** option is not available in Project Server 2013 due to improvements in Active Directory synchronization. When a Project Server 2010 user is migrated to Project Server 2013 during upgrade with this option enabled, the very first security group synchronization will remove them from any Project Server security groups that they are not a member of in Active Directory.

    Before upgrading to Project Server 2013 from Project Server 2010, verify that the **Prevent Active Directory synchronization for this user** option is disabled for all users.

    You can determine which Project Server 2010 users have the **Prevent Active Directory synchronization for this user** option enabled through the Project Server 2010 Publish database. You can use the following code:

  ```
  Use ProjectServer_Published select RES_NAME, WRES_ACCOUNT, WRES_EMAIL from MSP_RESOURCES where RES_PREVENT_ADSYNC = 1
  ```

    In order for these users to maintain their membership to their security groups in Project Server 2013, you must insure they are added to the Active Directory groups that are configured to synchronize with the Project Server security groups to which they belong.

- If your Project Server 2010 Published database contains resource accounts in which the WRES_Account field contains an empty string (the expected value is NULL), upgrade of this database will fail. To check for this condition, run the following SQL script on the backup copy of your Project Server 2010 Published database:

  ```
  Use ProjectServer_Published
  select RES_Name, RES_TYPE, RES_ID from MSP_RESOURCES where WRES_ACCOUNT =''
  ```

    If accounts with this condition are found, run the following SQL script on the same database to fix up any accounts with this condition: 

  ```
  Use ProjectServer_Published
  Update MSP_RESOURCES set WRES_ACCOUNT = null where WRES_ACCOUNT =''
  ```

    > [!NOTE]
    > We recommend that you check for this condition before attempting an upgrade, especially if you have upgraded resource accounts from Office Project Server 2007 to Project Server 2010 in the past. If your upgrade to Project Server 2013 fails because of this condition, you cannot use the same copies of your Project Server 2010 databases to fix the issue and retry upgrade. You must restore the original Project Server 2010 databases to the computer that is running SQL Server, fix the condition, and then retry the upgrade. 

## Project Server forums and documentation feedback
<a name="section4"> </a>

If you have additional questions, try the [Project forums](https://social.technet.microsoft.com/Forums/en-US/category/project). The Project forums give you the chance to have your question discussed by other participants, Project MVPs, and Project community experts.

If you would like to provide feedback on this article, choose the **Yes** or **No** option for **Did you find this article helpful?** located at the end of this page, and then type your feedback in the box that appears.

![This feedback tool appears at the end of each Project Server library article on TechNet.](images/technetFeedbackBox.png)

## See also
<a name="section4"> </a>

#### 

[Plan for upgrade to Project Server 2013](plan-for-upgrade-to-project-server-2013.md)

[Overview of the Project Server 2013 upgrade process](overview-of-the-upgrade-process-to-project-server-2013.md)
#### 

[Plan for upgrade (SharePoint 2013 Products)](/SharePoint/upgrade-and-update/plan-for-upgrade)

[Create a communication plan (SharePoint 2013)](/SharePoint/upgrade-and-update/create-a-plan-for-current-customizations-during-upgrade-to-sharepoint-2013)