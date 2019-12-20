---
title: "Turn off Project for the web "
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: 
search.appverid: PJO150
localization_priority: Normal
description: "Learn how to turn off Project for the web for users in your organization."
---


# Turn off Project for the web for specific users in your organization

 An admin can manage access to Project for the web for specific users by assigning and unassigning the associated licenses. 

Access to Project for the web is granted to users if they are assigned one of the following licenses:

- Project Plan 1
- Project Plan 3 (previously called Project Online Professional)
- Project Plan 5 (previously called Project Online Premium)

 If you want to turn off Project for the web for specific users in your organization, an admin can do this by turning off the service for the user in the Microsoft 365 Admin Center.  

You might want to do this if your users currently use Project Online (through Project Plan P3 or Project Plan P5 licenses) and you don't want to give all of your users access to Project for the web at the moment.

> [!NOTE]
> Turning off Project for the web for the user will also turn off the Roadmap feature for them.

To turn off Project for the web for a user:

1. In the Microsoft 365 Admin Center, select **Users**, then select **Active Users**.
2. From the **Active users** list, select the checkbox next to the user, and then click **Manage product licenses**.</br>
![Select user](media/activeusers.png)
3.  On the user information page, select the **licenses and app** tab, in the **Apps** section,  select the user's Project Online license from the **Show apps for** drop down menu. This would be either Project Online Professional or Project Online Premium.
4. In the list of apps that display, uncheck **Project P3**, and then click **Save changes**.</br>
> [!Important]
> The service plan that disables Project for the web is called **Project P3**.  It is important to distinguish it from **Project Plan 3**, which is one of the three licenses in which Project for the web is available. Project Plan 1, Project Plan 3, and Project Plan 5 are all licenses that have the Project P3 service plan.</br>  
![Select user](media/p3service.png)

You can repeat this procedure for each user that you don't want to use Project for the web.

> [!NOTE]
> You cannot turn Project for the web off to your organization (like you can for Roadmap in the Project Online settings in the Microsoft 365 Admin Center).

## Turn off Project for the web for multiple users using Windows PowerShell

If you need to disable Project for the web for a large number of users, an admin can do this through Windows PowerShell.

> [!Note]
> Before attempting this, you first need to [install the required modules](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) and be a global admin on your tenant. </br>
> Also, when you open Windows PowerShell, make sure to run as an administrator. 



1. In Windows PowerShell, type and enter the following to sign into your tenant.</br>
```PowerShell
Connect-MsolService
```
2. Type the following to find the **AccountSkuId** of your Project Online licenses.</br>
```PowerShell
Get-MsolAccountSku
```
You should see a list of the licenses available on your tenant, for example:
![AccountSKUId](media/AccountSKUID.png) </br>
3. Look for the accountSKUid values that contain **PROJECTPREMIUM** or **PROJECTPROFESSIONAL**.
   - PROJECTPREMIUM is Project Plan 5 (Project Online Premium)
   - PROJECTPROFESSIONAL is Project Plan 3 (Project Online Professional)

        The value will be prefixed by the tenant domain name. For example, in the image above, the AccountSKUID value for the Project Online Premium license is **M365x115998:PROJECTPREMIUM**.</br>

4. Create a $LicenseOption object that disables the Project P3 service plan (PROJECT_PROFESSIONAL) from the Project Plan 3 and Project Plan 5 licenses (the AccountSKUID values). </br>In our example, the following will disable the Project P3 service plan in a Project Plan 5 license.</br>
```PowerShell
$LicenseOptionsPremium = New-MsolLicenseOptions -AccountSkuId "M365x115998:PROJECTPREMIUM" -DisabledPlans "PROJECT_PROFESSIONAL"
```
If the tenant had Project Plan P3 licenses (Project Online Professional) , the following will disable it in that license. </br>
```PowerShell
$LicenseOptionsProfessional = New-MsolLicenseOptions -AccountSkuId "M365x115998:PROJECTPROFESSIONAL" -DisabledPlans "PROJECT_PROFESSIONAL"
```
5. After you've created the objects, create a list of your user accounts in which you'd like to disable Project for the web.  There are different ways to do this, such as importing from a CSV file.  For our example, we'll create a UPNList with the user accounts in which we want to disable Project for the web.</br>
```PowerShell
`$UPNList = @("AdeleV@M365x115998.OnMicrosoft.com","AlexW@M365x115998.OnMicrosoft.com")
```

6. After creating your list, apply the applicable $LicenseOption object to each user account. </br>For our example, we're applying the $LicenseOptionsPremium object to each user in the UPNList, which would disable Project for the web from each user who has a Project Plan P5 license.  </br>
```PowerShell
ForEach ($UPN in $UPNList)
{
    Set-MsolUserLicense -UserPrincipalName $UPN -LicenseOptions $LicenseOptionsPremium    
}
```
For more information about disabling services through Office 365 PowerShell, see [Disable access to services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell). 

## Turn Project Online off

An admin may want certain users to have access to Project for the web and the Roadmap feature, and not Project Online.  To do this, an admin would need to turn off the Project Online service for the user through their assigned Project Plan 3 or Project Plan 5 license.  

> [!Note]
> Roadmap is only available in read-only through the Project Plan 1 license. You will not be able to edit or create a new roadmap.

To turn off Project Online:

1. In the Microsoft 365 Admin Center, select **Users**, then select **Active Users**.
2. From the **Active users** list, select the checkbox next to the user, and then click **Manage product licenses**.</br>
![Select user](media/activeusers.png)
3.  On the user information page, select the **licenses and app** tab, in the **Apps** section,  select the user's Project Online license from the **Show apps for** drop down menu. This would be either **Project Plan 3** or **Project Plan 5**.
4. In the list of apps that display, uncheck **Project Online Service**, and then click **Save changes**.</br>
 
    ![Project Online Service](media/projectonlineservice.png) 

    You can repeat this procedure for each user that you want to use only Project for the web and Roadmap.


## See Also
  
  



