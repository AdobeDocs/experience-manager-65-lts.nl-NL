---
title: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
description: Installeren  [!DNL Workfront for Experience Manager enhanced connector]
role: Admin
feature: Workfront Integrations and Apps
hide: true
solution: Experience Manager, Workfront
exl-id: dd6eec1e-fa63-410a-bcd3-61892861fd0c
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '406'
ht-degree: 1%

---

# Installeren [!DNL Workfront for Experience Manager enhanced connector] {#assets-integration-overview}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/integrations/workfront-connector-install.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |

Een gebruiker met beheerdertoegang in [!DNL Adobe Experience Manager] installeert de verbeterde schakelaar. Alvorens u installeert, herzie de platformsteun en andere [ eerste vereisten voor de schakelaar ](https://one.workfront.com/s/csh?context=2467&pubname=the-new-workfront-experience).

>[!IMPORTANT]
>
>* Adobe vereist implementatie en configuratie van de [!DNL Adobe Workfront for Experience Manager enhanced connector] alleen via gecertificeerde partners of [!DNL Adobe Professional Services] . Indien geïmplementeerd en geconfigureerd zonder een gecertificeerde partner of [!DNL Adobe Professional Services] , wordt dit niet ondersteund door Adobe.
>
>* Adobe kan updates voor [!DNL Adobe Workfront] en [!DNL Adobe Experience Manager] vrijgeven die deze connector redundant maken. Als dit gebeurt, kunnen klanten worden gevraagd over te stappen van het gebruik van deze connector.
>
>* Adobe ondersteunt verbeterde connectorversies 1.7.4 en hoger. Eerdere pre-release en aangepaste versies worden niet ondersteund. Om de verbeterde schakelaarversie te controleren, navigeer aan de `digital.hoodoo` groep beschikbaar in de linkerruit in [ Manager van het Pakket ](/help/sites-administering/package-manager.md).
>
>* Zie [ de certificatieexamen van de Partner voor Workfront voor Experience Manager Assets verbeterde schakelaar ](https://solutionpartners.adobe.com/solution-partners/home/applications/experience_cloud/workfront/journey/dev_core.html). Voor informatie over het examen, zie {de Gids van het 0} Examen [&#128279;](https://express.adobe.com/page/Tc7Mq6zLbPFy8/).

Voer de volgende stappen uit om de aansluiting te installeren:

1. Download de schakelaar van [[!DNL Software Distribution]  verbinding ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. [ vorm de firewall ](https://one.workfront.com/s/document-item?bundleId=the-new-workfront-experience&topicId=Content%2FAdministration_and_Setup%2FGet_started-WF_administration%2Fconfigure-your-firewall.html).
1. Sta in de Dispatcher de HTTP-headers `authorization` , `username` en `apikey` toe. `GET` -, `POST` - en `PUT` -aanvragen toestaan aan `/bin/workfront-tools` .
1. Zorg ervoor dat de volgende paden niet bestaan in de [!DNL Experience Manager] -opslagplaats:

   * `/apps/dam/gui/coral/components/admin/schemaforms/formbuilder`
   * `/apps/dam/gui/coral/components/admin/folderschemaforms/formbuilder`
   * `/apps/dam/gui/content/foldermetadataschemaeditor`
   * `/apps/dam/cfm/models/editor/components/datatypeproperties`
   * `/apps/settings/dam/cfm/models/formbuilderconfig`

1. Installeer het pakket met [!UICONTROL Package Manager] . Om te weten hoe te om pakketten te installeren, zie {de documentatie van de Manager van het 0} Pakket [&#128279;](/help/sites-administering/package-manager.md).
1. Maak `wf-workfront-users` in [!DNL Experience Manager] Gebruikersgroep en wijs de machtiging `jcr:all` toe aan `/content/dam` .
1. Voeg een aangepaste eigenschap toe aan de waarde voor de index van het vak voor **`ntFolderDamLucene(/oak:index/ntFolderDamLucene)`** . Voer de volgende stappen uit:
   * Voeg een eigenschap **`nt:unstructured`** genaamd **`wfReferenceNumber`** toe aan:

     `/oak:index/ntFolderDamLucene/indexRules/nt:folder/properties/wfReferenceNumber`.
   * Wijzig de index van de `index /oak:index/ntFolderDamLucene` door de herindexmarkering om te draaien naar `true` .

Er wordt automatisch een systeemgebruiker `workfront-tools` gemaakt en de vereiste machtigingen worden automatisch beheerd. Alle gebruikers van [!DNL Workfront] die de schakelaar gebruiken worden automatisch toegevoegd als deel van deze groep.

## De verbinding configureren tussen [!DNL Experience Manager] en [!DNL Workfront] {#configure-connection}

Ga als volgt te werk om een verbinding met Workfront te maken:

1. Selecteer **[!UICONTROL Tools]** > **[!UICONTROL Cloud Services]** > **[!UICONTROL Workfront Tools Configuration]** in [!DNL Experience Manager] .

1. Selecteer `workfront-tools` in het linkerpaneel en selecteer **[!UICONTROL Create]** optie in het hoger-juiste gebied van de pagina.

1. Geef in het dialoogvenster **[!UICONTROL Workfront Connection]** de vereiste details van de [!DNL Workfront] -implementatie op en selecteer de optie **[!UICONTROL Connect to Workfront]** . Zodra de verbinding is gelukt, wordt de aangepaste integratie van het [!DNL Workfront] -document automatisch gemaakt in de [!DNL Workfront] -omgeving.

   ![ Verbinden [!DNL Experience Manager] en [!DNL Workfront]](/help/assets/assets/wf-connection-config.png)

1. Als u de verbinding wilt controleren, opent u deze in [!DNL Workfront] en controleert u of de API-sleutel gelijk is en of de verbinding **[!UICONTROL Enabled]** is. Selecteer hiervoor **[!UICONTROL Setup]** > **[!UICONTROL Documents]** > **[!UICONTROL Custom Integrations]** in [!DNL Workfront] .

## [!DNL Workfront for Experience Manager enhanced connector] bijwerken {#update-enhanced-connector-for-workfront}

Met Experience Manager Assets kunt u [!DNL Workfront for Experience Manager enhanced connector] bijwerken van een vorige versie naar de meest recente versie.

Ga als volgt te werk om [!DNL Workfront for Experience Manager enhanced connector] bij te werken naar de meest recente versie:

1. Download de recentste versie van de verbeterde schakelaar van [[!DNL Software Distribution]  verbinding ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/product/assets/workfront-tools.ui.apps.zip).
1. Installeer het pakket met [!UICONTROL Package Manager] . Om te weten hoe te om pakketten te installeren, zie {de documentatie van de Manager van het 0} Pakket [&#128279;](/help/sites-administering/package-manager.md).
