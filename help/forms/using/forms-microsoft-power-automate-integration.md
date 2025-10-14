---
title: Hoe kan ik Adaptief-formuliergegevens verbinden en verzenden naar Microsoft&reg; Power Automate?
description: Een stapsgewijze handleiding voor het maken van een verbinding en het verzenden van Adaptief formulier naar Microsoft&reg; Power Automate.
keywords: Adaptive Forms Microsoft Power Automate, Adaptive Forms data verzenden naar Microsoft Power Automate
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: e2c4cae6-67db-4531-b1e1-0a378d9800f2
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 0%

---

# Adaptieve formuliergegevens verbinden en verzenden naar Microsoft® Power Automate {#connect-adaptive-form-with-power-automate}

U kunt een adaptief formulier configureren om een Microsoft® Power Automate Cloud Flow uit te voeren bij verzending. Met het geconfigureerde adaptieve formulier worden vastgelegde gegevens, bijlagen en het document met records naar Power Automate Cloud Flow verzonden voor verwerking. Het helpt u om een aangepaste ervaring op het gebied van gegevensvastlegging op te bouwen en tegelijk de kracht van Microsoft® Power Automate te benutten om bedrijfslogics rond vastgelegde gegevens te bouwen en de workflows van klanten te automatiseren. Hier volgen enkele voorbeelden van wat u kunt doen na de integratie van een adaptief formulier met Microsoft® Power Automate:

* Adaptieve Forms-gegevens gebruiken in een Power Automate-bedrijfsprocessen
* Gebruik Power Automate om vastgelegde gegevens naar meer dan 500 gegevensbronnen of een openbaar beschikbare API te verzenden
* Complexe berekeningen uitvoeren op vastgelegde gegevens
* Adaptieve Forms-gegevens opslaan naar opslagsystemen volgens een vooraf bepaald schema

De adaptieve redacteur van Forms verstrekt **roept een stroom van de Macht Microsoft®** automatisch verzendt actie om adaptieve vormgegevens, gehechtheid, en Document van Verslag te verzenden worden verzonden naar de Stroom van de Wolk van de Macht van de Macht van de Automatisering. Om de Submit actie te gebruiken om gevangen gegevens naar Microsoft® Power Automate te verzenden, [ verbind uw instantie van de Auteur van AEM Forms met Microsoft® Macht ] (#connect-your-aem-forms-instance-with-microsoft&reg;-power-automate)

## Vereisten

U hebt het volgende nodig om een adaptief formulier te verbinden met Microsoft® Power Automate:

* Microsoft® Power Automate Premium-licentie
* Microsoft® [&#x200B; Macht automatiseert stroom &#x200B;](https://docs.microsoft.com/en-us/power-automate/create-flow-solution) met de `When an HTTP request is received` trekker om Aangepaste Vorm goed te keuren voorlegt gegevens
* Een gebruiker van Experience Manager met [&#x200B; Forms Auteur &#x200B;](/help/forms/using/forms-groups-privileges-tasks.md) en [&#x200B; Forms Admin &#x200B;](/help/forms/using/forms-groups-privileges-tasks.md) voorrechten
* Account dat wordt gebruikt om verbinding te maken met Microsoft® Power Automate is eigenaar van de Power Automate-flow die is geconfigureerd om gegevens van het adaptieve formulier te ontvangen


## Sluit uw AEM Forms-instantie aan met Microsoft® Power Automate {#connect-forms-server-with-power-automate}

Voer de volgende handelingen uit om uw AEM Forms Author-instantie te verbinden met Microsoft® Power Automate:

1. [Een Microsoft maken](#ms-power-automate-application)
1. [Microsoft maken](#microsoft-power-automate-dataverse-cloud-configuration)
1. [Microsoft maken](#create-microsoft-power-automate-flow-cloud-configuration)
1. [Microsoft publiceren](#publish-microsoft-power-automate-dataverse-cloud-configuration)

### Microsoft® Azure Active Directory-toepassing maken {#ms-power-automate-application}

1. Login aan [&#x200B; Azure Portaal &#x200B;](https://portal.azure.com/).
1. Selecteer [!UICONTROL Azure Active Directory] in de linkernavigatie.
1. Selecteer op de pagina Standaardmap de optie [!UICONTROL App registrations] in het linkerdeelvenster.
1. Klik op Nieuwe registraties op de pagina App-registraties.
1. Geef de naam, ondersteunde accounttypen en de URI omleiden op de pagina op. Geef in de URI voor omleiding het volgende op en klik op Opslaan.
   * `https://[AEM Forms Author instance]/libs/fd/powerautomate/content/dataverse/config.html`
   * `https://[AEM Forms Author instance]/libs/fd/powerautomate/content/flowservice/config.html`

   ![&#x200B; Register een Azure Actieve Toepassing van de Folder &#x200B;](assets/power-automate-application.png)

   >[!NOTE]
   >U kunt desgewenst ook aanvullende URI&#39;s voor omleiding opgeven vanaf de pagina Verificatie.
   > Voor ondersteunde accounttypen selecteert u één huurder, meerdere huurders of persoonlijke Microsoft®-account, afhankelijk van uw gebruiksscenario


1. Schakel op de pagina Verificatie de volgende opties in en klik op Opslaan.


   * Toegangstokens (gebruikt voor impliciete stromen)
   * ID-tokens (gebruikt voor impliciete en hybride stromen)

1. Klik op de pagina met API-machtigingen op Een machtiging toevoegen.
1. Selecteer onder Microsoft® API&#39;s de Flow Service en selecteer de volgende machtigingen.
   * Flows.Manage.All
   * Flows.Read.All

   Klik op Machtigingen toevoegen om de machtigingen op te slaan.
1. Klik op de pagina met API-machtigingen op Een machtiging toevoegen. Selecteer API&#39;s die mijn organisatie gebruikt en zoek `DataVerse` .
1. Enable user_imitation en klik toevoegen toestemmingen.
1. (Optioneel) Klik op de pagina Certificates &amp; secrets op Nieuw clientgeheim. Voor Add een Geheim scherm van de Cliënt, verstrek een beschrijving en een tijdspanne voor het geheim om te verlopen, en de klik voegt toe. Er wordt een geheime tekenreeks gegenereerd.
1. Houd een nota van uw organisatie-specifieke [&#x200B; milieu URL van de Dynamica &#x200B;](https://docs.microsoft.com/en-us/power-automate/web-api#compose-http-requests).

### Microsoft® Power Automated Dataverse Cloud Configuration maken {#microsoft-power-automate-dataverse-cloud-configuration}

1. Op de auteursinstantie van AEM Forms, navigeer aan **[!UICONTROL Tools]** ![&#x200B; hammer &#x200B;](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Selecteer op de pagina **[!UICONTROL Configuration Browser]** de optie **[!UICONTROL Create]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** voor de configuratie op, schakel **[!UICONTROL Cloud Configurations]** in en selecteer **[!UICONTROL Create]** . Er wordt een configuratiecontainer gemaakt voor de opslag van Cloud Services. Zorg ervoor dat de mapnaam geen ruimte bevat.
1. Navigeer aan **[!UICONTROL Tools]** ![&#x200B; hamer &#x200B;](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft®® Power Automate Dataverse]** en open de configuratiecontainer u in de vorige stap creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het veld **[!UICONTROL Configuration Container]** .

1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Microsoft®® Power Automate Flow Service] -configuratie te maken in AEM Forms.
1. Geef op de pagina **[!UICONTROL Configure Dataverse Service for Microsoft®® Power Automate]** de waarden **[!UICONTROL Client ID]** (ook wel toepassings-id genoemd), **[!UICONTROL Client Secret]** , **[!UICONTROL OAuth URL]** en **[!UICONTROL Dynamic Environment URL]** op. Gebruik identiteitskaart van de Cliënt, Geheime Cliënt, OAuth URL, en Dynamische Milieu URL van [&#x200B; Microsoft® Azure Actieve Toepassing van de Folder &#x200B;](#ms-power-automate-application) u in de vorige sectie creeerde. De optie Eindpunten van het gebruik in Microsoft® Azure Actieve de toepassingsUI van de Folder om OAuth URL te vinden

   ![&#x200B; optie van Eindpunten van het Gebruik in Microsoft Power Automate toepassing UI om OAuth URL &#x200B;](assets/endpoints.png) te vinden

1. Selecteer **[!UICONTROL Connect]** . Meld u desgevraagd aan bij uw Microsoft® Azure-account. Selecteer **[!UICONTROL Save]** .

### Microsoft® Power Automated Flow Service Cloud Configuration maken {#create-microsoft-power-automate-flow-cloud-configuration}

1. Navigeer aan **[!UICONTROL Tools]** ![&#x200B; hamer &#x200B;](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft®® Power Automate Flow Service]** en open de configuratiecontainer u in de vorige sectie creeerde.

   >[!NOTE]
   >
   >Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het veld **[!UICONTROL Configuration Container]** .
1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Microsoft®® Power Automate Flow Service] -configuratie te maken in AEM Forms.
1. Geef op de pagina **[!UICONTROL Configure Dataverse for Microsoft®® Power Automate]** de waarden **[!UICONTROL Client ID]** (ook wel toepassings-id genoemd), **[!UICONTROL Client Secret]** , **[!UICONTROL OAuth URL]** en **[!UICONTROL Dynamic Environment URL]** op. Gebruik identiteitskaart van de Cliënt, Geheime cliënt, OAuth URL, en identiteitskaart van het Milieu van de Dynamiek. Gebruik de optie Eindpunten in de gebruikersinterface van de Microsoft® Azure Active Directory-toepassing om OAuth URL te zoeken. Open [&#x200B; Mijn stromen &#x200B;](https://us.flow.microsoft.com) verbinding en selecteer Mijn die Stromen gebruiken identiteitskaart in URL als identiteitskaart van het Milieu van de Dynamiek wordt vermeld.
1. Selecteer **[!UICONTROL Connect]**. Meld u desgevraagd aan bij uw Microsoft® Azure-account. Selecteer **[!UICONTROL Save]** .

### Publiceer zowel de Microsoft® Power Automate Data verse als de Microsoft® Power Automate Flow Service Cloud Configurations {#publish-microsoft-power-automate-dataverse-cloud-configuration}

1. Navigeer aan **[!UICONTROL Tools]** ![&#x200B; hamer &#x200B;](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Microsoft®® Power Automate Dataverse]** en open de configuratiecontainer u in de vorige [&#x200B; creeerde Macht Microsoft® Macht Automate Dataverse Cloud van de Configuratie &#x200B;](#microsoft-power-automate-dataverse-cloud-configuration) sectie.
1. Selecteer de `dataverse` -configuratie en selecteer **[!UICONTROL Publish]** .
1. Selecteer **[!UICONTROL All Configurations]** op de pagina Publiceren en selecteer **[!UICONTROL Publish]** . Publiceer zowel Power Automate Data verse als Power Automate Flow Service Cloud Configurations.

Uw AEM Forms Author-instantie is nu verbonden met Microsoft® Power Automate. U kunt nu Adaptive Forms-gegevens naar een Power Automate-flow verzenden.

## Gebruik de Invoke a Microsoft® Power Automate flow submit action to send data to a Power Automate Flow {#use-the-invoke-microsoft-power-automate-flow-submit-action}

Nadat u [&#x200B; uw instantie van de Auteur van AEM Forms met Microsoft® Macht &#x200B;](#connect-forms-server-with-power-automate) verbindt, voer de volgende actie uit om uw adaptieve vorm te vormen om gevangen gegevens naar een stroom te verzenden Microsoft® bij vormvoorlegging.

1. Meld u aan bij de instantie van de auteur, selecteer het adaptieve formulier en klik op **[!UICONTROL Properties]** .
1. In de Container van de Configuratie, doorblader en selecteer de container die in sectie [&#x200B; wordt gecreeerd de Macht Microsoft® Automate Configuratie van de Wolk Dataverse &#x200B;](#microsoft-power-automate-dataverse-cloud-configuration), en selecteer **[!UICONTROL Save and Close]**.
1. Open het Adaptief formulier voor bewerking en ga naar de sectie **[!UICONTROL Submission]** van de eigenschappen van de container van adaptieve formulieren.
1. Selecteer bij **[!UICONTROL Submit Actions]** in de eigenschappencontainer de optie **[!UICONTROL Invoke a Power Automate flow]** . Er wordt een lijst met beschikbare stroomstromen voor Automatisch beschikbaar onder de optie **[!UICONTROL Power Automate flow]** . Selecteer de vereiste stroom en de Adaptieve Forms-gegevens worden bij verzending naar de server verzonden.

   ![&#x200B; vormen voorleggen Actie &#x200B;](assets/submission.png)

>[!NOTE]
>
> Voordat u het adaptieve formulier verzendt, moet u ervoor zorgen dat de trigger `When an HTTP Request is received` met onder JSON-schema wordt toegevoegd aan de stroom Automatisch.

```
        {
            "type": "object",
            "properties": {
                "attachments": {
                    "type": "array",
                    "items": {
                        "type": "object",
                        "properties": {
                            "filename": {
                                "type": "string"
                            },
                            "data": {
                                "type": "string"
                            },
                            "contentType": {
                                "type": "string"
                            },
                            "size": {
                                "type": "integer"
                            }
                        },
                        "required": [
                            "filename",
                            "data",
                            "contentType",
                            "size"
                        ]
                    }
                },
                "templateId": {
                    "type": "string"
                },
                "templateType": {
                    "type": "string"
                },
                "data": {
                    "type": "string"
                },
                "document": {
                    "type": "object",
                    "properties": {
                        "filename": {
                            "type": "string"
                        },
                        "data": {
                            "type": "string"
                        },
                        "contentType": {
                            "type": "string"
                        },
                        "size": {
                            "type": "integer"
                        }
                    }
                }
            }
        }
```

## Zie ook:

* [Een adaptief formulier maken](create-an-adaptive-form-core-components.md)
* [Een verzendhandeling configureren](configuring-submit-actions.md)
* [&#x200B; de Schakelaar van Adobe Experience Manager voor de Macht van Microsoft® &#x200B;](https://learn.microsoft.com/en-us/connectors/adobeexperiencemanag/)
