---
title: GraphQL-eindpunten beheren in AEM
description: Leer hoe u GraphQL-eindpunten in Adobe Experience Manager beheert voor levering van inhoud zonder kop.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin,Architect,Data Architect,Developer
exl-id: 13a2e067-878f-4580-9d7f-cfb3237a335d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '510'
ht-degree: 0%

---

# GraphQL-eindpunten beheren in AEM {#graphql-aem-endpoint}

Het eindpunt is het pad dat wordt gebruikt om toegang te krijgen tot GraphQL voor AEM. Met dit pad kunt u (of uw app) het volgende doen:

* toegang tot het GraphQL-schema;
* je GraphQL query&#39;s sturen,
* de antwoorden ontvangen (op je GraphQL-vragen).

Er zijn twee soorten eindpunten in AEM:

* Algemeen
   * Beschikbaar voor gebruik door alle sites.
   * Dit eindpunt kan alle Modellen van het Fragment van de Inhoud van alle configuraties van Plaatsen gebruiken (die in [ Browser van de Configuratie ](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) worden bepaald).
   * Als er om het even welke Modellen van het Fragment van de Inhoud zijn die onder de configuraties van Plaatsen zouden moeten worden gedeeld, dan zouden deze onder de globale configuraties van Plaatsen moeten worden gecreeerd.
* Siteconfiguraties:
   * Komt overeen met een configuratie van Plaatsen, zoals die in [ Browser van de Configuratie ](/help/assets/content-fragments/content-fragments-configuration-browser.md#enable-content-fragment-functionality-in-configuration-browser) wordt bepaald.
   * Specifiek voor een opgegeven site/project.
   * Een configuratie-specifiek eindpunt van Plaatsen zal de Modellen van het Fragment van de Inhoud van die specifieke configuratie van Plaatsen samen met die van de globale configuratie van Plaatsen gebruiken.

>[!CAUTION]
>
>Met de Inhoudsfragmenteditor kan een inhoudsfragment van een siteconfiguratie verwijzen naar een inhoudsfragment van een andere siteconfiguratie (via beleid).
>
>In een dergelijk geval zal niet alle inhoud kunnen terugwinnen gebruikend een de configuratie van Plaatsen specifiek eindpunt.
>
>De inhoudauteur zou dit scenario moeten controleren; bijvoorbeeld, kan het nuttig zijn om het plaatsen van gedeelde Modellen van het Fragment van de Inhoud onder de Globale configuratie van Plaatsen te overwegen.

Het globale eindpunt van de GraphQL for AEM is:

`/content/cq:graphql/global/endpoint`

Voor welke toepassing uw toepassing het volgende pad in de aanvraag-URL kan gebruiken:

`/content/_cq_graphql/global/endpoint.json`

Om een eindpunt voor GraphQL voor AEM toe te laten moet u:

* [GraphQL-eindpunt inschakelen](#enabling-graphql-endpoint)
* [GraphQL-eindpunt publiceren](#publishing-graphql-endpoint)

## GraphQL Endpoint inschakelen {#enabling-graphql-endpoint}

Om een Eindpunt van GraphQL toe te laten moet u eerst een aangewezen configuratie hebben. Zie [ de Fragmenten van de Inhoud - Browser van de Configuratie ](/help/assets/content-fragments/content-fragments-configuration-browser.md).

>[!CAUTION]
>
>Als het [ gebruik van de modellen van het inhoudsfragment niet ](/help/assets/content-fragments/content-fragments-configuration-browser.md) is toegelaten, **creeer** optie zal niet beschikbaar zijn.

Om het overeenkomstige eindpunt toe te laten:

1. Navigeer aan **Hulpmiddelen**, **Assets**, dan uitgezocht **GraphQL**.
1. Selecteer **creeer**.
1. **creeer nieuwe de dialoogdoos van het Eindpunt van GraphQL** opent. Hier kunt u opgeven:
   * **Naam**: naam van het eindpunt; u kunt om het even welke tekst ingaan.
   * **schema van GraphQL van het Gebruik dat door** wordt verstrekt: gebruik dropdown om de vereiste plaats/het project te selecteren.

   >[!NOTE]
   >
   >De volgende waarschuwing wordt weergegeven in het dialoogvenster:
   >
   >* *de eindpunten van GraphQL kunnen gegevensveiligheid en prestatieskwesties introduceren als niet zorgvuldig beheerd. Gelieve te verzekeren om aangewezen toestemmingen te plaatsen na het creëren van een eindpunt.*

1. Bevestig met **creeer**.
1. De **Volgende stappen** dialoog zal een directe verbinding aan de console van de Veiligheid verstrekken zodat u kunt verzekeren dat het onlangs gecreeerde eindpunt geschikte toestemmingen heeft.

   >[!CAUTION]
   >
   >Het eindpunt is toegankelijk voor iedereen. Dit kan - vooral bij publicatieinstanties - een veiligheidszorg veroorzaken, aangezien de vragen van GraphQL een zware lading op de server kunnen opleggen.
   >
   >U kunt opstelling ACLs, aangewezen aan uw gebruiksgeval, op het eindpunt.

## GraphQL Endpoint publiceren {#publishing-graphql-endpoint}

Selecteer het nieuwe eindpunt en **publiceer** om het volledig beschikbaar te maken in alle milieu&#39;s.

>[!CAUTION]
>
>Het eindpunt is toegankelijk voor iedereen.
>
>Bij het publiceren van instanties kan dit een veiligheidszorg veroorzaken, aangezien de vragen van GraphQL een zware lading op de server kunnen opleggen.
>
>Opstelling ACLs aangewezen aan uw gebruiksgeval op het eindpunt.
