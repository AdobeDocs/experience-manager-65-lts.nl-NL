---
title: Dynamic Media Classic-functies (Scene7) toevoegen aan uw pagina
description: Adobe Dynamic Media Classic (Scene7) is een gehoste oplossing voor het beheren, verbeteren, publiceren en leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-verbonden vertoningen en druk.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: authoring
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: e452c343-3bba-4774-b153-c5ba05f24362
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '3409'
ht-degree: 0%

---

# Dynamic Media Classic-functies (Scene7) toevoegen aan uw pagina{#adding-scene-features-to-your-page}

[ Adobe Dynamic Media Classic (Scene7) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/home.html) is een ontvangen oplossing voor het leiden, het verbeteren, het publiceren, en het leveren van rijke media activa aan Web, mobiel, e-mail, en Internet-Verbonden vertoningen en druk.

U kunt de activa van Experience Manager bekijken die in Dynamic Media Classic (Scene7) in diverse kijkers worden gepubliceerd:

* Zoomen
* Flyout
* Video
* Afbeeldingssjabloon
* Afbeelding

U kunt digitale activa van Experience Manager aan Dynamic Media Classic (Scene7) direct publiceren en u kunt digitale activa van Dynamic Media Classic (Scene7) aan Experience Manager publiceren.

In dit document wordt beschreven hoe u digitale elementen kunt publiceren van Experience Manager naar Dynamic Media Classic (Scene7) en omgekeerd. Viewers worden ook in detail beschreven. Voor informatie bij het vormen van Experience Manager voor Dynamic Media Classic (Scene7), zie [ Integrating Dynamic Media Classic (Scene7) met Experience Manager ](/help/sites-administering/scene7.md).

Zie ook [ Afbeeldingskaarten ](/help/assets/image-maps.md) toevoegen.

Raadpleeg de volgende secties voor meer informatie over het gebruik van videocomponenten met Experience Manager:

* [Video](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md)

>[!NOTE]
>
>Als de activa van Dynamic Media Classic (Scene7) niet behoorlijk tonen, zorg ervoor dat de Dynamische Media [ gehandicapt ](/help/assets/config-dynamic.md#disabling-dynamic-media) is en vernieuw dan de pagina.

## Handmatig publiceren naar Dynamic Media Classic (Scene7) vanuit Assets {#manually-publishing-to-scene-from-assets}

U kunt digitale activa aan Dynamic Media Classic (Scene7) of van de console van Assets in klassieke UI of direct van de activa publiceren.

>[!NOTE]
>
>Experience Manager publiceert asynchroon naar Dynamic Media Classic (Scene7). Nadat u **[!UICONTROL Publish]** hebt geselecteerd, kan het enkele seconden duren voordat uw element naar Dynamic Media Classic (Scene7) wordt gepubliceerd.
>

### Publiceren vanaf de Assets-console {#publishing-from-the-assets-console}

U kunt aan Dynamic Media Classic (Scene7) van de console van Assets publiceren als de activa in een Dynamic Media Classic (Scene7) doelomslag zijn.

1. Selecteer in de klassieke gebruikersinterface van Experience Manager de optie **[!UICONTROL Digital Assets]** voor toegang tot het beheer van digitale elementen.

1. Selecteer het element (of de elementen) of de map in de doelmap die u naar Dynamic Media Classic wilt publiceren (Scene7), klik met de rechtermuisknop en selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** . U kunt ook **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** selecteren in het menu **[!UICONTROL Tools]** .

   ![ chlimage_1-48 ](assets/chlimage_1-48.png)

1. Ga naar Dynamic Media Classic (Scene7) en bevestig dat de activa beschikbaar zijn.

   >[!NOTE]
   >
   >Als de elementen zich niet in een gesynchroniseerde Dynamic Media Classic (Scene7) map bevinden, is **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in beide menu&#39;s zichtbaar maar uitgeschakeld.

### Publiceren vanuit een element {#publishing-from-an-asset}

U kunt activa manueel publiceren zolang dat middel binnen de gesynchroniseerde omslag van Dynamic Media Classic (Scene7) wordt gevestigd.

>[!NOTE]
>
>Als het element niet in de gesynchroniseerde map Dynamic Media Classic (Scene7) staat, wordt de koppeling naar **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** niet weergegeven.

Om aan Dynamic Media Classic (Scene7) direct van een digitaal middel te publiceren:

1. Selecteer in Experience Manager **[!UICONTROL Digital Assets]** voor toegang tot het beheer van digitale elementen.

1. Dubbelklik om een element te openen.

1. Selecteer **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** in het deelvenster Elementdetails.

   ![ screen_shot_2012-02-22at34828pm ](assets/screen_shot_2012-02-22at34828pm.png)

1. De koppeling verandert in **[!UICONTROL Publishing ...]** en vervolgens in **[!UICONTROL Published]** . Ga naar Dynamic Media Classic (Scene7) en bevestig dat de activa beschikbaar zijn.

   >[!NOTE]
   >
   >Als het element niet correct naar Dynamic Media Classic (Scene7) publiceert, verandert de koppeling in **[!UICONTROL Publishing Failed]**. Als het element al is gepubliceerd naar Dynamic Media Classic (Scene7), leest de koppeling **[!UICONTROL Re-Publish to Dynamic Media Classic (Scene7)]**. Door middel van opnieuw publiceren kunt u elementen in Experience Manager wijzigen en opnieuw publiceren.

### Elementen publiceren van buiten de CQ-doelmap {#publishing-assets-from-outside-the-cq-target-folder}

Adobe raadt u aan elementen alleen vanuit de doelmap Dynamic Media Classic (Scene7) naar Dynamic Media Classic te publiceren. Nochtans, als u activa van een omslag buiten de doelomslag moet uploaden, kunt u dat nog doen door hen aan een omslag op bestelling op Dynamic Media Classic (Scene7) te uploaden. Configureer eerst de cloudconfiguratie voor de pagina waarop u het element wilt weergeven. Vervolgens voegt u een Dynamic Media Classic-component (Scene7) toe aan de pagina en sleept u een element naar de component. Nadat de pagina-eigenschappen voor die pagina zijn ingesteld, wordt een **[!UICONTROL Publish to Dynamic Media Classic (Scene7)]** -koppeling weergegeven die bij selectie het uploaden naar Dynamic Media Classic (Scene7) activeert.

>[!NOTE]
>
>Assets die zich in de omslag op bestelling bevinden verschijnt niet in de Browser van de Inhoud van Dynamic Media Classic (Scene7).

**om activa van buiten de CQ doelomslag te publiceren:**

1. In Experience Manager in klassieke UI, uitgezochte **[!UICONTROL Websites]** en navigeer aan de Web-pagina die u een digitaal middel aan wilt toevoegen dat nog niet aan Dynamic Media Classic (Scene7) wordt gepubliceerd. (Normale regels voor paginaovererving zijn van toepassing.)

1. Selecteer in het zijpaneel het pictogram **[!UICONTROL Page]** en selecteer **[!UICONTROL Page Properties]** .

1. Selecteer **[!UICONTROL Cloud Services]** .
1. Selecteer **[!UICONTROL Add services]** .
1. Selecteer **[!UICONTROL Dynamic Media Classic (Scene7)]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL Adobe Dynamic Media Classic (Scene7)]** de gewenste configuratie en selecteer **[!UICONTROL OK]** .

   ![ chlimage_1-49 ](assets/chlimage_1-49.png)

1. Voeg op de webpagina een Dynamic Media Classic-component (Scene7) toe aan de gewenste locatie op de pagina.
1. Sleep een digitaal element vanuit de zoeker naar de component. Er wordt een koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven.

   >[!NOTE]
   >
   >Als het digitale element zich in de CQ-doelmap bevindt, wordt er geen koppeling naar **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]** weergegeven. De elementen worden in de component geplaatst.

   ![ chlimage_1-50 ](assets/chlimage_1-50.png)

1. Selecteer **[!UICONTROL Check Dynamic Media Classic (Scene7) Publication Status]**. Als de activa niet worden gepubliceerd, publiceert Experience Manager de activa aan Dynamic Media Classic (Scene7). Nadat het element is geüpload, vindt u het in de map op aanvraag. Standaard bevindt de map op aanvraag zich in de map **[!UICONTROL name_of_the_company/CQ5_adhoc]** . U kunt [ de omslag vormen op bestelling, indien nodig ](#configuringtheadhocfolder).

   >[!NOTE]
   >
   >Als de activa niet in een gesynchroniseerde omslag van Dynamic Media Classic (Scene7) is en er geen de wolkenconfiguratie van Dynamic Media Classic (Scene7) verbonden aan de huidige pagina is, ontbreekt het uploaden.

## Dynamic Media Classic (Scene7)-componenten {#scene-components}

De volgende Dynamic Media Classic (Scene7) componenten zijn beschikbaar in Experience Manager:

* Zoomen
* Flyout (zoomen)
* Afbeeldingssjabloon
* Afbeelding
* Video

>[!NOTE]
>
>Deze componenten zijn niet standaard beschikbaar en moeten in de ontwerpmodus worden geselecteerd voordat ze kunnen worden gebruikt.

Nadat de componenten in de ontwerpmodus beschikbaar zijn gemaakt, kunt u ze net als alle andere Experience Manager-componenten aan de pagina toevoegen. Assets die nog niet aan Dynamic Media Classic (Scene7) worden gepubliceerd wordt gepubliceerd aan Dynamic Media Classic (Scene7) als in een gesynchroniseerde omslag of op een pagina of met een Configuratie van de Wolk van Dynamic Media Classic (Scene7).

>[!NOTE]
>
>Als u aangepaste S7-viewers maakt en ontwikkelt en de Inhoudszoeker gebruikt, moet u de parameter `allowfullscreen` expliciet toevoegen.

### Eindbericht voor Flash-viewers {#flash-viewers-end-of-life-notice}

Vanaf 31 januari 2017 is de ondersteuning voor het Flash-viewerplatform door Adobe Dynamic Media Classic (Scene7) officieel beëindigd.

### Een Dynamic Media Classic-component (Scene7) toevoegen aan een pagina {#adding-a-scene-component-to-a-page}

Het toevoegen van een Dynamic Media Classic (Scene7) component aan een pagina is het zelfde als het toevoegen van een component aan om het even welke pagina. De componenten van Dynamic Media Classic (Scene7) worden beschreven in detail in de volgende secties.

Om een component Dynamic Media Classic (Scene7)/kijker aan een pagina in klassieke UI toe te voegen:

1. Open in Experience Manager de pagina waaraan u de Dynamic Media Classic-component (Scene7) wilt toevoegen.

1. Als geen componenten van Dynamic Media Classic (Scene7) beschikbaar zijn, selecteer de heerser in sidekick om **wijze van het Ontwerp** in te gaan, **[!UICONTROL Edit]** parsys te selecteren, en alle **[!UICONTROL Dynamic Media Classic (Scene7)]** componenten te selecteren om hen beschikbaar te maken.

1. Terugkeer aan **geef** wijze uit door het potlood in sidekick te selecteren.

1. Sleep een component van de **[!UICONTROL Dynamic Media Classic (Scene7)]** groep in het hulpstuk op de pagina in de gewenste plaats.

1. Selecteer * **[!UICONTROL Edit]** zodat u de component kunt openen.

1. Bewerk de component naar wens en selecteer **[!UICONTROL OK]** om de wijzigingen op te slaan.

### Interactieve weergaven toevoegen aan een responsieve website {#adding-interactive-viewing-experiences-to-a-responsive-website}

Het responsieve ontwerp voor uw elementen betekent dat uw elementen worden aangepast op basis van de locatie waar ze worden weergegeven. Bij een responsief ontwerp kunnen dezelfde elementen effectief op meerdere apparaten worden weergegeven.

Een interactieve kijkervaring toevoegen aan een responsieve site in de klassieke gebruikersinterface:

1. Login aan Experience Manager, en zorg ervoor dat u de Diensten van de Wolk van Adobe Dynamic Media Classic (Scene7) [&#128279;](/help/sites-administering/scene7.md#configuring-scene-integration) hebt gevormd en dat de componenten van Dynamic Media Classic (Scene7) beschikbaar zijn.

   >[!NOTE]
   >
   >Als Dynamic Media Classic (Scene7) WCM componenten niet beschikbaar zijn, zeker om hen via de wijze van het Ontwerp toe te laten.

1. In een website waarvoor de Dynamic Media Classic-componenten (Scene7) zijn ingeschakeld, sleept u een **[!UICONTROL Image]** -viewer naar de pagina.
1. Bewerk de component en pas de onderbrekingspunten aan op het tabblad **[!UICONTROL Dynamic Media Classic (Scene7) Settings]** .

   ![ chlimage_1-51 ](assets/chlimage_1-51.png)

1. Controleer of de viewers het formaat responsief wijzigen en of alle interacties zijn geoptimaliseerd voor computers, tablets en mobiele apparaten.

### Gemeenschappelijke montages voor alle componenten van Dynamic Media Classic (Scene7) {#settings-common-to-all-scene-components}

Hoewel de configuratieopties variëren, zijn het volgende gemeenschappelijk voor alle componenten van Dynamic Media Classic (Scene7):

* **Verwijzing van het Dossier** - doorblader aan een dossier dat u wilt van verwijzingen voorzien. De verwijzing van het dossier toont de activa URL en niet noodzakelijk volledige Dynamic Media Classic (Scene7) URL met inbegrip van de bevelen URL en de parameters. U kunt geen Dynamic Media Classic (Scene7) URL bevelen en parameters op dit gebied toevoegen. In plaats daarvan, moeten zij door de overeenkomstige functionaliteit in de component worden toegevoegd.
* **Breedte** - laat u de breedte plaatsen.
* **Hoogte** - laat u de hoogte plaatsen.

U plaatst deze configuratieopties door (het tweemaal klikken) een component van Dynamic Media Classic (Scene7) te openen, bijvoorbeeld, wanneer u a **&#x200B;**&#x200B;component van het Gezoem opent:

![ chlimage_1-52 ](assets/chlimage_1-52.png)

### Zoomen {#zoom}

De HTML5-component Zoom geeft een grotere afbeelding weer wanneer u op + drukt.

Het element heeft onderaan zoomgereedschappen. Selecteer **[!UICONTROL +]** om te vergroten. Selecteer **[!UICONTROL -]** om te reduceren. Als u de zoompijl **[!UICONTROL x]** of de zoompijl opnieuw instelt, wordt de afbeelding weer op de oorspronkelijke grootte ingesteld die was geïmporteerd als. Selecteer de diagonale pijlen zodat u deze op volledig scherm kunt weergeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic vormen ](#settings-common-to-all-scene-components).

![ Beeld van Tipbloemen binnen de component van het Gezoem HTML5.](do-not-localize/chlimage_1-3.png)

### Flyout {#flyout}

In de HTML5 Flyout-component wordt het element weergegeven als een gesplitst scherm, waarbij het element in de opgegeven grootte wordt geplaatst en rechts het zoomgedeelte wordt weergegeven. Selecteer **[!UICONTROL Edit]** zodat u de component kunt configureren. Met deze component, kunt u [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic vormen ](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Als uw Flyout-component een aangepaste grootte gebruikt, wordt die aangepaste grootte gebruikt en wordt de responsieve instelling van de component uitgeschakeld.
>
>Als de component Flyout de standaardgrootte gebruikt, zoals die in de ontwerpweergave is ingesteld, wordt de standaardgrootte gebruikt. De component wordt uitgerekt om de grootte van de paginalay-out aan te passen met responsieve instelling van de component ingeschakeld. Houd er echter rekening mee dat er een beperking geldt voor de responsieve installatie van de component. Wanneer u de component Flyout met ontvankelijke opstelling gebruikt, zou u het niet met volledige paginalrek moeten gebruiken. Anders kan de Flyout de rechterrand van de pagina overschrijden.

![ chlimage_1-53 ](assets/chlimage_1-53.png)

### Afbeelding {#image}

Met de Dynamic Media Classic-afbeeldingscomponent (Scene7) kunt u Dynamic Media Classic-functionaliteit (Scene7) aan uw afbeeldingen toevoegen, zoals wijzigingstoetsen voor Dynamic Media Classic (Scene7), voorinstellingen voor afbeeldingen of viewers en verscherpen. De Dynamic Media Classic (Scene7) beeldcomponent is gelijkaardig aan andere beeldcomponenten in Experience Manager met speciale functionaliteit van Dynamic Media Classic (Scene7). In dit voorbeeld is de optie Dynamic Media Classic (Scene7) URL op de afbeelding toegepast, `&op_invert=1` .

![ Beeld van een gebied binnen de het beeldcomponent van Dynamic Media Classic (Scène 7) ](do-not-localize/chlimage_1-4.png)

**Titel, de Tekst van Alt** - op het Geavanceerde lusje, voeg een titel aan het beeld en alt tekst voor die gebruikers toe die grafiek hebben uitgezet.

**URL, Open in** - u kunt activa van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![ chlimage_1-54 ](assets/chlimage_1-54.png)

**vooraf ingestelde Kijker** - selecteer een bestaande vooraf ingestelde kijker van het drop-down menu. Als de viewervoorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Viewer-voorinstellingen beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**Dynamic Media Classic (Scene7) Configuratie** - selecteer de configuratie van Dynamic Media Classic (Scene7) die u wilt gebruiken om actieve beeldvoorinstellingen van SPS te halen.

**vooraf ingesteld Beeld** - selecteer een bestaand beeld vooraf ingesteld van het drop-down menu. Als de voorinstelling die u zoekt niet zichtbaar is, moet u deze zichtbaar maken. Zie Voorinstellingen afbeelding beheren. U kunt geen viewervoorinstelling selecteren als u een voorinstelling voor afbeeldingen gebruikt en omgekeerd.

**Formaat van de Output** - selecteer het outputformaat van het beeld, bijvoorbeeld, jpeg. Afhankelijk van de uitvoerindeling die u selecteert, hebt u mogelijk aanvullende configuratieopties. Zie Aanbevolen werkwijzen voor voorinstellingen afbeelding.

**Verscherpen** - selecteer hoe u het beeld wilt verscherpen. Verscherpen wordt gedetailleerd uitgelegd in de aanbevolen werkwijzen voor voorinstellingen van afbeeldingen en in de aanbevolen werkwijzen voor Verscherpen.

**de Modifiers URL** - u kunt beeldgevolgen veranderen door extra S7 beeldbevelen te leveren. Deze opdrachten worden beschreven in Voorinstellingen afbeelding en de opdrachtverwijzing.

**Onderbrekingspunten** - als uw website ontvankelijk is, wilt u de breekpunten aanpassen. Onderbrekingspunten moeten worden gescheiden door komma&#39;s (,).

### Afbeeldingssjabloon {#image-template}

De Malplaatjes van het Beeld van Dynamic Media Classic (Scene7) zijn gelaagde inhoud van Photoshop die in Dynamic Media Classic (Scene7) werd ingevoerd, waar de inhoud en de eigenschappen voor variabiliteit werden bepaald. Met de component **[!UICONTROL Image template]** kunt u afbeeldingen importeren en de tekst dynamisch wijzigen in Experience Manager. Daarnaast kunt u de component **[!UICONTROL Image template]** zo configureren dat waarden van de clientcontext worden gebruikt, dat elke gebruiker de afbeelding op een gepersonaliseerde manier ervaart.

Selecteer **[!UICONTROL Edit]** - om de component te configureren. U kunt [ montages gemeenschappelijk voor alle (Scene7) componenten van Dynamic Media Classic vormen ](/help/sites-administering/scene7.md#settingscommontoallscene7components) en andere montages die in deze sectie worden beschreven.

![ chlimage_1-55 ](assets/chlimage_1-55.png)

**Verwijzing van het Dossier, Breedte, Hoogte** - zie [ montages gemeenschappelijk voor alle componenten van Dynamic Media Classic (Scene7) ](/help/sites-administering/scene7.md#settingscommontoallscene7components).

>[!NOTE]
>
>Dynamic Media Classic (Scene7) URL-opdrachten en -parameters kunnen niet rechtstreeks aan de URL van de bestandsverwijzing worden toegevoegd. Ze kunnen alleen worden gedefinieerd in de gebruikersinterface van de component in het deelvenster **[!UICONTROL Parameter]** .

**Titel, de Tekst van Alt** - in het Malplaatje van het Beeld van Dynamic Media Classic (Scene7), voeg een titel aan het beeld en alt tekst voor die gebruikers toe die grafiek hebben uitgezet.

**URL, Open in** - u kunt activa van plaatsen om een verbinding te openen. Stel de URL in en kies Openen in om aan te geven of deze in hetzelfde venster of in een nieuw venster moet worden geopend.

![ chlimage_1-56 ](assets/chlimage_1-56.png)

**het Comité van de Parameter** - wanneer het invoeren van een beeld, worden de parameters pre-bevolkt met informatie van het beeld. Als er geen inhoud is die dynamisch kan worden gewijzigd, is dit venster leeg.

![ chlimage_1-57 ](assets/chlimage_1-57.png)

#### Tekst dynamisch wijzigen {#changing-text-dynamically}

Als u de tekst dynamisch wilt wijzigen, voert u nieuwe tekst in de velden in en selecteert u **[!UICONTROL OK]** . In dit voorbeeld, is de **Prijs** nu $50 en het verschepen is 99 cent.

![ chlimage_1-58 ](assets/chlimage_1-58.png)

De tekst in de afbeelding verandert. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![ chlimage_1-59 ](assets/chlimage_1-59.png)

#### Tekst wijzigen om de waarde van de context van een client weer te geven {#changing-text-to-reflect-the-value-of-a-client-context-value}

Als u een veld aan een clientcontextwaarde wilt koppelen, selecteert u **[!UICONTROL Select]** om het contextmenu van de client te openen, selecteert u de clientcontext en selecteert u **[!UICONTROL OK]** . In dit voorbeeld verandert de naam op basis van de koppeling van de naam met de opgemaakte naam in het profiel.

![ chlimage_1-60 ](assets/chlimage_1-60.png)

De tekst geeft de naam weer van de gebruiker die momenteel is aangemeld. U kunt de tekst terugzetten naar de oorspronkelijke waarde door **[!UICONTROL Reset]** naast het veld te selecteren.

![ chlimage_1-61 ](assets/chlimage_1-61.png)

#### Van de Dynamic Media Classic (Scene7) beeldmalplaatje een verbinding maken {#making-the-scene-image-template-a-link}

U kunt van de de beeldmalplaatjecomponent van Dynamic Media Classic (Scene7) een klikbare verbinding maken.

1. Selecteer **[!UICONTROL Edit]** op de pagina met de Dynamic Media Classic-afbeeldingssjablooncomponent (Scene7).
1. Voer in het veld **[!UICONTROL URL]** de URL in waarnaar gebruikers gaan wanneer op de afbeelding wordt geklikt. Selecteer in het veld **[!UICONTROL Open in]** of u het doel wilt openen (een nieuw venster of hetzelfde venster).

   ![ chlimage_1-62 ](assets/chlimage_1-62.png)

1. Selecteer **[!UICONTROL OK]** .

### Video-component {#video-component}

De component Dynamic Media Classic (Scene7) **[!UICONTROL Video]** (beschikbaar bij de sectie van Dynamic Media Classic (Scene7) van sidekick) gebruikt apparaat en bandbreedteopsporing om de juiste video aan elk scherm te dienen. Deze component is een HTML5-videospeler; het is één viewer die met meerdere kanalen kan worden gebruikt.

Deze kan worden gebruikt voor adaptieve videosets, één MP4-video of één F4V-video.

Zie [ Video ](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) voor meer informatie over hoe de video&#39;s met de integratie van Dynamic Media Classic (Scene7) werken. Bovendien zie hoe [ de **Dynamic Media Classic (Scene7) video** component met de stichting **video** component ](/help/sites-classic-ui-authoring/manage-assets-classic-s7-video.md) vergelijkt.

![ chlimage_1-63 ](assets/chlimage_1-63.png)

### Bekende beperkingen voor de video-component {#known-limitations-for-the-video-component}

Adobe DAM en WCM laten zien of een primaire bronvideo is geüpload. Deze proxy-elementen worden niet weergegeven:

* Dynamic Media Classic (Scene7) gecodeerde uitvoeringen
* Adaptieve videosets van Dynamic Media Classic (Scene7)

Wanneer u een adaptieve videoset gebruikt met de Dynamic Media Classic-videocomponent (Scene7), moet de grootte van de component worden aangepast aan de afmetingen van de video.

## Dynamic Media Classic-inhoudbrowser (Scene7) {#scene-content-browser}

De de inhoudbrowser van Dynamic Media Classic (Scene7) laat u inhoud van Dynamic Media Classic (Scene7) direct in Experience Manager bekijken. Om tot inhoudbrowser, in de Vinder van de Inhoud toegang te hebben, selecteer **Dynamic Media Classic (Scene7)** in het aanraking-geoptimaliseerde gebruikersinterface of het **S7** pictogram in het klassieke gebruikersinterface. De functionaliteit is identiek tussen beide gebruikersinterfaces.

Als u veelvoudige configuraties hebt, toont Experience Manager door gebrek de [ standaardconfiguratie ](/help/sites-administering/scene7.md#configuring-a-default-configuration). U kunt verschillende configuraties in Dynamic Media Classic (Scene7) inhoudbrowser in het drop-down menu direct selecteren.

>[!NOTE]
>
>* Assets in de map op aanvraag wordt niet weergegeven in de browser met Dynamic Media Classic-inhoud (Scene7).
>* Wanneer [ Veilige Voorproef ](/help/sites-administering/scene7.md#configuring-the-state-published-unpublished-of-assets-pushed-to-scene) wordt toegelaten, zowel gepubliceerde als unpublished activa op Dynamic Media Classic (Scene7) verschijnen in Dynamic Media Classic (Scene7) inhoudsbrowser.
>* Als u **[!UICONTROL Dynamic Media Classic (Scene7)]** of het **[!UICONTROL S7]** pictogram niet als optie in inhoudbrowser ziet, moet u [ Dynamic Media Classic (Scene7) vormen om met Experience Manager ](/help/sites-administering/scene7.md) te werken.
>* Voor video, steunt Dynamic Media Classic (Scene7) inhoudbrowser:
>   * Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>   * Eén MP4-video
>   * Single F4V-video

### Bladeren door inhoud {#browsing-content-in-the-classic-ui}

Blader door inhoud in Dynamic Media Classic (Scene7) door de tab **[!UICONTROL S7]** te selecteren.

U kunt de configuratie veranderen u toegang hebt door de configuratie te selecteren. De mappen veranderen afhankelijk van de geselecteerde configuratie.

![ chlimage_1-64 ](assets/chlimage_1-64.png)

Net als bij de zoekfunctie voor inhoud voor Assets kunt u zoeken naar elementen en resultaten filteren. Nochtans, in tegenstelling tot de vinder van Assets, wanneer het ingaan van een sleutelwoord in het **S7** lusje, begint het dossier - naam **met** het koord dat u inging, eerder dan **bevattend** het sleutelwoord in het dossier - naam.

Elementen worden standaard weergegeven op bestandsnaam. U kunt resultaten echter ook filteren op elementtype.

>[!NOTE]
>
>Voor video, steunt Dynamic Media Classic (Scene7) inhoudbrowser van WCM:
>
>* Adaptieve videosets: container met alle video-uitvoeringen die nodig zijn voor naadloze weergave op meerdere schermen
>* Eén MP4-video
>* Single F4V-video
>

### Zoeken naar Dynamic Media Classic-elementen (Scene7) met de inhoudbrowser {#searching-for-scene-assets-with-the-content-browser}

Het zoeken naar Dynamic Media Classic-elementen (Scene7) lijkt op het zoeken naar Experience Manager-elementen. De uitzondering is dat wanneer u zoekt u eigenlijk een verre mening van de activa in het systeem van Dynamic Media Classic (Scene7) ziet, eerder dan hen direct in Experience Manager in te voeren.

U kunt zowel de klassieke interface als de interface met geoptimaliseerde aanrakingen gebruiken om elementen weer te geven en te zoeken. Afhankelijk van de interface, is hoe u zoekt lichtjes verschillend.

Wanneer u in een van beide UI zoekt, kunt u filteren op de volgende criteria (die hier in de voor aanraking geoptimaliseerde UI worden getoond):

**ga sleutelwoorden** in - u kunt activa door naam zoeken. Wanneer u de trefwoorden zoekt, geeft u op waar de bestandsnaam mee begint. Als u bijvoorbeeld het woord &quot;zwemmen&quot; typt, wordt gezocht naar namen van elementbestanden die met die letters in die volgorde beginnen. Selecteer `Enter` nadat u de term hebt getypt om het element te zoeken.

![ chlimage_1-65 ](assets/chlimage_1-65.png)

**Omslag/weg** - de naam van de omslag is gebaseerd op de configuratie die u selecteerde. U kunt tot lagere niveaus boren door het omslagpictogram te selecteren en subfolder te selecteren, dan het controleteken te selecteren om het te selecteren.

Als u een trefwoord invoert en een map selecteert, doorzoekt Experience Manager die map en eventuele submappen. Als u bij het zoeken echter geen trefwoorden invoert, worden bij het selecteren van de map alleen de elementen in die map weergegeven en worden er geen submappen opgenomen.

Standaard zoekt Experience Manager naar de geselecteerde map en naar alle submappen.

![ chlimage_1-66 ](assets/chlimage_1-66.png)

**Type van Activa** - selecteer Dynamic Media Classic (Scene7) om Dynamic Media Classic (Scene7) inhoud te doorbladeren. Deze optie is slechts beschikbaar als Dynamic Media Classic (Scene7) is gevormd.

![ chlimage_1-67 ](assets/chlimage_1-67.png)

**Configuratie** - als u meer dan één configuratie van Dynamic Media Classic (Scene7) hebt die in de Diensten van de Wolk wordt bepaald, kunt u het hier selecteren. Hierdoor wordt de map gewijzigd op basis van de gekozen configuratie.

![ chlimage_1-68 ](assets/chlimage_1-68.png)

**type van Activa** - binnen Dynamic Media Classic (Scene7) browser, kunt u resultaten filtreren om het even welke volgend te omvatten: beelden, malplaatjes, video&#39;s, en adaptieve videoreeksen. Als u geen elementtype selecteert, zoekt Experience Manager standaard alle elementtypen.

![ chlimage_1-69 ](assets/chlimage_1-69.png)

>[!NOTE]
>
>* In klassieke UI, kunt u ook naar **Flits** en **FXG** zoeken. Filteren voor deze twee termen in de interface met geoptimaliseerde aanrakingen wordt niet ondersteund.
>
>* Bij het zoeken naar video zoekt u op één vertoning. Resultaten retourneren de oorspronkelijke uitvoering (alleen &#42; .mp4) en de gecodeerde uitvoering.
>* Wanneer u in een adaptieve videoset zoekt, zoekt u in de map en in alle submappen, maar alleen als u een trefwoord aan de zoekopdracht hebt toegevoegd. Als u geen trefwoord hebt toegevoegd, doorzoekt Experience Manager de submappen niet.
>

**publiceer Status** - u kunt voor activa filtreren die op publicatiestatus worden gebaseerd: Niet gepubliceerd of Gepubliceerd. Als u geen publicatiestatus selecteert, zoekt Experience Manager standaard alle publicatiestatus.

![ chlimage_1-70 ](assets/chlimage_1-70.png)
