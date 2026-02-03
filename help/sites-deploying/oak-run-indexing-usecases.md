---
title: Oak-run.jar Indexing Use cases
description: Leer meer over de verschillende gebruikersgevallen voor het indexeren met het Oak-programma.
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
noindex: true
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: a7a8a20a-e513-43df-80b7-1e6daf957f20
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '1348'
ht-degree: 0%

---

# Oak-run.jar Indexing Use cases{#oak-run-jar-indexing-use-cases}

Oak-in werking stelt steunt het indexeren van gebruiksgevallen op de bevellijn zonder het moeten de uitvoering van deze gebruiksgevallen door middel van AEM JMX console organiseren.

De volgende overkoepelende voordelen van de opdrachtmethode `oak-run.jar` index voor het beheer van Oak-indexen zijn mogelijk:

* Oak-run index command verstrekt een nieuwe indexerende toolset sinds de versie van AEM 6.4.
* Oak-run verkort tijd-aan-herdex die herindextijden op grotere bewaarplaatsen vermindert.
* Oak-run vermindert het verbruik van bronnen tijdens herindexering in AEM, wat resulteert in over het algemeen betere systeemprestaties.
* Oak-run biedt out-of-band herindexering, ondersteunende situaties waarin productie beschikbaar moet zijn, en kan geen onderhoud of downtime tolereren die anders vereist zijn om opnieuw te indexeren.

De onderstaande secties bevatten voorbeeldopdrachten. Oak-run index command ondersteunt alle NodeStore- en BlobStore-instellingen. De voorbeelden die hieronder worden gegeven, zijn voor instellingen met FileDataStore en SegmentNodeStore.

## Hoofdlettergebruik 1 - Indexconsistentiecontrole {#usercase1indexconsistencycheck}

Dit geval van gebruik is verwant met indexcorruptie. Soms was het niet mogelijk om te bepalen welke indexen corrupt zijn. Daarom heeft Adobe instrumenten beschikbaar gesteld die:

* Voert indexconsistentiecontroles op alle indexen uit en verstrekt een rapport waarop indexen geldig zijn en die ongeldig zijn.
* De werktuigen zijn ook bruikbaar als AEM niet toegankelijk is;
* Het is gebruiksvriendelijk.

Gebruik `--index-consistency-check` om te controleren op beschadigde indexen:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-consistency-check
```

Deze bewerking genereert een rapport in `indexing-result/index-consistency-check-report.txt` . Zie hieronder voor een voorbeeldrapport:

```
Valid indexes :
        - /content/oak:index/enablementResourceName
        - /oak:index/cqProjectLucene
        - /oak:index/cqTagLucene
        - /oak:index/lucene
        - /oak:index/ntBaseLucene
        - /oak:index/socialLucene
    Invalid indexes :
        - /oak:index/atDamIndex
        - /oak:index/atIndex
        - /oak:index/cqPageLucene
        - /oak:index/damAssetLucene
        - /oak:index/groups
        - /oak:index/slingeventJob
        - /oak:index/users
        - /oak:index/workflowDataLucene
    Ignored indexes as these are not of type lucene:
        - /oak:index/acPrincipalName
        - /oak:index/active
```

### Voordelen {#uc1benefits}

Ondersteunings- en systeembeheerders kunnen met de gereedschappen beschadigde indexen snel identificeren en opnieuw indexeren.

## Hoofdlettergebruik 2 - Indexstatistieken {#usecase2indexstatistics}

Voor het diagnostiseren van sommige gevallen rond vraagprestaties, vereiste Adobe vaak bestaande indexdefinitie, op index betrekking hebbende statistieken van de klantenopstelling. Om het oplossen van problemen gemakkelijker te maken, heeft Adobe tooling gecreeerd die het volgende doet:

1. Alle indexdefinitie in het systeem in één JSON-bestand dumpen.

1. Belangrijke statistieken uit bestaande indexen dumpen;

1. de inhoud van de pompindex voor offline analyse;

1. Het kan ook worden gebruikt als AEM niet toegankelijk is

U kunt de bovenstaande bewerkingen uitvoeren met de volgende indexopdrachten:

* `--index-info` - Verzamelt en dumpt verschillende statistieken met betrekking tot de indexen

* `--index-definitions` - Verzamelt en dumpt indexdefinities

* `--index-dump` - Indexinhoud wordt gedumpt

Zie hieronder een voorbeeld van hoe de bevelen in de praktijk werken:

```shell
java -jar oak-run*.jar index --fds-path=/path/to/datastore  /path/to/segmentstore/ --index-info --index-definitions --index-dump
```

De rapporten worden gegenereerd in `indexing-result/index-info.txt` en `indexing-result/index-definitions.json`

Bovendien worden de zelfde details verstrekt door middel van de Console van het Web en zouden deel van de configuratiedumpit zip uitmaken. Ze kunnen op de volgende locatie worden benaderd:

`https://serverhost:serverport/system/console/status-oak-index-defn`

### Voordelen {#uc2benefits}

Dit hulpmiddel laat het verzamelen van alle vereiste details met betrekking tot het indexeren of vraagkwesties toe snel en vermindert de tijd besteed in het halen van deze informatie.

## Hoofdlettergebruik 3 - Opnieuw indexeren {#usecase3reindexing}

Afhankelijk van de [&#x200B; scenario&#39;s &#x200B;](https://jackrabbit.apache.org/oak/docs/query/indexing.html#reindexing), soms, moet het opnieuw indexeren worden uitgevoerd. U herindexeert momenteel de markering `reindex` op `true` in het indexdefinitieknooppunt met behulp van CRXDE of de gebruikersinterface van Indexbeheer. Nadat u de markering hebt ingesteld, wordt het opnieuw indexeren asynchroon uitgevoerd. Nadat de markering is ingesteld, wordt het opnieuw indexeren asynchroon uitgevoerd.

Enkele punten die u wilt opmerken bij het opnieuw indexeren:

* Het opnieuw indexeren gaat veel langzamer bij `DocumentNodeStore` -instellingen dan bij `SegmentNodeStore` -instellingen waarbij alle inhoud lokaal is.

* Met het huidige ontwerp, terwijl het opnieuw indexeren gebeurt, wordt async indexer geblokkeerd en alle andere async indexen worden verouderd en niet bijgewerkt tijdens het indexeren. Als het systeem in gebruik is, kunnen gebruikers bijgevolg geen actuele resultaten zien;
* Bij de herindexering wordt de hele opslagplaats doorkruist, wat een grote belasting kan betekenen voor de AEM-installatie en zo van invloed kan zijn op de gebruikerservaring.
* Voor een `DocumentNodeStore` -installatie waarbij opnieuw indexeren veel tijd in beslag kan nemen, kan een fout in de verbinding met een Mongo-database tijdens de bewerking de indexering onderbreken. In dat geval moet u de indexering helemaal opnieuw starten.


* Soms kan het opnieuw indexeren veel tijd in beslag nemen door het extraheren van tekst. Een dergelijk probleem kan zich voordoen wanneer dit specifiek is voor instellingen met veel PDF-bestanden, waarbij de tijd die aan tekstextractie wordt besteed van invloed kan zijn op de indexatietijd.

Om deze doelstellingen te bereiken, steunt de in werking gestelde Oak-indextooling verschillende wijzen voor het opnieuw indexeren die kunnen worden gebruikt zoals vereist. De Oak-run-indexopdracht biedt de volgende voordelen:

* **out-of-band het opnieuw indexeren** - Oak-looppas het opnieuw indexeren kan van een lopende opstelling van AEM afzonderlijk worden gedaan en zo, minimaliseert het het effect op de instantie van AEM die in gebruik is;

* **out-of-lane het opnieuw indexeren** - het opnieuw indexeren vindt plaats zonder het beïnvloeden van indexerende verrichtingen. De async-indexeerder kan andere indexen blijven indexeren;

* **Vereenvoudigde herdex voor installaties DocumentNodeStore** - voor `DocumentNodeStore` installaties, kan het opnieuw indexeren met één enkel bevel worden gedaan dat ervoor zorgt dat het opnieuw indexeren op de meest optimale manier wordt gedaan;

* **Steunt het bijwerken van indexdefinities en het introduceren van nieuwe indexdefinities**

### Opnieuw indexeren - DocumentNodeStore {#reindexdocumentnodestore}

Voor `DocumentNodeStore` -installaties kunt u opnieuw indexeren met behulp van één Oak-run-opdracht:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore mongodb://server:port/aem
```

Deze bewerking biedt de volgende voordelen:

* Minimale invloed op het uitvoeren van AEM-instanties. De meeste leesbewerkingen kunnen worden uitgevoerd op secundaire servers en het uitvoeren van AEM-caches heeft geen negatieve invloed op alle verplaatsingen die nodig zijn voor opnieuw indexeren.
* Gebruikers kunnen ook een JSON van een nieuwe of bijgewerkte index opgeven via de optie `--index-definitions-file` .

### Opnieuw indexeren - SegmentNodeStore {#reindexsegmentnodestore}

Voor `SegmentNodeStore` -installaties kan opnieuw indexeren op een van de volgende manieren worden uitgevoerd:

#### Online opnieuw indexeren - SegmentNodeStore {#onlinereindexsegmentnodestore}

Voer de markering `reindex` in op de gebruikelijke manier waarop opnieuw indexeren wordt uitgevoerd.

#### Online opnieuw indexeren - SegmentNodeStore - De AEM-instantie wordt uitgevoerd {#onlinereindexsegmentnodestoretheaeminstanceisrunning}

Voor `SegmentNodeStore` -installaties heeft slechts één proces toegang tot segmentbestanden in de modus lezen-schrijven. Voor sommige bewerkingen in de indexering door Oak moeten dan ook handmatige aanvullende stappen worden ondernomen, waaronder:

1. Staptekst.
1. Verbind `oak-run` met de zelfde bewaarplaats die door AEM op read-only wijze wordt gebruikt.
1. Indexering uitvoeren met het volgende voorbeeld:

   ```shell
   java -jar oak-run-1.7.6.jar index --fds-path=/Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/datastore/ --checkpoint 26b7da38-a699-45b2-82fb-73aa2f9af0e2 --reindex --index-paths=/oak:index/lucene /Users/dhasler/dev/cq/quickstart/target/crx-quickstart/repository/segmentstore/
   ```

1. Importeer ten slotte de gemaakte indexbestanden via de `IndexerMBean#importIndex` -bewerking vanaf het pad waar de indexeringsbestanden zijn opgeslagen door Oak nadat de bovenstaande opdracht is uitgevoerd.

In dit scenario hoeft u de AEM-server niet te stoppen of een nieuwe instantie in te stellen. Als indexering echter gepaard gaat met een verplaatsing van de hele opslagplaats, zou de I/O-belasting van de installatie toenemen, wat negatieve gevolgen zou hebben voor de prestaties bij uitvoering.

#### Online opnieuw indexeren - SegmentNodeStore - De AEM-instantie wordt afgesloten {#onlinereindexsegmentnodestoreaeminstanceisdown}

Voor `SegmentNodeStore` -installaties kunt u opnieuw indexeren met behulp van één Oak-run-opdracht. De AEM-instantie moet echter worden afgesloten.

U kunt het opnieuw indexeren met het volgende bevel teweegbrengen:

```shell
java -jar oak-run*.jar index --reindex --index-paths=/oak:index/lucene --read-write --fds-path=/path/to/datastore  /path/to/segmentstore/
```

Het verschil tussen deze aanpak en de hierboven beschreven aanpak is dat het maken van controlepunten en het importeren van indexen automatisch worden uitgevoerd. Het nadeel is dat AEM tijdens het proces omlaag moet zijn.

#### Buiten-de-band herindex - SegmentNodeStore {#outofbandreindexsegmentnodestore}

In dit geval kunt u opnieuw indexeren op een gekloonde instelling om de invloed op de actieve AEM-instantie tot een minimum te beperken:

1. Een controlepunt maken door middel van een JMX-bewerking. Ga naar de [&#x200B; Console JMX &#x200B;](/help/sites-administering/jmx-console.md) en onderzoek naar `CheckpointManager`. Dan, klik **createCheckpoint (lange p1)** verrichting die een hoge waarde voor afloop in seconden gebruikt (bijvoorbeeld, **2592000**).
1. Kopieer de map `crx-quickstart` naar een nieuwe computer.
1. Herindexeren uitvoeren met de opdracht Oak-run index.

1. Kopieer de gegenereerde indexbestanden naar een AEM-server.

1. Importeer de indexbestanden via JMX.

In dit geval moet de Data Store toegankelijk zijn vanuit een andere instantie, wat mogelijk niet mogelijk is wanneer `FileDataStore` zich op een cloudoplossing zoals EBS bevindt. Deze situatie sluit het scenario uit waarin `FileDataStore` ook wordt gekloond. Als in de indexdefinitie geen fullText-indexering wordt uitgevoerd, is toegang tot `DataStore` niet vereist.

## Hoofdlettergebruik 4 - Indexdefinities bijwerken {#usecase4updatingindexdefinitions}

Momenteel, kunt u de veranderingen van de indexdefinitie als [&#x200B; ACS verschepen verzekeren het pakket van de Index &#x200B;](https://adobe-consulting-services.github.io/acs-aem-commons/features/ensure-oak-index/index.html). U kunt de indexdefinities in een inhoudspakket verzenden en vervolgens opnieuw indexeren door de markering `reindex` in te stellen op `true` .


Dit werkt goed voor kleinere installaties waar het opnieuw indexeren niet lang duurt. Voor grote gegevensbanken gebeurt herindexering echter veel langer. In dergelijke gevallen kunt u nu de Oak-run-index gebruiken.

Oak-run biedt nu ondersteuning voor het opgeven van indexdefinities in JSON-indeling en het maken van index in out-of-band modus, waarbij geen wijzigingen worden uitgevoerd op een live instantie.

Voor dit geval moet u het volgende in overweging nemen:

1. Een ontwikkelaar zou de indexdefinities op een lokale instantie bijwerken en dan een JSON-bestand met indexdefinitie genereren via de optie `--index-definitions` .
1. De bijgewerkte JSON wordt vervolgens aan de systeembeheerder gegeven.
1. De Beheerder van het systeem volgt de out-of-band benadering en bereidt de index op een verschillende installatie voor.
1. Wanneer de gegenereerde indexbestanden zijn voltooid, worden deze geïmporteerd in een AEM-installatie die wordt uitgevoerd.
