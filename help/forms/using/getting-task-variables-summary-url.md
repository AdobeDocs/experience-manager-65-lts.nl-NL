---
title: Taakvariabelen ophalen in Summiere URL
description: Hoe te om de informatie over een taak te hergebruiken en een Samenvatting URL te produceren om een taak samen te vatten of te beschrijven.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 1cd2aae7-306f-4f7a-b4d2-e8c64827c09a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '431'
ht-degree: 0%

---

# Taakvariabelen ophalen in Summiere URL {#getting-task-variables-in-summary-url}

Op de overzichtspagina wordt informatie over taken weergegeven. In dit artikel wordt beschreven hoe u taakgerelateerde informatie in de overzichtspagina kunt hergebruiken.

In deze voorbeeldorganisatie dient een medewerker een formulier voor een verlofaanvraag in. Het aanvraagformulier gaat vervolgens ter goedkeuring naar de manager van de werknemer.

1. Creeer een de renderer van de steekproefHTML (html.esp) voor RESCURTType **Werknemers/PtoApplication**.

   De renderer gaat ervan uit dat de volgende eigenschappen op het knooppunt moeten worden ingesteld:

   * naam
   * leegmaken
   * reden
   * duur

   >[!NOTE]
   >
   >Deze renderer is de sjabloon voor de overzichtspagina.

   De volgende voorbeeldcode voor deze renderer is opgenomen in:

   `apps/Employees/PtoApplication/html.esp`

   ```html
   <html>
     <body>
       <table>
       <tbody>
       <tr>
           <td>
               <h3>Employee Name: <%= currentNode.ename %></h3>
               <h3>Employee ID: <%= currentNode.eid %></h3>
               <h3>Leave duration: <%= currentNode.duration %> days</h3>
               <h3>Reason: <%= currentNode.reason %></h3>
           </td>
       </tr>
       </tbody>
       </table>
     </body>
   </html>
   ```

1. Pas het orkest aan om de vier eigenschappen uit de ingediende formuliergegevens te halen. Na dit creeer een knoop in CRX van type **Werknemers/PtoApplication**, met de bevolkte eigenschappen.

   1. Creeer een proces **creeer PTO samenvatting** en gebruik dit als subprocess alvorens **Taak** verrichting in uw orchestratie toewijst.
   1. Bepaal **employeeName**, **employeeID**, **ptoReason**, **totalDays**, en **nodeName** als inputvariabelen in uw nieuw proces. Deze variabelen worden doorgegeven als verzonden formuliergegevens.

      Bepaal ook een outputvariabele **ptoNodePath** die terwijl het plaatsen van summiere Url wordt gebruikt.

   1. In **creeer PTO summiere** proces, gebruik de **vastgestelde waarde** component om de inputdetails in kaart te plaatsen a **nodeProperty** (**nodeProps**).

      De sleutels in deze kaart zouden het zelfde moeten zijn als de sleutels die in uw HTML renderer in de vorige stap worden bepaald.

      Ook, voeg a **sling toe:resourceType** sleutel met waarde **Werknemers/PtoApplication** in de kaart.

   1. Gebruik subprocess **storeContent** van de **** dienst ContentRepositoryConnector in **creeer PTO summiere** proces. Dit subproces maakt een CRX-knooppunt.

      Er zijn drie invoervariabelen voor nodig:

      * **Weg van de Omslag**: De weg waar de nieuwe knoop van CRX wordt gecreeerd. Stel het pad in op **/content** .
      * **naam van de Knoop**: Wijs input variable nodeName aan dit gebied toe. Dit is een unieke tekenreeks met een knooppuntnaam.
      * **Type van Knoop**: Bepaal het type als **niet:ongestructureerde**. De uitvoer van dit proces is nodePath. Het nodePath is het CRX-pad van het nieuwe knooppunt. NodoPath zou de definitieve output van **zijn creeert PTO** summiere proces.

   1. Geef de voorgelegde vormgegevens (**employeeName**, **employeeID**, **ptoReason**, en **totalDays**) als input tot het nieuwe proces **tot PTO samenvatting**. Neem de output als **ptoSummaryNodePath**.

1. Bepaal de summiere Url als uitdrukking XPath die de serverdetails samen met **bevat ptoSummaryNodePath**.

   XPath: `concat('https://[*server*]:[*port*]/lc',/process_data/@ptoSummaryNodePath,'.html')`.

Wanneer u een taak opent in de AEM Forms-werkruimte, opent de summiere URL het CRX-knooppunt en geeft de HTML-renderer het overzicht weer.

De overzichtslay-out kan worden gewijzigd zonder het proces te wijzigen. De HTML-renderer geeft het overzicht op de juiste wijze weer.
