---
title: Werken met 3D-elementen in dynamische media
description: Leer hoe u 3D-middelen kunt uploaden, beheren, weergeven en leveren in Dynamic Media als een overweldigende ervaring.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: introduction
content-type: reference
feature: 3D Assets,Asset Management
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: f27b595b-24eb-444c-a598-6f70c59ed8fc
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2283'
ht-degree: 1%

---

# Werken met 3D-elementen in dynamische media {#working-with-three-d-assets-dm}

Met dynamische media kunt u 3D-elementen uploaden, beheren, weergeven en leveren als indrukwekkende ervaringen.

* Klik met één klik op het publiceren van 3D-elementen (met **[!UICONTROL Quick Publish]** op de werkbalk) om een URL te genereren.
* Geoptimaliseerde ondersteuning voor het weergeven van 3D-middelen met de voorinstelling voor interactieve maatviewer van hoge kwaliteit, aangedreven door Adobe Dimension.
* Met de 3D Media WCM-component kunt u eenvoudig 3D-elementen toevoegen aan uw Adobe Experience Manager Sites-pagina&#39;s.

Er is geen aanvullende configuratie vereist voor het gebruik van 3D-elementen in dynamische media.

![&#x200B; Schuif in 3d &#x200B;](/help/assets/assets-dm/3d-dimensional-viewer-quickpublish-url-embed2.png) *pagina van Details van een driedimensionale schoen.*

<!-- See also [Dynamic Media 3D Release Notes](/help/release-notes/aem3d-release-notes.md). -->

## 3D-indelingen die worden ondersteund in dynamische media {#supported-three-d-file-formats-in-dm}

Dynamische media ondersteunt de volgende 3D-indelingen.

Zie ook [&#x200B; gesteunde 3D formaten &#x200B;](/help/assets/assets-formats.md).

| 3D-bestandsextensie | Bestandsindeling | MIME-type | Notities |
|---|---|---|---|
| GLB | Binaire GL-transmissie | model/gltf-binair | Hiermee neemt u de materialen en structuren op als één enkel element. |
| OBJ | WaveFront 3D-objectbestand | application/x-tgif |  |
| STL | Stereolithografie | application/vnd.ms-pki.stl |  |
| USDZ | Universal Scene Description Zip-archief | model/vnd.usdz+zip | *Steun voor slechts opname; geen het bekijken of interactie is beschikbaar.* USDZ is een eigen 3D-indeling die door Safari- en iOS-apparaten kan worden weergegeven. |

>[!NOTE]
>
>De 3D Media WCM-component en de 3D-voorvertoning op de pagina Details van een element zijn niet compatibel met de nieuwste versie van Chrome (97.x). Als u met 3D-elementen wilt werken, gebruikt u Firefox of Safari of een eerdere versie van Chrome (96.x).

## Snel starten: 3D-elementen in dynamische media {#quick-start-three-d}

De volgende geleidelijke werkschemabeschrijving wordt ontworpen om u te helpen snel met 3D activa op Dynamische Media - wijze Scene7 in werking stellen.

>[!IMPORTANT]
>
>3D-elementen worden niet ondersteund in de modus Dynamische media - Hybride.

Alvorens u met 3D activa in Dynamische Media werkt, zorg ervoor dat uw beheerder van Experience Manager de Dynamische Diensten van de Wolk van Media in Dynamische Media - wijze Scene7 reeds heeft toegelaten en gevormd.

Zie [&#x200B; ConfigurE de Dynamische Diensten van de Wolk van Media &#x200B;](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) in het Vormen van Dynamische Media - wijze Scene7 en [&#x200B; Los Dynamische Media problemen op - wijze Scene7 &#x200B;](/help/assets/troubleshoot-dms7.md).

1. **upload 3D activa**

   * [&#x200B; upload uw 3D activa voor gebruik in Dynamische Media &#x200B;](/help/assets/manage-assets.md#uploading-assets).
   * [&#x200B; Ondersteunde 3D dossierformaten voor upload in Dynamische Media &#x200B;](#supported-three-d-file-formats-in-dm).

1. **beheert 3D activa**

   * 3D-middelen organiseren en doorzoeken

      * [&#x200B; organiseer digitale activa &#x200B;](/help/assets/organize-assets.md#organize-digital-assets).
      * [&#x200B; Onderzoek 3D activa &#x200B;](/help/assets/search-assets.md).
      * [&#x200B; de douanevoorspelling van het Gebruik aan de resultaten van het filteronderzoek &#x200B;](/help/assets/search-assets.md#custompredicates).

   * 3D-elementen weergeven

      * [&#x200B; Mening en het in wisselwerking staan met 3D activa &#x200B;](#viewing-three-d-assets).
      * [&#x200B; beheer vooraf ingesteld de Dimensionele kijker &#x200B;](/help/assets/managing-viewer-presets.md).

   * Werken met metagegevens van 3D-elementen

      * [&#x200B; beheer meta-gegevens voor digitale activa &#x200B;](/help/assets/metadata.md).
      * [&#x200B; schema&#39;s van Meta-gegevens &#x200B;](/help/assets/metadata-schemas.md).

1. **publiceer 3D activa**

   * [Statische dynamische media 3D-elementen publiceren](#publishing-three-d-assets)
   * [Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer](#alternate-publish-methods)

## Informatie over het weergeven van en communiceren met 3D-elementen {#viewing-three-d-assets}

In deze sectie wordt beschreven hoe u 3D-elementen op twee verschillende manieren kunt weergeven en gebruiken: van binnen de pagina met elementdetails en van binnen de 3D-mediacomponent in Experience Manager Sites.

De interactieve 3D-viewer bevat onder andere een verzameling interactieve besturingselementen voor camera waarmee u het 3D-element kunt draaien, zoomen en pannen.

De tijd die nodig is om een 3D-element te openen in de weergave Asset Details is afhankelijk van verschillende factoren. Deze factoren zijn onder andere:

* Bandbreedte voor de server.
* Koppelingen naar de server
* Complexiteit van de afbeelding.

Bovendien zijn de mogelijkheden van de clientcomputer, zoals een werkstation, laptop of mobiel aanraakapparaat, ook belangrijk om te overwegen wanneer u de camera interactief manipuleert. Een redelijk krachtig systeem met goede grafische mogelijkheden kan de interactieve 3D-kijkervaring vloeiender en gunstiger maken.

>[!TIP]
>
>U kunt de voorinstelling voor de maatviewer openen in de Viewer Preset Editor om te navigeren door een 3D-element zonder dat u eerst 3D-bestanden hoeft te uploaden. De voorinstelling van de DIMM-viewer heeft een ingebouwd 3D-element waarmee u kunt communiceren.
>
>Zie [&#x200B; vooraf instelt van de kijker beheren &#x200B;](/help/assets/managing-viewer-presets.md).

## Een 3D-element weergeven en interactief werken via de pagina met elementdetails {#viewing-three-d-assets-from-asset-details-page}

Zie ook [&#x200B; activa van de Voorproef gebruikend de softwareinterface &#x200B;](/help/assets/previewing-assets.md).

**om met een 3D activa van de pagina van elementdetails te bekijken en in wisselwerking te staan:**

1. Zorg ervoor dat u 3D-elementen hebt geüpload naar Experience Manager.

   Zie [&#x200B; uw 3D activa voor gebruik in Dynamische Media &#x200B;](/help/assets/manage-assets.md#uploading-assets) uploaden.

1. Ga vanuit Experience Manager op de pagina **[!UICONTROL Navigation]** naar **[!UICONTROL Assets]** > **[!UICONTROL Files]** .
1. Selecteer in de vervolgkeuzelijst **[!UICONTROL View]** rechtsboven op de pagina de optie **[!UICONTROL Card View]** .
1. Navigeer naar een 3D-element dat u wilt weergeven.
1. Selecteer de kaart van het 3D-element.
1. Voer op de pagina met de detailweergave voor het 3D-element een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, selecteert u in de rechterbenedenhoek van de pagina het pictogram Volledig scherm. |   |   |

1. Selecteer **[!UICONTROL Close]** in de rechterbovenhoek van de pagina om terug te keren naar de Assets-pagina.

## Een 3D-element in een 3D-mediacomponent weergeven en hiermee communiceren {#interacting-with-asset-inside-three-d-media-component}

Wanneer de modus **[!UICONTROL Edit]** van een webpagina is geactiveerd, is interactie met een 3D-element niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

>[!IMPORTANT]
>
>U kunt deze taak pas uitvoeren nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd en een 3D-element aan de component hebt toegewezen. Zie [&#x200B; Toevoegend de 3D component van Media aan een Web-pagina &#x200B;](#adding-the-three-d-media-component-to-a-web-page) en [&#x200B; Toewijzend een 3D activa aan een 3D component van Media &#x200B;](#assigning-a-three-d-asset-to-the-component).

Zie ook [&#x200B; activa van de Voorproef gebruikend de softwareinterface &#x200B;](/help/assets/previewing-assets.md).

**om met een 3D activa binnen een 3D component van Media te bekijken en in wisselwerking te staan:**

1. Voer een van de volgende handelingen uit terwijl de modus **[!UICONTROL Edit]** voor een webpagina is geactiveerd:

   * Selecteer **[!UICONTROL Preview]** rechtsboven op de pagina om de modus **[!UICONTROL Preview]** te activeren.
   * Verwijder `/editor.html` uit de pagina-URL in de browser.

   ![&#x200B; 3D activa die binnen de 3D component van Media tonen &#x200B;](/help/assets/assets-dm/3d-asset-in-3d-media.png)
Een volledig interactief 3D-element zoals wordt weergegeven in de modus **[!UICONTROL Preview]** .

1. Voer in de modus **[!UICONTROL Preview]** een van de volgende handelingen uit:

   | Weergave | Beschrijving | Muishandeling | Handeling op het aanraakscherm |
   | --- | --- | --- | --- |
   | **draai uw camera** | Draai de weergave rond de 3D-scène en -objecten. | Klik met de linkermuisknop en sleep. | Druk met één vinger en sleep. |
   | **Pannen uw camera** | U kunt de weergave naar links, rechts, omhoog of omlaag pannen. | Klik met de rechtermuisknop en sleep. | Druk met twee vingers en sleep. |
   | **Gezoem uw camera** | Ga in- en uit gebieden in de 3D-scène. | Schuifwiel. | Kneep met twee vingers. |
   | **herenter uw camera** | Voer de camera opnieuw in op een punt op een object in de 3D-scène. | Dubbelklik. | Dubbelselecteren. |
   | **Terugstellen** | Selecteer in de rechterbenedenhoek van de pagina het pictogram Herstellen om het doelpunt van de weergave te herstellen naar het midden van het 3D-element. Met Herstellen wordt de camera ook dichter bij of verder weg geplaatst om het middel volledig en bij een redelijke weergavegrootte weer te geven. |   |   |
   | **Volledige het schermwijze** | Als u de modus Volledig scherm wilt inschakelen, selecteert u in de rechterbenedenhoek van de pagina het pictogram Volledig scherm. |   |   |

## Informatie over het werken met de 3D-mediacomponent {#working-with-three-d-media-component}

Dynamic Media bevat een Dynamic Media 3D Media-component die u in Adobe Experience Manager Sites kunt gebruiken om interactieve weergave van 3D-modellen op uw webpagina&#39;s mogelijk te maken.

* [De 3D-mediacomponent toevoegen aan de paginasjabloon](#adding-three-d-media-component-to-page-template)
* [De 3D-mediacomponent toevoegen aan een webpagina](#adding-the-three-d-media-component-to-a-web-page)
   * [Optioneel - De 3D-mediacomponent configureren](#configuring-the-three-d-component)
* [Een 3D-element toewijzen aan de 3D-mediacomponent](#assigning-a-three-d-asset-to-the-component)

## De 3D-mediacomponent toevoegen aan de paginasjabloon {#adding-three-d-media-component-to-page-template}

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL General]** > **[!UICONTROL Templates]** .
1. Navigeer naar de paginasjabloon waarin u de 3D-component wilt inschakelen en selecteer de sjabloon.
1. Selecteer **[!UICONTROL Edit]** zodat u de sjabloon kunt openen.
1. Selecteer in de rechterbovenhoek van de pagina de optie **[!UICONTROL Structure]** -modus in het keuzemenu als deze nog niet actief is.

   ![&#x200B; 3d-media-component-structuur &#x200B;](/help/assets/assets-dm/3d-media-component-structure.png)

1. Selecteer een leeg gebied in het **[!UICONTROL Layout Container]** -gebied, zodat u dit kunt selecteren en de bijbehorende werkbalk kunt openen.
1. Selecteer op de werkbalk het pictogram **[!UICONTROL Policy]** om het dialoogvenster **[!UICONTROL Policy Editor]** te openen.
1. Blader in de sectie **[!UICONTROL Properties]** onder de tab **[!UICONTROL Allowed Components]** naar **[!UICONTROL Dynamic Media]** , vouw de lijst uit en controleer **[!UICONTROL 3D Media]** .
1. Selecteer **[!UICONTROL Done]** om de wijzigingen op te slaan en **[!UICONTROL Policy Editor]** te sluiten.

   U kunt de component Dynamische media 3D Media nu op alle pagina&#39;s plaatsen die dit malplaatje gebruiken.

## De 3D Media-component toevoegen aan een webpagina {#adding-the-three-d-media-component-to-a-web-page}

Als u Experience Manager gebruikt als het webcontentbeheersysteem, kunt u 3D-elementen aan uw webpagina&#39;s toevoegen met behulp van de 3D Media-component.

Zie ook [&#x200B; Dynamische activa van Media op pagina&#39;s &#x200B;](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

**om de 3D component van Media op een Web-pagina toe te voegen:**

1. Open Experience Manager Sites en selecteer de webpagina waaraan u de Dynamic Media 3D Media-component wilt toevoegen.
1. Selecteer het pictogram **[!UICONTROL Edit]** (potlood) zodat u de pagina in de paginaeditor kunt openen. Zorg ervoor dat de modus **[!UICONTROL Edit]** rechtsboven op de pagina is geselecteerd.

   ![&#x200B; 3d-media-component-voeg toe &#x200B;](/help/assets/assets-dm/3d-media-component-edit.png)

1. Selecteer op de werkbalk het pictogram Zijpaneel om de weergave van het deelvenster in of uit te schakelen.

1. Selecteer in het zijpaneel het pictogram met het plusteken om de lijst van **[!UICONTROL Components]** te openen.

   ![&#x200B; 3d-media-component-belemmering-daling &#x200B;](/help/assets/assets-dm/3d-assets-filter.png)

1. Sleep de component **[!UICONTROL 3D Media]** van de lijst **[!UICONTROL Components]** naar de locatie op de pagina waar u de 3D-viewer wilt weergeven.

U kunt nu een 3D-element aan de component toewijzen.

Zie [&#x200B; activa toewijzen 3D aan de 3D component van Media &#x200B;](#assigning-a-three-d-asset-to-the-component).

### Optioneel - De 3D-mediacomponent configureren {#configuring-the-three-d-component}

1. Selecteer in de Experience Manager Sites-pagina-editor de component **[!UICONTROL 3D Media Viewer]** die u eerder aan de pagina hebt toegevoegd.
1. Selecteer het pictogram **[!UICONTROL Configuration]** (moersleutel) zodat u het dialoogvenster voor componentconfiguratie kunt openen.

   ![&#x200B; 3d-media-component-config &#x200B;](/help/assets/assets-dm/3d-media-component-config.png)

1. Selecteer in het dialoogvenster 3D-media in de vervolgkeuzelijst Voorinstelling viewer de optie **[!UICONTROL Dimensional]** om de voorinstelling voor de maatviewer toe te wijzen aan de component.

   ![&#x200B; 3d-media-component-geef-config uit &#x200B;](/help/assets/assets-dm/3d-media-component-edit-config.png)

1. Selecteer in de rechterbovenhoek het vinkje waarop u de wijzigingen wilt opslaan.

## Een 3D-element toewijzen aan de 3D-mediacomponent {#assigning-a-three-d-asset-to-the-component}

Nadat u een 3D-mediacomponent aan een webpagina hebt toegevoegd, kunt u er een 3D-element aan toewijzen.

Zie [&#x200B; de 3D component van Media aan een Web-pagina &#x200B;](#adding-the-three-d-media-component-to-a-web-page) toevoegen.

**om een 3D activa aan de 3D component van Media toe te wijzen:**

1. Selecteer in de Experience Manager Sites-pagina-editor het pictogram **[!UICONTROL Assets]** dat u wilt openen **[!UICONTROL Assets]** in het zijpaneel.
1. Selecteer **[!UICONTROL 3D]** in de vervolgkeuzelijst om alleen 3D-elementbestandstypen weer te geven.
1. Zoek in het zijpaneel naar het 3D-element dat u wilt weergeven op de pagina die u bewerkt.
1. Sleep het 3D-element van het zijpaneel van Assets naar de component **[!UICONTROL 3D Media]** die u eerder aan de pagina hebt toegevoegd.

   ![&#x200B; wijst 3D activa aan de 3D component van Media &#x200B;](/help/assets/assets-dm/3d-asset-add.png) toe

>[!NOTE]
>
>In de Experience Manager Sites **[!UICONTROL Edit]** -modus wordt het 3D-element weergegeven in de 3D-mediacomponent, maar interactie met het element is niet mogelijk. Als u het element interactief wilt maken, kunt u de functie **[!UICONTROL Preview]** gebruiken om de webpagina in de pagina-editor weer te geven met volledige toegang tot de functionaliteit van de 3D Media-component.

## Statische dynamische media 3D-elementen publiceren {#publishing-three-d-assets}

De dynamische Media keurt diverse 3D dossierformaten goed die als *statische inhoud* in Dynamische Media worden gesteund. De statische inhoud betekent dat u 3D activa kunt uploaden en publiceren, maar er is geen steun voor *veranderlijke beeldvorming* of beeld die dat met 3D activa wordt geassocieerd. De reden hiervoor is dat Dynamic Media Imaging Server 3D-indelingen niet herkent. Nadat u een 3D-element hebt gepubliceerd in dynamische media, hebt u dus een directe URL die u kunt kopiëren. De URL voor het 3D-element volgt de gebruikelijke URL-structuur voor dynamische media. In tegenstelling tot traditionele afbeeldingselementen in Dynamic Media kunt u echter geen parameters in de URL van het element bewerken.

Zie ook [&#x200B; een URL voor statische activa &#x200B;](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-a-static-asset) verkrijgen.

In **[!UICONTROL Card View]** wordt een klein globpictogram direct onder de naam van een element weergegeven en links van de datum en tijd om aan te geven dat het is gepubliceerd. In de **[!UICONTROL List View]** geeft een kolom **[!UICONTROL Published]** aan welke assets zijn gepubliceerd en welke niet.

Als u Experience Manager als uw WCM gebruikt, gebruikt u deze publicatiemethode om de Dynamic Media 3D-elementen rechtstreeks op uw webpagina toe te voegen.

Zie ook [&#x200B; de Dynamische activa van Media publiceren &#x200B;](publishing-dynamicmedia-assets.md).

Zie ook [&#x200B; publiceren pagina&#39;s &#x200B;](/help/sites-authoring/publishing-pages.md).

**om statische Dynamische Media 3D activa te publiceren:**

1. Open een 3D-element (GLB-, OBJ- of STL-bestandsindeling), zodat u dit kunt bekijken op de pagina met elementdetails.
1. Selecteer **[!UICONTROL Quick Publish]** op de werkbalk.

   ![&#x200B; 3d-activa-snel-publiceer &#x200B;](/help/assets/assets-dm/3d-asset-quick-publish.png)

1. Selecteer **[!UICONTROL Close]** om het dialoogvenster te sluiten en terug te keren naar de pagina met elementdetails.
1. Selecteer **[!UICONTROL Renditions]** in de vervolgkeuzelijst links van de bestandsnaam van het 3D-element.

   ![&#x200B; 3d-activa-vertoningen &#x200B;](/help/assets/assets-dm/3d-asset-renditions.png)

1. Selecteer **[!UICONTROL original]**. Wanneer een 3D-element wordt gepubliceerd (of geactiveerd), wordt de knop **[!UICONTROL URL]** linksonder op de pagina weergegeven als aan alle volgende 3D-elementvoorwaarden is voldaan:
   * Het 3D-element heeft een ondersteunde indeling (GLB, OBJ, STL en USDZ).
   * Het 3D element werd opgenomen in het Dynamische Systeem van de Productie van het Beeld van Media (IPS).
   * Het 3D-element wordt gepubliceerd.

   ![&#x200B; 3d-activa-url &#x200B;](/help/assets/assets-dm/3d-asset-url.png)

1. Selecteer **[!UICONTROL URL]** om de directe productie-URL van het 3D-element weer te geven, die u kunt kopiëren en gebruiken op webpagina&#39;s.

### Alternatieve methoden voor het publiceren van Dynamic Media 3D-elementen met de Dimensional-viewer {#alternate-publish-methods}

Gebruik de volgende twee methodes om Dynamische Media 3D activa te publiceren als u *niet* Experience Manager als uw WCM gebruikt.

* **[!UICONTROL URL]** - Gebruik **[!UICONTROL URL]** als u een systeem voor webcontentbeheer van derden gebruikt en u dynamische media 3D-elementen met de DIMM-viewer wilt koppelen aan uw webpagina&#39;s.

  Zie [&#x200B; Verbinding URLs aan uw Webtoepassing &#x200B;](/help/assets/linking-urls-to-yourwebapplication.md#obtaining-a-url-for-an-asset).

* **[!UICONTROL Embed]** - Gebruik **[!UICONTROL Embed]** als u een dynamisch Media 3D-element wilt weergeven dat is ingesloten op een webpagina met de DIMM-viewer. U kopieert de insluitcode naar het klembord, zodat u deze op uw webpagina&#39;s kunt plakken. Het bewerken van de code is niet toegestaan in het dialoogvenster **[!UICONTROL Embed]**.

  Zie [&#x200B; de Dynamische Video van Media, de kijker van het Beeld, of de kijker van de Afmeting op een Web-pagina &#x200B;](/help/assets/embed-code.md#embedding-the-video-or-image-viewer-on-a-web-page) inbedden.
