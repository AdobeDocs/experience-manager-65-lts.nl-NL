---
title: Toepassingen van derden integreren in de AEM Forms-werkruimte
description: Integreer toepassingen van derden, zoals Correspondence Management, in de AEM Forms-werkruimte.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
exl-id: b383fa80-1643-41f3-bc6c-176727fea688
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '634'
ht-degree: 0%

---

# Toepassingen van derden integreren in de AEM Forms-werkruimte{#integrating-third-party-applications-in-aem-forms-workspace}

De werkruimte van AEM Forms ondersteunt het beheer van taken en voltooiingsactiviteiten voor formulieren en documenten. Deze formulieren en documenten kunnen XDP Forms, Flex®-formulieren of (afgekeurde) hulplijnen zijn die zijn gerenderd in de indelingen XDP, PDF, HTML of Flex.

Deze mogelijkheden worden verder versterkt. AEM Forms biedt nu ondersteuning voor samenwerking met toepassingen van derden die functionaliteit ondersteunen die vergelijkbaar is met de AEM Forms-werkruimte. Een veelvoorkomend onderdeel van deze functionaliteit is de workflow van de toewijzing en de daaropvolgende goedkeuring van een taak. AEM Forms biedt een enkele uniforme ervaring voor AEM Forms-zakelijke gebruikers, zodat al dergelijke taaktoewijzingen of goedkeuringen voor de ondersteunde toepassingen kunnen worden verwerkt via de AEM Forms-werkruimte.

Laten we Correspondence Management bijvoorbeeld beschouwen als de voorbeeldkandidaat voor integratie met de AEM Forms-werkruimte. Correspondentiebeheer heeft het concept van een &#39;brief&#39;, die kan worden weergegeven en acties mogelijk maakt.

## Correspondentenbeheermiddelen maken {#create-correspondence-management-assets}

Begin door een malplaatje van het Beheer van de Correspondentie te creëren dat in de werkruimte van AEM Forms wordt teruggegeven. Voor meer details, zie [ een brievenmalplaatje ](../../forms/using/create-letter.md) creëren.

Heb toegang tot het malplaatje van het Beheer van de Correspondentie bij zijn URL om te verifiëren of het malplaatje van het Beheer van de Correspondentie met succes kan worden teruggegeven. De URL heeft een patroon dat lijkt op `https://'[server]:[port]'/lc/content/cm/createcorrespondence.html?cmLetterId=encodedLetterId&cmUseTestData=1&cmPreview=0;`

Hierbij is `encodedLetterId` de URL-gecodeerde letter-ID. Geef dezelfde letter-id op wanneer u het renderproces voor werkruimtetaak in Workbench definieert.

## Een taak maken om een brief te renderen en te verzenden in AEM Workspace {#create-a-task-to-render-and-submit-a-letter-in-aem-workspace}

Voordat u deze stappen uitvoert, moet u ervoor zorgen dat u lid bent van de volgende groepen:

* cm-agent-gebruikers
* Workspace-gebruikers

Voor meer informatie, zie [ gebruikers ](/help/forms/using/admin-help/adding-configuring-users.md) toevoegen en vormen.

Ga als volgt te werk om een taak te maken om een brief te renderen en te verzenden in AEM Workspace:

1. Start Workbench. Meld u als beheerder aan bij de localhost.
1. Klik op Bestand > Nieuw > Toepassing. Typ `CMDemoSample` in het veld Toepassingsnaam en klik op Voltooien.
1. Selecteer `CMDemoSample/1.0` en klik met de rechtermuisknop `NewProcess` . Typ `CMRenderer` in het naamveld en klik op Voltooien.
1. Sleep de activiteitskiezer voor het beginpunt en configureer deze:

   1. Selecteer bij Presentatiegegevens de optie CRX-element gebruiken.

      ![ useacrxasset ](assets/useacrxasset.png)

   1. Blader naar een element. In het dialoogvenster Formulierelement selecteren worden op het tabblad Letters alle letters op de server weergegeven.

      ![ het lusje van de Brief ](assets/letter_tab_new.png)

   1. Selecteer de aangewezen brief en klik **O.K.**.

1. Klik op Actieprofielen beheren. Het dialoogvenster Actieprofiel beheren wordt geopend. Zorg ervoor dat het renderproces en het verzendproces op de juiste wijze zijn geselecteerd.
1. Als u de letter wilt openen met een XML-gegevensbestand voor gegevens, bladert u naar het desbetreffende gegevensbestand in het proces Gegevens voorbereiden en selecteert u dit.
1. Klik op OK.
1. Definieer de variabelen voor Uitvoer beginpunt en Taakbijlagen. De gedefinieerde variabelen bevatten gegevens van Start Point Output en Task Attachments.
1. (Optioneel) Als u een andere gebruiker aan de workflow wilt toevoegen, sleept u een activiteitskiezer, configureert u deze en wijst u deze toe aan een gebruiker. Schrijf een douaneomslag (hieronder steekproef wordt gegeven) of download en installeer DSC (hieronder gegeven) om het malplaatje van de Brief, de Output van het Punt van het Begin, en taakgehechtheid uit te breiden.

   Hieronder ziet u een voorbeeld van een aangepaste omslag:

   ```javascript
   public LetterInstanceInfo getLetterInstanceInfo(Document dataXML) throws Exception {
   try {
   if(dataXML == null)
   throw new Exception("dataXML is missing");
   
   CoreService coreService = getRemoteCoreService();
   if (coreService == null)
   throw new Exception("Unable to retrive service. Please verify connection details.");
   Map<String, Object> result = coreService.getLetterInstanceInfo(IOUtils.toString(dataXML.getInputStream(), "UTF-8"));
   LetterInstanceInfo letterInstanceInfo = new LetterInstanceInfo();
   
   List<Document> attachmentDocs = new ArrayList<Document>();
   List<byte[]> attachments = (List<byte[]>)result.get(CoreService.ATTACHMENT_KEY);
   if (attachments != null){
   for (byte[] attachment : attachments)
   { attachmentDocs.add(new Document(attachment)); }
   
   }
   letterInstanceInfo.setLetterAttachments(attachmentDocs);
   
   byte[] updateLayout = (byte[])result.get(CoreService.LAYOUT_TEMPLATE_KEY);
   if (updateLayout != null)
   { letterInstanceInfo.setLetterTemplate(new Document(updateLayout)); }
   
   else
   { throw new Exception("template bytes missing while getting Letter instance Info."); }
   
   return letterInstanceInfo;
   } catch (Exception e)
   { throw new Exception(e); }
   
   }
   ```

   [ krijgt Dossier ](assets/dscsample.zip)
DSC downloaden: een voorbeeld-DSC is beschikbaar in het bestand DSCSample.zip dat hierboven is gekoppeld. Download en decomprimeer het bestand DSCSample.zip. Alvorens u de dienst van DSC gebruikt, moet u het vormen. Zie [ de Dienst van DSC ](../../forms/using/add-action-button-in-create-correspondence-ui.md#p-configure-the-dsc-service-p) vormen.

   In de Define dialoog van de Activiteit, selecteer de aangewezen activiteit zoals getLetterInstanceInfo en klik **O.K.**.

1. Implementeer de toepassing. Als u hierom wordt gevraagd, checkt u de middelen in en slaat u deze op.
1. Login aan de de vormenwerkruimte van AEM in https://&#39;[ server ]:[ haven ]&#39;/lc/content/ws.
1. Open de taak die u had toegevoegd, CMRenderer. De letter Correspondence Management wordt weergegeven.

   ![ cminworkspace ](assets/cminworkspace.png)

1. Vul de vereiste gegevens in en verzend de brief. Het venster wordt gesloten. Tijdens dit proces wordt de taak toegewezen aan de gebruiker die in stap 9 in de workflow is opgegeven.

   >[!NOTE]
   >
   >De knop Verzenden wordt pas ingeschakeld als alle vereiste variabelen in de letter zijn ingevuld.
