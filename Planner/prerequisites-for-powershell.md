---
title: "Prerequisites for making Planner changes in Windows PowerShell"
f1.keywords:
- NOCSH
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 06/12/2024
audience: Admin
ms.topic: overview
ms.service: office-perpetual-itpro
ms.subservice: planner
ms.localizationpriority: high
search.appverid:
- MET150
description: "This procedure walks you through downloading the files needed to run Planner admin commands in PowerShell"
---

# Prerequisites for making Planner changes in Windows PowerShell

This procedure walks you through downloading the files needed to run Planner admin commands in PowerShell.

If you're new to Windows PowerShell, see [Getting started with Windows PowerShell](/powershell/scripting/learn/ps101/01-getting-started).

## Pr Planner Tenant Admin PowerShell Dependencies

1. Verify Installation: Check if the MSAL.PS module is installed by running the following command in PowerShell:
   ```PowerShell
   Get-Module -ListAvailable MSAL.PS
   ```
2. Install the Module: If the module is not installed, install it using:
   ```PowerShell
   Install-Module -Name MSAL.PS -Scope CurrentUser 
   ```
## Download Planner Tenant Admin PowerShell Commands

> [!NOTE]
> You must be a global admin to run the Planner Tenant Admin Powershell Commands.

> [!NOTE]
> By downloading this package, you agree to the enclosed license and terms.

Download the [Planner Tenant Admin PowerShell file](https://download.microsoft.com/download/d/3/e/d3e7ade9-56c3-4f7b-b3e2-03ffdab2c964/tenant-admin-scripts.zip). Unzip it to a location you can access from PowerShell.
## Unblock your files

You'll need to "unblock" one of the files you downloaded in the Planner Tenant Admin PowerShell package in order to use them in PowerShell. This is because by default, executing scripts downloaded from the Internet isn't allowed. The file you need to unblock is *plannertenantadmin.psm1*.

Do the following to unblock *plannertenantadmin.psm1*:

1. In File Explorer, go to the location in which you unzipped your files.
1. Right-click on *plannertenantadmin.psm1* and select **Properties**.
1. On the General tab, select **Unblock**.

    ![unblock-files.](media/unblock-files.png) 
   
1. Select **OK**.

## Load the Planner Tenant Admin PowerShell module

After unblocking your *plannertenantadmin.psm1*, do the following to load the Planner Tenant Admin PowerShell module:

1. Start Windows PowerShell. In PowerShell, type the following to enable running scripts downloaded from the internet for this session only. It might prompt you to confirm by typing "Y."

   ```PowerShell
   Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Scope Process
   ```

2. Type the following to run the PlannerTenantAdmin PowerShell script. This will import a module with all available cmdlets.

   ```PowerShell
   Import-module "<location of the plannertenantadmin.psm1 file you unzipped>"
   ```

   For example, if your file is stored in C:\AdminScript, you would type:

   ```PowerShell
   Import-module "C:\AdminScript\PlannerTenantAdmin.psm1"
   ```
   
Now you're ready to make changes to Planner at the organizational level using PowerShell.
