---
title: AEM Repo
description: Het gereedschap AEM Repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM-server via een opdrachtregel die vergelijkbaar is met FTP. Het gereedschap AEM Repo is vergelijkbaar met het gereedschap Jackrabbit FileVault, maar is sneller, heeft minimale afhankelijkheden en is een eenvoudig basisscript.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# AEM Repo{#aem-repo-tool}

Het gereedschap AEM Repo is een eenvoudige oplossing voor het overbrengen van JCR-inhoud tussen uw lokale bestandssysteem en de AEM-server via een opdrachtregel die vergelijkbaar is met FTP. Het hulpmiddel van de Repo van AEM is gelijkaardig aan het [ hulpmiddel FileVault van het Sjasje ](/help/sites-developing/ht-vlttool.md), maar is sneller, heeft minimale gebiedsdelen, en is een eenvoudig bash manuscript.

Dit hulpmiddel vereenvoudigt de overdracht van dossiers voor de ontwikkelaar en kan ook in IntelliJ en Eclipse worden geïntegreerd om ontwikkeling nog efficiënter te maken.

## Overzicht {#overview}

Voor een bepaald pad binnen een `jcr_root` -bestandsstructuur op het bestandssysteem maakt AEM Repo Tool een pakket met één filter voor de gehele substructuur en plaatst deze op de server (vergelijkbaar met FTP `put` ), haalt deze op van de server ( `get` ) of vergelijkt de verschillen ( `status` en `diff` ).

Het gereedschap biedt geen ondersteuning voor meerdere filterpaden of FileVault-paden `filter.xml` .

>[!CAUTION]
>
>Met het gereedschap AEM-repo overschrijft u altijd het gehele opgegeven bestand of de opgegeven map.

## Downloaden en documentatie {#download-and-documentation}

Het [ Hulpmiddel van de Repo van AEM is beschikbaar op GitHub via deze verbinding ](https://github.com/Adobe-Marketing-Cloud/tools/tree/master/repo) samen met gedetailleerde installatie en gebruiksinstructies.

Als u de bron van het Hulpmiddel van de Repo van AEM wilt downloaden, zie het hieronder verbonden project GitHub.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ Open hulpmiddelproject op GitHub ](https://github.com/Adobe-Marketing-Cloud/tools)
* Download het project als [ een dossier van het PIT ](https://github.com/Adobe-Marketing-Cloud/tools/archive/master.zip)
