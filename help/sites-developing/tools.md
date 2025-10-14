---
title: Gereedschappen voor testen en bijhouden
description: AEM biedt een raamwerk voor het testen van de gebruikersinterface van componenten en een mechanisme voor het testen en opsporen van fouten in componenten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4aa0f10d-e915-4ad2-a886-080ed8b9b10f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '288'
ht-degree: 0%

---

# Gereedschappen voor testen en bijhouden{#testing-and-tracking-tools}

## Testen {#testing}

AEM biedt:

* [&#x200B; een kader voor het testen van component UI &#x200B;](/help/sites-developing/hobbes.md).
* [&#x200B; een mechanisme om componenten &#x200B;](/help/sites-developing/developer-mode.md) te testen en te zuiveren.

Hieronder vindt u twee Open Source-testprogramma&#39;s:

**Selenium**

Selenium wordt gebruikt voor functietests in een browser met één gebruiker per activiteit. Het registreert teststappen (kliks) als of HTML lijsten of klassen Java™.

Voor meer informatie, zie [&#x200B; https://www.selenium.dev/ &#x200B;](https://www.selenium.dev/).

**JMeter**

JMeter wordt gebruikt om verzoeken bij te houden en kan worden gebruikt voor functionele, prestatie- en stresstests.

Voor meer informatie, zie [&#x200B; https://jmeter.apache.org/ &#x200B;](https://jmeter.apache.org/).

Er zijn ook veel bedrijfseigen instrumenten voor het automatiseren van tests en het beheren van testplannen.

### Tekstspatiëring {#tracking}

De volgende gereedschappen zijn gemakkelijk beschikbaar. Nochtans is een zeer belangrijke kwestie in alle gevallen de beschikbaarheid van de gegevens aan alle leden van het projectteam - partner en klant.

**Bugzilla**

Een bug-volgsysteem dat aan uw eigen vereisten kan worden gevormd.

**Spreadsheets**

Hoewel niet specifiek een insect-volgend hulpmiddel, spreadsheets vaak *verkeerd* worden gebruikt voor dit doel aangezien zij gemakkelijk zijn te begrijpen en de meeste gebruikers ervaring van hun functionaliteit hebben.

Als deze spreadsheets worden gebruikt voor tracering, geldt het volgende:

* zij moeten eenvoudig worden gehouden .
* het aantal afzonderlijke spreadsheets moet tot een minimum worden beperkt .
* zij moeten regelmatig worden bijgewerkt .
* slechts één primaire kopie moet worden bewaard en iedereen moet weten waar de primaire kopie is.
* zij moeten toegankelijk zijn voor alle projectleden .
* als de veiligheid een kwestie (vaak voorkomt bij grote bedrijven) is en gemeenschappelijke toegang niet mogelijk is, dan kunnen de exemplaren worden verdeeld zolang iedereen begrijpt dat deze spreadsheets kopieën zijn en niet kunnen worden bijgewerkt.

Ook hier zijn er veel bedrijfseigen hulpmiddelen voor het bijhouden van fouten en eigenschapvereisten.
