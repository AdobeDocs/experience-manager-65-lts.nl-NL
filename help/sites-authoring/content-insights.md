---
title: Inhoudsinzicht
description: Content Insight biedt informatie over paginaprestaties met behulp van webanalyses en SEO-aanbevelingen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User,Admin,Architect,Developer
exl-id: 10bf533d-c0a8-43ac-8dd5-d4fa501b8726
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '537'
ht-degree: 0%

---

# Inhoudsinzicht{#content-insight}

Content Insight biedt informatie over de prestaties van pagina&#39;s aan de hand van webanalyses en SEO-aanbevelingen. Met Inzicht in inhoud kunt u bepalen hoe pagina&#39;s moeten worden gewijzigd of hoe vorige wijzigingen de prestaties hebben gewijzigd. Voor elke pagina die u ontwerpt, kunt u Inzicht van de Inhoud openen om de pagina te analyseren.

![ chlimage_1-311 ](assets/chlimage_1-311.png)

De lay-out van de pagina Inzicht in inhoud wordt aangepast aan de schermafmetingen en de stand van het apparaat dat u gebruikt.

## Rapportgegevens

De pagina Content Insight bevat rapporten waarin Adobe SiteCatalyst-, Adobe Target-, Adobe Social- en BrightStor-gegevens worden gebruikt:

* SiteCatalyst: rapporten voor de volgende meetgegevens zijn beschikbaar:

   * Paginaweergaven
   * Gemiddelde tijd besteed aan pagina
   * Bronnen

* Doel: rapporteert over campagneactiviteiten waarvoor uw pagina voorstellen bevat.
* BrightStor: meldt de paginafuncties die de zichtbaarheid van de pagina voor zoekprogramma&#39;s verbeteren en raadt functies aan die moeten worden geïmplementeerd.

Zie [ Openend Analytics en Aanbevelingen voor een Pagina ](/help/sites-authoring/ci-analyze.md#opening-analytics-and-recommendations-for-a-page).

## Rapportageperiode

De rapporten tonen gegevens voor een periode die u controleert. Wanneer u de rapportageperiode aanpast, worden de rapporten automatisch vernieuwd met gegevens voor die periode. Visuele aanwijzingen geven de tijd aan waarop paginaversies zijn gewijzigd, zodat u de prestaties van elke versie kunt vergelijken.

>[!NOTE]
>
>De tijdlijn voor het dashboard Inzicht van inhoud staat in `GMT` .

U kunt ook de granulariteit van de gerapporteerde gegevens opgeven. U kunt bijvoorbeeld dagelijkse, wekelijkse, maandelijkse of jaarlijkse gegevens zien.

Zie [ Veranderend de Rapportageperiode ](/help/sites-authoring/ci-analyze.md#changing-the-reporting-period).

>[!NOTE]
>
>De rapporten met inzichten van inhoud vereisen dat uw beheerder AEM heeft geïntegreerd met SiteCatalyst, Target en BrightStor. Zie [ Integrerend met SightCatalyst ](/help/sites-administering/adobeanalytics.md), [ Integrerend met Adobe Target ](/help/sites-administering/target.md), en [ Integrerend met BrightEdge ](/help/sites-administering/brightedge.md).

## Het weergavenrapport {#the-views-report}

Het rapport Weergaven bevat de volgende functies voor het evalueren van het paginaverkeer:

* Het totale aantal weergaven voor een pagina voor de verslagperiode.
* Een grafiek van het aantal weergaven in de verslagperiode:

   * Totaal aantal weergaven.
   * Unieke bezoekers.

![ chlimage_1-312 ](assets/chlimage_1-312.png)

## Rapport over paginagewicht {#the-page-average-engaged-report}

Het rapport Paginagemiddelde van deelnemers bevat de volgende functies voor het evalueren van de doeltreffendheid van pagina&#39;s:

* De gemiddelde tijd dat de pagina gedurende de gehele rapportageperiode open blijft.
* Een grafiek van de gemiddelde lengte van een paginaweergave over de verslagperiode.

![ chlimage_1-313 ](assets/chlimage_1-313.png)

## Bronnen {#the-sources-report}

Het rapport Bronnen geeft aan hoe gebruikers naar de pagina zijn genavigeerd, bijvoorbeeld op basis van resultaten van zoekprogramma&#39;s of via de bekende URL.

![ chlimage_1-314 ](assets/chlimage_1-314.png)

## Het Bounces-rapport {#the-bounces-report}

Het rapport Bounces bevat een grafiek die het aantal grenzen aangeeft dat zich tijdens de geselecteerde rapportageperiode op een pagina heeft voorgedaan.

![ chlimage_1-315 ](assets/chlimage_1-315.png)

## Het activiteitenverslag van de campagne {#the-campaign-activity-report}

Voor elke campagne waarvoor de pagina actief is, verschijnt een rapport genoemd *Activiteit van de Naam van de Campagne 0&rbrace;.* Het rapport toont paginamonpressies en omzettingen voor elk segment waarvoor een aanbieding wordt verstrekt.

![ chlimage_1-316 ](assets/chlimage_1-316.png)

## Rapport SEO-aanbevelingen {#the-seo-recommendations-report}

Het rapport SEO Recommendations bevat de resultaten van de BrightEdge-analyse voor de pagina. Het rapport is een controlelijst van paginafuncties die aangeeft welke functies de pagina heeft en niet bevat voor het maximaliseren van de zoekbaarheid met behulp van zoekmachines.

Met dit rapport kunt u taken maken die u wilt verbeteren en de zoekbaarheid van pagina&#39;s verbeteren. De aanbevelingen wijzen erop dat de taken voor de uitvoering van de aanbeveling zijn gecreeerd. Zie [ Toewijzende Taken voor SEO Aanbevelingen ](/help/sites-authoring/ci-analyze.md#assigning-tasks-for-seo-recommendations).

![ chlimage_1-317 ](assets/chlimage_1-317.png)
