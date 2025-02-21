---
title: Opvallende wijzigingen in de invoegtoepassing Commerce integration framework (CIF)
description: Opvallende wijzigingen in de invoegtoepassing Commerce integration framework (CIF) ten opzichte van de oude CIF-versies.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '312'
ht-degree: 0%

---

# Notable Changes to the Commerce integration framework (CIF) add-on{#notable-changes}

In dit document worden de belangrijke verschillen tussen de Commerce integration framework (CIF) add-on en de oude CIF-versies belicht, die voornamelijk CIF Classic (Quickstart) en CIF Open-source worden genoemd.

## Installatie en updates

Het AEM CIF add-on pakket wordt geïnstalleerd en bijgewerkt met AEM Package Manager.

**Vorige versies van CIF**

* CIF Classic: Geen installatie nodig, CIF was onderdeel van de Quickstart. CIF-updates maakten deel uit van reguliere AEM- of servicepack-updates
* CIF Open-source: installatie via GitHub. Updates maakten deel uit van handmatige update-/onderhoudswerkzaamheden.

## Eindpuntconfiguratie

Het eindpunt wordt gevormd via console OSGi.

**Vorige versies van CIF**

* CIF Classic: Via OSGi-configuratie in AEM
* CIF Open-source: Via CIF Configuration Browser

## Invoering van het CIF-project van Venia

Project beschikbaar op [ GitHub AEM Guides - CIF Venia Project ](https://github.com/adobe/aem-cif-guides-venia) en plaatsing die via de Manager van het Pakket van AEM wordt gedaan.

**Vorige versies van CIF**

* CIF Classic: via AEM-pakketinstallatie

## Productcatalogusgegevens

De catalogusgegevens van het product worden gevraagd op bestelling via vraag in real time aan een extern eindpunt dat vereiste GraphQL APIs steunt. Deze API&#39;s ondersteunen toegang tot live- of gefaseerde gegevens op een bepaalde datum. Geen replicatie nodig.

**Vorige versies van CIF**

* CIF Classic: live en gefaseerde productgegevens worden geïmporteerd in en voortgezet in JCR op AEM Author via volledige of delta productimport. Live-productgegevens worden gerepliceerd naar AEM Publish.

## Ervaringen met productcatalogi met AEM-rendering

AEM geeft de ervaringen met productcatalogi direct weer met AEM-catalogussjablonen die zijn toegewezen aan producten en categorieën. Geen replicatie nodig.

**Vorige versies van CIF**

* CIF Classic: AEM Author maakt een AEM-pagina voor elke categorie/elk product met het gereedschap Catalogusblauwdruk. Deze pagina&#39;s worden gerepliceerd naar AEM Publish.

>[!NOTE]
>
>Voor extra documentatie op hoe te om CIF met AEM te gebruiken Beheerde Dienst of AEM op-Premise, zie [ Commerce integration framework ](https://www.adobe.io/apis/experiencecloud/commerce-integration-framework/getting-started.html)
