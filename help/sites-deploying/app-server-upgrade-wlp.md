---
title: De Stappen van de verbetering voor de Installaties van de Server van de Toepassing (WLP)
description: Leer hoe u AEM-exemplaren upgradet die via Webspehere Liberty zijn geïmplementeerd.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 6a62741ee0ce22a6fb80cf8c68c6eeafacd2e873
workflow-type: tm+mt
source-wordcount: '479'
ht-degree: 0%

---

# De Stappen van de verbetering voor de Installaties van de Server van de Toepassing (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor de AEM 6.5 LTS oorlog op WLP (WebSphere Liberty).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Zorg er bovendien voor dat uw systeem voldoet aan de vereisten voor AEM 6.5 LTS. Zie hoe de Analysator u kan helpen de ingewikkeldheid van uw verbetering schatten en ook een plan voor de verbetering zien (zie [ plannend Uw Verbetering ](/help/sites-deploying/upgrade-planning.md) voor meer informatie).

### Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java**: Zorg ervoor u IBM Sumeru JRE 17 op uw server WLP hebt geïnstalleerd.

### De upgrade uitvoeren {#performing-the-upgrade}

1. Maak een back-up van de instantie voordat u een upgrade uitvoert.
1. Identificeer als u op zijn plaats verbetering of sidegrade afhankelijk van de versie van de server van WLP nodig hebt die u gebruikt. Als uw huidige server WLP Servlet 6 steunt, dan kunt u op zijn plaats verbetering uitvoeren en met deze documentatie verdergaan. Anders, moet u sidegrade uitvoeren. Voor sidegrade, gelieve te volgen de Migratie van de Inhoud met Oak-Upgrade documentatie - [ toe te voegen verbinding TBD ]
1. Stop de AEM-instantie. Dit kan normaal gesproken worden gedaan met deze opdracht:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Verwijder de bestanden en mappen die u niet meer nodig hebt. De items die u specifiek moet verwijderen zijn:

   * De map `cq-quickstart-65.war` in de map `dropins` en de uitgevouwen map bevindt zich gewoonlijk in respectievelijk `<path-to-aem-server>/dropins/cq-quickstart-65.war` en `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war` .
   * De map `launchpad/startup` . U kunt het schrappen door het volgende bevel in de terminal in werking te stellen veronderstelt u in de serveromslag bent:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Het `base.jar` -bestand. U kunt dit doen door de volgende bevelen in werking te stellen:

     ```shell
     find crx-quickstart/launchpad -type f -name 
     "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
     ```

   * Het `BootstrapCommandFile_timestamp.txt` -bestand:

     ```shell
     rm -f crx-quickstart/launchpad/felix/bundle0/BootstrapCommandFile_timestamp.txt
     ```

   * Verwijder het `sling.options` -bestand door het uit te voeren:

     ```shell
     find crx-quickstart/launchpad -type f -name "sling.options.file" -exec rm -rf {} \; 
     ```

   * Verwijder het `sling.bootstrap.txt` -bestand:

     ```shell
     rm -rf crx-quickstart/launchpad/sling_bootstrap.txt
     ```

1. Maak een back-up van het `sling.properties` -bestand (gewoonlijk aanwezig in `crx-quickstart/conf/` ) en verwijder deze
1. Verander de versie van servlet in **6.0** in het `server.xml` dossier
1. Controleer de beginparameters voor de AEM-server en zorg ervoor dat u de parameters bijwerkt volgens uw systeemvereisten. Zie [ Standalone Installatie van de Douane ](/help/sites-deploying/custom-standalone-install.md) voor meer informatie
1. Installeer Java 17 en zorg ervoor dat het correct geïnstalleerd door te lopen is:

   ```shell
   java -version
   ```

1. Download de nieuwe war 6.5 LTS van de distributie van de Software en kopieer het aan dropins omslag die bij wordt gevestigd: `/<path-to-aem-server>/dropins/`
1. AEM-instantie starten: dit kan doorgaans gebeuren met de volgende opdracht:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Volg onderstaande instructies voor het geval u aangepaste wijzigingen in `sling.properties` hebt:

   1. De AEM-instantie stoppen door `<path-to-wlp-directory>/bin/server stop server_name` uit te voeren
   1. Pas uw aangepaste `sling.properties` wijzigingen toe op het nieuwe `sling.properties` -bestand (door naar het back-upbestand te verwijzen dat bij stap 6 is gemaakt)
   1. Start de AEM-instantie. Dit kan doorgaans worden gedaan door: `<path-to-wlp-directory>/bin/server start server_name`

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in de [ pagina van de Code en van de Aanpassingen van de Verbetering van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [ Controle van de Verbetering van het Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) voor meer informatie.