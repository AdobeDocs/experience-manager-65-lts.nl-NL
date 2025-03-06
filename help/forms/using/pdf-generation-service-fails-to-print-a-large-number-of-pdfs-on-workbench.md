---
title: PDF Generation kan geen groot aantal PDF's afdrukken met WorkBench
description: Wanneer een klant een groot aantal PDF's genereert via services die zijn geïmplementeerd via WorkBench, mislukt de afdrukservice.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
role: User, Developer
exl-id: 80a4e5c0-d68f-4591-a43d-ab75b5f0764c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '775'
ht-degree: 0%

---

# PDF Generation kan een groot aantal PDF&#39;s niet afdrukken via WorkBench {#PDF-generation-fails-to-print-a-large-number-of-PDFs-via-WorkBench}

## Probleem {#issue}

Wanneer een klant een groot aantal PDF&#39;s genereert via services die via WorkBench zijn geïmplementeerd. De service mislukt als gevolg van onvoldoende geheugen. De fout wordt weergegeven als:

`ALC-OUT-002-013: XMLFormFactory, PAexecute failure: "0: Out of Memory"`

<!-- Attached is a simplified template (BollatoRiservatiLandscape_table_simple.xdp) that simulates the problem.
Using the Designer, if we associate the template "BollatoRiservatiLandscape_table_semplice.xdp" with the XML file "BollatoRiservati.xml" during the generation of the pdf, the process comes to occupy 1.6 Gb of RAM. On the server side, with the complete template, the pdf generation process breaks down, occupying 2 GB of RAM.-->

Dit komt doordat het maximumaantal pagina&#39;s in een afdrukverzoek is beperkt tot ongeveer 1000 pagina&#39;s in Windows. Wanneer een drukoutput wordt geproduceerd, moeten het malplaatje en de gegevens in geheugen worden geladen en de resulterende lay-out wordt opgebouwd in geheugen. Dit betekent dat er grenzen zijn aan de grootte van de einduitvoer. Het proces dat de afdrukuitvoer genereert, is een 32-bits taak, wat betekent dat deze beperkt is tot 2 GB RAM in Windows <!--and 4 GB on UNIX--> .

## Van toepassing op {#applies-to}

De oplossing is van toepassing op AEM Forms <!--JEE Server and AEM Forms on OSGi Server--> for x86_win32 XMLFM.

## Oplossing {#solution}

De grootste factor die het geheugengebruik beïnvloedt, is de hoeveelheid gegevens op een formulier. Er zijn echter andere factoren in een formulierontwerp die het geheugengebruik in mindere mate beïnvloeden. Wanneer u zich van deze factoren bewust bent, kunt u een formulier ontwerpen voor grotere drukuitvoer. In de volgende sectie worden in volgorde met prioriteit factoren aangegeven die de geheugenvoetafdruk beïnvloeden:

### Botsfactor {#impact-factor}

**Hoog**

1. **Subforms van de Keuze** - een gekozen subformulierreeks is een variatie van het voorwerp van de subformulierreeks die u toestaat om de vertoning van specifieke subformulieren van binnen de reeks aan te passen door voorwaardelijke verklaringen te gebruiken.
1. **Statische tekst van het Gebruik in plaats van titels** - bijna elk gebied verstrekt een titel binnen, zou de gebruiker dat in plaats van het hebben van een extra statische tekst als titel moeten gebruiken.
1. Het formaat van de tekst van het gebruik **Rich (RTF)** waar mogelijk.

**Gemiddelde**

Bij het ontwerpen van formuliersjablonen moet u rekening houden met extra factoren om het geheugengebruik te verbeteren:

1. Gebruik geen statische tekst om een veld een label te geven. Gebruik in plaats daarvan bijschriften in het tekstveld.
2. Gebruik geen rechthoeken, lijnen, objecten en tabellen.
3. Gebruik indien mogelijk geen RichText en Choice Subforms.
4. Gebruik niet te veel subformulieren en geneste subformulieren.

### Beperking gegevensgrootte {#data-size-limitations}

Omdat het maximale procesgeheugen ons beperkt en het geheugen dat door het proces wordt verbruikt, is niet alleen afhankelijk van de grootte van het gegevensbestand. Het is nauw verbonden met het formulierontwerp en tot op zekere hoogte met de hoeveelheid gegevens die daadwerkelijk in het formulier worden samengevoegd.

Als het formulier veel kleine knooppunten met kleine gegevens bevat, verbruikt het proces meer geheugen (en gaat het dus sneller uit het geheugen) dan een formulier met minder knooppunten (zelfs) met grote gegevens.

Lees het [ Bijlage hieronder ](#appendix) voor meer informatie, waar de testresultaten op de vorm van de Druk (niet-Gelabelde PDF) worden gebaseerd. Door het gebruik van gelabelde PDF-procesgeheugenvereisten neemt de geheugenbehoefte toe. Het hangt ook af van het aantal velden in het formulier. ruwweg de vereiste voor het procesgeheugen zou iets meer dan 1,5 keer groter zijn dan die van niet-gecodeerde PDF.

### Interactieve Forms {#interactive-forms}

Interactieve formulieren verbruiken meer geheugen dan Print Forms omdat interactieve velden opnieuw worden weergegeven. In de uitgevoerde tests nam het geheugengebruik ongeveer toe met een factor 1,5 ten opzichte van de gedrukte formulieren en dit waren statische interactieve formulieren.

### Afbeeldingsindelingen {#image-formats}

Adobe raadt geen specifieke afbeeldingsindeling aan. Het zou echter mooi zijn als de afbeelding kleiner zou zijn, bijvoorbeeld PNG (Portable Network Graphics). Het is ook niet aan te raden afbeeldingen met een hoge resolutie te gebruiken waarvan de grootte honderden MegaBytes kan variëren. Het is ook niet aan te raden gecomprimeerde afbeeldingen te gebruiken waarvan de grootte bij decompressie tot honderden megabytes aan gegevens wordt uitgebreid.

### Bijlage {#appendix}

**Voorbeelden van de Lijst**

Hieronder ziet u verschillende varianten voor tabellen die het renderaantal pagina&#39;s versus de gegevensgrootte voor eenvoudige tabel en complexe tabel weergeven.

1. Een tabel met één kolom waarin 5000 pagina&#39;s PDF&#39;s worden gegenereerd, gegevensbestanden met een bestandsgrootte van 24 MB en 30 kB.

   ![ table_single_column ](/help/forms/using/assets/table_single_column.png)

1. Een tabel met veel kleine kolommen waarin 800 pagina&#39;s PDF&#39;s worden gegenereerd, de grootte van het gegevensbestand is 4,6 MB en 20 kB records.
   ![ table_many_small_columns ](/help/forms/using/assets/table_many_small_columns.png)

1. Een tabel met veel kleine kolommen, maar een groter gegevensbestand vanwege het gebruik van grotere namen voor xmlTag.
Hier is alles gelijk aan de vorige, maar namen van XML-tags zijn groot gemaakt (zodat het gegevensbestand groter wordt zonder dat de effectieve gegevens toenemen), is het eindresultaat (bovengrens) bijna hetzelfde. De grootte van het gegevensbestand is echter toegenomen van 4,6 MB tot 44,6 MB. Hier worden 800 pagina&#39;s PDF&#39;s gegenereerd. De bestandsgrootte van het gegevensbestand is 44,6 MB en 20 kB.

   ![ table_greater_xml_tagname ](/help/forms/using/assets/table_bigger_xml_tagname.png)

Het is dus moeilijk om een algemene bovengrens op de grootte van het gegevensbestand te zetten. Elk formulier is uniek en daarom verschilt het geheugengebruik per formulier.
