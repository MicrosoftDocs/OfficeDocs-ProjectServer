---
title: "Enable your organization’s Planner tenant to be moved"
f1.keywords:
- NOCSH
ms.author: ryany
author: efrene
manager: pamgreen
ms.date: 08/25/2020
audience: Admin
ms.topic: Overview
layout: LandingPage
ms.service: o365-administration
ms.localizationpriority: high
search.appverid:
- MET150
description: "If you're a tenant admin who has made a support request for your organization’s Planner tenancy to be moved, first authorize using PowerShell"
---

# Enable your organization’s Planner tenant to be moved

> [!IMPORTANT]
>
> This article applies to:
>
> - Basic plans in the Planner app in Teams
> - All plans in other Planner endpoints (including Planner web, Planner mobile, and Planner connectors)
>
> It does not apply to To Do lists and premium plans in the Planner app in Teams. Learn more about the Planner app in Teams here: [Manage the Planner app for your organization in Microsoft Teams](/microsoftteams/manage-tasks-app)

If you're a tenant admin who has made a support request for your organization’s Planner tenancy to be moved into a new region, you must first authorize the move using PowerShell. 

- [Prerequisites for making Planner changes in Windows PowerShell](#prerequisites-for-making-planner-changes-in-windows-powershell)
- [Authorize a Planner tenant move using PowerShell](#authorize-a-tenant-move-using-powershell)

> [!NOTE]
> Moving a Planner tenancy into a new region will result in the loss of any existing Planner data.

## Prerequisites for making Planner changes in Windows PowerShell

Follow the steps in [Prerequisites for making Planner changes in Windows PowerShell](prerequisites-for-powershell.md) to make Planner changes in Windows PowerShell.

## Authorize a tenant move using PowerShell

1. Open PowerShell and run the following command to authorize your tenant to be moved:

   ```PowerShell
   Set-PlannerConfiguration -AllowTenantMoveWithDataLoss $true
   ```

   If you’ve changed your mind and would like to prevent your tenant from being moved, run the following command. Note that tenant moves are final once started by the Planner team.

   ```PowerShell
   Set-PlannerConfiguration -AllowTenantMoveWithDataLoss $false
   ```

   > [!NOTE]
   > You'll need to sign in using your Microsoft Entra credentials and use a local PowerShell window (not Azure Cloud Shell).

2. To verify your settings, run:

   ```PowerShell
   Get-PlannerConfiguration
   ```

   - The AllowTenantMoveWithDataLoss value returned by this command indicates whether a tenant move is currently authorized.
