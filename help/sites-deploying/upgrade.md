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
exl-id: ebc34847-dc3d-41ed-b0d6-f004c3debcd9
source-git-commit: 4c3402aa813c115625d624f3b33ca73d31bed850
workflow-type: tm+mt
source-wordcount: '198'
ht-degree: 0%

---

# Upgrade naar Adobe Experience Manager (AEM) 6,5 LTS {#upgrading-to-aem}

>[!NOTE]
>De verbetering aan AEM 6.5 LTS wordt gesteund van de laatste 6 pakken van de Dienst.

In dit gedeelte wordt de upgrade van een AEM-installatie naar AEM 6.5 LTS besproken:

<!-- Alexandru: drafting for now 

* [Planning Your Upgrade](/help/sites-deploying/upgrade-planning.md)
* [Assessing the Upgrade Complexity with Pattern Detector](/help/sites-deploying/pattern-detector.md)
* [Backward Compatibility in AEM 6.5](/help/sites-deploying/backward-compatibility.md)
  This was drafted before: * [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

<!--
* [Upgrade Procedure](/help/sites-deploying/upgrade-procedure.md)
* [Upgrading Code and Customizations](/help/sites-deploying/upgrading-code-and-customizations.md)
* [Pre-Upgrade Maintenance Tasks](/help/sites-deploying/pre-upgrade-maintenance-tasks.md)
* [Performing an In-Place Upgrade](/help/sites-deploying/in-place-upgrade.md)
* [Post Upgrade Checks and Troubleshooting](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md)
* [Sustainable Upgrades](/help/sites-deploying/sustainable-upgrades.md)
* [Lazy Content Migration](/help/sites-deploying/lazy-content-migration.md)

-->

Om gemakkelijker te kunnen verwijzen naar de AEM-instanties die bij deze procedures betrokken zijn, worden in deze artikelen de volgende termen gebruikt:

* De *bron* instantie is de instantie van AEM die u van bevordert.
* De *doel* instantie is die u bevordert aan.

## Wat is er veranderd? {#what-has-changed}

### Updates {#updates}

De laag van de stichting steunt nu Java 17 en Java 21, die recentste open-bronbundels van Apache Sling, Felix, en Jackrabbit Oak omvat. Bovendien is de verpakking van de AEM 6.5 LTS uber-jar veranderd. Bovendien zijn een aantal verouderde functies verwijderd uit AEM 6.5 LTS. Voor meer informatie, verwijs naar [ de nota&#39;s van de Versie ](/help/release-notes/release-notes.md#whats-new-what-s-new) en [ Lijst van de Verouderde Bundels die na de Verbetering ](/help/sites-deploying/obsolete-bundles.md) worden gedesinstalleerd

AEM 6.5 LTS richt zich sterk op achterwaartse compatibiliteit van functies en wordt geleverd met een analyseprogramma. Zie [ het Beoordelen van de Complexiteit van de Verbetering met de Analysator van AEM ](/help/sites-deploying/aem-analyzer.md) voor beoordeling van ingewikkeldheid aangezien u [ planning voor de verbetering ](/help/sites-deploying/upgrade-planning.md) begint.
