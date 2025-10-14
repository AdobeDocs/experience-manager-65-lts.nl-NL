---
title: Problemen met replicatie oplossen
description: Dit artikel biedt informatie over hoe u problemen met replicatie kunt oplossen.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: configuring
docset: aem65
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 015def31-c7de-42b3-8218-1284afcb6921
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# Problemen met replicatie oplossen{#troubleshooting-replication}

Deze pagina biedt informatie over hoe u problemen met replicatie kunt oplossen.

## Probleem {#problem}

De replicatie (niet-omgekeerde replicatie) ontbreekt om één of andere reden.

## Resolutie {#resolution}

Er zijn diverse redenen voor replicatie om te ontbreken. In dit artikel wordt uitgelegd welke aanpak u kunt volgen bij het analyseren van deze kwesties.

**worden de replicaties teweeggebracht bij allen wanneer het klikken van de Activate knoop? Als NIET dan het volgende doet:**

1. Ga naar /crx/de/index.jsp en meld u aan als beheerder.
1. Zie of bestaat een knoop /bin/replicate of /bin/replicate.json. Als het knooppunt bestaat, verwijdert u het en slaat u het op.

**worden de replicaties een rij gevormd in de rijen van de replicatieagent?**

Controleer dit door naar /etc/replication/agents.author.html te gaan dan de replicatieagenten klikken om te controleren.

**als één agentenrij of een paar agentenrijen vast zijn:**

1. Toon de rij **geblokkeerde** status? Zo ja, wordt de publicatie-instantie dan niet uitgevoerd of reageert deze niet? Controleer de publicatie-instantie om te zien wat er mis is. Dat wil zeggen, controleer de logboeken en controleer of er een fout OutOfMemory of een ander probleem is. Als het slechts langzaam is, dan neem draaddumps en analyseer hen.
1. Toon de rijstatus **Rij actief - # hangend** is? De replicatietaak kan in feite vastzitten in een socket die wacht tot de publicatie-instantie of Dispatcher reageert. Dit kan betekenen dat de publicatie-instantie of Dispatcher onder hoge druk staat of vastzit in een vergrendeling. Neem draaddumps van auteur en publiceer in dit geval.

   * Open de draaddumps van auteur in een analysator van de draadstortplaats, controleer of het toont dat de sling van de replicatieagent de gebeurtenisbaan in socketRead vastzit.
   * Open de draaddumps van publiceren in een analysator van de draadstortplaats, analyseer wat zou kunnen veroorzaken publiceer instantie om niet te antwoorden. U zou een draad met POST /bin/receive in zijn naam moeten zien die de draad is die de replicatie van auteur ontvangt.

**als alle agentenrijen geplakt** zijn

1. Het is mogelijk dat een bepaald stuk inhoud niet onder /var/replication/data kan in series worden vervaardigd toe te schrijven aan de corruptie van de bewaarplaats of een andere kwestie. Ga naar logs/error.log voor een verwante fout. Ga als volgt te werk om het slechte replicatiepunt te wissen:

   1. Ga naar https://&lt;host>:&lt;port>/crx/de en meld u aan als beheerder.
   1. Klik op &quot;Gereedschappen&quot; in het bovenste menu.
   1. Klik op de vergrootglasknop.
   1. Selecteer XPath als Type.
   1. Voer in het vak &quot;Query&quot; deze query/jcr:root/var/eventing/jobs//element(&lbrace;0,slingevent:Job)-volgorde in door @slingevent:created&#42;
   1. Klik op Zoeken.
   1. In de resultaten zijn de belangrijkste items de meest recente slingerende taken. Klik op elke kopie en zoek de geplakte replicaties die overeenkomen met wat boven in de wachtrij wordt weergegeven.

**creeer een replication.log**

Soms is het nuttig om al replicatieregistreren te plaatsen om in een afzonderlijk logboekdossier op het niveau van DEBUG worden toegevoegd. Dit doet u als volgt:

1. Ga naar https://host:port/system/console/configMgr en meld u aan als beheerder.
1. Zoek de configuratie van het Logboekprogramma voor Apache Sling Logging en maak een instantie door op de knop **+** rechts van de fabrieksconfiguratie te klikken. Hiermee maakt u een nieuw logbestand.
1. Stel de configuratie als volgt in:

   * Logniveau: FOUTOPSPORING
   * Logbestand: logs/replication.log
   * Logger: com.day.cq.replication

1. Als u vermoedt dat het probleem te maken heeft met sling-gebeurtenissen/taken, kunt u dit Java™-pakket ook toevoegen onder categorieën:org.apache.sling.event

## Wachtrij replicatieagent pauzeren  {#pausing-replication-agent-queue}

Soms kan het geschikt zijn om de replicatiewachtrij te pauzeren om de belasting van het auteursysteem te verminderen zonder deze uit te schakelen. Momenteel, is dit slechts mogelijk door een hack van tijdelijk het vormen van een ongeldige haven. Vanaf 5.4 kon u pauzeknoop in replicatieagentenrij zien het één of andere beperking heeft

1. De status blijft niet bestaan. Dit betekent dat als u een server opnieuw opstart of een replicatiebundel wordt gerecycled, de status weer actief wordt.
1. De pauze is nutteloos voor een kortere periode (OOB 1 uur na geen activiteiten met replicatie door andere draden) en niet voor een langere tijd. Omdat er een functie in sling is die nutteloze draden vermijdt. Controleer in feite of een thread voor een taakwachtrij langer ongebruikt is, als dit het geval is, of er opschoningscycli zijn. Vanwege het opschoonprogramma stopt het de thread en daardoor gaat de gepauzeerde instelling verloren. Omdat de banen worden voortgeduurd, stelt het een nieuwe draad in werking om de rij te verwerken die geen details van de gepauzeerde configuratie heeft. Vanwege deze wachtrij wordt deze status ingeschakeld.

## Paginamachtigingen worden niet herhaald bij activering van de gebruiker {#page-permissions-are-not-replicated-on-user-activation}

Paginamachtigingen worden niet gerepliceerd omdat ze worden opgeslagen onder de knooppunten waartoe toegang wordt verleend, niet met de gebruiker.

In het algemeen moeten paginamachtigingen niet door de auteur worden gerepliceerd om te publiceren en zijn ze niet standaard. Dit komt omdat toegangsrechten in deze twee omgevingen verschillend zouden moeten zijn. Daarom adviseert Adobe dat u ACLs bij publiceert, gescheiden van auteur vormt.

## Replicatiereeks geblokkeerd tijdens replicatie van naamruimtegegevens van Auteur voor publiceren {#replication-queue-blocked-when-replicating-namespace-information-from-author-to-publish}

Soms wordt de replicatiewachtrij geblokkeerd wanneer wordt geprobeerd naamruimtegegevens te repliceren van de auteurinstantie naar de publicatieinstantie. Dit gebeurt omdat de replicatiegebruiker geen `jcr:namespaceManagement` bevoegdheid heeft. Om dit probleem te voorkomen, moet u ervoor zorgen dat:

* De replicatiegebruiker (zoals die onder [&#x200B; wordt gevormd Vervoer &#x200B;](/help/sites-deploying/replication.md#replication-agents-configuration-parameters) tab>Gebruiker) bestaat ook op de Publish instantie.
* De gebruiker heeft lees- en schrijfrechten op het pad waar de inhoud is geïnstalleerd.
* De gebruiker heeft `jcr:namespaceManagement` bevoegdheden op het niveau van de gegevensopslagruimte. U kunt deze bevoegdheid als volgt toekennen:

1. Meld u aan bij CRX/DE ( `https://localhost:4502/crx/de/index.jsp` ) als beheerder.
1. Klik het **Controle van de Toegang** tabel.
1. Selecteer **Bewaarplaats**.
1. Klik **toevoegen Ingang** (het plusteken).
1. Voer de naam van de gebruiker in.
1. Selecteer `jcr:namespaceManagement` in de lijst met bevoegdheden.
1. Klik **OK**.
