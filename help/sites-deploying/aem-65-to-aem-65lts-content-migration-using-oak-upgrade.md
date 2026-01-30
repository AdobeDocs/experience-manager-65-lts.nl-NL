---
title: AEM 6.5 tot AEM 6.5 LTS-migratie van inhoud met Oak-upgrade
description: Leer hoe u inhoud van AEM 6.5 naar AEM 6.5 LTS migreert met de Oak-upgrade
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 8c4ffb0e-b4dc-4a81-ac43-723754cbc0de
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# AEM 6.5 tot AEM 6.5 LTS-migratie van inhoud met Oak-upgrade {#aem-65-to-aem-65lts-content-migration-using-oak-upgrade}

Dit document verklaart hoe te om Adobe Experience Manager van **te bevorderen 6.5** aan **6.5 LTS**, met een nadruk op het migreren van de inhoudsbewaarplaats. Het gaat om het gebruik van het Oak-upgradehulpprogramma om inhoud met nauwkeurigheid en controle over te brengen tussen opslagruimten.

## Vereisten {#prerequisites}

Voordat u de migratie start, moet u controleren of aan de volgende vereisten is voldaan:

1. Java-compatibiliteit: AEM 6.5 LTS moet zijn geïnstalleerd en geconfigureerd voor uitvoering met Java™ 17. Start de AEM-instantie nadat u deze hebt ingesteld en controleer of alle bundels actief en actief zijn zonder problemen
1. Systeembronnen: zorg ervoor dat er voldoende schijfruimte en geheugen beschikbaar zijn om beide opslagruimten tijdens het migratieproces te verwerken
1. Oak-upgrade Tool: Download de `oak-upgrade` pot van de [ officiële Gemaakt bewaarplaats ](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade). Zorg ervoor dat de versie overeenkomt met de Oak-kernversie die wordt gebruikt in AEM 6.5 LTS. Oak-upgradeprogramma wordt uitgevoerd op Oracle® Java™ 11 of hoger

## Migratieproces {#step-by-step-migration-process}

### AEM 6.5 en AEM 6.5 LTS stoppen {#stopping-aem65-and-aem65lts}

Stop voordat u de migratie start uw AEM 6.5- en AEM 6.5 LTS-instanties. Dit zorgt ervoor dat de opslagplaats zich in een stabiele toestand bevindt en er tijdens de migratie geen extra schrijvingen plaatsvinden.

### Back-up maken van de AEM 6.5-instantie {#backing-up-the-aem65-instance}

Maak een volledige back-up van uw AEM 6.5-exemplaar als dit nog niet is gebeurd.

### Oak-upgradeprogramma gebruiken voor migratie van inhoud {#using-the-oak-upgrade-tool-for-content-migration}

Het gereedschap Oak-upgrade wordt uitgevoerd via de opdrachtregel, zoals hier wordt getoond:

```
java -jar oak-upgrade-*.jar [options] /path/to/source/repository /path/to/destination/repository 
```

Hieronder vindt u de belangrijkste opdrachten en opties:

**Zeer belangrijke opties**

* `--include-paths`: geef de substructuren op die u wilt opnemen in de migratie. Zie dit voorbeeld voor het opdrachtgebruik:

  ```
  java -jar oak-upgrade-*.jar --include-paths=/content/site /old/repository /new/repository
  ```

* `--exclude-paths`: sluit specifieke paden uit van migratie. Wees voorzichtig met het gebruik van deze optie - als het pad op het doelsysteem aanwezig is, wordt het verwijderd. Zie dit voorbeeld voor het opdrachtgebruik:

  ```
  java -jar oak-upgrade-*.jar --exclude-paths=/content/old_site /old/repository /new/repository 
  ```

* `--copy-binaries`: Oak-upgrade migreert standaard alleen verwijzingen naar binaire getallen, zodat de bestanden in het oorspronkelijke blob-/gegevensarchief blijven staan. Dientengevolge, vertrouwt de nieuwe bewaarplaats nog op de bronopslag voor binaire getallen. Als u binaire bestanden samen met de inhoud van de opslagplaats wilt migreren, gebruikt u de parameter `--copy-binaries` om alle binaire gegevens naar de nieuwe opslagplaats te kopiëren, zoals hieronder wordt getoond:

  ```
  java -jar oak-upgrade-*.jar \
  --copy-binaries \
  --src-datastore=/old/repository/datastore \
  --datastore=/new/repository/datastore \
  /old/repository \
  /new/repository 
  ```

### Controlepunten migreren {#migratiing-checkpoints}

Bij het migreren van een oude SegmentMK-opslagplaats (vóór Oak 1.6) naar een nieuwe SegmentMK (Oak-versie groter of gelijk aan 1.6), worden de controlepunten ook gemigreerd. Dit proces vermijdt opnieuw indexeren wanneer de Oak voor de eerste keer in de nieuwe opslagplaats wordt uitgevoerd. In de volgende gevallen worden de controlepunten echter niet gemigreerd:

1. Aangepaste include-, exclude- of merge- paden zijn opgegeven of
1. Het systeem kopieert de binaire getallen naar referentie. Er is geen brondatastore opgegeven en twee verschillende controlepunten bevatten een ander binair element onder hetzelfde pad.

In het tweede geval geeft de Oak-upgrade de volgende waarschuwing en onderbrekingen weer:

```
Checkpoints are not copied, because no external datastore has been specified. This results in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info. 
```

De eenvoudigste manier om dit probleem op te lossen is het opgeven van de brondatastore in de opdrachtregelopties (bijvoorbeeld `--src-datastore` of `--src-s3datastore` ).

De waarschuwing kan ook worden genegeerd, maar in dit geval wordt de repository volledig opnieuw gedesgroepeerd bij het eerste opstarten. Het kan een lang proces zijn, vooral voor de grote instantie. De repository is pas bruikbaar als het herindexeringsproces is voltooid. Gebruik de optie `--skip-checkpoints` om de waarschuwing te onderdrukken.

U kunt de bewaarplaats ook off-line opnieuw indexeren alvorens AEM te beginnen die [ off-line opnieuw indexeren ](/help/sites-deploying/offline-reindexing.md) gebruiken om volledige herindexering op het eerste opstarten te vermijden.

Voor meer informatie over het Oak-upgrade hulpmiddel en het geavanceerde gebruik, verwijs naar de [ officiële documentatie ](https://jackrabbit.apache.org/oak/docs/migration.html).
