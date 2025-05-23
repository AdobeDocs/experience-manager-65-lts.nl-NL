---
title: Algemene instellingen voor dynamische media configureren
description: Leer hoe u Algemene instellingen in dynamische media beheert. U kunt hier de naam van de publicatieserver en de naam van de oorspronkelijke server instellen en een optie voor het overschrijven van afbeeldingen instellen. Er zijn ook standaard uploadopties voor onscherpe maskers van afbeeldingen en uploadopties voor de manier waarop u PostScript-, Adobe Photoshop-, PDF- en Adobe Illustrator-bestanden wilt verwerken.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: administering
content-type: reference
feature: Image Profiles
role: User, Admin
mini-toc-levels: 4
solution: Experience Manager, Experience Manager Assets
exl-id: 99cd5f46-f1aa-46f5-b112-311724e00490
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2315'
ht-degree: 0%

---

# Algemene instellingen voor dynamische media configureren

Het configureren van **[!UICONTROL Dynamic Media General Settings]** is alleen beschikbaar als:

* U stelt Dynamische Media op wijze Scene7 in werking. Zie [ Dynamische Media op wijze Scene7 ](/help/assets/config-dms7.md#enabling-dynamic-media-in-scene-mode) toelaten.
* U hebt *bestaand* **[!UICONTROL Dynamic Media Configuration]** (in **[!UICONTROL Cloud Services]**) in Adobe Experience Manager 6.5.11 of hierboven. Zie [ een Dynamische Configuratie van Media in de Diensten van de Wolk ](/help/assets/config-dms7.md#configuring-dynamic-media-cloud-services) creëren.
* U bent een Experience Manager-systeembeheerder met beheerdersrechten.

Dynamische media algemene instellingen zijn bedoeld voor gebruik door ervaren websiteontwikkelaars en -programmeurs. Adobe Dynamic Media raadt gebruikers die deze publicatie-instellingen wijzigen aan op de hoogte te zijn van Dynamic Media op Adobe Experience Manager en de basistechnologie voor beeldbewerking.

Bij het maken van accounts biedt Adobe Dynamic Media automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account.

Op de pagina Dynamische media publiceren stelt u standaardinstellingen in die bepalen hoe elementen van Adobe Dynamic Media-servers worden geleverd aan websites of toepassingen. Als er geen instelling is opgegeven, levert de Adobe Dynamic Media-server een element op basis van een standaardinstelling die is geconfigureerd op de pagina Dynamische media publiceren-instelling.

Zie ook [ Facultatief - Opstelling en configuratie van Dynamische Media - Scene7 wijzemontages ](/help/assets/config-dms7.md#optional-setup-and-configuration-of-dynamic-media-scene7-mode-settings) voor meer facultatieve configuratietaken.

>[!NOTE]
>
>Dynamic Media Classic uitbreiden naar Dynamic Media op Adobe Experience Manager? De Algemene pagina van Montages en [ publiceren de pagina van de Opstelling ](/help/assets/dm-publish-settings.md) in Dynamische Media wordt pre-bevolkt met de waarden die van uw rekening van Dynamic Media Classic worden genomen. De uitzonderingen zijn alle waarden die worden vermeld onder **[!UICONTROL Default upload options]** gebied van de Algemene pagina van Montages. Deze waarden staan al in Experience Manager. Alle wijzigingen die u onder **[!UICONTROL Default upload options]** aanbrengt in een van de vijf tabbladen via de Experience Manager-gebruikersinterface, worden daarom weerspiegeld in Dynamic Media, niet in Dynamic Media Classic. Alle andere montages en waarden in de Algemene pagina van Montages en [ publiceren de pagina van de Opstelling ](/help/assets/dm-publish-settings.md) wordt gehandhaafd tussen Dynamic Media Classic en Dynamische Media op Experience Manager.

**om Dynamische Media Algemene Montages te vormen:**

1. Selecteer in de Experience Manager Auteur-modus het Experience Manager-logo voor toegang tot de algemene navigatieconsole.
1. Selecteer in de linkertrack het pictogram Gereedschappen en ga vervolgens naar **[!UICONTROL Assets]** > **[!UICONTROL Dynamic Media General Settings]** .
1. Stel op de pagina Server de opties **[!UICONTROL Published Server Name]** en **[!UICONTROL Origin Server Name]** in en gebruik vervolgens de vijf tabbladen om de standaardopties voor het uploaden van afbeeldingen te configureren voor Beeldbewerking en voor Postscript-, Photoshop-, PDF- en Illustrator-bestanden.

   * [Server](#server-general-setting)
   * [Uploaden naar toepassing](#upload-to-application)
   * [ Beeld die ](#image-editing-tab) tabel uitgeeft
   * [ PostScript ](#postscript-tab) lusje
   * [ Photoshop ](#photoshop-tab) lusje
   * [ PDF ](#pdf-tab) lusje
   * [ Illustrator ](#illustrator-tab) lusje

   ![ Dynamische pagina van de Montages van Media Algemene ](/help/assets/assets-dm/dm-general-settings.png)
   *Dynamische pagina van de Montages van Media Algemene, met het **[!UICONTROL Image Editing]**&#x200B;geselecteerde lusje.*<br><br>

1. Wanneer u klaar bent, selecteert u **[!UICONTROL Save]** in de rechterbovenhoek van de pagina.

## Server {#server-general-setting}

Bij het maken van accounts biedt Adobe Dynamic Media automatisch de toegewezen servers voor uw bedrijf. Deze servers worden gebruikt om URL-tekenreeksen voor uw website en toepassingen samen te stellen. Deze URL-aanroepen gelden specifiek voor uw account.

| Optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Published Server Name]** | Vereist.<br> de naam moet `https://` in de weg gebruiken.<br> Deze server is de levende die server CDN (het Netwerk van de Levering van de Inhoud) in alle systeem-geproduceerde vraag wordt gebruikt URL die voor uw rekening specifiek is. Wijzig deze servernaam alleen als u hiervoor instructies hebt gekregen van de technische ondersteuning van Adobe. |
| **[!UICONTROL Origin Server Name]** | Vereist.<br> Deze server wordt gebruikt voor het testen van de kwaliteitsverzekering slechts. Wijzig deze servernaam alleen als hiervoor instructies zijn gegeven door de technische ondersteuning van Adobe. |

## Uploaden naar toepassing {#upload-to-application}

* **[!UICONTROL Overwrite Images]**

  Adobe Dynamic Media staat niet toe dat twee bestanden dezelfde naam hebben. De dynamische media-id van Adobe van elk item (de naam van de afbeelding min de extensie van de bestandsnaam) moet uniek zijn. Vanwege deze regel wordt in **[!UICONTROL Upload to Application]** overschreven. Het exacte effect van deze optie is afhankelijk van de opgegeven optie Afbeeldingen overschrijven die u hebt gekozen. Met deze opties geeft u op hoe vervangende afbeeldingen worden geüpload: of ze de oorspronkelijke afbeeldingen vervangen of dubbele afbeeldingen worden. Dubbele afbeeldingen krijgen een nieuwe naam met een `-1` . De naam van `chair.tif` wordt bijvoorbeeld gewijzigd in `chair-1.tif` . Deze opties zijn van toepassing op afbeeldingen die naar een andere map zijn geüpload dan het origineel of afbeeldingen met een andere bestandsnaamextensie dan het origineel, zoals JPG, TIF of PNG.

  >[!NOTE]
  >
  >Selecteer de optie Afbeeldingen overschrijven **[!UICONTROL Overwrite in current folder, same base name/extension]** om de consistentie met Experience Manager te behouden.

  | Afbeeldingen overschrijven, optie | Beschrijving |
  | --- | --- |
  | **[!UICONTROL Overwrite in current folder, same base name/extension]** | *Gebrek* voor nieuwe Dynamische slechts rekeningen van Media.<br> deze optie is de strengste regel voor vervanging. Hiervoor moet u de vervangende afbeelding uploaden naar dezelfde map als het origineel en moet de vervangende afbeelding dezelfde bestandsnaamextensie hebben als het origineel. Als niet aan deze vereisten wordt voldaan, wordt een dubbel gecreeerd.<br>*om consistentie met Experience Manager te handhaven, selecteer deze optie*. |
  | **[!UICONTROL Overwrite in current folder, same base name regardless of extension]** | U moet de vervangende afbeelding uploaden naar dezelfde map als het origineel, maar de bestandsnaamextensie kan afwijken van het origineel. bijvoorbeeld stoel.tif vervangt stoel.jpg. |
  | **[!UICONTROL Overwrite in any folder, same base asset name/extension]** | Vereist dat de vervangende afbeelding dezelfde bestandsnaamextensie heeft als de oorspronkelijke afbeelding (bijvoorbeeld stoel.jpg moet de naam stoel.jpg vervangen, niet stoel.tif). U kunt de vervangende afbeelding echter naar een andere map uploaden dan het origineel. De bijgewerkte afbeelding bevindt zich in de nieuwe map. Het bestand is niet meer gevonden op de oorspronkelijke locatie. |
  | **[!UICONTROL Overwrite in any folder, same base asset name regardless of extension]** | Deze optie is de meest inclusieve vervangingsregel. U kunt een vervangende afbeelding uploaden naar een andere map dan het origineel, een bestand met een andere bestandsnaamextensie uploaden en het oorspronkelijke bestand vervangen. Als het oorspronkelijke bestand zich in een andere map bevindt, bevindt de vervangende afbeelding zich in de nieuwe map waarnaar het is geüpload. |

* **[!UICONTROL Preserve Crop]**

  Hiermee regelt u het behoud van bestaande handmatige snijddefinities.

  Zie ook `preserveCrop` in [ UploadPostJob ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-upload-post-job.html?lang=nl-NL) en [ ReprocessAssetsJob ](https://experienceleague.adobe.com/docs/dynamic-media-developer-resources/image-production-api/data-types/r-reprocess-assets-job.html?lang=nl-NL), zowel in de Dynamische Gids van de Verwijzing van de Kijkers van Media.

## Standaardopties voor uploaden {#default-upload-options}

### Tabblad Beeldbewerking {#image-editing-tab}

Met dit filter kunt u een verscherpingsfiltereffect op de uiteindelijke gedownsampelde afbeelding perfectioneren. Hiermee kunt u de intensiteit van het effect, de straal van het effect (gemeten in pixels) en een drempel voor het contrast instellen die wordt genegeerd.

Voor het effect Onscherp masker worden dezelfde opties gebruikt als voor het filter Onscherp masker van Photoshop. In tegenstelling tot wat de naam suggereert, is Onscherp masker een verscherpingsfilter.

| Onscherpe maskeropties | Beschrijving |
| --- | --- |
| **[!UICONTROL Amount]** | Vereist.<br> controleert de hoeveelheid contrast die op randpixel wordt toegepast.<br> denk van het als de intensiteit van het effect. Het belangrijkste verschil tussen de waarden voor Onscherp masker in Adobe Dynamic Media en de waarden voor de hoeveelheid in Adobe Photoshop is dat Photoshop een bereik heeft van 1% tot 500%. In Adobe Dynamic Media is het waardebereik `0.0` tot `5.0` . Een waarde van 5,0 in Adobe Dynamic Media is het ruwe equivalent van 500% in Photoshop, een waarde van 0,9 is het equivalent van 90%, enzovoort. |
| **[!UICONTROL Radius]** | Vereist.<br> controleert de straal van het effect.<br> Het waardebereik is `0` tot `250` . Het effect wordt op alle pixels in een afbeelding uitgevoerd en wordt vanuit alle pixels in alle richtingen uitgestraald. De straal wordt gemeten in pixels. Als u bijvoorbeeld een vergelijkbaar verscherpingseffect wilt toepassen op een afbeelding van 2000 x 2000 pixels en een afbeelding van 500 x 500 pixels, stelt u een straal van twee pixels in voor de afbeelding van 2000 x 2000 pixels. Stel vervolgens een straalwaarde in van 1 pixel in de afbeelding van 500 x 500 pixels. Een hogere waarde wordt gebruikt voor een afbeelding met meer pixels. |
| **[!UICONTROL Threshold]** | Vereist.<br> de Drempel is een waaier van contrast die wordt genegeerd wanneer de filter Onscherp Masker wordt toegepast. Dit effect is belangrijk, zodat er geen &#39;ruis&#39; wordt toegevoegd aan een afbeelding wanneer dit filter wordt gebruikt. Het waardebereik is `0` - `255` . Dit is het aantal helderheidsstappen in een grijswaardenafbeelding. `0`=zwart, `128`=50% grijs en `255`=wit.<br> de drempelwaarde van A van `12` negeert lichte variaties is de helderheid van de huidskleur om het toevoegen van lawaai te vermijden, maar nog toevoegt randcontrast aan contrasterende gebieden zoals waar de wimpers huid ontmoeten.<br> als u een foto van iemands gezicht hebt, beïnvloedt het Onscherp Masker de contrasterende delen van het beeld. Bijvoorbeeld, waar wimpers en huid samenkomen om een duidelijk gebied van contrast tot stand te brengen, en de vlotte huid zelf. Zelfs de meest vloeiende skin vertoont subtiele wijzigingen in helderheidswaarden. Als u geen drempelwaarde gebruikt, accentueert het filter deze subtiele wijzigingen in de pixels van de skin. Er wordt op zijn beurt een lawaai en ongewenst effect gecreëerd terwijl het contrast op de wimpers wordt verhoogd, waardoor de scherpte wordt vergroot.<br> om deze kwestie te vermijden, wordt een drempelwaarde geïntroduceerd die het filter vertelt om pixel te negeren die contrast, zoals vlotte huid niet dramatisch veranderen.<br> in zipper grafisch vroeger getoond, merk de textuur naast de ritppers op. Ruis in de afbeelding wordt weergegeven omdat de drempelwaarden te laag waren om de ruis te onderdrukken. |
| **[!UICONTROL Monochrome]** | Selecteer deze optie om de helderheid (intensiteit) van een afbeelding zonder scherp masker te wijzigen.<br> schrap aan unshark-masker elke kleurencomponent afzonderlijk. |

Zie ook [ scherp beelden in de Dynamische Media van Adobe en op de Server van het Beeld ](/help/assets/assets/sharpening_images.pdf).

### Het tabblad PostScript {#postscript-tab}

U kunt Adobe PostScript®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.

U kunt Adobe PostScript®-bestanden (EPS) gebruiken in Adobe Dynamic Media. Adobe Dynamic Media biedt opdrachten voor het configureren van deze bestanden tijdens het uploaden.

Wanneer u PostScript (EPS)-afbeeldingsbestanden uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen.

| PostScript, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | Kies Rasteren om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| **[!UICONTROL Maintain transparent background in rendered images]** | Hiermee blijft de achtergrondtransparantie van het bestand behouden. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de RGB-kleurruimte.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |

### Het tabblad Photoshop {#photoshop-tab}

U kunt sjablonen maken van Adobe® Photoshop®-bestanden, lagen behouden, opgeven hoe lagen worden genoemd, tekst extraheren en opgeven hoe afbeeldingen worden verankerd in sjablonen.

| Photoshop, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Maintain layers]** | Hiermee worden de lagen in de PSD, indien aanwezig, uitgelijnd op afzonderlijke elementen. De elementlagen blijven gekoppeld aan de PSD. U kunt ze weergeven door het PSD-bestand te openen in de Gedetailleerde weergave en het deelvenster Lagen te selecteren. Zie Lagen weergeven en bewerken in een PSD-bestand. |
| **[!UICONTROL Create template]** | Maakt een sjabloon op basis van de lagen in het PSD-bestand. |
| **[!UICONTROL Extract text]** | Extraheert de tekst zodat gebruikers naar tekst in een viewer kunnen zoeken. |
| **[!UICONTROL Extend layers to background size]** | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag. |
| **[!UICONTROL Layer naming]** | Hiermee vergroot u de grootte van de uitgesneden afbeeldingslagen tot de grootte van de achtergrondlaag.<br>・ **[!UICONTROL Layer name]** - De afbeeldingen krijgen een naam na hun laagnamen in het PSD-bestand. Een laag met de naam Prijscode in het oorspronkelijke PSD-bestand wordt bijvoorbeeld een afbeelding met de naam Prijscode. Als de laagnamen in het PSD-bestand echter standaard Photoshop-laagnamen zijn (Achtergrond, Laag 1, Laag 2, enzovoort), krijgen de afbeeldingen een naam na hun laagnummers in het PSD-bestand. <br>・ **[!UICONTROL Photoshop and layer number]** - De afbeeldingen krijgen een naam na hun laagnummer in het PSD-bestand, waarbij de namen van de oorspronkelijke lagen worden genegeerd. Afbeeldingen krijgen de naam Photoshop en een toegevoegd laagnummer. De tweede laag van een bestand met de naam `Spring Ad.psd` krijgt bijvoorbeeld de naam `Spring Ad_2` , zelfs als het bestand een andere naam heeft dan de standaardnaam in Photoshop.<br>・ **[!UICONTROL Photoshop and layer name]** - De afbeeldingen krijgen een naam na het PSD-bestand, gevolgd door de laagnaam of het laagnummer. Het laagnummer wordt gebruikt als de laagnamen in het PSD-bestand standaard Photoshop-laagnamen zijn. Een laag met de naam `Price Tag` in een PSD-bestand met de naam `SpringAd` krijgt bijvoorbeeld de naam `Spring Ad_Price Tag` . Een laag met de standaardnaam Laag 2 wordt genoemd `Spring Ad_2`. |
| **[!UICONTROL Anchor]** | Geef op hoe afbeeldingen worden verankerd in sjablonen die worden gegenereerd op basis van de laagsamenstelling die uit het PSD-bestand is samengesteld. Standaard is het anker het middelpunt. Met een middelste anker kunnen vervangende afbeeldingen dezelfde ruimte het beste vullen, ongeacht de hoogte-breedteverhouding van de vervangende afbeelding. Afbeeldingen met een ander aspect dat deze afbeelding vervangt, nemen bij het verwijzen naar de sjabloon en het gebruik van parametervervanging in feite dezelfde ruimte in. Schakel over naar een andere instelling als de vervangende afbeeldingen de toegewezen ruimte in de sjabloon moeten vullen. |

### Het tabblad PDF {#pdf-tab}

U kunt de bestanden omzetten in pixels, zoekwoorden en koppelingen extraheren, de resolutie instellen en een kleurruimte kiezen.

| PDF, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | ・ **[!UICONTROL None]** - De PDF wordt niet verwerkt.<br>・ **[!UICONTROL Thumbnail]** - Ript elke pagina in het PDF-bestand en zet het om in een miniatuurafbeelding.<br> ・ **[!UICONTROL Rasterize]** - Ript de pagina&#39;s in het PDF-bestand en zet vectorafbeeldingen om in bitmapafbeeldingen. Kies deze optie om een eCatalog te maken. |
| **[!UICONTROL Extract]** | ・ **[!UICONTROL None]** - Er worden geen zoekwoorden of koppelingen uit de PDF geëxtraheerd.<br>・ **[!UICONTROL Search words]** - Extraheert zoekwoorden uit het PDF-bestand, zodat het bestand kan worden doorzocht op trefwoord in een eCatalog-viewer.<br>・ **[!UICONTROL Links]** - Extraheert koppelingen uit de PDF-bestanden en converteert deze naar afbeeldingen met hyperlinks die worden gebruikt in een eCatalog-viewer.<br>・ **[!UICONTROL Search words and links]** - Extraheert zowel zoekwoorden als koppelingen voor gebruik in een eCatalog-viewer. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het PDF-bestand worden weergegeven. De standaardwaarde is 150. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het PDF-bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de RGB-kleurruimte.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |

### Het tabblad Illustrator {#illustrator-tab}

U kunt Adobe Illustrator®-bestanden rasteren, transparante achtergronden behouden, een resolutie kiezen en een kleurruimte kiezen.

U kunt Adobe® Illustrator® (AI)-bestanden gebruiken in Adobe Dynamic Media. Adobe Dynamic Media biedt opdrachten voor het configureren van deze bestanden tijdens het uploaden.

Wanneer u Illustrator-afbeeldingsbestanden (AI) uploadt, kunt u deze op verschillende manieren opmaken. U kunt de bestanden rasteren, de transparante achtergrond behouden, een resolutie kiezen en een kleurruimte kiezen. Opties voor de opmaak van PostScript- en Illustrator-bestanden zijn beschikbaar op het scherm Uploaden onder PostScript-opties en Illustrator-opties in het vak Opties voor uploaden.


| Illustrator, optie | Beschrijving |
| --- | --- |
| **[!UICONTROL Processing]** | Kies Rasteren om vectorafbeeldingen in het bestand om te zetten in de bitmapindeling. |
| **[!UICONTROL Maintain transparent background in rendered images]** | Hiermee blijft de achtergrondtransparantie van het bestand behouden. |
| **[!UICONTROL Resolution (pixel/inch)]** | Hiermee bepaalt u de resolutie-instelling. Deze instelling bepaalt hoeveel pixels per inch in het bestand worden weergegeven. |
| **[!UICONTROL Color space]** | ・ **[!UICONTROL Detect automatically]** - Behoudt de kleurruimte van het bestand.<br>・ **[!UICONTROL Force as RGB]** - Converteert naar de RGB-kleurruimte.<br>・ **[!UICONTROL Force as CMYK]** - Converteert naar de CMYK-kleurruimte.<br>・ **[!UICONTROL Force as Grayscale]** - Zet om in de grijswaardenkleurruimte. |
