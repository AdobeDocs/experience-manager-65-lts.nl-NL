---
title: Integreren met BrightStor Content Optimizer
description: Meer informatie over de integratie van AEM met BrightStor Content Optimizer.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: fbc55cbd-c754-44f8-8159-72cedc60e137
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '490'
ht-degree: 0%

---

# Integreren met BrightStor Content Optimizer{#integrating-with-brightedge-content-optimizer}

Maak een BrightEdge-cloudconfiguratie zodat AEM verbinding kan maken met de referenties van uw BrightStor-account. U kunt meerdere configuraties maken als u meerdere accounts gebruikt.

Wanneer u de configuratie creeert, specificeert u een titel. De titel moet beschrijvend zijn, zodat mensen de configuratie kunnen correleren met de BrightStor-account. Wanneer een auteur of beheerder van een pagina een webpagina maakt met het BrightStor-account, wordt deze titel weergegeven in een vervolgkeuzelijst.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik op de koppeling die wordt weergegeven in de sectie BrightEdge Content Optimizer. De koppelingstekst wordt bepaald door het feit of er een BrightEdge-configuratie is gemaakt:

   * Nu configureren: deze koppeling wordt weergegeven wanneer er geen configuratie is gemaakt.
   * Configuraties tonen: deze koppeling wordt weergegeven wanneer een of meer configuraties zijn gemaakt.

   ![&#x200B; chlimage_1-4 &#x200B;](assets/chlimage_1-4a.png)

1. Als u op Configuraties tonen hebt geklikt, klikt u op de koppeling + naast Beschikbare configuraties.
1. Typ een titel voor de configuratie. Naar keuze, typ een naam voor de knoop die wordt gebruikt om de configuratie in de bewaarplaats op te slaan. Klik op Maken.
1. Typ in het dialoogvenster Configuratie van BrightStor Content Optimizer de gebruikersnaam en het wachtwoord van de BrightStor-account en klik op OK.

## Een BrightEdge-configuratie bewerken {#editing-a-brightedge-configuration}

Wijzig indien nodig de gebruikersnaam en het wachtwoord van een BrightStor-configuratie. De wijzigingen zijn van invloed op alle pagina&#39;s die de configuratie gebruiken.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik in de sectie BrightEdge Content Optimizer op Configuraties tonen.

   ![&#x200B; chlimage_1-5 &#x200B;](assets/chlimage_1-5a.png)

1. Klik op de naam van de configuratie die u wilt bewerken.
1. Klik op Bewerken, wijzig de eigenschapswaarden en klik op OK.

## Pagina&#39;s koppelen aan een BrightEdge-configuratie {#associating-pages-with-a-brightedge-configuration}

Koppel pagina&#39;s aan een BrightStor-configuratie om paginagegevens naar de BrightStor-service te verzenden voor analyse. Wanneer u een pagina aan een configuratie associeert, erven de kindpagina&#39;s de vereniging. Meestal koppelt u de startpagina van uw site, zodat gegevens van alle pagina&#39;s naar BrightStor Edge worden verzonden.

1. Open de klassieke websiteconsole. ([&#x200B; http://localhost:4502/siteadmin#/content](http://localhost:4502/siteadmin#/content))
1. Selecteer in de boomstructuur Websites de map of pagina die de pagina bevat die u aan de configuratie van BrightStor wilt koppelen.
1. Klik in de lijst met pagina&#39;s met de rechtermuisknop op de pagina die u wilt configureren en klik op Eigenschappen.
1. Klik op het tabblad Cloud Services op de knop Service toevoegen en selecteer BrightEdge Content Optimizer in het dialoogvenster Cloud Services en klik vervolgens op OK.
1. Selecteer in de lijst BrightEdge Content Optimizer de BrightEdge-configuratie die u aan de pagina wilt koppelen en klik op OK.

   ![&#x200B; chlimage_1-6 &#x200B;](assets/chlimage_1-6a.png)

## Een BrightEdge-configuratie activeren {#activating-a-brightedge-configuration}

Activeer een BrightEdge-configuratie om deze te repliceren op de publicatie-instantie en om gepubliceerde pagina&#39;s in staat te stellen te communiceren met de BrightStor-service.

1. Klik op Sites in de track en blader naar de pagina die u aan de configuratie van BrightStor Edge hebt gekoppeld en selecteer deze.
1. Klik op het pictogram Publiceren en klik vervolgens op Publiceren.

   ![&#x200B; chlimage_1-7 &#x200B;](assets/chlimage_1-7a.png)

1. Controleer in de lijst met configuraties die wordt weergegeven of uw BrightStor-configuratie is geselecteerd en klik op Publiceren.

   ![&#x200B; chlimage_1-8 &#x200B;](assets/chlimage_1-8a.png)
