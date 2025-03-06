---
title: Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL
description: Leer hoe u AEM Content Fragments met GraphQL kunt gebruiken voor het leveren van inhoud zonder kop.
feature: Content Fragments,Headless,GraphQL
role: User,Developer
solution: Experience Manager, Experience Manager Assets
exl-id: 8d0271c0-a795-4ff6-a2ae-72329f05a401
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '669'
ht-degree: 0%

---

# Levering van inhoud zonder kop met gebruik van inhoudsfragmenten met GraphQL {#headless-content-delivery-using-content-fragments-with-graphQL}

Met Adobe Experience Manager (AEM) kunt u Content Fragments samen met de AEM GraphQL API (een aangepaste implementatie, gebaseerd op standaard GraphQL) gebruiken om zonder problemen gestructureerde inhoud te leveren voor gebruik in uw toepassingen. Met de mogelijkheid om één API-query aan te passen kunt u de specifieke inhoud ophalen en leveren die u wilt/moet renderen (als antwoord op de enkele API-query).

<!--
>[!NOTE]
>
>See [Headless and AEM](/help/implementing/developing/headless/introduction.md) for an introduction to Headless Development for AEM Sites.
-->

>[!NOTE]
>
>GraphQL wordt momenteel gebruikt in twee (afzonderlijke) scenario&#39;s in Adobe Experience Manager (AEM):
>
>* [ AEM Commerce verbruikt gegevens van een handelsplatform via GraphQL ](/help/commerce/cif/integrating/magento.md).
>* [ de Inhoudsfragmenten van AEM werken samen met AEM GraphQL API (een aangepaste implementatie, die op standaardGraphQL wordt gebaseerd), om gestructureerde inhoud voor gebruik in uw toepassingen ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) te leveren.

## Headless CMS {#headless-cms}

Een headless Content Management System (CMS) is:

* &quot;*A headless inhoudsbeheersysteem, of headless CMS, is een back-end slechts inhoudsbeheersysteem (CMS) dat van de grond omhoog als inhoudsbewaarplaats wordt gebouwd die inhoud door middel van API voor vertoning op om het even welk apparaat toegankelijk maakt.*

  Zie [ Wikipedia ](https://en.wikipedia.org/wiki/Headless_content_management_system).

Met betrekking tot het ontwerpen van inhoudsfragmenten in AEM betekent dit dat:

* U kunt Content Fragments gebruiken om inhoud te schrijven die niet in de eerste plaats bedoeld is om rechtstreeks (1:1) te worden gepubliceerd op opgemaakte pagina&#39;s.

* De inhoud van de inhoudsfragmenten wordt vooraf gestructureerd volgens de modellen van het inhoudsfragment. Hierdoor wordt de toegang voor uw toepassingen vereenvoudigd, waardoor uw inhoud verder wordt verwerkt.

## GraphQL - Een overzicht {#graphql-overview}

GraphQL is:

* &quot;*...een vraagtaal voor APIs en runtime voor het vervullen van die vragen met uw bestaande gegevens.*&quot;.

  Zie [ GraphQL.org ](https://graphql.org)

[ AEM GraphQL API ](#aem-graphql-api) laat u (complexe) vragen op uw [ Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) uitvoeren; met elke vraag die volgens een specifiek modeltype is. De geretourneerde inhoud kan vervolgens door uw toepassingen worden gebruikt.

## AEM GRAPHQL API {#aem-graphql-api}

Voor Adobe Experience is een aangepaste implementatie van de standaard GraphQL API ontwikkeld. Zie [ AEM GraphQL API voor gebruik met de Fragmenten van de Inhoud ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) voor details.

De implementatie van AEM GraphQL API is gebaseerd op de [ bibliotheken van GraphQL Java ](https://graphql.org/code/#java).

## Inhoudsfragmenten voor gebruik met de AEM GraphQL API {#content-fragments-use-with-aem-graphql-api}

[ de Fragmenten van de Inhoud ](#content-fragments) kunnen als basis voor GraphQL voor AEM vragen als worden gebruikt:

* Hiermee kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren.
* De [ Modellen van het Fragment van de Inhoud ](#content-fragments-models) verstrekken de vereiste structuur door middel van bepaalde gegevenstypes.
* De [ Verwijzing van het Fragment ](#fragment-references), beschikbaar wanneer het bepalen van een model, kan worden gebruikt om extra lagen van structuur te bepalen.

![ de Fragmenten van de Inhoud voor gebruik met de Fragmenten van de Inhoud van GraphQL ](assets/cfm-nested-01.png " voor gebruik met GraphQL ")

### Inhoudsfragmenten {#content-fragments}

Content Fragments:

* Bevat gestructureerde inhoud.

* Zij zijn gebaseerd op het Model van het Fragment van de a [ Inhoud ](#content-fragments-models), dat de structuur voor het resulterende fragment vooraf bepaalt.

### Modellen van inhoudsfragmenten {#content-fragments-models}

Deze [ Modellen van het Fragment van Inhoud ](/help/assets/content-fragments/content-fragments-models.md):

* Wordt gebruikt om de [ Schema&#39;s ](https://graphql.org/learn/schema/) te produceren, eens **Toegelaten**.

* Geef de gegevenstypen en velden op die vereist zijn voor GraphQL. Ze zorgen ervoor dat uw toepassing alleen vraagt wat mogelijk is en wat wordt verwacht ontvangt.

* Het gegevenstype **[Verwijzingen van het Fragment](#fragment-references)** kan in uw model worden gebruikt om een ander Fragment van de Inhoud van verwijzingen te voorzien, en zo extra niveaus van structuur introduceren.

### Fragmentverwijzingen {#fragment-references}

De **[Verwijzing van het Fragment](/help/assets/content-fragments/content-fragments-models.md#fragment-reference-nested-fragments)**:

* Is in samenwerking met GraphQL van bijzonder belang.

* Dit is een specifiek gegevenstype dat kan worden gebruikt bij het definiëren van een inhoudsfragmentmodel.

* Verwijst naar een ander fragment, afhankelijk van een specifiek inhoudsfragmentmodel.

* Hiermee kunt u gestructureerde gegevens ophalen.

   * Wanneer bepaald als a **multifeed**, kunnen de veelvoudige sub-fragmenten (teruggewonnen) door het eerste fragment van verwijzingen worden voorzien.

### JSON-voorvertoning {#json-preview}

Om met het ontwerpen van en het ontwikkelen van uw Modellen van het Fragment van de Inhoud te helpen, kunt u voorproef [ output JSON ](/help/assets/content-fragments/content-fragments-json-preview.md).

## GraphQL leren gebruiken met AEM - Voorbeeldinhoud en query&#39;s {#learn-graphql-with-aem-sample-content-queries}

Zie [ Lerend om GraphQL met AEM te gebruiken - de Inhoud en Vragen van de Steekproef ](/help/sites-developing/headless/graphql-api/content-fragments-graphql-samples.md) voor een inleiding aan het gebruiken van AEM GraphQL API.

## Zelfstudie - Aan de slag met AEM Headless en GraphQL

Op zoek naar een praktische zelfstudie? Controle uit [ Begonnen het Worden met de Hoofdloze AEM en GraphQL ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/overview.html) leerprogramma van begin tot eind illustrerend hoe te om inhoud op te bouwen en bloot te stellen gebruikend GraphQL APIs van AEM en verbruikt door een externe app, in een headless scenario van CMS.
