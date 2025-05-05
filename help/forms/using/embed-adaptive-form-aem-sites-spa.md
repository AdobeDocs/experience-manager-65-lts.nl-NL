---
title: Een adaptief formulier of interactieve communicatie insluiten in AEM Sites-toepassing voor één pagina
description: Aangepaste formulieren of interactieve communicatie insluiten in AEM Sites-pagina's. Gebruikers kunnen formulieren invullen en verzenden zonder de sitepagina te verlaten.
topic-tags: author, interactive-communications
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Adaptive Forms
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 2ac51487-42e0-4b8a-b224-2858f26e85ef
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1107'
ht-degree: 0%

---

# Een adaptief formulier of interactieve communicatie insluiten in AEM Sites-toepassing voor één pagina{#embed-an-adaptive-form-or-interactive-communication-in-aem-sites-single-page-application}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Overzicht {#overview}

Met AEM Forms kunnen ontwikkelaars van formulieren adaptieve formulieren en interactieve communicatie naadloos insluiten in een AEM Sites Single Page Application (SPA). Het ingesloten adaptieve formulier en de interactieve communicatie zijn volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd communiceren met het adaptieve formulier of de interactieve communicatie.

In AEM Sites Één enkele Toepassing van de Pagina, kunt u een adaptieve vorm of een Interactieve Mededeling toevoegen gebruikend de [ component van de Container van AEM Forms SPA ](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) [.](../../forms/using/embed-adaptive-form-aem-sites-spa.md#af-component) Het is een AEM Forms-component voor AEM Sites SPA&#39;s die u kunt toevoegen aan uw sitepagina.

Voor informatie over het inbedden van een adaptieve vorm in een niet-SPA AEM Sites, zie [ een adaptieve vorm of interactieve mededeling in de pagina van AEM Sites ](/help/forms/using/embed-adaptive-form-aem-sites.md) inbedden.

## Vereisten {#prerequisites}

Als u een adaptief formulier of interactieve communicatie wilt insluiten in een AEM-site SPA met behulp van de AEM Forms SPA Container-component, moet u controleren of u het volgende hebt geïnstalleerd:

* Java SE Development Kit 8 of hoger
* Apache Maven 3.3.1 of hoger
* AEM-auteur-exemplaar
* [ AEM Forms 6.4.2 toe:voegen-op pakket ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) op auteursinstantie

## AEM Forms SPA-containercomponent installeren {#install-aem-forms-spa-container-component}

Voer de volgende stappen uit installeert de component van de Container van AEM Forms SPA:

1. [ Kloon of download de component van AEM Forms voor SPA ](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa).
1. Installeer de AEM Forms-component voor SPA. De instructies om de component te installeren zijn beschikbaar in het {[&#128279;](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa#aem-form-component) dossier 0} README.md.

   De component omvat de component van het a [ steekproefReact ](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component) die kan worden gebruikt om de containercomponent van het KUUROORD met een React-Gebaseerd project van het KUUROORD te integreren.

1. [ Kloon of download een React-Gebaseerd project van het KUUROORD ](https://github.com/adobe/aem-sample-we-retail-journal).
1. Integreer de containercomponent van het KUUROORD met een React-Gebaseerd project van het KUUROORD gebruikend de instructies beschikbaar in het {[&#128279;](https://github.com/Adobe-Marketing-Cloud/aem-forms/tree/master/forms-spa/react-component#aem-form-react-component-for-spa---editor) dossier 0} README.md.

   Nadat u de AEM Forms SPA Container-component hebt geïnstalleerd en de component hebt geïntegreerd met een React-based SPA-project, kunt u adaptieve formulieren en interactieve communicatie insluiten in de AEM Sites-pagina.

## Een adaptief formulier of interactieve communicatie insluiten {#af-component}

Een adaptief formulier of interactieve communicatie insluiten met AEM Forms for SPA Container-component:

1. Open de AEM-sitepagina in de bewerkingsmodus waarin u een adaptief formulier of interactieve communicatie wilt insluiten.
1. Tussenvoegsel de **Vorm van AEM voor de component van het KUUROORD** op de pagina gebruikend om het even welke volgende opties:

   * Selecteer de lay-outcontainer op de pagina van Plaatsen, selecteer **+** en selecteer de **Vorm van AEM voor de component van het KUUROORD**.

   * Van het browser paneel van de Component, sleep-daling de **Vorm van AEM voor SPA** component op de pagina.
   * Zoek een adaptief formulier of interactieve communicatie in de Assets-browser en sleep het naar de Sites-pagina. Het sluit de vorm in een AEM Forms voor de componentencontainer van SPA in.

   >[!NOTE]
   >
   >Het weergeven van meerdere AEM Forms SPA Container-componenten op een pagina wordt niet ondersteund. U kunt de veelvoudige Container van AEM Forms SPA op een pagina hebben maar slechts één component tegelijkertijd wordt teruggegeven. Zorg ervoor dat slechts één component zichtbaar is op een pagina om discrepanties te voorkomen.

1. Selecteer de ingebedde component van de Container van AEM Forms SPA in de plaatspagina, en selecteer dan ![ settings_icon ](assets/settings_icon.png) op de actiebar. Het **geeft de Container van AEM Forms SPA uit** dialoog opent.
1. In **geef de Container van AEM Forms** dialoog uit, specificeer het volgende:

   * **Type van Activa:** selecteer het type van activa om in te bedden. De opties zijn **Aangepaste Vorm** en **Interactieve Communicatie**

   * **Weg van Activa**: doorblader en selecteer de adaptieve vorm of de Interactieve Communicatie om in te bedden. Het veld wordt automatisch ingevuld als een adaptief formulier of interactieve communicatie wordt ingevoegd via de Assets-browser.
   * **Kanaal** (Interactieve Communicatie slechts): Selecteer het type van interactief kanaal om in te bedden. De opties zijn **Kanaal van het Web** en **Kanaal van de Druk**.

   * **Thema**: Selecteer een thema dat het stileren voor componenten van uw adaptieve vorm of Interactieve Communicatie bepaalt. Stijlen omvat vormgevingseigenschappen zoals letterstijl, achtergrondkleur, afmetingen en uitlijning.

1. Selecteer ![ done_icon ](assets/done_icon.png) om de montages te bewaren. Het adaptieve formulier of de interactieve communicatie is nu ingesloten in de pagina.

## Ingesloten adaptief formulier en interactieve communicatie publiceren {#publish-embedded-adaptive-form-and-interactive-communication}

Overweeg de volgende scenario&#39;s voor het publiceren van een ingesloten element (adaptief formulier of interactieve communicatie) op de AEM Sites-pagina:

* Als u de AEM Sites-pagina voor het eerst publiceert en een ingesloten adaptief formulier of interactieve communicatie bevat, publiceert u de pagina Sites en het ingesloten element.
* Als u alleen het ingesloten adaptieve formulier of de interactieve communicatie op een gepubliceerde sitepagina hebt gewijzigd, publiceert u het oorspronkelijke element en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde pagina Sites bevat een verwijzing naar het element en de pagina hoeft niet opnieuw te worden gepubliceerd.
* Als u de pagina Sites en het ingesloten adaptieve formulier of Interactieve communicatie hebt gewijzigd, publiceert u de pagina Sites en het ingesloten element opnieuw.

## Ingesloten adaptief formulier en interactieve communicatie wijzigen {#modify-embedded-adaptive-form-and-interactive-communication}

Op de AEM-sitepagina wordt een verwijzing naar het adaptieve formulier en de interactieve communicatie bijgehouden in de AEM Forms Container. Daarom blijven alle configuraties en eigenschappen, zoals het thema, de stijlen en de verzendactie, die in het oorspronkelijke adaptieve formulier en de interactieve communicatie zijn geconfigureerd, behouden in het ingesloten adaptieve formulier en de interactieve communicatie.

Voer een van de volgende handelingen uit als u een configuratie of eigenschap van het ingesloten adaptieve formulier en interactieve communicatie wilt wijzigen.

* Open het oorspronkelijke formulier in adaptieve formulieren of Interactieve communicatie in de respectievelijke editors en wijzig deze.
* Selecteer de adaptieve vorm of de Interactieve Communicatie van binnen de pagina van Plaatsen op geef wijze uit en selecteer dan **uitgeven in een nieuw venster**. Het oorspronkelijke formulier wordt geopend in de bewerkingsmodus.

## Overwegingen en beste praktijken {#considerations-and-best-practices}

Houd rekening met de volgende punten wanneer u adaptieve formulieren insluit in AEM-sitepagina&#39;s:

* Koptekst en voettekst in het oorspronkelijke formulier worden niet opgenomen in het ingesloten formulier.
* Concepten en opmerkingen van gebruikers met ingesloten formulieren worden ondersteund en kunnen worden weergegeven op de tabbladen Concepten en Verzonden Forms op de portal Formulieren.
* De verzendactie die op het oorspronkelijke formulier is geconfigureerd, blijft behouden in het ingesloten formulier.
* De ervaring die het richten en A/B tests die op de originele vorm worden gevormd werkt niet in de ingebedde vorm richten. U kunt echter wel de ervaring gebruiken die u op de pagina Sites hebt geselecteerd om verschillende formulieren weer te geven op basis van gebruikersprofielen.
* Als u Adobe Analytics hebt geconfigureerd voor het oorspronkelijke formulier, worden de analysegegevens van het ingesloten formulier vastgelegd in Adobe Analytics. Het is echter niet beschikbaar in het rapport Formulieranalyse.
