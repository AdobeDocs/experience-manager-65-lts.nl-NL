---
title: Terugvallettertypen configureren
description: Leer hoe u fallback-lettertypen kunt configureren voor AEM Forms. Met het bestand FontManagerResources.properties kunt u de standaardlettertypen handmatig toewijzen aan terugvallettertypen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d11bb8dc-d0fe-4182-88dd-9ef1ecf687db
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '264'
ht-degree: 0%

---

# Terugvallettertypen configureren {#configuring-fallback-fonts}

U kunt het bestand FontManagerResources.properties handmatig zodanig configureren dat de standaard AEM-formulierlettertypen worden toegewezen aan fallback (of vervangen) als de standaardlettertypen niet beschikbaar zijn op de server. Dit eigenschapbestand bevindt zich in het bestand adobe-fontmanager.jar.

>[!NOTE]
>
>De fontconfiguratie van de reserve is ook op de assembleerdienst van toepassing.

1. Navigeer naar het bestand adobe-livecycle-*`[appserver]`* .ear in de map *`[aem-forms root]`* /configurationManager/export, maak een reservekopie en pak het origineel uit.
1. Zoek het bestand adobe-fontmanager.jar en pak het uit.
1. Zoek het bestand FontManagerResources.properties en open het in een teksteditor.
1. Wijzig desgewenst de locaties en namen van de lettertypen Algemeen en Fallback en sla het bestand op.

   De fontitems in het bestand FontManagerResources.properties zijn relatief ten opzichte van de map *`[aem-forms root]`* /fonts. Als u lettertypen opgeeft die geen standaard AEM-formulierlettertypen zijn, moet u deze lettertypen installeren in deze directorystructuur (binnen een bestaande map of in een nieuw gemaakte map).

   >[!NOTE]
   >
   >Als het opgegeven lettertype of standaardlettertype geen specifiek Unicode-teken bevat of als dit niet beschikbaar is, wordt het teken volgens de volgende prioriteit van een fallback-lettertype genomen:

   * Landspecifiek lettertype
   * HOOFDLETTERlettertype indien landinstelling niet is ingesteld
   * Algemeen lettertype, doorzocht op volgorde ingesteld in de fallback-tabel

1. Verpak het bestand adobe-fontmanager.jar opnieuw.
1. Herhaal het bestand adobe-livecycle-*`[appserver]`*.ear en pas het bestand vervolgens handmatig of met Configuratiebeheer opnieuw in.

>[!NOTE]
>
>Gebruik Configuration Manager niet om het bestand adobe-livecycle-`[appserver]`.ear opnieuw te verpakken, omdat hierdoor uw wijzigingen worden overschreven door de standaardwaarden voor AEM-formulieren.
