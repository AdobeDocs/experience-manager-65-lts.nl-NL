---
title: Adobe-classificaties
description: Leer hoe u met Adobe Classifications classificaties classificatiegegevens exporteert naar Adobe Analytics.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: f564bda3-4141-40b3-8c08-140d4da92e2c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '612'
ht-degree: 0%

---

# Adobe-classificaties{#adobe-classifications}

De Classificaties van Adobe voeren classificatiegegevens naar [&#x200B; Adobe Analytics &#x200B;](/help/sites-administering/adobeanalytics.md) op een geplande manier uit. Exporter is een implementatie van a **com.adobe.cq.scheduled.exporter.Exporter**.

Om dit te vormen:

1. Gebruikend **Navigatie**, uitgezochte **Hulpmiddelen**, **de Diensten van de Wolk**, toen **de Diensten van de Wolk van de Oudere Oude**.
1. De rol aan **Adobe Analytics** en selecteert **toont Configuraties**.
1. Klik de **[+]** verbinding naast uw configuratie van Adobe Analytics.

1. In **creeer Kader** dialoog:

   * Specificeer a **Titel**.
   * Naar keuze kunt u de **Naam** specificeren, voor de knoop die de kaderdetails in de bewaarplaats opslaat.
   * Selecteer **Classificaties van Adobe Analytics**

   En klik **creeer**.

   ![&#x200B; creeer de dialoog van het Kader &#x200B;](assets/aa-25.png)

1. De **dialoog van de Montages van Classificaties** opent voor het uitgeven.

   ![&#x200B; de dialoog van de Montages van Classificaties &#x200B;](assets/aa-classifications-settings.png)

   Tot de eigenschappen behoren:

   | **Gebied** | **Beschrijving** |
   |---|---|
   | Ingeschakeld | Selecteer **ja** om de montages van de Classificaties van Adobe toe te laten. |
   | Overschrijven bij conflict | Selecteer **ja** om het even welke gegevensbotsingen te beschrijven. Door gebrek, wordt dit geplaatst aan **Nr**. |
   | Verwerkt verwijderen | Als de reeks aan **ja**, verwerkte knopen schrapt nadat zij worden uitgevoerd. Het gebrek is **Vals**. |
   | Taakbeschrijving exporteren | Voer een beschrijving in voor de classificatietaak van Adobe. |
   | E-mailbericht | Voer een e-mailadres in voor berichten over Adobe-classificaties. |
   | Rapportsuite | Voer de rapportsuite in waarop de importtaak moet worden uitgevoerd. |
   | Gegevensset | Voer de relatie-id van de gegevensset in om de importtaak uit te voeren waarvoor. |
   | Transformer | Selecteer een transformatorimplementatie in het keuzemenu. |
   | Data Source | Navigeer naar het pad voor de gegevenscontainer. |
   | Export Plan | Selecteer het schema voor het exporteren. De standaardwaarde is elke 30 minuten. |

1. Klik **O.K.** om uw montages te bewaren.

## Paginaformaat wijzigen {#modifying-page-size}

Records worden op pagina&#39;s verwerkt. Standaard worden met Adobe Classifications pagina&#39;s gemaakt met een paginaformaat van 1000.

Een pagina kan maximaal 25000 pagina&#39;s groot zijn, per definitie in Adobe-classificaties en kan worden gewijzigd vanaf de Felix-console. Tijdens het exporteren vergrendelt Adobe Classifications het bronknooppunt om gelijktijdige wijzigingen te voorkomen. Het knooppunt wordt ontgrendeld na exporteren, bij een fout of wanneer de sessie wordt gesloten.

Het paginaformaat wijzigen:

1. Navigeer aan de console OSGI in **https://&lt;host>:&lt;port>/system/console/configMgr** en selecteer **de Exporter van de Classificaties van Adobe AEM**.

   ![&#x200B; a-26 &#x200B;](assets/aa-26.png)

1. Werk de **Grootte van de Pagina van de Uitvoer** zoals vereist bij, dan klik **sparen**.

## SAINTDefaultTransformer {#saintdefaulttransformer}

>[!NOTE]
>
>Adobe Classifications werd voorheen SAINT Exporter genoemd.

Een exporteur kan een Transformer gebruiken om de exportgegevens om te zetten in een specifieke indeling. Voor Adobe Classifications is een subinterface `SAINTTransformer<String[]>` beschikbaar voor het implementeren van de Transformer-interface. Deze interface wordt gebruikt om het gegevenstype te beperken tot `String[]` dat door de SAINT API wordt gebruikt en om een markeringsinterface te hebben om dergelijke services voor selectie te zoeken.

In de standaardimplementatie SAINTDefaultTransformer, worden de kindmiddelen van de exporterbron behandeld als verslagen met bezitsnamen als sleutels en bezitswaarden als waarden. De **Zeer belangrijke** kolom wordt automatisch toegevoegd als eerste kolom - zijn waarde zal de knoopnaam zijn. Benoemde eigenschappen (die `:` bevatten) worden genegeerd.

*structuur van de Knoop:*

* id-classificatie `nt:unstructured`

   * 1 `nt:unstructured`

      * Product = Mijn productnaam (Koord)
      * Price = 120.90 (String)
      * Size = M (String)
      * Color = black (String)
      * Color^Code = 101 (String)

**Kopbal en Verslag van SAINT:**

| **Sleutel** | **Product** | **Prijs** | **Grootte** | **Kleur** | **kleur^Code** |
|---|---|---|---|---|---|
| 1 | Mijn productnaam | 120,90 | M | zwart | 101 |

Tot de eigenschappen behoren:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschappenpad</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>transformator</td>
   <td>Een klassenaam van een SAINTTransformer-implementatie</td>
  </tr>
  <tr>
   <td>email</td>
   <td>E-mailadres voor melding.</td>
  </tr>
  <tr>
   <td>reportsuites</td>
   <td>ID's van suite rapporteren waarin de importtaak moet worden uitgevoerd. </td>
  </tr>
  <tr>
   <td>gegevensset</td>
   <td>Dataset relatie-id om de importtaak uit te voeren voor. </td>
  </tr>
  <tr>
   <td>beschrijving</td>
   <td>Taakbeschrijving. <br /> </td>
  </tr>
  <tr>
   <td>overschrijven</td>
   <td>Markering om gegevensbotsingen te overschrijven. Het gebrek is <strong> vals </strong>.</td>
  </tr>
  <tr>
   <td>controleafdelingen</td>
   <td>Markering om te controleren of de rapportsuite compatibel is. Het gebrek is waar <strong> </strong>.</td>
  </tr>
  <tr>
   <td>gereduceerd</td>
   <td>Markering om de verwerkte knooppunten na het exporteren te verwijderen. Het gebrek is <strong> vals </strong>.</td>
  </tr>
 </tbody>
</table>

## Exporteren van Adobe-classificaties automatiseren {#automating-adobe-classifications-export}

U kunt uw eigen werkschema tot stand brengen, zodat om het even welke nieuwe invoer de werkschema lanceert om aangewezen, en correct gestructureerd, gegevens in **te creëren/var/export/** zodat het naar classificaties van Adobe kan worden uitgevoerd.
