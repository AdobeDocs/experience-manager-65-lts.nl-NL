---
title: Aanmelden bij AEM Forms-workflows
description: Leer hoe u fouten in AEM Forms Workflow-problemen kunt opsporen en foutopsporingslogbestanden kunt inschakelen voor AEM Forms-workflows om de logbestanden weer te geven.
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 90a44cab-3ecf-4a71-95d4-e8ce2d996980
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 5%

---

# Aanmelden bij AEM Forms-workflows{#logging-in-aem-forms-workflows}

Forms Workflow-stappen bieden gedetailleerde logboeken voor het eenvoudig opsporen van fouten in workflowgerelateerde problemen. Schakel foutopsporingslogboeken in voor AEM Forms-workflows om de logbestanden weer te geven.

Door gebrek, is alle registrereninformatie beschikbaar in het {**dossier 0} error.log bij de */crx-repository/logs/* folder.**

De logbestanden voor foutopsporing voor formulierworkflows zijn onder andere:

* Invoer van elke workflowstap. Bijvoorbeeld:\
  `[DEBUG] "Executing Invoke DDX Process step"`

* Afsluiten van elke workflowstap. Bijvoorbeeld:\
  `[DEBUG] "Successfully finished Invoke DDX Process step"`

* Service-oproepberichten. Bijvoorbeeld:\
  `[DEBUG] Invoking Adobe Sign Service for creating agreement`

* Service exit messages. Bijvoorbeeld:\
  `[DEBUG] Agreement created successfully with agreement id <agreement id>`

* Variabelen worden gelezen van de metagegevenskaart. Bijvoorbeeld:\
  `[DEBUG] Successfully retrieved variable <variable name> from workflow meta data map`

* Variabelen die zijn geschreven in de JCR-gegevensopslagruimte. Bijvoorbeeld:

  ```verilog
     [DEBUG] Successfully written variable <variable name> into meta data node at <JCR path where meta data is being written>
  ```

* Uitzonderingsberichten met volledige stacktracering. Bijvoorbeeld:\
  `[DEBUG] Exception in Adobe Sign Service <complete stack trace>`

* Dynamische stapmetagegevensparameters. Bijvoorbeeld:

  ```verilog
  [DEBUG] Document of Record to be generated for adaptive form <path of adaptive form>
   [DEBUG] Locale to be used for Document of Record is <locale>
  ```

In het volgende voorbeeld worden de logboeken voor de stap Document ondertekenen weergegeven:

```verilog
[DEBUG] Executing sign document step.
[DEBUG] Using adobe sign configuration: <path of adobe sign configuration>
[DEBUG] Invoking Adobe Sign Service for creating agreement
[DEBUG] Agreement created successfully with agreement id <agreement id>
[DEBUG] Exception in Adobe Sign Service <complete stack trace>
[ERROR] Exception in Adobe Sign Service
[DEBUG] Successfully finished sign document step
```

Gebruik de logboeken om te evalueren dat:

* U gebruikt een correcte configuratie van het Teken van Adobe.
* De Adobe-ondertekeningsservice wordt afgesloten nadat een overeenkomst is gemaakt.
* De stap Document ondertekenen sluit af met een succesbericht.

Als er een uitzondering is, kunt u de volledige stacktracering bekijken om de oorzaak van de fout te evalueren.

## Foutopsporingsregistratie inschakelen voor AEM Forms-workflows {#enable-debug-logging-for-aem-forms-workflows}

Ga als volgt te werk, zodat u foutopsporingslogbestanden kunt inschakelen voor AEM Forms-workflows:

1. Ga naar AEM Web Console Configuration Manager op:

   https://&#39;[ server ]:[ haven ]&#39;/system/console/configMgr

1. Selecteer **[!UICONTROL Sling]** > **[!UICONTROL Log Support]** .
1. Selecteren **[!UICONTROL Add new Logger.]**
1. Selecteer **[!UICONTROL Debug]** als de **[!UICONTROL Log Level]** .
1. Geef de locatie van het logbestand op. De standaardplaats voor het logboekdossier is: *logboeken \ error.log*
1. Specificeer de naam van het pakket als **com.adobe.granite.workflow.core** in de **[!UICONTROL Logger]** kolom.

   Het uitvoeren van deze stappen laat het opslaan van toe zuivert logboeken voor het {**pakket 0} com.adobe.granite.workflow.core.** Selecteer **[!UICONTROL +]** en voeg de volgende pakketnamen aan de lijst toe:

   * com.adobe.fd.workflow
   * com.adobe.fd.workspace
