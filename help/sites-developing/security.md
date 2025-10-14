---
title: Beveiliging
description: De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase
solution: Experience Manager, Experience Manager Sites
feature: Developing,Security
role: Developer
exl-id: abc2747f-cfd8-4ee1-bbc0-5ad89beb383a
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '392'
ht-degree: 0%

---

# Beveiliging{#security}

De Veiligheid van de toepassing begint tijdens de ontwikkelingsfase. Adobe raadt u aan de volgende best practices op het gebied van beveiliging toe te passen.

## Aanvraagsessie gebruiken {#use-request-session}

Volgens het beginsel van minst voorrecht raadt Adobe aan dat elke toegang tot de opslagplaats wordt uitgevoerd door gebruik te maken van de sessie die gebonden is aan het verzoek van de gebruiker en een juiste toegangscontrole.

## Beveiligen tegen XSS (Cross-Site Scripting) {#protect-against-cross-site-scripting-xss}

Met XSS (Cross-site scripting) kunnen aanvallers code injecteren in webpagina&#39;s die door andere gebruikers worden weergegeven. Deze kwetsbaarheid op het gebied van beveiliging kan door kwaadaardige webgebruikers worden misbruikt om toegangsbesturingselementen te omzeilen.

AEM past het beginsel toe om alle door de gebruiker opgegeven inhoud bij uitvoer te filteren. Het voorkomen van XSS krijgt de hoogste prioriteit tijdens zowel ontwikkeling als testen.

Het XSS beschermingsmechanisme dat door AEM wordt verstrekt is gebaseerd op de [&#x200B; Bibliotheek Java™ van AntiSamy &#x200B;](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) door [&#x200B; OWASP (het Open Project van de Veiligheid van de Toepassing van het Web) wordt verstrekt &#x200B;](https://owasp.org/). De standaardconfiguratie van AntiSamy vindt u op

`/libs/cq/xssprotection/config.xml`

Het is belangrijk dat u deze configuratie aanpast aan uw eigen veiligheidsbehoeften door het configuratiedossier te bedekken. De officiële [&#x200B; documentatie AntiSamy &#x200B;](https://wiki.owasp.org/index.php/Category:OWASP_AntiSamy_Project) voorziet u van alle informatie u uw veiligheidsvereisten moet uitvoeren.

>[!NOTE]
>
>Adobe adviseert dat u altijd tot de XSS bescherming API toegang hebt door [&#x200B; XSSAPI te gebruiken die door AEM &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/adobe/granite/xss/XSSAPI.html) wordt verstrekt.

Ook, kan een firewall van de Webtoepassing, zoals [&#x200B; mod_security voor Apache &#x200B;](https://www.modsecurity.org), betrouwbare, centrale controle over de veiligheid van het plaatsingsmilieu verstrekken en tegen eerder onontdekte dwars-plaats scripting aanvallen beschermen.

## Toegang tot Cloud Service-informatie {#access-to-cloud-service-information}

>[!NOTE]
>
>ACLs voor de Informatie van Cloud Service en de montages OSGi die worden vereist om uw instantie te beveiligen worden geautomatiseerd als deel van de [&#x200B; Klaar Wijze van de Productie &#x200B;](/help/sites-administering/production-ready.md). Terwijl dit betekent dat u niet de configuratie moet manueel veranderen, wordt het nog geadviseerd dat u hen controleert alvorens u met uw plaatsing gaat leven.

Wanneer u [&#x200B; uw instantie van AEM met Adobe Experience Cloud &#x200B;](/help/sites-administering/marketing-cloud.md) integreert, gebruikt u [&#x200B; configuraties van Cloud Service &#x200B;](/help/sites-developing/extending-cloud-config.md). Informatie over deze configuraties, samen met alle verzamelde statistieken, wordt opgeslagen in de gegevensopslagruimte. Adobe raadt aan dat als u deze functionaliteit gebruikt, u controleert of de standaardbeveiliging van deze gegevens aan uw vereisten voldoet.

De module webservicesSupport schrijft statistieken en configuratiegegevens onder:

`/etc/cloudservices`

Met de standaardmachtigingen:

* Auteursomgeving: `read` voor `contributors`

* Publicatie-omgeving: `read` for `everyone`

## Beveiligen tegen aanvallen van smeden voor meerdere sites {#protect-against-cross-site-request-forgery-attacks}

Voor meer informatie over de veiligheidsmechanismen gebruikt AEM om aanvallen te verlichten CSRF, zie de [&#128279;](/help/sites-administering/security-checklist.md#protect-against-cross-site-request-forgery) sectie van de Filter van de Verwijzer van 0&rbrace; Verschuiving van de Controle van de Veiligheid en de [&#x200B; documentatie van het Kader van de Bescherming CSRF &#x200B;](/help/sites-developing/csrf-protection.md).
