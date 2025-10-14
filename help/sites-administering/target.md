---
title: Integreren met Adobe Target
description: Leer hoe u Adobe Experience Manager kunt integreren met Adobe Target.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Administering,Personalization
role: Admin
exl-id: d2f5fc90-7047-4a45-9c82-996f0da60782
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '567'
ht-degree: 0%

---

# Integreren met Adobe Target{#integrating-with-adobe-target}

Als deel van Adobe Marketing Cloud, [&#x200B; Adobe Target &#x200B;](https://www.adobe.com/ro/solutions/testing-targeting/testandtarget.html) laat u inhoudsrelevantie door het richten en het meten over alle kanalen verhogen. Adobe Target wordt door marketers gebruikt voor het ontwerpen en uitvoeren van online tests, het maken van on-the-fly publiekssegmenten (gebaseerd op gedrag) en het automatiseren van het richten van inhoud en online ervaringen. AEM heeft de workflow voor het opgeven van doelen overgenomen die wordt gebruikt in Adobe Target Standard. Als u Target gebruikt, bent u bekend met de omgeving voor doelbewerking in AEM.

Integreer uw AEM-sites met Adobe Target om inhoud op uw pagina&#39;s aan te passen:

* Implementeer het richten van inhoud.
* Gebruik Doelpubliek om persoonlijke ervaringen te creëren.
* Contextgegevens naar doel verzenden wanneer bezoekers op uw pagina&#39;s reageren.
* Conversietarieven bijhouden.

Voer de volgende taken uit om met Doel te integreren:

1. [&#x200B; voer in eerste instantie vereiste taken &#x200B;](/help/sites-administering/target-requirements.md) uit: Register met Adobe Target en vorm bepaalde aspecten van de de auteursinstantie van AEM. Uw Adobe Target-account moet minimaal **fiatteur &#x200B;** level-machtigingen hebben. Bovendien moet u de activiteitenmontages op publiceren knoop beveiligen zodat het voor gebruikers ontoegankelijk is.

1. Ofwel:

   1. [&#x200B; Opt in Adobe Target &#x200B;](/help/sites-administering/opt-in.md): De opt-in tovenaar neemt uw de rekeningsinformatie van het Doel en leidt tot een de wolkenconfiguratie van Adobe Target en een Kader van het Doel. De tovenaar associeert ook uw plaatsen met het Kader van het Doel. Als de tovenaar niet met doel kan verbinden, zie het [&#x200B; oplossen van verbindingsprobleem &#x200B;](/help/sites-administering/target-configuring.md#troubleshooting-target-connection-problems) sectie. U kunt dan [&#x200B; de standaardwolkenconfiguraties &#x200B;](/help/sites-administering/target-configuring.md#modifying-the-opt-in-wizard-configurations) wijzigen: Indien noodzakelijk, wijzig de wolkenconfiguratie en het kader dat de opt-in tovenaar creeerde. Wijzig bijvoorbeeld het framework om aanvullende contextgegevens naar Target te verzenden. Als u Adobe Analytics als rapporteringsbron voor Adobe Target wilt gebruiken, moet u de wolkenconfiguratie wijzigen om aan de configuratie A4T te richten.
   1. [&#x200B; integreren manueel met Adobe Target &#x200B;](/help/sites-administering/target-configuring.md#manually-integrating-with-adobe-target).

1. [&#x200B; vorm Activiteiten &#x200B;](/help/sites-authoring/activitylib.md): Verdeel uw Activiteiten met de de wolkenconfiguratie van het Doel.

>[!NOTE]
>
>Zie ook [&#x200B; Integrating AEM met Adobe Target en Adobe Analytics gebruikend DTM &#x200B;](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

>[!NOTE]
>
>Als u Target gebruikt met een aangepaste proxyconfiguratie, moet u zowel de proxyconfiguraties van de HTTP-client configureren als sommige functies van AEM de 3.x-API&#39;s en sommige andere de 4.x-API&#39;s gebruiken:
>
>* 3.x wordt gevormd met [&#x200B; http://localhost:4502/system/console/configMgr/com.day.commons.httpclient](http://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>* 4.x wordt gevormd met [&#x200B; http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](http://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>

>[!CAUTION]
>
>Beveilig de knoop van activiteitenmontages **cq:ActivitySettings** op publiceer instantie zodat het voor normale gebruikers ontoegankelijk is. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.
>
>Zie [&#x200B; Vereisten voor het Integreren met Adobe Target &#x200B;](/help/sites-administering/target-requirements.md#securing-the-activity-settings-node) voor gedetailleerde informatie.

Wanneer de integratie volledig is, kunt u [&#x200B; auteur gerichte inhoud &#x200B;](/help/sites-authoring/content-targeting-touch.md) die bezoekersgegevens naar Adobe Target verzendt. Paginacomponenten hebben specifieke code nodig om het aanwijzen van inhoud mogelijk te maken. (Zie [&#x200B; Ontwikkelen voor gerichte Inhoud &#x200B;](/help/sites-developing/target.md).)

>[!NOTE]
>
>Wanneer u een component in de auteur van AEM richt, maakt de component een reeks server-zijvraag aan Adobe Target om de campagne te registreren, opstellingsaanbiedingen, en de segmenten van Adobe Target terug te winnen (als gevormd). Er worden geen serveraanroepen vanuit AEM naar Adobe Target gepubliceerd.

## Bronnen voor achtergrondinformatie {#background-information-sources}

Voor de integratie van AEM met Adobe Target is kennis van Adobe Target, AEM Activity Management en AEM Audiences Management vereist. U zou met de volgende informatie vertrouwd moeten zijn:

* Adobe Target (zie de [&#x200B; documentatie van Adobe Target &#x200B;](https://experienceleague.adobe.com/docs/target/using/target-home.html?lang=nl-NL)).
* De console van de Activiteiten van AEM (zie [&#x200B; het Leiden Activiteiten &#x200B;](/help/sites-authoring/activitylib.md)).
* Het publiek van AEM (zie [&#x200B; het Leiden Soorten publiek &#x200B;](/help/sites-authoring/managing-audiences.md)).

>[!NOTE]
>
>Als u met Adobe Target werkt, is het volgende het maximumaantal artefacten dat is toegestaan in een campagne:
>
>* 50 locaties
>* 2.000 ervaringen
>* 50 cijfers
>* 50 rapporteringssegmenten
>
