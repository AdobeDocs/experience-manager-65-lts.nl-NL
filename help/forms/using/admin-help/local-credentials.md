---
title: Lokale referenties beheren
description: Leer hoe u lokale gegevens beheert met Betrouwbaarheidsbeheer. AEM-formulieren ondersteunen RSA- en DSA-referenties in de standaard PKCS12-vorm.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_certificates_and_credentials
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: d297ab09-2b92-442a-8b19-ffee86e24bb9
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '533'
ht-degree: 0%

---

# Lokale referenties beheren {#managing-local-credentials}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Lokale referenties zijn persoonlijke sleutelgegevens die worden gehost in Betrouwbaarheidsbeheer. A *lokale referentie* identificeert waar de referentie van DES van een gebruiker wordt opgeslagen. Met Betrouwbaarheidsbeheer kunt u uw lokale gegevens importeren en beheren door bijvoorbeeld bestaande PFX-bestanden te gebruiken, zodat u lokale gegevens kunt importeren, bewerken en verwijderen.

AEM-formulieren ondersteunen RSA- en DSA-referenties van maximaal 4096 bits in de standaard PKCS12-indeling (.pfx- en .p12-bestanden).

U kunt elk gewenst aantal referenties importeren en exporteren. Als u een verlopen referentie wilt vervangen met dezelfde alias, verwijdert u de referentie en importeert u de nieuwe referentie met dezelfde alias.

Voor informatie en instructies met betrekking tot de Uitbreidingen van gelijkstroom van de Reader van de Acrobaat, zie [ het Vormen geloofsbrieven voor gebruik met de Uitbreidingen van gelijkstroom van de Lezer van de Acrobaat ](/help/forms/using/admin-help/configuring-credentials-acrobat-reader-dc.md#configuring-credentials-for-use-with-acrobat-reader-dc-extensions).

## Een referentie importeren {#import-a-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op Import. Selecteer onder Type vertrouwde winkel een van de volgende opties:

   * **Document Signing Credential:** De referentie van A die wordt gebruikt om een digitale handtekening op een document uit te geven.
   * **de Referentie van de Uitbreidingen van de Uitbreidingen van de Acrobaat van de Acrobaat van de Lezer van gelijkstroom:** een digitaal certificaat specifiek voor de Uitbreidingen van de Lezer van de Acrobaat die de gebruiksrechten van Adobe toelaat worden geactiveerd in de geproduceerde documenten van PDF.
   * **Gebrek:** wijst erop dat dit de standaardreferentie aan gebruik met de Uitbreidingen van gelijkstroom van de Lezer van de Acrobaat is.

   Voor informatie over het verkrijgen van referentie, zie [ Voorbereidend om de vormen van AEM ](https://helpx.adobe.com/pdf/aem-forms/6-3/prepare-install-single-server.pdf) te installeren.

1. Typ in het vak Alias een id voor de referentie. Deze id wordt gebruikt als de weergavenaam voor de referentie in Acrobat Reader DC Extensions en de service Handtekening. Deze alias wordt ook gebruikt om via programmacode toegang te krijgen tot de referentie met de AEM-formulieren SDK.

   >[!NOTE]
   >
   >De naam van de alias wordt automatisch omgezet in hoofdletters voor weergavedoeleinden. De naam van de alias is niet hoofdlettergevoelig wanneer u er in een proces naar verwijst.

1. Klik op Bladeren om de referentie te zoeken, typ het wachtwoord van de referentie en klik op OK.

   Als het foutbericht &quot;Kan referentie niet importeren vanwege een onjuiste bestandsindeling of een onjuist wachtwoord&quot; wordt weergegeven, controleert u of het wachtwoord geldig is.

## Een referentie exporteren {#export-a-credential}

Referenties worden geëxporteerd als P12-bestanden in de PKCS#12-indeling.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt exporteren en klik vervolgens op Exporteren.
1. Typ het wachtwoord in het vak Wachtwoord. Dit wachtwoord is nieuw en wordt gebruikt om de geëxporteerde referentie te coderen.
1. Klik op Exporteren, volg de aanwijzingen zodat u de referentie kunt exporteren en klik op OK.

## Alias of vertrouwenswinkeltype van een referentie bewerken {#edit-a-credential-s-alias-or-trust-store-type}

Nadat een referentie is geïmporteerd, kunt u de naam van de alias en het type vertrouwde opslagruimte bewerken.

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Klik op de naam van de alias van de referentie die u wilt bewerken.
1. Klik op Referentie bijwerken.
1. Bewerk de naam van de alias en het type vertrouwde winkel naar wens en klik op OK.

## Een referentie verwijderen {#delete-a-credential}

1. Klik in de beheerconsole op Instellingen > Betrouwbaarheidsopslagbeheer > Lokale referenties.
1. Schakel de selectievakjes in waarin u de gegevens wilt verwijderen.
1. Klik op Verwijderen en vervolgens op OK.
