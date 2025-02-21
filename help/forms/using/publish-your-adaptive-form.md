---
title: 'Zelfstudie: uw adaptieve formulier publiceren'
description: Het adaptieve formulier publiceren als een AEM-pagina, het formulier insluiten op een AEM Sites-pagina of het adaptieve formulier insluiten in een externe webpagina
contentOwner: khsingh
topic-tags: introduction
docset: aem65
feature: Adaptive Forms
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '859'
ht-degree: 0%

---

# Zelfstudie: uw adaptieve formulier publiceren {#tutorial-publish-your-adaptive-form}

![ Hero-beeld ](do-not-localize/13-publish-your-adaptive-form-small.png)

Dit leerprogramma is een stap in [ creeert Uw Eerste AanpassingsVorm ](https://helpx.adobe.com/experience-manager/6-3/forms/using/create-your-first-adaptive-form.html) reeksen. U wordt aangeraden de reeks in chronologische volgorde te volgen om het volledige gebruik van de zelfstudie te begrijpen, uit te voeren en aan te tonen.

Nadat het aangepaste formulier gereed is, kunt u het publiceren en beschikbaar maken voor eindgebruikers. De eindgebruikers kunnen het gepubliceerde formulier openen op elk apparaat en in de internetbrowser. Wanneer een adaptief formulier wordt gepubliceerd, worden het formulier en de bijbehorende inhoud gekopieerd van een AEM-auteur naar een AEM-publicatie-exemplaar. Het formulier wordt via het publicatieexemplaar beschikbaar gesteld voor de eindgebruiker.

U kunt op de volgende manieren een adaptief formulier publiceren:

* [Het adaptieve formulier publiceren als een AEM-pagina](../../forms/using/publish-your-adaptive-form.md#publish-the-adaptive-form-as-an-aem-page)
* [Het adaptieve formulier insluiten in een AEM Sites-pagina](#embed-the-adaptive-form-in-an-aem-sites-page)
* [Het adaptieve formulier insluiten in een externe webpagina (een niet-AEM-webpagina die buiten AEM wordt gehost)](../../forms/using/publish-your-adaptive-form.md)

## Voordat u begint {#before-you-start}

* **[opstelling AEM Forms publiceert instantie ](https://helpx.adobe.com/experience-manager/6-3/forms/using/installing-configuring-aem-forms-osgi.html)**: De publiceer instantie is een openbaar onder ogen ziende instantie van AEM [!DNL Forms] die op publicatiewijze loopt. In een productieomgeving bevindt de publicatie-instantie zich buiten de firewall van de organisatie.
* **[de replicatie van de opstelling en omgekeerde replicatie ](https://helpx.adobe.com/experience-manager/6-3/help/sites-deploying/replication.html)**: De replicatie kopieert inhoud van de auteursinstantie aan publiceer instantie en keert gebruikersinput (bijvoorbeeld, vorminput) van terug publiceer instantie aan de auteursinstantie.

## Het adaptieve formulier publiceren als een AEM-pagina {#publish-the-adaptive-form-as-an-aem-page}

Als het adaptieve formulier wordt gepubliceerd als een AEM-pagina, bevat de hele webpagina alleen het gepubliceerde formulier. U kunt de URL van het aangepaste formulier gebruiken om het formulier te koppelen van een andere webpagina. Om de **verschepen-adres-toe:voegen-update-vorm** adaptieve vorm als een Pagina van AEM te publiceren:

1. Meld u aan bij de auteur van AEM [!DNL Forms] en zoek het aangepaste formulier voor het verzendadres en de update van het formulier in de gebruikersinterface van AEM [!DNL Forms] .
   `https://localhost:4502/aem/forms.html/content/dam/formsanddocuments`
1. Selecteer het adaptieve formulier voor het verzendadres en de update en selecteer **[!UICONTROL Publish]** . Er wordt een dialoogvenster weergegeven met elementen die betrekking hebben op het adaptieve formulier. Selecteer **[!UICONTROL Publish]**. Het adaptieve formulier wordt gepubliceerd en er verschijnt een succesdialoogvenster.
1. Open het formulier op het publicatieexemplaar. Het formulier kan door de eindgebruiker worden ingevuld en verzonden.
   `https://localhost:4503/content/forms/af/shipping-address-add-update-form.html`

## Het adaptieve formulier insluiten in een AEM Sites-pagina {#embed-the-adaptive-form-in-an-aem-sites-page}

Met AEM [!DNL Forms] kunnen ontwikkelaars van formulieren adaptieve formulieren naadloos insluiten in een AEM [!DNL Sites] -pagina. Het ingesloten adaptieve formulier is volledig functioneel en gebruikers kunnen het formulier invullen en verzenden zonder de pagina te verlaten. Hiermee kan de gebruiker in de context van andere elementen op de webpagina blijven en tegelijkertijd met het formulier communiceren.

AEM [!DNL Forms] biedt een component, AEM [!DNL Forms] Container, voor het insluiten van een adaptief formulier op een AEM [!DNL Sites] -pagina. De component is standaard niet zichtbaar in de AEM [!DNL Sites] -container. Voer de volgende stappen uit om de AEM [!DNL Forms] Container-component in te schakelen en het adaptieve formulier in te sluiten in een AEM [!DNL Sites] -pagina:

1. Maak en open een pagina in de website Web.Retail voor bewerking. Bijvoorbeeld, [ https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html ](https://localhost:4502/editor.html/content/we-retail/us/en/user/shipping-and-billing-address.html). Het aangepaste formulier wordt ingesloten op de pagina [!DNL Sites] .

   U kunt het adaptieve formulier ook insluiten in een bestaande Web.Retail [!DNL Site's] -pagina. Bijvoorbeeld, ONDER Amerikaanse pagina [ https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html ](https://localhost:4502/editor.html/content/we-retail/us/en/about-us.html). Hiermee bespaart u de tijd om een pagina te maken. In de onderstaande stappen wordt de nieuwe pagina gebruikt.

   De website We.Retail wordt verzonden met AEM. Als u niet de wij.Retail geïnstalleerde plaats hebt, zie [ Wij.Retail de Implementatie van de Verwijzing ](https://helpx.adobe.com/experience-manager/6-3/help/sites-developing/we-retail.html) installeren de plaats.

1. Selecteer ![ eigenschappen ](assets/properties.png) paginainformatie en selecteer de **[!UICONTROL Edit Template]** optie in de pas gecreëerde Web.Retail plaatspagina. De sjabloon van de pagina wordt geopend op een nieuw tabblad van de browser.
1. Selecteer binnen de **[!UICONTROL layout container]** doos en selecteer ![ terugkoppel ](assets/feedmanagement.png). In het **[!UICONTROL Allowed Components]** lusje, breid **[!UICONTROL General]** accordion uit, selecteer de **[!UICONTROL AEM Form]** optie, en selecteer ![ save_icon ](assets/save_icon.svg). De AEM [!DNL Forms] Container-component is ingeschakeld voor de pagina.

1. Open het browsertabblad met de AEM [!DNL Sites] -pagina dat u in stap 1 hebt geopend. Selecteer het vak **[!UICONTROL Drag components here]** en selecteer **+.** Selecteer **[!UICONTROL AEM Form]** in het vak **[!UICONTROL Insert New Component]** . De component **[!UICONTROL AEM Forms Container]** wordt toegevoegd aan de pagina.
1. Selecteer de **[!UICONTROL AEM Forms container]** component en selecteer ![ vorm-pictogram ](assets/configure-icon.svg). Er wordt een dialoogvenster weergegeven met eigenschappen van de container AEM [!DNL Forms] . Blader in het veld **[!UICONTROL Asset Path]** naar het adaptieve formulier voor het verzendadres en de update. Selecteer ![ save_icon ](assets/save_icon.svg). Het adaptieve formulier is ingesloten op de pagina.
1. Publiceer zowel het aangepaste formulier als de [!DNL Sites] pagina. Hieronder volgen enkele punten die u in overweging wilt nemen:

   * Als u de AEM [!DNL Sites] -pagina voor de eerste keer publiceert en een ingesloten formulier bevat, publiceert u de [!DNL Sites] -pagina en het ingesloten formulier.
   * Als u alleen het ingesloten formulier op een gepubliceerde sitepagina wijzigt, publiceert u het oorspronkelijke formulier en de wijzigingen worden weerspiegeld in de gepubliceerde sitepagina. De gepubliceerde sitepagina bevat een verwijzing naar het formulier en de pagina hoeft niet opnieuw te worden gepubliceerd.
   * Als u de pagina [!DNL Sites] en het ingesloten formulier wijzigt, publiceert u de pagina [!DNL Sites] en het formulier opnieuw.

     ![ bed-in-a-plaats-plaatsen ](assets/embed-in-aem-sites.png) in

   Formulier Verzendadres en factuuradres wijzigen toegevoegd aan een AEM [!DNL Sites] -pagina.

## Het adaptieve formulier insluiten in een externe webpagina {#embed-the-adaptive-form-in-an-external-webpage}

U kunt een adaptief formulier insluiten in een externe webpagina (een niet-AEM-webpagina die buiten AEM wordt gehost) door een paar regels JavaScript in de externe webpagina in te voegen. De JavaScript-code verzendt een HTTP-aanvraag naar de AEM [!DNL Forms] -server voor het adaptieve formulier en de gerelateerde bronnen en voegt het adaptieve formulier toe aan de webpagina. Voor gedetailleerde stappen, zie [ de adaptieve vorm aan een externe Web-pagina ](/help/forms/using/embed-adaptive-form-external-web-page.md) inbedden.
