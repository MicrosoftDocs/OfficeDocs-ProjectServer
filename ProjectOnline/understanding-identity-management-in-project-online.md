---
title: "Understanding identity management in Project Online"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 5/29/2015
audience: admin
ms.topic: overview
ms.service: project-online
localization_priority: Normal
search.appverid: MET150
ms.custom: IT_ProjectAdmin
ms.assetid: ec6a2c12-b179-46ca-ac3b-2f06984e4f66
description: "Before you start using Project Online, one of the most important decisions that you have to make is how you want to manage your Project Online user accounts."
---

# Understanding identity management in Project Online

Before you start using Project Online, one of the most important decisions that you have to make is how you want to manage your Project Online user accounts.
  
## Options for user accounts in Project Online

Project Online uses the user accounts that you set up for Office 365.
  
There are two ways to set up user accounts in Office 365:
  
- You can add accounts for each user yourself or import users from a list, such as an Excel workbook.
    
- You can synchronize the accounts that you already have in Active Directory Domain Services (AD DS) with Office 365.
    
    While synchronizing your Active Directory accounts requires some additional configuration, the advantage of doing so is that users only have one username and one password that works with both your local network and Office 365. This makes account maintenance much easier and gives your users a more seamless and friendly experience.
    
    If you choose to synchronize your accounts with Active Directory, it's very important that you do that before you give your users access to Office 365 or Project Online. If you add accounts to Office 365 manually, and then later decide to synchronize your accounts with Active Directory, then you can end up with two accounts for each user in Office 365. In Project Online, where you're assigning resources to tasks and managing your projects, you'll end up with duplicate resources. You won't be able to delete the old accounts in favor of the new accounts, because the old accounts will be associated with project and time reporting data.
    
    **Here's an example:**
    
    You subscribe to Office 365 with Project Online and use your company name, Contoso, when you sign up. Your Office 365 domain is then contoso.onmicrosoft.com. You then add an account for Robyn Buckley, one of your users. Her account in Office 365 is robynb@contoso.onmicrosoft.com; while her Active Directory account on the Contoso network is robyn@contoso.com.
    
    If you later synchronize your Active Directory accounts to Office 365, both robynb@contoso.onmicrosoft.com and robyn@contoso.com will exist in Office 365. Robyn can log into either account, and each appears as a separate resource in Project Online.
    
    **Synchronize your users first**
    
    If you use Active Directory Domain Services as part of your company's network, we highly recommend synchronizing your Active Directory accounts with Office 365. This will be much easier to manage in the long run and will help reduce your help desk costs and improve user satisfaction.
    
    To learn how to synchronize your users, see [Office 365 integration with on-premises environments](https://support.office.com/article/263faf8d-aa21-428b-aed3-2021837a4b65).
    

