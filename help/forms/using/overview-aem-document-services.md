---
title: Overzicht van AEM Document Services
description: AEM Document Services is een set OSGi Services voor het maken, samenstellen en beveiligen van PDF-documenten.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
docset: aem65
feature: Document Services,Reader Extensions, Forms Service,PDF Generator
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 03e87c5a-c106-4b4c-9b42-8ce7a04d9c0c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1413'
ht-degree: 0%

---

# Overzicht van AEM Document Services{#overview-of-aem-document-services}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/using-communications/aem-forms-cloud-service-communications-introduction.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |


AEM Document Services is een set OSGi Services voor het maken, samenstellen en beveiligen van PDF-documenten. Document Services bevatten de volgende services:

## Uitvoerservice {#output-service}

Met de uitvoerservice kunt u documenten in verschillende indelingen maken, zoals PDF, indelingen voor laserprinters en indelingen voor labelprinters. Laserprinterindelingen zijn PostScript en Printer Control Language (PCL). In de volgende lijst ziet u de indeling van labelprinters:

* Zebra (ZPL)
* Intermec (IPL)
* Datamax (DPL)
* TecToshiba (TPCL)

Een document kan naar een netwerkprinter, een lokale printer of een bestand op het bestandssysteem worden verzonden. De service Uitvoer voegt XML-formuliergegevens samen met een formulierontwerp om een document te genereren. De service Uitvoer kan een document genereren zonder XML-formuliergegevens samen te voegen in het document. De primaire workflow is echter het samenvoegen van gegevens in het document.

>[!NOTE]
>
>Een formulierontwerp wordt meestal gemaakt met Designer. Raadpleeg de Help van Designer voor informatie over het maken van formulierontwerpen voor de Output-service.

Als u de Output-service gebruikt om XML-gegevens samen te voegen met een formulierontwerp, is het resultaat een niet-interactief PDF-document. In een niet-interactief PDF-document kunnen gebruikers geen gegevens invoeren in de bijbehorende velden. U kunt daarentegen de Forms-service gebruiken om een interactief PDF-formulier te maken waarmee gebruikers gegevens in de betreffende velden kunnen invoeren.

De volgende vier de dienstverrichtingen van de Output zijn beschikbaar voor gebruik:

* **generatePDFOuput**: Voegt een vormontwerp met gegevens samen om een document van PDF te produceren
* **generatePrintedOutput**: Voegt een vormontwerp met vormgegevens samen om een document te produceren om naar of een laser of een printer van het etiketnetwerk te verzenden

* **generatePDFOutputBatch**: Voegt veelvoudige malplaatjes met veelvoudige verslagen van gegevens in één enkele aanroeping samen om een partij van de dossiers van PDF te produceren. Er is ook een optie om één PDF te genereren door alle PDF&#39;s te combineren
* **generatePrintedOutputBatch**: Voegt veelvoudige malplaatjes met veelvoudige verslagen van gegevens in één enkele aanroeping samen om een partij drukdocumenten (PS, PCL, ZPL, DPL, IPL, TPCL) te produceren. U kunt ook één afdrukdocument genereren.

## Assembler-service {#assembler-service}

Met de Assembler-service kunt u PDF- en XDP-documenten combineren, opnieuw rangschikken en uitbreiden en informatie over PDF-documenten opvragen. Elke baan die aan de dienst van de Assembler wordt voorgelegd omvat een document van XML van de Beschrijving van het Document (DDX), brondocumenten, en externe middelen (koorden en grafiek). Het DDX-document bevat instructies voor het gebruik van de brondocumenten om een set resulterende documenten te maken.

Naast bovengenoemde mogelijkheden, de dienst van de Assembler:

* Converteert PDF-documenten naar PDF/A-standaard.
* Transformeert PDF forms, XML-formulieren (gemaakt in Designer) en PDF forms (gemaakt in Acrobat) naar PDF/A-1b, PDF/A-2b en PDFA/A-3b.
* Hiermee converteert u ondertekende of niet-ondertekende PDF-documenten (digitale handtekeningen vereist).
* Hiermee wordt de compatibiliteit van een PDF/A-bestand gevalideerd en zo nodig geconverteerd.

### Informatie over DDX {#about-ddx}

Wanneer het gebruiken van de dienst van de Assembler, gebruik een op XML-Gebaseerde taal genoemd XML van de Beschrijving van het Document (DDX) om de output te beschrijven u wilt. DDX is een verklarende prijsverhogingstaal de waarvan elementen bouwstenen van documenten vertegenwoordigen. Deze bouwstenen omvatten PDF-documenten, XDP-documenten, XDP-formulierfragmenten en andere elementen, zoals opmerkingen, bladwijzers en gestileerde tekst.

In het DDX-document kunnen resultaatdocumenten met de volgende kenmerken worden opgegeven:

* PDF-document dat is samengesteld uit meerdere PDF-documenten
* Meerdere PDF-documenten die zijn gesplitst van één PDF-document
* PDF Portfolio met een zelfstandige gebruikersinterface en meerdere PDF- en niet-PDF-documenten
* XDP-document dat is samengesteld uit meerdere XDP-documenten
* XDP-document dat XML-fragmenten bevat die dynamisch in een XDP-document worden ingevoegd
* PDF-document dat een XDP-document verpakt
* XML-bestanden die de kenmerken van een PDF-document rapporteren. Tot de gerapporteerde kenmerken behoren tekst, opmerkingen, formuliergegevens, bestandsbijlagen, bestanden die worden gebruikt in PDF-portfolio&#39;s, bladwijzers en PDF-eigenschappen. PDF-eigenschappen zijn onder andere formuliereigenschappen, pagina-rotatie en documentauteur.

U kunt DDX gebruiken om de documenten van PDF als deel van documentassemblage of demontage te verhogen. U kunt een willekeurige combinatie van de volgende effecten opgeven:

* Watermerken of achtergronden toevoegen aan of verwijderen uit geselecteerde pagina&#39;s.
* Kop- en voetteksten toevoegen aan of verwijderen uit geselecteerde pagina&#39;s.
* Hiermee verwijdert u de structuur en navigatiemogelijkheden van een PDF-pakket of PDF Portfolio. Het resultaat is één PDF-bestand.
* Paginalabels opnieuw nummeren. Paginalabels worden doorgaans gebruikt voor paginanummering.
* Metagegevens uit een ander brondocument importeren.
* Bestandsbijlagen, bladwijzers, koppelingen, opmerkingen en JavaScript toevoegen of verwijderen.
* Stel de oorspronkelijke weergavekenmerken in en optimaliseer deze voor weergave op het web.
* Machtigingen instellen voor gecodeerde PDF.
* Pagina&#39;s roteren of inhoud roteren en verschuiven op pagina&#39;s.
* Wijzig de grootte van geselecteerde pagina&#39;s.
* Gegevens samenvoegen met een op XFA gebaseerde PDF.

U kunt een eenvoudige invoerkaart gebruiken om de locaties van de bron en de resulterende documenten op te geven. U kunt ook de volgende externe gegevens-URL-typen gebruiken:

* Bestand
* FTP
* HTTP/HTTPS

## Doc Assurance Service {#doc-assurance-service}

Met de Doc Assurance Service kunt u documenten versleutelen en ontsleutelen, de functionaliteit van Adobe Reader uitbreiden met extra gebruiksrechten en digitale handtekeningen toevoegen aan uw documenten. Uw gebruikers kunnen eenvoudig communiceren met PDF forms en documenten, terwijl uw organisatie de beveiliging, archivering en compatibiliteit verbetert.

De Doc Assurance-service bevat drie services: handtekening, versleuteling en reader-extensie.

### Handtekeningenservice {#signature-service}

Met de service Handtekening kunt u werken met digitale handtekeningen en documenten op de AEM-server. De service Handtekening wordt bijvoorbeeld doorgaans in de volgende situaties gebruikt:

* De AEM-server certificeert een formulier voordat het naar een gebruiker wordt verzonden om te worden geopend met Acrobat of Adobe Reader.
* De AEM-server valideert een handtekening die aan een formulier is toegevoegd met Acrobat of Adobe Reader.
* De AEM-server ondertekent een formulier namens een openbare notaris.

De handtekeningservice krijgt toegang tot certificaten en referenties die zijn opgeslagen in de vertrouwde opslag.

### Coderingsservice {#encryption-service}

Met de coderingsservice kunt u documenten versleutelen en ontsleutelen. Wanneer een document wordt versleuteld, wordt de inhoud ervan onleesbaar. U kunt het gehele PDF-document (inclusief de inhoud, metagegevens en bijlagen), alle gegevens behalve de metagegevens of alleen de bijlagen versleutelen. Een geautoriseerde gebruiker kan het document decoderen om toegang tot de inhoud te krijgen. Als een PDF-document is versleuteld met een wachtwoord, moet de gebruiker het wachtwoord voor openen opgeven voordat het document kan worden weergegeven in Adobe Reader of Acrobat. Als een PDF-document is versleuteld met een certificaat, moet de gebruiker het PDF-document decoderen met een persoonlijke sleutel (certificaat). De persoonlijke sleutel waarmee het PDF-document wordt ontsleuteld, moet overeenkomen met de openbare sleutel waarmee het wordt versleuteld.

### Reader Extension Service {#reader-extension-service}

Met de service Reader Extensions kunt u eenvoudig interactieve PDF-documenten delen door de functionaliteit van Adobe Reader uit te breiden met extra gebruiksrechten. De service Reader Extensions werkt met Adobe Reader 7.0 of hoger. De service voegt gebruiksrechten toe aan een PDF-document. Met deze actie activeert u functies die gewoonlijk niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken.

Wanneer de juiste gebruiksrechten zijn toegevoegd aan PDF-documenten, kunnen ontvangers de volgende activiteiten uitvoeren vanuit Adobe Reader:

* PDF-documenten en -formulieren online of offline invullen, zodat ontvangers kopieën lokaal kunnen opslaan voor hun administratie en de toegevoegde informatie intact kunnen houden
* PDF-documenten opslaan op een lokale vaste schijf om het originele document en eventuele aanvullende opmerkingen, gegevens of bijlagen te behouden
* Bestanden en mediaclips aan PDF-documenten koppelen
* Onderteken, certificeer en authenticeer PDF-documenten door digitale handtekeningen toe te passen met PKI-technologieën (Public Key Infrastructure) die industriestandaard zijn
* Ingevulde of geannoteerde PDF-documenten elektronisch verzenden
* PDF-documenten en -formulieren gebruiken als een intuïtieve ontwikkeling die gericht is op interne databases en webservices
* Deel PDF-documenten met anderen, zodat revisoren opmerkingen kunnen toevoegen met intuïtieve opmaakgereedschappen. Deze gereedschappen zijn onder andere elektronische notities, stempels, hooglichten en doorhalen van tekst. Dezelfde functies zijn beschikbaar in Acrobat.
* Decodering van streepjescodes voor formulieren ondersteunen.

Deze speciale gebruikersmogelijkheden worden automatisch geactiveerd wanneer een PDF-document met toegangsrechten wordt geopend in Adobe Reader. Wanneer de gebruiker klaar is met het werken met een document waarvoor rechten zijn ingeschakeld, worden deze functies opnieuw uitgeschakeld in Adobe Reader. Ze blijven uitgeschakeld totdat de gebruiker een ander PDF-document met ingeschakelde rechten ontvangt.

Uit de doos, is de dienst DocAssurance niet beschikbaar voor gebruik. Om de dienst te vormen DocAssurance, zie [ Installerend en Vormend de Diensten van het Document ](../../forms/using/install-configure-document-services.md).

## Naar printerservice verzenden {#send-to-printer-service}

Send To Printer Service biedt API waarmee u documenten naar een opgegeven printer kunt verzenden voor afdrukken.
