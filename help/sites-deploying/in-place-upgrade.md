---
title: Een op locatie uitgevoerde upgrade uitvoeren
description: Leer hoe u een upgrade ter plekke kunt uitvoeren voor AEM 6.5 LTS.
topic-tags: upgrading
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: c7351625-b29e-45a7-b966-e7c0f56d4f22
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Een op locatie uitgevoerde upgrade uitvoeren {#performing-an-in-place-upgrade}

>[!NOTE]
>
>Deze pagina schetst de op zijn plaats verbeteringsprocedure voor AEM 6.5 LTS. Als u een installatie hebt die aan een toepassingsserver wordt opgesteld, zie [ de Stappen van de Verbetering voor de Installaties van de Server van de Toepassing ](/help/sites-deploying/app-server-upgrade.md).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Bovendien, zorg ervoor dat uw systeem aan de [ vereisten voor AEM 6.5 LTS ](/help/sites-deploying/technical-requirements.md) voldoet en [ verbetering planningsoverwegingen ](/help/sites-deploying/upgrade-planning.md) ziet en hoe [ Analysator ](/help/sites-deploying/pattern-detector.md) u kan helpen de ingewikkeldheid schatten.

<!--Finally, the downtime during the upgrade can be significally reduced by indexing the repository **before** performing the upgrade. For more information, see [Using Offline Reindexing To Reduce Downtime During an Upgrade](/help/sites-deploying/upgrade-offline-reindexing.md)-->

## Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java:** zorg ervoor u Oracle Java™ 17 hebt geïnstalleerd op uw systeem.

## Voorbereiding van het JAR-bestand van AEM Quickstart {#prep-quickstart-file}

1. Download het nieuwe AEM 6.5 LTS jar-bestand

1. [Bepaal het correcte verbeteringsbegin bevel](/help/sites-deploying/in-place-upgrade.md#determining-the-correct-upgrade-start-command-determining-the-correct-upgrade-start-command)

1. De instantie stoppen als deze wordt uitgevoerd

1. Nieuwe AEM 6.5 LTS-jar gebruiken om de oude buiten de `crx-quickstart` -map te vervangen

1. Maak een back-up van het `sling.properties` -bestand (meestal aanwezig in de `crx-quickstart/conf/` ) en verwijder het vervolgens

1. Pak de nieuwe QuickStart-jar uit door deze uit te voeren:

   ```shell
   java -Xmx4096m -jar aem-quickstart.jar -unpack
   ```

1. Met de opdracht Uitpakken wordt een nieuw `sling.properties` -bestand onder de map `crx-quickstart/conf/` gegenereerd. U kunt nu uw aangepaste wijzigingen toepassen op het nieuwe `sling.properties` -bestand.

<!-- Alexandru: drafting temporarily

## Content Repository Migration {#content-repository-migration}

This migration is not required if you are upgrading from AEM 6.3. For versions older than 6.3, Adobe provides a tool that can be used to migrate the repository to the new version of the Oak Segment Tar present in AEM 6.3. It is provided as part of the quickstart package and is mandatory for any upgrades that will be using TarMK. Upgrades for environments that are using MongoMK do not require repository migration. For more information on what the benefits of the new Segment Tar format are, see the [Migrating to Oak Segment Tar FAQ](/help/sites-deploying/revision-cleanup.md#online-revision-cleanup-frequently-asked-questions).

The actual migration is performed using the standard AEM quickstart jar file, executed with a new `-x crx2oak` option which executes the crx2oak tool to simplify the upgrade and make it more robust.

>[!NOTE]
>
>If you are performing TarMK repository content migration using the CRX2Oak Quickstart extension, you might remove the **samplecontent** runmode by adding the following to the migration command line:
>
>* `--promote-runmode nosamplecontent`
>

To determine the command that you should run, use the following command:

```shell
java -Xmx4096m -jar aem-quickstart.jar -v -x crx2oak -xargs -- --load-profile <<YOUR_PROFILE>> <<ADDITIONAL_FLAGS>>
```

Where `<<YOUR_PROFILE>>` and `<<ADDITIONAL_FLAGS>>` are replaced with the profile and flags listed in the following table:

<table>
 <tbody>
  <tr>
   <td><strong>Source Repository</strong></td>
   <td><strong>Target Repository</strong></td>
   <td><strong>Profile</strong></td>
   <td><strong>Additional Flags</strong><br /> </td>
  </tr>
  <tr>
   <td>crx2 or TarMK with <code>FileDataStore</code></td>
   <td>TarMK</td>
   <td>segment-fds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>crx2</td>
   <td>MongoMK</td>
   <td>mongo-from-crx2 </td>
   <td><code>-T mongo-uri=mongo://mongo-host:mongo-port -T mongo-db=mongo-database-name</code></td>
  </tr>
  <tr>
   <td>TarMK or crx2 with <code>S3DataStore</code></td>
   <td>TarMK</td>
   <td>segment-custom-ds</td>
   <td>See Troubleshooting section below</td>
  </tr>
  <tr>
   <td>TarMK with no datastore</td>
   <td>TarMK</td>
   <td>segment-no-ds</td>
   <td> </td>
  </tr>
  <tr>
   <td>MongoMK</td>
   <td>MongoMK</td>
   <td>No migration is needed</td>
   <td> </td>
  </tr>
 </tbody>
</table>

**Where:**

* `mongo-host` is the MongoDB server IP (for example, 127.0.0.1)

* `mongo-port` is the MongoDB server port (for example: 27017)

* `mongo-database-name` represents the name of the database (for example: aem-author)

**You may also require additional switches for the following scenarios:**

* If you are performing the upgrade on a Windows system where Java memory mapping is not handled correctly, add the `--disable-mmap` parameter to the command.

For additional instructions on using the crx2oak tool, see Using the [CRX2Oak Migration Tool](/help/sites-deploying/using-crx2oak.md). The crx2oak helper JAR can be manually upgraded if needed, by manually replacing it with newer versions after unpacking the quickstart. Its location in the AEM installation folder is: `<aem-install>/crx-quickstart/opt/extensions/crx2oak.jar`. The newest version of the CRX2Oak migration tool is available for download from the Adobe Repository at: [https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/](https://repo1.maven.org/maven2/com/adobe/granite/crx2oak/)

If the migration has completed successfully, the tool will exit with an exit code of zero. Additionally, check for WARN and ERROR messages in the `upgrade.log` file, located under `crx-quickstart/logs` in the AEM installation directory, as these could indicate non-fatal errors that occurred during the migration.

Check the configuration files beneath `crx-quickstart/install` folder. If a migration was necessary these will be updated to reflect the target repository.

**A note on datastores:**

While `FileDataStore` is the new default for AEM 6.3 installations, using an external datastore is not required. While using an external datastore is recommended as a best practice for production deployments, it is not a prerequisite to upgrade. Due to the complexity already present in upgrading AEM, Adobe recommends performing the upgrade without doing a datastore migration. If desired, a datastore migration can be executed afterwards as a separate effort.

## Troubleshooting Migration Issues {#troubleshooting-migration-issues}

Skip this section if you are upgrading from 6.3. While the provided crx2oak profiles should meet the needs of most customers, there are times when additional parameters will be necessary. If you run into an error during your migration, it is possible that there are aspects of your environment that require additional configuration options to be provided. If so, you will likely encounter the following error:

**Checkpoints are not copied, because no external datastore has been specified. This will result in the full repository reindexing on the first start. Use --skip-checkpoints to force the migration or see https://jackrabbit.apache.org/oak/docs/migration.html#Checkpoints_migration for more info.**

For some reason, the migration process needs access to binaries in the datastore and is unable to find it. To specify your datastore configuration, include the following flags in the `<<ADDITIONAL_FLAGS>>` portion of your migration command:

**For S3 datastores:**

```shell
--src-s3config=/path/to/SharedS3DataStore.config --src-s3datastore=/path/to/datastore
```

Where `/path/to/SharedS3DataStore.config` represents the path to your S3 datastore config file and `/path/to/datastore` represents the path to your S3 datastore.

**For File datastores:**

```shell
--src-datastore=/path/to/datastore
```

Where `/path/to/datastore` represents the path to your File Datastore.

-->

## De upgrade uitvoeren {#performing-the-upgrade}

**als het gebruiken van S3:**

1. Verwijder eventuele potten onder `crx-quickstart/install` die zijn gekoppeld aan een eerdere versie van de S3-connector.

1. Download de recentste versie van 1.60.2 S3 schakelaar van [ https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/ ](https://repo1.maven.org/maven2/com/adobe/granite/com.adobe.granite.oak.s3connector/) <!-- Alexandru: this is a stub link for now -->

1. Pak de S3-connector (versie 1.60.2) uit en kopieer de inhoud van de volgende mappen onder `crx-quickstart/install` als volgt:

   1. Kopiëren `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/1` onder `crx-quickstart/install/1`
   1. Kopiëren `com.adobe.granite.oak.s3connector-1.60.2/jcr_root/libs/system/install/15` onder `crx-quickstart/install/15`

Nu, begin de instantie van AEM gebruikend het nieuwe die bevel wordt bepaald gebruikend de informatie onder [ het correcte bevel van het verbeteringsbegin ](#determining-the-correct-upgrade-start-command) sectie bepaalt.

### Bepaal het correcte bevel van het verbeteringsbegin {#determining-the-correct-upgrade-start-command}

>[!NOTE]
>
>De steun voor sommige argumenten van Java 8/11 is verwijderd in Java 17, zie [ Oracle Java™ 17 documenten ](https://docs.oracle.com/en/java/javase/17/docs/specs/man/java.html) en [ Java&amp;trade argumenten overwegingen voor AEM 6.5 LTS ](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations).

Als u de upgrade wilt uitvoeren, is het belangrijk dat u AEM start met het jar-bestand om het exemplaar te tonen.

De upgrade wordt niet gestart wanneer u AEM start vanaf het startscript. De meeste klanten beginnen AEM gebruikend het beginmanuscript en hebben dit beginmanuscript aangepast om schakelaars voor omgevingsconfiguraties zoals geheugenmontages, veiligheidscertificaten, etc. te omvatten. Daarom raadt Adobe u aan deze procedure te volgen om de juiste upgradeopdracht te bepalen:

1. Bij een lopende AEM-instantie voert u het volgende uit via de opdrachtregel:

   ```shell
   ps -ef | grep java
   ```

1. Kijk naar het AEM-proces. Het zal er ongeveer als volgt uitzien:

   ```shell
   /usr/bin/java -server -Xmx1024m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar crx-quickstart/app/cq-quickstart-6.5.0-standalone-quickstart.jar start -c crx-quickstart -i launchpad -p 4502 -Dsling.properties=conf/sling.properties
   ```

1. Wijzig de opdracht door het pad naar de bestaande jar ( `crx-quickstart/app/aem-quickstart*.jar` in dit geval) te vervangen door de nieuwe AEM 6.5 LTS-jar die op hetzelfde niveau staat als de `crx-quickstart` -map. Gebruikend ons vorige bevel als voorbeeld, zou ons bevel zijn:

   ```shell
   /usr/bin/java -server -Xmx4096m -Djava.awt.headless=true -Dsling.run.modes=author,crx3,crx3tar -jar <AEM-6.5-LTS.jar> -c crx-quickstart -p 4502 -Dsling.properties=conf/sling.properties
   ```

   Hierdoor worden alle juiste geheugeninstellingen, aangepaste runmodi en andere omgevingsparameters voor de upgrade toegepast. Nadat de upgrade is voltooid, kan de instantie met het beginscript worden gestart in de toekomst.

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [ de Code en de pagina van Aanpassingen van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Controles achteraf en probleemoplossing uitvoeren {#perform-post-upgrade-check-troubleshooting}

Zie [ Controle van de Verbetering van de Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
