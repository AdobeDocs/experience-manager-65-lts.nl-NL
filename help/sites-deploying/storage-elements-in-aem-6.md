---
title: Opslagelementen in AEM 6.5 LTS
description: Leer over de implementaties van de knoopopslag beschikbaar in AEM 6.5 LTS en hoe te om de bewaarplaats te handhaven.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
legacypath: /content/docs/en/aem/6-0/deploy/upgrade/microkernels-in-aem-6-0
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: e51842b5-fa91-42d2-a490-5a7e867dada7
source-git-commit: 0e60c406a9cf1e5fd13ddc09fd85d2a2f8a410f6
workflow-type: tm+mt
source-wordcount: '712'
ht-degree: 0%

---

# Opslagelementen in AEM 6.5 LTS{#storage-elements-in-aem}

Dit artikel heeft betrekking op:

* [Overzicht van opslag in AEM 6.5 LTS](/help/sites-deploying/storage-elements-in-aem-6.md#overview-of-storage-in-aem)
* [Behoud van de opslagplaats](/help/sites-deploying/storage-elements-in-aem-6.md#maintaining-the-repository)

## Overzicht van opslag in AEM 6.5 LTS {#overview-of-storage-in-aem}

Een van de belangrijkste wijzigingen in AEM 6.5 LTS zijn de innovaties op het niveau van de opslagplaats.

Er zijn momenteel twee knoopopslagimplementaties beschikbaar in AEM 6.5 LTS: Tar-opslag en MongoDB-opslag.

### Teeropslag {#tar-storage}

#### Een nieuw geïnstalleerd AEM-exemplaar uitvoeren met Tar Storage {#running-a-freshly-installed-aem-instance-with-tar-storage}

AEM 6.5 LTS gebruikt standaard de Tar-opslag voor het opslaan van knooppunten en binaire bestanden, waarbij de standaardconfiguratieopties worden gebruikt. U kunt de opslaginstellingen handmatig configureren door het volgende te doen:

1. Download de AEM 6.5 LTS QuickStart jar en plaats deze in een nieuwe map.
1. AEM uitpakken door uit te voeren:

   `java -jar <aem-65-lts>.jar -unpack`

1. Maak een map met de naam `crx-quickstart\install` in de installatiemap.

1. Maak een bestand met de naam `org.apache.jackrabbit.oak.segment.SegmentNodeStoreService.config` in de nieuwe map.

1. Bewerk het bestand en stel de configuratieopties in. De volgende opties zijn beschikbaar voor de Opslag van de Knoop van het Segment, die de basis van de de opslagimplementatie van de Tar van AEM vormt:

   * `repository.home`: pad naar de thuislocatie van de gegevensopslagruimte waarin verschillende gegevensbestanden met betrekking tot de gegevensopslagruimte zijn opgeslagen. Standaard worden segmentbestanden opgeslagen onder de map crx-quickstart/segmentstore.
   * `tarmk.size`: Maximale grootte van een segment in MB. De standaardwaarde is 256 MB.

1. Start AEM.

### Mongo-opslag {#mongo-storage}

>[!NOTE]
>
>De minimaal ondersteunde versie van Mongo is Mongo 6.

#### Een nieuw geïnstalleerd AEM-exemplaar uitvoeren met Mongo Storage {#running-a-freshly-installed-aem-instance-with-mongo-storage}

AEM 6.5 LTS kan worden geconfigureerd voor gebruik met MongoDB-opslag door de onderstaande procedure te volgen:

1. Download de AEM 6.5 LTS QuickStart jar en plaats deze in een nieuwe map.
1. Pak AEM uit met de volgende opdracht:

   `java -jar <aem-65-lts>.jar -unpack`

1. Controleer of MongoDB is geïnstalleerd en of een instantie van `mongod` wordt uitgevoerd. Voor meer info, zie [&#x200B; Installerend MongoDB &#x200B;](https://docs.mongodb.org/manual/installation/).
1. Maak een map met de naam `crx-quickstart\install` in de installatiemap.
1. Vorm de knoopopslag door een configuratiedossier met de naam van de configuratie te creëren die u in de `crx-quickstart\install` folder wilt gebruiken.

   De Document Node Store (die de basis voor de AEM MongoDB-opslagimplementatie vormt) gebruikt een bestand met de naam `org.apache.jackrabbit.oak.plugins.document.DocumentNodeStoreService.config`

1. Bewerk het bestand en stel de configuratieopties in. De volgende opties zijn beschikbaar:

   * `mongouri`: [&#x200B; MongoURI &#x200B;](https://docs.mongodb.org/manual/reference/connection-string/) wordt vereist om met het Gegevensbestand van Mongo te verbinden dat. De standaardwaarde is `mongodb://localhost:27017`
   * `db`: naam van de Mongo-database. Door gebrek gebruikt nieuwe AEM 6.5 LTS installaties **aem-auteur** als gegevensbestandnaam.
   * `cache`: De cachegrootte in megabytes. Deze cachegrootte wordt verdeeld over verschillende caches die in DocumentNodeStore worden gebruikt. De standaardwaarde is 256.
   * `changesSize`: Grootte in MB van de afgetopte inzameling die in Mongo voor caching van de diff output wordt gebruikt. De standaardwaarde is 256.
   * `customBlobStore`: Booleaanse waarde die aangeeft dat een aangepaste gegevensopslag wordt gebruikt. De standaardwaarde is false.

1. Maak een configuratiebestand met de PID van de gegevensopslagruimte die u wilt gebruiken en bewerk het bestand om de configuratieopties in te stellen. Voor meer info, zie [&#x200B; het Vormen de Opslag van de Knoop en de Opslag van Gegevens &#x200B;](/help/sites-deploying/data-store-config.md).

1. Start de AEM 6.5 LTS-kaart met een MongoDB-opslagback-end door deze uit te voeren:

   ```shell
   java -jar <aem-65-lts>.jar -r crx3,crx3mongo
   ```

   In de modus voor uitvoering op de achtergrond **`-r`** begint het voorbeeld met ondersteuning voor MongoDB.

#### Transparante grote pagina&#39;s uitschakelen {#disabling-transparent-huge-pages}

Red Hat® Linux® gebruikt een algoritme voor geheugenbeheer met de naam Transparent Huge Pages (THP). Terwijl AEM fijnkorrelige lees- en schrijfbewerkingen uitvoert, is THP geoptimaliseerd voor grote bewerkingen. Daarom wordt aangeraden THP zowel op Tar- als op Mongo-opslag uit te schakelen. Voer de volgende stappen uit om het algoritme uit te schakelen:

1. Open het bestand `/etc/grub.conf` in de teksteditor van uw keuze.
1. Voeg de volgende lijn aan het {**dossier 0} grub.conf toe:**

   ```
   transparent_hugepage=never
   ```

1. Tot slot controleert u of de instelling van kracht is geworden door:

   ```
   cat /sys/kernel/mm/redhat_transparent_hugepage/enabled
   ```

   Als THP is uitgeschakeld, moet de uitvoer van de bovenstaande opdracht als volgt zijn:

   ```
   always madvise [never]
   ```

>[!NOTE]
>
>Raadpleeg de volgende bronnen:
>
>* Voor meer informatie betreffende de Transparante Pagina&#39;s van de Groot van de Lezing op Red Hat® Linux®, raadpleeg het volgende artikel van het Portaal van de Klant Red Hat®: [&#x200B; gebruiken, controleren, en onbruikbaar maken transparante gezoempagina&#39;s in de Onderneming Linux 6, 7 en 8 van Red Hat?](https://access.redhat.com/solutions/46111)
>* Voor Linux® het stemmen uiteinden, zie [&#x200B; Optimalisering van Prestaties &#x200B;](/help/sites-deploying/configuring-performance.md).
>

## Behoud van de opslagplaats {#maintaining-the-repository}

Bij elke update van de opslagplaats wordt een inhoudsrevisie gemaakt. Als gevolg hiervan neemt de grootte van de gegevensopslagruimte bij elke update toe. Om ongecontroleerde groei van de opslagplaats te voorkomen, moeten oude revisies worden opgeschoond tot vrije schijfmiddelen. Deze onderhoudsfunctionaliteit wordt Revision Cleanup genoemd. Het correctiemechanisme van de Herziening wint schijfruimte terug door verouderde gegevens uit de bewaarplaats te verwijderen. Voor verdere details over de Opruiming van de Revisie, lees de [&#x200B; pagina van de Opruiming van de Revisie &#x200B;](/help/sites-deploying/revision-cleanup.md).
