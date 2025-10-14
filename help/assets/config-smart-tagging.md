---
title: Asset tagging configureren met behulp van Smart Content Service
description: Leer hoe te om slimme het etiketteren en verbeterde slimme het etiketteren in  [!DNL Adobe Experience Manager] te vormen, gebruikend de Slimme Dienst van de Inhoud.
role: Admin
feature: Tagging,Smart Tags
solution: Experience Manager, Experience Manager Assets
exl-id: be7c294c-149b-4825-8376-573f9e2987e2
source-git-commit: 1cedead501597fb655c2c7b87336b29cbf048294
workflow-type: tm+mt
source-wordcount: '1747'
ht-degree: 13%

---

# [!DNL Assets] voorbereiden voor slimme tags {#configure-asset-tagging-using-the-smart-content-service}

Voordat u met het labelen van uw middelen begint met Smart Content Services, moet u [!DNL Experience Manager Assets] integreren met Adobe Developer Console om de slimme service van [!DNL Adobe Sensei] te gebruiken. Als de service eenmaal is geconfigureerd, kunt u de service trainen met enkele afbeeldingen en een tag.
Controleer het volgende voordat u de Smart Content Service gebruikt:

* [&#x200B; integreer met Adobe Developer Console &#x200B;](#integrate-adobe-io).
* [&#x200B; Lijn de Slimme Dienst van de Inhoud &#x200B;](#training-the-smart-content-service).
* Installeer het recentste [[!DNL Experience Manager]  Pak van de Dienst &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/aem-releases-updates.html?lang=nl-NL).

>[!IMPORTANT]
>
>Verwijs naar [&#x200B; Assets voor slimme het etiketteren &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65/content/assets/administer/config-smart-tagging) voor de configuratie van slimme markeringen in AEM 6.5 voorbereiden.

**Nieuwe Gebruikers**

Smart Content Services is niet meer beschikbaar voor nieuwe [!DNL Experience Manager Assets] gebruikers op locatie.

**Bestaande gebruikers**

Bestaande gebruikers op locatie die deze mogelijkheid al hebben ingeschakeld, kunnen services voor slimme inhoud blijven gebruiken.

## Integreren met Adobe Developer Console {#integrate-adobe-io}

Wanneer u met Adobe Developer Console integreert, verifieert de [!DNL Experience Manager] server uw de dienstgeloofsbrieven met de gateway van Adobe Developer Console alvorens uw verzoek aan de Slimme Dienst van de Inhoud door:sturen. Voor integratie hebt u een Adobe ID-account nodig met beheerdersrechten voor de organisatie en de licentie voor Smart Content Service die u hebt aangeschaft en ingeschakeld voor uw organisatie.

Om de Slimme Dienst van de Inhoud te vormen, volg deze top-level stappen:

1. Creeer een integratie in [&#x200B; Adobe Developer Console &#x200B;](#create-adobe-io-integration).

1. Creeer [&#x200B; IMS technische rekeningsconfiguratie &#x200B;](#create-ims-account-config) gebruikend de API sleutel en andere geloofsbrieven van Adobe Developer Console.

1. [&#x200B; vorm de Slimme Dienst van de Inhoud &#x200B;](#configure-smart-content-service).

1. [Test de configuratie](#validate-the-configuration).

### Adobe Developer Console-integratie maken {#create-adobe-io-integration}

Als u API&#39;s voor Smart Content Service wilt gebruiken, maakt u een integratie in Adobe Developer Console om [!UICONTROL API Key] (gegenereerd in [!UICONTROL CLIENT ID] field of Adobe Developer Console integration), [!UICONTROL ORGANIZATION ID] en [!UICONTROL CLIENT SECRET] for [!UICONTROL Assets Smart Tagging Service Settings] van de cloudconfiguratie te verkrijgen in [!DNL Experience Manager] .

1. Toegang [&#x200B; https://developer.adobe.com &#x200B;](https://developer.adobe.com/) in browser. Selecteer de aangewezen rekening en verifieer dat de bijbehorende organisatorische rol systeem **beheerder** is.

1. Maak een project een geef het de gewenste naam. Klik op **[!UICONTROL Add API]**.

1. Ga naar de pagina **[!UICONTROL Add an API]** en selecteer achtereenvolgens **[!UICONTROL Experience Cloud]** en **[!UICONTROL Smart Content]**. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL OAuth Server-to-Server]**. Klik op **[!UICONTROL Next]** .
Raadpleeg de documentatie bij Developer Console voor meer informatie over het uitvoeren van deze configuratie, afhankelijk van uw vereisten:

   * Overzicht:
      * [&#x200B; Server aan de authentificatie van de Server &#x200B;](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/)

   * Een nieuwe OAuth-referentie maken:
      * [&#x200B; OAuth Server-aan-Server de gids van de credentieimplementatie &#x200B;](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/implementation)

   * Een bestaande JWT-referentie migreren naar een OAuth-referentie:
      * [&#x200B; migrerend van de Rekening van de Dienst (JWT) credential aan OAuth Server-aan-Server credential &#x200B;](https://developer.adobe.com/developer-console/docs/guides/authentication/ServerToServerAuthentication/migration)


1. Selecteer **[!UICONTROL Select product profiles]** op de pagina **[!UICONTROL Smart Content Services]** . Klik op **[!UICONTROL Save configured API]**.

   De pagina die verschijnt biedt meer informatie over de configuratie. Zorg dat deze pagina geopend blijft en kopieer deze waarden in [!UICONTROL Assets Smart Tagging Service Settings] van de cloudconfiguratie in [!DNL Experience Manager] om slimme tags te configureren.

   ![&#x200B; Referentie OAuth in Developer Console &#x200B;](assets/ims-configuration-developer-console.png)

### Configuratie van technische IMS-account maken {#create-ims-account-config}

U moet de configuratie van de technische IMS-account maken met de onderstaande stappen:

1. Ga in de [!DNL Experience Manager]-gebruikersinterface naar **[!UICONTROL Tools]** > **[!UICONTROL Security]** > **[!UICONTROL Adobe IMS Configurations]**.

1. Klik op **[!UICONTROL Create]**.

1. Gebruik de volgende waarden in het dialoogvenster Configuratie technische account van IMS:

   ![&#x200B; het venster van de Configuratie van Adobe IMS &#x200B;](assets/adobe-ims-config.png)

   | Veld | Beschrijving |
   | -------- | ---------------------------- |
   | Cloudoplossing | Kies **[!UICONTROL Smart Tags]** in de vervolgkeuzelijst. |
   | Titel | Voeg een titel toe van de configurerende IMS-account. |
   | Autorisatieserver | Toevoegen `https://ims-na1.adobelogin.com` |
   | Client-id | Te verstrekken door [&#x200B; console van Adobe Developer &#x200B;](https://developer.adobe.com/console/). |
   | Clientgeheim | Te verstrekken door [&#x200B; console van Adobe Developer &#x200B;](https://developer.adobe.com/console/). |
   | Scope | Te verstrekken door [&#x200B; console van Adobe Developer &#x200B;](https://developer.adobe.com/console/). |
   | Org-id | Te verstrekken door [&#x200B; console van Adobe Developer &#x200B;](https://developer.adobe.com/console/). |

1. Selecteer de configuratie die u hebt gemaakt en klik op **[!UICONTROL Check Health]** .

1. Bevestig het dialoogvenster Gezondheid controleren en klik op Sluiten als de configuratie gezond is.

### Een nieuwe configuratie maken {#configure-smart-content-service}

Als u de integratie wilt configureren, gebruikt u de waarden van de velden [!UICONTROL TECHNICAL ACCOUNT ID] , [!UICONTROL ORGANIZATION ID] , [!UICONTROL CLIENT SECRET] en [!UICONTROL CLIENT ID] van de Adobe Developer Console-integratie. Door een cloud-configuratie met slimme tags te maken, kunnen API-aanvragen van de [!DNL Experience Manager] -implementatie worden geverifieerd.

1. Navigeer in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Cloud Service]** > **[!UICONTROL Smart Tag]** om het dialoogvenster [!UICONTROL Smart Tag Configurations] te openen.

1. Klik op **[!UICONTROL Create]** om een nieuwe configuratie te maken. Anders klikt u op **[!UICONTROL Properties]** om de bestaande configuratie bij te werken.

1. Vul de volgende velden in:

   ![&#x200B; Slimme Configuratie van Markeringen &#x200B;](assets/smart-tags-config.png)

   | Veld | Beschrijving |
   | -------- | ---------------------------- |
   | Titel | Voeg een titel toe van de configurerende IMS-account. |
   | Gekoppelde Adobe IMS-configuratie | Kies configuratie in de keuzelijst. |
   | Service-URL | `https://smartcontent.adobe.io/<region where your Experience Manager author instance is hosted>`. Bijvoorbeeld `https://smartcontent.adobe.io/apac` . U kunt `na` , `emea` of , `apac` opgeven als de gebieden waar de Experience Manager-auteur-instantie wordt gehost. |

   >[!NOTE]
   >
   >Als de Experience Manager Managed Service is ingericht vóór 1 september 2022, gebruikt u de volgende Service-URL:
   >`https://mc.adobe.io/marketingcloud/smartcontent`

1. Klik op **[!UICONTROL Save & Close]**.

### De configuratie valideren {#validate-the-configuration}

Nadat u de configuratie hebt voltooid, kunt u een JMX MBean gebruiken om de configuratie te bevestigen. Voer de volgende stappen uit om te valideren.

1. Open de [!DNL Experience Manager] -server op `https://[aem_server]:[port]` .

1. Ga naar **[!UICONTROL Tools]** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]** om de OSGi-console te openen. Klik op **[!UICONTROL Main]>[!UICONTROL JMX]** .

<!--
1. Click `com.day.cq.dam.similaritysearch.internal.impl`. It opens **[!UICONTROL SimilaritySearch Miscellaneous Tasks]**.-->

1. Klik op `com.day.cq.dam.similaritysearch.internal.impl (SCS)`.

   ![&#x200B; het venster van het Boon &#x200B;](assets/mbean.png)

1. Klik op `validateConfigs()`. Klik in het dialoogvenster **[!UICONTROL Validate Configurations]** op **[!UICONTROL Invoke]** .

De validatieresultaten worden in hetzelfde dialoogvenster weergegeven.

### Slimme tags toepassen inschakelen in de [!UICONTROL DAM Update Asset] -workflow (optioneel) {#enable-smart-tagging-in-the-update-asset-workflow-optional}

1. Ga in [!DNL Experience Manager] naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .

1. Selecteer op de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]**-workflowmodel.

1. Klik op **[!UICONTROL Edit]** op de werkbalk.

1. Vouw het zijpaneel uit om de stappen weer te geven. Sleep de stap **[!UICONTROL Smart Tag Asset]** die beschikbaar is in de DAM-workflowsectie en plaats deze na de stap **[!UICONTROL Process Thumbnails]**.

   ![De stap Asset met slimme tag toevoegen na de stap met de procesminiaturen in de DAM Update Asset-workflow](assets/smart-tag-in-dam-update-asset-workflow.png)

1. Open de eigenschappen van de stap om de details te wijzigen. Ga naar **[!UICONTROL Advanced Settings]** en controleer of de optie **[!UICONTROL Handler Advance]** is ingeschakeld.

   ![&#x200B; vorm het werkschema van de Activa van de Update DAM en voeg slimme markeringsstap &#x200B;](assets/smart-tag-step-properties-workflow1.png) toe

1. Selecteer op het tabblad **[!UICONTROL Arguments]** de optie **[!UICONTROL Ignore Errors]** als u de workflow wilt voltooien, zelfs als de stap Automatisch labelen is mislukt.

   Als u bovendien elementen wilt labelen terwijl ze worden geüpload, ongeacht of slimme tags zijn ingeschakeld voor mappen, selecteert u **[!UICONTROL Ignore Smart Tag Flag]** .

   ![&#x200B; vorm het werkschema van de Activa van de Update DAM om slimme markeringsstap toe te voegen en manager vooruit te selecteren &#x200B;](assets/smart-tag-step-properties-workflow2.png)

1. Klik gedaan ![&#x200B; gereed pictogram &#x200B;](assets/do-not-localize/check-ok-done-icon.png) om de processtap te sluiten.

1. Klik op **[!UICONTROL Sync]** om de workflow op te slaan.

## De Smart Content Service trainen {#training-the-smart-content-service}

Als u wilt dat de Smart Content Service uw bedrijfskrionomie herkent, voert u deze uit op een reeks elementen die al tags bevatten die relevant zijn voor uw bedrijf. Om uw merkbeelden effectief te etiketteren, vereist de Slimme Dienst van de Inhoud dat de trainingsbeelden aan bepaalde richtlijnen voldoen. Na de training kan de service dezelfde taxonomie toepassen op een vergelijkbare set activa.

U kunt de service meerdere keren trainen om de service beter in staat te stellen relevante tags toe te passen. Voer na elke trainingscyclus een labelworkflow uit en controleer of uw elementen correct zijn gecodeerd.

U kunt de Slimme Dienst van de Inhoud periodiek of op vereiste basis trainen.

>[!NOTE]
>
>De trainingsworkflow wordt alleen uitgevoerd voor mappen.

### Richtsnoeren voor opleiding {#guidelines-for-training}

Voor de beste resultaten voldoen de afbeeldingen in de trainingsset aan de volgende richtlijnen:

**Hoeveelheid en grootte:** Minimaal 30 afbeeldingen per tag. Minimaal 500 pixels aan de langere zijde.

**Samenhang**: De beelden die voor een specifieke markering worden gebruikt zijn visueel gelijkaardig.

Het is bijvoorbeeld geen goed idee om al deze afbeeldingen als `my-party` te labelen (voor training) omdat ze er anders uitzien.

![&#x200B; Illustratieve beelden om de richtlijnen voor opleiding &#x200B;](/help/assets/assets/do-not-localize/coherence.png) te illustreren

**Dekking**: Gebruik voldoende verscheidenheid in de beelden in de opleiding. Het is de bedoeling om een paar maar redelijk verschillende voorbeelden te geven, zodat Experience Manager leert zich te richten op de juiste zaken. Als u dezelfde tag toepast op visueel verschillende afbeeldingen, moet u ten minste vijf voorbeelden van elke soort opnemen.

Bijvoorbeeld, voor de markering *model-onderstel*, omvat meer opleidingsbeelden gelijkend op het benadrukte beeld hieronder voor de dienst om gelijkaardige beelden nauwkeuriger tijdens het etiketteren te identificeren.

![&#x200B; Illustratieve beelden om de richtlijnen voor opleiding &#x200B;](/help/assets/assets/do-not-localize/coverage_1.png) te illustreren

**Vervorming/belemmering**: De de diensttreinen beter op beelden die minder afleiding (duidelijke achtergronden, niet verwante accompanimenten, zoals voorwerpen/personen met het belangrijkste onderwerp) hebben.

Bijvoorbeeld, voor de markering *casual-shoe*, is het tweede beeld geen goede opleidingskandidaat.

![&#x200B; Illustratieve beelden om de richtlijnen voor opleiding &#x200B;](/help/assets/assets/do-not-localize/distraction.png) te illustreren

**Volledigheid:** Als een afbeelding in aanmerking komt voor meer dan één tag, voegt u alle relevante tags toe voordat u de afbeelding opneemt voor training. Voeg bijvoorbeeld voor tags, zoals `raincoat` en `model-side-view`, beide tags toe aan het in aanmerking komende element voordat u dit opneemt voor training.

![&#x200B; Illustratieve beelden om de richtlijnen voor opleiding &#x200B;](/help/assets/assets/do-not-localize/completeness.png) te illustreren

>[!NOTE]
>
>Of de Smart Content Service uw tags kan trainen en deze op andere afbeeldingen kan toepassen, hangt af van de kwaliteit van de afbeeldingen die u voor de training gebruikt. Voor de beste resultaten raadt Adobe aan visueel vergelijkbare afbeeldingen te gebruiken om de service voor elke tag op te leiden.

### Periodieke training {#periodic-training}

U kunt de Slimme Dienst van de Inhoud toelaten om periodiek op de activa en bijbehorende markeringen binnen een omslag te trainen. Open de pagina [!UICONTROL Properties] van de elementmap, selecteer **[!UICONTROL Enable Smart Tags]** onder het tabblad **[!UICONTROL Details]** en sla de wijzigingen op.

![&#x200B; enable_smart_tags &#x200B;](assets/enable_smart_tags.png)

Als deze optie voor een map is geselecteerd, voert [!DNL Experience Manager] automatisch een trainingsworkflow uit om de Smart Content Service op te leiden voor de mappenelementen en hun tags. Standaard wordt de trainingsworkflow wekelijks om 12:30 uur uitgevoerd op zaterdag.

### Opleiding op aanvraag {#on-demand-training}

U kunt de Slimme Dienst van de Inhoud wanneer vereist van de console van het Werkschema trainen.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL Smart Tags Training]** workflow en klik vervolgens op **[!UICONTROL Start Workflow]** op de werkbalk.
1. Blader in het dialoogvenster **[!UICONTROL Run Workflow]** naar de payload-map met de gecodeerde elementen voor training voor de service.
1. Geef een titel op voor de workflow en voeg een opmerking toe. Klik vervolgens op **[!UICONTROL Run]** . De elementen en tags worden ter training aangeboden.

   ![&#x200B; workflow_dialog &#x200B;](assets/workflow_dialog.png)

>[!NOTE]
>
>Nadat de middelen in een map zijn verwerkt voor training, worden alleen de gewijzigde middelen verwerkt in volgende trainingscycli.

### Trainingsrapporten weergeven {#viewing-training-reports}

Om te controleren of de Slimme Dienst van de Inhoud op uw markeringen in de trainingsreeks activa wordt getraind, herzie het rapport van de opleidingswerkstroom van de console van Rapporten.

1. Ga in de [!DNL Experience Manager] -interface naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL Reports]** .
1. Klik op **[!UICONTROL Asset Reports]** op de pagina **[!UICONTROL Create]** .
1. Selecteer het rapport **[!UICONTROL Smart Tags Training]** en klik vervolgens op **[!UICONTROL Next]** op de werkbalk.
1. Geef een titel en beschrijving voor het rapport op. Laat onder **[!UICONTROL Schedule Report]** de optie **[!UICONTROL Now]** ingeschakeld. Als u het rapport voor later wilt plannen, selecteert u **[!UICONTROL Later]** en geeft u een datum en tijd op. Klik vervolgens op **[!UICONTROL Create]** op de werkbalk.
1. Selecteer op de pagina **[!UICONTROL Asset Reports]** het rapport dat u hebt gegenereerd. Klik op **[!UICONTROL View]** op de werkbalk om het rapport weer te geven.
1. Bekijk de details van het rapport.

   Het rapport geeft de trainingsstatus weer voor de tags die u hebt getraind. De groene kleur in de kolom **[!UICONTROL Training Status]** geeft aan dat de Smart Content Service is getraind voor de tag. Een gele kleur geeft aan dat de service niet volledig is getraind voor een bepaalde tag. Voeg in dit geval meer afbeeldingen met de desbetreffende tag toe en voer de trainingsworkflow uit om de service volledig op de tag te trainen.

   Als dit rapport uw tags niet bevat, voert u de trainingsworkflow voor deze tags opnieuw uit.

1. Als u het rapport wilt downloaden, selecteert u het in de lijst en klikt u op **[!UICONTROL Download]** op de werkbalk. Het rapport wordt gedownload als een Microsoft Excel-spreadsheet.

## Beperkingen {#limitations}

* Verbeterde slimme tags zijn gebaseerd op leermodellen van afbeeldingen en hun tags. Deze modellen zijn niet altijd perfect bij het identificeren van tags. De huidige versie van de Smart Content Service heeft de volgende beperkingen:

   * Kan subtiele verschillen in afbeeldingen niet herkennen. Bijvoorbeeld dunne en standaard gemonteerde hemden.
   * Kan geen tags identificeren op basis van kleine patronen/delen van een afbeelding. Bijvoorbeeld logo&#39;s op T-shirts.
   * Tags worden ondersteund in de landinstellingen waarin [!DNL Experience Manager] wordt ondersteund.

* Als u wilt zoeken naar elementen met slimme tags (normaal of uitgebreid), gebruikt u [!DNL Assets] Omnzoekopdracht (full-text zoekopdracht). Er is geen afzonderlijke zoekvoorspelling voor slimme tags.

>[!MORELIKETHIS]
>
>* [&#x200B; Overzicht en hoe te om Slimme Markeringen &#x200B;](enhanced-smart-tags.md) te trainen
>* [&#x200B; het Oplossen van problemen slimme markeringen voor geloofsbrieven OAuth &#x200B;](config-oauth.md)
>* [&#x200B; Videozelfstudie over slimme markeringen &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-learn/assets/metadata/image-smart-tags.html?lang=nl-NL)
