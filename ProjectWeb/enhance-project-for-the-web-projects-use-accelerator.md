---
title: Enhance your projects with the Project for the web Accelerator
description: The Project for the web Accelerator is a managed solution your admin can deploy to your Project environment. It adds five scenarios - Project Requests, Programs, Risks and Issues, Changes, and Status. Read this topic to learn how to use them.
author: v-stthomas
ms.author: v-stthomas
manager: alexla
ms.service: Project
ms.topic: how-to 
ms.date: 04/01/2022
ms.custom: template-how-to 
audience: end user
---

# Enhance your projects with the Project for the web Accelerator

Project for the web is convenient and easy-to-use. Because it's based on the Microsoft Power Platform, it's easy to customize using solutions. We've created a solution that adds five project management scenarios&mdash;the Project for the web Accelerator. This article shows you how to use it to enhance your projects in Project for the web.

## Prerequisites

- Your environment must have the Project for the web Accelerator solution deployed and enabled by your admin.
- You'll need to belong to a group that has the security roles required for creating or editing projects in Project for the web.

## Scenarios added by the Accelerator

💡 **Project Requests**. Create a list for project ideas that include a business case and expected impact. The included Power Automate flow creates a project when a request is set to *Approved*.

💼 **Programs**. Create a hierarchy of programs and projects see how work fits into the bigger picture.

🔥 **Risks and Issues**. Manage the surprises that accompany every project. Create and assign risks and issues to minimize impacts to a project's schedule.

🚧 **Changes**. Use change tracking processes to manage changes and help understand the history of a project.

📝 **Status**. Centralize recording of project status to keep stakeholders up-to-date.

## Scenario: Project Requests

The Accelerator includes a *Project Request* table that your teams can use to propose projects, and a Power Automate cloud flow to create a project when a proposal is approved.

> [!NOTE]
> Your admin must turn the cloud flow on so the approval of a request will create a new project. However, you can still add project ideas to the Project Request table. When the cloud flow is turned on, your ideas can be approved and become projects.
>
> :::image type="content" source="media/p4w-accelerator-flow-is-on.png" alt-text="Check the command bar to see whether the flow is turned on":::

### Propose a project

1. In the navigation pane, select **Project Request**.
1. On the command bar, select **New**.

   :::image type="content" source="media/p4w-accelerator-new-project-request.png" alt-text="Add a new Project Request":::

1. The proposal's *Request State* is *New*.

  :::image type="content" source="media/new-state.png" alt-text="A newly proposed Project Request":::

1. Enter a value for **Name**, then provide as much additional information about the request as you can. The person who can approve proposals will use it to decide whether to approve this one.
1. After you finish adding more data, on the command bar select **Save and Close**.

  :::image type="content" source="media/p4w-accelerator-new-project-request_form.png" alt-text="Project Request with plenty of decision-support data":::

### Approve a project request

1. In the navigation pane, select **Project Request**.
1. Select the request, then select the arrow on the right edge of its record to open the form.

   :::image type="content" source="media/p4w-accelerator-open-request.png" alt-text="Select a new request and open it":::

1. Set **Request State** to *Approved* and save the record.

  :::image type="content" source="media/p4w-accelerator-approve-request.png" alt-text="Approve a Project Request to turn it into a Project":::

1. In a few moments, the project appears as a new record in *Project*.

  :::image type="content" source="media/p4w-accelerator-approved-project.png" alt-text="The cloud flow creates a new Project from the approved Project Request":::

## Scenario: Programs

The Accelerator adds a Program table that enables summary tracking of related projects. This creates a hierarchy so your organization can review ongoing work without opening each project to review the details.

:::image type="content" source="media/p4w-accelerator-programs.png" alt-text="The Active Programs view lists key fields for listed programs. 1, Set the checkmark at the left edge of the row to choose a program. 2, Select the arrow at the right edge to open the program. 3, Or, choose an action on the command bar to apply the action to the selected program.":::

1. Set the checkmark to select a program.
1. Select the arrow to open the selected program.
1. Or, use the command bar to choose an action for the selected program.

> [!NOTE]
> After you create a project, you need to activate it before it will start monitoring the projects it includes.
>
> :::image type="content" source="media/p4w-accelerator-activate-program.png" alt-text="Select Activate on the command bar.":::

### Create a program

#### Add stakeholders (project managers, program owners)

#### Add projects to a program

### Refresh program data

### Reporting

## Scenario: Risks and Issues

For this scenario, the Accelerator adds two tables:

- *Risk* lets you track risks associated with completing a project.
- *Issue* lets you track issues that hinder the completion of a project.

The Accelerator also creates relationships between these tables and the *Project* table, so that each becomes a lookup column. It adds them to the Information form as tabs where you can add and edit risks and issues for the open project.

### Add or edit a risk or issue

1. Open the relevant project.
1. Select the relevant tab:

   - To flag an issue that is or could be blocking the project's progress, select **Issues**.
   - To flag a risk that could result from the completion of a project, select **Risks**.

1. A list of related risks or issues appears on the tab.

    On the list's command bar, you can do any of the following actions. If the command isn't displayed, select the vertical dots on the right edge of the command bar to see a menu:
    - To create a new item, select **+ New Risk** or **+ New Issue**.
    - To add an item that already exists (a common risk or issue), select **Add Existing Risk** or **Add Existing Issue**.
    - You can select an existing risk or issue to open the record, but you can only edit the record if it's *State* is  *Active*. To select an item, select the left edge of its row in the list. The **Edit** command will appear on the command bar.

   :::image type="content" source="media/p4w-accelerator-edit-risk.png" alt-text="Select a list item and then select Edit on the command bar.":::

1. Add details to the risk or issue. When you are done, on the command bar select **Save** or **Save and Close**.

## Scenario: Changes

The Accelerator adds a *Change* table, and creates a relationship between it and the *Project* table. It also adds a **Changes** tab to the *Project* table's Information form.

## Scenario: Status

The Accelerator adds a *Status* table, and creates a relationship between it and the *Project* table. It also adds a **Status** tab to the *Project* table's Information form.

## Next steps

- Get the big picture from the *Home* dashboard
- Analyze your projects in Power BI
