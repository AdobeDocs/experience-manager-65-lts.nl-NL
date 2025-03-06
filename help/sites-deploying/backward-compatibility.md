---
title: Achterwaartse compatibiliteit in AEM 6.5
description: Leer hoe u uw apps en configuraties compatibel kunt houden met Adobe Experience Manager (AEM 6.5)
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 96e44da3-da89-4671-a4fb-19ce1b9a38c4
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '462'
ht-degree: 0%

---

# Achterwaartse compatibiliteit in AEM 6.5{#backward-compatibility-in-aem}

## Overzicht {#overview}

In Adobe Experience Manager (AEM) 6.5 zijn alle functies ontwikkeld met achterwaartse compatibiliteit voor ogen.

Meestal hoeven klanten die AEM 6.3 uitvoeren, de code of aanpassingen niet te wijzigen wanneer ze de upgrade uitvoeren. Voor AEM 6.1- en 6.2-klanten zijn er geen extra onderbrekingswijzigingen die u tijdens een upgrade naar 6.3 zou moeten doorvoeren.

Voor uitzonderingen waar de eigenschappen niet achteruit compatibel konden worden gehouden, kunnen de achterwaartse onverenigbaarheidskwesties voor bundels en inhoud worden verlicht. U doet dit door een compatibiliteitspakket voor 6.4 te installeren (zie hieronder hoe u meer informatie kunt vinden over de downloadlocatie). Dit compatibiliteitspakket helpt de compatibiliteit te herstellen, meestal voor toepassingen die voldoen aan AEM 6.4.

Met het compatibiliteitspakket kunt u AEM uitvoeren in de compatibiliteitsmodus en de aangepaste ontwikkeling uitstellen tegen de nieuwe AEM-functies:

>[!NOTE]
>
>Het compatibiliteitspakket is slechts een tijdelijke oplossing om de ontwikkeling uit te stellen die nodig is om compatibel te zijn met AEM 6.5. Adobe raadt het alleen als laatste optie aan als u compatibiliteitsproblemen niet direct na de upgrade kunt oplossen via ontwikkeling. Bovendien raadt Adobe u aan over te schakelen op de native modus en het compatibiliteitspakket te verwijderen wanneer u besluit verder te gaan met aangepaste ontwikkeling op basis van 6.5 en gebruik te maken van de volledige 6.5-functionaliteit.

![ sase ](assets/sase.png)

Het pakket van de Verenigbaarheid heeft twee wijzen: **Verpletterend Toegelaten** en **Verpletterend Gehandicapten**.

Zo kan AEM 6.5 in drie modi worden uitgevoerd:

**Inheemse Wijze:**

De modus Native is bedoeld voor klanten die alle nieuwe functies van AEM 6.5 willen gebruiken en die klaar zijn om enige ontwikkeling uit te voeren om hun aanpassingen te laten werken met alle nieuwe functies.

Dit betekent dat u de toepassing direct na de upgrade moet aanpassen.

**Wijze van de Verenigbaarheid: Het Pakket van de verenigbaarheid die met het Verpletteren Toegelaten** wordt geïnstalleerd

De Wijze van de verenigbaarheid is voor klanten die aanpassingen van interfaces hebben die niet achterwaarts compatibel zijn. Zo kan AEM worden uitgevoerd in de compatibiliteitsmodus en kan de aangepaste ontwikkeling worden uitgesteld die vereist is voor nieuwe AEM-functies die niet compatibel zijn met sommige van uw aangepaste code.

**Verouderde Wijze: Het Pakket van de verenigbaarheid dat met het Verpletteren van Gehandicapten** wordt geïnstalleerd

De verouderde wijze is voor klanten die douaneinterfaces hebben die op erfenis of verouderde code van AEM worden gebaseerd die uit in het verenigingspakket is bewogen.

![ sap ](assets/sapte.png)

## Instellen {#how-to-set-up}

Het **AEM 6.4 Pak van de Verenigbaarheid voor 6.5** kan als pakket worden geïnstalleerd gebruikend de Manager van het Pakket. U kunt het [ AEM 6.4 Pak van de Verenigbaarheid voor 6.5 van de plaats van de Distributie van de Software downloaden ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=compat*&amp;orderby=%40jcr%3Acontent%2Fjcr%3AlastModified&amp;orderby.sort=desc&amp;layout=list&amp;p.offset=0&amp;p.limit=20&amp;package=%2Fcontent%2Fsoftware-distribution%2Fen%2Fdetails.html%2Fcontent%2Fdam%2Faem%2Fpublic%2Fadobe%2Fpackages%2Fcq650%2Fcompatpack%2Faem-compat-cq65-to-cq64).

Zodra het Pakket van de Verenigbaarheid wordt geïnstalleerd, kan het verpletteren worden toegelaten of worden onbruikbaar gemaakt gebruikend een schakelaar in de configuratie OSGI zoals hieronder getoond:

![ Compat Schakelaars ](assets/compat-switches.png)

Nadat het compatibiliteitspakket is geïnstalleerd en ingesteld, worden de functies gebruikt op basis van de gekozen compatibiliteitsmodus.
