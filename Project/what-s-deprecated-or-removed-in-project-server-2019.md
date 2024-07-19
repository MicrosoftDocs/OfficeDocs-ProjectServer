---
title: "What's deprecated or removed in Project Server 2019 "
ms.author: jenz
author: jenzamora
manager: jtremper
ms.date: 7/24/2018
audience: ITPro
ms.topic: overview
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection:
- IT_ProjectAdmin
- IT_ProjectAdmin_Top
ms.assetid: 04fee973-5623-4768-a3ba-c109e45dd7eb
description: "Learn what has been deprecated or removed in Project Server 2019."
---

# What's deprecated or removed in Project Server 2019 
Learn what has been deprecated or removed in Project Server 2019.
  
This article describes features and functionality that have been removed in Project Server 2019 that had been previously available in Project Server 2016.
  
- [Resource Plans](what-s-deprecated-or-removed-in-project-server-2019.md#RePlan)
    
- [My Tasks](what-s-deprecated-or-removed-in-project-server-2019.md#MyTasks)
    
- [Project Server Interface (PSI) Project class removed](what-s-deprecated-or-removed-in-project-server-2019.md#ProjectClass)
    
- [Project Server Interface (PSI) members](what-s-deprecated-or-removed-in-project-server-2019.md#PSImem)
    
- [Project Server Interface (PSI) extensions](what-s-deprecated-or-removed-in-project-server-2019.md#PSIext)
    
## Resource Plans
<a name="RePlan"> </a>

In Project Server 2016, what was previously known as Resource Plans in Project Server 2013 has now evolved into Resource Engagements. Resource Engagements will allow project managers working in Project Professional 2016 or the Project Online Desktop Client to systematically place resource requests in order to build their project teams. Resource managers working in Project Server 2016 will then be able to modify, accept or reject those requests. 
  
Existing Resource Plans can be converted to Resource Engagements when you upgrade from Project Server 2013 to Project Server 2016 as an optional part of the upgrade process. The Resource Plan view will no longer be available in Project Professional 2016 or Project Professional 2019.
  
> [!NOTE]
> For more information about Resource Engagements, see this [blog post](https://go.microsoft.com/fwlink/?LinkID=620823&amp;clcid=0x409). For more information about migrating your Project Server 2013 Resource Plans to Resource Engagements as part of the Project Server 2016 upgrade process, see [Upgrading to Project Server 2019](upgrading-to-project-server-2019.md). 
  
## My Tasks
<a name="MyTasks"> </a>

The My Tasks and associated Exchange Task Sync features have been removed in SharePoint Servers 2016 or SharePoint Server 2019. The Work Management Service Application that is required for both features has also been removed.
  
## Project Server Interface (PSI) Project class removed
<a name="ProjectClass"> </a>

The Project class in the PSI is not supported in Project Servers 2016 or Project Server 2019. For all new development, use the [Project Client Side Object Model (CSOM)](/previous-versions/office/project-class/jj236068(v=office.15)).
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcProject** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|Project  <br/> |All  <br/> |
|ProjectContextDataSet  <br/> |All  <br/> |
|ProjectDataSet  <br/> |All  <br/> |
|ProjectImpactDataSet  <br/> |All  <br/> |
|ProjectRelationsDataSet  <br/> |All  <br/> |
|ProjectTeamDataSet  <br/> |All  <br/> |
|SyncDataSet  <br/> |All  <br/> |
|SyncErrorsDataSet  <br/> |All  <br/> |
   
## Project Server Interface (PSI) members
<a name="PSImem"> </a>

In Project Server 2019, the following PSI members have been removed: 
  
> [!NOTE]
> For more information about the Project Server Interface, see [Project Server 2013 class library and web service reference](/previous-versions/office/project-class/ee767707(v=office.15))
  
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Microsoft.Office.Project.Server.Library** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|Activity  <br/> |PROPOSAL_REVIEW_APPROVAL_FEATURE_UID  <br/> PROPOSAL_REVIEW_WORKFLOW_FEATURE_UID  <br/> |
|CubeStatus.CbsProcessErrorId  <br/> |DsoTranslatorNotFound  <br/> DsoNotInstalled  <br/> |
|IPSContextInfo  <br/> |Lcid  <br/> |
|PSContextInfo  <br/> |PSContextInfo(Boolean, String, Guid, Guid, Guid, String)  <br/> PSContextInfo(Boolean, String, Guid, Guid, Guid, Int32, String)  <br/> Lcid  <br/> SiteVersion  <br/> |
|PSErrorID  <br/> |LookupTableItemHasTrailingOrLeadingWhitespace  <br/> |
|PSEventID  <br/> |Deprecated8  <br/> Deprecated9  <br/> |
|PSDBUtility  <br/> |IntArrayListToCommaDelimitedString  <br/> |
|PSSecurityCategory  <br/> |MyPersonaIProjects  <br/> |
|PSSecurityGIobaIPermission  <br/> |ChangeProjectState  <br/> CreateNewProposalOrActivity  <br/> DownloadPwaOutlookAddIn  <br/> ManageStatusReports  <br/> ViewDataAnalysis  <br/> |
|PSSecurityObjectType  <br/> |MaxBuildInObjectType  <br/> Model  <br/> |
|Security  <br/> |PROPOSAL_APPROVERS_GROUP_UID  <br/> |
|ViewConstants.ViewType  <br/> |VISION  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Microsoft.Office.Project.Server.WebServiceProxy** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|LoginWindows  <br/> |\<all>  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**Microsoft.Office.Project.Server.Workflow** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|WorkflowStringIds  <br/> |SEND_EMAIL_PROJECT_COMPLETED_BODY  <br/> STATUS_INITIALIZE_FAILED_INVALID_PROJECT  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcCubeAdmin** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|CubeAdmin  <br/> |SetCubeBuiIdingSettings  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcEvents** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|PSEventID  <br/> |Deprecated8  <br/> Deprecated9  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcPortfolioAnalyses** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|AnalysisDataSet.AnalysisProjectsDataTable  <br/> |AddAnalysisProjectsRow (AnalysisDataSet.AnalysisRow, Guid, String, Double, Double, DateTime, DateTime, DateTime, Int32, DateTime, DateTime, Byte)  <br/> |
|AnalysisDataSet.AnalysisProjectsRow  <br/> |FNLT  <br/> SNET  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcStatusing** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|ProjectDataSet.TaskRow  <br/> |DurationType  <br/> PROJ_OPT_CURRENCY_DIGITS  <br/> PROJ_OPT_CURRENCY_POSITION  <br/> PROJ_OPT_CURRENCY_SYMBOL  <br/> |
   
|&nbsp;|&nbsp;|
|:-----|:-----|
|**WebSvcTimeSheet** <br/> | |
| *Type*  <br/> | *Removed members*  <br/> |
|TimesheetListDataSet.TimesheetsRow  <br/> |TS_AUX_STATUS  <br/> |
   
## Project Server Interface (PSI) extensions
<a name="PSIext"> </a>

In Project Server 2019, Project Server Interface (PSI) extension scenarios are not supported. These scenarios enabled integration with custom Windows Communication Foundation (WCF) services. 
  
> [!NOTE]
> For more information about PSI extensions, see the MSDN article [Developing PSI Extensions](/previous-versions/office/developer/office-2010/ff843378(v=office.14)). 
  
## See also
<a name="PSIext"> </a>


[What's new for IT pros in Project Server 2019 ](what-s-new-for-it-pros-in-project-server-2019.md)


[New and improved features in SharePoint Server 2019 ](/SharePoint/what-s-new/new-and-improved-features-in-sharepoint-server-2019)


[What's deprecated from SharePoint Server 2019 ](/SharePoint/what-s-new/what-s-deprecated-or-removed-from-sharepoint-server-2019)
