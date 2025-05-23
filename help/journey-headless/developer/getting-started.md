---
title: Aan de slag met AEM Headless
description: In dit deel van de AEM Headless Developer Journey, leer je over AEM Headless-voorwaarden.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin, Developer
exl-id: 2bae83cc-ad0e-4a6a-a56e-1aa6533bde7e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2999'
ht-degree: 0%

---

# Aan de slag met AEM Headless {#getting-started}

In dit deel van de [ Hoofdloze Reis van de Ontwikkelaar van AEM, ](overview.md) leert over wat wordt vereist om uw eigen project te krijgen begonnen met AEM Headless.

## Het verhaal tot nu toe {#story-so-far}

In het vorige document van de hoofdloze reis van AEM, [ Leer over de Hoofdloze Ontwikkeling van CMS ](learn-about.md) u de basistheorie van leerde wat een headless CMS is en u zou nu moeten:

* Begrijp de basisconcepten en de terminologie van de inhoud zonder kop levering
* Begrijpen waarom en wanneer een kop zonder kop nodig is
* Op hoog niveau weten hoe concepten zonder kop worden gebruikt en hoe ze met elkaar verweven zijn

Dit artikel bouwt op die grondbeginselen voort zodat begrijpt u hoe u AEM kunt gebruiken om een headless oplossing uit te voeren.

## Doelstelling {#objective}

Dit document helpt u AEM Headless te begrijpen in de context van uw eigen project. Na het lezen moet u:

* Begrijp de basisbeginselen van de AEM-functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u de AEM-functies zonder kop moet gebruiken.
* Wees op de hoogte van AEM&#39;s instapniveau.
* U kunt uw project definiëren in termen van bereik.

## AEM Basics {#aem-basics}

Voordat u een project zonder kop kunt definiëren in AEM, is het belangrijk dat u een aantal basisbeginselen van AEM begrijpt.

### Instantie van auteur {#author}

Bij zijn eenvoudigst, bestaat AEM uit een auteursinstantie en a [ publiceer instantie ](#publish) die samenwerken om, uw inhoud tot stand te brengen te beheren en te publiceren.

Inhoud begint op de instantie van de auteur. Op deze manier maken auteurs van inhoud hun inhoud. De auteursomgeving biedt diverse hulpmiddelen voor auteurs aan om hun inhoud tot stand te brengen, te organiseren en opnieuw te gebruiken.

### Exemplaar publiceren {#publish}

Wanneer de inhoud in de auteurinstantie is gemaakt, moet deze worden gepubliceerd om beschikbaar te zijn voor andere services. Een publicatie-instantie bevat alle inhoud die is gepubliceerd.

### Replicatie {#replication}

Replicatie is het overbrengen van inhoud van de auteurinstantie naar de publicatie-instantie. Dit wordt automatisch door AEM gedaan wanneer een auteur of andere gebruiker met de juiste rechten inhoud publiceert.

### AEM Basics-overzicht {#aem-basics-summary}

Op het eenvoudigste niveau moeten de volgende stappen worden gezet om digitale ervaringen in AEM te creëren:

1. De auteurs van de inhoud maken inhoud zonder kop in de ontwerpinstantie.
1. Wanneer deze inhoud gereed is, wordt deze gerepliceerd naar de publicatie-instantie.
1. API&#39;s kunnen vervolgens worden aangeroepen om deze inhoud op te halen.

AEM Headless bouwt van deze technische stichting door krachtige hulpmiddelen aan te bieden om inhoud zonder kop te beheren die [ in de volgende sectie wordt beschreven.](#aem-headless-basics)

## AEM Headless Basics {#aem-headless-basics}

De headless mogelijkheden van AEM zijn gebaseerd op een paar zeer belangrijke eigenschappen. Deze worden in latere delen van de reis uitgebreid toegelicht. Het is nu belangrijk om alleen maar te weten wat ze doen en wat ze noemen.

### Modellen van inhoudsfragmenten {#content-fragment-models}

Met Content Fragment Models wordt de structuur gedefinieerd van de gegevens en inhoud die u maakt en beheert in AEM. Ze dienen als een soort basisstructuur voor je inhoud. Wanneer u ervoor kiest inhoud te maken, selecteren de auteurs een van de door u gedefinieerde modellen van inhoudsfragmenten die u als hulplijnen bij het maken van inhoud gebruikt.

### Inhoudsfragmenten {#content-fragments}

Met inhoudsfragmenten kunt u pagina-onafhankelijke inhoud ontwerpen, maken, beheren en publiceren. Hiermee kunt u inhoud voorbereiden en deze op meerdere locaties en via meerdere kanalen gebruiken.

Inhoudsfragmenten bevatten gestructureerde inhoud en kunnen in JSON-indeling worden geleverd.

### GraphQL- en REST-API&#39;s {#apis}

AEM biedt twee robuuste API&#39;s om uw inhoud zonder problemen aan te passen.

* Met de GraphQL API kunt u aanvragen maken voor toegang tot en levering van inhoudsfragmenten.
* Met de Assets REST API kunt u inhoudsfragmenten (en andere elementen) maken en wijzigen.

U leert over deze API&#39;s en hoe u deze kunt gebruiken in een later deel van de AEM-headless-reis. Of, zie de [ extra middelen ](#additional-resources) sectie hieronder voor extra documentatie.

## Niveaus voor toploze integratie {#integration-levels}

AEM ondersteunt zowel de volledige headless als de traditionele volledige stack of de populaire modellen van een CMS. AEM biedt echter niet alleen deze twee exclusieve keuzes, maar ook de mogelijkheid om hybride modellen te ondersteunen die de voordelen van beide combineren en unieke flexibiliteit bieden voor uw project zonder titel.

Deze AEM Headless Developer Journey richt zich op het pure headless-model, zodat u zo snel mogelijk weer aan de slag kunt zonder dat u in AEM codeert. Zo weet u zeker van uw begrip van headless-concepten.

Houd er echter rekening mee dat er nog meer hybride mogelijkheden zijn die u kunt gebruiken als u eenmaal de headless functies van AEM hebt begrepen. Deze gevallen worden hieronder beschreven voor uw bewustzijn. Aan het eind van de reis, zult u aan deze concepten in detail worden geïntroduceerd voor het geval dat zulk flexibiliteit voor uw project wordt vereist.

### U hebt al een externe consumptie van inhoud zonder kop, zoals één enkele paginatoepassing (SPA). {#already-have-a-spa}

Laten we ervan uitgaan dat uw basisvereiste minimaal is om inhoud van AEM te leveren aan een bestaande externe service.

#### Niveau 1: integratie van inhoudsfragmenten - traditioneel headless-model {#level-1}

Dit integratieniveau is het traditionele model zonder kop en stelt uw makers van inhoud in staat om inhoud te maken in AEM en deze zonder dralen te leveren aan een aantal externe services met behulp van GraphQL of om deze te bewerken van externe services met behulp van de Assets API. Geen codering vereist in AEM.

In dit model wordt AEM alleen gebruikt voor het maken en leveren van de inhoud met behulp van AEM Content Fragments. Renderen en interactie met de inhoud wordt gedelegeerd aan de verbruikende externe toepassing, vaak een single-page toepassing (SPA).

#### Niveau 2: de SPA insluiten in AEM - hybride model {#level-2}

Dit integratieniveau bouwt voort op het eerste niveau, maar laat ook de externe toepassing (SPA) toe om in AEM worden ingebed zodat de inhoudsauteurs de inhoud in de context van de externe toepassing binnen AEM kunnen bekijken. De toepassing kan ook beperkte bewerking van de externe toepassing in AEM ondersteunen.

Dit niveau heeft het voordeel om inhoudsauteurs toe te staan om inhoud in AEM op een flexibele manier te schrijven, met hun inhoud die in context met ingebedde externe SPA wordt voorgesteld, terwijl nog steeds het leveren van de inhoud zonder kop.

#### Niveau 3: SPA insluiten en volledig inschakelen in AEM - hybride model {#level-3}

Dit integratieniveau bouwt voort op niveau twee door de meeste inhoud in de externe SPA bewerkbaar te maken binnen AEM.

### U hebt nog geen externe consument van de inhoud zonder kop zoals één enkele paginatoepassing (SPA). {#do-not-have-a-spa}

Als uw doel een KUUROORD moet tot stand brengen die inhoud van AEM zonder kop verbruikt, kunt u eigenschappen zoals de Fragments van de Inhoud gebruiken om uw headless inhoud te beheren, en ook een KUUROORD met het kader van de Redacteur van het KUUROORD van AEM bouwen.

Gebruikend de Redacteur van het KUUROORD, verbruikt niet alleen inhoud van AEM, maar is ook volledig editable binnen AEM door uw inhoudsauteurs die u zowel de flexibiliteit van hoofdloze levering als in-context het uitgeven binnen AEM geven.

## Eisen en voorwaarden {#requirements-prerequisites}

Er zijn verschillende vereisten voor het starten van een AEM-project zonder titel.

### Kennis {#knowledge}

* GraphQL
* Ervaring met het maken van SPA&#39;s met React- of Angular-frameworks
* Basisvaardigheden van AEM die tot de Fragmenten van de Inhoud leiden en redacteur gebruiken

### Gereedschappen {#tools}

* Sandbox-toegang voor het testen van de implementatie van uw project
* Local development instance for data modelling and testing
* Bestaande externe SPA of andere consument van AEM-inhoud zonder kop

## Uw project definiëren {#defining-your-project}

Voor elk succesvol project is het belangrijk niet alleen de eisen van het project duidelijk te definiëren, maar ook de rollen en verantwoordelijkheden.

### Scope {#scope}

Het is belangrijk dat er een duidelijk afgebakende draagwijdte voor het project is. Het bereik bevat acceptatiecriteria en u kunt een definitie van &#39;gedaan&#39; vaststellen.

De eerste vraag die je moet stellen is: &quot;Wat probeer ik te bereiken met AEM Headless?&quot; Het antwoord moet in het algemeen zijn dat u een ervaringstoepassing hebt of in de toekomst zult hebben die u met uw eigen ontwikkelingshulpmiddelen niet met AEM hebt gebouwd. Deze ervaringstoepassing kan een mobiele app, een website of een andere eindgebruiker zijn die een ervaringstoepassing moet gebruiken. Het doel voor het gebruik van AEM Headless is om uw ervaringstoepassing inhoud te voorzien die in AEM wordt gemaakt, opgeslagen en beheerd met geavanceerde API&#39;s die AEM Headless zouden aanroepen om inhoud op te halen of zelfs volledig CRUD-inhoud rechtstreeks van uw ervaringstoepassing. Als dit niet is wat u wilt doen, wilt u waarschijnlijk [ terug naar de documentatie van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=nl-NL) gaan en de sectie vinden die beter past wat u wilt verwezenlijken.

### Rollen en verantwoordelijkheden {#roles-responsibilities}

De rollen voor om het even welk individueel project variëren, maar belangrijke die in de inhoud van de ontwikkeling van AEM zonder titel moeten overwegen zijn:

* [Beheerder](#administrator)
* [Inhoudsauteur](#content-author)
* [Content Architect](#content-architect)
* [Developer](#developer)

#### Beheerder {#administrator}

De beheerder is verantwoordelijk voor de basisopstelling en configuratie van uw systeem. De beheerder stelt bijvoorbeeld uw organisatie in in het Adobe-gebruikersbeheersysteem, dat naar Identity Management System (IMS) wordt verwezen. De beheerder is de eerste gebruiker van de organisatie die een e-mailuitnodiging van Adobe ontvangt zodra uw organisatie door Adobe binnen IMS is gemaakt. De beheerder kan zich aanmelden bij IMS en gebruikers van andere personen toevoegen.

Zodra de gebruikers door de beheerder worden gevormd, krijgen zij de toestemmingen om tot alle middelen van AEM toegang te hebben om hun werk als medewerkers te verwezenlijken om de ervaringstoepassing te leveren gebruikend AEM Headless.

De beheerder zou de gebruiker moeten zijn die omhoog AEM plaatst en het runtime milieu voorbereidt om [ inhoudsauteurs ](#content-author) toe te laten om inhoud tot stand te brengen en bij te werken en [ ontwikkelaars ](#developer) om APIs te gebruiken die inhoud voor hun ervaringstoepassingen halen of wijzigen.

#### Inhoudsauteur {#content-author}

Inhoudsauteurs maken en beheren de inhoud die zonder kop door AEM wordt geleverd. Inhoudsauteurs gebruiken AEM-functies zoals Content Fragments en de Assets Console om hun inhoud te beheren.

Inhoudsauteurs dienen de volgende aanbevolen procedures in acht te nemen.

#### Plan voor vertaling {#translation}

Plan voor vertaling aan het begin van het project. U kunt &quot;Translation Specialist&quot; beschouwen als een afzonderlijke persoon die tot taak heeft te bepalen welke inhoud moet worden vertaald en wat niet, en welke vertaalde inhoud door regionale of lokale inhoudproducenten kan worden gewijzigd.

Maak een plan voor wat u nodig hebt voor het vertalen van inhoud.

* Hebt u verschillende talen of ook taal nodig om zich aan te passen aan regionale bijzonderheden?
* Hebt u rijke media-inhoud zoals afbeeldingen of video&#39;s nodig om voor verschillende landinstellingen te kunnen verschillen?

Wis over uw workflow voor het bijwerken van inhoud. Wat is het goedkeuringsproces dat het systeem moet ondersteunen? Kunnen AEM-workflows worden gebruikt om dit proces te automatiseren?

Merk op dat uw [ inhoudshiërarchie ](#content-hierarchy) kan worden gebruikt om vertaling gemakkelijker te maken.

Zie de [ extra middelen ](#additional-resources) sectie voor extra documentatie over de werkschema&#39;s van AEM en vertaalhulpmiddelen met inbegrip van verbindingen aan de Transitney van de Vertaling van AEM Headless.

##### Gebruikmaken van de inhoudshiërarchie {#content-hierarchy}

Maphiërarchie kan twee belangrijke problemen met betrekking tot inhoudsbeheer aanpakken:

* [ Vertaling ](#translation) - AEM beheert vertaling van inhoud door exemplaren van inhoud in scènespecifieke omslagen te handhaven.
* Organisatie - Mappen worden gebruikt om een inhoudshiërarchie te bepalen die wordt vereist om vertaalbehoeften te steunen en logisch inhoudsfragmenten te beheren.

AEM maakt een flexibele inhoudsstructuur mogelijk en een hiërarchie kan willekeurig groot zijn. Nochtans is het belangrijk om zich te realiseren dat om het even welke veranderingen in omslagstructuur onbedoelde gevolgen voor bestaande vragen kan hebben die [ op de inhoudspad baseren.](#developer) Daarom kan een duidelijk gedefinieerde hiërarchie die vooraf is ingesteld, nuttig zijn voor de auteurs van de inhoud.

Mappen kunnen ook worden beperkt tot bepaalde typen inhoud (op basis van modellen van inhoudsfragmenten). Het wordt aanbevolen altijd expliciet op te geven welke modellen zijn toegestaan voor alle mappen in de hiërarchie. Toegestane inhoud opgeven voor een bepaalde map:

* Voorkomt dat inhoudsauteurs inhoud ontwerpen die niet in de map thuishoort.
* Optimaliseert het proces voor het maken van inhoud door de typen inhoud te filteren die tijdens het maken in de map zijn toegestaan, zodat alleen geldige typen inhoud worden weergegeven.

Door een geschikte inhoudsstructuur te maken, wordt het eenvoudiger om het schrijven van inhoud zonder kop tussen kanalen te coördineren om het hergebruik van inhoud te maximaliseren. De hefboomwerking van inhoud over veelvoudige kanalen verbetert zeer inhoudsproductie efficiency en veranderingsbeheer.

##### Goede naamgevingsconventies tot stand brengen {#naming-conventions}

Namen van inhoudsfragmenten moeten beschrijvend zijn voor inhoudsauteurs. AEM handelt het escapen en/of het afkappen van de gebruikte namen op het niveau van de repository transparant af. Daarom moeten de logische namen die door de auteurs van de inhoud worden verstrekt altijd leesbaar zijn en de inhoud vertegenwoordigen.

* Ongeldige naam: `cta_btn_1`
* Goede naam: `Call To Action Button`

Zie de [ extra middelen ](#additional-resources) sectie voor extra documentatie op de pagina van AEM noemende overeenkomsten.

##### Inhoud niet te veel nesten {#content-nesting}

[ de Fragmenten van de Inhoud ](#content-fragments) worden gebruikt in AEM om koploze inhoud tot stand te brengen. AEM ondersteunt tot tien niveaus voor het nesten van inhoud voor inhoudsfragmenten. Het is echter belangrijk om in gedachten te houden dat AEM elke referentie die in het bovenliggende inhoudsfragment is gedefinieerd, moet oplossen en vervolgens moet controleren of er onderliggende verwijzingen voorkomen op alle locaties op hetzelfde niveau. Deze bewerkingen kunnen snel worden uitgevoerd en zorgen voor de prestaties.

Als algemene regel van-duim, zouden de verwijzingen van het Fragment van de Inhoud niet voorbij vijf niveaus moeten worden genesteld.

#### Content Architect {#content-architect}

Inhoudsarchitecten analyseren de vereisten voor de gegevens die zonder kop moeten worden geleverd en definiëren de structuur voor deze gegevens. Deze structuren worden genoemd [ Modellen van het Fragment van de Inhoud ](#content-fragment-models) in AEM. Modellen van inhoudsfragmenten worden gebruikt als basis voor de inhoudsfragmenten die de auteurs van de inhoud maken.

Een handige methode bij het definiëren van modellen van inhoudsfragmenten is het maken van modellen die zijn toegewezen aan de UX-componenten van de toepassingen die de inhoud gebruiken.

Omdat de makers van de inhoud voortdurend met de modellen werken terwijl ze nieuwe inhoud maken, kunnen ze de resulterende digitale ervaring visualiseren door de modellen op de UX uit te lijnen. Als u deze uitlijning verder uitlijnt, kunt u pictogrammen toewijzen aan de modellen van inhoudsfragmenten die het UX-element vertegenwoordigen, zodat de auteurs op intuïtieve wijze het juiste model kunnen selecteren op basis van visuele aanwijzingen.

#### Developer {#developer}

Ontwikkelaars zijn verantwoordelijk voor het samenvoegen van de inhoud die in AEM wordt gemaakt tot de consument van die inhoud. Dit kan vaak een toepassing met één pagina (SPA), een progressieve webapp (PWA), een webshop of een andere service buiten AEM zijn.

GraphQL fungeert als de &quot;lijm&quot; tussen AEM en de consumenten van inhoud zonder kop. GraphQL is de taal die AEM om de noodzakelijke inhoud vraagt.

De ontwikkelaars zouden een paar basisaanbevelingen in mening moeten houden aangezien zij hun vragen plannen:

* De vragen zouden niet op een vaste weg (`ByPath`) moeten vertrouwen om de Fragmenten van de Inhoud terug te winnen.
   * [ de auteurs van de Inhoud hebben volledige controle over de hiërarchie van het inhoudsfragment ](#content-hierarchy) en konden veranderingen aanbrengen die zulk een vraag zouden breken.
   * De vragen zouden in plaats daarvan voor de modelverwijzingen van het inhoudsfragment met dynamische vraagparameters moeten kiezen om de resultaten te filtreren om de gewenste nuttige lading te produceren.
* Voor de beste vraagprestaties, gebruik altijd voortgeduurde vragen in AEM. Deze worden later op de reis besproken.
* GraphQL is declaratief na het motto &quot;Vraag precies wat u nodig hebt, en krijg precies dat.&quot; Dit betekent dat u bij het maken van GraphQL-query&#39;s altijd query&#39;s van het type `select *` vermijdt die u in een relationele database kunt maken.

Voor a [ typische hoofdloze implementatie die AEM gebruikt, ](#level-1) vereist de ontwikkelaar geen codeerkennis van AEM.

### Prestatievereisten {#performance-requirements}

Om een project tot een succes te maken, moeten de prestaties worden overwogen alvorens om het even welke inhoud wordt gecreeerd.

Zorg ervoor dat u de verwachtingen van uw gebruikers/bezoekers en uw ontwerp voor deze gebruikers/bezoekers begrijpt. Plaats de doelstellingen van het de dienstniveau (SLOs) en meet hen om te begrijpen als u aan de verwachtingen van uw gebruiker voldoet.

#### Verkeerspatronen {#traffic-patterns}

Om verkeer en verkeerspatronen te begrijpen begin met het verzamelen van wat u van het verleden en dan project aan de verwachte groei in de komende jaren kent. Enkele van de belangrijkste te overwegen variabelen:

* Hoeveel API vraag per uur/dag/maand verwacht u en is er potentieel voor pieken en seizoensgebondenheid?
* Hoeveel verschillende inhoudsauteurs zijn er?
* Hoeveel auteurs van inhoud verwacht u gelijktijdig te werken?
* Hoe vaak wordt de inhoud bijgewerkt?
* Hoeveel inhoudsmodellen zijn nodig?
* Hoeveel exemplaren van modellen zijn nodig?

#### Frequentie bijwerken {#update-frequency}

Vaak hebben verschillende secties van ervaringen verschillende frequenties van inhoudsupdates. Het begrip van dit is belangrijk om CDN en geheim voorgeheugenconfiguraties te kunnen verfijnen. Dit is ook belangrijke input voor de [ Architecten van de Inhoud ](#content-architects) aangezien zij modellen ontwerpen om uw inhoud te vertegenwoordigen. Overweeg:

* Moeten bepaalde soorten inhoud na een bepaalde periode verlopen?
* Zijn er elementen die gebruikersspecifiek zijn en dus niet in de cache kunnen worden opgeslagen?

## Volgende functies {#what-is-next}

Nu u dit deel van de AEM Headless Developer Journey hebt voltooid, moet u:

* Begrijp de basisbeginselen van de AEM-functies zonder kop.
* Zorg dat u weet aan welke voorwaarden u de AEM-functies zonder kop moet gebruiken.
* Wees op de hoogte van AEM&#39;s instapniveau.
* U kunt uw project definiëren in termen van bereik.

U zou uw reis zonder kop van AEM moeten voortzetten door het document [ Weg aan Uw Eerste Ervaring te herzien Gebruikend de Zetel van AEM ](path-to-first-experience.md) waar u zult leren hoe te opstelling de noodzakelijke hulpmiddelen en hoe te beginnen denken over het modelleren van uw gegevens in AEM.

## Aanvullende bronnen {#additional-resources}

Terwijl het wordt geadviseerd dat u zich op het volgende deel van de headless ontwikkelingstraject door het document [ Weg aan Uw Eerste Ervaring te herzien Gebruikend AEM Headless beweegt, ](path-to-first-experience.md) het volgende zijn sommige extra, facultatieve middelen die een diepere duik op sommige die concepten in dit document worden vermeld doen, maar zij worden niet vereist om op de headless reis verder te gaan.

* [ Kopieerbaar en Hoofdloos in AEM ](/help/sites-developing/headful-headless.md) - een volledige bespreking van de hoofdloze integratieniveaus beschikbaar in AEM

* Een [ Inleiding aan AEM als Headless CMS ](/help/sites-developing/headless/introduction.md)

* [&#128279;](/help/journey-headless/translation/overview.md) de Vertaalreis van 0&rbrace; AEM Headless  - Deze documentatietraject geeft u een breed inzicht in headless technologie, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.

* [ Hoofdloze Leerprogramma&#39;s van AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL) - gebruik deze hands-on leerprogramma&#39;s om te onderzoeken hoe te om de diverse opties te gebruiken om inhoud aan headless eindpunten met AEM te leveren en te kiezen wat voor u juist is.
* [ het Beheer van de Inhoud zonder hoofd Gebruikend GraphQL APIs ](https://experienceleague.adobe.com/nl?Solution=Experience+Manager&amp;Solution=Experience+Manager+Sites&amp;Solution=Experience+Manager+Forms&amp;Solution=Experience+Manager+Screens&amp;launch=ExperienceManager-D-1-2020.1.headless#courses) - volg deze cursus voor een overzicht van GraphQL API die in AEM wordt uitgevoerd. Verificatie via AdobeID is vereist.
* [ AEM Guides WKND - GraphQL ](https://github.com/adobe/aem-guides-wknd-graphql) - Dit project GitHub omvat voorbeeldtoepassingen die AEM GraphQL APIs benadrukken.
* [ Authoring Concepts ](/help/sites-authoring/author.md) - Technische documentatie voor het auteursmilieu van AEM met inbegrip van details op auteur-publiceer opstelling
* [ het Publiceren Pagina&#39;s ](/help/sites-authoring/publishing-pages.md) - Technische documentatie voor het publiceren van inhoud op AEM
* [ noemend Conventies ](/help/sites-developing/naming-conventions.md) - Technische documentatie van pagina noemende beperkingen in AEM
* [ de Manager en Vertaling van de Vertaling van de MultiPlaats ](/help/sites-administering/msm-and-translation.md) - Technische documentatie op AEM krachtige vertaaleigenschappen
* [ de werkschema&#39;s van AEM ](/help/sites-authoring/workflows.md) - Technische documentatie op hoe te om werkschema&#39;s in AEM te automatiseren
* [ de Fragmenten van de Inhoud ](/help/assets/content-fragments/content-fragments.md) - Technische documentatie voor de Fragmenten van de Inhoud.
* [ Modellen van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-models.md) - Technische documentatie voor de Modellen van het Fragment van de Inhoud.
* [ GraphQL Technische Documentatie ](https://graphql.org) - de definitie van GraphQL (externe verbinding)
* [ GraphQL API ](/help/sites-developing/headless/graphql-api/graphql-api-content-fragments.md) - Technische documentatie die verklaart hoe te om verzoeken tot toegang te leiden en tevreden Fragments te leveren
* [ Assets REST API ](/help/assets/assets-api-content-fragments.md) - Technische documentatie die verklaart hoe te om de Fragmenten van de Inhoud (en andere activa) te creëren en te wijzigen
* [ Verblijfsde Vragen ](/help/sites-developing/headless/graphql-api/persisted-queries.md) - Technische documentatie op gepresteerde vragen in AEM
* Het [ Portaal van de Ontwikkelaar van AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
