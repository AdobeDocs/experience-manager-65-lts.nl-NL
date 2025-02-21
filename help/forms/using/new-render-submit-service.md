---
title: Nieuwe renderservice en verzendservice
description: Definieer de renderings- en verzendservices in Workbench om XDP-formulieren te genereren als HTML of PDF, afhankelijk van het apparaat waartoe deze toegang hebben.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '891'
ht-degree: 0%

---

# Nieuwe renderservice en verzendservice{#new-render-and-submit-service}

## Inleiding {#introduction}

Wanneer u in Workbench een `AssignTask` -bewerking definieert, geeft u een bepaald formulier op (XDP- of PDF-formulier). Geef ook een set services voor renderen en verzenden op via een actieprofiel.

Een XDP kan worden weergegeven als een PDF-formulier of een HTML-formulier. De nieuwe mogelijkheden omvatten de capaciteit om:

* Een XDP-formulier weergeven en verzenden als HTML
* Een XDP-formulier weergeven en verzenden als PDF op het bureaublad en als HTML op mobiele apparaten (bijvoorbeeld een iPad)

### Nieuwe HTML Forms-service {#new-html-forms-service}

De nieuwe HTML Forms-service gebruikt de nieuwe functie in Forms om het weergeven van XDP-formulieren als HTML te ondersteunen. De nieuwe HTML Forms-service stelt de volgende methoden beschikbaar:

```java
/*
 * Generates a URL (for the HTML Form) to be passed to client, given a TaskContext.
 * The output of this API is something like this - /lc/content/xfaforms/profiles/default.ws.html?ContentRoot=repository://Applications/MyApplication/MyFolder&template=MyForm.xdp
 * @param taskContext task context
 * @param profileName Forms servlet URL.
 * @return form URL string
 */
public String generateFormURL(TaskContext taskContext, String profileName);

/*
 * Render the XDP Form as HTML. Can be used directly for updating the runtimeMap in render.
 * It adds the following keys to the map -
 * hint:new html form = true
 * newHTMLFormURL = the URL returned after calling 'generateFormURL' API.
 * @param TaskContext taskContext
 * @param profileName Forms servlet URL.
 * @param runtimeMap runtime map<string,object> associated with form rendering.
 * return runtimeMap
 */
public Map<String, Object> renderHTMLForm (TaskContext taskContext, String profileName, Map<String,Object> runtimeMap);
```

Meer informatie over de Mobiele profielen van de Vorm kan bij [ worden gevonden Creërend een douaneprofiel ](/help/forms/using/custom-profile.md).

## Nieuwe HTML-processen voor het renderen en verzenden van formulieren {#new-html-form-render-amp-submit-processes}

Geef voor elke bewerking &#39;AssignTask&#39; een Render- en een Verzendproces op met het formulier. Deze processen worden geroepen door TaskManager `renderForm` en `submitForm` APIs om douanebehandeling toe te staan. Semantiek van deze processen voor Nieuw HTML-formulier:

### Een nieuw HTML-formulier renderen {#render-a-new-html-form}

Het nieuwe proces voor het renderen van HTML heeft, net als elk renderproces, de volgende I/O-parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outFormDoc`

Deze methode simuleert het exacte gedrag van de `renderHTMLForm` API van NewHTMLFormsService. De `generateFormURL` API wordt aangeroepen om de URL voor HTML-uitvoering van het formulier op te halen. Vervolgens wordt de runtimeMap gevuld met de volgende sleutel of waarden:

new html form = true

newHTMLFormURL = de URL die wordt geretourneerd na het aanroepen van de `generateFormURL` API.

### Een nieuw HTML-formulier verzenden {#submit-a-new-html-form}

Dit proces voor het verzenden van een nieuw HTML-formulier werkt met de volgende I/O-parameters -

Invoer - `taskContext`

Uitvoer - `runtimeMap`

Uitvoer - `outputDocument`

Het proces plaatst `outputDocument` aan `inputDocument` die van `taskContext` wordt teruggewonnen.

## Standaardwaarden voor renderen of verzenden, processen en actieprofielen {#default-render-or-submit-processes-and-action-profiles}

Met de standaardservices Renderen en Verzenden kunt u ondersteuning inschakelen voor het weergeven van PDF&#39;s op een desktopcomputer en HTML op mobiele apparaten (iPad).

### Standaardformulier voor renderen {#default-render-form}

Met dit proces wordt een XDP-formulier naadloos weergegeven op meerdere platforms. Het proces wint de gebruikersagent van `taskContext` terug, en gebruikt de gegevens om het proces te roepen om of HTML of PDF terug te geven.

![ gebrek-geef-vorm ](assets/default-render-form.png)

### Standaardformulier verzenden {#default-submit-form}

Met dit proces wordt een XDP-formulier naadloos verzonden naar meerdere platforms. Het wint de gebruikersagent van `taskContext` terug en gebruikt de gegevens om het proces te roepen om of HTML of PDF voor te leggen.

![ gebrek-voorlegt-vorm ](assets/default-submit-form.png)

## De weergave van mobiele formulieren overschakelen van PDF naar HTML {#switch-the-rendering-of-mobile-forms-from-pdf-to-html}

Browsers trekken de ondersteuning voor op NPAPI gebaseerde plug-ins, waaronder plug-ins voor Adobe Acrobat en Adobe Acrobat Reader, geleidelijk in. U kunt de weergave van mobiele formulieren van PDF naar HTML als volgt wijzigen:

1. Meld u als geldige gebruiker aan bij Workbench.
1. Selecteer **Dossier** > **krijgt Toepassingen**.

   Het dialoogvenster Toepassingen ophalen wordt geopend.

1. Selecteer de toepassingen waarvoor u mobiele vorm wilt veranderen teruggevend en **O.K.** klikken.
1. Open het proces waarvoor u de rendering wilt wijzigen.
1. Open het gerichte startpunt/de taak, navigeer aan de Presentatie &amp; sectie van Gegevens, en klik **leiden de Profielen van de Actie**.

   Het dialoogvenster Actieprofielen beheren wordt geopend.
1. De Standaard van de verandering geeft profielconfiguraties van PDF aan HTML terug en klikt **O.K.**.
1. Controleer het proces.
1. Herhaal de stappen om de rendering voor andere processen te wijzigen.
1. Implementeer de toepassing die relevant is voor de processen die u hebt gewijzigd.

### Standaardactieprofiel {#default-action-profile}

Met het standaardactieprofiel wordt het XDP-formulier weergegeven als PDF. Dit gedrag is nu gewijzigd en gebruikt nu de processen Standaardformulier renderen en Standaardformulier verzenden.

Enkele vaak gestelde vragen over actieprofielen zijn als volgt:

![ gen_question_b_20 ](assets/gen_question_b_20.png) **wat teruggeeft/processen zal voorleggen uit de doos beschikbaar zijn?**

* Handleiding voor renderen (hulplijnen zijn afgekeurd)
* Formulierhulplijn renderen
* PDF-formulier renderen
* HTML-formulier renderen
* Nieuw HTML-formulier renderen (nieuw)
* Standaardformulier renderen (nieuw)

Equivalente verzendprocessen.

![ gen_question_b_20 ](assets/gen_question_b_20.png) **Welke Profielen van de Actie uit de doos beschikbaar zullen zijn?**

Voor XDP Forms:

* Standaard (renderen/verzenden met de nieuwe processen Standaard renderen/verzenden)

![ gen_question_b_20 ](assets/gen_question_b_20.png) **wat door de procesontwerper moet worden gedaan om de vorm toe te laten om in HTML op een apparaat, en in PDF op een Desktop worden teruggegeven?**

Niets. Het standaardprofiel van de Actie wordt automatisch gekozen, en de wijze van het teruggeven wordt ook behandeld, automatisch.

![ gen_question_b_20 ](assets/gen_question_b_20.png) **wat moet worden gedaan om de vorm toe te laten om in HTML op een Desktop worden teruggegeven?**

De gebruiker moet het HTML-keuzerondje voor het standaardprofiel selecteren.

![ gen_question_b_20 ](assets/gen_question_b_20.png) **zal er om het even welk verbeteringseffect op het veranderen van het standaardgedrag van het actieprofiel zijn?**

Ja, omdat de vorige renderings- en verzendservices die aan het standaardactieprofiel zijn gekoppeld verschillend waren, worden deze beschouwd als een aanpassing van de bestaande formulieren. Bij het klikken **herstel Gebreken**, geeft het gebrek terug en legt de diensten voor in plaats daarvan worden geplaatst.

Als u de bestaande services voor het renderen of verzenden van PDF-formulieren of aangepaste services (zoals custom1) hebt gewijzigd, wilt u nu dezelfde functionaliteit gebruiken voor HTML-uitvoering. U moet de nieuwe renderen herhalen of de dienst voorleggen (zoals custom2) en gelijkaardige aanpassingen op die toepassen. Pas nu het actieprofiel voor uw XDP aan begin gebruikend de diensten custom2, in plaats van custom1 voor terug of voorleggen.

Wat moet de procesontwerper doen om ervoor te zorgen dat het formulier in HTML op een apparaat en in PDF op een bureaublad kan worden weergegeven?
Wat moet de procesontwerper doen om ervoor te zorgen dat het formulier in HTML op een apparaat en in PDF op een bureaublad kan worden weergegeven?
