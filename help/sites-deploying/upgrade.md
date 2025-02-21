---
title: Upgrade uitvoeren naar Adobe Experience Manager 6.5
description: Leer meer over de basisbeginselen van het upgraden van een oudere Adobe Experience Manager-installatie (AEM) naar AEM 6.5.
contentOwner: sarchiz
topic-tags: upgrading
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 956da2542a958ee6548ede63a7e564f5a4705552
workflow-type: tm+mt
source-wordcount: '656'
ht-degree: 0%

---

# Upgrade uitvoeren naar Adobe Experience Manager (AEM) 6.5 {#upgrading-to-aem}

In dit gedeelte wordt de upgrade van een AEM-installatie naar AEM 6.5 besproken:

* [Uw upgrade plannen](/help/sites-deploying/upgrade-planning.md)
* [De complexiteit van upgrades beoordelen met patroondetector](/help/sites-deploying/pattern-detector.md)
* [ Achterwaartse Verenigbaarheid in AEM 6.5 ](/help/sites-deploying/backward-compatibility.md)
  <!--* [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->
* [Upgradeprocedure](/help/sites-deploying/upgrade-procedure.md)
* [Code en aanpassingen bijwerken](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Onderhoudstaken vóór upgrade](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Een op locatie uitgevoerde upgrade uitvoeren](/help/sites-deploying/in-place-upgrade.md)
* [Controles en probleemoplossing na upgrade](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Duurzame verbeteringen](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

Om gemakkelijker te kunnen verwijzen naar de AEM-instanties die bij deze procedures betrokken zijn, worden in deze artikelen de volgende termen gebruikt:

* De *bron* instantie is de instantie van AEM die u van bevordert.
* De *doel* instantie is die u bevordert aan.

## Wat is er veranderd? {#what-has-changed}

Hieronder vindt u een aantal belangrijke wijzigingen in de afgelopen paar versies van AEM:

AEM 6.0 introduceerde de nieuwe Jackrabbit Oak-opslagplaats. De persistentiemanagers werden vervangen door [ Micro Kernels ](/help/sites-deploying/platform.md#contentbody_title_4). Vanaf versie 6.1 wordt CRX2 niet meer ondersteund. Een migratiehulpmiddel genoemd crx2oak moet worden in werking gesteld om CRX2 bewaarplaatsen van 5.6.1 instanties te migreren. Voor meer informatie, zie [ Gebruikend het Hulpmiddel van de Migratie CRX2OAK ](/help/sites-deploying/using-crx2oak.md).

Als Assets Insights wordt gebruikt en u een upgrade uitvoert vanaf een versie die ouder is dan AEM 6.2, moeten assets worden gemigreerd en id&#39;s laten genereren via een JMX-boon. Voor interne tests van Adobe werden 125.000 bedrijfsmiddelen in een TarMK-omgeving over een uur gemigreerd, maar de resultaten kunnen afwijken.

6.3 introduceerde een nieuw formaat voor `SegmentNodeStore`, dat de basis van de implementatie TarMK vormt. Als u een upgrade uitvoert van een versie die ouder is dan AEM 6.3, is hiervoor een migratie naar de opslagplaats vereist als onderdeel van de upgrade, met inbegrip van systeemdowntime.

Adobe Engineering schat dit op ongeveer 20 minuten. Opnieuw indexeren is niet nodig. Er is ook een nieuwe versie van het crx2oak-gereedschap uitgebracht om te werken met de nieuwe opslaglocatie-indeling.

**Deze migratie wordt niet vereist als bevordering van AEM 6.3 aan AEM 6.5.**

De onderhoudstaken vóór de upgrade zijn geoptimaliseerd ter ondersteuning van automatisering.

De opdrachtregelgebruiksopties voor het gereedschap crx2oak zijn gewijzigd en zijn zo automatievriendelijk en ondersteunen meer upgradepaden.

De controles na de upgrade zijn ook automatiseringsvriendelijk gemaakt.

De periodieke vuilinzameling van revisies en de inzameling van het huisvuil van de gegevensopslag zijn nu routinematige onderhoudstaken die periodiek moeten worden uitgevoerd. Met de introductie van AEM 6.3 biedt Adobe ondersteuning voor het opschonen van online revisies en raadt het deze aan. Zie ](/help/sites-deploying/revision-cleanup.md) van de Opruiming van de Revisie [ voor informatie over hoe te om deze taken te vormen.

AEM introduceert onlangs de [ Detector van het Patroon ](/help/sites-deploying/pattern-detector.md) voor beoordeling van ingewikkeldheid van de verbetering aangezien u voor de verbetering begint te plannen. 6.5 heeft ook een sterke nadruk op [ achterwaartse verenigbaarheid ](/help/sites-deploying/backward-compatibility.md) van eigenschappen. Tot slot worden de beste praktijken voor [ duurzame verbeteringen ](/help/sites-deploying/sustainable-upgrades.md) ook toegevoegd.

Zie de volledige releaseopmerkingen voor meer informatie over wat er in recente AEM-versies anders is gewijzigd:

* [Opmerkingen bij de release van Adobe Experience Manager 6.5 Nieuwste Service Pack](/help/release-notes/release-notes.md)

## Overzicht van upgrade {#upgrade-overview}

Het upgraden van AEM is een proces dat uit meerdere stappen bestaat en soms meerdere maanden duurt. Het volgende overzicht is verstrekt als overzicht van wat inbegrepen is in een verbeteringsproject en de inhoud die in deze documentatie is omvat:

![ screen_shot_2018-03-30at80708am ](assets/screen_shot_2018-03-30at80708am.png)

## Upgradestroom {#upgrade-overview-1}

In het onderstaande diagram wordt de algemene aanbevolen stroom gemarkeerd met de upgradeaanpak. Let op de nieuwe functies die Adobe heeft geïntroduceerd. De verbetering zou met de Detector van het Patroon moeten beginnen (zie [ die de Complexiteit van de Verbetering met de Detector van het Patroon ](/help/sites-deploying/pattern-detector.md)) beoordeelt die u zou moeten laten beslissen de weg u voor verenigbaarheid met AEM 6.4 wilt nemen die op de patronen in het geproduceerde rapport wordt gebaseerd.

Er was een significante nadruk in 6.5 om alle nieuwe eigenschappen achteruit compatibel te houden, maar in gevallen waar u nog enkele achterwaartse verenigbaarheidskwesties ziet, laat de verenigbaarheidswijze u ontwikkeling tijdelijk uitstellen om uw douanecode volgzaam met 6.5 te houden. Deze benadering helpt u ontwikkelingsinspanning onmiddellijk na de verbetering (zie [ Achterwaartse Verenigbaarheid in AEM 6.5 ](/help/sites-deploying/backward-compatibility.md)) vermijden.

Tot slot in uw 6.5 ontwikkelingscyclus, helpen de eigenschappen die onder Duurzame Verbeteringen (zie [ Duurzame Verbeteringen ](/help/sites-deploying/sustainable-upgrades.md)) worden geïntroduceerd u beste praktijken volgen om toekomstige verbeteringen nog efficiënter en naadloos te maken.

![ 6_4_upgrade_overviewflow-newpage3 ](assets/6_4_upgrade_overviewflowchart-newpage3.png)
