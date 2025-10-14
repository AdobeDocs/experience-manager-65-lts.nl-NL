---
title: Bedekkingen
description: Adobe Experience Manager gebruikt het principe van overlays om consoles en andere functies uit te breiden en aan te passen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d8fe6fb6-8ede-4fa7-95da-adee313bf768
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '587'
ht-degree: 0%

---

# Bedekkingen{#overlays}

Adobe Experience Manager (AEM)-en vóór dat, CQ-heeft lang het beginsel van bekledingen gebruikt om u uit te breiden en de [&#x200B; consoles &#x200B;](/help/sites-developing/customizing-consoles-touch.md) en andere functionaliteit (bijvoorbeeld, [&#x200B; pagina authoring &#x200B;](/help/sites-developing/customizing-page-authoring-touch.md)) aan te passen.

Bedekking is een term die in veel contexten wordt gebruikt. In deze context (AEM uitbreiden) betekent een overlay dat u de vooraf gedefinieerde functionaliteit moet overnemen en daar uw eigen definities op wilt leggen (om de standaardfunctionaliteit aan te passen).

In een standaardinstantie blijft de vooraf gedefinieerde functionaliteit onder `/libs` en het wordt aanbevolen de overlay (aanpassingen) onder de `/apps` -vertakking te definiëren. AEM gebruikt een onderzoekspad om een middel te vinden, die eerst de `/apps` tak en toen de `/libs` tak zoeken (de [&#x200B; onderzoekspad kan worden gevormd &#x200B;](#configuring-the-search-paths)). Dit mechanisme betekent dat uw bedekking (en de aanpassingen die daar worden bepaald) prioriteit heeft.

Sinds AEM 6.0 zijn er wijzigingen aangebracht in de manier waarop overlays worden geïmplementeerd en gebruikt:

* AEM 6.0 en op - voor [&#x200B; graniet &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) - verwante overlays (namelijk touch-enabled UI)

   * Methode

      * Reconstrueer de juiste `/libs` -structuur onder `/apps` .

        Dit vereist geen 1:1 exemplaar, wordt de [&#x200B; Verschuivende Fusie van het Middel &#x200B;](/help/sites-developing/sling-resource-merger.md) gebruikt om de originele definities van verwijzingen te voorzien die worden vereist. De het Verdelen Fusie van het Middel verleent de diensten om tot middelen met (het onderscheiden) mechanismen toegang te hebben en samen te voegen.

      * Breng onder `/apps` eventuele wijzigingen aan.

   * Voordelen

      * Meer robuust voor wijzigingen onder `/libs` .
      * Alleen opnieuw definiëren wat vereist is.

* Overlays en overlays die geen graniet zijn, ouder dan AEM 6.0

   * Methode

      * De inhoud kopiëren van `/libs` naar `/apps`

        Kopieer de volledige subvertakking, inclusief eigenschappen.

      * Breng onder `/apps` eventuele wijzigingen aan.

   * Nadelen

      * Hoewel de wijzigingen niet verloren gaan wanneer iets onder `/libs` verandert, moet u wellicht bepaalde wijzigingen die zich in de overlay onder `/apps` voordoen, opnieuw maken.

>[!CAUTION]
>
>De [&#x200B; Verschuivende Fusie van het Middel &#x200B;](/help/sites-developing/sling-resource-merger.md) en de verwante methodes kunnen slechts met [&#x200B; Graniet &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/jcr_root/libs/granite/ui/index.html) worden gebruikt. Dit betekent dat het maken van een bedekking met een skeletstructuur alleen geschikt is voor de standaardinterface met aanraakbediening.
>
>Bij overlays voor andere gebieden (inclusief de klassieke UI) worden het juiste knooppunt en de volledige substructuur gekopieerd en worden vervolgens de vereiste wijzigingen aangebracht.

De bekledingen zijn de geadviseerde methode voor vele veranderingen, zoals [&#x200B; vormend uw consoles &#x200B;](/help/sites-developing/customizing-consoles-touch.md#create-a-custom-console) of [&#x200B; creërend uw selectiecategorie aan activa browser in het zijpaneel &#x200B;](/help/sites-developing/customizing-page-authoring-touch.md#add-new-selection-category-to-asset-browser) (gebruikt wanneer het ontwerpen van pagina&#39;s). Zij zijn vereist als:

* ***maak geen* veranderingen in de `/libs` tak &#x200B;** Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:

   * upgrade uitvoeren op uw exemplaar
   * een hotfix toepassen
   * een functiepakket installeren

* Zij concentreren uw veranderingen in één plaats; makend het voor u gemakkelijker om, uw veranderingen te volgen, te migreren, file, of te zuiveren, zonodig.

## De zoekpaden configureren {#configuring-the-search-paths}

Voor bedekkingen is de geleverde bron een aggregaat van de opgehaalde bronnen en eigenschappen, afhankelijk van zoekpaden die kunnen worden gedefinieerd:

* Het middel **Weg van het Onderzoek van de Oplossen** zoals die in de [&#x200B; configuratie OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) voor de **Apache het Verdelen van de Factory van de Resolver van het Middel** wordt bepaald.

   * De top-down orde van onderzoekspaden wijst op hun respectieve prioriteiten.
   * In een standaardinstallatie, zijn de primaire gebreken `/apps`, `/libs` - zo heeft de inhoud van `/apps` een hogere prioriteit dan dat van `/libs` (namelijk het *overlays* het).

* Twee servicegebruikers hebben JCR nodig:ReAD toegang tot de locatie waar de scripts zijn opgeslagen. Deze gebruikers zijn: components-search-service (gebruikt door de componenten com.day.cq.wcm.coreto access/cache) en sling-scripting (gebruikt door org.apache.sling.servlets.resolver om servlets te zoeken).
* De volgende configuratie moet ook worden gevormd volgens waar u uw manuscripten (in dit voorbeeld onder /etc, /libs of /apps) zet.

  ```
  PID = org.apache.sling.jcr.resource.internal.JcrResourceResolverFactoryImpl
  resource.resolver.searchpath=["/etc","/apps","/libs"]
  resource.resolver.vanitypath.whitelist=["/etc/","/apps/","/libs/","/content/"]
  ```

* Tot slot moet de Resolver van Servlet ook worden gevormd (in dit voorbeeld, om /etc ook toe te voegen)

  ```
  PID = org.apache.sling.servlets.resolver.SlingServletResolver
  servletresolver.paths=["/bin/","/libs/","/apps/","/etc/","/system/","/index.servlet","/login.servlet","/services/"]
  ```

## Voorbeeld van gebruik {#example-of-usage}

Enkele voorbeelden worden behandeld wanneer:

* [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md)
* [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md)
