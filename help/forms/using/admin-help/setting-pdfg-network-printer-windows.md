---
title: Een PDFG-netwerkprinter instellen (alleen Windows)
description: Leer hoe u een PDFG-netwerkprinter instelt (alleen Windows)
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 6e9c42d9-fb1d-432b-95b9-6e21706b2a3e
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '616'
ht-degree: 0%

---

# Een PDFG-netwerkprinter instellen (alleen Windows) {#setting-up-a-pdfg-network-printer-windows-only}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met PDFG Network Printer kunnen gebruikers een PDF-document genereren vanuit elke toepassing die afdrukken ondersteunt. Nadat een gebruiker de Printer van het Netwerk PDFG installeert, verschijnt een nieuwe printer genoemd *de generator van PDF* in de sectie van Printers van het Controlebord van Vensters. Als er al een printer met dezelfde naam bestaat, wordt de gebruiker gevraagd een andere naam op te geven.

Als u vanuit een toepassing op deze printer afdrukt, wordt het document (in PostScript-indeling) naar PDF Generator verzonden, waardoor het PostScript-bestand naar PDF wordt geconverteerd. Afhankelijk van hoe u PDF Generator hebt geconfigureerd, verzendt het het PDF-document naar de gebruiker als een bijlage bij een e-mailbericht, stuurt het PDF-document door naar een opgegeven AEM-formulierservice of -proces, of voert beide handelingen uit.

U moet de volgende stappen uitvoeren om een PDFG-netwerkprinter in te stellen:

1. E-mailinstellingen configureren. (Zie [ e-mailmontages voor de Printer van het Netwerk PDFG ](setting-pdfg-network-printer-windows.md#configure-email-settings-for-pdfg-network-printer) vormen.)
1. In de beheersconsole, vorm de montages van de Printer van het Netwerk PDFG. (Zie [ de montages van de Printer van het Netwerk PDFG ](setting-pdfg-network-printer-windows.md#configure-the-pdfg-network-printer-settings) vormen.)
1. Zorg ervoor dat uw gebruikers zijn geconfigureerd met een geldig e-mailadres in de AEM-formulierdatabase en wijs de PDFGUserPermission toe aan elke gebruiker. <!-- Fix broken link See Setting up and organizing users -->
1. Zorg ervoor dat 32-bits JRE6 is geïnstalleerd op de computers van uw gebruikers.
1. Installeer de printer op de computers van uw gebruikers. (Zie [ de Printer van het Netwerk PDFG op de computer van een gebruiker installeren ](setting-pdfg-network-printer-windows.md#install-pdfg-network-printer-on-a-user-s-computer).)

## E-mailinstellingen configureren voor PDFG Network Printer {#configure-email-settings-for-pdfg-network-printer}

1. Klik in de beheerconsole op Services > Toepassingen en services > Servicebeheer.
1. Voor de pagina van het Beheer van de Dienst, klik provider.email_sendmail_service, specificeer de montages SMTP, en klik sparen.

## De instellingen voor de PDFG-netwerkprinter configureren {#configure-the-pdfg-network-printer-settings}

1. Klik in de beheerconsole op Services > PDF Generator > PDFG Network Printer
1. Selecteer in de lijsten Adobe PDF-instellingen en Beveiligingsinstellingen de opties die u wilt toepassen op de gegenereerde PDF. Voor details op deze montages, zie [ Vormend de montages van Adobe PDF ](/help/forms/using/admin-help/configuring-pdf-settings.md#configuring-adobe-pdf-settings) en [ Vormend veiligheidsmontages ](/help/forms/using/admin-help/configuring-security-settings.md#configuring-security-settings).
1. Als u de geconverteerde PDF&#39;s weer naar gebruikers wilt verzenden, selecteert u de optie Het geconverteerde PDF-bestand e-mailen naar gebruiker en geeft u de volgende gegevens op:

   * Het e-mailadres dat moet worden gebruikt om PDF&#39;s naar de gebruikers te verzenden
   * Het onderwerp van het e-mailbericht
   * De kop-, tekst- en voettekst van het e-mailbericht. In het e-mailbericht wordt &lt;receiverName> vervangen door de volledige naam van de gebruiker die het document heeft afgedrukt.

1. Als u de geconverteerde PDF&#39;s naar een AEM-formulierservice of -proces wilt verzenden, selecteert u de optie De geconverteerde PDF doorsturen naar de opgegeven AEM-formulierservice of -procesoptie en geeft u de volgende informatie op:

   * De naam van de service die moet worden aangeroepen
   * De naam van de verrichting van de dienst aan te halen
   * De naam van de invoerparameter, zoals opgegeven in het bestand component.xml van de service of het proces. Het PDF-document wordt gebruikt als een waarde voor die invoerparameter.

1. Klik op Opslaan.

Als u de oorspronkelijke standaard-e-mailtekst wilt herstellen, klikt u op E-mailinhoud herstellen.

## PDFG-netwerkprinter installeren op de computer van een gebruiker {#install-pdfg-network-printer-on-a-user-s-computer}

Gebruikers met de rol PDFG-beheerder of PDFG-gebruiker kunnen een PDFG-netwerkprinter installeren. Er moet een 32-bits JDK op de computer zijn geïnstalleerd.

1. (PDFG-beheerders) Klik in de beheerconsole op Services > PDF Generator > PDFG Network Printer.

   (PDFG-gebruikers) Ga naar `http(s)://[host]:'port'/pdfgui` en klik op de koppeling onder Installatie van PDFG-netwerkprinter.

1. Klik op de koppeling onder Installatie van PDFG-netwerkprinter. Geef bij de aanwijzing voor gegevens van gebruikersaccounts de gebruikersnaam en het wachtwoord op die u in stap 1 hebt gebruikt voor aanmelding. Er verschijnt een bericht met de mededeling dat de printer is geïnstalleerd.

   ***nota **: Als het wachtwoord van de gebruiker verandert, dan moeten de gebruikers de Printer van het Netwerk PDFG op hun computers opnieuw installeren. U kunt niet het wachtwoord van beleidsconsole bijwerken.*

1. Klik op OK.
