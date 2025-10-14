---
title: Dynamische media-elementen leveren
description: Leer hoe u dynamische media-elementen, zoals video en afbeeldingen, op uw webpagina's kunt plaatsen.
role: User, Admin
feature: Asset Management,Renditions
solution: Experience Manager, Experience Manager Assets
exl-id: b91173b4-f1d1-4aad-97d2-782bc8aeaeab
source-git-commit: 47b82956b41c3f78bed5ae220c7e993ce29e0385
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---

# Dynamische media-elementen leveren{#delivering-dynamic-media-assets}

De manier waarop u uw dynamische media-elementen - zowel video als afbeeldingen - kunt leveren, is afhankelijk van de manier waarop uw website is geïmplementeerd.

Met Dynamische media hebt u verschillende opties:

* Als uw website wordt gehost op Adobe Experience Manager, wilt u de Dynamic Media-elementen rechtstreeks aan uw pagina toevoegen.
* Als uw website zich niet op Experience Manager bevindt, kunt u kiezen uit:

   * Uw video of afbeelding insluiten op uw website.
   * Koppel URL&#39;s aan uw webtoepassing. Gebruik koppelingen wanneer u een videospeler wilt leveren als een pop-up- of modaal venster.
   * Als uw plaats ontvankelijk is, kunt u [&#x200B; geoptimaliseerde beelden &#x200B;](/help/assets/responsive-site.md) leveren.

>[!NOTE]
>
>Slimme beeldverwerking werkt met bestaande voorinstellingen voor afbeeldingen en maakt gebruik van intelligentie tijdens de laatste milliseconde van levering om de bestandsgrootte van de afbeelding verder te beperken op basis van de snelheid van de browser of netwerkverbinding. Zie [&#x200B; Slimme Beeldvorming &#x200B;](/help/assets/imaging-faq.md) voor meer informatie.

Raadpleeg de volgende onderwerpen voor meer informatie:

* [Dynamische media-elementen toevoegen aan webpagina&#39;s](/help/assets/adding-dynamic-media-assets-to-pages.md)
* [De video- of afbeeldingsviewer insluiten op een webpagina](/help/assets/embed-code.md)
* [Hotlink-beveiliging activeren in Dynamic Media](/help/assets/hotlink-protection.md)
* [URL&#39;s koppelen aan uw webtoepassing](/help/assets/linking-urls-to-yourwebapplication.md)
* [Geoptimaliseerde afbeeldingen leveren voor een responsieve site](/help/assets/responsive-site.md)
* [HTTP2-levering van inhoud](/help/assets/http2.md)
* [Regels gebruiken om URL&#39;s te transformeren](/help/assets/using-rulesets-to-transform-urls.md)

## HTTP/2-levering van Dynamic Media-elementen {#http-delivery-of-dynamic-media-assets}

Experience Manager ondersteunt nu de levering van alle Dynamic Media-inhoud (afbeeldingen en video) via HTTP/2. Dit wil zeggen dat er een gepubliceerde URL of insluitcode voor de afbeelding of video beschikbaar is om te worden geïntegreerd met elke toepassing die een gehoste element accepteert. Dat gepubliceerde element wordt vervolgens geleverd via het HTTP/2-protocol. Deze methode van levering verbetert de manier browsers en servers communiceren, die voor betere reactie en ladingstijden van al uw Dynamische activa van Media toestaan.

Meer leren, zie [&#x200B; HTTP/2 levering van inhoud vaak gestelde vragen &#x200B;](/help/sites-administering/scene7-http2faq.md).
