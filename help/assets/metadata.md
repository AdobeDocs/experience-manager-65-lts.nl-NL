---
title: Metagegevens van uw digitale elementen beheren
description: Leer meer over de typen metagegevens en hoe u metagegevens kunt beheren voor elementen om elementen eenvoudig te organiseren en te verwerken.
contentOwner: AG
mini-toc-levels: 1
feature: Tagging, Metadata
role: Architect, Leader
hide: true
solution: Experience Manager, Experience Manager Assets
exl-id: dc231e6b-d656-4626-a800-ee66533b1c86
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '2231'
ht-degree: 10%

---

# Metagegevens van uw digitale elementen beheren {#managing-metadata-for-digital-assets}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/manage-metadata.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |

<!-- Scope of metadata articles:
* metadata.md: The scope of this article is basic metadata updates, changes, and so on, operations that end-users can do.
* metadata-concepts.md: All conceptual information. Minor instructions are OK but it is an FYI article about support and standards.
* metadata-config.md: New article. Contains all configuration and administration how-to info related to metadata of assets.
-->

[!DNL Adobe Experience Manager Assets] houdt metagegevens bij voor elk element. Het maakt het gemakkelijker om activa te categoriseren en te organiseren en het helpt mensen die naar een specifiek bezit zoeken. Dankzij de mogelijkheid om metagegevens te extraheren uit bestanden die zijn geüpload naar [!DNL Experience Manager Assets] , kan het beheer van metagegevens worden geïntegreerd in de creatieve workflow. Met de mogelijkheid om metagegevens bij uw elementen te houden en te beheren, kunt u elementen automatisch ordenen en verwerken op basis van hun metagegevens.

## Metagegevens en de oorsprong ervan {#how-to-edit-or-add-metadata}

Metagegevens zijn aanvullende informatie over het element die kan worden doorzocht. Deze wordt toegevoegd aan elementen en in [!DNL Experience Manager] wordt deze verwerkt wanneer u een element uploadt. U kunt de bestaande metagegevens bewerken en nieuwe eigenschappen van metagegevens toevoegen aan bestaande velden. Organisaties hebben beheerste en betrouwbare metagegevenswoordenboeken nodig. Daarom staat [!DNL Experience Manager Assets] het toevoegen van nieuwe eigenschappen van metagegevens op aanvraag niet toe. Alleen beheerders en ontwikkelaars kunnen nieuwe eigenschappen of velden toevoegen die metagegevens bevatten. Gebruikers kunnen de bestaande velden vullen met metagegevens.

U kunt de volgende methoden gebruiken om metagegevens toe te voegen aan digitale elementen:

* Om te beginnen voegen de native toepassingen die elementen maken er metagegevens aan toe. Bijvoorbeeld, [ Acrobat voegt sommige meta-gegevens ](https://helpx.adobe.com/nl/acrobat/using/pdf-properties-metadata.html) aan de dossiers van PDF toe of een camera voegt sommige basismeta-gegevens aan de foto&#39;s toe. Wanneer u elementen genereert, kunt u de metagegevens toevoegen in native toepassingen zelf. Bijvoorbeeld, kunt u [ meta-gegevens van IPTC in Adobe Lightroom ](https://helpx.adobe.com/nl/lightroom-classic/help/metadata-basics-actions.html) toevoegen.

* Voordat u een element uploadt naar [!DNL Experience Manager], kunt u metagegevens bewerken en wijzigen met de oorspronkelijke toepassing die is gebruikt om een element te maken of met een andere toepassing voor het bewerken van metagegevens. Wanneer u middelen uploadt naar Experience Manager, worden de metagegevens verwerkt. Bijvoorbeeld, zie hoe te [ werken met meta-gegevens in  [!DNL Adobe Bridge] ](https://helpx.adobe.com/nl/bridge/user-guide.html/bridge/using/metadata-adobe-bridge.ug.html) en zie het [ paneel van markeringen voor  [!DNL Adobe Bridge] ](https://exchange.adobe.com/creativecloud.details.20009.aem-tags-panel-for-bridge-cc.html) in [!DNL Adobe Exchange].

* In [!DNL Experience Manager Assets] kunt u metagegevens van elementen handmatig toevoegen of bewerken op de pagina [!UICONTROL Properties] .

* U kunt [ meta-gegevensprofielen ](/help/assets/metadata-config.md#metadata-profiles) functionaliteit van [!DNL Experience Manager Assets] gebruiken om meta-gegevens automatisch toe te voegen wanneer de activa aan DAM worden geupload.

## Metagegevens toevoegen of bewerken in [!DNL Experience Manager Assets] {#add-edit-metadata}

Voer de volgende stappen uit als u de metagegevens van een element wilt bewerken in de gebruikersinterface van [!DNL Assets] :

1. Voer een van de volgende handelingen uit:

   * Selecteer het element in de interface van [!DNL Assets] en klik op **[!UICONTROL View Properties]** op de werkbalk.
   * Selecteer in de miniatuur van het element de handeling **[!UICONTROL View Properties]** quick.
   * Van de activapagina, klik **[!UICONTROL View Properties]** ![ Assets- infopictogram ](assets/do-not-localize/info-circle-icon.png) van de toolbar.

   Op de elementpagina worden alle metagegevens van het element weergegeven. De metagegevens worden geëxtraheerd wanneer het element wordt geüpload (opgenomen) naar [!DNL Experience Manager] .

   ![ Uitgezochte Eigenschappen van een activa om zijn meta-gegevens ](assets/asset-metadata.png) te bekijken

   *Cijfer: geef of voeg meta-gegevens op activa [!UICONTROL Properties] pagina uit.*

1. Breng desgewenst wijzigingen aan in de metagegevens op de verschillende tabbladen en klik, wanneer u klaar bent, op **[!UICONTROL Save]** op de werkbalk om de wijzigingen op te slaan. Klik op **[!UICONTROL Close]** om terug te keren naar de webinterface van [!DNL Assets] .

   >[!NOTE]
   >
   >Als een tekstveld leeg is, is er geen bestaande metagegevensset. U kunt een waarde in het veld invoeren en deze opslaan om de eigenschap metadata toe te voegen.

Eventuele wijzigingen in de metagegevens van een element worden teruggeschreven naar het oorspronkelijke binaire bestand als onderdeel van de XMP-gegevens. De workflow voor het terugschrijven van metagegevens voegt de metagegevens toe aan het oorspronkelijke binaire bestand. Wijzigingen die worden aangebracht in de bestaande eigenschappen (zoals `dc:title` ), worden overschreven en nieuwe eigenschappen (zoals aangepaste eigenschappen zoals `cq:tags` ) worden toegevoegd aan het schema.

XMP schrijf-terug wordt gesteund en toegelaten voor de platforms en dossierformaten die in [ worden beschreven technische vereisten.](/help/sites-deploying/technical-requirements.md)

## Eigenschappen van metagegevens van meerdere elementen bewerken {#editing-metadata-properties-of-multiple-assets}

Met [!DNL Adobe Enterprise Manager Assets] kunt u de metagegevens van meerdere elementen tegelijk bewerken, zodat u snel algemene wijzigingen in metagegevens in meerdere elementen kunt doorgeven. U kunt de metagegevens voor meerdere verzamelingen ook bulksgewijs bewerken. Gebruik de eigenschappenpagina om wijzigingen in metagegevens uit te voeren voor meerdere elementen of verzamelingen:

* Eigenschappen van metagegevens wijzigen in een algemene waarde
* Tags toevoegen of wijzigen

Om de pagina van meta-gegevenseigenschappen, met inbegrip van het toevoegen van, het wijzigen van, het schrappen van meta-gegevenseigenschappen aan te passen, gebruik de [ schemageditor ](metadata-config.md#folder-metadata-schema).

>[!NOTE]
>
>De bulkbewerkingsmethoden werken voor elementen die beschikbaar zijn in een map of een verzameling. Voor de activa die over omslagen beschikbaar zijn of een gemeenschappelijke criteria aanpassen, is het mogelijk aan [ bulkupdate de meta-gegevens na het zoeken ](search-assets.md#metadataupdates).

1. Navigeer in de gebruikersinterface van [!DNL Assets] naar de locatie van de elementen die u wilt bewerken.
1. Selecteer de elementen waarvan u de algemene eigenschappen wilt bewerken.
1. Klik op de werkbalk op **[!UICONTROL Properties]** om de pagina met eigenschappen voor de geselecteerde elementen te openen.
1. Wijzig de eigenschappen van metagegevens voor geselecteerde elementen onder de verschillende tabbladen.
1. Als u de metagegevens van een specifiek element wilt weergeven, annuleert u de selectie van de resterende elementen in de lijst. Als u de selectie van een paar elementen op de pagina [!UICONTROL Properties] annuleert, worden de metagegevens van dergelijke elementen niet bijgewerkt.
1. Als u een ander metagegevensschema voor de elementen wilt selecteren, klikt u op **[!UICONTROL Settings]** op de werkbalk en selecteert u een schema. Klik op **[!UICONTROL Save & Close]**.
1. Selecteer **[!UICONTROL Append mode]** om de nieuwe metadata toe te voegen aan de bestaande metadata in velden die meerdere waarden bevatten. Als u deze optie niet selecteert, worden de bestaande metadata in de velden vervangen door de nieuwe metadata. Klik op **[!UICONTROL Submit]**.

![ het schemaschemabulk is van toepassing op veelvoudige activa ](assets/metadata-schema-bulk-edit.gif)

>[!CAUTION]
>
>Voor velden met één waarde worden de nieuwe metadata niet toegevoegd aan de bestaande waarde in het veld, zelfs niet als u **[!UICONTROL Append mode]** selecteert.

## Metagegevens importeren {#import-metadata}

Met [!DNL Assets] kunt u metagegevens van elementen in bulk importeren met een CSV-bestand. U kunt bulkupdates uitvoeren voor de onlangs geüploade elementen of de bestaande elementen door een CSV-bestand te importeren. U kunt ook metagegevens van elementen bulksgewijs invoeren vanuit een systeem van derden in de CSV-indeling.

De import van metagegevens is asynchroon en belemmert de systeemprestaties niet. Gelijktijdige update van de metagegevens voor meerdere elementen kan bronintensief zijn vanwege de terugschrijfactiviteit van XMP als de werkstroommarkering wordt gecontroleerd. Plan zo&#39;n import tijdens het gebruik van een slanke server, zodat de prestaties voor andere gebruikers niet worden beïnvloed.

>[!NOTE]
>
>Registreer de naamruimten eerst om metagegevens in aangepaste naamruimten te importeren.

1. Ga naar de gebruikersinterface van [!DNL Assets] en klik op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer **[!UICONTROL Metadata]** in het menu.
1. Klik op **[!UICONTROL Select File]** op de pagina **[!UICONTROL Metadata Import]** . Selecteer het CSV-bestand met de metadata.
1. Geef de volgende parameters op. Zie een steekproefCSV- dossier bij [ meta-invoer-steekproef-file.csv ](/help/assets/assets/metadata-import-sample-file.csv).

   | Parameters voor het importeren van metagegevens | Beschrijving |
   |:---|:---|
   | [!UICONTROL Batch Size] | Aantal elementen in een batch waarvoor metagegevens moeten worden geïmporteerd. De standaardwaarde is 50. Maximumwaarde is 100. |
   | [!UICONTROL Field Separator] | De standaardwaarde is `,` (een komma). U kunt elk ander teken opgeven. |
   | [!UICONTROL Multi Value Delimiter] | Scheidingsteken voor metagegevenswaarden. De standaardwaarde is `|` . |
   | [!UICONTROL Launch Workflows] | Standaard false. Wanneer deze eigenschap is ingesteld op `true` en de standaardinstellingen zijn van kracht voor de [!UICONTROL DAM Metadata WriteBack] -workflow (die metagegevens naar de binaire XMP-gegevens schrijft). Als u de workflows inschakelt, wordt het systeem trager. |
   | [!UICONTROL Asset Path Column Name] | Hiermee definieert u de kolomnaam voor het CSV-bestand met elementen. |

1. Klik op **[!UICONTROL Import]** op de werkbalk. Nadat de metagegevens zijn geïmporteerd, wordt een melding weergegeven in het Postvak IN [!UICONTROL Notification] .

1. Navigeer naar de [!UICONTROL Properties] -pagina van een element en controleer de waarden in de velden om te controleren of het bestand correct is geïmporteerd.

Als u datum en tijdstempel wilt toevoegen tijdens het importeren van metagegevens, gebruikt u de `YYYY-MM-DDThh:mm:ss.fff-00:00` -indeling voor datum en tijd. Datum en tijd worden door `T` van elkaar gescheiden, `hh` is uren in 24-uursnotatie, `fff` is nanoseconden en `-00:00` is tijdzoneverschuiving. Bijvoorbeeld, `2020-03-26T11:26:00.000-07:00` is 26 Maart, 2020 bij 11 :26: 00.000 AM PST tijd.

>[!CAUTION]
>
>Als de datumnotatie niet overeenkomt met `YYYY-MM-DDThh:mm:ss.fff-00:00` , worden de datumwaarden niet ingesteld. De datumnotaties van het geëxporteerde CSV-bestand met metagegevens hebben de indeling `YYYY-MM-DDThh:mm:ss-00:00` . Als u het wilt invoeren, zet het in het aanvaardbare formaat door de nanosecondewaarde toe te voegen die door `fff` wordt vermeld.

## Metagegevens exporteren {#export-metadata}

U kunt metagegevens voor meerdere elementen in CSV-indeling exporteren. De metagegevens worden asynchroon geëxporteerd en hebben geen invloed op de prestaties van het systeem. Als u metagegevens wilt exporteren, doorloopt [!DNL Experience Manager] de eigenschappen van het elementknooppunt `jcr:content/metadata` en de onderliggende knooppunten en worden de eigenschappen van de metagegevens geëxporteerd naar een CSV-bestand.

Hier volgen enkele voorbeelden van het gebruik van metagegevens voor bulksgewijs exporteren:

* Importeer de metagegevens in een systeem van derden wanneer u elementen migreert.
* Metagegevens over elementen delen met een groter projectteam.
* Test of controleer de metagegevens op conformiteit.
* Maak de metagegevens extern om deze afzonderlijk te lokaliseren.

1. Selecteer de elementenmap die elementen bevat waarvoor u metagegevens wilt exporteren. Selecteer **[!UICONTROL Export metadata]** in de werkbalk.

1. Geef in het dialoogvenster [!UICONTROL Metadata Export] een naam op voor het CSV-bestand. Selecteer **[!UICONTROL Include assets in subfolders]** als u metagegevens voor elementen in submappen wilt exporteren.

   ![ Interface en opties om meta-gegevens van alle activa in een omslag ](assets/export_metadata_page.png " Interface en opties uit te voeren om meta-gegevens van alle activa in een omslag ") uit te voeren

1. Selecteer de gewenste opties. Geef een bestandsnaam en zo nodig een datum op.

1. Geef in het veld **[!UICONTROL Properties to be exported]** op of u alle of specifieke eigenschappen wilt exporteren. Als u Selectieve eigenschappen kiest die u wilt exporteren, voegt u de gewenste eigenschappen toe.

1. Klik in de werkbalk op **[!UICONTROL Export]** . Een bericht bevestigt dat de metagegevens worden geëxporteerd. Sluit het bericht.

1. Open het bericht in het Postvak IN voor de exporttaak. Selecteer de taak en klik op **[!UICONTROL Open]** op de werkbalk. Klik op **[!UICONTROL CSV Download]** op de werkbalk om het CSV-bestand met de metagegevens te downloaden. Klik op **[!UICONTROL Close]**.

   ![ Dialoog om het Csv- dossier te downloaden dat meta-gegevens bevat die in bulk worden uitgevoerd ](assets/csv_download.png)

   *Cijfer: Dialoog om het Csv- dossier te downloaden dat meta-gegevens bevat die in bulk worden uitgevoerd.*

## Metagegevens van verzamelingen bewerken {#collections-metadata}

Voor details, zie [ mening en geef inzamelingsmeta-gegevens ](/help/assets/manage-collections.md#view-edit-collection-metadata) uit en [ geef meta-gegevens van veelvoudige inzamelingen in bulk ](/help/assets/manage-collections.md#editing-collection-metadata-in-bulk) uit.

## Een metagegevensprofiel toepassen op mappen {#applying-a-metadata-profile-to-folders}

<!-- TBD: Review this overview.
-->

Wanneer u een metagegevensprofiel toewijst aan een map, nemen eventuele submappen het profiel automatisch over van de bovenliggende map. Dit betekent dat u slechts één metagegevensprofiel kunt toewijzen aan een map. Denk daarom zorgvuldig na over de mapstructuur van de locatie waar u middelen uploadt, opslaat, gebruikt en archiveert.

Als u een ander metagegevensprofiel aan een map hebt toegewezen, overschrijft het nieuwe profiel het vorige profiel. De vorige bestaande mapelementen blijven ongewijzigd. Het nieuwe profiel wordt toegepast op de elementen die later aan de map worden toegevoegd.

Mappen waaraan een profiel is toegewezen, worden in de gebruikersinterface aangeduid met de naam van het profiel dat in de kaartnaam wordt weergegeven.

![ de mening van de Kaart toont het meta-gegevensprofiel dat op een omslag ](assets/metadata-profile-card-view-display.png) wordt toegepast

U kunt metagegevensprofielen toepassen op specifieke mappen of op alle elementen.

U kunt elementen opnieuw verwerken in een map die al een bestaand metagegevensprofiel heeft dat u later hebt gewijzigd. Zie [ het Opverwerken activa in een omslag nadat u zijn verwerkingsprofiel ](processing-profiles.md#reprocessing-assets) hebt uitgegeven.

U kunt een metadataprofiel toepassen op een map vanuit het menu **[!UICONTROL Tools]**, of vanuit **[!UICONTROL Properties]** als u zich in een map bevindt. In deze sectie wordt beschreven hoe u op beide manieren metadataprofielen kunt toepassen op mappen.

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

U kunt elementen in een map opnieuw verwerken die al een bestaand videoprofiel heeft dat u later wijzigt. Zie [ het Opverwerken activa in een omslag nadat u zijn verwerkingsprofiel ](processing-profiles.md#reprocessing-assets) hebt uitgegeven.

### Metagegevensprofielen toepassen op mappen vanuit de gebruikersinterface van [!UICONTROL Profiles] {#applying-metadata-profiles-to-folders-from-profiles-user-interface}

Voer de stappen uit om het metagegevensprofiel toe te passen:

1. Klik op het logo [!DNL Experience Manager] en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .
1. Selecteer het metagegevensprofiel dat u wilt toepassen op een of meerdere mappen.
1. Klik op **[!UICONTROL Apply Metadata Profile to Folder(s)]** en selecteer de map of meerdere mappen die u wilt gebruiken om de nieuw geüploade elementen te ontvangen. Klik vervolgens op **[!UICONTROL Done]** . Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

### Metagegevensprofielen toepassen op mappen vanuit [!UICONTROL Properties] {#applying-metadata-profiles-to-folders-from-properties}

1. Klik in de linkertrack op **[!UICONTROL Assets]** en navigeer naar de map waarop u een metagegevensprofiel wilt toepassen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens op **[!UICONTROL Properties]** .

1. Selecteer de tab **[!UICONTROL Metadata Profiles]** , selecteer het profiel in het pop-upmenu en klik op **[!UICONTROL Save]** .

Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

<!-- TBD: Commenting as the topic in metadata-config.md is incomplete.

### Apply metadata profile globally {#metadata-profile-global}

For details, see [configuration to apply metadata profile globally](/help/assets/metadata-config.md#apply-a-metadata-profile-globally). -->

### Een metagegevensprofiel uit mappen verwijderen {#removing-a-metadata-profile-from-folders}

Wanneer u een metagegevensprofiel uit een map verwijdert, nemen eventuele submappen automatisch de verwijdering van het profiel uit de bovenliggende map over. Alle verwerking van bestanden die in de mappen zijn opgetreden, blijft echter intact.

U kunt een metagegevensprofiel uit een map verwijderen vanuit het menu **[!UICONTROL Tools]** of vanuit de map **[!UICONTROL Properties]** in de map.

#### Metaprofielen uit mappen verwijderen via de gebruikersinterface Profielen {#removing-metadata-profiles-from-folders-via-profiles-user-interface}

1. Klik op het logo [!DNL Experience Manager] en navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Metadata Profiles]** .
1. Selecteer het metagegevensprofiel dat u uit een of meerdere mappen wilt verwijderen.
1. Klik op **[!UICONTROL Remove Metadata Profile from Folder(s)]** , selecteer de map of meerdere mappen waaruit u een profiel wilt verwijderen en klik op **[!UICONTROL Done]** .

   U kunt bevestigen dat het metagegevensprofiel niet meer wordt toegepast op een map omdat de naam niet langer onder de mapnaam wordt weergegeven.

#### Metagegevensprofielen uit mappen verwijderen via eigenschappen {#removing-metadata-profiles-from-folders-via-properties}

1. Klik op het logo [!DNL Experience Manager] en navigeer **[!UICONTROL Assets]** naar de map waaruit u een metagegevensprofiel wilt verwijderen.
1. Klik in de map op het vinkje om het te selecteren en klik vervolgens op **[!UICONTROL Properties]** .
1. Selecteer het tabblad **[!UICONTROL Metadata Profiles]**, selecteer **[!UICONTROL None]** in het vervolgkeuzemenu en klik op **[!UICONTROL Save]**. Mappen waaraan al een profiel is toegewezen, worden aangegeven door de naam van het profiel direct onder de mapnaam weer te geven.

## Tips en beperkingen {#best-practices-limitations}

* De metagegevensupdates via de gebruikersinterface wijzigen de eigenschappen van de metagegevens in de naamruimte `dc` . Wanneer updates via de HTTP-API worden uitgevoerd, veranderen de eigenschappen van de metagegevens in de naamruimte `jcr` . Zie [ hoe te om meta-gegevens bij te werken gebruikend HTTP API ](/help/assets/mac-api-assets.md#update-asset-metadata).

* Het CSV-bestand voor het importeren van metagegevens van elementen heeft een zeer specifieke indeling. Als u moeite en tijd wilt besparen en onbedoelde fouten wilt voorkomen, kunt u de CSV-bestanden beginnen te maken met de indeling van een geëxporteerd CSV-bestand.

* Wanneer u metagegevens importeert met een CSV-bestand, is de vereiste datumnotatie `YYYY-MM-DDThh:mm:ss.fff-00:00` . Als een andere notatie wordt gebruikt, worden de datumwaarden niet ingesteld. De datumnotaties van het geëxporteerde CSV-bestand met metagegevens hebben de indeling `YYYY-MM-DDThh:mm:ss-00:00` . Als u het wilt invoeren, zet het in het aanvaardbare formaat door de nanosecondewaarde toe te voegen die door `fff` wordt vermeld.

>[!MORELIKETHIS]
>
>* [ concepten van Meta-gegevens en begrip ](metadata-concepts.md).
>* [ geef meta-gegevenseigenschappen van veelvoudige inzamelingen ](manage-collections.md#editing-collection-metadata-in-bulk) uit
>* [ de invoer en de uitvoer van Meta-gegevens in Experience Manager Assets ](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/metadata-import-feature-video-use.html?lang=nl-NL)

<!-- TBD: Try filling the available information in these topics to the extent possible. As and when complete, publish the sections live.

## Where to find metadata of an asset or folder {#find-metadata}

What all methods to access asset Properties. More Details option in column view. Select asset and click Properties. Keyboard shortcut `p`. What else?

## Understand metadata handling in Experience Manager {#metadata-possibilities-with-aem}

Describe the journey of an assets' metadata. What all happens to metadata when an asset is added to Experience Manager.

## Add metadata to your digital assets {#add-metadata}

* To begin with, assets come with some metadata. The applications that create digital assets add some metadata to the assets created. Before uploading an asset to Experience Manager, you can edit and modify metadata using either the native application used to create an asset or using some other metadata editing application. When you upload an asset to Experience Manager, the metadata is processed.

* Link to PS, ID, AI, PDF, and so on, metadata-related help articles.

* Link to XMP writeback.

* Manually add (or edit) metadata in AEM in Properties page.

* Metadata profiles

* Any workflows related to metadata?

* Advanced topic: Add, edit, modify, process and writeback metadata of subassets.

## Metadata of assets, folders, and collections {#metadata-of-assets-folders-collections}

Similarities and differences between metadata of asset and folder. 

Link to metadata handling of collections.

## Modify metadata of an asset, folder, or collection {#modify-metadata}

* While creating assets: Native application.

* Before ingesting assets: Metadata editors

* After ingesting assets: Properties of an asset, folder, collection, and so on.

* Any supported programmatic method to bulk edit metadata directly in JCR?

## Modify metadata in bulk {#modify-metadata-in-bulk}

[!DNL Adobe Enterprise Manager Assets] lets you edit the metadata of multiple assets simultaneously so you can quickly propagate common metadata changes to assets in bulk. You can also edit the metadata for multiple collections in bulk.

Use the properties page to perform metadata changes on multiple assets or collections:

* Change metadata properties to a common value

* Add or modify tags

To customize the metadata properties page, including adding, modifying, deleting metadata properties, use the schema editor.

>[!NOTE]
>
>The bulk editing methods work for assets available in a folder or a collection. For the assets that are available across folders or match a common criteria, it is possible to [bulk update the metadata after searching](search-assets.md#metadataupdates).

1. In the [!DNL Assets] user interface, navigate to the location of the assets you want to edit.
1. Select the assets for which you want to edit common properties.
1. From the toolbar, click **[!UICONTROL Properties]** to open the properties page for the selected assets.

   >[!NOTE]
   >
   >When you select multiple assets, the lowest common parent form is selected for the assets. In other words, the properties page only displays metadata fields that are common across the properties pages of all the individual assets.

1. Modify the metadata properties for selected assets under the various tabs.
1. To view the metadata editor for a specific asset, deselect the remaining assets in the list. The metadata editor fields are populated with the metadata for the particular asset.

   >[!NOTE]
   >
   >* In the Properties page, you can remove assets from the asset list by deselecting them. The asset list has all the assets selected by default. The metadata for assets that you remove from the list is not updated.
   >
   >* At the top of assets list, select the check box near **[!UICONTROL Title]** to toggle between selecting the assets and clearing the list.

1. To select a different metadata schema for the assets, click **[!UICONTROL Settings]** from the toolbar, and select the desired schema.
1. Save the changes.
1. To append the new metadata with the existing metadata in fields that contain multiple values, select **[!UICONTROL Append mode]**. If you do not select this option, the new metadata replaces the existing metadata in the fields. click **[!UICONTROL Submit]**.

   >[!CAUTION]
   >
   >For single-value fields, the new metadata is not appended to the existing value in the field even if you select **[!UICONTROL Append mode]**.

-->
