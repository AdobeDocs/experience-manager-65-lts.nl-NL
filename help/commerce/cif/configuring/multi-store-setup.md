---
title: Commerce Multi-Store Setup
description: Leer hoe u meerdere winkelweergaven van Adobe Commerce naar AEM kunt toewijzen. Hierdoor kunnen projecten ondersteuning bieden voor meertalige en meertalige gebruiksgevallen.
sub-product: Commerce
doc-type: technical-video
activity: setup
audience: administrator
feature: Commerce Integration Framework
solution: Experience Manager,Commerce
role: Admin, Developer
exl-id: 3a5d10d2-4ef8-4f85-942e-47ece6538acb
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Commerce Multi-Store Setup {#multi-store}

De AEM CIF Core-componenten kunnen worden gebruikt op meerdere AEM-sitestructuren en de onderliggende GraphQL-clientimplementatie kan verbinding maken met verschillende Adobe Commerce-winkels/winkelweergaven. Hierdoor kunnen projecten complexe multistore-/multisite-instellingen implementeren.

In een video wordt een overzicht gegeven van de opties voor het integreren van meerdere Adobe Commerce Store Views met Adobe Experience Manager Sites.

>[!VIDEO](https://video.tv.adobe.com/v/28952/?quality=12)

De AEM Multi-Site Management-functies van Live Copy en Language Copy worden samen met de Commerce integration framework gebruikt voor het wereldwijd beheren van sites in verschillende regio&#39;s en regio&#39;s.

De aanbevolen setup bestaat uit het gebruik van een 1:1-relatie tussen de AEM-site en de Adobe Commerce-winkelweergave.

Voer de onderstaande stappen uit om een AEM-site en AEM CIF Core Components aan te sluiten op een toegewijde winkelweergave:

## Configuratie {#configuration}

1. Vorm veelvoudige opslag &amp; opslagmeningen volgens het patroon dat in [ wordt beschreven Websites van Adobe Commerce, Opslag &amp; Weergaven ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)

2. Controleer of de verbinding tussen AEM en Adobe Commerce werkt.

3. Creeer een kindconfiguratie van CIF Cloud Service config die deze stappen volgt:

   * In AEM gaat naar Hulpmiddelen > Algemeen > [ Browser van de Configuratie ](/help/sites-administering/configurations.md#using-configuration-browser)
   * Selecteer de basisconfiguratie die u hebt gemaakt
   * Een configuratie maken met de stappen die hierboven in punt 2 worden beschreven

   Deze nieuwe configuratie wordt gecreeerd als kindconfiguratie van de basis. U kunt nu naar Extra > Algemeen > de Browser van de Configuratie gaan en de configuratiemontages creëren.

   >[!TIP]
   >
   >Commerce-catalogi kunnen worden geadresseerd met behulp van id&#39;s of UID&#39;s. UID&#39;s zijn geïntroduceerd in Adobe Commerce 2.4.2. Schakel deze optie alleen in als uw commerciële backend een GraphQL-schema van versie 2.4.2 of hoger ondersteunt.

4. Wijs de kindconfiguratie aan een plaats van AEM toe

   * Ga naar de AEM Sites-console
   * Navigeer aan het gebied of de taalwortel van uw plaatsstructuur, bijvoorbeeld, /content/venia/us _of_ /content/venia/us/nl voor de Venia steekproefpagina
   * Selecteer de pagina en open de pagina-eigenschappen
   * Selecteer het tabblad Geavanceerd
   * Selecteer in de sectie `Configuration` de configuratie die u bij stap hebt gemaakt

## Aanvullende bronnen

* [ Websites van Adobe Commerce, Opslag &amp; Mening ](https://experienceleague.adobe.com/docs/commerce-admin/start/setup/websites-stores-views.html)
* [ de Componenten van de Kern van AEM CIF - Multistore/plaatconfiguratie ](https://github.com/adobe/aem-core-cif-components#multi-store--site-configuration)
* [ Gebruikend Manager Van meerdere plaatsen ](https://experienceleague.adobe.com/docs/experience-manager-learn/sites/translation/multi-site-manager-feature-video-use.html)
* [Inhoud opnieuw gebruiken: Sitebeheer en Live kopiëren](/help/sites-administering/msm.md)
