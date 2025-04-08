---
title: Veelgestelde vragen over technische aspecten
description: Veelgestelde technische vragen over AEM 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 2352420843c613884ad3cae487ed048bd775e294
workflow-type: tm+mt
source-wordcount: '171'
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

De AEM Groovy-consoleversie die in AEM 6.5 werd gebruikt, werkt mogelijk niet in AEM 6.5 LTS vanwege ontbrekende guave-afhankelijkheden. De onlangs gesteunde versie van de console van AEM Groovy is [ 19.0.8 ](https://mvnrepository.com/artifact/be.orbinson.aem/aem-groovy-console/19.0.8).

## Aanvullende Help opvragen

Als u problemen tegenkomt die hier niet worden behandeld:
* Herzie de [ versienota&#39;s ](/help/release-notes/release-notes.md) voor bekende kwesties.
* Neem contact op met Adobe Support voor hulp.
