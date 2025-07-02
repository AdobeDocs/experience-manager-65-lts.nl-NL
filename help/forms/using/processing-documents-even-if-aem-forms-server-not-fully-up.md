---
title: AEM Forms Server begint de documenten te verwerken, zelfs voordat alle services actief zijn.
description: De Server van AEM Forms begint de documenten zelfs te verwerken alvorens alle diensten op Server JEE en Server OSGi in werking zijn.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 22dd8daa-b8c6-4e7d-bca3-3958a79fb4b5
source-git-commit: 402b42d8ce5539739205a85d99bcb035d382a036
workflow-type: tm+mt
source-wordcount: '110'
ht-degree: 0%

---

# AEM Forms Server begint de documenten te verwerken, zelfs voordat alle services zijn gestart{#aem-forms-server-start-processing-documents-even-if-it-is-not-fully-up}

## Probleem {#issue}

<!--When user restarts AEM Forms server, the current calling processes or services still continue such as rendering PDF documents and more. It causes the restart of the AEM Forms server to not startup correctly.-->

Voordat de AEM Forms-server volledig is geactiveerd en alle toepassingen actief zijn, begint AEM Forms Server met het verwerken van de documenten.


## Van toepassing op {#applies-to}

De oplossing is van toepassing op AEM Forms op JEE Server en AEM Forms op OSGi Server.

## Oplossing {#solution}

Om de kwestie op te lossen, voeg een argument `Dcom.adobe.livecycle.dsc.deferServiceStart=true` aan het [ partijdossier ](/help/sites-deploying/command-line-start-and-stop.md#windows-platform-start-bat-script-example) tijdens serveropstarten toe.
