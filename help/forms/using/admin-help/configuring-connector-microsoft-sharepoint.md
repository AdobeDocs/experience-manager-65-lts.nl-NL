---
title: Connector configureren voor Microsoft SharePoint
description: Configureer Connector voor Microsoft SharePoint om communicatie tussen AEM-formulieren en Microsoft SharePoint mogelijk te maken.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: d1575576-3a05-496c-b683-bb5badc02711
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '214'
ht-degree: 0%

---

# Connector configureren voor Microsoft SharePoint {#configuring-connector-for-microsoft-sharepoint}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Connector voor Microsoft SharePoint maakt communicatie mogelijk tussen AEM-formulieren en Microsoft SharePoint. Voor extra achtergrondinformatie, zie &quot;Connectors voor ECM&quot;in [&#x200B; Verwijzing van de Diensten &#x200B;](https://www.adobe.com/go/learn_aemforms_services_63).

1. Klik in de beheerconsole op Services > Connector voor Microsoft SharePoint.
1. Geef de volgende instellingen op voor uw SharePoint-server:

   **de Naam van de Gastheer van de Server van SharePoint:** het de havenaantal van de gastheernaam van de Webtoepassing op de server van SharePoint, in het formaat `[hostname]:'port'`.

   **Naam van de Gebruiker:** De gebruikersrekening die wordt gebruikt om met de server van SharePoint te verbinden.

   **Wachtwoord:** Wachtwoord voor de gebruikersrekening die wordt gebruikt om met de server van SharePoint te verbinden

   **Naam van het Domein:** Domein waar de server van SharePoint wordt gevestigd.

1. Klik op Opslaan.

## Microsoft SharePoint-configuratieservice {#microsoft-sharepoint-configuration-service}

Met de Microsoft SharePoint-configuratieservice `(MSSharePointConfigService)` kunt u referenties opgeven voor de gebruiker van AEM-formulieren die imitatierechten heeft. Voor informatie over imitatierechten, zie [&#x200B; het Vormen Schakelaar voor Microsoft SharePoint &#x200B;](https://help.adobe.com/en_US/AEMForms/6.1/SharePointConfig/index.html). Voer de volgende stappen uit om instellingen op te geven voor `MSSharePointConfigService` :

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Navigeer in de lijst met services en klik op `MSSharePointConfigService` .
1. Specificeer de volgende montages op de pagina van de Configuratie:

   * Gebruikersnaam voor een gebruiker met imitatierechten
   * Wachtwoord voor bovenstaande gebruiker

1. Klik op Opslaan.
