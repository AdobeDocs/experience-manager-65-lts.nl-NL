---
title: Forms-centric workflow op OSGi installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
topic-tags: installing
docset: aem65
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication,AEM Forms on OSGi
source-git-commit: 168cb023768ff3139937ab7f437ab7d00185bca0
workflow-type: tm+mt
source-wordcount: '1601'
ht-degree: 0%

---

# Forms-centric workflow op OSGi installeren en configureren{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Inleiding {#introduction}

Ondernemingen verzamelen en verwerken gegevens uit meerdere formulieren, back-endsystemen en andere gegevensbronnen. De verwerking van gegevens omvat beoordelings- en goedkeuringsprocedures, repetitieve taken en gegevensarchivering. Bijvoorbeeld het controleren van een formulier en het converteren naar een PDF-document. Wanneer ze handmatig worden uitgevoerd, kunnen de repetitieve taken veel tijd en veel middelen in beslag nemen.

U kunt een formuliergerichte werkstroom op OSGi](../../forms/using/aem-forms-workflow.md) gebruiken [om snel adaptieve werkstromen op basis van formulieren te bouwen. Deze werkstromen kunnen u helpen bij het automatiseren van beoordelings- en goedkeuringswerkstromen, werkstromen voor bedrijfsprocessen en andere repetitieve taken. Deze workflows helpen ook bij het verwerken van documenten (PDF-documenten maken, samenstellen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken, formulieren met streepjescodes decoderen en meer) en bij het gebruik van de Adobe Sign-ondertekeningsworkflow voor formulieren en documenten.

Eenmaal ingesteld, kunnen deze workflows handmatig worden geactiveerd om een gedefinieerd proces te voltooien of programmatisch worden uitgevoerd wanneer gebruikers een formulier of interactieve communicatie verzenden. De mogelijkheid is opgenomen in het add-on-pakket AEM Forms.

AEM Forms is een krachtig platform op bedrijfsniveau. Forms-gerichte workflow op OSGi is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [ Inleiding aan AEM Forms ](introduction-aem-forms.md).

>[!NOTE]
>
>Met Forms-centric workflow op OSGi kunt u snel workflows bouwen en implementeren voor verschillende taken op de OSGi-stack, zonder dat u de volwaardige Process Management-mogelijkheid op de JEE-stack hoeft te installeren. Bekijk een [vergelijking](capabilities-osgi-jee-workflows.md) van de formuliergerichte AEM Workflows op OSGi en Process Management op JEE om het verschil en de overeenkomsten in de mogelijkheden te leren.
>
>Als u ervoor kiest om na de vergelijking de mogelijkheid Procesbeheer op de JEE-stack te installeren, raadpleegt [u AEM Forms op JEE](/help/forms/using/introduction-aem-forms.md) installeren of upgraden voor gedetailleerde informatie over het installeren en configureren van de JEE-stack en de mogelijkheden voor procesbeheer.

## Implementatie Topologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één AEM Author Processing-instantie (productieauteur) nodig om de Forms-centric workflow op OSGi-functionaliteit uit te voeren. Een verwerkingsinstantie is a [ geharde de Auteur van AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md) instantie. Voer geen daadwerkelijke ontwerpbewerkingen uit, zoals het maken van workflows of adaptieve formulieren, op de auteur van de productie.

De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

![ geadviseerd-topologie ](assets/recommended-topology.png)

AEM Forms Forms-centric workflow op OSGi voert de creatieve gebruikersinterface van AEM Inbox en AEM Workflow Model uit op de Author-instanties van AEM Forms.

## Systeemvereisten {#system-requirements}

>[!NOTE]
>
>Skip aan de [ Volgende stappen ](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) sectie van het document, als u reeds AEM Forms op OSGi zoals die in [ wordt verklaard installeert en gegevens vormt vangt mogelijkheden ](../../forms/using/installing-configuring-aem-forms-osgi.md) artikel.

Voordat u begint met het installeren en configureren van een op Forms gerichte workflow op OSGi, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Een AEM-instantie wordt uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt minstens één AEM-instantie (Auteur of Verwerking) nodig om een op Forms gerichte workflow uit te voeren op OSGi:

   * **Auteur**: Een instantie van AEM die wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** de verwerkingsinstantie van A is a [ geharde instantie van de Auteur van AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md). Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **publiceer**: Een instantie van AEM die de gepubliceerde inhoud aan het publiek over Internet of een intern netwerk dient.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft Windows-installaties.
   * 6 GB tijdelijke ruimte voor UNIX-installaties.

* Extra vereisten voor op UNIX gebaseerde systemen: als u het op UNIX gebaseerde besturingssysteem gebruikt, installeert u de volgende pakketten via de installatiemedia van het desbetreffende besturingssysteem.

<table>
 <tbody>
  <tr>
   <td>uitzetten</td>
   <td>libxcb</td>
   <td>freetype</td>
   <td>libXau</td>
  </tr>
  <tr>
   <td>libSM</td>
   <td>zlib</td>
   <td>libICE</td>
   <td>libuuid</td>
  </tr>
  <tr>
   <td>glibc</td>
   <td>libXext</td>
   <td><p>nss-softokn-freebl</p> </td>
   <td>fontconfig</td>
  </tr>
  <tr>
   <td>libX11</td>
   <td>libXrender</td>
   <td>libXrandr</td>
   <td>libXinerama</td>
  </tr>
 </tbody>
</table>

## AEM Forms-invoegtoepassing installeren {#install-aem-forms-add-on-package}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat een op Forms gerichte workflow voor OSGi en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](https://experienceleague.adobe.com/docs/experience-manager-65-lts/administering/contentmanagement/package-manager.html) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]**.

   U kunt het pakket ook downloaden via de directe koppeling die wordt vermeld in het artikel over AEM [Forms-releases](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) .

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd het AEM exemplaar opnieuw te starten. **Start de server niet onmiddellijk opnieuw op.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het [bestand AEM-Installation-Directory]/crx-quickstart/logs/error.log en het logboek stabiel is.

   >[!NOTE]
   >
   > Het wordt aanbevolen om de opdracht &#39;Ctrl + C&#39; te gebruiken om de SDK opnieuw op te starten. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een aantal verplichte en optionele configuraties. De verplichte configuraties omvatten het configureren van BouncyCastle-bibliotheken en serialisatieagent. De optionele configuraties omvatten het configureren van de dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM-instantie.
1. Open het [ dossier van de de installatiemap van AEM ] \crx-quickstart\conf\sling.properties voor het uitgeven.

   Als u [ de installatiemap van AEM ] \crx-quickstart\bin\start.bat gebruikte om AEM te beginnen, dan de sling.properties die bij [ worden gevestigd AEM_root ] \ crx-quickstart \ uit te geven.

1. Voeg de volgende eigenschappen toe aan het bestand sling.properties:

   ```shell
   sling.bootdelegation.class.com.rsa.jsafe.provider.JsafeJCE=com.rsa.*  
   ```

1. Sla het bestand op, sluit het en start het AEM-exemplaar.
1. Herhaal stap 1-4 voor alle instanties Auteur en Publiceren.

#### Vorm de rangschikkingsagent {#configure-the-serialization-agent}

Voer de volgende stappen uit op alle instanties Auteur en Publish om het pakket aan de lijst van gewenste personen toe te voegen:

1. Open AEM Configuration Manager in een browservenster. Het gebrek URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.
1. Onderzoek en open **Configuratie van de Firewall 0} Deserialization.**
1. Voeg het {**pakket 0} sun.util.endar aan het** lijst van gewenste personen **gebied toe.** Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is bezig met het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook de AEM-server te beschermen tegen aanvallen. U kunt de beveiliging van uw AEM-instantie verhogen door de Dispatcher in combinatie met een webserver op bedrijfsniveau te gebruiken. Als u [ Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Voor gedetailleerde informatie over filters, zie {de documentatie van 0} Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html).[

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. Standaard URL van de configuratiemanager is https://&#39;server&#39;:[ port_number ]/system/console/configMgr. In het **menu van Configuraties**, selecteer de **Apache het Verdelen van de Filter van de Verwijzing** optie. In het Allow gebied van Gastheren, ga gastheernaam van de verzender in om het als verwijzer toe te staan en klik **sparen**. De opmaak van de vermelding is `https://'[server]:[port]'` .

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Bij het gebruiken van het adaptieve vormengeheime voorgeheugen, gebruik [ AEM Dispatcher ](https://helpx.adobe.com/experience-manager/dispatcher/using/dispatcher-configuration.html) om cliëntbibliotheken (CSS en JavaScript) van een adaptieve vorm in het voorgeheugen onder te brengen.
* Zorg tijdens het ontwikkelen van aangepaste componenten dat de cache van adaptieve formulieren uitgeschakeld blijft op de server die voor ontwikkeling wordt gebruikt.

Voer de volgende stappen uit om de cache voor adaptieve formulieren te configureren:

1. Ga naar AEM webconsoleconfiguratiebeheer op `https://'[server]:[port]'/system/console/configMgr` .
1. Klik op **[!UICONTROL Adaptive Form and Interactive Communication Web Channel Configuration]** om de configuratiewaarden ervan te bewerken. In geef de dialoog van de configuratiewaarden uit, specificeer het maximumaantal vormen of documenten een geval van de server van AEM Forms in het **Aantal van het AanpassingsForms** gebied in cache kan plaatsen. De standaardwaarde is 100. Klik **sparen**.

   >[!NOTE]
   >
   >Om het geheime voorgeheugen onbruikbaar te maken, plaats de waarde op het Aantal van het AanpassingsForms gebied aan **0**. De cache wordt opnieuw ingesteld en alle formulieren en documenten worden uit de cache verwijderd wanneer u de cachemonfiguratie uitschakelt of wijzigt.

#### Adobe-ondertekening configureren {#configure-adobe-sign}

Met Adobe Sign kunnen workflows voor e-handtekeningen worden gebruikt voor adaptieve formulieren. E-handtekeningen verbeteren workflows om documenten te verwerken voor juridische documenten, verkoop, salarisadministratie, personeelsbeheer en nog veel meer gebieden.

In een typisch het Ondertekenen van Adobe en Forms-centric werkschema op scenario OSGi, vult een gebruiker een adaptieve vorm aan **van toepassing is voor de dienst**. Bijvoorbeeld een creditcardaanvraag en een burgerservicepakket. Wanneer een gebruiker het aanvraagformulier invult, verzendt en ondertekent, wordt een workflow voor goedkeuring/afwijzing gestart. Het servicebureau evalueert de toepassing in AEM Inbox en gebruikt Adobe Sign om de toepassing elektronisch te ondertekenen. Als u vergelijkbare workflows voor elektronische handtekeningen wilt inschakelen, kunt u Adobe Sign met AEM Forms integreren.

Om het Teken van Adobe met AEM Forms te gebruiken, [ integreer het Teken van Adobe met AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van een op Forms gerichte workflow met OSGi-mogelijkheden. De volgende stappen voor het gebruik van de mogelijkheid zijn:

* [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Nabewerking van brieven en interactieve communicatie](../../forms/using/submit-letter-topostprocess.md)
