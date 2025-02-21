---
title: AEM Headless Developer Journey
description: AEM Headless CMS Documentation. Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste ontwikkelingsproject te gebruiken.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,GraphQL,Persisted Queries,Developing
role: Admin, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '1204'
ht-degree: 1%

---

# AEM Headless Developer Journey {#aem-headless-developer-journey}

Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste project zonder titel te gebruiken. Deze reis voorziet u van alle Documentatie van AEM Headless u nodig hebt om uw eerste headless toepassing te ontwikkelen.

## Inleiding {#introduction}

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels. De implementatie is gericht op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering ervan via meerdere kanalen. Het is een modern en dynamisch ontwikkelingspatroon voor de implementatie van digitale ervaringen.

Deze gids leidt u door de belangrijkste implementatieonderwerpen in AEM zodat u na voltooiing:

* U moet goed begrijpen wat de inhoud zonder kop levert en wat de voordelen ervan zijn.
* Begrijp de baanloze AEM-functies en hoe ze samenwerken om een eindeloze ervaring te bieden.
* Heb de capaciteit om de eerste stappen te nemen die uw eerste project van AEM zonder kop uitvoeren.

## AEM-documentatiereizen {#documentation-journeys}

[ de Reis van de Documentatie van A ](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die aan AEM nieuw kan zijn, een bedrijfsprobleem van begin tot eind begrijpen en oplossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of de kennis van AEM.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op informatie van Adobe over het meest recente onderzoek, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als u wilt weten hoe Adobe adviseert om hoofdloze bedrijfszaken met AEM op te lossen, [ de Draadloze Reizen van AEM ](/help/journey-headless/overview.md) zijn waar te beginnen.

>[!TIP]
>
>Als u verkiest om **te leren door** te doen en technisch gegeneerd bent, bezoek de Hoofdloze zelfstudies van AEM, die door API en kader worden georganiseerd en in de [ Aanvullende sectie van Middelen ](#additional-resources) aan het eind van dit document beschikbaar zijn.

## Publiek {#audience}

Deze reis is ontworpen voor de ontwikkelaar persona, die de vereisten, de stappen, en de benadering van een AEM Headless project uit het perspectief van de ontwikkelaar beschrijft. De reis bepaalt extra mensen waarmee de ontwikkelaar voor een succesvol project moet in wisselwerking staan, maar het punt van mening voor de reis is dat van de ontwikkelaar.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in deze reis |
|---|---|---|
| Ontwikkelaar (doelgroep) | Heeft ervaring met het ontwikkelen van toepassingen zonder kop die inhoud uit verschillende bronnen gebruiken | Doelgroep van deze reis |
| Inhoudsauteur | Hiermee maakt en beheert u inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de ontwikkelaar zonder kop levert. |
| Beheerder | Beheert de basisconfiguratie en -configuratie van AEM | De ontwikkelaar werkt met de beheerder om configuratieveranderingen nodig voor ontwikkeling aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Ontwikkelaars werken samen met de inhoudarchitect om de structuur van de gegevens en de vereisten voor het leveren van de inhoud te begrijpen. |

De informatie in deze reis kan voor alle mensen nuttig zijn, maar sommige informatie kan aan bepaalde rollen overbodig zijn. Blijf voor [ aanstaande reizen die extra rollen behandelen.](/help/journey-documentation/home.md#journeys)

## De headless Developer Journey {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. In de volgende artikelen wordt u op basis van kennis van de kop in AEM en een link naar gedetailleerde technische documentatie getoond.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Als u in AEM nog geen ervaring hebt met headless, raadt Adobe u dan ook aan aan aan het begin te beginnen en opeenvolgend verder te gaan.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Developer Journey | Dit document |
| 1 | [ Leer over de Hoofdloze Ontwikkeling van CMS ](learn-about.md) | Meer informatie over Headless Technology en wanneer u deze gebruikt. |
| 2 | [ Begonnen het worden met de Zetel van AEM ](getting-started.md) | Meer informatie over AEM Headless-vereisten |
| 3 | [ Weg aan uw eerste ervaring gebruikend de Zetel van AEM ](path-to-first-experience.md) | Stel uw ontwikkelomgeving in en leer hoe u een eenvoudige app kunt integreren met AEM Headless |
| 4 | [ hoe te om uw inhoud ](model-your-content.md) te modelleren | Leer hoe u uw inhoudsstructuur kunt modelleren. Bespreek vervolgens die structuur voor Adobe Experience Manager (AEM) met gebruik van Content Fragments Models en Content Fragments, voor hergebruik over kanalen. |
| 5 | [ hoe te om tot uw inhoud via levering APIs van AEM toegang te hebben ](access-your-content.md) | Leer hoe u GraphQL-query&#39;s gebruikt om toegang te krijgen tot inhoud van Content Fragments. |
| 6 | [ hoe te om uw inhoud via AEM Assets APIs bij te werken ](update-your-content.md) | Leer hoe u REST API kunt gebruiken om de inhoud van Content Fragments te openen en bij te werken. |
| 7 | [ hoe te om het allen samen te zetten - uw app en uw inhoud in AEM Headless ](put-it-all-together.md) | Leer hoe u uw AEM-project kunt nemen en voorbereiden op live gaan met de AEM Headless SDK. |
| 8 | [ hoe te om met uw headless toepassing te gaan ](go-live.md) | Leer hoe u de toepassing live kunt implementeren en neem uw lokale code in Git en verplaats deze naar Cloud Manager Git voor CI/CD-pijplijn. |
| 9 | [ Facultatief - hoe te om enige paginatoepassingen (SPAs) met AEM ](create-spa.md) tot stand te brengen | Zodra u de belangrijkste eigenschappen van AEM begrijpt, onderzoek hoe te om krachtige en zonder kop levering te combineren en te leren hoe u editable SPAs kunt tot stand brengen gebruikend het kader van de Redacteur van het KUUROORD van AEM. |

## Volgende functies {#what-is-next}

Je bent nu klaar om aan de slag te gaan met je Adobe Headless-reis. Wij moedigen u aan om op het volgende deel van de reis voort te gaan en het artikel [ te lezen Leer over de Ontwikkelingen van CMS Headless.](learn-about.md)

### Kies uw eigen avontuur {#choose-your-path}

Adobe wil echter dat u slaagt wanneer u aan de slag gaat met uw AEM Headless-project, ongeacht uw leerstijl. Bekijk deze twee opties.

* Als u verkiest om **over headless concepten en AEM te blijven leren zonder kop technologieën**, zou u uw reis zonder kop van AEM moeten voortzetten zoals geadviseerd door het document [ te herzien hoe te Uw Inhoud als Modellen van de Inhoud van AEM te modelleren ](model-your-content.md) waar u leert hoe te om uw inhoudsstructuur in AEM te modelleren.
* Als u verkiest om **te leren door** te doen, kunt u aan [ springen Begonnen het Worden met AEM Headless hands-on leerprogramma ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/graphql/multi-step/overview.html) waar u direct in de Zwaarloze ontwikkeling van AEM zult springen door een eenvoudig project uit te voeren om de inhoud van AEM zonder kop bloot te stellen.

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te bieden dat u door complexe, onderling samenhangende processen en functies begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn reizen zodanig ontworpen dat ze op zichzelf staan. Verschillende kunnen echter aan elkaar zijn gerelateerd. Bekijk deze extra ritten voor meer informatie over hoe de krachtige functies van AEM samenwerken.

* [ Hoofdloze zelfstudies van AEM ](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html) - als u verkiest te leren door te doen en technisch gegeneerd bent, neem onze hands-on leerprogramma&#39;s die door API en kader worden georganiseerd, die het creëren van en het gebruiken van toepassingen onderzoeken die op de Hoofdloze AEM worden gebouwd.
* ](/help/journey-headless/translation/overview.md) de Vertaalreis van 0} AEM Headless [ - Deze documentatietraject geeft u een breed inzicht in headless technologie, hoe AEM inhoud zonder kop dient, en hoe u het kunt vertalen.
* [ Koploze het Authoring Reis ](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [ Eis van de Architect zonder hoofd ](/help/journey-headless/architect/overview.md) - Begin hier voor een inleiding aan de krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
* [ technische documentatie van AEM ](https://experienceleague.adobe.com/docs/experience-manager-65.html) - als u reeds een stevig inzicht in AEM en headless technologieën hebt, kunt u onze diepgaande technische documenten direct willen raadplegen.

   * Een [ Inleiding aan AEM als Headless CMS ](/help/sites-developing/headless/introduction.md)

* Het [ Portaal van de Ontwikkelaar van AEM ](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html)
