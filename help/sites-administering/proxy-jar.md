---
title: Proxyserver (proxy.jar)
description: Leer over het Hulpmiddel van de Server van de Volmacht (proxy.jar) in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d918ddf2-aa70-4742-97d5-24a2c51f578a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1174'
ht-degree: 0%

---

# Proxyserver (proxy.jar){#proxy-server-tool-proxy-jar}

De proxyserver fungeert als een tussenliggende server die verzoeken tussen een client en een server afspeelt. De volmachtsserver volgt alle cliënt-server interactie en output een logboek van de volledige mededeling van TCP. Dit laat u precies controleren wat aan de hand is, zonder het moeten tot de belangrijkste server toegang hebben.

U vindt de proxyserver in de juiste installatiemap:

* &lt;cq_install_path>/opt/helpers/proxy.jar
* &lt;crx_install_path>/opt/helpers/proxy.jar

U kunt de volmachtsserver gebruiken om alle cliënt-server interactie, ongeacht het onderliggende communicatie protocol te controleren. U kunt bijvoorbeeld de volgende protocollen controleren:

* HTTP voor Web-pagina&#39;s
* HTTPS voor beveiligde webpagina&#39;s
* SMTP voor e-mailberichten
* LDAP voor gebruikersbeheer

U kunt bijvoorbeeld de proxyserver plaatsen tussen twee toepassingen die via een TCP/IP-netwerk communiceren, bijvoorbeeld een webbrowser en AEM. Hiermee kunt u precies controleren wat er gebeurt wanneer u een AEM-pagina aanvraagt.

## Het gereedschap Proxyserver starten {#starting-the-proxy-server-tool}

U vindt het gereedschap in de map /opt/helpers van de AEM-installatie. Het type starten:

```xml
java -jar proxy.jar <host> <remoteport> <localport> [options]
```

### Opties {#options}

* **q (stille Wijze)** schrijft niet de verzoeken aan het consolevenster. Gebruik deze optie als u de verbinding niet wilt vertragen of als u de uitvoer naar een bestand wilt vastleggen (zie de optie -logfile).
* **b (binaire Wijze)** als u specifieke bytecombinaties in het verkeer zoekt, laat binaire wijze toe. De uitvoer bevat de hexadecimale uitvoer en de tekenuitvoer.
* **t (de ingangen van het tijdstempellogboek)** voegt een tijdstempel aan elke logboekoutput toe. Het tijdstempel is in seconden, zodat het mogelijk niet geschikt is voor het controleren van afzonderlijke aanvragen. Gebruik het om van gebeurtenissen de plaats te bepalen die in een specifiek ogenblik voorkwamen als u de volmachtsserver over een langere tijdspanne gebruikt.
* **logfile &lt;filename> (schrijf aan logboekdossier)** schrijft het cliënt-server gesprek aan een logboekdossier. Deze parameter werkt ook in de stille modus.
* **i &lt;numIndentions> (voeg inspringing toe)** Elke actieve verbinding is ingesprongen voor betere leesbaarheid. De standaardwaarde is 16 niveaus. (Nieuw in proxy.jar versie 1.16).

## Gebruikt het gereedschap Proxyserver {#uses-of-the-proxy-server-tool}

De volgende scenario&#39;s illustreren een paar van de doeleinden waarvoor het Hulpmiddel van de Server van de Volmacht kan worden gebruikt:

**Controle voor Cookies en hun Waarden**

In het volgende voorbeeld van een logbestandvermelding worden alle cookies en hun waarden weergegeven die door de client worden verzonden via de zesde verbinding die sinds het starten van de proxy is geopend:

```xml
C-6-#000635 -> [Cookie: cq3session=7e39bc51-ac72-3f48-88a9-ed80dbac0693; Show=ShowMode; JSESSIONID=68d78874-cabf-9444-84a4-538d43f5064d ]
```

**het Controleren op Kopballen en hun Waarden** het volgende voorbeeld van de logboekingang toont aan dat de server een houden-levende verbinding kan maken en de kopbal van de inhoudslengte behoorlijk plaatste was:

```xml
S-7-#000017 -> [Connection: Keep-Alive ]
...
S-7-#000107 -> [Content-Length: 124 ]
```

**het Controleren als Levend houden** werkt

**Levend houden** betekent dat een cliënt de verbinding aan de server opnieuw gebruikt om veelvoudige dossiers (de paginacode, beelden, stijlbladen, etc.) te vervoeren. Zonder houden-levend, moet de cliënt een nieuwe verbinding voor elk verzoek vestigen.

Controleren of in leven houden werkt:

1. Start de proxyserver.
1. Vraag een pagina aan.

* Als houden-levend werkt, zou de verbindenteller nooit boven 5 tot 10 verbindingen moeten gaan.
* Als houden-levend niet werkt, stijgt de verbindenteller snel.

**Vindend Verzoeken Verloren**

Als u aanvragen kwijtraakt in een complexe serverinstelling, bijvoorbeeld met een firewall en een Dispatcher, kunt u met de proxyserver achterhalen waar de aanvraag is verloren. Als er een firewall is:

1. Een proxy starten voor een firewall
1. Een andere proxy starten na een firewall
1. Gebruik deze om te zien hoe ver de verzoeken krijgen.

**Verzoeken die** veranderen

Als u van tijd tot tijd hangende verzoeken ervaart:

1. Start een proxy.jar.
1. Wacht of schrijf het toegangslogboek in een dossier - met elke ingang een timestamp heeft.
1. Wanneer het verzoek begint te hangen, kunt u zien hoeveel verbindingen open waren en welk verzoek problemen veroorzaakt.

## De indeling van logberichten {#the-format-of-log-messages}

De logboekingangen die door proxy.jar worden geproduceerd hebben elk het volgende formaat:

```xml
[timestamp (optional)] [<b>C</b>lient|<b>S</b>erver]-[ConnectionNumber]-[BytePosition] ->[Character Stream]
```

Een verzoek om een webpagina kan er bijvoorbeeld als volgt uitzien:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102938422341 HTTP/1.1 ]
```

* C betekent dat deze ingang uit de cliënt (het is een verzoek om een Web-pagina) komt
* 0 is het verbindingsnummer (de verbindenteller begint bij 0)
* #00000 de verschuiving in de bytestream. Dit is de eerste vermelding, dus de verschuiving is 0.
* [ GET &lt;?> ] is de inhoud van het verzoek, in het voorbeeld één van de kopballen van HTTP (url).

Wanneer een verbinding sluit, wordt de volgende informatie geregistreerd:

```xml
C-6-Finished: 758 bytes (1.0 kb/s)
S-6-Finished: 665 bytes (1.0 kb/s)
```

Dit toont het aantal bytes die tussen cliënt en server op de zesde verbinding en bij de gemiddelde snelheid overgingen.

## Een voorbeeld van een logbestandsuitvoer {#an-example-of-log-output}

Bekijk een eenvoudige sjabloon die de volgende code produceert wanneer u hierom wordt gevraagd:

```xml
<html>
  <head>
    <title>Welcome</title>
  </head>
  <body>
    Welcome to Playground<br>
    <img src="/logo.gif">
  </body>
</html>
```

Als AEM wordt uitgevoerd op localhost:4303, start u de proxyserver als volgt:

```xml
java -jar proxy.jar localhost 4303 4444 -logfile test.log
```

U kunt tot de server (`localhost:4303`) zonder de volmachtsserver toegang hebben, maar als u het via `localhost:4444` toegang hebt, registreert de volmachtsserver de mededeling. Open een browser en open een pagina die met de bovenstaande sjabloon is gemaakt. Kijk vervolgens naar het logbestand.

>[!NOTE]
>
>Tot proxy.jar versie 1.14, zijn de logboekingangen van één verbinding niet gesynchroniseerd, betekenend zijn de logboekingangen van één cliënt/serververbinding niet noodzakelijk in de correcte opeenvolgende orde. De nieuwere versies (>=1.14) van de proxyserver hebben dit probleem niet.

Wanneer u begint, wordt de volgende informatie naar het logbestand geschreven:

```xml
starting proxy for localhost:4303 on port 4444
using logfile: C:\CQUnify355default\opt\helpers\test.log
```

De volgende headervelden worden weergegeven aan het begin van de eerste verbinding (0), die de HTML-hoofdpagina aanvraagt:

```xml
C-0-#000000 -> [GET /author/prox.html?CFC_cK=1102936796533 HTTP/1.1 ]
C-0-#000053 -> [Accept: image/gif, image/x-xbitmap, image/jpeg, image/pjpeg, application/vnd.ms-powerpoint, application/vnd.ms-excel, application/msword, appl]
C-0-#000194 -> [ication/x-shockwave-flash, */* ]
C-0-#000227 -> [Accept-Language: de-ch ]
C-0-#000251 -> [Accept-Encoding: gzip, deflate ]
C-0-#000283 -> [User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0) ]
C-0-#000347 -> [Host: localhost:4444 ]
```

De client vraagt om een verbinding met behoud-levend, zodat de server meerdere bestanden via dezelfde verbinding kan verzenden:

```xml
C-0-#000369 -> [Connection: Keep-Alive ]
```

De proxyserver is een goed hulpmiddel om te controleren of cookies correct zijn ingesteld of niet. Hier ziet u het volgende:

* cq3session-cookie gegenereerd door AEM
* het schakelaar koekje van de showwijze dat door CFC wordt geproduceerd
* een cookie met de naam JSESSIONID; dit wordt automatisch gemaakt door JSP als deze niet expliciet wordt uitgeschakeld met &lt;%@ page session=&quot;false&quot; %>:

```xml
C-0-#000393 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-0-#000514 -> [ ]
S-0-#000000 -> [HTTP/1.0 200 OK ]
```

De server sluit verbinding 0 na de aanvraag. Levend houden is niet mogelijk, omdat het verzoek een vraagteken heeft. Dit betekent dat de server geen caching versie kan terugkeren, en daarom niet de inhoudslengte op dit punt kan bepalen, die voor een te houden-levende verbinding wordt vereist.

```xml
S-0-#000017 -> [Connection: Close ]
S-0-#000036 -> [Server: Communique Servlet Engine/3.5.5 ]
S-0-#000077 -> [Content-Type: text/html;charset=iso-8859-1 ]
S-0-#000121 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-0-#000158 -> [Set-Cookie: JSESSIONID=4161a56b-f193-d8-88a5-e09c5ff7ef2a;Path=/author ]
S-0-#000232 -> [ ]
```

Hier begint de server de HTML-code te verzenden bij verbinding 0:

```xml
S-0-#000234 -> [<html> ]
S-0-#000242 -> [.<head> ]
S-0-#000251 -> [..<title>Welcome</title> ]
S-0-#000277 -> [.</head> ]
S-0-#000287 -> [.<body> ]
S-0-#000296 -> [..Welcome to Playground<br> ]
S-0-#000325 -> [..<img src="/author/logo.gif"> ]
S-0-#000357 -> [.</body> ]
S-0-#000367 -> [</html>]
```

Verbinding 0 wordt onmiddellijk gesloten nadat het HTML-bestand is verzonden:

```xml
C-0-Finished: 516 bytes (0.0 kb/s)
S-0-Finished: 374 bytes (0.0 kb/s)
```

De uitvoer start nu voor verbinding 1, waardoor de afbeelding in de HTML-code wordt gedownload:

```xml
C-1-#000000 -> [GET /author/logo.gif HTTP/1.1 ]
C-1-#000031 -> [Accept: */* ]
C-1-#000044 -> [Referer: http://localhost:4444/author/prox.html?CFC_cK=1102936796533 ]
C-1-#000114 -> [Accept-Language: de-ch ]
C-1-#000138 -> [Accept-Encoding: gzip, deflate ]
C-1-#000170 -> [User-Agent: Mozilla/4.0 (compatible; MSIE 6.0; Windows NT 5.0) ]
C-1-#000234 -> [Host: localhost:4444 ]
```

Nogmaals, vraagt de cliënt om een te houden-levende verbinding:

```xml
C-1-#000256 -> [Connection: Keep-Alive ]
C-1-#000280 -> [Cookie: Show=ShowMode; cq3session=3bce15cf-1575-1b4e-8ea6-0d1a0c64738e; JSESSIONID=4161a56b-f193-d748-88a5-e09c5ff7ef2a ]
C-1-#000401 -> [ ]
S-1-#000000 -> [HTTP/1.0 200 OK ]
```

Voor verbinding 1, kan de server houden-levend verstrekken, omdat het beeld statisch is en daarom is de inhoudslengte gekend.

```xml
S-1-#000017 -> [Connection: Keep-Alive ]
S-1-#000041 -> [Server: Communique Servlet Engine/3.5.5 ]
S-1-#000082 -> [Content-Type: image/gif ]
```

De server retourneert de lengte van de inhoud van de afbeelding bij verbinding 1:

```xml
S-1-#000107 -> [Content-Length: 124 ]
S-1-#000128 -> [Date: Tue, 14 Dec 2004 09:46:44 GMT ]
S-1-#000165 -> [ ]
```

Nu de lengte van de inhoud is vastgesteld, verzendt de server de afbeeldingsgegevens op verbinding 1:

```xml
S-1-#000167 -> [GIF87a..........................,.......
...I....0.A..8......YDA.W...1..`i.`..6...Z...$@.F..)`..f..A.....iu.........$..;]
```

Nadat de bewaarlevingstijd is bereikt, sluit verbinding 1 eveneens:

```xml
S-1-Finished: 291 bytes (0.0 kb/s)
C-1-Finished: 403 bytes (0.0 kb/s)
```

Het bovenstaande voorbeeld is relatief eenvoudig, omdat de twee verbindingen opeenvolgend plaatsvinden:

* de server retourneert eerst de HTML-code
* vervolgens vraagt de browser de afbeelding op en wordt een nieuwe verbinding geopend

In de praktijk kan een pagina veel parallelle aanvragen genereren voor afbeeldingen, stijlpagina&#39;s, JavaScript-bestanden enzovoort. Dit betekent dat de logboeken overlappende vermeldingen van parallelle open verbindingen hebben. In dat geval raadt Adobe aan om optie -i te gebruiken om de leesbaarheid te verbeteren.
