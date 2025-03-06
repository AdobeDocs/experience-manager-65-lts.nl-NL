---
title: Fouten met betrekking tot CRX/bundle- en Start-paginaservice zijn niet beschikbaar zodra het servicepakket 6.5.15.0 is geïnstalleerd
description: Fouten met betrekking tot CRX/bundle- en Start-paginaservice zijn niet beschikbaar zodra het servicepakket 6.5.15.0 is geïnstalleerd
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms,AEM Forms on JEE,AEM Forms on OSGi
exl-id: f62d526b-9510-4db8-9351-02fd7f192109
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Service unavailable error after installing AEM (6.5.15.0) service pack {#steps-to-resolve-error-after-installing-service-pack}

## Probleem {#issue}

Na het installeren van het 6.5.15.0 de dienstpak van AEM [ ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip), komt de fout als voor:
* FOUT [ FelixDispatchQueue ] org.apache.sling.scripting.console FrameworkEvent FOUT (org.osgi.framework.BundleException: Onbekwaam om org.apache.sling.scripting.console op te lossen

Na de installatie van de AEM 6.5.15.0 -service worden de CRX/bundle en de startpagina weergegeven met onbeschikbare fouten.

## Van toepassing op {#applies-to}

Deze oplossing geldt voor:
* AEM Forms op alle JEE-servers, behalve op JBoss EAP 7.4.0

## Oplossing {#solution}

>[!NOTE]
>
>De stappen voor probleemoplossing zijn van toepassing op alle toepassingsservers behalve JBoss EAP 7.4.

Na het installeren van [ AEM 6.5.15.0 de dienstpak ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/aem-service-pkg-6.5.15.0.zip), als CRX/bundel en de beginpagina de dienst niet beschikbare fouten tonen, voer de volgende stappen uit:

1. Stop de toepassingsserver.
1. Navigeer naar `[aem-forms root]\crx-repository\launchpad\felix\bundle52` .
1. Zoek het `bundle.info` -bestand.
1. Open het `bundle.info` -bestand in een teksteditor en zoek naar de bundelnaam als `org.apache.felix.http.bridge` .

   >[!NOTE]
   >
   >Als `bundle.info` under `bundle52` niet de `org.apache.felix.http.bridge` -bundel bevat, controleert u het bundelnummer tussen vierkante haken naast `org.apache.felix.http.bridge` . Dan navigeer aan [ aem-vormen wortel ] \crx-repository\launchpad\felix\bundle [ x ] en voer de volgende stappen bij deze plaats uit.

1. Ga naar URL: `[aem-forms root]\crx-repository\launchpad\felix\bundle[x]\version0.1` .
1. Zoek naar `bundle.jar` en noem `bundle.jar` to `bundle.jar.bak` anders.
1. Kopieer `Bundle for AEM 6.5 Forms on JEE Service Pack 15` bij deze plaats van de [ Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/bundle.jar).
1. Start de toepassingsserver, wacht tot de logbestanden zijn gestabiliseerd en controleer de toestand van de bundel.
1. Zodra alle bundels in de actieve staat zijn, installeer het [ Fragment voor AEM 6.5 Forms op JEE Service Pack 15 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/featurepack/org.apache.felix.http.servlet-api-1.2.0_fragment_full.jar) van `system/console/bundles` en wacht op de toepassingsserver om te stabiliseren.
1. Stop de toepassingsserver.
1. Navigeer naar `[aem-forms root]\crx-repository\launchpad\felix\bundle52\version0.1` en verwijder de `bundle.jar` .
1. Wijzig de naam van de `bundle.jar.bak` in de `bundle.jar` .
1. Start de toepassingsserver.
