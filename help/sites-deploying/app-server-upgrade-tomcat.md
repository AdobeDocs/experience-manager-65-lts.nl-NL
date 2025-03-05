---
title: Upgradestappen voor installatie van toepassingsservers (Tomcat)
description: Leer hoe u AEM-exemplaren die via Tomcat zijn geïmplementeerd, kunt upgraden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: a8367ff25591c6ea7916aab17e733605ec3f59c8
workflow-type: tm+mt
source-wordcount: '467'
ht-degree: 0%

---

# Upgradestappen voor installatie van toepassingsservers (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor AEM 6.5 LTS op Tomcat.

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) en [ pre-Verbeterde Taken van het Onderhoud ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Bovendien, zorg ervoor dat uw systeem aan de [ vereisten voor AEM 6.5 LTS ](/help/sites-deploying/technical-requirements.md) voldoet en [ verbetering planningsoverwegingen ](/help/sites-deploying/upgrade-planning.md) ziet en hoe [ Analysator ](/help/sites-deploying/pattern-detector.md) u kan helpen de ingewikkeldheid schatten.


### Migratievereisten {#migration-prerequisites}

* **Minimum Vereiste versie van Java**: Zorg ervoor u Oracle® JRE 17 op uw server van Tomcat hebt geïnstalleerd.
* **Tomcat server**: De versie van de server van Tomcat die voor 6.5 LTS wordt vereist is **11.0.x**.

### De upgrade uitvoeren {#performing-the-upgrade}

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM reeds opgesteld hebt. De procedure wordt bedoeld om verbeteringen te documenteren die van versie van AEM **6.5** aan **worden uitgevoerd 6.5 LTS**.

1. Als AEM 6.5 al is geïmplementeerd, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/system/console/bundles`*
1. Stop vervolgens met AEM 6.5. Dit kan worden gedaan vanuit Tomcat App Manager op: *`https://<serveraddress:port>/manager/html`*
1. Zorg ervoor dat u [ pre-verbeterings ](#pre-upgrade-steps) activiteiten zoals steun van AEM 6.5 server alvorens om het even welke verbeteringsactiviteit hebt voltooid
1. Installeer Java 17 en zorg ervoor dat het correct geïnstalleerd door het bevel in werking te stellen is:

   ```
   java –version
   ```

1. AEM 6.5 LTS-compatibele Tomcat-server instellen
1. Controleer de beginparameters voor de AEM-server en zorg ervoor dat u de parameters bijwerkt volgens de systeemvereisten. Zie [ Java 17 Overwegingen ](/help/sites-deploying/custom-standalone-install.md#java-17-considerations-java-considerations) voor meer informatie
1. Implementeer de nieuwe gedownloade 6,5 LTS-oorlog op de Tomcat-server met behulp van Java 17 en start AEM 6.5 LTS Tomcat-server door:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Nadat de AEM is gestart, controleert u of alle bundels actief zijn door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Stop de AEM 6.5 LTS Tomcat-server. In de meeste gevallen kunt u dit doen door het script `./catalina.sh` uit te voeren, door deze opdracht uit te voeren vanaf de terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Migreer nu uw inhoud van AEM 6.5 aan AEM 6.5 LTS door de stappen hier te volgen: [ AEM 6.5 aan AEM 6.5 LTS de Migratie van de Inhoud die Oak-upgrade gebruikt ](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Nadat de inhoud is gemigreerd, past u de vereiste aangepaste wijzigingen in het `sling.properties` -bestand toe
1. Start de AEM 6.5 LTS Tomcat-server door deze uit te voeren:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. De foutenlogboeken controleren terwijl AEM begint om te controleren dat er geen fouten zijn en AEM loopt regelmatig
1. Nadat AEM 6.5 LTS is gestart, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [ de Code en de pagina van Aanpassingen van de Verbetering ](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [ Controle van de Verbetering van het Post en het Oplossen van problemen ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) voor meer informatie.
