---
title: Opmerkingen bij de huidige release voor Adobe Experience Manager 6.5 LTS, SP1
description: Hier vindt u de actuele release-informatie voor Adobe Experience Manager 6.5 LTS, service pack 1.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: b5a8f555-c061-4fe2-a100-cc01335959cb
source-git-commit: 12e2966754fe317c2a20951ee29b401425de486b
workflow-type: tm+mt
source-wordcount: '7223'
ht-degree: 0%

---

# Huidige releaseopmerkingen voor Adobe Experience Manager 6.5 LTS, SP1 {#release-notes}

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] 6,5 LTS |
|---|---|
| Versie | Service Pack 1 (SP1), Hotfix voor GRANITE-61551 <!-- UPDATE FOR EACH NEW RELEASE --> |
| Type | Service Pack-release |
| Datum | 9 september 2025 <!-- UPDATE FOR EACH NEW RELEASE --> |
| URL downloaden | [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq660%2Fhotfixes%2Fcq-6.5.lts.1-hotfix-GRANITE-61551-1.2.zip) |

<!-- OLD URL TO JAR
(https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack-lts/cq-quickstart-6.6.1.jar) | -->


<!-- UPDATE ABOVE FOR EACH NEW RELEASE -->

## Wat is inbegrepen in [!DNL Adobe Experience Manager] 6.5 LTS, SP1 {#what-is-new}

<!-- UPDATE EACH RELEASE -->

[!DNL Experience Manager] 6.5 LTS, SP1 omvat nieuwe eigenschappen, zeer belangrijke klant-gevraagde verhogingen, en insectenmoeilijke situaties. Het omvat ook prestaties, stabiliteit, en veiligheidsverbeteringen die sinds de aanvankelijke beschikbaarheid van 6.5 LTS in Maart 2025 worden vrijgegeven. [ installeer dit Pak van de Dienst ](#install-update) op 6.5 LTS.

<!-- ## Key features and enhancements -->

<!-- 6.5 LTS REVIEWERS: WHAT ARE THE KEY FEATURES AND ENHANCEMENTS THAT YOU WANT TO HIGHLIGHT IN THIS RELEASE? -->

<!-- UPDATE EACH RELEASE -->

## Problemen opgelost in 6,5 LTS, Service Pack 1 {#fixed-issues}

<!-- UPDATE BELOW FOR EACH NEW RELEASE -->

### [!DNL Sites]{#sites-65-LTS-SP1}

#### Toegankelijkheid {#sites-accessibility-65-lts-sp1}

* Probleem verholpen waarbij het tekstredement in inhoudsfragmenten standaard werd afgekapt. In de teksteditor wordt nu de volledige inhoud zonder afkapping weergegeven. (SITES-33005)
* Probleem verholpen waarbij met klikken op URL-paden de homepage van Indigo werd geopend in plaats van de juiste doel-URL. (SITES-33004)
* Probleem met toegankelijkheid verholpen in een aangepaste AEM-component die problemen met de naleving van ADA tijdens geautomatiseerde tests veroorzaakte. (SITES-30660)
* Problemen met ADA-compatibiliteit in het dialoogvenster Waarschuwing en Workflowberichten zijn opgelost door ervoor te zorgen dat tekst zwart wordt weergegeven op lichte achtergronden en voldoet aan de WCAG 2.0-contrastvereisten. (SITES-30138)
* Probleem verholpen waarbij de knop &#39;Categorie&#39; in de AEM Sites-editor geen specifiek label had, waardoor JAWS het zou aankondigen als &#39;Menu Afbeeldingen knop&#39; in plaats van een beschrijvend label. (SITES-27497)
* Probleem met toegankelijkheid verholpen waarbij pictogrammen voor vinkjes in het scherm Effectieve machtigingen geen alternatieve tekst hadden, waardoor JAWS de betekenis niet kon lezen en overbrengen. (SITES-27272)
* Probleem met toegankelijkheid verholpen waarbij de pagina Machtigingen geen duidelijke JAWS-aankondiging bevat voor het verwijderen van gebruikers- of groepsmachtigingen, wat tot verwarring bij gebruikers van schermlezers leidde. (SITES-27238)
* Probleem verholpen waarbij foutberichten alleen als pictogrammen zonder beschrijvende tekst werden weergegeven, zodat JAWS de fouten niet kon aankondigen toen deze zich voordeden. (SITES-27155)
* Probleem met toegankelijkheid verholpen waarbij JAWS onjuiste en onduidelijke knopbeschrijvingen leest in de AEM On-Premise-omgeving, inclusief ontbrekende koptekst op niveau 2 voor de sectie Modules. (SITES-27152)
* Probleem met toegankelijkheid verholpen waarbij JAWS het aantal resultaten niet aankondigde na het filteren van waarden op het tabblad AEM Assets. (SITES-27150)
* Probleem met toegankelijkheid verholpen waarbij bij het maken van een map geen bevestiging werd weergegeven en JAWS dit niet aankondigde in de gebruikersinterface van Assets. (SITES-27141)
* Probleem met toegankelijkheid in AEM Sites opgelost. JAWS heeft geen formulierfouten gemeld, focus verplaatst naar niet-interactieve foutelementen en vereiste-veldfouten zijn niet weergegeven op de tab-out. (SITES-27138)
* Probleem verholpen waarbij het menu van de knop Tijdlijnen een specifiek label bevatte, waardoor JAWS alleen &quot;Activiteiten knopmenu&quot; kon lezen zonder een duidelijke beschrijving te geven. (SITES-27134)
* Probleem verholpen waarbij JAWS de handeling of rol voor containeritems niet aankondigde en alleen &quot;Breadcrumb v1&quot; en &quot;button v2&quot; las in plaats van beschrijvende labels. (SITES-27131)
* Probleem verholpen waarbij het pop-upbericht Snel publiceren niet het juiste succes gaf, zodat schermlezers geen feedback over voltooiing konden aankondigen. (SITES-26912)
* Probleem met toegankelijkheid in de weergave van de koraalkolom verholpen waarbij elementen met ARIA-rollen die onderliggende rollen vereisen, deze niet bevatten, waardoor de toegankelijkheidsnormen niet werden nageleefd. (SITES-26898)
* Probleem verholpen waarbij &#39;sjabloon&#39;- en &#39;eigenschappen&#39;-tekst in de bovenste navigatie van de pagina Maken niet zichtbaar waren in de modus Opnieuw plaatsen, waardoor gebruikers van het toetsenbord en de schermlezer geen toegang kregen. (SITES-26895)
* Probleem met toegankelijkheid verholpen waarbij knopinfo voor de pictogrammen &quot;search&quot;, &quot;solution&quot;, &quot;help&quot;, &quot;inbox&quot; en &quot;user&quot; in de bovenste navigatie niet toegankelijk was via toetsenbordnavigatie. (SITES-26889)
* Probleem met toegankelijkheid verholpen waarbij formuliervelden op het tabblad Standaard geen suggesties voor fouten bevatten, zodat gebruikers geen aanwijzingen kunnen krijgen wanneer vereiste invoervelden leeg waren. (SITES-26885)
* Probleem verholpen waarbij NVDA en schermlezers van Narrator geen sjabloonbestandsgegevens op de pagina Maken aankondigden, zodat gebruikers niet via programmacode volledige informatie konden ontvangen. (SITES-26884)
* Probleem verholpen waarbij een onjuiste naam werd gebruikt voor het tekstvak Paginatitel op het tabblad Standaard, zodat schermlezers geen nauwkeurige informatie aan gebruikers konden geven. (SITES-26879)
* De bijgewerkte knoop voor en achtergrondkleuren om aan WCAG 2.2 te voldoen a minimumeisen van de contrastverhouding, die leesbaarheid en toegankelijkheid voor alle gebruikers verbeteren. (SITES-26877)
* Oplossing van een probleem dat ervoor zorgde dat de tekst &#39;template&#39; en &#39;eigenschappen&#39; in de bovenste navigatie van de pagina create verdwenen na het wijzigen van de grootte, zodat gebruikers met een laag gezichtsvermogen de zichtbaarheid en toegankelijkheid kregen. (SITES-26872)
* Probleem verholpen waarbij meerdere horizontale schuifbalken werden weergegeven op de hoofdpagina nadat een Opnieuw plaatsen was toegepast. Zo hebt u ervoor gezorgd dat één schuifbalk wordt weergegeven voor een goede toegankelijkheid en zichtbaarheid van de inhoud. (SITES-26800)
* Probleem met toegankelijkheid verholpen in de AEM Page Editor waarbij de toetsenbordfocus onverwachts wordt teruggezet op het begin van de demografische werkbalk nadat knoppen zoals Persona, Kaart of Verlaten zijn geactiveerd. De geactiveerde knop blijft nu geactiveerd om consistente workflows voor toetsenbordnavigatie en schermlezers te ondersteunen. (SITES-25306)
* Probleem met koppeling van toegankelijkheidslabel voor paginatitel- en -tagvelden opgelost. De AEM-interface koppelt toegankelijkheidslabels nu correct aan de velden Titel en Paginatitel wanneer schermlezers worden gebruikt, zoals JAWS. Met deze correctie wordt een correcte aflezing van labels gegarandeerd en wordt de ADA-compatibiliteit verbeterd voor het maken van pagina&#39;s, eigenschappen en workflows verplaatsen. (SITES-27149)
* Het ontbrekende visuele label voor invoervelden voor opmerkingen in de tijdlijn is gecorrigeerd. Ontbrekende visuele labels voor invoervelden voor &quot;opmerkingen&quot; zijn gecorrigeerd in de tijdlijnsectie om de toegankelijkheid te verbeteren. De update zorgt ervoor dat schermlezers de veldlabels correct kunnen aankondigen. Deze ervaring verbetert de navigatie en verzending van formulieren voor alle gebruikers, in het bijzonder gebruikers die op ondersteunende hulpmiddelen vertrouwen. (SITES-26903)
* Toegankelijkheid met toetsenbord voor knop met ovaal in tijdlijnopmerkingen gecorrigeerd. Toetsenbordnavigatie ingeschakeld voor de elliptische knop (drie punten) naast opmerkingen onder de tijdlijnsectie. Gebruikers kunnen nu toegang krijgen tot de knop en communiceren met de Tab-toets, waardoor de toegankelijkheid voor gebruikers die alleen op het toetsenbord navigeren, wordt verbeterd. (SITES-26891)
* Verbeterde aankondigingen van NVDA/Narrator voor zoekresultaten in selectievalken. Het dialoogvenster Selectie openen is bijgewerkt om aan te kondigen of zoekresultaten worden gevonden bij gebruik van schermlezers, zoals NVDA of Narrator. Deze verbetering helpt gebruikers die op hulptechnologieën vertrouwen het resultaat van hun onderzoeksacties begrijpen zonder visuele bevestiging te hoeven. (SITES-26883)
* Correcte ARIA-rol voor weglatingspictogram naast veld voor invoer opmerking. Het pictogram met de ellips (drie punten) naast het invoerveld voor opmerkingen is bijgewerkt om de juiste ARIA-rol te gebruiken, zodat schermlezers het element nauwkeurig kunnen identificeren. Deze verbetering verbetert toegankelijkheids naleving en verbetert de ervaring voor gebruikers die zich op hulptechnologieën baseren. (SITES-26881)
* Ongeldige ARIA-kenmerken gecorrigeerd in Coral UI-componenten. Bijgewerkte Coral UI-componenten om ervoor te zorgen dat alle ARIA-kenmerken geldige waarden gebruiken, waardoor de compatibiliteit met toegankelijkheid wordt verbeterd. Er zijn vooral gevallen opgelost waarin ongeldige waarden zoals `aria-modal="dialog"` onjuist werden toegewezen. Dankzij deze verbetering kunnen schermlezers dialoogvensterelementen correct interpreteren, waardoor de toegankelijkheid voor gebruikers die op ondersteunende hulpmiddelen vertrouwen, wordt verbeterd. (SITES-26873)
* Verbeterde zichtbaarheid en knopinfo voor pictogrammen in scenario&#39;s voor opnieuw plaatsen. Verbeterde het gedrag van de Terugvloeiing om tooltips vertoning correct voor **Download** te verzekeren, **activa** opnieuw verwerken, en **uitcheckpictogrammen**. Gericht op een toegankelijkheidsprobleem waarbij pictogrammen en hun labels onzichtbaar werden toen de zoominstellingen van de viewport werden gewijzigd of gewijzigd. Deze correctie ondersteunt gebruikers met een laag gezichtsvermogen door de zichtbaarheid te behouden en juiste pictogrambeschrijvingen te bieden tijdens het opnieuw plaatsen. (SITES-26871)


#### Gebruikersinterface van Admin{#sites-adminui-65-lts-sp1}

* Probleem verholpen waarbij JAWS geen lijstrollen aankondigde of navigatie- en activeringsinstructies gaf in het dialoogvenster Site maken. (SITES-30661)
* De ondersteuning van schermlezers voor statusberichten in de filterweergave Sites werkt zoals u had verwacht, zodat gebruikers duidelijke en tijdige feedback krijgen wanneer ze van mening veranderen. (SITES-24992)
* De Datumkiezer in de Filters Rail wordt volledig weergegeven in de bijbehorende container, zodat u over de juiste grootte van het aanraakdoel beschikt en er geen uitknipproblemen optreden. (SITES-24988)
* Geselecteerde filterlabels gebruiken nu semantische HTML- en aria-labels die overeenkomen met de visuele presentatie, zodat u over nauwkeurige rolondersteuning en duidelijke acties voor ondersteunende hulpmiddelen beschikt. (SITES-24980)
* Er is een aria-labelkenmerk toegevoegd aan het gebied References Rail om een uniek, beschrijvend label voor schermlezers te bieden en een consistente landmerkidentificatie op de pagina te garanderen. (SITES-24973)
* De referentierail is bijgewerkt om relatieve eenheden te gebruiken voor het vergroten/verkleinen en positioneren, zodat inhoud kan worden geschaald en volledig functioneel blijft wanneer wordt ingezoomd op 400% op een viewport van 1280x1024. (SITES-24972)
* De bevestigde lijstelementen in de Mening van de Lijst van de Pagina van Plaatsen van het Huis bevatten juiste kolomkoprollen, toelatend schermlezers om kopballen voor elke gegevenscel aan te kondigen. (SITES-24942)
* NVDA kondigt nu de Gewijzigde datum in de Folder van de Boom aan, die ervoor zorgt dat de gebruikers van de schermlezer volledige informatie van activadetails ontvangen. (SITES-24782)
* De NVDA-schermlezer kondigde onvolledige tekst aan voor items in de structuurmapcomponent in AEM Sites. Dit probleem is nu opgelost. De NVDA leest nu volledige tekst voor elk punt, verbeterend toegankelijkheid en naleving. (SITES-24780)
* Toetsenbordtoegankelijkheid toegevoegd aan de Windows-splitser in de structuurmap, zodat gebruikers de linkerzijbalk alleen met een toetsenbord kunnen vergroten of verkleinen. (SITES-24779)
* De bijgewerkte resultaten van het het menuonderzoek van de Hulp om correcte rollen ARIA voor lijstpunten te omvatten, ervoor zorgen de schermlezers verbindingen behoorlijk voor betere toegankelijkheid aankondigen. (SITES-24729)
* Probleem verholpen waarbij schermlezers het statusbericht &quot;X of Y results&quot; niet aankondigden. U kunt ook het bericht &quot;Geen resultaten gevonden&quot; weergeven nadat u filters hebt toegepast in het deelvenster Sites-filter. Zo weet u zeker dat de resultaten correct worden bevestigd. (SITES-24720)
* Ontbrekende roltoewijzingen voor navigatiekoppelingen in de App-navigatie zijn gecorrigeerd. Toegevoegde geschikte ARIA-rollen om ervoor te zorgen dat schermlezers navigatie-elementen correct herkennen en aankondigen. (SITES-24719)
* Onjuiste rasterrolopmaak voor geselecteerde filtercodes is vervangen door knopelementen en toegevoegde namen, zodat schermlezers de tags correct kunnen aankondigen en identificeren. (SITES-24717)
* Aankondigingen van schermlezers toegevoegd voor het statusbericht References Rail wanneer u meerdere selecties uitvoert, zodat gebruikers bevestiging van wijzigingen ontvangen. (SITES-24678)
* Het gedrag van het zoekveld is gecorrigeerd, zodat het eerste resultaat niet automatisch wordt aangekondigd. Schermlezers kondigen nu het aantal gevonden resultaten aan, waardoor gebruikers zonder onjuiste focusberichten door de lijst kunnen navigeren. (SITES-24658)
* Onjuiste `aria-label` -kenmerken uit niet-interactieve statische elementen in de lijstweergave zijn verwijderd om te voorkomen dat schermlezers misleidende of irrelevante informatie bekendmaken. (SITES-24515)
* Het selectievakje in de eerste kolom van de lijstweergave is bijgewerkt zodat de tekst in de kolom Titel wordt gebruikt voor de toegankelijke naam. Hierdoor kunnen schermlezers het doel van het formulierveld nauwkeurig aangeven. (SITES-24514)
* De juiste ARIA-kenmerken en ondersteuning voor live regio&#39;s zijn toegevoegd om aan te kondigen dat statusberichten voor het laden naar schermlezers worden verzonden wanneer deze door inhoud navigeren. (SITES-24481)
* Bijgewerkt responsief ontwerp om horizontaal schuiven te elimineren wanneer inhoud wordt ingezoomd op 400% met een viewport breedte van 1280×1024, waardoor volledige zichtbaarheid zonder zijschuiven wordt gegarandeerd. (SITES-24308)
* Correcte focusnavigatie in de gebruikersinterface van Sites Admin om een logische volgorde te volgen, waarbij de focus op de knop Alles selecteren wordt geretourneerd nadat op Esc is gedrukt en nadat de focus naar het volgende interactieve element is verplaatst nadat op Tab is gedrukt. (SITES-24307)
* De bijgewerkte focusvolgorde in de gebruikersinterface van Sites Admin zodat de knop breadcrumbs in het `<betty-titlebar-title>` -element tijdens toetsenbordnavigatie focus krijgt in de juiste volgorde. (SITES-24305)
* De geverifieerde functionaliteit voor het overslaan van koppelingen zorgt ervoor dat de toetsenbordfocus naar het hoofdinhoudsgebied wordt verplaatst, zodat gebruikers van het toetsenbord koptekstelementen kunnen omzeilen en op efficiënte wijze toegang kunnen krijgen tot inhoud. (SITES-24061)


#### Klassieke gebruikersinterface{#sites-classicui-65-lts-sp1}

Probleem verholpen in de klassieke gebruikersinterface waarbij selectievakjes ontbraken en HTML als gecodeerde tekst werd weergegeven in meerdere UI-elementen, waaronder Datumzoekfunctie en niet-standaardinterfaces. (SITES-31822)

#### [!DNL Content Fragments]{#sites-contentfragments-65-lts-sp1}

AEM voorkomt nu prestatievermindering die wordt veroorzaakt door onjuist gevormde XMP-metagegevens in afbeeldingselementen. Assets die ongeldige of niet-compatibele XMP-eigenschapsnamen bevatten, zoals die met numerieke segmenten of ongekwalificeerde structuren, activeren niet langer herhaalde waarschuwingslogboeken tijdens de verwerking. Het systeem filtert problematische meta-gegevens uit om ervoor te zorgen dat de opname en de bevestiging van activa zonder fouten volledig zijn. (SITES-30683)

<!--
#### [!DNL Content Fragments] - Admin{#sites-admin-65-lts-sp1} -->

#### [!DNL Content Fragments] - Fragmenteditor{#sites-fragments-editor-65-lts-sp1}

Andere auteurs kunnen nog steeds Content Fragments publiceren, zelfs wanneer een andere auteur ze uitcheckt. Dit is in strijd met het beoogde gedrag van de uitcheckfunctie. Deze correctie voorkomt dat andere gebruikers de publicatieknoppen in de ontwerpinterface zien of gebruiken wanneer een inhoudsfragment wordt uitgecheckt. (SITES-30578)

<!--
#### [!DNL Content Fragments] - GraphQL API {#sites-graphql-api-65-lts-sp1}

#### [!DNL Content Fragments] - GraphQL Query Editor{#sites-graphql-query-editor-65-lts-sp1}

#### [!DNL Content Fragments] - REST API{#sites-restapi-65-lts-sp1} -->

#### Component Console{#sites-component-console-65-lts-sp1}

Probleem verholpen in de component van de Lijst van het Product waar &quot;Uitgezochte Al&quot;checkbox slechts de eerste 20 SKUs van de aanvankelijke pagina in plaats van alle SKUs in de onderzoeksresultaten toevoegde. (SITES-29191)

#### Core-backend{#sites-core-backend-65-lts-sp1}

Bij onjuist opgemaakte XMP-metagegevens is een fout opgetreden tijdens het verwerken van afbeeldingselementen in de `ValidationDataServlet` . Deze correctie zorgt voor compatibele verwerking van metagegevens en voorkomt overbodige parsering van ongeldige eigenschappen. (SITE-30683)

<!--
#### Core Components{#sites-core-components-65-lts-sp1}

#### Campaign integration{#sites-campaign-integration-65-lts-sp1}

#### Experience Fragments{#sites-experiencefragments-65-lts-sp1}

#### Foundation Components (Legacy){#sites-foundation-components-legacy-65-lts-sp1}

#### Launches{#sites-launches-65-lts-sp1}

#### Link Checker{#sites-link-checker-65-lts-sp1} -->

#### MSM - Actieve kopieën{#sites-msm-live-copies-65-lts-sp1}

* Oplossing voor een JavaScript-fout `ns.ui.alert is not a function` die optrad bij het opnieuw inschakelen van de overerving van spookcomponenten in AEM 6.5 On-prem. (SITES-31993)
* Probleem verholpen waarbij de optie Uitvoeren &quot;Later&quot; doorging zonder een datum te selecteren in AEM 6.5. (SITES-31374)

#### Paginaeditor{#sites-pageeditor-65-lts-sp1}

* Oplossing voor een probleem in de Teaser Modal waarbij op het tabblad Koppelingen en handelingen de opmaak van fouten, pictogrammen en het kenmerk aria-ongeldig na een geldige gegevensinvoer en foutresolutie werden weergegeven. (SITES-25527)
* Probleem verholpen in de tekstredacteur van het Modaal van de Taser Modus waar de lijsten en de knopen van Alinea hun uitgevouwen of doen ineenstorten staat niet overbrengen aan het schermlezers, die nauwkeurige a.u.b. controleren-uitgebreide kenmerkupdates verzekeren. (SITES-25365)
* Probleem verholpen in de werkbalk Demografie waarbij de schuifregelaar Illustratie met toetsenbordinvoer de focus naar de knop Illustratie verplaats in plaats van de focus op de schuifregelaar, waardoor de navigatieefficiëntie voor toetsenbordgebruikers wordt verbeterd. (SITES-25324)
* Een toegankelijke naam toegevoegd aan de schuifregelaar Illustratie in de werkbalk Demografische gegevens door een waarde toe te wijzen aan het bijbehorende element `<label>` . Deze oplossing verbetert de compatibiliteit met ondersteunende hulpmiddelen en verbetert de bruikbaarheid voor schermlezers. (SITES-25322)
* Toegevoegde ARIA-rollen en toegankelijke namen aan knoppen in het vervolgkeuzemenu van de werkbalk Demografie. Met deze correctie konden gebruikers van het toetsenbord en de schermlezer naar behoren worden geïdentificeerd met behulp van ondersteunende hulpmiddelen en verbeterde navigatie. (SITES-25315)
* De indeling van de demografische werkbalk is aangepast om te voorkomen dat de inhoud bij een zoompercentage van 200% buiten de viewport loopt. Op deze manier blijven alle besturingselementen toegankelijk zonder horizontaal schuiven. (SITES-25309)
* Correct focusbeheer in de demografische werkbalk om de toetsenbordfocus op de geactiveerde knop te houden in plaats van de focus opnieuw in te stellen op de startpositie van de werkbalk. (SITES-25306)
* De knoplabel overlappen functies die zijn ontworpen met knopinfo om het label weer te geven wanneer modi met vergelijkbare schermbreedten actief zijn. (SITES-25285)
* Het annotatiemodel bevat een knop voor het verzenden van een afbeelding, waarmee gebruikers annotaties kunnen verzenden zonder op de toets Escape te vertrouwen of buiten het modale pad te klikken. (SITES-25281)
* Het annotatiemodaal bevat een knop voor het penpictogram waarmee gebruikers annotaties kunnen verzenden en waarmee een duidelijke en toegankelijke verzendmethode wordt geboden. (SITES-25269)
* Gecorrigeerde schermlezeraankondigingen voor de knoppen Annoteren en Annoteren sluiten om nauwkeurige, relevante feedback te geven en niet-gerelateerde of verwarrende informatie te verwijderen. (SITES-25268)
* Canvassecties in AEM Editor-pagina&#39;s bieden nu ondersteuning voor volledige toetsenbordtoegankelijkheid. Gebruikers kunnen sectitels activeren en knoppen bewerken met alleen het toetsenbord, zonder de muisaanwijzer te hoeven aanwijzen. Deze update zorgt voor compatibiliteit met WCAG 2.1.1 en verbetert de bruikbaarheid in verschillende componenten (zoals de modi Taser, Image, Carousel, Layout, Timewarp en Annotation). (SITES-25256)
* U hebt overbodig horizontaal schuiven in de Carousel-module met een breedte van 320 px verwijderd om ervoor te zorgen dat alle inhoud wordt weergegeven in de viewport zonder dat navigatie van de ene naar de andere laag vereist is. (SITES-25254)
* Er is overbodig horizontaal schuiven in de afbeeldingsmodule met een breedte van 320 px verwijderd om ervoor te zorgen dat alle inhoud wordt weergegeven in de viewport zonder dat navigatie van de ene naar de andere zijde nodig is. (SITES-25244)
* Overbodig horizontaal schuiven in de teasmodus met een breedte van 320 px is verwijderd om ervoor te zorgen dat alle inhoud wordt weergegeven in de viewport zonder dat navigatie van de ene naar de andere zijde nodig is. (SITES-25242)
* Toetsenbordnavigatie ingeschakeld voor het pop-upmenu `List` en `Paragraph Format` , beide in de Taser Modal. Met deze correctie hebben gebruikers toegang tot deze menu&#39;s en kunnen ze door deze menu&#39;s navigeren met de pijltoetsen. (SITES-25235)
* Gecorrigeerde schermlezeraankondigingen voor de knoppen Annoteren en Annotatie sluiten om nauwkeurige, relevante feedback weer te geven die is uitgelijnd met de bijbehorende acties. (SITES-25234)
* Verbeterde het knoopetiket van de Hulp in de Modal van de Teaser om zijn doel duidelijk te beschrijven en betekenisvolle context voor alle gebruikers, met inbegrip van hulptechnologiegebruikers te verstrekken. (SITES-25224)
* De emulatorliniaal voor schermlezers is verbeterd doordat liniaalmetingen worden gekoppeld aan hun respectievelijke apparaten. Ook, die tooltip met een aria-beschrijft element vervangen. (SITES-24955)
* Er is geen oplossing geïmplementeerd omdat de knop Bewerken naar behoren functioneert en een informatieve context biedt in plaats van een handeling uit te voeren. (SITES-24950)
* De bevestigde focusvolgorde op de Editor-pagina volgt een logische volgorde, zodat gebruikers door alle interactieve elementen kunnen navigeren zonder dat ze onverwachts hoeven te worden overgeslagen of herhaald. (SITES-24937)
* Met het canvas met de modus Bevestigde voorvertoning wordt de tekstafstand correct bijgewerkt wanneer gebruikers aangepaste instellingen voor de tekstspatiëring toepassen, zodat de opmaak in alle inhoudsgebieden consistent is. (SITES-24936)
* De geverifieerde knop Voorvertoning activeert niet langer de focus voor context- of statuswijzigingen, zodat gebruikers de knop bewust activeren voordat de paginaweergave wordt bijgewerkt. (SITES-24784)
* Correcte ARIA-roltoewijzingen toegevoegd aan App-navigatiekoppelingen, zodat schermlezers navigatie-items nauwkeurig kunnen identificeren en aankondigen voor betere toegankelijkheid. (SITES-24718)
* De knop Filters wijzigen is bijgewerkt om de uitgevouwen en samengevouwen statussen aan schermlezers aan te kondigen, overbodige ARIA-kenmerken te verwijderen en de labels aan te passen en duidelijke, niet-dubbele beschrijvingen te geven. (SITES-24713)
* Aankondigingen van schermlezers voor de statusberichten van zoekresultaten in het dialoogvenster Koppeling. Zo weet u zeker dat gebruikers een bevestiging ontvangen wanneer de resultaten zijn geladen of er geen overeenkomsten zijn gevonden. (SITES-24700)
* Aankondigingen van schermlezers voor de laadstatus van Image Modal, zodat gebruikers feedback krijgen wanneer het modaal wordt geladen en klaar zijn voor interactie. (SITES-24697)
* Oplossing voor een toegankelijkheidsprobleem waarbij de plakkoptekst de Teaser Modal-inhoud verduisterde met een zoompercentage van 200% en 400%, zodat u de pagina volledig kunt zien en gebruiken met vergroting van de pagina. (SITES-24523)
* Er is een statusbericht met het aantal zoekresultaten toegevoegd aan het veld Zoeken/Filter, zodat schermlezers de resultaten kunnen bekendmaken aan gebruikers. (SITES-24506)
* Aankondigingen van schermlezers toegevoegd voor het aantal zoekresultaten in het veld Zoeken/Filter, zodat gebruikers direct feedback ontvangen wanneer de resultaten worden geladen. (SITES-24505)
* Er is een toegankelijke naam toegevoegd aan de tablijst in het deelvenster Zijspoor, zodat schermlezers hun doel kunnen aankondigen in overeenstemming met de WAI-ARIA-richtlijnen. (SITES-24492)
* Er zijn beschrijvende labels toegevoegd aan dubbelzinnige editorpictogrammen, zodat alle gebruikers de functie van elke knop duidelijk begrijpen. (SITES-24480)
* Volledige toetsenbordtoegankelijkheid voor sectitels en actieknoppen in de weergave Canvas ingeschakeld, zodat gebruikers met de muis en het toetsenbord consistent kunnen werken. (SITES-24479)

<!--
#### Replication{#sites-replication-65-lts-sp1}

#### Rich Text Editor{#sites-rte-65-lts-sp1} -->

#### Universele editor {#sites-universal-editor-65-lts-sp1}

* Vaste een rasvoorwaarde in QueryTokenService die slechte logins veroorzaakte wanneer de veelvoudige verzoeken met vraagparameters die vóór de login-symbolische dienst werden teweeggebracht een resultaat terugkeerde. (SITES-30659)
* Probleem verholpen in UniversalEditorURLService waarbij bij het opslaan van een array van toegewezen paden in Felix ConfigMgr alleen het eerste item behouden bleef. (SITES-30292)

### [!DNL Assets]{#assets-65-lts-sp1}

Probleem verholpen waarbij door het synchroniseren van elementen van externe DAM naar lokale AEM Sites de gepubliceerde status en eigenschappen met betrekking tot replicatie werden verwijderd uit elementen. (Assets-48958)

<!--
#### [!DNL Dynamic Media]{#assets-dm-65-lts-sp1}

#### [!DNL Dynamic Media] - Hybrid Mode {#assets-dm-hybrid-65-lts-sp1}



### [!DNL Forms]{#forms-65-lts-sp1}


#### Forms Designer 

#### Forms

#### Forms JEE 
 
#### Forms Captcha {#forms-captcha-65-lts-sp1} 

#### XMLFM {#forms-xmlfm-65-lts-sp1}

#### [!DNL Adaptive Forms] {#adaptive-forms-65-lts-sp1}

#### [!DNL Forms Designer] {#forms-designer-65-lts-sp1} -->



### Stichting {#foundation-65-lts-sp1}

<!--
#### Apache Felix {#foundation-apachefelix-65-lts-sp1}

#### Campaign{#foundation-campaign-65-lts-sp1}

#### Cloud Services{#foundation-cloudservices-65-lts-sp1}



#### Communities {#foundation-communities-65-lts-sp1}

#### Content distribution{#foundation-content-distribution-65-lts-sp1}

#### CRX {#foundation-crx-65-lts-sp1}

#### Granite{#foundation-granite-65-lts-sp1} -->

#### HTL{#foundatoin-htl-5-lts-sp1}

Oplossing voor OSGi gebiedingscycli die de fabriek van de HTML manuscriptmotor van het functioneren blokkeerden, die correcte de dienstresolutie en manuscriptuitvoering verzekerde. (Graniet-58275)

#### Integrations{#foundation-integrations-65-lts-sp1}

* Het gebruik van commons-httpclient 3.x is uit de `com.adobe.cq.cq-analytics-integration` -bundel verwijderd en vervangen door `org.apache.httpcomponents.httpclient` 4.5.13.B0001 om deze aan te passen aan de nieuwste AEM 6.5 LTS-standaarden. (CQ-4360586)
* De vervangen zoek&amp;Bevorder integratiepakket uit AEM verwijderd om ongebruikte onderdelen te verwijderen en de overhead op het gebied van onderhoud te verminderen. (CQ-4358030)
* Er zijn nieuwe back-endtestgevallen toegevoegd voor de integratie van SiteCatalyst om de validatie van analysemogelijkheden te verbeteren en een uitgebreidere dekking te garanderen. (CQ-4359991)
* Oplossing voor een probleem in de sectie Eigenschappen van configuratie starten waarin de vervolgkeuzelijst Bedrijf en Eigenschap niet werd weergegeven. Ook, sparen en Sluiten teweegbrachten fouten ondanks alle verplichte gebieden die, en onjuiste foutenmeldingen voor Bedrijf en Bezit worden getoond wanneer slechts het gebied van de Titel leeg was. (CQ-4359853)
* De vermelding voor het `searchpromote` servlet-pad is verwijderd uit versie 6.6 en uitgelijnd met de verwijdering van de bundel Zoeken&amp;Promoten. (CQ-4359523)
* Correctie van HTTP-testgevallen voor de Target-gegevensopslagplaats om nauwkeurige validatie en verbeterde betrouwbaarheid van de test te garanderen. (CQ-4359022)
* Het gebruik van Guava-caching is verwijderd uit de module integration-adobeims-console om te voorkomen dat Guava-bibliotheekafhankelijkheden ontstaan. (CQ-4358710)
* Gevalideerde DTM-integratieworkflows, inbox-taken en projectfunctionaliteit in AEM 6.6 voor een correcte werking in AEM 6.5. (CQ-4358151)
* De gevalideerde Insight-functionaliteit voor inhoud in AEM 6.6 zorgt voor compatibiliteit en correcte werking in AEM 6.5. (CQ-435774)
* Validated Cloud Services functionaliteit in AEM 6.6 om compatibiliteit en correcte werking in AEM 6.5 te garanderen. (CQ-435773)
* De gevalideerde integratie van Adobe IMS Console in AEM 6.6 zorgt voor compatibiliteit en correcte werking in AEM 6.5. (CQ-4357772)
* De bijgewerkte pijpleiding Jenkins voor de Test&amp;Target integratie om op Java 17 te lopen, het ontbreken tests van Selenium op te lossen, uitgezochte tests te bewegen aan Playwright, en alle eenheidstests te verzekeren slagen. (CQ-4357770)
* Uitgelijnde DX-integratie, -workflow, -inbox en -projecten met de 6.6.0-vertakking door het bijwerken van build- en testpijpleidingen. Ook, het oplossen van de kwesties van de verbeteringsverenigbaarheid, en het bevestigen van alle beïnvloede diensten voor stabiliteit en functionaliteit. (CQ-4357767)

<!--
#### Jetty{#foundation-jetty-65-lts-sp1} -->

#### Lokalisatie{#foundation-localization-65-lts-sp1}

* De tekenreeksen zijn gelokaliseerd in het dialoogvenster Toegangsbeheer verwijderen in de lijst &quot;Machtigingen&quot; om de juiste vertalingen weer te geven. (GRANITE-59427)
* Probleem verholpen met de optie ‘Of Eigenschappen splitsen’ in het dialoogvenster Regel toevoegen van de modeleditor, waarbij meerdere UI-tekenreeksen, inclusief operatoren en veldlabels, niet-gelokaliseerd werden weergegeven. Alle tekenreeksen worden nu weergegeven met de juiste lokalisatie. (CQ-4354/014)
* Ontbrekende vertaling toegevoegd voor de knopinfo &#39;Beschrijving tonen voor&#39; in het dialoogvenster Workflowmodellen bewerken. (CQ-4347996)

#### Oak {#foundation-oak-65-lts-sp1}

Probleem opgelost waarbij AEM tijdens upgrades bestaande configuratiebestanden onder `/apps/system/config` opnieuw heeft gemaakt of de naam ervan heeft gewijzigd en `.cfg.json` bestanden vervangt door `.config` bestanden. (GRANITE-58899)

#### Omnissearch{#foundation-omnisearch-65-lts-sp1}

Probleem verholpen waarbij plaatsaanduidingen onjuist werden weergegeven als labels voor invoervelden. Dit probleem leidt tot ontbrekende veldlabels in Zoeken, AEM Experience Fragments, Content Fragments en Content Fragment Models. (Graniet-61791)

<!--
#### Platform{#foundation-platform-65-lts-sp1} -->

#### Projecten{#foundation-projects-65-lts-sp1}

* Oplossing voor een probleem dat een onjuiste fout pop-up wanneer het schrappen van een project in de mening van de Kalender, ondanks succesvolle projectreductie toonde. (CQ-4358890)
* Probleem verholpen waarbij de voettekst van de kaart &quot;Asset Collection&quot; in de projectweergave de kaartrand overlapte. De voettekst wordt nu correct uitgelijnd zonder overlapping. (CQ-4353317)

#### QuickStart{#foundation-quickstart-65-lts-sp1}

* Het verwijderscript is bijgewerkt om het versiebereik voor de Guava-bundel aan te passen, zodat deze niet kan worden gevoegd op lijst van gewenste personen wanneer deze via Package Manager wordt geïnstalleerd. (GRANITE-5959)
* Oplossing voor een kwestie in de UI van de Replicatie die een fout (`#1660`) toonde toen het uitgeven van replicatieagenten door de behandeling van klassieke controledozen in de interface te verbeteren. (GRANITE-58302)
* Oplossing van veelvoudige startfouten voor S3 datastore wanneer het runnen van AEM 6.5 LTS met JDK 21 door ontbrekende de diensttoestemmingen te richten, configuratie behandeling bij te werken, en de vereiste diensten te verzekeren initialiseert correct. (GRANITE-57082)
* De onderhouds- en onderhoudsstrategie voor AEM 6.5. Deze correctie omvatte het volgende:
   * Service Pack-cadence.
   * Hotfix-cadence.
   * Parallelle ondersteuning met AEM 6.6.
   * Bijgewerkte ondersteuningsmatrix.
   * Verantwoordelijkheden van invoegtoepassingen. (GRANITE-50459)

<!--
#### Security{#foundation-security-65-lts-sp1} -->

#### Sling{#foundation-sling-65-lts-sp1}

* Bijgewerkte Sling ResourceAccessSecurity naar versie 1.1.2 om een `ClassCastException` op te lossen die optrad wanneer meerdere `ResourceAccessGate` references initialized `ResourceAccessSecurityImpl` waren. (NPR-42750)
* Probleem verholpen waarbij het dialoogvenster Licentie grijs werd weergegeven tijdens het integreren met Adobe Stock. Dit probleem is ontstaan doordat de functie `sunt:initList` vereiste invoervelden heeft verwijderd. De functie is gevonden in de clientbibliotheken van de Coral Foundation. De clientbibliotheken zijn bijgewerkt om de benodigde velden te behouden en de functionaliteit van het licentiedialoogvenster is nu juist. (NPR-42748)
* De oplossing voor het probleem Sling Scripting die tijdens de pakketinstallatie tot uitzonderingen `DataTimeParseException` en `String.length()` null pointer was geleid, is nu opgelost. Bijgewerkte het Schrappen van het Schrappen aan versie 2.8.3 - 1.0.10.6 om installatiefouten te verminderen en stabiliteit te verbeteren. (NPR-42640)

<!--
#### Translation{#foundation-translation-65-lts-sp1} -->

#### Gebruikersinterface{#foundation-ui-65-lts-sp1}

* Probleem opgelost in de gebruikersinterface van AEM-auteur waarbij de weergave van gebruikersgroepen werd beperkt tot 41. Dit probleem is het gevolg van een standaardbatchlimiet in de selectieve UI-groepskiezer. De component is bijgewerkt en alle groepen zonder afkapping weergegeven. (NPR-42749)
* Correctie van het probleem in de wizard Pagina&#39;s maken op prem waarbij vereiste velden in componenten met meerdere velden niet opnieuw werden gevalideerd tijdens het bewerken van pagina-eigenschappen. Hierdoor konden auteurs de validatie omzeilen en onvolledige gegevens verwerken. (GRANITE-58826)
* Correcteerde ARIA-kenmerken voor de Help-knop in AEM om ervoor te zorgen dat JAWS-schermlezers een duidelijk, gebruiksvriendelijk label aankondigen in plaats van onvertaalde pictogrammen en tekstmetagegevens weer te geven. (GRANITE-55360)

#### WCM{#foundation-wcm-65-lts-sp1}

* Toegevoegde Java 17-ondersteuning voor AEM-vertalingen door het bijwerken van vertaalbundels, het controleren van compatibiliteit met Java-pakketten, het verwijderen van verouderde afhankelijkheden en het garanderen van volledige functionaliteit door uitgebreide tests. (CQ-4357525)
* De zwarte Evergreen-test `com.adobe.cq.platform.it.http.workflow.inbox.InboxOnOffTimeIT.testActivateLater` is verwijderd om fout-fouten tijdens de automatische test te voorkomen. (CQ-4298376)

#### Workflow{#foundation-workflow-65-lts-sp1}

* Het kenmerk missing `data-detailsurl` is toegevoegd in items in het Postvak IN om te voorkomen dat ongedefinieerde waarden in URL&#39;s verschijnen wanneer AEM 6.5 LTS met Java 21 wordt gebruikt. (GRANITE-60158)
* Probleem verholpen met een NullPointerException in de `deactivate` -methode van de `WorkflowToPublishEventService` -bundel wanneer AEM 6.5 LTS wordt uitgevoerd met Java 21. Hierdoor wordt de workflowservice correct afgesloten zonder fouten. (GRANITE-58151)
* Bijgewerkt de werkschemaindex om het delen, out-of-office aanpassing, en resolutie van chronologie vraagkwesties te steunen. (GRANITE-52640)
* De workflowindex is bijgewerkt met ondersteuning voor delen, aanpassingsfuncties buiten het kantoor en het oplossen van problemen met tijdlijnquery&#39;s. (GRANITE-52294)
* Oplossing voor verhoogde fouten van het foutenlogboek tijdens logboekvergelijkingsbevestiging voor een programmaverbetering aan AEM versie 10912, die stabiele werkschemauitvoering verzekerde. (GRANITE-44268)
* De URL-ontsmettingsmethode is bijgewerkt in Workflowrapporten, zodat `url.searchParams` wordt vervangen door `url.search` . Hierdoor wordt de XSS-beveiliging voor kwetsbare URL&#39;s verbeterd. (CQ-4359585)
* De gevalideerde workflow, inbox en projectfunctionaliteit in AEM 6.6 Forms voor een correcte werking en integratie. (CQ-4358777)
* Geïmplementeerde automatisering voor het vrijgeven van workflowcontent-artefacten via Jenkins, waardoor gestroomlijnde en consistente implementatieprocessen in AEM 6.5 mogelijk zijn. (CQ-4358472)
* Probleem verholpen in de werkstroom Taak maken van Postvak In waarin het dialoogvenster Taak toevoegen niet werd gesloten nadat op Verzenden werd geklikt, ondanks de taak die werd gemaakt, als gevolg van een syntaxisfout van JavaScript. (CQ-4355336)
* Oplossing voor een probleem dat het opslaan van de configuratie van de Postvak In-weergave verhinderde omdat de eigenschapdefinitie voor `isEndUserConfigurationEnabled` ontbreekt. (CQ-4287757)

## Forms

### Forms Designer

* Wanneer een gebruiker de gegevens voor een op XFA gebaseerde PDF exporteert met behulp van de exportDataAPI, toont de resulterende XML discrepanties in vergelijking met de XML-gegevens die handmatig worden geëxporteerd met behulp van Acrobat Reader. De waarden van sommige velden ontbraken in de uitvoer in vergelijking met de uitvoer van Acrobat Reader. (LC-3922791)
* Als u een gelabelde PDF genereert met de Uitvoerservice in Workbench, wordt een onverwachte labeltag toegevoegd onder de referentietag in een inhoudsopgave-item. (LC-3922756)
* Bij het afvlakken van dynamische, invulbare PDF&#39;s naar de PDF/A-indeling met de Output Service, blijft de dynamische status niet behouden. Dit leidt tot gegevensverlies en potentiële nalevingsproblemen, vooral wanneer het etiketteren wordt toegelaten. (LC-3922708)
* Wanneer een gebruiker bijschriften van velden met de uitlijning onder of rechts uitlijnt in AEM Forms Designer, bevat de codestructuur alleen het bijschrift zonder de bijbehorende waarde. Dit leidt tot onvolledige toegankelijkheidscodes. (LC-3922619)
* De QR-codes in gegenereerde PDF&#39;s kunnen niet meer worden gelezen. De alternatieve tekst voor de QR-codes mislukt ook toegankelijkheidstests, wat van invloed is op de compatibiliteit van schermlezers. (LC-3922551)
* Wanneer een gebruiker een brief in Agent UI teruggeeft, ontbreekt de inhoud correct om te tonen toe te schrijven aan FormService render () API. (LC-3922461)
* Wanneer een gebruiker PDF/A-bestanden probeert te maken van XDP&#39;s met de stijl Verzonken vierkant in AEM Forms, levert dit problemen op bij het renderen van randen. (LC-3922180)
* Het afvlakken van dynamische formulieren die zijn gebonden aan een XSD-schema leidt tot gedeeltelijk gegevensverlies, omdat bepaalde gebonden formuliergegevens niet behouden blijven in de uiteindelijke PDF. (LC-392/08)
* Wanneer een gebruiker gegevens uit interactieve PDF&#39;s probeert te exporteren met de extractieData-API in AEM Forms 6.5.13 en latere versies, resulteert dit in ontbrekende gegevens in vergelijking met handmatig exporteren. (LC-3921983)
* Gebruikers hebben te maken met een compatibiliteitsprobleem met betrekking tot toegankelijkheid waarbij meerdere Link-OBJR-codes worden gemaakt bij de conversie van XDP-formulieren naar statische PDF&#39;s met AEM Forms Designer of Output-service, in plaats van één enkele koppelingstag te maken. (LC-392/1977)

### Adaptieve Forms

* Als u in AEM Forms de optie &#39;RTF-tekst toestaan voor titel&#39; inschakelt in het hoofddeelvenster, wordt de titel &#39;Titel uitsluiten van document van record&#39; in een genest deelvenster onjuist verborgen. Dit gebeurt in het gegenereerde document of record. (FORMS-19696)
* Het systeem negeert de douane die schuine streep :resourceType door aem :afProperties in een schema JSON wordt toegewezen. Het type aangepaste bron wordt tijdens het renderen genegeerd. (FORMS-19691)
* Wanneer een gebruiker een adaptief formulier met vooraf gevulde bijlagen verzendt met behulp van URI&#39;s, mislukt het verzenden van het formulier met een NullPointerException vanwege ontbrekende binaire gegevens. (FORMS 19371) (FORMS 19486)
* Wanneer een gebruiker een PDF uploadt onder de sectie &#39;Forms en Documenten&#39;, werkt de tijdlijnfunctie niet meer. (FORMS-19407)(FORMS-19234)
* Wanneer een gebruiker bestanden uploadt met de OOTB-component (out-of-the-box) voor bestandsbijlagen in AEM Forms, worden beveiligingskwetsbaarheden geïdentificeerd. Deze kwestie leidt tot mogelijke onderschepping van het indieningsproces door onbevoegde entiteiten. (FORMS-19271)
* Wanneer een gebruiker een uit-de-doos Aangepast Vorm in AEM Forms configureert om een Document van Verslag (DoR) automatisch te produceren, toont het gebied van de &quot;Titel&quot;in de Eigenschappen van het Document van Acrobat Reader niet de gevangen Titel van DoR. Standaard wordt de titel van het formulier niet weergegeven in plaats van de bestandsnaam. (FORMS-19263)
* Wanneer een gebruiker een Interactieve Communicatie in Agent UI opent, kunnen de vooraf ingevulde gegevens niet volledig worden gewist; op verwijdering, vult het automatisch met de zelfde gegevens. (FORMS-19151)
* Wanneer een gebruiker een datumgebied in de Agent UI previews, verandert de datum onverwacht. Dit probleem doet zich voor als gevolg van verschillen in tijdzone tussen de UTC-instelling van de VM en de interpretatie van de datum door het systeem. (FORMS-1915)
* Wanneer een gebruiker een formulier verzendt, kunnen bestandsbijlagen worden gedupliceerd, wat leidt tot meerdere uploads van hetzelfde bestand. (FORMS-19045) (FORMS-19051)
* Het toevoegen van coördinatoren aan beleidssets in Documentbeveiliging mislukt in zowel de productie- als de lagere omgeving. (FORMS-18603, FORMS-18212, FORMS-19697)
* Wanneer een gebruiker in de bureaubladmodus op het pictogram &quot;datepicker-agenda-icon&quot; klikt met een leeg veld, treedt een fout op vanwege de ongedefinieerde variabele _$focusedDate, waardoor gekoppelde aangepaste scripts worden onderbroken. (FORMS-18483) (FORMS-18268)
* Wanneer een klant een voorvertoning van een letter weergeeft, worden in het veld &#39;Hoeveelheid in woorden&#39; de getalwaarden niet correct weergegeven of bijgewerkt. Dit leidt tot een onjuiste uitlijning en ontbrekende spaties in de inhoud. (FORMS-18437, FORMS-17330, FORMS-18209, FORMS-18557, CTG-4150848, FORMS-19614, LC-3922004)
* Wanneer een klant een voorvertoning weergeeft van een opgeslagen brief op RHEL, worden de inhoud verkeerd uitgelijnd, ontbreken spaties en worden onverwachte tekens zoals &#39;x&#39; weergegeven. (FORMS-18422)(FORMS-17641)
* Wanneer een gebruiker in AEM Forms tussen tabbladen navigeert, reageert het selecteren van componenten op het eerste tabblad niet meer. (FORMS-18345)
* Wanneer een gebruiker een HTML-bestand naar PDF converteert met de optie WebToPDF, ontbreekt de koptekstsectie in de uitvoer-PDF, inclusief metagegevens en titeltags. (FORMS-18223, FORMS-17835, FORMS-19642, FORMS-18224)
* Wanneer een gebruiker in AEM JEE Process Manager SDK de methode retryAction(long actionOid) aanroept, probeert het systeem ten onrechte de eerste actie in de tabel tb_action_instance. Deze workflow vindt zelfs plaats wanneer een specifieke actie-id wordt opgegeven of wanneer de id null is, wat onbedoeld gedrag tot gevolg heeft. (FORMS-18187)
* Een gebruiker vindt problemen waar het opgeslagen concept en de verzendfuncties mislukken zonder een foutbericht weer te geven. (FORMS-18069)
* De overgang van op XSD gebaseerde stichtingscomponenten aan kerncomponenten verhindert de implementatie van dwars-dossierverwijzingen in JSON- schema&#39;s, die de Adaptieve migratie van Forms beïnvloeden. (FORMS-18065)
* Wanneer een gebruiker een brief in de Agent UI previews, toont het datumgebied een onjuiste waarde toe te schrijven aan de kwesties van de tijdomzetting van IC. Deze verschillen zijn het gevolg van verschillen in tijdzone tussen de VM-omgeving en de interpretatie van de tijd van het systeem (UTC versus lokale tijd). (FORMS-17988) (FORMS-17248)
* Wanneer een gebruiker voorvertoningen van letters gebruikt gebruikend de malplaatjes van Notice IC in AEM Forms, variëren de generatietijden van PDF beduidend, van 1.5 seconden tot meer dan 10 seconden, zelfs op de zelfde server. Deze inconsistentie beïnvloedt bedrijfskritieke werkstromen. (FORMS-17951)
* Wanneer een gebruiker een voorwerp van de Handtekening van de Krabbels in een AanpassingsVorm aan XDP gebruikend de optie &quot;Gegevensbronnen&quot;bindt, kunnen de veranderingen niet worden bewaard. De reden hiervoor is dat er validatiefouten zijn met betrekking tot de permanente hoogte-breedteverhouding, zelfs als geldige waarden worden gebruikt. (FORMS-17587)
* Wanneer een gebruiker specifieke XDP met vele verborgen gebieden voor documentfragmenten gebruikt, leidt AEM tot de knopen van CRX met het cm :optional bezit dat aan vals wordt geplaatst, wat de Interactieve Communicatie (IC) voorlegging veroorzaakt om te ontbreken. (FORMS-17538)
* Wanneer een klant een voorvertoning van een letter weergeeft, worden negatieve waarden in het veld van het numerieke vak niet correct verwerkt wanneer cijferlimieten voor lead en frame zijn gedefinieerd. Dit probleem treedt op als gevolg van het gebruik van parseFloat, dat het minteken als onderdeel van het getal behandelt. (FORMS-17451)
* Wanneer een voorvertoning van een brief wordt weergegeven, wordt het gebruik van de jokerteken &quot;*&quot; in het bestand Adobe.json opgemerkt, wat aanleiding geeft tot bezorgdheid over het doel en de mogelijke wijziging ervan. (FORMS-17317)
* Wanneer een gebruiker een schermlezer gebruikt op de gezamenlijke account Toepassen voor een Vaste snelheidsbesparingsserver, worden de koppen ten onrechte als klikbaar aangekondigd, wat toegankelijkheidsproblemen veroorzaakt. (FORMS-17038)
* Wanneer een formulier wordt ingesloten, ontbreekt in het gegenereerde iframe een titelkenmerk, wat leidt tot een compatibiliteitsprobleem met betrekking tot de toegankelijkheid. (FORMS-17010)
* Het downloaden van een formulier via de gebruikersinterface van Forms Manager omvat altijd de bijbehorende afhankelijkheden, zoals thema&#39;s en fragmenten. (FORMS-15811)
* Wanneer een gebruiker het formulier opent op mobiele apparaten (iOS en Android™), worden de knoppen Volgende en Vorige op de eerste pagina uitgeschakeld. De schermlezer herkent deze echter niet als uitgeschakeld. (FORMS-15773)
* Wanneer een gebruiker een groot formulier opslaat met fragmenten en het laden van de laadproblemen is ingeschakeld, worden concepten niet opgehaald, waardoor de workflow wordt verstoord. (FORMS-19890, FORMS-19808)
* Gebruikers ondervonden problemen bij het opslaan van formuliereigenschappen voor adaptief formulier op basis van Core Components. Dit kwam voor omdat de overtollige manuscripten van de Adaptieve Vorm die op de redacteur van de Componenten van de Stichting wordt gebaseerd inbegrepen, veroorzakend conflicten in de Aangepaste Vorm die op de Componenten van de Kern wordt gebaseerd. editor. (FORMS-17474)
* Gebruikers hebben problemen ondervonden met de pagina Handtekening voor GovCloud-handtekening van Adobe. Deze pagina wordt niet weergegeven in een iframe. (FORMS-16803)
* Gebruikers ervaren fouten bij het selecteren van verwijzingen voor Forms-fragmenten (AF) die specifiek zijn voor de Core Component Adaptive. Het foutbericht &quot;Kan verwijzing niet renderen: geen absoluut pad&quot; verscheen ter voorkoming van correcte rendering van verwijzingen. (FORMS-19678)
* Toegevoegde ondersteuning voor multi-threaded conversie met Acrobat DC, waardoor gebruikers Word-, Excel- en PowerPoint-documenten efficiënter kunnen converteren naar PDF-documenten. (FORMS-21310)
* Toegevoegde opname van `com.adobe.granite.toggle.impl.dev` -bundel in AEM Service Pack 24, waardoor meer gestroomlijnde ontwikkelingsprocessen mogelijk worden gemaakt door deze uit de invoegtoepassing Forms te verwijderen. (FORMS-20139)
* FeatureToggleRenderConditionServlet is verwijderd uit de form-foundation en com.adobe.granite.toggle.impl.dev-bundel uit de form add-on. Deze update zorgt ervoor dat na de installatie van de add-on formulieren de rendervoorwaarde correct wordt omgezet, waardoor de functionaliteit van de component voor klanten wordt verbeterd. (FORMS-20138)
* Gebruikers ondervonden trage prestaties als gevolg van langdurige query&#39;s in Adaptive Forms. Deze update backports vraagveranderingen om efficiency te verbeteren. Klanten kunnen nu index met tagnamen aemformsAFReferences maken. (FORMS-21411)
* Gebruikers ondervonden onjuist uitgelijnde koptekstposities tijdens het converteren van HTML naar Portable Document Format (PDF) met WebPDF. Dit probleem heeft invloed op de consistentie en leesbaarheid van de uitvoerindeling van documenten. (FORMS-21502, FORMS-21540)
* Gebruikers ondervonden validatiefouten bij PDF/A-1b ondanks geslaagde verificatie vóór de vlucht. Dit probleem betrof de controle op de naleving van documenten voor zakelijke klanten die PDF-validatieprogramma&#39;s gebruiken. (FORMS-20196)
* De gebruikers ervoeren onvertaalde koorden op UI, veroorzakend verwarring en moeilijkheid in het begrijpen van de interface. (FORMS-6542)
* Gebruikers hebben problemen ondervonden met e-mailmeldingen. De stap E-mailworkflow verzenden heeft geen invloed op geautomatiseerde communicatieprocessen. (FORMS-17961)
* Gebruikers ondervonden mislukte tests voor formulierwerkstromen, die invloed hadden op hun vermogen om werkstroomprocessen efficiënt te voltooien. (FORMS-16231)
* Gebruikers konden de tijdlijnfunctie van PDF-bestanden niet gebruiken in AEM-formulieren. Dit probleem heeft invloed op het vermogen van gebruikers om documentwijzigingen en revisies effectief bij te houden. Wanneer u een PDF uploadt onder de sectie &#39;Forms en Documenten&#39; in het gebied AEM-formulieren, werkt de tijdlijnweergave niet meer. (FORMS-19408)
* De gebruikers ervaren een ongeldige wijzeruitzondering wanneer het in wisselwerking staan met OData. Dit veroorzaakt onderbrekingen in de processen van de gegevensherwinning. (FORMS-20348)
* De google.common.collection-bibliotheek is verwijderd nadat Guava, een opensource Java-bibliotheek, is verwijderd. Deze update zorgt voor betere compatibiliteit en prestaties voor zakelijke klanten die gebruikmaken van Adaptive Forms. (FORMS-17031)

### Forms Captcha

* Toegevoegde Hcaptcha- en Turnstile-ondersteuning voor adaptieve Forms op basis van Foundation Components. (FORMS-16562)
* Gebruikers met een ervaren pictogram overlappen problemen in het dialoogvenster Captcha-configuratie maken. Bij het invullen van de vereiste velden overlapte het informatiepictogram het foutpictogram, wat verwarring veroorzaakt tijdens de configuratie-instelling. (FORMS-16916)
* Gebruikers ondervonden een onjuiste configuratie die voor reCAPTCHA werd opgepakt in Adaptive Forms op basis van stichtingscomponenten. Wanneer de configuratiecontainer niet is geselecteerd voor een formulier, hebben meerdere configuraties in de map `conf/global` het probleem veroorzaakt. (FORMS-19237)
* Gebruikers ondervonden problemen met het renderen van reCAPTCHA. Dit beïnvloedde formulierverzendingen en beveiligingsvalidatie voor zakelijke klanten. (FORMS-17136, FORMS-19596)
* Gebruikers ervaren een probleem waarbij de grootte van de reCAPTCHA-onderneming niet wordt weerspiegeld in de gebruikersinterface (UI). (FORMS-16574)
* Gebruikers hebben problemen ondervonden met de functionaliteit van ReCaptcha als gevolg van een niet-gesloten ResourceResolver in &#39;ReCaptchaConfigurationServiceImpl&#39;, die periodiek validatiefouten veroorzaken tijdens formulierverzendingen. (FORMS-19241)
* Gebruikers ondervonden problemen met de validatie van reCAPTCHA wanneer formulieren in sites worden gemaakt. AEM-formulieren herkennen de formuliernaam niet correct, waardoor validatiefouten zijn opgetreden. (FORMS-20486)
* Gebruikers hebben formulieren ingediend, zelfs als de reCAPTCHA-score van de onderneming 1,0 was, wat tot potentiële beveiligingsrisico&#39;s leidde. (FORMS-16766) {{$include }}
* Verbeterde reCAPTCHA-waarschuwingen in Adaptive Forms door het bijwerken van de verzendfoutcodes naar 400. Ook, verfijnde logboekalarm om tussen onderbrekingen, verlopen, en beide mislukkingen van de ontdekkingsopsporing te onderscheiden, die het verbeteren van het oplossen van problemennauwkeurigheid en systeemwaarneming verbeteren. (FORMS-19240)
* Sluit een niet-gesloten instantie ResourceResolver in ReCaptchaConfigurationServiceImpl om potentiële middellekken te verhinderen en systeemstabiliteit te verbeteren wanneer het gebruiken van reCAPTCHA integraties in AEM Forms. (FORMS-19242)
* Verbeterde CAPTCHA-configuratieverwerking voor AEM Forms door ervoor te zorgen dat de juiste configuratie aan elk formulier wordt gekoppeld wanneer er meerdere items in de map /conf/global aanwezig zijn. Voorkomt onbedoeld gebruik van onjuiste CAPTCHA-instellingen wanneer de configuratiecontainer niet expliciet is geselecteerd. (FORMS-19239)

### Gebruikersinterface Forms Management

* Gebruikers ondervonden niet-gelokaliseerde tekenreeksen in Forms > Controlemap maken > Maken van controlemap. Bij het maken van een gecontroleerde map zijn geen tekenreeksen gevonden, zoals &#39;Controlemap maken&#39; en &#39;Controlemap gemaakt&#39;. Dit heeft invloed op de gebruikersinterface. (FORMS-15234)

## [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Het platform van [!DNL Adobe Experience Manager] 6.5 LTS bouwt voort op bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java™ Content Repository: Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wordt gebruikt als servletmotor voor QuickStart.

### Java™-ondersteuning  {#java-support}

* Ondersteuning voor Java™ 17 en Java™ 21.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Voor meer informatie, zie [ installeer en werk ](/help/sites-deploying/custom-standalone-install.md) sectie bij.
* Adobe verspreidt updates voor Java™ 17- en Java™ 21-onderhoud voor gebruik door klanten in AEM-gerelateerde projecten, wanneer deze niet openbaar zijn vanuit Oracle.

### Uberjar-verpakking {#uber-jar-packaging}

* Er is een klein verschil tussen de Uberjar-verpakking en de AEM 6,5 LTS. Voor meer informatie, zie [ Update de versie van AEM Uber Jar ](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

### Upgrade {#upgrade}

* Voor details over de verbeteringsprocedure, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

## Installeren en bijwerken {#install-update}

Voor opstellingsvereisten, zie [ installatieinstructies ](/help/sites-deploying/custom-standalone-install.md).

>[!NOTE]
>
> Als u rechtstreeks aan LTS SP1 van oude 6.5 SPs bevordert, gelieve de instructies te volgen die voor 6.5 tot 6.5 LTS GA [ verbetering ](/help/sites-deploying/upgrade.md) worden gegeven.


Voor gedetailleerde instructies, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Voor nieuwe AEM 6.5 LTS-installaties moeten indexdefinities afzonderlijk worden geïnstalleerd. Voor meer informatie, zie [ dit artikel ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## AEM Forms-invoegtoepassing installeren en bijwerken {#install-update-aem-forms-add-on}

Voor gedetailleerde instructies, zie [ Uitvoerend een Verbetering op zijn plaats ](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/release-notes/aem-forms-current-service-pack-installation-instructions).



## Ondersteunde platforms {#supported-platforms}

Vind de volledige matrijs van gesteunde platforms met inbegrip van steun-niveau op [ AEM 6.5 LTS technische vereisten ](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 zijn de aanbevolen versies voor gebruik met AEM 6.5 LTS.


## Verouderde en verwijderde functies {#deprecated-and-removed-features}

<!-- CARRY OVER EACH RELEASE -->

Adobe controleert voortdurend de productmogelijkheden om de waarde van klanten te verbeteren door oudere functies te moderniseren of te vervangen. Deze veranderingen worden gemaakt met zorgvuldige aandacht aan achterwaartse verenigbaarheid.

Om de aanstaande verwijdering of vervanging van Adobe Experience Manager (AEM) mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De daadwerkelijke streefdatum voor verwijdering is gepland voor bekendmaking later.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

### Verouderde functies {#deprecated-features}

In deze sectie worden de functies en mogelijkheden weergegeven die Adobe in AEM 6.5 LTS heeft vervangen. Adobe heeft doorgaans een lagere functie dan functies voordat deze in een toekomstige versie worden verwijderd. Bovendien is dit een alternatief.


Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Gebied | Functie | Vervanging | Versie (SP) |
| --- | --- | --- | --- |
| Sites | [ Redacteur van het KUUROORD ](/help/sites-developing/spa-overview.md) | De aangewezen redacteurs voor het beheren van hoofdloze inhoud in AEM zijn:<br> - [ de Universele Redacteur ](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven.<br> - [ de Redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) voor op vorm-gebaseerde het uitgeven. | 6,5 LTS GA |

### Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5 LTS. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging | Versie (SP) |
| --- | --- | --- | --- |
| Commerce | AEM CIF Classic wordt niet ondersteund. | Migreer aan [ AEM CIF ](/help/commerce/cif/migration.md). | 6,5 LTS GA |
| Oplossingen | Sociaal/Gemeenschappen worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Screens | Screens wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `dam-pim` en `dam-rating` worden niet ondersteund omdat bundels afhankelijk zijn van sociale componenten. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` is verwijderd. | Gebruik de alternatieve api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` die is toegevoegd. | 6,5 LTS GA |
| Portal | AEM Portal Director wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | Bundel `com.adobe.granite.socketio` wordt verwijderd. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `com.adobe.granite.crx-explorer` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `crx2oak` wordt niet ondersteund. | Kies de relevante versie van [ Oak-upgrade ](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6,5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Guava | Alle guave-afhankelijkheden worden nu verwijderd in AEM en daarom maakt de `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` -bundel geen deel uit van AEM. | Klanten kunnen alleen guave toevoegen als ze afhankelijk zijn van guave of de guave-code indien mogelijk vervangen door Java-verzamelingen of andere alternatieven. | 6,5 LTS GA |
| `We.Retail` | `We-retail` -voorbeeldsite wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `oak-solr-osgi` -bundel wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.servicemix.bundles.abdera-parser` , `org.apache.servicemix.bundles.jdom` en `org.apache.sling.atom.taglib` worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.commons.io` -pakketten worden nu geëxporteerd uit `org.apache.commons.commons-io` . | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `javax.mail` -pakketten worden geëxporteerd uit de `com.sun.javax.mail` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `org.apache.jackrabbit.api` -pakketten worden nu geëxporteerd uit de `org.apache.jackrabbit.oak-jackrabbit-api` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `com.github.jknack.handlebars` wordt niet ondersteund | Kies de relevante [ versie ](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6,5 LTS GA |


## Bekende problemen {#known-issues}

<!-- DO THESE KNOWN ISSUES CARRY OVER EACH RELEASE? THE "PRODUCT UPDATES TEAM" IS SUPPOSED TO VERIFY EACH ISSUE AND LET YOU KNOW IF ANYTHING NEEDS TO BE ADDED, DELETED, OR CHANGED IN THIS LIST. -->

### Issue with JSP scripting bundle in AEM 6.5.21-6.5.23 and AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 en AEM 6.5 LTS GA schip met de `org.apache.sling.scripting.jsp:2.6.0` bundel, die een bekende kwestie bevat. De kwestie komt typisch onder hoge lading voor wanneer de instantie van AEM vele gezamenlijke verzoeken behandelt.

Wanneer dit probleem optreedt, kan een van de volgende uitzonderingen voorkomen in de foutenlogboeken naast verwijzingen naar `org.apache.sling.scripting.jsp:2.6.0` :

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Een hotfix [ cq-6.5.lts.0-hotfix-NPR-42640 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) is beschikbaar om dit probleem op te lossen.

### Dispatcher-verbindingsfout met alleen-SSL-functie (opgelost in AEM 6.5 LTS SP1 en hoger){#ssl-only-feature}

>[!NOTE]
>
> Dit probleem is alleen aanwezig in de AEM 6.5 LTS GA-release.

Wanneer het toelaten van de SSL-enige eigenschap in de plaatsingen van AEM, is er een bekende kwestie die connectiviteit tussen de instanties van Dispatcher en van AEM beïnvloedt. Nadat u deze functie hebt ingeschakeld, kunnen de gezondheidscontroles mislukken en kan de communicatie tussen Dispatcher- en AEM-instanties worden verstoord. Dit probleem doet zich met name voor wanneer klanten `https + IP` proberen te doorlopen van de Dispatcher naar AEM-instanties. Het heeft betrekking op SNI (de Verwijzing van de Naam van de Server) bevestigingsproblemen.

**Effect:**

* Fouten in de health check met HTTP 400-responscodes
* Gebroken verkeer tussen Dispatcher en AEM
* Inhoud kan niet correct worden aangeboden via de Dispatcher
* Verbindingsfouten bij gebruik van HTTPS met IP-adressen in Dispatcher-configuratie
* HTTP 400 &quot;Ongeldige SNI&quot;fouten wanneer het verbinden via HTTPS + IP

**Betrokken milieu&#39;s:**

* AEM-implementaties met Dispatcher-configuraties
* Systemen waarbij de functie Alleen SSL is ingeschakeld
* Dispatcher-configuraties die gebruikmaken van de methode `https + IP` connection to AEM instances

**Oplossing:**
Neem contact op met Customer Support van Adobe als dit probleem zich voordoet. Een hotfix [ cq-6.5.lts.0-hotfix-CQ-4359803 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is beschikbaar om dit probleem op te lossen. Probeer alleen SSL-functies in te schakelen voordat u de vereiste hotfix toepast.

## OSGi-bundels en inhoudspakketten inbegrepen{#osgi-bundles-and-content-packages-included}

De volgende tekstdocumenten maken een lijst van de bundels OSGi en de Pakketten van de Inhoud inbegrepen in [!DNL Experience Manager] 6.5 LTS, Service Pack 1 versie:

* [ Lijst van bundels OSGi inbegrepen in Experience Manager 6.5 LTS, Service Pack 1 ](/help/release-notes/assets/65lts_sp1_bundles.txt) <!-- UPDATE FOR EACH NEW RELEASE -->
* [ Lijst van Inhoudspakketten inbegrepen in Experience Manager 6.5 LTS, Service Pack 1 ](/help/release-notes/assets/65lts_sp1_packages.txt) <!-- UPDATE FOR EACH NEW RELEASE -->

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [ download van het Product bij licensing.adobe.com ](https://licensing.adobe.com/)
* [ de Klantenondersteuning van Adobe van het Contact ](https://experienceleague.adobe.com/nl/docs/customer-one/using/home).

