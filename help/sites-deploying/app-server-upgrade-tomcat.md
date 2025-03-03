---
title: Upgradestappen voor installatie van toepassingsservers (Tomcat)
description: Leer hoe u AEM-exemplaren die via Tomcat zijn geïmplementeerd, kunt upgraden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 8798c608ea168d753be2a08b25a0d0d344b0fef6
workflow-type: tm+mt
source-wordcount: '484'
ht-degree: 0%

---

# Upgradestappen voor installatie van toepassingsservers (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Deze pagina beschrijft de verbeteringsprocedure voor de AEM 6.5 LTS oorlog op Tomcat.

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Zorg er bovendien voor dat uw systeem voldoet aan de vereisten voor AEM 6.5 LTS. Zie hoe de Analysator u kan helpen de ingewikkeldheid van uw verbetering schatten en ook een plan voor de verbetering zien (zie [ plannend Uw Verbetering ](/help/sites-deploying/upgrade-planning.md) voor meer informatie).

### Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java**: Zorg ervoor u IBM Sumeru JRE 17 op uw server van Tomcat hebt geïnstalleerd.
* **Tomcat server**: De versie van de server van Tomcat die voor 6.5 LTS wordt vereist is **11.0.x**.

### De upgrade uitvoeren {#performing-the-upgrade}

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM reeds opgesteld hebt. De procedure wordt bedoeld om verbeteringen te documenteren die van versie van AEM **6.5** aan **worden uitgevoerd 6.5 LTS**.

1. Als AEM 6.5 al is geïmplementeerd, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Stop vervolgens met AEM 6.5. Dit kan worden gedaan vanuit Tomcat App Manager op: *`https://<serveraddress:port>/manager/html`*
1. Zorg ervoor dat u [ pre-verbeterings ](#pre-upgrade-steps) activiteiten zoals steun van AEM 6.5 server alvorens om het even welke verbeteringsactiviteit hebt voltooid
1. Installeer Java 17 en zorg ervoor dat het correct geïnstalleerd door het bevel in werking te stellen is:

   ```
   java –version
   ```

1. AEM 6.5 LTS-compatibele Tomcat-server instellen
1. Controleer de beginparameters voor de AEM-server en zorg ervoor dat u de parameters bijwerkt volgens de systeemvereisten. Zie [ Standalone installatie van de Douane ](/help/sites-deploying/custom-standalone-install.md) voor meer informatie
1. Implementeer de nieuwe gedownloade 6,5 LTS-oorlog op de Tomcat-server met behulp van Java 17 en start AEM 6.5 LTS Tomcat-server door:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Zodra AEM in gebruik is, zorg ervoor alle bundels in lopende staat door tot: * `https://<serveraddress:port>/cq/system/console/bundles*` toegang te hebben
1. Stop nu de AEM 6.5 LTS Tomcat-server. In de meeste gevallen kunt u dit doen door het script `./catalina.sh` uit te voeren, door deze opdracht uit te voeren vanaf de terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Migreer nu uw inhoud van AEM 6.5 aan AEM 6.5 LTS gebruikend dit leerprogramma: [ AEM 6.5 aan AEM 6.5 de Migratie van de Inhoud die Oak-upgrade gebruikt ](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Nadat de inhoud is gemigreerd, past u de vereiste aangepaste wijzigingen in het `sling.properties` -bestand toe
1. Start de AEM 6.5 LTS Tomcat-server door deze uit te voeren:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. De foutenlogboeken controleren terwijl AEM begint om te controleren dat er geen fouten zijn en AEM loopt regelmatig
1. Nadat AEM 6.5 LTS is gestart, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het op zijn plaats verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in de [ pagina van de Code en van de Aanpassingen van de Verbetering van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [ Controle van de Verbetering van het Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) voor meer informatie.