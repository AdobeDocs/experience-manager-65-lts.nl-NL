---
title: De samenvoeging van Verkoopbronnen in AEM gebruiken
description: De het Verdelen Samenvoeging van het Middel verleent de diensten om tot middelen toegang te hebben en samen te voegen
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 6fb6e522-fb81-4ba2-90b2-aad68f8bfa9e
source-git-commit: 9bc1cad84bb14b7513ede1fff2c1a37768dac442
workflow-type: tm+mt
source-wordcount: '1238'
ht-degree: 0%

---

# De samenvoeging van Verkoopbronnen in AEM gebruiken{#using-the-sling-resource-merger-in-aem}

## Doel {#purpose}

Sling Resource Merger verleent de diensten om tot middelen toegang te hebben en samen te voegen. Het verstrekt afdiff (differentiërende) mechanismen voor allebei:

* **[Bedekkingen](/help/sites-developing/overlays.md)** van middelen die [ gevormde onderzoekspaden ](/help/sites-developing/overlays.md#configuring-the-search-paths) gebruiken.

* **treedt** van componentendialogen voor aanraking-toegelaten UI (`cq:dialog`) met voeten, gebruikend de hiërarchie van het middeltype (door middel van het bezit `sling:resourceSuperType`).

Sling Resource Merger combineert zowel overlay als override resources (en hun eigenschappen) met de oorspronkelijke bronnen en eigenschappen:

* De inhoud van de aangepaste definitie heeft een hogere prioriteit dan het origineel. Namelijk het *overlays* of *treedt* het met voeten.

* Waar noodzakelijk, [ eigenschappen ](#properties) die in de aanpassing worden bepaald, wijzen erop hoe de inhoud die van origineel wordt samengevoegd moet worden gebruikt.

>[!CAUTION]
>
>De het Verdelen Fusie van het Middel en verwante methodes kunnen slechts met [ Graniet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/granite-ui/api/index.html) worden gebruikt. Deze situatie betekent ook dat deze alleen geschikt is voor de standaardinterface met aanraakbediening. Met name overschrijvingen die op deze manier worden gedefinieerd, zijn alleen van toepassing voor het aanraakdialoogvenster van een component.
>
>Als u andere gebieden wilt bedekken of overschrijven (inclusief andere onderdelen van een component met aanraakbediening of de klassieke UI), kopieert u het desbetreffende knooppunt en de structuur van het origineel. Plaats de kopie op de plaats waar u de aanpassing definieert.

### Doelen voor AEM {#goals-for-aem}

De doelstellingen voor het gebruiken van de Verschuivende Fusie van Middel in AEM zijn:

* zorgt u ervoor dat er geen wijzigingen in de aanpassing worden aangebracht in `/libs` .
* reduceert de structuur die wordt gerepliceerd vanuit `/libs` .

  Wanneer u Sling Resource Merger gebruikt, wordt het niet aangeraden de volledige structuur van `/libs` te kopiëren. De reden hiervoor is dat er te veel informatie in de aanpassing wordt opgeslagen (meestal `/apps` ). Het dupliceren van informatie verhoogt onnodig de kans op problemen wanneer het systeem wordt bevorderd.

>[!NOTE]
>
>Overschrijvingen zijn niet afhankelijk van de zoekpaden. Ze gebruiken de eigenschap `sling:resourceSuperType` om de verbinding te maken.
>
>Overschrijvingen worden echter vaak gedefinieerd onder `/apps` , omdat aanpassingen het beste in AEM kunnen worden gedefinieerd onder `/apps` . De reden is dat u niets onder `/libs` moet wijzigen.

>[!CAUTION]
>
>** verander niets in de `/libs` weg.
>
>De reden is dat de inhoud van `/libs` de volgende keer dat u een upgrade uitvoert van de instantie, wordt overschreven. Het kan ook zijn dat deze wordt overschreven wanneer u een hotfix- of functiepakket toepast.
>
>De aanbevolen methode voor configuratie en andere wijzigingen is:
>
>1. Het vereiste item opnieuw maken (dat wil zeggen, zoals het in `/libs` staat) onder `/apps`
>
>1. Breng eventuele wijzigingen aan binnen `/apps`
>

### Eigenschappen {#properties}

De resourcefusie biedt de volgende eigenschappen:

* `sling:hideProperties` ( `String` of `String[]`)

  Geeft de eigenschap op, of een lijst met eigenschappen, die moet worden verborgen.

  Alle jokertekens worden verborgen. `*`

* `sling:hideResource` ( `Boolean`)

  Het geeft aan of de middelen volledig verborgen zijn, inclusief de kinderen.

* `sling:hideChildren` ( `String` of `String[]`)

  Het bevat het onderliggende knooppunt of de lijst met onderliggende knooppunten die moet worden verborgen. De eigenschappen van het knooppunt blijven behouden.

  Alle jokertekens worden verborgen. `*`

* `sling:orderBefore` ( `String`)

  Het bevat de naam van de sibling knoop die de huidige knoop voor van wordt geplaatst.

Deze eigenschappen beïnvloeden hoe de corresponderende / oorspronkelijke bronnen / eigenschappen (van `/libs`) worden gebruikt door de overlay / overschrijving (vaak in `/apps` ).

### De structuur maken {#creating-the-structure}

Als u een overlay wilt maken of overschrijven, moet u het oorspronkelijke knooppunt opnieuw maken, met de equivalente structuur, onder het doel (gewoonlijk `/apps` ). Bijvoorbeeld:

* Bedekking

   * De definitie van het navigatie-item voor de Sites-console, zoals weergegeven in de spoorstaaf, is gedefinieerd op:

     `/libs/cq/core/content/nav/sites/jcr:title`

   * Als u een bedekking wilt maken, maakt u het volgende knooppunt:

     `/apps/cq/core/content/nav/sites`

     Werk vervolgens de eigenschap `jcr:title` naar wens bij.

* Negeren

   * De definitie van het aanraakvenster voor de console van Teksten is als volgt:

     `/libs/foundation/components/text/cq:dialog`

   * Om met voeten te treden, creeer de volgende knoop. Bijvoorbeeld:

     `/apps/the-project/components/text/cq:dialog`

Als u een van beide wilt maken, hoeft u alleen de skeletstructuur opnieuw te maken. Om de recreatie van de structuur te vereenvoudigen, kunnen alle intermediaire knooppunten van het type `nt:unstructured` zijn (ze hoeven niet op het oorspronkelijke knooppunttype te wijzen. Bijvoorbeeld in `/libs` .

In het bovenstaande overlayvoorbeeld zijn dus de volgende knooppunten nodig:

```shell
/apps
  /cq
    /core
      /content
        /nav
          /sites
```

>[!NOTE]
>
>Wanneer u Sling Resource Merger gebruikt (dat wil zeggen, wanneer u werkt met de standaardinterface met aanraakbediening), wordt het niet aangeraden de volledige structuur te kopiëren van `/libs` . De reden is dat dit ertoe zou leiden dat er te veel informatie in `/apps` wordt opgeslagen. Dit kan problemen veroorzaken wanneer het systeem wordt bijgewerkt.

### Gebruik hoofdletters {#use-cases}

Met de standaardfunctionaliteit kunt u met deze gebruiksgevallen het volgende doen:

* **voeg een bezit** toe

  De eigenschap bestaat niet in de definitie `/libs` , maar is vereist in de `/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. Maak de nieuwe eigenschap op dit knooppunt &quot;

* **herdefinieert een bezit (niet auto-gecreeerde eigenschappen)**

  De eigenschap wordt gedefinieerd in `/libs` , maar er is een nieuwe waarde vereist in de `/apps` overlay/override.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. De overeenkomende eigenschap op dit knooppunt maken (onder `apps`)

      * Het bezit heeft een prioriteit die op de het Verspreiden configuratie van de Resolver van het Middel wordt gebaseerd.
      * Het wijzigen van het type eigenschap wordt ondersteund.

        Als u een ander type eigenschap gebruikt dan in `/libs` wordt gebruikt, wordt het type eigenschap dat u definieert gebruikt.

  >[!NOTE]
  >
  >Het wijzigen van het type eigenschap wordt ondersteund.

* **herdefinieert een auto-gecreeerde bezit**

  Standaard zijn automatisch gemaakte eigenschappen (zoals `jcr:primaryType` ) niet onderworpen aan een bedekking/overschrijving om ervoor te zorgen dat het knooppunttype dat momenteel onder `/libs` valt, wordt gerespecteerd. Als u een bedekking/overschrijving wilt toepassen, moet u het knooppunt opnieuw maken in `/apps` , de eigenschap expliciet verbergen en opnieuw definiëren:

   1. Maak het corresponderende knooppunt onder `/apps` met het gewenste `jcr:primaryType`
   1. Maak de eigenschap `sling:hideProperties` op dat knooppunt, met de waarde ingesteld op die van de eigenschap auto-created, bijvoorbeeld `jcr:primaryType`

      Deze eigenschap, gedefinieerd onder `/apps` , krijgt nu prioriteit boven de eigenschap die is gedefinieerd onder `/libs` .

* **herdefinieert een knoop en zijn kinderen**

  Het knooppunt en de onderliggende knooppunten worden gedefinieerd in `/libs` , maar er is een nieuwe configuratie vereist in de `/apps` -overlay/overschrijving.

   1. Combineer de handelingen van:

      1. Onderliggende items van een knooppunt verbergen (de eigenschappen van het knooppunt behouden)
      1. De eigenschap/eigenschappen opnieuw definiëren

* **verberg een bezit**

  De eigenschap wordt gedefinieerd in `/libs` , maar is niet vereist in de `/apps` overlay/overschrijving.

   1. Het corresponderende knooppunt maken binnen `/apps`
   1. Maak een eigenschap `sling:hideProperties` van het type `String` of `String[]` . Gebruik deze optie om de eigenschappen op te geven die moeten worden verborgen of genegeerd. Jokertekens kunnen ook worden gebruikt. Bijvoorbeeld:

      * `*`
      * `["*"]`
      * `jcr:title`
      * `["jcr:title", "jcr:description"]`

* **verberg een knoop en zijn kinderen**

  Het knooppunt en de onderliggende knooppunten worden gedefinieerd in `/libs` , maar zijn niet vereist in de `/apps` -overlay/overschrijving.

   1. Het corresponderende knooppunt maken onder `/apps`
   1. Een eigenschap maken `sling:hideResource`

      * type: `Boolean`
      * value: `true`

* **de kinderen van de Huid van een knoop (terwijl het houden van de eigenschappen van de knoop)**

  Het knooppunt, de eigenschappen en onderliggende knooppunten worden gedefinieerd in `/libs` . Het knooppunt en de bijbehorende eigenschappen zijn vereist in de `/apps` -overlay/overschrijving, maar sommige of alle onderliggende knooppunten zijn niet vereist in de `/apps` -overlay/overschrijving.

   1. Het corresponderende knooppunt maken onder `/apps`
   1. Maak de eigenschap `sling:hideChildren` :

      * type: `String[]`
      * waarde: een lijst met onderliggende knooppunten (zoals gedefinieerd in `/libs`) die moeten worden verborgen/genegeerd

      Jokerteken&amp;ast; kan worden gebruikt om alle onderliggende knooppunten te verbergen of te negeren.

* **opnieuw ordenen knopen**

  Het knooppunt en de knooppunten op hetzelfde niveau worden gedefinieerd in `/libs` . Als u de volgorde wilt wijzigen, maakt u het knooppunt opnieuw in de `/apps` -bedekking of -overschrijving. Definieer de nieuwe positie door te verwijzen naar het juiste knooppunt op hetzelfde niveau in `/libs` .


   * Gebruik de eigenschap `sling:orderBefore` :

      1. Het corresponderende knooppunt maken onder `/apps`
      1. Maak de eigenschap `sling:orderBefore` :

         Geeft het knooppunt aan (zoals in `/libs`) dat voor het huidige knooppunt wordt geplaatst:

         * type: `String`
         * value: `<before-SiblingName>`

### Roep de samenvoeging van het Verspreide Middel van uw code aan {#invoking-the-sling-resource-merger-from-your-code}

De samenvoeging van het Verspreide Middel omvat twee leveranciers van douanemiddel - voor bekledingen en een andere voor met voeten treedt. Elk element kan binnen de code worden aangeroepen met behulp van een koppelpunt:

>[!NOTE]
>
>Wanneer het toegang tot van uw middel, wordt het geadviseerd om het aangewezen koppelingspunt te gebruiken.
>
>Deze benadering roept de Verschuivende Fusie van het Middel aan en keert volledig samengevoegde middel terug. Het vermindert ook de hoeveelheid structuur die u van `/libs` moet kopiëren.

* Bedekking:

   * doel: voeg bronnen samen op basis van hun zoekpad
   * koppelpunt: `/mnt/overlay`
   * use: `mount point + relative path`
   * voorbeeld:

      * `getResource('/mnt/overlay' + '<relative-path-to-resource>');`

* Overschrijven:

   * doel: voeg bronnen samen op basis van hun supertype
   * koppelpunt: `/mnt/overide`
   * use: `mount point + absolute path`
   * voorbeeld:

      * `getResource('/mnt/override' + '<absolute-path-to-resource>');`

### Voorbeeld van het gebruik {#example-of-usage}

Enkele voorbeelden worden behandeld:

* Bedekking:

   * [De consoles aanpassen](/help/sites-developing/customizing-consoles-touch.md)
   * [Paginaontwerp aanpassen](/help/sites-developing/customizing-page-authoring-touch.md)

* Overschrijven:

   * [De pagina-eigenschappen configureren](/help/sites-developing/page-properties-views.md#configuring-your-page-properties)
