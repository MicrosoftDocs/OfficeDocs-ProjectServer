---
title: "Turn off Project for the web"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 10/28/2019
audience: admin
ms.topic: article
ms.service: 
search.appverid: PJO150
localization_priority: Normal
m
description: "Learn how to turn off Project for the web for users in your organization."
---

# Turn off Project for the web

Access to Project for the web is granted to users if they are assigned a Project P3 or Project P5 license (previously called Project Online Professional and Project Online Premium). An admin can manage access by assigning and unassigning the associated licenses. If you want to turn off Project for the web for specific users in your organization, an admin can do this by turning off the service for the user in the Microsoft 365 Admin Center.  

You might want to do this if your users currently use Project Online and you don't want to give all of your users access to Project for the web at the moment.

> [!NOTE]
> Turning off Project for the web for the user will also turn off the Roadmap feature.

To turn off Project for the web for a user:

1. In the Microsoft 365 Admin Center, select **Users**, then select **Active Users**.
2. From the **Active users** list, select the checkbox next to the user, and then click **Manage product licenses**.</br>
![Select user](media/activeusers.png)
3.  On the user information page, select the **licenses and app** tab, in the **Apps** section,  select the user's Project Online license from the **Show apps for** drop down menu. This would be either Project Online Professional or Project Online Premium.
4. In the list of apps that display, uncheck **Project P3**, and then click **Save changes**.</br>
![Select user](media/p3service.png)

You can repeat this procedure for each user that you don't want to use Project for the web.

> [!NOTE]
> You can only turn off Project for the web to one user at a time through the Office 365 Admin Center user interface.  You also cannot turn Project for the web off to your organization (like you can for Roadmap in the Project Online settings in the Microsoft 365 Admin Center).

## Turn off Project for the web to multiple users using Windows PowerShell

An admin can turn off Project for the web for multiple users through Windows PowerShell. 

> [!Note]
> Before attempting this, you first need to [install the required modules](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-microsoft-azure-active-directory-module-for-windows-powershell) and be a global admin on your tenant.





1. In Windows PowerShell type and enter the following to sign into your tenant.</br>
`Connect-MsolService`
2. Type the following to find the **AccountSkuId** of your Project Online licenses.</br>
`Get-MsolAccountSku`</br>
You should see a list of the licenses available on your tenant, for example:
![AccountSKUId](media/AccountSKUID.png) 
3. Look for the accountSKUid values that contain **PROJECTPREMIUM** or **PROJECTPROFESSIONAL**.
    - PROJECTPREMIUM is Project Online Premium
    - PROJECTPROFESSIONAL is Project Online Professional

    The value will be prefixed by the tenant domain name. For example, in the image above, the AccountSKUID value for the Project Online Premium license is **M365x115998:PROJECTPREMIUM**.
 4. Create a $LicenseOption object that disables the Project P3 service plan (PROJECT_PROFESSIONAL) from the Project Online licenses (the AccountSKUID values).</br>
`$LicenseOptions = New-MsolLicenseOptions -AccountSkuId "M365x115998:PROJECTPREMIUM" -DisabledPlans "PROJECT_PROFESSIONAL"`</br>
5. After you've created the object, pass a list of your user accounts in which you'd like to disable Project for the web.  There are different ways to do this, such as importing from a CSV file.</br>
`$UPNList = @("AdeleV@M365x115998.OnMicrosoft.com","AlexW@M365x115998.OnMicrosoft.com")`</br>
6. After creating your list, apply the $LicenseOption object to each user account. </br>
`ForEach ($UPN in $UPNList)
{
    Set-MsolUserLicense -UserPrincipalName $UPN -LicenseOptions $LicenseOptions    
}`
 
For more information about disabling services through Office 365 PowerShell, see [Disable access to services with Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/disable-access-to-services-with-office-365-powershell). 


## See Also
  
  



