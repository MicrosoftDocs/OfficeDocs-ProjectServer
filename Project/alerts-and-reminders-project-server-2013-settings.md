---
title: "Alerts and Reminders (Project Server 2013 settings)"
ms.author: serdars
author: serdars
manager: serdars
ms.date: 12/1/2017
audience: ITPro
ms.topic: article
ms.prod: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: ff633803-7a5e-42d7-9e93-6e51eb9f5604
description: "Summary: Use the Alerts and Reminders page in SharePoint Central Administration to configure notification email settings for Project Server 2013."
---

# Alerts and Reminders (Project Server 2013 settings)
 
 **Summary:** Use the Alerts and Reminders page in SharePoint Central Administration to configure notification email settings for Project Server 2013.<br/>
**Applies to:** Project Server 2013
  
The Alerts and Reminders Project Server settings page in SharePoint Central Administration is used to configure notification email settings in your Project Server 2013 environment. There settings on the Alerts and Reminders page are for the two types of notification emails that Project Server sends: 
  
- **Alerts**: This is an email that is sent based on a triggering event. For example, an alert email can be generated for a resource when a project manager assigns a new task to it.
    
- **Reminders**: This is an email that is sent daily noting events that are upcoming or overdue. For example, a reminder email for a team member can include a task that it owns that is scheduled to start tomorrow.
    
Configuration of the Alerts and Reminders page is required for Project Server 2013 to use the automated notification system. On the Alerts and Reminders page, you can:
  
- Configure a connection to an SMTP mail server and associated port number.
    
- Specify the default sender email address and message information that is automatically included with each email notification or reminder that is sent by Project Server.
    
In order to access and use the Alerts and Reminders Project Server settings page in SharePoint Central Administration, you must be a farm administrator.
  
## Notification email settings

### To configure the notification email settings

1. In SharePoint Central Administration, click ** Application Management**.
    
2. On the Application Management page, in the Service Application section, click **Manage Service Applications**.
    
3. On the Service Applications page, click the Project Application Service that contains the Project Web App instance for which you want to access the Administrative Backup settings.
    
4. On the Manage Project Web Apps page, click the drop-down menu for the PWA instance for which you want to access the Administrative Backup settings, and click **Manage**.
    
5. On the Project Web App Server Settings page, in the Operational Policies section, click **Alerts and Reminders**.
    
6. On the Alerts and Reminders page:
    
   - Select **Turn on notification with the following settings** to maintain all of your notification email settings. You must select this option for your settings on this page to apply. Deselecting this option allows you to keep your configuration settings on the page, but have them be non-applicable.
    
   - For the **SMTP mail server** box, enter the server name. Verify the port used in the **Port** box (default value of 25). Change the Port value if your SMTP server uses a port other than the default port for SMTP (Port 25).
    
   - In the **From address** box, enter the default email address from which the email will be sent. This address is the reply-to address for all notification and reminder emails.
    
   - In the **Company domain** box, type the domain name of your company (for example, Contoso.com).
    
   - In the E-mail footer box, type the default message that you want appended to all notification emails. For example: This email message may contain confidential information and is intended for the recipients named above.
    
7. Click **Save**.
    

