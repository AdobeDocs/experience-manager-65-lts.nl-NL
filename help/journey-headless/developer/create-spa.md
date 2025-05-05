---
title: Optioneel - Hoe kunt u toepassingen voor één pagina (SPA's) maken met Adobe Experience Manager
description: In deze facultatieve voortzetting van de Journey van de Ontwikkelaar van Adobe Experience Manager (AEM) Headless, leert u hoe AEM koploze levering met traditionele full-stack eigenschappen van CMS kan combineren en hoe u editable SPAs kunt tot stand brengen gebruikend het kader van de Redacteur van het KUUROORD van AEM.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments
role: Admin, Developer
exl-id: 47e73efa-997d-44d9-bb41-6f550eac137a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1248'
ht-degree: 0%

---

# Hoe te om de Toepassingen van de Enige Pagina (SPAs) met AEM te creëren {#create-spa}

In deze facultatieve voortzetting van de [ Hoofdloze Reis van de Ontwikkelaar van AEM, ](overview.md) leert u hoe Adobe Experience Manager (AEM) koploze levering met traditionele full-stack eigenschappen van CMS kan combineren en hoe u editable SPAs kunt creëren gebruikend het kader van de Redacteur van het KUUROORD van AEM, en externe SPAs integreren, toelatend mogelijkheden zoals vereist.

## Het verhaal tot nu toe {#story-so-far}

Op dit punt, zou u de volledige [ Reis van de Ontwikkelaar van AEM Headless ](overview.md) moeten voltooien en de grondbeginselen van hoofdloze levering in AEM begrijpen met inbegrip van het begrip van:

* Het verschil tussen koploze en koprijke levering van inhoud.
* AEM-functies zonder kop.
* Hoe organiseren en AEM Headless-project.
* Hoe u inhoud zonder kop maakt in AEM.
* Inhoud zonder kop ophalen en bijwerken in AEM.
* Hoe ga je leven met een AEM Headless-project.

Dus je bent nu ofwel gaan leven met je eerste AEM Headless-project, of je hebt de kennis om dat te doen. Gefeliciteerd!

Waarom leest u deze extra, optionele voortzetting van de reis? Vergelijkbaar, herinnert u eraan dat in [ Begonnen ](getting-started.md#integration-levels), er een korte bespreking over was hoe AEM niet alleen hoofdloze levering en traditionele full-stack modellen steunt, maar ook hybride modellen kan steunen die de voordelen van allebei combineren. Hoewel niet het traditionele model zonder kop, kunnen dergelijke hybride modellen ongekende flexibiliteit aan bepaalde projecten aanbieden.

Dit artikel bouwt op uw kennis van AEM Headless voort door diepgaand te onderzoeken hoe u uw eigen single-page toepassingen (SPAs) kunt tot stand brengen die in AEM editable zijn. Op deze manier, kunt u inhoud tot stand brengen en het leiden zonder kop aan een KUUROORD, maar dat KUUROORD editable in AEM blijft.

## Doelstelling {#objective}

Dit document helpt u begrijpen hoe Toepassingen van de Enige Pagina gebruikend het kader van de Redacteur van AEM SPA worden ontwikkeld. Nadat u dit document hebt gelezen, moet u:

* Begrijp de basisfunctie van de Redacteur van het KUUROORD.
* Weet de vereisten voor de bouw van volledig editable SPA voor AEM.
* Begrijp hoe externe SPAs in AEM kan worden geïntegreerd.
* Begrijp hoe rendering op de server al dan niet moet worden geïmplementeerd.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verscheidene vereisten alvorens u met SPAs in AEM begint te werken.

### Kennis {#knowledge}

* Ervaring met het maken van SPA&#39;s met React- of Angular-frameworks
* Basisvaardigheden van AEM die tot de Fragmenten van de Inhoud leiden en redacteur gebruiken
* Ben zeker om het document [ te herzien Kopieer en Zwaartepunt in AEM ](/help/sites-developing/headful-headless.md) om de diverse niveaus van integratie van het KUUROORD mogelijk te begrijpen.

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA (facultatief, afhankelijk van welk integratiemodel wordt gekozen)
* AEM Project Archetype

## Wat is een SPA? {#what-is-a-spa}

Een single-page toepassing (SPA) verschilt van een conventionele pagina in die zin dat het cliënt-kant wordt teruggegeven en hoofdzakelijk JavaScript-gedreven, die op Ajax vraag baseert om gegevens te laden en dynamisch de pagina bij te werken. De meeste of alle inhoud wordt één keer opgehaald in één pagina die wordt geladen met extra bronnen die asynchroon worden geladen, afhankelijk van gebruikersinteractie met de pagina.

Hierdoor is het minder nodig pagina&#39;s te vernieuwen en wordt de gebruiker een ervaring geboden die naadloos, snel is en meer lijkt op een native app-ervaring.

De redacteur van AEM SPA staat front-end ontwikkelaars toe om SPAs tot stand te brengen die in een plaats van AEM kan worden geïntegreerd, toestaand de inhoudsauteurs om de inhoud van het KUUROORD zo gemakkelijk als om het even welke andere inhoud van AEM uit te geven.

## Waarom een SPA? {#why-spa}

Door sneller, dynamisch, en meer als een inheemse toepassing te zijn, wordt een SPA een aantrekkelijke ervaring niet alleen voor de bezoeker van de webpagina, maar ook voor marketers en ontwikkelaars toe te schrijven aan de aard van hoe SPAs werkt.

Voor een volledige beschrijving van SPAs en waarom u hen zou gebruiken, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Hoe AEM SPA&#39;s afhandelt

Het ontwikkelen van enige paginatoepassingen op AEM veronderstelt dat de front-end ontwikkelaar standaardbeste praktijken wanneer het creëren van een SPA naleeft. Als front-end ontwikkelaar, als u deze algemene beste praktijken en een paar AEM-specifieke principes volgt, zal uw SPA functioneel met AEM en zijn inhoud-creatie mogelijkheden zijn.

* **Portability** - zoals met om het even welke componenten, zouden de componenten van het KUUROORD moeten worden gebouwd om zo draagbaar mogelijk te zijn. Het KUUROORD zou met draaglijk en herbruikbare componenten moeten worden gebouwd.
* **AEM drijft de Structuur van de Plaats van de Plaats** - de front-end ontwikkelaar leidt tot componenten en bezit hun interne structuur, maar baseert zich op AEM om de inhoudsstructuur van de plaats te bepalen.
* **Dynamische Rendering** - allen zou het teruggeven dynamisch moeten zijn.
* **Dynamisch Verpletterend** - het KUUROORD is verantwoordelijk voor het verpletteren en AEM luistert aan het en haalt die op het wordt gebaseerd. Om het even welk verpletteren zou ook dynamisch moeten zijn.

Voor een volledige beschrijving van hoe AEM SPAs behandelt, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaande documentatie.

## De AEM SPA-editor {#aem-spa-editor}

De plaatsen die gebruikend gemeenschappelijke kaders van het KUUROORD zoals React en Angular worden gebouwd laden hun inhoud via dynamische JSON en verstrekken niet de structuur van HTML die voor de Redacteur van de Pagina van AEM noodzakelijk is om bewerkingscontroles te kunnen plaatsen.

Om het uitgeven van SPAs binnen AEM toe te laten, is een afbeelding tussen de output JSON van het KUUROORD en het inhoudsmodel in de bewaarplaats van AEM nodig om veranderingen in de inhoud te bewaren.

De steun van het KUUROORD in AEM introduceert een dunne laag JS die met de code van het KUUROORD JS wanneer geladen in de Redacteur van de Pagina interactie heeft waarmee de gebeurtenissen kunnen worden verzonden en de plaats voor uitgeeft controles kunnen worden geactiveerd om in-context het uitgeven toe te staan. Deze eigenschap bouwt op het concept van het Eindpunt van de Diensten van de Inhoud API voort omdat de inhoud van het KUUROORD als Diensten van de Inhoud moet worden geladen.

Voor een volledige beschrijving van de Redacteur van AEM SPA, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Bestaande SPA&#39;s aanpassen {#existing-spas}

Als u een bestaande SPA hebt, biedt AEM ondersteuning voor het insluiten van de SPA in AEM, zodat deze zichtbaar is voor de auteurs van de inhoud in de AEM Editor. Dit kan handig zijn om de inhoud die ze maken, weer te geven via Content Fragments in de context van de eindtoepassing waarin deze wordt gebruikt.

Ook, met slechts kleine veranderingen, kunt u bepaalde het uitgeven capaciteit aan het externe KUUROORD binnen de Redacteur van AEM toelaten.

De component RemotePage staat het teruggeven van een externe SPA in AEM toe.

Voor een volledige beschrijving van hoe te om een externe KUUROORD editable in AEM te maken, zie de [ extra middelen ](#additional-resources) sectie voor verbindingen aan diepgaandere documentatie.

## Volgende functies {#what-is-next}

Ga als volgt te werk om uw eigen SPA&#39;s voor AEM te gaan ontwikkelen:

* [SPA WKND-zelfstudie](/help/sites-developing/spa-wknd.md)
* [Aan de slag met Reageren](/help/sites-developing/spa-getting-started-react.md)
* [Aan de slag met Angular](/help/sites-developing/spa-getting-started-angular.md)

Als u bestaande SPA moet aanpassen om het in AEM te gebruiken, herzie de volgende documenten:

* [De RemotePage-component](/help/sites-developing/spa-remote-page.md)
* [Een externe SPA bewerken in AEM](/help/sites-developing/spa-edit-external.md)

Zie hieronder voor [ extra middelen ](#additional-resources) die u dieper in de onderwerpen van het KUUROORD in AEM kunnen nemen.

## Aanvullende bronnen {#additional-resources}

Hieronder vindt u een aantal aanvullende bronnen die dieper ingaan op bepaalde concepten die in dit document worden genoemd.

* [ Kopieerbaar en Hoofdloos in AEM ](/help/sites-developing/headful-headless.md) - een beschrijving van de verschillende leveringsmodellen beschikbaar in AEM
* [ Inleiding en Analyse van het KUUROORD.](/help/sites-developing/spa-walkthrough.md) - Een goede inleiding aan SPAs in AEM
* [ het Ontwikkelen SPAs voor AEM ](/help/sites-developing/spa-architecture.md) - Richtlijnen op hoe te om SPAs voor AEM te ontwikkelen
* [ Overzicht van de Redacteur van het KUUROORD ](/help/sites-developing/spa-overview.md) - Details van hoe de Redacteur van het KUUROORD werkt
* [ Documenten van de Verwijzing van het KUUROORD ](/help/sites-developing/spa-reference-materials.md) - de verwijzingen van JavaScript API en verbindingen aan de open-bron projecten van AEM SPA GitHub
* [ Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) - hoe te om de Fragmenten van de Inhoud tot stand te brengen
* [ Archetype van het Project van AEM ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/developing/archetype/overview.html?lang=nl-NL) - Geweven malplaatje dat tot een minimaal, best-practices-gebaseerd project van Adobe Experience Manager (AEM) als uitgangspunt voor uw website leidt
