---
title: IMS-integratie instellen voor AEM
description: Meer informatie over het instellen van IMS-integratie voor AEM
feature: Security
role: Admin
exl-id: 05ba39fc-4b53-43c0-9a9f-7da3293b1ca2
source-git-commit: 929a2175449a371ecf81226fedb98a0c5c6d7166
workflow-type: tm+mt
source-wordcount: '397'
ht-degree: 1%

---

# IMS-integratie instellen voor AEM {#setting-up-ims-integrations-for-aem}


>[!NOTE]
>
>De klanten van Adobe gebruiken [ Adobe Developer Console ](https://developer.adobe.com/console) om geloofsbrieven te produceren die toegang tot diverse APIs toelaten. Klanten kiezen uit verschillende soorten referentie, variërend van OAuth Server-to-Server tot Single-Page App. Het referentietype Service Account (JWT) is nu vervangen door de OAuth Server-to-Server-referenties.

Adobe Experience Manager (AEM) kan met vele andere oplossingen van Adobe worden geïntegreerd. Bijvoorbeeld Adobe Target, Adobe Analytics en andere.

De integratie gebruikt een integratie IMS, die met S2S OAuth wordt gevormd.

* Nadat u hebt gemaakt:

   * [ Geloofsbrieven in Developer Console ](#credentials-in-the-developer-console)

* Dan kunt u:

   * Creeer a (nieuw) [ configuratie OAuth ](#creating-oauth-configuration)

   * [Een bestaande JWT-configuratie migreren naar een OAuth-configuratie](#migrating-existing-JWT-configuration-to-oauth)

>[!CAUTION]
>
>Eerder, werden de configuraties gemaakt met [ Credentials JWT die nu onderworpen aan afschrijving in Adobe Developer Console ](/help/sites-administering/jwt-credentials-deprecation-in-adobe-developer-console.md) zijn.
>
>Dergelijke configuraties kunnen niet meer worden gemaakt of bijgewerkt, maar kunnen worden gemigreerd naar OAuth-configuraties.

## Referenties in de Developer Console {#credentials-in-the-developer-console}

Als eerste stap, moet u de geloofsbrieven OAuth in Adobe Developer Console vormen.

Raadpleeg de documentatie bij Developer Console voor meer informatie over het uitvoeren van deze configuratie, afhankelijk van uw vereisten:

* Overzicht:

   * [ Server aan de authentificatie van de Server ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

* Een nieuwe OAuth-referentie maken:

   * [ OAuth Server-aan-Server de gids van de credentieimplementatie ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

* Een bestaande JWT-referentie migreren naar een OAuth-referentie:

   * [ migrerend van de Rekening van de Dienst (JWT) credential aan OAuth Server-aan-Server credential ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration)

Bijvoorbeeld:

![ Referentie OAuth in Developer Console ](assets/ims-configuration-developer-console.png)

## Een OAuth-configuratie maken {#creating-oauth-configuration}

Een nieuwe Adobe IMS-integratie maken met OAuth:

1. In AEM, navigeer aan **Hulpmiddelen**, **Veiligheid**, **Integratie van Adobe IMS**.

1. Selecteer **creeer**.

1. Voltooi de configuratie die op details van [ wordt gebaseerd Developer Console ](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation). Bijvoorbeeld:

   ![ creeer OAuth Configuratie ](assets/ims-create-oauth-configuration.png)

1. **sparen** uw veranderingen.

## Een bestaande JWT-configuratie migreren naar een OAuth-configuratie {#migrating-existing-JWT-configuration-to-oauth}

Een bestaande Adobe IMS-integratie migreren op basis van JWT-referenties:

>[!NOTE]
>
>Dit voorbeeld toont een Configuratie van IMS van de Lancering.

1. In AEM, navigeer aan **Hulpmiddelen**, **Veiligheid**, **Integratie van Adobe IMS**.

1. Selecteer de JWT-configuratie die moet worden gemigreerd. De configuraties JWT zijn duidelijk met de waarschuwing **(afgekeurde) Credentials JWT**.

1. Selecteer **Eigenschappen**:

   ![ Uitgezochte Configuratie JWT ](assets/ims-migrate-jwt-select-configuration.png)

1. De configuratie wordt als alleen-lezen geopend:

   ![ Eigenschappen van de Configuratie - slechts-lezen ](assets/ims-migrate-jwt-properties-read-only.png)

1. Selecteer **OAuth** van het **Type van Authentificatie** dropdown:

   ![ Uitgezochte Type van Authentificatie ](assets/ims-migrate-jwt-authentication-type.png)

1. De beschikbare eigenschappen worden bijgewerkt. Voer de gegevens van de Developer Console in om deze in te vullen:

   ![ Volledige details OAuth ](assets/ims-migrate-jwt-complete-oauth-details.png)

1. Gebruik **sparen &amp; sluit** om uw updates voort te zetten.
Wanneer u aan de console terugkeert, is de **(afgekeurde)** waarschuwing JWT.
