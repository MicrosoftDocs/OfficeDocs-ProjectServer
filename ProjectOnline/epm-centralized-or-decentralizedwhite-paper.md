---
title: "EPM Centralized or decentralized? white paper"
ms.author: serdars
author: serdars
manager: pamgreen
ms.date: 12/30/2016
audience: admin
ms.topic: overview
ms.service: project-online
localization_priority: Normal
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- PJU150
- PJO160
- PJU160
- MET150
ms.assetid: 5dd958b1-2b38-4482-899f-96cd0ee5f474
description: "This article is part of our From the Trenches collection. It describes how organizations need to understand the problems they are trying to solve when deciding on implementing a project management system. Sometimes deploying a centralized project management system may not be the best answer."
---

# EPM: Centralized or decentralized?

This article is part of our "From the Trenches" collection. It describes how organizations need to understand the problems they are trying to solve when deciding on implementing a project management system. Sometimes deploying a centralized project management system may not be the best answer. 
  
To download the Word version of this article, see [EPM-Centralized or Decentralized?](https://go.microsoft.com/fwlink/?LinkId=207890).
  
To see more articles, see ["From the Trenches" white papers](https://support.office.com/article/faec6b1a-c217-4c79-b8c4-0514f402106b).
  
## EPM - Centralized or Decentralized?

I've been a proponent of Enterprise Project Management since I first entered the project management industry in the early 1980s. You'd think, then, that I would always vote on the side of centralized project management, but that isn't always the case. Let's discuss for a moment just what we mean by Enterprise Project Management. 
  
EPM can mean a lot of different things to different people. I've already discussed in other articles in this column how the focus of an EPM deployment might be document management for one organization and integrated schedules for the next. Enterprise Project Management has at its core, however, the notion that people must interact with each other in the project management exercise. That means that the project manager and/or project management team don't work completely independently. But does that mean that the only way to achieve this "interaction" is to have a centralized project scheduling system? Not necessarily. For some organizations, the project management challenge might be an inability to produce summary, enterprise-wide project management reports due to projects being all managed on an ad-hoc basis. In this case, EPM might be achieved just by having project standards that are shared between all project management personnel. That might best be achieved with a central pool of templates, training materials, documents, and report standards that everyone can use. Perhaps a simple SharePoint site would suffice.
  
For some organizations, the project management challenge might be ineffective personal schedules due to a lack of communication between resources about what they're working on and what their next focus is. In this case, EPM might be achieved by improving team and inter-team communication. The tools could be as simple as a shared calendar, Instant Messaging, or a shared portal where people could list what their priorities are.
  
In some organizations, the project management challenge is just getting progress on the programming development projects. If that's the case, then the tools already present in a product like Visual Studio Team Services might suffice. It's quite common in programming projects to find that many tasks can be completed in almost any order, so the rigors of Critical Path Scheduling might not even be appropriate depending on the type of development being done.
  
 I can remember a number of years ago working with the maintenance department of an airline. The staff were allowed to choose their own schedules at the start of each month and if this wasn't coordinated (as was often the case), it was possible to arrive to manage a shift only to find out that no one was working. Their project management challenge wasn't "When will the work get complete?" it was "is anyone coming to work?" In this case, EPM was achieved by implementing a shift scheduling tool. 
  
Even when we focus the EPM challenge to project schedules, it's not immediately obvious that deploying a centralized project management system is the only or the best answer. It's worthwhile to ask what interaction the project management personnel need to have with each other. If they must collaborate on a regular basis to resolve resource conflicts, to see what other priorities in the organization are coming up, or to see how the progress of one project will affect another, then looking at a tool like Project Server makes perfect sense, but often I end up interacting with organizations that have not even asked this question of themselves. 
  
In some organizations we find a tiny number of schedulers and a large number of resources. Even in a good-sized organization, this can be the structure depending on the industry and type of projects being accomplished. Not that long ago I met with an organization that was sure they had picked the right solution for their EPM challenge. They asked to me to articulate the solution but, as usual, I asked that they first articulate their project management problem. 
  
By the time they were done describing their environment on a white board it was apparent even to them that the solution they'd chosen wasn't going to solve their problem. 
  
In this case, the problem was a lack of project progress that was being reported by a large pool of subcontractors. The client determined that what they'd really need to do would be to impose a time and billing type of timesheet on their subcontractors. The Program Director was discouraged. "We'll never be able to get that into the subcontractor contracts," they said. Fortunately, a member of the Finance Department was present. "You know," that person replied, "a clause that requires them to fill in the timesheet of our choice is already in the subcontractor contract." Problem solved.
  
The idea of walking through the problem before coming to the solution is one I talk about often around here but it's a tough one to adopt. Logical thinking would dictate that the order of determining an automated solution would be:
  
1. Identify the problem
    
2. Define the solution
    
3. Determine whether to (and, if so, how to) automate the solution
    
Automated solution demonstrations on web sites, videos, and elsewhere make us forget that. We don't look for a solution, of course, unless we have some kind of problem, but the automated solutions look and sound so compelling that we end up doing this:
  
1. Choose the automated solution
    
2. Make the problem deploying the solution
    
3. Solve that problem by defining how the automated tool can be applied to the solution
    
4. Try to remember what the original problem was
    
The new problem becomes deploying the solution for quite some time and then weeks, months, or even a couple of years down the road someone from upper management asks when the original problem will be solved and everyone looks at each other rather surprised. It was easy to forget about. 
  
Over the years I've recommended all kinds of possible automated solutions. Oh, Project Server has been one of the options of course, but I've also recommended a combination of Microsoft Project Pro and SharePoint Server. I've recommended using a combination of Excel and Outlook. I've recommended using third party timesheets with Project. 
  
I even once recommended using a big white board. Honest. The organization was one I'd done business with for years. The person in question was in a real-estate role and had to renew long term leases in real estate. When I asked what the problem was, it was clearly a scheduling issue. The person had missed a few deadlines that were important and was sure that an enterprise project management tool would fix the problem. The organization had already asked for reports to be distributed to several executives so that future deadlines wouldn't be missed. "How many users would there be?" I asked. "Just me," he replied. "How many of these projects are there at a time?" I asked "Seven or eight," he replied. "And how many of these deadline milestones do you manage for each project "It's very complicated. There are about a half-dozen deadlines for each one," he told me.
  
It was already clear to me that we shouldn't be installing a big centralized EPM system for this poor fellow. 
  
"Why not just put up a big white board in your cubicle and use some colored markers for the different milestones?" I asked. "You could use blue for the first one, green for the second, red for the last, etc."
  
He took copious notes, fascinated by the concept. I left the firm knowing that I'd not sold any services or product that day but that I'd left the person disappointed that he couldn't deploy the system he'd envisaged. On the way home my phone rang in the car. It was him. "Could you explain the different colors for the white board?" he asked. 
  
Figuring out what problems you're trying to solve before you design the solution and before you choose how to automate it doesn't just save money. It can save an enormous amount of time spent working on elements of the organization that didn't have a problem that needed solving in the first place. 
  
 When the problems you're trying to solve can be best solved with centralized enterprise project management software, then nothing else will really do, but the focus you'll have gained by articulating the problem will help even there. Your deployment team can create success metrics that allow the project to be declared a success when the problems have been resolved. Centralize or decentralize? Enterprise Project Management can be achieved with either. 
  
## About the Author

Chris Vandersluis is the president and founder of Montreal, Canada-based HMS Software, a Microsoft Certified Partner. He has an economics degree from McGill University and over 30 years experience in the automation of project control systems. He is a long-standing member of the Project Management Institute (PMI) and helped found the Montreal, Toronto, and Quebec chapters of the Microsoft Project Users Group (MPUG). Publications for which Chris has written include Fortune, Heavy Construction News, Computing Canada magazine, and PMI's PMNetwork, and he is a regular columnist for Project Times. He teaches Advanced Project Management at McGill University and often speaks at project management association functions across North America and around the world. HMS Software is the publisher of the TimeControl project-oriented timekeeping system and has been a Microsoft Project Solution Partner since 1995. 
  
Chris Vandersluis can be contacted by e-mail at: chris.vandersluis@hms.ca
  
If you would like to read more EPM-related articles by Chris Vandersluis, see HMS's EPM Guidance site (https://www.epmguidance.com/?page_id=39).
  

