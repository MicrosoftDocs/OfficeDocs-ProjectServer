---
title: "Deploying Project"
ms.author: alexla
author: alexla
manager: hocull
ms.date: 01/07/2021
audience: admin
ms.topic: article
ms.service: project-web
localization_priority: Normal
description: "Learn how to deploy Project to the Dataverse."
---

# Deploying Project

> [!Note]
> This section refers to upcoming functionality. Project can only be deployed to the default Dataverse instance. It is not yet possible to deploy Project to other types of Dataverse instances.

Project for the web is available for use in the Default Environment as well as in Sandbox and Production Dataverse environments.

Project for the web in the Default environment enables customers to quickly get started creating projects, managing schedules, and sharing them with other users in the organization. Because everyone is a member of this environment by default, enabling users to create and manage Projects only requires that you assign a Project license to them.

For some situations, you should consider deploying Project to additional environments. These are:
* Application Lifecycle management (Development/Test/Production)
* Data residency requirements for when the tenant is in a different geography than the users
* Customizing Project to behave differently for different business units

If you are looking to deploy to additional environments, you will need to create the environments, deploy Project, and configure access for users.

[Learn more about Dataverse environments](https://docs.microsoft.com/power-platform/admin/environments-overview)

## Provisioning a new environment
> [!Note]
> This section only applies to Admins interested in deploying Project to a non-Default environment.

Project is supported in the following types of environments
* Default
* Production
* Sandbox

To be able to deploy to Sandbox and Production environments, the environment needs to be created with a database and the "Enable Dynamics 365 Apps" toggle *must* be disabled.

 ![D365 App Toggle](media/AppToggle.png) 

[Learn more about creating and managing environments](https://docs.microsoft.com/power-platform/admin/create-environment)

## Deploying Project for the web

### System requirements

In order to be able to provision and use a project for the web, there are system prerequisites which are expected to be on, by default. The details of these system prerequisites are provided in the table below.

**Enterprise applications**

The following enterprise applications are to be enabled, by default.


|Application Name  |Application ID  |
|---------|---------|
|  Dynamics Provision   |    39e6ea5b-4aa4-4df2-808b-b6b5fb8ada6f      |
|Common Data Service    |      00000007-0000-0000-c000-000000000000    |
|Microsoft Flow     |      7df0a125-d3be-4c96-aa54-591f83ff541c    |
|Microsoft PowerApps    |  475226c6-020e-4fb2-8a90-7a972cbfc1d4        |
|Dynamics CRM Online Administration   |     637fcc9f-4a9b-4aaa-8713-a2a3cfda1505     |

**Verifying status of Enterprise applications**

To verify whether the required Enterprise applications are enabled, perform the following steps:

1. Sign in to as the tenant admin using https://aad.portal.azure.com/  

2. Click **Enterprise Applications**. The **Enterprise applications** screen appears.

<include the image enterprise-applications-screen.png>

3. From the **Application Type** dropdown, choose **All Applications** and click **Apply**. 

<include the image choosing-all-applications-value.png>

4. Use the textbox right below and search for the application ID listed in the table above. For example, **39e6ea5b-4aa4-4df2-808b-b6b5fb8ada6f**. The application **Dynamics Provision** is displayed in the result pane.

<include the image application-id-and-result.png>

5. Click **Dynamics Provision**. The **Dynamics Provision** screen appears.

<include the image dynamics-provision-screen.png>

6. Click **Properties** on the left pane.

<include the image dynamics-provision-properties.png>

7. Ensure that **Enabled for users to sign-in** is set to **Yes**.

<include the image configure-status-of-user-sign-in.png>

8. Repeat Steps 1-7 for each of the Enterprise applications listed above.

**Verifying status of required Enterprise applications using Azure Active Directory PowerShell for Graph**

For administrators who prefer [Azure Active Directory PowerShell for Graph](https://docs.microsoft.com/powershell/azure/active-directory/install-adv2) instead of the above manual steps, they can use the following script to check if the above list of Applications are enabled:

```powershell
Connect-AzureAd
Write-Host "Detecting required Azure AD Applications that have been disabled..." -ForegroundColor Yellow
$ProjectRequiredAppsThatAreDisabled = Get-AzureADServicePrincipal -Filter "
AppId eq '00000007-0000-0000-c000-000000000000' or '475226c6-020e-4fb2-8a90-7a972cbfc1d4' or '637fcc9f-4a9b-4aaa-8713-a2a3cfda1505' or '7df0a125-d3be-4c96-aa54-591f83ff541c'  or'39e6ea5b-4aa4-4df2-808b-b6b5fb8ada6f'" | ? {$_.AccountEnabled -eq $false}

If ($ProjectRequiredAppsThatAreDisabled) 

{ 

    Write-Host "Required Azure AD Apps that have been disabled: " 

    $ProjectRequiredAppsThatAreDisabled | Select AppId, DisplayName, AccountEnabled, ObjectId | ft -a 

} 

Else 

{ 

    Write-Host "All Azure AD Applications required for Project for the web functionality has been enabled." -ForegroundColor Yellow 

}
```
The following script does the same as above and in addition, for each disabled application, it prompts the administrators if they want it enabled:

```powershell
Connect-AzureAd
Write-Host "Detecting required Azure AD Applications that have been disabled..." -ForegroundColor Yellow 

$ProjectRequiredAppsThatAreDisabled = Get-AzureADServicePrincipal -Filter " 
AppId eq '00000007-0000-0000-c000-000000000000' or '475226c6-020e-4fb2-8a90-7a972cbfc1d4' or '637fcc9f-4a9b-4aaa-8713-a2a3cfda1505' or '7df0a125-d3be-4c96-aa54-591f83ff541c' or '39e6ea5b-4aa4-4df2-808b-b6b5fb8ada6f' " | ? {$_.AccountEnabled -eq $false}

If ($ProjectRequiredAppsThatAreDisabled) 

{ 

    Write-Host "Required Azure AD Apps that have been disabled: " 
    $ProjectRequiredAppsThatAreDisabled | Select AppId, DisplayName, AccountEnabled, ObjectId | ft -a 

      #For each detected App that has been disabled, reenable it.  

    foreach ($DisabledApp in $ProjectRequiredAppsThatAreDisabled) 

    { 
        Write-Host "`nProcessing Application: $($DisabledApp.DisplayName) with Application Id: $($DisabledApp.AppId) and AccountEnabled state of: $($DisabledApp.AccountEnabled)" -ForegroundColor Yellow 

        $ResponseToEnableApp = Read-Host "Do you want to enable this application? [Yes or No]" 

        while("Yes","No" -notcontains $ResponseToEnableApp){$ResponseToEnableApp = Read-Host "Do you want to enable this application? [Yes or No]"} 

        if ($ResponseToEnableApp -ieq "Yes") 
        { 
            Set-AzureADServicePrincipal -ObjectId $DisabledApp.ObjectId -AccountEnabled $True 
            Write-Host "App: $($DisabledApp.DisplayName) has been enabled." 
        } 
 else 
        { 
            Write-Host "AccountEnabled state for app: $($DisabledApp.DisplayName) left as is at the current state of: $($DisabledApp.AccountEnabled)" 
        } 
    } 
} 
Else 
{ 
    Write-Host "All Azure AD Applications required for Project for the web functionality has been enabled." -ForegroundColor Yellow 
} 
```

### Deploying to the Default environment

Deployment of Project to the Default environment is done for you automatically. When Project for the web or Roadmap are first used in an Office 365 tenant, a Default Dataverse instance is provisioned for the tenant and the solutions are deployed.

### Deploying to a non-Default environment
Deploying Project to a non-Default environment is done from within the [Power Platform Admin Center (PPAC)](https://admin.powerplatform.microsoft.com). 

Open the **Resources > Dynamics 365 apps** page from the left-hand navigation menu. Then, install the **Project Service Core** package into your environment.
![Project package](media/InstallProject.png) 

> [!Note]
> If the installation package isn't appearing in the list of available packages, either the tenant doesn't have a Project license, or the environment was created with the "Enable Dynamics 365 Apps toggle" enabled. 


[Learn more about using the PPAC to deploy applications](https://docs.microsoft.com/power-platform/admin/manage-apps)

## Configuring Roles and Security

Sandbox and Production environments require additional configuration. Assign the **Project Common** and **Project User** roles to anyone who will be creating Projects in the environment. Also, ensure these users have the appropriate Project license.

There is no additional configuration needed to enable users to manage Projects in the Default environment. Users in the Default environment only need a Project license to be able to create and manage Projects. 

[Learn more about security roles in the Dataverse](https://docs.microsoft.com/power-platform/admin/security-roles-privileges)

> [!Note]
> Project-related roles are only available after the Project Service Core package has been deployed to the environment.

## Creating and managing projects in non-Default environments

In non-Default environments, projects are created and managed via the Project Power App. Users with the Project User and Project Common roles will see the Project app tile appear in [Dynamics Home](https://home.dynamics.com).
