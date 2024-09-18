---
# Required metadata
# For more information, see https://review.learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata?branch=main
# For valid values of ms.service, ms.prod, and ms.topic, see https://review.learn.microsoft.com/en-us/help/platform/metadata-taxonomies?branch=main

title: Turn off Copilot in Planner for your organization
description: This document walks you through the process of turning off the Copilot in Planner feature for your organization through our PowerShell suite
author: jenzamora
ms.author: jenz
ms.service: office-perpetual-itpro
ms.topic: how-to
ms.date:     07/25/2024
ms.subservice: planner
manager: jtremper
ms.localizationpriority: high
ms.reviewer: jevaudri
---

# Turn off Microsoft 365 Copilot in Planner for your organization

## Overview

Microsoft 365 Copilot in Planner offers an in-app natural language chat experience, allowing your users to request updates to their Plans and receive summaries and insights from the Plan content. As an admin, you can turn Microsoft 365 Copilot in Planner on or off. When you turn off Microsoft 365 Copilot in Planner, the functionality is hidden from your users.

> [!NOTE]
> If Microsoft 365 Copilot in Planner needs to be turned off for a tenant that has Planner Plan 1, Project Plan 3 or Project Plan 5 but doesn't have Planner (included with M365), open a request with support to have it turned off for your organization. 
## Prerequisites

Follow the steps in [Prerequisites for making Planner changes in Windows PowerShell](prerequisites-for-powershell.md) to make Planner changes in Windows PowerShell.


## Turn off Microsoft 365 Copilot in Planner

> [!NOTE]
> It might take up to an hour to reflect the policy changes.

1. Sign in to PowerShell using your Microsoft Entra credentials and use a local PowerShell window (not Azure Cloud Shell).

1. Open PowerShell and run the following command to turn off Microsoft 365 Copilot in Planner:

   ```PowerShell 
   Set-PlannerConfiguration -AllowPlannerCopilot $false
   ```
   
   To turn on Microsoft 365 Copilot in Planner, run the following command:
   
   ```PowerShell
   Set-PlannerConfiguration -AllowPlannerCopilot $true
   ```
   
1. To verify your settings, run the following command:

      ```PowerShell
   Get-PlannerConfiguration
   ```

The value for **`-AllowPlannerCopilot`**  returned by the 'Get-PlannerConfiguration' command indicates whether Microsoft 365 Copilot in Planner can be turned on for your organization.
