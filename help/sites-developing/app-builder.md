---
title: Uitbreidend  [!DNL Adobe Experience Manager]  6.5 gebruikend Adobe Developer App Builder.
description: Uitbreidend  [!DNL Adobe Experience Manager]  6.5 gebruikend Adobe Developer App Builder.
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: f9b3df58-c94b-4143-aeec-85ff031bac2e
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '519'
ht-degree: 0%

---

# [!DNL Adobe Experience Manager] uitbreiden met Adobe Developer App Builder {#extend-using-app-builder}

## Wat is App Builder voor AEM {#project-appbuilder}

De nieuwe Adobe Developer App Builder biedt een uitbreidbaarheidskader voor een ontwikkelaar om de functies van AEM eenvoudig uit te breiden.

App Builder biedt een uniform uitbreidbaarheidskader van derden voor het integreren en maken van aangepaste ervaringen die Adobe Experience Manager uitbreiden. Met dit complete uitbreidingsframework, gebaseerd op de Adobe-infrastructuur, kunnen ontwikkelaars aangepaste microservices bouwen, Adobe Experience Manager uitbreiden en integreren in Adobe-oplossingen en de rest van de IT-stack.

App Builder biedt klanten de mogelijkheid om Adobe Experience Manager in verschillende gebruiksgevallen eenvoudig uit te breiden:

* Middleware-uitbreidbaarheid: sluit externe systemen aan met Adobe-toepassingen die aangepaste connectors maken of een pakket van vooraf gebouwde integraties gebruiken.
* De Uitbreidbaarheid van de Diensten van de kern - breid kerntoepassingsmogelijkheden door het standaardgedrag met douaneeigenschappen &amp; bedrijfslogica uit te breiden.
* Gebruikerservaring Uitbreidbaarheid: breid de kernervaring uit om bedrijfsvereisten te ondersteunen of klantspecifieke digitale eigenschappen, winkelcentra en back-office toepassingen te ontwikkelen.

App Builder is sinds zomer 2020 beschikbaar voor zakelijke klanten en partners via Adobe Developer Preview. De algemene beschikbaarheid (GA) van App Builder is gepland voor december 2021. Adobe verwelkomt ontwikkelaars om App Builder door Adobe [ Proefprogramma ](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/set-up#access-and-credentials) uit te proberen.

>[!NOTE]
>
>Voor klanten van AEM as a Cloud Service, die App Builder willen gebruiken, zie [ Uitbreidend Adobe Experience Manager as a Cloud Service gebruikend Adobe Developer App Builder ](/help/sites-developing/app-builder.md).

## Architectuur {#architecture}

Adobe Developer App Builder biedt in plaats van een out-of-the-box oplossing een gemeenschappelijk, consistent, gestandaardiseerd ontwikkelingsplatform voor het uitbreiden van Adobe Cloud-oplossingen zoals AEM, met inbegrip van:

* Adobe Developer Console — Voor de ontwikkeling van aangepaste microservices en extensies kunnen ontwikkelaars projecten maken en beheren en tegelijk toegang krijgen tot alle hulpmiddelen en API&#39;s die ze nodig hebben om plug-ins en integratie te maken.
* Gereedschappen voor ontwikkelaars — Open-source-gereedschappen, SDK&#39;s en bibliotheken waarmee ontwikkelaars eenvoudig aangepaste extensies en integratie kunnen maken. Gebruik de React Spectrum (de toolkit van de UI van Adobe) om één gemeenschappelijke UI voor alle Adobe apps te hebben.
* Services — I/O-runtime voor het hosten van infrastructuren op Adobe-serverplatform en I/O-gebeurtenissen voor op gebeurtenissen gebaseerde integratie. Adobe biedt ook offline ondersteuning voor het opslaan van gegevens en bestanden.
* Adobe Experience Cloud — Ontwikkelaars kunnen extensies en integraties indienen voor publicatie binnen hun Experience Cloud Org. Systeembeheerders kunnen deze extensies vervolgens controleren, beheren en goedkeuren. Na publicatie vindt u naast andere Adobe Experience Cloud-apps ook aangepaste App Builder-extensies en -gereedschappen.

In het volgende diagram ziet u hoe een standaardtoepassing die op App Builder is gebouwd deze functies gebruikt:

![Architectuur](assets/appbuilder-architecture.jpg)

Voor meer details over de architectuur van App Builder, heb een blik bij [ Overzicht van de Architectuur ](https://developer.adobe.com/app-builder/docs/guides/app_builder_guides/architecture_overview/architecture-overview).

## Aan de slag met App Builder {#additional-resources}

Om u te helpen aan de slag te gaan met App Builder, is een aantal documentatie gemaakt waarmee u kunt beginnen:

* [ Aan de slag App Builder ](https://developer.adobe.com/app-builder/docs/get_started/app_builder_get_started/first-app)

## Doorgaan met leren met documentatie {#appbuilder-documentation}

App Builder biedt video&#39;s en documentatie voor ontwikkelaars, waaronder hulplijnen en documentatie voor naslagwerken, waarmee u uw eigen aangepaste toepassingen kunt ontwikkelen:

* [ documentatie van App Builder ](https://developer.adobe.com/app-builder/docs/overview/)
* [ de video&#39;s van App Builder ](https://www.youtube.com/playlist?list=PLcVEYUqU7VRfDij-Jbjyw8S8EzW073F_o)

## Een van de voorbeeldtoepassingen uitproberen {#appbuilder-codesamples}

Klaar om te beginnen met ontwikkelen? Er zijn veel voorbeeldtoepassingen waarmee u snel aan de slag kunt:

* [ de Etiketten van de Code van App Builder op de Website van Adobe Developer ](https://developer.adobe.com/app-builder/docs/resources/)
