---
title: Prestaties afstemmen van AEM Forms-server
description: AEM Forms kan de cache-instellingen en JVM-parameters optimaliseren. Ook kan het gebruik van een webserver de prestaties van AEM Forms-implementatie verbeteren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 4009c85e-cb8a-4bed-a6ff-7c76fe78a47f
source-git-commit: 060bb23d64a90f0b2da487ead4c672cbf471c9a8
workflow-type: tm+mt
source-wordcount: '795'
ht-degree: 0%

---

# Prestaties afstemmen op AEM Forms Server{#performance-tuning-of-aem-forms-server}

Dit artikel bespreekt strategieën en beste praktijken die u kunt uitvoeren om knelpunten te verminderen en de prestaties van uw plaatsing van AEM Forms te optimaliseren.

## Cacheinstellingen {#cache-settings}

U kunt de caching strategie voor AEM Forms vormen en controleren gebruikend de **component van de Configuraties van 0&rbrace; Mobiele Forms in de Console van de Configuratie van het Web van AEM bij:**

* (AEM Forms op OSGi) `https://'[server]:[port]'/system/console/configMgr`

<!--
* (AEM Forms on JEE) `https://'[server]:[port]'/lc/system/console/configMgr`
-->

De beschikbare opties voor caching zijn als volgt:

* **niets**: Dwingt om geen artefact in het voorgeheugen onder te brengen. Dit zal in de praktijk de prestaties vertragen en hoge geheugenbeschikbaarheid wegens het ontbreken van geheim voorgeheugen vereist.
* **Conservatief**: Dictates om slechts die tussentijdse artefacten in het voorgeheugen onder te brengen die vóór het teruggeven van de vorm, zoals een malplaatje worden geproduceerd dat gealigneerde fragmenten en beelden bevat.
* **Agressief**: Dwingt om bijna alles in het voorgeheugen onder te brengen die, met inbegrip van teruggegeven inhoud van HTML naast alle artefacten van het Conservatieve in het voorgeheugen onderbrengende niveau kan worden opgeslagen. Het resulteert in de beste prestaties maar verbruikt ook meer geheugen voor het opslaan van artefacten in cache. Met een agressieve cachestrategie krijgt u constante prestaties bij het weergeven van een formulier terwijl de weergegeven inhoud in de cache wordt opgeslagen.

De standaardinstellingen voor de cache van AEM Forms zijn mogelijk niet geschikt voor optimale prestaties. Daarom wordt aangeraden de volgende instellingen te gebruiken:

* **Strategie van het Geheime voorgeheugen**: Agressief
* **grootte van het Geheime voorgeheugen** (in termen van aantal vormen): Zoals vereist
* **Max de Grootte van Objecten**: Zoals vereist

![ Mobiele Configuraties van Forms ](assets/snap.png)

>[!NOTE]
>
>Als u AEM Dispatcher gebruikt om adaptieve formulieren in cache te plaatsen, wordt ook het adaptieve formulier in cache geplaatst dat formulieren met voorgevulde gegevens bevat. Als dergelijke formulieren worden aangeboden in het cachegeheugen van AEM Dispatcher, kan dit ertoe leiden dat voorgevulde of opgevulde gegevens worden weergegeven aan de gebruikers. Gebruik dus AEM Dispatcher om adaptieve formulieren die geen voorgevulde gegevens gebruiken in cache op te slaan. Bovendien maakt een Dispatcher-cache cachefragmenten in de cache niet automatisch ongeldig. Gebruik het dus niet om formulierfragmenten in de cache op te slaan. Voor dergelijke vormen en fragmenten, gebruik [ Adaptief vormengeheime voorgeheugen ](../../forms/using/configure-adaptive-forms-cache.md).

## JVM-parameters {#jvm-parameters}

Voor optimale prestaties is het raadzaam de volgende JVM `init` -argumenten te gebruiken om de `Java heap` en `PermGen` -argumenten te configureren.

```shell
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xms8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -Xmx8192m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:PermSize=256m
set CQ_JVM_OPTS=%CQ_JVM_OPTS% -XX:MaxPermSize=1024m
```

>[!NOTE]
>
>De aanbevolen instellingen zijn voor Windows 2008 R2 8 Core en Oracle HotSpot 1.7 (64-bits) JDK en moeten worden vergroot of verkleind volgens de systeemconfiguratie.

## Een webserver gebruiken {#using-a-web-server}

Adaptieve formulieren en HTML5-formulieren worden weergegeven in HTML5-indeling. De resulterende uitvoer kan groot zijn, afhankelijk van factoren zoals de formuliergrootte en afbeeldingen in het formulier. Om de gegevensoverdracht te optimaliseren, verdient het aanbeveling de HTML-reactie te comprimeren met de webserver van waaruit de aanvraag wordt verzonden. Deze benadering vermindert de reactiegrootte, het netwerkverkeer, en de tijd die wordt vereist om gegevens tussen server en cliëntmachines te stromen.

Voer bijvoorbeeld de volgende stappen uit om compressie op Apache Web Server 2.0 32-bits met JBoss® in te schakelen:

>[!NOTE]
>
>De volgende instructies zijn niet van toepassing op andere servers dan Apache Web Server 2.0 32-bits. Zie de bijbehorende productdocumentatie voor stappen die specifiek zijn voor andere servers.

De volgende stappen tonen de vereiste wijzigingen aan om compressie met Apache Web Server mogelijk te maken

**verkrijg de software van de Apache Webserver van toepassing op uw werkend systeem**

* Windows: download de Apache-webserver van de Apache HTTP Server Project-site.
* Solaris™ 64-bits: download de Apache-webserver van de Sunfreeware for Solaris™-website.
* Linux®: de Apache-webserver is vooraf geïnstalleerd op een Linux®-systeem.

Apache kan met CRX communiceren via het HTTP-protocol. De configuraties zijn bedoeld voor optimalisatie met gebruik van HTTP.

1. Verwijder de commentaarmarkering van de volgende moduleconfiguraties in `APACHE_HOME/conf/httpd.conf` dossier.

   ```shell
   LoadModule proxy_balancer_module modules/mod_proxy.so
   LoadModule proxy_balancer_module modules/mod_proxy_http.so
   LoadModule deflate_module modules/mod_deflate.so
   ```

   >[!NOTE]
   >
   >Voor Linux® is de standaardwaarde `APACHE_HOME` `/etc/httpd/` .

1. Vorm de volmacht op haven 4502 van crx.
Voeg de volgende configuratie toe in het configuratiebestand van `APACHE_HOME/conf/httpd.conf` .

   ```shell
   ProxyPass / https://<server>:4502/
   ProxyPassReverse / https://<server>:4502/
   ```

1. Compressie inschakelen. Voeg de volgende configuratie toe in het configuratiebestand van `APACHE_HOME/conf/httpd.conf` .

   **voor vormen HTML5**

   ```xml
   <Location /content/xfaforms>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Do not compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   **voor adaptieve vormen**

   ```xml
   <Location /content/forms/af>
       <IfModule mod_deflate.c>
           SetOutputFilter DEFLATE
           #Do not compress
           SetEnvIfNoCase Request_URI \.(?:gif|jpe?g|png)$ no-gzip dont-vary
           SetEnvIfNoCase Request_URI \.(?:exe|t?gz|zip|bz2|sit|rar)$ no-gzip dont-vary
           #Dealing with proxy servers
               <IfModule mod_headers.c>
                   Header append Vary User-Agent
               </IfModule>
       </IfModule>
   </Location>
   ```

   Als u toegang wilt krijgen tot de crx-server, gebruikt u `https://'server':80` , waarbij `server` de naam is van de server waarop de Apache-server wordt uitgevoerd.

## Een antivirus gebruiken op een server waarop AEM Forms wordt uitgevoerd {#using-an-antivirus-on-server-running-aem-forms}

U kunt trage prestaties ervaren op de servers die een antivirussoftware uitvoeren. Een altijd-op antivirus (op-toegang aftasten) software scant alle dossiers van een systeem. Het kan de server vertragen en de prestaties van de AEM Forms worden beïnvloed.

Om de prestaties te verbeteren, kunt u de antivirussoftware zo instellen dat de volgende AEM Forms-bestanden en -mappen niet altijd worden gescand (tijdens het scannen):

* AEM Installation directory. Als het niet mogelijk is de volledige map uit te sluiten, sluit u het volgende uit:

   * [ AEM installatiemap ] \ crx-bewaarplaats \ temp
   * [ de installatiemap van AEM ] \ crx-bewaarplaats \ bewaarplaats
   * [ de installatiemap van AEM ] \ crx-bewaarplaats \ lanceerpad

<!--

* Application server temporary directory. The default location is:

    * (JBoss&reg;) [AEM installation directory]\jboss\standalone\tmp
    * (WebLogic) \Oracle\Middleware\user_projects\domains\LCDomain\servers\LCServer1\tmp
    * (WebSphere&reg;) \Program Files\IBM\WebSphere\AppServer\profiles\AppSrv01\temp

* **(AEM Forms on JEE only)** Global Document Storage (GDS) directory. The default location is:

    * (JBoss&reg;) [appserver root]/server/'server'/svcnative/DocumentStorage
    * (WebLogic) [appserverdomain]/'server'/adobe/LiveCycleServer/DocumentStorage
    * (WebSphere&reg;) [appserver root]/installedApps/adobe/'server'/DocumentStorage

* **(AEM Forms on JEE only)** AEM Forms Server logs and temporary directory. The default location is:

    * Server logs - [AEM Forms installation directory]\Adobe\AEM forms\[app-server]\server\all\logs
    * Temp directory - [AEM Forms installation directory]\temp
-->

>[!NOTE]
>
>* Als u een verschillende plaats voor GDS en tijdelijke folder gebruikt, open AdminUI bij `https://'[server]:[port]'/adminui`, navigeer aan **Huis > Montages > de Montages van het Systeem van de Kern > de Configuraties van de Kern** om de plaats in gebruik te bevestigen.
>
>* Als de AEM Forms-server traag werkt, zelfs nadat de voorgestelde mappen zijn uitgesloten, sluit u ook het uitvoerbare bestand van Java™ (java.exe) uit.
>
