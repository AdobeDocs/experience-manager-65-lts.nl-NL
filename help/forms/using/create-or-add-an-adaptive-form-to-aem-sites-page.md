---
title: Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina
description: Ontdek hoe u moeiteloos een adaptief formulier kunt maken of toevoegen aan uw AEM Sites-pagina. Leer stapsgewijze technieken en tips en trucs voor het integreren van dynamische en aanpasbare formulieren in uw website en het optimaliseren van uw digitale ervaringen voor maximale impact.
Keywords: AEM Forms in sites, AF in Sites editor, af in aem sites, aem sites af, add af to a sites page, af aem sites, af sites, create af in a sites page, adaptive form in aem sites, forms aem sites, add form to a sites page, adaptive forms aem sites, add adaptive forms to aem page, create forms in an aem sites page
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 6e69ca67-883f-4079-96e2-5b7a9c843ada
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2832'
ht-degree: 0%

---

# Een adaptief formulier maken of toevoegen aan een AEM Sites-pagina {#create-or-add-an-adaptive-form-to-aem-sites-page}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM 6.5 | Dit artikel |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/create-or-add-an-adaptive-form-to-aem-sites-page.html?lang=nl-NL) |

Met AEM Forms kunt u naadloos adaptieve formulieren opnemen in uw webpagina&#39;s. Zo kunnen bezoekers formulieren op een gemakkelijke manier invullen en verzenden zonder de pagina waarop ze staan te verlaten. Op die manier kunnen ze moeiteloos betrokken blijven bij andere elementen van de website terwijl ze actief met het formulier communiceren.

Met de AEM Page Editor kunt u snel meerdere formulieren maken en toevoegen aan uw AEM Sites-pagina&#39;s. Met de AEM Page Editor kunnen auteurs van inhoud naadloze ervaringen met het vastleggen van gegevens maken op een sitepagina met behulp van de kracht van adaptieve formuliercomponenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document van record- en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

AEM Forms biedt adaptieve formuliercontainer en adaptieve Forms - Embed-componenten. U kunt de container van het Aangepaste Vorm gebruiken om een vorm in een Fragment van de Ervaring of een pagina van AEM Sites tot stand te brengen, terwijl de Aangepast Forms - sluit component u een bestaand Aangepast Formulier of tot een vorm toe te voegen gebruikend de Redacteur van de AanpassingsForms.

![ Aangepaste vorm in plaatspagina ](/help/forms/using/assets/adaptive-form-in-sites-page.png)

## Voordelen van het gebruik van de component Adaptieve formuliercontainer in de AEM Page Editor of Experience Fragment

Met de adaptieve formuliercontainer in de AEM Page Editor kunt u naadloze ervaringen met het vastleggen van gegevens op een sitepagina creëren met behulp van de kracht van Adaptive Forms-componenten, zoals dynamisch gedrag, validaties, gegevensintegratie, het genereren van een document voor registratie en bedrijfsprocesautomatisering. Met deze functie kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, doelgericht maken, vertalen en beheer op meerdere sites, waardoor het maken en beheren van formulieren in hun geheel wordt verbeterd. Hieronder volgen enkele voorbeelden:

* **Versioning:** de pagina&#39;s van AEM Sites bieden [ robuuste versieringsmogelijkheden ](/help/sites-authoring/working-with-page-versions.md) aan, toestaand u om verschillende versies van uw vormen te volgen en te beheren. Op deze manier kunt u wijzigingen aanbrengen en formulieren verbeteren terwijl u de mogelijkheid behoudt om indien nodig terug te draaien naar vorige versies. Versioning zorgt voor een beheerste en georganiseerde benadering van formulierontwikkeling en -ontwikkeling.
* **het richten (Integratie met Adobe Target):** met de pagina&#39;s van AEM Sites die mogelijkheden richten, kunt u de vormervaring voor verschillend publiek [&#128279;](/help/sites-administering/target.md) ook  personaliseren. Door gebruikerssegmenten en doelcriteria te gebruiken, kunt u de inhoud, het ontwerp of het gedrag van het formulier aanpassen aan specifieke groepen gebruikers. Hierdoor kunt u een gepersonaliseerde en relevante formulierervaring bieden, waardoor de betrokkenheid en conversiesnelheden toenemen.
* **Vertaling:** AEM Sites [ naadloze integratie met de vertaaldiensten ](/help/sites-administering/translation.md), toestaand u om vormen in veelvoudige talen gemakkelijk te vertalen. Deze functie vereenvoudigt het lokalisatieproces, zodat uw formulieren toegankelijk zijn voor een wereldwijd publiek. U kunt vertalingen efficiënt beheren in AEM-vertaalprojecten, waardoor u minder tijd en moeite nodig hebt voor meertalige formulierondersteuning. Zie de sectie Overwegingen voor meer informatie over vertaling.
* **Beheer van meerdere plaatsen en Levend Exemplaar:** AEM Sites verstrekt robuust [ Multisite Beheer en Levende mogelijkheden van het Exemplaar ](/help/sites-administering/msm.md), toelatend u om veelvoudige websites binnen één enkel milieu tot stand te brengen en te beheren. Met deze functie kunt u nu formulieren hergebruiken op verschillende sites, zodat u consistent bent en dubbel werk kunt voorkomen. Met gecentraliseerde controle en beheer kunt u formulieren efficiënt onderhouden en bijwerken op meerdere websites.
* **Thema&#39;s:** de pagina&#39;s van AEM Sites verstrekken een kader voor het ontwerpen van en het handhaven van verenigbare visuele stijlen over veelvoudige Web-pagina&#39;s. Met deze opties definieert u kleuren, lettertypen, stijlpagina&#39;s en andere visuele elementen die een bijdrage leveren aan het algehele uiterlijk van de website. [ u kunt de thema&#39;s gebruiken die voor een pagina van AEM Sites voor een Aanpassings vorm worden ontworpen, die tijd en inspanning besparen ](/help/sites-authoring/style-system.md).
* **Tags toevoegen:** de pagina&#39;s van AEM Sites laten u [ markeringen of etiketten aan een pagina, een activa, of andere inhoud ](/help/sites-authoring/tags.md) toewijzen. Tags zijn trefwoorden of metagegevenslabels waarmee u inhoud kunt indelen en indelen op basis van specifieke criteria. U kunt een of meer tags toewijzen aan pagina&#39;s, elementen of andere inhoud in AEM om de zoekopdracht te verbeteren en de elementen te categoriseren.
* **het Vergrendelen en Ontgrendelen van inhoud:** AEM Sites staat gebruikers toe om [ toegang en wijzigingen aan pagina&#39;s ](/help/sites-authoring/editing-content.md#locking-a-page-locking-a-page) binnen het milieu van AEM Sites te controleren. Wanneer een pagina is vergrendeld, betekent dit dat deze is beveiligd tegen onbevoegde wijzigingen of bewerkingen door andere gebruikers. Alleen de gebruiker die de inhoud heeft vergrendeld of een aangewezen beheerder kan deze ontgrendelen om wijzigingen toe te staan.


## Verschillende opties voor het toevoegen van een adaptief formulier in de AEM Page Editor

U kunt deze functie optimaal benutten door de volgende opties te gebruiken:

* **[voeg een douane Aangepaste Vorm aan een pagina van AEM Sites toe:](#create-an-adaptive-form-in-sites-editor)** bouw een gloednieuwe vorm van kras, die het specifiek aan uw vereisten en ontwerpvoorkeur aanpast.

* **[voeg een douane Aangepaste Vorm aan een Fragmenten van de Ervaring toe:](#create-an-adaptive-form-in-experience-fragment)** breid het bereik van uw vormen uit door hen aan de Fragmenten van de Ervaring van AEM toe te voegen, die voor naadloos hergebruik over veelvoudige pagina&#39;s of plaatsen toestaan.

* **[zet een Aangepast die Vorm in het Fragment van de Ervaring om:](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)** zet een Aangepast die Vorm aan een pagina van AEM Sites wordt toegevoegd in een Fragment van de Ervaring om de vorm over veelvoudige pagina&#39;s van AEM Sites opnieuw te gebruiken.

* **creeer en voeg vormen toe die op goedgekeurde malplaatjes aan een pagina van AEM Sites worden gebaseerd:** Gebruik pre-goedgekeurde malplaatjes om vormen snel tot stand te brengen die zich op de brandende richtlijnen en ontwerpnormen van uw organisatie richten. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.

* **voeg bestaande vormen aan een pagina van AEM Sites toe:** integreer gemakkelijk vormen die u reeds in uw websites hebt gecreeerd, toelatend bezoekers om met hen direct in wisselwerking te staan. Deze optie is alleen beschikbaar voor Adaptive Forms die is gemaakt met de Adaptive Forms Editor of de Adaptive Forms - Embed-component.

* **voeg veelvoudige vormen aan een pagina van AEM Sites of de Fragment van de Ervaring toe:** voeg veelvoudige vormen aan een pagina toe om veelvoudige keuzen aan gebruikers te verstrekken die op hun voorkeur en vereisten worden gebaseerd. Dit kan een combinatie van geheel nieuwe formulieren en bestaande formulieren zijn.

## Overwegingen {#consideration}

* Wanneer u een formulier maakt of toevoegt met de container voor adaptieve formulieren, worden de formulieren vertaald en gelokaliseerd via de AEM Sites-vertaalstroom. Voor elke taal wordt een afzonderlijke kopie (taalkopie) van de sitepagina en de bijbehorende formulieren gegenereerd en wanneer een auteur van de inhoud een regel in een formulier op de bovenliggende pagina wijzigt, moeten dezelfde wijzigingen worden aangebracht in alle taalkopieën van het formulier. Met de adaptieve formuliercontainer kunt u ook verschillende functies van AEM Sites-pagina&#39;s gebruiken, zoals versioning, adressering, vertaling en beheer voor meerdere sites.

* Wanneer u een formulier maakt of toevoegt met de component Adaptief insluiten van formulieren, worden de formulieren vertaald en gelokaliseerd met behulp van de AEM Forms-vertaalstroom. In dit geval wordt één formulier onderhouden en wordt ernaar verwezen in alle taalkopieën van de sitepagina&#39;s. De adaptieve component Form-embed biedt geen toegang tot verschillende functies van AEM Sites-pagina&#39;s, zoals versioning, adressering, vertaling en beheer voor meerdere sites.


## Voordat u begint {#before-you-start}

+++  Adaptieve Forms Core-componenten inschakelen voor uw omgeving

Zorg ervoor dat de [ Aangepaste Componenten van de Kern van Forms voor uw milieu ](https://experienceleague.adobe.com/docs/experience-manager-headless-adaptive-forms/using/quick-setup/enable-headless-adaptive-forms-and-core-components.html?lang=nl-NL) worden toegelaten.

+++

+++  Adaptieve Forms-clientbibliotheken toevoegen aan uw AEM Sites-pagina en onderdelen van de Experience Fragment-pagina

Om volledige functionaliteit van de Adaptive Forms Container component toe te laten, voeg de Customheaderlibs en Customfooterlibs cliëntbibliotheken aan uw AEM Sites pagina toe gebruikend de plaatsingspijpleiding. De bibliotheken toevoegen:

1. Meld u aan bij de AEM Author-instantie en open CRX DE. De standaard-URL voor een instantie Auteur die lokaal wordt uitgevoerd, is `http://localhost:4502/crx/de` .

1. Open het bestand `/apps/[your-sites-project]/components/page/customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open het bestand `/apps/[your-sites-project]/components/page/customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Open het bestand `/apps/[your-sites-project]/components/xfpage/customheaderlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //Customheaderlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-call="${clientlib.css @ categories='core.forms.components.runtime.all'}"/>
       </sly> 
   ```

1. Open het bestand `/apps/[your-sites-project]/components/customfooterlibs.html` en voeg de volgende code toe aan het bestand:

   ```
       //customfooterlibs.html
       <sly data-sly-use.clientlib="core/wcm/components/commons/v1/templates/clientlib.html">
       <sly data-sly-test="${!wcmmode.edit}" data-sly-call="${clientlib.js @ categories='core.forms.components.runtime.all', async=true}"/>
       </sly> 
   ```

1. Herhaal bovenstaande stappen voor alle instanties Auteur en Publiceren in uw omgeving.

+++

+++ Adaptieve Forms-container inschakelen

Voer de volgende stappen uit om [!UICONTROL Adaptive Forms Container] -component in sjabloonbeleid in te schakelen:

1. Open de AEM Sites-pagina of Experience Fragment om te bewerken. Als u de pagina wilt openen om te bewerken, selecteert u de pagina en klikt u op Bewerken.
1. Open de sjabloon van de pagina Sites of Experience Fragment. Om het malplaatje te openen, ga naar [!UICONTROL Page Information] ![ de Informatie van de Pagina ](/help/forms/using/assets/Smock_Properties_18_N.svg) > [!UICONTROL Edit Template]. De bijbehorende sjabloon wordt geopend in de sjablooneditor.
1. In de mening van de Structuur, klik het **[!UICONTROL Policy]** ![ Beleid ](/help/forms/using/assets/Smock_FeedManagement_18_N.svg) pictogram in de menubar. In de **[!UICONTROL Allowed Components]** lijst en selecteer **[!UICONTROL Adaptive Forms Container]** checkbox onder de **[Naam van het Project van de Archetype van AEM ] - Aangepaste Vorm**.
1. Klik op **[!UICONTROL Done]**.

>[!VIDEO](https://video.tv.adobe.com/v/3419370?quality=12&learn=on)

+++

## Een adaptief formulier maken {#create-an-adaptive-form-in-sites-editor-or-experience-fragment}

U kunt een geheel nieuw formulier maken en dit aanpassen aan uw vereisten en ontwerpvoorkeuren, rechtstreeks op een AEM Sites-pagina of in Experience Fragment. Voor formulieren voor eenmalig gebruik wordt direct schrijven naar een AEM Sites-pagina aanbevolen, terwijl Experience Fragments ideaal zijn voor formulieren die opnieuw moeten worden gebruikt op meerdere pagina&#39;s op uw website.

* [Een formulier maken op een AEM Sites-pagina](#create-an-adaptive-form-in-sites-editor)
* [ creeer een vorm in een Fragment van de Ervaring ](#create-an-adaptive-form-in-experience-fragment)
* [ zet een Aangepast Vorm in de pagina van AEM Sites in een Fragment van de Ervaring om ](#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment)

### Een formulier maken op een AEM Sites-pagina {#create-an-adaptive-form-in-sites-editor}

Met de component Adaptief formuliercontainer in de AEM Page Editor kunt u een aangepast formulier maken. Met de component kunt u een formulier maken door de formuliercomponenten te slepen en neer te zetten. De formuliercomponenten zijn gebaseerd op kerncomponenten. U kunt deze instellingen eenvoudig aanpassen aan de vereisten van uw organisatie.

>[!VIDEO](https://video.tv.adobe.com/v/3419284?quality=12&learn=on)

Een adaptief formulier maken op een sitepagina:

1. Open de AEM Sites-pagina in de bewerkingsmodus.
1. Sleep de component **[!UICONTROL Adaptive Forms Container]** van de Componentbrowser naar de pagina Sites. Er wordt een spatie op de pagina voor het formulier gemaakt. U kunt de lay-outmodus gebruiken om de grootte van de containerruimte te wijzigen.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte om het formulier te maken.
1. Voeg de knop Verzenden toe.

Daarna, plaatst u [ de Submit Actie ](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een formulier maken in een ervaringsfragment {#create-an-adaptive-form-in-experience-fragment}

U kunt het bereik van uw formulieren uitbreiden door ze toe te voegen aan AEM Experience Fragments, zodat u ze naadloos kunt hergebruiken op meerdere pagina&#39;s of sites. U kunt bijvoorbeeld een inschrijvingsformulier voor een nieuwsbrief opnemen in een Experience-fragment. Zo kunt u het fragment op meerdere pagina&#39;s van uw website opnieuw gebruiken, zodat u het formulier niet herhaaldelijk opnieuw hoeft te maken. Alle updates of wijzigingen die worden aangebracht in het inschrijvingsformulier voor nieuwsbrieven binnen het Experience Fragment, worden automatisch doorgegeven aan alle pagina&#39;s waar het wordt gebruikt. Dit stroomlijnt het proces en zorgt voor een naadloze gebruikerservaring en vereenvoudigt het beheer van de formulieren van uw website.

Een adaptief formulier maken in een ervaringsfragment:

1. Open een ervaringsfragment.
1. Sleep de component **[!UICONTROL Adaptive Forms Container]** van de Componentbrowser naar het fragment van de Experience.
1. Sleep Adaptieve componenten van Form Core naar de containerruimte in het Experience Fragment om het formulier te maken.
1. Voeg de knop Verzenden toe.

Daarna, plaatst u [ de Submit Actie ](#configure-submit-action-for-form) en geavanceerde eigenschappen.

### Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment {#convert-an-adaptive-form-in-sites-page-to-an-experience-fragment}

U kunt een bestaand adaptief formulier in een sitepagina-editor converteren naar een ervaringsfragment om het formulier te hergebruiken op meerdere pagina&#39;s of sites.

Een adaptief formulier in AEM Sites-pagina converteren naar een Experience-fragment:

1. Open de AEM Sites-pagina met het adaptieve formulier (in de Adaptive Forms Container-component) in de bewerkingsmodus.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Voor de menubar, selecteer ![ Bekeerling om het pictogram van de fragmentvariatie ](/help/forms/using/assets/Smock_FilingCabinet_18_N.svg) Omzetten in het de variatiepictogram van het Fragment van de Ervaring te ervaren.
   ![ zet vorm in plaatspagina in een ervaringsfragment om ](/help/forms/using/assets/convert-form-in-sites-page-to-an-experience-fragment.png)

   Er wordt een dialoogvenster weergegeven waarin u de container Adaptief formulier kunt converteren naar een nieuw Ervaringsfragment of een bestaand Erviteitsfragment kunt uitbreiden
1. Stel in het dialoogvenster Converteren naar ervaringsfragmentvariatie waarden in voor de volgende opties:

   * **Actie:** Uitgezocht om een Fragment van de Ervaring tot stand te brengen of aan een bestaand Fragment van de Ervaring toe te voegen.
   * **de weg van de Ouder:** specificeer weg van de omslag om het Fragment van de Ervaring binnen te ontvangen. De optie is alleen beschikbaar voor het maken van een ervaringsfragment.
   * **Malplaatje:** specificeer weg van het malplaatje van het Fragment van de Ervaring. Als u geen malplaatje van het Fragment van de Ervaring hebt, [ creeer het ](/help/sites-developing/experience-fragments.md). De optie is alleen beschikbaar als u een adaptief formulier toevoegt aan een bestaand ervaringsfragment.
   * **titel van het Fragment:** specificeer titel van het Fragment van de Ervaring. De titel identificeert op unieke wijze een ervaringsfragment


## Handeling voor verzenden voor het formulier configureren {#configure-submit-action-for-form}

Met een handeling Verzenden kunt u de bestemming kiezen van gegevens die zijn vastgelegd in een adaptief formulier. Deze wordt geactiveerd wanneer een gebruiker op de knop Verzenden klikt op een adaptief formulier. Aangepaste formulieren bevatten enkele van de verzendacties. U kunt ook een standaardverzendactie uitbreiden om uw eigen aangepaste verzendactie te maken. Een handeling verzenden voor uw formulier configureren:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van verzendacties wordt geopend.
   ![ Aangepaste vormencontainer ](/help/forms/using/assets/adaptive-forms-container.png)
1. Selecteer en vorm een Submit actie, die op uw vereisten wordt gebaseerd. Voor gedetailleerde informatie over Submit Acties, zie [ Aangepaste Vorm verzenden Actie ](configuring-submit-actions.md)


## Een schema of formuliergegevensmodel voor een formulier configureren {#configure-schema-or-data-model-for-form}

Met het formuliergegevensmodel kunt u een formulier verbinden met een gegevens-Source en gegevens verzenden en ontvangen op basis van gebruikersacties. U kunt een formulier ook verbinden met een JSON-schema om de verzonden gegevens in een vooraf gedefinieerde indeling te ontvangen.

Voordat u een formulier koppelt aan een schema of formuliergegevensmodel

* [Een JSON-schema maken en uploaden naar uw omgeving](adaptive-form-json-schema-form-model.md)
* [Een formuliergegevensmodel maken](create-form-data-models.md)

Een JSON-schema of formuliergegevensmodel configureren voor uw formulier:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![ het gegevensmodel van de Vorm adaptieve vormencontainer ](/help/forms/using/assets/form-data-model-adaptive-forms-container.png)
1. Selecteer en configureer een JSON-schema of formuliergegevensmodel op basis van uw vereisten. Voor gedetailleerde informatie over Submit Acties, zie [ Aangepaste Vorm verzenden Actie ](configuring-submit-actions.md).

   * Als u de optie **[!UICONTROL Form Model]** selecteert, gebruikt u de optie **[!UICONTROL Select Form Data Model]** om een vooraf geconfigureerd formuliergegevensmodel te selecteren.
   * Als u de optie **[!UICONTROL Schema]** selecteert, gebruikt u de optie **[!UICONTROL Schema]** om een JSON-schema voor uw formulier te selecteren.

1. Klik op **[!UICONTROL Done]**.

## Een prefill-service voor een formulier configureren {#configure-prefill-service-for-form}

U kunt de Prefill-service gebruiken om automatisch velden van een adaptief formulier in te vullen met bestaande gegevens. Wanneer een gebruiker een formulier opent, worden de waarden voor die velden vooraf ingevuld. U kunt:

* [Een aangepaste prefill-service maken](prepopulate-adaptive-form-fields.md)
* [ van de Gegevens van de Vorm van het Gebruik Model vooraf ingevulde dienst ](#fdm-prefill-service)

### Vooraf ingevulde service Formuliergegevensmodel gebruiken {#fdm-prefill-service}

Met de service Vooraf invullen formuliergegevensmodel kunt u velden van een formulier vooraf invullen met een geconfigureerd formuliergegevensmodel. Het model van Gegevens van de Vorm Prefill de dienst gebruikt [ krijgt Dienst van het gevormde Model van Gegevens van de Vorm ](work-with-form-data-model.md#add-data-model-objects-and-services-add-data-model-objects-and-services) om gegevens terug te winnen. Als u de service Vooraf invullen van formuliergegevensmodel wilt gebruiken voor een adaptief formulier:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
   ![ prefill de paginaredacteur van de de dienstfdm de plaatsen van de dienstpagina ](/help/forms/using/assets/prefill-service-fdm-aem-sites-page-editor.png)
1. Selecteer een formuliergegevensmodel. Open de tab **[!UICONTROL Basic]** . Selecteer **[!UICONTROL Forms Portal Draft Prefill Service]** in de service Prefill.
1. Klik op **[!UICONTROL Done]**.

## Leid de gebruiker om naar een nieuwe gebruiker bij het indienen van een formulier of toon een bedankje

Bij het verzenden van een formulier kunt u de gebruiker omleiden naar een andere webpagina of een bericht. Om de gebruiker om te leiden of het dank u bericht te vormen:

1. Open de AEM Page Editor of Experience Fragment dat het adaptieve formulier bevat.
1. Open de inhoudsstructuur en selecteer de **[!UICONTROL Adaptive Forms Container]** die als host fungeert voor het adaptieve formulier. Een AEM Sites-pagina kan meerdere Adaptive Forms hosten. Selecteer dus zorgvuldig de juiste adaptieve Forms-container.
1. Klik het AanpassingsEigenschappen van de Container van de Vorm ![ AanpassingsContainer eigenschappen ](/help/forms/using/assets/configure-icon.svg) pictogram. Het dialoogvenster Aangepaste formuliercontainer voor het configureren van gegevensmodellen wordt geopend.
1. Open de tab **[!UICONTROL Submission]** .

   * Als u een omleidings-URL wilt configureren, selecteert u bij Verzenden de optie Omleiden naar URL en geeft u een absoluut adres, een omleidings-URL of een relatief pad van een AEM Sites-pagina op.

   * Als u een aangepast bericht of een bedankbericht wilt configureren, selecteert u bij Verzenden de optie Bericht tonen en geeft u een bericht op in het vak Berichtinhoud. Het is een tekstvak met tekstopmaak. U kunt de optie Volledig scherm gebruiken om alle beschikbare tekstitems weer te geven.

## Zie ook {#see-also}

* [Een op zichzelf staand adaptief formulier voor kerncomponenten maken](/help/forms/using/create-an-adaptive-form-core-components.md)
* [Stijlen of thema&#39;s maken voor uw formulieren](/help/forms/using/create-or-customize-themes-for-adaptive-forms-core-components.md)
