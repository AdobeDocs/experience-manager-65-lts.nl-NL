---
title: Verlopen van Reader Extensions-certificaten en de gevolgen ervan
description: Verlopen van Reader Extensions-certificaten en de gevolgen ervan
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 83dbd00e-28ad-4a2e-ac22-3658fb6f639b
source-git-commit: 7a1bbcb84a0be301bba4473f30ca4a8d9ea3f906
workflow-type: tm+mt
source-wordcount: '1087'
ht-degree: 0%

---

# Verlopen van Reader Extensions-certificaten en de gevolgen ervan {#expiration-of-reader-extensions-certificates-and-its-impact}

Adobe Experience Manager Forms (AEM Forms)-klanten met Adobe Managed Services- of On-premise Enterprise Base-licenties hebben het recht om Acrobat Reader DC Extensions-service te gebruiken. Met deze service kan een organisatie eenvoudig interactieve PDF-documenten delen door de functionaliteit van Acrobat Reader uit te breiden met extra gebruiksrechten. De service voegt gebruiksrechten toe aan een PDF-document en activeert functies die niet beschikbaar zijn wanneer een PDF-document wordt geopend met Adobe Acrobat Reader, zoals het toevoegen van opmerkingen aan een document, het invullen van formulieren en het opslaan van het document. Gebruikers van derden hebben geen extra software of plug-ins nodig om met documenten waarvoor rechten zijn ingeschakeld te kunnen werken. PDF-documenten waaraan gebruiksrechten zijn toegevoegd, worden documenten met ingeschakelde rechten genoemd. Een gebruiker die een PDF-document met ingeschakelde rechten opent in Acrobat Reader, kan de bewerkingen uitvoeren die voor dat document zijn ingeschakeld.

Adobe gebruikt een PKI (Public Key Infrastructure) om digitale certificaten uit te geven voor gebruik in licenties en functionaliteit. Adobe heeft certificaten onder het certificaatgezag **Adobe Root CA** uitgeeft, die op 7 Januari, 2023 wordt geplaatst te verlopen. De vervaldatum van certificaat beïnvloedt geen de documenten van PDF die gebruikend productiecertificaten worden uitgebreid die van de **gebaseerde certificaten van de Wortel CA van Adobe** worden uitgegeven (oude certificaten). Alle PDF-documenten, Reader die vóór 7 januari 2023 zijn uitgebreid met de oude certificaten, inclusief de documenten die door uw klanten zijn gedownload, blijven werken met alle gebruiksrechten die op deze documenten zijn toegepast en hoeven niet te worden bijgewerkt.

Een nieuw certificaatgezag, **de Wortel CA G2 van Adobe**, en certificaten die op het nieuwe certificaatgezag worden gebaseerd zijn nu beschikbaar. Op of vóór 7 Januari, 2023, begin de nieuwe certificaten te gebruiken — die gebaseerd op **de Wortel CA G2 van de Adobe** — om uw nieuwe documenten van PDF uit te breiden.  U kunt [ nieuwe certificaten van de het Verlenen van vergunningenWebsite van Adobe ](https://licensing.adobe.com/) of de Steun van Adobe verkrijgen.

## Veelgestelde vragen

**Q. Wat is het verschil tussen een Adobe Root-certificaat en een Acrobat Reader Extensions-certificaat? Is het Adobe Root-certificaat afhankelijk van een Acrobat Reader Extensions-certificaat? Zijn beide certificaten die in Januari 2023 verlopen?**

A. Adobe Root CA is de certificeringsinstantie van waaruit een Acrobat Reader Extensions-certificaat wordt uitgegeven. Op 7 januari 2023 verlopen &quot;Adobe Root CA&quot; en alle certificaten die daaruit worden uitgegeven.

**Q. Adobe heeft al eerder meegedeeld dat de geldigheidsduur van certificaten afloopt en dat het gebruik en de opening van PDF-documenten gevolgen hebben. Moet die mededeling worden genegeerd?**

A. Op basis van de herbeoordeling van de situatie blijven alle PDF-documenten die vóór 7 januari 2023 zijn uitgebreid met productiecertificaten die zijn uitgegeven door de oude &quot;Adobe Root CA&quot;, ongewijzigd na 7 januari 2023 werken. Als u uw PDF-documenten al hebt bijgewerkt, is er geen wijziging in de ervaring.

**Q. Wie moet ik contacteren als ik extra vragen heb?**

A. U kunt [ Steun van Adobe ](https://experienceleague.adobe.com/nl?support-solution=Experience+Manager#support) contacteren of een steunkaartje opheffen.

**Q. Wat gebeurt er als ik mijn certificaat niet vóór 7 januari 2023 bijwerk?**

A. Alle PDF-documenten die zijn uitgebreid met productiecertificaten die vóór 7 januari 2023 zijn uitgegeven door de oude Adobe Root CA, werken na 7 januari 2023 ongewijzigd. PDF&#39;s die met evaluatiecertificaten zijn uitgebreid, werken niet meer na de vervaldatum.

**Q. Is de beschrijving van nieuwe certificaten om het even welk verschillend van oude certificaten?**

A. De beschrijving van de nieuwe certificaten van de Uitbreidingen van Acrobat Reader noemt **G3-P24** als programmanaam. In de beschrijving van oudere certificaten (certificaten die op &quot;Adobe Root CA&quot;worden gebaseerd), **P24** wordt vermeld als programmanaam.

**Q. Hoe verkrijg ik de recentste certificaten?**

A. Alle gerechtigde Klanten van Forms (met actieve vergunning) kunnen de nieuwe certificaten (certificaten downloaden die op &quot;Adobe Root CA G2&quot;worden gebaseerd) van de [ Adobe Vergunnende Website ](https://licensing.adobe.com/). Als u niet het certificaat op de Website van het Verlenen van vergunningen van Adobe kunt vinden, contacteer [ Steun van Adobe ](https://experienceleague.adobe.com/nl?support-solution=Experience+Manager&lang=en#support) of ophef een steunkaartje.

**Q. Werken mijn PDF-documenten die zijn uitgebreid met certificaten die zijn uitgegeven door &quot;Adobe Root CA&quot; (de oude certificeringsinstantie) nog steeds na 7 januari 2023?**

A. Ja, alle PDF-documenten die vóór 7 januari 2023 zijn uitgebreid met productiecertificaten die zijn uitgegeven door de &quot;Adobe Root CA&quot; (de oude certificeringsautoriteit), blijven na 7 januari 2023 zonder wijziging werken. PDF-documenten die met evaluatiecertificaten zijn uitgebreid, werken niet meer na de vervaldatum.

**Q. Welke versie van Adobe Acrobat Reader is vereist om PDF-documenten te blijven gebruiken die zijn uitgebreid met certificaten die zijn uitgegeven door &quot;Adobe Root CA&quot; (de oude certificeringsinstantie)?**

A. Adobe Acrobat Reader 2020 of hoger is vereist voor het gebruik van PDF-documenten die zijn uitgebreid met &quot;Adobe Root CA&quot; (de oude certificeringsinstantie). Dit is de ondersteunde versie van Acrobat Reader op het moment van publicatie van dit document. Als u a [ niet-gesteunde versie van Adobe Acrobat ](https://helpx.adobe.com/nl/support/programs/eol-matrix.html) gebruikt, adviseert Adobe dat u [ de recentste versie van Adobe Acrobat Reader ](https://get.adobe.com/reader/) downloadt en installeert.

**Q. Welke versie van Adobe Acrobat Reader wordt vereist om de documenten van PDF verder te gebruiken die met certificaten worden uitgebreid die van &quot;Adobe Root CA 2&quot;(de nieuwe certificaatautoriteit) worden uitgegeven?**

A. Adobe Acrobat Reader 2020 of hoger is vereist voor het gebruik van PDF-documenten die zijn uitgebreid met &quot;Adobe Root CA 2&quot; (de nieuwe certificeringsinstantie). Als u a [ niet-gesteunde versie van Adobe Acrobat Reader ](https://helpx.adobe.com/nl/support/programs/eol-matrix.html) gebruikt, adviseert Adobe dat u [ de recentste versie van Adobe Acrobat Reader ](https://get.adobe.com/reader/) downloadt en installeert.

**Q. Kan ik een oud certificaat van de Uitbreidingen van Acrobat Reader schrappen en een nieuwe toevoegen op een Server van Adobe Experience Manager Forms terwijl het blijven gebruiken van de bestaande alias?**

A. Ja, u kunt een oud certificaat van de Uitbreidingen van Acrobat Reader schrappen en een nieuwe met de bestaande alias aan een Server van Adobe Experience Manager Forms toevoegen.

**Q. Kan ik zowel nieuwe als oude Acrobat Reader Extensions-certificaten op een Adobe Experience Manager Forms Server bewaren?**

A. Ja, u kunt beide certificaten maar met verschillende aliassen op een Adobe Experience Manager Forms Server houden. Vanaf 7 januari 2023 kunt u alleen het nieuwe certificaat gebruiken voor Reader om een PDF-document uit te breiden.

**Q. Kan ik hetzelfde Acrobat Reader Extensions-certificaat importeren in alle Adobe Experience Manager Forms-omgevingen?**

A. Ja, hetzelfde Acrobat Reader Extensions-certificaat kan in meerdere omgevingen worden gebruikt.

**Q. Hoe kan ik de gebruiksrechten controleren die op een PDF-document zijn toegepast?**

A. U kunt [ getDocumentUsageRights ](/help/forms/developing/acrobat-reader-dc-extensions-service.md) API gebruiken om de informatie over de gebruiksrechten terug te winnen die op een document van PDF worden toegepast.

**Q. Hoe kan ik het wachtwoord van een Acrobat Reader Extensions-certificaatbestand wijzigen?**

A. Op Microsoft Windows, om het certificaatWachtwoord te veranderen, installeer het certificaat gebruikend de Console van het Beheer van Microsoft (MMC) en selecteer **Teken de sleutel als Exportable**. Exporteer het certificaat met een persoonlijke sleutel nadat u het hebt geïnstalleerd en gebruik een ander wachtwoord voor het PFX-bestand.


<!-- 
## Applying the certificates {#obtaning-and-applying-the-certificates} 

You can choose one of the following paths to apply latest certificates:

* [Updating certificates for an AEM Forms on JEE environment](#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment) 
* [Updating certificates for an AEM Forms on OSGi environment](#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment)

>[!NOTE]
>
>The document uses the term certificates and credentials interchangeably.

### Pre-requisites {#Pre-requisites}

Updating the certificates requires using actions available on AEM Forms administrator console and Reader Extension APIs provided by AEM Forms. The document is intended for users and administrators with knowledge of using Adobe Experience Manger Forms APIs. Before you start, ensure that: 

* the user has administrator rights on underlying AEM Forms environment. 
* the user has setup the [development environment](https://experienceleague.adobe.com/docs/experience-manager-65-lts/developing/devtools/howto-projects-eclipse.html) and has access to it.
* [obtain the certificates](#obtain-the-certificates).


### Obtain the certificates {#obtain-the-certificates}

The Rights credential is delivered as a digital certificate that contains the public key, the private key, and the password used to access the credential.

If your organization purchases a production version of Reader Extensions, the production Rights credential is delivered by Adobe Licensing Website (LWS). A production Rights credential is unique to your organization and can enable the specific usage rights that you require.

If you obtained Reader Extensions through a partner or software provider who integrated Reader Extensions into their software, the Rights credential is provided to you by that partner who, in turn, receives this credential from Adobe.

>[!NOTE]
>
>The Rights credential cannot be used for typical document signing or assertion of identity. For these applications, you can use a self-sign certificate or acquire an identity certificate from a Certificate Authority (CA).

The following types of Rights credentials are available:

**Customer Evaluation**: A credential with a short validity period that is provided to customers who want to evaluate Reader Extensions. Usage rights applied to documents using this credential expire when the credential expires. This type of credential is valid only for two to three months.

**Production**: A credential with a long validity period that is provided to customers who purchased the full product. Production credentials are unique to each customer but can be installed on multiple systems.

If you have already used certificates to reader extend PDF files, download a production certificate from [Adobe Licensing Website (LWS)](https://licensing.adobe.com/).

### Applying certificates for an AEM Forms on JEE environment {#Updating-and-Applying-certificates-for-an-AEM-Forms-on-JEE-environment} 

Applying new certificates on AEM Forms on JEE stack requires importing new credentials and applying usage rights. You can use admin console to import credentials and AEM Forms Reader Extension APIs to apply usage rights. 

#### Import and configure credentials 

You can use the Trust Store Management pages to import a new credential. The Trust Store may contain more than one Reader Extensions credential. Designate one of those credentials as the default Reader Extensions credential. The default credential is used when a Workbench user is unable to determine which credential to use during process creation. These rules apply to default credentials:

* If you import a Reader Extensions credential and the Trust Store contains no other Reader Extensions credentials, it is set as the default.
* If you import a Reader Extensions credential with the Default option selected, the default type is removed from an existing default credential. The imported credential becomes the default.
* You cannot delete a default Reader Extensions credential. To delete the default credential, first set another credential as the default. An exception to this rule is that if there is only one credential, you can delete it even though it is the default.
* You cannot update a default Reader Extensions credential.

To import the credentials: 

1. In administration console, click Settings > Trust Store Management > Local Credentials.
1. Click Import and, under Trust Store Type, select Acrobat Reader DC extensions Credential.
1. (Optional) To indicate that this credential is the default credential to use with Acrobat Reader DC extensions, select Default.
1. In the Alias box, type an identifier for the credential. This identifier is used as the display name for the credential in Acrobat Reader DC extensions. This alias is also used to access the credential programmatically using the AEM forms SDK.
1. Click Choose File to locate the credential, type the password of the credential, and then click OK.

If the error message "Failed to import credential due to either incorrect file format, or incorrect password" appears, verify that the password is valid.

You can also import and delete credentials programmatically. (See [Programming with AEM forms](../../developing/credentials.md).)

<!-- ### Remove usage rights from existing rights-enabled PDF documents

Remove usage rights from existing rights-enabled PDF documents before applying usage rights with latest credentials. AEM Forms on JEE provides APIs to remove usage rights. For detailed instructions, see [Removing Usage Rights from PDF Documents](../../developing/assigning-usage-rights.md#removing-usage-rights-from-pdf-documents).

To remove usage rights for AEM Forms on JEE processes developed in Workbench, see [Workbench Help](https://helpx.adobe.com/content/dam/help/en/experience-manager/6-5/forms/pdf/WorkbenchHelp.pdf). 

#### Apply the usage rights to PDF documents 

After importing new credentials, you can apply usage rights to PDF documents using the Acrobat Reader DC extensions Java Client API and web service.  For details, see [Applying Usage Rights to PDF Documents](../../developing/assigning-usage-rights.md#applying-usage-rights-to-pdf-documents). 


### Applying certificates for an AEM Forms on OSGi environment {#Updating-and-applying-certificates-for-an-AEM-Forms-on-OSGi-environment}

Applying new certificates on AEM Forms on OSGi stack requires importing new credentials and applying usage rights. You can use admin console to import credentials and AEM Forms Reader Extension APIs to apply usage rights. 

#### Import credentials {#Import-credentials}

In an AEM Forms on OSGi environment, a Reader Extension credential is associated with fd-service user. Before adding credentials for fd-user key store, perform the following steps to create a key store: 

1. Log in to your AEM Author instance as an Administrator.
1. Go to **[!UICONTROL Tools]**> **[!UICONTROL Security]**>**[!UICONTROL Users]**.
1. Scroll down the list of users until you find fd-service user account.
1. Click **[!UICONTROL fd-service]** user.
1. Click keystore tab.
1. Click **[!UICONTROL Create KeyStore]**.
1. Set the KeyStore Access Password and save your settings to create the KeyStore password.

After creating the key-store, add credentials to fd-service user. The following video explains the steps: 

>[!VIDEO](https://images-tv.adobe.com/mpcv3/5577/8db8e554-f04b-4fae-8108-b9b5e0eb03ad_1627925794.854x480at800_h264.mp4)

The following command list the details of the pfx file. Before running the command, navigate to the directory that contains the .pfx file.

`keytool -v -list -storetype pkcs12 -keystore [name of your .pfx file]`

For example, keytool -v -list -storetype pkcs12 -keystore 1005566.pfx where 1005566.pfx is the name of my pfx file

<!-- ### Remove usage rights from existing rights-enabled PDF documents

Remove usage rights from existing rights-enabled PDF documents before applying usage rights with latest credentials. You can remove the usage rights for a document by invoking the removeUsageRights API from within the docAssuranceServiceAPI. For detailed information, see [Remove Usage Rights](/help/forms/using/aem-document-services-programmatically.md#removing-usage-rights) document.

#### Apply the usage rights to PDF documents 

To apply usage rights in an AEM Forms on OSGi environment, Create custom OSGi service to usage rights to the documents. You can also create a servlet with a POST method to return the reader extended PDF to the user. For detailed instructions, see [Applying Reader Extensions](https://experienceleague.adobe.com/docs/experience-manager-learn/forms/document-services/apply-reader-extension-rights-to-pdf.html?lang=nl-NL).  -->
