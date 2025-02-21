---
title: Reader houdende uitbreiding van met beleid beveiligde PDF-documenten met gebruik van Portable Protection Library
description: Reader-extensies maken interactieve functies in Adobe PDF-documenten mogelijk via Acrobat Reader. Met de Portable Protection Library (PPL) kunt u de met DRM beveiligde PDF-documenten uitbreiden.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: document_services
feature: Document Security,Reader Extensions
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 0%

---

# Reader houdende uitbreiding van met beleid beveiligde PDF-documenten met gebruik van Portable Protection Library {#reader-extending-policy-protected-pdf-documents-using-portable-protection-library}

Houd u vertrouwd met concepten als documentbeveiliging, Reader-extensie en de programmeertaal Java om de met beveiligingsbeleid beveiligde PDF-documenten door het document uit te breiden.

Met documentbeveiliging kunt u de toegang van specifieke PDF-documenten beperken tot alleen geautoriseerde gebruikers. U kunt ook bepalen hoe een ontvanger een beveiligd document kan gebruiken. U kunt bijvoorbeeld opgeven of ontvangers tekst van een document dat met een beveiligingsbeleid is beveiligd, kunnen afdrukken, kopiëren of bewerken. Meer over documentveiligheid leren, zie [ over documentveiligheid ](/help/forms/using/admin-help/document-security.md).

Met Reader-extensies kunt u interactieve functies in Adobe PDF-documenten inschakelen via Acrobat Reader. Deze interactieve functies zijn normaal alleen beschikbaar via Adobe Acrobat Professional en Standard. Om over de interactieve eigenschappen te leren die de lezeruitbreiding kan toelaten, zie [ de dienst van Adobe Experience Manager Forms DocAssurance ](/help/forms/using/overview-aem-document-services.md)**.**

U kunt de draagbare beveiligingsbibliotheek gebruiken om beleid toe te passen op het document zonder dat u documenten hoeft te lezen via het netwerk. Slechts reizen de veiligheidsgeloofsbrieven en bescherming-beleid details over het netwerk. Het document zelf laat de client nooit over en het beveiligingsbeleid wordt lokaal op de client toegepast.

## Reader tot uitbreiding van door het beveiligingsbeleid beveiligde PDF-documenten {#reader-extending-document-security-policy-protected-pdf-documents}

De documenten die met een beleid zijn beveiligd, zijn versleutelde documenten. U kunt standaard API&#39;s voor leesextensies niet gebruiken voor het toepassen, verwijderen en ophalen van gebruiksrechten voor PDF-documenten die met een beleid zijn beveiligd. Alleen de Reader Extensions-service van de Portable Protection Library biedt API&#39;s voor het toepassen, verwijderen en ophalen van gebruiksrechten voor PDF-documenten die met beveiligingsbeleid zijn beveiligd.

### Reader Extensions-service {#reader-extensions-service}

De lezer-extensieservice voegt gebruiksrechten toe aan een met beleid beveiligd PDF-document. Functies die normaal niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Acrobat Reader, worden geactiveerd. Het heeft ook APIs om gebruiksrechten van een beleid-beschermd document te verwijderen en terug te winnen.

De Reader Extensions-service biedt volledige ondersteuning voor PDF-documenten die zijn gebaseerd op PDF-standaard 1.6 en hoger. Naast Acrobat Reader hebben externe gebruikers geen extra software of plug-ins nodig om de PDF-documenten te kunnen gebruiken die met een beleid zijn beveiligd.

U kunt de volgende taken uitvoeren met de service Reader Extensions:

* Gebruiksrechten toepassen op een PDF-document dat met een beleid is beveiligd.
* Verwijder gebruiksrechten van een met beleid beveiligd PDF-document.
* Haal gebruiksrechten op die zijn toegepast op een PDF-document dat met een beleid is beveiligd.

### Gebruiksrechten toepassen op een PDF-document dat met een beveiligingsbeleid is beveiligd. {#apply-usage-rights-to-a-document-security-policy-protected-pdf-document}

U kunt `applyUsageRights` Java API gebruiken om gebruiksrechten op beleid-beschermde documenten van PDF toe te passen. Gebruiksrechten hebben betrekking op functies die standaard beschikbaar zijn in Acrobat, maar niet in Adobe Reader, zoals de mogelijkheid om opmerkingen toe te voegen aan een formulier of formuliervelden in te vullen en het formulier op te slaan. PDF-documenten waarop gebruiksrechten zijn toegepast, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een document met ingeschakelde rechten opent in Adobe Reader, kan bewerkingen uitvoeren die zijn ingeschakeld voor dat specifieke document.

**Syntaxis:** `InputStream applyUsageRights(InputStream inputFile, File certFile, String credentialPassword, UsageRights usageRights)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inputFile</p> </td>
   <td><p>Geef InputStream op die het PDF-document vertegenwoordigt waarop gebruiksrechten moeten worden toegepast. U kunt met LiveCycle Rights Management of AEM Forms beveiligde documenten gebruiken.</p> </td>
  </tr>
  <tr>
   <td><p>certFile</p> </td>
   <td><p>Geef een File-object op dat een .jks-bestand vertegenwoordigt. Het .jks-bestand is een sleutelarchiefbestand. Het verwijst naar een certificaat dat gebruiksrechten toekent.</p> </td>
  </tr>
  <tr>
   <td><p>credentialPassword</p> </td>
   <td><p>Geef het wachtwoord van het sleutelarchief op. </p> </td>
  </tr>
  <tr>
   <td><p>usageRights</p> </td>
   <td><p>Specificeert een voorwerp van type <a href="https://help.adobe.com/en_US/livecycle/11.0/ProgramLC/javadoc/com/adobe/livecycle/readerextensions/client/UsageRights.html" target="_blank"> UsageRights </a>. Het object usageRights vertegenwoordigt individuele rechten die kunnen worden toegepast op een met beleid beveiligd PDF-document.</p> </td>
  </tr>
 </tbody>
</table>

### Haal gebruiksrechten op die zijn toegepast op een PDF-document dat met een beleid is beveiligd.   {#retrieve-usage-rights-applied-to-a-policy-protected-pdf-document-nbsp}

U kunt `getDocumentUsageRights` Java API gebruiken om de gebruiksrechten terug te winnen van de reader uitbreiding die op een beleid-beschermd document van PDF worden toegepast. Door informatie over gebruiksrechten op te halen, kunt u meer weten over de functies die de extensie van de lezer heeft ingeschakeld voor het door het beleid beveiligde PDF-document.

**Syntaxis:** `public GetUsageRightsResult getDocumentUsageRights(InputStream inDoc)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p>inDoc</p> </td>
   <td><p>Geef InputStream op die staat voor het PDF-document waaruit gebruiksrechten moeten worden opgehaald. U kunt met LiveCycle Rights Management of AEM Forms beveiligde documenten gebruiken.</p> </td>
  </tr>
 </tbody>
</table>

#### Codevoorbeeld {#code-sample}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\protected.pdf"; //Input file can be RM protected or unprotected pdf file
File certFile = new File("C:\\Sample\\cert.jks"); //RE certificate file
String password = "password"; //password for RE certificate
UsageRights usageRights = getUsageRights(true,true,false,false,true,true,false,false,false,false,true);

//RE rights to be applied on the file : FormFillIn, FormDataImportExport, SubmitStandalone, OnlineForms, DynamicFormField, DynamicFormPages, BarcodeDecoding, DigitalSignatures, Comments, CommentsOnline, EmbeddedFiles

InputStream inputFileStream = new FileInputStream(inputFileName);
InputStream output = rmClient2.getRightsManagementReaderExtensionService().applyUsageRights(inputFileStream, certFile, credentialPassword, rights);

String outputFileName = "C:\\Sample\\ReAdded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = output.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}

System.out.println("UsageRights applied successfully to the document. ");
 outputStream.close();
inputFileStream.close();

//Get Usage Rights for the output pdf document
InputStream fileWithRe = new FileInputStream(myFile);

GetUsageRightsResult usageRights = rmClient2.getRightsManagementReaderExtensionService().getDocumentUsageRights(fileWithRe);

UsageRights rights = usageRights.getRights();
String right1 = rights1.toString();
System.out.println("RE rights for the file are :\n"+right1);
 fileWithRe.close();
```

### Gebruiksrechten van een met een beleid beveiligd PDF-document verwijderen {#remove-usage-rights-of-a-policy-protected-pdf-document}

U kunt `removeUsageRights` Java API gebruiken om gebruiksrechten uit een beleid-beschermd document te verwijderen. U moet gebruiksrechten verwijderen uit een met beleid beveiligd PDF-document om andere AEM Forms-bewerkingen uit te voeren op het document. U moet bijvoorbeeld een PDF-document digitaal ondertekenen (of certificeren) voordat u gebruiksrechten instelt. Daarom als u verrichtingen op een beleid-beschermd document wilt uitvoeren, moet u gebruiksrechten uit het document van PDF verwijderen, de andere verrichtingen uitvoeren, zoals digitaal het ondertekenen van het document, en dan gebruiksrechten op het document opnieuw toepassen.

**Syntaxis:** `InputStream removeUsageRights(InputStream inputFile)`

<table>
 <tbody>
  <tr>
   <td><p><strong>Parameter</strong></p> </td>
   <td><p><strong>Beschrijving</strong></p> </td>
  </tr>
  <tr>
   <td><p> </p> <p>inputFile</p> </td>
   <td>Specificeer InputStream die het document van PDF vertegenwoordigt waarvan gebruik <br /> rechten moeten worden verwijderd. U kunt met LiveCycle Rights Management of AEM Forms beveiligde documenten gebruiken.</td>
  </tr>
 </tbody>
</table>

#### Codevoorbeeld {#code-sample-1}

```java
//Create a ServiceClientFactory instance
ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
//Create a RightsManagementClient object
RightsManagementClient2 rmClient2= new RightsManagementClient2(factory);

String inputFileName = "C:\\Sample\\fileWithRe.pdf"; //Input file can be RM protected or unprotected pdf file
InputStream inputFileStream = new FileInputStream(inputFileName);

InputStream fileStream = rmClient2.getRightsManagementReaderExtensionService().removeUsageRights(inputFileStream);

String outputFileName = "C:\\Sample\\ReRemoveded.pdf";
//Save the PDF document
File myFile = new File(outputFileName);
FileOutputStream outputStream = new FileOutputStream(myFile);

int read = 0;
byte[] bytes = new byte[1024];

while ((read = fileStream.read(bytes)) != -1) {

    outputStream.write(bytes, 0, read);
}
System.out.println("RE rights removed successfully from the document.");
outputStream.close();
inputFileStream.close();
```
