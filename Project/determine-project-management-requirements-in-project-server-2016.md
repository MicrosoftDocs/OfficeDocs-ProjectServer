---
title: "Determine project management requirements in Project Server 2016"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 11/29/2017
audience: ITPro
ms.topic: concetpual
ms.prod: project-server-itpro
localization_priority: Normal
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: bbfa709c-11c3-435e-8b2e-f6ae332e3b09
description: "Summary: Learn about Project Server feature usage for Enterprise Project Management, timesheet, and demand management scenarios."
---

# Determine project management requirements in Project Server
 
 **Summary:** Learn about Project Server feature usage for Enterprise Project Management, timesheet, and demand management scenarios.<br/>
**Applies to:** Project Server 2016, Project Server 2013
  
It is important to determine the project management needs and requirements for your organization. Your configuration will vary according to the kind of work that your organization performs and whether you use Project Server for time tracking, collaboration, or portfolio management. After you characterize the typical projects for your organization, determine which Project Server scenarios that you have to support.
  
## Characterize your projects
<a name="section1"> </a>

Understanding the characteristics of the projects in your organization enables you to plan your Project Server configuration. The following characteristics have a significant effect on your configuration:
  
- The number of projects that your organization is working on at a particular time
    
- The size of your projects, which varies with the number of tasks and assignments that your projects include
    
- The length of time that is required to complete a project
    
- The number of team members that are assigned tasks in projects
    
Most organizations manage projects that vary in size and duration, but the degree to which they vary is a function of the size of the organization and the kind of work that it performs. For example, a large consulting company might manage several thousand projects that range from small, 10-task projects that last two weeks to large projects that include 1,500 tasks and last for over a year. 
  
Organizations typically have many projects that range in size from small to medium to large. For planning, make sure that you can adequately support the kind of project that your organization works on most frequently.
  
## Determine your Project Server scenario
<a name="section2"> </a>

Your project management needs and requirements vary according to the kind of work that your organization performs. As part of your configuration planning process, determine which scenario that you need to support. For example, you can use Project Server to support the following kinds of scenarios:
  
- Enterprise Project Management 
    
- Time tracking
    
- Demand management
    
### Using Project Server for Enterprise Project Management

The Project Server scenario for EPM applies to a large organization whose area of focus is top-down planning driven through the Project Management Office (PMO). This scenario is more frequently seen in the product development and manufacturing markets. It has the following characteristics:
  
- A small number of large projects that are often related 
    
- Focus on the PMO 
    
- Extensive use of Project Professional 2016
    
- Work Tracker usage 
    
Critical considerations for this kind of deployment include the following:
  
- The level of detail to track
    
- Using leveling as a process
    
- How to prioritize capacity
    
- How to use skill tracking
    
In this scenario, client usage is as follows:
  
|**Client application**|**Rate of usage**|
|:-----|:-----|
|Project Professional  <br/> |High  <br/> |
|Project Web App  <br/> |High  <br/> |
   
In this scenario, server usage is as follows:
  
|**Project Web App feature**|**Rate of usage**|
|:-----|:-----|
|Work Tracker  <br/> |High  <br/> |
|Programs  <br/> |High  <br/> |
|Timesheets  <br/> |Medium  <br/> |
|Portfolio management  <br/> |Medium  <br/> |
|Master projects  <br/> |High  <br/> |
|Project workspaces  <br/> |Low  <br/> |
|Risk management  <br/> |Medium  <br/> |
|Issues management  <br/> |High  <br/> |
|Document management  <br/> |Medium  <br/> |
|Resource management  <br/> |Medium  <br/> |
|Task management  <br/> |Medium  <br/> |
   
### Using Project Server for time tracking

The Project Server scenario for professional services/timesheet deployment can apply to a large organization that wants to use Project Server mainly to capture and report time. In this scenario, employees and contractors use Project Server timesheet functionality to submit hours worked on tasks during specific time periods. This scenario has the following characteristics:
  
- Minimal use of Project Professional
    
- Time and material billing
    
- A large number of projects that have fairly few tasks 
    
- A predictable peak period of usage that corresponds to scheduled timesheet entry in Project Web App
    
Organizations that support this scenario typically use a limited set of Project Professional features to track time and costs by using timesheets to capture information. This scenario presents scalability issues, because, when many timesheets are submitted in a short period of time, system resources can become severely strained.
  
Critical considerations for this kind of deployment include the following:
  
- What time classifications to use
    
- What time periods to use
    
- Calendars and overtime setup
    
- What fiscal periods to use
    
- Source of cost data
    
- Custom field configuration — process control custom fields vs. reporting custom fields
    
- Currency configuration
    
- Auditing
    
There are additional factors that can be affected by the processes that are used within your organization, including the following:
  
- Types of usage
    
- What the project update cycle is
    
- What the reporting cycle is
    
In this scenario, client usage is as follows:
  
|**Client application**|**Rate of usage**|
|:-----|:-----|
|Project Professional  <br/> |Medium  <br/> |
|Project Web App  <br/> |High  <br/> |
   
In this scenario, server usage is as follows:
  
|**Project Web App feature**|**Rate of usage**|
|:-----|:-----|
|Work Tracker  <br/> |High  <br/> |
|Programs  <br/> |Low  <br/> |
|Timesheets  <br/> |High  <br/> |
|Portfolio management  <br/> |Low  <br/> |
|Master projects  <br/> |Low  <br/> |
|Project workspaces  <br/> |Low  <br/> |
|Risk management  <br/> |Low  <br/> |
|Issues management  <br/> |Low  <br/> |
|Document management  <br/> |Low  <br/> |
|Resource management  <br/> |High  <br/> |
|Task management  <br/> |Medium  <br/> |
   
### Using Project Server for Demand Management

The Project Server scenario for Demand Management deployment can apply to any medium-to-large organization that wants to use Project Server to manage project portfolios. These organizations typically have the following characteristics:
  
- A large number of projects that have many assignments 
    
- A high percentage of project managers 
    
- Frequent use of Project Professional
    
Organizations that support this scenario typically use the breadth of Project Server features that include timesheets, document libraries, issues, risks, the Enterprise Global Template, and the Enterprise Resource Pool.
  
The organization to which this scenario can apply can be as small as a medium-size organization (or a department in a larger organization) whose users all share the same physical location on the same LAN, or it can be a large organization whose users work in several different physical locations. 
  
These organizations use Project Professional and Project Web App daily to publish or update projects to Project Server, and they use Project Web App to view assignments; report actuals; and access documents, issues, and risks. Additionally, these organizations generate online analytical processing (OLAP) cubes weekly.
  
Critical considerations for this kind of deployment include the following:
  
- Level of resource data to track
    
- What project nomination process to use
    
- What kind of review process to use
    
- What the report cycle will be
    
- Workflow requirements
    
- What kind of work to track
    
- Who manages the process
    
- What demand is captured
    
In this scenario, client usage is as follows:
  
|**Client application**|**Rate of usage**|
|:-----|:-----|
|Project Professional  <br/> |Medium  <br/> |
|Project Web App  <br/> |High  <br/> |
   
In this scenario, server usage is as follows:
  
|**Project Web App feature**|**Rate of usage**|
|:-----|:-----|
|Work Tracker  <br/> |Low  <br/> |
|Timesheets  <br/> |Medium  <br/> |
|Portfolio management  <br/> |High  <br/> |
|Programs  <br/> |Low  <br/> |
|Administrative projects  <br/> |Low  <br/> |
|Collaboration  <br/> |Medium  <br/> |
|Document management  <br/> |Medium  <br/> |
|Risk management  <br/> |Medium  <br/> |
|Issues management  <br/> |Medium  <br/> |
|Resource management  <br/> |Medium  <br/> |
|Project workspace sites  <br/> |Medium  <br/> |
   

