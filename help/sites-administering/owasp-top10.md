---
title: OWASP Top 10
description: Leer hoe AEM omgaat met de tien grootste beveiligingsrisico's van OWASP.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
feature: Security
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: c49a9876-3a8e-4837-a1a7-e0e62bc60e32
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 0%

---

# OWASP Top 10{#owasp-top}

Het [ Open Project van de Veiligheid van de Toepassing van het Web ](https://owasp.org/) (OWASP) handhaaft een lijst van wat zij als de [ Hoogste Tien Veiligheidsrisico&#39;s van de Toepassing van het Web ](https://owasp.org/www-project-top-ten/) beschouwen.

Deze worden hieronder vermeld, samen met een uitleg van hoe CRX ermee omgaat.

## 1. Injectie {#injection}

* SQL - Voorkomen door ontwerp: De standaardopslagopstelling omvat noch vereist een traditionele gegevensbestand, alle gegevens worden opgeslagen in de inhoudsbewaarplaats. Alle toegang is beperkt tot geverifieerde gebruikers en kan alleen worden uitgevoerd via de JCR API. SQL wordt alleen ondersteund voor zoekopdrachten (SELECT). Bovendien biedt SQL ondersteuning voor waardebinding.
* LDAP - LDAP-injectie is niet mogelijk, omdat de verificatiemodule de invoer filtert en de gebruiker importeert met de methode bind.
* OS - Er wordt geen shell uitgevoerd vanuit de toepassing.

## 2. XSS (Cross-Site Scripting) {#cross-site-scripting-xss}

De algemene matigingspraktijk moet al output van gebruiker-geproduceerde inhoud coderen gebruikend een server-kantXSS beschermingsbibliotheek die op [ wordt gebaseerd Codeur van OWASP ](https://owasp.org/www-project-java-encoder/) en [ AntiSamy ](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project).

XSS is een hoogste prioriteit tijdens zowel het testen als de ontwikkeling, en om het even welke gevonden kwesties worden (typisch) onmiddellijk opgelost.

## 3. Verbroken verificatie en sessiebeheer {#broken-authentication-and-session-management}

AEM gebruikt geluid en bewezen authentificatietechnieken, die op [ Apache Jasrabbit ](https://jackrabbit.apache.org/jcr/index.html) en [ Apache Sling ](https://sling.apache.org/) vertrouwen. Browsersessies/HTTP-sessies worden niet gebruikt in AEM.

## 4. Onveilige verwijzingen naar directe objecten {#insecure-direct-object-references}

Alle toegang tot gegevensvoorwerpen wordt bemiddelen door de bewaarplaats en daarom beperkt door op rol-gebaseerd toegangsbeheer.

## 5. Smeeuw voor aanvragen voor andere sites (CSRF) {#cross-site-request-forgery-csrf}

CSRF (Cross-Site Request Svervalsing) wordt beperkt door automatisch een cryptografisch token in alle formulieren en AJAX-aanvragen in te voeren en dit token op de server voor elke POST te controleren.

Bovendien verscheept AEM met een op verwijzing-kopbal gebaseerde filter, die kan worden gevormd om *slechts* verzoeken van POST van specifieke gastheren (die in een lijst worden bepaald) toe te staan.

## 6. Onjuiste beveiliging {#security-misconfiguration}

Het is onmogelijk te garanderen dat alle software altijd correct is geconfigureerd. Adobe streeft er echter naar zoveel mogelijk begeleiding te bieden en de configuratie zo eenvoudig mogelijk te maken. Voorts schepen van AEM met [ geïntegreerde Gezondheidscontroles van de Veiligheid ](/help/sites-administering/operations-dashboard.md) die u helpen veiligheidsconfiguratie in een blik controleren.

Herzie de [ Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md) voor meer informatie die u van geleidelijke het verharden instructies voorziet.

## 7. Onveilige cryptografische opslag {#insecure-cryptographic-storage}

Wachtwoorden worden opgeslagen als cryptografische hashes in het gebruikersknooppunt. Dergelijke knooppunten kunnen standaard alleen door de beheerder en de gebruiker zelf worden gelezen.

Gevoelige gegevens zoals referenties van derden worden in gecodeerde vorm opgeslagen met behulp van een voor FIPS 140-2 gecertificeerde cryptografische bibliotheek.

## 8. Kan URL-toegang niet beperken {#failure-to-restrict-url-access}

De bewaarplaats staat het plaatsen van [ nauwkeurig gegrainde voorrechten (zoals die door JCR worden gespecificeerd) ](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html) voor om het even welke bepaalde gebruiker of groep op om het even welke bepaalde weg, door toegangsbeheeringangen toe. Toegangsbeperkingen worden afgedwongen door de opslagplaats.

## 9. Onvoldoende bescherming van de Laag van het Vervoer {#insufficient-transport-layer-protection}

Gemengde door serverconfiguratie (bijvoorbeeld alleen HTTPS gebruiken).

## 10. Niet-gevalideerde omleidingen en doorsturen {#unvalidated-redirects-and-forwards}

Gematigd door alle omleidingen aan gebruiker-geleverde bestemmingen aan interne plaatsen te beperken.
