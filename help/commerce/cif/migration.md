---
title: Migratie naar de invoegtoepassing AEM Commerce integration framework (CIF)
description: Migreren naar de AEM Commerce integration framework-invoegtoepassing (CIF) vanuit een oude versie.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: 847c33c1-17d6-447a-9f2c-91f2a81a3f04
source-git-commit: 981b175b039fd7ffbddf558a77d2da2fed52ad79
workflow-type: tm+mt
source-wordcount: '259'
ht-degree: 0%

---

# Migratiehandleiding voor de Experience Manager-invoegtoepassing {#cif-migration}

Deze handleiding helpt u de gebieden te identificeren die u voor de Experience Manager-add-on migratie moet bijwerken.

## CIF-invoegtoepassing

CIF toe:voegen-op is beschikbaar via het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?fulltext=commerce*&2_group.propertyvalues.property=.%2Fjcr%3Acontent%2Fmetadata%2Fdc%3Aversion&2_group.propertyvalues.operation=equals&2_group.propertyvalues.0_values=target-version%3Aem%2F6-5-lts&orderby=%40jcr%3Acontent%2Fjcr%3AlastGewijzigd&orderby.sort desc&layout=list&p.offset=0&p.limit=16). Het is compatibel en biedt dezelfde functies als de CIF-invoegtoepassing voor Experience Manager as a Cloud Service.

Zie [ Begonnen het worden met de Inhoud van AEM en Commerce ](getting-started.md).

Om projecten te steunen die CIF opstellen, verstrekt Adobe {de Componenten van de Kern van 0} AEM CIF [.](https://github.com/adobe/aem-core-cif-components)

## Productcatalogus

Het importeren van productcatalogusgegevens wordt niet ondersteund door de invoegtoepassing CIF. Gebruikend de toe:voegen-op principes van CIF, zijn de product &amp; catalogusverzoeken op bestelling via vraag in real time aan een externe handelsoplossing. Ga naar hoofdstuk Integrating om meer over het integreren van een handelsoplossing te leren.

>[!TIP]
>
>Als er geen real-time API&#39;s beschikbaar zijn, moet een externe productcache met API&#39;s worden gebruikt voor de integratie. Voorbeeld [ open-source van Magento ](https://business.adobe.com/products/magento/open-source.html).

## Ervaringen met productcatalogus met AEM-rendering

Als u catalogusblauwdruk gebruikt met Classic CIF, moet u de workflow voor de productcatalogus bijwerken. De invoegtoepassing CIF geeft nu direct ervaringen met productcatalogi weer met AEM-catalogussjablonen. Geen replicatie van productgegevens of productpagina&#39;s meer wordt vereist.

## Interactie voor gegevens en winkelen die niet in cache kunnen worden geplaatst

De cliënt-zijverzoeken voor niet cacheable gegevens en de interactie (bijvoorbeeld, toe:voegen-aan-kart, onderzoek) zouden rechtstreeks naar het handelseindpunt (of handelsoplossing of integratielaag) via CDN/Dispatcher moeten gaan. Verwijder om het even welke vraag waar AEM enkel een volmacht was.
