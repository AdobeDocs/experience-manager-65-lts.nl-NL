---
title: Miniatuur van de JavaScript-bestanden
description: Instructies voor het genereren van geminificeerde code na aanpassingen in de AEM Forms-werkruimte om de JS-bestanden voor het web te optimaliseren.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: d2d17d2c-b82f-4a7b-8ff1-0c226626412a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '188'
ht-degree: 0%

---

# Miniatuur van de JavaScript-bestanden {#minification-of-the-javascript-files}

Met Minificatie worden de overbodige tekens, zoals witruimte, nieuwe regels en opmerkingen, uit de broncode verwijderd. Dit verbetert de prestaties door de grootte van de code te verminderen. De miniatuur heeft geen invloed op de functionaliteit, maar vermindert de leesbaarheid van de code.

Voer de volgende stappen uit om geminificeerde code voor semantische wijzigingen te genereren.

1. Kopieer `client-html/src/main/webapp/js` van src-pakket op bestandssysteem.

   >[!NOTE]
   >
   >Zie [ Inleiding aan het Aanpassen van de werkruimte van AEM Forms ](/help/forms/using/introduction-customizing-html-workspace.md) voor meer details over de pakketten.

1. Werk paden bij in `main.js` onder client-html/src/main/webapp/js voor toegevoegde/bijgewerkte modellen/weergaven.

   Bijvoorbeeld, de toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/models/sharequeue',
   ```

   Naar

   ```javascript
   sharequeuemodel : pathprefix + 'runtime/myModels/mySharequeue',
   ```

1. Werk `registry-config.xml, located at client-html/src/main/webapp/js/resource_generator,` bij voor het geval dat er een wijziging/toevoeging van een alias in `main.js` optreedt.

   Bijvoorbeeld, de toevoeging van een nieuw model van de Schaduwrij, zeg mySharequeue, verandering:

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/models/sharequeue.js"
               service="service"/>
   ```

   Naar

   ```xml
   <sharequeue
               name="sharequeue"
               path="runtime/myModels/mySharequeue.js"
               service="service"/>
   ```

1. Voer de opdracht uit op client-html/src/main/webapp/js/minifier:

   ```shell
   mvn clean install
   ```

   Er wordt een map met geminificeerde bestanden gegenereerd, onder client-html/src/main/webapp/js met geminificeerde main.js en register.js.

>[!NOTE]
>
>Minificatie werkt alleen op een 64-bits JVM.

>[!NOTE]
>
>Als u een minieme upgrade uitvoert, heeft dit gevolgen voor de upgrade.
