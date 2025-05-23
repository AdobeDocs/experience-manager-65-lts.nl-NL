---
title: Aangepaste speciale tekens in Correspondentenbeheer
description: Leer hoe u aangepaste speciale tekens toevoegt in Correspondentiebeheer.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: f4f563ed-ccdd-49f6-885d-48f97a958a8e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '653'
ht-degree: 0%

---

# Aangepaste speciale tekens in Correspondentenbeheer{#custom-special-characters-in-correspondence-management}

## Overzicht {#overview}

Correspondence Management biedt ingebouwde standaardondersteuning voor 210 speciale tekens die u eenvoudig in letters kunt invoegen.

U kunt bijvoorbeeld de volgende speciale tekens invoegen:

* Valutasymbolen zoals €, ¥ en £
* Wiskundige symbolen zoals A, Ö, ∂ en ^
* Interpunctiesymbolen als ‟ en &quot;

U kunt speciale tekens in letters invoegen:

* In de [ tekstredacteur ](/help/forms/using/document-fragments.md#createtext)
* In een [ editable, gealigneerde module in een correspondentie ](../../forms/using/create-correspondence.md#managecontent)

![ speciCharacsinlinemodule ](assets/specialcharactersinlinemodule.png)

De beheerder kan ondersteuning voor meer/aangepaste speciale tekens toevoegen door deze aan te passen. In dit artikel vindt u instructies voor het toevoegen van ondersteuning voor extra, aangepaste speciale tekens.

## Ondersteuning toevoegen of wijzigen voor aangepaste speciale tekens in Correspondentenbeheer {#creatingfolderstructure}

Gebruik de volgende stappen om ondersteuning voor aangepaste speciale tekens toe te voegen:

1. Ga naar `https://'[server]:[port]'/[ContextPath]/crx/de` en meld u aan als beheerder.
1. Maak in de map apps een map met de naam **[!UICONTROL specialcharacters]** met een pad/structuur die lijkt op de map specialcharacters (in de map textEditorConfig onder libs):

   1. Klik met de rechtermuisknop op de **specicharacters** omslag bij de volgende weg en selecteer **Knoop van de Bedekking**:

      `/libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters`

   1. Zorg ervoor dat het dialoogvenster Overlay-knooppunt de volgende waarden heeft:

      **Weg:** /libs/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters

      **Plaats van de Bedekking:** /apps/

      **de Types van Knoop van de Gelijke:** Gecontroleerd

      >[!NOTE]
      >
      >Wijzig de /libs tak niet. Alle wijzigingen die u aanbrengt, kunnen verloren gaan, omdat deze vertakking mogelijk wordt gewijzigd wanneer u:
      >
      >
      >
      >    * Upgrade op uw exemplaar
      >    * Een hotfix toepassen
      >    * Een functiepakket installeren
      >
      >

   1. Klik **O.K.** en klik dan **sparen allen**. De map met speciale tekens wordt gemaakt in het opgegeven pad.

      Controleer na het maken van de overlay de structuurcodes van het knooppunt. Elk knooppunt dat wordt gemaakt in /apps met behulp van de overlay, moet dezelfde klasse en eigenschappen hebben als gedefinieerd in /libs voor dat knooppunt. Als een eigenschap of tag ontbreekt in de nodestructuur onder de locatie /apps, synchroniseert u de tags met het corresponderende knooppunt in /libs.

1. Controleer of het knooppunt **[!UICONTROL textEditorConfig]** de volgende eigenschappen en waarden heeft:

   | Naam | Type | Waarde |
   |---|---|---|
   | cmConfigurationType | String | cmTextEditorConfiguration |
   | cssPath | String | /libs/fd/cm/ma/gui/components/admin/createasset/textcontrol/clientlibs/textcontrol |

1. Klik met de rechtermuisknop op de **[!UICONTROL specialcharacters]** omslag bij de volgende weg en selecteer **creeer > de Knoop van het Kind** en klik dan **sparen allen**:

   /apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters/&lt;YourChildNode>

1. Vernieuw de Teksteditor\Create Correspondence UI page. Het knooppunt dat u hebt toegevoegd, is het laatste in de lijst met speciale tekens in de gebruikersinterface.
1. Klik **sparen allen**.
1. Eventuele wijzigingen in de speciale tekens:

<table>
 <tbody>
  <tr>
   <td><strong>Aan...</strong></td>
   <td><strong>Voer de volgende stappen uit</strong></td>
  </tr>
  <tr>
   <td>Een aangepast speciaal teken toevoegen</td>
   <td>
    <ol>
     <li>Voeg een onderliggende node toe onder "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters" met verplichte eigenschappen.</li>
     <li>Klik op Alles opslaan</li>
     <li>Vernieuw de Teksteditor\Create Correspondence UI zodat u de wijzigingen kunt zien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>De eigenschappen van een bestaand speciaal teken bijwerken</td>
   <td>
    <ol>
     <li>Bedek het knooppunt dat moet worden bijgewerkt zoals hierboven beschreven en controleer de tags en klassen.</li>
     <li>Wijzig alle waarden, zoals bijschrift, waarde, endValue en multipleCaption. </li>
     <li>Klik op Alles opslaan. </li>
     <li>Vernieuw de Teksteditor\Create Correspondence UI zodat u de wijzigingen kunt zien.</li>
    </ol> </td>
  </tr>
  <tr>
   <td>Een speciaal teken verbergen</td>
   <td>
    <ol>
     <li>Plaats het knooppunt dat u wilt verbergen onder "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters"</li>
     <li>Voeg de eigenschap sling:hideResource (Boolean) toe aan het knooppunt (onder apps) dat moet worden verborgen. </li>
     <li>Klik op Alles opslaan. </li>
     <li>Vernieuw de Redacteur van de Tekst \ creeer Correspondentie UI zodat kunt u de veranderingen zien.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Meerdere speciale tekens verbergen</td>
   <td>
    <ol>
     <li>Voeg de eigenschap "sling:hideChildren (String of String[])" toe aan "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters". </li>
     <li>Voeg knooppuntnamen (speciale tekens die moeten worden verborgen) toe als waarden voor de eigenschap "sling:hideChildren". </li>
     <li>Klik op Alles opslaan. </li>
     <li>Vernieuw de Redacteur van de Tekst \ creeer Correspondentie UI zodat kunt u de veranderingen zien.<br /> </li>
    </ol> </td>
  </tr>
  <tr>
   <td>Speciale tekens ordenen</td>
   <td>
    <ol>
     <li>Voeg een onderliggende node toe onder "/apps/fd/cm/ma/gui/configuration/textEditorConfig/specialcharacters" met verplichte eigenschappen. </li>
     <li>Voeg de eigenschap "sling:orderBefore (String)" toe aan het nieuwe onderliggende knooppunt. </li>
     <li>Voeg de knooppuntnaam toe als waarde vóór het toegevoegde speciale karakter moet worden getoond. </li>
     <li>Klik op Alles opslaan. </li>
     <li>Vernieuw de Redacteur van de Tekst \ creeer Correspondentie UI zodat kunt u de veranderingen zien.<br /> </li>
    </ol> </td>
  </tr>
 </tbody>
</table>
