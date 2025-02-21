---
title: Werken met PDF-hulpprogramma's
description: Met de PDF-hulpprogramma's kunt u PDF- en XDP-bestandsindelingen omzetten, PDF-documenteigenschappen instellen en ophalen en XMP-metagegevens bewerken.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services,APIs & Integrations
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '2549'
ht-degree: 0%

---

# Werken met PDF-hulpprogramma&#39;s {#working-with-pdf-utilities}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

**Ongeveer de Dienst van Hulpmiddelen van PDF**

De PDF-hulpprogramma&#39;s kunnen converteren tussen PDF- en XDP-bestandsindelingen, PDF-documenteigenschappen instellen en ophalen en XMP-metagegevens bewerken. Voordat u bijvoorbeeld een PDF-document omzet in een andere indeling, is het handig om de eigenschappen te controleren om te bepalen welke servicebewerking moet worden aangeroepen voor de conversie.

U kunt deze taken uitvoeren met de PDF Utilities-service:

* Converteer PDF-documenten naar XDP-documenten.
* XDP-documenten converteren naar PDF-documenten. (Zie [ Converterend XDP Documenten in de Documenten van PDF ](pdf-utilities.md#converting-xdp-documents-into-pdf-documents).)
* Eigenschappen van PDF-documenten ophalen. (Zie [ het Terugwinnen van de Eigenschappen van het Document van PDF ](pdf-utilities.md#retrieving-pdf-document-properties).)
* Sla een PDF-document op en optimaliseer het voor snelle webweergave. (Zie [ Plaatsend het Document van PDF sparen Wijzen ](pdf-utilities.md#setting-pdf-document-save-modes).)

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

## PDF-documenten converteren naar XDP-documenten {#converting-pdf-documents-into-xdp-documents}

Met de PDF Utilities Java en de webservice-API&#39;s kunt u PDF-documenten programmatisch converteren naar XDP-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary-of-steps}

Voer de volgende stappen uit om een PDF-document om te zetten in een XDP-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking PDF naar XDP aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een cliënt PDFUtilityService**

Voordat u een PDF-hulpprogrammabewerking kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit gedaan door een `PDFUtilityServiceClient` -object te maken. Met de webservice-API gebeurt dit met behulp van een `PDFUtilityServiceService` -object.

**Roep PDF aan XDP omzettingsverrichting**

Nadat u de serviceclient hebt gemaakt, kunt u de conversiebewerking PDF naar XDP uitvoeren.

**zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de Java API {#convert-pdf-documents-into-xdp-documents-using-the-java-api}

Converteer PDF-documenten naar XDP-documenten met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertPDFtoXDP` van het object `PDFUtilityServiceClient` aan en geeft u een `com.adobe.idp.Document` -object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` -object dat het nieuwe XDP-bestand vertegenwoordigt.

**zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten converteren naar XDP-documenten met de webservice-API {#convert-pdf-documents-into-xdp-documents-using-the-web-service-api}

Converteer PDF-documenten naar XDP-documenten met de PDF Utilities API (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die het dossier van WSDL van de dienst van PDF gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` -object met de constructor van de proxyklasse.

1. De conversiebewerking PDF naar XDP aanroepen

   Roep de methode `convertPDFtoXDP` van het object `PDFUtilityServiceService` aan en geef een `BLOB` -object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `BLOB` -object dat het nieuwe XDP-bestand vertegenwoordigt.

**zie ook**

[PDF-documenten converteren naar XDP-documenten](pdf-utilities.md#converting-pdf-documents-into-xdp-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## XDP-documenten converteren naar PDF-documenten {#converting-xdp-documents-into-pdf-documents}

Met de PDF Utilities Java en de webservice-API&#39;s kunt u XDP-documenten programmatisch converteren naar PDF-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-1}

Voer de volgende stappen uit om een XDP-document te converteren naar een PDF-document:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de conversiebewerking XDP naar PDF aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een cliënt PDFUtilityService**

Voordat u een PDF-hulpprogrammabewerking kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit gedaan door een `PDFUtilityServiceClient` -object te maken. Met de webservice-API gebeurt dit met behulp van een `PDFUtilityServiceService` -object.

**Roep XDP aan de omzettingsverrichting van PDF** aan

Nadat u de de dienstcliënt creeert, kunt u de XDP aan de omzettingsverrichting van PDF aanhalen.

**zie ook**

[XDP-documenten converteren naar PDF-documenten met de Java API](pdf-utilities.md#convert-xdp-documents-into-pdf-documents-using-the-java-api)

[XDP-documenten omzetten in PDF-documenten met de webservice-API](pdf-utilities.md#converting-xdp-documents-into-pdf-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten converteren naar PDF-documenten met de Java API {#convert-xdp-documents-into-pdf-documents-using-the-java-api}

XDP-documenten converteren naar PDF-documenten met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertXDPtoPDF` van het object `PDFUtilityServiceClient` aan en geeft u een `com.adobe.idp.Document` -object door dat het XDP-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` -object dat het nieuwe PDF-bestand vertegenwoordigt.

**zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### XDP-documenten omzetten in PDF-documenten met de webservice-API {#converting-xdp-documents-into-pdf-documents-using-the-web-service-api}

XDP-documenten converteren naar PDF-documenten met de PDF Utilities API (webservice-API):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die het dossier van WSDL van de dienst van PDF gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` -object met de constructor van de proxyklasse.

1. De conversiebewerking XDP naar PDF aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertXDPtoPDF` van het object `PDFUtilityServiceService` aan en geeft u een `BLOB` -object door dat het XDP-bestand vertegenwoordigt. De methode retourneert een `BLOB` -object dat het nieuwe PDF-bestand vertegenwoordigt.

**zie ook**

[XDP-documenten converteren naar PDF-documenten](pdf-utilities.md#converting-xdp-documents-into-pdf-documents)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Eigenschappen van PDF-documenten ophalen {#retrieving-pdf-document-properties}

Met de PDF Utilities Java en de webservice-API&#39;s kunt u PDF-documenteigenschappen programmatisch ophalen, bijvoorbeeld of het document een invulbaar formulier is of de minimaal vereiste Acrobat-versie om het document te lezen.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63)

### Overzicht van de stappen {#summary_of_steps-2}

Voer de volgende stappen uit om PDF-documenteigenschappen op te halen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ophaalbewerking voor eigenschappen aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een cliënt PDFUtilityService**

Voordat u een PDF-hulpprogrammabewerking kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit gedaan door een `PDFUtilityServiceClient` -object te maken. Met de webservice-API wordt dit gedaan met een `PDFUtilityServiceService` -object.

**haalt de eigenschappen herwinning verrichting** aan

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**zie ook**

[Eigenschappen van PDF-documenten ophalen met de Java API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-java-api)

[Eigenschappen van PDF-documenten ophalen met de webservice-API](pdf-utilities.md#retrieve-pdf-document-properties-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de Java API {#retrieve-pdf-document-properties-using-the-java-api}

Eigenschappen van PDF-documenten ophalen met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `getPDFProperties` van het object `PDFUtilityServiceClient` aan en geeft u het volgende door:

   * Een `com.adobe.idp.Document` -object dat het PDF-document vertegenwoordigt.
   * Een `PDFPropertiesOptionSpec` -object dat de eigenschappen bevat die moeten worden geëvalueerd.

   De methode retourneert een `PDFPropertiesResult` -object dat de resultaten van de query bevat.

**zie ook**

[Eigenschappen van PDF-documenten ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Eigenschappen van PDF-documenten ophalen met de webservice-API {#retrieve-pdf-document-properties-using-the-web-service-api}

U kunt de eigenschappen van PDF-documenten ophalen met de API voor de PDF Utilities-webservice:

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die het dossier van WSDL van de dienst van PDF gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` -object met de constructor van de proxyklasse.

1. Ophaalbewerking voor eigenschappen aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `getPDFProperties` van het object `PDFUtilityServiceService` aan en geeft u het volgende door:

   * Een `BLOB` -object dat het PDF-document vertegenwoordigt.
   * Een `PDFPropertiesOptionSpec` -object dat de eigenschappen bevat die moeten worden geëvalueerd.

   De methode retourneert een `PDFPropertiesResult` -object dat de resultaten van de query bevat.

**zie ook**

[Eigenschappen van PDF-documenten ophalen](pdf-utilities.md#retrieving-pdf-document-properties)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## Modus voor opslaan van PDF-document instellen {#setting-pdf-document-save-modes}

Met de PDF Utilities Service Java en de webservice-API&#39;s kunt u een opslagmodus voor een PDF-document programmatisch instellen. Als u een opslagmodus instelt met de service PDF Utilities, stelt de service PDF Utilities alleen de opslagmodus in en wordt het PDF-document niet daadwerkelijk opgeslagen. Het PDF-document wordt opgeslagen wanneer het wordt doorgegeven aan een andere servicebewerking. U kunt bijvoorbeeld de PDF Utilities-service gebruiken om een specifieke opslagmodus in te stellen en deze door te geven aan de coderingsservice, waarbij het PDF-document daadwerkelijk wordt opgeslagen en versleuteld.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-3}

Voer de volgende stappen uit om de opslagoptie voor PDF-documenten in te stellen:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Stel de opslagmodus in.
1. Roep de opslagbewerking aan.
1. Geef het PDF-document door aan een andere bewerking.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, dient u de proxybestanden op te nemen.

**creeer een cliënt PDFUtilityService**

Voordat u een PDF-hulpprogrammabewerking kunt uitvoeren, moet u een PDFUtilityService-client maken. Met de Java API wordt dit gedaan door een `PDFUtilityServiceClient` -object te maken. Met de webservice-API wordt dit gedaan met een `PDFUtilityServiceService` -object.

**plaats sparen wijze**

U kunt een van de volgende opslagopties kiezen:

* `INCREMENTAL`: Opslaan in stappen om de tijd die nodig is om te besparen te verkorten
* `FAST_WEB_VIEW`: opslaan voor snelle webweergave
* `FULL`: Opslaan met volledige opslag (zonder optimalisaties)

**Roep sparen stijlverrichting** aan

Nadat u de de dienstcliënt creeert, kunt u de eigenschappen terugwinningsverrichting aanhalen.

**ga het document van PDF tot een andere verrichting van AEM Forms over**

Wanneer de PDF Utilities-service de opgegeven opslagmodus heeft ingesteld, geeft u het PDF-document door aan een andere AEM Forms-bewerking. Nadat het PDF-document uit die bewerking is geretourneerd, wordt het in de opgegeven modus opgeslagen. Als u bijvoorbeeld de PDF Utilities-service gebruikt om de `FAST_WEB_VIEW` -modus in te stellen en het PDF-document vervolgens doorgeeft aan de `encryptUsingPassword` -bewerking van de Coderingsservice, wordt het geretourneerde PDF-document versleuteld met een wachtwoord en opgeslagen in de `FAST_WEB_VIEW` -modus.

>[!NOTE]
>
>Met Snel starten die aan deze sectie is gekoppeld, wordt de modus `FAST_WEB_VIEW` ingesteld en wordt het PDF-document vervolgens doorgegeven aan de bewerking `encryptUsingPassword` van de coderingsservice.

**zie ook**

[Opslagopties voor PDF-documenten instellen met de Java API](pdf-utilities.md#set-pdf-document-save-options-using-the-java-api)

[Opslagopties voor PDF-documenten instellen met de webservice-API](pdf-utilities.md#set-pdf-document-save-options-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

[PDF-documenten versleutelen met een wachtwoord](/help/forms/developing/encrypting-decrypting-pdf-documents.md#encrypting-pdf-documents-with-a-password)

### Opslagopties voor PDF-documenten instellen met de Java API {#set-pdf-document-save-options-using-the-java-api}

Stel de opslagopties voor PDF-documenten in met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode` -object met behulp van de constructor.
   * Stel de opslagmodus in door de methode `setSaveStyle` van het object `PDFUtilitySaveMode` aan te roepen en een tekenreekswaarde door te geven die de opslagmodus aangeeft. Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u `FAST_WEB_VIEW` door.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode `setSaveMode` van het object `PDFUtilityServiceClient` aan en geef de volgende waarden door:

   * Een `com.adobe.idp.Document` -object dat het PDF-document vertegenwoordigt.
   * Een `PDFUtilitySaveMode` -object dat de opslagstijl bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.

   De methode retourneert een `com.adobe.idp.Document` -object dat is opgemaakt met de opgegeven opslagstijl.

1. PDF-document doorgeven aan een andere AEM Forms-bewerking

   * Geef het geretourneerde `com.adobe.idp.Document` -object door aan een andere AEM Forms-bewerking.

**zie ook**

[Modus voor opslaan van PDF-document instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### Opslagopties voor PDF-documenten instellen met de webservice-API {#set-pdf-document-save-options-using-the-web-service-api}

Stel de opslagopties voor het PDF-document in met behulp van het AP Hulpprogramma&#39;s van PDF (webservice):

1. Projectbestanden opnemen

   * Creeer een Microsoft .NET cliëntassemblage die het dossier van WSDL van de dienst van PDF gebruikt.
   * Verwijs naar de Microsoft .NET cliëntassemblage.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceService` -object met de constructor van de proxyklasse.

1. De modus Opslaan instellen

   * Maak een `PDFUtilitySaveMode` -object met behulp van de constructor.
   * Stel de opslagmodus in door een tekenreekswaarde toe te wijzen aan de methode `saveStyle` van het object `PDFUtilitySaveMode` die de opslagmodus aangeeft. Als u bijvoorbeeld wilt opslaan voor snelle webweergave, geeft u `FAST_WEB_VIEW` op.

1. Opslaan van stijlbewerking aanroepen

   Roep de methode `setSaveMode` van het object `PDFUtilityServiceService` aan en geef de volgende waarden door:

   * Een `BLOB` -object dat het PDF-document vertegenwoordigt.
   * Een `PDFUtilitySaveMode` -object dat de opslagstijl bevat die moet worden gebruikt.
   * Een Booleaanse waarde die wordt gebruikt om te bepalen of vorige instellingen moeten worden overschreven.

   De methode retourneert een `BLOB` -object dat is opgemaakt met de opgegeven opslagstijl. U kunt dat object vervolgens opslaan als een PDF-document.

1. PDF-document doorgeven aan een andere Forms-bewerking

   * Geef het geretourneerde `BLOB` -object door aan een andere AEM Forms-bewerking.

**zie ook**

[Modus voor opslaan van PDF-document instellen](pdf-utilities.md#setting-pdf-document-save-modes)

[AEM Forms aanroepen met Base64-codering](/help/forms/developing/invoking-aem-forms-using-web.md#invoking-aem-forms-using-base64-encoding)

[Creërend een .NET cliëntassemblage die het coderen Base64 gebruikt](/help/forms/developing/invoking-aem-forms-using-web.md#creating-a-net-client-assembly-that-uses-base64-encoding)

## PDF-documenten bewerken {#sanitizing-pdf-documents}

Met de PDF Utilities Java API&#39;s kunt u PDF-documenten programmatisch converteren naar XDP-documenten.

>[!NOTE]
>
>Voor meer informatie over de dienst van Hulpmiddelen van PDF, zie [ Verwijzing van de Diensten voor AEM Forms ](https://www.adobe.com/go/learn_aemforms_services_63).

### Overzicht van de stappen {#summary_of_steps-4}

Voer de volgende stappen uit om het PDF-document te ontsmetten:

1. Inclusief projectbestanden.
1. Maak een PDFUtilityService-client.
1. Roep de ontsmettingsbewerking aan.

**omvat projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Neem de benodigde JAR-bestanden op als u een clienttoepassing met Java wilt maken.

**creeer een cliënt PDFUtilityService**

Alvorens u een ontsmettingsverrichting programmatically kunt uitvoeren, moet u een cliënt PDFUtilityService tot stand brengen. Met de Java API wordt dit gedaan door een `PDFUtilityServiceClient` -object te maken.

**Roep PDF aan XDP omzettingsverrichting**

Nadat u de de dienstcliënt creeert, kunt u de ontsmettingsverrichting aanhalen.

**zie ook**

[PDF-documenten converteren naar XDP-documenten met de Java API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-java-api)

[PDF-documenten converteren naar XDP-documenten met de webservice-API](pdf-utilities.md#convert-pdf-documents-into-xdp-documents-using-the-web-service-api)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)

### PDF-documenten ontsmetten met de Java API {#sanitize-pdf-documents-using-the-java-api}

Documenten ontsmetten met de PDF Utilities API (Java):

1. Projectbestanden opnemen

   Neem client-JAR-bestanden, zoals adobe-pdfutility-client.jar, op in het klassenpad van uw Java-project.

1. Een PDFUtilityService-client maken

   Maak een `PDFUtilityServiceClient` -object door de constructor ervan te gebruiken en een `ServiceClientFactory` -object door te geven dat verbindingseigenschappen bevat.

1. De conversiebewerking PDF naar XDP aanroepen

   Als u de conversie wilt uitvoeren, roept u de methode `convertPDFtoXDP` van het object `PDFUtilityServiceClient` aan en geeft u een `com.adobe.idp.Document` -object door dat het PDF-bestand vertegenwoordigt. De methode retourneert een `com.adobe.idp.Document` -object dat het nieuwe XDP-bestand vertegenwoordigt.

**zie ook**

[PDF-documenten bewerken](/help/forms/developing/pdf-utilities-service-java-api.md#quick-start-soap-mode-sanitizing-pdf-documents)

[Inclusief AEM Forms Java-bibliotheekbestanden](/help/forms/developing/invoking-aem-forms-using-java.md#including-aem-forms-java-library-files)

[Verbindingseigenschappen instellen](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties)
