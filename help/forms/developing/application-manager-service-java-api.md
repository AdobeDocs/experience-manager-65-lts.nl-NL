---
title: Application Manager Service JavaAPI Quick Start (SOAP)
description: Application Manager Service JavaAPI Quick Start (SOAP)
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
exl-id: 4b7d417f-6480-479e-9b8d-bcf2c9790a97
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 0%

---

# Application Manager Service JavaAPI Quick Start (SOAP) {#application-manager-service-javaapi-quick-start-soap}

Java API Quick Start (SOAP) is beschikbaar voor de service Application Manager.

[Snel starten: toepassingen implementeren met de Java API (SOAP)](application-manager-service-java-api.md#quick-start-soap-mode-deploying-applications-using-the-java-api)

[Snel starten: een toepassing verwijderen met de Java API (SOAP)](application-manager-service-java-api.md#quick-start-soap-mode-removing-an-application-using-the-java-api)

>[!NOTE]
>
>De API&#39;s van de toepassingsmanager ondersteunen alleen AEM Forms LCA-bestanden. LCA-bestanden van LiveCycle ES2 en ES4 worden niet ondersteund.

AEM Forms-bewerkingen kunnen worden uitgevoerd met behulp van de API met sterk getypte AEM Forms en de verbindingsmodus moet zijn ingesteld op SOAP.

>[!NOTE]
>
>Java API (SOAP) Quick Start in Programming with AEM forms is gebaseerd op de Forms als u een ander besturingssysteem gebruikt, zoals Unix, vervangt Windows-specifieke paden door paden die worden ondersteund door het betreffende besturingssysteem. Als u een andere J2EE-toepassingsserver gebruikt, moet u ook geldige verbindingseigenschappen opgeven. Zie [ Plaatsende verbindingseigenschappen ](/help/forms/developing/invoking-aem-forms-using-java.md#setting-connection-properties).

## Snel starten (SOAP-modus): Toepassingen implementeren met de Java API {#quick-start-soap-mode-deploying-applications-using-the-java-api}

Het volgende codevoorbeeld van Java voert een toepassing in die op een bestaand dossier LCA wordt gebaseerd genoemd *EncryptDocument.lca*.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-livecycle-client.jar
     * 2. adobe-usermanager-client.jar
     * 3. activation.jar (required for SOAP mode)
     * 4. axis.jar (required for SOAP mode)
     * 5. commons-codec-1.3.jar (required for SOAP mode)
     * 6. commons-collections-3.2.jar  (required for SOAP mode)
     * 7. commons-discovery.jar (required for SOAP mode)
     * 8. commons-logging.jar (required for SOAP mode)
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 11. jaxrpc.jar (required for SOAP mode)
     * 12. log4j.jar (required for SOAP mode)
     * 13. mail.jar (required for SOAP mode)
     * 14. saaj.jar (required for SOAP mode)
     * 15. wsdl4j.jar (required for SOAP mode)
     * 16. xalan.jar (required for SOAP mode)
     * 17. xbean.jar (required for SOAP mode)
     * 18. xercesImpl.jar (required for SOAP mode)
     * 19. adobe-workflow-client-sdk.jar
     * 20. adobe-applicationmanager-client-sdk.jar
 
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
     */
 
 import java.io.FileInputStream;
 import java.util.*;
 
 import com.adobe.idp.Document;
 import com.adobe.idp.applicationmanager.application.ApplicationStatus;
 import com.adobe.idp.applicationmanager.client.ApplicationManager;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class DeployApplication {
 
     public static void main(String[] args) {
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Get the AEM Forms application to deploy
             FileInputStream fileApp = new FileInputStream("C:\\Adobe\EncryptDocument.lca");
             Document lcApp = new Document(fileApp);
 
             //Create an ApplicationManager object
             ApplicationManager appManager = new ApplicationManager(myFactory);
 
             //Import the application into the production server
             ApplicationStatus appStatus = appManager.importApplicationArchive(lcApp);
             int status = appStatus.getStatusCode();
 
             //Determine if the application was successfully deployed
             if (status==1)
                     System.out.println("The application was successfully deployed");
             else
                     System.out.println("The application was not successfully deployed. The status is "+status);
         }
         catch(Exception e)
         {
             e.printStackTrace();
         }
     }
 }
 
```

## Snel starten (SOAP-modus): een toepassing verwijderen met de Java API {#quick-start-soap-mode-removing-an-application-using-the-java-api}

Het volgende de codevoorbeeld van Java verwijdert een toepassing genoemd *EncryptDocument*.

```java
 /*
     * This Java Quick Start uses the SOAP mode and contains the following JAR files
     * in the class path:
     * 1. adobe-livecycle-client.jar
     * 2. adobe-usermanager-client.jar
     * 3. activation.jar (required for SOAP mode)
     * 4. axis.jar (required for SOAP mode)
     * 5. commons-codec-1.3.jar (required for SOAP mode)
     * 6. commons-collections-3.2.jar  (required for SOAP mode)
     * 7. commons-discovery.jar (required for SOAP mode)
     * 8. commons-logging.jar (required for SOAP mode)
     * 9. dom3-xml-apis-2.5.0.jar (required for SOAP mode)
     * 10. jaxen-1.1-beta-9.jar (required for SOAP mode)
     * 11. jaxrpc.jar (required for SOAP mode)
     * 12. log4j.jar (required for SOAP mode)
     * 13. mail.jar (required for SOAP mode)
     * 14. saaj.jar (required for SOAP mode)
     * 15. wsdl4j.jar (required for SOAP mode)
     * 16. xalan.jar (required for SOAP mode)
     * 17. xbean.jar (required for SOAP mode)
     * 18. xercesImpl.jar (required for SOAP mode)
     * 19. adobe-workflow-client-sdk.jar
     * 20. adobe-applicationmanager-client-sdk.jar
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
     */
 
 
 import java.util.*;
 
 import com.adobe.idp.applicationmanager.application.Application;
 import com.adobe.idp.applicationmanager.application.ApplicationId;
 
 import com.adobe.idp.applicationmanager.client.ApplicationManager;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;
 import com.adobe.idp.dsc.clientsdk.ServiceClientFactoryProperties;
 
 public class RemoveApplication {
 
     public static void main(String[] args) {
 
 
         try{
             //Set connection properties required to invoke AEM Forms
             Properties connectionProps = new Properties();
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_DEFAULT_SOAP_ENDPOINT, "https://'[server]:[port]'");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_TRANSPORT_PROTOCOL,ServiceClientFactoryProperties.DSC_SOAP_PROTOCOL);
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_SERVER_TYPE, "JBoss");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_USERNAME, "administrator");
             connectionProps.setProperty(ServiceClientFactoryProperties.DSC_CREDENTIAL_PASSWORD, "password");
 
             //Create a ServiceClientFactory object
             ServiceClientFactory myFactory = ServiceClientFactory.createInstance(connectionProps);
 
             //Create a ComponentRegistryClient object
             ApplicationManager appManager = new ApplicationManager(myFactory);
 
             //Get all the deployed applications
             List allApps = appManager.getApplications();
 
             //Iterate through the applications
             Iterator iter= allApps.iterator();
             while (iter.hasNext()) {
 
              //Cast each element to an Application object
              Application myApplication  = (Application)iter.next();
              ApplicationId appID = myApplication.getApplicationId();
              String appName = appID.getApplicationName();
 
              System.out.println("The name of the AEM Forms application is "+ appID.getApplicationName());
              //Determine the name of the application
              if (appName.compareTo("EncryptDocument")==0)
              {
                  //Remove the application
                 appManager.removeApplication(appID);
                 System.out.println("The  "+ appID.getApplicationName() +" application was removed.");
              }
         }
         }
         catch(Exception e)
             {
             e.printStackTrace();
             }
     }
 }
 
```
