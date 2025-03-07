---
title: AEM Forms configureren voor het verzenden van gegevens naar een AEM Forms on JEE-proces
description: Aangepaste formulieren integreren met AEM Forms in JEE-processen voor de verwerking van formuliergegevens.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: c888da5d-6a98-4139-9656-a187177efcb0
hide: true
hidefromtoc: true
source-git-commit: 1336ccddcc73459f933e5e4b00a3a22605cdb9a1
workflow-type: tm+mt
source-wordcount: '318'
ht-degree: 0%

---

# AEM Forms configureren om formuliergegevens via JEE naar een AEM-formulier te verzenden{#configuring-aem-forms-to-submit-form-data-to-an-aem-forms-on-jee-process}

Adaptieve formulieren ondersteunen het verzenden van gegevens naar AEM Forms over JEE-processen voor verdere verwerking. Hiermee kunt u een AEM Forms on JEE-proces activeren met de gegevens die beschikbaar zijn in het verzonden formulier. Voer de volgende stappen uit zodat u uw AEM Forms-exemplaar kunt inschakelen om een adaptief formulier naar AEM Forms te verzenden tijdens het JEE-proces:

## AEM Forms-server configureren {#configure-your-aem-forms-server}

Voer de volgende stappen uit zodat u uw AEM Forms Server kunt inschakelen om gegevens naar een AEM Forms op de JEE-server te verzenden:

1. Ga naar de console van de Webconfiguratie van AEM in https:// [*gastheer*]:[*haven*]/system/console/configMgr.

1. Bepaal en klik de **component van de Configuratie van de Cliënt van Adobe LiveCycle van SDK**.
1. Klik hierop om de URL van de configuratieserver, de gebruikersnaam en het wachtwoord voor de AEM Forms op de JEE-server te bewerken.
1. Herzie de montages en klik **sparen**.

![ Adobe LiveCycle Client SDK configuratie ](assets/clientsdkconfiguration.jpg)

## Gegevens toewijzen aan procesvelden {#map-data-with-process-fields}

Nadat u AEM Forms hebt geconfigureerd, wijst u de XML-gegevens en bijlagen van het verzonden formulier toe aan de velden in het AEM Forms on JEE-proces. Ga als volgt te werk:

1. In de console van de het Webconfiguratie van AEM, klik om de **Locator van het Proces van de Gids LiveCycle en de Configuratie van de Invoker** uit te geven.
1. Geef de volgende parameters op:

   * **Naam van de gegevensxml parameter** (verplicht): specificeer het het bezitsdossier van XML van AEM Forms op proces JEE dat de voorgelegde gegevens moet verwerken. De standaardwaarde is dataxml ****.

   * **Naam van de parameter van dossiergehechtheid** (facultatief): specificeer de lijst van documentvoorwerpen die AEM Forms op JEE proces moet verwerken. De standaardwaarde is **fileAttachmentsList**.

1. Herzie de montages en klik **sparen**.

![ het Locator en de Invoker van het Proces van de Gids LiveCycle ](assets/test3.jpg)

Als deze optie eenmaal is geconfigureerd, wordt bij Verzenden naar Forms Workflow de AEM Forms op JEE-serverprocessen weergegeven die de opgegeven XML-gegevensparameter bevatten.
