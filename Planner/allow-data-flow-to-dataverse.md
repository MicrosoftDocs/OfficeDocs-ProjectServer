---
title: "Disable the conversion of basic plans by users into premium plans"
f1.keywords:
- NOCSH
ms.author: namerali
author: nadinmerali
manager: dellerderick
ms.date: 09/30/2024
audience: Admin
ms.topic: article
ms.service: office-perpetual-itpro
ms.subservice: planner
description: "This article shares information on how admins can disable the flow of data to Dataverse on basic plans"
---

# Disable the conversion of basic plans by users into premium plans 

## Overview
In the Planner app, there are basic plans and premium plans (formerly projects in Project for the web which are backed by Dataverse ).  Premium users can now add premium features (Timeline view, dependencies, subtasks etc.) to their plans by converting basic plans into premium plans that support those features.  The entire team can continue to work on the plan while premium users can utilize the premium features.

Please review the following for more relevant information:
   - Differences between basic and premium plans see [Comparing Basic vs Premium Plans](https://support.microsoft.com/office/comparing-basic-vs-premium-plans-5e351170-4ed5-43dc-bf30-d6762f5a6968)
   - [Converting basic plans into premium plans](plan-conversion.md)
   - How premium plans work and are stored see [Project architecture overview](/project-for-the-web/project-architecture-overview#project-for-the-web)


## Prerequisites for making Planner changes in Windows PowerShell

Follow the steps in [Prerequisites for making Planner changes in Windows PowerShell](prerequisites-for-powershell.md) to make Planner changes in Windows PowerShell.

## Changing the ability for end users to convert basic plans into premium plans

1. Open PowerShell and run the following command to disable the conversion of basic plans to premium plan by users (it's enabled by default):

   ```powershell
   Set-PlannerConfiguration -AllowDataFlowToDataverse  $false
   ```
  
   If you have changed your mind and would like to allow users to convert basic plans into premium plans, run the following command.

   ```powershell
   Set-PlannerConfiguration -AllowDataFlowToDataverse $true
   ```

   > [!NOTE]
   > You'll need to sign in using your Microsoft Entra credentials and use a local PowerShell window (not Azure Cloud Shell).

2. To verify your settings, in PowerShell, run: 
   
     ```powershell
     Get-PlannerConfiguration
     ```
     
   The AllowDataFlowToDataverse value returned by this command indicates whether users can convert basic plans.
