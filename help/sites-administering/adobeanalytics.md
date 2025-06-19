---
title: Integreren met Adobe Analytics
description: Leer hoe u Adobe Experience Manager (AEM) kunt integreren met Adobe Analytics.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 4f7e1794-af5a-45a2-8dc6-80029c47caeb
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '249'
ht-degree: 20%

---

# Integreren met Adobe Analytics{#integrating-with-adobe-analytics}

Door Adobe Analytics en AEM te integreren, kunt u de activiteiten van uw webpagina volgen:

* Met een Adobe Analytics-configuratie kan AEM verifiëren met Adobe Analytics.
* Een framework geeft de gegevens aan die naar uw Adobe Analytics-rapportenpakket worden verzonden.

De gegevens bevatten pagina- en gebruikersgegevens, bijvoorbeeld:

* gegevens die door AEM-componenten worden verzameld
* koppelingsklikken
* videogebruiksinformatie
* het aantal pagina-bezoeken van Adobe Analytics

Met de volgende pagina&#39;s kunt u de integratie configureren:

* [Verbinding maken met Adobe Analytics en frameworks maken](/help/sites-administering/adobeanalytics-connect.md)
* [Koppeling bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-link.md)
* [Componentgegevens toewijzen aan Adobe Analytics-eigenschappen](/help/sites-administering/adobeanalytics-mapping.md)
* [Video bijhouden configureren voor Adobe Analytics](/help/sites-administering/adobeanalytics-video.md)
* [Adobe-classificaties](/help/sites-administering/adobeanalytics-classifications.md)

U kunt [ Opt-binnen tovenaar ](/help/sites-administering/opt-in.md) ook gebruiken om de integratie gemakkelijk uit te voeren.

>[!NOTE]
>
>Zie ook hoe te artikel: [ Integrating AEM met Adobe Target en Adobe Analytics gebruikend DTM ](https://helpx.adobe.com/experience-manager/using/integrate-digital-marketing-solutions.html).

## Aanvullende informatie {#further-information}

Zie:

* [ Uitbreidend de Integratie van Adobe Analytics ](/help/sites-developing/extending-analytics.md) voor informatie over het ontwikkelen van componenten die gebruikersgegevens verzamelen en het kader van Adobe Analytics aanpassen.

>[!NOTE]
>
>Als u Adobe Analytics gebruikt met een aangepaste proxyconfiguratie, moet u [twee OSGi-bundels configureren](/help/sites-deploying/configuring-osgi.md) (bijvoorbeeld met de webconsole) die voor de **Apache HTTP Client**-proxyconfiguraties vereist zijn. Beide zijn vereist omdat sommige functies van AEM de 3.x-API&#39;s gebruiken, terwijl andere de 4.x-API&#39;s gebruiken. Configureren:
>
>* **Cliënt 3.1 van HTTP van de Commons van de Dag 3.x** om 3.x API te vormen;
>  >  bijvoorbeeld, [ https://localhost:4502/system/console/configMgr/com.day.commons.httpclient](https://localhost:4502/system/console/configMgr/com.day.commons.httpclient)
>
>* **Apache de Configuratie van de Volmacht van HTTP Componenten** om 4.x API te vormen;
>  >  bijvoorbeeld, [ https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator](https://localhost:4502/system/console/configMgr/org.apache.http.proxyconfigurator)
>
