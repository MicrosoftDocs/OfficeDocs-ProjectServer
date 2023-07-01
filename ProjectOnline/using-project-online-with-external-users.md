---
title: "Using Project Online with external users"
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 1/5/2018
audience: admin
ms.topic: article
ms.service: project-online
ms.collection: M365-subscription-management
ms.localizationpriority: medium
ms.custom:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top_Top
search.appverid: 
- PJO150
- MET150
ms.assetid: f305a365-3d81-48bc-a3d0-4260e7326899
description: "Learn how to use external users with Project Online."
---

# Using Project Online with external users

In Project Online, a Project Web App site is a site collection within SharePoint Online and sharing a Project Web App site with external users works the same as sharing any other SharePoint Online site. In this article, we cover the options for external sharing that are relevant to Project Web App in Project Online, along with licensing implications for giving your external users access to Project Web App features in Project Online. We also encourage you to read about how to [manage external sharing for your SharePoint Online environment](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85).
  
Once a Project Web App site has been shared with an external user, the user can collaborate through documents and lists in that site, including risks and issues. Any interaction on a Project Site requires a Project Online license.

You can create and manage resources with a **Project Plan 3 or Project Plan 5** license.
  
> [!NOTE]
> For more information about Project Online license considerations for external users, see the [Project Online Service Description](/office365/servicedescriptions/project-online-service-description/project-online-service-description). 
  
Managing licenses and permissions for external users is the same as for internal users. (To find the external users in your user list, look for users with **#EXT#** in the user name.) 
  
## Plan sharing Project Web App with external users

There are two options for sharing your Project Web App site in Project Online. You can pre-populate your Office 365 directory with the users with whom you want to share the site, or you can send sharing invitations to users directly from your Project Web App site.
  
 **Pre-populating your directory**
  
You can pre-populate your Office 365 directory with external users, such as by using [Azure Active Directory B2B collaboration](/azure/active-directory/external-identities/what-is-b2b) or by adding users manually and changing the user type to Guest. There are several advantages to doing this: 
  
- When you configure sharing for your Project Web App site, you can choose the **Allow sharing only with the external users that already exist in your organizations's directory** option. This gives you a greater level of control over sharing the site by limiting the scope of who can be invited to the site. 
    
- If you import a list of users into your directory all at once, you can automatically add them to security groups and use these security groups to control site permissions for the various Project Web App roles, such as project manager, team member, and so on.
    
- You can assign licenses to the imported users before sending them the link to the Project Web App site so they have the proper access when they log into Project Web App.
    
 **Adding users as you go**
  
If you choose not to pre-populate your directory, you can choose the **Allow external users who accept sharing invitations and sign in as authenticated users** option when you configure sharing for the site. 
  
The advantage of this method is that the site can be easily shared with anyone who has an Office 365 or Microsoft account. You can invite new users whenever you need to by clicking **Share** on the Project Web App site. Users who accept invitations are added to your Office 365 directory and you can manage them there. 
  
One thing to note in using this method is that invited users aren't added to your Office 365 directory until they accept the sharing invitation, and they must be in your directory before you can assign them a Project Online license. Because of this, they will not have full access to the Project Web App site when they first receive the invitation. They can still work with documents, issues, and risks, but won't be able to manage projects or work with time sheets until they have a Project Online license and have accepted the invitation.
  
 **Choosing a sharing method**
  
You can use either of the above sharing methods, or you can use a combination of the two. You can pre-populate your directory with an initial list of users, then invite more later. The important thing is to choose the sharing option that's best for you.
  
The **Allow sharing only with the external users that already exist in your organizations's directory** option is more restrictive and allows you greater control over who can be invited to the site. To use this option, you must pre-populate your directory with the users who you want to invite to the site. 
  
The **Allow external users who accept sharing invitations and sign Office 365in as authenticated users** option is the most versatile and allows you to send invitations to anyone with an or Microsoft account. You can still pre-populate users in your directory with this option, but it's not required. 
  
## Configure sharing for Project Web App

Use the following procedure to configure sharing for your Project Web App site in Project Online. Be sure that sharing is [enabled at the tenant level](https://support.office.com/article/C8A462EB-0723-4B0B-8D0A-70FEAFE4BE85) before you proceed. 
  
 **To configure sharing for Project Web App**
  
1. In the SharePoint Online admin center, in the **site collections** area, select the check box for the Project Web App site that you want to share. 
    
2. In the ribbon, click **Sharing**.
    
3. Select the option that you want to use for sharing:
    
  - **Allow sharing only with the external users that already exist in your organizations's directory** if you want to share only with users that you've imported from another directory or tenant. 
    
  - **Allow external users who accept sharing invitations and sign in as authenticated users** if you want to be able to send invitations to users with a Microsoft or Office 365 account. 
    
4. Click **Save**.
    
Once you've configured the sharing options for your Project Web App site and added users to your Office 365 directory if needed, you can invite external users to the site by using the **Share** button on the site in the same way that you would invite internal users. 
