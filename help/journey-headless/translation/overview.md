---
title: AEM Headless Translation Reis
description: Begin hier voor een begeleide reis door uw inhoud zonder kop te vertalen met de krachtige vertaalhulpmiddelen van AEM.
solution: Experience Manager, Experience Manager Sites
feature: Headless,Content Fragments,Language Copy
role: Admin, Architect,Data Architect,Developer,User,Leader
exl-id: dcec1797-c1da-4738-95e8-9d77fa9e9bec
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1037'
ht-degree: 0%

---

# AEM Headless Translation Reis {#aem-headless-translation-journey}

Begin hier voor een begeleide reis door uw inhoud zonder kop te vertalen met de krachtige vertaalhulpmiddelen van AEM.

## Inleiding {#introduction}

Implementatie zonder hoofd wordt steeds belangrijker om uw publiek ervaringen te bieden, waar ze zich ook bevinden en ongeacht kanaal, regio of landinstelling.

Bij implementatie zonder kop gaan pagina- en componentbeheer verloren, zoals gebruikelijk is in oplossingen voor volledige stapels. De implementatie is gericht op het maken van kanaalneutrale, herbruikbare fragmenten van inhoud en de levering ervan via meerdere kanalen. Door gebruik te maken van de krachtige vertaalhulpmiddelen van AEM, kunnen deze herbruikbare fragmenten eenvoudig worden vertaald en geleverd aan uw publiek waar het ook is.

Deze gids leidt u door de belangrijkste hoofdloze vertaalonderwerpen zodat u na voltooiing:

* Heb een overzicht van wat koploze inhoudlevering is.
* Basiskennis van AEM-functies zonder kop.
* Begrijp de vertaalfuncties van AEM en hoe deze verwant zijn aan inhoud zonder kop.
* De mogelijkheid hebben om uw eigen inhoud zonder kop te vertalen.

Het doel is om u een breed inzicht te geven in technologie zonder kop, hoe AEM inhoud zonder kop dient en hoe u deze kunt vertalen. Als u met geen van deze onderwerpen vertrouwd bent, is dit uw ideale plaats om te beginnen.

Als u al bekend bent met AEM, zonder kop en vertaling, hebt u wellicht al de grondkennis van deze reis. Overweeg verwijzend naar onze technische documentatie die onder de [&#x200B; extra hieronder middelensectie wordt verbonden.](#additional-resources)

## AEM-documentatiereizen {#documentation-journeys}

[&#x200B; de Reis van de Documentatie van A &#x200B;](/help/journey-documentation/home.md) verbindt vele verschillende en misschien ingewikkelde onderwerpen en eigenschappen door een verhaal te verstrekken dat de lezer helpt, die aan AEM nieuw kan zijn, een bedrijfsprobleem van begin tot eind begrijpen en oplossen, terwijl het veronderstellen van minimale voorafgaand onderwerp of de kennis van AEM.

Documentatiereizen zijn gebaseerd op de beginselen van best practices, op informatie van Adobe over het meest recente onderzoek, bewezen ervaring met de implementatie van Adobe-consultants en feedback van klantprojecten.

Als u wilt weten hoe Adobe adviseert om hoofdloze bedrijfszaken met AEM op te lossen, [&#x200B; de Draadloze Reizen van AEM &#x200B;](/help/journey-headless/overview.md) zijn waar te beginnen.

## Publiek {#audience}

Deze reis wordt ontworpen voor de vertaal specialistische persoon, die vaak als de Manager van het Project van de Vertaling of TPM wordt bedoeld. Deze reis beschrijft de vereisten, de stappen, en de benadering om inhoud zonder kop in AEM te vertalen. De reis kan aanvullende personen definiëren waarmee de vertaalspecialist moet communiceren, maar het gezichtspunt voor de reis is dat van de vertaalspecialist.

Deze reis veronderstelt de lezer ervaring vertaalend inhoud op een groot systeem van CMS heeft, maar veronderstelt geen kennis van technologie zonder kop of AEM.

Het volgende is de persoon die in deze reis interactie heeft.

| Persona | Beschrijving | Rol in reis |
|---|---|---|
| Specialist voor vertaling | Hiermee definieert u welke inhoud moet worden omgezet en beheert u deze workflows | Publiek van deze reis |
| Inhoudsauteur | Creeert en beheert inhoud die zonder kop wordt geleverd | Inhoudsauteurs maken inhoud die de vertaalspecialist moet vertalen. |
| Beheerder | Beheert de basisconfiguratie en -configuratie van AEM | De vertaalspecialist werkt met de beheerder om configuratieveranderingen nodig voor vertaling zoals het installeren van een vertaalschakelaar aan te brengen. |
| Content Architect | Analyseert de vereisten voor de gegevens die zonder kop moeten worden geleverd en bepaalt de structuur voor deze gegevens | Vertaalspecialisten werken samen met de inhoudarchitect om de organisatie van de inhoud te bepalen zodat het gemakkelijk kan worden vertaald. |

De informatie in deze reis kan voor alle mensen nuttig zijn, maar sommige informatie kan aan bepaalde rollen overbodig zijn. Blijf voor [&#x200B; aanstaande reizen die extra rollen behandelen.](/help/journey-documentation/home.md#journeys)

## De Headless Translation Reis {#the-journey}

U zult vele onderwerpen in deze reis onderzoeken. De volgende artikelen geven u basiskennis van het vertalen van inhoud zonder kop in AEM en koppelen naar gedetailleerde technische documentatie.

Hoewel u rechtstreeks naar een bepaald gedeelte van de reis kunt gaan, bouwen vele concepten op degenen in vorige artikelen. Als u in AEM nog niet veel nieuws hebt over krantenloze vertalingen, raadt Adobe u daarom aan om aan het begin te beginnen en opeenvolgend verder te gaan.

| Aantal | Artikel | Beschrijving |
|---|---|---|
| 0 | AEM Headless Translation Reis | Dit document |
| 1 | [&#x200B; leer over hoofdloze inhoud en hoe te om het in AEM &#x200B;](learn-about.md) te vertalen | Ontdek headless-concepten, hoe ze in kaart brengen naar AEM, en de theorie van de AEM-vertaling. |
| 2 | [&#x200B; worden begonnen met de hoofdloze vertaling van AEM &#x200B;](getting-started.md) | Lees hoe u uw inhoud zonder kop kunt ordenen en hoe de vertaalhulpmiddelen van AEM werken. |
| 3 | [&#x200B; vorm de vertaalintegratie &#x200B;](configure-connector.md) | Leer hoe u AEM kunt verbinden met een vertaalservice. |
| 4 | [&#x200B; vorm vertaalregels &#x200B;](translation-rules.md) | Leer hoe u vertaalregels definieert om inhoud voor vertaling te identificeren. |
| 5 | [&#x200B; vertaal inhoud &#x200B;](translate-content.md) | Gebruik de vertaalintegratie en de regels om uw inhoud zonder kop te vertalen. |
| 6 | [&#x200B; publiceer vertaalde inhoud &#x200B;](publish-content.md) | Leer hoe u uw vertaalde inhoud publiceert en de vertaling bijwerkt wanneer de onderliggende inhoud wordt bijgewerkt. |

## Volgende functies {#what-is-next}

U bent nu klaar om aan de slag te gaan met uw Adobe-vertaalreis zonder kop. Wij moedigen u aan om op het volgende deel van de reis voort te gaan en het artikel [&#x200B; te lezen Leer over hoofdloze inhoud en hoe te om het in AEM &#x200B;](learn-about.md) te vertalen

## Aanvullende bronnen {#additional-resources}

Documentatiereizen tonen u hoe AEM een bedrijfsprobleem oplost door een verhaal te bieden dat u door complexe, onderling samenhangende processen en functies begeleidt. Een reis illustreert hoe de veelvoudige eigenschappen samenwerken om één enkele bedrijfsbehoefte te dienen.

Als zodanig zijn reizen zodanig ontworpen dat ze op zichzelf staan. Verschillende kunnen echter aan elkaar zijn gerelateerd. Bekijk deze extra ritten voor meer informatie over hoe de krachtige functies van AEM samenwerken.

* [&#x200B; Koploze het Authoring Reis &#x200B;](/help/journey-headless/author/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele headless eigenschappen van AEM, hun mogelijkheden, en hoe te om uw inhoud op uw eerste headless project te modelleren.
* [&#x200B; Eis van de Architect zonder hoofd &#x200B;](/help/journey-headless/architect/overview.md) - Begin hier voor een inleiding aan de krachtige, en flexibele, headless eigenschappen van Adobe Experience Manager, en hoe te om inhoud voor uw project te modelleren.
* [&#x200B; AEM Headless Developer Journey &#x200B;](/help/journey-headless/developer/overview.md) - Begin hier voor een geleide reis door de krachtige en flexibele hoofdloze eigenschappen van AEM, hun mogelijkheden, en hoe te om hen op uw eerste ontwikkelingsproject te gebruiken.
* [&#x200B; technische documentatie van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65.html?lang=nl-NL) - als u reeds een stevig inzicht in AEM en headless technologieën hebt, kunt u onze diepgaande technische documenten direct willen raadplegen.
   * Een [&#x200B; Inleiding aan AEM als Headless CMS &#x200B;](/help/sites-developing/headless/introduction.md)
* [&#x200B; Hoofdloze zelfstudies van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-with-aem-headless/overview.html?lang=nl-NL) - als u verkiest te leren door te doen en technisch gegeneerd bent, neem onze hands-on leerprogramma&#39;s die door API en kader worden georganiseerd, die het creëren van en het gebruiken van toepassingen onderzoeken die op de Hoofdloze AEM worden gebouwd.
* Het [&#x200B; Portaal van de Ontwikkelaar van AEM &#x200B;](https://experienceleague.adobe.com/landing/experience-manager/headless/developer.html?lang=nl-NL)
