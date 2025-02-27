---
title: Onderhoudstaken vóór upgrade
description: Meer informatie over de voor AEM aanbevolen upgradetaken.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 2eb9307f37098ee9f57ba9383600f74a5e3b2501
workflow-type: tm+mt
source-wordcount: '1187'
ht-degree: 0%

---

# Onderhoudstaken vóór upgrade{#pre-upgrade-maintenance-tasks}

Voordat u begint met de upgrade, is het belangrijk dat u de volgende onderhoudstaken uitvoert om ervoor te zorgen dat het systeem klaar is en kan worden teruggedraaid als zich problemen voordoen:

* [Indexdefinities](#index-definitions)
* [Zorgen voor voldoende schijfruimte](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#ensure-sufficient-disk-space)
* [Volledige back-up van AEM maken](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#fully-back-up-aem)
* [Het bestand quickstart.properties genereren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#generate-quickstart-properties)
* [Werkstroom- en controlelogbestanden leegmaken configureren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#configure-wf-audit-purging)
* [De taken vóór de upgrade installeren, configureren en uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#install-configure-run-pre-upgrade-tasks)
* [Updates verwijderen uit de map /install](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#remove-updates-install-directory)
* [Koude stand-byinstanties stoppen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#stop-tarmk-coldstandby-instance)
* [Aangepaste geplande taken uitschakelen](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#disable-custom-scheduled-jobs)
* [Offline revisie opschonen uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-offline-revision-cleanup)
* [Verzameling van afval uit datastore uitvoeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#execute-datastore-garbage-collection)
* [Upgrade het databaseschema indien nodig](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#upgradethedatabaseschemaifneeded)
* [Gebruikers verwijderen die de upgrade mogelijk kunnen blokkeren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#delete-users-that-might-hinder-the-upgrade)

* [Logbestanden roteren](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#rotate-log-files)

## Indexdefinities {#index-definitions}

Zorg ervoor dat u de vereiste indexdefinities hebt geïnstalleerd die met AEM 6.5 de Packs van de Dienst met AEM Service Pack 22 bij een minimum worden vrijgegeven (verwijs naar [ AEM 6.5 de nota&#39;s van de de dienstversie ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/release-notes/release-notes) voor meer informatie).

## Zorgen voor voldoende schijfruimte {#ensure-sufficient-disk-space}

Bij het uitvoeren van de upgrade moet, naast de activiteiten voor het upgraden van de inhoud en code, een migratie naar de opslagplaats worden uitgevoerd. Tijdens de migratie wordt een kopie van de opslagplaats gemaakt in de nieuwe indeling Segment Tar. Hierdoor hebt u voldoende schijfruimte nodig om een tweede, mogelijk grotere versie van uw opslagplaats te behouden.

## Volledige back-up van AEM maken {#fully-back-up-aem}

Er moet een volledige back-up van AEM worden gemaakt voordat de upgrade wordt gestart. Maak indien van toepassing een back-up van de opslagplaats, de installatie van de toepassing, de datastore en de Mongo-exemplaren. Voor meer informatie bij het steunen van en het herstellen van een instantie van AEM, zie [ Steun en herstel ](/help/sites-administering/backup-and-restore.md).

## Het bestand quickstart.properties genereren {#generate-quickstart-properties}

Wanneer u AEM start vanuit het jar-bestand, wordt een `quickstart.properties` -bestand gegenereerd onder `crx-quickstart/conf` . Als AEM in het verleden alleen met het beginscript is gestart, is dit bestand niet aanwezig en mislukt de upgrade. Controleer of dit bestand bestaat en start AEM opnieuw vanuit het jar-bestand als dit niet aanwezig is.

## Werkstroom- en controlelogbestanden leegmaken configureren {#configure-wf-audit-purging}

De `WorkflowPurgeTask` en `com.day.cq.audit.impl.AuditLogMaintenanceTask` taken vereisen afzonderlijke configuraties OSGi en kunnen niet zonder hen werken. Als ze tijdens de uitvoering van een pre-upgrade-taak mislukken, is het ontbreken van configuraties de meest waarschijnlijke reden. Daarom zorg ervoor om configuraties OSGi voor deze taken toe te voegen of hen volledig te verwijderen uit de lijst van pre-verbeteringstaken als u niet wenst om hen in werking te stellen. De documentatie voor het vormen werkschemazuiveringstaken kan bij [ het Beheer de Instanties van het Werkschema ](/help/sites-administering/workflows-administering.md) en de configuratie van de de onderhoudstaak van het controlelogboek kunnen bij [ het Onderhoud van het Logboek van de Controle in AEM 6 ](/help/sites-administering/operations-audit-log.md) worden gevonden.

Voor werkschema en controlelogboek het zuiveren op CQ 5.6 en controlelogboek het zuiveren op AEM 6.0, zie {het werkschema van 0} zuiveren en controleknopen ](https://helpx.adobe.com/experience-manager/kb/howtopurgewf.html).[

## De taken vóór de upgrade installeren, configureren en uitvoeren {#install-configure-run-pre-upgrade-tasks}

De onderhoudstaken die vóór de upgrade moesten worden uitgevoerd, worden geoptimaliseerd en geautomatiseerd. De optimalisering van het pre-verbeteringsonderhoud laat een verenigde manier toe om deze taken teweeg te brengen en hun resultaat op bestelling te kunnen inspecteren.

### Hoe wordt het gebruikt {#how-to-use-it}

De `PreUpgradeTasksMBean` component OSGI wordt vooraf geconfigureerd met een lijst van pre-upgrade onderhoudstaken die allemaal tegelijk kunnen worden uitgevoerd. U kunt de taken vormen door de hieronder procedure te volgen:

1. Ga naar de Console van het Web door aan *https://serveraddress:serverport/system/console/configMgr* te doorbladeren

1. Onderzoek naar &quot;**preupgradetasks**&quot;, dan klik de eerste passende component. De volledige naam van de component is `com.adobe.aem.upgrade.prechecks.mbean.impl.PreUpgradeTasksMBeanImpl`

1. Wijzig de lijst met onderhoudstaken die moet worden uitgevoerd zoals hieronder wordt weergegeven:

   ![ 1487758925984 ](assets/1487758925984.png)

Hieronder volgt een beschrijving van de uitvoeringsmodus waarvoor elke onderhoudstaak is ontworpen.

| Taak | Notities |
|---|---|
| WorkflowPurgeTask | U moet de configuratie-OSGi voor OSGi van de Adobe Granite-workflow configureren voordat u deze uitvoert. |
| GenerateBundlesListFileTask |   |
| RevisionCleanupTask |   |
| com.day.cq.audit.impl.AuditLogMaintenanceTask | Moet de configuratie vormen van OSGi van de Planner van de Woorden van het Logboek van de Controle alvorens in werking te stellen. |

### Standaardconfiguratie van de health checks vóór de upgrade {#default-configuration-of-the-pre-upgrade-health-checks}

De `PreUpgradeTasksMBeanImpl` OSGI-component wordt vooraf geconfigureerd met een lijst met tags die voorafgaand aan de upgrade moeten worden uitgevoerd wanneer de `runAllPreUpgradeHealthChecks` -methode wordt aangeroepen:

* **systeem** - de markering die door de granietcontroles van de onderhoudsgezondheid wordt gebruikt

* **pre-verbetering** - een douanetag die aan alle gezondheidscontroles kon worden toegevoegd die u kunt plaatsen om vóór een verbetering te lopen

**MBean Methods**

De beheerde boonfunctionaliteit kan worden betreden gebruikend de [ Console JMX ](/help/sites-administering/jmx-console.md).

U kunt tot MBeans toegang hebben door:

1. Ga naar de Console JMX in *https://serveraddress:serverport/system/console/jmx*
1. Onderzoek naar **PreUpgradeTasks** en klik het resultaat

1. Selecteer om het even welke methode van de **sectie van Verrichtingen** en selecteer **aanhalen** in het volgende venster.

Hieronder vindt u een lijst met alle beschikbare methoden die door de `PreUpgradeTasksMBeanImpl` worden beschreven:

| Naam methode | Type | Beschrijving |
|---|---|---|
| runAllPreUpgradeTasks() | ACTIE | Voert alle preupgradeonderhoudstaken in de lijst uit. |
| runPreUpgradeTask(preUpgradeTaskName) | ACTIE | Hiermee wordt de onderhoudstaak vóór de upgrade uitgevoerd met de naam die als parameter is opgegeven. |
| getPreUpgradeTaskLastRunTime(preUpgradeTaskName) | ACTIE | Toont de nauwkeurige lopende tijd van de pre-verbeterings onderhoudstaak met de naam die als parameter wordt gegeven. |
| getPreUpgradeTaskLastRunState(preUpgradeTaskName) | ACTIE | Toont de laatste lopende staat van de pre-verbeterings onderhoudstaak met de naam die als parameter wordt gegeven. |
| runAllPreUpgradeHealthChecks(closedDownOnSuccess) | ACTIE | Voert alle controles van de pre-verbeteringsgezondheid uit en bewaart hun status in een dossier genoemd preUpgradeHCStatus.properties in de sling huisweg. Als closedDownOnSuccess aan waar wordt geplaatst, wordt de instantie van AEM gesloten, maar slechts als alle pre-verbeteringsgezondheidscontroles een O.K. status hebben. Het eigenschappenbestand wordt gebruikt als voorwaarde voor een toekomstige upgrade en het upgradeproces wordt gestopt als de uitvoering van de health check vóór de upgrade is mislukt. Als u het resultaat van de gezondheidscontroles vóór de upgrade wilt negeren en de upgrade toch wilt starten, kunt u het bestand verwijderen. |
| detectionUsageOfUnavailableAPI(aemVersion) | ACTIE | Hiermee worden alle geïmporteerde pakketten weergegeven waaraan niet meer wordt voldaan wanneer een upgrade naar de opgegeven AEM-versie wordt uitgevoerd. De AEM-doelversie moet als parameter worden opgegeven. |

>[!NOTE]
>
>De methodes MBean kunnen worden aangehaald via:
>
>* De JMX-console
>* Een externe toepassing die verbinding maakt met JMX
>* cURL
>

## Updates verwijderen uit de map /install {#remove-updates-install-directory}

>[!NOTE]
>
>Verwijder alleen pakketten uit de map crx-quickstart/install NA het afsluiten van de AEM-instantie. Deze stap is één van het laatste alvorens de op zijn plaats verbeteringsprocedure te beginnen.

Verwijder alle servicepacks, functiepakketten of hotfixes die via de map `crx-quickstart/install` in het lokale bestandssysteem zijn geïmplementeerd. Hierdoor wordt voorkomen dat oude hotfixes en servicepacks onbedoeld boven op de nieuwe AEM-versie worden geïnstalleerd nadat de update is voltooid.

## Koude stand-byinstanties stoppen {#stop-tarmk-coldstandby-instance}

Als u TarMK koude stand-by gebruikt, moet u eventuele koude stand-byinstanties stoppen. Dit garandeert een efficiënte manier om online terug te keren als er problemen zijn in de upgrade. Nadat de verbetering met succes heeft voltooid, moeten de koude standby instanties van de promotieprimaire instanties worden herbouwd.

## Aangepaste geplande taken uitschakelen {#disable-custom-scheduled-jobs}

Schakel geplande OSGi-taken uit die in uw toepassingscode zijn opgenomen.

## Offline revisie opschonen uitvoeren {#execute-offline-revision-cleanup}

>[!NOTE]
>
>Deze stap is alleen nodig voor TarMK-installaties

Als u TarMK gebruikt, moet u de functie Offline revisie opschonen uitvoeren voordat u de upgrade uitvoert. Hierdoor worden de migratie naar de opslagplaats en de daarop volgende upgradetaken veel sneller uitgevoerd en wordt ervoor gezorgd dat Online revisie-opschoning met succes kan worden uitgevoerd nadat de upgrade is voltooid. Voor informatie bij het in werking stellen van de Opruiming van de Off-line Revisie, zie [ het Uitvoeren van de Opruiming van de Offline Revisie ](/help/sites-deploying/storage-elements-in-aem-6.md#performing-offline-revision-cleanup).

## Verzameling van afval uit datastore uitvoeren {#execute-datastore-garbage-collection}

Nadat u de revisie hebt opgeschoond op CRX3-instanties, moet u de afvalverzameling van de datastore uitvoeren om eventuele niet-gerefereerde balken in de gegevensopslag te verwijderen. Voor instructies, zie de documentatie op [ de Inzameling van het huisvuil van de Opslag van Gegevens ](/help/sites-administering/data-store-garbage-collection.md).

## Logbestanden roteren {#rotate-log-files}

Adobe raadt u aan uw huidige logbestanden te archiveren voordat u begint met de upgrade. Zo kunt u logbestanden tijdens en na de upgrade gemakkelijker controleren en scannen om eventuele problemen op te sporen en op te lossen.
