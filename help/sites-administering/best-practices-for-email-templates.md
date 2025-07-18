---
title: Aanbevolen procedures voor e-mailsjablonen
description: Vind beste praktijken bij het creëren van e-mailmalplaatjes in AEM.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration, best-practices
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 34678cae-3c7f-4c9f-b7b6-c1dd4e0758ad
index: false
source-git-commit: 2edf37c2d6bb04b418618f2780f773ab37559114
workflow-type: tm+mt
source-wordcount: '1072'
ht-degree: 0%

---


# Aanbevolen procedures voor e-mailsjablonen {#best-practices-for-email-templates}

>[!CAUTION]
>
>Dit artikel is op de afgekeurde componenten van de Stichting van toepassing die AEM e-mailcomponenten baseren.
>
>De gebruikers worden aangemoedigd om de moderne [ Componenten E-mailcomponenten van de Kern te gebruiken.](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/email/introduction.html?lang=nl-NL)

In dit document worden enkele van de aanbevolen procedures beschreven voor het ontwerpen van e-mailberichten. Dit resulteert in een goed ontwikkelde sjabloon voor e-mailcampagnes.

De demo-campagne in AEM volgt al deze best practices. Hoe de beste praktijken in de demo campagne worden uitgevoerd wordt beschreven voor elke beste praktijken.

Gebruik deze aanbevolen procedures bij het maken van uw eigen nieuwsbrief.

>[!NOTE]
>
>Alle inhoud van de campagne moet worden gemaakt onder een `master` pagina van het type `cq/personalization/components/ambitpage` .
>
>Als uw geplande campagnestructuur bijvoorbeeld ongeveer zo is
>
>`/content/campaigns/teasers/en/campaign-promotion-global`
>
>Controleer of het item zich onder een `master` -pagina bevindt
>
>`/content/campaigns/teasers/master/en/campaign-promotion-global`

>[!NOTE]
>
>Wanneer het creëren van een postmalplaatje voor Adobe Campaign, moet u het bezit **acMapping** met de waarde **mapRecipient** in de **jcr:content** knoop van het malplaatje omvatten. Als u niet, kunt u niet het malplaatje van Adobe Campaign in **Eigenschappen van de Pagina** van Experience Manager (het gebied is gehandicapt) selecteren.

## Sjabloon/pagina-component {#template-page-component}

***/libs/mcm/campagne/components/campagne_newsletterpage***

<table>
 <tbody>
  <tr>
   <td><strong>Beste praktijken</strong></td>
   <td><strong>Implementatie</strong></td>
  </tr>
  <tr>
   <td><p>Geef het documenttype op zodat u een consistente rendering garandeert.</p> <p>DOCTYPE aan het begin toevoegen (HTML of XHTML)</p> </td>
   <td><p>Is configureerbaar door ontwerp veranderend <i> cq:doctype </i> bezit in <i>"/etc/designs/default/jcr:content/campagne_newsletterpage"</i></p> <p>De standaardwaarde is "XHTML":</p> <p>&lt;!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional/EN" "https://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd"&gt;</p> <p>Kan worden gewijzigd in "HTML_5":</p> <p>&lt;!DOCTYPE HTML&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Geef een tekendefinitie op zodat speciale tekens correct worden weergegeven.</p> <p>CHARSET-declaratie (bijvoorbeeld iso-8859-15, UTF-8) toevoegen aan &lt;head&gt;</p> </td>
   <td><p>Is ingesteld op UTF-8.</p> <p>&lt;meta http-equiv="content-type" content="text/html; charset=UTF-8"&gt;</p> </td>
  </tr>
  <tr>
   <td><p>Codeer alle structuur met behulp van het &lt;table&gt;element. Voor complexere lay-outs moet u tabellen nesten om complexe structuren te maken.</p> <p>E-mail moet er goed uitzien, zelfs zonder css.</p> </td>
   <td><p>Tabellen worden in de gehele sjabloon gebruikt voor het structureren van inhoud. Momenteel met maximaal vier geneste tabellen (1 basislabel + max.) 3 nestniveaus)</p> <p>&lt;div&gt;-tags worden alleen in de ontwerpmodus gebruikt voor een juiste componentbewerking.</p> </td>
  </tr>
  <tr>
   <td>Gebruik elementkenmerken (zoals celopvulling, valsing en breedte) om tabelafmetingen in te stellen. Deze methode forceert een kader-modelstructuur.</td>
   <td><p>Alle lijsten bevatten noodzakelijke attributen zoals <i> grens </i>, <i> celpadding </i>, <i> het cel uit elkaar plaatsen </i>, en <i> breedte </i>.</p> <p>Om element het plaatsen binnen lijsten te harmoniseren, hebben alle lijstcellen de attributen <i> valign= "bovenkant"</i> die worden geplaatst.</p> </td>
  </tr>
  <tr>
   <td><p>Houd, indien mogelijk, rekening met de vriendelijkheid van mobiele apparaten. Gebruik mediaquery's om de tekstgrootte op kleine schermen te verhogen en selecteer aanraakgebieden met de grootte van het blokje voor koppelingen.</p> <p>Maak een e-mail ontvankelijk als het ontwerp het toestaat.</p> </td>
   <td>Voor zover CSS-stijlen worden gebruikt om demonstratieontwerp te illustreren, worden mediaquery's gebruikt om een mobiele versie aan te bieden.</td>
  </tr>
  <tr>
   <td>Inline CSS is beter dan het plaatsen van alle CSS aan het begin.</td>
   <td><p>Om de onderliggende HTML-structuur beter aan te tonen en de mogelijkheid om de nieuwsbrief-structuur aan te passen te vereenvoudigen, zijn slechts enkele CSS-definities gealigneerd.</p> <p>Basisstijlen en sjabloonvariaties zijn geëxtraheerd naar een stijlblok in de &lt;head&gt; van de pagina. Bij de definitieve indiening van de nieuwsbrief zijn deze CSS-definities in de HTML opgenomen. Een automatisch inlijningsmechanisme is gepland, maar is momenteel niet beschikbaar.</p> </td>
  </tr>
  <tr>
   <td>Houd uw CSS eenvoudig. Gebruik geen samengestelde stijldeclaraties, stenocode, CSS-lay-outeigenschappen, complexe kiezers en pseudo-elementen.</td>
   <td>Voor zover CSS-stijlen worden gebruikt om demonstratieontwerp te illustreren, worden de CSS-aanbevelingen gevolgd.</td>
  </tr>
  <tr>
   <td>E-mails moeten een maximale breedte van 600-800 pixels hebben. Deze grootte zorgt ervoor dat ze zich beter gedragen binnen de grootte van het voorvertoningsvenster die door veel clients wordt geboden.</td>
   <td>De <i> breedte </i> van inhoudstafel is beperkt tot 600 pixel in duoontwerp.</td>
  </tr>
 </tbody>
</table>

### Afbeeldingen {#images}

/libs/mcm/campagne/componenten/image

| **Beste praktijken** | **Implementatie** |
|---|---|
| Voeg *alt* attributen aan beelden toe | Het *alt* attribuut is bepaald als verplicht voor de beeldcomponent. |
| Gebruik *jpg* in plaats van *png* formaat voor beelden | Afbeeldingen worden altijd door de afbeeldingscomponent als JPG gebruikt. |
| Gebruik het element `<img>` in plaats van achtergrondafbeeldingen in een tabel. | Er worden geen achtergrondafbeeldingsgegevens gebruikt in de sjablonen. |
| Kenmerkstijl=&quot;weergaveblok&quot; toevoegen aan afbeeldingen. Als u dit doet, kunnen ze goed worden weergegeven op Gmail. | Alle beelden bevatten per gebrek *style= &quot;vertoningsblok&quot;* attributen. |

### Tekst en koppelingen {#text-and-links}

/libs/mcm/campagne/components/heading, /libs/mcm/campagne/components/textiel

<table>
 <tbody>
  <tr>
   <td><strong>Beste praktijken</strong></td>
   <td><strong>Implementatie</strong></td>
  </tr>
  <tr>
   <td>HTML &lt;font&gt; gebruiken in plaats van stijl in CSS (font-family)</td>
   <td>De RichTextEditor (bijvoorbeeld in de component TextImage) ondersteunt nu het kiezen en toepassen van lettertypefamilies en tekengrootten op geselecteerde teksten. Ze worden weergegeven als &lt;font&gt;-tags.</td>
  </tr>
  <tr>
   <td>Gebruik basis, dwars-platformdoopvonten zoals <i> Arial®, Verdana, Georgië </i>, en <i> Tijden Nieuwe Roman® </i>.</td>
   <td><p>Afhankelijk van het ontwerp van de nieuwsbrief.</p> <p>Voor het demo-ontwerp wordt het lettertype "Helvetica®" gebruikt, maar het wordt teruggezet naar een algemeen sans-serif-lettertype, indien dit niet aanwezig is.</p> </td>
  </tr>
 </tbody>
</table>

### Algemeen {#generic}

| **Beste praktijken** | **Implementatie** |
|---|---|
| Gebruik W3C-validatie om de HTML-code te corrigeren. Zorg ervoor dat alle open labels goed zijn gesloten. | Code is gevalideerd. Alleen voor XHTML-overgangsdocumenttype ontbreekt het ontbrekende xmlns-kenmerk voor het `<html>` -element. |
| Vermijd het gebruik van JavaScript of Flash. Deze technologieën worden vaak niet ondersteund door e-mailclients. | JavaScript of Flash wordt niet gebruikt in de sjabloon voor nieuwsbrieven. |
| Voeg een gewone tekstversie toe voor het verzenden van meerdere onderdelen. | Er is een nieuwe widget ingebouwd in de pagina-eigenschappen om eenvoudig een plaintekstversie uit de pagina-inhoud te extraheren. U kunt deze gebruiken als beginpunt voor de laatste plaintext-versie. |

## Sjablonen en voorbeelden voor nieuwsbrieven voor campagnes {#campaign-newsletter-templates-and-examples}

AEM wordt geleverd met verschillende sjablonen en componenten uit de verpakking die u kunt gebruiken voor het maken van nieuwsbrieven voor campagnes. U kunt deze sjablonen en componenten gebruiken om uw aangepaste nieuwsbrieven te maken.

### Sjablonen {#templates}

Om een stevige basis aan te bieden en de verscheidenheid van de mogelijkheden van de inhoudsstroom uit te breiden, zijn er drie lichtjes verschillende malplaatjetypes beschikbaar uit-van-de-doos. U kunt deze drie typen eenvoudig gebruiken om een aangepaste nieuwsbrief te maken.

Al hebben a **kopbal**, a **footer**, en a **lichaam** sectie. Onder de lichaamssectie, verschilt elk malplaatje in **kolomontwerp** (één, twee, of drie kolommen).

![ Varianten van mogelijke nieuwsbrieven ](assets/chlimage_1-69.png)

### Onderdelen {#components}

Er zijn momenteel [ zeven componenten beschikbaar voor gebruik binnen campagnemalplaatjes ](/help/sites-authoring/adobe-campaign-components.md). Deze componenten zijn allen gebaseerd op de prijsverhogingstaal van Adobe **HTML**.

| **de naam van de Component** | **de weg van de Component** |
|---|---|
| Kop | /libs/mcm/campagne/componenten/kop |
| Afbeelding | /libs/mcm/campagne/componenten/image |
| Tekst&amp;Personalization | /libs/mcm/campagne/componenten/personalisatie |
| Textimage | /libs/mcm/campagne/onderdelen/textielafbeelding |
| Koppeling | /libs/mcm/campagne/componenten/reference |
| Dynamic Media Classic (voorheen Scene7)-afbeeldingssjabloon | /libs/mcm/campagne/s7image |
| Gerichte referentie | /libs/mcm/campagne/componenten/reference |

>[!NOTE]
>
>Deze componenten zijn geoptimaliseerd voor e-mailinhoud, dat wil zeggen dat ze de beste werkwijzen volgen die in dit document worden beschreven. Het gebruiken van andere uit-van-de-doos componenten schendt gewoonlijk deze regels.

Deze componenten worden beschreven in detail in [ de componenten van Adobe Campaign ](/help/sites-authoring/adobe-campaign-components.md).
