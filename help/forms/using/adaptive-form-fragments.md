---
title: Adaptieve formulierfragmenten
description: Aangepaste formulieren bieden een mechanisme voor het maken van een formuliersegment, zoals een deelvenster of een groep velden, zoals het in elk adaptief formulier wordt gebruikt. U kunt een bestaand deelvenster ook opslaan als fragment.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
feature: Adaptive Forms,Foundation Components
discoiquuid: 1a32eb24-db3b-4fad-b1c7-6326b5af4e5e
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 7da165ac-2039-4ac8-810d-fbe6f771453a
source-git-commit: c03b3e3e4526530715718b68804ac26d2562bdb8
workflow-type: tm+mt
source-wordcount: '2353'
ht-degree: 0%

---

# Adaptieve formulierfragmenten{#adaptive-form-fragments}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-core-components/create-an-adaptive-form-on-forms-cs/adaptive-form-fragments-core-components.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

Hoewel elk formulier voor een bepaald doel is ontworpen, zijn er in de meeste vormen enkele gangbare segmenten, zoals het verstrekken van persoonlijke gegevens zoals naam en adres, familiedetails en inkomstengegevens. Formulierontwikkelaars moeten deze algemene segmenten telkens maken wanneer een nieuw formulier wordt gemaakt.

Adaptieve formulieren bieden een handig mechanisme om slechts eenmaal een formuliersegment als een deelvenster of een groep velden te maken en deze in adaptieve formulieren opnieuw te gebruiken. Deze herbruikbare en standalone segmenten worden de Adaptieve Fragmenten van de Vorm genoemd.

>[!NOTE]
>
> U kunt uw fragmentervaring voor gebruikers met [ gemakkelijk aanpassen vormt dialoog en de dialoog van het Ontwerp van de component van het Fragment van de Vorm ](https://experienceleague.adobe.com/nl/docs/experience-manager-core-components/using/adaptive-forms/adaptive-forms-components/adaptive-form-fragment).

## Een fragment maken {#create-a-fragment}

U kunt een adaptief formulierfragment helemaal opnieuw maken of een deelvenster in een bestaand adaptief formulier opslaan als fragment.

### Geheel fragment maken {#create-fragment-from-scratch}

1. Logboek in de auteursinstantie van AEM Forms in https://[*hostname*]:[*haven*] /aem/forms.html.
1. Klik **creëren > het AanpassingsFragment van de Vorm**.
1. Geef een titel, naam, beschrijving en tags voor het fragment op.

   >[!NOTE]
   >
   >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

1. Klik om het **Model van de Vorm** lusje te openen, en van **Uitgezocht van** drop-down menu, selecteer één van de volgende modellen voor het fragment:

   * **niets**: Specificeert om het fragment van kras tot stand te brengen zonder enig vormmodel te gebruiken.

     >[!NOTE]
     >
     > In Adaptief Forms op basis van kerncomponenten kunt u één formulierfragment meerdere keren gebruiken in een formulier. Deze ondersteunt zowel op geen gebaseerde als op schema gebaseerde formulierfragmenten.

   * **Malplaatje van de Vorm**: Specificeert om het fragment tot stand te brengen gebruikend een malplaatje XDP dat aan AEM Forms wordt geupload. Selecteer de juiste XDP-sjabloon als het formuliermodel voor het fragment.

   ![ Creërend een adaptieve vorm gebruikend vormmalplaatje als model ](assets/form-template-model.png)

   De subformulieren die als fragmenten zijn gemarkeerd in de geselecteerde formuliersjabloon, worden ook weergegeven. U kunt een subformulier voor adaptief formulierfragment selecteren in de vervolgkeuzelijst.

   ![ Uitgezochte subforms van het gespecificeerde vormmalplaatje ](assets/fragment-subform.png)

   Daarnaast kunt u een adaptief formulierfragment maken met subformulieren die niet zijn gemarkeerd als fragmenten in de formuliersjabloon door de SOM-expressie voor het subformulier op te geven in de vervolgkeuzelijst.

   * **Schema van XML**: Specificeert om het fragment tot stand te brengen gebruikend een schema van XML dat aan AEM Forms wordt geupload. U kunt een van de beschikbare XML-schema&#39;s uploaden of selecteren als het formuliermodel voor het fragment.

   ![ creeer een adaptief vormfragment dat op een schema van XML als model wordt gebaseerd ](assets/xml-schema-model.png)

   U kunt ook een adaptief formulierfragment maken door in de vervolgkeuzelijst een complexType te selecteren dat aanwezig is in het geselecteerde schema.

   ![ selecteer een complex type van het gespecificeerde het schemamodel van XML ](assets/complex-type.png)

1. Klik **creëren** en klik dan **Open** om het fragment, met een standaardmalplaatje, op uit te geven wijze te openen.

In de bewerkingsmodus kunt u elke adaptieve formuliercomponent van het AEM-hulpstuk naar het fragment slepen en neerzetten. Voor informatie over adaptieve vormcomponenten, zie [ Inleiding aan auteursadaptieve vormen ](../../forms/using/introduction-forms-authoring.md).

Als u bovendien een XML-schema of XDP-formuliersjabloon hebt geselecteerd als het formuliermodel voor uw fragment, wordt een nieuw tabblad met de hiërarchie van het formuliermodel weergegeven in de zoeker naar inhoud. Hiermee kunt u formuliermodelelementen naar het fragment slepen en neerzetten. De toegevoegde formuliermodelelementen worden geconverteerd naar formuliercomponenten, terwijl de oorspronkelijke eigenschappen van de gekoppelde XDP of XSD behouden blijven.

### Deelvenster opslaan als een fragment {#save-panel-as-a-fragment}

1. Open een adaptief formulier met het deelvenster dat u wilt opslaan als adaptief formulierfragment.
1. Klik op **[!UICONTROL Save as Fragment]** op de werkbalk van het deelvenster. Het dialoogvenster Opslaan als fragment wordt geopend.

   >[!NOTE]
   >
   >Als het deelvenster dat u opslaat als fragment een onderliggend deelvenster bevat, worden deze opgenomen in het resulterende fragment.

1. Geef in het dialoogvenster Fragment maken de volgende informatie op:

   * **Naam**: Naam van het fragment. De standaardwaarde is de elementnaam van het deelvenster. Het is een verplicht veld.

     >[!NOTE]
     >
     >Zorg ervoor dat u een unieke naam voor het fragment opgeeft. Als er een ander fragment met dezelfde naam bestaat, kan het fragment niet worden gemaakt.

   * **Titel**: Titel van het fragment. De standaardwaarde is de titel van het deelvenster.

   * **Beschrijving**: Beschrijving van het fragment.

   * **Markeringen**: De meta-gegevens van markeringen voor het fragment.

   * **Weg van het Doel**: De weg van de Bewaarplaats waar het fragment wordt bewaard. Als u geen pad opgeeft, wordt een knooppunt met dezelfde naam als dat van het fragment gemaakt naast het knooppunt dat het adaptieve formulier bevat. Het fragment wordt opgeslagen in dit knooppunt.

   * **Model van de Vorm**: Afhankelijk van het vormmodel voor de adaptieve vorm, toont dit gebied het **Schema van XML**, **Malplaatje van de Vorm**, of **niets**. Het is een niet-bewerkbaar veld.

   * **Basis van het Model van het Fragment**: Verschijnt slechts in op XSD-Gebaseerde adaptieve vormen. Hiermee geeft u de basis voor het fragmentmodel op. U kunt **kiezen/** of het complexe type XSD van drop-down. U kunt het fragment alleen opnieuw gebruiken in een ander adaptief formulier als u het complexe type selecteert als hoofdknooppunt van het fragmentmodel.
Als u **&#x200B;**&#x200B;als hoofdmap van het fragmentmodel kiest, is de volledige XSD-structuur van het basismodel zichtbaar op het tabblad van het adaptieve formuliergegevensmodel. Voor de hoofdmap van een complex type fragmentmodel zijn alleen de onderliggende elementen van het geselecteerde complexe type zichtbaar op het tabblad van het adaptieve formuliergegevensmodel. Als u een fragment creeert en een complex type als **Basis van het Model van het Fragment** kiest, kunt u het gebruiken waar dat complexe type, of binnen de zelfde vorm of over veelvoudige vormen wordt gebruikt.

   * **XSD Ref**: Verschijnt slechts in op XSD-Gebaseerde adaptieve vormen. De locatie van het XML-schema wordt weergegeven.

   * **XDP Verwijzing**: Verschijnt slechts in op XDP-Gebaseerde adaptieve vormen. De locatie van de XDP-formuliersjabloon wordt weergegeven.

   ![ sparen-fragment ](assets/save-fragment.png)

   Dialoogvenster Opslaan als fragment

1. Klik **OK**.

   Het deelvenster wordt opgeslagen op de opgegeven of standaardlocatie in de opslagplaats. In het aangepaste formulier wordt het deelvenster vervangen door een opname van het fragment. Zoals hieronder wordt weergegeven, worden het deelvenster Algemene informatie en de onderliggende deelvensters Persoonlijke gegevens en Adres als een fragment opgeslagen.

   Als u het fragment wilt bewerken, klikt u op **[!UICONTROL Edit Asset]** op de werkbalk van het deelvenster. Het fragment wordt in de bewerkingsmodus op een nieuw tabblad of in een nieuw venster geopend.

   ![ Uitgevend fragment ](assets/edit-fragment.png)

## Werken met fragmenten {#working-with-fragments}

### Fragmentweergave configureren {#configure-fragment-appearance}

Elk fragment dat u in adaptieve formulieren invoegt, wordt weergegeven als een voorlopige afbeelding. De plaatsaanduiding bevat titels van maximaal tien onderliggende deelvensters in het fragment. U kunt AEM Forms zo configureren dat het volledige fragment wordt weergegeven in plaats van de voorlopige afbeelding.

Voer de volgende stappen uit zodat u volledige fragmenten in formulieren kunt weergeven:

1. Ga naar de configuratiepagina van de Webconsole van AEM in https:[*gastheer*]:[*haven*]/system/console/configMgr.

1. Zoek en selecteer **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om het in uitgeeft wijze te openen.
1. Schakel het selectievakje **[!UICONTROL Enable Placeholder in place of Fragment]** uit zodat u volledige fragmenten kunt weergeven in plaats van de voorlopige afbeelding.

### Een fragment invoegen in een adaptief formulier {#insert-a-fragment-in-an-adaptive-form}

De adaptieve formulierfragmenten die u maakt, worden weergegeven op het tabblad Adaptieve formulierfragmenten van de zoeker naar AEM-inhoud. Een adaptief formulierfragment invoegen in een adaptief formulier:

1. Open het adaptieve formulier in de bewerkingsmodus waarin u een adaptief formulierfragment wilt invoegen.
1. Klik **Assets** ![ activa-browser ](assets/assets-browser.png) in sidebar. In activa browser, uitgezochte **Adaptieve Fragmenten van de Vorm** van drop-down.

   U kunt er ook voor kiezen om alle adaptieve formulierfragmenten of filters weer te geven op basis van het formuliermodel (Formuliersjabloon, XML-schema of Standaard).

1. Sleep een adaptief formulierfragment naar het adaptieve formulier.

   >[!NOTE]
   >
   >Het adaptieve formulierfragment is niet ingeschakeld voor ontwerpen vanuit het adaptieve formulier. Bovendien kunt u een XSD-fragment niet gebruiken in een JSON-gebaseerd adaptief formulier en omgekeerd.

Het adaptieve formulierfragment wordt door verwijzing ingevoegd in het adaptieve formulier en wordt gesynchroniseerd met het standalone adaptieve formulierfragment. Dit betekent dat wanneer u het adaptieve formulierfragment bijwerkt, de wijzigingen worden doorgevoerd in alle adaptieve formulieren waarin het fragment wordt gebruikt.

### Een fragment in adaptieve vorm insluiten {#embed-a-fragment-in-adaptive-form}

U kunt verkiezen om een adaptief vormfragment in een adaptieve vorm in te bedden door **te klikken bedt Activa: &lt;*fragmentName*>** knoop op de paneeltoolbar van het toegevoegde fragment, zoals aangetoond in het volgende voorbeeldbeeld.

![ bed een vormfragment in adaptieve vorm in ](assets/embed-fragment.png)

>[!NOTE]
>
>Het ingesloten fragment is niet meer gekoppeld aan het zelfstandige fragment. U kunt de componenten in het ingesloten fragment bewerken vanuit het adaptieve formulier.

### Fragmenten in fragmenten gebruiken {#using-fragments-within-fragments}

U kunt geneste adaptieve formulierfragmenten maken, wat betekent dat u een fragment naar een ander fragment kunt slepen en neerzetten en dat u een geneste fragmentstructuur kunt hebben.

### Fragmenten wijzigen {#change-fragments}

U kunt een adaptief vormfragment door een ander fragment vervangen of veranderen door het **Uitgezochte bezit van de Activa van het Fragment** in de Edit componentendialoog voor een adaptief paneel van het vormfragment te gebruiken.

### Document van record genereren voor adaptief formulierfragment {#generate-DOR-for-fragments}

Met Document of Record (DOR) kunt u gegevens van uw formulieren in de afdruk- of documentindeling bewaren. Op die manier kunt u op elk gewenst moment later informatie over uw klanten bijhouden en u kunt het Document of Record ook gebruiken om formulieren en inhoud samen te archiveren in PDF-indeling. [ Leer om document van verslag voor de Adaptieve fragmenten van de Vorm ](/help/forms/using/generate-document-of-record-for-non-xfa-based-adaptive-forms.md) te produceren.

### Een formulierfragment meerdere keren gebruiken in een adaptief formulier {#using-form-fragment-mutiple-times-in-af}

U kunt een formulierfragment op basis van een schema meerdere keren gebruiken in een adaptief formulier om gegevens uniek op te slaan voor elk formulierfragmentveld. U kunt bijvoorbeeld een fragment van een adresformulier gebruiken om adresgegevens te verzamelen voor permanente communicatie en het weergeven van levende adressen in een aanvraagformulier voor een lening.

![ gebruikend veelvoudige fragment in adaptieve vorm ](/help/forms/using/assets/using-multiple-fragment-af.gif)

>[!NOTE]
>
> * Als u op geen gebaseerde formulierfragmenten meerdere keren gebruikt in een adaptief formulier, worden gegevens gesynchroniseerd tussen de fragmentvelden. Het probleem met gegevenssynchronisatie doet zich niet voor in op kerncomponenten gebaseerde formulierfragmenten, waar u een fragment op basis van een schema of een fragment op basis van geen meerdere keren in een formulier kunt gebruiken.

## Automatische toewijzing van fragmenten voor gegevensbinding {#auto-mapping-of-fragments-for-data-binding}

Wanneer u een adaptief formulierfragment maakt met een XFA-formuliersjabloon of een XSD-complex type en het fragment naar een adaptief formulier sleept, wordt het XFA-fragment of het XSD-complexe type automatisch vervangen door het bijbehorende adaptieve formulierfragment waarvan de hoofdmap van het fragmentmodel is toegewezen aan het XFA-fragment of het XSD-complexe type.

U kunt het fragmentelement en de bijbehorende bindingen wijzigen in het dialoogvenster Component bewerken.

>[!NOTE]
>
>U kunt een gebonden adaptief formulierfragment ook slepen en neerzetten vanuit de bibliotheek met adaptief formulierfragment in de zoekfunctie voor AEM-inhoud en de juiste bindingsverwijzing opgeven in het dialoogvenster Component bewerken van het adaptieve deelvenster voor formulierfragmenten.

## Fragmenten beheren {#manage-fragments}

U kunt verschillende bewerkingen op adaptieve formulierfragmenten uitvoeren met de gebruikersinterface van AEM Forms.

1. Ga naar `https://[hostname]:'port'/aem/forms.html` .

1. Klik **Uitgezocht** in de toolbar van UI van AEM Forms en selecteer een adaptief vormfragment. De werkbalk bevat de volgende bewerkingen die u kunt uitvoeren op het geselecteerde adaptieve formulierfragment.

<table>
 <tbody>
  <tr>
   <td><p><strong>Bewerking</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>Openen</p> </td>
   <td><p>Hiermee opent u het geselecteerde adaptieve formulierfragment in de bewerkingsmodus. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Eigenschappen weergeven</p> </td>
   <td><p>Hiermee opent u het deelvenster Eigenschappen. In het deelvenster Eigenschappen kunt u eigenschappen weergeven en bewerken, een voorvertoning genereren en een miniatuurafbeelding voor het geselecteerde fragment uploaden. Voor meer informatie, zie <a href="../../forms/using/manage-form-metadata.md" target="_blank"> het Leiden meta-gegevens </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Kopiëren</p> </td>
   <td><p>Hiermee kopieert u het geselecteerde fragment. De knop Plakken wordt weergegeven op de werkbalk. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Downloaden</p> </td>
   <td><p>Hiermee downloadt u het geselecteerde fragment. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Voorvertoning</p> </td>
   <td><p>Hiermee kunt u een voorvertoning van het fragment weergeven als een HTML of een aangepaste voorvertoning door gegevens uit een XML-bestand samen te voegen met het fragment. Voor meer informatie, zie <a href="/help/forms/using/previewing-forms.md" target="_blank"> Previewing een vorm </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Revisie starten/Revisie beheren</p> </td>
   <td><p>Hiermee kunt u een revisie van het geselecteerde fragment starten en beheren. Voor meer informatie, zie <a href="../../forms/using/create-reviews-forms.md" target="_blank"> Creërend en het leiden overzichten </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Woordenboek maken</p> </td>
   <td><p>Genereert een woordenboek voor het lokaliseren van het geselecteerde fragment. Voor meer informatie, zie <a href="/help/forms/using/lazy-loading-adaptive-forms.md" target="_blank"> Localizing adaptive forms </a>.<br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Publiceren/Publiceren ongedaan maken</p> </td>
   <td><p>Hiermee publiceert u het geselecteerde fragment of maakt u de publicatie ervan ongedaan. <br /> <br /> </p> </td>
  </tr>
  <tr>
   <td><p>Verwijderen</p> </td>
   <td><p>Hiermee verwijdert u het geselecteerde fragment. <br /> <br /> </p> </td>
  </tr>
 </tbody>
</table>

## Aangepaste formulieren met fragmenten lokaliseren {#localizing-adaptive-form-containing-fragments}

Als u een adaptief formulier met adaptieve formulierfragmenten wilt lokaliseren, moet u het fragment en het formulier afzonderlijk lokaliseren. Het is de bedoeling een fragment één keer te lokaliseren en opnieuw te gebruiken in meerdere adaptieve formulieren.

>[!NOTE]
>
>De lokalisatietoetsen in het fragment worden niet weergegeven in het XLIFF-bestand voor een adaptief formulier.

## Belangrijke punten die u moet onthouden wanneer u werkt met fragmenten {#key-points-to-remember-when-working-with-fragments}

* Zorg ervoor dat de fragmentnaam uniek is. Het fragment kan niet worden gemaakt als er een bestaand fragment met dezelfde naam bestaat.
* Als u in een op XDP gebaseerd adaptief formulier een deelvenster opslaat als fragment dat een ander XDP-fragment bevat, wordt het resulterende fragment automatisch gebonden aan het onderliggende XDP-fragment. Als er een adaptief formulier op basis van XSD is, wordt het resulterende fragment gebonden aan de hoofdmap van het schema.
* Wanneer u een adaptief formulierfragment maakt, wordt in CRXDE Lite een fragmentknooppunt gemaakt, dat vergelijkbaar is met het knooppunt guideContainer voor een adaptief formulier.
* Een fragment in een adaptief formulier dat een ander formuliergegevensmodel gebruikt, wordt niet ondersteund. Een op XDP gebaseerd fragment wordt bijvoorbeeld niet ondersteund in een op XSD gebaseerde adaptieve vorm en omgekeerd.
* Adaptieve formulierfragmenten zijn beschikbaar voor gebruik via het tabblad Adaptieve formulierfragmenten in de zoekfunctie voor AEM-inhoud.
* Expressies, scripts of stijlen in een op zichzelf staand adaptief formulierfragment blijven behouden wanneer deze via verwijzing worden ingevoegd of in een adaptieve vorm worden ingesloten.
* U kunt een adaptief formulierfragment, dat via verwijzing wordt ingevoegd, niet bewerken vanuit een adaptief formulier. Als u het fragment wilt bewerken, bewerkt u het zelfstandige, adaptieve formulierfragment of sluit u het fragment in het adaptieve formulier in.
* Wanneer u een adaptief formulier publiceert, moet u de stand-alone adaptieve formulierfragmenten publiceren die door verwijzing in het adaptieve formulier zijn ingevoegd.
* Wanneer u een bijgewerkt adaptief formulierfragment opnieuw publiceert, worden de wijzigingen weerspiegeld in de gepubliceerde exemplaren van het adaptieve formulier waarin het fragment wordt gebruikt.
* Het adaptieve formulier met de component Verify ondersteunt geen anonieme gebruikers. Het wordt ook afgeraden de component Verify te gebruiken in een adaptief formulierfragment.
* (**Mac slechts**) om ervoor te zorgen dat de functionaliteit van vormfragmenten perfect in alle scenario&#39;s werkt, voeg de volgende ingang aan het /private/etc/hosts- dossier toe:
  `127.0.0.1 <Host machine>` **de machine van de Gastheer**: De machine van Apple Mac waarop AEM Forms wordt opgesteld.

## Referentiekaders {#reference-fragments}

Aangepaste formulierfragmenten voor verwijzingen die u kunt gebruiken om uw formulier te maken, zijn beschikbaar. Voor meer informatie, zie [ Fragmenten van de Verwijzing ](../../forms/using/reference-adaptive-form-fragments.md).
