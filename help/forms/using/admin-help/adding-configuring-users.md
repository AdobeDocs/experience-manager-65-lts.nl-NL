---
title: Gebruikers toevoegen en configureren
description: Met de instellingen voor gebruikersbeheer in de beheerconsole kunt u gebruikers maken of verwijderen en andere gebruikersinstellingen configureren.
solution: Experience Manager, Experience Manager Forms
role: User, Developer
feature: Adaptive Forms
hide: true
hidefromtoc: true
exl-id: b3f8e1d6-3e6e-4b2c-8528-3346bbda3396
source-git-commit: 9dcdf84b70a3b0ea6fb332cd2cf8ccf1d4476489
workflow-type: tm+mt
source-wordcount: '1625'
ht-degree: 0%

---

# Gebruikers toevoegen en configureren {#adding-and-configuring-users}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Gebruiker- en groepsgegevens worden bijgehouden in een opslagsysteem van derden, zoals een LDAP-directory. Gebruikersbeheer schrijft niet naar het opslagsysteem van derden. In plaats daarvan synchroniseert Gebruikersbeheer de gebruikers- en groepsgegevens met een eigen database

## Een gebruiker maken {#create-a-user}

Wanneer u gebruikers creeert, kunt u hen aan groepen toevoegen en rollen toewijzen aan hen.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]** en klik op **[!UICONTROL New User]** .
.
1. Geef onder **[!UICONTROL General Settings]** de vereiste informatie op en klik op **[!UICONTROL Next]** . Voor details over de montages, zie [ montages van de Gebruiker ](adding-configuring-users.md#user-settings).
1. (Optioneel) Als u de gebruiker aan een groep wilt toevoegen, klikt u op **[!UICONTROL Find Groups]** en voert u de volgende taken uit:

   * Typ in het vak **[!UICONTROL Find]** de naam van de groep geheel of gedeeltelijk.
   * Selecteer het domein waarnaar u wilt zoeken, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]** .
   * (Optioneel) Als u groepdetails wilt weergeven, selecteert u de groepsnaam en klikt u op **[!UICONTROL OK]** om terug te keren naar de pagina met zoekresultaten.
   * Schakel het selectievakje voor de groep in en klik op **[!UICONTROL OK]** .
   * Klik op **[!UICONTROL Next]**.

1. (Optioneel) Als u rollen wilt toewijzen aan de gebruiker, klikt u op **[!UICONTROL Find Roles]**, schakelt u het selectievakje in voor de rollen die u wilt toewijzen en klikt u vervolgens op **[!UICONTROL OK]** .
1. Klik op **[!UICONTROL Finish]**.

## Gebruikersinstellingen {#user-settings}

Geef de volgende instellingen op wanneer u een gebruiker maakt of bewerkt.

**Canonical Naam:** (Verplicht) Unieke herkenningsteken voor de gebruiker. Elke gebruiker en groep in een domein moet een unieke canonieke naam hebben. Schakel het selectievakje Door systeem gegenereerd in als u wilt dat gebruikersbeheer een unieke waarde toewijst of schakel het selectievakje uit en geef een aangepaste waarde op voor Canonical Name.

Gebruik geen onderstrepingstekens (_) in canonieke namen, bijvoorbeeld `sample_user` . Wanneer u naar gebruikers zoekt op basis van hun canonieke naam, worden de gebruikers met onderstrepingstekens niet geretourneerd.

**Voornaam:** (Verplicht) Voornaam van de Gebruiker

**Familienaam:** (Verplicht) de familienaam van de Gebruiker

**Gemeenschappelijke Naam:** Volledige naam of vertoningsnaam voor de gebruiker. Bijvoorbeeld, als Voornaam = Gloria en Achternaam = Rios, dan Gemeenschappelijke Naam = Gloria Rios.

**E-mail:** e-mailadres van de gebruiker

**Telefoon:** het telefoonaantal van de gebruiker

**Beschrijving:** Facultatieve beschrijving. U kunt dit veld gebruiken in overeenstemming met de behoeften van uw organisatie.

**Adres:** het postadres van de gebruiker

**Organisatie:** Organisatie waartot de gebruiker behoort

**E-mailaliassen:** e-mailaliassen van de Gebruiker. Scheid de e-mailaliassen met komma&#39;s.

**Domein:** Domein waartot de gebruiker behoort

**Landinstelling:** de scène van ISO van de Gebruiker

**Bedrijfs Sleutel van de Kalender:** laat u toe om een bedrijfskalender aan een gebruiker in kaart te brengen, die op de waarde voor dit het plaatsen wordt gebaseerd. Zakelijke kalenders definiëren zakelijke en niet-zakelijke dagen. AEM-formulieren kunnen zakelijke kalenders gebruiken voor het berekenen van toekomstige datums en tijden voor gebeurtenissen zoals herinneringen, deadlines en escalaties. De manier waarop u zakelijke kalendersleutels toewijst aan gebruikers hangt af van of u een onderneming, lokaal, of hybride domein gebruikt. (Zie [ Toevoegend domeinen ](/help/forms/using/admin-help/adding-domains.md#adding-domains).)

Als u een lokaal of hybride domein gebruikt, wordt de informatie over gebruikers opgeslagen slechts in het gegevensbestand van het Beheer van de Gebruiker. Stel voor deze gebruikers de Business Calendar Key in op een tekenreeks. Wijs vervolgens de agenda-key van het bedrijf (de tekenreeks) toe aan een agenda voor het bedrijf in de formulierwerkstroom.

Als u een ondernemingsdomein gebruikt, verblijft de informatie over gebruikers in een derdesopslagsysteem, zoals een folder LDAP. Gebruikersbeheer synchroniseert gebruikersgegevens uit de map met de gebruikersbeheerdatabase. Met deze functie kunt u een zakelijke kalendersleutel toewijzen aan een veld in de LDAP-directory. Neem bijvoorbeeld een scenario waarin elk gebruikersrecord in uw map een landveld bevat en u bedrijfsplannen wilt toewijzen op basis van het land waar de gebruiker zich bevindt. In dit geval geeft u de naam van het landveld op als de waarde voor de instelling Key Business Calendar. Vervolgens kunt u de agenda-sleutels voor het bedrijf (de waarden die zijn gedefinieerd voor het landveld in de LDAP-lijst) toewijzen aan de agenda&#39;s voor het bedrijf in de formulierworkflow.

Voor extra informatie over bedrijfscalendars, met inbegrip van hoe te om bedrijfskalendersleutels aan bedrijfscalendars in kaart te brengen, zie [ Vormend Bedrijfscalendars ](/help/forms/using/admin-help/configuring-business-calendars.md#configuring-business-calendars).

Beperk de naam tot minder dan 53 tekens. Een kortere naam helpt problemen verhinderen tonend de bedrijfskalendersleutel in de pagina&#39;s van het Beheer van het Proces in beleidsconsole.

**identiteitskaart van de Gebruiker:** (Verplicht) Gebruiker - identiteitskaart die de gebruiker aan login gebruikt. De gebruikersnaam is niet hoofdlettergevoelig en moet in het hele domein uniek zijn.

In ondernemingsdomeinen, gebruik een niet-DN attribuut als gebruiker - identiteitskaart omdat DN van een gebruiker kan veranderen als zij naar een ander deel van de organisatie bewegen. Deze instelling is afhankelijk van de directoryserver. De waarde is `objectGUID` voor Active Directory 2003, `nsuniqueID` voor Sun™ One en `guid` voor eDirectory.

Controleer of de gebruikersnaam uniek is. Gebruik geen code die is toegewezen aan een verwijderde gebruiker.

AEM-formulieren kunnen geen onderscheid maken tussen gebruikersaccounts die identieke gebruikers-id&#39;s en wachtwoorden hebben, maar tot verschillende domeinen behoren. Maak geen accounts met dezelfde gebruikersnaam op meerdere domeinen om dit probleem te voorkomen.

Wanneer u SQL Server als uw database gebruikt, kunt u geen gebruikers-id maken die meer dan 255 tekens bevat.

Wanneer u MySQL gebruikt, kan de gebruikersnaam uitgebreide tekens bevatten. Wanneer echter een vergelijking wordt gemaakt tussen twee tekenreeksen, zoals abcde en âbcdè, worden deze als hetzelfde beschouwd. Als bij het synchroniseren bijvoorbeeld een nieuwe gebruiker aan de database is toegevoegd, wordt een vergelijking gemaakt om te controleren of een gebruiker met dezelfde gebruikersnaam in de database aanwezig is. Als gebruiker *abcde* in het gegevensbestand bestaat wanneer de nieuwe gebruiker *âbcdè* wordt toegevoegd, kan de vergelijking niet tussen de twee namen onderscheiden. Aangenomen wordt dat de gebruiker in de database bestaat en dat de nieuwe gebruiker wordt genegeerd en niet toegevoegd.

Maak geen gebruikersnamen die met een hekje (#) beginnen. Het uitvoeren van taakonderzoeken keert geen resultaten voor die gebruikersnamen terug. (Zie [ Werkend met taken ](/help/forms/using/admin-help/tasks.md#working-with-tasks).)

**Wachtwoord en Bevestig Wachtwoord:** Wachtwoord dat de gebruiker aan login gebruikt. Het moet minimaal acht tekens hebben. Een wachtwoord is niet vereist voor een gebruiker die deel uitmaakt van een hybride domein.

## Details van een gebruiker weergeven {#view-details-about-a-user}

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Gebruikers en groepen.
1. Geef informatie op om de zoekopdracht te beperken en selecteer Gebruikers in de lijst In en klik vervolgens op Zoeken. De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Klik op de naam van de gebruiker om details weer te geven over. Op de pagina Gebruiker bewerken worden de volgende gegevens over de gebruiker weergegeven:

   * Algemene identificatiegegevens, zoals naam, e-mail, adres, domein en organisatie
   * Rollen die aan de gebruiker zijn toegewezen
   * Groepen de gebruiker een lid van is

## Het wachtwoord voor een lokale gebruiker wijzigen {#change-the-password-for-a-local-user}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]** .
1. Geef informatie op om de zoekopdracht naar een bepaalde gebruiker te beperken en klik op **[!UICONTROL Find]** . De resultaten van de zoekopdracht worden onder aan de pagina weergegeven. U kunt de lijst sorteren door op een van de kolomkoppen te klikken.
1. Klik op de naam van de gebruiker en klik vervolgens op **[!UICONTROL Change Password]** .
1. Typ en bevestig het nieuwe wachtwoord en klik op **[!UICONTROL OK]** . Het wachtwoord moet minimaal acht tekens lang zijn.

## De eigenschappen van een gebruiker bewerken {#edit-a-user-s-properties}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]** .
1. Voer de volgende taken uit om te zoeken naar de gebruiker die u wilt bewerken:

   * Typ in het vak **[!UICONTROL Find]** de zoekcriteria.
   * Selecteer **[!UICONTROL Using]** , **[!UICONTROL Name]** of **[!UICONTROL Email]** in de lijst **[!UICONTROL User ID]** .
   * Selecteer **[!UICONTROL In list]** in de **[!UICONTROL Users]** .
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]** .

1. Klik op de gebruiker die u wilt bewerken.
1. Voor een gebruiker die deel uitmaakt van een lokaal of hybride domein, bewerkt u op het tabblad **[!UICONTROL Detail]** de **[!UICONTROL General Settings]** en **[!UICONTROL Login Settings]** en klikt u op **[!UICONTROL Save]** . Voor details over de montages, zie [ montages van de Gebruiker ](adding-configuring-users.md#user-settings). U kunt de algemene instellingen en aanmeldingsinstellingen niet bewerken voor een gebruiker die tot een ondernemingsdomein behoort.
1. Als u de groepsinstellingen voor de gebruiker wilt bewerken, klikt u op het tabblad **[!UICONTROL Group Membership]** en voert u de volgende taken uit:

   * Klik op **[!UICONTROL Find Group]** en voer de zoekinformatie in.
   * Als u de gebruiker aan een nieuwe groep wilt toevoegen, schakelt u het selectievakje voor de groep in, klikt u op **[!UICONTROL OK]** en klikt u vervolgens op **[!UICONTROL Save]** .

   >[!NOTE]
   >
   >Lokale gebruikers kunnen niet worden toegevoegd aan directorygroepen. Directorygebruikers kunnen echter wel aan lokale groepen worden toegevoegd.

   * Als u de gebruiker uit een groep wilt verwijderen, schakelt u het selectievakje voor de groep in, klikt u op **[!UICONTROL Delete]** en klikt u vervolgens op **[!UICONTROL Save]** .

1. Als u de rollen van de gebruiker wilt bewerken, klikt u op het tabblad **[!UICONTROL Role Assignments]** en voert u de volgende taken uit:

   * Klik op **[!UICONTROL Find Roles]** om een lijst met rollen weer te geven.
   * Als u een rol wilt toevoegen, schakelt u het selectievakje voor de rol in, klikt u op **[!UICONTROL OK]** en klikt u vervolgens op **[!UICONTROL Save]** .
   * Als u een rol wilt verwijderen, schakelt u het selectievakje voor de rol in, klikt u op **[!UICONTROL Unassign]** en klikt u vervolgens op **[!UICONTROL Save]** .

## Een gebruiker verwijderen {#delete-a-user}

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Users and Groups]** .
1. Voer de volgende taken uit om te zoeken naar de gebruiker die u wilt verwijderen:

   * Typ in het vak **[!UICONTROL Find]** de zoekcriteria.
   * Selecteer **[!UICONTROL Using]** , **[!UICONTROL Name]** of **[!UICONTROL Email]** in de lijst **[!UICONTROL User ID]** .
   * Selecteer **[!UICONTROL In list]** in de **[!UICONTROL Users]** .
   * Selecteer het domein, selecteer het aantal items dat u wilt weergeven en klik op **[!UICONTROL Find]** .

1. Selecteer het selectievakje voor de gebruiker, klik op **[!UICONTROL Delete]** en klik op **[!UICONTROL OK]** .

>[!NOTE]
>
>Met AEM Forms on JEE kunnen gebruikers van de invoegtoepassing voor AEM-formulieren die op een OSGi worden uitgevoerd, ook worden herkend als AEM-gebruikers. Dit is vereist voor scenario&#39;s waarbij invoegtoepassing voor één aanmelding tussen AEM Forms op JEE en AEM vereist is (bijvoorbeeld HTML-werkruimte). Met bovengenoemde verwijderingsbewerking wordt een gebruiker alleen uit AEM Forms op JEE verwijderd. De gebruiker wordt niet geschrapt van AEM Forms toe:voegen-op lopend op milieu OSGi. Maar om het even welke login poging die na het schrappen van de gebruiker wordt gemaakt (een login poging aan de server van AEM Forms toe:voegen-op JEE of toe:voegen-on AEM Forms op milieu OSGi) wordt ontkend.

## Aangepaste handler voor aanmeldingsfouten maken {#create-custom-login-error-handler}

Als een gebruiker zonder de vereiste AEM-formulieren en CQ-machtigingen zich probeert aan te melden bij de volgende toepassingen die zijn ingesloten in CQ, wordt de gebruiker omgeleid naar de standaard CQ 404-pagina met de fouttrace:

* Correspondentenbeheeroplossing
* AEM-formulieren Workspace

  ***nota &#x200B;**: De Werkruimte van Flex wordt afgekeurd voor de vormenversie van AEM.*

* formulierbeheer
* Procesrapportage

CQ verstrekt een mechanisme om standaard 404 manager jsp met voeten te treden.

Voor details op hoe te om de fout behandelende pagina aan te passen, zie [ Aanpassende Pagina&#39;s die door de Handler van de Fout ](/help/sites-developing/customizing-errorhandler-pages.md) in de documentatie van Adobe Experience Manager worden getoond.
