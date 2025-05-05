---
title: Caching en prestaties
description: Leer over de verschillende beschikbare configuraties om GraphQL en inhoud het in cache plaatsen toe te laten om de prestaties van uw handelsimplementatie te optimaliseren.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 7da2c607-b407-4e4b-bfba-bfaa78aff475
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '821'
ht-degree: 0%

---

# Caching en prestaties {#caching}

## Component &amp; GraphQL Response Caching {#graphql}

De AEM CIF Core-componenten beschikken al over geïntegreerde ondersteuning voor het in cache plaatsen van GraphQL-reacties voor afzonderlijke componenten. Deze functie kan worden gebruikt om het aantal GraphQL backend vraag met een grote factor te verminderen. Een efficiënte caching kan vooral voor het herhalen van vragen zoals het terugwinnen van de categorieboom voor een navigatiecomponent of het halen van alle beschikbare samenvoegingen/facetwaarden worden bereikt die op de productonderzoek en categoriepagina&#39;s worden getoond.

Voor de AEM CIF Core-componenten wordt caching geconfigureerd op componentbasis, zodat het mogelijk is om te bepalen of (en hoe lang) GraphQL-verzoeken/-reacties voor elke component in de cache worden opgeslagen. Het is ook mogelijk om het caching gedrag voor de diensten te bepalen OSGi gebruikend de cliënt van GraphQL.

### Configuratie

Zodra gevormd voor een bepaalde component, begint het geheime voorgeheugen GraphQL vragen en antwoorden zoals die door elke ingang van de geheim voorgeheugenconfiguratie worden bepaald op te slaan. De grootte van het geheime voorgeheugen en de in het voorgeheugen onderbrengingsduur van elke ingang moeten op een projectbasis worden bepaald, afhankelijk bijvoorbeeld, op hoe vaak de catalogusgegevens zouden kunnen veranderen, hoe kritiek het is dat een component altijd de recentste mogelijke gegevens toont, etc. Merk op dat er geen geheim voorgeheugenongeldigverklaring is, zodat ben zorgvuldig wanneer het plaatsen van de geheim voorgeheugenduur.

Wanneer het vormen caching voor componenten, moet de geheim voorgeheugennaam de naam van de **volmacht** componenten zijn die u in uw project bepaalt.

Alvorens de cliënt een verzoek van GraphQL verzendt, controleert het als dat **nauwkeurig** zelfde verzoek van GraphQL reeds in het voorgeheugen ondergebracht is en misschien de caching reactie terugkeert. Om overeen te komen, MOET de GraphQL- verzoek precies aanpassen, namelijk de vraag, verrichtingsnaam (als om het even welk), variabelen (als om het even welk) moeten allen aan het caching verzoek gelijk zijn, en ook alle kopballen van douaneHTTP die zouden kunnen worden geplaatst MOET het zelfde zijn. De Adobe Commerce `Store` -header MOET bijvoorbeeld overeenkomen.

### Voorbeelden

Wij adviseren dat om wat caching voor de onderzoeksdienst te vormen die alle beschikbare samenvoegingen/facetwaarden haalt die op het productonderzoek en categoriepagina&#39;s worden getoond. Deze waarden veranderen doorgaans alleen wanneer een nieuw kenmerk bijvoorbeeld wordt toegevoegd aan producten, zodat de duur voor deze cachevermelding &quot;groot&quot; kan zijn als de set met productkenmerken niet vaak wordt gewijzigd. Hoewel dit projectspecifiek is, beveelt Adobe waarden aan van een paar minuten in projectontwikkelingsfasen en een paar uur in stabiele productiesystemen.

Dit wordt typisch gevormd met de volgende geheim voorgeheugeningang:

```
com.adobe.cq.commerce.core.search.services.SearchFilterService:true:10:3600
```

Een ander voorbeeldscenario waar de eigenschap GraphQl in het voorgeheugen onderbrengend wordt geadviseerd om te worden gebruikt is de navigatiecomponent omdat het de zelfde vraag van GraphQL op alle pagina&#39;s verzendt. In dit geval wordt de cachevermelding doorgaans ingesteld op:

```
venia/components/structure/navigation:true:10:600
```

Wanneer het overwegen van de [ opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt gebruikt. Neem nota van het gebruik van de naam van de componentenvolmacht `venia/components/structure/navigation`, en **niet** de naam van de navigatiecomponent van CIF (`core/cif/components/structure/navigation/v1/navigation`).

Caching voor andere componenten zou op projectbasis, gewoonlijk in coördinatie met caching moeten worden bepaald die op het niveau van Dispatcher wordt gevormd. Herinner dat er geen actieve ongeldigverklaring van deze geheime voorgeheugens is, zodat zou de caching duur zorgvuldig moeten worden geplaatst. Er zijn geen standaardwaarden die overeenkomen met alle mogelijke projecten en gebruiksgevallen. Zorg ervoor dat u een caching strategie op het projectniveau bepaalt die het best de vereisten van uw project aanpast.

## Dispatcher Caching {#dispatcher}

Het in cache plaatsen van AEM pagina&#39;s of fragmenten in [ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL) is een beste praktijk voor om het even welk project van AEM. Doorgaans is dit afhankelijk van validatietechnieken die ervoor zorgen dat alle inhoud die in AEM is gewijzigd, correct wordt bijgewerkt in de Dispatcher. Dit is een kernelement van de AEM Dispatcher caching-strategie.

Naast zuivere door AEM beheerde inhoud kan CIF op een pagina gewoonlijk handelsgegevens weergeven die dynamisch van Adobe Commerce via GraphQL worden opgehaald. Hoewel de paginastructuur zelf misschien nooit verandert, kan de commerciële inhoud veranderen, bijvoorbeeld, als sommige productgegevens (zoals naam of prijs) in Adobe Commerce veranderen.

Om ervoor te zorgen dat de pagina&#39;s van CIF voor een beperkte hoeveelheid tijd in AEM Dispatcher kunnen worden in het voorgeheugen ondergebracht, adviseren wij daarom het gebruik van [ Op tijd gebaseerde Invalidatie van het Geheime voorgeheugen ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL#configuring-time-based-cache-invalidation-enablettl) (ook genoemd geworden op TTL-Gebaseerde caching) wanneer het in het voorgeheugen onderbrengen van de pagina&#39;s van CIF in AEM Dispatcher. Deze eigenschap kan in AEM met het gebruiken van het extra [ ACS AEM Commons ](https://adobe-consulting-services.github.io/acs-aem-commons/) pakket worden gevormd.

Met op TTL gebaseerde caching, bepaalt een ontwikkelaar typisch één of veelvoudige caching duur voor geselecteerde pagina&#39;s van AEM. Dit zorgt ervoor dat CIF-pagina&#39;s alleen in de AEM Dispatcher in de cache worden geplaatst tot de geconfigureerde duur en dat de inhoud regelmatig wordt bijgewerkt.

>[!NOTE]
>
>Hoewel gegevens aan de serverzijde door de AEM Dispatcher in cache kunnen worden opgeslagen, halen sommige CIF-componenten zoals de componenten `product` , `productlist` en `searchresults` doorgaans altijd de productprijzen opnieuw op in een browserverzoek aan de clientzijde wanneer de pagina wordt geladen. Dit zorgt ervoor dat cruciale dynamische inhoud altijd wordt opgehaald bij het laden van een pagina.

## Aanvullende bronnen

- [ de opslag van de Verwijzing van Venia ](https://github.com/adobe/aem-cif-guides-venia)
- [ GraphQL caching configuratie ](https://github.com/adobe/commerce-cif-graphql-client#caching)
- [ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/dispatcher.html?lang=nl-NL)
