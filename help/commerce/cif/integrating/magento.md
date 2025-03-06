---
title: AEM- en Adobe Commerce-integratie met Commerce integration framework
description: AEM en Adobe Commerce zijn naadloos geïntegreerd met Commerce integration framework (CIF). CIF stelt AEM in staat toegang te krijgen tot een Adobe Commerce-exemplaar en te communiceren met Adobe Commerce via GraphQL. AEM-auteurs kunnen ook Product- en rubriekkiezers en de productconsole gebruiken om door producten en categoriegegevens te bladeren die op verzoek van Adobe Commerce zijn opgehaald. Daarnaast biedt CIF een winkel die de handelsprojecten kan versnellen.
thumbnail: aem-magento-architecture.jpg
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: cecd9591-bff4-4b4e-a3fd-4ab4278a0b81
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '343'
ht-degree: 0%

---

# Integratie van AEM en Adobe Commerce (Magento) met Commerce integration framework {#aem-commerce-framework}

De Experience Manager en Adobe Commerce zijn naadloos geïntegreerd met Commerce integration framework (CIF). CIF laat AEM toe om tot direct toegang te hebben en met de handelsinstantie te communiceren gebruikend Adobe Commerce [ GraphQL APIs ](https://devdocs.magento.com/guides/v2.4/graphql/).

>[!NOTE]
>
>De minimaal ondersteunde GraphQL API-versie is 2.3.5. Bepaalde functies worden alleen ondersteund in nieuwere versies of alleen in de Adobe Commerce-editie.

## Overzicht van architectuur {#overview}

De architectuur ziet er als volgt uit:

![ het Overzicht van de Architectuur van CIF ](../assets/AEM_Magento_Architecture.png)

Binnen CIF is er ondersteuning voor communicatiepatronen aan de serverzijde en de client.
De server-kant APIs vraag wordt uitgevoerd gebruikend de bouwstijl-binnen, generische [ cliënt van GraphQL ](https://github.com/adobe/commerce-cif-graphql-client) in combinatie met a [ reeks geproduceerde gegevensmodellen ](https://github.com/adobe/commerce-cif-magento-graphql) voor het schema van handelsGraphQL. Daarnaast kan elke GraphQL-query of -mutatie in GQL-indeling worden gebruikt.

Voor de cliënt-zijcomponenten, die gebruikend [ React ](https://reactjs.org/) bouwen, wordt de [ Cliënt van Apollo ](https://www.apollographql.com/docs/react/) gebruikt.

## AEM CIF Core-componentarchitectuur {#cif-core-components}

![ de Architectuur van de Component van de Kern van AEM CIF ](../assets/cif-component-architecture.jpg)

{de Componenten van de Kern van AEM CIF van 0} ](https://github.com/adobe/aem-core-cif-components) volgen zeer gelijkaardige ontwerppatronen en beste praktijken zoals [ de Componenten van de Kern van AEM WCM ](https://github.com/adobe/aem-core-wcm-components).[

De bedrijfslogica en de achtergrondcommunicatie met Adobe Commerce voor de AEM CIF Core Components worden geïmplementeerd in Sling Models. Als deze logica moet worden aangepast om aan projectspecifieke vereisten te voldoen, kan het delegatiepatroon voor Sling Models worden gebruikt.

>[!TIP]
>
>[ het Aanpassen van de Componenten van de Kern van AEM CIF ](../customizing/customize-cif-components.md) pagina heeft een gedetailleerd voorbeeld en beste praktijken op hoe te om de Componenten van de Kern van CIF aan te passen.

Binnen projecten, kunnen de Componenten van de Kern van AEM CIF en de componenten van het douaneproject de gevormde cliënt voor een opslag van Adobe Commerce gemakkelijk terugwinnen verbonden aan een pagina van AEM via het Verdelen van context-Aware configuratie.
