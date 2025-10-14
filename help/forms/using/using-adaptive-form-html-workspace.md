---
title: Een adaptief formulier gebruiken in HTML Workspace
description: Leer hoe u in HTML Workspace een adaptief formulier gebruikt waarmee veldwerkers het formulier op hun apparaten kunnen openen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Workbench
role: User, Developer
exl-id: 3fdd889d-0984-457e-9b12-b55a4593a573
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '683'
ht-degree: 0%

---

# Een adaptief formulier gebruiken in HTML Workspace{#using-an-adaptive-form-in-html-workspace}

AEM Forms on JEE biedt de mogelijkheid om een adaptief formulier te gebruiken in HTML Workspace.

Omdat u tijdens het ontwerpen van het proces een XDP kunt selecteren, is de mogelijkheid om te bladeren vanuit een bestaande adaptieve AEM-opslagplaats toegevoegd. De mogelijkheid biedt de Process Designer de mogelijkheid om een adaptief formulier te configureren in Startpunt en Taken.

## Procesontwerpervaring {#process-design-experience}

Voer het volgende uit om het gebruik van adaptieve formulieren in procesontwerp mogelijk te maken:

* In Taak toewijzen en Startpunt kunt u naar een adaptief formulierelement in de CRX-opslagplaats bladeren wanneer u een formulierelement aan een taak toewijst.
* In het Werkbalkeigenschappenblad Taak/beginpunt toewijzen kunt u de werkbalk op hoofdniveau/globaal van een adaptief formulier verbergen.
* U kunt nieuwe actieprofielen gebruiken voor het renderen en verzenden van handelingen in adaptieve formulieren.

### LiveCycle-toepassing exporteren en importeren {#livecycle-application-export-and-import}

Omdat adaptieve formulieren zich in de AEM-opslagplaats bevinden, bevat de export van de LiveCycle-toepassing alleen de referenties voor gebruikte adaptieve formulieren. Daarom is het exporteren en importeren van LiveCycle-toepassing een proces dat uit twee stappen bestaat. De LiveCycle-toepassing bevat procesdefinities, enzovoort. Een afzonderlijk pakket met adaptieve formulieren wordt geëxporteerd als een ZIP-bestand uit AEM. Tijdens het importeren wordt de LiveCycle-toepassing geïmporteerd via Workbench en worden adaptieve formulieren geïmporteerd via AEM.

## Gebruikerservaring met adaptief formulier in HTML Workspace {#user-experience-of-adaptive-form-in-html-workspace}

HTML Workspace biedt naast de besturingselementen voor mobiele formulieren ook enkele adaptieve formulierspecifieke besturingselementen. Een gebruiker kan bijlagen toevoegen, opslaan, ondertekenen, verzenden en door de adaptieve formulieren navigeren in HTML Workspace wanneer de gebruiker een taak of beginpunt opent. Hieronder worden de specifieke kenmerken beschreven:

1. Als u bestanden wilt bijvoegen, gebruikt u Taakbijlagen, net als bij Mobile Forms. Een knop van het type bestandsbijlage van het adaptieve formulier is verborgen.

1. Om een adaptieve vorm te bewaren, klik **sparen**, zoals het geval in Mobiele Forms was. Elke knop voor het type Opslaan van het adaptieve formulier is verborgen.

1. Om een adaptieve vorm voor te leggen, gebruik **voorleggen** knoop of routeacties beschikbaar, zoals het geval in Mobiele Forms. De knop Verzendtype van het adaptieve formulier is verborgen.

1. **Adaptief Globale toolbarzicht van de Vorm**: Als het Proces Designer de globale/top-level toolbar verbergt, verschijnen de toolbar, en de knopen niet op adaptieve vormen.

1. **de navigatiecontroles van Workspace voor Aanpassings Forms**: De volgende/Vorige knopen zijn beschikbaar samen met sparen, voorleggen, en de knopen van de Actie van de Route voor een adaptieve vorm in HTML Workspace. Klik op de knop Volgende/Vorige om door de deelvensters met adaptieve formulieren in HTML Workspace te navigeren. De knoppen Volgende/Vorige bieden diepgaande navigatie, vergelijkbaar met navigatiebesturingselementen in de weergave Mobiel van adaptieve formulieren.

1. **eSign de Diensten en SamenvattingsComponent van AanpassingsVorm**: De Summiere component is niet operationeel in HTML Workspace. Met andere woorden, als een adaptief formulier een overzichtscomponent heeft, is het niet zichtbaar in de werkruimte. In plaats van Automatisch verzenden in de component E-sign, klikt de werkruimtefunctie de Submit of een routeactie in HTML Workspace. Nadat een document is ondertekend, is het zichtbaar als een vlak ondertekend document. Klik **voorleggen** of een routeactie zodat kunt u de taak of Punt van het Begin sluiten/voltooien.\
   Het ondertekende document wordt verzameld van de eSign-serviceserver en het data-xml-bestand wordt doorgestuurd naar de volgende stap in het proces.

## Stappen voor het gebruik van adaptieve formulieren in procesontwerp {#steps-to-use-adaptive-forms-in-process-design}

1. Open Adobe Experience Manager Forms Workbench.

1. Ga naar **Dossier > Nieuw > Toepassing** of gebruik de bestaande toepassing om een toepassing tot stand te brengen.

   ![&#x200B; creeer nieuwe toepassing &#x200B;](assets/create_new_appl.png)

   Toepassing maken

1. Maak een proces of gebruik een bestaand proces in de toepassing.

   ![&#x200B; creeer nieuw proces &#x200B;](assets/create_new_process.png)

   Proces maken

1. Creeer een Punt van het Begin of wijs Taak toe en klik het tweemaal.
1. Selecteer **[!UICONTROL use a CRX asset]** onder de sectie **[!UICONTROL Presentation & Data]** en klik op de ellipsen vóór het element.

   ![&#x200B; Gebruik een activa van CRX &#x200B;](assets/use_crx_asset.png)

   CRX-middelen gebruiken

1. Selecteer het adaptieve formulier dat is gemaakt via de gebruikersinterface van Assets beheren en klik op **[!UICONTROL OK]** .

   ![&#x200B; selecteer een adaptieve vorm &#x200B;](assets/selecting_form.png)

   Een adaptief formulier selecteren

   >[!NOTE]
   >
   >Voor details rond het creëren van een adaptieve vorm, zie [&#x200B; Creërend een adaptieve vorm &#x200B;](../../forms/using/creating-adaptive-form.md).
   >
   >
   >Voor details rond het creëren van een proces, zie [&#x200B; Creërend en het leiden processen &#x200B;](https://help.adobe.com/en_US/AEMForms/6.1/WorkbenchHelp/WS92d06802c76abadb-1cc35bda128261a20dd-7ff7.2.html).
