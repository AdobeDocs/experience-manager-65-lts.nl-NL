---
title: Microsoft Dynamics OData-configuratie
description: Leer gebruiken, integreren, en werken met online en op-gebouw de diensten van Microsoft Dynamics door het model van vormgegevens.
topic-tags: integration
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Form Data Model
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 6c3c4d7f-fc4c-44ad-886f-f76d0532d91a
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1195'
ht-degree: 0%

---

# Microsoft Dynamics OData-configuratie{#microsoft-dynamics-odata-configuration}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/ms-dynamics-odata-configuration.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |

![ gegeven-integratie ](assets/data-integeration.png)

Microsoft Dynamics is een software van het Beheer van de Verhouding van de Klant (CRM) en van de Planning van het Middel van de Onderneming (ERP) die ondernemingsoplossingen voor het creëren van en het beheren van klantenrekeningen, contacten, lood, kansen, en gevallen verstrekt. [ de Integratie van Gegevens van AEM Forms ](../../forms/using/data-integration.md) verstrekt een configuratie van de wolkendienst OData om Forms met zowel online als op-gebouw de server van Microsoft Dynamics te integreren. Hiermee kunt u een formuliergegevensmodel maken op basis van de entiteiten, kenmerken en services die zijn gedefinieerd in de Microsoft Dynamics-service. Het formuliergegevensmodel kan worden gebruikt om adaptieve formulieren te maken die communiceren met de Microsoft Dynamics-server om bedrijfsworkflows mogelijk te maken. Bijvoorbeeld:

* Query uitvoeren op Microsoft Dynamics-server voor gegevens en aangepaste formulieren vooraf invullen
* Gegevens naar Microsoft Dynamics schrijven wanneer het formulier adaptief wordt verzonden
* Gegevens schrijven in Microsoft Dynamics via aangepaste entiteiten die zijn gedefinieerd in het formuliergegevensmodel, en omgekeerd

Het AEM Forms-add-on-pakket bevat ook een referentie OData-configuratie die u kunt gebruiken om Microsoft Dynamics snel met AEM Forms te integreren.

Wanneer het pakket is geïnstalleerd, zijn de volgende entiteiten en services beschikbaar op uw AEM Forms-exemplaar:

* MS Dynamics OData Cloud Service (OData Service)
* Formuliergegevensmodel met vooraf geconfigureerde Microsoft Dynamics-entiteiten en -services.

Vooraf geconfigureerde Microsoft Dynamics-entiteiten en -services in een formuliergegevensmodel zijn alleen beschikbaar op uw AEM Forms-exemplaar als de uitvoermodus voor de AEM-instantie is ingesteld op `samplecontent` (standaard). MS Dynamics OData Cloud Service (OData Service) is ook beschikbaar in andere uitvoeringsmodi. Voor meer informatie bij het vormen looppaswijzen voor een instantie van AEM, zie [ Wijzen van de Looppas ](/help/sites-deploying/configure-runmodes.md).

## Vereisten {#prerequisites}

Voordat u begint met het instellen en configureren van Microsoft Dynamics, moet u ervoor zorgen dat:

* Geïnstalleerd het [ toe:voegen-op pakket van AEM Forms ](../../forms/using/installing-configuring-aem-forms-osgi.md)
* Microsoft Dynamics 365 is online geconfigureerd of heeft een exemplaar van een van de volgende Microsoft Dynamics-versies geïnstalleerd:

   * Microsoft Dynamics 365 ter plaatse
   * Microsoft Dynamics 2016 ter plaatse

* [ registreerde de toepassing voor de online dienst van Microsoft Dynamics met Microsoft Azure Actieve Folder ](https://docs.microsoft.com/en-us/dynamics365/customer-engagement/developer/walkthrough-register-dynamics-365-app-azure-active-directory). Noteer de waarden voor de client-id (ook toepassings-id genoemd) en het clientgeheim voor de geregistreerde service. Deze waarden worden gebruikt terwijl [ het vormen de wolkendienst voor uw dienst van Microsoft Dynamics ](../../forms/using/ms-dynamics-odata-configuration.md#configure-cloud-service-for-your-microsoft-dynamics-service).

## Reactie-URL instellen voor geregistreerde Microsoft Dynamics-toepassing {#set-reply-url-for-registered-microsoft-dynamics-application}

Ga als volgt te werk om de antwoordURL voor geregistreerde Microsoft Dynamics-toepassingen in te stellen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van AEM Forms met de online Microsoft Dynamics-server.

1. Ga naar Microsoft Azure Actieve rekening van de Folder en voeg de volgende URL van de de dienstconfiguratie van de wolk in **Reageer URLs** montages voor uw geregistreerde toepassing toe:

   `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

   ![ Azure folder ](assets/azure_directory_new.png)

1. Sla de configuratie op.

## Microsoft Dynamics voor IFD configureren {#configure-microsoft-dynamics-for-ifd}

Microsoft Dynamics gebruikt op claims gebaseerde verificatie om externe gebruikers toegang te bieden tot gegevens op de Microsoft Dynamics CRM-server. Om dit toe te laten, doe het volgende Microsoft Dynamics voor Internet-Onder ogen ziet plaatsing (IFD) vormen en claimmontages vormen.

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van AEM Forms met de Microsoft Dynamics-server op locatie.

1. Vorm Microsoft Dynamics op-gebouw instantie voor IFD zoals die in [ wordt beschreven vorm IFD voor Microsoft Dynamics ](https://technet.microsoft.com/en-us/library/dn609803.aspx).
1. Stel de volgende bevelen in werking gebruikend Vensters PowerShell om claimmontages op IFD-Toegelaten Microsoft Dynamics te vormen:

   ```shell
   Add-PSSnapin Microsoft.Crm.PowerShell
    $ClaimsSettings = Get-CrmSetting -SettingType OAuthClaimsSettings
    $ClaimsSettings.Enabled = $true
    Set-CrmSetting -Setting $ClaimsSettings
   ```

   Zie [ registratie van de app voor CRM op-gebouw (IFD) ](https://msdn.microsoft.com/sl-si/library/dn531010(v=crm.7).aspx#bkmk_ifd) voor details.

## OAuth-client configureren op AD FS-computer {#configure-oauth-client-on-ad-fs-machine}

Doe het volgende om een cliënt OAuth op de Actieve machine van de Diensten van de Federatie van de Folder (AD FS) te registreren en toegang op de machine van het ADS te verlenen:

>[!NOTE]
>
>Gebruik deze procedure alleen tijdens de integratie van AEM Forms met de Microsoft Dynamics-server op locatie.

1. Voer de volgende opdracht uit:

   `Add-AdfsClient -ClientId "<Client-ID>" -Name "<name>" -RedirectUri "<redirect-uri>" -GenerateClientSecret`

   Waarbij:

   * `Client-ID` is een cliëntID u het gebruiken van om het even welke generator kunt produceren GUID.
   * `redirect-uri` is de URL naar de Microsoft Dynamics OData-cloudservice op AEM Forms. De standaardcloudservice die wordt geïnstalleerd met het AEM Forms-pakket, wordt geïmplementeerd op de volgende URL:

     `https://'[server]:[port]'/libs/fd/fdm/gui/components/admin/fdmcloudservice/createcloudconfigwizard/cloudservices.html`

1. Voer de volgende opdracht uit om toegang te verlenen op de AD FS-computer:

   `Grant-AdfsApplicationPermission -ClientRoleIdentifier "<Client-ID>" -ServerRoleIdentifier <resource> -ScopeNames openid`

   Waarbij:

   * `resource` is de Microsoft Dynamics-organisatie-URL.

1. Microsoft Dynamics gebruikt het HTTPS-protocol. Als u AD FS-eindpunten wilt aanroepen vanaf de Forms-server, installeert u Microsoft Dynamics-sitecertificaat naar het Java-certificaatarchief met de opdracht `keytool` op de computer waarop AEM Forms wordt uitgevoerd.

## Cloudservice configureren voor uw Microsoft Dynamics-service {#configure-cloud-service-for-your-microsoft-dynamics-service}

De **configuratie van de Dynamica OData Cloud Service van 0&rbrace; MS (Dienst OData) komt met standaard configuratie OData.** Ga als volgt te werk om de toepassing te configureren voor verbinding met uw Microsoft Dynamics-service.

1. Navigeer naar **[!UICONTROL Tools > Cloud Services > Data Sources]** en selecteer de configuratiemap van `global` .
1. Selecteer **configuratie van de Dynamica OData Cloud Service van 0&rbrace; MS (de Dienst van OData) &lbrace;en selecteer &#x200B;** [!UICONTROL Properties]&#x200B;**.** Het dialoogvenster voor de configuratie-eigenschap van de cloudservice wordt geopend.

   In het **lusje van de Montages van de Authentificatie**:

   1. Ga de waarde voor het **gebied van de Wortel van de Dienst 0&rbrace; in.** Ga naar de instantie van de Dynamiek en navigeer aan **Middelen van de Ontwikkelaar** om de waarde voor het gebied van de Wortel van de Dienst te bekijken. Bijvoorbeeld https://&lt;huurder-name>/api/data/v9.1/

   1. Vervang de standaardwaarden in **Identiteitskaart van de Cliënt** (die ook als **identiteitskaart van de Toepassing** wordt bedoeld), **Geheime Cliënt**, **OAuth URL**, **verfrist Symbolische URL**, **Symbolische URL van de Toegang**, en **gebieden van het Middel met waarden van uw de dienstconfiguratie van Microsoft Dynamics.** Het is verplicht om de dynamische instantie URL op het **gebied van het Middel** te specificeren om Microsoft Dynamics met een model van vormgegevens te vormen. Gebruik de URL van de hoofdmap van de service om de URL van de dynamische instantie af te leiden. Bijvoorbeeld, [ https://org.crm.dynamics.com ](https://org.crm.dynamics.com/).

   1. Specificeer **openid** in het **gebied van het Toepassingsgebied van de Vergunning** voor vergunningsproces op Microsoft Dynamics.

   ![ Montages van de Authentificatie ](assets/dynamics_authentication_settings_new.png)

1. Klik op **[!UICONTROL Connect to OAuth]**. U wordt omgeleid naar de Microsoft Dynamics-aanmeldingspagina.
1. Meld u aan met uw Microsoft Dynamics-referenties en accepteer de configuratie van de cloudservice om verbinding te maken met de Microsoft Dynamics-service. Het is een eenmalige taak om verbinding tot stand te brengen tussen de cloudservice en de service.

   Vervolgens wordt u omgeleid naar de configuratiepagina van de cloudservice, die een bericht weergeeft dat de OData-configuratie is opgeslagen.

De MS Dynamics OData Cloud Service (OData Service)-cloudservice is geconfigureerd en verbonden met uw Dynamics-service.

## Formuliergegevensmodel maken {#create-form-data-model}

Wanneer u het pakket van AEM Forms installeert, wordt een model van vormgegevens, **Microsoft Dynamics FDM**, opgesteld op uw instantie van AEM. Standaard gebruikt het model voor formuliergegevens de Microsoft Dynamics-service die is geconfigureerd in MS Dynamics OData Cloud Service (OData Service) als gegevensbron.

Wanneer het formuliergegevensmodel voor het eerst wordt geopend, wordt verbinding gemaakt met de geconfigureerde Microsoft Dynamics-service en worden entiteiten opgehaald van uw Microsoft Dynamics-exemplaar. De &#39;contact&#39;- en &#39;lead&#39;-entiteiten uit Microsoft Dynamics zijn al toegevoegd aan het formuliergegevensmodel.

Ga naar **[!UICONTROL Forms > Data Integrations]** om het formuliergegevensmodel te bekijken. Selecteer **Microsoft Dynamics FDM** en klik **uitgeven** om het model van vormgegevens op uit te geven wijze te openen. U kunt het formuliergegevensmodel ook rechtstreeks openen via de volgende URL:

`https://'[server]:[port]'/aem/fdm/editor.html/content/dam/formsanddocuments-fdm/ms-dynamics-fdm`

![ gebrek-fdm-1 ](assets/default-fdm-1.png)

Vervolgens kunt u een adaptief formulier maken op basis van het formuliergegevensmodel en dit gebruiken in verschillende aangepaste gevallen voor formuliergebruik, zoals:

* Aangepast formulier vooraf invullen door informatie van Microsoft Dynamics-entiteiten en -services op te vragen
* Microsoft Dynamics-serverbewerkingen aanroepen die zijn gedefinieerd in een formuliergegevensmodel met behulp van adaptieve formulierregels
* Verzonden formuliergegevens naar Microsoft Dynamics-entiteiten schrijven

Het wordt aanbevolen een kopie te maken van het formuliergegevensmodel dat bij het AEM Forms-pakket wordt geleverd en gegevensmodellen en -services naar wens te configureren. Zo weet u zeker dat toekomstige updates van het pakket het gegevensmodel van het formulier niet overschrijven.

Voor meer informatie over het creëren van en het gebruiken van het model van vormgegevens in bedrijfswerkschema&#39;s, zie {de Integratie van 0} Gegevens [&#128279;](../../forms/using/data-integration.md).
