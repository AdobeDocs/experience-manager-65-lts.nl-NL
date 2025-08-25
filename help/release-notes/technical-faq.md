---
title: Veelgestelde vragen over technische aspecten
description: Veelgestelde technische vragen over AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 051244f1-cc67-4222-bd45-0c135c28bb15
source-git-commit: f983fc1edc613feaa070c4e82a92aabab9d50cbb
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# AEM 6.5 LTS - Technische veelgestelde vragen {#technical-faq}

Deze pagina is bedoeld om een aantal veelgestelde technische vragen over AEM 6.5 LTS te beantwoorden.

## Technische veelgestelde vragen

### Het eindpunt van `/systemalive` is niet meer beschikbaar in AEM 6.5 LTS.

De Felix System Ready-bundel, die is geconfigureerd om het `/systemalive` -eindpunt te bieden, is vervangen door Apache Felix Health Checks. Deze bundel is niet meer inbegrepen in AEM 6.5 LTS.

Het nieuwe eindpunt van de health check is beschikbaar bij `/system/health` en wordt geïmplementeerd met Apache Felix Health Checks.

Voor gedetailleerde documentatie over het kader van de Controle van de Gezondheid van Felix, verwijs naar de [ felix documentatie ](https://github.com/apache/felix-dev/blob/master/healthcheck/README.md).

### AEM Groovy-consolesupport

De AEM Groovy-consoleversie die in AEM 6.5 werd gebruikt, werkt mogelijk niet in AEM 6.5 LTS vanwege ontbrekende guave-afhankelijkheden. De onlangs gesteunde versie van de console van AEM Groovy is [ 19.0.8 ](https://github.com/orbinson/aem-groovy-console/releases/download/19.0.8/aem-groovy-console-all-19.0.8.zip).

### Biedt AEM 6.5 LTS ondersteuning voor gebruikerssynchronisatie?

Ja, AEM 6.5 LTS ondersteunt gebruikerssynchronisatie. De functionaliteit van gebruikerssync tussen AEM 6.5 en 6.5 LTS verandert niet.

### De Uber JAR op Maven Central lijkt beschadigd te zijn — wat is het probleem?

Controleer of u de Uber JAR gebruikt met de classificator `apis` . De verpakkingsstructuur van de Uber JAR is veranderd in AEM 6.5 LTS. Voor meer informatie, zie [ Update de versie van AEM Uber Jar ](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

## Aanvullende Help opvragen

Als u problemen tegenkomt die hier niet worden behandeld:
* Herzie de [ versienota&#39;s ](/help/release-notes/release-notes.md) voor bekende kwesties.
* Neem contact op met Adobe Support voor hulp.
