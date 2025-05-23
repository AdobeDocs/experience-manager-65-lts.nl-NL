---
title: Integreren met Adobe Dynamic Tag Management
description: Leer meer over integratie met Adobe Dynamic Tag Management.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 8bf470d5-1824-41d6-80e4-4af1eb6df713
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2146'
ht-degree: 0%

---

# Integreren met Adobe Dynamic Tag Management {#integrating-with-adobe-dynamic-tag-management}

Integreer [ Dynamische Tag Management van Adobe ](https://business.adobe.com/products/experience-platform/adobe-experience-platform.html) met AEM zodat u uw Dynamische het Webeigenschappen van Tag Management kunt gebruiken om de plaatsen van AEM te volgen. Met Dynamic Tag Management kunnen marketers tags beheren voor het verzamelen van gegevens en gegevens verspreiden over digitale marketingsystemen. Gebruik bijvoorbeeld Dynamic Tag Management om gebruiksgegevens voor uw AEM-website te verzamelen en de gegevens voor analyse te verspreiden in Adobe Analytics of Adobe Target.

Alvorens u integreert, creeer het Dynamische Tag Management [ Webbezit ](https://microsite.omniture.com/t2/help/en_US/dtm/#Web_Properties) dat het domein van uw plaats van AEM volgt. [ het ontvangen opties ](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) van het Webbezit moeten worden gevormd zodat u AEM kunt vormen om tot de Dynamische bibliotheken van Tag Management toegang te hebben.

Nadat u de integratie hebt geconfigureerd, vereisen wijzigingen in de hulpmiddelen en regels voor dynamische Tag Management-implementatie niet dat u de configuratie van Dynamic Tag Management in AEM wijzigt. De wijzigingen zijn automatisch beschikbaar voor AEM.

>[!NOTE]
>
>Als u DTM met een configuratie van de douanevolmacht gebruikt, vorm zowel de volmachtsconfiguraties van de Cliënt van HTTP aangezien sommige functionaliteiten van AEM 3.x APIs en sommige anderen 4.x APIs gebruiken:
>
>* 3.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt gevormd met [ http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

## Implementatieopties {#deployment-options}

De volgende plaatsingsopties beïnvloeden de configuratie van de integratie met Dynamische Tag Management.

### Dynamic Tag Management Hosting {#dynamic-tag-management-hosting}

AEM ondersteunt Dynamic Tag Management die wordt gehost in de cloud of wordt gehost op AEM.

* In de cloud gehoste: de Dynamic Tag Management JavaScript-bibliotheken worden opgeslagen in de cloud en uw AEM-pagina&#39;s verwijzen er rechtstreeks naar.
* AEM-gehost: Dynamic Tag Management genereert JavaScript-bibliotheken. AEM gebruikt een workflowmodel voor het ophalen en installeren van de bibliotheken.

Het type van het ontvangen dat uw implementatie gebruikt bepaalt enkele configuratie en implementatietaken die u uitvoert. Voor informatie over de het ontvangen opties, zie [ ontvangen - bed Lusje ](https://microsite.omniture.com/t2/help/en_US/dtm/#Hosting__Embed_Tab) in Dynamische Hulp van Tag Management in.

### Staging- en productiebibliotheek {#staging-and-production-library}

Bepaal of uw AEM-auteurinstantie de dynamische Tag Management-staging- of productiecode gebruikt.

Meestal gebruikt de instantie van uw auteur de staging-bibliotheken van Dynamic Tag Management en gebruikt de instantie van de productie de productiebibliotheken. In dit scenario kunt u de auteurinstantie gebruiken om niet-goedgekeurde dynamische Tag Management-configuraties te testen.

Indien gewenst, kan uw auteurinstantie de productiebibliotheken gebruiken. De browser van het Web plugins zijn beschikbaar die u toelaten om tussen het gebruik van het opvoeren bibliotheken voor testende doeleinden te schakelen wanneer de bibliotheken wolk-ontvangen zijn.

### De Dynamic Tag Management Deployment Hook gebruiken {#using-the-dynamic-tag-management-deployment-hook}

Wanneer AEM de Dynamic Tag Management-bibliotheken host, kunt u de Dynamic Tag Management-implementatiehakenservice gebruiken om bibliotheekupdates automatisch door te sturen naar AEM. De bibliotheekupdates worden geduwd wanneer de veranderingen in de bibliotheken zoals worden aangebracht wanneer de Dynamische eigenschappen van het Web van Tag Management worden uitgegeven.

Dynamic Tag Management moet verbinding kunnen maken met de AEM-instantie die de bibliotheken host. [ laat toegang tot AEM ](/help/sites-administering/dtm.md#enabling-access-for-the-deployment-hook-service) voor de Dynamische servers van Tag Management toe.

In sommige gevallen kan AEM onbereikbaar zijn, bijvoorbeeld wanneer AEM zich achter een firewall bevindt. In deze gevallen kunt u de opiniepeilingimporteroptie voor AEM gebruiken om de bibliotheken regelmatig op te halen. Een uitsnijdtaakexpressie schrijft het programma voor het downloaden van bibliotheken voor.

## Toelatend Toegang voor de Dienst van Hook van de Plaatsing {#enabling-access-for-the-deployment-hook-service}

Schakel de Dynamic Tag Management-implementatiehakenservice in om toegang te krijgen tot AEM, zodat de service de op AEM gehoste bibliotheken kan bijwerken. Geef het IP-adres op van Dynamic Tag Management-servers die de staging- en productiebibliotheken naar wens bijwerken:

* Staging: `107.21.99.31`
* Productie: `23.23.225.112` en `204.236.240.48`

Voer de configuratie uit gebruikend of de [ Console van het Web ](/help/sites-deploying/configuring-osgi.md#osgi-configuration-with-the-web-console) of a [`sling:OsgiConfig`](/help/sites-deploying/configuring-osgi.md#osgi-configuration-in-the-repository) knoop:

* In de Console van het Web, gebruik het punt van de Configuratie van het Hook van de Distributie van Adobe DTM op de pagina van de Configuratie.
* Voor een configuratie OSGi, is de dienst PID `com.adobe.cq.dtm.impl.servlets.DTMDeployHookServlet`.

In de volgende tabel worden de eigenschappen beschreven die moeten worden geconfigureerd.

| Webconsole, eigenschap | OSGi, eigenschap | Beschrijving |
|---|---|---|
| DTM IP-witte lijst opslaan | `dtm.staging.ip.whitelist` | Het IP-adres van de Dynamic Tag Management-server die de testbibliotheken bijwerkt. |
| Productie DTM IP witte lijst | `dtm.production.ip.whitelist` | Het IP-adres van de Dynamic Tag Management-server die de productiebibliotheken bijwerkt. |

## De dynamische Tag Management-configuratie maken {#creating-the-dynamic-tag-management-configuration}

Maak een wolkenconfiguratie zodat de AEM-instantie kan worden geverifieerd met Dynamic Tag Management en kan communiceren met uw webeigenschap.

>[!NOTE]
>
>Vermijd de opneming van twee het volgen van Adobe Analytics codes op uw pagina&#39;s wanneer uw DTM Webbezit het hulpmiddel van Adobe Analytics omvat en u ook [ Inzicht van de Inhoud ](/help/sites-authoring/content-insights.md) gebruikt. In uw [ configuratie van Adobe Analytics Cloud ](/help/sites-administering/adobeanalytics-connect.md#configuring-the-connection-to-adobe-analytics), selecteer niet het Volgen van de optie van de Code.

### Algemene instellingen {#general-settings}

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>API-token</td>
   <td>De waarde van de eigenschap API Token van uw Dynamic Tag Management-gebruikersaccount. AEM gebruikt deze eigenschap om te verifiëren met Dynamic Tag Management.</td>
  </tr>
  <tr>
   <td>Bedrijf</td>
   <td>Het bedrijf waaraan uw login identiteitskaart wordt geassocieerd.</td>
  </tr>
  <tr>
   <td>Eigenschap</td>
   <td>De naam van de eigenschap Web die u hebt gemaakt voor het beheer van de tags voor uw AEM-site.</td>
  </tr>
  <tr>
   <td>Productiecode opnemen op auteur</td>
   <td><p>Selecteer deze optie zodat de AEM-auteur en -publicatieinstanties de productieversie van de Dynamic Tag Management-bibliotheken gebruiken. </p> <p>Als deze optie niet is geselecteerd, zijn de instellingen voor afspelen van toepassing op de auteurinstantie en zijn de Productie-instellingen van toepassing op de publicatie-instantie.</p> </td>
  </tr>
 </tbody>
</table>

### Eigenschappen voor Zelf hosten - Staging en productie {#self-hosting-properties-staging-and-production}

Met de volgende eigenschappen van de Dynamic Tag Management-configuratie kan AEM de Dynamic Tag Management-bibliotheken hosten. Met deze eigenschappen kan AEM de bibliotheken downloaden en installeren. Desgewenst kunt u de bibliotheken automatisch bijwerken om ervoor te zorgen dat deze de wijzigingen weerspiegelen die zijn aangebracht in de Dynamic Tag Management-beheertoepassing.

Sommige eigenschappen gebruiken waarden die u in het gedeelte Bibliotheek downloaden van het tabblad Insluiten van de dynamische Tag Management-webeigenschap hebt verkregen. Voor informatie, zie [ de Download van de Bibliotheek ](https://microsite.omniture.com/t2/help/en_US/dtm/#Library_Download) in Dynamische Hulp van Tag Management.

>[!NOTE]
>
>Wanneer u de Dynamic Tag Management-bundel op AEM host, moet Bibliotheek downloaden zijn ingeschakeld in Dynamic Tag Management voordat u de configuratie maakt. Akamai moet ook zijn ingeschakeld, omdat Akamai de bibliotheken beschikbaar stelt om te downloaden.

Als u de Dynamic Tag Management-bibliotheken op AEM host, configureert AEM automatisch bepaalde eigenschappen van de webeigenschap op basis van uw configuratie. Zie de beschrijvingen in de volgende lijst.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Zelf hosten gebruiken</td>
   <td>Selecteer deze optie wanneer u het Dynamic Tag Management-bibliotheekbestand in AEM host. Als u deze optie selecteert, worden de andere eigenschappen in deze tabel weergegeven.</td>
  </tr>
  <tr>
   <td>DTM Bundle URL</td>
   <td>De URL die moet worden gebruikt voor het downloaden van de Dynamic Tag Management-bibliotheek. Verkrijg deze waarde van de sectie van Download URLs van de Bibliotheek downloadt pagina van Dynamic Tag Management. Om veiligheidsredenen moet deze waarde handmatig worden geconfigureerd.</td>
  </tr>
  <tr>
   <td>Workflow downloaden</td>
   <td><p>Het workflowmodel voor het downloaden en installeren van de Dynamic Tag Management-bibliotheek. Het standaardmodel is Default DTM Bundle Download. Gebruik dit model tenzij u een aangepast model hebt gemaakt.</p> <p>De standaarddownloadworkflow activeert automatisch de bibliotheken wanneer ze worden gedownload.</p> </td>
  </tr>
  <tr>
   <td>Domeinhint</td>
   <td><p>(Optioneel) Het domein van de AEM-server die als host fungeert voor de Dynamic Tag Management-bibliotheek. Specificeer een waarde zodat kunt u het standaarddomein met voeten treden dat voor de <a href="/help/sites-developing/externalizer.md"> Dienst van de Verbinding van CQ van de Dag CQ </a> wordt gevormd.</p> <p>Wanneer AEM verbinding maakt met Dynamic Tag Management, gebruikt deze waarde om het Staging HTTP Path of het Production HTTP Path van de Library Download-eigenschappen voor de Dynamic Tag Management web-eigenschap te configureren.</p> </td>
  </tr>
  <tr>
   <td>Beveiligde domeintip</td>
   <td><p>(Optioneel) Het domein van de AEM-server die als host fungeert voor de Dynamic Tag Management-bibliotheek via HTTPS. Specificeer een waarde zodat kunt u het standaarddomein met voeten treden dat voor de <a href="/help/sites-developing/externalizer.md"> Dienst van de Verbinding van CQ van de Dag CQ </a> wordt gevormd.</p> <p>Wanneer AEM verbinding maakt met Dynamic Tag Management, gebruikt deze waarde om het Staging HTTPS-pad of het Production HTTPS-pad van de eigenschappen Library Download voor de Dynamic Tag Management-webeigenschap te configureren.</p> </td>
  </tr>
  <tr>
   <td>Gedeeld geheim</td>
   <td><p>(Optioneel) Het gedeelde geheim dat moet worden gebruikt voor het decoderen van de download. Verkrijg deze waarde van het Gedeelde Geheime gebied van de pagina van de Download van de Bibliotheek van Dynamic Tag Management.</p> <p><strong> Nota:</strong> u moet de bibliotheken OpenSSL hebben die op de computer worden geïnstalleerd waar AEM wordt geïnstalleerd zodat AEM de gedownloade bibliotheken kan decrypteren.</p> </td>
  </tr>
  <tr>
   <td>Opiniepeilingimportfunctie inschakelen</td>
   <td><p>(Optioneel) Selecteer deze optie om de Dynamic Tag Management-bibliotheek periodiek te downloaden en installeren om er zeker van te zijn dat u een bijgewerkte versie gebruikt. Als deze optie is ingeschakeld, verzendt Dynamic Tag Management geen HTTP POST-aanvragen naar de URL van Hook implementeren.</p> <p>AEM configureert automatisch de eigenschap Hook-URL distribueren van de eigenschappen voor het downloaden van bibliotheken voor de dynamische Tag Management-webeigenschap. Wanneer geselecteerd, wordt het bezit gevormd zonder waarde. Als deze optie niet is geselecteerd, wordt de eigenschap geconfigureerd met de URL van de configuratie van Dynamic Tag Management.</p> <p>Schakel polling importer in wanneer de Dynamic Tag Management-implementatiehaak geen verbinding kan maken met AEM, bijvoorbeeld wanneer AEM zich achter een firewall bevindt.</p> </td>
  </tr>
  <tr>
   <td>Planningsexpressie</td>
   <td>(Wordt weergegeven en is vereist als Polling Importer inschakelen is geselecteerd.) Een uitsnijdexpressie die bepaalt wanneer de bibliotheken voor dynamisch tagbeheer worden gedownload.</td>
  </tr>
 </tbody>
</table>

![ chlimage_1-352 ](assets/chlimage_1-352.png)

### Hosteigenschappen voor cloud - Staging en productie {#cloud-hosting-properties-staging-and-production}

U configureert de volgende eigenschappen voor uw dynamische Tag Management-configuratie wanneer Dynamic Tag Configuration in de cloud wordt gehost.

<table>
 <tbody>
  <tr>
   <th>Eigenschap</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>Zelf hosten gebruiken</td>
   <td>Schakel deze optie uit als het dynamische Tag Management-bibliotheekbestand wordt gehost in de cloud.</td>
  </tr>
  <tr>
   <td>Koptekstcode</td>
   <td><p>De koptekstcode voor het opvoeren die is verkregen van Dynamic Tag Management voor uw host. Deze waarde wordt automatisch ingevuld wanneer u verbinding maakt met Dynamic Tag Management.</p> <p> Als u de code in Dynamic Tag Management wilt weergeven, klikt u op het tabblad Insluiten en vervolgens op de hostnaam. Vouw de sectie Koptekstcode uit en klik op de code Insluiten kopiëren van de code Insluiten van het werkgebied of het gebied Code insluiten van de productie.</p> </td>
  </tr>
  <tr>
   <td>Voettekstcode</td>
   <td><p>De voettekstcode voor het opvoeren die is verkregen van Dynamic Tag Management voor uw host. Deze waarde wordt automatisch ingevuld wanneer u verbinding maakt met Dynamic Tag Management.</p> <p>Als u de code in Dynamic Tag Management wilt weergeven, klikt u op het tabblad Insluiten en vervolgens op de hostnaam. Vouw de sectie Voettekstcode uit en klik op de sectie Code insluiten kopiëren van de code Insluiten van werkruimte of het gebied Code insluiten van productie.</p> </td>
  </tr>
 </tbody>
</table>

![ chlimage_1-353 ](assets/chlimage_1-353.png)

In de volgende procedure wordt gebruikgemaakt van de geoptimaliseerde interface voor aanrakingen om de integratie met Dynamic Tag Management te configureren.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. In het gebied Dynamic Tag Management wordt een van de volgende koppelingen weergegeven voor het toevoegen van een configuratie:

   * Klik vormen nu als dit de eerste configuratie is die u toevoegt.
   * Klik op Configuraties tonen en klik vervolgens op de koppeling + naast Beschikbare configuraties als er een of meer configuraties zijn gemaakt.

   ![ chlimage_1-354 ](assets/chlimage_1-354.png)

1. Typ een titel voor de configuratie en klik vervolgens op Maken.
1. Voer in het veld API-token de waarde in van de eigenschap API Token van uw Dynamic Tag Management-gebruikersaccount.

   Neem contact op met de DTM Client Care voor de waarde van uw API-token.

   >[!NOTE]
   >
   >Het API-token verloopt pas wanneer de Dynamic Tag Management-gebruiker dit expliciet aanvraagt.

   ![ chlimage_1-355 ](assets/chlimage_1-355.png)

1. Klik op Verbinding maken met DTM. AEM wordt geverifieerd met Dynamic Tag Management en haalt de lijst op van bedrijven waaraan uw account is gekoppeld.
1. Selecteer het Bedrijf, en selecteer dan het Bezit dat u gebruikt om uw plaats van AEM te volgen.
1. Schakel de optie Productiecode opnemen op auteur uit als u code in de opmaakcode gebruikt.
1. Geef indien nodig waarden op voor de eigenschappen op het tabblad Staging-instellingen en het tabblad Productie-instellingen en klik op OK.

## De dynamische Tag Management-bibliotheek handmatig downloaden {#manually-downloading-the-dynamic-tag-management-library}

Download de Dynamic Tag Management-bibliotheken handmatig om deze direct bij te werken op AEM. Download bijvoorbeeld handmatig wanneer u een bijgewerkte bibliotheek wilt testen voordat de pollingimporter is gepland om de bibliotheek automatisch te downloaden.

1. Klik in de track op Gereedschappen > Bewerkingen > Wolk > Cloud Services.
1. Klik in het gedeelte Dynamische Tag Management op Configuraties tonen en klik vervolgens op uw configuratie.
1. Klik in het gebied Instellingen voor staging of Productie-instellingen op de knop Workflow voor downloaden om de bibliotheekbundel te downloaden en implementeren.

   ![ chlimage_1-356 ](assets/chlimage_1-356.png)

>[!NOTE]
>
>De gedownloade bestanden worden opgeslagen onder `/etc/clientlibs/dtm/my config/companyID/propertyID/servertype` .
>
>Het volgende wordt genomen direct van uw [ configuratie DTM ](#creating-the-dynamic-tag-management-configuration).
>
>* `myconfig`
>* `companyID`
>* `propertyID`
>* `servertype`
>

## Een dynamische Tag Management-configuratie koppelen aan uw site {#associating-a-dynamic-tag-management-configuration-with-your-site}

Koppel uw Dynamic Tag Management-configuratie aan de pagina&#39;s van uw website, zodat AEM het vereiste script aan de pagina&#39;s toevoegt. Koppel de hoofdpagina van uw site aan de configuratie. Alle afstammingen van die pagina nemen de koppeling over. Indien nodig, kunt u de vereniging op een afstammende pagina met voeten treden.

Gebruik de volgende procedure om een pagina en de afstammelingen aan een Dynamische configuratie van Tag Management te associëren.

1. Open de hoofdpagina van uw site in de klassieke gebruikersinterface.
1. Gebruik Sidekick om de pagina-eigenschappen te openen.
1. Klik op het tabblad Cloud Services op Service toevoegen, selecteer Dynamic Tag Management en klik op OK.

   ![ chlimage_1-357 ](assets/chlimage_1-357.png)

1. Gebruik het Dynamische drop-down menu van Tag Management om uw configuratie te selecteren, en klik dan O.K.

Gebruik de volgende procedure om de geërfte configuratievereniging voor een pagina met voeten te treden. De overschrijving heeft invloed op de pagina en op alle onderliggende pagina&#39;s.

1. Open de pagina in klassieke UI.
1. Gebruik Sidekick om de pagina-eigenschappen te openen.
1. Klik op het tabblad Cloud Services op het hangslotpictogram naast de eigenschap Geërfd van en klik vervolgens op Ja in het bevestigingsdialoogvenster.

   ![ chlimage_1-358 ](assets/chlimage_1-358.png)

1. Verwijder of selecteer een andere Dynamische configuratie van Tag Management, en klik dan O.K.
