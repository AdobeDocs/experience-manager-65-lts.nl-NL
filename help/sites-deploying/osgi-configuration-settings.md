---
title: OSGi-configuratie-instellingen
description: Dit artikel detailleert de OSGi configuratiemontages (die volgens bundel worden vermeld) die voor projectimplementatie relevant zijn. De lijst dient als richtsnoer en is niet limitatief.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: configuring
content-type: reference
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: d3356f5f-f80f-4ce0-b4e2-3ee927208ab1
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '3247'
ht-degree: 0%

---

# OSGi-configuratie-instellingen{#osgi-configuration-settings}

[&#x200B; OSGi &#x200B;](https://www.osgi.org/) is een fundamenteel element in de technologiestapel van AEM. Het wordt gebruikt om de samengestelde bundels van AEM en hun configuratie te controleren.

OSGi &quot;*verstrekt de gestandaardiseerde primitieven die toepassingen toestaan om van kleine, herbruikbare, en samenwerkingscomponenten worden geconstrueerd. Deze componenten kunnen in een toepassing worden samengesteld en worden opgesteld*&quot;.

Deze functionaliteit maakt eenvoudig beheer van bundels mogelijk, aangezien deze kunnen worden gestopt, geïnstalleerd en afzonderlijk kunnen worden gestart. De onderlinge afhankelijkheden worden automatisch verwerkt. Elke Component OSGi (zie de [&#x200B; Specificatie OSGi &#x200B;](https://docs.osgi.org/specification/)) is bevat in één van de diverse bundels. Wanneer het werken met AEM, zijn er verscheidene methodes om de configuratiemontages voor dergelijke bundels te beheren; zie [&#x200B; Vormend OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor meer details en de geadviseerde praktijken.

De volgende OSGi configuratiemontages (die volgens bundel worden vermeld) zijn relevant voor projectimplementatie. Niet alle instellingen in de lijst hoeven te worden aangepast. Sommige instellingen worden vermeld om te begrijpen hoe AEM werkt.

>[!CAUTION]
>
>De lijst is bedoeld als richtsnoer en is niet limitatief. Niet alle bundels worden vermeld, noch alle parameters voor sommige bundels die zijn.
>
>De noodzakelijke configuratie varieert van project tot project.
>
>Zie de console van het Web voor gebruikte waarden en gedetailleerde informatie over parameters.

>[!NOTE]
>
>Voor specifieke functiegebieden in AEM kunnen verdere bundels vereist zijn. In deze gevallen vindt u configuratiegegevens op de pagina die betrekking heeft op de juiste functionaliteit.

**de Listener van de Gebeurtenis van de Replicatie van AEM** vormt:

* De **Wijzen van de Looppas**, waarin de replicatiegebeurtenissen aan luisteraars worden verdeeld. Bijvoorbeeld, als bepaald als auteur, is het systeem dat de replicatie &quot;initieert&quot;.

* Voeg de looppas wijze **toe publiceert** als de projectcode replicatiegebeurtenissen (omgekeerde replicatie) in publiceert milieu verwerkt. Bijvoorbeeld wanneer de Dispatcher wordt gebruikt om van het publicatiemilieu te spoelen of wanneer de standaardreplicatie aan andere publicatieinstanties voorkomt.

**de veranderingsluisteraar van de Bewaarplaats van AEM** vormt:

* De **Wegen**, plaatsen om op bewaarplaatgebeurtenissen klaar voor distributie te luisteren.

**CRX Sling Client Repository** vormt toegang tot de onderliggende inhoudsbewaarplaats.

* Het **Wachtwoord Admin** zou na installatie moeten worden veranderd om de [&#x200B; veiligheid &#x200B;](/help/sites-administering/security-checklist.md) van uw instantie te verzekeren.
* Andere wijzigingen zouden niet nodig moeten zijn en er moet zorgvuldig op worden gelet dat ze de toegang tot de opslagplaats kunnen beïnvloeden.

**Apache Felix OSGi de Console van het Beheer** vormt:

* **Insteekmodules**, de belangrijkste navigatiepunten (consolestoppen) om in de **Console van het Beheer van het Web van de Felix van Apache** als top-level menupunten beschikbaar te zijn. Schakel een optie uit die u niet nodig hebt omdat voor elke optie ruimte en bronnen vereist zijn.

>[!CAUTION]
>
>Ben zeker om het volgende te vormen:
>
>**Naam van de Gebruiker** en **Wachtwoord**, de geloofsbrieven voor de toegang tot van de Console van het Beheer van het Web van de Felix van Apache zelf.
>Het wachtwoord moet na de aanvankelijke installatie worden veranderd om de [&#x200B; veiligheid &#x200B;](/help/sites-administering/security-checklist.md) van uw instantie te verzekeren.

>[!NOTE]
>
>Deze configuratie moet worden gemaakt met de Felix Console zoals dat bij het opstarten nodig is - voordat de opslagplaats beschikbaar is.

**Apache die Aanpasbare Logger van de Gegevens van het Verzoek plaatst** vormt:

* **de Naam van het Logboek** en **Formaat van het Logboek** om de plaats en het formaat van verzoek en toegangsregistreren (gebrek: `request.log`) te vormen. Dit logbestand is van essentieel belang voor het analyseren van de prestaties of foutopsporingsfunctionaliteit in verband met de webketen. Het is met [&#x200B; Apache Sling Logger van het Verzoek &#x200B;](#apacheslingrequestlogger) in paren gerangschikt.

Zie [&#x200B; het Registreren van AEM &#x200B;](/help/sites-deploying/configure-logging.md) en [&#x200B; het Sling Registreren &#x200B;](https://sling.apache.org/documentation/development/logging.html).

**Apache die de Groep van de Verbindingsdraad** vormt:

* **Min de Grootte van de Pool** en **Max de Grootte van de Pool**, de grootte van de pool die wordt gebruikt om gebeurtenisdraden te houden.

* **de Grootte van de Rij**, de maximumgrootte van de draadrij als de pool uitgeput is.
De aanbevolen waarde is `-1` omdat de wachtrij op onbeperkt wordt ingesteld. Als een limiet wordt vastgesteld, kunnen verliezen optreden wanneer deze worden overschreden.

* Het wijzigen van deze instellingen kan de prestaties in scenario&#39;s met een groot aantal gebeurtenissen ten goede komen. Bijvoorbeeld zwaar AEM DAM- of workflowgebruik.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Deze instellingen kunnen van invloed zijn op de prestaties van uw instantie. Wijzig deze instellingen dus niet zonder reden en met gepaste aandacht.

**Apache Sling GET Servlet** vormt sommige aspecten van het teruggeven:

* **AutoIndex** om folder het teruggeven voor het doorbladeren toe te laten/onbruikbaar te maken.
* **laat** toe (of maak) standaardvertoningen onbruikbaar, zoals **HTML**, **Onbewerkte Tekst**, **JSON**, of **XML**.
Schakel JSON niet uit.

>[!NOTE]
>
>Dit het plaatsen wordt automatisch gevormd voor productieinstanties als u AEM in [&#x200B; Productie Klaar Wijze &#x200B;](/help/sites-administering/production-ready.md) in werking stelt.

**Apache het Verdelen de Handler van het Manuscript van Java** vormt montages voor de compilatie van.java- dossiers als manuscripten (servlets).

Bepaalde instellingen kunnen van invloed zijn op de prestaties. Schakel deze instellingen waar mogelijk uit, met name voor een productie-instantie.

* **VM van Source VM** en **Doel VM**, bepaal de versie JDK die als runtime JVM wordt gebruikt

* voor productiegevallen:

   * maak **onbruikbaar produceren zuivert Info**

**Apache die de Installateur van JCR Sling** Deze parameters vergen waarschijnlijk geen configuratie, maar kunnen nuttig zijn om te weten wanneer het ontwikkelen of het zuiveren. De installatiemappen kunnen bijvoorbeeld handig zijn om in of uit te checken of om een pakket te maken.

* **de omslagen van de Installatie naam regexp** en **Max hiërarchiediepte van installeert omslagen** - specificeer waar, en aan welke diepte, bewaarplaatsomslagen worden gezocht naar middelen om worden geïnstalleerd. Wanneer een jokerteken wordt gebruikt (zoals in.&#42;/install) alle overeenkomende items worden doorzocht, bijvoorbeeld `/libs/sling/install` en `/libs/cq/core/install` .

* **Weg van het Onderzoek**, lijst van wegen die jcrinstall zoekt naar te installeren middelen, samen met een aantal die op de wegingsfactor voor die weg wijzen.

**Apache die de Configuratie van de Rij van de Rij** vormt parameters die baan het plannen beheren:

* **probeert opnieuw interval**, **Maximum probeert**, **Maximum Parallelle Banen**, onder anderen.

* Als u deze instellingen wijzigt, worden de prestaties verbeterd in scenario&#39;s met een groot aantal taken, zoals een intensief gebruik van AEM DAM en Workflows.
* De waarden specifiek voor uw scenario zouden moeten worden bepaald gebruikend tests.
* Wijzig deze instellingen niet zonder reden en pas na zorgvuldige afweging aan.

**Apache het Schrapen JSP de Handler van het Manuscript** vormt prestaties relevante montages voor de JSP manuscriptmanager. Om de prestaties te verbeteren, zou u zoveel mogelijk onbruikbaar moeten maken.

Met name voor productiegevallen:

* maak **onbruikbaar produceren zuivert Info**
* maak **Gegenereerde Java™** onbruikbaar houden
* maak **Toegewezen Inhoud** onbruikbaar
* maak **de Fragmenten van Source van de Vertoning** onbruikbaar

>[!NOTE]
>
>Dit het plaatsen wordt automatisch gevormd voor productieinstanties als u AEM in [&#x200B; Productie Klaar Wijze &#x200B;](/help/sites-administering/production-ready.md) in werking stelt.

**Apache die Logging Configuratie** vormt:

* **Niveau van het Logboek** en **Dossier van het Logboek**, om de plaats en het logboekniveau van de centrale registrerenconfiguratie (error.log) te bepalen. Het niveau kan worden ingesteld op een van de volgende waarden: `DEBUG` , `INFO` , `WARN` , `ERROR` en `FATAL` .

* **Aantal de Dossiers van het Logboek** en **Drempel van het Dossier van het Logboek** om de grootte en versieomwenteling van het logboekdossier te bepalen.

* **Patroon van het Bericht** bepaalt het formaat van de logboekberichten.

Zie [&#x200B; het Registreren van AEM &#x200B;](/help/sites-deploying/configure-logging.md#global-logging) en [&#x200B; het Sling Registreren &#x200B;](https://sling.apache.org/documentation/development/logging.html).

**Apache het Verdelen Logboekconfiguratie van het Logboekregistratie (de Configuratie van de Fabriek)** vormt:

* **Niveau van het Logboek**, **Dossier van het Logboek** en **Formaat van het Bericht** om details van het logboekdossier en berichten te bepalen.

* **Logger** om de categorie te bepalen; bijvoorbeeld, slechts logboek voor com.day.cq.

* Door **de Configuraties van de Fabriek te gebruiken**, kan om het even welk aantal extra configuraties worden toegevoegd om met de diverse vereiste logboekniveaus en categorieën te behandelen.
* Dergelijke configuraties zijn nuttig tijdens ontwikkeling; bijvoorbeeld, om de berichten van TRACE voor de specifieke dienst in een specifiek logboekdossier te registreren.
* Dergelijke configuraties zijn nuttig in een productiemilieu; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [&#x200B; het Registreren van AEM &#x200B;](/help/sites-deploying/configure-logging.md) en [&#x200B; het Sling Registreren &#x200B;](https://sling.apache.org/documentation/development/logging.html).

**Apache het Verdelen de Configuratie van de Schrijver van de Registratie (de Configuratie van de Fabriek)** vormt:

* **Dossier van het Logboek** om het bestaan van een logboekdossier te bepalen.
* **Aantal Dossiers van het Logboek** om de versieomwenteling te bepalen.

* De schrijver kan door een **Apache Sling Logging Logger configuratie** worden gebruikt.

* Dergelijke configuraties zijn nuttig tijdens ontwikkeling; bijvoorbeeld, om de berichten van TRACE voor de specifieke dienst in een specifiek logboekdossier te registreren.
* Dergelijke configuraties zijn nuttig in een productiemilieu; bijvoorbeeld, om berichten over de specifieke dienst te hebben die aan een individueel logboekdossier voor gemakkelijkere controle wordt geregistreerd.

Zie [&#x200B; het Registreren van AEM &#x200B;](/help/sites-deploying/configure-logging.md) en [&#x200B; het Sling Registreren &#x200B;](https://sling.apache.org/documentation/development/logging.html).

**Apache die HoofdServlet** vormt:

* **Aantal Vraag per Verzoek** en **Diepte van de Recursie** om uw systeem tegen oneindige recursie en bovenmatige manuscriptvraag te beschermen.

**Apache Sling Commons MIME de Dienst van het Type** vormt:

* **types MIME** om types toe te voegen die door uw project aan het systeem worden vereist. Hierdoor kan een `GET` -aanvraag in een bestand de juiste header van het inhoudstype instellen voor het koppelen van het bestandstype en de toepassing.

**de Filter van de Verwijzer van de Verkoper van Apache** om bekende veiligheidskwesties met de Serie van het Verzoek van de Verwijzing (CSRF) in CRX WebDAV en Apache te richten die u moet het filter van de Referteur vormen.

De dienst van de verwijzingsfilter is de dienst OSGi die u laat vormen:

* welke http-methoden moeten worden gefilterd
* of een lege verwijzingskoptekst is toegestaan
* en een lijst met servers die naast de serverhost zijn toegestaan.

Zie de [&#x200B; Controlelijst van de Veiligheid - Kwesties met de Versmeding van het Verzoek van de Verkeer van de Verkeer van de Verkeer van de Plaats &#x200B;](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) voor verdere details.

>[!NOTE]
>
>Het filter Apache Sling Referrer is afhankelijk van de installatie van een snel reparatiepakket.

**Logger van het Verzoek van Apache Sling** vormt:

* diverse parameters om te bepalen hoe de verzoeken worden geregistreerd.
* **laat Logboek van het Verzoek** toe, om toe te laten of onbruikbaar te maken.

* **laat Logboek van de Toegang** toe, om toe te laten of onbruikbaar te maken.

Gepaureerd met [&#x200B; Apache Sling Aanpasbare Logger van de Gegevens van het Verzoek &#x200B;](#apacheslingcustomizablerequestdatalogger).

Zie [&#x200B; het Registreren van AEM &#x200B;](/help/sites-deploying/configure-logging.md) en [&#x200B; het Sling Registreren &#x200B;](https://sling.apache.org/documentation/development/logging.html).

**Apache het Verdelen van de Factory van de Resolver van het Middel** vormt centrale aspecten van het Verdelen van middelresolutie:

* **Wegen van het Onderzoek van het Middel**, voeg om het even welke project-specifieke wegen toe (maar verwijder niet `/libs` of `/apps`).

* **Virtuele URLs** om uw ijdelheid in kaart te brengen URL.

* **Mappings URL** om het even welke aliassen te bepalen. Bijvoorbeeld van `/content` tot `/` .

* **de Plaats van de Toewijzing**, de mapconfiguratie die in `/etc/map` wordt geexternaliseerd.

* Gebruik uw lokale installatie (bijvoorbeeld gebruik `https://localhost:4502/system/console/jcrresolver`) om te bepalen welke Resolver van Middel actief is.

Zie: [&#x200B; https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution &#x200B;](https://cwiki.apache.org/confluence/display/SLING/Flexible+Resource+Resolution).

>[!CAUTION]
>
>Configureer deze opties in de opslagplaats.
>
>Anders, zouden de veranderingen die aan **worden aangebracht Toewijzingen URL** gebruikend de console van Felix door AEM op het volgende opstarten kunnen worden beschreven.

**Apache Sling Servlet/de Besloeiing van het Manuscript en de Handler van de Fout** Servlet Sling en de Besloeiing van het Manuscript heeft veelvoudige taken:

1. Deze wordt gebruikt als de `ServletResolver` om de Servlet of het Manuscript te selecteren om de aanvraag af te handelen.

1. Deze fungeert als de `SlingScriptResolver` .

1. Het beheert foutafhandeling door de `ErrorHandler` -interface te implementeren met hetzelfde algoritme om foutafhandelingsservlets en scripts te selecteren die worden gebruikt om aanvraagverwerkingsservlets en scripts op te lossen.

Er kunnen verschillende parameters worden ingesteld, waaronder:

* **de Wegen van de Uitvoering** - maakt een lijst van de wegen aan onderzoek naar uitvoerbare manuscripten. Door specifieke paden te configureren, kunt u beperken welke scripts kunnen worden uitgevoerd. Als geen weg wordt gevormd, dan wordt het gebrek gebruikt ( `/` = wortel), toestaand het lopen van alle manuscripten.
Als een gevormde wegwaarde met een schuine streep beëindigt, wordt de volledige subboom gezocht. Zonder een dergelijke slash wordt het script alleen uitgevoerd als het exact overeenkomt.

* **StandaardUitbreidingen** - de lijst van uitbreidingen waarvoor het standaardgedrag wordt gebruikt. Het laatste wegsegment van het middeltype kan als manuscriptnaam worden gebruikt.

**de Configuratie van de Volmacht van de Volmacht van HTTP van Apache** - de volmachtsconfiguratie voor alle code die de cliënt van HTTP Apache gebruikt, wordt gebruikt wanneer HTTP wordt gemaakt. Bijvoorbeeld bij replicatie.

Wijzig de fabrieksconfiguratie niet wanneer u een configuratie maakt. In plaats daarvan, creeer een fabrieksconfiguratie voor deze component gebruikend de hier beschikbare configuratiemanager: **https://localhost:4502/system/console/configMgr/**. De volmachtsconfiguratie is beschikbaar in **org.apache.http.proxyconfigurator.**

**Adobe Granite HTML Library Manager** vormt om de behandeling van cliëntbibliotheken (css of js) met inbegrip van te controleren, bijvoorbeeld, hoe de onderliggende structuur wordt gezien.

* Voor productiegevallen:

   * laat **toe Minify** (om CRLF en whitespace karakters te verwijderen).
   * laat **Gzip** toe (om dossiers toe te staan om met één verzoek worden gecomprimeerd en worden betreden).
   * maak **Debug** onbruikbaar
   * maak **Timing** onbruikbaar

* Voor JS-ontwikkeling (vooral bij foutopsporing/foutopsporing):

   * maak **onbruikbaar**
   * laat **Debug** toe om de dossiers voor het zuiveren en gebruik met brand te scheiden insect.
   * laat **Timing** toe als geinteresseerd in timing.
   * laat **toe zuivert** console om JS te zien console logboekberichten.

>[!CAUTION]
>
>Wanneer het veranderen van het plaatsen voor of **&#x200B;**&#x200B;of **Gzip**, schrap de inhoud van cliëntlibgeheime voorgeheugen. Zie [&#x200B; artikel van de Kennisbank &#x200B;](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-16543.html?lang=nl-NL) voor details.

>[!NOTE]
>
>Dit het plaatsen wordt automatisch gevormd voor productieinstanties als u AEM in [&#x200B; Productie Klaar Wijze &#x200B;](/help/sites-administering/production-ready.md) in werking stelt.

**Adobe Granite HTTP Handler van de Authentificatie van de Kopbal** de montages van de systeembrede voor de basisauthentificatiemethode van het HTTP- verzoek.

Wanneer het gebruiken van [&#x200B; gesloten gebruikersgroepen &#x200B;](/help/sites-administering/cug.md), kunt u, onder anderen, het volgende vormen:

* **Uitspraak van HTTP**
* De **Standaard Login Pagina**

**Controle van de Dienst van de Controle van de Verbinding van 0&rbrace; Dag CQ en indien nodig vormen:**

* **de Periode van de Planner** om het interval te bepalen waarbij de externe verbindingen automatisch moeten worden gecontroleerd.

* Controle **het Onjuiste Interval van de Tolerantie van de Verbinding** voor de periode waarna een onsuccesvolle externe verbinding als slecht wordt beschouwd.
* **de Patronen van de Overschrijving van de Controle van de Verbinding**, om het even welke wegen te bepalen die van verbinding het controleren moeten worden uitgesloten.

**CQ van de Verbinding van de Dag CQ Taak** vormt montages voor één enkele taak van de verbindingscontroleur (een taak die een externe verbinding controleert):

* Controle de intervallen die in **worden bepaald het Interval van de Test van de Verbinding 1&rbrace; en** het Onjuiste Interval van de Test van de Verbinding **&#x200B;**

* De verschillende parameters met betrekking tot proxy&#39;s voor internettoegang en NTLM die nodig zijn voor externe toegang bij het controleren van een koppeling.

**Vorm hostname en toegangsdetails voor de postserver van de Dag CQ.** Zie het Vormen de sectie van de Dienst van de Post.

**Dag CQ MCM- Bulletin** vormt de diverse montages die met nieuwsbrief worden gebruikt.

**vormt de Toewijzing van de Wortel van 0&rbrace; Dag CQ:**

* **Weg van het Doel** om te bepalen waar een verzoek aan &quot; `/`&quot;wordt opnieuw gericht aan.

Er zijn twee gebruikersinterface beschikbaar in AEM:

* de interface met aanraakbediening is de standaardinterface
* en de verouderde klassieke interface nog volledig operationeel is

Met AEM Root Mapping kunt u de gebruikersinterface configureren die u als standaard voor uw instantie wilt gebruiken:

* Om aanraking-toegelaten UI als gebrek UI te hebben, zou het **Weg van het Doel** aan het volgende moeten richten:

  ```shell
     /projects.html
  ```

* Om klassieke UI als gebrek UI te hebben, zou het **Weg van het Doel** aan het volgende moeten richten:

  ```shell
     /welcome.html
  ```

>[!NOTE]
>
>Op een standaardinstallatie is de interface met geoptimaliseerde aanrakingen de standaardinterface.

**Adobe Granite SSO de Handler van de Authentificatie** - vorm SSO (Enige Sign On) details. Deze gegevens zijn vaak nodig in instellingen van de auteur van een bedrijf, vaak met LDAP.

Er zijn verschillende configuratie-eigenschappen beschikbaar:

* **Weg**
Het pad waarvoor deze verificatiehandler actief is. Als deze parameter leeg wordt gelaten, wordt de authentificatiemanager onbruikbaar gemaakt. Het pad/zorgt er bijvoorbeeld voor dat de verificatiehandler wordt gebruikt voor de gehele gegevensopslagruimte.

* **Rangschikking van de Dienst**
OSGi de Rangschikkende waarde van de Dienst van het Kader wordt gebruikt om op de orde te wijzen die voor het roepen van deze dienst wordt gebruikt. Deze waarde is een `int` -waarde waarbij hogere waarden een hogere prioriteit aangeven.
De standaardwaarde is `0` .

* **de Namen van de Kopbal**
De namen van kopteksten die een gebruikers-id kunnen bevatten.

* **Namen van het Koekje**
De namen van cookies die een gebruikers-id kunnen bevatten.

* **Namen van de Parameter**
De namen van aanvraagparameters die de gebruikers-id kunnen verstrekken.

* **Kaart van de Gebruiker**
Voor geselecteerde gebruikers kan de gebruikersnaam die uit de HTTP-aanvraag is geëxtraheerd, worden vervangen door een andere naam in het object credentials. De toewijzing wordt hier gedefinieerd. Als de gebruikersnaam `admin` aan weerszijden van de kaart wordt weergegeven, wordt de toewijzing genegeerd. Aan het teken &quot;=&quot; moet een regelafstand &quot;\&quot; worden toegevoegd.

* **Formaat**
Hiermee geeft u de indeling aan waarin de gebruikers-id wordt opgegeven. Gebruik:

   * `Basic` als de gebruikers-id is gecodeerd in de indeling HTTP Basic Authentication.
   * `AsIs` als de gebruiker-id wordt opgegeven in onbewerkte tekst of als een toegepaste waarde voor een reguliere expressie moet worden gebruikt zoals deze of een reguliere expressie

**Eind CQ WCM zuivert Filter** Dit is nuttig wanneer het ontwikkelen aangezien het het gebruik van achtervoegsels zoals ?debug=layout wanneer het toegang tot van een pagina toestaat. Bijvoorbeeld, verstrekt https://localhost:4502/cf#/content/geometrixx/en/support.html?debug=layout lay-outinformatie die van belang voor de ontwikkelaar kan zijn.

* Schakel apparaten uit om prestaties en beveiliging te garanderen.

**De Filter van WCM van de Dag CQ WCM** vormt:

* **Wijze WCM** om de standaardwijze te bepalen.
* Op een auteurinstantie, zou deze wijze `edit`, `disable,preview`, of `analytics` kunnen zijn.
De andere modi zijn toegankelijk via het zijpaneel of het achtervoegsel `?wcmmode=disabled` kan worden gebruikt om een productieomgeving te emuleren.

* Op een publicatie-instantie moet deze modus zijn ingesteld op `disabled` om ervoor te zorgen dat er geen andere modus toegankelijk is.

>[!NOTE]
>
>Dit het plaatsen wordt automatisch gevormd voor productieinstanties als u AEM in [&#x200B; Productie Klaar Wijze &#x200B;](/help/sites-administering/production-ready.md) in werking stelt.

**dag CQ WCM de Controle van de Verbinding van WCM** vormt:

* **Lijst van herschrijven configuraties** om een lijst van plaatsen voor op inhoud-gebaseerde configuraties van de verbindingscontrole te specificeren. De configuraties kunnen op looppaswijze worden gebaseerd. Dit is belangrijk om onderscheid te maken tussen auteur- en publicatieomgevingen, omdat de instellingen voor koppelingencontrole kunnen verschillen.

**vormt de Factory van de Manager van de Pagina WCM van 0&rbrace; Dag CQ:**

* **Controle van de Activering van de Subboom van de Pagina** voor een gebruiker (zonder replicatiemachtigingen) om pagina&#39;s te schrappen of te bewegen (zelfs als de pagina&#39;s niet worden geactiveerd).

**Vorm van de Bewerker van de Pagina van 0&rbrace; Dag CQ WCM:**

* **Wegen**, een lijst van plaatsen waar het systeem op paginawijzigingen alvorens a `jcr:Event` te teweegbrengen luistert.

**Beheer van de Indrukking van de Pagina van Adobe** voor een auteursinstantie, vorm als het volgende:

* **sling.auth.requirements**: plaats de waarde van dit bezit aan `-/libs/wcm/stats/tracker`

>[!CAUTION]
>
>Deze configuratie staat anonieme verzoeken aan de volgende dienst toe.

>[!NOTE]
>
>Zie [&#x200B; de Indrukking van de Pagina &#x200B;](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**CQ van de Dag CQ de Statistieken van de Pagina WCM** voor publiceer instantie vormen:

* **URL om gegevens** te verzenden om URL te vormen die aan de statistieken van de spoorpagina wordt gebruikt (is essentieel als een trackerverzoek door Dispatcher) gaat; bijvoorbeeld, is het gebrek `https://localhost:4502/libs/wcm/stats/tracker`.

* **het Volgen toegelaten manuscript** om ( `true`) toe te laten of ( `false`) onbruikbaar te maken de opneming van het volgende manuscript op de pagina&#39;s. De standaardwaarde is `false` .

>[!NOTE]
>
>Zie [&#x200B; de Indrukking van de Pagina &#x200B;](/help/sites-deploying/configuring.md#enabling-page-impressions) voor meer informatie.

**Controle van de Manager van de Versie van WCM van 0&rbrace; Dag CQ WCM als, en hoe, de versies in uw systeem worden beheerd:**

* **creeer Versie op Activering**, die in een standaardinstallatie wordt toegelaten
* **laat het Opschonen** toe

* **Wis Wegen**, de wegen die een onderzoeksactie zoekt.
* **impliciete Versioning Wegen**, de wegen waar het impliciete versioning actief is.

* **Max de Leeftijd van de Versie**, de maximumleeftijd (in dagen) van een versie

* **Max de Versies van het Aantal**, het maximumaantal versies om te houden

Zie [&#128279;](/help/sites-deploying/version-purging.md) het Opheffen van de Versie 0&rbrace; &lbrace;voor meer informatie.

**de Dienst van het Bericht van het E-mail van het Werkschema van de Dag CQ** vormt de e-mailmontages voor berichten die door een werkschema worden verzonden.

**Adobe AEM Rewriter HTML Parser Factory**

Controls the HTML Parser for the CQ rewriter.

* **Extra Markeringen aan Proces** - u kunt de markeringen van HTML toevoegen of verwijderen die door de parser moeten worden verwerkt. Standaard worden de volgende tags verwerkt: A,IMG,AREA,FORM,BASE,LINK,SCRIPT,BODY,HEAD.
* **Behoud het Geval van de Camel** - Door gebrek, zet de parser van HTML attributen in camel geval (bijvoorbeeld, `eBay`) in kleine letters (bijvoorbeeld, `ebay`) om. U kunt deze instelling uitschakelen om de kenmerken van het camerahoofdlettergebruik te behouden. Deze instelling is handig wanneer u frontend-frameworks zoals Angular 2 gebruikt.

**vormt de Groep van Verbindingen JDBC van de Commons van de Dag toegang tot een extern gegevensbestand dat als bron voor inhoud wordt gebruikt.**

Een Configuratie van de Fabriek, zodat kunnen de veelvoudige instanties worden gevormd.

**CDN herschrijver** Communicatie tussen AEM en een CDN moet worden gewaarborgd zodat de activa/binaire getallen aan een eind - gebruiker op een veilige manier worden geleverd. Dit proces omvat de volgende twee taken:

* De eerste keer dat de bron via de CDN wordt benaderd vanuit AEM (of nadat deze in cache is verlopen).
* Toegang tot het middel caching in CDN veilig. Nadat het middel in CDN in het voorgeheugen wordt opgeslagen, gaat het verzoek niet naar AEM, en alle gebruikers die toegang tot dat middel hebben zouden van CDN moeten worden gediend.

AEM biedt een rewriter voor het herschrijven van interne elementen-URL&#39;s naar externe CDN-URL&#39;s. Het herschrijft verbindingen die tot CDN met inbegrip van een handtekening JWS moeten worden overgegaan en verloopt tijd om de activa toe te staan om veilig worden betreden. Deze functie moet worden gebruikt op auteur-instanties.

De totale stroom is als volgt:

1. De gebruiker verklaart zich bij AEM voor en vraagt om een pagina met activa.
1. Aangevraagde pagina bevat een element dat lijkt op `/content/dam/geometrixx-media/articles/paladin_trailer.jpg/jcr:content/renditions/cq5dam.thumbnail.319.319.png`
1. Rewriter transformeert de koppeling naar een CDN-URL die een JWS-handtekening bevat:
   `CDN_domain/content/dam/geometrixx-media/articles/paladin_trailer.jpg/_jcr_content/renditions/cq5dam.thumbnail.319.319.png?cdn_sign=JWS_SIGNATURE`

1. De browser van de gebruiker stuurt het elementverzoek vervolgens door naar de CDN-server
1. CDN moet zo worden geconfigureerd dat de aanvraag samen met de parameter `cdn_sign` naar AEM wordt doorgestuurd.
1. Een verificatiehandler valideert de parameter `cdn_sign` en retourneert het element naar de CDN die vervolgens aan de gebruiker wordt geleverd

De stroom tussen browser van de gebruiker, CDN, en AEM kan als volgt worden visualiseerd.

![&#x200B; chlimage_1-8 &#x200B;](assets/chlimage_1-8.png)

>[!NOTE]
>
>Deze functie is alleen ingeschakeld voor auteur-instanties van AEM.

**CDNConfigServiceImpl** verstrekt CDN configuraties

CDN die eigenschap herschrijven kan worden toegelaten door **CDN naam van het distributiedomein** in de configuratie voor com.adobe.cq.cdn.rewriter.impl.CDNConfigServiceImpl te verstrekken.

De service bevat ook andere configuratieopties, zoals het opnieuw schrijven van CDN in- en uitschakelen, padvoorvoegsels waarvoor CDN wordt herschreven, TTL-waarden en protocol (HTTP of HTTPS).

**CDNRewriter** opnieuw schrijver voor het herschrijven van interne beeld URLs aan CDN URLs

De **waarde van de Attributen van de Markering** in com.adobe.cq.cdn.rewriter.impl.CDNRewriter kan worden bepaald zodat slechts de selectieve beeldverbindingen worden herschreven.
