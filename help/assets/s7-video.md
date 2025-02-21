---
title: Video
description: In deze video's leert u over het gecentraliseerde beheer van video-elementen in Adobe Experience Manager Assets, waar u video's voor automatische codering kunt uploaden naar Dynamic Media Classic en rechtstreeks vanuit Experience Manager Assets toegang kunt krijgen tot Dynamic Media Classic-video's. Door Dynamic Media Classic-video-integratie wordt het bereik van geoptimaliseerde video uitgebreid naar alle schermen.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: managing-assets
content-type: reference
role: User, Admin
mini-toc-levels: 3
feature: Video
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1496'
ht-degree: 0%

---

# Video {#video}

Adobe Experience Manager Assets biedt gecentraliseerd beheer van video-elementen waarmee u video&#39;s rechtstreeks naar Assets kunt uploaden voor automatische codering naar Dynamic Media Classic en Dynamic Media Classic-video&#39;s rechtstreeks vanuit Assets kunt openen voor het ontwerpen van pagina&#39;s.

Dynamic Media Classic-videointegratie breidt het bereik van geoptimaliseerde video uit naar alle schermen (automatische detectie van apparaat en bandbreedte).

* De component **[!UICONTROL Scene7 Video]** voert automatisch apparaat- en bandbreedtedetectie uit om de juiste indeling en video van de juiste kwaliteit af te spelen op desktopcomputers, tablets en mobiele apparaten.
* Assets - U kunt adaptieve videosets opnemen in plaats van alleen afzonderlijke video-elementen. Een adaptieve videoset bevat alle video-uitvoeringen die nodig zijn om video naadloos af te spelen op meerdere schermen. Een adaptieve videoreeks groepeert versies van de zelfde video die bij verschillende beetjetarieven en formaten zoals 400 kbps, 800 kbps, en 1000 kbps worden gecodeerd. U gebruikt een adaptieve videoset, samen met de S7-videocomponent, voor adaptieve videostreaming op meerdere schermen, zoals desktopcomputers, iOS, Android™, BlackBerry® en mobiele Windows-apparaten.
<!-- See [Scene7 documentation about adaptive video sets for more information](https://help.adobe.com/en_US/scene7/using/WS53492AE1-6029-45d8-BF80-F4B5CF33EB08.html). -->

## Info over FFMPEG en Dynamic Media Classic {#about-ffmpeg-and-scene}

Het standaardproces voor videocodering is gebaseerd op het gebruik van de op FFMPEG gebaseerde integratie met videoprofielen. Daarom bevat de uit-van-de-doos workflow voor DAM-opname de volgende twee op ffmpeg gebaseerde workflowstappen:

* FMPEG-miniaturen
* FFMPEG-codering

Als u de integratie met Dynamic Media Classic inschakelt en configureert, worden deze twee workflowstappen niet automatisch verwijderd of gedeactiveerd uit de workflow voor het innemen van DAM-bestanden die buiten de box valt. Als u de op FFMPEG gebaseerde videocodering al in Adobe Experience Manager gebruikt, is het waarschijnlijk dat FFMPEG is geïnstalleerd in uw ontwerpomgeving. In dit geval wordt een nieuwe video die met DAM wordt ingevoerd, twee keer gecodeerd: één keer van de FFMPEG-codeermodule en één keer van de Dynamic Media Classic-integratie.

Als u op FFMPEG-Gebaseerde videocodering in Experience Manager hebt gevormd en FFMPEG geïnstalleerd, adviseert Adobe dat u de twee werkschema&#39;s van FFMPEG uit uw DAM inname werkschema&#39;s verwijdert.

## Ondersteunde indelingen {#supported-formats}

De volgende formaten worden gesteund voor de Video component Scene7:

* F4V H.264
* MP4 H.264

## Bepaal waar u de video wilt uploaden {#deciding-where-to-upload-your-video}

Bepaal waar u uw video-elementen wilt uploaden afhankelijk van het volgende:

* Hebt u een workflow voor het video-element nodig?
* Hebt u versiebeheer nodig voor het video-element?

Als het antwoord op een van deze vragen &quot;ja&quot; is, uploadt u uw video rechtstreeks naar Adobe DAM. Als het antwoord op beide vragen &quot;nee&quot; is, uploadt u uw video rechtstreeks naar Dynamic Media Classic. Het werkschema voor elk scenario wordt beschreven in de volgende sectie.

### Als u de video rechtstreeks uploadt naar Adobe DAM {#if-you-are-uploading-your-video-directly-to-adobe-dam}

Als u een workflow of versie voor uw middelen nodig hebt, uploadt u deze eerst naar Adobe DAM. Hieronder vindt u de aanbevolen workflow:

1. Upload het video-element naar Adobe DAM en codeer en publiceer het automatisch naar Dynamic Media Classic.
1. Open in Experience Manager video-elementen op het tabblad **[!UICONTROL Movies]** van de Inhoudszoeker in WCM.
1. Auteur met **[!UICONTROL Scene7 Video]** of **[!UICONTROL Foundation Video]** component.

### Als u uw video uploadt naar Dynamic Media Classic {#if-you-are-uploading-your-video-to-scene}

Als u geen werkschema of het versioning voor uw activa nodig hebt, upload uw activa aan Scene7. Hieronder vindt u de aanbevolen workflow:

1. In Dynamic Media Classic, [ opstelling een geplande FTP uploadend en het coderen aan Scene7 (systeem geautomatiseerd) ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/upload-publish/uploading-files.html#upload-files-using-via-ftp).
1. Open in Experience Manager video-elementen op het tabblad **[!UICONTROL Scene7]** van de Inhoudszoeker in WCM.
1. Auteur met de component **[!UICONTROL Scene7 Video]** .

## Integratie met Scene7-video configureren {#configuring-integration-with-scene-video}

1. Navigeer in **[!UICONTROL Cloud Services]** naar de **[!UICONTROL Scene7]** -configuratie en selecteer **[!UICONTROL Edit]** .
1. Selecteer de tab **[!UICONTROL Video]** .

   ![ chlimage_1-363 ](assets/chlimage_1-363.png)

   >[!NOTE]
   >
   >Het tabblad **[!UICONTROL Video]** wordt niet weergegeven als de pagina geen cloudconfiguratie heeft.

1. Selecteer het adaptieve videocoderingsprofiel, een uit-van-de-doos enig videocoderingsprofiel, of een profiel van de douanevideocodering.

   >[!NOTE]
   >
   >Voor meer informatie over wat de video vooraf instelt betekent, zie de [ documentatie van Dynamic Media Classic ](https://experienceleague.adobe.com/docs/dynamic-media-classic/using/setup/application-setup.html#video-presets-for-encoding-video-files).
   >
   >Adobe raadt u aan beide adaptieve videosets te selecteren wanneer u de universele voorinstellingen configureert of de optie **[!UICONTROL Adaptive Video Encoding]** te selecteren.

1. De geselecteerde coderingsprofielen worden automatisch toegepast op alle video&#39;s die zijn geüpload naar de CQ DAM-doelmap die u hebt ingesteld voor deze Scene7-cloudconfiguratie. U kunt veelvoudige Scene7 wolkenconfiguraties met verschillende doelomslagen plaatsen om verschillende het coderen profielen toe te passen zoals nodig.

## Viewer- en coderingsvoorinstellingen bijwerken {#updating-viewer-and-encoding-presets}

Als u de viewer- en coderingsvoorinstellingen voor video wilt bijwerken omdat de voorinstellingen in Scene7 zijn bijgewerkt, navigeert u naar de Scene7-configuratie in de Cloud Configuration en selecteert u **[!UICONTROL Update the viewer and encoding presets]** .

![ chlimage_1-364 ](assets/chlimage_1-364.png)

## Upload uw primaire bronvideo aan Scene7 van Adobe DAM {#uploading-your-master-video}

1. Navigeer naar de CQ DAM doelomslag waar u opstelling uw wolkenconfiguratie met Scene7 het coderen profielen hebt.
1. Selecteer **[!UICONTROL Upload]** om primaire bronvideo te uploaden. Het uploaden en coderen van video is voltooid nadat de [!UICONTROL DAM Update Asset] -workflow is voltooid en **[!UICONTROL Publish to Scene7]** een vinkje heeft.

   >[!NOTE]
   >
   >Het genereren van videominiaturen duurt langer.

   Het slepen van de primaire bronvideo DAM op de videocomponententoegang *alle* Scene7 gecodeerde volmachtsvertoningen voor levering.

## De VideoComponent van de stichting tegenover Video Scene7 Component {#foundation-video-component-versus-scene-video-component}

Wanneer het gebruiken van Experience Manager, hebt u toegang tot zowel de Video component beschikbaar in Plaatsen als de videocomponent Scene7. Deze componenten zijn niet onderling verwisselbaar.

De videocomponent Scene7 werkt slechts voor Scene7 video&#39;s. De stichtingscomponent werkt met video&#39;s die van Experience Manager (gebruikend mpeg) en Scene7 video&#39;s worden opgeslagen.

De volgende matrix legt uit wanneer de component moet worden gebruikt:

![ chlimage_1-365 ](assets/chlimage_1-365.png)

>[!NOTE]
>
>De videocomponent S7 gebruikt het universele videoprofiel uit het vak. U kunt de op HTML5 gebaseerde videospeler echter verkrijgen voor gebruik door Experience Manager. Kopieer in Scene7 de insluitcode van de uit-van-doos HTML5 videospeler en zet het in uw Experience Manager pagina.

## Experience Manager Video-component {#aem-video-component}

Zelfs als het gebruiken van de videocomponent Scene7 voor het bekijken van Scene7 video&#39;s wordt geadviseerd, beschrijft deze sectie het gebruiken van video Scene7 met de Component van de Video van de Stichting in Experience Manager, voor volledigheid.

### Experience Manager Video- en Scene7-videovergelijking {#aem-video-and-scene-video-comparison}

De volgende lijst verstrekt een high-level vergelijking van gesteunde mogelijkheden tussen de Videomponent van de Stichting van Experience Manager en de Video component Scene7:

|   | Experience Manager Foundation-video | Scene7-video |
|---|---|---|
| Benadering | HTML5 eerste aanpak. Flash wordt alleen gebruikt voor andere fallback dan HTML5. | Flash op de meeste desktops. HTML5 wordt gebruikt voor mobiele apparaten en tablets. |
| Aflevering | Progressief | Adaptieve streaming |
| Tekstspatiëring | Ja | Ja |
| Uitbreidbaarheid | Ja | Nee |
| Mobiele video | Ja | Ja |

### Instellen {#setting-up}

#### Videoprofielen maken {#creating-video-profiles}

De verschillende videocoderingen worden gecreeerd volgens de S7 coderende voorinstellingen die in S7 wolkenconfig worden geselecteerd. Als u wilt dat de basis-videocomponent deze gebruikt, moet u een videoprofiel maken voor elke geselecteerde S7-coderingsvoorinstelling. Met deze methode kan het videoonderdeel de DAM-uitvoeringen op basis hiervan selecteren.

>[!NOTE]
>
>Nieuwe videoprofielen en wijzigingen ervan moeten worden geactiveerd om te publiceren.

1. Selecteer in Experience Manager **[!UICONTROL Tools]** > **[!UICONTROL Configuration Console]** .
1. Navigeer in de **[!UICONTROL Configuration Console]** naar **[!UICONTROL Tools]** > **[!UICONTROL DAM]** > **[!UICONTROL Video Profiles]** in de navigatiestructuur.
1. Maak een S7-videoprofiel. In de lus **[!UICONTROL New]** . selecteert u **[!UICONTROL Create Page]** en selecteert u vervolgens de sjabloon Scene7-videoprofiel. Geef de nieuwe pagina met videoprofielen een naam en selecteer **[!UICONTROL Create]** .

   ![ chlimage_1-366 ](assets/chlimage_1-366.png)

1. Bewerk het nieuwe videoprofiel. Selecteer eerst de cloudconfiguratie. Selecteer vervolgens dezelfde coderingsvoorinstelling die u in de cloudconfiguratie hebt geselecteerd.

   ![ chlimage_1-367 ](assets/chlimage_1-367.png)

   | Eigenschap | Beschrijving |
   |---|---|
   | Scene7 Cloud Config | De cloud config die voor de coderingsvoorinstellingen moet worden gebruikt. |
   | Scene7-coderingsvoorinstelling | De coderingsvoorinstelling waarmee dit videoprofiel wordt toegewezen. |
   | HTML5-videotype | Met deze eigenschap kunt u de waarde instellen van de eigenschap type van het HTML5-videobronelement. Deze informatie wordt niet verschaft door de S7-coderingsvoorinstellingen, maar is vereist voor het correct renderen van video&#39;s met HTML5-video-element. Er is een lijst met algemene indelingen beschikbaar, maar deze lijst kan worden overschreven voor andere indelingen. |

   Herhaal deze stap voor alle coderingsvoorinstellingen die zijn geselecteerd in de cloudconfiguratie die u wilt gebruiken in de videocomponent.

#### Ontwerp configureren {#configuring-design}

De component **[!UICONTROL Foundation Video]** moet weten welke videoprofielen moeten worden gebruikt om de lijst met videobronnen te maken. Open het dialoogvenster Ontwerp van videocomponenten en configureer het componentontwerp voor het gebruik van de nieuwe videoprofielen.

>[!NOTE]
>
>Als u de component **[!UICONTROL Foundation Video]** op een mobiele pagina gebruikt, herhaalt u deze stappen bij het ontwerp van de mobiele pagina.

>[!NOTE]
>
>Wijzigingen in het ontwerp vereisen dat het ontwerp wordt geactiveerd om na publicatie van kracht te worden.

1. Open het ontwerpdialoogvenster van de component **[!UICONTROL Foundation Video]** en wijzig dit in de tab **[!UICONTROL Profiles]** . Verwijder vervolgens de profielen uit de doos en voeg de nieuwe S7-videoprofielen toe. De volgorde van de profiellijst in het dialoogvenster Ontwerp bepaalt de volgorde van het element Videobronnen bij het renderen.
1. Voor browsers die geen HTML5 ondersteunen, kunt u met de video-component een Flash-fallback configureren. Open het dialoogvenster voor het ontwerpen van videocomponenten en wijzig de tab **[!UICONTROL Flash]** . Configureer de Flash Player-instellingen en wijs een fallback-profiel toe aan de Flash Player.

#### Checklist {#checklist}

1. Creeer een S7 wolkenconfiguratie. Zorg ervoor dat de voorinstellingen voor videocodering zijn ingesteld en dat de importmodule wordt uitgevoerd.
1. Maak een S7-videoprofiel voor elke videocoderingsvoorinstelling die is geselecteerd in de cloudconfiguratie.
1. De videoprofielen moeten worden geactiveerd.
1. Configureer het ontwerp van de component **[!UICONTROL Foundation Video]** op de pagina.
1. Activeer het ontwerp nadat u klaar bent met uw ontwerpwijzigingen.
