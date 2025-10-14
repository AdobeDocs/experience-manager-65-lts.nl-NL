---
title: Inhoudsfragmenten - Configuratiebrowser
description: Leer hoe u bepaalde functionaliteit voor inhoudsfragmenten in de configuratiegrowser kunt inschakelen voor het gebruik van Adobe Experience Manager-functies voor krachtige koploze levering.
feature: Content Fragments
role: User
solution: Experience Manager, Experience Manager Assets
exl-id: b526cd3a-9b04-403a-a6f4-6abe973aaeac
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 12%

---

# Inhoudsfragmenten - Configuratiebrowser{#content-fragments-configuration-browser}

Leer hoe u bepaalde functies voor inhoudsfragmenten in de configuratiegrowser kunt inschakelen voor het gebruik van Adobe Experience Manager (AEM) met krachtige functies voor koploze weergave.

## Functionaliteit van inhoudsfragment inschakelen voor uw instantie {#enable-content-fragment-functionality-instance}

Alvorens Inhoudsfragmenten te gebruiken, gebruik Browser van de Configuratie **&#x200B;**&#x200B;om het volgende toe te laten:

* **Modellen van het Fragment van de Inhoud** - verplicht
* **de Blijvende Vragen van GraphQL** - facultatief

>[!CAUTION]
>
>Als u niet **Modellen van het Fragment van de Inhoud** toelaat:
>
>* **creeer** optie zal niet beschikbaar voor het creëren van modellen zijn.
>* u kunt niet [&#x200B; de configuratie van Plaatsen selecteren om het verwante eind-punt &#x200B;](/help/sites-developing/headless/graphql-api/graphql-endpoint.md#enabling-graphql-endpoint) tot stand te brengen.

U moet het volgende doen om de functionaliteit van inhoudsfragmenten in te schakelen:

* Het gebruik van de functionaliteit voor inhoudsfragmenten inschakelen via de configuratiebrowser
* De configuratie toepassen op uw Assets-map

### Functionaliteit van inhoudsfragment inschakelen in configuratievenster {#enable-content-fragment-functionality-in-configuration-browser}

Om [&#x200B; bepaalde functionaliteit van het Fragment van de Inhoud &#x200B;](#creating-a-content-fragment-model) te gebruiken, moet u **&#x200B;**&#x200B;eerst hen als **Browser van de Configuratie** toelaten:

>[!NOTE]
>
>Voor meer informatie, zie [&#x200B; Browser van de Configuratie:](/help/sites-administering/configurations.md#using-configuration-browser).

1. Ga naar **Tools**, **Algemeen** en open vervolgens de **Browserconfiguratie**.

1. Het gebruik **creeert** om de dialoog te openen, waar u:

   1. Specificeer a **Titel**.
   1. Om hun gebruik toe te laten selecteer
      * **Modellen van contentfragmenten**
      * **de Blijvende Vragen van GraphQL**

      ![&#x200B; bepaalt configuratie &#x200B;](assets/cfm-conf-01.png)

1. Selecteer **creeer** om de definitie te bewaren.

<!-- 1. Select the location appropriate to your website. -->

### De configuratie toepassen op uw Assets-map {#apply-the-configuration-to-your-assets-folder}

Wanneer de configuratie **globale** voor de functionaliteit van het inhoudsfragment wordt toegelaten, dan op om het even welke omslag van Assets van toepassing is.

Als u andere configuraties (dus exclusief algemene configuraties) wilt gebruiken met een vergelijkbare Assets-map, moet u de verbinding definiëren. U doet dit door de juiste **Configuratie** te selecteren op het tabblad **Cloud Services** van de **Mapeigenschappen** van de juiste map.

![&#x200B; pas configuratie &#x200B;](assets/cfm-conf-02.png) toe
