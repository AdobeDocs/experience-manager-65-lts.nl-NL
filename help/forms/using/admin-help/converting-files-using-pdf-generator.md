---
title: Bestanden converteren met PDF Generator
description: De PDF Generator-service converteert native bestandsindelingen naar PDF. PDF wordt ook geconverteerd naar andere bestandsindelingen en de grootte van PDF-documenten wordt geoptimaliseerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 1d2adc53-498f-43f5-b664-0b9dd864b9a1
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1185'
ht-degree: 0%

---

# Bestanden converteren met PDF Generator{#converting-files-using-pdf-generator}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt de PDF Generator-webpagina&#39;s gebruiken om bestanden om te zetten.

## Een PDF-bestand maken {#create-a-pdf-file}

1. Klik in de beheerconsole op Services > PDF Generator > PDF maken.
1. Klik op Bladeren om het bestand te zoeken en te selecteren.

   >[!NOTE]
   >
   >PDF Generator kan automatisch het bestandstype .doc, .xls, .ppt en .rtf-bestanden detecteren, zelfs als de bestandsnaam de bestandsextensie mist. Deze functie werkt niet met .docx-, .xlsx- en .pptx-bestanden.

1. Selecteer Aangepaste instellingen gebruiken of instellingenbestand uploaden onder Configuration Settings.

   * Als u aangepaste instellingen gebruikt, selecteert u een Adobe PDF-instelling, beveiligingsinstelling en instelling voor het bestandstype en geeft u een time-out op.

     De Adobe PDF-instellingen zijn alleen van toepassing op conversies van PS-naar-PDF, EPS-naar-PDF, PRN-naar-PDF, Image-to-PDF met OCR ingeschakeld en Native-naar-PDF. Met de time-out-instelling bepaalt u de maximale tijd die de conversie nodig heeft. De standaardwaarde is 270 seconden. Deze instellingen worden niet gebruikt tijdens conversies van Image-to-PDF en OpenOffice-naar-PDF.

   * Als u een instellingenbestand uploadt, typt u het pad en de naam in het vak of klikt u op Bladeren om het bestand te zoeken en te selecteren.

1. (Optioneel) Typ onder Metagegevensbestand van XMP het pad en de naam van het XMP-bestand of klik op Bladeren om het bestand te zoeken en te selecteren. Een XMP-bestand kan worden gebruikt om standaardmetagegevens op te nemen. (Zie [ Ongeveer XMP dossiers ](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Klik op Maken. Wanneer het bestand is gemaakt, wordt er een koppeling naar weergegeven. Als tijdens de conversie een fout optreedt, wordt een waarschuwing weergegeven. Als u een Postscript-bestand maakt, bevat de waarschuwing ook een koppeling naar het logbestand.
1. Klik op de koppeling voor het PDF-bestand. Het bestand wordt geopend in Acrobat.

### Informatie over XMP-bestanden {#about-xmp-files}

PDF-documenten die PDF Generator maakt in Acrobat 5.0 of hoger, bevatten documentmetagegevens in XML-indeling. *Meta-gegevens* omvat informatie over het document en zijn inhoud, zoals de naam van de auteur, sleutelwoorden, en auteursrechtinformatie die onderzoeksnut kunnen gebruiken.

De metagegevens van het document bevatten (maar zijn niet beperkt tot) informatie die ook wordt weergegeven op het tabblad Beschrijving van het dialoogvenster Documenteigenschappen in Acrobat. Wijzigingen die worden aangebracht op het tabblad Beschrijving, worden weerspiegeld in de metagegevens van het document. Metagegevens van documenten kunnen worden uitgebreid en gewijzigd met producten van derden.

Adobe Extensible Metadata Platform (XMP) biedt Adobe-toepassingen een algemeen XML-framework dat het maken, verwerken en uitwisselen van metagegevens in documenten in publicatieworkflows gestandaardiseerd. U kunt de XML-broncode van documentmetagegevens opslaan en importeren in XMP-indeling, zodat u gemakkelijk metagegevens kunt delen tussen verschillende documenten. Voor meer informatie over de dossiers van XMP, zie [ Extensible Metadata Platform (XMP) ](https://www.adobe.com/products/xmp/) en [ Adobe XMP Developer Center ](https://www.adobe.com/devnet/xmp.html).

U kunt XMP-bestanden maken in Acrobat.

## Een HTML-bestand of ZIP-bestand converteren naar PDF {#convert-an-html-file-or-zip-file-to-pdf}

U kunt PDF Generator gebruiken om de volgende bestandstypen om te zetten in Adobe PDF:

* HTML-bestanden die u kunt converteren door een HTML-bestand te uploaden of door de URL van een webpagina of website op te geven.
* Gearchiveerde bestanden (ZIP) die HTML-bestanden, afbeeldingsbestanden of beide kunnen bevatten.

Als het ZIP-bestand meer dan één HTML-bestand op het laagste niveau van de maphiërarchie bevat, moet het ZIP-bestand ook het bestand index.htm of index.html bevatten.

>[!NOTE]
>
>* Voor de functie HTML naar PDF zijn bepaalde lettertypen in de systeemmap met lettertypen vereist. Op Linux-, Solaris- en AIX-systemen moet de systeemmap met lettertypen het Courier-lettertype bevatten. Op Windows-systemen moet de systeemmap voor lettertypen Times New Roman bevatten.
>
>* (Alleen op UNIX gebaseerd systeem) Een van de volgende Japanse lettertypen moet beschikbaar zijn op de AEM Forms-server om een webpagina met een Japans lettertype om te zetten in een PDF-document.
>
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Gothic Pro-VI&quot;
>  * Kozuka Mincho Pro-VI
>  * &quot;Sazanami Gothic&quot;
>  * &quot;Kozuka Mincho Pr6N&quot;
>  * &quot;Sazanami Mincho&quot;
>  * &quot;Adobe Heiti Std&quot;
>  * &quot;Adobe Song Std&quot;
>
>* Als u een bestand vanaf het lokale bestandssysteem wilt uploaden, gebruikt u de optie Bestand uploaden op de pagina HTML naar PDF.

1. Klik in de beheerconsole op Services > PDF Generator > HTML naar PDF.
1. Geef het bestand op dat u wilt converteren door een van de volgende taken uit te voeren:

   * Typ in het veld Bestand uploaden het pad en de bestandsnaam van het HTML-bestand of het ZIP-bestand of klik op Bladeren om het bestand te zoeken en te selecteren.
   * Typ in het vak URL opgeven de URL van de pagina of website die u wilt converteren.

   >[!NOTE]
   >
   >Het bestand dat u converteert, moet de bestandsnaamextensie .html, .htm of .zip hebben.

1. Geef de configuratie-instellingen op:

   * Als u aangepaste instellingen wilt gebruiken, selecteert u Aangepaste instellingen gebruiken, geeft u de instellingen voor de beveiliging en het bestandstype op en geeft u een time-outwaarde op. De standaardwaarde is 270 seconden.

   >[!NOTE]
   >
   >Als u de dienst Generate PDF om Acrobat WebCapture te gebruiken vormde, beïnvloeden de Montages van het Type van Dossier die u op deze pagina selecteert geen geproduceerde PDF. Breng in plaats daarvan de gewenste wijzigingen aan in de versie van Acrobat die op de server is geïnstalleerd.

   * Als u een bestaand instellingenbestand wilt gebruiken, selecteert u Bestand met instellingen uploaden en klikt u op Bladeren om naar de bestandslocatie te gaan.

1. Als u een XMP-bestand wilt uploaden, klikt u op Bladeren en gaat u naar de bestandslocatie. Een XMP-bestand kan worden gebruikt om standaardmetagegevens op te nemen. (Zie [ Ongeveer XMP dossiers ](converting-files-using-pdf-generator.md#about-xmp-files).)
1. Klik op Maken. Wanneer het bestand is gemaakt, wordt een koppeling naar het PDF-bestand weergegeven.
1. Klik op de koppeling om het PDF-document in Acrobat weer te geven.

## Een PDF-bestand exporteren naar een andere bestandsindeling (alleen Windows) {#export-a-pdf-file-to-another-file-format-windows-only}

U kunt de dossiers van PDF naar diverse dossierformaten uitvoeren, zoals die in het Generate hoofdstuk van de Dienst van PDF van [ Verwijzing van de Diensten ](https://www.adobe.com/go/learn_aemforms_services_63) wordt beschreven.

1. Klik in de beheerconsole op Services > PDF Generator > Export PDF.
1. Klik op Bladeren om het te exporteren PDF-bestand te zoeken.
1. Selecteer in het Export PDF-bestand waarnaar u wilt exporteren de indeling waarnaar u het PDF-bestand wilt exporteren.
1. Geef in het vak Een time-out opgeven de tijd op die moet worden gewacht voordat de toepassing wordt uitgeschakeld. De standaardwaarde is 270 seconden.

   De omzettingstijd die wordt weergegeven wanneer het bestand wordt geconverteerd, kan groter zijn dan de waarde die u hier opgeeft. De Tijd van de Omzetting omvat de tijd die besteed aan het wachten op de draad of het proces, tijd wordt genomen om het dossier om te zetten, en de tijd die door de reserve omzetter (indien van toepassing) wordt genomen. tijd. De waarde bij Time-out opgeven is alleen de tijd die nodig is om het bestand om te zetten.

1. (Facultatief) in **specificeer het profiel van Preflight** optie, doorbladert de klik, en selecteert a [ profiel van Preflight ](https://helpx.adobe.com/nl/acrobat/using/preflight-profiles-acrobat-pro.html). Preflight-profielen worden alleen gebruikt bij het converteren van documenten naar de indeling PDF Archive (PDF/A).
1. Klik op Export. Wanneer de conversie is voltooid, wordt een koppeling naar het geëxporteerde bestand weergegeven.
1. Klik op de koppeling om het omgezette bestand weer te geven.

## Een PDF optimaliseren (alleen Windows) {#optimize-a-pdf}

PDF Generator ondersteunt het verkleinen van PDF-bestanden.

>[!NOTE]
>
>Als u een digitaal ondertekend document optimaliseert, worden de digitale handtekeningen verwijderd en ongeldig gemaakt.

1. Klik in de beheerconsole op Services > PDF Generator > PDF optimaliseren.
1. Klik op Bladeren om het PDF-bestand te zoeken dat u wilt optimaliseren.
1. Geef de configuratie-instellingen op:

   * Als u aangepaste instellingen wilt gebruiken, selecteert u Aangepaste instellingen gebruiken, geeft u de instellingen voor het bestandstype op en geeft u een time-outwaarde op. De standaardwaarde is 270 seconden.
   * Als u een bestaand instellingenbestand wilt gebruiken, selecteert u Bestand met instellingen uploaden en klikt u op Bladeren om naar de bestandslocatie te gaan.

1. Klik op Maken.
