---
title: "We're selling holes, not drills! white paper"
ms.author: efrene
author: efrene
manager: pamgreen
ms.date: 8/31/2015
ms.audience: End User
ms.topic: overview
ms.service: project-online
localization_priority: Normal
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- PJU150
- PJO160
- PJU160
ms.assetid: 790caa2c-f44d-4a77-a72c-a47acc22f46f
description: "I came across an interesting expression recently. A software salesperson was talking about delivering the entire solution to his client.We don't sell drills. We sell holes,he said. It's a great analogy. Many people (me included) have gone to the hardware store and window shopped in the power tools department while wondering what project I could possibly think of which would justify buying this great power tool. But applying this logic makes as much sense in the do-it-yourself world as it does in enterprise software systems."
---

# We're selling holes, not drills!: white paper

I came across an interesting expression recently. A software salesperson was talking about delivering the entire solution to his client. "We don't sell drills. We sell holes," he said. It's a great analogy. Many people (me included) have gone to the hardware store and window shopped in the power tools department while wondering what project I could possibly think of which would justify buying this great power tool. But applying this logic makes as much sense in the do-it-yourself world as it does in enterprise software systems.
  
If you don't have a problem, you don't need a solution.
  
Just as no one should go looking for a drill unless the problem they'd like to solve is to make a hole, no one should go looking for enterprise software unless it solves some problem. Now if you've got a problem that deploying enterprise software will fix, the next thing to ensure is that what you are buying will deliver the solution you need. That's often a lot more than just buying the software.
  
Deploying an enterprise system is a complex challenge so the payoff has to be worth the effort. In today's world of global project teams, one of the most common things to do is to divide the tremendous effort of an enterprise system deployment. While this can give us economies of scale in using teams which are highly trained in their aspect of the project, it also holds the risk of overlooking aspects of the project in highly risky ways. This risk is compounded the more physically and organizationally disconnected the different teams are.
  
Let's take a look at the most common elements of an enterprise systems project.
  
## What's an enterprise?

First of all, what do I mean by enterprise? I'll take a definition that should work for almost everyone. "Enterprise," in this context, means any project which will impact how the entire organization functions. I'll say this is true for any organization. Implementations that qualify as enterprise implementations aren't just about how many users but how much impact they have. So, updating our virus scanning software from vendor A to vendor B probably wouldn't qualify. The implementation of project scheduling software on the desktop for a handful of users likely wouldn't qualify. Centralizing our project management and using a centralized enterprise project management system probably would qualify.
  
Okay, so if that's an enterprise project, what are the most common elements of a deployment of an enterprise system? In our offices the most common experience is deploying enterprise timesheet systems, such as our own TimeControl, or enterprise project management systems, like Microsoft Project Server, but these elements will be common to almost any enterprise system implementation.
  
## Bits and bytes

First let's tackle the most fundamental building blocks of software: the technical architecture. These days we have to divide our thinking based on our decision to go with an on-premises deployment or an in-the-cloud subscription. I'll leave the wonders of choosing which of these is best under which conditions for another day, but here are some of the basics of what we'll have to think of in each category.
  
If we're going with an on-premises installation, we have to think about what hardware we'll use. What are the hardware requirements for memory and CPUs? Will we use physical servers or virtual servers? Will we use dedicated servers or shared? What kinds of servers might be required? Will we need application servers, security servers, web server servers? What about load balancing, disaster recovery, and backups? Will we need cold or warm backup servers? Whew! But we're not done! What about the database? What are the requirements there? How about support for our existing security, application, and database architectures? What about support for browsers, browser versions, and mobile devices? Once we've got all those questions answered, we have to handle the issues of installation, test, and production environments, and then system health and monitoring once the system is up and running.
  
If we're going with an in-the-cloud subscription implementation, we still have questions to answer though they may be very different questions. Which online service do we use? Do we go with a dedicated installation or a multi-tenant service? What about security? Can we integrate with our own authentication? How do we handle disaster recovery with the subscription service? Where is the data physically located? Does this present legal issues for us? How about support for our internal browsers and mobile devices? How will we get our data out and how can we connect with out internal databases or other external SaaS (Software as a Service) services to integrate functionality?
  
Out of breath yet? When we're talking about an enterprise system, these questions and more are on the agenda. If we shift this part of our project off to our highly trained technical team, they might start to think of this as the scope of the entire project, when this is just the construction of our drill, not yet the making of the hole we need.
  
## Configure me!

Aside from just getting our system working, there is also applying the functionality within that system to our specific problems. I've seen Project Server deployments where the client gets Project Server up and running and then realizes they have not allocated any funding for creating workflows, learning how to prioritize their portfolio of projects, or learning how to make a single report. Just like Systems Analysis 101 back in college, we typically start this part of the implementation at the far right side of a white board as we ask the business people who have the actual business problem what "outputs" they'll need. I've spoken of this before in other writings so I won't belabor it here, but the outputs should ultimately be business decisions. To make those decisions, what reports, analysis, and, ultimately, data inputs do I need? We work our way from the right side of the screen to the left and we end up with a list of all the building blocks we'll need in the form of data elements, analytical calculations, and exports and reports that will need to be configured in the system. This configuration exercise can take weeks or months depending on its complexity.
  
Often the types of resources we'll need for this aspect of the project are a combination of business analyst and system expert, and it's common that while these people may be highly skilled in the functionality of the system being deployed, they are not as skilled in the technical architecture. That makes having disconnected teams for two critical elements of the system quite common. The less these two groups communicate, the more likely it is that we'll face challenges later.
  
## It's a process

It is impossible to deploy a new enterprise system and not affect the organization's processes. Even if you are abandoning one centralized enterprise system and moving to its competitor, processes will change. In fact, if you don't want your processes to change, then it is entirely possible that you don't have a problem that needs solving, and herein lies yet another challenge. When a person's daily routine changes, it causes upset. I don't mean some of the time. In my experience, upset at this time of change is a given. This is true  *even when the process change will result in a better process!*  So thinking about how the processes will change and working with those who will be affected is critical to the success of the project. However, the very experts who are critical to designing this change in process are probably the same people who will be affected by that change, so this can be a challenging aspect of the implementation. Usually, a skilled and experienced facilitator will work with the internal experts in guiding the change in process that has become possible with the implementation of the new system. In our line of work, we see this challenge all the time. "But the project managers have to do the timesheet approvals first," a new TimeControl client tells us. "That's our process." When we explain that matrix approvals can allow project managers to do their timesheet approvals as part of a larger, more effective process, we get upset; pushback. At this point, we have one of our most experienced staff work with the people affected to ensure that their concerns are taken care of, and that they are an integral part of how the process will change. 
  
So the process people are probably not the configuration people **or** the technical people, yet if we don't have this team planned for, all our hard work on the installation and configuration is probably not going to be deployed. This team too must be part of our planning, included in communications and decisions made by the other two teams. 
  
## Training

"So, will we need training?" is unfortunately a question that is often asked last. Some training may come through the process changes as that part of the project requires a lot of hands-on discussion, but what about the actual user guide of how the new system will work in more of a step-by-step fashion? At one time, training was considered to be a critical element of software deployments and clients expected to put aside about 20% of the total budget on it. But, with the changes in software costs and speed of installation, gradually that 20% became less and less money. If we're paying $20 per month per user for a system, should I put aside $4 per user for training? I can't promise it won't go too far. There are many online subscription options for training, but none of that will take into account the exact solution you've designed.
  
Trainers may come from the outside or may come from the configuration or process parts of the project, but they are often people who are specialists rather than the people who actually did the implementation work. So even if you've put funding aside for this team (and I hope you have), you still need to make sure that these people know what the system they're training people in is actually designed to do. I've seen trainers arrive for Microsoft Project Server and had them start explaining to users how to configure enterprise fields and set up business drivers in portfolio analysis, only to have the users give a blank stare because their enterprise fields were already all set up and they're not going to be using portfolio analysis in their initial roll out. Do your trainers even know the problem this particular deployment is supposed to solve? They should. Thinking about training at the start of the project gives it the greatest chance of success. The technical, configuration, and process teams can be putting critical data aside all through their sections for the training that will ultimately be delivered. That means involving the training team early.
  
## Roll-out/acceptance/culture change

If you were forward thinking and put aside the resources to initiate these teams and have had all of them working and communicating together through the project, then the roll-out of your new system is likely to go much smoother than it might otherwise, but don't underestimate the resistance to culture change. Having key evangelists available at the right time can be critical. Also, will all these team members be packing up and moving on to their next project? There will be a lot of system knowledge wrapped up in these people by the time the project rolls out. I was particularly impressed with one of our clients early last year. It was the IT department a large financial organization. One of the concerns we surfaced to the key technical user who was evaluating the software early in the project was "who will be the administrator once you wrap the project up?" "I will," he said. He was true to his word. His skills and knowledge evolved through the multi-month deployment, which was a great success, and he remains the key administrator still.
  
## Wrapping up

There are a hundred other things to think about in how to make sure your teams are communicating and working as part of a larger goal, and we've talked about only a few. Hopefully it is making you think already about your next enterprise system deployment. "What about documentation?" you might be thinking. "What about technical support?"
  
The key thing to remember is this: When you are planning an enterprise system deployment, you have to expand your perspective to include not just the installation effort, but also the delivery of the completed solution. Make sure the hole appears just where it should in just the right size, right depth, and right angle.
  
## About the author

Chris Vandersluis is the president and founder of Montreal, Canada-based HMS Software, a Microsoft Certified Partner. He has an economics degree from McGill University and over 30 years experience in the automation of project control systems. He is a long-standing member of the Project Management Institute (PMI) and helped found the Montreal, Toronto, and Quebec chapters of the Microsoft Project Users Group (MPUG). Publications for which Chris has written include Fortune, Heavy Construction News, Computing Canada magazine, and PMI's PMNetwork, and he is a regular columnist for Project Times. He teaches Advanced Project Management at McGill University and often speaks at project management association functions across North America and around the world. HMS Software is the publisher of the TimeControl project-oriented timekeeping system and has been a Microsoft Project Solution Partner since 1995.
  
Chris Vandersluis can be contacted by e-mail at: chris.vandersluis@hms.ca
  
If you would like to read more EPM-related articles by Chris Vandersluis, see HMS's EPM Guidance site (http://www.epmguidance.com/?page_id=39).
  

