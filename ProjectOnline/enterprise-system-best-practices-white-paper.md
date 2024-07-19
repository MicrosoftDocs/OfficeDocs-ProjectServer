---
title: "Enterprise system best practices white paper"
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 12/30/2016
audience: admin
ms.topic: overview
ms.service: project-online
ms.localizationpriority: medium
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- ZPJ150
- PJU150
- PJO160
- PJU160
- MET150
ms.assetid: cf300560-ed31-4db8-9e53-b5a1003ea26e
description: "This article is part of our From the Trenches collection. It describes operational best practices for enterprise systems in general (including Microsoft Project Server). It notes how, although enterprise systems strive to provide an easy-to-use interface at the user level, the technology and infrastructure required to provide it is often very complex. This white paper then describes how this complexity requires you to use some basic best practices that give you the best chance of maintaining a high degree of reliability in your enterprise system."
---

# Enterprise system best practices

This article is part of our "From the Trenches" collection. It describes operational best practices for enterprise systems in general (including Microsoft Project Server). It notes how, although enterprise systems strive to provide an easy-to-use interface at the user level, the technology and infrastructure required to provide it is often very complex. This white paper then describes how this complexity requires you to use some basic best practices that give you the best chance of maintaining a high degree of reliability in your enterprise system.
  
To download the Word version of this article, see [Enterprise Management Best Practices](https://go.microsoft.com/fwlink/?LinkId=218145).
  
To see more articles, see ["From the Trenches" white papers](https://support.office.com/article/faec6b1a-c217-4c79-b8c4-0514f402106b).
  
## Enterprise Management Best Practices

I mostly write about enterprise timesheet or enterprise project management systems, and the most common phase of deployment that I talk about with such systems would be either the selection or configuration phase: talking about the strategic perspective. This article is much more about operational practices and isn't specific just to enterprise timesheet or project systems like Microsoft Project Server. Rather, it is about enterprise systems in general, though the subject matter can certainly relate to almost all Project Server deployments.
  
When we encounter already-deployed Project Server systems or we talk to existing clients, we often ask questions about how the organization deployed and has supported the system and its environment. When we got started in the industry, these were simple conversations because the project software we would install would always live on the end-user's PC, and care of the system was always a local concept. These days that's rarely the case. Enterprise systems are simple at the interface or display level where end users can typically access the functionality through a web browser in what looks like any other web page. As simple as these systems might be in front is as complex as they might be in the back. The technology required to display that interface likely has numerous layers, depends on multiple sources for the technology and infrastructure, and (if that's not enough) is probably being updated all the time.
  
But, there are some basic best practices that can give you the best chance of maintaining a high degree of reliability in your enterprise system.
  
### Find an owner

In fact, we have to divide this into two owners because any successful enterprise system has both a business owner and a technical owner. Only when the business owner is an executive in the IT department and the enterprise system is primarily for that department can the owners be the same. So, let's take this in two parts:
  
#### Find a business owner

This person should be an executive level or senior management level person who has a vested interest in the results of the project management system. The benefits that the system must deliver or the business challenges that the system must overcome will have to be benefits and challenges that affect this executive directly. And, before someone even says it; no, typically it can't be a committee or multiple persons. 
  
The responsibility has to lay somewhere and that almost always means one person. This person might also be the executive sponsor for the implementation of the system but might not be. Often the executive sponsor is not the ultimate business owner of an enterprise system. 
  
Even after the deployment project is over, the business owner will still own the system and, should they no longer require it, either another business owner needs to be identified and must commit to the system or the system should be retired.
  
#### Find a technical owner

For enterprise level systems, just having a technician available is insufficient. Remember, enterprise systems depend on many layers of technology. The technical owner must be a senior enough manager or executive in the IT department that he or she will be able to immediately interact with the owners of those other layers of technology. That may include senior people who own the SQL Server database, the database server that SQL Server is installed on, the application server(s) that Project Server is installed on, the networking, the Web server or server farm, the Internet connection, the firewall, Active Directory and Exchange servers, Security servers or systems, and the client-level operating system image. Someone senior must be able to represent this enterprise system to those managers who control other aspects of the environment.
  
### Be purposeful

Make sure that Project Server a) has a purpose and b) is fulfilling its purpose. Sound obvious? It's not. All too often enterprise systems are acquired for the wrong reason, and it falls to someone in IT to look for a purpose to apply the system to. The person signing off on the business purpose for the enterprise system should be the business owner, though others might be involved. I always ask such executives a question I've used for years, "What business decision can you now not make or can you only make with great difficulty, the making of which will be enabled by the deployment of this system?" Once the business requirement (note that I didn't say the desired functionality) is settled, make sure that the enterprise system is actually fulfilling that requirement. I meet a lot of people who have a shopping list of functions but little understanding of what they are trying to accomplish with them. 
  
As the organization evolves, make sure that the business owner comes back to this basic concept. Just the deployment of an enterprise system like Project Server can fundamentally alter the business it is deployed into, so it's not surprising to find that the organization's requirements for a system can change. 
  
It is common to come into an organization several years after Project Server was adopted and deployed only to find it impossible to locate someone who knows why it is important to the organization. The system is in use to be sure. It is being carried forward on sheer inertia but the purpose has been lost and the executives who benefit from it every day don't realize where that benefit is coming from.
  
### Get it into your enterprise architecture

Several years ago I remember going with one of our technical staff to an upset client's location. The instance of Project Server they had installed themselves was causing all kinds of trouble. While there in person, we asked to interview a number of technical personnel, tracing the system back through its layers. When we got to the database layer, we were stunned. Instead of being one of the organization's standard database servers, the SQL Server version on which they'd installed the system was on an end-user's PC. Every time they rebooted, turned the PC off or installed something, the database would become unavailable. This affected literally hundreds of end users.
  
The organization was a large one so there was no lack of enterprise servers or infrastructure to rely on. In this case, the problem was easily fixed. It was a good lesson though. Is the system that you are deploying being woven into the existing corporate infrastructure on which the organization may have spent an enormous effort getting stable, being reliable, and being secure? 
  
### Back it up

I know. This is silly, right? Amazingly and unfortunately it's not. Enterprise systems can be notoriously complex to back up as they may depend on multiple aspects of the system to be backed up at the same time. There is the basic data of course, but also the metadata and configuration data of the implementation. And any related data from ancillary systems that might have to match the system may have to be part of the same backup scheme. When we think of Project Server, we have to think of backing up not just the project database(s) but also the SharePoint Server database. In Project Server versions before 2010 we might need to back up the Global Template. Even now there might be elements of templates that are on individual PCs. 
  
And just backing up isn't enough. When the systems change or are upgraded, do a database restore at least once. I remember years ago being with a client whom we had helped design a backup strategy for. He shut down the server, pulled out the hard disk, put in another hard disk and then looked at us and said "There. The hard disk just crashed. That's a newly formatted hard disk. Please restore my Project Server." I was taken aback, but more so because I realized how good a request it was, and the more I thought of it, the more I realized how shocking it was that no one had ever made the request before (or since). So, do a restore test at least once. We were able to restore that system by the way, but it didn't go back in as cleanly as we'd suspected it would and we had to update our backup procedures.
  
### Staging/Production

"All the world's a stage, and all the men and women merely players," said Shakespeare a long time ago. In this case, the stage is more about staging and that's key for any enterprise system. Once the system is in production, you will want to try new configurations, add new customizations, try new reports, links, fields, and other changes. You will have updates and upgrades and all of these should be tried first in a staging or development environment before they are inflicted on the users in the production environment. Something as basic as a browser update or a database update can throw enterprise systems for a loop, so make sure you keep and maintain a staging environment that's separate from a production environment. In this day and age of virtual servers, this may be easier than it might have been in the past. An entire environment can now often just be cloned from the production system, but that may be easier said than done depending on how you have deployed. Remember lots of different parts of the technology puzzle may be referenced even though you have copied an entire server.
  
### Monitor, monitor, monitor

There are lots of points of oversight that can be used to monitor an enterprise system. First of all, making sure Project Server is available to end users is critical, and ensuring that the appropriate technical staff are notified as quickly as possible if it is ever not available is also essential. Thankfully, there are many tools on the market for ensuring that the system is functional and available that can automatically notify technical staff even if end users haven't noticed the problem yet. But there are other aspects of monitoring that are also important. It is good to keep a watch and a log of the health of the application, including the amount of memory it is using, the amount of the CPU(s) it is taking up, any errors that the system may have reported even if it recovered from them itself, any restarts of the server required, and the relevant health of other elements of the technical infrastructure. Knowing, for example, that IIS is having technical issues might be very important to maintaining the availability of your enterprise application.
  
### Even small changes are changes

The technology on which Project Server is based changes day by day. It's impossible to avoid all of these changes. The Windows Server operating system often receive updates every few days, SQL Server can receive updates every few weeks. Individual Windows client operating systems, their virus scanners, firewalls, and Internet Explorer and its add-ins get updates on a regular basis. Any part of the chain between the data and the end user is a potential point at which the application can break down, so create a structure to manage changes throughout the entire stack of technology. 
  
This can be a challenge, as many different enterprise applications may depend on similar aspects of the stack. We had one client who innocently updated Project Server awhile back only to find that the entire SharePoint Server environment was brought down. Clearly there had been an error in how the Project Server / SharePoint Server update had been applied. While there were complete backups and no data was lost, the upgrade process did not have an instant rollback provision and thus the effects were devastating, as they took days to reverse. 
  
At another organization, we had a client who had updated another enterprise application to find that it absolutely required all users to upgrade their browser version only to discover that other enterprise applications already in use at the company did not support the more recent browser version. It was the proverbial rock and the hard place. In the end, they had to roll back the upgrade of the enterprise system and wait until all the enterprise applications could move forward with a new browser upgrade.
  
### Sometimes it's better to look integrated than be integrated

Sales demonstrations always make the integration of multiple tools look so easy. Hey presto, the data starts here and ends there! Establishing a link between highly flexible tools like Project Server and other enterprise systems like Finance/ERP is tough enough, and we always recommend that both systems be in production and stable before any links are established. Once they are underway, however, it's even more important to monitor any changes of the two systems with a mind to making sure they will continue to link properly. 
  
With any upgrade of either system, there may be data changes, structure changes or different technical requirements. There may also be new features and benefits that are possible, but make sure the existing linking functionality is tested in your staging environment before it's rolled out to production.
  
### Document, document, document

The people who were there when Project Server was selected and deployed won't be in those roles forever. In fact, if they did a great job, they'll be off managing the next enterprise deployment that the organization needs. So documenting the configuration decisions, the projected benefits, the operating expectations, and parameters that were used to make those decisions is essential. On the future, others will be looking at this system and scratching their heads saying, "What were they thinking?" Make sure you tell them. 
  
Enterprise system documents should be living documents that are updated with every upgrade, each change in business or technical owner, or any major change in either the operating structure or the business requirements. 
  
### Look before you leap

It's the advice we give people diving into a murky lake for the first time. Is it shallow? Are there rocks just below the surface? Enterprise project management systems like Project Server can indeed bring complex data elements into one place where decisions based on that data can be more effective and the benefits of those decisions can make a profound difference to an organization. But you need to do your homework to ensure that you are operating your enterprise system in a way that you can get the benefits you need without exposing your organization to costs and risks that can quickly wipe out the value of those benefits.
  
## About the Author

Chris Vandersluis is the president and founder of Montreal, Canada-based HMS Software, a Microsoft Certified Partner. He has an economics degree from McGill University and over 30 years experience in the automation of project control systems. He is a long-standing member of the Project Management Institute (PMI) and helped found the Montreal, Toronto, and Quebec chapters of the Microsoft Project Users Group (MPUG). Publications for which Chris has written include Fortune, Heavy Construction News, Computing Canada magazine, and PMI's PMNetwork, and he is a regular columnist for Project Times. He teaches Advanced Project Management at McGill University and often speaks at project management association functions across North America and around the world. HMS Software is the publisher of the TimeControl project-oriented timekeeping system and has been a Microsoft Project Solution Partner since 1995. 
  
Chris Vandersluis can be contacted by e-mail at: chris.vandersluis@hms.ca
  
If you would like to read more EPM-related articles by Chris Vandersluis, see HMS's EPM Guidance site (https://www.epmguidance.com/?page_id=39).
  

