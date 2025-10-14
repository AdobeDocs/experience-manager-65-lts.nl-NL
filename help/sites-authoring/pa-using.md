---
title: Paginaanalysegegevens bekijken om de doeltreffendheid van pagina-inhoud te meten
description: Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
solution: Experience Manager, Experience Manager Sites
feature: Authoring,Integration
role: User,Admin,Architect,Developer
exl-id: debcc73f-c2bb-4e3a-8ebf-c7590264d289
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '638'
ht-degree: 0%

---

# Gegevens van paginaanalyse bekijken{#seeing-page-analytics-data}

Gebruik pagina-analysegegevens om de doeltreffendheid van de pagina-inhoud te meten.

## Analyse zichtbaar vanuit de console {#analytics-visible-from-the-console}

![&#x200B; a-10 &#x200B;](assets/aa-10.png)

De analysegegevens van de pagina worden getoond in [&#x200B; Mening van de Lijst &#x200B;](/help/sites-authoring/basic-handling.md#list-view) van de console van Plaatsen. Wanneer de pagina&#39;s in lijstformaat worden getoond, zijn de volgende kolommen beschikbaar door gebrek:

* Paginaweergaven
* Unieke bezoekers
* Tijd op pagina

In elke kolom wordt een waarde voor de lopende rapportageperiode weergegeven en wordt ook aangegeven of de waarde sinds de vorige rapportageperiode is gestegen of gedaald. De gegevens die u ziet, worden elke 12 uur bijgewerkt.

>[!NOTE]
>
>Om de updateperiode te veranderen, [&#x200B; vorm het de invoerinterval &#x200B;](/help/sites-administering/adobeanalytics-connect.md#configuring-the-import-interval).

1. Open de **console van Plaatsen**; bijvoorbeeld, [&#x200B; http://localhost:4502/sites.html/content &#x200B;](http://localhost:4502/sites.html/content)
1. In het uiterste recht van de toolbar (hoger-juiste hoek), klik het pictogram om **Mening van de Lijst** te selecteren (het getoonde pictogram zal van de [&#x200B; huidige mening &#x200B;](/help/sites-authoring/basic-handling.md#viewing-and-selecting-resources) afhangen).

1. Opnieuw, in het uiterste recht van de toolbar (hoger-juiste hoek), klik het pictogram dan selecteren **Montages van de Mening**. Het **vormt de dialoog van Kolommen** opent. Breng om het even welke vereiste veranderingen aan en bevestig met **Update**.

   ![&#x200B; a-04 &#x200B;](assets/aa-04.png)

### De rapportageperiode selecteren {#selecting-the-reporting-period}

Selecteer de rapportperiode waarvoor de gegevens van Analytics op de console van Plaatsen verschijnen:

* Gegevens laatste 30 dagen
* Gegevens van afgelopen 90 dagen
* Gegevens van dit jaar

De huidige rapportageperiode wordt weergegeven op de werkbalk van de Sites-console (rechts van de bovenste werkbalk). Gebruik de vervolgkeuzelijst om de vereiste rapportageperiode te selecteren.
![&#x200B; a-05 &#x200B;](assets/aa-05.png)

### Beschikbare gegevenskolommen configureren {#configuring-available-data-columns}

Leden van de analytische-beheerders gebruikersgroep kunnen de console van Plaatsen vormen om auteurs toe te laten om extra kolommen van Analytics te zien.

>[!NOTE]
>
>Wanneer een boomstructuur met pagina&#39;s onderliggende elementen bevat die zijn gekoppeld aan verschillende Adobe Analytics-wolkenconfiguraties, kunt u de beschikbare gegevenskolommen voor de pagina&#39;s niet configureren.

1. In de Mening van de Lijst, gebruik de meningsselecteurs (recht van toolbar), de uitgezochte **Montages van de Mening** en dan **voegt de Gegevens van de Analyse van de Douane** toe.

   ![&#x200B; a-15 &#x200B;](assets/aa-15.png)

1. Selecteer de metriek die u aan auteurs in de console van Plaatsen wilt blootstellen, en dan **toevoegen** klikken.

   De kolommen die worden weergegeven, worden opgehaald uit Adobe Analytics.

   ![&#x200B; a-16 &#x200B;](assets/aa-16.png)

### Inhoudsgegevens van sites openen {#opening-content-insights-from-sites}

Open [&#x200B; Inzicht van de Inhoud &#x200B;](/help/sites-authoring/content-insights.md) van de console van Plaatsen om paginadoeltreffendheid verder te onderzoeken.

1. Selecteer in de Sites-console de pagina waarvoor u Inhoudsgegevens wilt weergeven.
1. Klik op het pictogram Analytics and Recommendations (Analytics en Aanbevelingen) op de werkbalk.

   ![&#x200B; Analytics en het pictogram van Aanbevelingen &#x200B;](do-not-localize/chlimage_1-16a.png)

## Analyses zichtbaar in de Pagina-editor (Activity Map) {#analytics-visible-from-the-page-editor-activity-map}

>[!NOTE]
>
>Dit wordt getoond als [&#x200B; Activity Map &#x200B;](/help/sites-administering/adobeanalytics-connect.md#configuring-for-the-activity-map) voor uw website is gevormd.

>[!NOTE]
>
>Gegevens voor de Activity Map zijn afkomstig uit Adobe Analytics.

Wanneer uw website [&#x200B; voor Adobe Analytics &#x200B;](/help/sites-administering/adobeanalytics-connect.md) is gevormd, kunt u de [&#x200B; wijze Activity Map &#x200B;](/help/sites-authoring/author-environment-tools.md#page-modes) gebruiken om relevante gegevens te bekijken. Bijvoorbeeld:

![&#x200B; a-07 &#x200B;](assets/aa-07.png)

### Toegang tot de Activity Map {#accessing-the-activity-map}

Na het selecteren van de [&#x200B; Activity Map &#x200B;](/help/sites-authoring/author-environment-tools.md#page-modes) wijze, zult u worden gevraagd om uw geloofsbrieven van Adobe Analytics in te gaan.

![&#x200B; a-03 &#x200B;](assets/aa-03.png)

De **Analytics** drijvende toolbar wordt getoond; hier kunt u:

* verander het toolbarformaat gebruikend de dubbele pijlen (**>>**)
* Paginadetails in-/uitschakelen (oogpictogram)
* Activity Map-instellingen configureren (cogingpictogram)
* Selecteer de analysefunctie die u wilt weergeven (verschillende keuzelijsten)
* Sluit de Activity Map en sluit de werkbalk (x)

![&#x200B; a-09 &#x200B;](assets/aa-09.png)

### De weer te geven analyse selecteren {#selecting-the-analytics-to-show}

U kunt aan de hand van de verschillende criteria bepalen welke analysegegevens moeten worden weergegeven en hoe deze moeten worden weergegeven:

* **Norm**/**Levend**

* gebeurtenistype
* gebruikersgroep
* **Bubbles**/**Verloop**/**Gainers &amp; Gebruikers**/**weg**

* te tonen periode

![&#x200B; a-13 &#x200B;](assets/aa-13.png)

### De Activity Map configureren {#configuring-the-activity-map}

Gebruik het **pictogram van Montages** tonen om de **de Montages van Activity Map** dialoog te openen.

![&#x200B; a-04-1 &#x200B;](assets/aa-04-1.png)

Het **de Montages van Activity Map** dialoog verstrekt een waaier van opties op drie lusjes:

![&#x200B; a-06 &#x200B;](assets/aa-06.png)

* Algemeen

   * Rapportsuite
   * Paginanaam
   * Taal
   * Labelbedekkingen met
   * Tekengrootte label
   * Verloopkleur
   * Bubbelkleur
   * Kleurverloop op basis van
   * Transparantie verloop

* Standaard

   * Weergeven (type en aantal koppelingen)
   * Bedekkingen verbergen voor koppelingen die geen treffers hebben ontvangen

* Live

   * Bovenkant weergeven (Gainers of Losers)
   * Onderkant % uitsluiten
   * Automatisch bijwerken (gegevens en periode)
