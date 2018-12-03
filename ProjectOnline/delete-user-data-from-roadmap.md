---
title: "Delete user data from Roadmap"
ms.author: efrene
author: efrene
manager: pamgreen
audience: admin
ms.topic: article
ms.service: project-online
localization_priority: Normal
ms.custom: Adm_Project
search.appverid: PJO150
description: "Learn how an Office 365 global administrator can delete a user's information from Roadmap."
---

# Delete user data from Roadmap

To delete user data from Roadmap, you need the user's Azure AD Object ID. You can get this by checking the user's profile properties in Azure AD or by using [Get-AzureADUser](https://docs.microsoft.com/powershell/module/azuread/get-azureaduser).

To find a user's roadmaps

1. In the [Microsoft 365 amin center](https://admin.microsoft.com), under **Admin centers**, click Dynamics 365.
2. In the Dynamics 365 Administraton Center, select the default instance, and then click **Open**.
3. Click Advanced Find.
4. From the **Look for** menu, choose **Roadmaps**.
5. Click **Edit Columns**
6. Click **Add Columns**.
7. Choose the columns below that you want to search on. Be sure to include **Office 365 Group AAD ID**.

   |**Display name**|**Description**|
   |:---------------|:--------------|
   |Name|Name of the roadmap.|
   |Order Hint|Ordering of the roadmap rows within a roadmap.|
   |Owner AAD ID|ID of the user in AAD who owns the roadmap.|
   |Parent Roadmap|ID of the parent roadmap.|
   |Creator AAD ID|ID of the user in AAD who created the roadmap.|
   |Office 365 Group AAD ID|ID of the roadmap's Office 365 group in AAD.|
   |Roadmap|Unique identifier of a roadmap.|
   |Roadmap Type|The type of roadmap record.|

8. Click **OK**, and then click **OK** again.
9. In the **Fields** list, choose **Owner AAD Id** and type in the user's Azure AD Object ID.
10. Click **Results**.

Make note of the Office 365 Group AAD ID for any roadmap that you want to make changes to. You must join this group as an owner in order to make updates to the roadmap.

To add yourself as a group owner, use [Add-AzureADGroupOwner](https://docs.microsoft.com/powershell/module/azuread/add-azureadgroupowner):

`Add-AzureADGroupOwner -ObjectId <GroupID> -RefObjectId <YourAADObjectID>`

For example,

`Add-AzureADGroupOwner -ObjectId "62438306-7c37-4638-a72d-0ee8d9217680" -RefObjectId "0a1068c0-dbb6-4537-9db3-b48f3e31dd76"`

Once you are an owner for the groups, you can open the roadmaps from Project Home and make edits or deletions directly. ([Roadmap must be enabled](turn-roadmap-on-or-off.md) to do this.)

## See Also

[Create, edit, or save an Advanced Find search](https://docs.microsoft.com/dynamics365/customer-engagement/basics/save-advanced-find-search)

[Delete user data from Project Online](delete-user-data-from-project-online.md)
  
  

