---
title: We.Retail Reference Implementation
description: We.Retail is een technologische voorvertoning van een referentie-implementatie die de aanbevolen manier illustreert om een online aanwezigheid in te stellen met AEM
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 71a49353-5273-46ee-a1ff-5bbfe5b6b0b4
source-git-commit: c0bf6864bb344e582c4f88371c892d401ce2827c
workflow-type: tm+mt
source-wordcount: '688'
ht-degree: 0%

---

# `We.Retail` Referentie-implementatie{#we-retail-reference-implementation}

## Inleiding {#introduction}

De `We.Retail` -pagina&#39;s zijn een referentie-implementatie en voorbeeldinhoud die de aanbevolen manier illustreren om een online aanwezigheid in te stellen met Adobe Experience Manager.

De `We.Retail` -site gebruikt de nieuwste Adobe Experience Manager (AEM)-technologieën, zoals HTML, responsieve lay-outs, bewerkbare sjablonen, kerncomponenten en nog veel meer.

Hoewel het een verticale handelsversie illustreert, kan de manier waarop de site is ingesteld op elke verticale locatie worden toegepast, en zijn alleen de productcatalogus en de winkelwagenonderdelen specifiek.

## Functies {#features}

Als standaardimplementatie van de verwijzing van AEM, toont `We.Retail` enkele van de krachtigste eigenschappen van AEM.

| **Eigenschap** | **Beschrijving** | **Geïnteresseerd?** |
|---|---|---|
| [ Globalized plaatsstructuur ](/help/sites-administering/tc-bp.md) | `We.Retail` bevat pagina&#39;s voor de primaire taal die live worden gekopieerd naar landspecifieke sites. | [ probeer het!](/help/sites-developing/we-retail-globalized-site-structure.md) |
| [ Responsieve lay-out ](/help/sites-authoring/responsive-layout.md) | Alle pagina&#39;s hebben een responsieve indeling die dynamisch kan worden aangepast aan de grootte van het scherm en het apparaat. | [ probeer het!](/help/sites-developing/we-retail-responsive-layout.md) |
| [ Bewerkbare malplaatjes ](/help/sites-developing/page-templates-editable.md) | Alle pagina&#39;s zijn gebaseerd op bewerkbare sjablonen, waarmee niet-ontwikkelaars de sjablonen kunnen aanpassen en aanpassen. | [ probeer het!](/help/sites-developing/we-retail-editable-templates.md) |
| [ Taal van het Malplaatje van HTML ](https://experienceleague.adobe.com/en/docs/experience-manager-htl/content/overview) | Alle componenten zijn gebaseerd op HTML |  |
| [ Componenten van de Kern ](https://experienceleague.adobe.com/en/docs/experience-manager-core-components/using/introduction) | Alle componenten zijn gebaseerd op de nieuwe kerncomponenten en zijn bruikbaarder en gebruiker-configureerbaar uit-van-de-doos | [ probeer het!](/help/sites-developing/we-retail-core-components.md) |
| [Contentfragmenten](/help/assets/content-fragments/content-fragments.md) | In de sectie `We.Retail` Ervaring wordt de kracht getoond van het opnieuw gebruiken van inhoud door middel van inhoudsfragmenten. | [ probeer hen!](/help/sites-developing/we-retail-content-fragments.md) |
| [Ervaringsfragmenten](/help/sites-authoring/experience-fragments.md) | Een ervaringsfragment is een groep van een of meer componenten, inclusief inhoud en lay-out, waarnaar op pagina&#39;s kan worden verwezen. | [ probeer hen!](/help/sites-developing/we-retail-experience-fragments.md) |

## Aan de slag {#getting-started}

De `We.Retail` -site wordt geleverd als voorbeeldinhoud voor AEM. Om te gebruiken, eenvoudig [ begin AEM zoals u normaal ](/help/sites-deploying/deploy.md#getting-started) zou doen, ervoor zorgend dat de steekproefinhoud niet gehandicapt is.

>[!CAUTION]
>
>Installeer `We.Retail` niet op productieexemplaren. De instanties van de productie zouden op `nosamplecontent` [ looppaswijze ](/help/sites-deploying/configure-runmodes.md) moeten zijn begonnen.

>[!CAUTION]
>
>De `We.Retail` plaats is gebaseerd op de recentste technologie van AEM en steunt daarom niet [ klassieke UI creatie ](/help/sites-classic-ui-authoring/classic-page-author-first-steps.md).

### Laatste versie {#latest-version}

Hoewel `We.Retail` samen met de AEM-versie wordt gedistribueerd, kunnen updates voor de inhoud en de functies ervan na de release worden uitgevoerd. Daarom is het mogelijk om [ de recentste versie van GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases) te downloaden en dan [ ](/help/sites-administering/package-manager.md#uploading-packages-from-your-file-system) te uploaden en [ te installeren ](/help/sites-administering/package-manager.md#installing-packages) het als pakket op uw instantie van AEM.

### Eerste stappen {#first-steps}

1. Zodra AEM is begonnen (en/of `We.Retail` geïnstalleerd), is de plaats **`We.Retail`** beschikbaar in de [ console van Plaatsen ](/help/sites-authoring/basic-handling.md#global-navigation).
1. Bijvoorbeeld, kan de volgende pagina worden geopend en het zou moeten kijken zoals getoond in [ bijlage ](#appendix) hieronder:

   `https://<server name>:<port number>/editor.html/content/we-retail/language-masters/en.html`

## `We.Retail` en Geometrixx {#we-retail-geometrixx}

Geometrixx en zijn vele landen dienden als voorbeeldinhoud in vroegere versies van AEM. Sinds versie 6.3 is `We.Retail` de voorbeeldinhoud die bij AEM wordt geleverd en fungeert het als de nieuwe standaardimplementatie.

De `We.Retail` -site is technisch robuuster en maakt gebruik van de nieuwste AEM-technologie om flexibeler en schaalbaarder te zijn, terwijl de nieuwste kenmerken van het product ook worden getoond.

### Functievergelijking {#feature-comparison}

In de volgende tabel vindt u een overzicht van de belangrijkste functies die beschikbaar zijn in `We.Retail` in vergelijking met Geometrixx.

* **Beschikbaar** betekent dat de voorbeelden van de eigenschap in de steekproefinhoud worden gevonden.
* **niet beschikbaar** betekent dat de steekproefinhoud van eigenschapvoorbeelden, maar de eigenschap kan nog beschikbaar zijn.


| **Eigenschap** | **`We.Retail`** | **Geometrixx** |
|---|---|---|
| Globale sitestructuur | Pagina&#39;s in de primaire taal worden live gekopieerd naar landspecifieke sites | Niet beschikbaar |
| Inhoudsfragmenten | Beschikbaar | Niet beschikbaar |
| Ervaar fragmenten | Beschikbaar | Niet beschikbaar |
| Responsieve lay-out | Voor alle pagina&#39;s | Alleen Geometrixx Media |
| Bewerkbare sjablonen | Voor alle pagina&#39;s | Niet beschikbaar |
| HTL | Alle componenten | Beperkt |
| Targeting | Voor alle pagina&#39;s | Alleen Geometrixx Outdoors |
| Manuscripts | Niet beschikbaar | Beschikbaar |
| Carousel-viewer, -downloads en -diagramonderdelen | Niet beschikbaar | Beschikbaar |
| Kolombesturingselement | Vervangen door opmaakcontainer | Beschikbaar |
| Forms | Niet beschikbaar | Beschikbaar |
| Campagne | Geen e-mailvoorbeelden | Beschikbaar |

>[!NOTE]
>
>Deze lijst is volledig, maar mag niet als volledig worden beschouwd.

## Contribute {#contribute}

De `We.Retail` plaats wordt vrijgegeven als open-bronproject en de recentste versie van de broncode kan van GitHub worden gedownload.

CODE VOOR GITHUB

U kunt de code van deze pagina op GitHub vinden.

* [ open a-sample-wij-kleinhandelsproject op GitHub ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail)
* Download het project als [ een dossier van het PIT ](https://codeload.github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/zip/refs/heads/master)

De recentste versie kan ook [ direct ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/releases/tag/we.retail.reactor-4.0.0) als installable pakket worden gedownload.

Als u problemen ontmoet, dossier a [ GitHub kwestie ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/issues).

Voel vrij om met [ trekkingsverzoeken ](https://github.com/Adobe-Marketing-Cloud/aem-sample-we-retail/pulls) bij te dragen.

## Voorvertoning {#preview}

Voorbeeld van de welkomstpagina van `We.Retail` :

![ screencapture-localhost-4502-editor-html-content-we-retail-us-nl-html-2018-08-17-14_33_32 ](assets/screencapture-localhost-4502-editor-html-content-we-retail-us-en-html-2018-08-17-14_33_32.png)
