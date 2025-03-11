---
title: Installeren van toepassingsserver
description: Leer hoe u Adobe Experience Manager met een toepassingsserver installeert.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: deploying
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
exl-id: 09d54b52-485a-453c-a2d0-535adead9e6c
source-git-commit: 5f968f5dc0696a683cc063d330c8edfba05f11ab
workflow-type: tm+mt
source-wordcount: '0'
ht-degree: 0%

---

# Installeren van toepassingsserver{#application-server-install}

>[!NOTE]
>
>`JAR` en `WAR` zijn de bestandstypen waarin Adobe Experience Manager (AEM) wordt vrijgegeven. Deze formaten worden kwaliteitsborgd om aan de steunniveaus tegemoet te komen die Adobe heeft toegezegd.
>

In deze sectie wordt uitgelegd hoe u Adobe Experience Manager (AEM) kunt installeren met een toepassingsserver. Raadpleeg de [ Gesteunde sectie van Platforms ](/help/sites-deploying/technical-requirements.md#servlet-engines-application-servers) om over de specifieke steunniveaus te lezen die voor de individuele toepassingsservers worden verstrekt.

De installatiestappen van de volgende toepassingsservers worden beschreven:

* [WebSphere](#websphere)
* [Tomcat 11.0.x](#tomcat)

Raadpleeg de documentatie bij de toepassingsserver voor meer informatie over het installeren van webtoepassingen, serverconfiguraties en over het starten en stoppen van de server.

<!-- >[!NOTE]
>
>If you are using Dynamic Media in a WAR deployment, see [Dynamic Media documentation](/help/assets/config-dynamic.md#enabling-dynamic-media). -->

## Algemene beschrijving {#general-description}

### Standaardgedrag bij het installeren van AEM in een toepassingsserver {#default-behaviour-when-installing-aem-in-an-application-server}

AEM wordt geleverd als één oorlogsbestand dat moet worden geïmplementeerd.

Indien opgesteld, gebeurt het volgende door gebrek:

* De uitvoermodus is `author`
* De instantie (Repository, Felix OSGI-omgeving, bundels enzovoort) wordt geïnstalleerd in is `${user.dir}/crx-quickstart` , waar `${user.dir}` de huidige werkmap is. Dit pad naar crx-quickstart wordt `sling.home` genoemd

* De hoofdmap van de context is de naam van het oorlogsbestand. Bijvoorbeeld `aem-65-lts` .

#### Configuratie {#configuration}

U kunt het standaardgedrag als volgt wijzigen:

* uitvoeringsmodus: configureer de parameter `sling.run.modes` in het `WEB-INF/web.xml` -bestand van het AEM-oorlogsbestand vóór de implementatie

* sling.home: configureer de parameter `sling.home` in het `WEB-INF/web.xml` -bestand van het AEM-oorlogsbestand vóór de implementatie

* contextroot: naam van AEM-oorlogsbestand wijzigen

#### Installatie publiceren {#publish-installation}

Als u een publicatie-instantie wilt implementeren, moet u de uitvoeringsmodus instellen om te publiceren:

* De `WEB-INF/web.xml` uit het AEM-oorlogsbestand uitpakken
* Parameter `sling.run.modes` wijzigen in publicatie
* `web.xml` bestand opnieuw plaatsen in het AEM-oorlogsbestand
* AEM-oorlogsbestand implementeren

#### Installatiecontrole {#installation-check}

Om te controleren of alles is geïnstalleerd, kunt u:

* staart het `error.log` dossier om te zien dat al inhoud wordt geïnstalleerd
* in `/system/console` alle bundels geïnstalleerd zijn

#### Twee instanties op dezelfde toepassingsserver {#two-instances-on-the-same-application-server}

Voor demonstratiedoeleinden kan het aangewezen zijn om zowel auteur te installeren als instantie te publiceren in één toepassingsserver. Om dat te bereiken, moet u:

1. Variabelen `sling.home` en `sling.run.modes` van het publicatie-exemplaar wijzigen
1. Het `WEB-INF/web.xml` -bestand uitpakken uit het AEM-oorlogsbestand
1. De parameter `sling.home` wijzigen in een ander pad (absolute en relatieve paden zijn mogelijk)
1. `sling.run.modes` wijzigen in `publish` voor de publicatie-instantie
1. Het `web.xml` -bestand herhalen
1. Wijzig de naam van de oorlogsbestanden, zodat ze verschillende namen hebben. Wijzig bijvoorbeeld de naam van de ene naar `aemauthor.war` en de andere naar `aempublish.war`
1. Gebruik hogere geheugeninstellingen. Standaard AEM-instanties gebruiken bijvoorbeeld `-Xmx3072m`
1. De twee webtoepassingen implementeren
1. Nadat de Plaatsing de twee Webtoepassingen ophoudt
1. Zorg er in zowel auteur- als publicatieinstanties voor dat in het `sling.properties` -bestand de eigenschap `felix.service.urlhandlers` is ingesteld op `false` . (De standaardwaarde is dat deze is ingesteld op `true` .)
1. Start de twee webtoepassingen opnieuw.

## Installatieprocedures voor toepassingsservers {#application-servers-installation-procedures}

### WebSphere® 24.0.0.7 {#websphere}

Voor de plaatsing, gelieve te lezen de [ Algemene Beschrijving ](#general-description) hierboven.

**Voorbereiding van de Server**

* Laat de Basiskopballen van de Auditie door overgaan:

   * Een manier om AEM een gebruiker te laten verifiëren, is het uitschakelen van de algemene beheerbeveiliging van de WebSphere®-server. Om dat te doen, ga naar **Veiligheid > Globale Veiligheid** en uncheck **administratieve veiligheidscontroledoos** toelaten, sparen, en begin de server opnieuw.

* Instellen `"JAVA_OPTS= -Xmx2048m"`
* Als u AEM wilt installeren met gebruik van contextroot = /, wijzigt u de basis van de context van de bestaande standaardwebtoepassing.

**stel de Toepassing van het Web van AEM** op

* AEM-oorlogsbestand downloaden
* Maak indien nodig uw configuraties in het `web.xml` -bestand. Voor meer info, zie [ Algemene Beschrijving ](#general-description) hierboven.

   * Het `WEB-INF/web.xml` -bestand uitpakken
   * De parameter `sling.run.modes` wijzigen in `publish`
   * Verwijder de commentaarmarkering van de eerste parameter `sling.home` en stel dit pad naar wens in
   * Herhaal het bestand `web.xml` .

* AEM-oorlogsbestand implementeren

   * Kies een hoofdmap voor de context. Als u de sling looppaswijzen wilt plaatsen moet u de gedetailleerde stappen van de opstellen tovenaar selecteren, dan specificeer het in stap 6 van de tovenaar.

* De AEM-webtoepassing starten

#### Tomcat 11.0.x {#tomcat}

Alvorens een plaatsing leest de [ Algemene Beschrijving ](#general-description) hierboven.

* **bereidt de Server van Tomcat voor**

   * VM-geheugeninstellingen verhogen:

      * Voeg in `bin/catalina.bat` (resp. `catalina.sh` op UNIX®) de volgende instelling toe:

        ```
        set "JAVA_OPTS= -Xmx2048m`
        ```

   * Tomcat schakelt de toegang van beheerders of beheerders bij de installatie niet in. Daarom moet u `tomcat-users.xml` handmatig bewerken om toegang toe te staan voor deze accounts:

      * Bewerk `tomcat-users.xml` om toegang voor beheerder en manager op te nemen. De configuratie zou gelijkaardig aan het volgende voorbeeld moeten kijken:

        ```xml
        <?xml version='1.0' encoding='utf-8'?>
        <tomcat-users>
        role rolename="manager"/>
        role rolename="tomcat"/>
        <role rolename="admin"/>
        <role rolename="role1"/>
        <role rolename="manager-gui"/>
        <user username="both" password="tomcat" roles="tomcat,role1"/>
        <user username="tomcat" password="tomcat" roles="tomcat"/>
        <user username="admin" password="admin" roles="admin,manager-gui"/>
        <user username="role1" password="tomcat" roles="role1"/>
        </tomcat-users>
        ```

   * Als u AEM wilt implementeren met contextroot &quot;/&quot;, moet u de hoofdmap van de context van de bestaande ROOT-webapp wijzigen:

      * De ROOT-webapp stoppen en de implementatie ervan ongedaan maken
      * Wijzig de naam van de map `ROOT.war` in de webapps-map van Tomcat
      * Start de webapp opnieuw

   * Als u de AEM-webtoepassing installeert met behulp van de manager-gui, moet u de maximale grootte van een geüpload bestand verhogen, aangezien de standaard alleen uploadgrootte van 50 MB toestaat. U bereikt als volgt de bewerking `web.xml` van de webtoepassing van het beheer:

     `webapps/manager/WEB-INF/web.xml`

     en verhoog de waarden voor `max-file-size` en `max-request-size` tot ten minste 500 MB. Zie het volgende `multipart-config` in een voorbeeldbestand `web.xml` hieronder:

     ```xml
     <multipart-config>
     <!-- 500MB max -->
     <max-file-size>524288000</max-file-size>
     <max-request-size>524288000</max-request-size>
     <file-size-threshold>0</file-size-threshold>
     </multipart-config>
     ```

* **stel het Webtoepassing van AEM** op

   * Download het AEM-oorlogsbestand.
   * Maak indien nodig uw configuraties in het `web.xml` -bestand.

      * Het `WEB-INF/web.xml` -bestand uitpakken
      * De parameter `sling.run.modes` wijzigen in `publish`
      * Verwijder de commentaarmarkering van de eerste parameter van `sling.home` en stel dit pad naar wens in
      * Herhaal het bestand `web.xml` .

   * Wijzig de naam van het AEM-oorlogsbestand in `ROOT.war` als u het wilt gebruiken als basiswebapp. Wijzig de naam in `aemauthor.war` als u `aemauthor` wilt gebruiken als hoofdmap van de context.
   * Kopieer deze naar de webapps-map van Tomcat
   * Wacht tot AEM is geïnstalleerd.
