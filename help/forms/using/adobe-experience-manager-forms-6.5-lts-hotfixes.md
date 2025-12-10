---
title: Adobe Experience Manager Forms 6.5 LTS SP1-hotfixes
description: Hier vindt u informatie over het downloaden en installeren van een hotfix voor AEM Forms 6.5 LTS.
exl-id: 37287332-3c8d-4ddc-a77e-3c5ee332898b
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
source-git-commit: 7ea96536f3047e31f4d2122a61def2b068757d6a
workflow-type: tm+mt
source-wordcount: '251'
ht-degree: 0%

---

# Adobe Experience Manager Forms 6.5 LTS-hotfixes{#aem-form-hotfix}

Dit artikel bevat een overzicht van de kritieke oplossingen die zijn geïmplementeerd om bekende problemen aan te pakken, de stabiliteit van het systeem te verbeteren en de algehele prestaties van AEM Forms 6.5 LTS te verbeteren.

>[!NOTE]
>
> De hotfixes zijn cumulatief ontworpen en omvatten alle voorafgaande fixes. Wanneer u de nieuwste hotfix toepast op een release, wordt niet alleen het meest recente probleem opgelost, maar worden ook alle eerdere correcties en verbeteringen aangebracht.

## Hotfixes voor AEM Forms 6.5 LTS {#hotfix-for-aem-forms}

<table>
  <tbody>
  <tr>
    <td><strong>Datum</strong></td>
    <td><strong>Hotfix-downloadkoppeling (AEM-koppeling voor softwaredistributie)</strong></td>
    <td><strong>Opgeloste problemen</strong></td>
  </tr>
  <tr>
    <td>
      <strong> september 09, 2025 </strong><br>
    <td>
    <ul>
    <li>Vensters - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-win-pkg-6.1.176-RHF-002.zip"> Hotfix2 voor AEM Service Pack 6.5 LTS op Vensters </a></li>
    <li>Linux - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]hotfix-on-add-on/adobe-aemfd-linux-pkg-6.1.176-RHF-002.zip"> Hotfix2 voor AEM Service Pack 6.5 LTS op Linux </a></li>
     <li>MacOS - <a href="https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?pack[...]1-hotfix-on-add-on/adobe-aemfd-osx-pkg-6.1.176-RHF-002.zip"> Hotfix2 voor AEM Service Pack 6.5 LTS op MacOS </a></li>
    <td>
    <ul>
    <li>Verbeterde betrouwbaarheid voor het verzenden van formulieren door een probleem op te lossen waarbij verzending kan mislukken als Server-Side Validation (SSV) is ingeschakeld. Neem contact op met de [Adobe Experience Manager Forms Support] (https://business.adobe.com/in/support/main.html)
    </li>
    </ul>
    </td>    
  </tr>
    </ul>
    </td>    
  </tr>
  <tbody>
</table>


## Een OSGi Hotfix downloaden en installeren {#download-install-hotfix}

Voer de volgende stappen uit om de hotfix te downloaden en installeren:

1. Download [&#x200B; Hotfix &#x200B;](#hotfix-for-adaptive-forms) van de verbinding van de Distributie van de Software.
1. Extraheer het Hotfix-archiefbestand zodat u een Experience Manager-pakket (.zip) en -bundelbestanden (.jar) kunt verkrijgen.
1. Upload en installeer het pakket (.zip) via de [&#x200B; Manager van het Pakket &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/content/sites/administering/contentmanagement/package-manager.html?lang=es#accessing).
1. Open de bundels voor configuratiebeheer `https://server:host/system/console/bundles`, upload en installeer de bundel (.jar). De hotfix is geïnstalleerd.
