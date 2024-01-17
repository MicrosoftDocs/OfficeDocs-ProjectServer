---
title: Deploy language packs in Project Server 2013
ms.author: serdars
author: SerdarSoysal
manager: serdars
ms.date: 11/22/2017
audience: ITPro
ms.topic: how-to
ms.service: project-server-itpro
ms.localizationpriority: medium
ms.collection: IT_ProjectAdmin
ms.assetid: c2964c5e-a2a4-4113-b72a-0f2abc1871cf
description: Install and configure Project Server 2013 language packs so that users can select their preferred language for their PWA user interface.
---

# Deploy language packs in Project Server 2013
 
 **Summary:** Install and configure Project Server 2013 language packs so that users can select their preferred language for their PWA user interface.<br/>
**Applies to:** Project Server 2013
  
Project Server 2013 language packs enable Project Server 2013 users to view Project Web App sites in multiple languages without requiring separate installations of Project Server 2013. You can add language support for additional languages to Project Server 2013 by installing the language pack for the language that you want to add. Language packs are typically used in multinational deployments where one server farm supports people in different locations and users want to see the Project Web App user interface displayed in their preferred language.
  
Project Server 2013 language packs will only allow you to change the language of your Project Web App sites user interface. They do not affect the display language of project sites, or Project Web App web parts that are added to project sites. The language of project sites user interface and PWA web parts added to the project site can be changed by applying SharePoint Server 2013 language packs, which are bundled and installed with Project Server 2013 language packs.
  
Project Server 2013 language packs do not affect the project data that is displayed in Project Web App. The project data will display in the language of the Project Server 2013 base installation, which is required to install a Project Server 2013 language pack. For example, if you apply the Project Server 2013 Japanese language pack on a base installation of Project Server 2013 English, you can display the Project Web App user interface in Japanese, but the project data on the PWA site will display in English.
  
Language packs are not bundled into multilingual installation packages. You must install a specific language pack for each language that you want to support. 
  
In this article:
  
- [Available languages for Project Server 2013 language packs](#first_section)
    
- [Compatibility with SharePoint Server 2013 language packs](#second_section)
    
- [Language Pack deployment scenarios](#dep)
    
- [Deploy a Project Server 2013 language pack](#third__section)
    
- [Uninstall language packs](#fifth_section)
    
## Available languages for Project Server 2013 language packs
<a name="first_section"> </a>

Project Server 2013 language packs are available for the following languages:
  
|**Language**|**ll-cc**|**Locale ID (LCID)**|**Note**|
|:-----|:-----|:-----|:-----|
|Arabic  <br/> |ar-sa  <br/> |1025  <br/> ||
|Brazilian  <br/> |pt-br  <br/> |1046  <br/> ||
|Chinese (PRC)  <br/> |zh-cn  <br/> |2056  <br/> ||
|Chinese (Taiwan)  <br/> |zh-tw  <br/> |1028  <br/> ||
|Czech  <br/> |cs-cz  <br/> |1029  <br/> ||
|Danish  <br/> |da-dk  <br/> |1030  <br/> ||
|Dutch  <br/> |nl-nl  <br/> |1043  <br/> ||
|English (US)  <br/> |en-us  <br/> |1033  <br/> ||
|Finnish  <br/> |fi-fi  <br/> |1035  <br/> ||
|French  <br/> |fr-fr  <br/> |1036  <br/> ||
|German  <br/> |de-de  <br/> |1031  <br/> ||
|Greek  <br/> |el-gr  <br/> |1032  <br/> ||
|Hebrew  <br/> |he-il  <br/> |1037  <br/> ||
|Hungarian  <br/> |hu-hu  <br/> |1038  <br/> ||
|Italian  <br/> |it-it  <br/> |1040  <br/> ||
|Japanese  <br/> |ja-jp  <br/> |1041  <br/> ||
|Korean  <br/> |ko-kr  <br/> |1042  <br/> ||
|Norwegian  <br/> |nb-no  <br/> |1044  <br/> ||
|Polish  <br/> |pl-pl  <br/> |1045  <br/> ||
|Portuguese (Brazil)  <br/> |pt-br  <br/> |1046  <br/> ||
|Portuguese (Portugal)  <br/> |pt-pt  <br/> |2070  <br/> ||
|Romanian  <br/> |ro-ro  <br/> |1048  <br/> |New in Project Server 2013  <br/> |
|Russian  <br/> |ru-ru  <br/> |1049  <br/> ||
|Slovak  <br/> |sk-sk  <br/> |1051  <br/> |New in Project Server 2010  <br/> |
|Slovenian  <br/> |sl-si  <br/> |1060  <br/> |New in Project Server 2010  <br/> |
|Spanish  <br/> |es-es  <br/> |3082  <br/> ||
|Swedish  <br/> |sv-se  <br/> |1053  <br/> ||
|Turkish  <br/> |tr-tr  <br/> |1055  <br/> ||
|Ukrainian  <br/> |uk-ua  <br/> |1058  <br/> |New in Project Server 2010  <br/> |
   
## Compatibility with SharePoint Server 2013 language packs
<a name="second_section"> </a>

Project Server 2013 language packs are bundled with SharePoint Server 2013 language packs. For example, when you download and install the SharePoint Server 2013 Spanish language pack, you also download and install the Project Server 2013 Spanish language pack.
  
> [!IMPORTANT]
> Project Server 2013 does not support all of the languages that SharePoint Server 2013 supports. If a Project Server 2013 language pack is not available for a language that supported in SharePoint Server 2013, the download file will only include the SharePoint Server 2013 language pack. 
  
The following languages are supported by SharePoint Server 2013, but are not available in Project Server 2013 language packs:
  
- Basque
    
- Bulgarian
    
- Catalan
    
- Croatian
    
- Estonian
    
- Galician
    
- Hindi
    
- Kazakh
    
- Latvian
    
- Lithuanian
    
- Serbian (Latin)
    
- Thai
    
As an example, the SharePoint Server 2013 Thai language pack is not bundled with a Thai language pack for Project Server 2013, since it does not exist.
  
For more information about SharePoint Server 2013 language packs, see [Install or uninstall language packs for SharePoint](/sharepoint/install/install-uninstall-language-packs-2019). 
  
## Language Pack deployment scenarios
<a name="dep"> </a>

The following are some deployment scenarios involving Project Server 2013 and SharePoint Server 2013 language packs.
  
### Scenario 1

The customer has a base installation of SharePoint Server 2013 (English). He wants to install Project Server 2013, but also has some users who require Project Web App in a German user interface. The customer does the following:
  
1. Install Project Server 2013 (English).
    
2. Install the Project Server 2013 German Language Pack. 
    
> [!NOTE]
> The SharePoint Server 2013 German Language Pack is not required for this scenario, but is installed since it is bundled with the Project Server 2013 German Language Pack. 
  
> [!NOTE]
> For base installations of SharePoint Server 2013 and Project Server 2013, the same language must be installed. For example, if you have a base installation of SharePoint Server 2013 English, you can only install the base version of Project Server 2013 English with it. And a base installation of Project Server 2013 is required to install any Project Server 2013 language pack. 
  
### Scenario 2

The customer has a base installation of SharePoint Server 2013 (Japanese) and Project Server 2013 (Japanese). She has some customers who require Project Web App in an English user interface. The customer does the following:
  
- Install the Project Server 2013 English Language Pack.
    
> [!NOTE]
> The SharePoint Server 2013 English Language Pack is not required for this scenario, but is installed since it is bundled with the Project Server 2013 English Language Pack. 
  
### Scenario 3

The customer has a base installation of SharePoint Server 2013 (Hindi). He wants to install Project Server 2013 for PWA users who require an English interface. The customer does the following:
  
1. Uninstall the SharePoint Server 2013 (Hindi) base installation.
    
2. Install SharePoint Server 2013 (English).
    
3. Install Project Server 2013 (English).
    
4. Install the SharePoint Server 2013 Hindi Language Pack.
    
Since a Project Server 2013 (Hindi) base SKU does not exist, the customer cannot install it with the SharePoint Server 2013 (Hindi) base installation (base installation SKUs of SharePoint Server 2013 and Project Server 2013 must be in the same language). Installing the SharePoint Server 2013 (English) and Project Server 2013 (English) base SKUs allows him to make PWA available to his users who require an English user interface. Since English PWA is only required for a subset of his users, he still needs to have SharePoint Server 2013 available in Hindi. To have a Hindi SharePoint Server 2013 user interface, he can install the Hindi SharePoint Server 2013 Language Pack. Note that the Hindi SharePoint Server 2013 Language Pack will not contain a language pack for Project Server 2013, since it is not available in that language.
  
### Scenario 4

The customer has a base installation of English SharePoint Server 2013 and Project Server 2013. She requires her SharePoint Server users to have a Romanian user interface. The customer does the following:
  
- Install the Romanian SharePoint Server 2013 Language Pack.
    
> [!NOTE]
> Installing the Romanian SharePoint Server 2013 Language Pack will also install the Romanian Project Server 2013 Language Pack, which is not required for this scenario since PWA users do not require the Romanian user interface. 
  
## Deploy a Project Server 2013 language pack
<a name="third__section"> </a>

The steps for deploying a Project Server 2013 language pack and making the language available to users are as follows:
  
1. [Download the language pack](#section2)
    
2. [Install the language pack](#section3)
    
3. [Make the language available for the Project Web App site](#section5)
    
4. [Specify the display language for the site](#section4)
    
> [!IMPORTANT]
> As mentioned previously, if a Project Server 2013 Language Pack is available for a specific language, it is bundled with the SharePoint Server 2013 Language Pack for that specific language. They will be downloaded as a single file and installed together to your farm. For more information about the availability of Project Server 2013 Language Packs for specific languages, see the "Available languages for Project Server 2013 language packs" section of this article. 
  
### Download the language pack
<a name="section2"> </a>

You must perform the following steps for each language that you want to support. If you decide to download more than one language, be aware that a unique file that has a common name is downloaded for each language. Therefore, make sure that you download each language pack to a separate folder on the hard disk so that you do not overwrite a language pack of a different language.
  
### To download the language pack

1. In your Web browser, go to [Language Packs for SharePoint Server 2013](https://www.microsoft.com/en-us/download/details.aspx?id=37140). 
    
2. On the Language Packs for SharePoint Server 2013 page, select the language that you want from the **Change Language** list, and then click **Change**. 
    
3. The language displayed on the site now corresponds to the language selected in the previous step. Click **Download** on the Web page.
    
    > [!NOTE]
    > If the language on the page has not changed prior to clicking the **Download** command, verify that the language that you selected in step 2 is displayed in the **Change Language** field.
  
4. In the dialog box that appears, click **Save** to download a copy of the file to the local computer.
    
    > [!NOTE]
    > If you are adding multiple language packs, you should rename the language pack file (ServerLanguagePack.exe) to a more descriptive name (for example, FrenchServerLanguagePack.exe). Because the default name for all language pack files is the same, renaming the file will help to prevent confusion when you are installing the language packs. 
  
### Install the language pack
<a name="section3"> </a>

If you have a server farm environment and you are installing language packs to support multiple languages, you must install each language pack on all application servers and Web servers in your farm. 
  
> [!NOTE]
> Note that you are also installing the SharePoint Server 2013 language pack for the specified language during this procedure. 
  
If you are installing the Project Server 2013 language pack on a single-server farm, use the following procedure:
  
### To install a Project Server 2013 language pack for a single-server farm deployment

1. In Windows Explorer, double-click the ServerLanguagePack.exe file to start the installation.
    
2. On the Read the Microsoft Software License Terms page, review the terms, select the **I accept the terms of this agreement** check box, and then click **Continue**. 
    
3. The Setup wizard runs and installs the language pack.
    
4. Run the SharePoint Products Configuration Wizard, using the default settings. 
    
If you are installing Project Server 2013 language packs for a multi-server farm deployment, use the following procedure:
  
### To install a Project Server 2013 language pack for a multi-server farm deployment

1. On a Web or application server in your farm, double-click the ServerLanguagePack.exe file to start the installation.
    
2. On the Read the Microsoft Software License Terms page, review the terms, select the **I accept the terms of this agreement** check box, and then click **Continue**. 
    
3. The Setup wizard runs and installs the language pack.
    
4. The Run Configuration Wizard page appears when the language pack installation is complete. Clear the **Run the SharePoint Products Configuration Wizard now** check box, and then click **Close**. 
    
    > [!CAUTION]
    > Do not run the SharePoint Products Configuration Wizard at this time. 
  
5. On each Web and application server in the farm, install the language pack by using steps 1-4. Make sure not to run the SharePoint Products Configuration Wizard after you install the language pack.
    
    > [!NOTE]
    > If you are installing multiple language packs, install each one to all Web and application servers in the farm by using steps 1-5. Make sure not to run the SharePoint Products Configuration Wizard after installing the language pack. 
  
6. After installing the Project Server 2013 language pack to all Web and application servers in the farm, return to your original server and run the SharePoint Products Configuration Wizard. Use the following steps to run the wizard:
    
1. Click **Start**, click **All Programs**, click **Microsoft SharePoint 2013 Products**, and then click **SharePoint 2013 Products Configuration Wizard**.
    
2. On the Welcome to SharePoint Products page, click **Next**.
    
3. Click **Yes** in the dialog box that alerts you that some services might have to be restarted during configuration.
    
4. On the Completing the SharePoint Products and Technologies Configuration Wizard page, click **Next**.
    
5. On the Configuration Successful page, click **Finish**.
    
7. Run the SharePoint Products Configuration Wizard on all Web and application servers on the farm to complete the installation.
    
### Make the language available for the Project Web App site
<a name="section5"> </a>

After installing the Project Server 2013 language pack, you now have to make the language available for the site. When you make the language available, you are making the language available on a site-by-site basis. For example, making the French language available for Project Web App only allows French to be available for Project Web App sites. The language must be made available for the Business Intelligence Center or for the SharePoint Central Administration Web site for it to be possible to display the site in that language.
  
Use the following procedure to select the language that you want to make available for the site.
  
### To select a language for the site

1. On the Project Web App site, click the **Settings** icon, and then click **Site Settings**.
    
2. On the Site Settings page, in the **Site Administration** section, click **Language Settings**.
    
3. On the Language Settings page, in the **Alternate Language(s)** section, click the check box next to the language that you want to make available for the site. If you have installed the Project Server 2013 language pack, the language for that language pack will be listed as an option for you to select.
    
    > [!NOTE]
    > You can select multiple languages if the site has to be available in more than one language. 
  
4. Click **OK**.
    
### Specify the display language for the site
<a name="section4"> </a>

After you have specified the languages that are available for the site, Project Web App users can then specify the language they want to display for that site. A site user can use the following procedure to display the site user interface in an available language:
  
### To select a display language

1. On the Project Web App site page, click the user account name to display the drop-down list, and then click **My Settings**.
    
2. On the User Information page, click **My Language and Region**.
    
3. On the User Information Language and Region page, in the Language section, under the Display Languages list, click the **Pick a new language** menu. From the menu, select the language in which you want your Project Web App to display. Then click **Add** to add it to the My Display Language list.
    
4. In the My Display Language list, use the arrow to move the language you want your Project Web App site to display in to the top of the list. For example, if you installed the Project Server 2013 Spanish language pack on a base installation of Project Server 2013 English (United States), you will want to move Spanish (Spain) above English (United States) if you want your Project Web App site user interface to display in Spanish.
    
5. Click **OK**.
    
## Uninstall language packs
<a name="fifth_section"> </a>

You can uninstall a Project Server 2013 language pack by using the Control Panel. You can uninstall a SharePoint Server 2013 language pack in the same manner. 
  
If you no longer want to make a language available for a site, clear the language from the list on the Language Settings page for the site.
  
### To remove a language for the site

1. On the Web site, click the **Settings** icon, and then click **Site Settings**.
    
2. On the Site Settings page, in the Site Administration section, click **Language Settings**.
    
3. On the Language Settings page, in the **Alternate Language(s)** section, clear the check box next to the language that you want to make unavailable for the site.
    
4. Click **OK**.
    
## See also
<a name="fifth_section"> </a>

[Install or uninstall language packs for SharePoint](/sharepoint/install/install-uninstall-language-packs-2019)