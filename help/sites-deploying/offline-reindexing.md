---
title: Offline opnieuw indexeren voor AEM
description: Leer hoe u offline herindexeringsmethoden kunt gebruiken om AEM-opslagplaatsen opnieuw te indexeren.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 076db19026a0992725062ec9965ff6c1cb84333e
workflow-type: tm+mt
source-wordcount: '1165'
ht-degree: 0%

---

# Offline opnieuw indexeren voor AEM {#offline-reindexing-for-aem}

## Inleiding {#introduction}

Voor AEM Assets-projecten, die doorgaans grote gegevensopslagruimten en een hoog niveau van uploads van bedrijfsmiddelen hebben, kan het opnieuw indexeren van Oak-indexen veel tijd in beslag nemen.

In deze sectie wordt beschreven hoe u het gereedschap Oak kunt gebruiken om offline opnieuw te indexeren. De voorgestelde stappen kunnen op [&#x200B; worden toegepast Lucene &#x200B;](https://jackrabbit.apache.org/oak/docs/query/lucene.html) indexen voor versies AEM 6.4 en hoger.

## Overzicht {#overview}

AEM-opslagruimten moeten vaak opnieuw worden gecomprimeerd om verschillende redenen, zoals wijzigingen in de indexdefinitie, optimalisatie van de prestaties of belangrijke wijzigingen in de inhoud. Het opnieuw indexeren is duur voor middelenimplementaties omdat tekst in elementen (bijvoorbeeld tekst in PDF-bestanden) wordt geëxtraheerd en geïndexeerd. Bij MongoMK-opslagruimten blijven gegevens via het netwerk behouden, waardoor er meer tijd nodig is voor opnieuw indexeren. De oplossing moet het opnieuw indexeren **offline** uitvoeren gebruikend het Oak-in werking gestelde hulpmiddel, dan de pre-gebouwde indexen in de lopende instantie van AEM invoeren. Deze benadering minimaliseert het opnieuw indexeren tijd en staat voor beter middelbeheer toe.

## Benadering {#approach}

![&#x200B; off-line-redexing-verbetering-tekst-extractie &#x200B;](assets/offline-reindexing-upgrade-process.png)

Het idee moet offline indexen creëren gebruikend het [&#x200B; Oak-in werking gestelde &#x200B;](/help/sites-deploying/indexing-via-the-oak-run-jar.md) hulpmiddel, dan hen invoeren in de lopende instantie van AEM. In het bovenstaande diagram wordt de methode voor het offline opnieuw indexeren weergegeven.

Bovendien is dit de orde van de stappen zoals die in de benadering worden beschreven:

1. Tekst van binaire tekens wordt als eerste geëxtraheerd
2. Indexdefinities worden gemaakt of bijgewerkt
3. Offlineindexen worden gemaakt
4. De indexen worden vervolgens geïmporteerd in de actieve AEM-instantie

### Tekst uitnemen {#text-extraction}

Om volledige indexering in AEM mogelijk te maken, wordt tekst uit binaire getallen zoals PDF geëxtraheerd en aan de index toegevoegd. Dit is meestal een kostbare stap in het indexeringsproces. Tekstomloop is een optimaliseringsstap die vooral wordt aanbevolen voor het opnieuw indexeren van opslagruimten voor elementen, aangezien er grote aantallen binaire getallen worden opgeslagen.

![&#x200B; off-line-redexing-verbetering-tekst-extractie &#x200B;](assets/offline-reindexing-upgrade-text-extraction.png)

Tekst van binaire bestanden die in het systeem zijn opgeslagen, kan worden geëxtraheerd met behulp van het gereedschap voor het uitvoeren van een eikel met behulp van de tikabibliotheek. Voor dit tekstextractieproces kan een kloon van het productiesysteem worden genomen en gebruikt. Dit proces leidt dan tot de tekstopslag, door de volgende stappen te gaan:

**1. De repository doorlopen en de details van binaries verzamelen**

Met deze stap maakt u een CSV-bestand met een paar binaire getallen, die een pad en een blob-id bevatten.

Voer de onderstaande opdracht uit vanuit de map waar u de index wilt maken. In het onderstaande voorbeeld wordt uitgegaan van de thuismap van de repository.

```
java java -jar oak-run.jar tika <nodestore path> --fds-path <datastore path> --data-file text-extraction/oak-binary-stats.csv --generate
```

Waar `nodestore path` de `mongo_uri` of `crx-quickstart/repository/segmentstore/` is

Gebruik de parameter `--fake-ds-path=temp` in plaats van `–fds-path` om het proces te versnellen.

**2. Hergebruik de binaire tekstopslag beschikbaar in de bestaande index**

Pak de indexgegevens uit het bestaande systeem en extraheer de tekstwinkel.

U kunt de bestaande indexgegevens dumpen met de volgende opdracht:

```
java -jar oak-run.jar index <nodestore path> --fds-path=<datastore path> --index-dump
```

Waar `nodestore path` de `mongo_uri` of `crx-quickstart/repository/segmentstore/` is

Gebruik vervolgens de bovenstaande indexdump om de winkel te vullen:

```
java -jar oak-run.jar tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --index-dir ./indexing-result/index-dumps/<oak-index-name>/data populate
```

Waar `oak-index-name` de naam van de volledige tekstindex is, bijvoorbeeld &#39;lucene&#39;.

**3. Voer het tekstextractieproces uit met behulp van de tikabibliotheek voor de binaire getallen die in de bovenstaande stap zijn overgeslagen**

```
java -cp oak-run.jar:tika-app-*.jar org.apache.jackrabbit.oak.run.Main tika --data-file text-extraction/oak-binary-stats.csv --store-path text-extraction/store --fds-path <datastore path> extract
```

>[!NOTE]
>
>Gebruik dezelfde versie van Tika als in AEM.

Waar `datastore path` het pad naar de binaire gegevensopslag is.

De gemaakte tekstopslag kan worden bijgewerkt en opnieuw worden gebruikt voor toekomstige omschakelingsscenario&#39;s.

Voor meer details rond het proces van de tekstextractie, zie de [&#x200B; Oak-in werking gestelde documentatie &#x200B;](https://jackrabbit.apache.org/oak/docs/query/pre-extract-text.html).

### Offline opnieuw indexeren {#offline-reindexing}

![&#x200B; off-line-redexing-verbetering-off-line-redexing &#x200B;](assets/offline-reindexing-upgrade-offline-reindexing.png)

Maak de index van Lucene offline. Als het gebruiken van MongoMK, wordt het geadviseerd om het op één van de knopen in werking te stellen MongoMK, aangezien dit netwerkoverheadkosten vermijdt.

Volg onderstaande stappen om de index offline te maken:

**1. Oak Lucene-indexdefinities genereren**

Zet de bestaande indexdefinities neer. Indexdefinities kunnen worden gegenereerd met de Adobe Granite-opslagbundel en eak-run.

Als u de indexdefinitie van de AEM-instantie wilt dumpen, voert u deze opdracht uit:

>[!NOTE]
>
>Voor meer details over het dumpen van indexdefinities, raadpleeg de [&#x200B; documentatie van Oak &#x200B;](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#async-index-data).

```
java -jar oak-run.jar index --fds-path <datastore path> <nodestore path> --index-definitions
```

Waar `datastore path` en `nodestore path` vandaan komen uit de AEM-instantie.

Vervolgens genereert u indexdefinities met behulp van de juiste graniet-opslagbundel.

```
java -cp oak-run.jar:bundle-com.adobe.granite.repository.jar org.apache.jackrabbit.oak.index.IndexDefinitionUpdater --in indexing-definitions_source.json --out merge-index-definitions_target.json --initializer com.adobe.granite.repository.impl.GraniteContent
```

>[!NOTE]
>
>Het maken van de bovenstaande indexdefinitie wordt alleen ondersteund vanaf de versie `oak-run-1.12.0` . Het richten wordt gedaan gebruikend de bundel van de granietbewaarplaats `com.adobe.granite.repository-x.x.xx.jar`.

Met de bovenstaande stappen maakt u een JSON-bestand met de naam `merge-index-definitions_target.json` dat de indexdefinitie bevat.

**2. Creeer een controlepunt in de bewaarplaats**

Maak een controlepunt in de productie-AEM-instantie met een lange levensduur. Dit moet gebeuren voordat de opslagplaats wordt gekloond.

Via JMX-console op `http://serveraddress:serverport/system/console/jmx` gaat u naar `CheckpointMBean` en maakt u een controlepunt met een lange levensduur (bijvoorbeeld 200 dagen). Roep hiervoor `CheckpointMBean#createCheckpoint` aan met `17280000000` als argument voor de levensduur in milliseconden.

Kopieer vervolgens de zojuist gemaakte checkpoint-id en valideer de levensduur met JMX `CheckpointMBean#listCheckpoints` .

>[!NOTE]
>
>Dit controlepunt wordt verwijderd wanneer de index later wordt geïmporteerd.

Voor meer details, raadpleeg [&#x200B; de verwezenlijking van het controlepunt van 0&rbrace; van de documentatie van Oak.](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html#out-of-band-create-checkpoint)

**Voer off-line indexeren voor de geproduceerde indexdefinities uit**

Lucene-herindexering kan offline worden uitgevoerd met behulp van een eik-run. Dit proces leidt tot indexgegevens op schijf onder `indexing-result/indexes`. Het **&#x200B;**&#x200B;schrijft niet aan de bewaarplaats en vereist daarom niet het tegenhouden van de lopende instantie van AEM. Het gemaakte tekstarchief wordt in dit proces gebruikt:

```
java -Doak.indexer.memLimitInMB=500 -jar oak-run.jar index <nodestore path> --reindex --doc-traversal-mode --checkpoint <checkpoint> --fds-path <datastore path> --index-definitions-file merge-index-definitions_target.json --pre-extracted-text-dir text-extraction/store

Sample <checkpoint> looks like r16c85700008-0-8
—fds-path: path to data store.
--pre-extracted-text-dir: Directory of pre-extracted text.
merge-index-definitions_target: JSON file having merged definitions for the target AEM instance. indexes in this file will be re-indexed.
```

Het gebruik van de parameter `--doc-traversal-mode` is handig bij MongoMK-installaties, omdat dit de herindextijd aanzienlijk verbetert door de inhoud van de opslagplaats in een lokaal, plat bestand te spoolen. Er is echter meer schijfruimte nodig van tweemaal de grootte van de opslagplaats.

Als er MongoMK is, kan dit proces worden versneld als deze stap in een instantie dichter bij de instantie MongoDB wordt uitgevoerd. Als de looppas op de zelfde machine, netwerkoverheadkosten kan worden vermeden.

De extra technische details kunnen in de [&#x200B; eiken-looppas documentatie voor het indexeren &#x200B;](https://jackrabbit.apache.org/oak/docs/query/oak-run-indexing.html) worden gevonden.

### Indexen importeren {#importing-indexes}

Met AEM 6.4 en nieuwere versies kan AEM tijdens de opstartreeks indexen van schijf importeren. De map `<repository>/indexing-result/indexes` wordt tijdens het opstarten gecontroleerd op de aanwezigheid van indexgegevens. U kunt de vooraf gemaakte index naar de bovenstaande locatie kopiëren voordat u het AEM-exemplaar start. AEM importeert het in de opslagplaats en verwijdert het overeenkomstige controlepunt uit het systeem. Een herindex wordt dus volledig vermeden.

## Aanvullende tips en probleemoplossing {#troubleshooting}

Hieronder vindt u enkele nuttige tips en aanwijzingen voor het oplossen van problemen.

### Het effect op het systeem van de live productie verminderen {#reduce-the-impact-on-the-live-production-system}

U wordt aangeraden het productiesysteem te klonen en de offline index te maken met de kloon. Hierdoor worden mogelijke gevolgen voor het productiesysteem weggenomen. Het voor het importeren van indexen vereiste controlepunt moet echter aanwezig zijn in het productiesysteem. Daarom is het van essentieel belang dat u een controlepunt maakt voordat u de kloon gebruikt.

### Runbook en proefversie voorbereiden {#prepare-a-runbook-and-trial-run}

Het wordt aanbevolen een runbook op te stellen en enkele tests uit te voeren voordat het herindexeringsproces in productie wordt genomen.

### Doc Traversal Mode with Offline Indexing {#doc-traversal-mode-with-offline-indexing}

Offlineindexering vereist meerdere traversals van de gehele repository. Met installaties MongoMK, wordt de bewaarplaats betreden over het netwerk die de prestaties van het indexeren proces beïnvloeden. Één optie moet het off-line indexeren proces op de replica in werking stellen MongoDB zelf die de netwerkoverheadkosten zal elimineren. Een andere optie is het gebruik van de modus doc traversal.

De de traversal wijze van Doc kan worden toegepast door de parameter van de bevellijn `—doc-traversal` aan het bevel-looppas voor off-line indexeren toe te voegen. In deze modus wordt een kopie van de gehele opslagplaats op de lokale schijf als een plat bestand gespaard en wordt het gebruikt om de indexering uit te voeren.
