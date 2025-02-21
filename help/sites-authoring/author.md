---
title: Authoring
description: Concepten van ontwerpen en publiceren in Adobe Experience Manager 6.5.
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
source-git-commit: d1297182b801ff4db163b8ae91332f5aebb94b9b
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Authoring{#authoring}

## Concept of Authoring (en publicatie) {#concept-of-authoring-and-publishing}

AEM biedt u twee omgevingen:

* Auteur
* Publiceren

Met deze interacties kunt u inhoud op uw website beschikbaar maken, zodat uw bezoekers de inhoud kunnen lezen.

De auteursomgeving verstrekt de mechanismen om, deze inhoud tot stand te brengen bij te werken en te herzien alvorens het daadwerkelijk te publiceren:

* Een auteur maakt en beoordeelt de inhoud (dit kan van verschillende typen zijn, bijvoorbeeld pagina&#39;s, middelen, publicaties, enzovoort)
* die op een gegeven moment op uw website worden gepubliceerd.

![ Overzicht van Milieu&#39;s ](assets/chlimage_1-132.png)

Voor de auteursomgeving, wordt de functionaliteit van AEM beschikbaar gemaakt door twee UIs. Voor het publicatiemilieu, ontwerpt u het volledige blik-en-gevoel van de interface die aan uw gebruikers ter beschikking wordt gesteld.

### Auteursomgeving {#author-environment}

De auteur werkt in wat als het **auteursmilieu** wordt bekend. Dit verstrekt een makkelijk te gebruiken interface (grafische gebruikersinterface (GUI of UI)) voor het creëren van de inhoud. Het wordt gevestigd achter de firewall van een bedrijf die volledige bescherming biedt en de auteur vereist om zich aan te melden, gebruikend een rekening die de aangewezen toegangsrechten is toegewezen.

>[!NOTE]
>
>Uw account heeft de juiste toegangsrechten nodig om inhoud te maken, bewerken of publiceren.

Afhankelijk van hoe uw instantie en uw persoonlijke toegangsrechten worden gevormd kunt u vele taken op uw inhoud, met inbegrip van (onder anderen) uitvoeren:

* nieuwe inhoud genereren of bestaande inhoud bewerken op een pagina
* vooraf gedefinieerde sjablonen gebruiken om nieuwe inhoudspagina&#39;s te maken
* uw elementen en verzamelingen maken, bewerken en beheren
* uw publicaties maken, bewerken en beheren
* uw campagnes en de bijbehorende bronnen ontwikkelen
* inhoudspagina&#39;s, elementen, enzovoort verplaatsen, kopiëren of verwijderen
* pagina&#39;s, elementen, enzovoort publiceren (of de publicatie ervan ongedaan maken)

Bovendien zijn er beheertaken die u helpen uw inhoud te beheren:

* workflows die bepalen hoe wijzigingen worden beheerd; bijvoorbeeld een revisie vóór publicatie afdwingen
* projecten die individuele taken coördineren

>[!NOTE]
>
>AEM wordt ook [ beheerd ](/help/sites-administering/home.md) (voor de meeste taken) van het auteursmilieu.

#### Publicatie-omgeving {#publish-environment}

Wanneer klaar, wordt de inhoud van de plaats van AEM gepubliceerd aan **publiceer milieu**. Hier worden de pagina&#39;s van de website beschikbaar gemaakt voor het beoogde publiek, in overeenstemming met de vormgeving van de ontworpen interface.

Meestal bevindt de publicatieomgeving zich in de gedemilitariseerde zone, met andere woorden beschikbaar voor het internet, maar niet langer onder volledige bescherming van het interne netwerk.

>[!NOTE]
>
>Helaas is er soms sprake van een overlapping in de gebruikte terminologie. Dit kan gebeuren met:
>
>* **publiceren/unpublish**
>  Dit zijn de belangrijkste termen voor de acties die uw inhoud openbaar maken in uw publicatieomgeving (of niet).
>
>* **activeert/deactiveert**
>  Deze termen zijn synoniem met publiceren/verwijderen.
>
>* **Replicatie/Replicatie**
>  Dit zijn de technische termen die worden gebruikt om de beweging van gegevens (bijvoorbeeld pagina-inhoud, bestanden, code, gebruikerscommentaren) aan te geven van de ene omgeving naar de andere, dat wil zeggen bij het publiceren of omgekeerde replicatie van gebruikersopmerkingen.
>

#### Dispatcher {#dispatcher}

Om prestaties voor bezoekers aan uw website te optimaliseren, voert **[Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html)** lading het in evenwicht brengen en het in het voorgeheugen onderbrengen uit.
