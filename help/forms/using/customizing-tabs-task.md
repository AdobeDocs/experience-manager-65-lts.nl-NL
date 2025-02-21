---
title: Tabs aanpassen voor een taak
description: In LiveCycle AEM Forms-werkruimte kunt u de namen van de tabbladen voor uw taken aanpassen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Tabs aanpassen voor een taak {#customizing-tabs-for-a-task}

U kunt tabnamen voor de component `Start Process` aanpassen in de `Start Process` Uberweergave en de component `Task Details` in de `ToDo` Uberweergave.

1. Volg de [ Algemene stappen voor de werkruimte van AEM Forms aanpassing ](/help/forms/using/generic-steps-html-workspace-customization.md).
1. Wijzig de waarde van `tabname` in het `translation.json` -bestand.

   Wijzig bijvoorbeeld `/apps/ws/locales/en-US/translation.json` voor Engels in het volgende.

   * Gebruik het volgende fragment uit het `"startprocess" : {}` -blok voor taken die tijdens het startproces worden gestart.

   ```json
   "tabname" : {
               "form" : "Application",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Helper Notes"
           }
   ```

   * Voor taken in Aan-doe, gebruik het volgende fragment van het `"todo" : {}` blok.

   ```json
   "tabname" : {
               "summary" : "Bird's-eye view",
               "history" : "Past",
               "form" : "Form",
               "details" : "Overview",
               "attachments" : "Attachments",
               "notes" : "Notes"
   }
   ```

   >[!NOTE]
   >
   >Voeg het corresponderende sleutel-waardepaar voor alle ondersteunde talen toe.
