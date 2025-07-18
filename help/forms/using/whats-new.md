---
title: Overzicht van nieuwe functies | AEM 6.5 Forms
description: De nieuwste functies en verbeteringen voor AEM-formulieren en -documenten, 's werelds meest geavanceerde oplossing voor het beheer van digitale ervaringen.
solution: Experience Manager, Experience Manager Forms
feature: Release Information
role: Admin, User, Developer
hide: true
hidefromtoc: true
exl-id: 4db457d2-fefb-410d-8e74-58147f52bbd3
source-git-commit: 2e291acfc412bbddf215357f57fffbc662bbbd30
workflow-type: tm+mt
source-wordcount: '613'
ht-degree: 0%

---

# Overzicht van nieuwe functies | AEM 6.5 Forms{#new-features-summary-aem-forms}

| Product | Adobe Experience Manager 6.5 |
| -------- | ---------------------------- |
| Versie | 6.5.19.0 |
| Type | Service Pack-release |
| Datum | vrijdag 8 december 2023 |

## Wat is inbegrepen in Adobe Experience Manager 6.5 Forms Service Pack 19 (6.5.19.0)

Experience Manager 6.5.19.0 bevat nieuwe functies, belangrijke verbeteringen die door de klant worden aangevraagd, foutoplossingen en verbeteringen op het gebied van prestaties, stabiliteit en beveiliging die zijn geïntroduceerd sinds de eerste beschikbaarheid van 6.5 in april 2019.

### Nieuwe functies

#### Nieuwe adaptieve Core-componenten van het formulier

De verticale tabbladen, Algemene voorwaarden en Selectievakje worden toegevoegd om de schaalbaarheid van formulieren te verbeteren.

* **[CheckBox component ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/checkbox.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een checkbox component omvatten. Hiermee kunnen gebruikers binaire keuzes maken door een bepaalde optie te selecteren of te deselecteren. De optie wordt meestal weergegeven als een klein vak waarop u kunt klikken of tikken om te schakelen tussen twee statussen: ingeschakeld en uitgeschakeld. Het selectievakje is een veelgebruikt formulierelement voor een ja/nee- of waar/onwaar-keuze.

* **[de component van de Bepalingen en van de Voorwaarden ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/terms-and-conditions.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan nu een component van de Voorwaarden en van de Voorwaarden omvatten. Hiermee kunnen auteurs van formulieren een specifieke sectie in het formulier invoeren waarin gebruikers de voorwaarden, juridische overeenkomsten of het gebruik van een service, product of platform krijgen aangeboden. Deze component is bedoeld om gebruikers te informeren over de regels, regels en verplichtingen waarmee zij instemmen door het formulier in te dienen.

  ![ Verticale lusjes, Voorwaarden en componenten Checkbox ](/help/forms/using/assets/forms-components.png)

* **[Verticale de component van lusjes ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/vertical-tabs.html?lang=nl-NL)**: De adaptieve Forms die op de Componenten van de Kern wordt gebaseerd kan vorminhoud in een verticale lijst van lusjes nu organiseren, die een gestructureerde en navigeerbare lay-out verstrekken. Het gebruik van verticale tabbladen in een formulier kan de algehele gebruikerservaring verbeteren door de navigatie te vereenvoudigen en de organisatie van formulierinhoud te verbeteren, met name in situaties waarin een formulier meerdere secties of complexe informatie bevat.

#### 64-bits versie van AEM Forms Designer

De [ versie met 64 bits van AEM Forms Designer ](/help/forms/using/installing-configuring-designer.md) brengt verbeterde prestaties, scalability, en geheugenbeheer om uw ervaring van de vormverwezenlijking te versterken. Met de 64-bits architectuur kunt u nog grotere en complexere projecten eenvoudig aanpakken, zodat u kunt zorgen voor naadloze ontwerpworkflows en geoptimaliseerde efficiëntie. Verhoog uw mogelijkheden voor formulierontwerp en omarm de toekomst van AEM Forms Designer met deze baanbrekende release.

#### Een adaptieve Forms verbinden met de Microsoft® SharePoint List

AEM Forms verstrekt een out-of-the-box integratie om [ formuliergegevens direct aan de Lijst van SharePoint ](/help/forms/using/configuring-submit-actions.md#submit-to-microsoft&reg;-sharepoint-list)) voor te leggen, latend u de mogelijkheden van de Lijsten van SharePoint gebruiken. U kunt de Microsoft® SharePoint-lijst configureren als gegevensbron voor een formuliergegevensmodel en de verzendactie Verzenden met het formuliergegevensmodel gebruiken om een adaptief formulier te verbinden met de SharePoint-lijst.

#### Ondersteuning voor het configureren van Document of Record-eigenschappen voor adaptieve formulierfragmenten

U kunt uw Adaptieve fragmenten van de Vorm en zijn gebieden in de Adaptieve redacteur van de Vorm [ nu gemakkelijk aanpassen.](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md)

#### Inclusief 64-bits versie van XMLFM

De 64-bits iteratie van XMLFM introduceert verhoogde prestaties, schaalbaarheid en verfijnd geheugenbeheer. Het is de eerste inheemse dienst met 64 bits die op server-kant wordt opgesteld. Met XMLFM 64-bits kan een naadloze afhandeling van grotere renderingwerklasten worden bewerkstelligd door gebruik te maken van zijn inherente mogelijkheden om toegang te krijgen tot aanzienlijk grotere geheugenbronnen in vergelijking met zijn 32-bits tegenhanger. Deze mijlpaal betekent niet alleen een prestatiesprong, maar introduceert ook belangrijke verbeteringen aan het native serviceframework binnen de AEM Forms-server. Deze update zorgt ervoor dat AEM Forms-server naadloos ondersteuning biedt voor elke 64-bits native service.


## Opgeloste problemen

De release bevat ook oplossingen voor meer dan 20 door de klant gemelde problemen. Voor gedetailleerde lijst van moeilijke situaties inbegrepen in het de dienstpak, zie [ versienota&#39;s ](/help/release-notes/release-notes.md)


## Het de dienstpak installeren

Het de dienstpak brengt nieuwe eigenschappen en insectenmoeilijke situaties voor zowel AEM Forms op JEE als AEM Forms op OSGi. De installatieinstructies hebben veranderingen in vergelijking met vorige de dienstpakken.

<!-- 
## Transaction Reports {#transaction-reports}



Transaction reports lets you capture and track the number of submitted forms, processed documents, and rendered documents. The objective behind tracking these transactions is to make an informed decision about the product usage and rebalancing investments in hardware and software. Some examples of transactions include:

* Submission of an Adaptive Form, an HTML5 Form, or a Form Set
* Rendition of a print or a web version of an interactive communication
* Conversion of a document from one file format to another

For information about configuring and using transaction reports, see [Transaction Reports Overview](../../forms/using/transaction-reports-overview.md).

![A sample transaction report](assets/surface_transaction_reporting.png)

## Interactive Communications {#interactive-communications}

**Define data display patterns**

Interactive Communication authors can now define [data display patterns](create-interactive-communication.md#datadisplaypatterns) for fields, variables, and form data model elements. For example, date, currency, or phone formats.

**Use new types of charts**

You can now add [Quadrant charts and charts with multiple series](../../forms/using/chart-component-interactive-communications.md) to Interactive Communications.

**Sort columns in a table**

You can now [sort columns of a table](../../forms/using/create-interactive-communication.md#sortcolumns) in the Interactive Communication. You can bind and sort table columns with static text or data model objects.

**Use new components in a web channel**

You can now add Button and Separator components to the web channel. For more information, see [Add Button component to the web channel](../../forms/using/create-interactive-communication.md#add-button-component-to-the-web-channel) and [Separator component in web channel](../../forms/using/create-interactive-communication.md#separatorcomponent).

**Layout mode to resize components**

You can now switch to [Layout mode](../../forms/using/resize-using-layout-mode.md) to resize components in the Web channel using a WYSIWYG interface.

**Usability improvements**

Interactive Communication authors can now utilize various easy-to-use operations while creating correspondences. The list of operations includes:

* [Perform undo-redo actions in print and web channels](../../forms/using/create-interactive-communication.md#undoredoactions)
* [Add variables in a document fragment using @ symbol](../../forms/using/texts-interactive-communications.md#searchvariables)
* [Add data model elements in a document fragment using @ symbol](../../forms/using/texts-interactive-communications.md#searchdatamodelproperties)
* [Delete or add a web channel to an existing Interactive Communication](../../forms/using/create-interactive-communication.md#edit-interactive-communication-properties)
* [Bind data source elements with fields and variables using drag-and-drop actions](../../forms/using/create-interactive-communication.md#binddatasourceelements)
* [Highlight unbound fields and variables while authoring Interactive Communication](../../forms/using/create-interactive-communication.md#distinguishunboundfields)
* [Perform additional actions such as copy, group, or more on inherited components in a web channel](../../forms/using/create-interactive-communication.md#componenttoolbar)

**Improvements in sync process**

There are several improvements in the Web channel layout auto-generated using the Print channel.

![Interactive Communications Charts](assets/interactive-communication-charts.png)

## Adaptive Forms {#adaptive-forms}

### Use Adobe Sign's cloud-based digital signatures in Adaptive Forms {#use-adobe-sign-s-cloud-based-digital-signatures-in-adaptive-forms}

[Cloud-based digital signatures](https://helpx.adobe.com/nl/sign/kb/digital-certificate-providers.html) or remote signatures are a new generation of digital signatures that work across desktop, mobile, and the web — and meet the highest levels of compliance and assurance for signer authentication. You can now [sign an Adaptive Form](../../forms/using/working-with-adobe-sign.md) with Cloud-based digital signatures.

#### Embed an Adaptive Form or Interactive Communication in AEM Sites Single Page Applications {#embed-an-adaptive-form-or-interactive-communcation-in-aem-sites-single-page-applications}

AEM Forms lets you [seamlessly embed an Adaptive Form](../../forms/using/embed-adaptive-form-aem-sites-spa.md) or Interactive Communication in an AEM Sites single page application (SPA). The embedded Adaptive Form and Interactive Communication is fully functional and users can fill and submit the form without leaving the page. It helps user remain in context of other elements on the web page and simultaneously interact with the adaptive form or Interactive Communication.

#### Sort columns of Adaptive Form tables {#sort-columns-of-adaptive-form-tables}

You can [sort any column of an Adaptive Form table](../../forms/using/adaptive-forms-tables.md#sortcolumnstable) in an ascending or descending order. You can apply sorting to table columns with static text, data model object properties, or a combination of static text and data model object properties.

#### Restrict the availability of Adaptive Forms templates to specific paths {#restrict-the-availability-of-adaptive-forms-templates-to-specific-paths}

Adaptive forms has added support for the cq:allowedPaths property. The property [restricts availability of Adaptive Forms templates to specific paths](creating-adaptive-form.md#adaptive-form-templates).

#### Add check boxes to the Adaptive Form dynamically {#add-check-boxes-to-the-adaptive-form-dynamically}

You can now define rules to [add checkboxes to the Adaptive Form dynamically](../../forms/using/rule-editor.md#setpropertyrule) based on custom function, a form object, or an object property.

## AEM Workflows {#aem-workflows}

### Use variables in AEM Workflows {#use-variables-in-aem-workflows}

Variables enable workflow steps to hold and pass metadata across workflow steps at runtime. You can create different types of variables for storing different types of data. For example, integers, strings, documents, or form data model instances. Typically, you use a variable or a collection of variables when you need to make a decision based on the value that it holds or to store information that you need later in a process.

Variables are an extension of [MetaDataMap](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/workflow/metadata/MetaDataMap.html) interface available in the previous version. It helps save time spent in developing custom ECMAScript code used to retrieve and update metadata values. You continue using MetaDataMap interface and ECMAScript code to manipulate metadata. Some benefits of using variables over MetaDataMap and ECMAScript are:

* Dynamically store, update, and use values stored in a variable across the workflow without relying on custom code
* Retrieve and update values directly to a form data model and data file (XML/JSON ) of a submitted form
* Store complete documents in a variable to perform document processing

The Go To step, OR Split step, and all AEM Forms workflow steps support variables. You can use MetaDataMap interface to access variables in workflow steps that do not have a native support for variables. For more information, see [Variables in AEM Workflows](../../forms/using/variable-in-aem-workflows.md).

![Setting a variable for in a workflow](assets/variable.png)

#### Use a workflow with different Adaptive Forms  {#use-a-workflow-with-different-adaptive-forms}

You can [specify an Adaptive Form for the assign task](../../forms/using/aem-forms-workflow-step-reference.md#assign-task-step) and document of record step of form-centric workflows on the runtime. It allows a workflow to work with different Adaptive Forms. You can decide the method to select an Adaptive Form while designing the workflow. The Adaptive Form can be located at an absolute path, submitted as payload to the workflow, or available at a path calculated using a variable.

#### Use enhanced logging capabilities of forms-centric workflow steps {#use-enhanced-logging-capabilities-of-forms-centric-workflow-steps}

Logging capabilities of forms-centric workflow steps are standardized. Now, all form-centric workflow steps produce similarly standardized logs. It helps improve debugging speed.

## Data Integration {#data-integration}

You can now:

* [Validate input data](../../forms/using/work-with-form-data-model.md#automated-validation-of-input-data) based on a list of constraints. It helps ensure that only valid data is submitted to data source.
* [Override default endpoint](../../forms/using/configure-data-sources.md#configure-soap-web-services) defined in a WSDL (Web Services Description Language) file.

* [Override default](../../forms/using/configure-data-sources.md#configure-restful-web-services) [scheme, host, and base path](../../forms/using/configure-data-sources.md#configure-restful-web-services) defined in Swagger definition file.

## Platform and Security updates {#platform-and-security-updates}

### Major platform updates {#major-platform-updates}

AEM Forms can be set up using any combination of supported operating systems, application servers, databases, database drivers, JDK, LDAP servers, and email servers. The following are the major changes in [supported platforms](../../forms/using/aem-forms-jee-supported-platforms.md):

<table>
 <tbody>
  <tr>
   <td>Component</td>
   <td>Support Removed</td>
  </tr>
  <tr>
   <td>Operating systems</td>
   <td>
    <ul>
     <li>Microsoft Windows Server 2012 R2</li>
     <li>IBM AIX*</li>
     <li>Sun Solaris*</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Application servers<br /> </td>
   <td>
    <ul>
    <li>WebSphere Liberty profile</li>
    <li>Oracle WebLogic</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Databases</td>
   <td>
    <ul>
     <li>IBM DB2 <br /> </li>
     <li>Oracle RAC</li>
    </ul> </td>
  </tr>
  <tr>
   <td>LDAP servers</td>
   <td>
    <ul>
     <li>Microsoft Active Directory 2012</li>
     <li>Novell eDirectory 8.8.7 </li>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Email servers</td>
   <td>
    <ul>
     <li>IBM Lotus Domino 8.5.0 </li>
    </ul> </td>
  </tr>
  <tr>
   <td>Connectors</td>
   <td>
    <ul>
     <li>Connector for Microsoft Sharepoint 2013</li>
     <li>Connector for EMC Documentum 7.0</li>
    </ul> </td>
  </tr>
  <tr>
   <td>AEM Forms app<br /> </td>
   <td>
    <ul>
     <li>Windows 8.1 support</li>
    </ul> </td>
  </tr>
  <tr>
   <td>Java </td>
   <td>
    <ul>
     <li>Java 11</li>
    </ul> </td>
  </tr>
 </tbody>
</table>

&#42; Contact Adobe Support for information on migrating to a different platform

#### New HTML5-based UIs {#new-html-based-uis}

In line with planned EOL of Adobe Flash Player and overall direction of migrating Flash-based content to open standards, AEM 6.5 Forms has replaced Flash-based UI of Health Monitor, Process Management, Reader Extension, and Category Management UI of AEM Forms on JEE Administration Console with HTML5-based UI.

#### Security improvements {#security-improvements}

* AEM 6.5 Forms on JEE administration console UI is now based on Apache Struts 2.5.
* AEM 6.5 Forms now uses jQuery to 3.2.1 and jQuery UI 1.12.1. See, [upgrade documentation](/help/forms/using/introduction-aem-forms.md) for the impact of the change.

#### Accessibility improvements {#accessibility-improvements}

AEM 6.5 Forms has improved accessibility of AEM Forms Workspace. 
!-->
