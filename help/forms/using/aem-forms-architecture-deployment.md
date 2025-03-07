---
title: Architectuur en plaatsingstopologieën voor AEM Forms
description: Architectuurgegevens voor AEM Forms en aanbevolen topologieën voor nieuwe en bestaande AEM-klanten en klanten die een upgrade uitvoeren van LiveCycle ES4 naar AEM Forms.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
exl-id: 23ffbaa6-1bd9-48c3-afa3-19737bb15de0
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '1471'
ht-degree: 0%

---

# Architectuur en plaatsingstopologieën voor AEM Forms {#architecture-and-deployment-topologies-for-aem-forms}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/forms-overview/aem-forms-cloud-service-architecture.html) |
| AEM 6.5 | Dit artikel |

## Architectuur {#architecture}

AEM Forms is een toepassing die in AEM wordt geïmplementeerd als een AEM-pakket. Het pakket wordt ook wel AEM Forms-add-onpakket genoemd. Het AEM Forms add-on pakket bevat beide services (API-providers), die worden geïmplementeerd in de AEM OSGi-container, en servlets of JSP&#39;s (die zowel front-end als REST API-functionaliteit bieden) die worden beheerd door het AEM Sling-framework. Het volgende diagram toont deze opstelling:

![ architectuur ](assets/architecture.png)

De architectuur voor AEM Forms omvat de volgende componenten:

* {de diensten van AEM van de Kern 0}:**Basisdiensten die AEM aan een opgestelde toepassing verleent.** Deze services omvatten een inhoudsopslagruimte die compatibel is met JCR, een OSGI-servicecontainer, een workflowengine, een vertrouwde opslag, een sleutelarchief, enzovoort. Deze services zijn beschikbaar voor AEM Forms-toepassingen, maar worden niet geleverd door AEM Forms-pakketten. Deze services vormen een integraal onderdeel van de algemene AEM-stack en verschillende AEM Forms-componenten gebruiken deze services.
* **de diensten van Forms:** verstrek formulieren-verwante functionaliteit, zoals creeer, assembleer, verdeel, en archiveer de documenten van PDF, voeg digitale handtekeningen toe om toegang tot documenten te beperken, en gedecodeerde formulieren te decoderen. Deze diensten zijn openbaar beschikbaar voor consumptie door douanecode die in AEM wordt opgesteld.
* **laag van het Web:** JSPs of servlets, die over gemeenschappelijke en vormendiensten worden gebouwd, die de volgende functionaliteit verstrekken:

   * **Authoring frontEnd**: A forms authoring and forms management user interface for authoring and managing forms.
   * **Vertoning en vooraan de voorzijde van de voorlegging van de Vorm**: Een eind - gebruiker die interface voor gebruik door het eind - gebruikers van AEM Forms (bijvoorbeeld, burgers die tot een overheidswebsite toegang hebben) wordt gericht. Dit biedt formulieruitvoering (weergaveformulier in een webbrowser) en verzendfuncties.
   * **REST APIs**: JSPs en servlets voeren een ondergroep vormdiensten voor ver gebruik door op HTTP-Gebaseerde cliënten, zoals de vormen mobiele SDK uit.

**AEM Forms op OSGi:** AEM Forms op milieu OSGi is standaardAEM Auteur of AEM publiceert met AEM Forms pakket dat op het wordt opgesteld. U kunt AEM Forms op OSGi in a [ één enkel servermilieu, Farm, en gegroepeerde montages ](/help/sites-deploying/recommended-deploys.md) in werking stellen. Clusterinstellingen zijn alleen beschikbaar voor AEM Author-instanties.

<!--

**AEM Forms on JEE:** AEM Forms on JEE is AEM Forms server running on JEE stack. It has AEM Author with AEM Forms add-on packages and additional AEM Forms JEE capabilities co-deployed on a single JEE stack running on an application server. You can run AEM Forms on JEE in single-server and clustered setups. AEM Forms on JEE is required only to run document security, process management, and for LiveCycle customers upgrading to AEM Forms. Here are a few additional scenarios to use AEM Forms on JEE:

* **HTML workspace support (for customers using HTML workspace):** AEM Forms on JEE enables single sign-on with Processing instances, serves certain assets rendered on Processing instances, and handles submission of forms rendered within the HTML workspace.
* **Advanced additional form/interactive communication data processing**: AEM Forms on JEE can be utilized for additionally processing form/interactive communication data (and saving the results to a suitable data store) in complex use-cases where advanced process-management capabilities are required.

AEM Forms on JEE also includes provides following supporting services to the AEM components:

* **Integrated user management:** Allows users of AEM Forms on JEE to be recognized as AEM forms on OSGi users and helps enable SSO for both OSGi and JEE users. This is required for scenarios where single sign-on between AEM forms on OSGi and AEM Forms on JEE is required (for example, HTML workspace).
* **Asset hosting:** AEM Forms on JEE can serve assets (for example, HTML5 forms) rendered on AEM Forms on OSGi.

-->

De AEM Forms-ontwerpgebruikersinterface ondersteunt het maken van Document of Record (DOR), PDF forms en HTML5 Forms niet. Dergelijke middelen worden ontworpen met behulp van de stand-alone toepassing van Forms Designer en individueel geupload aan AEM Forms Manager. <!--Alternatively, for AEM Forms on JEE, forms can be designed as application (in AEM Forms Workbench) assets and deployed into AEM Forms on JEE server.-->

AEM Forms op OSGi <!--and AEM Forms on JEE both--> beschikt over workflowmogelijkheden. U kunt basiswerkschema&#39;s voor diverse taken op de vormen van AEM op OSGi snel bouwen en opstellen.<!--, without having to install the full-fledged Process Management capability of AEM Forms on JEE. There is some difference in the [features of Form-centric workflow on AEM Forms on OSGi and Process Management capability of AEM Forms on JEE](capabilities-osgi-jee-workflows.md). The development and management of Form-centric workflows on AEM Forms on OSGi uses the familiar AEM Workflow and AEM Inbox capabilities.-->

## Terminologie {#terminologies}

In de volgende afbeelding worden verschillende AEM Form-serverconfiguraties en hun onderdelen weergegeven die worden gebruikt bij een gebruikelijke AEM Forms-implementatie:

![ aem_forms_-_recommendedtopologie ](assets/aem_forms_-_recommendedtopology.png)

**Auteur:** een auteursinstantie is een server van AEM Forms die op de standaardwijze van de de looppas van de Auteur loopt. <!--It can be AEM Forms on JEE or AEM Forms on OSGi environment.--> Het is bedoeld voor interne gebruikers, formulieren en interactieve communicatieontwerpers, en ontwikkelaars. Het maakt de volgende functies mogelijk:

* **Authoring en beheer van formulieren en interactieve communicatie:** Ontwerpers en ontwikkelaars kunnen adaptieve formulieren en interactieve communicatie maken en bewerken, andere soorten formulieren uploaden die extern zijn gemaakt, bijvoorbeeld formulieren die zijn gemaakt in Adobe Forms Designer, en deze middelen beheren met de Forms Manager-console.
* **Vorm en interactieve mededeling het publiceren:** Assets die op een auteursinstantie wordt ontvangen kan aan publiceer instantie worden gepubliceerd om runtime verrichtingen uit te voeren. Bij het publiceren van bedrijfsmiddelen worden de replicatiefuncties van AEM gebruikt. Adobe adviseert dat een replicatieagent op alle auteursinstanties wordt gevormd om gepubliceerde vormen aan verwerkingsinstanties manueel te duwen, en een andere replicatieagent wordt gevormd op verwerkingsinstanties met *op Receive* toegelaten trekker om de ontvangen vormen automatisch te herhalen om instanties te publiceren.

**publiceer:** a publiceer instantie is een server van AEM Forms die op de norm loopt publiceer looppas wijze. Publicatie-instanties zijn bedoeld voor eindgebruikers van formuliertoepassingen, bijvoorbeeld gebruikers die een openbare website openen en formulieren verzenden. Het maakt de volgende functies mogelijk:

* Forms renderen en verzenden voor eindgebruikers.
* Het vervoer van ruwe ingediende formuliergegevens naar verwerkingsinstanties voor verdere verwerking en opslag in het definitieve registratiesysteem. De standaardimplementatie die in AEM Forms wordt verstrekt bereikt dit gebruikend de omgekeerde replicatiemogelijkheden van AEM. Er is ook een alternatieve implementatie beschikbaar voor het rechtstreeks verplaatsen van formuliergegevens naar verwerkingsservers in plaats van deze eerst lokaal op te slaan (de laatste is een noodzakelijke voorwaarde voor het activeren van reverse-replicatie). Klanten die zorgen over opslag van potentieel gevoelige gegevens hebben over publiceren instanties kunnen binnen voor deze [ alternatieve implementatie ](/help/forms/using/configuring-draft-submission-storage.md) gaan, aangezien de verwerkingsinstanties typisch in een veiligere streek liggen.
* Renderen en verzenden van interactieve communicatie en letters: bij publicatie-instanties wordt een interactieve communicatie en brief weergegeven en de bijbehorende gegevens worden naar verwerkingsinstanties verzonden voor opslag en naverwerking. De gegevens kunnen lokaal op een publicatie-instantie worden opgeslagen en later worden gerepliceerd naar een verwerkingsinstantie (de standaardoptie), of rechtstreeks naar een verwerkingsinstantie worden geduwd zonder op de publicatie-instantie op te slaan. De laatstgenoemde implementatie is nuttig voor veiligheid-bewuste klanten.

**Verwerking:** Een geval van AEM Forms die op de wijze van de de looppas van de Auteur met geen gebruikers loopt die aan de vorm-manager groep worden toegewezen. U kunt <!--AEM Forms on JEE or--> AEM Forms op OSGi als verwerkingsinstantie opstellen. De gebruikers worden niet toegewezen om ervoor te zorgen dat de activiteiten van de creatie en het beheer van de vorm niet op de instantie van de Verwerking worden uitgevoerd en slechts op de instantie van de Auteur voorkomen. Een verwerkingsinstantie schakelt de volgende functies in:

* **Verwerking van ruwe vormgegevens die uit een Publish instantie aankomen:** dit wordt hoofdzakelijk bereikt op een instantie van de Verwerking via de werkschema&#39;s van AEM die teweegbrengen wanneer de gegevens aankomen. De workflows kunnen gebruikmaken van de stap Formuliergegevensmodel die buiten het vak wordt weergegeven om de gegevens of het document naar een geschikte gegevensopslag te archiveren.
* **Veilige opslag van vormgegevens**: De verwerking verstrekt een achter-de-firewallbewaarplaats voor ruwe vormgegevens die van gebruikers geïsoleerd zijn. Geen van de formulierontwerpers op de instantie Auteur en eindgebruikers op de instantie Publiceren hebben toegang tot deze opslagplaats.

  >[!NOTE]
  >
  >Adobe raadt aan een gegevensopslagsysteem van derden te gebruiken om de uiteindelijke verwerkte gegevens op te slaan in plaats van AEM-opslagruimte te gebruiken.

* **opslag en naverwerking van brievengegevens die uit een Publish instantie aankomen:** de werkschema&#39;s van AEM voeren de facultatieve naverwerking van de overeenkomstige brievendefinities uit. Deze workflows kunnen de uiteindelijke verwerkte gegevens opslaan in een geschikte externe gegevensopslag.

* **Workspace die van HTML** ontvangt: Een verwerkingsinstantie bewaart de frontend voor HTML Workspace. De HTML-werkruimte biedt de interface voor de toewijzing van taken en groepen voor revisie- en goedkeuringsprocessen.

Een instantie van de Verwerking wordt gevormd om op de wijze in werking te stellen van de Auteur omdat:

* Hiermee wordt omgekeerde replicatie van onbewerkte formuliergegevens van een instantie Publish ingeschakeld. De manager van de standaardgegevensopslag vereist de omgekeerde replicatieeigenschap.
* AEM Workflows, het belangrijkste middel om onbewerkte formuliergegevens die afkomstig zijn van een instantie Publish, te verwerken, worden aanbevolen op een auteurssysteem uit te voeren.

<!--

## Sample physical topologies for AEM Forms on JEE {#sample-physical-topologies-for-aem-forms-on-jee}

The AEM Forms on JEE topologies recommended below are mainly for customers upgrading from LiveCycle or a previous version of AEM Forms on JEE. Adobe recommends using AEM Forms on OSGi for fresh installations. A fresh installation of AEM Forms on JEE only recommended for using Document Security and Process Management capabilities.

### Topology for using document services or document security capabilities {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms customers planning to use only document services or document security capabilities can have a topology similar to the one displayed below. This topology recommends using a single instance of AEM Forms. You can also create a cluster or farm of AEM Forms servers, if necessary. This topology is recommended when most users programmatically access capabilities of AEM Forms server and intervention through the user interface is minimum. The topology is helpful in batch processing operations of document services. For example, using output service to create hundreds of non-editable PDF documents on daily basis.

Although, AEM Forms lets you set up and run all the functionalities from a single server, yet, you should do capacity planning, load balancing, and set up dedicated servers for specific capabilities in a production environment. For example, for an environment using the PDF Generator service to convert thousands of pages a day and add digital signatures to limit access to documents, set up separate AEM Forms servers for the PDF Generator service and digital signature capabilities. It helps provide optimum performance and scale the servers independent of each other.

![basic-features](assets/basic-features.png)

### Topology for using AEM Forms process management {#topology-for-using-aem-forms-process-management}

AEM Forms customers planning to use AEM Forms process management features, for example, HTML Workspace can have a topology similar to the one displayed below. The AEM Forms on JEE server can be in a single server or cluster configuration.

If you are upgrading from LiveCycle ES4, this topology closely mirrors with what you already have in LiveCycle except for the addition of AEM Author built-in to AEM Forms on JEE. Moreover, there is no change in the clustering requirements for customers performing an upgrade. If you were using AEM Forms in a clustered environment, you can continue with same in AEM 6.5 Forms. For a fresh installation of AEM Forms of JEE for using HTML Workspace, running AEM author instance built-in to the JEE environment is an additional requirement.

Form data store is a third-party data store used for storing final processed data of forms and interactive communications. This is an optional element in the topology. You can also choose to set up a processing instance and use its repository as the final system-of-record system, if necessary.

![topology_for_usinghtmlworkspaceandformsapp](assets/topology_for_usinghtmlworkspaceandformsapp.png)

The topology is recommended to the customers planning to use AEM Forms on JEE server for process management capabilities (HTML Workspace) without using any post-processing, adaptive forms, HTML5 forms, and interactive communication capabilities.

### Topology for using adaptive forms, HTML5 forms, interactive communication capabilities {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms customers planning to use AEM Forms data capture capabilities, for example, adaptive forms, HTML5 Forms, PDF Forms, can have a topology similar to the one displayed below. This topology is also recommended for using interactive communication capabilities of AEM Forms.

![topology-for-using-forms-osgi-modules](assets/topology-for-using-forms-osgi-modules.png)

You can make the following changes/customizations to the above-suggested topology:

* Using HTML Workspace and AEM Forms app requires an AEM author or processing instance. You can use the AEM author instance built-in to AEM Forms on JEE server instead of setting up an additional external AEM author server.
* An AEM Author or Processing instance is required only for Forms-centric workflows on OSGi, adaptive forms, forms portal, and interactive communication.
* interactive communication Agent UI is generally run within the organization. So, you can keep a publish server for Agent UI within the private network.
* AEM forms on OSGi instance built-in to AEM Forms on JEE server can also run Forms-centric workflows on OSGi and Watched Folders.

-->

## Steekproef fysieke topologieën voor het gebruiken van AEM Forms op OSGi {#sample-physical-topologies-for-using-aem-forms-on-osgi}

### Topologie voor gegevensvangst, interactieve mededeling, vorm-Centric Workflow op mogelijkheden OSGi {#topology-for-data-capture-interactive-communication-form-centric-workflow-on-osgi-capabilities}

AEM Forms-klanten die AEM Forms-mogelijkheden voor het vastleggen van gegevens willen gebruiken, bijvoorbeeld adaptieve formulieren, HTML5 Forms, PDF forms, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook geadviseerd voor het gebruiken van interactieve mededelingen en Forms-Centric Workflows op vermogen OSGi, bijvoorbeeld, voor het gebruiken van AEM Inbox en de App van AEM Forms voor bedrijfsproceswerkschema&#39;s.

![ interactief-gebruik-case-af-cm-osgi-workflow ](assets/interactive-use-cases-af-cm-osgi-workflow.png)

### Topologie voor het gebruiken van gelete op omslagmogelijkheden voor off-line partijverwerking {#topology-for-using-watched-folder-capabilities-for-offline-batch-processing}

AEM Forms-klanten die gecontroleerde mappen voor batchverwerking willen gebruiken, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. De topologie toont een gegroepeerd milieu maar u besluit om één enkel geval of een landbouwbedrijf van de servers van AEM Forms afhankelijk van de lading te gebruiken. De gegevensbron van derden is uw eigen systeem-van-verslag. Deze functie fungeert als invoerbron voor Gecontroleerde mappen. De topologie toont ook output in de vorm van een gedrukt dossier. U kunt de uitvoerinhoud ook opslaan in een bestandssysteem, verzenden via e-mail en andere aangepaste methoden gebruiken om uitvoer te verbruiken.

![ off-line-batch-verwerking-via-gecontroleerd-omslagen ](assets/offline-batch-processing-via-watched-folders.png)

### Topologie voor het gebruiken van de mogelijkheden van de documentdiensten voor off-line API-Gebaseerde verwerking {#topology-for-using-document-services-capabilities-for-offline-api-based-processing}

De klanten van AEM Forms die van plan zijn om slechts het vermogen van de documentdiensten te gebruiken kunnen een topologie hebben gelijkend op hieronder getoond. Deze topologie adviseert gebruikend een cluster van AEM Forms op servers OSGi. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically (Gebruikend APIs) toegangsmogelijkheden van de server van AEM Forms en interventie door het gebruikersinterface minimum zijn. De topologie is vrij nuttig in veelvoudige scenario&#39;s van de softwarecliënt. Meerdere clients gebruiken bijvoorbeeld de PDF Generator-service om PDF-documenten op aanvraag te maken.

Hoewel u met AEM Forms alle functies van één server kunt instellen en uitvoeren, moet u capaciteitsplanning uitvoeren, taakverdeling toepassen en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Voor een omgeving die bijvoorbeeld gebruikmaakt van de PDF Generator-service voor het converteren van duizenden pagina&#39;s per dag en van meerdere adaptieve formulieren voor het vastleggen van gegevens, stelt u afzonderlijke AEM Forms-servers in voor de PDF Generator-service en de mogelijkheden voor adaptieve formulieren. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![ off-line-api-based-processing ](assets/offline-api-based-processing.png)
