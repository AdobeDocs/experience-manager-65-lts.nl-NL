---
title: Exporteren van ervaringsfragmenten naar Adobe Target
description: Leer hoe u Adobe Experience Manager (AEM) Experience Fragments exporteert naar Adobe Target.
contentOwner: carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 39473f0a-e4ee-4372-a0ea-ccf5d32501b9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1438'
ht-degree: 0%

---

# Exporteren van ervaringsfragmenten naar Adobe Target{#exporting-experience-fragments-to-adobe-target}

U kunt [ Fragmenten van de Ervaring ](/help/sites-authoring/experience-fragments.md) uitvoeren, die in Adobe Experience Manager (AEM), aan Adobe Target (Doel) worden gecreeerd. Zij kunnen dan als aanbiedingen in de activiteiten van het Doel worden gebruikt, om, ervaringen op schaal te testen en te personaliseren.

Er zijn drie formaatopties beschikbaar voor het uitvoeren van een Fragment van de Ervaring naar Adobe Target:

* HTML (standaard): ondersteuning voor het web en de levering van hybride inhoud
* JSON: ondersteuning voor levering van inhoud zonder kop
* HTML &amp; JSON

AEM Experience Fragments kan worden geëxporteerd naar de standaardwerkruimte in Adobe Target of naar door de gebruiker gedefinieerde werkruimten voor Adobe Target. Dit wordt gedaan gebruikend Adobe Developer Console, waarvoor AEM [ met Adobe Target moet worden geïntegreerd gebruikend IMS ](/help/sites-administering/setting-up-ims-integrations-for-aem.md).

>[!NOTE]
>
>[ IMS de integratie wordt nu gevormd met S2S OAuth ](/help/sites-administering/setting-up-ims-integrations-for-aem.md).
>
>De vorige configuraties werden gemaakt met [ geloofsbrieven JWT die nu onderworpen aan verval in Adobe Developer Console ](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md) zijn.

>[!NOTE]
>
>De Adobe Target-werkruimten bestaan niet in Adobe Target zelf. Deze worden gedefinieerd en beheerd in Adobe IMS (Identity Management System) en vervolgens geselecteerd voor gebruik in verschillende oplossingen met behulp van integratie vanuit de Adobe Developer Console.

>[!NOTE]
>
>De werkruimten van Adobe Target kunnen worden gebruikt om leden van een organisatie (groep) toe te staan om aanbiedingen en activiteiten voor deze organisatie slechts tot stand te brengen en te beheren; zonder toegang tot andere gebruikers te verlenen. Bijvoorbeeld landspecifieke organisaties binnen een wereldwijd bereik.

>[!NOTE]
>
>Zie ook voor meer informatie:
>
>* [ de ontwikkeling van Adobe Target ](https://developers.adobetarget.com/)
>* [ Componenten van de Kern - de Fragmenten van de Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html)
>

## Vereisten {#prerequisites}

Er zijn verschillende acties vereist:

1. U moet [ AEM met Adobe Target integreren gebruikend IMS ](/help/sites-administering/setting-up-ims-integrations-for-aem.md).

   >[!NOTE]
   >
   >[ IMS de integratie wordt nu gevormd met S2S OAut ](/help/sites-administering/setting-up-ims-integrations-for-aem.md).
   >
   >De vorige configuraties werden gemaakt met [ geloofsbrieven JWT die nu onderworpen aan verval in Adobe Developer Console ](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md) zijn.

1. De Fragmenten van de ervaring worden uitgevoerd van de de auteurinstantie van AEM, zodat moet u [ de Verbinding van AEM uiterlijk vormen ](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer) op de auteursinstantie om ervoor te zorgen dat om het even welke verwijzingen binnen het Fragment van de Ervaring voor Weblevering worden geexternaliseerd.

   >[!NOTE]
   >
   >Voor verbinding die niet door het gebrek herschrijft, is de [ Verstrekker van de Verbinding van het Fragment van de Ervaring Rewriter ](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html) beschikbaar. Met dit, kunnen de aangepaste regels voor uw geval worden ontwikkeld.

## Cloudconfiguratie toevoegen {#add-the-cloud-configuration}

Alvorens een fragment uit te voeren, moet u de **Configuratie van de Wolk** voor **Adobe Target** aan het fragment, of de omslag toevoegen. Hierdoor kunt u ook:

* Geef de indelingsopties op die voor het exporteren moeten worden gebruikt
* een doelwerkruimte selecteren als doel
* Selecteer een externalizer-domein voor het herschrijven van verwijzingen in het ervaringsfragment (optioneel)

De vereiste opties kunnen in **Eigenschappen van de Pagina** van de vereiste omslag en/of het fragment worden geselecteerd; de specificatie zal zonodig worden geërft.

1. Navigeer aan de **console van de Fragmenten van de Ervaring**.

1. Open **Eigenschappen van de Pagina** voor de aangewezen omslag of het fragment.

   >[!NOTE]
   >
   >Als u de wolkenconfiguratie aan de ouderomslag van het Fragment van de Ervaring toevoegt, wordt de configuratie geërft door alle kinderen.
   >
   >
   >Als u de wolkenconfiguratie aan het Fragment van de Ervaring zelf toevoegt, wordt de configuratie geërft door alle variaties.

1. Selecteer de **tabel van de Diensten van de Wolk 0} {.**

1. Onder **Configuratie van Cloud Service**, uitgezochte **Adobe Target** van de drop-down lijst.

   >[!NOTE]
   >
   >De JSON-indeling van een Experience Fragment-aanbieding kan worden aangepast. Hiertoe definieert u een componentervaringsfragmentcomponent en noteert u vervolgens hoe u de eigenschappen ervan in het deelstijlmodel exporteert.
   >
   >Zie de kerncomponent:
   >
   >[ Componenten van de Kern - de Fragmenten van de Ervaring ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/wcm-components/experience-fragment.html)

   Onder **Adobe Target** uitgezocht:

   * de juiste configuratie
   * de optie voor de vereiste indeling
   * een Adobe Target-werkruimte
   * indien nodig - het Externalalizer-domein

   >[!CAUTION]
   >
   >Het ExternalAlizer-domein is optioneel.
   >
   >Een externalizer van AEM wordt gevormd wanneer u de uitgevoerde inhoud aan specifiek *wilt richten publiceert* domein. Voor meer details, zie [ Vormend de Verbinding Externalzer van AEM ](/help/sites-administering/target-requirements.md#configuring-the-aem-link-externalizer).
   >
   >Houd er ook rekening mee dat Externe domeinen alleen relevant zijn voor de inhoud van het ervaringsfragment dat naar Doel wordt verzonden, en niet voor metagegevens zoals Inhoud weergaveaanbod.

   Bijvoorbeeld voor een map:

   ![ Omslag - de Omslag van de Diensten van de Wolk ](assets/xf-target-integration-01.png " - de Diensten van de Wolk ")

1. **sparen &amp; sluit**.

## Een ervaringsfragment exporteren naar Adobe Target {#exporting-an-experience-fragment-to-adobe-target}

>[!CAUTION]
>
>Voor media-elementen, zoals afbeeldingen, wordt alleen een verwijzing naar Doel geëxporteerd. Het element zelf blijft opgeslagen in AEM Assets en wordt geleverd via het AEM-publicatie-exemplaar.
>
>Daarom moet het Experience Fragment, met alle gerelateerde elementen, worden gepubliceerd voordat het naar Target wordt geëxporteerd.

Een ervaringsfragment exporteren van AEM naar Target (nadat u de Cloud Configuration hebt opgegeven):

1. Navigeer naar de Experience Fragment-console.
1. Selecteer het ervaringsfragment dat u naar doel wilt exporteren.

   >[!NOTE]
   >
   >Het moet een variant van het Web van het Fragment van de Ervaring zijn.

1. Klik **Uitvoer aan Adobe Target**.

   >[!NOTE]
   >
   >Als het Fragment van de Ervaring reeds is uitgevoerd, uitgezochte **Update in Adobe Target**.

1. Klik **Uitvoer zonder het publiceren** of **publiceren** zoals vereist.

   >[!NOTE]
   >
   >Het selecteren **publiceert** publiceert het Fragment van de Ervaring onmiddellijk en verzendt het naar Doel.

1. Klik **O.K.** in de bevestigingsdialoog.

   Het ervaringsfragment moet nu Doel zijn.

   >[!NOTE]
   >
   >[ de Diverse details ](/help/sites-authoring/experience-fragments.md#details-of-your-experience-fragment) van de uitvoer kunnen in **Mening van de Lijst** van de console en **Eigenschappen** worden gezien.

   >[!NOTE]
   >
   >Wanneer het bekijken van een Fragment van de Ervaring in Adobe Target, is de *laatst gewijzigde* datum die wordt gezien de datum dat het fragment het laatst in AEM werd gewijzigd, niet de datum dat het fragment het laatst werd uitgevoerd naar Adobe Target.

>[!NOTE]
>
>Alternatief, kunt u de uitvoer van de paginaredacteur uitvoeren, gebruikend vergelijkbare bevelen in het [ menu van de Informatie van de Pagina ](/help/sites-authoring/author-environment-tools.md#page-information).

## Uw ervaringsfragmenten in Adobe Target gebruiken {#using-your-experience-fragments-in-adobe-target}

Nadat u de voorgaande taken hebt uitgevoerd, wordt het Experience Fragment weergegeven op de pagina Offers in Adobe Target. Bekijk de [ specifieke documentatie van het Doel ](https://experienceleague.adobe.com/docs/target/using/experiences/offers/aem-experience-fragments.html) om over te leren wat u daar kunt bereiken.

>[!NOTE]
>
>Wanneer het bekijken van een Fragment van de Ervaring in Adobe Target, is de *laatst gewijzigde* datum die wordt gezien de datum dat het fragment het laatst in AEM werd gewijzigd, niet de datum dat het fragment het laatst werd uitgevoerd naar Adobe Target.

## Een ervaringsfragment verwijderen dat al naar Adobe Target is geëxporteerd {#deleting-an-experience-fragment-already-exported-to-adobe-target}

Als u een ervaringsfragment verwijdert dat al naar Target is geëxporteerd, kan dit problemen veroorzaken als het fragment al in een aanbieding in Adobe Target wordt gebruikt. Als u het fragment verwijdert, wordt het aanbod onbruikbaar omdat de fragmentinhoud door AEM wordt geleverd.

Om dergelijke situaties te voorkomen:

* Als het ervaringsfragment momenteel niet wordt gebruikt in een activiteit, staat AEM de gebruiker toe om het fragment zonder een waarschuwingsbericht te schrappen.
* Als het ervaringsfragment in gebruik is door een activiteit in Adobe Target, wordt de AEM-gebruiker een foutbericht gegeven over de mogelijke gevolgen die het verwijderen van het fragment kan hebben voor de activiteit.

  Het foutbericht in AEM belet de gebruiker niet (geforceerd) het ervaringsfragment te verwijderen. Als het ervaringsfragment wordt verwijderd:

   * De Target-aanbieding met AEM Experience Fragment kan ongewenste werking vertonen

      * Het aanbod wordt waarschijnlijk nog steeds weergegeven, aangezien het Experience Fragment HTML naar Target werd geduwd
      * Eventuele verwijzingen in het ervaringsfragment werken mogelijk niet correct als middelen waarnaar wordt verwezen ook in AEM worden verwijderd.

   * Eventuele verdere wijzigingen in het ervaringsfragment zijn onmogelijk omdat het ervaringsfragment niet meer bestaat in AEM.


## ClientLibs verwijderen uit Experience Fragments geëxporteerd naar Target {#removing-clientlibs-from-fragments-exported-target}

De Fragmenten van de ervaring bevatten volledige HTML- markeringen en alle noodzakelijke Bibliotheken van de Cliënt (CSS/JS) om het fragment precies terug te geven aangezien het door de Inhoudsauteur van het Fragment van de Ervaring werd gecreeerd. Dit is bijontwerp.

Wanneer u een Experience Fragment Offer met Adobe Target gebruikt op een pagina die wordt geleverd door AEM, bevat de doelpagina al alle benodigde clientbibliotheken. Bovendien is vreemde html in de Aanbieding van het Fragment van de Ervaring niet nodig één van beide (zie [ Overwegingen ](#considerations)).

Hier volgt een pseudo-voorbeeld van de HTML in een Experience Fragment-aanbieding:

```html
<!DOCTYPE>
<html>
   <head>
      <title>…</title>
      <!-- all the client libraries (css/js) -->
      …
   </head>
   <body>
        <!--/* Actual XF Offer content would appear here... */-->
   </body>
</html>
```

Op een hoog niveau doet AEM bij het exporteren van een Experience-fragment naar Adobe Target dat met behulp van verschillende extra Sling Selectors. De URL voor het geëxporteerde ervaringsfragment kan er bijvoorbeeld als volgt uitzien (opmerking `nocloudconfigs.atoffer`):

* http://www.your-aem-instance.com/content/experience-fragments/my-offers/my-xf-offer.nocloudconfigs.atoffer.html

De kiezer van `nocloudconfigs` wordt gedefinieerd met HTML en kan worden bedekt door deze te kopiëren uit:

* /libs/cq/experience-fragments/components/xfpage/nocloudconfigs.html

De `atoffer` selecteur wordt toegepast post-verwerking gebruikend [ het Schipen Rewriter ](/help/sites-developing/experience-fragments.md#the-experience-fragment-link-rewriter-provider-html). Of kan worden gebruikt om de Bibliotheken van de Cliënt te verwijderen.

### Voorbeeld {#example}

Laten we hier illustreren hoe u dit kunt doen met `nocloudconfigs` .

>[!NOTE]
>
>Zie [ Bewerkbare Malplaatjes ](/help/sites-developing/templates.md#editable-templates) voor verdere details.

#### Bedekkingen {#overlays}

In dit bijzondere voorbeeld, zullen de [ bekledingen ](/help/sites-developing/overlays.md) die worden omvat de Bibliotheken van de Cliënt *en* de vreemde html verwijderen. Aangenomen wordt dat u al het Sjabloontype voor fragmenten uit ervaring hebt gemaakt. De volgende bestanden moeten worden gekopieerd uit `/libs/cq/experience-fragments/components/xfpage/` :

* `nocloudconfigs.html`
* `head.nocloudconfigs.html`
* `body.nocloudconfigs.html`

#### Sjabloonoverlays {#template-type-overlays}

In dit voorbeeld is dit de volgende structuur:

![ malplaatje-Type Bedekkingen ](assets/xf-target-integration-02.png " malplaatje-Type Bedekkingen ")

De inhoud van deze bestanden is als volgt:

* `body.nocloudconfigs.html`

  ![ body.nocloudconfigs.html ](assets/xf-target-integration-03.png " body.nocloudconfigs.html ")

* `head.nocloudconfigs.html`

  ![ head.nocloudconfigs.html ](assets/xf-target-integration-04.png " head.nocloudconfigs.html ")

* `nocloudconfigs.html`

  ![ nocloudconfigs.html ](assets/xf-target-integration-05.png " nocloudconfigs.html ")

>[!NOTE]
>
>Als u `data-sly-unwrap` wilt gebruiken om de tag body te verwijderen, hebt u `nocloudconfigs.html` nodig.

### Overwegingen {#considerations}

Als u zowel AEM-sites als niet-AEM-sites wilt ondersteunen met behulp van Experience Fragment-aanbiedingen in Adobe Target, moet u twee Experience Fragments (twee verschillende sjabloontypen) maken:

* Eén met de overlay om clientlibs/extra html te verwijderen

* Een die niet de overlay heeft en daarom de vereiste clientlibs bevat
