---
title: AEM Forms Workspace-architectuur
description: Conceptuele informatie en overzicht van de architectuur van de LiveCycle AEM Forms-werkruimte.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: User, Developer
exl-id: d317274f-2c9a-4809-b43e-2efebc8fcb3f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '219'
ht-degree: 0%

---

# AEM Forms Workspace-architectuur {#aem-forms-workspace-architecture}

De AEM Forms-werkruimte is een webtoepassing die wordt gehost op CRX™. Wanneer de werkruimte in een browser wordt geopend, wordt een CRX-bron benaderd en wordt de toepassing weergegeven als HTML-pagina in de browser.

De toepassing benadert de AEM Forms-server op REST-eindpunten voor het volgende:

* Gebruikerstaken ophalen, beginpunten van processen, procesgeschiedenis en gebruikersgegevens
* Handeling uitvoeren op taken
* Query uitvoeren in database
* Gebruikersvoorkeuren en meer bijwerken

De AEM Forms-server heeft via JDBC toegang tot de AEM Forms-database. De database bestaat uit taken, processen en instanties, gebruikers en gerelateerde informatie.

De AEM Forms-werkruimte is ontworpen voor modulaire JavaScript™-onderdelen die afzonderlijk kunnen worden aangepast en opnieuw kunnen worden gebruikt in andere webtoepassingen. De componenten zijn gebaseerd op BackBone, een JavaScript-bibliotheek die structuur geeft aan webtoepassingen. Een gedetailleerd artikel beschrijvend interactie van componenten met BackBone is [ hier ](/help/forms/using/backbone-interaction.md). De organisatie van componenten in de de omslagstructuur van CRX wordt besproken in [ dit ](/help/forms/using/folder-structure.md) artikel.

Pakketten geleverd voor de AEM Forms-werkruimte:

* `adobe-lc-workspace-pkg-<version>.zip`: Het is een CRX-pakket, dat wil zeggen dat het in CRX kan worden geïmplementeerd met de Package Manager.
* `adobe-lc-workspace-<version>-src.zip`: Het is een archief dat volledige code van de werkruimte en de manuscripten van AEM Forms bevat om opstellen pakketten-verschepen, zuivert, en Dev pakketten.
