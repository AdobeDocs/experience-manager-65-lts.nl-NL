---
title: AEM Forms verbinden met Adobe LiveCycle
description: Met de Adobe Experience Manager (AEM) LiveCycle-connector kunt u LiveCycle ES4 Acrobat Services starten vanuit AEM-apps en -workflows.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: Configuration
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Interactive Communication
exl-id: f6530bd3-16cd-4d6b-b92b-6c96f01f1939
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1026'
ht-degree: 0%

---

# AEM Forms verbinden met Adobe LiveCycle {#connecting-aem-forms-with-adobe-livecycle}

De Adobe Experience Manager (AEM) LiveCycle-aansluiting maakt het naadloos oproepen van Adobe LiveCycle ES4 Acrobat Services mogelijk vanuit AEM-webapps en -workflows. LiveCycle biedt een rijke client-SDK, waarmee clienttoepassingen LiveCycle-services kunnen starten met Java™ API&#39;s. AEM LiveCycle Connector vereenvoudigt het gebruik van deze API&#39;s in de OSGi-omgeving.

## AEM-server verbinden met Adobe LiveCycle {#connecting-aem-server-to-adobe-livecycle}

De Schakelaar van AEM LiveCycle maakt deel uit van het [&#x200B; toe:voegen-op pakket van AEM Forms &#x200B;](/help/forms/using/installing-configuring-aem-forms-osgi.md). Nadat u het AEM Forms-invoegpakket hebt geïnstalleerd, voert u de volgende stappen uit, zodat u details van de LiveCycle-server kunt toevoegen aan de AEM-webconsole.

1. Zoek in AEM Web Console Configuration Manager de Adobe LiveCycle Client SDK configuratiecomponent.
1. Klik op de component zodat u de URL van de configuratieserver, de gebruikersnaam en het wachtwoord kunt bewerken.
1. Herzie de montages en klik **sparen**.

Hoewel de eigenschappen vanzelfsprekend zijn, zijn de belangrijkste:

* **Server URL** - specificeert URL aan de server LiveCycle. Start AEM met de volgende JVM als u wilt dat LiveCycle en AEM communiceren via https

  ```java
  argument
   -Djavax.net.ssl.trustStore=<<em>path to LC keystore</em>>
  ```

  -optie.

* **Gebruikersnaam** - specificeert de gebruikersnaam van de rekening die wordt gebruikt om communicatie tussen AEM en LiveCycle te vestigen. Het account is een LiveCycle-gebruikersaccount die gemachtigd is om Acrobat Services te starten.
* **Wachtwoord** - specificeert het wachtwoord.
* **Naam van de Dienst** - specificeert de diensten die begonnen zijn gebruikend de gebruikersgeloofsbrieven die op de gebieden van de Gebruikersbenaming en van het Wachtwoord worden verstrekt. Standaard worden geen referenties doorgegeven tijdens het starten van LiveCycle-services.

## Documentservices starten {#starting-document-services}

Clienttoepassingen kunnen LiveCycle-services programmatisch starten met een Java™ API, webservices, Remoting en REST. Voor Java™-clients kan de toepassing de LiveCycle SDK gebruiken. LiveCycle SDK biedt een Java™ API waarmee deze services op afstand kunnen worden gestart. Als u bijvoorbeeld een Microsoft® Word-document wilt converteren naar PDF, start de client GeneratePDFService. De aanroepingsstroom bestaat uit de volgende stappen:

1. Maak een ServiceClientFactory-instantie.
1. Elke service biedt een clientklasse. Om de dienst te beginnen, creeer een cliëntgeval van de dienst.
1. Start de service en verwerkt het resultaat.

AEM LiveCycle Connector vereenvoudigt de stroom door deze cliëntinstanties als diensten bloot te stellen OSGi die kunnen worden betreden gebruikend standaardOSGi middelen. De LiveCycle-aansluiting biedt de volgende functies:

* De instanties van de cliënt als Dienst OSGi: De cliënten die als bundels worden verpakt OSGI zijn vermeld in de [&#x200B; de lijst van de Diensten van Acrobat &#x200B;](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p) sectie. Elke cliëntjar registreert de cliëntinstantie als dienst OSGi met de Registratie van de Dienst OSGi.
* Doorgave gebruikersreferenties: de verbindingsgegevens die nodig zijn om verbinding te maken met de LiveCycle-server worden centraal beheerd.
* ServiceClientFactory Service: om de processen te starten, heeft de clienttoepassing toegang tot de ServiceClientFactory-instantie.

### Beginnend via de Verwijzingen van de Dienst van OSGi Registratie van de Dienst {#starting-via-service-references-from-osgi-service-registry}

Voer de volgende stappen uit om een blootgestelde service te starten vanuit AEM:

1. Geweven afhankelijkheden bepalen. Voeg de afhankelijkheid van de vereiste clientjar toe aan het gemaakte pom.xml-bestand. Voeg minstens afhankelijkheid toe aan adobe-livecycle-client en adobe-usermanager-client-jars.

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-livecycle-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-usermanager-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-cq-integration-api</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

   Om de dienst te beginnen, voeg een overeenkomstige Geweven gebiedsdeel voor de dienst toe. Voor de lijst van gebiedsdelen, zie [&#x200B; Lijst van de Diensten van Acrobat &#x200B;](/help/forms/using/aem-livecycle-connector.md#p-document-services-list-p). Voeg voor de service PDF genereren bijvoorbeeld de volgende afhankelijkheid toe:

   ```xml
   <dependency>
     <groupId>com.adobe.livecycle</groupId>
     <artifactId>adobe-generatepdf-client</artifactId>
     <version>11.0.0</version>
   </dependency>
   ```

1. Verkrijg de de dienstverwijzing. Krijg een handvat aan de de dienstinstantie. Als u een klasse Java™ schrijft, kunt u de Aantekeningen van de Diensten van de Verklarende gebruiken.

   ```java
   import com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient;
   import com.adobe.livecycle.generatepdf.client.CreatePDFResult;
   import com.adobe.idp.Document;
   
   @Reference
   GeneratePdfServiceClient generatePDF;
   ...
   
   Resource r = resourceResolver.getResource("/path/tp/docx");
   Document sourceDoc = new Document(r.adaptTo(InputStream.class));
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

   Met het bovenstaande codefragment wordt de createPDF API van GeneratePDFServiceClient gestart om een document naar PDF te converteren. U kunt een gelijkaardige aanroeping in JSP uitvoeren gebruikend de volgende code. Het belangrijkste verschil is dat de volgende code Sling ScriptHelper gebruikt om tot GeneratePdfServiceClient toegang te hebben.

   ```jsp
   <%@ page import="com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient" %>
   <%@ page import="com.adobe.livecycle.generatepdf.client.CreatePDFResult" %>
   <%@ page import="com.adobe.idp.Document" %>
   
   GeneratePdfServiceClient generatePDF = sling.getService(GeneratePdfServiceClient.class);
   Document sourceDoc = ...
   CreatePDFResult result = generatePDF.createPDF2(
                       sourceDoc,
                       extension, //inputFileExtension
                       null, //fileTypeSettings
                       null, //pdfSettings
                       null, //securitySettings
                       settingsDoc, //settingsDoc
                       null //xmpDoc
               );
   ```

### Starten via ServiceClientFactory {#starting-via-serviceclientfactory}

De klasse ServiceClientFactory wordt soms vereist. U hebt bijvoorbeeld ServiceClientFactory nodig om processen aan te roepen.

```java
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider;
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory;

@Reference
ServiceClientFactoryProvider scfProvider;

...
ServiceClientFactory scf = scfProvider.getDefaultServiceClientFactory();
...
```

## Ondersteuning voor RunAs {#runas-support}

Bijna elke Acrobat Services in LiveCycle vereisen verificatie. U kunt om het even welke volgende opties gebruiken om deze diensten te beginnen zonder expliciete geloofsbrieven in de code te verstrekken:

### Configuratie Lijst van gewenste personen {#allowlist-configuration}

De configuratie van LiveCycle Client SDK bevat een instelling voor servicenamen. Deze configuratie is een lijst van de diensten waarvoor de aanroepingslogica een beheerderreferentie uit de doos gebruikt. Als u bijvoorbeeld DirectoryManager-services (onderdeel van de gebruikersbeheer-API) aan deze lijst toevoegt, kan elke clientcode de service rechtstreeks gebruiken. Bovendien geeft de aanroepingslaag automatisch de geconfigureerde gegevens door als onderdeel van de aanvraag die naar de LiveCycle-server is verzonden.

### RunAsManager {#runasmanager}

Als deel van de integratie, wordt de nieuwe dienst RunAsManager verstrekt. Hiermee kunt u via programmacode een referentie beheren die moet worden gebruikt wanneer u de LiveCycle-server aanroept.

```java
import com.adobe.livecycle.dsc.clientsdk.security.PasswordCredential;
import com.adobe.livecycle.dsc.clientsdk.security.PrivilegedAction;
import com.adobe.livecycle.dsc.clientsdk.security.RunAsManager;
import com.adobe.idp.dsc.registry.component.ComponentRegistry;

@Reference
private RunAsManager runAsManager;

List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
            public List<Component> run() {
                return componentRegistry.getComponents();
            }
        });
assertNotNull(components);
```

Als u een verschillende referentie wilt overgaan, kunt u de overbelaste methode gebruiken die een instantie PasswordCredential neemt.

```java
PasswordCredential credential = new PasswordCredential("administrator","password");
List<Component> components = runAsManager.doPrivileged(new PrivilegedAction<List<Component>>() {
    public List<Component> run() {
        return componentRegistry.getComponents();
    }
},credential);
```

### InvocationRequest, eigenschap {#invocationrequest-property}

Als u een proces roept of direct gebruik maakt van de klasse ServiceClientFactory, en een InvocationRequest creeert, kunt u een bezit specificeren om erop te wijzen dat de aanroepingslaag gevormde geloofsbrieven zou moeten gebruiken.

```java
import com.adobe.idp.dsc.InvocationResponse
import com.adobe.idp.dsc.InvocationRequest
import com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider
import com.adobe.idp.dsc.clientsdk.ServiceClientFactory
import com.adobe.livecycle.dsc.clientsdk.InvocationProperties

ServiceClientFactoryProvider scfp = sling.getService(ServiceClientFactoryProvider.class)
ServiceClientFactory serviceClientFactory = scfp.getDefaultServiceClientFactory()
InvocationRequest ir = serviceClientFactory.createInvocationRequest("sample/LetterSubmissionProcess", "invoke", new HashMap(), true);

//Here we are invoking the request with system user
ir.setProperty(InvocationProperties.INVOKER_TYPE,InvocationProperties.INVOKER_TYPE_SYSTEM)

InvocationResponse response = serviceClientFactory.getServiceClient().invoke(ir);
```

## Lijst met Acrobat-services {#document-services-list}

### Adobe LiveCycle Client SDK API-bundel {#adobe-livecycle-client-sdk-api-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.um.api.AuthenticationManager
* com.adobe.idp.um.api.DirectoryManager
* com.adobe.idp.um.api.AuthorizationManager
* com.adobe.idp.dsc.registry.service.ServiceRegistry
* com.adobe.idp.dsc.registry.component.ComponentRegistry

#### Geweven afhankelijkheden {#maven-dependencies}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-client</artifactId>
  <version>11.0.0</version>
</dependency>
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-usermanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Client SDK-bundel {#adobe-livecycle-client-sdk-bundle}

De volgende services zijn beschikbaar:

* com.adobe.livecycle.dsc.clientsdk.security.RunAsManager
* com.adobe.livecycle.dsc.clientsdk.ServiceClientFactoryProvider

#### Geweven afhankelijkheden {#maven-dependencies-1}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-livecycle-cq-integration-api</artifactId>
  <version>1.1.10</version>
</dependency>
```

### Adobe LiveCycle TaskManager Client-bundel {#adobe-livecycle-taskmanager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.taskmanager.dsc.client.task.TaskManager
* com.adobe.idp.taskmanager.dsc.client.TaskManagerQueryService
* com.adobe.idp.taskmanager.dsc.client.queuemanager.QueueManager
* com.adobe.idp.taskmanager.dsc.client.emailsettings.EmailSettingService
* com.adobe.idp.taskmanager.dsc.client.endpoint.TaskManagerEndpointClient
* com.adobe.idp.taskmanager.dsc.client.userlist.UserlistService

#### Geweven afhankelijkheden {#maven-dependencies-2}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-taskmanager-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Workflow Client Bundle {#adobe-livecycle-workflow-client-bundle}

De volgende service is beschikbaar:

* com.adobe.idp.workflow.client.WorkflowServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-3}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-workflow-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle PDF Generator Client-bundel {#adobe-livecycle-pdf-generator-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.generatepdf.client.GeneratePdfServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-4}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-generatepdf-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Application Manager Client-bundel {#adobe-livecycle-application-manager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.idp.applicationmanager.service.ApplicationManager
* com.adobe.livecycle.applicationmanager.client.ApplicationManager
* com.adobe.livecycle.design.service.DesigntimeService

#### Geweven afhankelijkheden {#maven-dependencies-5}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-applicationmanager-client-sdk</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Assembler Client-bundel {#adobe-livecycle-assembler-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.assembler.client.AssemblerServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-6}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-assembler-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Form Data Integration Client-bundel {#adobe-livecycle-form-data-integration-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.formdataintegration.client.FormDataIntegrationClient

#### Geweven afhankelijkheden {#maven-dependencies-7}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-formdataintegration-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Forms Client-bundel {#adobe-livecycle-forms-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.formsservice.client.FormsServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-8}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-forms-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Output Client-bundel {#adobe-livecycle-output-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.output.client.OutputClient

#### Geweven afhankelijkheden {#maven-dependencies-9}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-output-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Reader Extensions-clientbundel {#adobe-livecycle-reader-extensions-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.readerextensions.client.ReaderExtensionsServiceClient

#### Geweven afhankelijkheden {#maven-dependencies-10}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-reader-extensions-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Rights Manager Client-bundel {#adobe-livecycle-rights-manager-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.livecycle.rightsmanagement.client.DocumentManager
* com.adobe.livecycle.rightsmanagement.client.EventManager
* com.adobe.livecycle.rightsmanagement.client.ExternalUserManager
* com.adobe.livecycle.rightsmanagement.client.LicenseManager
* com.adobe.livecycle.rightsmanagement.client.WatermarkManager
* com.adobe.livecycle.rightsmanagement.client.PolicyManager
* com.adobe.livecycle.rightsmanagement.client.AbstractPolicyManager

#### Geweven afhankelijkheden {#maven-dependencies-11}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-rightsmanagement-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Signatures Client-bundel {#adobe-livecycle-signatures-client-bundle}

De volgende service is beschikbaar:

* com.adobe.livecycle.signatures.client.SignatureServiceClientInterface

#### Geweven afhankelijkheden {#maven-dependencies-12}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-signatures-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Truststore Client-bundel {#adobe-livecycle-truststore-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.truststore.dsc.TrustConfigurationService
* com.adobe.truststore.dsc.CRLService
* com.adobe.truststore.dsc.CredentialService
* com.adobe.truststore.dsc.CertificateService

#### Geweven afhankelijkheden {#maven-dependencies-13}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-truststore-client</artifactId>
  <version>11.0.0</version>
</dependency>
```

### Adobe LiveCycle Repository Client-bundel {#adobe-livecycle-repository-client-bundle}

De volgende services zijn beschikbaar:

* com.adobe.repository.bindings.ResourceRepository
* com.adobe.repository.bindings.ResourceSynchronizer

#### Geweven afhankelijkheden {#maven-dependencies-14}

```xml
<dependency>
  <groupId>com.adobe.livecycle</groupId>
  <artifactId>adobe-repository-client</artifactId>
  <version>11.0.0</version>
</dependency>
```
