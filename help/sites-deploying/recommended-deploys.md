---
title: Aanbevolen implementaties
description: In dit artikel worden de aanbevolen topologieën voor AEM beschreven.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 9baa4111-831a-4b68-9ce5-82aeeb06e07f
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '1493'
ht-degree: 0%

---

# Aanbevolen implementaties{#recommended-deployments}

>[!NOTE]
>
>Deze pagina verwijst naar geadviseerde topologieën voor AEM. Voor meer informatie bij het groeperen van mogelijkheden en hoe te om hen te vormen, zie de [ Apache Sling API documentatie van de Ontdekking ](https://sling.apache.org/documentation/bundles/discovery-api-and-impl.html).

MicroKernels fungeren vanaf AEM 6.2 als persistentiemanagers. Het kiezen van één om uw behoeften te passen hangt van het doel van uw instantie en het plaatsingstype af u overweegt.

De volgende voorbeelden moeten een indicatie zijn van wat hun aanbevolen gebruik in de meest gangbare AEM-instellingen is.

## Implementatiescenario&#39;s {#deployment-scenarios}

### Single TarMK-instantie {#single-tarmk-instance}

In dit scenario, loopt één enkele instantie TarMK op één enkele server.

**dit is de standaardplaatsing voor auteursinstanties.**

![ chlimage_1-15 ](assets/chlimage_1-15.png)

De voordelen:

* eenvoudig
* Eenvoudig onderhoud
* Goede prestaties

De nadelen:

* Niet schaalbaar buiten de grenzen van de servercapaciteit
* Geen failover-capaciteit

### TarMK Cold Standby {#tarmk-cold-standby}

Eén TarMK-instantie fungeert als de primaire instantie. De opslagplaats van de primaire opslagplaats wordt gerepliceerd naar een stand-by failover-systeem.

Het koude reservemechanisme kan ook als steun worden gebruikt omdat de volledige bewaarplaats constant aan de failoverserver wordt herhaald. De failoverserver loopt op koude reservewijze, wat betekent dat slechts HttpReceiver van de instantie loopt.

![ chlimage_1-16 ](assets/chlimage_1-16.png)

De voordelen:

* Eenvoud
* Onderhoudsmogelijkheden
* Prestaties
* Failover

De nadelen:

* Niet schaalbaar buiten de grenzen van de servercapaciteit
* Eén server is meestal inactief
* De failover is niet automatisch. Het moet extern worden ontdekt alvorens het failoversysteem verzoeken kan beginnen te dienen.

>[!NOTE]
>
>Voor meer informatie over hoe te om AEM met TarMK te vormen Koude Reserve, zie [ dit ](/help/sites-deploying/tarmk-cold-standby.md) artikel.

>[!NOTE]
>
>De plaatsing van de Reserve van de Koude in dit voorbeeld TarMK vereist dat zowel de primaire als reserve instanties afzonderlijk worden vergunning gegeven, aangezien er constante replicatie aan de failoverserver is. Voor meer informatie over vergunning verlenen, raadpleeg de [ Algemene het Vergunningstermijnen van Adobe ](https://www.adobe.com/legal/terms/enterprise-licensing.html).

### TarMK Farm {#tarmk-farm}

Meerdere Oak-instanties voeren elk uit met één TarMK-instantie. De TarMK-opslagplaatsen zijn onafhankelijk en moeten gesynchroniseerd blijven.

Het houden van de bewaarplaatsen in synchronisatie wordt voorzien van het feit dat de auteurserver de zelfde inhoud aan elk landbouwbedrijflid publiceert. Voor meer informatie, zie [ Replicatie ](/help/sites-deploying/replication.md).

**dit is de standaardplaatsing voor publiceer milieu&#39;s.**

![ chlimage_1-17 ](assets/chlimage_1-17.png)

De voordelen:

* Prestaties
* Schaalbaarheid voor leestoegang
* Failover

### Oak Cluster met MongoMK-failover voor hoge beschikbaarheid in één datacenter {#oak-cluster-with-mongomk-failover-for-high-availability-in-a-single-datacenter}

>[!NOTE]
>
>De minimaal ondersteunde versie van Mongo is Mongo 6.

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die is ingesteld binnen één datacenter. In feite wordt er een actief-actief cluster gemaakt voor de AEM-auteuromgeving. Replicasets in MongoDB worden gebruikt om hoge beschikbaarheid en redundantie te bieden in het geval van een hardware- of netwerkstoring.

![ chlimage_1-18 ](assets/chlimage_1-18.png)

De voordelen:

* Mogelijkheid om horizontaal te schalen met nieuwe AEM-auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag

De nadelen:

* De prestaties kunnen lager zijn dan met TarMK voor sommige scenario&#39;s

### Oak-cluster met MongoMK-failover over meerdere datacenters {#oak-cluster-with-mongomk-failover-across-multiple-datacenters}

Deze aanpak impliceert dat meerdere Oak-instanties toegang hebben tot een MongoDB-replica die in meerdere datacenters is ingesteld. In feite wordt er een actief-actief cluster voor de AEM-auteuromgeving gemaakt. Met meerdere datacenters biedt de replicatie van MongoDB dezelfde hoge beschikbaarheid en redundantie, maar nu ook de mogelijkheid om een storing in het datacenter te verwerken.

![ oakclustermongofailover2datacenters ](assets/oakclustermongofailover2datacenters.png)

De voordelen:

* Mogelijkheid om horizontaal te schalen met nieuwe AEM-auteur-instanties
* Hoge beschikbaarheid, overtolligheid, en geautomatiseerde failover van gegevenslaag (met inbegrip van gegevenscentrumstroomonderbrekingen)

>[!NOTE]
>
>In het diagram hierboven, wordt Server 3 van AEM en Server 4 van AEM voorgesteld met een inactieve status veronderstellend een netwerklatentie tussen de Servers van AEM in Centrum 2 van Gegevens en het primaire knooppunt MongoDB in Centrum 1 van Gegevens die hoger is dan het vereiste dat onder [ Adobe Experience Manager met MongoDB - Controlklists ](/help/sites-deploying/aem-with-mongodb.md#checklists) wordt gedocumenteerd. Als de maximale latentie compatibel is met de vereisten, bijvoorbeeld door het gebruik van beschikbaarheidszones, kunnen de AEM-servers in Data Center 2 ook actief zijn, waardoor een actief-actieve AEM-cluster in meerdere datacenters ontstaat.

>[!NOTE]
>
>Voor extra informatie over de architecturale concepten MongoDB die in deze sectie worden beschreven, zie {de Replicatie van 0} MongoDB [&#128279;](https://docs.mongodb.org/manual/replication/).

## Microkorrels: één voor gebruik {#microkernels-which-one-to-use}

De basisregel waarmee rekening moet worden gehouden bij het kiezen tussen de twee beschikbare microkorrels is dat TarMK ontworpen is voor prestaties, terwijl MongoMK wordt gebruikt voor schaalbaarheid.

U kunt deze besluitmatrices gebruiken om te bepalen wat het beste type implementatie is dat aan uw vereisten is aangepast.

Adobe raadt TarMK ten zeerste aan de standaardpersistentietechnologie te zijn die door klanten wordt gebruikt in alle implementatiescenario&#39;s, voor zowel de AEM-auteur als de-publicatie, behalve in de hieronder beschreven gebruiksgevallen.

### Uitzonderingen voor het kiezen van AEM MongoMK in plaats van TarMK in instantie van Auteur {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-author-instances}

De primaire reden voor het kiezen van de MongoMK persistence backend over TarMK is de instanties horizontaal te schalen. Dit betekent dat er altijd twee of meer actieve auteur-instanties moeten worden uitgevoerd en dat MongoDB moet worden gebruikt als het opslagsysteem voor persistentie. De noodzaak om meer dan één auteurinstantie in werking te stellen vloeit over het algemeen voort uit het feit dat de CPU en geheugencapaciteit van één enkele server, die alle gezamenlijke auteursactiviteiten steunt, niet meer duurzaam is.

Het is bijna onmogelijk om te voorspellen wat het precieze gelijktijdige model zal zijn nadat een nieuwe site live gaat. Daarom raadt Adobe u aan de volgende criteria in overweging te nemen bij het beoordelen of MongoMK en twee of meer actieve knooppunten van de Auteur moeten worden gebruikt:

1. Aantal benoemde gebruikers verbonden in een dag: in de duizenden of meer.
1. Aantal gelijktijdige gebruikers: in honderden of meer.
1. Hoeveelheid ingenomen activa per dag: in honderdduizenden of meer.
1. Volume van paginabewerkingen per dag: in honderdduizenden of meer (inclusief automatische updates via Meerdere Sitebeheer of inname van nieuwsberichten).
1. Aantal zoekopdrachten per dag: in tienduizenden of meer.

>[!NOTE]
>
>[ Stevige Dag ](/help/sites-developing/tough-day.md) kan worden gebruikt om de prestaties van de toepassing van de klant in de context van de opgestelde hardwareconfiguratie te evalueren.

Een minimumplaatsing met MongoDB zal typisch de volgende topologie impliceren:

* Een MongoDB-replicaset bestaande uit één primair knooppunt, twee secundaire knooppunten met elk van de MongoDB-instanties die in een beschikbaarheidszone met een latentie onder 15 milliseconden op elk knooppunt worden uitgevoerd;
* Een cluster van auteurinstanties met één leaderknoop, één niet-leaderknooppunt en beide actief op elk moment, met elk van de auteurinstanties die in elk van de datacenters worden uitgevoerd, waar de primaire en secundaire MongoDB-instanties worden uitgevoerd.

Daarnaast wordt het ten zeerste aanbevolen de datastore op een gedeeld bestandssysteem of Amazon S3 te configureren, zodat de elementen of binaire bestanden niet in MongoDB worden opgeslagen. Dit zorgt voor optimale prestaties binnen de implementatie.

Een van de extra voordelen van de implementatie van een MongoDB-replicaset met een cluster van twee of meer auteurinstanties is dat er een geautomatiseerd herstelscenario met minimale downtime bestaat als er auteurinstanties, MongoDB-replica of een volledige datacenterfout zijn. Niettemin zou de keuze van MongoMK over TarMK niet alleen door het terugwinningsvereiste moeten worden gedreven, aangezien TarMK ook een minimale downtime oplossing met een gecontroleerd failovermechanisme kan verstrekken.

Als tijdens de eerste 18 maanden van implementatie naar verwachting niet aan de bovenstaande criteria wordt voldaan, wordt het aangeraden eerst AEM te implementeren met TarMK, vervolgens uw configuratie opnieuw te evalueren op een latere datum waarop de bovenstaande criteria van toepassing zijn, en ten slotte te bepalen of u op TarMK moet blijven of naar MongoMK moet migreren.

### Uitzonderingen voor het kiezen van AEM MongoMK in TarMK bij publicatie-instanties {#exceptions-for-choosing-aem-mongomk-over-tarmk-on-publish-instances}

Het wordt afgeraden MongoMK te implementeren voor publicatie-instanties. De publicatielaag van de plaatsing wordt bijna altijd opgesteld als landbouwbedrijf van volledig onafhankelijke publiceer instanties die TarMK in werking stellen, die in synchronisatie door inhoud van de auteursinstanties te herhalen worden gehouden. Deze &quot;gedeelde niets&quot;architectuur, behoorlijk aan de publiceer instanties, staat de plaatsing van toe publiceert rij om horizontaal op een lineaire manier te schrapen. De landbouwbedrijftopologie verstrekt ook het voordeel om het even welke update of verbetering toe te passen om instanties op een voortschrijdende basis te publiceren, zodat om het even welke verandering in publiceer rij geen onderbreking zal vereisen.

### Vereisten en aanbevelingen bij de implementatie van AEM met MongoMK {#prerequisites-and-recommendations-when-deploying-aem-with-mongomk}

Er is een reeks voorwaarden en aanbevelingen beschikbaar als u een MongoMK-implementatie voor AEM overweegt:

**Verplichte eerste vereisten voor plaatsingen MongoDB:**

1. De mongoDB-implementatiearchitectuur en -grootte moeten deel uitmaken van de projectimplementatie met hulp van Adobe Consulting- of MongoDB-architecten die bekend zijn met AEM;
1. De deskundigheid MongoDB moet binnen de partner of het klantenteam aanwezig zijn om vertrouwen in het kunnen een bestaande of nieuwe milieu te kunnen handhaven MongoDB;
1. U kunt ervoor kiezen om de commerciële of open-sourceversie van MongoDB te implementeren (AEM ondersteunt beide), maar u moet een MongoDB-onderhouds- en ondersteuningscontract rechtstreeks aanschaffen bij MongoDB Inc.
1. AEM- en MongoDB-architecturen en -infrastructuren moeten in hun geheel goed zijn gedefinieerd en gevalideerd door een Adobe AEM Architect;
1. Bekijk het supportmodel voor AEM-implementaties met MongoDB.

**Sterke aanbevelingen voor plaatsingen MongoDB:**

* Raadpleeg het [ Overzicht van de Plaatsing MongoDB voor Adobe Experience Manager ](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager);
* Herzie [ Checklist van de Verrichtingen MongoDB ](https://docs.mongodb.org/manual/administration/production-checklist/);
* Woon a [ certificatieklasse op MongoDB - beschikbaar online ](https://university.mongodb.com/) bij.

>[!NOTE]
>
>Voor alle extra vragen over deze richtlijnen, eerste vereisten, en aanbevelingen contacteren [ de Zorg van de Klant van Adobe ](https://helpx.adobe.com/nl/marketing-cloud/contact-support.html).
