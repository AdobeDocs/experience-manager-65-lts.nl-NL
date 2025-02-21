---
title: Aanbevolen procedures voor het verwerken van de ondersteunde bestandsindelingen
description: Aanbevolen procedures om de diverse ondersteunde bestandstypen te verwerken met  [!DNL Experience Manager Assets] .
contentOwner: AG
role: Admin
feature: Asset Management,Developer Tools
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '470'
ht-degree: 0%

---

# Aanbevolen werkwijzen voor Assets-bestandsindelingen {#assets-file-format-best-practices}

[!DNL Adobe Experience Manager Assets] biedt ondersteuning voor een groot aantal bibliotheken met bestandsindelingen van leveranciers en derden, zodat gebruikers aan verschillende vereisten voor bestandsondersteuning kunnen voldoen. Tot de ondersteunde Adobe-bibliotheken behoren [!DNL Adobe Camera Raw] , Gibson, Adobe PDF Rasterizer en [!DNL Adobe InDesign Server] . Daarnaast biedt [!DNL Experience Manager Assets] ondersteuning voor bibliotheken van derden, zoals [!DNL ImageMagick] , [!DNL TwelveMonkeys] , enzovoort.

Voor de gesteunde dossierformaten, zie [ Assets gesteunde formaten ](/help/assets/assets-formats.md).

>[!TIP]
>
>Als u [!DNL Experience Manager] gebruikt op Adobe Managed Services (AMS), kunt u contact opnemen met de klantenondersteuning van Adobe als u van plan bent een groot aantal grote PSD- of PSB-bestanden te verwerken. Werk samen met de Adobe Customer Support-medewerker om deze best practices te implementeren voor uw AMS-implementatie en om de best mogelijke tools en modellen te kiezen voor de eigen indelingen van Adobe. [!DNL Experience Manager] verwerkt mogelijk geen PSB-bestanden met zeer hoge resolutie die groter zijn dan 30000 x 23000 pixels.

## [!DNL Adobe Camera Raw] library {#adobe-camera-raw-library}

Voor optimale prestaties raadt Adobe aan [!DNL Adobe Camera Raw] -bibliotheek te gebruiken voor RAW- en DNG-bestanden.

[!DNL Adobe Camera Raw] -bibliotheek ondersteunt CMYK-kleurprofiel als invoer. De uitvoer wordt echter alleen in de RGB-kleurruimte gegenereerd en de uitvoer wordt alleen in de JPEG-indeling ondersteund. De kleurruimte van het bronbestand (bijvoorbeeld CMYK) blijft niet behouden in de miniaturen.

Voor meer informatie, zie [ de steun van Camera Raw ](/help/assets/camera-raw.md).

## Adobe PDF Rasterizer-bibliotheek {#adobe-pdf-rasterizer-library}

Voor de beste resultaten raadt Adobe aan de Adobe PDF Rasterizer-bibliotheek te gebruiken voor de volgende bestanden:

* PDF-bestanden met veel inhoud
* AI-bestanden met miniaturen die niet uit het vak zijn gegenereerd
* Voor AI-bestanden met SPOT-kleuren (PMS)

Miniaturen en voorvertoningen die met PDF Rasterizer worden gegenereerd, zijn beter van kwaliteit dan rasteruitvoer die niet in de doos voorkomt. De Adobe PDF Rasterizer-bibliotheek biedt geen ondersteuning voor conversie van kleurruimten. Ongeacht de kleurruimte van het PDF-bronbestand genereert Adobe PDF Rasterizer alleen RGB-uitvoer.

## [!DNL Adobe InDesign Server] {#adobe-indesign-server}

Adobe raadt u aan [!DNL Adobe InDesign Server] te gebruiken om [!DNL Adobe InDesign] -specifieke uitvoeringen, zoals IDML en HTML, te extraheren. Voor meer informatie, zie [ Toevoegend de activa van Experience Manager als verwijzingen in Adobe InDesign ](/help/assets/managing-linked-subassets.md#refai).

## [!DNL Dynamic Media] {#dynamic-media}

[!DNL Dynamic Media] genereert en levert meerdere variaties van rijke inhoud in real-time via het algemene, schaalbare en voor prestaties geoptimaliseerde netwerk. Het dient voor interactieve kijkervaringen en stroomlijnt het beheerproces voor digitale campagnes. Voor details rond het toelaten van [!DNL Dynamic Media], zie [ Vormend Dynamische Media ](/help/assets/config-dynamic.md).

Op dit moment kan [!DNL Dynamic Media] video&#39;s met maximaal 15 GB aan inhoud per bestand ondersteunen.

## ImageMagick-bibliotheek {#imagemagick-library}

Adobe raadt u aan de ImageMagick-bibliotheek in de volgende scenario&#39;s te gebruiken:

* Miniatuurweergaven genereren voor EPS-bestanden.
* Hiermee behoudt u de afbeeldingsprofielgegevens.
* De transparantie behouden.
* PSD- en PSB-bestanden verwerken.

Om te weten hoe te opstelling de [!DNL ImageMagick] bibliotheek in [!DNL Experience Manager], zie [ Gebruikend ImageMagick ](/help/assets/media-handlers.md#an-example-using-imagemagick). Voor optimaal gebruik, zie [ Beste praktijken voor het Vormen ImageMagick ](/help/assets/best-practices-for-imagemagick.md).

## Bibliotheek voor transformatie van afbeeldingen {#image-transcoding-library}

De Adobe Imaging Transcoding Library is een oplossing voor beeldverwerking die basisfuncties voor beeldverwerking uitvoert, zoals beeldcodering, transcodering, hersampling, formaatwijziging, enzovoort.

De Beeldtransformatiebibliotheek ondersteunt de volgende MIME-typen:

* JPG/JPEG
* PNG (8 bits en 16 bits)
* GIF
* BMP
* TIFF/Compressed TIFF (behalve 32 Bit TIFF en PTiff).
* ICO
* ICN

Voor details, zie [ Beeldend Transcoding Bibliotheek ](/help/assets/imaging-transcoding-library.md).
