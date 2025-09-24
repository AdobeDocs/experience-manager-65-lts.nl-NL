---
title: Adobe Sign with AEM Forms integreren
description: Leer Adobe Sign voor uw AEM Adaptive Forms te configureren. Adobe Sign verbetert de workflow en verwerkt de documenten voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.
feature: Adaptive Forms,Foundation Components,Acrobat Sign
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: fdf95738-3075-43d6-9d51-64c83cf0f0b7
source-git-commit: 30ec8835be1af46e497457f639d90c1ee8b9dd6e
workflow-type: tm+mt
source-wordcount: '1896'
ht-degree: 0%

---

# [!DNL Adobe Sign] integreren met AEM [!DNL Forms]{#integrate-adobe-sign-with-aem-forms}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [ Componenten van de Kern ](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html) voor [ het creëren van nieuwe Aangepaste Forms ](/help/forms/using/create-an-adaptive-form-core-components.md) of [ het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites ](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

## Van toepassing op {#applies-to}

Deze documentatie is op **AEM 6.5 LTS Forms** van toepassing.

Voor de documentatie van AEM as a Cloud Service, zie [ AEM Forms op Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/integrate/services/adobe-sign-integration-adaptive-forms.html?lang=en#adobe-acrobat-sign-for-government).

Met [!DNL Adobe Sign] kunt u workflows voor e-handtekeningen inschakelen voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een standaard [!DNL Adobe Acrobat Sign] - en Adaptief Forms-scenario vult een gebruiker een adaptief formulier in om een service aan te vragen. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het toepassingsformulier invult, verzendt en ondertekent, wordt het formulier naar de serviceprovider verzonden voor verdere actie. Serviceprovider controleert de toepassing en gebruikt [!DNL Adobe Acrobat Sign] om de goedgekeurde toepassing te markeren. AEM Forms steunt zowel Adobe Acrobat Sign als Adobe Acrobat Sign Solutions voor de regering. Afhankelijk van uw licentie en vereisten kunt u AEM Forms integreren in of verbinden met een van de twee oplossingen:

* [AEM Forms verbinden met Adobe Acrobat Sign](#adobe-sign)
* [Connect AEM Forms met Adobe Acrobat Sign Solutions for Government](#adobe-acrobat-sign-for-government)

## AEM Forms verbinden met Adobe Acrobat Sign {#adobe-sign}

Als u **[!DNL AEM Forms]** wilt verbinden met **[!DNL Adobe Acrobat Sign]** , stelt u de software en accounts in die worden vermeld in de sectie met voorwaarden en verbindt u Adobe Sign met alle instanties van AEM Forms Author and Publish:

## Vereisten {#prerequisites}

U hebt het volgende nodig om [!DNL Adobe Sign] te integreren met AEM [!DNL Forms] :

* Een actieve [ rekening van de ontwikkelaar van het Teken van Adobe.](https://www.adobe.com/acrobat/business/developer-form.html)
* Een [ SSL toegelaten ](/help/sites-administering/ssl-by-default.md) AEM [!DNL Forms] server.
* Een [ toepassing van het Teken van Adobe API ](https://opensource.adobe.com/acrobat-sign/developer_guide/index.html#!adobedocs/adobe-sign/master/gstarted/create_app.md).
* Referenties (client-id en clientgeheim) van [!DNL Adobe Sign] API-toepassing.
* Wanneer u de configuratie opnieuw configureert, verwijdert u de bestaande [!DNL Adobe Sign] -configuratie uit zowel auteur- als publicatieinstanties.
* Gebruik [ identieke crypto sleutel ](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur en publiceer instanties.

## [!DNL Adobe Sign] configureren met AEM [!DNL Forms] {#configure-adobe-sign-with-aem-forms}

Voer de volgende stappen uit om [!DNL Adobe Sign] te configureren met AEM [!DNL Forms] in de Author-instantie nadat aan de voorwaarden is voldaan:

1. Op AEM [!DNL Forms] auteursinstantie, navigeer aan **Hulpmiddelen** ![ hamer ](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Selecteer op de pagina **[!UICONTROL Configuration Browser]** de optie **[!UICONTROL Create]** .
   * Zie Browser van de Configuratie [ documentatie 0&rbrace; &lbrace;voor meer informatie.](/help/sites-administering/configurations.md)
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** voor de configuratie op, schakel **[!UICONTROL Cloud Configurations]** in en selecteer **[!UICONTROL Create]** . Er wordt een configuratiecontainer gemaakt.
1. Navigeer aan **Hulpmiddelen** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]** en selecteer de configuratiecontainer u in de bovengenoemde stap creeerde.

   >[!NOTE]
   >
   >U kunt of stappen 1-4 uitvoeren om een configuratiecontainer tot stand te brengen en een [!DNL Adobe Sign] configuratie in de container tot stand te brengen of de bestaande `global` omslag in **Hulpmiddelen** ![ te gebruiken hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Sign]**. Als u de configuratie maakt in de nieuwe configuratiecontainer, moet u de naam van de container opgeven in het veld **[!UICONTROL Configuration Container]** wanneer u een adaptief formulier maakt.

   >[!NOTE]
   >
   >Zorg ervoor dat URL van de Pagina van de Configuratie van de Diensten van de Wolk met **HTTPS** begint. Als niet, [ laat SSL ](/help/sites-administering/ssl-by-default.md) voor de server van AEM [!DNL Forms] toe.


1. Tik op de configuratiepagina op **[!UICONTROL Create]** om [!DNL Adobe Sign] configuration in AEM [!DNL Forms] te maken.
1. Geef op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Create Adobe Sign Configuration]** -pagina een **[!UICONTROL Name]** voor de configuratie op en tik op **[!UICONTROL Next]** . U kunt desgewenst een titel opgeven en naar een miniatuur voor de configuratie bladeren.
1. U kunt nu **[!UICONTROL Select solution]** selecteren om [!DNL Adobe Acrobat Sign] te selecteren.

   ![ Adobe Acrobat Sign Solutions ](/help/forms/using/assets/adobe-sign-solution.png)

1. Kopieer de URL in het huidige browservenster naar een aantekenblok en verwijder het onderdeel /`ui#/aem` van de URL. De gewijzigde URL is vervolgens vereist om de [!DNL Adobe Acrobat Sign] -toepassing in een latere stap te configureren met [!DNL AEM Forms] . Tik op [!UICONTROL Next] .

1. Op het tabblad **[!UICONTROL Settings]**
   * het veld **[!UICONTROL OAuth URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/public/oauth/v2`

     Bijvoorbeeld:
     `https://secure.na1.echosign.com/public/oauth/v2`

   * het veld **[!UICONTROL Access token URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/oauth/v2/token`

     Bijvoorbeeld:
     `https://api.na1.echosign.com/oauth/v2/token`

   waarbij:

   **na1** verwijst naar het standaardgegevensbestandaandeel. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL &#x200B; Adobe Acrobat Sign] Configuraties van de Wolk aan [ correct richten deelt ](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   >* Houd **creeer de Configuratie van Adobe Acrobat Sign** open pagina. Sluit het bestand niet. U kunt **Identiteitskaart van de Cliënt terugwinnen** en **Geheime cliënt** na het vormen van montages OAuth voor de [!DNL Adobe Acrobat Sign] toepassing zoals die in volgende stappen wordt beschreven.
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over de Adobe Sign OAuth URL en Access Token URL.

1. Configureer OAuth-instellingen voor de [!DNL Adobe Sign] -toepassing:

   1. Open een browservenster en meld u aan bij de [!DNL Adobe Sign] -ontwikkelaarsaccount.
   1. Selecteer de toepassing die voor AEM is geconfigureerd [!DNL Forms] en selecteer **[!UICONTROL Configure OAuth for Application]** .
   1. Kopieer de **[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** naar een laptop.
   1. Voeg in het vak **[!UICONTROL Redirect URL]** de HTTPS-URL toe die u in de vorige stap hebt gekopieerd.
   1. Schakel de volgende OAuth-instellingen voor de [!DNL Adobe Sign] -toepassing in en klik op **[!UICONTROL Save]** .

   * agreement_read
   * agreement_write
   * agreement_send
   * widget_write
   * workflow_read

   Voor geleidelijke informatie om montages OAuth voor een [!DNL Adobe Sign] toepassing te vormen en de sleutels te verkrijgen, zie [ montages van Auth voor de 2&rbrace; de ontwikkelaarsdocumentatie van de toepassing &lbrace;vormen.](https://developer.adobe.com/apis/documentcloud/sign/docs.html#!adobedocs/adobe-sign/master/gstarted/configure_oauth.md)

   ![ OAuth Config ](assets/oauthconfig_new.png)

<!--
1. Go back to the **[!UICONTROL Create Adobe Sign Configuration]** page. In the **[!UICONTROL Settings]** tab, the **[!UICONTROL OAuth URL]** field mentions the  default URL. The format of the URL is:

   `https://<shard>/public/oAuth/v2`

   For example: 
   `https://secure.na1.echosign.com/public/oauth/v2`

   where:

   **na1** refers to the default database shard.

   You can modify the value for the database shard. Restart the server to be able to use the new value for the database shard.

   >[!NOTE]
   >
   >Ensure that your author and publish instance configurations point to the same shard. If you create multiple Adobe Sign configurations for an organization, ensure all the configurations utilize the same shard. -->

1. Ga terug naar de **[!UICONTROL Create Adobe Sign Configuration]** pagina. In het **[!UICONTROL Settings]** lusje, specificeer **identiteitskaart van de Cliënt** (die ook als identiteitskaart van de Toepassing wordt bedoeld) en **Geheim van de Cliënt**. Gebruik [ identiteitskaart van de Cliënt en Geheim van de Cliënt van de toepassing van het Teken van Adobe ](https://opensource.adobe.com/acrobat-sign/developer_guide/helloworld.html#get-the-app-id-and-secret) die voor AEM Forms wordt gecreeerd.

1. Selecteer de optie **[!UICONTROL Enable Adobe Sign for attachments also]** om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het bijbehorende [!DNL Adobe Sign] -document dat is verzonden voor ondertekening.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL Adobe Sign] -toepassing.

   ![ Succes van de Configuratie van de Wolk Adobe Acrobat Sign ](assets/adobe-sign-cloud-configuration-success.png)

1. Tik op **[!UICONTROL Create]** om de [!DNL Adobe Sign] -configuratie te maken.
1. Open AEM-webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Openen **[!UICONTROL Forms Common Configuration Service].**
1. Op het **[!UICONTROL Allow]** gebied, **uitgezocht** Alle gebruikers - Alle gebruikers, anoniem of het programma geopend, kunnen voorproef gehechtheid, vormen verifiëren en ondertekenen, en **[!UICONTROL Save]klikken.** De instantie Auteur is geconfigureerd voor gebruik van [!DNL Adobe Sign] .
1. Publiceer de configuratie.
1. De replicatie van het gebruik [&#128279;](/help/sites-deploying/replication.md) om identieke configuratie op het corresponderen te creëren publiceert instanties.

[!DNL Adobe Sign] is nu geïntegreerd met AEM [!DNL Forms] en klaar voor gebruik in adaptieve formulieren. Om [ de dienst van het Ondertekenen van Adobe in een adaptieve vorm ](../../forms/using/working-with-adobe-sign.md#configure-adobe-sign-for-an-adaptive-form) te gebruiken, specificeer de configuratiecontainer hierboven in adaptieve vormeigenschappen wordt gecreeerd die.

>[!NOTE]
>
> Om de zandbak van het Teken van Adobe te vormen, kunt u de zelfde configuratiestappen volgen zoals die in [ het Teken van Adobe ](#adobe-sign) worden verklaard.

## Connect AEM Forms met Adobe Acrobat Sign Solutions for Government {#adobe-acrobat-sign-for-government}

Het verbinden van AEM Forms met Adobe Acrobat Sign Solutions voor de overheid is een proces dat uit meerdere stappen bestaat. Het gaat om:

* Omleidings-URL maken voor uw AEM-instanties
* URL en bereik omleiden delen met het Adobe-team Oplossingen ondertekenen voor de overheid
* Referenties ontvangen van het Adobe-ondertekeningsteam
* Ontvangen gebruikersgegevens gebruiken om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

![ adobe-acrobat-sign-govt-workflow ](/help/forms/using/assets/adobe-acrobat-sign-govt-workflow.png)

### Voordat u begint {#prerequisites-for-adobe-sign-for-acrobat-sign-for-government}

Voordat u AEM Forms gaat verbinden met Adobe Acrobat Sign Solution,

* Zorg ervoor dat uw [ Adobe Acrobat Sign Solutions voor de rekening van de Regering ](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#account-provisioning) provisioned is.
* Uw AEM [!DNL Forms] servers zijn [ toegelaten SSL ](/help/sites-administering/ssl-by-default.md).
* Uw AEM [!DNL Forms] servers gebruiken [ identieke crypto sleutel ](/help/sites-administering/security-checklist.md#make-sure-you-properly-replicate-encryption-keys-when-needed) voor auteur en publiceer instanties.

### AEM Forms verbinden met Adobe Acrobat Sign Solutions voor de overheid {#connect-adobe-acrobat-sign-for-government}

#### Een omleidings-URL maken voor uw AEM-instantie

1. Voor uw instantie van AEM Forms, navigeer aan **[!UICONTROL Tools]** ![ hammer ](assets/hammer.png) > **[!UICONTROL General]** > **[!UICONTROL Configuration Browser]**.
1. Selecteer op de pagina **[!UICONTROL Configuration Browser]** de optie **[!UICONTROL Create]** .
1. Geef in het dialoogvenster **[!UICONTROL Create Configuration]** een **[!UICONTROL Title]** voor de configuratie op, schakel **[!UICONTROL Cloud Configurations]** in en selecteer **[!UICONTROL Create]** . Er wordt een configuratiecontainer gemaakt. Zorg ervoor dat de naam van de container/map geen ruimte bevat.

1. Navigeer aan **[!UICONTROL Tools]** ![ hamer ](assets/hammer.png) > **[!UICONTROL Cloud Services]** > **[!UICONTROL Adobe Acrobat Sign]** en open de configuratiecontainer u in de vorige stap creeerde. Wanneer u een adaptief formulier maakt, geeft u de naam van de container op in het veld **[!UICONTROL Configuration Container]** .
1. Selecteer op de configuratiepagina **[!UICONTROL Create]** om [!DNL Adobe Acrobat Sign] -configuratie te maken in AEM Forms.
1. Kopieer de URL van het huidige browservenster naar een aantekenblok via de URL. Deze URL wordt `re-direct URL` genoemd. In de volgende sectie deelt u de instructies `re-direct URL` en `Scopes` met het Adobe-ondertekeningsteam en vraagt u referenties aan (client-id en clientgeheim).

>[!NOTE]
>
>
> * A `re-direct URL` zou a [ top-level ](https://en.wikipedia.org/wiki/Top-level_domain) domein moeten bevatten. Bijvoorbeeld: `https://adobe.com/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global`
> * Gebruik geen lokale URL als `re-direct URL`. Bijvoorbeeld `https://localhost:4502/libs/adobesign/cloudservices/adobesign/createcloudconfigwizard/cloudservices.html/conf/global` .


#### Deel de omleiding van URL en het bereik met het Adobe-ondertekeningsteam en ontvang referenties

Het team van Adobe Acrobat Sign for Government Solutions vereist dat `re-direct URL` en het bepaalde bereik zijn ingeschakeld voor uw Adobe Acrobat Sign-toepassing (hieronder vermeld) om referenties te genereren (client-id en clientgeheim) waarmee u AEM Forms kunt verbinden met Adobe Acrobat Sign Solutions for Government.

Deel `scopes` (hieronder vermeld) en `re-direct URL` creeerde en noteerde neer de laatste stap van vorige sectie met uw Adobe Acrobat Sign voor het teamlid van de Oplossing van de Overheid [ Adobe Professional Services ](https://opensource.adobe.com/acrobat-sign/signgov/gstarted.html#password).

**_Scopes_**

* [!DNL agreement_read]
* [!DNL agreement_write]
* [!DNL agreement_send]
* [!DNL widget_read]
* [!DNL widget_write]
* [!DNL workflow_read]
* [!DNL offline_access]

De vertegenwoordiger genereert en deelt referenties met u. In de volgende sectie gebruikt u de referenties (client-id en clientgeheim) om AEM Forms te verbinden met Adobe Acrobat Sign Solutions for Government.

#### Gebruik de ontvangen referenties om AEM Forms te verbinden met Adobe Acrobat Sign Solutions voor de overheid

1. Open `re-direct URL` in uw browser. U creeerde en noteerde neer `re-direct URL` in de laatste stap van [ tot een omleidingsURL op uw instantie van AEM ](#create-redirect-url) sectie.

1. Geef op het tabblad **[!UICONTROL General]** van de **[!UICONTROL Create Adobe Sign Configuration]** -pagina een **[!UICONTROL Name]** voor de configuratie op en selecteer **[!UICONTROL Next]** . U kunt optioneel een **[!UICONTROL Title]** opgeven en bladeren om een **[!UICONTROL Thumbnail]** voor de configuratie te selecteren. Klik op **[!UICONTROL Next]**.

1. Selecteer **[!UICONTROL Settings]** op het tabblad **[!UICONTROL Create Adobe Sign Configuration]** van de **[!UICONTROL Select solution]** -pagina voor de optie [!DNL Adobe Acrobat Sign Solutions for Government] .

   ![ Adobe Acrobat Sign Solutions voor Regering ](/help/forms/using/assets/adobe-sign-for-govt.png)

1. Geef in het veld **[!UICONTROL Email]** het e-mailadres op dat is gekoppeld aan uw Adobe Acrobat Sign Solutions for Government-account.

1. Op het tabblad **[!UICONTROL Settings]**
   * het veld **[!UICONTROL OAuth URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/authorize`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/authorize`

   * het veld **[!UICONTROL Access token URL]** bevat de standaard-URL, die de Adobe Sign-databaseschakel bevat. De opmaak van de URL is:

     `https://<shard>/api/gateway/adobesignauthservice/api/v1/token`

     Bijvoorbeeld:
     `https://secure.na1.adobesign.us/api/gateway/adobesignauthservice/api/v1/token`

   waarbij:

   **na1** verwijst naar het standaardgegevensbestandaandeel. U kunt de waarde voor het delen van de database wijzigen. Zorg ervoor dat de [!DNL &#x200B; Adobe Acrobat Sign] Configuraties van de Wolk aan [ correct richten deelt ](https://helpx.adobe.com/sign/using/identify-account-shard.html).

   >[!NOTE]
   >
   > * Nadat u zich hebt aangemeld bij uw Adobe Sign-account, navigeert u naar **[!UICONTROL Acrobat Sign API]** > **[!UICONTROL API Information]** > **[!UICONTROL REST API Methods Documentation]** > **[!UICONTROL OAuth Access Token]** voor toegang tot informatie over de URL van de Adobe Sign Auth en Access Token URL.

1. Gebruik de geloofsbrieven die door Adobe Acrobat Sign voor de vertegenwoordiger van de Oplossing van de Overheid ([ Adobe Professional Services teamlid ]) in de vorige sectie als &lbrack;**[!UICONTROL Client ID]** en **[!UICONTROL Client Secret]** worden gedeeld.

1. Selecteer de optie **[!UICONTROL Enable Adobe Acrobat Sign for attachments]** om bestanden die zijn gekoppeld aan een adaptief formulier, toe te voegen aan het corresponderende [!DNL Adobe Acrobat Sign] -document dat ter ondertekening is verzonden.

1. Selecteer **[!UICONTROL Connect to Adobe Sign]**. Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL Adobe Acrobat Sign] -toepassing. Klik op `Adobe Acrobat Sign for Government Solutions` wanneer u wordt gevraagd de toegang voor **[!UICONTROL Allow Access]** en  te bevestigen. Als de gegevens juist zijn en u [!DNL AEM Forms] toegang geeft tot uw [!DNL Adobe Acrobat Sign] -ontwikkelaarsaccount, verschijnt een succesbericht dat lijkt op het volgende.

   ![ Succes van de Configuratie van de Wolk Adobe Acrobat Sign ](/help/forms/using/assets/adobe-sign-cloud-configuration-success.png)

   Geef bij de aanwijzing voor referenties de gebruikersnaam en het wachtwoord op van het account dat wordt gebruikt bij het maken van de [!DNL Adobe Acrobat Sign] -toepassing. Klik op `your account` wanneer u wordt gevraagd de toegang voor **[!UICONTROL Allow Access]** te bevestigen.

1. Selecteer **[!UICONTROL Create]** om de configuratie te maken.
1. Open AEM-webconsole. De URL is `https://'[server]:[port]'/system/console/configMgr`
1. Openen **[!UICONTROL Forms Common Configuration Service].**
1. Op het **[!UICONTROL Allow]** gebied, **uitgezocht** Alle gebruikers - Alle gebruikers, anoniem of het programma geopend, kunnen voorproef gehechtheid, vormen verifiëren en ondertekenen, en **[!UICONTROL Save]klikken.** De instantie Auteur is geconfigureerd voor gebruik van [!DNL Adobe Sign] .

1. Publiceer de configuratie.
1. De replicatie van het gebruik [&#128279;](/help/sites-deploying/replication.md) om identieke configuratie op het corresponderen te creëren publiceert instanties.

Nu, kunt u [ gebruiken toevoegt de gebieden van Adobe Acrobat Sign in een AanpassingsVorm ](working-with-adobe-sign.md) of [ Werkschema van AEM ](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step). Zorg ervoor dat u de configuratiecontainer die voor de Cloud Service-configuratie wordt gebruikt, toevoegt aan alle Adaptive Forms die voor [!DNL Adobe Acrobat Sign] wordt ingeschakeld. U kunt een configuratiecontainer opgeven met de eigenschappen van een adaptief formulier.


## Configureer de [!DNL Adobe Sign] planner voor synchronisatie van de ondertekeningsstatus {#configure-adobe-sign-scheduler-to-sync-the-signing-status}

Een [!DNL Adobe Sign] ingeschakeld adaptief formulier wordt alleen verzonden nadat alle ondertekenaars het ondertekeningsproces hebben voltooid. Standaard wordt de respons van de ondertekenaar van de [!DNL Adobe Sign] Scheduler-services na elke 24 uur gecontroleerd. U kunt het standaardinterval voor uw milieu veranderen. Voer de volgende stappen uit om het standaardinterval te wijzigen:

1. Login aan de server van AEM [!DNL Forms] met admin geloofsbrieven en navigeer aan **Hulpmiddelen** > **[!UICONTROL Operations]** > **[!UICONTROL Web Console]**.

   U kunt ook de volgende URL openen in een browservenster:
   `https://[localhost]:'port'/system/console/configMgr`

1. Zoek en open de optie **[!UICONTROL Adobe Sign Configuration Service]** . Specificeer a [ gewassenuitdrukking ](https://en.wikipedia.org/wiki/Cron#CRON_expression) op het **[!UICONTROL Status Update Scheduler Expression]** gebied en klik **[!UICONTROL Save]**. Bijvoorbeeld, om de configuratieservice dagelijks om 00 :00 am in werking te stellen, specificeer `0 0 0 1/1 * ? *` op het **[!UICONTROL Status Update Scheduler Expression]** gebied.

Het standaardinterval voor het synchroniseren van de status van [!DNL Adobe Sign] wordt nu gewijzigd.

## Verwante artikelen {#related-articles}

* [Adobe Sign in een adaptief formulier gebruiken](../../forms/using/working-with-adobe-sign.md)
* [Adobe Ondertekenen met FormsCentral-workflows](/help/forms/using/aem-forms-workflow-step-reference.md#sign-document-step-sign-document-step)
* [ Gebruikend het Teken van Adobe met AEM Forms (Video) ](https://helpx.adobe.com/experience-manager/kt/forms/using/adobe-sign-integration-feature-video.html)
