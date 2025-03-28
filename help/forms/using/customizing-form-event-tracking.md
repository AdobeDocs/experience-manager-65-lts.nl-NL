---
title: Gebeurtenissen van formulieren aanpassen
description: Als een gebruiker meer dan 60 seconden aan een veld doorgeeft, wordt een veldbezoek-gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe SiteCatalyst verzonden.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: customization
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,Foundation Components
exl-id: 79f0c1e7-6345-4cfb-8186-3ecca82cac44
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '449'
ht-degree: 0%

---

# Gebeurtenissen van formulieren aanpassen {#customizing-form-event-tracking}

Uit het vak worden de volgende gebeurtenissen bijgehouden in een adaptieve vorm die geschikt is voor analyses:

<table>
 <tbody>
  <tr>
   <th>Gebeurtenis</th>
   <th>Beschikbare variabelen</th>
  </tr>
  <tr>
   <td>renderen</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>opgeven</td>
   <td>formName, formTitle, formInstance, panelName, panelTitle</td>
  </tr>
  <tr>
   <td>opslaan</td>
   <td>formName, formTitle, formInstance, panelName, source</td>
  </tr>
  <tr>
   <td>indienen</td>
   <td>formName, formTitle, formInstance, source</td>
  </tr>
  <tr>
   <td>fout</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>help</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle</td>
  </tr>
  <tr>
   <td>fieldVisit</td>
   <td>formName, formTitle, fieldName, fieldTitle, panelTitle <br /> </td>
  </tr>
  <tr>
   <td>panelVisit</td>
   <td>formName, formTitle, panelName, panelTitle</td>
  </tr>
 </tbody>
</table>

## Tijdslimiet voor de gebeurtenis &#39;visit&#39; van het veld aanpassen {#customizing-the-field-visit-event-timeout}

Als een gebruiker in de standaard AEM-formulierinstelling meer dan 60 seconden doorgeeft aan een veld, wordt een `fieldvisit` -gebeurtenis geactiveerd en worden de gegevens van het veld naar Adobe Analytics verzonden. U kunt de basislijn voor het bijhouden van veldtijd aanpassen bij AEM Forms Analytics Configuration op de AEM Configuration-console (/system/console/configMgr) om de time-outlimiet te verhogen of te verlagen.

## De volgende gebeurtenissen aanpassen {#customizing-the-tracking-events}

U kunt de `trackEvent` functie wijzigen beschikbaar in `/libs/afanalytics/js/custom.js` dossier om gebeurtenis het volgen aan te passen. Wanneer een gebeurtenis die in een adaptieve vorm wordt gevolgd voorkomt, wordt de `trackEvent` functie geroepen. De functie `trackEvent` accepteert twee parameters: `eventName` en `variableValueMap` .

U kunt waarde van *eventName* en *variableValueMap* argumenten evalueren om het volgende gedrag van gebeurtenissen te veranderen. U kunt er bijvoorbeeld voor kiezen om de gegevens naar de analytische server te verzenden nadat een aantal foutgebeurtenissen is opgetreden. U kunt ook de volgende aanpassingen uitvoeren:

* U kunt een drempeltijd instellen voordat u de gebeurtenis verzendt.
* U kunt een staat handhaven om actie te besluiten, bijvoorbeeld, *fieldVisit* duwt een dummygebeurtenis die op timestamp van de laatste gebeurtenis wordt gebaseerd.
* U kunt de functie `pushEvent` gebruiken om de gebeurtenis naar de analytische server te verzenden *.*

* U kunt ervoor kiezen om de gebeurtenis helemaal niet naar de analyseserver te duwen.

### Monster {#sample}

In het volgende voorbeeld, staat voor de *fout* gebeurtenis van elk *fieldName* attribuut wordt gehandhaafd. De gebeurtenis wordt alleen naar de analyseserver verzonden als er opnieuw een fout optreedt.

```javascript
case 'error':
        if(errorOccurred[variableValueMap.fieldName] == true) {
            pushEvent(eventName, variableValueMap)
        }
        errorOccurred[variableValueMap.fieldName] = true;
        break;
```

## De gebeurtenis panelvisit aanpassen {#customizing-the-panelvisit-event}

Bij de standaard AEM Forms-instelling wordt na elke 60 seconden gecontroleerd of het venster met het adaptieve formulier actief is. Als het venster actief is, wordt de gebeurtenis van a `panelVisit` teweeggebracht aan Adobe Analytics. Hiermee kunt u controleren of het document of formulier actief is en kunt u de tijd berekenen die aan het desbetreffende formulier of document is besteed.

>[!NOTE]
>
>De naam van de gebeurtenis die wordt gebruikt om activiteit op te halen en de tijd die wordt doorgebracht te berekenen is &quot;panelVisit&quot;. Deze gebeurtenis is anders dan de gebeurtenis die het deelvenster bezoeken in de bovenstaande tabel wordt weergegeven.

U kunt de functie planningHeartBeatCheck die beschikbaar is in het `/libs/afanalytics/js/custom.js` -bestand wijzigen om deze gebeurtenis die regelmatig naar Adobe Analytics wordt verzonden, te wijzigen of te stoppen.
