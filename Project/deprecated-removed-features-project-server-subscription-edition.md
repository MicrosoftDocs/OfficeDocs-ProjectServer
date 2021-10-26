---
title: "What's deprecated or removed in Project Server Subscription Edition"
ms.author: v-benzyd
author: benzicald
manager: serdars
ms.date: 6/24/2021
audience: ITPro
ms.topic: overview
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 04fee973-5623-4768-a3ba-c109e45dd7eb
description: "Learn what has been deprecated or removed in Project Server Subscription Edition."
---

# What's deprecated or removed from Project Server Subscription Edition

**Summary**: Learn what has been deprecated or removed in Project Server Subscription Edition. <br/>
**Applies to**: Project Server Subscription Edition

## Features removed in Project Server Subscription Edition

### Project OData Service

The Project OData Service for reporting has been removed in Project Server Subscription Edition.

The alternative is to access database (only reporting schema - pjrep) through SQL Server Database Snapshots/SQL Server Integration Services. Accessing anything outside the reporting schema might lead to product out of support.

The OData service remains available in Project Server 2019, 2016, and 2013.
