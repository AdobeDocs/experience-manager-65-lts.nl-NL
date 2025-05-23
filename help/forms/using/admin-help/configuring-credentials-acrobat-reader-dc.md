---
title: Referenties configureren voor gebruik met Acrobat Reader DC Extensions
description: Leer hoe u referenties configureert voor gebruik met Acrobat Reader DC Extensions.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 040a4db1-45e1-4501-8117-d2d41d4a73ea
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '558'
ht-degree: 0%

---

# Referenties configureren voor gebruik met Acrobat Reader DC Extensions{#configuring-credentials-for-use-with-acrobat-reader-dc-extensions}

Als u gebruiksrechten wilt toepassen op PDF-documenten, configureert u AEM-formulieren met een geldige referentie voor Acrobat Reader DC Extensions. Mogelijk is een referentie geconfigureerd tijdens de installatie van AEM-formulieren. Als u de referentiegegevens voor Acrobat Reader DC Extensions niet hebt geconfigureerd tijdens het uitvoeren van Configuration Manager, of als u een nieuwe of vervangende referentie moet importeren, kunt u dit doen met de pagina&#39;s van het Betrouwbaarheidsarchief Management.

Als u een evaluatiereferentie gebruikt, vervang het met een productieleferentie wanneer het bewegen aan uw productiemilieu. Als u een verlopen of evaluatiereferentie wilt bijwerken, verwijdert u eerst de oude Acrobat Reader DC Extensions-referentie.

Voor informatie over het verkrijgen van referentie, zie [ Voorbereidend om de vormen van AEM (Enige Server) te installeren ](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf).

De Trust Store kan meer dan één referentie voor Acrobat Reader DC Extensions bevatten. Wijs een van deze referenties aan als standaard Reader Extensions-referentie. De standaardreferentie wordt gebruikt wanneer een Workbench-gebruiker niet kan bepalen welke referentie moet worden gebruikt tijdens het maken van processen. Deze regels zijn van toepassing op standaardreferenties:

* Als u een referentiewaarde voor Acrobat Reader DC Extensions importeert en het vertrouwensarchief geen andere referenties voor Acrobat Reader DC Extensions bevat, wordt dit ingesteld als de standaardinstelling.
* Als u een referentie voor Acrobat Reader DC Extensions importeert terwijl de optie Standaard is geselecteerd, wordt het standaardtype verwijderd uit een bestaande standaardreferentie. De geïmporteerde referentie wordt de standaardinstelling.
* U kunt een standaardreferentie voor Acrobat Reader DC Extensions niet verwijderen. Om de standaardreferentie te schrappen, plaats eerst een andere referentie als gebrek. Een uitzondering op deze regel is dat als er slechts één referentie is, u het kunt schrappen alhoewel het het gebrek is.
* U kunt een standaardreferentie voor Acrobat Reader DC Extensions niet bijwerken.

>[!NOTE]
>
>U kunt geloofsbrieven ook invoeren en schrappen programmatically. (Zie [ Programmering met de vormen van AEM ](https://experienceleague.adobe.com/docs/experience-manager-release-information/aem-release-updates/previous-updates/aem-previous-versions.html?lang=nl-NL).)

## Een Acrobat Reader DC Extensions-referentie importeren {#import-a-acrobat-reader-dc-extensions-credential}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Importeren en selecteer onder Type vertrouwde opslag de optie Acrobat Reader DC Extensions Credential.
1. (Optioneel) Selecteer Standaard om aan te geven dat deze referentie de standaardreferentie is voor gebruik met Acrobat Reader DC Extensions.
1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC Extensions. Deze alias wordt ook gebruikt om via programmacode toegang te krijgen tot de referentie met de AEM-formulieren SDK.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bestand kiezen om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een Acrobat Reader DC Extensions-referentie verwijderen {#remove-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Selecteer de referentie en klik op Verwijderen.

## Referentie voor Acrobat Reader DC Extensions vervangen {#replace-a-acrobat-reader-dc-extensions-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Noteer de alias van de bestaande referentie, selecteer deze en klik op Verwijderen.
1. Importeer de nieuwe referentie met exact dezelfde aliasnaam.
