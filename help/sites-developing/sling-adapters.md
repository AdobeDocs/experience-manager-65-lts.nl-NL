---
title: Sling Adapters gebruiken
description: Sling biedt een adapterpatroon aan om voorwerpen geschikt te vertalen die de Aanpasbare interface uitvoeren.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 7eae83bd-7982-4051-821f-b43f65c5af2b
source-git-commit: cf22b13e0f7c8e66b598f85aab81b022480e60bc
workflow-type: tm+mt
source-wordcount: '1338'
ht-degree: 0%

---

# Sling-adapters gebruiken{#using-sling-adapters}

[&#x200B; het Verschuiven &#x200B;](https://sling.apache.org) biedt een [&#x200B; patroon van de Adapter &#x200B;](https://sling.apache.org/documentation/the-sling-engine/adapters.html) aan om voorwerpen geschikt te vertalen die de [&#x200B; Aanpasbare &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) interface uitvoeren. Deze interface verstrekt een generische [&#x200B; adjustTo () &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/Adaptable.html#adaptTo%28java.lang.Class%29) methode die het voorwerp aan het klassentype vertaalt dat als argument wordt overgegaan.

Als u bijvoorbeeld een Resource-object naar het corresponderende Node-object wilt vertalen, kunt u gewoon het volgende doen:

```java
Node node = resource.adaptTo(Node.class);
```

## Gebruik hoofdletters {#use-cases}

Er zijn de volgende gebruiksgevallen:

* Hiermee krijgt u implementatiespecifieke objecten.

  Bijvoorbeeld, verleent een op JCR-Gebaseerde implementatie van de generische [`Resource` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/Resource.html) interface toegang tot onderliggende JCR [`Node` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html).

* Het maken van sneltoetsen voor objecten waarvoor interne contextobjecten moeten worden doorgegeven.

  Bijvoorbeeld, op JCR-Gebaseerd [`ResourceResolver` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/resource/ResourceResolver.html) houdt een verwijzing naar verzoek [`JCR Session` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html), die beurtelings voor vele voorwerpen nodig is die op die verzoekzitting, zoals [`PageManager` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html) of [`UserManager` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html) kunnen werken.

* Snelkoppeling naar services.

  Een zeldzaam geval - `sling.getService()` is ook eenvoudig.

### Retourwaarde Null {#null-return-value}

De waarde `adaptTo()` retourneert null.

De redenen variëren, waaronder:

* De implementatie ondersteunt het doeltype niet.
* Een adapterfabriek die dit geval afhandelt, is niet actief (bijvoorbeeld vanwege ontbrekende serviceverwijzingen)
* Een interne voorwaarde is mislukt.
* De service is niet beschikbaar.

Het is belangrijk dat u de null-case netjes afhandelt. Voor JPEG-renderingen kan het acceptabel zijn dat de JPEG-opname mislukt als deze resulteert in een leeg stuk inhoud.

### Caching {#caching}

Om de prestaties te verbeteren, kunnen implementaties het object dat door een `obj.adaptTo()` -aanroep is geretourneerd, in de cache plaatsen. Wanneer `obj` hetzelfde is, is het geretourneerde object hetzelfde.

Deze caching wordt uitgevoerd voor alle `AdapterFactory` gebaseerde gevallen.

Er is echter geen algemene regel: het object kan een nieuw of een bestaand object zijn. Dit betekent dat u niet op één van beide gedrag kunt vertrouwen. Daarom is het belangrijk, vooral binnen `AdapterFactory`, dat objecten in dit scenario opnieuw kunnen worden gebruikt.

### Hoe werkt het {#how-it-works}

U kunt `Adaptable.adaptTo()` op verschillende manieren implementeren:

* Door het object zelf; de methode zelf implementeren en aan bepaalde objecten toewijzen.
* Door een [`AdapterFactory` &#x200B;](https://sling.apache.org/apidocs/sling5/org/apache/sling/api/adapter/AdapterFactory.html), die willekeurige voorwerpen in kaart kan brengen.

  De objecten moeten nog steeds de `Adaptable` interface implementeren en moeten [`SlingAdaptable` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/adapter/SlingAdaptable.html) uitbreiden (die de `adaptTo` aanroep aan een centrale adaptermanager doorgeeft).

  Wordt gekoppeld aan het mechanisme `adaptTo` voor bestaande klassen, zoals `Resource` .

* Een combinatie van beide.

In het eerste geval kunnen de Java™-documenten aangeven wat `adaptTo-targets` mogelijk is. Voor specifieke subklassen zoals de JCR-gebaseerde bron is het echter vaak niet mogelijk. In het laatste geval maken implementaties van `AdapterFactory` doorgaans deel uit van de klassen van het type private van een bundel en worden deze dus niet weergegeven in een client-API of in Java™-documenten. Theoretisch, zou het mogelijk zijn om tot alle `AdapterFactory` implementaties van [&#x200B; OSGi &#x200B;](/help/sites-deploying/configuring-osgi.md) de dienstruntime toegang te hebben en hun &quot;adaptables&quot;(bronnen en doelstellingen) configuraties te bekijken, maar niet om hen aan elkaar in kaart te brengen. Uiteindelijk hangt het af van de interne logica, die moet worden gedocumenteerd. Vandaar de verwijzing.

## Referentie {#reference}

### Sling {#sling}

[**Middel** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron of een JCR-eigenschap is die naar een knooppunt verwijst</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Property.html">Eigenschap</a></td>
   <td>Als het een op JCR-eigenschap gebaseerde resource is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Item.html">Item</a></td>
   <td>Als het een op JCR gebaseerde bron (knooppunt of eigenschap) is</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Map.html">Kaart</a></td>
   <td>Het keert een kaart van de eigenschappen terug, als het een JCR-knoop-gebaseerd middel (of andere middel ondersteunend waardekaarten) is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html">ValueMap</a></td>
   <td>Het keert een geschikt-aan-gebruiks kaart van de eigenschappen terug, als het een JCR-knoop-gebaseerd middel of andere middel ondersteunend waardekaarten is. Deze kan ook (eenvoudigere) worden bereikt door <br /> <code><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceUtil.html">ResourceUtil.getValueMap(Resource)</a></code> (behandelt null-hoofdletters, enzovoort) te gebruiken.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/inherit/InheritanceValueMap.html">InheritanceValueMap</a></td>
   <td>Uitbreiding van <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html"> ValueMap </a> die de hiërarchie van middelen toestaat om worden in aanmerking genomen wanneer het zoeken naar eigenschappen.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ModifiableValueMap.html">ModisibleValueMap</a></td>
   <td>Een uitbreiding van <a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ValueMap.html"> ValueMap </a>, die u eigenschappen op die knoop laat wijzigen.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/InputStream.html">InputStream</a></td>
   <td>Het keert de binaire inhoud van een dossiermiddel terug wanneer het op knoop-gebaseerde JCR (<code>nt:file</code> of <code>nt:resource</code>), een bundelmiddel, of een middel van het dossiersysteem is. Het keert de gegevens van een binair JCR bezitsmiddel terug.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/net/URL.html">URL</a></td>
   <td>Er wordt een URL voor de bron geretourneerd. De URL van de gegevensopslagruimte wordt geretourneerd voor een JCR-bron op knooppunten, de JAR-bundel voor een bundelbron of de bestand-URL voor een bestandssysteembron.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/io/File.html">Bestand</a></td>
   <td>Als het een bestandssysteembron is</td>
  </tr>
  <tr>
   <td><a href="https://sling.apache.org/apidocs/sling5/org/apache/sling/api/scripting/SlingScript.html">SlingScript</a></td>
   <td>Als deze bron een script is (bijvoorbeeld jsp-bestand) waarvoor een scriptengine is geregistreerd met sling.</td>
  </tr>
  <tr>
   <td><a href="https://www.oracle.com/java/technologies/servlet-technology.html">Servlet</a></td>
   <td>Als deze bron een script is (bijvoorbeeld jsp-bestand) waarvoor een scriptengine is geregistreerd met sling of als het een servletbron is.</td>
  </tr>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html"> Koord </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html"> Van Boole </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html"> Lang </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Double.html"> tweemaal </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Kalender </a><br /> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html"> Waarde </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/String.html"> Koord [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Boolean.html"> Van Boole [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/lang/Long.html"> Lang [] </a><br /> <a href="https://docs.oracle.com/javase/1.5.0/docs/api/java/util/Calendar.html"> Kalender [] </a><br /> 9&rbrace; <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Value.html"> Waarde [] </a></td>
   <td>Retourneert de waarden als het een JCR-eigenschap-gebaseerde resource (en de value-fit) is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html">Pagina</a></td>
   <td>Als het een op JCR-knooppunten gebaseerde bron is en het knooppunt een <code>cq:Page</code> (of <code>cq:PseudoPage</code> ) is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html">Component</a></td>
   <td>Als het een knooppuntbron <code>cq:Component</code> is</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Design.html">Ontwerp</a></td>
   <td>Als het een ontwerpknoop (<code>cq:Page</code>) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html">Sjabloon</a></td>
   <td>Als het een knooppuntbron <code>cq:Template</code> is</td>
  </tr>  
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/msm/api/Blueprint.html">Blauwdruk</a></td>
   <td>Als het een knooppuntbron <code>cq:Template</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Asset.html">Element</a></td>
   <td>Als het een knooppuntbron <code>dam:Asset</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/Rendition.html">Vertoning</a></td>
   <td>Als het een <code>dam:Asset</code> rendition (<code>nt:file</code> onder de renditiemap van a <code>dam:Asset</code>) is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/Tag.html">Tag</a></td>
   <td>Als het een knooppuntbron <code>cq:Tag</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/security/UserManager.html">UserManager</a></td>
   <td>Gebaseerd op de zitting JCR als het een op JCR-Gebaseerde middel is en de gebruiker toestemmingen heeft om tot UserManager toegang te hebben.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html">Toestemming</a></td>
   <td>Autorisable is de gemeenschappelijke basisinterface voor Gebruiker en Groep.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html">Gebruiker</a></td>
   <td>De gebruiker is een speciale Authorizable die voor authentiek en kan worden verklaard.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/SimpleSearch.html">SimpleSearch</a></td>
   <td>Zoekt onder de bron (of gebruik setSearchIn()) als het een op JCR gebaseerde bron is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/workflow/status/WorkflowStatus.html">WorkflowStatus</a></td>
   <td>Workflowstatus voor het opgegeven payload-knooppunt voor de pagina/workflow.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html">ReplicationStatus</a></td>
   <td>Replicatiestatus voor de opgegeven bron of het bijbehorende <code>jcr:content</code> subknooppunt (eerst gecontroleerd).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/connector/ConnectorResource.html">ConnectorResource</a></td>
   <td>Het keert een aangepast schakelaarmiddel voor bepaalde types terug, als het een JCR-knoop-gebaseerd middel is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">Config</a></td>
   <td>Als het een knooppuntbron <code>cq:ContentSyncConfig</code> is</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/contentsync/config/package-summary.html">ConfigEntry</a></td>
   <td>Als deze zich onder een node <code>cq:ContentSyncConfig</code> -resource bevindt</td>
  </tr>
 </tbody>
</table>

[**ResourceResolver** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/ResourceResolver.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Session.html">Sessie</a></td>
   <td>De JCR-sessie van het verzoek, als dit een op JCR gebaseerde resourceoplosser is (standaardwaarde).</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html">PageManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/ComponentManager.html">ComponentManager</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/designer/Designer.html">Designer</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/dam/api/AssetManager.html">AssetManager</a></td>
   <td>Gebaseerd op de zitting JCR, als het een op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/tagging/TagManager.html">TagManager</a></td>
   <td>Gebaseerd op de zitting JCR, als het een op JCR-Gebaseerde middeloplosser is.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/UserManager.html">UserManager</a></td>
   <td>De UserManager verleent toegang tot en middelen om toegelaten voorwerpen te handhaven die gebruikers en groepen zijn. De UserManager is gebonden aan een bepaalde Zitting.
   </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/Authorizable.html"> Toegelaten </a> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/jackrabbit/api/security/user/User.html"> Gebruiker </a><br /> </td>
   <td>De huidige gebruiker.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/search/QueryBuilder.html">QueryBuilder</a></td>
   <td> </td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/Externalizer.html">ExternalAlizer</a></td>
   <td>Voor het externaliseren van absolute URLs, zelfs zonder het verzoekvoorwerp.<br /> </td>
  </tr>
 </tbody>
</table>

[**SlingHttpServletRequest** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletRequest.html) past aan:

Geen doelstellingen nog, maar voert Aangepast uit en kon als bron in een douane AdapterFactory worden gebruikt.

[**SlingHttpServletResponse** &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/SlingHttpServletResponse.html) past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://docs.oracle.com/javase/1.5.0/docs/api/org/xml/sax/ContentHandler.html"> ContentHandler </a><br /> (XML)</td>
   <td>Als het een slingerrewriter-reactie is</td>
  </tr>
 </tbody>
</table>

#### WCM {#wcm}

**[&#x200B; pagina &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Page.html)** past zich aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html"> Middel </a><br /> </td>
   <td>Bron van de pagina.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron is de huidige bron. Dat is hetzelfde object dat u bekijkt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van de pagina.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de pagina kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

**de [&#x200B; component &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/components/Component.html)** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de component. |
| --- | --- |
| [&#x200B; LabeledResource &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html) | Gelabelde bron is de huidige bron. Dat is hetzelfde object dat u bekijkt. |
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de component. |
| ... | Alles waaraan de bron van de component kan worden aangepast. |

**het [&#x200B; malplaatje &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/Template.html)** past aan:

<table>
 <tbody>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html"> Middel </a> <a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html"><br /> </a></td>
   <td>Bron van de sjabloon.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/commons/LabeledResource.html">LabeledResource</a></td>
   <td>Gelabelde bron is de huidige bron. Dat is hetzelfde object dat u bekijkt.</td>
  </tr>
  <tr>
   <td><a href="https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html">Knooppunt</a></td>
   <td>Knooppunt van deze sjabloon.</td>
  </tr>
  <tr>
   <td>...</td>
   <td>Alles waaraan de bron van de sjabloon kan worden aangepast.</td>
  </tr>
 </tbody>
</table>

#### Beveiliging {#security}

**Toegelaten**, **Gebruiker, en &#x200B;** Groep** past aan:

| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Retourneert het thuisknooppunt van de gebruiker/groep. |
| --- | --- |
| [&#x200B; ReplicationStatus &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/replication/ReplicationStatus.html) | Het keert de replicatiestatus voor de gebruiker/groepshuisknoop terug. |

#### DAM {#dam}

**Activa** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Middelen van het actief. |
| --- | --- |
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Node of the asset. |
| ... | Alles waaraan de middelen van het actief kunnen worden aangepast. |

#### Tag {#tagging}

**markering** past aan:

| [&#x200B; Middel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/org/apache/sling/api/resource/Resource.html) | Bron van de tag. |
| --- | --- |
| [&#x200B; Knoop &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/spec/javax.jcr/javadocs/jcr-2.0/javax/jcr/Node.html) | Knooppunt van de tag. |
| ... | Alles waaraan de bron van de tag kan worden aangepast. |

#### Overige {#other}

Voorts verstrekt het Verdelen / JCR / OCM ook een ` [AdapterFactory](https://sling.apache.org/site/adapters.html#Adapters-AdapterFactory)` voor douaneOCM ([&#x200B; de Inhoud van Objecten Toewijzing &#x200B;](https://jackrabbit.apache.org/jcr/object-content-mapping.html)) voorwerpen.
