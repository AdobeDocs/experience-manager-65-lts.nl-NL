---
title: XMP Utilities Service Java APIQuick Start (SOAP)
description: Met de XMP Utilities-service kunt u XMP-metagegevens exporteren en importeren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,AEM Forms on JEE
hide: true
hidefromtoc: true
exl-id: 6c2bdfc3-0f7b-4d53-b17e-f4cd11ab40ea
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '232'
ht-degree: 0%

---

# XMP Utilities Service Java API Quick Start (SOAP) {#xmp-utilities-service-java-apiquick-start-soap}

De volgende snelstarthandleidingen zijn beschikbaar voor de service XMP Utilities.

[Snel starten (SOAP-modus): XMP-metagegevens exporteren met de Java API](xmp-utilities-service-java-api.md#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api)

[Snel starten (SOAP-modus): XMP-metagegevens importeren met de Java API](xmp-utilities-service-java-api.md#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api)

AEM Forms-bewerkingen kunnen worden uitgevoerd met behulp van de API met sterk getypte AEM Forms en de verbindingsmodus moet zijn ingesteld op SOAP.

>[!NOTE]
>
>Snel aan de slag met Programmeren met AEM-formulieren is gebaseerd op de Forms-server als u een ander besturingssysteem gebruikt, zoals UNIX, vervangt Windows-specifieke paden door paden die worden ondersteund door het desbetreffende besturingssysteem. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP-modus): XMP-metagegevens exporteren met de Java API {#quick-start-soap-mode-exporting-xmp-metadata-using-the-java-api}

In het volgende codevoorbeeld worden XMP-metagegevens opgehaald, geïnspecteerd en opgeslagen. (Zie [ het Uitvoeren Meta-gegevens van de Documenten van PDF ](/help/forms/developing/xmp-utilities.md#exporting-metadata-from-pdf-documents).)

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-pdfutility-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms Java library files" in Programming
     * with AEM Forms
     */
 import com.adobe.livecycle.xmputility.*;
 import com.adobe.livecycle.xmputility.client.*;
 import java.util.*;
 import java.io.*;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class ExportMetadata
 {
     public static void main(String[] args)
     {
         try
         {
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory instance
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
 
             // Create a XMP Utility client
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory);
 
             // Specify a PDF document whose metadata is to be exported
             FileInputStream fileInputStream = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inDoc = new Document(fileInputStream);
 
             // Export the XMP metadata object
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(inDoc);
 
             // Inspect the XMP metadata object (retrieve the document?s author in this case)
             String name = myXmp.getAuthor();
             System.out.println("The document?s author is " + name);
 
             // Export the XMP metadata to an XML file
             Document outDoc = xmpUt.exportXMP(inDoc);
             File xmpFile = new File("c:\\LoanMetaData.xml");
             outDoc.copyToFile(xmpFile);
         }
         catch (Exception e)
         {
             System.out.println("Error occurred: " + e.getMessage());
         }
     }
 }
 
```

## Snel starten (SOAP-modus): XMP-metagegevens importeren met de Java API {#quick-start-soap-mode-importing-xmp-metadata-using-the-java-api}

In het volgende codevoorbeeld worden XMP-metagegevens geïmporteerd en wordt het nieuwe PDF-bestand op schijf opgeslagen. Het PDF-document is gebaseerd op een PDF-bestand met de naam Loan.pdf. Het document van XML dat de meta-gegevens bevat om in het document van PDF in te voeren is gebaseerd op een dossier van XML genoemd *LoanMetaData.xml*. Voor informatie over dit dossier van XML, zie [ het Invoeren Meta-gegevens in de Documenten van PDF ](/help/forms/developing/xmp-utilities.md#importing-metadata-into-pdf-documents).

```java
 /*
     * This Java Quick Start uses the following JAR files
     * 1. adobe-pdfutility-client.jar
     * 2. adobe-livecycle-client.jar
     * 3. adobe-usermanager-client.jar
    * 4. activation.jar (required for SOAP mode)
    * 5. axis.jar (required for SOAP mode)
    * 6. commons-codec-1.3.jar (required for SOAP mode)
    * 7. commons-collections-3.2.jar  (required for SOAP mode)
    * 8. commons-discovery.jar (required for SOAP mode)
    * 9. commons-logging.jar (required for SOAP mode)
    * 10. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
    * 11. jaxen-1.1-beta-9.jar (required for SOAP mode)
    * 12. jaxrpc.jar (required for SOAP mode)
    * 13. log4j.jar (required for SOAP mode)
    * 14. mail.jar (required for SOAP mode)
    * 15. saaj.jar (required for SOAP mode)
    * 16. wsdl4j.jar (required for SOAP mode)
    * 17. xalan.jar (required for SOAP mode)
    * 18. xbean.jar (required for SOAP mode)
    * 19. xercesImpl.jar (required for SOAP mode)
     *
     * The JBoss files must be kept in the jboss\client folder. You can copy the client folder to
     * your local development environment and then include the 3 JBoss JAR files in your class path
     *
     * These JAR files are in the following path:
     * <install directory>/sdk/client-libs/common
     *
     *
     * <install directory>/jboss/bin/client
     *
     * If you want to invoke a remote Forms Server instance and there is a
     * firewall between the client application and the server, then it is
     * recommended that you use the SOAP mode. When using the SOAP mode,
     * you have to include additional JAR files in the following
     * path
     * <install directory>/sdk/client-libs/thirdparty
     *
     * For information about the SOAP
     * mode and the additional JAR files that need to be included,
     * see "Setting connection properties" in Programming
     * with AEM Forms
     *
     * For complete details about the location of the AEM Forms JAR files,
     * see "Including AEM Forms Java library files" in Programming
     * with AEM Forms
     */
 import com.adobe.livecycle.xmputility.*;
 import com.adobe.livecycle.xmputility.client.*;
 import java.util.*;
 import java.io.*;
 import com.adobe.idp.Document;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class ImportMetadata
 {
     public static void main(String[] args)
     {
         try
         {
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory instance
             ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a XMP Utility client
             XMPUtilityServiceClient xmpUt = new XMPUtilityServiceClient(factory);
 
             //Specify a PDF document into which XMP metadata is imported
             FileInputStream filePDF = new FileInputStream("C:\\Adobe\Loan.pdf");
             Document inDoc = new Document(filePDF);
 
             //Specify an XML file containing XMP metadata to import
             FileInputStream fileXML = new FileInputStream("C:\\Adobe\LoanMetaData.xml");
             Document xmpDoc = new Document(fileXML );
 
             //Import the XMP metadata
             Document outDoc = xmpUt.importXMP(inDoc, xmpDoc);
 
             //Inspect the XMP metadata object (retrieve the document?s author in this case)
             XMPUtilityMetadata myXmp = xmpUt.exportMetadata(outDoc);
             String name = myXmp.getAuthor();
             System.out.println("The document?s author is " + name);
 
             //Save the PDF document containing the new metadata
             File pdfFile = new File("c:\\Adobe\LoanWithMetadata.pdf");
             outDoc.copyToFile(pdfFile);
         }
         catch (Exception e)
         {
             System.out.println("Error occurred: " + e.getMessage());
         }
     }
 }
```
