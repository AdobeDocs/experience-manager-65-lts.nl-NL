---
title: Salesforce-integratie met AEM Forms met behulp van OAuth 2.0-clientverificatiestroom
description: Stappen om de integratie van Salesforce met AEM Forms te integreren gebruikend OAuth 2.0 cliëntgeloofsbrieven stroom
solution: Experience Manager, Experience Manager Forms
feature: Form Data Model
role: Admin, User, Developer
exl-id: 56b4a767-1210-47f3-b022-766b0dda9943
source-git-commit: 30ec8835be1af46e497457f639d90c1ee8b9dd6e
workflow-type: tm+mt
source-wordcount: '370'
ht-degree: 0%

---

# Integratie van Salesforce met gebruik van OAuth 2.0 client credentials flow  {#configure-salesforce-with-ouath-2.0-client-credential}

## Van toepassing op {#applies-to}

Deze documentatie is op **AEM 6.5 LTS Forms** van toepassing.

Voor de documentatie van AEM as a Cloud Service, zie [ AEM Forms op Cloud Service ](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/forms/integrate/use-form-data-model/aem-forms-salesforce-integration).

U kunt OAuth 2.0 cliëntgeloofsbrieven gebruiken om AEM Forms met de toepassing van Salesforce te integreren. OAuth 2.0 cliëntgeloofsbrieven zijn een standaard en veilige methode voor directe mededeling zonder gebruikersbetrokkenheid.

![ Werkschema terwijl het plaatsen van mededeling tussen de toepassing van AEM Forms en van Salesforce ](/help/forms/using/assets/salesforce-workflow.png)

AEM Forms wisselt de clientgegevens uit (de consumentensleutel en het consumentengeheim), die zijn gedefinieerd in de Salesforce-toepassing, om een toegangstoken te verkrijgen.

Er zijn veelvoudige voordelen om OAuth 2.0 cliëntgeloofsbrieven voor authentificatie over de authentificatie van de Stroom van de Code van de Vergunning te gebruiken:

* OAuth 2.0 de authentificatie van de cliëntgeloofsbrieven staat meer dan vijf verbindingen per gebruiker toe.
* AEM-gegevensbronconfiguratie werkt verder aan deactivering, toegangswijzigingen en wachtwoordupdate voor een AEM-gebruiker.

## Vereisten {#prerequisites}

Voordat u de communicatie tussen een Salesforce-toepassing en een AEM-omgeving instelt:

* Creeer a [ Salesforce verbonden app met OAuth 2.0 cliëntcredentiële stroom ](https://help.salesforce.com/s/articleView?id=sf.connected_app_client_credentials_setup.htm&type=5) en een API-enige gebruiker voor uw organisatie en verkrijg de consumentensleutel en het consumentengeheim voor app.

* Zorg ervoor dat het Swagger-bestand op de juiste wijze is geconfigureerd zodat het overeenkomt met de API&#39;s van uw organisatie. Alternatief, kunt u verkiezen om [ tot een dossier van de Swagger ](https://experienceleague.adobe.com/en/docs/experience-manager-learn/cloud-service/forms/integrate-with-salesforce/describe-rest-api) van het kras te leiden, dat voor gebruik in uw milieu van AEM wordt gemaakt.
>[!NOTE]
>
> AEM 6.5 ondersteunt alleen Swagger 2.0-bestandsspecificaties.

+++

## Stappen voor het configureren van Salesforce met clientreferenties {#steps-to-create-aem-datasource-configuration}

1. Meld u aan bij de instantie Auteur.
1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Data Sources]** .
1. Selecteer de configuratiemap.
1. Klik op **[!UICONTROL Create]** en **[!UICONTROL Create Data Source Configuration]** verschijnt.
1. Geef de waarde **[!UICONTROL Title]** op en selecteer de waarde **[!UICONTROL Service Type]** as **[!UICONTROL RESTful Service]** .
1. Klik op **[!UICONTROL Next]**.
1. Selecteer **[!UICONTROL Swagger Source]** als **[!UICONTROL File].**
   >[!NOTE]
   >
   > Zodra het wagerbestand is geselecteerd, worden het schema, de hostnaam en het basispad automatisch ingevuld.

1. Upload het gemaakte wagerbestand van uw lokale computer door op **[!UICONTROL Browse]** te klikken.
1. Selecteer **[!UICONTROL Authentication Type]** as **[!UICONTROL OAuth 2.0]** en het deelvenster **[!UICONTROL Authentication Settings]** verschijnt.
1. Selecteer **[!UICONTROL Grant Type]** als **[!UICONTROL Client Credentials]** .
1. Geef de **[!UICONTROL Client Id]** en **[!UICONTROL Client Secret]** op die u wilt ophalen uit de Salesforce-app.
1. De **[!UICONTROL Access Token URL]** opgeven in de notatie
   `https://[MyDomainName].my.salesforce.com/services/oauth2/token`.

   >[!NOTE]
   >
   > Elke organisatie heeft een eigen specifieke domeinnaam.

1. Klik op **[!UICONTROL Test Connection]**.
1. Klik op de knop **[!UICONTROL Create]** als de verbinding tot stand is gebracht.

Nu, kunt u [ tot het Model van de Gegevens van de Vorm ](/help/forms/using/create-form-data-model.md) leiden om de gevormde gegevensbron met uw Aanpassings Forms te integreren.
