---
title: Dynamisch model aan Component Mapping voor SPAs
description: Leer hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor Adobe Experience Manager voorkomt.
contentOwner: bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: spa
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,SPA Editor
role: Developer
exl-id: 051be106-bb15-46b2-8158-53817f68f57c
index: false
source-git-commit: f6a3d16c55a6b62aea9a374904339e16d30f0a75
workflow-type: tm+mt
source-wordcount: '313'
ht-degree: 0%

---


# Dynamisch model aan Component Mapping voor SPAs{#dynamic-model-to-component-mapping-for-spas}

Dit document beschrijft hoe het dynamische model aan componentenafbeelding in JavaScript SPA SDK voor Adobe Experience Manager (AEM) voorkomt.

{{ue-over-spa}}

## ComponentMapping-module {#componentmapping-module}

De module `ComponentMapping` wordt verstrekt als pakket NPM aan het front-end project. Het slaat front-end componenten op en verstrekt een manier voor de Enige Toepassing van de Pagina om front-end componenten aan de middeltypes van AEM in kaart te brengen. Hierdoor wordt een dynamische resolutie van componenten ingeschakeld bij het parseren van het JSON-model van de toepassing.

Elke item in het model bevat een veld `:type` dat een AEM-brontype weergeeft. Als de front-end component is gekoppeld, kan deze zichzelf renderen met behulp van het fragment van het model dat is ontvangen van de onderliggende bibliotheken.

Zie [&#x200B; Vervaging van het KUUROORD &#x200B;](/help/sites-developing/spa-blueprint.md) voor meer informatie over model het ontleden en de front-end componententoegang tot het model.

Zie ook het npm pakket: [&#x200B; https://www.npmjs.com/package/@adobe/aem-spa-component-mapping &#x200B;](https://www.npmjs.com/package/@adobe/aem-spa-component-mapping)

## Modelgestuurde toepassing voor één pagina {#model-driven-single-page-application}

Toepassingen op één pagina die gebruikmaken van de JavaScript SPA SDK voor AEM, zijn gebaseerd op modellen:

1. De front-end componenten registreren zich aan de [&#x200B; Opslag van de Afbeelding van de Component &#x200B;](/help/sites-developing/spa-dynamic-model-to-component-mapping.md#componentmapping-module).
1. Dan de [&#x200B; Container &#x200B;](/help/sites-developing/spa-blueprint.md#container), eens voorzien van een model door de [&#x200B; ModelLeverancier &#x200B;](/help/sites-developing/spa-blueprint.md#the-model-provider), herhaalt over zijn modelinhoud ( `:items`).

1. Als er een pagina is, krijgen zijn kinderen ( `:children`) eerst een componentenklasse van de [&#x200B; Afbeelding van de Component &#x200B;](/help/sites-developing/spa-blueprint.md#componentmapping) en dan het concretiseren.

## Toepassingsinitialisatie {#app-initialization}

Elke component wordt uitgebreid met de mogelijkheden van [`ModelProvider`](/help/sites-developing/spa-blueprint.md#the-model-provider). Initialisatie heeft derhalve de volgende algemene vorm:

1. Elke modelleverancier initialiseert zich en luistert naar veranderingen die aan het stuk van model worden aangebracht dat aan zijn binnencomponent beantwoordt.
1. [`PageModelManager`](/help/sites-developing/spa-blueprint.md#pagemodelmanager) moet worden geïnitialiseerd zoals vertegenwoordigd door de [&#x200B; initialiseringsstroom &#x200B;](/help/sites-developing/spa-blueprint.md).

1. Nadat het paginamodel is opgeslagen, retourneert de paginamodelbeheerder het volledige model van de app.
1. Dit model wordt dan overgegaan tot de front-end wortel [&#x200B; component van de Container &#x200B;](/help/sites-developing/spa-blueprint.md#container) van de toepassing.
1. Stukken van het model worden uiteindelijk doorgegeven aan elke afzonderlijke onderliggende component.

![&#x200B; app_model_initialization &#x200B;](assets/app_model_initialization.png)
