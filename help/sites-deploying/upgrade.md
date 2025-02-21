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
source-git-commit: f66bb283e5c2a746821839269e112be8c2714ba7
workflow-type: tm+mt
source-wordcount: '317'
ht-degree: 0%

---

# Upgrade naar Adobe Experience Manager (AEM) 6,5 LTS {#upgrading-to-aem}

>[!NOTE]
>De verbetering aan AEM 6.5 LTS wordt gesteund van de laatste 6 pakken van de Dienst.

In dit gedeelte wordt de upgrade van een AEM-installatie naar AEM 6.5 besproken:

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

Hieronder vindt u een aantal belangrijke wijzigingen in de afgelopen paar versies van AEM:

1. De Foundation-laag is geüpgraded voor ondersteuning van Java 17 (die open-source lagen bundels van Apache Sling, Apache Felix en Apache Jackrabbit Oak omvat)

1. De AEM 6.5 LTS-verpakking voor jar ondersteunt nu de specificaties 5 van de Jarkarta Servlet API&#39;s en het verpakken van oorlogen kan worden ingezet voor servletcontainers die Jakarta Servlet API-specificaties 5/6 implementeren

1. De verpakking van AEM 6.5 LTS uber-jar is veranderd. Gelieve te verwijzen [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) voor meer informatie.

### Oudere functies/artefacten verwijderd {#removed-legacy-features-artifacts}

De volgende verouderde oplossingen zijn verwijderd uit AEM 6.5 LTS. Voor meer informatie, gelieve te verwijzen naar TBD: verbinding om nota&#39;s en [ Lijst van Verouderde Bundels vrij te geven die na de Verbetering ](/help/sites-deploying/obsolete-bundles.md) worden verwijderd

1. Sociaal
1. Commerce
1. Screens
1. Wij-detailhandel
1. Integratie van zoeken en bevorderen

**Verwijderde Artefacten**

1. CRX-explorator
1. Crx2oak
1. Google guava (verwijderd vanwege beveiligingsproblemen)
1. Abdera-parser (verwijderd vanwege beveiligingskwetsbaarheden)
1. jdom (`org.apache.servicemix.bundles.jdom`) (verwijderd vanwege beveiligingskwetsbaarheden)
1. `com.github.jknack.handlebars` (verwijderd vanwege beveiligingskwetsbaarheden)

AEM 6.5 LTS richt zich sterk op achterwaartse compatibiliteit van functies en wordt geleverd met een analyseprogramma. Zie [ het Beoordelen van de Complexiteit van de Verbetering met de Analysator van AEM ](/help/sites-deploying/pattern-detector.md) voor beoordeling van ingewikkeldheid aangezien u voor de verbetering begint te plannen. Meer informatie over wat anders is veranderd, zie hier de volledige versienota&#39;s. TBD: Koppeling naar releaseopmerkingen van AEM 6.5 LTS