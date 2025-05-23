---
title: De landinstelling van de gebruikersinterface van de AEM Forms-werkruimte wijzigen
description: Hoe te om de werkruimte van AEM Forms te wijzigen om tekst, doen ineenstorten categorieën, rijen, en processen, en de datumkiezer op de interface te lokaliseren.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 3f919e4d-0535-4816-8762-9c0088e47a2c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '556'
ht-degree: 0%

---

# De landinstelling van de gebruikersinterface van de AEM Forms-werkruimte wijzigen{#changing-the-locale-of-aem-forms-workspace-user-interface}

De werkruimte van AEM Forms biedt vanuit de verpakking ondersteuning voor Engelse, Franse, Duitse en Japanse talen. Het biedt ook de mogelijkheid om de gebruikersinterface van de AEM Forms-werkruimte te lokaliseren naar een andere taal.

U kunt als volgt de gebruikersinterface van de AEM Forms-werkruimte lokaliseren naar de taal van uw keuze:

* Tekst van de AEM Forms-werkruimte lokaliseren.
* U kunt samengevouwen categorieën, wachtrijen en processen lokaliseren.
* Datumkiezer lokaliseren

Alvorens de bovengenoemde stappen uit te voeren, zorg ervoor dat u de stappen volgt die bij [ worden vermeld Algemene stappen voor de werkruimteaanpassing van AEM Forms ](../../forms/using/generic-steps-html-workspace-customization.md).

>[!NOTE]
>
>Om de taal van het login scherm van de werkruimte van AEM Forms te veranderen, zie [ Creërend een login scherm ](../../forms/using/creating-new-login-screen.md).

## Tekst lokaliseren {#localizing-text}

Voer de volgende stappen uit zodat kunt u steun voor een taal *Nieuw* en browser scènecode *nieuw* toevoegen.

1. Meld u aan bij CRXDE Lite.
De standaard-URL van CRXDE Lite is `https://'[server]:[port]'/lc/crx/de/index.jsp` .
1. Ga naar de locatie `apps/ws/locales` en maak een map `nw.`
1. Kopieer het bestand `translation.json` van de locatie `/apps/ws/locales/en-US` naar de locatie `/apps/ws/locales/nw` .
1. Navigeer naar `/apps/ws/locales/nw` en open `translation.json` voor bewerking. Wijzig de landinstelling in het bestand translatie.json.

   De volgende voorbeelden bevatten het bestand translatie.json voor Engelse en Franse landinstellingen van de AEM Forms-werkruimte.

   ![&#128279;](assets/translation_json_in_en.png)  translatie_json_in_fr ![ ](assets/translation_json_in_fr.png)

## Samengevouwen categorieën, wachtrijen en processen lokaliseren {#localizing-collapsed-categories-queues-and-processes}

In de AEM Forms-werkruimte worden afbeeldingen gebruikt om koppen van categorieën, wachtrijen en processen weer te geven. U hebt een ontwikkelingspakket nodig om deze koppen te lokaliseren. Voor gedetailleerde informatie over het creëren van een ontwikkelingspakket, zie [ de werkruimtecode van AEM Forms bouwen.](introduction-customizing-html-workspace.md#building-html-workspace-code)

In de volgende stappen, wordt verondersteld dat de nieuwe gelokaliseerde beelddossiers *Categories_nw.png*, *Queue_nw.png* zijn, en *Processes_nw.png*. De aanbevolen breedte van de afbeeldingen moet op 19 pixels worden ingesteld.

>[!NOTE]
>
>U kunt als volgt de landinstellingscode van de browser voor de taal vinden. Open `https://'[server]:[port]'/lc/libs/ws/Locale.html`.

![ doen ineenstorten_panels_image ](assets/collapsing_panels_image.png)

Voer de volgende stappen uit om de afbeeldingen te lokaliseren:

1. Plaats de afbeeldingsbestanden met een WebDAV-client in de map */apps/ws/images* .
1. Navigeer naar */apps/ws/css* . Open *newStyle.css* voor het uitgeven en voeg de volgende ingangen toe:

   ```css
   #categoryListBar .content.nw {
        background: #3e3e3e url(../images/Categories_nw.png) no-repeat 10px 10px;
    }
   
   #filterListBar .content.nw {
       background: #3e3e3e url(../images/Queues_nw.png) no-repeat 10px 10px;
   }
   
   #processNameListBar .content.nw {
       background: #3e3e3e url(../images/Processes_nw.png) no-repeat 10px 10px;
   }
   ```

1. Voer alle semantische veranderingen uit die in het [&#128279;](../../forms/using/introduction-customizing-html-workspace.md) artikel van de Aanpassing van Workspace worden vermeld.
1. Navigeer aan *js/runtime/nut* omslag en open het {*dossier 2} usersessie.js voor het uitgeven.*
1. Bepaal de plaats van de code die in het originele codeblok wordt vermeld en voeg de voorwaarde *lang toe!== &quot;nw&quot;* aan de if verklaring:

   ```javascript
   // Orignal code
   setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

   ```javascript
   //new code
    setLocale = function () {
           var lang = $.trim(i18n.lng());
           if (lang === null || lang === '' || (lang !== 'fr-FR' && lang !== 'de-DE' && lang !== 'ja-JP' && lang !== 'nw')) {
               window.lcWorkspace.locale = 'en-US';
           } else {
               window.lcWorkspace.locale = lang;
           }
       }
   ```

## Datumkiezer lokaliseren {#localizing-date-picker}

U vereist een ontwikkelingspakket om *datepicker* API te lokaliseren. Voor gedetailleerde informatie over het creëren van een ontwikkelingspakket, zie [ de werkruimtecode van AEM Forms van de Bouw ](introduction-customizing-html-workspace.md#building-html-workspace-code).

1. Download en haal het [ pakket jQuery UI ](https://jqueryui.com/download/all/), navigeer aan *&lt;extracted jquery UI package>* \ jquery-ui-1.10.2.zip \ jquery-ui-1.10.2 \ ui \ i18n.
1. Kopieer het bestand jquery.ui.datepicker-nw.js voor code van de landinstelling nu naar apps/ws/js/libs/jqueryui en breng wijzigingen aan die specifiek zijn voor de landinstelling.
1. Navigeer naar `apps/ws/js` en open het `jquery.ui.datepicker-nw.js` -bestand voor bewerking.
1. Maak in het bestand main.js een alias voor `jquery.ui.datepicker-nw.js.` De code waarmee een alias voor het bestand `jquery.ui.datepicker-nw.js` wordt gemaakt, is:

   ```javascript
   jqueryuidatepickernw : pathprefix + 'libs/jqueryui/jquery.ui.datepicker-nw'
   ```

1. Gebruik alias `jqueryuidatepickernw` om het `jquery.ui.datepicker-nw.js` -bestand op te nemen in alle bestanden die datepicker gebruiken. De datepicker wordt gebruikt in de volgende bestanden:

   * `js/runtime/views/outofoffice.js`
   * `js/runtime/views/searchtemplatedetails.js`

   De voorbeeldcode hieronder laat zien hoe u de vermelding jquery.ui.datepicker-nw.js toevoegt:

   ```json
   //Original Code
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, slimScroll, UserSearch, LogManager, Logger) {
   ```

   ```json
   // Code with Date Picker alias for new language
   define([
       'jquery',
       'underscore',
       'backbone',
       'jqueryui',
       'jqueryuidatepickerja',
       'jqueryuidatepickerde',
       'jqueryuidatepickerfr',
       'jqueryuidatepickernw', // Date Picker alias
       'slimscroll',
       'usersearchview',
       'logmanagerutil',
       'loggerutil'
   ], function ($, _, Backbone, jQueryUI, jQueryUIDatePickerJA, jQueryUIDatePickerDE, jQueryUIDatePickerFR, jQueryUIDatePickerNW, slimScroll, UserSearch, LogManager, Logger) {
   ```

1. Wijzig in alle bestanden die de datepicker-API gebruiken de standaard datepicker API-instellingen. De datepicker-API wordt gebruikt in de volgende bestanden:

   * apps\ws\js\runtime\views\searchtemplatedetails.js
   * apps\ws\js\runtime\views\outofoffice.js

   Wijzig de volgende code om de nieuwe landinstelling toe te voegen:

   ```javascript
   if (locale === 'ja-JP') {
      $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
      $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
      $.datepicker.setDefaults($.datepicker.regional.fr);
   } else {
      $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```

   ```javascript
   if (locale === 'ja-JP') {
       $.datepicker.setDefaults($.datepicker.regional.ja);
   } else if (locale === 'de-DE') {
       $.datepicker.setDefaults($.datepicker.regional.de);
   } else if (locale === 'fr-FR') {
       $.datepicker.setDefaults($.datepicker.regional.fr);
   } else if (locale === 'nw') {
       $.datepicker.setDefaults($.datepicker.regional.nw);
   } else {
       $.datepicker.setDefaults($.datepicker.regional['']);
   }
   ```
