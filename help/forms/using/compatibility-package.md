---
title: Compatibiliteitspakket
description: Als u het compatibiliteitspakket op AEM Forms 6.5 LTS installeert, kunt u de Correspondentenbeheermiddelen van AEM Forms 6.5 en eerdere versies en afgekeurde adaptieve formuliersjablonen en pagina's gebruiken
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 3a529a82-e2fd-423c-96c1-a5accc87775e
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '364'
ht-degree: 0%

---

# Compatibiliteitspakket{#compatibility-package}

## Overzicht {#overview}

De interactieve mededeling is het gebrek en geadviseerde benadering om klantenmededelingen in AEM Forms 6.5 LTS tot stand te brengen. Om brieven in AEM Forms 6.5 LTS te blijven gebruiken, moet u het recentste [ pakket van de Verenigbaarheid AEMFD ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) installeren.

Het pakket van de Verenigbaarheid AEMFD laat u [ ook de volgende activa van AEM Forms 6.5.22.0, 6.4, 6.3 en 6.2 op AEM Forms 6.5 LTS ](../../forms/using/compatibility-package.md#add-support-for-aem-forms-and-assets-in-aem-forms) gebruiken

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

Voor meer informatie, zie [ Assets compatibel gemaakt met AEM Forms 6.5 door het pakket van de Verenigbaarheid ](../../forms/using/compatibility-package.md#assetsmadecompatible) te installeren.

## Voeg ondersteuning toe voor AEM Forms 6.5-, 6.4-, 6.3- en 6.2-elementen in AEM Forms 6.5 LTS {#add-support-for-aem-forms-and-assets-in-aem-forms-6.5.lts}

Nadat u een upgrade hebt uitgevoerd, voert u de volgende handelingen uit om het compatibiliteitspakket voor AEMFD te installeren en uw elementen compatibel te maken met 6.5:

Zorg ervoor dat u [ het pakket van de Verenigbaarheid van AEM ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) vooraf geïnstalleerd hebt.

1. Installeer het recentste AEM 6.5 LTS [ pakket van de Verenigbaarheid ](https://experienceleague.adobe.com/nl/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).

   Voor meer informatie bij het uploaden en het installeren van het pakket, zie [ hoe te met pakketten ](/help/sites-administering/package-manager.md) werken.

1. Start de server opnieuw nadat de logbestanden zijn gestabiliseerd.
1. Gebruik het migratiehulpprogramma om uw elementen compatibel te maken met 6,5 LTS.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht `Ctrl + C` . Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

   Voor meer informatie, zie [ migratienut ](../../forms/using/migration-utility.md).

## Assets maakte compatibel met AEM Forms 6.5 LTS door het compatibiliteitspakket te installeren {#assetsmadecompatible}

Door het compatibiliteitspakket te installeren, kunt u de volgende elementen en sjablonen compatibel maken met AEM Forms 6.5 LTS:

* Correspondentenbeheer Assets van AEM 6.4 en eerder:

   * [Letters](../../forms/using/create-letter.md)
   * [Gegevenswoordenboeken](/help/forms/using/data-dictionary.md)
   * Documentfragmenten

* Afgekeurde sjablonen voor adaptieve formulieren:

   * /libs/fd/af/templates/blankTemplate2
   * /libs/fd/af/templates/simpleEnrollmentTemplate
   * /libs/fd/af/templates/simpleEnrollmentTemplate2
   * /libs/fd/af/templates/surveyTemplate
   * /libs/fd/af/templates/surveyTemplate2
   * /libs/fd/af/templates/tabbedEnrollmentTemplate
   * /libs/fd/af/templates/tabbedEnrollmentTemplate2
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate
   * /libs/fd/afaddon/templates/advancedEnrollmentTemplate2

* Afgekeurde pagina&#39;s voor adaptieve formulieren:

   * /libs/fd/af/components/page/survey
   * /libs/fd/af/components/page/tabbedenrollment
   * /libs/fd/afaddon/components/page/advancedRolment
