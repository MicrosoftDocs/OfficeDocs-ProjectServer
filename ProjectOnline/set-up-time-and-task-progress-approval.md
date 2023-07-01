---
title: "Set up time and task progress approval"
ms.author: serdars
author: SerdarSoysal
manager: pamgreen
ms.date: 7/11/2017
audience: admin
ms.topic: article
ms.service: project-online
ms.localizationpriority: medium
ms.custom: IT_ProjectAdmin
search.appverid:
- PJO150
- PJU150
- PJO160
- PJU160
- MET150
ms.assetid: ac06db07-b8c3-4f58-be63-af68fa974a27
description: "Instructions on how to set up time and task progress approval using Project Web App."
---

# Set up time and task progress approval

When you decide that you want to use timesheets in your organization, you should also take a few minutes to do some thinking about how you want timesheet approval to work.
  
## How do I set up approvals in my organization?

Before you jump in and get approvals set up in Project Web App, it's a good idea to step back and think through how things currently work in your organization, and how you want them to work going forward. Here are some questions you should try to answer before locking in on a formal approval process.
  
### Do you actually need an approval process in place?

While it may seem natural to set things up so that a manager approves the work that a team member does, it's a good idea to spend some time chatting about whether you really need to have that formal approval process in place. What are you really trying to accomplish by requiring approvals? If your organization's pay structure is tied to the hours entered on timesheets, then the answer is probably yes. But if you're managing projects entirely separate from your financial systems, you may not really need to maintain a step between your team members getting work done, and that work being applied to the project plan.
  
> [!NOTE]
> **You aren't required to set up an approver for everyone!** If you don't need someone to approve the hours a person worked before those hours are applied to the project plan, you don't have to. Simply make the team member his or her own approver. In fact, that's how Project Web App automatically sets things up when you add someone new, so you really don't have to do anything. It doesn't get much easier than that! 
  
### Who's responsible for approving time?

When a team member does work in your organization, who should be on point to approve the hours spent on that work? Is it the project manager? Is it someone from payroll? Maybe it's both. To be able to set up Project Web App in a way that maps to how your organization actually works, you need to figure out the right people to approve time for work that happens in your organization.
  
Sometimes, more than one person needs to approve a timesheet. An example of this might be approvals from a resource manager as well as someone from payroll. If this is the case in your organization, you can set up a chain of approvers, similar to this:
  
|&nbsp;|&nbsp;|&nbsp;|
|:-----|:-----|:-----|
|![Team Member.](media/d7c268ca-1a2f-49b1-8ea0-bd35c44d3e06.png) **Bob** <br/> Bob is a team member, and Jill is his timesheet manager.  <br/> Bob fills out his timesheet and submits it to Jill.  <br/> |![Project Manager](media/e3f6031e-015a-40e6-bcb2-b0123225bb27.png) **Jill** <br/> Jill is a team lead, and Frank is her timesheet manager.  <br/> Jill approves Bob's timesheet, and it is automatically submitted to Frank for approval.  <br/> |![Payroll Specialist](media/07def6e4-4072-4716-862f-14fcea78f191.png) **Frank** <br/> Frank is in payroll, and is his own timesheet manager.  <br/> When Frank approves Bob's timesheet, the hours Bob entered are applied to the corresponding project plan.  <br/> |
   
Only those people listed on the **Timesheet Managers** page can approve timesheets. 
  
 **To add someone as an approver**
  
1. Choose **Settings**![Settings icon.](media/22ecb306-849a-4d04-8885-fe49ec9df8ce.png) \> **PWA Settings**. 
    
2. Under **Time and Task Management**, choose **Timesheet Managers**.
    
    ![Timesheet Managers.](media/8b87dc18-8e5d-4c97-9f6e-12f573f3cfc8.png)
  
3. Choose **Managers** \> **Add Manager**.
    
    ![Add Manager.](media/fe2c56b5-56df-4927-a94e-0f5fa94f22f7.png)
  
4. Choose the person you want to add as an approver, and then choose **OK**.
    
 **How do I set someone's timesheet approver in Project Web App?** You can set a person's **Timesheet Manager** in the [Add a resource to Project Web App](https://support.office.com/article/71c6aa5c-2a97-4cbb-9814-26289c62c471).
  
### Who's responsible for approving task progress?

Remember that [Step 3: Update progress](https://support.office.com/article/ca5c3826-85bf-4a31-9351-3b83fd7c8fe0), even if both are tracked on a team member's timesheet. Sometimes, different people are responsible for approving task progress than those who are responsible for approving time. For example, you may need someone from payroll to approve the number of hours worked (time), but you may not need that person to approve the percent of work that has been completed (task progress). On the flip side, you may need a team lead to approve updates to how much work is left to do on a task before it's completed (task progress), but you may not need that lead to approve the actual hours worked (time). In Project Web App, the project manager always needs to approve task progress, before it is applied to the project plan.
  
 **How do I set someone's task progress approver in Project Web App?** Much like approving time, there is also an approver for task progress too - and this is set to be the project manager making the assignments and is referred to as the **Status Manager**.
  
## What other options are there?

There are a couple of other options that might be appropriate for approvals in your organization. Both of these options are set by going to **Settings**![Settings icon.](media/22ecb306-849a-4d04-8885-fe49ec9df8ce.png) \> **PWA Settings**. From there, some of the settings will be under **Timesheet Settings and Defaults**.
  
![Timesheet Settings and Defaults.](media/4b39ea36-c7ed-4dd4-aece-56f4e959af2a.png)
  
### Can managers approve timesheets line by line?

In the **Timesheet Policies** section, under **Task Status Manager Approval**, choose **Enabled** if you want managers to be able to approve individual timesheet lines. You can also choose to **Require line approval before timesheet approval**. Click **Save** when you are done with your changes. 
  
 If you only want managers to approve entire timesheets, choose **Disabled**.
  
### Can a team member change who approves his or her timesheet first?

Under **Approval Routing**, select the **Fixed Approval Routing** check box if you don't want team members to be able to change the first person who approves a timesheet. Click **Save** when you are done with your changes. 
  
If it's okay for team members to change the first approver, leave this check box cleared. Once the first approver, set by the team member, approves the timesheet, the regular approval routing for the timesheet will kick off.
  
 **Can team members choose anyone they want as a first approver?** No, they can only choose from the list of people that have been added on the **Timesheet Managers** page. 
  

