---
title: Toepassingen importeren en beheren
description: Leer hoe u toepassingen kunt importeren en beheren. Een toepassing is een container voor het opslaan van elementen die vereist zijn voor het implementeren van een AEM-formulieroplossing.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/importing_and_managing_applications_and_archives
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e0984513-f70c-4409-885b-a2eb50757a7d
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '852'
ht-degree: 0%

---

# Toepassingen importeren en beheren{#import-and-manage-applications}

In de vormen van AEM, is een *toepassing* een container voor het opslaan van activa die voor het uitvoeren van een de vormenoplossing van AEM worden vereist. Voorbeelden van elementen zijn formulierontwerpen, formulierfragmenten, afbeeldingen, processen, DDX-bestanden, formulierhulplijnen, HTML-pagina&#39;s en SWF-bestanden. Tijdens de ontwikkelingsfase van een project, kunnen de gebruikers Workbench toepassingen van de mening van Toepassingen in Workbench direct opstellen. Zodra opgesteld, verschijnen deze toepassingen in beleidsconsole, op het lusje van Toepassingen op de pagina van het Beheer van de Toepassing.

Wanneer een toepassing volledig en klaar voor plaatsing aan een productieserver is, verpakt de gebruiker Workbench de toepassing in het dossier van de a *AEM vormentoepassing* (.lca). Dan gebruikt een beheerder beleidsconsole om het toepassingsdossier in te voeren en op te stellen, gebruikend het lusje van Toepassingen op de pagina van het Beheer van de Toepassing.

U kunt het archieflusje op de pagina van het Beheer van de Toepassing ook gebruiken om LCAs in te voeren die gebruikend werkbank 8.x werden gecreeerd.

>[!NOTE]
>
>Er is een bekend probleem dat LCA-bestanden uit een toekomstige release niet altijd compatibel zijn met oudere versies. Het is mogelijk om LCA-bestanden te bekijken en importeren vanuit een toekomstige versie van AEM-formulieren (bijvoorbeeld een voorbeeldversie), maar dit wordt niet ondersteund en kan leiden tot afwijkend gedrag.

Met het tabblad Toepassingen kunt u toepassingen importeren en beheren die in Workbench zijn gemaakt. Toepassingsbeheerders kunnen ook de runtimeconfiguratie voor een toepassing exporteren. Wanneer u de runtimeconfiguratie exporteert, hoeft u instellingen in de productieomgeving handmatig opnieuw te configureren voordat u de geïmplementeerde toepassingen start. Het runtime configuratiebestand bevat:

* serviceconfiguratie-instellingen
* groepconfiguratie-instellingen
* eindpuntconfiguratie-instellingen
* beveiligingsprofielen

## Een toepassing of archief importeren {#import-an-application-or-archive}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op Import.
1. Klik op Bladeren en selecteer het .lca-bestand dat u wilt importeren en klik op Voorvertoning. Op de pagina Voorvertoning toepassing wordt informatie over de toepassing weergegeven.
1. (Optioneel) Als u een lijst met de elementen in de toepassing wilt weergeven, klikt u op Assets weergeven.
1. (Optioneel) Als u de elementen wilt implementeren in de runtime, selecteert u Assets implementeren in runtime wanneer het importeren is voltooid. Als u deze optie niet selecteert, kunt u de elementen later implementeren.
1. Klik op Import. De toepassing wordt weergegeven op het tabblad Toepassingen.
1. Meld u aan bij de CRX-opslagplaats met beheerdersreferenties.
1. Navigeren naar inhoud/dam/toepassingen

   >[!NOTE]
   >
   >De geïmporteerde toepassingen worden weergegeven in het knooppunt Toepassingen.

1. Klik op een van de geïmporteerde toepassingen.

   Op het tabblad Eigenschappen aan de rechterkant worden de eigenschappen van het geselecteerde CRX-knooppunt weergegeven.

   Het **syncState** bezit wijst op de staat van synchronisatie van gegevens tussen de Server van AEM Forms en de bewaarplaats van CRX. Zodra het importproces begint, wordt deze status ingesteld op 0 (nul). Deze status geeft aan dat de gegevens momenteel niet zijn gesynchroniseerd. Wanneer de gegevens worden gesynchroniseerd, wordt de status ingesteld op 1.

## Een toepassing implementeren {#deploy-an-application}

U kunt toepassingen implementeren die u hebt geïmporteerd of die Workbench-gebruikers hebben geïmporteerd uit Workbench.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt implementeren in en klik op Implementeren.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## Implementatie van een toepassing ongedaan maken {#undeploy-an-application}

U kunt toepassingen verwijderen uit de runtime.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt verwijderen in en klik op Distribueren ongedaan maken.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## Een toepassing van de server verwijderen {#remove-an-application-from-the-server}

Verwijder de toepassing voordat u deze van de server verwijdert.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Schakel het selectievakje naast de toepassing die u wilt verwijderen in en klik op Verwijderen.
1. Klik op OK in het bevestigingsvenster dat wordt weergegeven.

## De runtimeconfiguratie van een toepassing importeren {#import-an-application-s-runtime-configuration}

Als een toepassingsbeheerder de runtime configuratie voor een toepassing heeft uitgevoerd, kunt u het in de opgestelde toepassing invoeren. U kunt het invoeren gebruikend of de beleidsconsole of via gescripte plaatsing LCA.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op de naam van de toepassing.
1. Klik op Runtime Config importeren.
1. Klik op Bladeren en selecteer het XML-bestand dat de runtimeconfiguratie bevat.
1. Klik op Import.

## De runtimeconfiguratie van een toepassing exporteren {#export-an-application-s-runtime-configuration}

U kunt de runtime configuratieinformatie voor opgestelde toepassingen uitvoeren.

1. Klik in de beheerconsole op Services > Toepassingen en services > Toepassingsbeheer.
1. Klik op de naam van de toepassing.
1. Klik op Runtime Config exporteren en sla het configuratiebestand (XML) op dat wordt gemaakt.

## Scripts implementeren van AEM-formuliertoepassingen {#scripted-deployment-of-aem-forms-applications}

U kunt ook een gescripte implementatie gebruiken om toepassingsbestanden in te voeren, inclusief een bestand settings.xml dat de volgende instellingen opgeeft:

* serviceconfiguratie-instellingen
* groepconfiguratie-instellingen
* eindpuntconfiguratie-instellingen
* beveiligingsprofielen

De plaatsing Scripted elimineert de behoefte om montages in het productiemilieu manueel aan te passen alvorens opgezette toepassingen te beginnen.

1. Van een bevelherinnering, navigeer aan *[aem-vormen wortel]*/sdk/misc/Foundation/ArchiveManagement.
1. Controleer het bestand ReadMe.txt voor meer gedetailleerde instructies.
1. Wijzig handmatig de bestanden scriptedDeploy.bat en sample-files/sample.xml, zoals beschreven in het bestand readme.txt.
1. Voer het bestand scriptedDeploy.bat uit. Met deze actie implementeert u het archiefbestand voor AEM-formulieren met de overschrijvingsinstellingen.
