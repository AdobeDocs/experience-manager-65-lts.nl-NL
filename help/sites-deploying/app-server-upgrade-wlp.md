---
title: De Stappen van de verbetering voor de Installaties van de Server van de Toepassing (WLP)
description: Leer hoe u AEM-exemplaren upgradet die via Webspehere Liberty zijn geïmplementeerd.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 2a5d9026-49bc-4766-bcbe-38d834c14f72
source-git-commit: 82af7ee5b3665dcc33b47e05c8580e9981728888
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 0%

---

# De Stappen van de verbetering voor de Installaties van de Server van de Toepassing (WLP) {#upgrade-steps-for-application-server-installations-wlp}

>[!NOTE]
>
>Deze pagina beschrijft de verbeteringsprocedure voor AEM 6.5 LTS op WLP (WebSphere® Liberty).

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Bovendien, zorg ervoor dat uw systeem aan de [ vereisten voor AEM 6.5 LTS ](/help/sites-deploying/technical-requirements.md) voldoet.

Controle [ plannend Uw Verbetering ](/help/sites-deploying/upgrade-planning.md) en hoe de [ Analysator van AEM ](/help/sites-deploying/aem-analyzer.md) u kan helpen de ingewikkeldheid rond de bevordering van AEM schatten.

### Migratievereisten {#migration-prerequisites}

* **Minimum Vereiste versie van Java**: Zorg ervoor u IBM® Sumeru JRE 17 op uw server van WLP hebt geïnstalleerd.

### De upgrade uitvoeren {#performing-the-upgrade}

1. Zorg ervoor dat u de [ pre-verbeterings ](#pre-upgrade-steps) stappen als het steunen van AEM 6.5 server alvorens om het even welke verbeteringsactiviteit hebt voltooid
1. Kies afhankelijk van uw vereisten een van de volgende upgradepaden:
   1. **Verbetering op plaats**: Als uw huidige server WLP Server Servlet 6 steunt, kunt u een verbetering op zijn plaats uitvoeren en met stap 3 verdergaan.
   1. **Sidegrade**: Als u verkiest een verse opstelling of als uw server WLP geen Servlet 6 steunt, opstelling een nieuwe instantie WLP met AEM 6.5 LTS en migrate de inhoud door [ AEM 6.5 aan AEM 6.5 LTS de Migratie van de Inhoud te volgen van Oak-upgrade ](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md) gids en overslaan aan [ Geüpgraded Codebase ](#deploy-upgraded-codebase) sectie op te stellen

1. Stop de AEM-instantie. Dit kan normaal gesproken worden gedaan met deze opdracht:

   ```shell
   <path-to-wlp-directory>/bin/server stop server_name
   ```

1. Verwijder de bestanden en mappen die u niet meer nodig hebt. De items die u specifiek moet verwijderen zijn:

   * **cq-quickstart-65.war** van de `dropins` omslag en de `expanded` omslag typisch die bij `<path-to-aem-server>/dropins/cq-quickstart-65.war` en `<path-to-aem-server>/apps/expanded/cq-quickstart-65.war` wordt gevestigd
   * De map `launchpad/startup` . U kunt het schrappen door het volgende bevel in de terminal in werking te stellen veronderstelt u in de serveromslag bent:

     ```shell
     rm -rf crx-quickstart/launchpad/startup
     ```

   * Het `base.jar` -bestand. U kunt dit doen door de volgende bevelen in werking te stellen:

     ```shell
     find crx-quickstart/launchpad -type f -name "org.apache.sling.launchpad.base.jar*" -exec rm -f {} \;
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
1. Installeer Java 17 en zorg ervoor dat het correct geïnstalleerd door te lopen is:

   ```shell
   java -version
   ```

1. Controleer de beginparameters voor de AEM-server en zorg ervoor dat de parameters aan uw vereisten voldoen. Zie [ Java 17 Overwegingen ](/help/sites-deploying/custom-standalone-install.md#java-considerations) voor meer informatie.
1. Download de nieuwe 6.5 LTS-oorlog en kopieer deze naar de map dropins in: `/<path-to-aem-server>/dropins/`
1. AEM-instantie starten: dit kan doorgaans gebeuren met de volgende opdracht:

   ```shell
   <path-to-wlp-directory>/bin/server start server_name
   ```

1. Volg onderstaande instructies voor het geval u aangepaste wijzigingen in `sling.properties` hebt:

   1. De AEM-instantie stoppen door `<path-to-wlp-directory>/bin/server stop server_name` uit te voeren
   1. Pas uw aangepaste `sling.properties` wijzigingen toe op het nieuwe `sling.properties` -bestand (door naar het back-upbestand te verwijzen dat in stap 5 is gemaakt)
   1. Start de AEM-instantie. Dit kan doorgaans worden gedaan door: `<path-to-wlp-directory>/bin/server start server_name`

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [ de Code en de pagina van Aanpassingen van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [ Controle van de Verbetering van de Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md).
