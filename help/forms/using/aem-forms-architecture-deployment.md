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
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2469'
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

**AEM Forms op JEE:** AEM Forms op JEE is de server die van AEM Forms op de stapel JEE loopt. Er zijn invoegpakketten voor AEM Author met AEM Forms en extra AEM Forms JEE-mogelijkheden die op één JEE-stapel worden geïmplementeerd die op een toepassingsserver wordt uitgevoerd. U kunt AEM Forms op JEE in enig-server en gegroepeerde montages in werking stellen. AEM Forms on JEE is alleen vereist voor het uitvoeren van documentbeveiliging, procesbeheer en voor LiveCycle-klanten die een upgrade naar AEM Forms uitvoeren. Hier volgen enkele aanvullende scenario&#39;s voor het gebruik van AEM Forms op JEE:

* **de werkruimtesteun van HTML (voor klanten die de werkruimte van HTML gebruiken):** AEM Forms op JEE laat enige aanmelding met de instanties van de Verwerking toe, dient bepaalde activa die op de instanties van de Verwerking worden teruggegeven, en behandelt voorlegging van vormen die binnen de werkruimte van HTML worden teruggegeven.
* **Geavanceerde extra vorm/interactieve communicatie gegevensverwerking**: AEM Forms op JEE kan voor extra verwerkings vorm/interactieve communicatie gegevens (en het opslaan van de resultaten aan een geschikte gegevensopslag) in complexe gebruik-gevallen worden gebruikt waar de geavanceerde proces-beheer mogelijkheden worden vereist.

AEM Forms on JEE biedt ook de volgende ondersteunende diensten aan de AEM-componenten:

* **Geïntegreerd gebruikersbeheer:** staat gebruikers van AEM Forms op JEE toe om als vormen van AEM op OSGi gebruikers worden erkend en de hulp laat SSO voor zowel gebruikers toe OSGi als JEE. Dit is vereist voor scenario&#39;s waarbij Single Sign-On tussen AEM-formulieren op OSGi en AEM Forms op JEE vereist is (bijvoorbeeld de HTML-werkruimte).
* **het ontvangen van activa:** AEM Forms op JEE kan activa (bijvoorbeeld, vormen HTML5) dienen die op AEM Forms op OSGi worden teruggegeven.

De AEM Forms-ontwerpgebruikersinterface ondersteunt het maken van Document of Record (DOR), PDF forms en HTML5 Forms niet. Dergelijke middelen worden ontworpen met behulp van de stand-alone toepassing van Forms Designer en individueel geupload aan AEM Forms Manager. Voor AEM Forms op JEE kunnen formulieren ook worden ontworpen als toepassingsmiddelen (in AEM Forms Workbench) en worden geïmplementeerd in AEM Forms op de JEE-server.

AEM Forms op OSGi en AEM Forms op JEE hebben beide workflowmogelijkheden. U kunt snel basisworkflows voor verschillende taken samenstellen en implementeren op de AEM-formulieren op OSGi, zonder dat u de volledige Process Management-capaciteit van AEM Forms op JEE hoeft te installeren. Er is één of ander verschil in de [ eigenschappen van vorm-centric werkschema op AEM Forms op OSGi en vermogen van het Beheer van het Proces van AEM Forms op JEE ](capabilities-osgi-jee-workflows.md). De ontwikkeling en het beheer van Form-centric workflows op AEM Forms op OSGi maakt gebruik van de bekende AEM Workflow- en AEM Inbox-mogelijkheden.

## Terminologie {#terminologies}

In de volgende afbeelding worden verschillende AEM Form-serverconfiguraties en hun onderdelen weergegeven die worden gebruikt bij een gebruikelijke AEM Forms-implementatie:

![ aem_forms_-_recommendedtopologie ](assets/aem_forms_-_recommendedtopology.png)

**Auteur:** een auteursinstantie is een server van AEM Forms die op de standaardwijze van de de looppas van de Auteur loopt. Het kan AEM Forms op JEE of AEM Forms op milieu OSGi zijn. Het is bedoeld voor interne gebruikers, formulieren en interactieve communicatieontwerpers, en ontwikkelaars. Het maakt de volgende functies mogelijk:

* **Authoring en beheer van formulieren en interactieve communicatie:** Ontwerpers en ontwikkelaars kunnen adaptieve formulieren en interactieve communicatie maken en bewerken, andere soorten formulieren uploaden die extern zijn gemaakt, bijvoorbeeld formulieren die zijn gemaakt in Adobe Forms Designer, en deze middelen beheren met de Forms Manager-console.
* **Vorm en interactieve mededeling het publiceren:** Assets die op een auteursinstantie wordt ontvangen kan aan publiceer instantie worden gepubliceerd om runtime verrichtingen uit te voeren. Bij het publiceren van bedrijfsmiddelen worden de replicatiefuncties van AEM gebruikt. Adobe adviseert dat een replicatieagent op alle auteursinstanties wordt gevormd om gepubliceerde vormen aan verwerkingsinstanties manueel te duwen, en een andere replicatieagent wordt gevormd op verwerkingsinstanties met *op Receive* toegelaten trekker om de ontvangen vormen automatisch te herhalen om instanties te publiceren.

**publiceer:** a publiceer instantie is een server van AEM Forms die op de norm loopt publiceer looppas wijze. Publicatie-instanties zijn bedoeld voor eindgebruikers van formuliertoepassingen, bijvoorbeeld gebruikers die een openbare website openen en formulieren verzenden. Het maakt de volgende functies mogelijk:

* Forms renderen en verzenden voor eindgebruikers.
* Het vervoer van ruwe ingediende formuliergegevens naar verwerkingsinstanties voor verdere verwerking en opslag in het definitieve registratiesysteem. De standaardimplementatie die in AEM Forms wordt verstrekt bereikt dit gebruikend de omgekeerde replicatiemogelijkheden van AEM. Er is ook een alternatieve implementatie beschikbaar voor het rechtstreeks verplaatsen van formuliergegevens naar verwerkingsservers in plaats van deze eerst lokaal op te slaan (de laatste is een noodzakelijke voorwaarde voor het activeren van reverse-replicatie). Klanten die zorgen over opslag van potentieel gevoelige gegevens hebben over publiceren instanties kunnen binnen voor deze [ alternatieve implementatie ](/help/forms/using/configuring-draft-submission-storage.md) gaan, aangezien de verwerkingsinstanties typisch in een veiligere streek liggen.
* Renderen en verzenden van interactieve communicatie en letters: bij publicatie-instanties wordt een interactieve communicatie en brief weergegeven en de bijbehorende gegevens worden naar verwerkingsinstanties verzonden voor opslag en naverwerking. De gegevens kunnen lokaal op een publicatie-instantie worden opgeslagen en later worden gerepliceerd naar een verwerkingsinstantie (de standaardoptie), of rechtstreeks naar een verwerkingsinstantie worden geduwd zonder op de publicatie-instantie op te slaan. De laatstgenoemde implementatie is nuttig voor veiligheid-bewuste klanten.

**Verwerking:** Een geval van AEM Forms die op de wijze van de de looppas van de Auteur met geen gebruikers loopt die aan de vorm-manager groep worden toegewezen. U kunt AEM Forms op JEE of AEM Forms op OSGi als verwerkingsinstantie opstellen. De gebruikers worden niet toegewezen om ervoor te zorgen dat de activiteiten van de creatie en het beheer van de vorm niet op de instantie van de Verwerking worden uitgevoerd en slechts op de instantie van de Auteur voorkomen. Een verwerkingsinstantie schakelt de volgende functies in:

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

## Steekproef fysieke topologieën voor AEM Forms op JEE {#sample-physical-topologies-for-aem-forms-on-jee}

De hieronder aanbevolen AEM Forms on JEE-topologieën zijn vooral bedoeld voor klanten die een upgrade uitvoeren van LiveCycle of een eerdere versie van AEM Forms op JEE. Adobe raadt aan AEM Forms op OSGi te gebruiken voor nieuwe installaties. Een nieuwe installatie van AEM Forms op JEE wordt alleen aanbevolen voor het gebruik van de functies Documentbeveiliging en Process Management.

### Topologie voor het gebruiken van de diensten van het document of documentveiligheidsmogelijkheden {#topology-for-using-document-services-or-document-security-capabilities}

AEM Forms-klanten die alleen documentservices of documentbeveiligingsmogelijkheden willen gebruiken, kunnen een topologie hebben die vergelijkbaar is met de hieronder weergegeven topologie. Deze topologie adviseert gebruikend één enkel geval van AEM Forms. Indien nodig kunt u ook een cluster of farm van AEM Forms-servers maken. Deze topologie wordt geadviseerd wanneer de meeste gebruikers programmatically tot mogelijkheden van de server van AEM Forms toegang hebben en de interventie door het gebruikersinterface minimum is. De topologie is nuttig in partijverwerkingsverrichtingen van de documentdiensten. Met uitvoerservice kunt u bijvoorbeeld dagelijks honderden niet-bewerkbare PDF-documenten maken.

Hoewel AEM Forms u in staat stelt alle functies van één server in te stellen en uit te voeren, moet u toch capaciteitsplanning, taakverdeling en specifieke servers instellen voor specifieke mogelijkheden in een productieomgeving. Als u bijvoorbeeld in een omgeving met de PDF Generator-service duizenden pagina&#39;s per dag wilt converteren en digitale handtekeningen wilt toevoegen om de toegang tot documenten te beperken, maakt u afzonderlijke AEM Forms-servers voor de PDF Generator-service en de mogelijkheden voor digitale handtekeningen. Het helpt optimale prestaties te bieden en de servers onafhankelijk van elkaar te schalen.

![ basis-eigenschappen ](assets/basic-features.png)

### Topologie voor het gebruik van AEM Forms-procesbeheer {#topology-for-using-aem-forms-process-management}

AEM Forms-klanten die AEM Forms-functies voor procesbeheer willen gebruiken, kunnen bijvoorbeeld een topologie hebben die vergelijkbaar is met de hieronder weergegeven topologie. De AEM Forms op JEE-server kan zich in één server- of clusterconfiguratie bevinden.

Als u een upgrade uitvoert vanuit LiveCycle ES4, weerspiegelt deze topologie nauw de bestaande eigenschappen in LiveCycle, met uitzondering van de toevoeging van ingebouwde AEM-auteur aan AEM Forms op JEE. Bovendien is er geen verandering in de het groeperen vereisten voor klanten die een verbetering uitvoeren. Als u AEM Forms in een geclusterde omgeving gebruikte, kunt u hetzelfde doen in AEM 6.5 Forms. Voor een nieuwe installatie van AEM Forms of JEE voor het gebruik van HTML Workspace, is het uitvoeren van de ingebouwde AEM-ontwerpinstantie in de JEE-omgeving een extra vereiste.

De opslag van formuliergegevens is een gegevensopslagruimte van derden die wordt gebruikt voor de opslag van de uiteindelijke verwerkte gegevens van formulieren en interactieve communicatie. Dit is een facultatief element in de topologie. U kunt er ook voor kiezen om een verwerkingsinstantie in te stellen en de opslagplaats ervan te gebruiken als het uiteindelijke systeem van gegevensbestanden, indien nodig.

![ topologie_for_usinghtmlworkspaceandformsapp ](assets/topology_for_usinghtmlworkspaceandformsapp.png)

De topologie wordt aanbevolen voor klanten die AEM Forms op de JEE-server willen gebruiken voor procesbeheermogelijkheden (HTML Workspace) zonder gebruik te maken van naverwerking, adaptieve formulieren, HTML5-formulieren en interactieve communicatiemogelijkheden.

### Topologie voor het gebruik van adaptieve formulieren, HTML5-formulieren, interactieve communicatiemogelijkheden {#topology-for-using-adaptive-forms-html-forms-interactive-communication-capabilities}

AEM Forms-klanten die AEM Forms-mogelijkheden voor het vastleggen van gegevens willen gebruiken, bijvoorbeeld adaptieve formulieren, HTML5 Forms, PDF forms, kunnen een soortgelijke topologie hebben als hieronder wordt weergegeven. Deze topologie wordt ook geadviseerd voor het gebruiken van interactieve communicatie mogelijkheden van AEM Forms.

![ topologie-voor-gebruiken-vormen-osgi-modules ](assets/topology-for-using-forms-osgi-modules.png)

U kunt de volgende veranderingen/aanpassingen aan de bovengenoemde topologie aanbrengen:

* Voor het gebruik van de HTML Workspace- en AEM Forms-app is een AEM-auteur of -verwerkingsexemplaar vereist. U kunt de ingebouwde AEM-auteurinstantie van AEM Forms op de JEE-server gebruiken in plaats van een extra externe AEM-auteurserver op te zetten.
* Een AEM-instantie voor auteur of verwerking is alleen vereist voor Forms-centric workflows op OSGi, adaptieve formulieren, formulierportal en interactieve communicatie.
* De interactieve UI van de communicatieAgent wordt over het algemeen in werking gesteld binnen de organisatie. Zo, kunt u een publicatieserver voor Agent UI binnen het privé netwerk houden.
* AEM-formulieren op OSGi-instantie die zijn ingebouwd in AEM Forms op JEE-server, kunnen ook op Forms gerichte workflows uitvoeren op OSGi en Gecontroleerde mappen.

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
