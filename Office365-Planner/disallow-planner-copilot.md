---
# Required metadata
# For more information, see https://review.learn.microsoft.com/en-us/help/platform/learn-editor-add-metadata?branch=main
# For valid values of ms.service, ms.prod, and ms.topic, see https://review.learn.microsoft.com/en-us/help/platform/metadata-taxonomies?branch=main

title: Disallow Copilot in Planner for your organization
description: This document walks you through the process of disallowing the Copilot in Planner feature for your organization through our PowerShell suite
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

# Disallow Planner Copilot for your organization

## Overview

Because Planner has enabled a Copilot experience, we're adding the ability for tenant administrators to turn this feature off for their tenants.

Copilot in Planner provides an in-app natural language chat experience that will allow users to request updates to their Plan as well as summaries and insights from the Plan content.

Choosing to disallow this feature will hide this functionality from customers in the adjusted organization.

> [!NOTE]
> If the Copilot in Planner feature needs to be disabled for a tenant that has Planner Plan 1, Project Plan 3 or Project Plan 5 but doesn't have Planner (included with M365), please open a request with support to have it disabled for your organization.
> [!NOTE]
> The effect is not instantaneous. It takes up to an hour after running the command to change the setting.
## Prerequisites for making Planner changes in Windows PowerShell

Follow the steps in [Prerequisites for making Planner changes in Windows PowerShell](prerequisites-for-powershell.md) to make Planner changes in Windows PowerShell.

## Disable the Copilot in Planner feature

1. Open PowerShell and run the following command to disallow the Copilot in Planner feature:

         ```PowerShell
   Set-PlannerConfiguration -AllowPlannerCopilot $false
   ```
   
         Likewise, if you want to re-allow the feature, run the below command:

         ```PowerShell
   Set-PlannerConfiguration -AllowPlannerCopilot $true
   ```
   
      > [!NOTE]
   > You'll need to sign in using your Microsoft Entra credentials and use a local PowerShell window (not Azure Cloud Shell).

1. To verify your settings, run:

         ```PowerShell
   Get-PlannerConfiguration
   ```

   The AllowPlannerCopilot value returned by this command indicates whether the Copilot in Planner experience is allowed to be enabled for your organization.
   
