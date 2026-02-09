---
title: Upgradestappen voor installatie van toepassingsservers (Tomcat)
description: Leer hoe u AEM-exemplaren die via Tomcat zijn geïmplementeerd, kunt upgraden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: b3c4e946a3f235fa0e3a0945f1ad692ee195e3ef
workflow-type: tm+mt
source-wordcount: '408'
ht-degree: 0%

---

# De Stappen van de verbetering voor de Installaties van de Server van de Toepassing (Tomcat - op plaats verbetering) {#upgrade-steps-for-application-server-installations-tomcat-inplace}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure (de verbetering van de Plaats) van AEM 6.5 LTS aan AEM 6.5 LTS Servicepack op Tomcat. Voor bevordering van AEM 6.5 aan 6.5 LTS, [ verwijs hier ](/help/sites-deploying/app-server-upgrade-tomcat.md).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Bovendien, zorg ervoor dat uw systeem aan de [ vereisten voor AEM 6.5 LTS Servicepack ](/help/sites-deploying/technical-requirements.md) voldoet en [ verbetering planningsoverwegingen ](/help/sites-deploying/upgrade-planning.md) ziet.


### Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java**: Zorg ervoor u Oracle® JRE 17/21 op uw server van Tomcat hebt geïnstalleerd.
* **Tomcat server**: De gesteunde versies van de server van Tomcat voor AEM 6.5 LTS en zijn ServicePacks zijn **10.0.x** en **10.1.x**.

### De upgrade uitvoeren {#performing-the-upgrade}

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM 6.5 LTS reeds opgesteld hebt. De procedure wordt bedoeld om verbeteringen te documenteren die van versie van AEM **6.5** LTS aan **worden uitgevoerd 6.5 LTS** Servicepack.

1. Als AEM 6.5 LTS al is geïmplementeerd, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/system/console/bundles`*
1. Stop vervolgens AEM 6.5 LTS. Dit kan worden gedaan vanuit Tomcat App Manager op: *`https://<serveraddress:port>/manager/html`*
1. Zorg ervoor dat u [ pre-verbeterings ](#pre-upgrade-steps) activiteiten zoals steun van de server van AEM 6.5 LTS alvorens om het even welke verbeteringsactiviteit hebt voltooid
1. Stop de AEM 6.5 LTS Tomcat-server. In de meeste gevallen kunt u dit doen door het script `./catalina.sh` uit te voeren, door deze opdracht uit te voeren vanaf de terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Verwijder de bestanden en mappen die u niet meer nodig hebt. De items die u specifiek moet verwijderen zijn:

   * Het **cq-quickstart-65.war** dossier en de `cq-quickstart-65` omslag van `webapps` omslag typisch die bij `<path-to-aem-server>/webapps` wordt gevestigd
   * De map `launchpad/startup` . U kunt het schrappen door het volgende bevel in de terminal in werking te stellen veronderstelt u in de serveromslag bent:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/startup
     ```

   * Het `base.jar` -bestand. U kunt dit doen door de volgende bevelen in werking te stellen:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Het `BootstrapCommandFile_timestamp.txt` -bestand:

     ```shell
     rm -f <path-to-aem-server>/bin/crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Verwijder het `sling.options` -bestand door het uit te voeren:

     ```shell
     find <path-to-aem-server>/bin/crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Verwijder het `sling.bootstrap.txt` -bestand:

     ```shell
     rm -rf <path-to-aem-server>/bin/crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Maak een back-up van het `sling.properties` -bestand (gewoonlijk aanwezig in `<path-to-aem-server>/bin/crx-quickstart/launchpad/` ) en verwijder deze
1. Kopieer het AEM 6.5 LTS Servicepack-oorlogsbestand naar de map `<path-to-aem-server>/webapps` .
1. Start de AEM 6.5 LTS Tomcat-server door deze uit te voeren:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. De foutenlogboeken controleren terwijl AEM begint om te controleren dat er geen fouten zijn en AEM loopt regelmatig
1. Nadat AEM 6.5 LTS is gestart, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [ Controle van de Verbetering van het Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) voor meer informatie.
