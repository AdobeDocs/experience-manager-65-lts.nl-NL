---
title: Upgradestappen voor installatie van toepassingsservers (Tomcat)
description: Leer hoe u AEM-exemplaren die via Tomcat zijn geïmplementeerd, kunt upgraden.
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 7f8de16f-9e9a-4d37-9978-d26c496b911c
source-git-commit: b9b5492b1bf5f717dec6a48ffbe808bf75cbce6a
workflow-type: tm+mt
source-wordcount: '478'
ht-degree: 0%

---

# Upgradestappen voor installatie van toepassingsservers (Tomcat) {#upgrade-steps-for-application-server-installations-tomcat}

>[!NOTE]
>
>Deze pagina schetst de verbeteringsprocedure voor AEM 6.5 LTS op Tomcat.

## Stappen voor upgrade {#pre-upgrade-steps}

Voordat u de upgrade uitvoert, moeten verschillende stappen worden uitgevoerd. Zie [&#x200B; Bevorderend Code en Aanpassingen &#x200B;](/help/sites-deploying/upgrading-code-and-customizations.md) en [&#x200B; pre-Verbeterde Taken van het Onderhoud &#x200B;](/help/sites-deploying/pre-upgrade-maintenance-tasks.md) voor meer informatie. Bovendien, zorg ervoor dat uw systeem aan de [&#x200B; vereisten voor AEM 6.5 LTS &#x200B;](/help/sites-deploying/technical-requirements.md) voldoet en [&#x200B; verbetering planningsoverwegingen &#x200B;](/help/sites-deploying/upgrade-planning.md) ziet en hoe [&#x200B; Analysator &#x200B;](/help/sites-deploying/aem-analyzer.md) u kan helpen de ingewikkeldheid schatten.


### Migratievereisten {#migration-prerequisites}

* **Minimaal Vereiste versie van Java**: Zorg ervoor u Oracle® JRE 17/21 op uw server van Tomcat hebt geïnstalleerd.
* **Tomcat server**: De gesteunde versies van de server van Tomcat voor AEM 6.5 LTS zijn **10.0.x** en **10.1.x**.

### De upgrade uitvoeren {#performing-the-upgrade}

Alle voorbeelden in deze procedure gebruiken Tomcat als de Server van de Toepassing en impliceren dat u een werkende versie van AEM reeds opgesteld hebt. De procedure wordt bedoeld om verbeteringen te documenteren die van versie van AEM **6.5** aan **worden uitgevoerd 6.5 LTS**.

1. Als AEM 6.5 al is geïmplementeerd, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/system/console/bundles`*
1. Stop vervolgens met AEM 6.5. Dit kan worden gedaan vanuit Tomcat App Manager op: *`https://<serveraddress:port>/manager/html`*
1. Zorg ervoor dat u [&#x200B; pre-verbeterings &#x200B;](#pre-upgrade-steps) activiteiten zoals steun van AEM 6.5 server alvorens om het even welke verbeteringsactiviteit hebt voltooid
1. Installeer Java 17/Java 21 en zorg ervoor dat het correct geïnstalleerd door het bevel in werking te stellen is:

   ```
   java –version
   ```

1. AEM 6.5 LTS-compatibele Tomcat-server instellen
1. Controleer de beginparameters voor de AEM-server en zorg ervoor dat u de parameters bijwerkt volgens de systeemvereisten. Zie [&#x200B; Java 17/Java 21 Overwegingen &#x200B;](/help/sites-deploying/custom-standalone-install.md#java-considerations) voor meer informatie
1. Implementeer de nieuwe gedownloade 6,5 LTS-oorlog op de Tomcat-server met Java 17/Java 21 en start AEM 6.5 LTS Tomcat-server door:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. Nadat de AEM is gestart, controleert u of alle bundels actief zijn door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*
1. Stop de AEM 6.5 LTS Tomcat-server. In de meeste gevallen kunt u dit doen door het script `./catalina.sh` uit te voeren, door deze opdracht uit te voeren vanaf de terminal:

   ```
   $CATALINA_HOME/bin/catalina.sh stop
   ```

1. Migreer nu uw inhoud van AEM 6.5 aan AEM 6.5 LTS door de stappen hier te volgen: [&#x200B; AEM 6.5 aan AEM 6.5 LTS de Migratie van de Inhoud die Oak-upgrade gebruikt &#x200B;](/help/sites-deploying/aem-65-to-aem-65lts-content-migration-using-oak-upgrade.md)
1. Nadat de inhoud is gemigreerd, past u de vereiste aangepaste wijzigingen in het `sling.properties` -bestand toe
1. Start de AEM 6.5 LTS Tomcat-server door deze uit te voeren:

   ```
   $CATALINA_HOME/bin/catalina.sh start
   ```

1. De foutenlogboeken controleren terwijl AEM begint om te controleren dat er geen fouten zijn en AEM loopt regelmatig
1. Nadat AEM 6.5 LTS is gestart, controleert u of de bundels correct werken door toegang te krijgen tot: *`https://<serveraddress:port>/cq/system/console/bundles`*

## Bijgewerkte Codebase implementeren {#deploy-upgraded-codebase}

Zodra het verbeteringsproces is voltooid, zou de bijgewerkte codebasis moeten worden opgesteld. De stappen voor het bijwerken van de codebasis om in de doelversie van AEM te werken kunnen in [&#x200B; de Code en de pagina van Aanpassingen van de Verbetering &#x200B;](/help/sites-deploying/upgrading-code-and-customizations.md) worden gevonden.

## Naupgrade-controles en probleemoplossing uitvoeren {#perform-post-upgrade-checks-and-troubleshooting}

Zie [&#x200B; Controle van de Verbetering van het Post en het Oplossen van problemen &#x200B;](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md) voor meer informatie.
