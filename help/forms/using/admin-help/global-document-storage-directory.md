---
title: Algemene map voor documentopslag
description: De GDS-map (global document storage) is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 9a93b8f9-33cb-4aec-81e0-a1146bba955a
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '684'
ht-degree: 0%

---

# Algemene map voor documentopslag{#global-document-storage-directory}

De *globale documentopslag (GDS)* folder is een folder die wordt gebruikt om langlevende dossiers op te slaan die binnen een proces worden gebruikt. Deze bestanden bevatten PDF&#39;s, beleidsregels en formuliersjablonen. Bestanden met een lange levensduur vormen een essentieel onderdeel van de algemene status van veel implementaties van AEM-formulieren. Als sommige of alle documenten met een lange levensduur verloren gaan of beschadigd raken, kan de Forms-server instabiel worden. Invoerdocumenten voor asynchrone taakaanroepen worden ook opgeslagen in de GDS-map en moeten beschikbaar zijn voor het verwerken van aanvragen. Het is belangrijk dat u rekening houdt met de betrouwbaarheid van het bestandssysteem dat de GDS-map host. Gebruik een redundante array met onafhankelijke schijven (RAID) of andere technologie die geschikt is voor uw servicekwaliteit en serviceniveau.

Bestanden met een lange levensduur kunnen vertrouwelijke gebruikersgegevens bevatten. Voor deze informatie zijn mogelijk speciale referenties vereist wanneer deze wordt geopend met de API&#39;s of gebruikersinterfaces voor AEM-formulieren. Het is belangrijk dat de GDS-map correct wordt beveiligd via het besturingssysteem. Alleen de beheerdersaccount die wordt gebruikt om de toepassingsserver uit te voeren, moet lees-/schrijftoegang hebben tot de GDS-map.

Naast het selecteren van een veilige, hoogst beschikbare folder voor GDS, kunt u ook verkiezen om documentopslag in het gegevensbestand toe te laten. Zelfs als u de AEM-formulierdatabase gebruikt voor het opslaan van documenten, vereist AEM-formulieren nog steeds de GDS-map. (Zie [ Reservekopties wanneer het gegevensbestand voor documentopslag ](/help/forms/using/admin-help/files-back-recover.md#backup-options-when-database-is-used-for-document-storage) wordt gebruikt.)

AEM-toepassingsgegevens voor formulieren bevinden zich in de GDS-map en de AEM-formulierdatabase. In de volgende tabel worden de gegevens en de locaties beschreven.

<table>
 <thead>
  <tr>
   <th><p>AEM-formuliergegevens</p></th>
   <th><p>Database</p></th>
   <th><p>GDS</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>Toepassingsgegevens (gebruikers, rollen, processen, beleid, eindpunten, gebeurtenissen, enzovoort.)</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Ingestelde servicecontainers</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Documentbeheer </p></td>
   <td><p>Nee</p></td>
   <td><p>Ja</p></td>
  </tr>
  <tr>
   <td><p>Forms-opslagplaats</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Systeemconfiguratie</p></td>
   <td><p>Ja</p></td>
   <td><p>Nee</p></td>
  </tr>
  <tr>
   <td><p>Gecontroleerde mappen</p></td>
   <td><p>Nee</p></td>
   <td><p>Ja</p></td>
  </tr>
 </tbody>
</table>

## De GDS-map configureren {#configuring-the-gds-directory}

De locatie van de GDS-directory kan handmatig worden geconfigureerd tijdens het installatieproces van AEM-formulieren. Als de locatie-instelling tijdens de installatie leeg blijft, wordt standaard als volgt een map onder de installatie van de toepassingsserver gebruikt:

* (JBoss) `[appserver root]/server/[type]/svcnative/DocumentStorage`
* (WebLogic) `[appserverdomain]/'server'/adobe/DocumentServer/DocumentStorage`
* (WebSphere) `[appserver root]/installedApps/adobe/'server'/DocumentStorage`

## De standaard GDS-locatie wijzigen {#change-the-default-gds-location}

U kunt de GDS-locatie in de beheerconsole wijzigen nadat de installatie van AEM-formulieren is voltooid. Verplaats de gegevens handmatig om het proces te voltooien.

>[!NOTE]
>
>* Migreer de gegevens op de volgende manier of er treedt gegevensverlies op.
>* Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Meld u aan bij de beheerconsole en klik op Instellingen > Core System Settings > Configurations.
1. Voer in het vak Algemene opslagmap voor documenten het volledige pad naar de nieuwe GDS-map in en klik op OK.
1. Sluit de toepassingsserver onmiddellijk af.
1. Verplaats alle bestanden van de oude GDS-map naar de nieuwe locatie, waarbij de interne mapstructuur behouden blijft.
1. Start de toepassingsserver opnieuw.

## Informatie over implementatiebestanden {#about-deployment-files}

AEM-formulieren bestaan uit twee typen implementatiebestanden, de servicecontainers en de Java 2 Platform, Enterprise Edition (J2EE) EAR-bestanden. De EAR-bestanden bestaan uit standaard J2EE-toepassingsbundels die de kernfunctionaliteit van AEM-formulieren bevatten. De server-specifieke EAR-bestanden van de toepassing zijn als volgt:

* adobe-core-*[appserver]*.ear
* adobe-kern - *[appserver]* - *[OS]* .ear

Bij het implementeren van AEM-formulieren moeten de geassembleerde EAB-bestanden en ondersteunende bestanden worden geïmplementeerd op de toepassingsserver waar u uw AEM-formulieroplossing wilt uitvoeren. Als u vormde en veelvoudige modules assembleerde, worden de plaatsbare modules verpakt binnen de plaatsbare EAR dossiers. Om deze dossiers op te stellen, kopieer hen aan het *[appserver huis]* \server\all\deploy folder.

Modules en AEM-formulierarchiefbestanden worden verpakt in JAR-bestanden. Omdat het geen J2EE-typebestanden zijn, worden deze niet geïmplementeerd op de toepassingsserver. In plaats daarvan worden ze naar de GDS-map gekopieerd en wordt een verwijzing naar de locatie ervan opgeslagen in de AEM-formulierdatabase. Daarom moet de GDS-map worden gedeeld tussen alle knooppunten van de cluster. Alle knopen moeten toegang tot de centrale opslagfolder voor DSCs hebben.

>[!NOTE]
>
>Alvorens u de de dienstcontainers opstelt, zorg ervoor dat u creeerde en de folder GDS vormde. (Zie [ Vormend de GDS folder ](global-document-storage-directory.md#configuring-the-gds-directory))
