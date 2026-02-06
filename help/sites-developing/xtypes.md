---
title: xtypes gebruiken (klassieke UI)
description: Meer informatie over alle xtypes die beschikbaar zijn in Adobe Experience Manager
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: components
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4a78de53-33bf-4999-ba3c-7d0bc33196a4
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '3668'
ht-degree: 0%

---

# xtypes gebruiken (klassieke UI){#using-xtypes-classic-ui}

Deze pagina beschrijft alle xtypes die bij Adobe Experience Manager (AEM) beschikbaar zijn.

In de taal ExtJS, is xtype een symbolische naam die aan een klasse wordt gegeven. U kunt de &quot;Component XTypes&quot;paragraaf van het [&#x200B; Overzicht van ExtJS 2 &#x200B;](https://docs.sencha.com/) voor een gedetailleerde verklaring lezen over wat een xtype is en hoe het kan worden gebruikt.

Voor meer informatie over alle beschikbare widgets in AEM, zie de [&#x200B; widget API documentatie &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Als u wilt weten in welke componenten een bepaald xtype wordt gebruikt in AEM, gebruikt u de volgende `Xpath` -query in CRXDE. Vervang gewoon &#39;checkbox&#39; door het xtype waarin u geïnteresseerd bent:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Deze pagina beschrijft het gebruik van ExtJS xtypes binnen klassieke UI.
>
>Adobe adviseert dat u standaard, modern, [&#x200B; aanraking-toegelaten UI &#x200B;](/help/sites-developing/touch-ui-concepts.md) gebruikt die op [&#x200B; Koraal UI &#x200B;](/help/sites-developing/touch-ui-concepts.md#coral-ui) en [&#x200B; wordt gebaseerd graniet UI &#x200B;](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Hieronder ziet u de beschikbare xtypes in Adobe Experience Manager:

* `annotation`

  [&#x200B; CQ.wcm.Annotation &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Annotation` is een speciaal venster. Het heeft een vorm in zijn lichaam en een knoopgroep in zijn footer. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* `arraystore`

  [&#x200B; CQ.Ext.data.ArrayStore &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Vroeger bekend als `SimpleStore` .

  Een kleine helperklasse om het creëren van [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van de gegevens van de Serie gemakkelijker te maken. Een `ArrayStore` wordt automatisch gevormd met a [&#x200B; CQ.Ext.data.ArrayReader &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `asseteditor`

  [&#x200B; CQ.dam.AssetEditor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Asset Editor` wordt gebruikt in DAM Admin.

* `assetreferencesearchdialog`

  [&#x200B; CQ.wcm.AssetReferenceSearchDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `AssetReferenceSearchDialog` is een dialoogvenster dat wordt weergegeven voor het geval dat een pagina naar elementen of tags verwijst.

* `blueprintconfig`

  [&#x200B; CQ.wcm.msm.BlueprintConfig &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In `BlueprintConfig` vindt u een deelvenster voor het weergeven van de actieve kopieën van een blauwdruk en het bewerken van deze eigenschappen voor het afdrukken van blauwdrukken (activering synchroniseren en acties synchroniseren).

* `blueprintstatus`

  [&#x200B; CQ.wcm.msm.BlueprintStatus &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De BluprintStatus biedt een deelvenster voor het weergeven en bewerken van een blauwdruk en de bijbehorende relaties voor actieve kopieën. Het doorbladeren wordt gedaan door a [&#x200B; CQ.wcm.msm.BlueprintStatus.Tree &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), uitgave door a [&#x200B; CQ.wcm.msm.BlueprintConfig &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en a [&#x200B; CQ.wcm.msm.LiveCopyProperties &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [&#x200B; CQ.Ext.BoxComponent &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De klasse van de basis voor om het even welke [&#x200B; Component &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die als doos moet worden gerangschikt, gebruikend breedte en hoogte.

  BoxComponent biedt automatische aanpassingen van het kadermodel voor grootte en positionering en werkt correct binnen het rendermodel van de Component.

* `browsedialog`

  [&#x200B; CQ.BrowseDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met het dialoogvenster BrowseDialog kan de gebruiker door de opslagplaats bladeren om een pad te selecteren. Het wordt typisch gebruikt door a [&#x200B; BrowseField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `browsefield`

  [&#x200B; CQ.form.BrowseField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [&#x200B; CQ.form.PathField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan**

* `bulkeditor`

  [&#x200B; CQ.wcm.BulkEditor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `BulkEditor` verstrekt een onderzoeksmotor en een net om onderzoeksresultaten uit te geven.

  De `BulkEditor` moet in een HTML-formulier worden ingevoegd (vereist voor importfunctionaliteit). Dit werkt perfect met a [&#x200B; CQ.Dialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [&#x200B; CQ.wcm.BulkEditorForm &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BulkEditorForm verstrekt [&#x200B; CQ.wcm.BulkEditor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) omringd door een vorm van HTML. De standalone versie van [&#x200B; CQ.wcm.BulkEditor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Een HTML-formulier is vereist voor de importknop.

* `button`

  [&#x200B; CQ.ext.Button &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Simple Button, klasse

* `buttongroup`

  [&#x200B; CQ.Ext.ButtonGroup &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Container voor een groep knoppen.

* `chart`

  [&#x200B; CQ.Ext.chart.Chart &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het pakket CQ.Ext.chart biedt de mogelijkheid om gegevens te visualiseren met flash-gebaseerde grafieken. Elke grafiek bindt direct aan een CQ.Ext.data.Store toelatend automatische updates van de grafiek. Om de blik en het gevoel van een grafiek te veranderen, zie [&#x200B; chartStyle &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [&#x200B; extraStyle &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config opties.

* `checkbox`

  [&#x200B; CQ.Ext.form.Checkbox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld voor één selectievakje. Kan worden gebruikt als directe vervanging voor traditionele selectievakjes.

* `checkboxgroup`

  [&#x200B; CQ.Ext.form.CheckboxGroup &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een groeperende container voor [&#x200B; CQ.Ext.form.Checkbox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controles.

* `clearcombo`

  [&#x200B; CQ.form.ClearableComboBox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De ClearableComboBox is een niet-bewerkbare keuzelijst met invoervak met een trigger om de waarde ervan te wissen.

* `colorfield`

  [&#x200B; CQ.form.ColorField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het ColorField laat de gebruiker een waarde van de kleurenhexuitdraai of het gebruiken van a [&#x200B; CQ.Ext.ColorMenu &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ingaan.

* `colorlist`

  [&#x200B; CQ.form.ColorList &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de ColorList kan de gebruiker een kleur kiezen in een bewerkbare lijst.

* `colormenu`

  [&#x200B; CQ.Ext.menu.ColorMenu &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menu dat a [&#x200B; CQ.Ext.ColorPalette &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Component bevat.

* `colorpalette`

  [&#x200B; CQ.Ext.ColorPalette &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eenvoudige kleurenpaletklasse voor het kiezen van kleuren. Het palet kan worden gerenderd naar elke gewenste container.

* `combo`

  [&#x200B; CQ.Ext.form.ComboBox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een combobox-besturingselement met ondersteuning voor automatisch aanvullen, extern laden, pagineren en vele andere functies.

  Een ComboBox werkt op een vergelijkbare manier als een traditioneel HTML &lt;select>-veld. Het verschil is dat om [&#x200B; valueField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor te leggen, moet u a [&#x200B; hiddenName &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) specificeren om een verborgen input tot stand te brengen.

* `component`

  [&#x200B; CQ.ext.Component &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor alle `Ext` -componenten. Alle subklassen van Component kunnen aan de geautomatiseerde `Ext` componentenlevenscyclus van verwezenlijking, het teruggeven, en vernietiging deelnemen die door de [&#x200B; 2&rbrace; klasse van de Container &lbrace;wordt verstrekt. &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) De componenten kunnen aan een Container door de [&#x200B; punten &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) worden toegevoegd config optie op het tijdstip dat de Container wordt gecreeerd.

* `componentextractor`

  [&#x200B; CQ.wcm.ComponentExtractor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met ComponentExtractor kan de gebruiker componenten van een website/pagina extraheren.

* `componentselector`

  [&#x200B; CQ.form.ComponentSelector &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gegroepeerde, geordende selectie van beschikbare componenten.

* `componentstyles`

  [&#x200B; CQ.form.ComponentStyles &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [&#x200B; CQ.form.CompositeField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor op deelvensters gebaseerde, complexe formuliervelden die één formulierveld of een groep formuliervelden bevatten.

* `container`

  [&#x200B; CQ.Ext.Container &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De klasse van de basis voor om het even welk [&#x200B; CQ.Ext.BoxComponent &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die andere Componenten kan bevatten. Containers verwerken het basisgedrag van het bevatten van items, namelijk items toevoegen, invoegen en verwijderen.

  De meest algemeen gebruikte klassen van de Container zijn [&#x200B; CQ.Ext.Panel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [&#x200B; CQ.Ext.Window &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), en [&#x200B; CQ.Ext.TabPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [&#x200B; CQ.wcm.ContentFinder &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinder is een gespecialiseerde twee-kolom [&#x200B; Viewport &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die de daadwerkelijke Vinder van de Inhoud op de linkerzijde en het Kader van de Inhoud op het recht bevat.

* `contentfindertab`

  [&#x200B; CQ.wcm.ContentFinderTab &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab is een gespecialiseerd paneel dat eigenschappen verstrekt die in de lusjepanelen van [&#x200B; worden gebruikt CQ.wcm.ContentFinder &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Doorgaans bevat het een zoekformulier - het vak Query - en een gegevensweergave om de zoekopdracht weer te geven.

* `cq.workflow.model.combo`

  [&#x200B; CQ.wcm.WorkflowModelCombo &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelCombo is een aangepaste [&#x200B; CQ.Ext.form.ComboBox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die een lijst van beschikbare werkschemamodellen toont.

* `cq.workflow.model.selector`

  [&#x200B; CQ.wcm.WorkflowModelSelector &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De WorkflowModelSelector combineert een WorkflowModelCombo met een duimnagelbeeld van het werkschema, en knopen om werkschemamodellen tot stand te brengen en uit te geven.

* `createsitewizard`

  [&#x200B; CQ.wcm.CreateSiteWizard &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De CreateSiteWizard is een geleidelijke tovenaar om (MSM) plaatsen tot stand te brengen.

* `createversiondialog`

  [&#x200B; CQ.wcm.CreateVersionDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster CreateVersionDialog is een dialoogvenster waarin een versie van een pagina kan worden gemaakt.

* `customcontentpanel`

  [&#x200B; CQ.CustomContentPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CustomContentPanel is een speciaal paneel voor gebruik in [&#x200B; CQ.Dialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html): Zijn inhoud wordt teruggewonnen van en voorgelegd aan een verschillende URL dan de andere gebieden in de dialoogdoos.

* `cycle`

  [&#x200B; CQ.Ext.CycleButton &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde SplitButton die een menu van [&#x200B; CQ.Ext.menu.CheckItem &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) elementen bevat. De knoop cycli automatisch door elk menupunt op elke klik, die de 1&rbrace; gebeurtenis van de verandering van de knoop [&#x200B; opheffen &lbrace;of die de &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) changeHandler [&#x200B; functie van de knoop roepen, als verstrekt) voor het actieve menupunt.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `dataview`

  [&#x200B; CQ.Ext.DataView &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een mechanisme voor het weergeven van gegevens met behulp van aangepaste lay-outsjablonen en opmaak. DataView gebruikt een [&#x200B; CQ.Ext.XTemplate &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) als zijn intern het malplaatjemechanisme, en gebonden aan [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zodat aangezien de gegevens in de opslag veranderen de mening automatisch wordt bijgewerkt om op de veranderingen te wijzen.

* `datefield`

  [&#x200B; CQ.Ext.form.DateField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het verstrekt een gebied van de datuminput van a [&#x200B; CQ.Ext.DatePicker &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) drop-down en automatische datumbevestiging.

* `datemenu`

  [&#x200B; CQ.Ext.menu.DateMenu &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menu dat een {[&#x200B; Component 0} CQ.Ext.DatePicker bevat.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `datepicker`

  [&#x200B; CQ.Ext.DatePicker &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een pop-updatumkiezer. Deze klasse wordt gebruikt door de [&#x200B; &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) klasse DateField om het doorbladeren en de selectie van geldige data toe te staan.

* `datetime`

  [&#x200B; CQ.form.DateTime &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DateTime laat de gebruiker een datum en een tijd ingaan door [&#x200B; CQ.Ext.form.DateField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [&#x200B; CQ.Ext.form.TimeField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te combineren.

* `dialog`

  [&#x200B; CQ.Dialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster is een speciaal venster. Het heeft een vorm in zijn lichaam en een knoopgroep in zijn footer. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* `dialogfieldset`

  [&#x200B; CQ.form.DialogFieldSet &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DialogFieldSet is a [&#x200B; FieldSet &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor gebruik in [&#x200B; Dialogi &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [&#x200B; CQ.Ext.data.DirectStore &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om tot een [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te leiden die met [&#x200B; CQ.Ext.data.DirectProxy &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [&#x200B; CQ.Ext.data.JsonReader &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) wordt gevormd om interactie met een [&#x200B; CQ.Ext.Direct &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Server-kant [&#x200B; gemakkelijker te maken Leverancier &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `displayfield`

  [&#x200B; CQ.Ext.form.DisplayField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een alleen-weergeven tekstveld dat niet is gevalideerd en niet is verzonden.

* `editbar`

  [&#x200B; CQ.wcm.EditBar &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De EditBar laat de gebruiker inhoud uitgeven gebruikend knopen op een bar.

  Hoewel hier niet vermeld, heeft EditBar alle leden van [&#x200B; CQ.wcm.EditBase &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [&#x200B; CQ.ext.Editor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een veld voor een basiseditor dat het weergeven/verbergen op aanvraag afhandelt en beschikt over ingebouwde logica voor grootte en gebeurtenisafhandeling.

* `editorgrid`

  [&#x200B; CQ.Ext.grid.EditorGridPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse breidt de [&#x200B; Klasse GridPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) uit om cel het uitgeven op geselecteerde [&#x200B; kolommen &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te verstrekken. De editable kolommen worden gespecificeerd door een [&#x200B; redacteur &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in de [&#x200B; kolomconfiguratie &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te verstrekken.

* `editrollover`

  [&#x200B; CQ.wcm.EditRollover &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de EditRollover kan de gebruiker inhoud bewerken door te dubbelklikken en worden meer bewerkhandelingen uitgevoerd via een contextmenu. Het bewerkbare gebied wordt aangegeven met een kader wanneer de muis over de inhoud beweegt.

* `feedimporter`

  [&#x200B; CQ.wcm.FeedImporter &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FeedImporter kan de gebruiker RSS- of Atom-feeds importeren en pagina&#39;s maken voor elke feed-invoer.

* `field`

  [&#x200B; CQ.Ext.form.Field &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor formuliervelden met standaardfuncties voor gebeurtenisafhandeling, -grootte, -afhandeling en andere functies.

* `fieldset`

  [&#x200B; CQ.Ext.form.FieldSet &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De standaard container die voor het groeperen van punten binnen a [&#x200B; wordt gebruikt vorm &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [&#x200B; CQ.form.FileUploadDialogButton &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FileUploadDialogButton wordt een knop gemaakt waarmee een nieuw dialoogvenster wordt geopend voor het uploaden van een bestand via FileUploadField. Kan worden gebruikt in bewerkingsdialoogvensters waar het uploaden in een afzonderlijk formulier moet plaatsvinden.

* `fileuploadfield`

  [&#x200B; CQ.form.FileUploadField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FileUploadField kan de gebruiker één bestand selecteren dat moet worden geüpload.

* `findreplacedialog`

  [&#x200B; CQ.wcm.FindReplaceDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De FindReplaceDialog is een dialoogdoos voor het vinden en het vervangen van tekenen in een pagina en zijn kindpagina&#39;s.

* `flash`

  [&#x200B; CQ.Ext.FlashComponent &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [&#x200B; CQ.Ext.grid.GridPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse vertegenwoordigt de primaire interface van een op component-gebaseerd netcontrole om gegevens in een tabelvorm formaat van rijen en kolommen te vertegenwoordigen.

* `groupingstore`

  [&#x200B; CQ.Ext.data.GroupingStore &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde opslagimplementatie die het groeperen van verslagen door één van de beschikbare gebieden voorziet. Gebruikt met [&#x200B; CQ.Ext.grid.GroupingView &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om het gegevensmodel voor een gegroepeerde GridPanel te bewijzen.

* `heavymovedialog`

  [&#x200B; CQ.wcm.HeavyMoveDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster HeavyMoveDialog is een dialoogvenster voor het verplaatsen van een pagina en de onderliggende pagina&#39;s, waarin ook wordt overwogen eerder geactiveerde pagina&#39;s opnieuw in te schakelen (&#39;zware&#39; verplaatsing).

* `hidden`

  [&#x200B; CQ.Ext.form.Hidden &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een verborgen basisveld voor het opslaan van verborgen waarden in formulieren die moeten worden doorgegeven aan het verzenden van het formulier.

* `historybutton`

  [&#x200B; CQ.HistoryButton &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HistoryButton is een kleine hulpklasse om rug en voorwaartse knopen gemakkelijk te verstrekken. Meestal zijn twee verwante instanties vereist: de voorwaartse knopinstantie is een eenvoudige knop die is gekoppeld aan de achtergrondknopinstantie die de geschiedenis afhandelt.

* `htmleditor`

  [&#x200B; CQ.Ext.form.HtmlEditor &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze biedt een lichtgewicht component van HTML Editor. Safari biedt geen ondersteuning voor bepaalde werkbalkfuncties, zodat deze automatisch door het systeem worden verborgen wanneer dat nodig is. Wordt in voorkomend geval vermeld in de configuratieopties.

  De de toolbarknopen van de redacteur hebben tooltips die in het [&#x200B; worden bepaald buttonTips &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bezit.

* `iframedialog`

  [&#x200B; CQ.IframeDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een dialoogvenster zonder opmaak waarin de inhoud van een iframe wordt weergegeven en waarin formulieren in iframes kunnen worden geplaatst.

* `iframepanel`

  [&#x200B; CQ.IframePanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een deelvenster met een iframe. Het biedt eenvoudige verwezenlijking van iframes, een iframe ladingsgebeurtenis, en gemakkelijke toegang tot de inhoud van iframe.

* `inlinetextfield`

  [&#x200B; CQ.form.InlineTextField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  InlineField is een tekstveld dat als label wordt weergegeven wanneer de focus niet is gericht.

* `jsonstore`

  [&#x200B; CQ.Ext.data.JsonStore &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om het creëren van [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van gegevens te maken JSON gemakkelijker. Een JsonStore wordt automatisch gevormd met a [&#x200B; CQ.Ext.data.JsonReader &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `label`

  [&#x200B; CQ.Ext.form.Label &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld Standaardlabel.

* `languagecopydialog`

  [&#x200B; CQ.wcm.LanguageCopyDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De LanguageCopyDialog is een dialoogvenster voor het kopiëren van taalbomen.

* `linkchecker`

  [&#x200B; CQ.wcm.LinkChecker &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De LinkChecker is een hulpmiddel om externe verbindingen in een plaats te controleren.

* `listview`

  [&#x200B; CQ.Ext.list.ListView &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView is een snelle en licht-gewichtimplementatie van a [&#x200B; Net-als &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) mening.

* `livecopyproperties`

  [&#x200B; CQ.wcm.msm.LiveCopyProperties &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LiveCopyProperties biedt een deelvenster voor het weergeven en bewerken van de eigenschappen van Live Copy (relatieovererving, synchronisatietrigger en synchronisatiehandelingen).

* `lvbooleancolumn`

  [&#x200B; CQ.Ext.list.BooleanColumn &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kolomdefinitieklasse die Booleaanse gegevensvelden rendert. Zie [&#x200B; xtype &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [&#x200B; CQ.Ext.list.Column &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `lvcolumn`

  [&#x200B; CQ.Ext.list.Column &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse kapselt kolomconfiguratiegegevens in die in initialisatie van a [&#x200B; moeten worden gebruikt ListView &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvdatecolumn`

  [&#x200B; CQ.Ext.list.DateColumn &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een de definitieklasse van de Kolom die een overgegaan datum volgens de standaardscène, of a gevormde [&#x200B; formaat &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) teruggeeft. Zie [&#x200B; xtype &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [&#x200B; CQ.Ext.list.Column &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `lvnumbercolumn`

  [&#x200B; CQ.Ext.list.NumberColumn &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een de definitieklasse van de Kolom die een numeriek gegevensgebied volgens a [&#x200B; formaat &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) koord teruggeeft. Zie [&#x200B; xtype &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [&#x200B; CQ.Ext.list.Column &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `mediabrowsedialog`

  [&#x200B; CQ.MediaBrowseDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [&#x200B; de Vinder van de Inhoud &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om media in plaats daarvan te doorbladeren.**

  De MediaBrowseDialog is een dialoogdoos voor het doorbladeren van de media bibliotheek.

* `menu`

  [&#x200B; CQ.Ext.menu.Menu &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menuobject. De container waaraan u menu-items kunt toevoegen. Het menu kan ook als basisklasse dienen wanneer u een gespecialiseerd die menu van een andere component (als [&#x200B; CQ.Ext.menu.DateMenu &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bijvoorbeeld) wordt gebaseerd.

  De menu&#39;s kunnen of [&#x200B; menupunten &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), of algemene [&#x200B; Component &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) s bevatten.

* `menubaseitem`

  [&#x200B; CQ.Ext.menu.BaseItem &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De basisklasse voor alle items die in menu&#39;s worden gerenderd. BaseItem verstrekt gebrek die, geactiveerd staatsbeheer, en de opties van de basisconfiguratie teruggeeft door alle menucomponenten worden gedeeld.

* `menucheckitem`

  [&#x200B; CQ.Ext.menu.CheckItem &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Hiermee wordt een menu-item toegevoegd dat standaard een selectievakje bevat, maar dat ook deel kan uitmaken van een groep keuzerondjes.

* `menuitem`

  [&#x200B; CQ.Ext.menu.Item &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een basisklasse voor alle menu-items die menu-gerelateerde functionaliteit vereisen (zoals submenu&#39;s) en die geen statische weergave-items zijn. Het punt breidt de basisfunctionaliteit van [&#x200B; CQ.Ext.menu.BaseItem &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) door menu-specifieke activering toe te voegen en behandeling te klikken uit.

* `menuseparator`

  [&#x200B; CQ.Ext.menu.Separator &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een scheidingsbalk toegevoegd aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Over het algemeen, voegt u één het toe door &quot;-&quot;in uw vraag te gebruiken om toe te voegen () of in uw punten config eerder dan direct tot stand te brengen.

* `menutextitem`

  [&#x200B; CQ.Ext.menu.TextItem &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een statische tekenreeks toegevoegd aan een menu dat wordt gebruikt als een kop- of groepsscheidingsteken.

* `metadata`

  [&#x200B; CQ.dam.form.Metadata &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Metadata` biedt een set velden waarmee de informatie wordt bepaald die nodig is voor een metagegevensveld, zoals bijvoorbeeld wordt gebruikt op pagina&#39;s in de Editor van middelen.

  Deze biedt de volgende velden:

* `multifield`

  [&#x200B; CQ.form.MultiField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `MultiField` is een bewerkbare lijst met formuliervelden voor het bewerken van eigenschappen met meerdere waarden.

* `mvt`

  [&#x200B; CQ.form.MVT &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de Multivariate Testing-component kunt u een set afbeeldingen definiëren en bewerken die als wisselende banners worden weergegeven. Klik door tariefstatistieken worden verzameld per banner.

* `notificationinbox`

  [&#x200B; CQ.wcm.NotificationInbox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `NotificationInbox` kan de gebruiker zich abonneren op WCM-handelingen en meldingen beheren.

* `numberfield`

  [&#x200B; CQ.Ext.form.NumberField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Numeriek tekstveld dat automatische toetsaanslag en numerieke validatie biedt.

* `offlineimporter`

  [&#x200B; CQ.wcm.OfflineImporter &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `OfflineImporter` is een programma voor het importeren en converteren van Microsoft® Word-documenten naar AEM-pagina&#39;s. Met deze functie kan inhoud offline worden bewerkt met een tekstverwerker.

* `ownerdraw`

  [&#x200B; CQ.form.OwnerDraw &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `OwnerDraw` kan aangepaste HTML-code bevatten (die rechtstreeks wordt ingevoerd of wordt opgehaald via een URL).

* `paging`

  [&#x200B; CQ.Ext.PagingToolbar &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Naarmate het aantal records toeneemt, neemt de tijd die de browser nodig heeft om deze weer te geven toe. Met paginering wordt de hoeveelheid gegevens die met de klant wordt uitgewisseld, verminderd.

* `panel`

  [&#x200B; CQ.ext.Panel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een `panel` is een container die specifieke functionaliteit en structurele componenten heeft die van het de perfecte bouwsteen voor toepassing-georiënteerde gebruikersinterfaces maken.

  De panelen, door hun overerving, zijn van [&#x200B; CQ.Ext.Container &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [&#x200B; CQ.form.ParagraphReference &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In het veld Alineasereferentie kunt u door pagina&#39;s bladeren en een van de alinea&#39;s selecteren. Het bestaat uit een triggerveld en een gekoppeld alineascherm.

* `password`

  [&#x200B; CQ.form.Password &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Password` is als a [&#x200B; CQ.Ext.form.TextField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) maar houdt zijn waarde privé, toestaand gebruikers om gevoelige gegevens in te gaan.

* `pathcompletion`

  [&#x200B; CQ.form.PathCompletion &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [&#x200B; CQ.form.PathField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan**

* `pathfield`

  [&#x200B; CQ.form.PathField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `PathField` is een inputgebied dat voor wegen met wegvoltooiing en een knoop wordt ontworpen om a [&#x200B; CQ.BrowseDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te openen voor het doorbladeren van de serverbewaarplaats. U kunt ook door alinea&#39;s bladeren om geavanceerde koppelingen te genereren.

* `progress`

  [&#x200B; CQ.Ext.ProgressBar &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een bij te werken voortgangsbalkcomponent. De voortgangsbalk ondersteunt twee verschillende modi: handmatig en automatisch.

  Op handwijze, bent u verantwoordelijk voor het tonen, het bijwerken (via [&#x200B; updateProgress &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) en het ontruimen van de vooruitgangsbar zoals nodig van uw eigen code. Deze methode is vooral geschikt wanneer u de voortgang wilt weergeven.

* `propertygrid`

  [&#x200B; CQ.Ext.grid.PropertyGrid &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde netimplementatie bedoeld om het traditionele bezitsnet zoals typisch gezien in ontwikkeling IDEs na te bootsen. Elke rij in het net vertegenwoordigt een bezit van één of ander voorwerp, en het gegeven wordt opgeslagen als reeks naam/waardeparen in [&#x200B; CQ.Ext.grid.PropertyRecord.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `propgrid`

  [&#x200B; CQ.PropertyGrid &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `PropertyGrid` is een algemeen raster dat wordt gebruikt voor het weergeven en bewerken van eigenschappen van objecten.

* `quicktip`

  [&#x200B; CQ.Ext.QuickTip &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` - een gespecialiseerde tooltip klasse voor tooltips die in prijsverhoging kunnen worden gespecificeerd en automatisch door de globale {[&#x200B; instantie 1} CQ.Ext.QuickTips worden geleid. &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Zie de QuickTips-klasseheader voor meer gebruiksdetails en voorbeelden.

* `radio`

  [&#x200B; CQ.Ext.form.Radio &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld Single `radio` . Hetzelfde als Selectievakje, maar als handig hulpmiddel om het invoertype automatisch in te stellen. De browser groepeert automatisch keuzerondjes wanneer elk keuzerondje in de groep dezelfde naam gebruikt.


* `radiogroup`

  [&#x200B; CQ.Ext.form.RadioGroup &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een groeperingscontainer voor [&#x200B; CQ.Ext.form.Radio &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controles.

* `referencesdialog`

  [&#x200B; CQ.wcm.ReferencesDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `ReferencesDialog` is een dialoogvenster waarin verwijzingen op een pagina worden weergegeven.

* `restoretreedialog`

  [&#x200B; CQ.wcm.RestoreTreeDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RestoreTreeDialog` is een dialoogvenster voor het herstellen van een vorige versie van een boomstructuur.

* `restoreversiondialog`

  [&#x200B; CQ.wcm.RestoreVersionDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De RestoreVersionDialog is een dialoogdoos voor het herstellen van een vorige versie van een pagina.

* `richtext`

  [&#x200B; CQ.form.RichText &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RichText` biedt een formulierveld voor het bewerken van opgemaakte tekstgegevens (RTF-gegevens).

  De component `RichText` biedt momenteel de volgende functies:

* `rolloutplan`

  [&#x200B; CQ.wcm.msm.RolloutPlan &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het rolloutPlan verstrekt een dialoogdoos om de vooruitgang van de paginalopulatie te bekijken. A [&#x200B; CQ.wcm.msm.RolloutWizard &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) begint rolloutPlan.

* `rolloutwizard`

  [&#x200B; CQ.wcm.msm.RolloutWizard &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RolloutWizard` verstrekt een tovenaar voor het opstellen van een pagina. RolloutWizard begint a [&#x200B; CQ.wcm.msm.RolloutPlan &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [&#x200B; CQ.form.SearchField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `SearchField` biedt een zoekveld dat de resultaten bevat in een vervolgkeuzelijst die kan worden gebruikt voor het zoeken in de opslagplaats.

* `selection`

  [&#x200B; CQ.form.Selection &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `Selection` kan de gebruiker kiezen uit verschillende opties. De opties kunnen onderdeel zijn van de configuratie of worden geladen vanuit een JSON-reactie. De selectie kan worden weergegeven als een vervolgkeuzelijst (selecteren) of als een keuzelijst met invoervak (selecteren plus tekst-item zonder opmaak).

* `sidekick`

  [&#x200B; CQ.wcm.Sidekick &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Sidekick` is een zwevende hulplijn waarmee de gebruiker algemene gereedschappen voor het bewerken van pagina&#39;s krijgt.

* `siteadmin`

  [&#x200B; CQ.wcm.SiteAdmin &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `SiteAdmin` is een console die WCM beleidsfuncties verstrekt.

* `siteimporter`

  [&#x200B; CQ.wcm.SiteImporter &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `SiteImporter` kan de gebruiker volledige websites importeren en eerste projecten maken.

* `sizefield`

  [&#x200B; CQ.form.SizeField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `SizeField` kan de gebruiker de breedte en hoogte invoeren (bijvoorbeeld voor een afbeelding).

* `slider`

  [&#x200B; CQ.Ext.Slider &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Schuifregelaar die ondersteuning biedt voor verticale of horizontale oriëntatie, toetsenbordaanpassingen, configureerbare magnetisch uitlijnen, asklikken en animatie. Het kan als punt aan om het even welke container worden toegevoegd. Bijvoorbeeld gebruik: ...

* `slideshow`

  [&#x200B; CQ.form.Slideshow &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de component Presentatie kunt u een set afbeeldingen en afbeeldingstitels definiëren en bewerken. Gebruikers kunnen de set als een presentatie weergeven.

  De component Slideshow is gebaseerd op de {[&#x200B; component 0} CQ.form.SmartImage.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `smartfile`

  [&#x200B; CQ.form.SmartFile &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het SmartFile-bestand is een intelligente uploader voor bestanden.

  Als een Flash-insteekmodule (versie >= 9) is geïnstalleerd, worden uploads uitgevoerd met behulp van de SWF-uploadbibliotheek die een handige manier biedt om uploads af te handelen.

* `smartimage`

  [&#x200B; CQ.form.SmartImage &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De SmartImage is een intelligente uploader voor afbeeldingen. Het biedt gereedschappen voor het verwerken van een geüploade afbeelding, bijvoorbeeld een gereedschap voor het definiëren van afbeeldingen met hyperlinks en een functie voor het uitsnijden van afbeeldingen.

  De component is ontworpen voor gebruik in een afzonderlijk tabblad in het dialoogvenster.

* `spacer`

  [&#x200B; CQ.ext.Spacer &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Wordt gebruikt om een grote ruimte in een lay-out te bieden.

* `spinner`

  [&#x200B; CQ.form.Spinner &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Spinner` is een triggerveld voor numerieke, datum- of tijdwaarden. De waarde kan worden verhoogd en verlaagd met de beschikbare triggers omhoog en omlaag, het schuifwiel of toetsen.

* `splitbutton`

  [&#x200B; CQ.Ext.SplitButton &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A `splitbutton` dat een ingebouwde drop-down pijl verstrekt die een gebeurtenis los van de standaard klikgebeurtenis van de knoop kan in brand steken. Doorgaans wordt het gebruikt om een vervolgkeuzemenu weer te geven dat aanvullende opties biedt voor de primaire knopactie, maar elke aangepaste handler kan de `arrowclick` -implementatie verschaffen.

* `static`

  [&#x200B; CQ.Static &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Static` kan worden gebruikt om willekeurige tekst of HTML weer te geven.

* `statistics`

  [&#x200B; CQ.wcm.Statistics &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In `Statistics` worden de paginamonpressies als een diagram weergegeven. Met de widget kunt u een periode selecteren waarvoor de statistieken moeten worden weergegeven.

* `store`

  [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `Store` klasse kapselt een cliënt-zijgeheime voorgeheugen van [&#x200B; Verslag &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voorwerpen in die inputgegevens voor Componenten zoals [&#x200B; GridPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [&#x200B; ComboBox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), of [&#x200B; DataView &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verstrekken.

* `suggestfield`

  [&#x200B; CQ.form.SuggestField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `SuggestField` biedt de gebruiker suggesties op basis van hun invoer.

* `switcher`

  [&#x200B; CQ.Switcher &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Switcher` verstrekt een knoopgroep voor de kopbalbar in een console om tussen Websites, Digitale Assets, Hulpmiddelen, Workflow, en Veiligheid te schakelen.

* `tableedit`

  [&#x200B; CQ.form.TableEdit &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [&#x200B; CQ.form.TableEdit2 &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan.**

* `tableedit2`

  [&#x200B; CQ.form.TableEdit2 &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `TableEdit2` biedt een widget voor het maken van tabellen.

* `tabpanel`

  [&#x200B; CQ.Ext.TabPanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een eenvoudige tabcontainer. TabPanels kunnen precies als standaard [&#x200B; CQ.Ext.Panel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor lay-outdoeleinden worden gebruikt, maar hebben ook speciale steun voor het bevatten van kindComponenten ([`items` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [&#x200B; CQ.tagging.TagInputField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

  is een formulierwidget voor het invoeren van codes. Het bevat een pop-upmenu voor het selecteren van bestaande tags, inclusief automatisch aanvullen en veel andere functies.

* `textarea`

  [&#x200B; CQ.Ext.form.TextArea &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Tekstveld met meerdere regels. Kan worden gebruikt als directe vervanging voor traditionele `textarea` -velden, plus ondersteuning voor automatisch aanpassen van grootte.

* `textbutton`

  [&#x200B; CQ.TextButton &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `TextButton` verstrekt een tekstverbinding met de mogelijkheden van a [&#x200B; CQ.Ext.Button &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [&#x200B; CQ.Ext.form.TextField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basistekstveld. Kan als directe vervanging voor traditionele tekstinput worden gebruikt, of als basisklasse voor verfijnde inputcontroles (als [&#x200B; CQ.Ext.form.TextArea &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [&#x200B; CQ.Ext.form.ComboBox &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `thumbnail`

  [&#x200B; CQ.form.Thumbnail &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [&#x200B; CQ.Ext.form.TimeField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het verstrekt een gebied van de tijdinput met tijd drop-down en automatische tijdbevestiging. Voorbeeld: ...

* `tip`

  [&#x200B; CQ.ext.Tip &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype uiteinde Dit is de basisklasse voor [&#x200B; CQ.Ext.QuickTip &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [&#x200B; CQ.Ext.Tooltip &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die de basislay-out en het plaatsen verstrekt die alle op uiteinde-gebaseerde klassen vereisen. Deze klasse kan direct voor eenvoudige, statisch gepositioneerde uiteinden worden gebruikt.

* `titleseparator`

  [&#x200B; CQ.menu.TitleSeparator &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een scheidingsbalk toegevoegd aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Het scheidingsteken kan ook een titel bevatten.

* `toolbar`

  [&#x200B; CQ.ext.Toolbar &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basic `Toolbar` -klasse. Hoewel [`defaultType` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor Toolbar [`button` &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) is, kunnen de elementen van de Toolbar (kindpunten voor de Toolbar container) vrijwel om het even welk type van Component zijn. Werkbalkelementen kunnen expliciet worden gemaakt via hun constructors.

* `tooltip`

  [&#x200B; CQ.Ext.ToolTip &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een standaardimplementatie `tooltip` voor het verstrekken van extra informatie wanneer het hangen over een doelelement. @xtype tooltip.

* `treegrid`

  [&#x200B; CQ.tree.TreeGrid &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [&#x200B; CQ.Ext.tree.TreePanel &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `TreePanel` verstrekt boom-gestructureerde vertegenwoordiging UI van boom-gestructureerde gegevens.

  [&#x200B; TreeNode &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) wordt toegevoegd aan `TreePanel` kan meta-gegevens bevatten die door uw toepassing in hun [&#x200B; worden gebruikt attributen &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bezit.

* `trigger`

  [&#x200B; CQ.Ext.form.TriggerField &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Dit is een handige omslag voor `TextFields` waarmee een klikbare triggerknop wordt toegevoegd (die standaard lijkt op een keuzelijst met invoervak). De trekker heeft geen standaardactie, zodat moet u een functie toewijzen om de trekker uit te voeren klikt manager door [&#x200B; onTriggerClick &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) met voeten te treden. U kunt een `TriggerField` rechtstreeks maken, aangezien het net als een combobox wordt weergegeven.

* `uploaddialog`

  [&#x200B; CQ.UploadDialog &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `UploadDialog` kan de gebruiker bestanden uploaden naar de opslagplaats. Hiermee wordt een nieuwe UploadDialog gemaakt.

* `userinfo`

  [&#x200B; CQ.UserInfo &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Werkbalkitem om de huidige gebruikersnaam weer te geven en gebruikersacties zoals het bewerken van gebruikerseigenschappen en imitatie toe te staan.

* `viewport`

  [&#x200B; CQ.Ext.Viewport &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde container die het zichtbare toepassingsgebied vertegenwoordigt (viewport van browser).

  De `Viewport` geeft zichzelf aan de documenttekst weer en past zichzelf automatisch aan de grootte van de viewport van de browser aan en beheert de grootte van het venster. Er kan slechts één Viewport zijn gemaakt.

* `window`

  [&#x200B; CQ.ext.Window &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een speciaal deelvenster dat is bedoeld voor gebruik als toepassingsvenster. De vensters worden gedreven, [&#x200B; resizable &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), en [&#x200B; draggable &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) door gebrek. De vensters kunnen [&#x200B; worden gemaximaliseerd &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om viewport te vullen, aan hun vroegere grootte wordt hersteld, en kunnen [&#x200B; worden geminimaliseerd &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) d.

* `xmlstore`

  [&#x200B; CQ.Ext.data.XmlStore &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om het creëren van [&#x200B; CQ.Ext.data.Store &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van de gegevens van XML gemakkelijker te maken. Een `XmlStore` wordt automatisch gevormd met a [&#x200B; CQ.Ext.data.XmlReader &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

  `cqinclude` - Een pseudo-xtype dat widgetdefinities bevat van een ander pad in de repository. Deze wordt meestal gebruikt in paginadialoogvensters. Er is geen werkelijke JavaScript-widget-klasse voor dit xtype. De `CQ.Util` -klasse verwerkt deze met behulp van de `formatData()` -functie.
