---
title: Connector configureren voor EMC Documentum
description: Leer hoe u de Connector voor EMC Documentum configureert voor communicatie tussen AEM-formulieren en EMC Documentum.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/connecting_to_a_content_management_system
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: a9eae40f-531f-4354-ade0-853e84dd88d9
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1032'
ht-degree: 0%

---

# Connector configureren voor EMC Documentum {#configuring-connector-for-emc-documentum}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Connector voor EMC Documentum maakt communicatie mogelijk tussen AEM-formulieren en EMC Documentum. Voor extra achtergrondinformatie, zie &quot;Connectors voor ECM&quot;in [ Verwijzing van de Diensten ](https://www.adobe.com/go/learn_aemforms_services_63).

Bij het instellen van een connector voor EMC Documentum moeten de serververbinding en de gegevens van de opslagplaats worden geconfigureerd.

>[!NOTE]
>
>In eerdere versies konden activa worden opgeslagen in een ECM-opslagplaats. In de huidige versie worden de middelen opgeslagen in de native opslagruimte voor AEM-formulieren en zijn de services van de Repository Provider afgekeurd. De migratie van elementen van een ECM-opslagplaats naar de opslagplaats voor AEM-formulieren vindt plaats wanneer u een upgrade uitvoert naar AEM-formulieren. Zie de handleiding voor het upgraden van AEM-formulieren voor uw toepassingsserver voor meer informatie.

## De serververbinding configureren {#configuring-the-server-connection}

In dit onderwerp worden de taken voor Connector voor EMC Documentum beschreven die u kunt uitvoeren op de pagina Configuration Settings.

>[!NOTE]
>
>Als u alle instellingen tegelijk configureert, hoeft u slechts eenmaal op Opslaan te klikken.

### De server configureren {#configure-the-server}

U moet de de serverinformatie van de verbindingsmakelaar vormen. Deze informatie is nodig om verbinding te maken met de Documentum-inhoudsopslagplaatsen en de Connector voor EMC Documentum te starten.

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Voer in het gebied Documentum Configuration Information de hostnaam of het IP-adres en het poortnummer van de verbindingsmakelaar in. Het poortnummer moet een positief geheel getal zijn (bijvoorbeeld 1489).
1. Klik op Opslaan.

### Hoofdreferenties configureren {#configure-principal-credentials}

Wanneer u de hoofdreferenties configureert, hangt de door u opgegeven naam van de opslagplaats af van het feit of tijdens de aanmelding een expliciete naam van de opslagplaats is opgegeven.

Als u een onjuiste gebruikersnaam of een onjuist wachtwoord invoert, krijgt u de volgende resultaten, afhankelijk van het feit of de service momenteel wordt uitgevoerd:

* Als zowel de EMC Documentum Repository Provider service als de EMC Documentum Content Repository Connector service worden gestopt, wordt er geen fout weergegeven wanneer u de serviceconfiguratiegegevens opslaat. Nochtans, de volgende tijd u de dienst begint, zal een uitzondering worden geworpen en de dienst zal niet beginnen.
* Als de EMC Documentum Repository Provider service of de EMC Documentum Content Repository Connector service wordt gestart, probeert de service onmiddellijk de referentie-informatie te valideren wanneer u de serviceconfiguratie-informatie opslaat. In dit geval treedt een fout op en worden de configuratiegegevens niet opgeslagen.

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Typ in het gebied Documentum Principal Credentials Information de gebruikersnaam en het wachtwoord van een gebruiker met superbeheerdersrechten.
1. Als er tijdens het aanmelden geen expliciete naam voor de opslagplaats wordt opgegeven, voert u de naam in van de opslagplaats waaraan de referenties zijn gekoppeld.
1. Klik op Opslaan.

### De provider van de dataopslagservice wijzigen {#change-the-repository-service-provider}

U kunt configureren welke repository service provider moet worden gebruikt met Documentum. De de dienstvraag van de bewaarplaats wordt gedelegeerd aan de leverancier u vormt. De volgende opties zijn beschikbaar:

**Huidige Naam van de Dienstverlener van de Bewaarplaats:** De naam van de huidige leverancier van de bewaarplaats

**ECM Documentum Repository Provider:** maakt van de Documentum repository provider de provider voor de repository. Deze optie is vervangen

**leverancier van de bewaarplaats:** maakt de inheemse leverancier van de bewaarplaats de leverancier voor de bewaarplaats

>[!NOTE]
>
>Als u een andere opslagplaats voor services wilt selecteren dan de vermelde, configureert u RepositoryService in Programma&#39;s en Services > Servicebeheer. <!-- Fix broken link (See Managing Services) -->.

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Selecteer in het gebied Providergegevens voor opslagplaats de alternatieve aanbieder van opslagplaats.
1. Klik op Opslaan.

## Opslaggegevens configureren {#configuring-repository-credentials}

De Documentum referentie-informatie wordt gebruikt in de context van het AEM-formuliersysteem. Referenties van opslagplaats zijn specifiek voor bepaalde gegevensbanken in Documentum. U kunt referenties opgeven voor een willekeurig aantal opslagplaatsen, maar u kunt per opslagplaats slechts één set gegevens opgeven.

### Creditering gegevensopslagruimte toevoegen {#add-a-repository-credential}

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Repository Credentials Settings.
1. Klik toevoegen. De pagina Documentum System Credentials Information wordt weergegeven.
1. Voer een naam in voor de gegevensopslagruimte.
1. Voer een gebruikersnaam en wachtwoord in.
1. Klik op Opslaan.

Als de Content Repository Connector voor EMC Documentum Service en/of de Repository Service voor EMC Documentum wordt uitgevoerd, wordt de referentie-informatie geverifieerd op basis van de opgegeven repository voordat deze in de database wordt opgeslagen. Als de referenties ongeldig zijn of bestaan, wordt een foutbericht weergegeven.

### Credentials van opslagplaats verwijderen {#remove-a-repository-credential}

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Schakel het selectievakje naast de gegevensopslagruimte in en klik op Verwijderen. De referenties voor de geselecteerde opslagplaats worden uit de database verwijderd.

### Wijzig de gebruikersnaam en het wachtwoord voor de gegevensopslagruimte {#change-the-user-name-and-password-for-a-repository-credential}

1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Klik op de naam van de repository waarvoor u referenties wilt bewerken.
1. Wijzig de gebruikersnaam of het wachtwoord van de opslagplaats, of beide. (De naam van de gegevensopslagruimte is alleen-lezen.)
1. Klik op Opslaan.

Als de Content Repository Connector voor EMC Documentum Service en/of de Repository Service voor EMC Documentum wordt uitgevoerd, wordt de referentie-informatie geverifieerd op basis van de opgegeven repository voordat deze in de database wordt opgeslagen. Als de referenties ongeldig zijn of bestaan, wordt een foutbericht weergegeven.

## Verzoek om delen van Workspace-taakwachtrijen inschakelen {#enable-the-request-for-sharing-of-workspace-task-queues}

Er zijn enkele handmatige stappen vereist om ervoor te zorgen dat de functie Aanvragen voor delen van taakwachtrij in Workspace correct functioneert met Connector voor EMC Documentum.

1. Nadat AEM-formulieren zijn geïmplementeerd en Workbench is geïnstalleerd, meldt u zich aan bij Workbench en opent u de weergave Bronnen. U bepaalt waar het bestand QueueSharing.swf zich in deze weergave bevindt.
1. Sleep het bestand QueueSharing.swf van de Bronweergave naar het bureaublad van Windows of een equivalente locatie, afhankelijk van uw besturingssysteem.
1. Klik in de beheerconsole op Services > Connector voor EMC Documentum > Configuration Settings.
1. Wijzig de geconfigureerde opslagprovider onder Informatie over opslagprovider in EMC Documentum Repository Provider.
1. Start Workbench en kopieer het bestand QueueSharing.swf van de locatie waar u het oorspronkelijk hebt gekopieerd (bijvoorbeeld het Windows-bureaublad of een andere locatie) naar een bestaande map in de EMC Documentum-opslagplaats.
1. Open in de weergave Workbench-processen het proces Wachtrij delen.
1. Open in de weergave Variabelen de eigenschappen van de variabele &quot;theForm&quot; en wijzig de URI zodat deze overeenkomt met het pad waar u het bestand QueueSharing.swf in stap 5 hebt geplaatst.
1. Sla het proces op.
1. Migreer het proces naar de productieomgeving volgens het beleid van uw organisatie.
