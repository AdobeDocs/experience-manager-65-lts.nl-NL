---
title: AEM DS-instellingen configureren
description: Leer hoe u de URL van de verwerkingsserver opgeeft voordat u een formulier verzendt.
contentOwner: amgoyal
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
docset: aem65
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 8ad3afd6-e1c6-4f21-bb0f-4d97ef50710e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# AEM DS-instellingen configureren{#configuring-aem-ds-settings}

Dit artikel beschrijft hoe te om de **dienst van de Montages van AEM DS** te vormen. Deze instelling kan in meerdere scenario&#39;s worden gebruikt, bijvoorbeeld:

* In het Correspondentenbeheer

   * Voor het configureren van de AEM Forms-workflow
   * Tijdens het gebruik van de Forms Portal voor het op afstand opslaan van concepten/verzendingen

* In adaptieve formulieren, voor gevallen waarin een adaptief formulier wordt ingediend vanuit een publicatie-instantie

Hier volgen de stappen voor het configureren van de **[!UICONTROL AEM DS Settings]** :

1. Open de Manager van de Configuratie op publiceer instantie gebruikend URL:\
   *https://localhost:port/system/console/configMgr*.

   ![&#x200B; Configuratie van de Console van het Web van AEM &#x200B;](assets/web_configuration_console_new.png)

1. Zoek in het **[!UICONTROL Adobe Experience Manager Web Console Configuration]** -venster de optie **[!UICONTROL AEM DS Settings]** en klik erop.

   ![&#x200B; DS Montages &#x200B;](assets/ds_settings_new.png)

1. In het venster **[!UICONTROL AEM DS Settings Service]** worden de algemene configuratie-instellingen voor AEM DS Components weergegeven.

   ![&#x200B; DS de Dienst van Montages &#x200B;](assets/ds_settings_service_new.png)

1. Voeg de volgende informatie in de respectieve gebieden toe:

   **[!UICONTROL Processing Server URL]**: De Verwerkingsserver is de server waarop de Forms- of AEM-workflow moet worden geactiveerd. Dit kan hetzelfde zijn als de URL van de AEM-auteurinstantie of de andere Server-URL (https://localhost:port/).

   **[!UICONTROL Processing Server User Name]**: De Naam van de Gebruiker van het werkschema gebruiker [ gebaseerd op de server URL die wordt gebruikt ]

   **[!UICONTROL Processing Server Password]**: Wachtwoord workflowgebruiker

   >[!NOTE]
   >
   >
   >    
   >    
   >    * Voordat u Forms- of AEM-workflows gebruikt, moet u eerst de service voor DS-instellingen configureren, voordat u gegevens van de publicatieserver kunt verzenden. Anders zal de indiening van het formulier mislukken.
   >    
   >
