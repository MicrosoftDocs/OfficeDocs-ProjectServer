---
title: "What should I do if my Project Online administrator gets locked out?"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 7/11/2017
audience: admin
ms.topic: troubleshooting
ms.service: project-online
localization_priority: Normal
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- PJO160
ms.assetid: 9ef4dd2a-a6f4-4fa5-ad41-acd586db2b1b
description: "Locked out? Don't panic. The site collection administrator for your Project Online site automatically has administrative permissions, and can get the Project Online administrator back in."
---

# What should I do if my Project Online administrator gets locked out?

Locked out? Don't panic. The site collection administrator for your Project Online site automatically has administrative permissions, and can get the Project Online administrator back in.
  
## Step 1: Try to figure out what happened

You might know exactly what happened to get the Project Online administrator account locked out. If so, you've tackled the first hurdle. If you're not sure, think through your last several actions in Project Online prior to the lockout.
  
While logged on as the Project Online administrator, you may have:
  
- **Removed everyone from the Administrators group** in Project Online, including the default administrator Active Directory group, and then saved changes. 
    
- **Set up Active Directory sync to control who has access** to Project Online, without being a member of the selected Active Directory group. 
    
- **Synchronized an Active Directory group in the Resource Center** while your account was already listed as a resource. When the synchronization occurred, your Project Online administrator account was made inactive as it was not part of the Active Directory group. 
    
These are just a few examples of things that may have happened. Your situation may be different, and your site collection administrator will have an easier time getting you back in if you can narrow down what may have caused the lockout.
  
## Step 2: Find your site collection administrator

Your organization may have a global (tenant) administrator for all of Office 365, a SharePoint Online administrator, a site collection administrator, and a Project Online administrator. One person may be filling all of those roles, or you may have multiple people filling each one. To figure out who your Project Online site collection administrator is, you'll need to try to identify someone in either the global administrator or SharePoint Online administrator roles. Then, that person can look into who is managing the specific site collection for Project Online.
  
 **If you're having trouble reaching your site collection administrator, or if that person isn't sure how to help you regain access to Project Online,** the global administrator or SharePoint Online administrator can also [Manage site collection administrators](https://support.office.com/article/9a7e46f9-3fc4-4297-955a-82cb292a5be0) for your Project Online site. As a site collection administrator, you will have all administrative permissions in Project Online, and you can try to resolve the lockout yourself. 
  
## Step 3: Help the site collection administrator get you back in

Once you've found the right person to help you, explain what you think happened that caused the lockout. Some issues that result in lockout can be resolved by adding the Project Online administrator account to an Active Directory group. When synchronization happens, you should regain access to Project Online.
  
If Active Directory changes will resolve the lockout, the site collection administrator won't need a Project Online license. However, in some cases, logging onto Project Online is required for fixing the issue, and the site collection administrator will need to be assigned a Project Online license. It's possible that he or she already has one. If not, have the site collection administrator select his or her account on the [Active Users page](https://go.microsoft.com/fwlink/?LinkId=529438) in the Office 365 admin center, and then choose **Edit** under **Assigned license** on the right side of the window to select a Project Online license. 
  
 **Don't have enough licenses?** If your organization already has all licenses assigned, the site collection administrator can remove the license from the locked-out Project Online administrator account, and then assign that license to themselves temporarily. You'll need to pass the license back and forth to test access, so be sure it gets assigned back to the Project Online administrator once access has been successfully restored. 
  

