---
title: Forms-centric workflow op OSGi installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
topic-tags: installing
docset: aem65
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication,AEM Forms on OSGi
exl-id: 4b316ade-4431-41fc-bb8a-7262a17fb456
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '1527'
ht-degree: 0%

---

# Forms-centric workflow op OSGi installeren en configureren{#installing-and-configuring-forms-centric-workflow-on-osgi}

## Inleiding {#introduction}

Ondernemingen verzamelen en verwerken gegevens van meerdere formulieren, back-endsystemen en andere gegevensbronnen. De verwerking van gegevens omvat toetsings- en goedkeuringsprocedures, herhaalde taken en archivering van gegevens. Een formulier reviseren en converteren naar een PDF-document. Wanneer manueel gedaan, kunnen de herhalende taken veel tijd en talrijke middelen vergen.

U kunt [&#x200B; Forms-centric werkschema op OSGi &#x200B;](../../forms/using/aem-forms-workflow.md) gebruiken om adaptieve op vorm-gebaseerde werkschema&#39;s snel te bouwen. Deze workflows kunnen u helpen bij het automatiseren van workflows voor revisie en goedkeuring, workflows voor bedrijfsprocessen en andere herhalende taken. Met deze workflows kunt u ook documenten verwerken (PDF-documenten maken, samenstellen, distribueren en archiveren, digitale handtekeningen toevoegen om de toegang tot documenten te beperken, gecodeerde formulieren decoderen en meer) en de ondertekeningsworkflow voor Adobe-handtekeningen gebruiken voor formulieren en documenten.

Nadat de werkstromen zijn ingesteld, kunnen deze handmatig worden geactiveerd om een gedefinieerd proces te voltooien of via programmacode worden uitgevoerd wanneer gebruikers een formulier of interactieve communicatie verzenden. De mogelijkheid is opgenomen in het invoegpakket voor AEM Forms.

AEM Forms is een krachtig platform op bedrijfsniveau. Forms-gerichte workflow op OSGi is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [&#x200B; Inleiding aan AEM Forms &#x200B;](introduction-aem-forms.md).

>[!NOTE]
>
>Met Forms-centric werkschema op OSGi, kunt u werkschema&#39;s voor diverse taken op de stapel snel bouwen en opstellen OSGi <!--, without having to install the full-fledged Process Management capability on JEE stack-->.<!-- See a [comparison](capabilities-osgi-jee-workflows.md) of the Forms-centric AEM Workflows on OSGi and Process Management on JEE to learn the difference and similarities in the capabilities.--><!--After the comparison, If you choose to install the Process Management capability on JEE stack, see [Install or Upgrade AEM Forms on JEE](/help/forms/using/introduction-aem-forms.md) for detailed information about installing and configuring JEE stack and the Process Management capabilities.-->

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U hebt slechts minimaal één AEM Author Processing-instantie (productieauteur) nodig om de Forms-centric workflow op OSGi-functionaliteit uit te voeren. Een verwerkingsinstantie is a [&#x200B; geharde de Auteur van AEM &#x200B;](/help/forms/using/hardening-securing-aem-forms-environment.md) instantie. Voer geen daadwerkelijke ontwerpbewerkingen uit, zoals het maken van workflows of adaptieve formulieren, op de auteur van de productie.

De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [&#x200B; Architectuur en plaatsingstopologieën voor AEM Forms &#x200B;](/help/forms/using/aem-forms-architecture-deployment.md).

![&#x200B; geadviseerd-topologie &#x200B;](assets/recommended-topology.png)

AEM Forms Forms-centric workflow op OSGi voert de creatieve gebruikersinterface van AEM Inbox en AEM Workflow Model uit op de Author-instanties van AEM Forms.

## Systeemvereisten {#system-requirements}

>[!NOTE]
>
>Skip aan de [&#x200B; Volgende stappen &#x200B;](../../forms/using/installing-configuring-forms-centric-workflow-on-osgi.md#next-steps) sectie van het document, als u reeds AEM Forms op OSGi zoals die in [&#x200B; wordt verklaard installeert en gegevens vormt vangt mogelijkheden &#x200B;](../../forms/using/installing-configuring-aem-forms-osgi.md) artikel.

Voordat u begint met het installeren en configureren van een op Forms gerichte workflow op OSGi, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [&#x200B; technische vereisten &#x200B;](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Een AEM-instantie wordt uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt minstens één AEM-instantie (Auteur of Verwerking) nodig om een op Forms gerichte workflow uit te voeren op OSGi:

   * **Auteur**: Een instantie van AEM die wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** de verwerkingsinstantie van A is a [&#x200B; geharde instantie van de Auteur van AEM &#x200B;](/help/forms/using/hardening-securing-aem-forms-environment.md). Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

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

1. Open [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [&#x200B; Manager van het Pakket &#x200B;](/help/sites-administering/package-manager.md) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

   U kunt het pakket via de directe verbinding ook downloaden die in het [&#x200B; wordt vermeld versies van AEM Forms &#x200B;](https://helpx.adobe.com/nl/aem-forms/kb/aem-forms-releases.html) artikel.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om het AEM-exemplaar opnieuw te starten. **begin niet onmiddellijk de server opnieuw.** alvorens de server van AEM Forms tegen te houden, wacht tot ServiceEvent REGISTERED en ServiceEvent niet GEREGISTREERDE berichten ophouden die in het [ AEM-Installatie-Folder ] /crx-quickstart/logs/error.log- dossier verschijnen en het logboek is stabiel.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van dispatcher en Adobe Target.

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
1. Onderzoek en open **Configuratie van de Firewall 0&rbrace; Deserialization.**
1. Voeg het {**pakket 0} sun.util.endar aan het** lijst van gewenste personen **gebied toe.** Klik op Opslaan.
1. Herhaal stap 1-3 voor alle instanties Auteur en Publiceren.

### Optionele configuraties na installatie {#optional-post-installation-configurations}

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is bezig met het in cache plaatsen en taakverdeling voor AEM. AEM Dispatcher helpt ook de AEM-server te beschermen tegen aanvallen. U kunt de beveiliging van uw AEM-instantie verhogen door de Dispatcher in combinatie met een webserver op bedrijfsniveau te gebruiken. Als u [&#x200B; Dispatcher &#x200B;](https://helpx.adobe.com/nl/experience-manager/dispatcher/using/dispatcher-configuration.html) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Voor gedetailleerde informatie over filters, zie {de documentatie van 0} Dispatcher [&#128279;](https://helpx.adobe.com/nl/experience-manager/dispatcher/using/dispatcher-configuration.html).

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. Standaard URL van de configuratiemanager is https://&#39;server&#39;:[ port_number ]/system/console/configMgr. In het **menu van Configuraties**, selecteer de **Apache het Verdelen van de Filter van de Verwijzing** optie. In het Allow gebied van Gastheren, ga gastheernaam van de verzender in om het als verwijzer toe te staan en klik **sparen**. De opmaak van de vermelding is `https://'[server]:[port]'` .

#### Cache configureren {#configure-cache}

Caching is een mechanisme om gegevenstoegang te verkorten, latentie te verminderen, en input/output (I/O) snelheden te verbeteren. In de cache van adaptieve formulieren worden alleen HTML-inhoud en JSON-structuur van een adaptief formulier opgeslagen zonder dat vooraf ingevulde gegevens worden opgeslagen. Hierdoor wordt de tijd die nodig is om een adaptief formulier te genereren, verkort.

* Bij het gebruiken van het adaptieve vormengeheime voorgeheugen, gebruik [&#x200B; AEM Dispatcher &#x200B;](https://helpx.adobe.com/nl/experience-manager/dispatcher/using/dispatcher-configuration.html) om cliëntbibliotheken (CSS en JavaScript) van een adaptieve vorm in het voorgeheugen onder te brengen.
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

Om het Teken van Adobe met AEM Forms te gebruiken, [&#x200B; integreer het Teken van Adobe met AEM Forms &#x200B;](../../forms/using/adobe-sign-integration-adaptive-forms.md).

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van een op Forms gerichte workflow met OSGi-mogelijkheden. De volgende stappen voor het gebruik van de mogelijkheid zijn:

* [Forms-centric workflow gebruiken op OSGi](../../forms/using/aem-forms-workflow.md)
* [Referentie workflowstap](/help/sites-developing/workflows-step-ref.md)
* [Nabewerking van brieven en interactieve communicatie](../../forms/using/submit-letter-topostprocess.md)
