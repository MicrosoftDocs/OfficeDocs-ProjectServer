---
title: "Portfolio analysis in the Microsoft Project Web Application"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 9/24/2019
audience: admin
ms.topic: overview
ms.service: project-online
localization_priority: Normal
search.appverid: MET150
ms.custom: IT_ProjectAdmin
description: "Learn what a project portfolio analysis is and how to get started doing portfolio analyses in Project Web App."
---

# Portfolio analysis in the Microsoft Project Web Application

‎**Summary:** Learn what a project portfolio analysis is and how to get started doing portfolio analyses in Project Web App.

**Applies to:** Project Online, Project Server 2016, Project Server 2013

One of the most commonly asked questions in project management is, "Are we delivering the right projects?" The portfolio analysis module in PWA is designed to help organizations answer that question. The portfolio analysis module answers that question by performing the following functions:

- Centralizing a list of requested projects or proposals.

- Developing a list of the estimated costs required to deliver those projects.

- Developing a list of the estimated resources required to deliver those projects.

- Providing several methods to prioritize the list of requested projects or proposals.

- Providing the organization with the ability to explore the various dimensions of the project portfolio.

These features may be combined to create specific scenarios. For example, one scenario may assume annual funding levels of $20,000,000. Other scenarios may assume funding levels of $10,000,000. Some scenarios may prioritize growth. Other scenarios may prioritize risk mitigation.

The process of assessing these scenarios and defining an optimal selection of projects is known as portfolio analysis. Portfolio analysis is a core feature in the Project Web Application, and is available in Project Online and supported versions of Project Server.

![Sample portfolio analysis in the Project Web Application](media/01-image1.png)

## **The portfolio of projects and ideas**

The project portfolio is defined as a centralized list of projects and proposals. This portfolio is managed to deliver specific organizational goals. Within PWA, a project portfolio should be defined as a set of projects that share the same cost or resource constraints.

Cost and resource estimates may be attached to the project portfolio. These become the demand profile that is input into the portfolio analysis exercise.

![Sample table name of project names and priority percentages](media/01-image2.png)

## **The portfolio of resources**

Resources are collected into a portfolio of resources. Within PWA, this resource portfolio is referred to as the resource pool. The resource pool represents the available resources that can be called upon to deliver the portfolio of projects and ideas.

![Sample portfolio of resources](media/01-image3.png)

Members of the resource pool may be assigned specific values to support the portfolio analysis exercise. For example, resources may be assigned to specific departments, skill sets, languages, etc. These attributes generally map to the different portfolios of work defined in the project portfolio.

## **Project prioritization**

PWA provides two methods of prioritizing the project portfolio:

- Business drivers

- Enterprise custom fields

Business drivers are a definition of the goals of the organization. Each project or idea within the project portfolio may be assessed against each of the business drivers. This will yield a prioritization of each project. For more information on defining business drivers, please click [here](portfolio-analysis-business-drivers.md).

![Sample business drivers](media/01-image4.png)

Some organizations choose to use custom fields to perform prioritization. Custom fields support the use of existing prioritization processes. Custom fields may also be used to support the use of third party decision support tools. The output of those processes and tools may be entered in custom fields within PWA to support a prioritization logic aligned with the needs of the organization.

## **Portfolio analyses**

You may use PWA to combine portfolio data to create specific scenarios. These scenarios represent an analysis of the project portfolio, a portfolio analysis. The scenario will describe the optimal list of projects based on external constraints such as available funds, resources, and organizational priorities.

![Sample portfolio analysis in the Project Web Application](media/01-image1.png)

The scenario calculations do not impact the project record itself. These are hypothetical scenarios that exist outside of the main project management environment. When the scenario is committed, specific fields are populated and the project is moved into the execution stage.

In Project Web App, you can create multiple analyses for a given set of projects and compare them to each other to help determine the best value for the budget that you have available.

## **Preparing for portfolio analysis**

The following steps are best performed before starting a portfolio analysis.

1. Define your projects and project proposals.

2. Define the key cost elements of these projects (i.e., total cost, capital expense, operational expense, etc.).

3. (Optional) Define the work required to support these projects and project proposals.

4. (Optional) Define the available pool of resources that will be delivering the project portfolio.

5. Define your portfolio prioritization mechanism(s). PWA supports the use of business drivers as well as manual prioritization methods.

## **Getting started with portfolio analysis**

Here's what you need to do to get started with portfolio analysis in Project Web App:

1. [Create a new portfolio analysis within PWA](creating-a-portfolio-analysis.md).

2. [Prioritize your project portfolio](prioritizing-the-portfolio-with-custom-fields.md).

3. Review the output of the cost analysis. Identify specific scenarios to explore further. Save those scenarios for comparison.

4. (Optional) Review the forecast resource commitments.

5. (Optional) Review the output of the resource analysis. Identify specific scenarios to explore further. Save those scenarios for comparison.

6. [Select one portfolio analysis scenario for execution](comparing-portfolio-scenarios.md).

7. [Commit that portfolio analysis scenario to advance the projects in the execution workflow](committing-the-scenario.md).

## Related Articles
