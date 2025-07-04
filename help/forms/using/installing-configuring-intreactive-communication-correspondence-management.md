---
title: Interactieve communicatie installeren en configureren
description: Installeer en configureer AEM Forms Interactive Communications om zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits te maken.
role: Admin, User, Developer
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication,Correspondence Management
exl-id: d03965e1-4fa3-414c-80b6-c9fca281bee4
source-git-commit: bd33420307a7be6664b6bbb52677af66edaa9c0e
workflow-type: tm+mt
source-wordcount: '1366'
ht-degree: 0%

---

# Interactieve communicatie installeren en configureren{#install-and-configure-interactive-communications}

## Inleiding {#introduction}

Met AEM Form kunt u het maken, samenstellen, beheren en leveren van beveiligde en interactieve documenten, zoals zakelijke correspondentie, documenten, instructies, kennisgevingen van voordelen, marketingmails, facturen en welkomstkits, centraliseren. Dit vermogen is gekend als interactieve mededeling. De mogelijkheid is opgenomen in het invoegpakket voor AEM Forms. Het invoegpakket wordt geïmplementeerd op een instantie Auteur of Publiceren van AEM.

U kunt de interactieve communicatiemogelijkheid gebruiken om communicatie in meerdere indelingen te produceren. Bijvoorbeeld web en PDF. U kunt interactieve communicatie met de Workflow van AEM integreren om de geassembleerde communicatie te verwerken en te leveren aan klanten op het kanaal van hun keuze. U kunt bijvoorbeeld een communicatie naar de eindgebruiker verzenden via e-mail.

Als u van een vorige versie bevordert en reeds in brievenbeheer hebt geïnvesteerd, kunt u het [ verenigbaarheidspakket ](../../forms/using/installing-configuring-intreactive-communication-correspondence-management.md#install-compatibility-package) installeren om correspondentiebeheer te blijven gebruiken. Voor informatie over de verschillen tussen interactieve mededeling en brievenbeheer, zie [ Interactief Communicatie Overzicht ](/help/forms/using/interactive-communications-overview.md#interactive-communications-vs-correspondence-management).

AEM Forms is een krachtig platform op bedrijfsniveau. Interactieve communicatie is slechts een van de mogelijkheden van AEM Forms. Voor de volledige lijst van mogelijkheden, zie [ Inleiding aan AEM Forms ](../../forms/using/introduction-aem-forms.md).

## Implementatietopologie {#deployment-topology}

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. U vereist slechts een minimum van één instantie van de Auteur en van de Verwerking van AEM om het Interactieve Communicatie vermogen in werking te stellen. De volgende topologie is indicatieve topologie om de Interactieve Mededelingen van AEM Forms, het Beheer van de Correspondentie, AEM Forms gegevensvangst, en Forms-Centric werkschema op mogelijkheden in werking te stellen OSGi. Voor gedetailleerde informatie over de topologie, zie [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md).

![ geadviseerd-topologie ](assets/recommended-topology.png)

AEM Forms Interactive Communications voert admin, authoring en gebruikersinterfaces voor agent uit op de Author-instanties van AEM Forms. De instanties van de Publish gastheer definitieve versie van interactieve mededelingen die klaar voor consumptie door eindgebruikers zijn.

## Systeemvereisten {#system-requirements}

Voordat u de mogelijkheden voor interactief communicatie- en correspondentiebeheer van AEM Forms gaat installeren en configureren, moet u ervoor zorgen dat:

* Hardware- en software-infrastructuur is aanwezig. Voor een gedetailleerde lijst van gesteunde hardware en software, zie [ technische vereisten ](/help/sites-deploying/technical-requirements.md).

* Het installatiepad van de AEM-instantie bevat geen spaties.
* Een AEM-instantie wordt uitgevoerd. In AEM-terminologie is een &quot;instantie&quot; een kopie van AEM die wordt uitgevoerd op een server in de auteur- of publicatiemodus. U hebt ten minste één AEM-instantie (Auteur of Verwerking) nodig om AEM Forms interactieve communicatie- en correspondentiebeheermogelijkheden uit te voeren:

   * **Auteur**: Een instantie van AEM die wordt gebruikt om, inhoud tot stand te brengen te uploaden en uit te geven en de website te beheren. Wanneer de inhoud gereed is om live te gaan, wordt deze gekopieerd naar de publicatie-instantie.
   * **Verwerking:** de verwerkingsinstantie van A is a [ geharde instantie van de Auteur van AEM ](/help/forms/using/hardening-securing-aem-forms-environment.md). Nadat u de installatie hebt uitgevoerd, kunt u een instantie Auteur instellen en deze lastiger maken.

   * **publiceer**: Een instantie van AEM die de gepubliceerde inhoud aan het publiek over Internet of een intern netwerk dient.

* Er wordt voldaan aan de geheugenvereisten. AEM Forms-add-on-pakket vereist:

   * 15 GB tijdelijke ruimte voor Microsoft® Windows-installaties.
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

AEM Forms add-on package is een toepassing die op AEM wordt geïmplementeerd. Het pakket bevat interactieve AEM Forms-communicatie, correspondentiebeheer en andere mogelijkheden. Voer de volgende stappen uit om het invoegpakket te installeren:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](/help/sites-administering/package-manager.md) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

   U kunt het pakket via de directe verbinding ook downloaden die in het [ wordt vermeld versies van AEM Forms ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases.html?lang=nl-NL) artikel.

1. Nadat het pakket is geïnstalleerd, wordt u gevraagd om het AEM-exemplaar opnieuw te starten. **begin niet onmiddellijk de server opnieuw.** alvorens de Server van AEM Forms tegen te houden, wacht tot ServiceEvent REGISTERED en ServiceEvent niet GEREGISTREERDE berichten ophouden die in het [ AEM-Installatie-Folder ] /crx-quickstart/logs/error.log- dossier verschijnen en het logboek stabiel is.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. Herhaal stap 1-7 voor alle instanties Auteur en Publiceren.

## Configuratie na installatie {#post-installation-configurations}

AEM Forms heeft een paar verplichte en optionele configuraties. De verplichte configuraties omvatten het vormen bibliotheken BouncyCastle en serialization agent. De optionele configuraties zijn het configureren van Dispatcher en Adobe Target.

### Verplichte configuraties na installatie {#mandatory-post-installation-configurations}

#### RSA- en BouncyCastle-bibliotheken configureren  {#configure-rsa-and-bouncycastle-libraries}

Voer de volgende stappen op alle Auteur uit en publiceer instanties om de bibliotheken op te starten afvaardigen:

1. Stop de onderliggende AEM-instantie.
1. Open het [ dossier van de de installatiemap van AEM ] \crx-quickstart\conf\sling.properties voor het uitgeven.

   Als u [ de installatiemap van AEM ] \crx-quickstart\bin\start.bat gebruikte om AEM te beginnen, dan geef sling.properties in [ AEM_root ] \ crx-quickstart uit \.

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

#### Compatibiliteitspakket installeren {#install-compatibility-package}

Interactieve communicatie is de standaard en aanbevolen aanpak om klantcommunicatie tot stand te brengen in AEM 6.5 Forms. Als u hebt bevorderd of van een vorige versie gemigreerd, en van plan bent om brieven (het Beheer van de Correspondentie) te blijven gebruiken, installeer het [ pakket van de Verenigbaarheid AEMFD ](/help/forms/using/compatibility-package.md).

Met het compatibiliteitspakket AEMFD kunt u de volgende elementen uit AEM 6.4 Forms, AEM 6.3 Forms en AEM 6.2 Forms op AEM 6.5 Forms gebruiken:

* Documentfragmenten
* Letters
* Gegevenswoordenboeken
* Afgekeurde sjablonen en pagina&#39;s voor adaptieve formulieren

#### Dispatcher configureren {#configure-dispatcher}

Dispatcher is een Adobe Experience Manager-programma voor caching en taakverdeling dat wordt gebruikt met een webserver op bedrijfsniveau. Als u [ Dispatcher ](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL) gebruikt, dan voer de volgende configuraties voor AEM Forms uit:

1. Toegang voor AEM Forms configureren:

   Open het bestand dispatcher.any voor bewerking. Navigeer naar de filtersectie en voeg het volgende filter toe aan de filtersectie:

   `/0025 { /type "allow" /glob "* /bin/xfaforms/submitaction*" } # to enable AEM Forms submission`

   Sla het bestand op en sluit het. Voor gedetailleerde informatie over filters, zie {de documentatie van 0} Dispatcher [.](https://experienceleague.adobe.com/docs/experience-manager-dispatcher/using/configuring/dispatcher-configuration.html?lang=nl-NL)

1. Configureer de referentiefilterservice:

   Meld u als beheerder aan bij Apache Felix. Standaard URL van de configuratiemanager is https://&#39;server&#39;:[ port_number ]/system/console/configMgr. In het **menu van Configuraties**, selecteer de **Apache het Verdelen van de Filter van de Verwijzing** optie. Op Toestaan het gebied van Gastheren, ga gastheernaam van Dispatcher in om het als verwijzer toe te staan en **te klikken sparen**. Het formaat van de ingang is https://&#39; [ server ]:[ haven ]&#39;.

#### Adobe Target integreren {#integrate-adobe-target}

Uw klanten zullen waarschijnlijk een interactieve mededeling verlaten als de ervaring het levert niet aansprekend is. Hoewel het voor de klanten frustrerend is, keert het ook het steunvolume en de kosten voor uw organisatie terug. Het is kritiek en uitdagend om de juiste klantenervaring te identificeren en te verstrekken die de omzettingssnelheid verhoogt. AEM-formulieren vormen de sleutel tot dit probleem.

AEM-formulieren zijn geïntegreerd met Adobe Target, een Adobe Experience Cloud-oplossing, om persoonlijke en aantrekkelijke klantervaringen te bieden via meerdere digitale kanalen. Om Adobe Target te gebruiken om een interactieve mededeling te personaliseren, [ integreer Adobe Target met AEM Forms ](../../forms/using/ab-testing-adaptive-forms.md#setupandintegratetargetinaemforms).

#### SSL-communicatie configureren voor formuliergegevensmodel  {#configure-ssl-communcation-for-form-data-model}

U kunt SSL-communicatie inschakelen voor het formuliergegevensmodel. Als u SSL-communicatie wilt inschakelen voor het formuliergegevensmodel, voegt u certificaten toe aan het Java™ Trust Store van alle exemplaren voordat u een AEM Forms-exemplaar start. U kunt de onderstaande opdracht uitvoeren om de certificaten toe te voegen:

`keytool -import -alias <alias-name> -file <pathTo .cer certificate file> -keystore <<pathToJRE>\lib\security\cacerts>`

## Volgende stappen {#next-steps}

U hebt een omgeving geconfigureerd voor het gebruik van de mogelijkheden voor interactieve communicatie en correspondentiebeheer. De volgende stappen zijn:

* [Overzicht van het correspondentiebeheer](/help/forms/using/interactive-communications-overview.md)

* [Een interactieve communicatie maken](../../forms/using/create-interactive-communication.md)

* [Een brief voor correspondentiebeheer maken](../../forms/using/create-letter.md)
