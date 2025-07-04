---
title: Strategie voor back-up en herstel in een geclusterde omgeving
description: Als in de implementatie van uw AEM-formulieren extra aangepaste gegevens worden opgeslagen in een andere database, moet u een strategie implementeren om back-ups van deze gegevens te maken, zodat deze consistent blijven met de AEM-formuliergegevens.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 0fe9b02a-96b4-462f-a940-a2d6084ed0a4
source-git-commit: 1b7e0c532ab46346059de01cee4a1adecf3a0a13
workflow-type: tm+mt
source-wordcount: '1391'
ht-degree: 0%

---

# Strategie voor back-up en herstel in een geclusterde omgeving {#strategy-for-backup-and-restore-in-a-clustered-environment}

>[!NOTE]
>
>Als in de implementatie van uw AEM-formulieren extra aangepaste gegevens worden opgeslagen in een andere database, moet u een strategie implementeren om back-ups van deze gegevens te maken, zodat deze consistent blijven met de AEM-formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

U moet een back-up maken van de volgende onderdelen van het AEM-formuliersysteem om te herstellen van een fout:

* Database gebruikt door AEM-formulieren
* GDS met langlevende gegevens en andere permanente documenten
* AEM-database (crx-repository)

>[!NOTE]
>
>U moet een back-up maken van alle andere gegevens die door de AEM-formulierinstelling worden gebruikt, zoals lettertypen van klanten, verbindingsgegevens enzovoort.

## Een back-up maken van een geclusterde omgeving {#back-up-a-clustered-environment}

In dit onderwerp worden de volgende strategieën besproken om een back-up te maken van een geclusterde AEM-omgeving:

* Offline back-up met downtime
* Offlineback-up zonder downtime (back-up van een tweede knooppunt dat is afgesloten)
* Onlineback-up zonder downtime maar vertraging in reactie
* Een back-up maken van het Bootstrap-eigenschappenbestand

### Offline back-up met downtime {#offline-backup-with-downtime}

1. Sluit de volledige cluster en de verwante diensten. (zie [ Beginnend en het tegenhouden van de diensten ](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [ Dossiers aan file en terugkrijgen ](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om een back-up te maken van de AEM-opslagplaats offline:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat de id van het clusterknooppunt bevat.
   1. Maak een back-up van alle bestanden van een secundair clusterknooppunt, inclusief submappen.
   1. Maak een back-up van de opslagplaats/systeem-id van elk clusterknooppunt afzonderlijk.

   Voor gedetailleerde stappen, zie [ Steun en herstel ](/help/sites-administering/backup-and-restore.md).

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Offline back-up zonder downtime {#offline-backup-with-no-downtime}

1. Ga de het rollen reservewijze in. (zie [ het ingaan van de reservewijzen ](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Laat de modus voor rolback-ups na herstel staan.

1. Sluit om het even welke secundaire knopen van de cluster betreffende AEM. (zie [ Beginnend en het tegenhouden van de diensten ](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [ Dossiers aan file en terugkrijgen ](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om een back-up te maken van de AEM-opslagplaats offline:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat de id van het clusterknooppunt bevat.
   1. Maak een back-up van alle bestanden van een secundair clusterknooppunt, inclusief submappen.
   1. Maak een back-up van repository/system.id van elk clusterknooppunt afzonderlijk.

   Voor gedetailleerde stappen, zie [ Steun en herstel ](/help/sites-administering/backup-and-restore.md).

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Onlineback-up zonder downtime maar vertraging in reactie {#online-backup-with-no-downtime-but-delay-in-response}

1. Ga de het rollen reservewijze in. (zie [ het ingaan van de reservewijzen ](/help/forms/using/admin-help/backing-aem-forms-data.md#entering-the-backup-modes))

   Laat de modus voor rolback-ups na herstel staan.

1. Sluit om het even welke secundaire knopen van de cluster betreffende AEM. (zie [ Beginnend en het tegenhouden van de diensten ](/help/forms/using/admin-help/starting-stopping-services.md#starting-and-stopping-services))
1. Voor om het even welke knoop, file het gegevensbestand, GDS, en Connectors. (zie [ Dossiers aan file en terugkrijgen ](/help/forms/using/admin-help/files-back-recover.md#files-to-back-up-and-recover))
1. Voer de volgende stappen uit om een back-up te maken van de AEM-opslagplaats online:

   1. Maak voor elk clusterknooppunt een back-up van het bestand dat het bestand cluster_node.id bevat.
   1. Maak een back-up van repository/system.id van elk clusterknooppunt afzonderlijk.
   1. Neem op elk secundair knooppunt een online back-up van de opslagplaats voor gedetailleerde stappen. Zie Online back-up.

1. Maak een back-up van andere gegevens, zoals klantertypen.
1. Start de cluster opnieuw.

### Een back-up maken van het Bootstrap-eigenschappenbestand {#back-up-the-bootstrap-properties-file}

Wanneer wij een cluster van AEM creëren, wordt een bezitsdossier gecreeerd in de toepassingsserver voor alle secundaire knopen. U wordt aangeraden een back-up te maken van het Bootstrap-eigenschappenbestand. U kunt het bestand op de volgende locatie op uw toepassingsserver vinden:

* JBoss®: in de BIN-directory
* WebLogic: in de domeinmap
* WebSphere®: in de profielmap

Maak een back-up van het bestand voor het scenario voor noodherstel van het secundaire AEM-knooppunt en vervang het bestand op de opgegeven locatie op de toepassingsserver, indien hersteld.

## Herstel in een geclusterde omgeving {#recovery-in-a-clustered-environment}

Als er een fout optreedt in de gehele cluster of in één knooppunt, kunt u dit herstellen met behulp van de back-up.

Voor één enkele knoopterugwinning, sluit de enige knoop en stel de enige procedure van de knoopterugwinning in werking.

Voer de volgende stappen uit als de volledige cluster mislukt als gevolg van fouten zoals het vastlopen van de database. Herstellen is afhankelijk van de gebruikte methode voor back-up.

### Eén knooppunt herstellen {#restoring-a-single-node}

1. Stop het corrupte knooppunt.

   >[!NOTE]
   >
   >Als het beschadigde knooppunt een primair AEM-knooppunt is, sluit u het gehele clusterknooppunt af.

1. Maak het fysieke systeem opnieuw op basis van een systeemafbeelding.
1. Pas patches of updates toe op AEM-formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie werd geregistreerd tijdens de reserveprocedure. AEM-formulieren moeten op hetzelfde patchniveau worden hersteld als toen een back-up van het systeem werd gemaakt.
1. (*Facultatief*) als alle andere knopen fijn werken, is het mogelijk dat de bewaarplaats van AEM ook wordt bedorven. In dit geval ziet u een bericht dat de repository niet synchroniseert in het bestand error.log van de AEM-opslagplaats.

   Voer de volgende stappen uit om de opslagplaats te herstellen.

   >[!NOTE]
   >
   >Als er online een gecomprimeerde back-up van de crx-dataopslag is gemaakt, decomprimeert u deze op een willekeurige locatie en volgt u het proces voor offline herstel.

   1. Verwijder de directory&#39;s voor gegevensopslagruimte, gedeelde mappen, versies en werkruimten in de directory clusterNode van het knooppunt.
   1. Herstel de back-up van het clusterknooppunt (inclusief submappen) naar het knooppunt.
   1. Verwijder het bestand clusterNode/revision.log op het knooppunt.
   1. Verwijder de .lock op het knooppunt, indien aanwezig.
   1. Verwijder de map repository/system.id op het knooppunt, indien aanwezig.
   1. &amp;Bestandsnaam verwijderen;ast;&ast;/listener.properties op het knooppunt, indien aanwezig.
   1. Herstel repository/cluster_node.id voor afzonderlijke clusterknooppunten.

>[!NOTE]
>
>Overweeg de volgende punten:

* Als het mislukte knooppunt een primair AEM-knooppunt was, kopieert u alle inhoud van de secundaire opslagmap (crx-repository\crx.0000, waarbij 0000 cijfers kunnen zijn) naar de crx-repository\ dataopslagmap en verwijdert u de secundaire repository-map.
* Voordat u een clusterknooppunt opnieuw start, moet u ervoor zorgen dat u de gegevensopslagruimte /clustered.txt van het primaire knooppunt verwijdert.
* Zorg ervoor dat het primaire knooppunt eerst wordt gestart en dat andere knooppunten worden gestart nadat het is opgestart.

### De gehele cluster herstellen {#restoring-the-entire-cluster}

1. Stop alle clusterknooppunten.
1. Herstel het fysieke systeem van een systeembeeld.
1. Pas patches of updates toe op AEM FormsAEM-formulieren die zijn toegepast sinds de afbeelding is gemaakt. Deze informatie werd geregistreerd in stap 1 van de reserveprocedure. AEM-formulieren moeten op hetzelfde patchniveau worden hersteld als toen een back-up van het systeem werd gemaakt.
1. Herstel de database, GDS en Connectors.
1. Ga als volgt te werk om de AEM-opslagplaats offline te herstellen:

   >[!NOTE]
   >
   >Als er online een gecomprimeerde back-up van de crx-dataopslag is gemaakt, decomprimeert u deze op een willekeurige locatie en volgt u het proces voor offline herstel.

   1. Verwijder op alle clusterknooppunten de directory&#39;s repository, shared, version en workspaces in de clusterNode directory.
   1. Verwijder alle bestanden en mappen in de gedeelde map.
   1. Herstel de back-up van het clusterknooppunt (inclusief submappen) naar één clusterknooppunten.
   1. Kopieer alle bestanden van het herstelde clusterknooppunt naar alle andere clusterknooppunten. Zodra gedaan, bevat elke clusterknoop de zelfde gegevens.
   1. Verwijder het bestand clusterNode/revision.log op alle clusterknooppunten.
   1. Verwijder de .lock op alle clusterknooppunten, indien aanwezig.
   1. Verwijder repository/system.id alle clusterknooppunten, indien aanwezig.
   1. De bestanden &amp;amp verwijderen;ast;&ast;/listener.properties op alle clusterknooppunten, indien aanwezig.
   1. Herstel repository/cluster_node.id voor afzonderlijke clusterknooppunten.

>[!NOTE]
>
>Overweeg de volgende punten:

* Als het mislukte knooppunt een primair AEM-knooppunt was, kopieert u alle inhoud van de secundaire opslagmap (het ziet eruit als crx-repository\crx.0000, waarbij 0000 cijfers kunnen zijn) naar de opslagplaats crx-repository\.
* Voordat u een clusterknooppunt opnieuw start, moet u ervoor zorgen dat u de gegevensopslagruimte /clustered.txt van het primaire knooppunt verwijdert.
* Zorg ervoor dat het primaire knooppunt eerst wordt gestart en dat andere knooppunten worden gestart nadat het is opgestart.

## Knooppunt voor het maken van back-ups en het herstellen van Correspondentenbeheeroplossingen {#back-up-and-restore-correspondence-management-solution-publish-node}

De uitgeversknoop heeft geen primair-secundaire verhouding in een gegroepeerde milieu. U kunt steun van om het even welke knoop van de Uitgever nemen door [ Steun te volgen en te herstellen ](/help/sites-administering/backup-and-restore.md).

### Eén uitgeversknooppunt herstellen {#recover-a-single-publisher-node}

1. Sluit de knoop die moet worden teruggekregen en doe geen publicatieactiviteit tot de knoop opnieuw omhoog is.
1. Herstel de Publish knoop gebruikend [ Herstellend de Steun ](/help/sites-administering/backup-and-restore.md).

### Een cluster herstellen {#recover-a-cluster}

1. Sluit de cluster af.
1. Herstel de Publish knoop gebruikend [ Herstellend de Steun ](/help/sites-administering/backup-and-restore.md).
1. Start het primaire knooppunt gevolgd door het secundaire knooppunt van de auteurcluster.
