---
title: Migratie naar de invoegtoepassing AEM Commerce integration framework (CIF)
description: Migreren naar de AEM Commerce integration framework-invoegtoepassing (CIF) vanuit een oude versie.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '253'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager-invoegtoepassing {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager-add-on migratie moet bijwerken.

## CIF-invoegtoepassing

CIF toe:voegen-op is beschikbaar voor AEM 6.5 via het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor Experience Manager as a Cloud Service.

Zie [ Begonnen het worden met de Inhoud van AEM en Commerce ](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt Adobe {de Componenten van de Kern van 0} AEM CIF ](https://github.com/adobe/aem-core-cif-components).[

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de invoegtoepassing CIF. Gebruikend de toe:voegen-op principes van CIF, zijn de product &amp; catalogusverzoeken op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ open-source van Magento ](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met productcatalogus met AEM-rendering

Als u catalogusblauwdruk gebruikt met Classic CIF, moet u de workflow voor de productcatalogus bijwerken. De invoegtoepassing CIF geeft nu direct ervaringen met productcatalogi weer met AEM-catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
