---
title: "Project Service Core solution version history"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 12/9/2019
audience: admin
ms.topic: article
ms.service: project-web
ms.localizationpriority: medium
search.appverid:
- PJO150
- PJO160
- MET150
description: "See version history and release notes for the Project Service Core solution."
---

# Project Service Core solution version history
  
## Introduction

This article lists all of the updates that have been made to Project Service Core solution in Microsoft Dynamics 365 to date, along with other information pertinent to those updates. This solution is used by the Project for the Web application that is available in Microsoft Project.

## Upgrade Information

If you want to upgrade your solution within Dynamics 365 when a newer version is available, please see [KB #3192042](https://support.microsoft.com/help/3192042/how-to-upgrade-the-solutions-for-a-microsoft-dynamics-crm-portals-depl).

## Version history
  
|**Version**|**Release date**|**Update description**|
|:-----|:-----|:-----|
|1.0.61.61| March 17, 2023 | Features included in this release:|
|  |  | **Schedule API Operation Set Details Limit Increase:** The Operation set detail limit has been increased from 100 to 200. For more information, see: https://learn.microsoft.com/en-us/dynamics365/project-operations/project-management/schedule-api-preview|
|  |  | **Work Breakdown Structure Save Performance Improvements:** For larger or more complex work breakdown structures, we have provided significant performance gains in save execution to Dataverse. |
|  |  | Items resolved in this version |
|  |  | - Bug: When the work hour template does not have a calendar assigned, a meaningful error is displayed. |
|1.0.7.94 | February 2, 2021 | Items resolved in this version:|
|  |  | - Bug: Copy Project intermittently fails |
|  |  | - Bug: Block installation on orgs of type (Teams) |
|  |  | Additional performance improvements and bug fixes |
|1.0.6.154 | January 12, 2021 |Items resolved in this version: |
|  |  | - Bug: Breaking change by renaming web resource |
|  |  | - Bug: Update web resources in base solution |
|  |  | - Bug: Named orgs need default PostImport configuration parameters |
|  |  | - Bug: Rename Common Data Service User to Project Common |
|  |  | - Bug: Named orgs toolbar updates |
|  |  | - Feature: Add customizable entities to app module |
|  |  | Additional improvements in performance and bug fixes |
|1.0.4.71  | November 7, 2020 | Items resolved in this version: |
|  |  | - Bug: Manual deployment fails with post-import error|
|  |  | - Bug: User timezone related notification is not localized |
|  |  | - Bug: Updated localization translation|
|  |  | - Bug: Missing validation on Project Start Date|
|  |  | - Feature: Added support for Project Operations|
|  |  | Additional improvements in performance and bug fixes |
|1.0.1.605 | April 3, 2020  |Improvements in installation of the solution to address instances where the default team has been modified. Additional bug fixes and performance improvements |
|1.0.1.427 | January 2020  |Several bug fixes and performance improvements  |
|1.0.1.211 | November 2019  |Several bug fixes and performance improvements  |
