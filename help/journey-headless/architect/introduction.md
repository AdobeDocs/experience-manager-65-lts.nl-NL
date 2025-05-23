---
title: Adobe Experience Manager Headless Content Architect Reis
description: Een inleiding tot de krachtige, flexibele, eindeloze eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Architect,Data Architect
exl-id: cb64e012-7001-47a3-b038-8f8f6891c6a0
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '720'
ht-degree: 0%

---

# Content Modeling for Headless met AEM - Een introductie {#architect-headless-introduction}

In dit deel van de [ Journey van de Architect van de Inhoud van AEM Headless ](overview.md), kunt u de (basis) concepten en de terminologie noodzakelijk leren om inhoud modellering voor hoofdloze inhoudslevering met Adobe Experience Manager (AEM) te begrijpen.

Met dit document krijgt u inzicht in de inhoud zonder kop, hoe AEM koploze inhoud ondersteunt en hoe inhoud wordt gemodelleerd voor headless inhoud. Na het lezen moet u:

* Begrijp de basisconcepten van inhoud zonder kop levering.
* Bekend zijn hoe AEM modellering zonder kop en inhoud ondersteunt.

## Doelstelling {#objective}

* **Publiek**: Begin
* **Doelstelling**: Introduceer de concepten en de terminologie relevant voor de Modellering van de Inhoud zonder hoofd.

## Volledige levering van inhoud {#full-stack}

Sinds de opkomst van gebruiksvriendelijke, grootschalige contentbeheersystemen (CMS&#39;s) hebben organisaties deze als centrale locatie gebruikt voor het beheer van berichten, branding en communicatie. Het gebruik van de CMS als centraal punt voor het beheer van ervaringen heeft geleid tot een verbeterde efficiëntie doordat het niet nodig is taken in verschillende systemen te dupliceren.

![ de klassieke volledig-stapel CMS ](/help/journey-headless/developer/assets/full-stack.png)

In een CMS met volledige stapel bevindt alle functionaliteit voor het manipuleren van inhoud zich in de CMS. De functies van het systeem bestaan uit verschillende onderdelen van de CMS-stapel. De full-stack oplossing heeft veel voordelen.

* Er is één systeem om te onderhouden.
* Inhoud wordt centraal beheerd.
* Alle diensten van het systeem zijn geïntegreerd.
* Inhoud schrijven is naadloos.

Als dus een nieuw kanaal moet worden toegevoegd of ondersteuning voor nieuwe soorten ervaringen is vereist, kunnen een (of meer) nieuwe componenten in de stapel worden ingevoegd en is er slechts één plaats om wijzigingen aan te brengen.

![ Toevoegend een nieuw kanaal aan de stapel ](/help/journey-headless/developer/assets/adding-channel.png)

Nochtans wordt de ingewikkeldheid van de gebiedsdelen binnen de stapel snel duidelijk aangezien andere punten in de stapel moeten worden aangepast om de veranderingen aan te passen.

## De kop in de kop {#the-head}

Het hoofd van een systeem is doorgaans de uitvoerrenderer van dat systeem, meestal in de vorm van een grafische interface of andere grafische uitvoer.

Als we het hebben over een CMS zonder kop, beheert de CMS de inhoud en blijft ze leveren aan de consument. Nochtans, door slechts de **inhoud** op een gestandaardiseerde manier te leveren, weglaat een headless CMS de definitieve output die teruggeeft, verlatend de **presentatie** van de inhoud aan de verbruikende dienst.

![ Headless CMS ](/help/journey-headless/developer/assets/headless-cms.png)

De verbruikende services, of het nu gaat om AIR, een webshop, mobiele ervaring, progressieve webapps (PWA&#39;s), enzovoort, nemen inhoud van de CMS zonder kop in en leveren hun eigen rendering. Ze zorgen ervoor dat ze hun eigen hoofd geven aan je inhoud.

Als u de kop weglaat, wordt de CMS vereenvoudigd doordat de complexiteit wordt weggenomen. Hierdoor wordt ook de verantwoordelijkheid voor het renderen van de inhoud verplaatst naar de diensten die de inhoud nodig hebben en die vaak beter geschikt zijn voor dergelijke rendering.

## Inhoud modelleren {#content-modeling}

Content Modeling (ook wel gegevensmodellering genoemd) is uw specialiteit, dus wat moet u in overweging nemen bij het modelleren voor headless?

Voor toepassingen zonder kop hebt u een vooraf gedefinieerde structuur nodig om toegang te krijgen tot uw inhoud en er iets mee te kunnen doen. Het zou mogelijk zijn om uw inhoud als vrij-vorm te hebben, maar het zou het leven *zeer* gecompliceerd voor de toepassingen maken.

Voor AEM zult u, als Architect van de Inhoud, de inhoud modelleren uitvoeren om een waaier van **Modellen van het Fragment van de Inhoud te ontwerpen**. Deze bepalen de gebruikte structuur wanneer uw inhoudsauteurs de **Fragmenten van de Inhoud** creëren die de inhoud houden.

### De inhoud openen {#access-content}

Dit is meer een ontwikkelingsdetail - maar het zou u kunnen interesseren, enkel om het verhaal te voltooien.

Nadat u de modellen voor inhoudsfragmenten hebt gemaakt en de auteurs deze hebben gebruikt om de inhoud te genereren, moeten de toepassingen zonder kop toegang krijgen tot deze inhoud.

Adobe Experience Manager (AEM) heeft via de AEM GraphQL-API selectief toegang tot uw inhoudsfragmenten. Alleen de benodigde inhoud wordt geretourneerd. Gebruikend API kan een ontwikkelaar vragen formuleren die specifieke inhoud selecteren.Dit selectieproces is gebaseerd op *uw* Modellen van het Fragment van de Inhoud.

Dit betekent dat uw project zonder kop gestructureerde inhoud voor gebruik in uw toepassingen kan realiseren.

## Volgende functies {#whats-next}

Nu u de concepten en de terminologie hebt geleerd, moet de volgende stap [ de grondbeginselen van het modelleren met de Modellen van het Fragment van de Inhoud ](basics.md) leren.

## Aanvullende bronnen {#additional-resources}

* AEM Headless Developer Journey
   * [Meer informatie over CMS Headless Development](/help/journey-headless/developer/learn-about.md)
   * [Leer hoe u uw inhoud kunt modelleren](/help/journey-headless/developer/model-your-content.md)
* [Inleiding tot AEM als een CMS zonder kop](/help/sites-developing/headless/introduction.md)
* [ AEM Developer Portal ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
* [ Leerprogramma&#39;s voor Zwaartepunt in AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL)
