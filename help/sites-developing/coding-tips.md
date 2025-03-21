---
title: Codetips
description: Lees wat tips voor het coderen van best practices in Adobe Experience Manager.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: e431a240-45a2-4222-b854-32b90e5cd100
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '857'
ht-degree: 0%

---

# Codetips{#coding-tips}

## Gebruik zo veel mogelijk tags of HTML {#use-taglibs-or-htl-as-much-as-possible}

Het opnemen van scriptlets in JSPs maakt het moeilijk om kwesties in de code te zuiveren. Door scriptlets in JSPs op te nemen, is het ook moeilijk om bedrijfslogica van de meningslaag te scheiden, die een schending van het Enige Verantwoordelijkheidsbeginsel en het ontwerppatroon MVC vormt.

### Leesbare code schrijven {#write-readable-code}

Code wordt één keer geschreven, maar vaak gelezen. Als u enige tijd vooruit besteedt aan het opschonen van de geschreven code, wordt het verschil over de weg verdeeld terwijl u en andere ontwikkelaars het later lezen.

### Namen kiezen die bedoeld zijn om te onthullen {#choose-intention-revealing-names}

Idealiter hoeft een andere programmeur geen module te openen om te begrijpen wat deze doet. Ze moeten ook kunnen zien wat een methode doet zonder deze te lezen. Hoe beter u zich op deze ideeën kunt abonneren, hoe gemakkelijker het is om de code te lezen en hoe sneller u de code kunt schrijven en wijzigen.

In de basis van de AEM-code worden de volgende conventies gebruikt:


* Een enkele implementatie van een interface heeft de naam `<Interface>Impl` , dat wil zeggen `ReaderImpl` .
* Meerdere implementaties van een interface hebben de naam `<Variant><Interface>` , dat wil zeggen `JcrReader` en `FileSystemReader` .
* Abstracte basisklassen krijgen de naam `Abstract<Interface>` of `Abstract<Variant><Interface>` .
* Pakketten krijgen de naam `com.adobe.product.module` . Elke Maven-artefact- of OSGi-bundel moet een eigen pakket hebben.
* Java™-implementaties worden in een impl-pakket onder de bijbehorende API geplaatst.


Deze overeenkomsten zijn niet noodzakelijk van toepassing op klantenimplementaties, maar het is belangrijk dat de overeenkomsten worden bepaald en vastgehouden zodat de code houdbaar kan blijven.

In het ideale geval zouden namen hun intentie moeten onthullen. Een gemeenschappelijke codetest voor wanneer de namen niet zo duidelijk zijn aangezien zij zouden moeten zijn de aanwezigheid van commentaren die verklaren wat de variabele of de methode voor zijn:

<table>
 <tbody>
  <tr>
   <td><p><strong>Onduidelijk</strong></p> </td>
   <td><p><strong>Wissen</strong></p> </td>
  </tr>
  <tr>
   <td><p>int d; //verstreken tijd in dagen</p> </td>
   <td><p>int elapsedTimeInDays;</p> </td>
  </tr>
  <tr>
   <td><p>//get getagde afbeeldingen <br /> public List getItems() {}</p> </td>
   <td><p>public List getTaggedImages() {}</p> </td>
  </tr>
 </tbody>
</table>

### Niet herhalen  {#don-t-repeat-yourself}

DRY geeft aan dat dezelfde codeset nooit mag worden gedupliceerd. Dit geldt ook voor zaken als letterlijke tekenreeksen. Codeduplicatie opent de deur voor defecten wanneer iets moet veranderen en moet worden gezocht en geëlimineerd.

### Naakte CSS-regels vermijden {#avoid-naked-css-rules}

CSS-regels moeten specifiek zijn voor uw doelelement in de context van uw toepassing. Bijvoorbeeld, zou een CSS regel die op *wordt toegepast.content.center* te ruim zijn en zou kunnen uiteindelijk veel inhoud over uw systeem beïnvloeden, die anderen zou vereisen om deze stijl in de toekomst met voeten te treden. Terwijl, *.mijnapp-centertext* een specifiekere regel zou zijn aangezien het gecentreerde *tekst* in de context van uw toepassing specificeert.

### Gebruik van verouderde API&#39;s elimineren {#eliminate-usage-of-deprecated-apis}

Wanneer een API wordt afgekeurd, is het altijd beter om de nieuwe geadviseerde benadering te vinden in plaats van het vertrouwen op afgekeurde API. Hierdoor zijn upgrades in de toekomst vloeiender.

### Lokaliseerbare code schrijven {#write-localizable-code}

Om het even welke koorden die niet door een auteur worden geleverd zouden in een vraag aan AEM i18n woordenboek door *moeten worden verpakt I18n.get ()* in JSP/Java en *CQ.I18n.get ()* in JavaScript. Deze implementatie retourneert de tekenreeks die eraan is doorgegeven als er geen implementatie wordt gevonden. Dit biedt dus de flexibiliteit om lokalisatie te implementeren nadat de functies in de primaire taal zijn geïmplementeerd.

### Escape-hulpbronnenpaden voor veiligheid {#escape-resource-paths-for-safety}

Paden in het JCR mogen geen spaties bevatten, maar de aanwezigheid ervan mag er niet toe leiden dat code wordt afgebroken. Jasje verstrekt een het hulpprogrammaklasse van de Tekst van *escape ()* en *escapePath ()* methodes. Voor JSPs, stelt granite UI a *granite bloot:encodeURIPath () EL* functie.

### Gebruik de XSS API en/of HTML om tegen cross-site scripting aanvallen te beschermen {#use-the-xss-api-and-or-htl-to-protect-against-cross-site-scripting-attacks}

AEM biedt een XSS API om parameters eenvoudig te reinigen en de veiligheid van cross-site scripting aanvallen te garanderen. Bovendien heeft HTL deze beschermingen direct in de sjabloontaal ingebouwd. Een API bedriegblad is beschikbaar voor download bij [ Ontwikkeling - Richtlijnen en Beste praktijken ](/help/sites-developing/dev-guidelines-bestpractices.md).

### Pas het aangewezen registreren toe {#implement-appropriate-logging}

Voor code Java™, steunt AEM slf4j als standaard API voor het registreren van berichten en zou met de configuraties moeten worden gebruikt die door de console OSGi ter wille van consistentie in beleid ter beschikking worden gesteld. Slf4j stelt vijf verschillende registrerenniveaus bloot. Adobe raadt u aan de volgende richtlijnen te volgen wanneer u kiest op welk niveau een bericht moet worden geregistreerd:

* FOUT: Wanneer er iets in de code is verbroken en de verwerking niet kan worden voortgezet. Dit gebeurt vaak als gevolg van een onverwachte uitzondering. Het is handig om stacksporen in deze scenario&#39;s op te nemen.
* WAARSCHUWING: Als iets niet goed heeft gewerkt, maar de verwerking kan doorgaan. Dit zal vaak het resultaat van een uitzondering zijn die wij, zoals a *PathNotFoundException* verwachtten.
* INFO: informatie die nuttig zou zijn bij het controleren van een systeem. Onthoud dat dit de standaardinstelling is en dat de meeste klanten dit op hun plaats zullen laten in hun omgeving. Gebruik het daarom niet te veel.
* FOUTOPSPORING: informatie op een lager niveau over verwerking. Nuttig wanneer het zuiveren van een kwestie met steun.
* TRACE: Het laagste niveau van informatie, dingen zoals het invoeren/afsluiten van methoden. Dit zal gewoonlijk slechts door ontwikkelaars worden gebruikt.

Als er JavaScript is, *console.log* zou slechts tijdens ontwikkeling moeten worden gebruikt en alle logboekverklaringen zouden vóór versie moeten worden verwijderd.

### Ladingencatalogus vermijden {#avoid-cargo-cult-programming}

Vermijd het kopiëren van code zonder te begrijpen wat het doet. In geval van twijfel is het altijd beter om iemand te vragen die meer ervaring heeft met de module of API waarop u niet duidelijk bent.
