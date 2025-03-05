---
title: Uw upgrade plannen
description: Dit artikel helpt duidelijke doelstellingen, fasen, en te leveren punten te vestigen wanneer het plannen van de verbetering van AEM.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: upgrading
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: d4f89be13039e53564cd3a3148a4b845bcc183a7
workflow-type: tm+mt
source-wordcount: '1188'
ht-degree: 0%

---

# Uw upgrade plannen {#planning-your-upgrade}

## Overzicht AEM Upgrade {#aem-upgrade-overview}

AEM wordt vaak gebruikt in implementaties met hoge impact die miljoenen gebruikers kunnen bedienen. Gewoonlijk zijn er aangepaste toepassingen die op de instanties worden geïmplementeerd en die de complexiteit vergroten. Om het even welke inspanning om zulk een plaatsing te bevorderen moet methodisch worden behandeld.

Deze gids helpt met het vestigen van duidelijke doelstellingen, fasen, en te leveren punten wanneer het plannen van uw verbetering. Het concentreert zich op algemene verbeteringsuitvoering en richtlijnen. Hoewel het een overzicht van de daadwerkelijke verbeteringsstappen verstrekt, verwijst het naar beschikbare technische middelen waar geschikt. Het moet worden gebruikt met de in het document vermelde beschikbare technische middelen.

Het AEM Upgradeproces vereist zorgvuldig afgehandelde planning, analyse, en uitvoeringsfasen met de belangrijkste te leveren items die voor elke fase worden bepaald.

>[!NOTE]
>
>De upgrade naar AEM 6.5 LTS wordt ondersteund door de laatste 6 servicepacks

Het is belangrijk dat u een ondersteund besturingssysteem, Java™-runtime, httpd en Dispatcher-versie gebruikt. Voor meer informatie, verwijs de [ technische vereisten voor AEM 6.5 LTS ](/help/sites-deploying/technical-requirements.md). Het upgraden van deze onderdelen moet in uw upgradeplan worden opgenomen en moet plaatsvinden voordat u AEM upgradet.

<!-- Alexandru: drafting for now

## Upgrade Scope and Requirements {#upgrade-scope-requirements}

Below you will find a list of areas that are impacted in a typical AEM Upgrade project:

<table>
 <tbody>
  <tr>
   <td><strong>Component</strong></td>
   <td><strong>Impact</strong></td>
   <td><strong>Description</strong></td>
  </tr>
  <tr>
   <td>Operating System</td>
   <td>Uncertain, but subtle effects</td>
   <td>At the time of the AEM upgrade, it may be time to upgrade the operating system as well and this might have some impact.</td>
  </tr>
  <tr>
   <td>Java&trade; Runtime</td>
   <td>Moderate Impact</td>
   <td>AEM 6.3 requires JRE 1.7.x (64 bit) or later. JRE 1.8 is the only version currently supported by Oracle.</td>
  </tr>
  <tr>
   <td>Hardware</td>
   <td>Moderate Impact</td>
   <td>Online Revision Cleanup requires free<br /> disk space equal to 25% of the repository's size and 15% free heap space<br /> to complete successfully. You may need to upgrade your hardware to<br /> ensure sufficient resources for Online Revision Cleanup to fully<br /> run. Also, if upgrading from a version prior to AEM 6, there<br /> may be additional storage requirements.</td>
  </tr>
  <tr>
   <td>Content Repository (CRX or Oak)</td>
   <td>High Impact</td>
   <td>Starting from version 6.1, AEM does not support CRX2, so a migration to<br /> Oak (CRX3) is required if upgrading from an older version. AEM 6.3 has<br /> implemented a new Segment Node Store that also requires a migration. The<br /> crx2oak tool is used for this purpose.</td>
  </tr>
  <tr>
   <td>AEM Components/Content</td>
   <td>Moderate Impact</td>
   <td><code>/libs</code> and <code>/apps</code> are easily handled through the upgrade, but <code>/etc</code> usually requires some manual reapplication of customizations.</td>
  </tr>
  <tr>
   <td>AEM Services</td>
   <td>Low Impact</td>
   <td>Most AEM core services are tested for upgrade. This is an area of low impact.</td>
  </tr>
  <tr>
   <td>Custom Application Services</td>
   <td>Low to High Impact</td>
   <td>Depending on the application and customization, there may be<br /> dependencies on JVM, operating system versions, and some indexing related<br /> changes, as indexes are not generated automatically in Oak.</td>
  </tr>
  <tr>
   <td>Custom Application Content</td>
   <td>Low to High Impact</td>
   <td>Content that will not be handled through the upgrade can be backed up<br /> before the upgrade takes place and then moved back into the repository.<br /> Most content can be handled through the migration tool.</td>
  </tr>
 </tbody>
</table>

It is important to ensure that you are running a supported operating system, Java&trade; runtime, httpd, and Dispatcher version. For more information, see the [AEM 6.5 Technical Requirements page](/help/sites-deploying/technical-requirements.md). Upgrading these components must be accounted for in your project plan and should take place before upgrading AEM. -->

## Upgradefasen {#upgrade-phases}

Er wordt veel gedaan aan het plannen en uitvoeren van een AEM-upgrade. Om de verschillende inspanningen die dit proces met zich meebrengt te verduidelijken, heeft Adobe de plannings- en uitvoeringsoefeningen in afzonderlijke fasen opgesplitst. In de onderstaande secties resulteert elke fase in een leverbaar dat vaak wordt gebruikt door een toekomstige fase van de upgrade.

<!-- Alexandru:drafting for now

### Planning for Author Training {#planning-for-author-training}

With any new release, there are potential changes to the UI and user workflows that may be introduced. Also, new releases introduce new features that may be beneficial for the business to use. Adobe recommends reviewing the functional changes that have been introduced and organizing a plan to train your users on using them effectively.

![unu_cropped](assets/unu_cropped.png)

New features in AEM 6.5 can be found in [the AEM section of adobe.com](/help/release-notes/release-notes.md). Make sure to note any changes to UIs or product features that are commonly used in your organization. As you look through the new features, also take note of any that can be of value to your organization. After looking through what has changed in AEM 6.5, develop a training plan for your authors. This could involve using freely available resources like the help feature videos or formal training offered through [Adobe Digital Learning Services](https://learning.adobe.com/). -->

### Een testplan maken {#creating-a-test-plan}

De implementatie van AEM door elke klant is uniek en is aangepast aan de zakelijke vereisten. Daarom is het belangrijk om alle aanpassingen te bepalen die aan het systeem zijn aangebracht zodat zij in een testplan kunnen worden omvat.

De exacte productieomgeving moet worden gedupliceerd en na de upgrade moeten er tests op worden uitgevoerd om te controleren of alle toepassingen en aangepaste code nog steeds naar wens worden uitgevoerd. Regenereer al uw aanpassingen en de prestaties, belasting en beveiligingstests. Wanneer het organiseren van uw testplan, zorg ervoor om alle aanpassingen te behandelen die aan het systeem naast uit de doos UIs en werkschema&#39;s zijn aangebracht die in uw dagelijkse verrichtingen worden gebruikt. Deze kunnen de diensten en de diensten van douaneOSGI, integraties aan de Adobe Experience Cloud, integraties met derden door de schakelaars van AEM, de integratie van de douanederde, douanecomponenten en malplaatjes, de overlays van de douanegebruikersinterface in AEM, en douanewerkschema&#39;s omvatten. Bovendien, zouden de douanevragen nog moeten worden getest om ervoor te zorgen dat hun indexen effectief na verbetering blijven werken.

### Complexiteit van upgrade beoordelen {#assessing-upgrade-complexity}

Vanwege de grote verscheidenheid aan aanpassingen die Adobe-klanten op hun AEM-omgevingen toepassen, is het belangrijk dat u enige tijd van tevoren doorbrengt om het totale inspanningsniveau te bepalen dat in uw upgrade moet worden verwacht. [ de Analysator van AEM voor AEM 6.5 LTS ](/help/sites-deploying/aem-analyzer.md) kan u helpen in het beoordelen van de ingewikkeldheid van de verbetering.

De [ Analyseer van AEM voor AEM 6.5 LTS ](/help/sites-deploying/pattern-detector.md) zou u een vrij nauwkeurige schatting van moeten geven wat tijdens een verbetering voor de meeste gevallen te verwachten. Nochtans, voor complexere aanpassingen en plaatsingen waar u onverenigbare veranderingen hebt, kunt u een ontwikkelingsinstantie aan AEM 6.5 LTS volgens de instructies in [ bevorderen Uitvoerend een Verbetering op zijn plaats ](/help/sites-deploying/in-place-upgrade.md). Na voltooiing, voer wat hoge rooktests op dit milieu uit. Het doel van deze exercitie is niet om de inventarisatie van de testgevallen volledig te voltooien en een formele inventarisatie van de gebreken te maken, maar om ons een ruwe schatting te geven van de hoeveelheid werk die nodig is om de code voor AEM 6.5 LTS-compatibiliteit te upgraden. Wanneer gecombineerd met de [ Analysator van AEM ](/help/sites-deploying/aem-analyzer.md) en de architecturale veranderingen die in de vorige sectie werden bepaald, kan een ruwe schatting aan het team van het projectbeheer voor de planning van de verbetering worden verstrekt.

### De upgrade- en terugdraaiversie van Runbook samenstellen {#building-the-upgrade-and-rollback-runbook}

Hoewel Adobe het proces voor de bevordering van een instantie van AEM heeft gedocumenteerd, vereisen de de netwerklay-out van elke klant, plaatsingsarchitectuur, en aanpassingen het verfijnen en het maken van op deze benadering. Daarom raadt Adobe u aan alle beschikbare documentatie te controleren en deze te gebruiken om een upgrade-specifieke runbook te informeren die de specifieke upgrade- en terugdraaiprocedures beschrijft die u in uw omgeving zult volgen.

<!--Alexandru:drafting for now

![runbook-diagram](assets/runbook-diagram.png) -->

Adobe heeft verbetering en terugschroeven van prijzenprocedures in [ Procedure van de Verbetering ](/help/sites-deploying/upgrade-procedure.md) en geleidelijke instructies voor het toepassen van de verbetering in het Uitvoeren van een [ Verbetering Op plaats ](/help/sites-deploying/in-place-upgrade.md) verstrekt. Deze instructies zouden met uw systeemarchitectuur, aanpassingen, en downtime tolerantie moeten worden herzien en overwogen om de aangewezen schakelaar-over en terugschroeven van prijzenprocedures te bepalen die u tijdens de verbetering zult uitvoeren. Wijzigingen in architectuur of serverformaten moeten worden opgenomen wanneer u uw aangepaste runbook gaat maken.

### Een upgradeplan ontwikkelen {#developing-an-upgrade-plan}

De output van de vorige oefeningen kan worden gebruikt om een verbeteringsplan te bouwen dat de verwachte chronologie voor uw test of ontwikkelingsinspanningen, en daadwerkelijke verbeteringsuitvoering behandelt.

<!--Alexandru: drafting for now

![develop-project-plan](assets/develop-project-plan.png) -->

Een alomvattend projectplan moet het volgende omvatten:

* Afronding van ontwikkelings- en testplannen
* Ontwikkeling en QA-omgevingen verbeteren
* De aangepaste codebasis voor AEM 6.5 LTS bijwerken
* Een test en reparatiecyclus van kwaliteitscontrole
* De testomgeving upgraden
* Integratie, prestaties en het testen van de belasting
* Milieu-certificering
* Live gaan

### Ontwikkeling en kwaliteitscontrole {#performing-development-and-qa}

Adobe heeft procedures voor [ Bevorderend Code en Aanpassingen ](/help/sites-deploying/upgrading-code-and-customizations.md) verstrekt om met AEM 6.5 LTS compatibel te zijn. Wanneer dit iteratieve proces wordt uitgevoerd, moeten wijzigingen worden aangebracht in de runbook.

<!--Alexandru: drafting for now

![patru_cropped](assets/patru_cropped.png) -->

Het ontwikkelings- en testproces is doorgaans een herhalend proces. Aangezien de kwesties worden ontdekt die aanpassingen aan het verbeteringsproces vereisen, zorg ervoor om hen aan uw runtime van de douaneverbetering toe te voegen. Na verscheidene herhalingen van het testen en het bevestigen, zou de codebasis volledig moeten worden bevestigd en voor plaatsing aan het opvoeren milieu klaar zijn.

### Eindtest {#final-testing}

Adobe raadt een laatste testronde aan nadat de codebase is gecertificeerd door het QA-team van uw organisatie. Deze testronde omvat het valideren van uw runbook in een testomgeving, gevolgd door gebruikersacceptatie, prestaties en beveiligingstests.

<!--Alexandru: drafting for now

![cinci_cropped](assets/cinci_cropped.png) -->

Deze stap is essentieel aangezien het de enige tijd is dat u de stappen in runbook tegen een productie-als milieu kunt bevestigen. Zodra het milieu is bevorderd, is het belangrijk om eind - gebruikers wat tijd toe te staan om zich aan te melden en door de activiteiten te gaan zij doen wanneer het gebruiken van het systeem in hun dagelijkse activiteiten. Het vinden en corrigeren van problemen in deze gebieden vóór go-live kan kostbare productieonderbrekingen helpen voorkomen.

### De upgrade uitvoeren {#performing-the-upgrade}

Zodra de definitieve aftekening van alle belanghebbenden is ontvangen, is het tijd om de gedefinieerde runbook-procedures uit te voeren. Adobe heeft stappen voor verbetering en het terugschroeven van prijzen in [ de Procedure van de Verbetering ](/help/sites-deploying/upgrade-procedure.md) en installatiestappen in het Uitvoeren van een [ Verbetering op zijn plaats ](/help/sites-deploying/in-place-upgrade.md) als verwijzingspunt verstrekt.

![ prepress ](assets/perform-upgrade.png)

Adobe heeft enkele stappen opgegeven in de instructies voor het valideren van de omgeving. Deze omvatten basiscontroles zoals het aftasten van de verbeteringslogboeken en het verifiëren dat alle bundels OSGi behoorlijk zijn begonnen, maar Adobe adviseert ook het bevestigen met uw eigen testgevallen die op uw bedrijfsprocessen worden gebaseerd. Adobe raadt ook aan het schema van AEM Online Revision Cleanup en verwante routines te controleren om ervoor te zorgen dat deze routines tijdens een rustige tijd voor uw bedrijf worden uitgevoerd. Deze routines zijn essentieel voor de prestaties op lange termijn van AEM.
