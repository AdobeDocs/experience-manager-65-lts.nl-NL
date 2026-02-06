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

In de taal ExtJS, is xtype een symbolische naam die aan een klasse wordt gegeven. U kunt de &quot;Component XTypes&quot;paragraaf van het [ Overzicht van ExtJS 2 ](https://docs.sencha.com/) voor een gedetailleerde verklaring lezen over wat een xtype is en hoe het kan worden gebruikt.

Voor meer informatie over alle beschikbare widgets in AEM, zie de [ widget API documentatie ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

Als u wilt weten in welke componenten een bepaald xtype wordt gebruikt in AEM, gebruikt u de volgende `Xpath` -query in CRXDE. Vervang gewoon &#39;checkbox&#39; door het xtype waarin u geïnteresseerd bent:

`//element(*, cq:Widget)[@xtype='checkbox']`

>[!NOTE]
>
>Deze pagina beschrijft het gebruik van ExtJS xtypes binnen klassieke UI.
>
>Adobe adviseert dat u standaard, modern, [ aanraking-toegelaten UI ](/help/sites-developing/touch-ui-concepts.md) gebruikt die op [ Koraal UI ](/help/sites-developing/touch-ui-concepts.md#coral-ui) en [ wordt gebaseerd graniet UI ](/help/sites-developing/touch-ui-concepts.md#granite-ui-foundation-components).

## xtypes {#xtypes}

Hieronder ziet u de beschikbare xtypes in Adobe Experience Manager:

* `annotation`

  [ CQ.wcm.Annotation ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Annotation` is een speciaal venster. Het heeft een vorm in zijn lichaam en een knoopgroep in zijn footer. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* `arraystore`

  [ CQ.Ext.data.ArrayStore ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Vroeger bekend als `SimpleStore` .

  Een kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van de gegevens van de Serie gemakkelijker te maken. Een `ArrayStore` wordt automatisch gevormd met a [ CQ.Ext.data.ArrayReader ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `asseteditor`

  [ CQ.dam.AssetEditor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Asset Editor` wordt gebruikt in DAM Admin.

* `assetreferencesearchdialog`

  [ CQ.wcm.AssetReferenceSearchDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `AssetReferenceSearchDialog` is een dialoogvenster dat wordt weergegeven voor het geval dat een pagina naar elementen of tags verwijst.

* `blueprintconfig`

  [ CQ.wcm.msm.BlueprintConfig ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In `BlueprintConfig` vindt u een deelvenster voor het weergeven van de actieve kopieën van een blauwdruk en het bewerken van deze eigenschappen voor het afdrukken van blauwdrukken (activering synchroniseren en acties synchroniseren).

* `blueprintstatus`

  [ CQ.wcm.msm.BlueprintStatus ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De BluprintStatus biedt een deelvenster voor het weergeven en bewerken van een blauwdruk en de bijbehorende relaties voor actieve kopieën. Het doorbladeren wordt gedaan door a [ CQ.wcm.msm.BlueprintStatus.Tree ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), uitgave door a [ CQ.wcm.msm.BlueprintConfig ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en a [ CQ.wcm.msm.LiveCopyProperties ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `box`

  [ CQ.Ext.BoxComponent ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De klasse van de basis voor om het even welke [ Component ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die als doos moet worden gerangschikt, gebruikend breedte en hoogte.

  BoxComponent biedt automatische aanpassingen van het kadermodel voor grootte en positionering en werkt correct binnen het rendermodel van de Component.

* `browsedialog`

  [ CQ.BrowseDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met het dialoogvenster BrowseDialog kan de gebruiker door de opslagplaats bladeren om een pad te selecteren. Het wordt typisch gebruikt door a [ BrowseField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `browsefield`

  [ CQ.form.BrowseField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [ CQ.form.PathField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan**

* `bulkeditor`

  [ CQ.wcm.BulkEditor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `BulkEditor` verstrekt een onderzoeksmotor en een net om onderzoeksresultaten uit te geven.

  De `BulkEditor` moet in een HTML-formulier worden ingevoegd (vereist voor importfunctionaliteit). Dit werkt perfect met a [ CQ.Dialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `bulkeditorform`

  [ CQ.wcm.BulkEditorForm ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  BulkEditorForm verstrekt [ CQ.wcm.BulkEditor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) omringd door een vorm van HTML. De standalone versie van [ CQ.wcm.BulkEditor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Een HTML-formulier is vereist voor de importknop.

* `button`

  [ CQ.ext.Button ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Simple Button, klasse

* `buttongroup`

  [ CQ.Ext.ButtonGroup ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Container voor een groep knoppen.

* `chart`

  [ CQ.Ext.chart.Chart ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het pakket CQ.Ext.chart biedt de mogelijkheid om gegevens te visualiseren met flash-gebaseerde grafieken. Elke grafiek bindt direct aan een CQ.Ext.data.Store toelatend automatische updates van de grafiek. Om de blik en het gevoel van een grafiek te veranderen, zie [ chartStyle ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [ extraStyle ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config opties.

* `checkbox`

  [ CQ.Ext.form.Checkbox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld voor één selectievakje. Kan worden gebruikt als directe vervanging voor traditionele selectievakjes.

* `checkboxgroup`

  [ CQ.Ext.form.CheckboxGroup ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een groeperende container voor [ CQ.Ext.form.Checkbox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controles.

* `clearcombo`

  [ CQ.form.ClearableComboBox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De ClearableComboBox is een niet-bewerkbare keuzelijst met invoervak met een trigger om de waarde ervan te wissen.

* `colorfield`

  [ CQ.form.ColorField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het ColorField laat de gebruiker een waarde van de kleurenhexuitdraai of het gebruiken van a [ CQ.Ext.ColorMenu ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) ingaan.

* `colorlist`

  [ CQ.form.ColorList ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de ColorList kan de gebruiker een kleur kiezen in een bewerkbare lijst.

* `colormenu`

  [ CQ.Ext.menu.ColorMenu ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menu dat a [ CQ.Ext.ColorPalette ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Component bevat.

* `colorpalette`

  [ CQ.Ext.ColorPalette ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Eenvoudige kleurenpaletklasse voor het kiezen van kleuren. Het palet kan worden gerenderd naar elke gewenste container.

* `combo`

  [ CQ.Ext.form.ComboBox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een combobox-besturingselement met ondersteuning voor automatisch aanvullen, extern laden, pagineren en vele andere functies.

  Een ComboBox werkt op een vergelijkbare manier als een traditioneel HTML &lt;select>-veld. Het verschil is dat om [ valueField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor te leggen, moet u a [ hiddenName ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) specificeren om een verborgen input tot stand te brengen.

* `component`

  [ CQ.ext.Component ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor alle `Ext` -componenten. Alle subklassen van Component kunnen aan de geautomatiseerde `Ext` componentenlevenscyclus van verwezenlijking, het teruggeven, en vernietiging deelnemen die door de [ 2} klasse van de Container {wordt verstrekt. ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) De componenten kunnen aan een Container door de [ punten ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) worden toegevoegd config optie op het tijdstip dat de Container wordt gecreeerd.

* `componentextractor`

  [ CQ.wcm.ComponentExtractor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met ComponentExtractor kan de gebruiker componenten van een website/pagina extraheren.

* `componentselector`

  [ CQ.form.ComponentSelector ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gegroepeerde, geordende selectie van beschikbare componenten.

* `componentstyles`

  [ CQ.form.ComponentStyles ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `compositefield`

  [ CQ.form.CompositeField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor op deelvensters gebaseerde, complexe formuliervelden die één formulierveld of een groep formuliervelden bevatten.

* `container`

  [ CQ.Ext.Container ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De klasse van de basis voor om het even welk [ CQ.Ext.BoxComponent ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die andere Componenten kan bevatten. Containers verwerken het basisgedrag van het bevatten van items, namelijk items toevoegen, invoegen en verwijderen.

  De meest algemeen gebruikte klassen van de Container zijn [ CQ.Ext.Panel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [ CQ.Ext.Window ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), en [ CQ.Ext.TabPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `contentfinder`

  [ CQ.wcm.ContentFinder ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinder is een gespecialiseerde twee-kolom [ Viewport ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die de daadwerkelijke Vinder van de Inhoud op de linkerzijde en het Kader van de Inhoud op het recht bevat.

* `contentfindertab`

  [ CQ.wcm.ContentFinderTab ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ContentFinderTab is een gespecialiseerd paneel dat eigenschappen verstrekt die in de lusjepanelen van [ worden gebruikt CQ.wcm.ContentFinder ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html). Doorgaans bevat het een zoekformulier - het vak Query - en een gegevensweergave om de zoekopdracht weer te geven.

* `cq.workflow.model.combo`

  [ CQ.wcm.WorkflowModelCombo ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  WorkflowModelCombo is een aangepaste [ CQ.Ext.form.ComboBox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die een lijst van beschikbare werkschemamodellen toont.

* `cq.workflow.model.selector`

  [ CQ.wcm.WorkflowModelSelector ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De WorkflowModelSelector combineert een WorkflowModelCombo met een duimnagelbeeld van het werkschema, en knopen om werkschemamodellen tot stand te brengen en uit te geven.

* `createsitewizard`

  [ CQ.wcm.CreateSiteWizard ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De CreateSiteWizard is een geleidelijke tovenaar om (MSM) plaatsen tot stand te brengen.

* `createversiondialog`

  [ CQ.wcm.CreateVersionDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster CreateVersionDialog is een dialoogvenster waarin een versie van een pagina kan worden gemaakt.

* `customcontentpanel`

  [ CQ.CustomContentPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CustomContentPanel is een speciaal paneel voor gebruik in [ CQ.Dialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html): Zijn inhoud wordt teruggewonnen van en voorgelegd aan een verschillende URL dan de andere gebieden in de dialoogdoos.

* `cycle`

  [ CQ.Ext.CycleButton ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde SplitButton die een menu van [ CQ.Ext.menu.CheckItem ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) elementen bevat. De knoop cycli automatisch door elk menupunt op elke klik, die de 1} gebeurtenis van de verandering van de knoop [ opheffen {of die de ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) changeHandler [ functie van de knoop roepen, als verstrekt) voor het actieve menupunt.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `dataview`

  [ CQ.Ext.DataView ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een mechanisme voor het weergeven van gegevens met behulp van aangepaste lay-outsjablonen en opmaak. DataView gebruikt een [ CQ.Ext.XTemplate ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) als zijn intern het malplaatjemechanisme, en gebonden aan [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) zodat aangezien de gegevens in de opslag veranderen de mening automatisch wordt bijgewerkt om op de veranderingen te wijzen.

* `datefield`

  [ CQ.Ext.form.DateField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het verstrekt een gebied van de datuminput van a [ CQ.Ext.DatePicker ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) drop-down en automatische datumbevestiging.

* `datemenu`

  [ CQ.Ext.menu.DateMenu ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menu dat een {[ Component 0} CQ.Ext.DatePicker bevat.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `datepicker`

  [ CQ.Ext.DatePicker ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een pop-updatumkiezer. Deze klasse wordt gebruikt door de [ ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) klasse DateField om het doorbladeren en de selectie van geldige data toe te staan.

* `datetime`

  [ CQ.form.DateTime ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DateTime laat de gebruiker een datum en een tijd ingaan door [ CQ.Ext.form.DateField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [ CQ.Ext.form.TimeField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te combineren.

* `dialog`

  [ CQ.Dialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster is een speciaal venster. Het heeft een vorm in zijn lichaam en een knoopgroep in zijn footer. Deze wordt gewoonlijk gebruikt om inhoud te bewerken, maar kan ook alleen informatie weergeven.

* `dialogfieldset`

  [ CQ.form.DialogFieldSet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  DialogFieldSet is a [ FieldSet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor gebruik in [ Dialogi ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `directstore`

  [ CQ.Ext.data.DirectStore ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om tot een [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te leiden die met [ CQ.Ext.data.DirectProxy ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [ CQ.Ext.data.JsonReader ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) wordt gevormd om interactie met een [ CQ.Ext.Direct ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Server-kant [ gemakkelijker te maken Leverancier ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `displayfield`

  [ CQ.Ext.form.DisplayField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een alleen-weergeven tekstveld dat niet is gevalideerd en niet is verzonden.

* `editbar`

  [ CQ.wcm.EditBar ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De EditBar laat de gebruiker inhoud uitgeven gebruikend knopen op een bar.

  Hoewel hier niet vermeld, heeft EditBar alle leden van [ CQ.wcm.EditBase ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `editor`

  [ CQ.ext.Editor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een veld voor een basiseditor dat het weergeven/verbergen op aanvraag afhandelt en beschikt over ingebouwde logica voor grootte en gebeurtenisafhandeling.

* `editorgrid`

  [ CQ.Ext.grid.EditorGridPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse breidt de [ Klasse GridPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) uit om cel het uitgeven op geselecteerde [ kolommen ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te verstrekken. De editable kolommen worden gespecificeerd door een [ redacteur ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in de [ kolomconfiguratie ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te verstrekken.

* `editrollover`

  [ CQ.wcm.EditRollover ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de EditRollover kan de gebruiker inhoud bewerken door te dubbelklikken en worden meer bewerkhandelingen uitgevoerd via een contextmenu. Het bewerkbare gebied wordt aangegeven met een kader wanneer de muis over de inhoud beweegt.

* `feedimporter`

  [ CQ.wcm.FeedImporter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FeedImporter kan de gebruiker RSS- of Atom-feeds importeren en pagina&#39;s maken voor elke feed-invoer.

* `field`

  [ CQ.Ext.form.Field ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basisklasse voor formuliervelden met standaardfuncties voor gebeurtenisafhandeling, -grootte, -afhandeling en andere functies.

* `fieldset`

  [ CQ.Ext.form.FieldSet ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De standaard container die voor het groeperen van punten binnen a [ wordt gebruikt vorm ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `fileuploaddialogbutton`

  [ CQ.form.FileUploadDialogButton ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FileUploadDialogButton wordt een knop gemaakt waarmee een nieuw dialoogvenster wordt geopend voor het uploaden van een bestand via FileUploadField. Kan worden gebruikt in bewerkingsdialoogvensters waar het uploaden in een afzonderlijk formulier moet plaatsvinden.

* `fileuploadfield`

  [ CQ.form.FileUploadField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met FileUploadField kan de gebruiker één bestand selecteren dat moet worden geüpload.

* `findreplacedialog`

  [ CQ.wcm.FindReplaceDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De FindReplaceDialog is een dialoogdoos voor het vinden en het vervangen van tekenen in een pagina en zijn kindpagina&#39;s.

* `flash`

  [ CQ.Ext.FlashComponent ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `grid`

  [ CQ.Ext.grid.GridPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse vertegenwoordigt de primaire interface van een op component-gebaseerd netcontrole om gegevens in een tabelvorm formaat van rijen en kolommen te vertegenwoordigen.

* `groupingstore`

  [ CQ.Ext.data.GroupingStore ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde opslagimplementatie die het groeperen van verslagen door één van de beschikbare gebieden voorziet. Gebruikt met [ CQ.Ext.grid.GroupingView ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om het gegevensmodel voor een gegroepeerde GridPanel te bewijzen.

* `heavymovedialog`

  [ CQ.wcm.HeavyMoveDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het dialoogvenster HeavyMoveDialog is een dialoogvenster voor het verplaatsen van een pagina en de onderliggende pagina&#39;s, waarin ook wordt overwogen eerder geactiveerde pagina&#39;s opnieuw in te schakelen (&#39;zware&#39; verplaatsing).

* `hidden`

  [ CQ.Ext.form.Hidden ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een verborgen basisveld voor het opslaan van verborgen waarden in formulieren die moeten worden doorgegeven aan het verzenden van het formulier.

* `historybutton`

  [ CQ.HistoryButton ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  HistoryButton is een kleine hulpklasse om rug en voorwaartse knopen gemakkelijk te verstrekken. Meestal zijn twee verwante instanties vereist: de voorwaartse knopinstantie is een eenvoudige knop die is gekoppeld aan de achtergrondknopinstantie die de geschiedenis afhandelt.

* `htmleditor`

  [ CQ.Ext.form.HtmlEditor ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze biedt een lichtgewicht component van HTML Editor. Safari biedt geen ondersteuning voor bepaalde werkbalkfuncties, zodat deze automatisch door het systeem worden verborgen wanneer dat nodig is. Wordt in voorkomend geval vermeld in de configuratieopties.

  De de toolbarknopen van de redacteur hebben tooltips die in het [ worden bepaald buttonTips ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bezit.

* `iframedialog`

  [ CQ.IframeDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een dialoogvenster zonder opmaak waarin de inhoud van een iframe wordt weergegeven en waarin formulieren in iframes kunnen worden geplaatst.

* `iframepanel`

  [ CQ.IframePanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een deelvenster met een iframe. Het biedt eenvoudige verwezenlijking van iframes, een iframe ladingsgebeurtenis, en gemakkelijke toegang tot de inhoud van iframe.

* `inlinetextfield`

  [ CQ.form.InlineTextField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  InlineField is een tekstveld dat als label wordt weergegeven wanneer de focus niet is gericht.

* `jsonstore`

  [ CQ.Ext.data.JsonStore ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van gegevens te maken JSON gemakkelijker. Een JsonStore wordt automatisch gevormd met a [ CQ.Ext.data.JsonReader ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `label`

  [ CQ.Ext.form.Label ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld Standaardlabel.

* `languagecopydialog`

  [ CQ.wcm.LanguageCopyDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De LanguageCopyDialog is een dialoogvenster voor het kopiëren van taalbomen.

* `linkchecker`

  [ CQ.wcm.LinkChecker ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De LinkChecker is een hulpmiddel om externe verbindingen in een plaats te controleren.

* `listview`

  [ CQ.Ext.list.ListView ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  CQ.Ext.list.ListView is een snelle en licht-gewichtimplementatie van a [ Net-als ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) mening.

* `livecopyproperties`

  [ CQ.wcm.msm.LiveCopyProperties ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  LiveCopyProperties biedt een deelvenster voor het weergeven en bewerken van de eigenschappen van Live Copy (relatieovererving, synchronisatietrigger en synchronisatiehandelingen).

* `lvbooleancolumn`

  [ CQ.Ext.list.BooleanColumn ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kolomdefinitieklasse die Booleaanse gegevensvelden rendert. Zie [ xtype ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [ CQ.Ext.list.Column ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `lvcolumn`

  [ CQ.Ext.list.Column ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Deze klasse kapselt kolomconfiguratiegegevens in die in initialisatie van a [ moeten worden gebruikt ListView ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `lvdatecolumn`

  [ CQ.Ext.list.DateColumn ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een de definitieklasse van de Kolom die een overgegaan datum volgens de standaardscène, of a gevormde [ formaat ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) teruggeeft. Zie [ xtype ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [ CQ.Ext.list.Column ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `lvnumbercolumn`

  [ CQ.Ext.list.NumberColumn ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een de definitieklasse van de Kolom die een numeriek gegevensgebied volgens a [ formaat ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) koord teruggeeft. Zie [ xtype ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) config optie van [ CQ.Ext.list.Column ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor meer details.

* `mediabrowsedialog`

  [ CQ.MediaBrowseDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [ de Vinder van de Inhoud ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om media in plaats daarvan te doorbladeren.**

  De MediaBrowseDialog is een dialoogdoos voor het doorbladeren van de media bibliotheek.

* `menu`

  [ CQ.Ext.menu.Menu ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een menuobject. De container waaraan u menu-items kunt toevoegen. Het menu kan ook als basisklasse dienen wanneer u een gespecialiseerd die menu van een andere component (als [ CQ.Ext.menu.DateMenu ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bijvoorbeeld) wordt gebaseerd.

  De menu&#39;s kunnen of [ menupunten ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), of algemene [ Component ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) s bevatten.

* `menubaseitem`

  [ CQ.Ext.menu.BaseItem ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De basisklasse voor alle items die in menu&#39;s worden gerenderd. BaseItem verstrekt gebrek die, geactiveerd staatsbeheer, en de opties van de basisconfiguratie teruggeeft door alle menucomponenten worden gedeeld.

* `menucheckitem`

  [ CQ.Ext.menu.CheckItem ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Hiermee wordt een menu-item toegevoegd dat standaard een selectievakje bevat, maar dat ook deel kan uitmaken van een groep keuzerondjes.

* `menuitem`

  [ CQ.Ext.menu.Item ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een basisklasse voor alle menu-items die menu-gerelateerde functionaliteit vereisen (zoals submenu&#39;s) en die geen statische weergave-items zijn. Het punt breidt de basisfunctionaliteit van [ CQ.Ext.menu.BaseItem ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) door menu-specifieke activering toe te voegen en behandeling te klikken uit.

* `menuseparator`

  [ CQ.Ext.menu.Separator ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een scheidingsbalk toegevoegd aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Over het algemeen, voegt u één het toe door &quot;-&quot;in uw vraag te gebruiken om toe te voegen () of in uw punten config eerder dan direct tot stand te brengen.

* `menutextitem`

  [ CQ.Ext.menu.TextItem ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een statische tekenreeks toegevoegd aan een menu dat wordt gebruikt als een kop- of groepsscheidingsteken.

* `metadata`

  [ CQ.dam.form.Metadata ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Metadata` biedt een set velden waarmee de informatie wordt bepaald die nodig is voor een metagegevensveld, zoals bijvoorbeeld wordt gebruikt op pagina&#39;s in de Editor van middelen.

  Deze biedt de volgende velden:

* `multifield`

  [ CQ.form.MultiField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `MultiField` is een bewerkbare lijst met formuliervelden voor het bewerken van eigenschappen met meerdere waarden.

* `mvt`

  [ CQ.form.MVT ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de Multivariate Testing-component kunt u een set afbeeldingen definiëren en bewerken die als wisselende banners worden weergegeven. Klik door tariefstatistieken worden verzameld per banner.

* `notificationinbox`

  [ CQ.wcm.NotificationInbox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `NotificationInbox` kan de gebruiker zich abonneren op WCM-handelingen en meldingen beheren.

* `numberfield`

  [ CQ.Ext.form.NumberField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Numeriek tekstveld dat automatische toetsaanslag en numerieke validatie biedt.

* `offlineimporter`

  [ CQ.wcm.OfflineImporter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `OfflineImporter` is een programma voor het importeren en converteren van Microsoft® Word-documenten naar AEM-pagina&#39;s. Met deze functie kan inhoud offline worden bewerkt met een tekstverwerker.

* `ownerdraw`

  [ CQ.form.OwnerDraw ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `OwnerDraw` kan aangepaste HTML-code bevatten (die rechtstreeks wordt ingevoerd of wordt opgehaald via een URL).

* `paging`

  [ CQ.Ext.PagingToolbar ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Naarmate het aantal records toeneemt, neemt de tijd die de browser nodig heeft om deze weer te geven toe. Met paginering wordt de hoeveelheid gegevens die met de klant wordt uitgewisseld, verminderd.

* `panel`

  [ CQ.ext.Panel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een `panel` is een container die specifieke functionaliteit en structurele componenten heeft die van het de perfecte bouwsteen voor toepassing-georiënteerde gebruikersinterfaces maken.

  De panelen, door hun overerving, zijn van [ CQ.Ext.Container ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `paragraphreference`

  [ CQ.form.ParagraphReference ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In het veld Alineasereferentie kunt u door pagina&#39;s bladeren en een van de alinea&#39;s selecteren. Het bestaat uit een triggerveld en een gekoppeld alineascherm.

* `password`

  [ CQ.form.Password ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Password` is als a [ CQ.Ext.form.TextField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) maar houdt zijn waarde privé, toestaand gebruikers om gevoelige gegevens in te gaan.

* `pathcompletion`

  [ CQ.form.PathCompletion ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [ CQ.form.PathField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan**

* `pathfield`

  [ CQ.form.PathField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `PathField` is een inputgebied dat voor wegen met wegvoltooiing en een knoop wordt ontworpen om a [ CQ.BrowseDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) te openen voor het doorbladeren van de serverbewaarplaats. U kunt ook door alinea&#39;s bladeren om geavanceerde koppelingen te genereren.

* `progress`

  [ CQ.Ext.ProgressBar ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een bij te werken voortgangsbalkcomponent. De voortgangsbalk ondersteunt twee verschillende modi: handmatig en automatisch.

  Op handwijze, bent u verantwoordelijk voor het tonen, het bijwerken (via [ updateProgress ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)) en het ontruimen van de vooruitgangsbar zoals nodig van uw eigen code. Deze methode is vooral geschikt wanneer u de voortgang wilt weergeven.

* `propertygrid`

  [ CQ.Ext.grid.PropertyGrid ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde netimplementatie bedoeld om het traditionele bezitsnet zoals typisch gezien in ontwikkeling IDEs na te bootsen. Elke rij in het net vertegenwoordigt een bezit van één of ander voorwerp, en het gegeven wordt opgeslagen als reeks naam/waardeparen in [ CQ.Ext.grid.PropertyRecord.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `propgrid`

  [ CQ.PropertyGrid ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `PropertyGrid` is een algemeen raster dat wordt gebruikt voor het weergeven en bewerken van eigenschappen van objecten.

* `quicktip`

  [ CQ.Ext.QuickTip ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `@xtype quicktip` - een gespecialiseerde tooltip klasse voor tooltips die in prijsverhoging kunnen worden gespecificeerd en automatisch door de globale {[ instantie 1} CQ.Ext.QuickTips worden geleid. ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) Zie de QuickTips-klasseheader voor meer gebruiksdetails en voorbeelden.

* `radio`

  [ CQ.Ext.form.Radio ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Veld Single `radio` . Hetzelfde als Selectievakje, maar als handig hulpmiddel om het invoertype automatisch in te stellen. De browser groepeert automatisch keuzerondjes wanneer elk keuzerondje in de groep dezelfde naam gebruikt.


* `radiogroup`

  [ CQ.Ext.form.RadioGroup ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een groeperingscontainer voor [ CQ.Ext.form.Radio ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) controles.

* `referencesdialog`

  [ CQ.wcm.ReferencesDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `ReferencesDialog` is een dialoogvenster waarin verwijzingen op een pagina worden weergegeven.

* `restoretreedialog`

  [ CQ.wcm.RestoreTreeDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RestoreTreeDialog` is een dialoogvenster voor het herstellen van een vorige versie van een boomstructuur.

* `restoreversiondialog`

  [ CQ.wcm.RestoreVersionDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De RestoreVersionDialog is een dialoogdoos voor het herstellen van een vorige versie van een pagina.

* `richtext`

  [ CQ.form.RichText ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RichText` biedt een formulierveld voor het bewerken van opgemaakte tekstgegevens (RTF-gegevens).

  De component `RichText` biedt momenteel de volgende functies:

* `rolloutplan`

  [ CQ.wcm.msm.RolloutPlan ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het rolloutPlan verstrekt een dialoogdoos om de vooruitgang van de paginalopulatie te bekijken. A [ CQ.wcm.msm.RolloutWizard ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) begint rolloutPlan.

* `rolloutwizard`

  [ CQ.wcm.msm.RolloutWizard ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `RolloutWizard` verstrekt een tovenaar voor het opstellen van een pagina. RolloutWizard begint a [ CQ.wcm.msm.RolloutPlan ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `searchfield`

  [ CQ.form.SearchField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `SearchField` biedt een zoekveld dat de resultaten bevat in een vervolgkeuzelijst die kan worden gebruikt voor het zoeken in de opslagplaats.

* `selection`

  [ CQ.form.Selection ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `Selection` kan de gebruiker kiezen uit verschillende opties. De opties kunnen onderdeel zijn van de configuratie of worden geladen vanuit een JSON-reactie. De selectie kan worden weergegeven als een vervolgkeuzelijst (selecteren) of als een keuzelijst met invoervak (selecteren plus tekst-item zonder opmaak).

* `sidekick`

  [ CQ.wcm.Sidekick ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Sidekick` is een zwevende hulplijn waarmee de gebruiker algemene gereedschappen voor het bewerken van pagina&#39;s krijgt.

* `siteadmin`

  [ CQ.wcm.SiteAdmin ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `SiteAdmin` is een console die WCM beleidsfuncties verstrekt.

* `siteimporter`

  [ CQ.wcm.SiteImporter ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `SiteImporter` kan de gebruiker volledige websites importeren en eerste projecten maken.

* `sizefield`

  [ CQ.form.SizeField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `SizeField` kan de gebruiker de breedte en hoogte invoeren (bijvoorbeeld voor een afbeelding).

* `slider`

  [ CQ.Ext.Slider ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Schuifregelaar die ondersteuning biedt voor verticale of horizontale oriëntatie, toetsenbordaanpassingen, configureerbare magnetisch uitlijnen, asklikken en animatie. Het kan als punt aan om het even welke container worden toegevoegd. Bijvoorbeeld gebruik: ...

* `slideshow`

  [ CQ.form.Slideshow ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met de component Presentatie kunt u een set afbeeldingen en afbeeldingstitels definiëren en bewerken. Gebruikers kunnen de set als een presentatie weergeven.

  De component Slideshow is gebaseerd op de {[ component 0} CQ.form.SmartImage.](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `smartfile`

  [ CQ.form.SmartFile ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het SmartFile-bestand is een intelligente uploader voor bestanden.

  Als een Flash-insteekmodule (versie >= 9) is geïnstalleerd, worden uploads uitgevoerd met behulp van de SWF-uploadbibliotheek die een handige manier biedt om uploads af te handelen.

* `smartimage`

  [ CQ.form.SmartImage ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De SmartImage is een intelligente uploader voor afbeeldingen. Het biedt gereedschappen voor het verwerken van een geüploade afbeelding, bijvoorbeeld een gereedschap voor het definiëren van afbeeldingen met hyperlinks en een functie voor het uitsnijden van afbeeldingen.

  De component is ontworpen voor gebruik in een afzonderlijk tabblad in het dialoogvenster.

* `spacer`

  [ CQ.ext.Spacer ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Wordt gebruikt om een grote ruimte in een lay-out te bieden.

* `spinner`

  [ CQ.form.Spinner ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Spinner` is een triggerveld voor numerieke, datum- of tijdwaarden. De waarde kan worden verhoogd en verlaagd met de beschikbare triggers omhoog en omlaag, het schuifwiel of toetsen.

* `splitbutton`

  [ CQ.Ext.SplitButton ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  A `splitbutton` dat een ingebouwde drop-down pijl verstrekt die een gebeurtenis los van de standaard klikgebeurtenis van de knoop kan in brand steken. Doorgaans wordt het gebruikt om een vervolgkeuzemenu weer te geven dat aanvullende opties biedt voor de primaire knopactie, maar elke aangepaste handler kan de `arrowclick` -implementatie verschaffen.

* `static`

  [ CQ.Static ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Static` kan worden gebruikt om willekeurige tekst of HTML weer te geven.

* `statistics`

  [ CQ.wcm.Statistics ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  In `Statistics` worden de paginamonpressies als een diagram weergegeven. Met de widget kunt u een periode selecteren waarvoor de statistieken moeten worden weergegeven.

* `store`

  [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `Store` klasse kapselt een cliënt-zijgeheime voorgeheugen van [ Verslag ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voorwerpen in die inputgegevens voor Componenten zoals [ GridPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), [ ComboBox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), of [ DataView ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) verstrekken.

* `suggestfield`

  [ CQ.form.SuggestField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `SuggestField` biedt de gebruiker suggesties op basis van hun invoer.

* `switcher`

  [ CQ.Switcher ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `Switcher` verstrekt een knoopgroep voor de kopbalbar in een console om tussen Websites, Digitale Assets, Hulpmiddelen, Workflow, en Veiligheid te schakelen.

* `tableedit`

  [ CQ.form.TableEdit ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  **Afgekeurd: Gebruik [ CQ.form.TableEdit2 ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) in plaats daarvan.**

* `tableedit2`

  [ CQ.form.TableEdit2 ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  De `TableEdit2` biedt een widget voor het maken van tabellen.

* `tabpanel`

  [ CQ.Ext.TabPanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een eenvoudige tabcontainer. TabPanels kunnen precies als standaard [ CQ.Ext.Panel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor lay-outdoeleinden worden gebruikt, maar hebben ook speciale steun voor het bevatten van kindComponenten ([`items` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `tags`

  [ CQ.tagging.TagInputField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  ```
  CQ.tagging.TagInputField
  ```

  is een formulierwidget voor het invoeren van codes. Het bevat een pop-upmenu voor het selecteren van bestaande tags, inclusief automatisch aanvullen en veel andere functies.

* `textarea`

  [ CQ.Ext.form.TextArea ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Tekstveld met meerdere regels. Kan worden gebruikt als directe vervanging voor traditionele `textarea` -velden, plus ondersteuning voor automatisch aanpassen van grootte.

* `textbutton`

  [ CQ.TextButton ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `TextButton` verstrekt een tekstverbinding met de mogelijkheden van a [ CQ.Ext.Button ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

* `textfield`

  [ CQ.Ext.form.TextField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basistekstveld. Kan als directe vervanging voor traditionele tekstinput worden gebruikt, of als basisklasse voor verfijnde inputcontroles (als [ CQ.Ext.form.TextArea ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [ CQ.Ext.form.ComboBox ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)).

* `thumbnail`

  [ CQ.form.Thumbnail ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

* `timefield`

  [ CQ.Ext.form.TimeField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Het verstrekt een gebied van de tijdinput met tijd drop-down en automatische tijdbevestiging. Voorbeeld: ...

* `tip`

  [ CQ.ext.Tip ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype uiteinde Dit is de basisklasse voor [ CQ.Ext.QuickTip ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) en [ CQ.Ext.Tooltip ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) die de basislay-out en het plaatsen verstrekt die alle op uiteinde-gebaseerde klassen vereisen. Deze klasse kan direct voor eenvoudige, statisch gepositioneerde uiteinden worden gebruikt.

* `titleseparator`

  [ CQ.menu.TitleSeparator ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Er wordt een scheidingsbalk toegevoegd aan een menu dat wordt gebruikt om logische groepen menu-items te verdelen. Het scheidingsteken kan ook een titel bevatten.

* `toolbar`

  [ CQ.ext.Toolbar ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Basic `Toolbar` -klasse. Hoewel [`defaultType` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) voor Toolbar [`button` ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) is, kunnen de elementen van de Toolbar (kindpunten voor de Toolbar container) vrijwel om het even welk type van Component zijn. Werkbalkelementen kunnen expliciet worden gemaakt via hun constructors.

* `tooltip`

  [ CQ.Ext.ToolTip ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een standaardimplementatie `tooltip` voor het verstrekken van extra informatie wanneer het hangen over een doelelement. @xtype tooltip.

* `treegrid`

  [ CQ.tree.TreeGrid ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  @xtype `treegrid`

* `treepanel`

  [ CQ.Ext.tree.TreePanel ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  `TreePanel` verstrekt boom-gestructureerde vertegenwoordiging UI van boom-gestructureerde gegevens.

  [ TreeNode ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) wordt toegevoegd aan `TreePanel` kan meta-gegevens bevatten die door uw toepassing in hun [ worden gebruikt attributen ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) bezit.

* `trigger`

  [ CQ.Ext.form.TriggerField ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Dit is een handige omslag voor `TextFields` waarmee een klikbare triggerknop wordt toegevoegd (die standaard lijkt op een keuzelijst met invoervak). De trekker heeft geen standaardactie, zodat moet u een functie toewijzen om de trekker uit te voeren klikt manager door [ onTriggerClick ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) met voeten te treden. U kunt een `TriggerField` rechtstreeks maken, aangezien het net als een combobox wordt weergegeven.

* `uploaddialog`

  [ CQ.UploadDialog ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Met `UploadDialog` kan de gebruiker bestanden uploaden naar de opslagplaats. Hiermee wordt een nieuwe UploadDialog gemaakt.

* `userinfo`

  [ CQ.UserInfo ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Werkbalkitem om de huidige gebruikersnaam weer te geven en gebruikersacties zoals het bewerken van gebruikerseigenschappen en imitatie toe te staan.

* `viewport`

  [ CQ.Ext.Viewport ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een gespecialiseerde container die het zichtbare toepassingsgebied vertegenwoordigt (viewport van browser).

  De `Viewport` geeft zichzelf aan de documenttekst weer en past zichzelf automatisch aan de grootte van de viewport van de browser aan en beheert de grootte van het venster. Er kan slechts één Viewport zijn gemaakt.

* `window`

  [ CQ.ext.Window ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een speciaal deelvenster dat is bedoeld voor gebruik als toepassingsvenster. De vensters worden gedreven, [ resizable ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html), en [ draggable ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) door gebrek. De vensters kunnen [ worden gemaximaliseerd ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) om viewport te vullen, aan hun vroegere grootte wordt hersteld, en kunnen [ worden geminimaliseerd ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) d.

* `xmlstore`

  [ CQ.Ext.data.XmlStore ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html)

  Een kleine helperklasse om het creëren van [ CQ.Ext.data.Store ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html) van de gegevens van XML gemakkelijker te maken. Een `XmlStore` wordt automatisch gevormd met a [ CQ.Ext.data.XmlReader ](https://developer.adobe.com/experience-manager/reference-materials/6-5/widgets-api/index.html).

  `cqinclude` - Een pseudo-xtype dat widgetdefinities bevat van een ander pad in de repository. Deze wordt meestal gebruikt in paginadialoogvensters. Er is geen werkelijke JavaScript-widget-klasse voor dit xtype. De `CQ.Util` -klasse verwerkt deze met behulp van de `formatData()` -functie.
