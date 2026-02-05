---
title: JSON-export inschakelen voor een component
description: Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.
contentOwner: User
content-type: reference
topic-tags: components
products: SG_EXPERIENCEMANAGER/6.5/SITES
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: aeb8e954-dd6c-4e18-bb78-6eaac86fa4b9
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '464'
ht-degree: 0%

---

# JSON-export inschakelen voor een component{#enabling-json-export-for-a-component}

Componenten kunnen worden aangepast om JSON-export van hun inhoud te genereren op basis van een modellerframework.

## Overzicht {#overview}

De uitvoer JSON is gebaseerd op [ Verschuivende Modellen ](https://sling.apache.org/documentation/bundles/models.html), en op het [ Verschuiven ModelExporter ](https://sling.apache.org/documentation/bundles/models.html#exporter-framework-since-130) kader (dat zelf op [ Jackson annotations ](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) vertrouwt).

Deze benadering betekent dat de component een Sling Model moet hebben als het JSON moet uitvoeren. Voer daarom de volgende twee stappen uit om JSON-export voor een willekeurige component mogelijk te maken.

* [Definieer een verkoopmodel voor de component](/help/sites-developing/json-exporter-components.md#define-a-sling-model-for-the-component)
* [Annoteer de interface van het Verkoopmodel](#annotate-the-sling-model-interface)

## Definieer een verkoopmodel voor de component {#define-a-sling-model-for-the-component}

Ten eerste moet een Sling-model worden gedefinieerd voor de component.

>[!NOTE]
>
>Voor een voorbeeld om het Verdelen Modellen te gebruiken, zie [ het Ontwikkelen van het Verdelen ModelExporters in AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/foundation/development/develop-sling-model-exporter).

De implementatieklasse Sling Model moet met het volgende worden geannoteerd:

```java
@Model(... adapters = {..., ComponentExporter.class})
@Exporter(name = ExporterConstants.SLING_MODEL_EXPORTER_NAME, extensions = ExporterConstants.SLING_MODEL_EXTENSION)
@JsonSerialize(as = MyComponent.class)
```

Zo weet u zeker dat de component zelfstandig kan worden geëxporteerd met de extensie `.model` kiezer en `.json` .

Bovendien wordt hiermee aangegeven dat de klasse Sling Model kan worden aangepast in de interface `ComponentExporter` .

>[!NOTE]
>
>Jackson-annotaties worden niet opgegeven op het klasseniveau Sling Model, maar wel op het interfaceniveau Model. Deze aanpak moet ervoor zorgen dat de JSON-export wordt beschouwd als onderdeel van de API voor componenten.

>[!NOTE]
>
>De klassen `ExporterConstants` en `ComponentExporter` zijn afkomstig uit de `com.adobe.cq.export.json` -bundel.

### Meerdere kiezers gebruiken {#multiple-selectors}

Hoewel het geen standaard gebruikscase is, is het mogelijk om meerdere kiezers te configureren naast de kiezer van `model` .

```
https://<server>:<port>/content/page.model.selector1.selector2.json
```

In een dergelijk geval moet de `model` kiezer echter de eerste kiezer zijn en moet de extensie `.json` zijn.

## Annoteer de interface van het Verkoopmodel {#annotate-the-sling-model-interface}

Het JSON Exporter-framework kan dit alleen verwerken als de Model-interface de `ComponentExporter` -interface (of `ContainerExporter` voor een containercomponent) implementeert.

De overeenkomstige het Verdelen Model interface ( `MyComponent`) zou dan worden geannoteerd gebruikend [ de annotaties van Jackson ](https://github.com/FasterXML/jackson-annotations/wiki/Jackson-Annotations) om te bepalen hoe het (geserialiseerd) zou moeten worden uitgevoerd.

De modelinterface moet behoorlijk worden geannoteerd om te bepalen welke methodes in series worden vervaardigd. Standaard worden alle methoden die de gebruikelijke naamgevingsconventie voor getters respecteren, geserialiseerd en worden de JSON-eigenschapnamen op natuurlijke wijze afgeleid van de namen van getters. Deze benadering kan worden voorkomen of overschreven door `@JsonIgnore` of `@JsonProperty` te gebruiken om de naam van de JSON-eigenschap te wijzigen.

## Voorbeeld {#example}

De Componenten van de Kern hebben de uitvoer JSON sinds versie [ 1.1.0 van de kerncomponenten ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) gesteund en kunnen als verwijzing worden gebruikt.

Een voorbeeld vindt u in de implementatie Sling Model van de Image Core-component en de bijbehorende geannoteerde interface.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden

* [ open aem-kern-wcm-componenten project op GitHub ](https://github.com/adobe/aem-core-wcm-components)
* Download het project als [ een dossier van het PIT ](https://codeload.github.com/adobe/aem-core-wcm-components/zip/main)


## Gerelateerde documentatie {#related-documentation}

* Het [ onderwerp van de Fragmenten van de Inhoud in de gebruikersgids van Assets ](https://experienceleague.adobe.com/en/docs/experience-manager-64/assets/home#)
* [Modellen van inhoudsfragmenten](/help/assets/content-fragments/content-fragments-models.md)
* [Ontwerpen met inhoudsfragmenten](/help/sites-authoring/content-fragments.md)
* [JSON-exportfunctie voor services voor inhoud](/help/sites-developing/json-exporter.md)
* [ Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) en de [ component van het Fragment van de Inhoud ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/wcm-components/content-fragment-component)
