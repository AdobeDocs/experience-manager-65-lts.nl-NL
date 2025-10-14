---
title: JSON-exportfunctie voor services voor inhoud
description: AEM Content Services is ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, maar niet alleen op webpagina's. Ze leveren inhoud aan kanalen die geen traditionele AEM-webpagina's zijn, met behulp van gestandaardiseerde methoden die door elke client kunnen worden gebruikt.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 8c66b978-872e-4f5e-8f64-1e2dfb7d7dde
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '411'
ht-degree: 0%

---

# JSON-exportfunctie voor services voor inhoud{#json-exporter-for-content-services}

AEM Content Services is ontworpen om de beschrijving en levering van inhoud in of vanuit AEM te veralgemenen, maar niet alleen op webpagina&#39;s.

Ze leveren inhoud aan kanalen die geen traditionele AEM-webpagina&#39;s zijn, met behulp van gestandaardiseerde methoden die door elke client kunnen worden gebruikt. Deze kanalen kunnen zijn:

* [Toepassingen voor één pagina](spa-walkthrough.md)
* Systeemeigen mobiele toepassingen
* andere kanalen en aanraakpunten buiten AEM

Met inhoudsfragmenten die gestructureerde inhoud gebruiken, kunt u inhoudsdiensten verlenen door de JSON-exporter te gebruiken om de inhoud van een AEM-pagina in JSON-gegevensmodelindeling te leveren. Deze methode kan vervolgens door uw eigen toepassingen worden gebruikt.

>[!NOTE]
>
>De hier beschreven functionaliteit is beschikbaar voor alle Componenten van de Kern sinds [&#x200B; versie 1.1.0 van de Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL).

## JSON-exportfunctie met kerncomponenten van inhoudsfragment {#json-exporter-with-content-fragment-core-components}

Met de AEM JSON-exportfunctie kunt u de inhoud van elke AEM-pagina in JSON-indeling voor gegevensmodellen leveren. Deze methode kan vervolgens door uw eigen toepassingen worden gebruikt.

In AEM wordt de levering uitgevoerd met de extensie selector `model` en `.json` .

`.model.json`

1. Bijvoorbeeld een URL zoals:

   ```shell
   http://localhost:4502/content/we-retail/language-masters/en.model.json
   ```

1. Levert inhoud zoals:

   ![&#x200B; chlimage_1-192 &#x200B;](assets/chlimage_1-192.png)

U kunt de inhoud van een gestructureerd inhoudsfragment ook leveren door dit specifiek te activeren.

Gebruik het volledige pad naar het fragment (als `jcr:content` ), bijvoorbeeld met een achtervoegsel zoals.

`.../jcr:content/root/responsivegrid/contentfragment.model.json`

De pagina kan één inhoudsfragment of meerdere componenten van verschillende typen bevatten. U kunt mechanismen zoals lijstcomponenten ook gebruiken om automatisch naar relevante inhoud te zoeken.

* Bijvoorbeeld een URL zoals:

  ```shell
  http://localhost:4502/content/we-retail/language-masters/en/manchester-airport/jcr:content/root/responsivegrid/contentfragment.model.json
  ```

* Levert inhoud zoals:

  ![&#x200B; chlimage_1-193 &#x200B;](assets/chlimage_1-193.png)

  >[!NOTE]
  >
  >U kunt [&#x200B; uw eigen componenten &#x200B;](/help/sites-developing/json-exporter-components.md) aanpassen om tot dit gegeven toegang te hebben en te gebruiken.

  >[!NOTE]
  >
  >Hoewel niet een standaardimplementatie, [&#x200B; veelvoudige selecteurs worden gesteund, &#x200B;](json-exporter-components.md#multiple-selectors) maar `model` moet de eerste zijn.

### Aanvullende informatie {#further-information}

Zie ook:

* ASSETS HTTP API

   * [ASSETS HTTP API](/help/assets/mac-api-assets.md)

* Modellen voor verkopen:

   * [&#x200B; het Verdelen Modellen - het associëren van een modelklasse met een middeltype sinds 130 &#x200B;](https://sling.apache.org/documentation/bundles/models.html#associating-a-model-class-with-a-resource-type-since-130)

* AEM met JSON:

   * [Pagina-informatie ophalen in JSON-indeling](/help/sites-developing/pageinfo.md)

## Verwante documentatie {#related-documentation}

Zie voor meer informatie:

* Het [&#x200B; onderwerp van de Fragmenten van de Inhoud in de gebruikersgids van Assets &#x200B;](/help/assets/content-fragments/content-fragments.md)

* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-export inschakelen voor een component](/help/sites-developing/json-exporter-components.md)

* [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/introduction.html?lang=nl-NL) en de [&#x200B; component van het Fragment van de Inhoud &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/content-fragment-component.html?lang=nl-NL)
