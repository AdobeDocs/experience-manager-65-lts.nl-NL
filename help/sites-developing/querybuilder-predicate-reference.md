---
title: Voorlopige naslaggids voor Query Builder
description: Volledige predikate verwijzing voor de Bouwer van de Vraag API.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: platform
solution: Experience Manager, Experience Manager Sites
feature: Developing,Search,Query Builder
role: Developer
exl-id: c044d541-24d6-4975-9b38-6a4317a16358
source-git-commit: a85b54d5a7c3b00f95f439941a390dcfee883187
workflow-type: tm+mt
source-wordcount: '2291'
ht-degree: 0%

---

# Voorlopige naslaggids voor Query Builder{#query-builder-predicate-reference}

>[!CAUTION]
>
>De informatie op deze pagina is niet volledig.
>
>Voor volledige informatie, zie de lijst onder **Beschikbare predikaten** op de Debugger van de Bouwer van de Vraag console; bijvoorbeeld, bij:
>* [ http://localhost:4502 /libs/cq/search/content/querydebug.html ](http://localhost:4502/libs/cq/search/content/querydebug.html)
>
>Zie bijvoorbeeld:
>
>* [ http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29 ](http://localhost:4502/system/console/services?filter=%28component.factory%3Dcom.day.cq.search.eval.PredicateEvaluator%2F*%29)

## Algemeen {#general}

* [basis](#root)
* [groep](#group)
* [ordonneren](#orderby)

## Voorspellen {#predicates}

* [boolproperty](/help/sites-developing/querybuilder-predicate-reference.md#boolproperty)
* [contentfragment](/help/sites-developing/querybuilder-predicate-reference.md#contentfragment)
* [dateComparison](/help/sites-developing/querybuilder-predicate-reference.md#datecomparison)
* [daterange](/help/sites-developing/querybuilder-predicate-reference.md#daterange)
* [exclusief paden](/help/sites-developing/querybuilder-predicate-reference.md#excludepaths)
* [fulltext](/help/sites-developing/querybuilder-predicate-reference.md#fulltext)
* [hasPermission](/help/sites-developing/querybuilder-predicate-reference.md#haspermission)
* [taal](/help/sites-developing/querybuilder-predicate-reference.md#language)
* [hoofdmiddel](/help/sites-developing/querybuilder-predicate-reference.md#mainasset)
* [lidOf](/help/sites-developing/querybuilder-predicate-reference.md#memberof)
* [nodenaam](/help/sites-developing/querybuilder-predicate-reference.md#nodename)
* [notexpired](/help/sites-developing/querybuilder-predicate-reference.md#notexpired)
* [pad](/help/sites-developing/querybuilder-predicate-reference.md#path)
* [eigenschap](/help/sites-developing/querybuilder-predicate-reference.md#property)
* [rangeproperty](/help/sites-developing/querybuilder-predicate-reference.md#rangeproperty)
* [relativedaterange](/help/sites-developing/querybuilder-predicate-reference.md#relativedaterange)
* [opgeslagen query](/help/sites-developing/querybuilder-predicate-reference.md#savedquery)
* [gelijkaardig](/help/sites-developing/querybuilder-predicate-reference.md#similar)
* [tag](/help/sites-developing/querybuilder-predicate-reference.md#tag)
* [gelabeld](/help/sites-developing/querybuilder-predicate-reference.md#tagid)
* [tagzoeken](/help/sites-developing/querybuilder-predicate-reference.md#tagsearch)
* [type](/help/sites-developing/querybuilder-predicate-reference.md#type)

### `boolproperty` {#boolproperty}

Komt overeen met de JCR BOOLEAN-eigenschappen. Accepteert alleen de waarden &quot; `true`&quot; en &quot; `false`&quot;. Indien ingesteld op &quot; `false`&quot;, komt deze overeen met de waarde &quot; `false`&quot; of als de eigenschap helemaal niet bestaat. Nuttig voor het controleren op booleaanse markeringen die alleen zijn ingesteld wanneer deze zijn ingeschakeld.

De overgeërfde parameter &quot; `operation`&quot; heeft geen betekenis.

Het ondersteunt facetextractie. Verstrekt emmers voor elke `true` of `false` waarde, maar slechts voor bestaande eigenschappen.

#### Eigenschappen {#properties}

* **boolproperty**
Relatief pad naar eigenschap, bijvoorbeeld `myFeatureEnabled` of `jcr:content/myFeatureEnabled` .

* **waarde**
Waarde waarvoor de eigenschap moet worden gecontroleerd: &quot; `true`&quot; of &quot; `false`&quot;.

### `contentfragment` {#contentfragment}

Hiermee beperkt u het resultaat tot inhoudsfragmenten.

Filteren wordt niet ondersteund.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-1}

* **contentfragment**
Deze kan met elke waarde worden gebruikt om te controleren op inhoudsfragmenten.

### `dateComparison` {#datecomparison}

Vergelijkt twee JCR DATE-eigenschappen met elkaar. U kunt testen of ze gelijk, ongelijk, groter dan of groter dan of gelijk zijn.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

#### Eigenschappen {#properties-2}

* **property1**

  Eigenschap pad naar eerste datum.

* **property2**

  Pad naar tweede-datumeigenschap.

* **verrichting**

  &quot; `equals`&quot; voor exacte overeenkomst, &quot; `!=`&quot; voor ongelijkheidsvergelijking, &quot; `greater`&quot; voor eigenschap1 groter dan eigenschap2, &quot; `>=`&quot; voor eigenschap1 groter dan of gelijk aan eigenschap2. De standaardwaarde is &quot; `equals`&quot;.

### `daterange` {#daterange}

Hiermee worden de JCR-DATE-eigenschappen vergeleken met een datum- en tijdinterval. Gebruikt ISO8601
notatie voor datums en tijden ( `YYYY-MM-DDTHH:mm:ss.SSSZ`) en staat ook gedeeltelijke representaties toe, zoals `YYYY-MM-DD` . U kunt de tijdstempel ook opgeven als het aantal milliseconden dat is verstreken sinds 1970 in de UTC-tijdzone, de UNIX®-tijdnotatie.

U kunt zoeken naar iets tussen twee tijdstempels, alles wat nieuwer of ouder is dan een bepaalde datum, en u kunt ook kiezen tussen inclusieve en open intervallen.

Het ondersteunt facetextractie. Verstrekt emmers &quot;vandaag,&quot;deze week,&quot;deze maand,&quot;laatste 3 maanden,&quot;dit jaar,&quot;vorig jaar&quot;en &quot;vroeger dan vorig jaar&quot;.

Filteren wordt niet ondersteund.

#### Eigenschappen {#properties-3}

* **bezit**

  Relatief pad naar een eigenschap `DATE` , bijvoorbeeld `jcr:lastModified` .

* **lowerBound**

  Lagere datum gebonden aan check eigenschap for, bijvoorbeeld `2014-10-01`.

* **lowerOperation**

  &quot; `>`&quot; (nieuwer) of &quot; `>=`&quot; (hoger of hoger) is van toepassing op de `lowerBound` . De standaardwaarde is &quot; `>`&quot;.

* **upperBound**

  Bovenaan gebonden om de eigenschap te controleren op, bijvoorbeeld, `2014-10-01T12:15:00` .

* **upperOperation**

  &quot; `<`&quot; (ouder) of &quot; `<=`&quot; (ouder of ouder), is van toepassing op `upperBound` . De standaardwaarde is &quot; `<`&quot;.

* **timeZone**

  Id van tijdzone die moet worden gebruikt wanneer deze niet wordt gegeven als een ISO-8601-datumtekenreeks. De standaardwaarde is de standaardtijdzone van het systeem.

### `excludepaths` {#excludepaths}

Hiermee sluit u knooppunten uit van het resultaat wanneer het pad ervan overeenkomt met een reguliere expressie.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-4}

* **exclusief wegen**

  Gewone expressie die overeenkomt met resultaatpaden, exclusief overeenkomende paden uit het resultaat.

### `fulltext` {#fulltext}

Zoekt naar termen in de fullText-index.

Filteren wordt niet ondersteund.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-5}

* **fulltext**

  De zoektermen in fulltext.

* **relPath**

  Het relatieve pad naar de eigenschap of het subknooppunt. Deze eigenschap is optioneel.

### `group` {#group}

Hiermee kunt u geneste voorwaarden maken. Groepen kunnen geneste groepen bevatten. Alles in een query builder-query bevindt zich impliciet in een hoofdgroep, die ook `p.or` - en `p.not` -parameters kan hebben.

Voorbeeld voor het afstemmen van een van de twee eigenschappen op een waarde:

```
group.p.or=true
group.1_property=jcr:title
group.1_property.value=My Page
group.2_property=navTitle
group.2_property.value=My Page
```

Conceptueel `(1_property` OF `2_property)` .

Voorbeeld voor geneste groepen:

```
fulltext=Management
group.p.or=true
group.1_group.path=/content/geometrixx/en
group.1_group.type=cq:Page
group.2_group.path=/content/dam/geometrixx
group.2_group.type=dam:Asset
```

Zoekt naar de termijn &quot;**Beheer**&quot;binnen pagina&#39;s in `/content/geometrixx/en` of in activa in `/content/dam/geometrixx`.

Conceptueel `fulltext AND ( (path AND type) OR (path AND type) )` . Zulke OF verbindingen hebben goede indexen voor prestaties nodig.

#### Eigenschappen {#properties-6}

* **p.or**

  Indien ingesteld op &quot; `true`&quot;, mag slechts één voorspelling in de groep overeenkomen. Heeft als standaardwaarde &quot; `false`&quot;, wat betekent dat alles moet overeenkomen

* **p.not**

  Indien ingesteld op &quot; `true`&quot;, wordt de groep genegeerd (standaard ingesteld op &quot; `false`&quot;).

* **&lt;preate>**

  Hiermee voegt u geneste voorvertoningen toe.

* **N_&lt;predicate>**

  Hiermee voegt u meerdere geneste voorspellen tegelijk toe, zoals `1_property, 2_property, ...` .

### hasPermission {#haspermission}

Beperkt het resultaat tot punten waar de huidige zitting de gespecificeerde [ voorrechten JCR heeft.](https://developer.adobe.com/experience-manager/reference-materials/spec/jcr/2.0/16_Access_Control_Management.html#16.2.3%20Standard%20Privileges)

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-7}

* **hasPermission**

  JCR-bevoegdheden die door komma&#39;s worden gescheiden en die ALLES voor de huidige gebruikerssessie moet hebben. Bijvoorbeeld `jcr:write` , `jcr:modifyAccessControl` .

### `language` {#language}

Hiermee zoekt u CQ-pagina&#39;s in een specifieke taal. Hierbij wordt zowel naar de eigenschap language van de pagina als naar het paginapad gekeken, dat vaak de taal of landinstelling in een site-structuur op hoofdniveau bevat.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt facetextractie. Verstrekt emmers voor elke unieke taalcode.

#### Eigenschappen {#properties-8}

* **taal**

  ISO taalcode, bijvoorbeeld, &quot;`de`&quot;.

### `mainasset` {#mainasset}

Controleert of een knooppunt een DAM-hoofdelement is en geen subelement. In principe is elk knooppunt niet binnen een knooppunt &quot;subassets&quot;. Hiermee wordt niet gecontroleerd op het knooppunttype `dam:Asset` . Als u deze voorspelling wilt gebruiken, stelt u &quot; `mainasset=true`&quot; of &quot; `mainasset=false`&quot; in en hebt u geen eigenschappen meer.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken.

Het ondersteunt facetextractie en biedt twee emmers voor hoofd- en subactiva.

#### Eigenschappen {#properties-9}

* **mainasset**

  Boolean, &quot; `true`&quot; voor hoofdelementen, &quot; `false`&quot; voor subelementen.

### lidOf {#memberof}

Vindt punten die lid van een specifieke [ sling middelinzameling ](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/resource/collection/ResourceCollection.html) zijn.

Een alleen-filteren-voorspelling en kan geen zoekindex gebruiken. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-10}

* **memberOf**

  Pad van Sling-bronverzameling.

### `nodename` {#nodename}

Komt overeen met namen van JCR-knooppunten.

Het ondersteunt facetextractie. Verstrekt emmers voor elke unieke knoopnaam (filename).

#### Eigenschappen {#properties-11}

* **nodename**

  Naamnotatiepatroon waarbij jokertekens zijn toegestaan: `*` = willekeurig of geen teken, `?` = willekeurig teken, `[abc]` = alleen tekens tussen haakjes.

### `notexpired` {#notexpired}

Komt overeen met items door te controleren of een JCR DATE-eigenschap groter of gelijk is aan de huidige servertijd. Kan worden gebruikt om een &quot; `expiresAt`&quot;-achtige datumeigenschap in te checken en alleen de eigenschappen die nog niet zijn verlopen ( `notexpired=true` ) of die al zijn verlopen ( `notexpired=false` ).

Filteren wordt niet ondersteund.

Het steunt facetextractie op de zelfde manier als daterange predikaat.

#### Eigenschappen {#properties-12}

* **notexpired**

  Boolean, &quot; `true`&quot; for not expired yet (date in the future or equal), &quot; `false`&quot; for expired (date in the past) (required).

* **bezit**

  Relatief pad naar de eigenschap `DATE` die moet worden gecontroleerd (vereist).

### `orderby` {#orderby}

Hiermee kunt u de resultaten sorteren. Als de volgorde door meerdere eigenschappen vereist is, moet deze voorspelling meerdere keren worden toegevoegd met behulp van het voorvoegsel number, zoals `1_orderby=first`, `2_oderby=second` .

#### Eigenschappen {#properties-13}

* **orderby**

  De JCR-eigenschapnaam die wordt aangeduid door een regelafstand @, bijvoorbeeld `@jcr:lastModified` of `@jcr:content/jcr:title` , of een andere voorspelling in de query, bijvoorbeeld `2_property` , waarop moet worden gesorteerd.

* **soort**

  Sorteer de richting &quot; `desc`&quot; voor aflopend of &quot; `asc`&quot; voor oplopend (standaard).

* **geval**

  Indien ingesteld op `ignore` , wordt het sorteren van hoofdletters en kleine letters ongevoelig, wat betekent dat &quot;a&quot; komt vóór &quot;B&quot;; als het sorteren leeg is of wordt weggelaten, is het sorteren hoofdlettergevoelig, wat betekent dat &quot;B&quot; komt vóór &quot;a&quot;

### `path` {#path}

Hiermee zoekt u in een bepaald pad.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-14}

* **weg**

  Padpatroon. Bij `exact=false` (standaardwaarde) komt de zoekopdracht overeen met de gehele substructuur onder het opgegeven pad. Deze substructuur komt overeen met `//*` in XPath, maar bevat niet het basispad zelf. Als `exact=true` , komt de zoekopdracht alleen overeen met het exacte pad, dat ook `*` -jokertekens kan bevatten. Als `self` is ingesteld, bevat de zoekopdracht het basisknooppunt en de volledige substructuur ervan.


* **nauwkeurig**

  Wanneer `exact` true (on) is, moet het exacte pad overeenkomen, maar het kan eenvoudige jokertekens ( `*` ) bevatten, die identieke namen, maar niet &quot; `/` &quot;. Wanneer het pad false (standaard) is, worden alle afstammingen opgenomen (optioneel).

* **vlak**

  Hiermee doorzoekt u alleen de directe onderliggende elementen (zoals &quot; `/*`&quot; in `xpath` toevoegen) (wordt alleen gebruikt als &#39; `exact`&#39; niet true is, optioneel).

* **zelf**

  Doorzoekt de substructuur maar neemt het basisknooppunt op dat als pad wordt opgegeven (geen jokertekens).

### `property` {#property}

Komt overeen met de JCR-eigenschappen en hun waarden.

Het ondersteunt facetextractie. Verstrekt emmers voor elke unieke bezitswaarde in de resultaten.

#### Eigenschappen {#properties-15}

* **bezit**

  Relatief pad naar eigenschap, bijvoorbeeld `jcr:title` .

* **waarde**

  Waarde waarop de eigenschap moet worden gecontroleerd; volgt het eigenschapstype JCR op tekenreeksconversies.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere waarden (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.3).

* **en**

  Ingesteld op true voor het combineren van meerdere waarden ( `N_value`) met AND (sinds 5.3).

* **verrichting**

  Gebruik `equals` voor een exacte overeenkomst (standaard) en `unequals` voor een ongelijkheidsvergelijking. Gebruik `like` om de optionele functie `jcr:like` XPath toe te passen. Gebruik `not` voor geen overeenkomst (bijvoorbeeld `not(@prop)` in XPath); in dit geval wordt de parameter `value` genegeerd. Gebruik `exists` om te controleren of een eigenschap bestaat: `true` (standaardwaarde) vereist de eigenschap en `false` is gelijk aan `not` .

* **diepte**

  Een aantal jokertekenniveaus waaronder de eigenschap en het relatieve pad kunnen bestaan. `property=size depth=2` controleert bijvoorbeeld het knooppunt en de grootte, het knooppunt/&amp;ast;/size en het knooppunt/&amp;ast;/&amp;ast;/size.

### `rangeproperty` {#rangeproperty}

Hiermee wordt een JCR-eigenschap vergeleken met een interval. Is van toepassing op eigenschappen met lineaire typen, zoals `LONG`, `DOUBLE` en `DECIMAL` . Zie voor `DATE` de daterange-voorspelling die geoptimaliseerde invoer voor de datumnotatie heeft.

U kunt een ondergrens en een bovengrens of slechts één van hen bepalen. De bewerking (bijvoorbeeld &quot;kleiner dan&quot; of &quot;kleiner of gelijk aan&quot;) kan ook afzonderlijk worden opgegeven voor de onderste en bovenste binding.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-16}

* **bezit**

  Relatief pad naar eigenschap.

* **lowerBound**

  Ondergrens om eigenschap te controleren voor.

* **lowerOperation**

  &quot; `>`&quot; (standaardwaarde) of &quot; `>=`&quot; is van toepassing op het `lowerValue`

* **upperBound**

  Bovengrens om de eigenschap te controleren op.

* **upperOperation**

  &quot; `<`&quot; (standaardwaarde) of &quot; `<=`&quot; is van toepassing op het `lowerValue`

* **decimaal**

  &quot; `true`&quot; als de gecontroleerde eigenschap van het type Decimaal is

### `relativedaterange` {#relativedaterange}

Vergelijkt `JCR DATE` -eigenschappen met een datum- en tijdinterval door tijdverschuivingen te gebruiken ten opzichte van de huidige servertijd. U kunt `lowerBound` en `upperBound` opgeven met een milliseconde-waarde of de bugzilla-syntaxis `1s 2m 3h 4d 5w 6M 7y` . Voorvoegsel met &quot; `-`&quot; om een negatieve verschuiving vóór de huidige tijd aan te geven. Als u alleen `lowerBound` of `upperBound` opgeeft, wordt de andere standaard ingesteld op 0, wat de huidige tijd betekent.

Bijvoorbeeld:

* `upperBound=1h` (en geen `lowerBound` ) selecteert de afbeelding in het volgende uur
* `lowerBound=-1d` (en geen `upperBound` ) selecteert niets in de afgelopen 24 uur
* `lowerBound=-6M` en `upperBound=-3M` selecteert elke 6 maanden tot 3 maanden oud
* `lowerBound=-1500` en `upperBound=5500` selecteert in het vervolg iets tussen 1500 milliseconden en 5500 milliseconden
* `lowerBound=1d` en `upperBound=2d` zouden overmorgen iets selecteren

Het neemt schrikkeljaren niet in overweging en alle maanden zijn 30 dagen.

Filteren wordt niet ondersteund.

Het steunt facetextractie op de zelfde manier als daterange predikaat.

#### Eigenschappen {#properties-17}

* **upperBound**

  Bovenste datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie.

* **lowerBound**

  Lagere datum gebonden in milliseconden of `1s 2m 3h 4d 5w 6M 7y` (één seconde, twee minuten, drie uren, vier dagen, vijf weken, zes maanden, zeven jaar) met betrekking tot huidige servertijd, gebruik &quot;-&quot;voor negatieve compensatie.

### `root` {#root}

Hoofdvoorspelbare groep. Het steunt alle eigenschappen van een groep en laat u globale vraagparameters plaatsen.

De naam &quot;wortel&quot;wordt nooit gebruikt in een vraag, het is impliciet.

#### Eigenschappen {#properties-18}

* **p.offset**

  Het getal dat het begin van de resultatenpagina aangeeft, dat wil zeggen het aantal items dat moet worden overgeslagen.

* **p.limit**

  Het getal dat het paginaformaat aangeeft.

* **p.radenTotal**

  Om de kosten te vermijden om een volledig resultaattotaal te berekenen, tel niet alle gelijken. Stel in plaats daarvan een maximumtotaal in om tot (bijvoorbeeld `1000` ) te tellen, zodat gebruikers een ruwe grootte en exacte totalen krijgen voor kleinere resultaten. Of stel het in op `true` om alleen tot het vereiste minimum te tellen: `p.offset + p.limit` .


* **p.excerpt**

  Indien ingesteld op &quot; `true`&quot;, neemt u het volledige tekstfragment op in het resultaat.

* **p.hits**

  (alleen voor de JSON-servlet) selecteer de manier waarop de treffers als JSON worden geschreven, met de volgende standaardresultaten (uitbreidbaar via de service ResultHitWriter):

   * **eenvoudig**:

     Minimale items zoals `path` , `title` , `lastmodified` en `excerpt` (indien ingesteld).

   * **volledig**:

     De resultaten worden weergegeven als Sling JSON voor elk knooppunt, waarbij `jcr:path` het raakpad weergeeft. Standaard bevat de reactie alleen de directe eigenschappen van het knooppunt; gebruik `p.nodedepth=N` om dieper liggende inhoud op te nemen, waarbij `0` de volledige substructuur retourneert. Stel `p.acls=true` in om de JCR-machtigingen van de huidige sessie voor elk item (`create` = `add_node` , `modify` = `set_property` , `delete` = `remove`) op te nemen.


   * **selectief**:

     De reactie bevat alleen de eigenschappen die worden vermeld in `p.properties` . Dit is een lijst met relatieve paden met spaties (gebruik `+` in URL&#39;s). Als een relatief pad een diepte groter dan 1 heeft, nest de uitvoer het als onderliggende objecten. De speciale eigenschap `jcr:path` bevat altijd het raakpad.


### `savedquery` {#savedquery}

Het omvat alle predikaten van een voortgezette vraag van de vraagbouwer in de huidige vraag als subgroup predikaat.

Er wordt geen extra query uitgevoerd, maar de huidige query wordt uitgebreid.

Query&#39;s kunnen met programmacode worden voortgezet met `QueryBuilder#storeQuery()` . De indeling kan een eigenschap van een tekenreeks met meerdere regels zijn of een knooppunt `nt:file` dat de query als een tekstbestand in de Java™-eigenschappenindeling bevat.

Het steunt facetextractie voor de predikaten van de bewaarde vraag niet.

#### Eigenschappen {#properties-19}

* **opgeslagen vraag**

  Pad naar de opgeslagen query (eigenschap String of knooppunt `nt:file` ).

### `similar` {#similar}

Gelijksoortige zoekopdracht met JCR XPath `rep:similar()`.

Filteren wordt niet ondersteund. Het ondersteunt geen facetextractie.

#### Eigenschappen {#properties-20}

* **gelijkaardig**
Absoluut pad naar het knooppunt waarvoor vergelijkbare knooppunten moeten worden gevonden.

* **lokaal**
Een relatief pad naar een afstammend knooppunt of `.` voor het huidige knooppunt (optioneel, standaard is &quot; `.`&quot;).

### `tag` {#tag}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags door titelpaden voor tags op te geven.

Het ondersteunt facetextractie. Verschaft emmers voor elke unieke tag, waarbij het huidige pad voor de tagtitel wordt gebruikt.

#### Eigenschappen {#properties-21}

* **markering**

  Titelpad van tag om bijvoorbeeld te zoeken naar &quot;Eigenschappen van element: oriëntatie / liggend&quot;.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere tags (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.6).

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) die moet worden bekeken (standaard &quot; `cq:tags`&quot;)

### `tagid` {#tagid}

Hiermee zoekt u naar inhoud die is gelabeld met een of meer tags, door tag-id&#39;s op te geven.

Het ondersteunt facetextractie. Verschaft emmers voor elke unieke tag met behulp van de huidige tag-id.

#### Eigenschappen {#properties-22}

* **tagid**

  Label id zodat u bijvoorbeeld naar &quot; `properties:orientation/landscape`&quot; kunt zoeken.

* **N_value**

  Gebruik `1_value`, `2_value` , ... om te controleren op meerdere `tagids` (standaard gecombineerd met `OR` , met `AND` if en=true) (sinds 5.6).

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard &quot; `cq:tags`&quot;).

### `tagsearch` {#tagsearch}

Zoekt naar inhoud gelabeld met een of meer tags door trefwoorden op te geven. Hiermee zoekt u eerst naar tags die deze trefwoorden in hun titels bevatten en beperkt u het resultaat vervolgens tot alleen getagde items.

Het ondersteunt geen facetextractie.

#### Eigenschappen {#Properties-1}

* **tagsearch**

  Trefwoord dat moet worden gezocht in tagtitels.

* **bezit**

  Eigenschap (of relatief pad naar eigenschap) om naar te kijken (standaard `cq:tags`).

* **lang**

  Als u alleen in een bepaalde gelokaliseerde tagtitel wilt zoeken (bijvoorbeeld `de` ).

* **allen**

  (bool) Zoek volledige labeltekst, dat wil zeggen alle titels, beschrijving enzovoort. Heeft voorrang op &quot;l `ang`&quot;.

### `type` {#type}

Beperkt resultaten tot een specifiek JCR knooptype, zowel primair knooptype als mixintype en vindt subtypes van dat knooptype. In de zoekindexen van de opslagplaats moeten de knooppunttypen worden opgenomen voor een efficiënte uitvoering.

Het ondersteunt facetextractie. Verstrekt emmers voor elk uniek type in de resultaten.

#### Eigenschappen {#Properties-2}

* **type**

  Node type of mixin naam aan onderzoek naar, bijvoorbeeld, `cq:Page`.
