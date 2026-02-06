---
title: Ervaar fragmenten in Adobe Experience Manager Sites-ontwikkeling
description: Leer hoe u Experience Fragments kunt aanpassen voor Adobe Experience Manager.
contentOwner: AEM Docs
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: extending-aem
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: bc621086-8128-4836-a580-dca99f61c439
source-git-commit: d894bb145d70fba819cc8452056e9e46112e69d9
workflow-type: tm+mt
source-wordcount: '1750'
ht-degree: 0%

---

# Ervaar fragmenten {#experience-fragments}

## De basisbeginselen {#the-basics}

Een [&#x200B; Fragment van de Ervaring &#x200B;](/help/sites-authoring/experience-fragments.md) is een groep van één of meerdere componenten met inbegrip van inhoud en lay-out die binnen pagina&#39;s van verwijzingen kunnen worden voorzien.

Een primair of variantervaringsfragment, of beide, gebruikt het volgende:

* `sling:resourceType` : `/libs/cq/experience-fragments/components/xfpage`

Als er geen `/libs/cq/experience-fragments/components/xfpage/xfpage.html` is, wordt het volgende hersteld:

* `sling:resourceSuperType` : `wcm/foundation/components/page`

## De normale HTML-uitvoering {#the-plain-html-rendition}

Met de kiezer `.plain.` in de URL hebt u toegang tot de onbewerkte HTML-uitvoering.

Deze mogelijkheid is beschikbaar in de browser. Het primaire doel is echter om andere toepassingen (bijvoorbeeld webapps van derden, aangepaste mobiele implementaties) rechtstreeks toegang te geven tot de inhoud van het Experience Fragment door alleen de URL te gebruiken.

Met de normale HTML-uitvoering voegt u het protocol-, host- en contextpad toe aan paden die:

* van het type: `src`, `href` of `action`

* of eindigen met: `-src`, of `-href`

Bijvoorbeeld:

`.../brooklyn-coat/master.plain.html`

>[!NOTE]
>
>Koppelingen verwijzen altijd naar de publicatie-instantie. Derde partijen gebruiken ze, dus ze roepen altijd de koppeling van de instantie Publishing aan, niet de instantie Authoring.
>
>Voor meer informatie, zie [&#x200B; het Extern stellen URLs &#x200B;](/help/sites-developing/externalizer.md).

![&#x200B; xf-14 &#x200B;](assets/xf-14.png)

De gewone vertoningsselecteur gebruikt een transformator in tegenstelling tot extra manuscripten; [`Sling Rewriter` &#x200B;](https://sling.apache.org/documentation/bundles/output-rewriting-pipelines-org-apache-sling-rewriter.html) wordt gebruikt als transformator en gevormd bij het volgende:

* `/libs/experience-fragments/config/rewriter/experiencefragments`

### De generatie van HTML-uitvoeringen configureren {#configuring-html-rendition-generation}

De HTML-uitvoering wordt gegenereerd met behulp van de pijplijnen van `Sling Rewriter` . De pijpleiding wordt bepaald bij `/libs/experience-fragments/config/rewriter/experiencefragments`. De HTML Transformer ondersteunt de volgende opties:

* `allowedCssClasses`
   * Een RegEx-expressie die overeenkomt met de CSS-klassen die in de uiteindelijke uitvoering moeten blijven staan.
   * Nuttig als de klant enkele specifieke CSS-klassen wil verwijderen
* `allowedTags`
   * Een lijst met HTML-tags die zijn toegestaan in de uiteindelijke uitvoering.
   * Het systeem staat standaard de volgende tags toe zonder configuratie: html, head, title, body, img, p, span, ul, li, a, b, i, em, strong, h1, h2, h3, h4, h5, h6, br, `noscript`, div, link en script.

Men adviseert dat u rewriter gebruikend een bekleding vormt. Zie [&#x200B; Bedekkingen &#x200B;](/help/sites-developing/overlays.md)

## Sociale variaties {#social-variations}

Sociale varianten kunnen op sociale media (tekst en afbeelding) worden geplaatst. In Adobe Experience Manager (AEM) kunnen deze sociale varianten componenten bevatten, bijvoorbeeld tekstcomponenten en afbeeldingscomponenten.

U kunt de afbeelding en tekst voor de sociale post vanuit elk afbeeldings- of tekstbrontype op elke gewenste diepte plaatsen. De bronnen kunnen afkomstig zijn van de bouwsteen of de lay-outcontainer.

Sociale variaties maken bouwstenen ook mogelijk en houden er rekening mee bij het uitvoeren van sociale acties (in de publicatieomgeving).

Om de correcte tekst en het beeld aan het sociale media netwerk te posten, moeten sommige overeenkomsten worden geëerbiedigd als u uw eigen aangepaste componenten ontwikkelt.

De volgende eigenschappen moeten worden gebruikt:

* Voor het extraheren van de afbeelding,

   * `fileReference`
   * `fileName`

* Voor het uitnemen van de tekst:

   * `text`

Alleen componenten die gebruikmaken van deze conventie worden in overweging genomen.

## Sjablonen voor ervaringsfragmenten {#templates-for-experience-fragments}

>[!CAUTION]
>
>***slechts*** [&#x200B; editable malplaatjes &#x200B;](/help/sites-developing/page-templates-editable.md) wordt gesteund voor de Fragmenten van de Ervaring.
>
>De Fragmenten van de ervaring kunnen slechts op pagina&#39;s worden gebruikt die op editable malplaatjes gebaseerd zijn.

Wanneer het ontwikkelen van een nieuw malplaatje voor de Fragmenten van de Ervaring, kunt u de standaardpraktijken voor een [&#x200B; editable malplaatje &#x200B;](/help/sites-developing/page-templates-editable.md) volgen.

Om een malplaatje van het Fragment van de Ervaring tot stand te brengen dat de **tovenaar van het Fragment van de Ervaring** ontdekt, moet u één van deze regelreeksen volgen:

1. Beide:

   1. Het middeltype van het malplaatje (de aanvankelijke knoop) moet erven van:
      `cq/experience-fragments/components/xfpage`

   1. De naam van de sjabloon moet beginnen met:
      `experience-fragments`
Gebruikers kunnen in `/content/experience-fragments` Experience Fragments maken, aangezien de eigenschap `cq:allowedTemplates` van deze map alle sjablonen bevat die een naam hebben die begint met `experience-fragment` . Klanten kunnen deze eigenschap bijwerken en hun eigen naamgevingsschema of sjabloonlocaties opnemen.

1. [&#x200B; Toegestane malplaatjes &#x200B;](/help/sites-authoring/experience-fragments.md#configure-allowed-templates-folder) kunnen in de console van de Fragmenten van de Ervaring worden gevormd.
<!--
1. Add the template details manually in `cq:allowedTemplates` on the `/content/experience-fragment` node.
-->

<!-- >[!NOTE]
>
>[Allowed templates](/help/sites-authoring/experience-fragments.md#configuring-allowed-templates) can be configured in the Experience Fragments console.
-->

## Componenten voor ervaringsfragmenten {#components-for-experience-fragments}

[&#x200B; ontwikkelend componenten &#x200B;](/help/sites-developing/components.md) voor gebruik met/in de Fragmenten van de Ervaring volgen standaardpraktijken.

De enige extra configuratie moet ervoor zorgen dat de componenten op het malplaatje worden toegestaan. Deze functionaliteit wordt bereikt met het [&#x200B; Beleid van de Inhoud &#x200B;](/help/sites-developing/page-templates-editable.md#content-policies).

## De Experience Fragment Link Rewriter Provider - HTML {#the-experience-fragment-link-rewriter-provider-html}

In AEM kunt u ervaringsfragmenten maken. Een ervaringsfragment:

* bestaat uit een groep componenten samen met een lay-out;
* kan bestaan onafhankelijk van een AEM-pagina.

Een van de gebruiksgevallen voor dergelijke groepen is het insluiten van inhoud in aanraakpunten van derden, zoals Adobe Target.

### Standaardkoppeling herschrijven {#default-link-rewriting}

Gebruikend de [&#x200B; Uitvoer aan de eigenschap van het Doel &#x200B;](/help/sites-administering/experience-fragments-target.md), kunt u:

* een fragment van de Ervaring tot stand brengen,
* er componenten aan toevoegen,
* en exporteer het als een Adobe Target-aanbieding in HTML-indeling of in JSON-indeling.

Deze eigenschap kan [&#x200B; op een auteursinstantie van AEM &#x200B;](/help/sites-administering/experience-fragments-target.md#Prerequisites) worden toegelaten. Het vereist een geldige Configuratie van Adobe Target, en configuraties voor de Verbinding Externalzer.

De functie Extern koppelen wordt gebruikt om te bepalen welke URL&#39;s correct zijn wanneer de HTML-versie van het doelaanbod wordt gemaakt. Deze versie wordt vervolgens naar Adobe Target verzonden. Adobe Target vereist openbare toegang tot alle koppelingen in een Target HTML-aanbieding. Publiceer het fragment van de Ervaring en om het even welke middelen die verbindingen verwijzen alvorens u hen gebruikt.


Wanneer u een HTML-doelaanbieding samenstelt, wordt standaard een aanvraag verzonden naar een aangepaste Sling-kiezer in AEM. Deze kiezer wordt `.nocloudconfigs.html` genoemd. Zoals de naam al aangeeft, wordt een eenvoudige HTML-rendering van een Experience-fragment gemaakt, maar worden cloudconfiguraties niet opgenomen (wat overbodige informatie zou zijn).

Nadat u de HTML-pagina hebt gegenereerd, wijzigt de `Sling Rewriter` -pijplijn de uitvoer:

1. De elementen `html` , `head` en `body` worden vervangen door `div` -elementen. De elementen `meta` , `noscript` en `title` worden verwijderd (dit zijn onderliggende elementen van het oorspronkelijke `head` -element en worden niet meegenomen wanneer ze worden vervangen door het `div` -element).

   Dit proces wordt uitgevoerd om ervoor te zorgen dat de HTML Target Offer kan worden opgenomen in Doelactiviteiten.

1. AEM wijzigt alle interne koppelingen in de HTML, zodat deze verwijzen naar een gepubliceerde bron.

   AEM volgt dit patroon voor kenmerken van HTML-elementen om te bepalen welke koppelingen moeten worden gewijzigd:

   1. `src` kenmerken
   1. `href` kenmerken
   1. `*-src` -kenmerken (zoals data-src, custom-src, enzovoort)
   1. `*-href` -kenmerken (zoals `data-href` , `custom-href` , `img-href` , enzovoort)

   >[!NOTE]
   >
   >De interne koppelingen in de HTML zijn meestal relatieve koppelingen, maar er kunnen zich gevallen voordoen waarin aangepaste componenten volledige URL&#39;s verschaffen in de HTML. AEM negeert deze volledig ontwikkelde URL&#39;s standaard en brengt geen wijzigingen aan.

   De koppelingen in deze kenmerken gaan door de AEM Link Externalzer `publishLink()` om de URL opnieuw te maken alsof deze op een gepubliceerd exemplaar staat en dus openbaar beschikbaar is.

Wanneer het gebruiken van een uit-van-de-doos implementatie, is het hierboven beschreven proces voldoende om de Aanbieding van het Doel van het Fragment van de Ervaring te produceren, en dan het naar Adobe Target uit te voeren. Er zijn echter enkele gebruiksgevallen die in dit proces niet in aanmerking worden genomen, waaronder de volgende:

* Sling Mapping is alleen beschikbaar voor de uitgeversinstantie.
* Dispatcher omleidt.

Voor deze gebruiksgevallen biedt AEM de Link Rewriter Provider Interface.

### Interface van Rewriter-provider koppelen {#link-rewriter-provider-interface}

Voor meer gecompliceerde gevallen, die niet door het [&#x200B; gebrek &#x200B;](#default-link-rewriting) worden behandeld, biedt AEM de Interface van de Leverancier van de Verbinding Rewriter aan. Deze workflow is een `ConsumerType` -interface die u als service in uw bundels kunt implementeren. Het omzeilt de wijzigingen die AEM uitvoert op interne koppelingen van een HTML-aanbieding, zoals deze worden weergegeven op basis van een Experience Fragment. Met deze interface kunt u het herschrijven van interne HTML-koppelingen aanpassen aan uw bedrijfsbehoeften.

Voorbeelden van gebruiksgevallen om deze interface als dienst uit te voeren omvatten:

* Sling Mappings worden ingeschakeld op de publicatie-instanties, maar niet op de auteurinstantie.
* Een Dispatcher of vergelijkbare technologie wordt gebruikt om URL&#39;s intern om te leiden.
* Er zijn `sling:alias` -mechanismen voor bronnen.

>[!NOTE]
>
>Deze interface verwerkt alleen de interne HTML-koppelingen van het gegenereerde doelaanbod.

De Link Rewriter Provider Interface ( `ExperienceFragmentLinkRewriterProvider`) ziet er als volgt uit:

```java
public interface ExperienceFragmentLinkRewriterProvider {

    String rewriteLink(String link, String tag, String attribute);

    boolean shouldRewrite(ExperienceFragmentVariation experienceFragment);

    int getPriority();

}
```

### Hoe te om de dienstverlener van de Verbinding te gebruiken Rewriter {#how-to-use-the-link-rewriter-provider-interface}

Om de interface te gebruiken, moet u eerst een bundel tot stand brengen die een nieuwe de dienstcomponent bevat die de Interface van de Leverancier van de Verbinding Rewriter uitvoert.

Deze service wordt gebruikt om in het dialoogvenster Exporteren van fragment uit ervaring naar doel te plaatsen voor toegang tot de verschillende koppelingen.

Bijvoorbeeld `ComponentService` :

```java
import com.adobe.cq.xf.ExperienceFragmentLinkRewriterProvider;
import com.adobe.cq.xf.ExperienceFragmentVariation;
import org.osgi.service.component.annotations.Service;
import org.osgi.service.component.annotations.Component;

@Component
@Service
public class GeneralLinkRewriter implements ExperienceFragmentLinkRewriterProvider {

    @Override
    public String rewriteLink(String link, String tag, String attribute) {
        return null;
    }

    @Override
    public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
        return false;
    }

    @Override
    public int getPriority() {
        return 0;
    }

}
```

Voor de dienst aan het werk, zijn er nu drie methodes die binnen de dienst moeten worden uitgevoerd:

* ` [shouldRewrite](#shouldrewrite)`
* ` [rewriteLink](#rewritelink)`

   * `rewriteLinkExample2`

* ` [getPriority](#priorities-getpriority)`

#### shouldRewrite {#shouldrewrite}

U moet aan het systeem erop wijzen of het de verbindingen moet herschrijven wanneer een vraag voor de Uitvoer aan Doel op een bepaalde wijziging van het Fragment van de Ervaring wordt gemaakt. U kunt dit **implementatie** doen door de volgende methode te gebruiken:


`shouldRewrite(ExperienceFragmentVariation experienceFragment);`

Bijvoorbeeld:

```java
@Override
public boolean shouldRewrite(ExperienceFragmentVariation experienceFragment) {
    return experienceFragment.getPath().equals("/content/experience-fragment/master");
}
```

Deze methode ontvangt, als parameter, de Variatie van het Fragment van de Ervaring die de Uitvoer naar systeem van het Doel momenteel herschrijft.

In het bovenstaande voorbeeld wilt u het volgende herschrijven:

* koppelingen aanwezig in `src`

* `href` alleen kenmerken

* voor een specifiek ervaringsfragment:
  `/content/experience-fragment/master`

Het systeem van de Uitvoer aan Doel negeert andere ErvingsFragments die door het overgaan, en deze dienst beïnvloedt hen niet.

#### rewriteLink {#rewritelink}

Voor de wijziging van het Fragment van de Ervaring die door het herschrijfproces wordt beïnvloed, gaat het te werk om de dienst te laten de verbinding herschrijven. Telkens wanneer een koppeling wordt aangetroffen in de interne HTML, wordt de volgende methode aangeroepen:

`rewriteLink(String link, String tag, String attribute)`

De methode ontvangt de parameters als invoer:

* `link`
De `String` -representatie van de koppeling die wordt verwerkt. Gewoonlijk een relatieve URL die naar de bron in de auteurinstantie verwijst.

* `tag`
De naam van het HTML-element dat wordt verwerkt.

* `attribute`
De exacte kenmerknaam.

Als het systeem Exporteren naar doel dit element bijvoorbeeld verwerkt, kunt u `CSSInclude` als volgt definiëren:

```java
<link rel="stylesheet" href="/etc.clientlibs/foundation/clientlibs/main.css" type="text/css">
```

De aanroep van de methode `rewriteLink()` wordt uitgevoerd met de volgende parameters:

```java
rewriteLink(link="/etc.clientlibs/foundation/clientlibs/main.css", tag="link", attribute="href" )
```

Wanneer u de dienst creeert, kunt u besluiten nemen die op de bepaalde input worden gebaseerd, en dan de verbinding dienovereenkomstig herschrijven.

U wilt bijvoorbeeld het `/etc.clientlibs` -gedeelte van de URL verwijderen en het juiste externe domein toevoegen. Om dingen eenvoudig te houden, denk dat u toegang tot een Resolver van het Middel voor uw dienst, zoals in `rewriteLinkExample2` hebt:

>[!NOTE]
>
>Voor meer informatie over hoe te om een middeloplosser door een de dienstgebruiker te krijgen, zie [&#x200B; Gebruikers van de Dienst in AEM &#x200B;](/help/sites-administering/security-service-users.md).

```java
private ResourceResolver resolver;

private Externalizer externalizer;

@Override
public String rewriteLink(String link, String tag, String attribute) {

    // get the externalizer service
    externalizer = resolver.adaptTo(Externalizer.class);
    if(externalizer == null) {
        // if there was an error, then we do not modify the link
        return null;
    }

    // remove leading /etc.clientlibs from resource link before externalizing
    link = link.replaceAll("/etc.clientlibs", "");

    // considering that we configured our publish domain, we directly apply the publishLink() method
    link = externalizer.publishLink(resolver, link);

    return link;
}
```

>[!NOTE]
>
>Als de bovenstaande methode `null` retourneert, laat het systeem Exporteren naar doel de koppeling zoals deze is, een relatieve koppeling naar een bron.

#### Prioriteiten - getPriority {#priorities-getpriority}

U hebt mogelijk verschillende services nodig om verschillende soorten fragmenten uit de ervaring te ondersteunen. U kunt een Algemene Dienst ook gebruiken om alle Fragmenten van de Ervaring uit te besteden en in kaart te brengen. In deze gevallen, conflicten over welke de dienst aan gebruik zou kunnen zich voordoen, zodat verstrekt AEM de mogelijkheid om **Prioriteiten** voor de verschillende diensten te bepalen. De prioriteiten worden bepaald volgens de methode:

* `getPriority()`

Met deze methode kunt u verschillende services gebruiken waarbij de methode `shouldRewrite()` true retourneert voor hetzelfde ervaringsfragment. De dienst die het hoogste aantal van zijn `getPriority()` methode terugkeert is de dienst die de Variatie van het Fragment van de Ervaring behandelt.

Als voorbeeld kunt u een `GenericLinkRewriterProvider` hebben die de basistoewijzing voor alle fragmenten van de Ervaring behandelt en wanneer de `shouldRewrite()` methode `true` voor alle Variaties van het Fragment van de Ervaring terugkeert. Voor verschillende specifieke ervaringsfragmenten wilt u wellicht speciale afhandeling. In dit geval kunt u dus een `SpecificLinkRewriterProvider` opgeven waarvoor de methode `shouldRewrite()` alleen waar retourneert voor bepaalde Ervings-fragmentvariaties. Om ervoor te zorgen dat `SpecificLinkRewriterProvider` wordt gekozen voor het verwerken van deze Experience Fragment-variaties, moet het in de `getPriority()` -methode een hoger getal retourneren dan `GenericLinkRewriterProvider.`
