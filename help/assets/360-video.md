---
title: 360/VR-video
description: Leer werken met en gebruik 360 en VR-video (Virtual Reality) in dynamische media.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
feature: 360 VR Video
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: 17e45464-3de4-40a8-b102-ccc9eaba92a3
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1139'
ht-degree: 0%

---

# 360/VR-video {#vr-video}

Bij video&#39;s van 360 graden wordt een weergave in elke richting tegelijkertijd vastgelegd. Ze worden opgenomen met een omnidirectionele camera of een verzameling camera&#39;s. Tijdens het afspelen op een plat beeldscherm heeft de gebruiker controle over de kijkhoek; afspeelapparatuur op mobiele apparaten gebruikt doorgaans de ingebouwde gyroscopische besturingselementen.

Dynamische media - de wijze Scene7 omvat inheemse steun voor de levering van 360 videoactiva. Standaard is geen aanvullende configuratie nodig voor weergave of afspelen. U levert 360 Video gebruikend standaardvideouitbreidingen zoals .mp4, .mkv, en .mov. De meest algemene codec is H.264.

In deze sectie wordt beschreven hoe u met de 360/VR Video-viewer werkt om equirechthoekige video te renderen voor een indrukwekkende kijkervaring van een kamer, eigenschap, locatie, landschap, medische procedure, enzovoort.

Ruimtelijke audio wordt momenteel niet ondersteund. Als audio in stereo wordt gemengd, verandert de balans (L/R) niet omdat de klant de kijkhoek van de camera wijzigt.

Zie ook [ het Leiden Kijker stelt ](/help/assets/managing-viewer-presets.md) vooraf in.

## 360 Video in actie {#video-in-action}

Selecteer [ Post 360 van de Ruimte ](https://s7d1.scene7.com/s7viewers/html5/Video360Viewer.html?asset=Viewers/space_station_360-AVS) om een browser venster te openen en op een video van 360 graadmeter te letten. Tijdens het afspelen van video sleept u de muisaanwijzer naar een nieuwe locatie om de weergavehoek te wijzigen.

![ 360-videosteekproef met het internationale ruimtestation drijvende in kosmische ruimte en de aarde en de zon achter het.](assets/6_5_360videoiss_simplified.png)
*Videoframe van Post 360 van de Ruimte*

## 360/VR-video en Adobe Premiere Pro {#vr-video-and-adobe-premiere-pro}

Met Adobe Premier Pro kunt u 360/VR-beeldmateriaal weergeven en bewerken. U kunt bijvoorbeeld logo&#39;s en tekst op de juiste wijze in een scène plaatsen en effecten en overgangen toepassen die specifiek zijn ontworpen voor rechthoekige media.

Zie [ video 360/VR ](https://helpx.adobe.com/nl/premiere-pro/how-to/edit-360-vr-video.html) uitgeven.

## Elementen uploaden voor gebruik met de 360-videoviewer {#uploading-assets-for-use-with-the-video-viewer}

360 videoactiva die in Adobe Experience Manager worden geupload worden geëtiketteerd als **Multimedia** op een pagina van Activa, gelijkend op normale videoactiva.

![ 6_5_360video-selecttopreview ](assets/6_5_360video-selecttopreview.png)
*Geüploade 360-video activa die in de mening van de Kaart worden gezien. Het middel wordt geëtiketteerd als Multimedia.*

**uploadt activa voor gebruik met de 360 Video kijker:**

1. Er is een map gemaakt voor uw 360-video-element.
1. [ pas een adaptief videoprofiel op de omslag ](/help/assets/video-profiles.md#applying-a-video-profile-to-folders) toe.

   Bij het renderen van 360-video-inhoud worden hogere eisen gesteld aan de resolutie van de bronvideo en aan de resolutie van gecodeerde vertoningen dan aan de standaard niet-360-video-inhoud.

   U kunt het uit-van-de-doos Aangepast Videoprofiel gebruiken dat reeds met Dynamische Media wordt geleverd. De kwaliteit van 360-video is echter merkbaar lager dan bij niet-360-video die is gecodeerd met dezelfde instellingen die zijn gerenderd met een niet-360-videoviewer. Ga daarom als volgt te werk als u hoogwaardige 360 video nodig hebt:

   * In het ideale geval kunt u het beste een van de volgende resoluties toepassen op de oorspronkelijke 360-video-inhoud:

      * 1080p - 1920 x 1080, bekend als Full HD- of FHD-resolutie of,
      * 2160p - 3840 x 2160, bekend als 4k, UHD of Ultra HD-resolutie. Deze grote weergaveresolutie wordt meestal aangetroffen op hoogwaardige televisies en computermonitoren. De resolutie van 2160p wordt vaak &#39;4k&#39; genoemd omdat de breedte dichtbij 4000 pixels ligt. Met andere woorden, het biedt vier keer de pixels van 1080p.

   * [ creeer een douane Aangepast VideoProfiel ](/help/assets/video-profiles.md#creating-a-video-encoding-profile-for-adaptive-streaming) met vertoningen van hogere kwaliteit. Maak bijvoorbeeld een adaptief videoprofiel met de volgende drie instellingen:

      * width=auto; height=720; bitrate=2500 kbps
      * width=auto; height=1080; bitrate=5000 kbps
      * width=auto; height=1440; bitrate=6600 kbps

   * Verwerk 360-video-inhoud in een map die exclusief is bestemd voor 360 video-elementen.

   Deze benadering plaatst grotere eisen aan het netwerk en CPU van de eindgebruiker.

1. [ uploadt uw video aan de omslag ](/help/assets/managing-video-assets.md#upload-and-preview-video-assets).

## De standaardverhouding van 360 video&#39;s overschrijven  {#overriding-the-default-aspect-ratio-of-videos}

Als u een geüpload element wilt kwalificeren als een 360-video die u wilt gebruiken met de 360-videoviewer, moet het element een hoogte-breedteverhouding van 2 hebben.

Experience Manager detecteert video standaard als &quot;360&quot; als de hoogte-breedteverhouding (breedte/hoogte) 2,0 is. Als u een beheerder bent, kunt u de standaardverhouding van 2 overschrijven door de optionele eigenschap `s7video360AR` in CRXDE Lite als volgt in te stellen:

* `/conf/global/settings/cloudconfigs/dmscene7/jcr:content`

   * **type van Bezit** - tweemaal
   * **Waarde** - floating-point aspectverhouding, gebrek 2.0.

Nadat u deze eigenschap hebt ingesteld, wordt deze direct van kracht op zowel bestaande als nieuw geüploade video&#39;s.

De aspectverhouding is op 360 videoactiva voor de pagina van activadetails en de [ Video 360 component van Media WCM ](/help/assets/adding-dynamic-media-assets-to-pages.md#dynamic-media-components) van toepassing.

Begin met het uploaden van 360 video&#39;s.

## Voorvertoning 360-video {#previewing-video}

Met Voorvertoning kunt u zien hoe uw 360-video er uitziet voor klanten en kunt u controleren of deze goed functioneert.

Zie ook [ vooraf instelt van de kijker ](/help/assets/managing-viewer-presets.md#editing-viewer-presets) uitgeven.

Als u tevreden bent met de 360-video, kunt u deze publiceren.

Zie [ de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md) inbedden.
Zie [ Verbinding URLs aan uw Webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie [ Dynamische Media Assets aan pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.

**aan voorproef 360 Video:**

1. Navigeer in **[!UICONTROL Assets]** naar een bestaande 360-video die u hebt gemaakt. Selecteer het 360 Video-element zodat u het kunt openen in de voorvertoningsmodus.

   ![ 6_5_360video-selecttopreview-1 ](assets/6_5_360video-selecttopreview-1.png)

   Selecteer het 360-video-element zodat u een voorvertoning van de video kunt bekijken.

1. Selecteer op de voorvertoningspagina, linksboven op de pagina, de vervolgkeuzelijst en selecteer vervolgens **[!UICONTROL Viewers]** .

   ![ 6_5_360video-voorproef-kijkers ](assets/6_5_360video-preview-viewers.png)

   Selecteer **[!UICONTROL Video360_social]** in de lijst Viewers en voer een van de volgende handelingen uit:

   * Sleep de muisaanwijzer over de video als u de kijkhoek van de statische scène wilt wijzigen.
   * Selecteer de knop **[!UICONTROL Play]** van de video als u wilt beginnen met afspelen. Terwijl de video wordt afgespeeld, sleept u de muisaanwijzer over de video om de kijkhoek te wijzigen.

   ![ A screenshot van de internationale ruimtestation die in kosmische ruimte met de aarde en de zon in de achtergrond drijft ](assets/6_5_360video-preview-video360-social.png)*A 360-video screenshot.*

   * Selecteer **[!UICONTROL Video360VR]** in de lijst Viewers.

     VR-video (Virtual Reality) is overweldigende video-inhoud die wordt benaderd met headsets van virtuele realiteit. Net als bij gewone video&#39;s maakt u aan het begin VR-video&#39;s wanneer een video wordt opgenomen of vastgelegd met videocamera&#39;s van 360 graden.

   ![ A screenshot van een close-up van het internationale ruimtestation die in kosmische ruimte drijft met de aarde en de zon gedeeltelijk zichtbaar in de achtergrond ](assets/6_5_360video-preview-video360vr.png)
   *A 360 VR videoscreenshot.*

1. Selecteer **[!UICONTROL Close]** rechtsboven op de voorvertoningspagina.

## 360-video publiceren {#publishing-video}

Publiceer de 360-video zodat u deze kunt gebruiken. Wanneer u een 360-video publiceert, wordt de URL en de insluitcode geactiveerd. Het publiceert ook de 360 Video aan de Dynamische wolk van Media die met een CDN voor scalable en prestatieslevering geïntegreerd is.

Zie [ Dynamische activa van Media publiceren ](/help/assets/publishing-dynamicmedia-assets.md) voor details op hoe te om 360 Video te publiceren.
Zie ook [ bed de Video of Kijker van het Beeld op een Web-pagina ](/help/assets/embed-code.md) in.
Zie ook [ Verbinding URLs aan uw Webtoepassing ](/help/assets/linking-urls-to-yourwebapplication.md). De op URL gebaseerde methode van het verbinden is niet mogelijk als uw interactieve inhoud verbindingen met relatieve URLs, in het bijzonder verbindingen met Experience Manager Sites pagina&#39;s heeft.
Zie ook [ Dynamische activa van Media aan pagina&#39;s ](/help/assets/adding-dynamic-media-assets-to-pages.md) toevoegen.
