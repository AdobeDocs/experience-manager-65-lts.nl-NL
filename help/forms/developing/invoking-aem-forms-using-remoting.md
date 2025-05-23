---
title: AEM Forms aanroepen met Remoting
description: Gebruik Remoting om een AEM Forms-proces aan te roepen om processen die in Workbench zijn gemaakt, aan te roepen. U kunt een AEM Forms-proces aanroepen vanuit een clienttoepassing die met Flex is gebouwd.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: coding
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations,Workbench
hide: true
hidefromtoc: true
exl-id: 37f5efaa-db0b-4035-987d-4140fc5a97be
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '4604'
ht-degree: 0%

---

# AEM Forms aanroepen met Remoting {#invoking-aem-forms-using-remoting}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op milieu JEE.**

In Workbench gemaakte processen kunnen worden aangeroepen door Remoting te gebruiken. Dat wil zeggen dat u een AEM Forms-proces kunt aanroepen vanuit een clienttoepassing die met Flex is gebouwd. Deze eigenschap is gebaseerd op de Diensten van Gegevens.

>[!NOTE]
>
>Als u Remoting gebruikt, wordt u aangeraden processen aan te roepen die in Workbench zijn gemaakt in plaats van AEM Forms-services. Het is echter mogelijk om AEM Forms-diensten rechtstreeks aan te roepen. (Zie PDF-documenten coderen met Remoting op AEM Forms Developer Center.)

>[!NOTE]
>
>Als een AEM Forms-service niet is geconfigureerd om anonieme toegang toe te staan, resulteren aanvragen van een Flex-client in een webbrowserprobleem. De gebruiker moet gebruikersnaam en wachtwoord invoeren.

Het volgende kortstondige AEM Forms-proces, met de naam `MyApplication/EncryptDocument` , kan worden aangeroepen met Remoting. (Voor informatie over dit proces zoals zijn input en outputwaarden, zie [ Kort levend procesvoorbeeld ](/help/forms/developing/aem-forms-processes.md).)

![ iu_iu_encryptdocumentprocess2 ](assets/iu_iu_encryptdocumentprocess2.png)

>[!NOTE]
>
>Als u een AEM Forms-proces wilt aanroepen met een Flex-toepassing, moet u ervoor zorgen dat een extern eindpunt is ingeschakeld. Door gebrek, wordt een remoting eindpunt toegelaten wanneer u een proces opstelt.

Wanneer dit proces wordt aangeroepen, worden de volgende handelingen uitgevoerd:

1. Verkrijgt het onbeveiligde PDF-document dat als invoerwaarde wordt doorgegeven. Deze handeling is gebaseerd op de bewerking `SetValue` . De naam van de invoerparameter is `inDoc` en het gegevenstype is `document` . (Het gegevenstype van `document` is een beschikbaar gegevenstype vanuit Workbench.)
1. Codeert het PDF-document met een wachtwoord. Deze handeling is gebaseerd op de bewerking `PasswordEncryptPDF` . De naam van de uitvoerwaarde voor dit proces is `outDoc` en vertegenwoordigt het met een wachtwoord gecodeerde PDF-document. Het gegevenstype van outDoc is `document`.
1. Hiermee slaat u het met wachtwoord gecodeerde PDF-document op als een PDF-bestand naar het lokale bestandssysteem. Deze handeling is gebaseerd op de bewerking `WriteDocument` .

>[!NOTE]
>
>Het `MyApplication/EncryptDocument` -proces is niet gebaseerd op een bestaand AEM Forms-proces. Als u de codevoorbeelden wilt volgen, maakt u een proces met de naam `MyApplication/EncryptDocument` met Workbench.

>[!NOTE]
>
>Voor informatie over het gebruiken van het Verwijderen om een langdurig proces aan te halen, zie [ het Aanhalen van mens-Centric langlevende Processen ](/help/forms/developing/invoking-human-centric-long-lived.md#invoking-human-centric-long-lived-processes).

**zie ook**

[Het AEM Forms Flex-bibliotheekbestand opnemen](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Documenten verwerken met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Client-toepassingen verifiëren die zijn gemaakt met Flex](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Beveiligde documenten doorgeven om processen aan te roepen met Verwijderen](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

[Aanroepen van aangepaste componentenservices met Remoting](invoking-aem-forms-using-remoting.md#invoking-custom-component-services-using-remoting)

[Een clienttoepassing maken die is gebouwd met Flex en die een menselijk-centrisch proces van lange duur aanroept](/help/forms/developing/invoking-human-centric-long-lived.md#creating-a-client-application-built-with-flex-that-invokes-a-human-centric-long-lived-process)

[Flash Builder-toepassingen maken die SSO-verificatie uitvoeren met HTTP-tokens](/help/forms/developing/creating-flash-builder-applications-perform.md#creating-flash-builder-applications-that-perform-sso-authentication-using-http-tokens)

<!-- For information on how to display process data in a Flex graph control, see [Displaying AEM Forms process data in Flex graphs](https://www.adobe.com/devnet/livecycle/articles/populating_flexcontrols.html). This URL is 404. No suitable replacement URL was found after a search. Do not make this link live if it is dead! -->

>[!NOTE]
>
>*ben zeker om het crossdomain.xml- dossier in de juiste plaats te plaatsen. Bijvoorbeeld, veronderstellend dat u AEM Forms op JBoss opstelde, plaats dit dossier in de volgende plaats: &lt;install_directory>\Adobe_Experience_Manager_forms\jboss\server\lc_turnkey\deploy\jboss-web.deployer\ROOT.war.*

## Het AEM Forms Flex-bibliotheekbestand opnemen {#including-the-aem-forms-flex-library-file}

Als u AEM Forms-processen programmatisch wilt aanroepen met Remoting, voegt u het bestand adobe-remoting-provider.swc toe aan het klassepad van uw Flex-project. Dit SWC-bestand bevindt zich op de volgende locatie:

* *&lt;install_directory>\Adobe_Experience_Manager_forms\sdk\misc\DataServices\Client-Libraries*

  waar &lt;*install_directory*> de folder is waar AEM Forms geïnstalleerd is.

**zie ook**

[AEM Forms aanroepen met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Documenten verwerken met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Client-toepassingen verifiëren die zijn gemaakt met Flex](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

## Documenten verwerken met Verwijderen {#handling-documents-with-remoting}

Een van de belangrijkste niet-primitieve Java™-typen die in AEM Forms wordt gebruikt, is de `com.adobe.idp.Document` -klasse. Een document is doorgaans vereist om een AEM Forms-bewerking aan te roepen. Het is voornamelijk een PDF-document, maar kan ook andere documenttypen bevatten, zoals SWF, HTML, XML of een DOC-bestand. (Zie [ het overgaan van gegevens tot de diensten van AEM Forms gebruikend Java API ](/help/forms/developing/invoking-aem-forms-using-java.md#passing-data-to-aem-forms-services-using-the-java-api).)

Een clienttoepassing die met Flex is gebouwd, kan niet rechtstreeks een document aanvragen. U kunt Adobe Reader bijvoorbeeld niet starten om een URL aan te vragen waarmee een PDF-bestand wordt gemaakt. Verzoeken om documenttypen, zoals PDF- en Microsoft® Word-documenten, retourneren een resultaat dat een URL is. Het is de verantwoordelijkheid van de klant om de inhoud van de URL weer te geven. Met de service Documentbeheer kunt u informatie over de URL en het inhoudstype genereren. Verzoeken om XML-documenten retourneren het volledige XML-document in het resultaat.

### Een document doorgeven als een invoerparameter {#passing-a-document-as-an-input-parameter}

Een clienttoepassing die met Flex is gebouwd, kan een document niet rechtstreeks doorgeven aan een AEM Forms-proces. In plaats daarvan gebruikt de clienttoepassing een instantie van de ActionScript-klasse `mx.rpc.livecycle.DocumentReference` om invoerparameters door te geven aan een bewerking die een `com.adobe.idp.Document` -instantie verwacht. Een Flex-clienttoepassing heeft verschillende opties voor het instellen van een `DocumentReference` -object:

* Wanneer het document op de server is en de bestandslocatie bekend is, stelt u de eigenschap referenceType van het object DocumentReference in op REF_TYPE_FILE. Stel de eigenschap fileRef in op de locatie van het bestand, zoals in het volgende voorbeeld:

```java
 ... var docRef: DocumentReference = new DocumentReference(); 
 docRef.referenceType = DocumentReference.REF_TYPE_FILE; 
 docRef.fileRef = "C:/install/adobe/cs2/How to Uninstall.pdf"; ...
```

* Wanneer het document zich op de server bevindt en u de URL kent, stelt u de eigenschap referenceType van het object DocumentReference in op REF_TYPE_URL. Stel de eigenschap url in op de URL, zoals in het volgende voorbeeld wordt getoond:

```java
... var docRef: DocumentReference = new DocumentReference(); 
docRef.referenceType = DocumentReference.REF_TYPE_URL; 
docRef.url = "https://companyserver:8080/DocumentManager/116/7855"; ...
```

* Als u een object DocumentReference wilt maken van een tekenreeks in de clienttoepassing, stelt u de eigenschap referenceType van het object DocumentReference in op REF_TYPE_INLINE. Stel de eigenschap text in op de tekst die u in het object wilt opnemen, zoals in het volgende voorbeeld wordt getoond:

```java
... var docRef: DocumentReference = new DocumentReference(); 
docRef.referenceType = DocumentReference.REF_TYPE_INLINE; 
docRef.text = "Text for my document";  // Optionally, you can override the server's default character set  // if necessary:  // docRef.charsetName=CharacterSetName  ...
```

* Als het document zich niet op de server bevindt, gebruikt u het verwijderbare uploadserver om een document te uploaden naar AEM Forms. Nieuw in AEM Forms is de mogelijkheid om beveiligde documenten te uploaden. Wanneer het uploaden van een veilig document, moet u een gebruiker gebruiken die het *Document heeft uploadt de rol van de Gebruiker van de Toepassing*. Zonder deze rol kan de gebruiker geen beveiligd document uploaden. U wordt aangeraden een beveiligd document met één aanmeldingsnaam te uploaden. (Zie [ het overgaan van veilige documenten om processen aan te halen gebruikend het Verwijderen ](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting).)

>[!NOTE]
>
>als AEM Forms zo is geconfigureerd dat onbeveiligde documenten kunnen worden geüpload, kunt u een gebruiker die niet over de gebruikersrol Document Upload Application beschikt, gebruiken om een document te uploaden. Een gebruiker kan ook beschikken over de machtiging Document uploaden. Als AEM Forms echter is geconfigureerd om alleen beveiligde documenten toe te staan, moet u ervoor zorgen dat de gebruiker beschikt over de rol Gebruiker van Document uploaden of de machtiging Uploaden document. (Zie [ Vormend AEM Forms om veilige en onveilige documenten ](invoking-aem-forms-using-remoting.md#configuring-aem-forms-to-accept-secure-and-unsecure-documents) goed te keuren.

U gebruikt standaard Flash-uploadmogelijkheden voor de opgegeven upload-URL: `https://SERVER:PORT/remoting/lcfileupload` . Vervolgens kunt u het object `DocumentReference` gebruiken wanneer een invoerparameter van het type `Document` wordt verwacht
` private function startUpload():void  {  fileRef.addEventListener(Event.SELECT, selectHandler);  fileRef.addEventListener("uploadCompleteData", completeHandler);  try  {   var success:Boolean = fileRef.browse();  }    catch (error:Error)  {   trace("Unable to browse for files.");  }  }      private function selectHandler(event:Event):void {  var request:URLRequest = new  URLRequest("https://SERVER:PORT/remoting/lcfileupload")  try   {   fileRef.upload(request);   }    catch (error:Error)   {   trace("Unable to upload file.");   }  }    private function completeHandler(event:DataEvent):void  {   var params:Object = new Object();   var docRef:DocumentReference = new DocumentReference();   docRef.url = event.data as String;   docRef.referenceType = DocumentReference.REF_TYPE_URL;  }` het Verwijderen Snel Begin gebruikt het Verwijderen uploadt servlet om een dossier van PDF tot het `MyApplication/EncryptDocument` proces over te gaan. (Zie [ Aanroepend een kortstondig proces door een onbeveiligd document over te gaan gebruikend (Vervangen voor de vormen van AEM) AEM Forms die ](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) verwijdert.)

```java
 
private
function startUpload(): void  { 
 fileRef.addEventListener(Event.SELECT, selectHandler); 
 fileRef.addEventListener("uploadCompleteData", completeHandler); 
 try  { 
  var success: Boolean = fileRef.browse(); 
 }  
 catch (error: Error)  { 
  trace("Unable to browse for files."); 
 } 
}   
private
function selectHandler(event: Event): void { 
 var request: URLRequest = new  URLRequest("https://SERVER:PORT/remoting/lcfileupload")  try  { 
  fileRef.upload(request); 
 }  
 catch (error: Error)  { 
  trace("Unable to upload file."); 
 } 
}  
private
function completeHandler(event: DataEvent): void  { 
 var params: Object = new Object(); 
 var docRef: DocumentReference = new DocumentReference(); 
 docRef.url = event.data as String; 
 docRef.referenceType = DocumentReference.REF_TYPE_URL; 
}
```

Het Verwijderen Snel Begin gebruikt het Verwijderen uploadt servlet om een dossier van PDF tot het `MyApplication/EncryptDocument` proces over te gaan. (Zie [ Aanroepend een kortstondig proces door een onbeveiligd document over te gaan gebruikend (Vervangen voor de vormen van AEM) AEM Forms die ](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting) verwijdert.)

### Een document terugsturen naar een clienttoepassing {#passing-a-document-back-to-a-client-application}

Een clienttoepassing ontvangt een object van het type `mx.rpc.livecycle.DocumentReference` voor een servicebewerking die een `com.adobe.idp.Document` -instantie als uitvoerparameter retourneert. Omdat een clienttoepassing werkt met ActionScript-objecten en niet met Java, kunt u een op Java gebaseerd Document-object niet teruggeven aan een Flex-client. In plaats daarvan genereert de server een URL voor het document en geeft de URL weer door aan de client. De eigenschap `referenceType` van het `DocumentReference` -object geeft aan of de inhoud zich in het `DocumentReference` -object bevindt of moet worden opgehaald van een URL in de eigenschap `DocumentReference.url` . De eigenschap `DocumentReference.contentType` geeft het type document op.

**zie ook**

[AEM Forms aanroepen met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Het AEM Forms Flex-bibliotheekbestand opnemen](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Client-toepassingen verifiëren die zijn gemaakt met Flex](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Beveiligde documenten doorgeven om processen aan te roepen met Verwijderen](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

## Een kortstondig proces aanroepen door een onbeveiligd document door te geven met Verwijderen {#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting}

Als u een AEM Forms-proces wilt aanroepen vanuit een toepassing die is gebouwd met Flex, voert u de volgende taken uit:

1. Maak een `mx:RemoteObject` -instantie.
1. Maak een `ChannelSet` -instantie.
1. Geef de vereiste invoerwaarden door.
1. Retourwaarden verwerken.

>[!NOTE]
>
>In deze sectie wordt besproken hoe u een AEM Forms-proces kunt aanroepen en een document kunt uploaden wanneer AEM Forms is geconfigureerd voor het uploaden van onbeveiligde documenten. Voor informatie over hoe te om processen van AEM Forms aan te halen en veilige documenten te uploaden en hoe te AEM Forms vormen om veilige en onveilige documenten goed te keuren, zie [ het overgaan veilige documenten om processen aan te halen gebruikend het Verwijderen ](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting).

**Creërend mx:instantie RemoteObject**

U maakt een `mx:RemoteObject` -instantie om een AEM Forms-proces aan te roepen dat in Workbench is gemaakt. Als u een `mx:RemoteObject` -instantie wilt maken, geeft u de volgende waarden op:

* **identiteitskaart:** de naam van de `mx:RemoteObject` instantie die het proces vertegenwoordigt om aan te halen.
* **bestemming:** de naam van het proces van AEM Forms om aan te halen. Als u bijvoorbeeld het `MyApplication/EncryptDocument` -proces wilt aanroepen, geeft u `MyApplication/EncryptDocument` op.
* **resultaat:** de naam van de methode van Flex die het resultaat behandelt.

Geef binnen de tag `mx:RemoteObject` een `<mx:method>` -tag op die de naam van de oproepmethode van het proces opgeeft. De naam van een Forms-oproepmethode is doorgaans `invoke` .

In het volgende codevoorbeeld wordt een instantie `mx:RemoteObject` gemaakt die het `MyApplication/EncryptDocument` -proces aanroept.

```java
 <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);">
          <mx:method name="invoke" result="handleExecuteInvoke(event)"/>
      </mx:RemoteObject>
```

**creeer een Kanaal aan AEM Forms**

Een clienttoepassing kan AEM Forms aanroepen door een kanaal op te geven in MXML of ActionScript, zoals in het volgende ActionScript-voorbeeld wordt getoond. Het kanaal moet een `AMFChannel`, `SecureAMFChannel`, `HTTPChannel` of `SecureHTTPChannel` zijn.

```java
     ...
     private function refresh():void{
         var cs:ChannelSet= new ChannelSet();
         cs.addChannel(new AMFChannel("my-amf",
             "https://yourlcserver:8080/remoting/messagebroker/amf"));
         EncryptDocument.setCredentials("administrator", "password");
         EncryptDocument.channelSet = cs;
     }
     ...
```

Wijs de `ChannelSet` -instantie toe aan het veld `mx:RemoteObject` instance&#39;s `channelSet` (zoals in het vorige codevoorbeeld). Over het algemeen importeert u de kanaalklasse in een importinstructie in plaats van de volledig gekwalificeerde naam op te geven wanneer u de methode `ChannelSet.addChannel` aanroept.

**het overgaan van inputwaarden**

Een in Workbench gemaakt proces kan nul of meer invoerparameters gebruiken en een uitvoerwaarde retourneren. Een clienttoepassing geeft invoerparameters binnen een `ActionScript` -object door met velden die overeenkomen met parameters die bij het AEM Forms-proces horen. Voor het kortstondige proces met de naam `MyApplication/EncryptDocument` is één invoerparameter met de naam `inDoc` vereist. De naam van de bewerking die door het proces wordt weergegeven, is `invoke` (de standaardnaam voor een kortstondig proces). (Zie [ het Aanhalen van AEM Forms die (voor de vormen van AEM wordt afgekeurd) AEM Forms verwijdert ](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting).)

In het volgende codevoorbeeld wordt een PDF-document doorgegeven aan het `MyApplication/EncryptDocument` -proces:

```java
     ...
     var params:Object = new Object();
 
     //Document is an instance of DocumentReference
     //that store an unsecured PDF document
     params["inDoc"] = pdfDocument;
 
     // Invoke an operation synchronously:
     EncryptDocument.invoke(params);
     ...
```

In dit codevoorbeeld is `pdfDocument` een `DocumentReference` -instantie die een onbeveiligd PDF-document bevat. Voor informatie over a `DocumentReference`, zie [ Behandelende documenten met (Vervangen voor de vormen van AEM) AEM Forms die ](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting) verwijdert.

**aanroepend een specifieke versie van de dienst**

U kunt een specifieke versie van een Forms-service aanroepen met behulp van een parameter `_version` in de parameterkaart van de aanroep. Als u bijvoorbeeld versie 1.2 van de service `MyApplication/EncryptDocument` wilt aanroepen:

```java
 var params:Object = new Object();
 params["inDoc"] = pdfDocument;
 params["_version"] = "1.2"
 var token:AsyncToken = echoService.echoString(params);
```

De parameter `version` moet een tekenreeks met één punt zijn. De waarden aan de linkerzijde, de belangrijkste versie, en juiste, minder belangrijke versie, van de periode moeten gehelen zijn. Als deze parameter niet wordt gespecificeerd, wordt de hoofd actieve versie aangehaald.

**Behandelend terugkeerwaarden**

AEM Forms-procesuitvoerparameters worden gedeserialiseerd naar ActionScript-objecten waaruit de clienttoepassing specifieke parameters op naam extraheert, zoals in het volgende voorbeeld wordt getoond. (De uitvoerwaarde van het `MyApplication/EncryptDocument` -proces krijgt de naam `outDoc` .)

```java
     ...
     var res:Object = event.result;
     var docRef:DocumentReference = res["outDoc"] as DocumentReference;
     ...
```

**aanroepend het proces MyApplication/EncryptDocument**

U kunt het `MyApplication/EncryptDocument` -proces activeren door de volgende stappen uit te voeren:

1. Maak een `mx:RemoteObject` -instantie via ActionScript of MXML. Zie Een instantie mx:RemoteObject maken.
1. Stel een `ChannelSet` -instantie in om te communiceren met AEM Forms en koppel deze aan de `mx:RemoteObject` -instantie. Zie Een kanaal naar AEM Forms maken.
1. Roep de methode `login` van ChannelSet of de methode `setCredentials` van de service aan om de waarde en het wachtwoord van de gebruikersidentificatie op te geven. (Zie [ Gebruikend enig teken-op ](invoking-aem-forms-using-remoting.md#using-single-sign-on).)
1. Vul een `mx.rpc.livecycle.DocumentReference` -instantie met een onbeveiligd PDF-document om het `MyApplication/EncryptDocument` -proces door te geven. (Zie [ het overgaan van een document als inputparameter ](invoking-aem-forms-using-remoting.md#passing-a-document-as-an-input-parameter).)
1. Codeer het PDF-document door de methode `invoke` van de instantie `mx:RemoteObject` aan te roepen. Geef `Object` door die de invoerparameter bevat (dit is het onbeveiligde PDF-document). Zie Invoerwaarden doorgeven.
1. Haal het met wachtwoord gecodeerde PDF-document op dat tijdens het proces wordt geretourneerd. Zie Retourwaarden afhandelen.

[Snel starten: Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](/help/forms/developing/invocation-api-quick-starts.md#quick-start-invoking-a-short-lived-process-by-passing-an-unsecure-document-using-deprecated-for-aem-forms-aem-forms-remoting)

## Client-toepassingen verifiëren die zijn gemaakt met Flex {#authenticating-client-applications-built-with-flex}

Er zijn verschillende manieren waarop AEM Forms User Manager een aanvraag Remoting uit een Flex-toepassing kan verifiëren, waaronder AEM Forms Single Sign-On via de centrale aanmeldingsservice, basisverificatie en aangepaste verificatie. Wanneer noch enige teken-op noch anonieme toegang wordt toegelaten, resulteert een verwijderend verzoek in of basisauthentificatie (het gebrek) of douaneauthentificatie.

De basisauthentificatie baseert zich op standaardJ2EE basisauthentificatie van de container van de Webtoepassing. Voor basisauthentificatie, veroorzaakt een fout van HTTP 401 een browser uitdaging. Dat betekent dat wanneer u probeert verbinding te maken met een Forms-toepassing met behulp van RemoteObject en zich nog niet hebt aangemeld bij de Flex-toepassing, de browser u om een gebruikersnaam en wachtwoord vraagt.

Voor douaneauthentificatie, verzendt de server een fout naar de cliënt om erop te wijzen dat de authentificatie wordt vereist.

>[!NOTE]
>
>Voor informatie over het uitvoeren van authentificatie gebruikend de tokens van HTTP, zie [ Creërend de toepassingen van de Bouwer van de Flits die authentificatie uitvoeren SSO gebruikend de tokens van HTTP ](/help/forms/developing/creating-flash-builder-applications-perform.md#creating-flash-builder-applications-that-perform-sso-authentication-using-http-tokens).

### Aangepaste verificatie gebruiken {#using-custom-authentication}

U laat douaneauthentificatie in beleidsconsole toe door de authentificatiemethode van Basis in Douane op het remoting eindpunt te veranderen. Als u aangepaste verificatie gebruikt, roept uw clienttoepassing de methode `ChannelSet.login` aan om u aan te melden en de methode `ChannelSet.logout` om zich af te melden.

>[!NOTE]
>
>In de vorige versie van AEM Forms hebt u referenties naar een doel verzonden door de methode `RemoteObject.setCredentials` aan te roepen. De methode `setCredentials` gaf de gegevens pas daadwerkelijk door aan de server als de component voor het eerst probeert verbinding te maken met de server. Daarom als de component een foutengebeurtenis uitbracht, kon u niet zeker zijn als de fout wegens een authentificatiefout, of om een andere reden gebeurde. De methode `ChannelSet.login` maakt verbinding met de server wanneer u deze aanroept, zodat u een verificatieprobleem direct kunt afhandelen. Hoewel u de methode `setCredentials` kunt blijven gebruiken, wordt aangeraden de methode `ChannelSet.login` te gebruiken.

Omdat de veelvoudige bestemmingen de zelfde kanalen, en het overeenkomstige voorwerp kunnen gebruiken ChannelSet, het programma openen aan één bestemmings login de gebruiker aan een andere bestemming die het zelfde kanaal of de kanalen gebruikt. Als twee componenten verschillende geloofsbrieven op het zelfde voorwerp toepassen ChannelSet, worden de laatste toegepaste geloofsbrieven gebruikt. Als meerdere componenten hetzelfde geverifieerde ChannelSet-object gebruiken, worden bij het aanroepen van de methode `logout` alle componenten uit de doelen uitgecheckt.

In het volgende voorbeeld worden de methoden `ChannelSet.login` en `ChannelSet.logout` gebruikt met een RemoteObject-besturingselement. Deze toepassing voert de volgende handelingen uit:

* Maakt een `ChannelSet` -object in de `creationComplete` -handler die de kanalen vertegenwoordigt die door de `RemoteObject` -component worden gebruikt.
* Geeft referenties door aan de server door de functie `ROLogin` aan te roepen als reactie op een klikgebeurtenis Button
* Gebruikt de component RemoteObject om een Koord naar de server te verzenden in antwoord op een Button klikgebeurtenis. De server retourneert dezelfde String terug naar de RemoteObject-component
* Gebruikt de resultaatgebeurtenis van de component RemoteObject om het Koord in een controle te tonen TextArea
* Hiermee wordt u afgemeld bij de server door de functie `ROLogout` aan te roepen als reactie op een klikgebeurtenis Button

```java
 <?xml version="1.0"?>
 <!-- security/SecurityConstraintCustom.mxml -->
 <mx:Application xmlns:mx="https://www.adobe.com/2006/mxml" width="100%"
     height="100%" creationComplete="creationCompleteHandler();">
 
     <mx:Script>
         <![CDATA[
             import mx.controls.Alert;
             import mx.messaging.config.ServerConfig;
             import mx.rpc.AsyncToken;
             import mx.rpc.AsyncResponder;
             import mx.rpc.events.FaultEvent;
             import mx.rpc.events.ResultEvent;
             import mx.messaging.ChannelSet;
 
             // Define a ChannelSet object.
             public var cs:ChannelSet;
 
             // Define an AsyncToken object.
             public var token:AsyncToken;
 
             // Initialize ChannelSet object based on the
             // destination of the RemoteObject component.
             private function creationCompleteHandler():void {
                 if (cs == null)
                 cs = ServerConfig.getChannelSet(remoteObject.destination);
             }
 
             // Login and handle authentication success or failure.
             private function ROLogin():void {
                 // Make sure that the user is not already logged in.
                 if (cs.authenticated == false) {
                     token = cs.login("sampleuser", "samplepassword");
                     // Add result and fault handlers.
                     token.addResponder(new AsyncResponder(LoginResultEvent,
                     LoginFaultEvent));
                 }
             }
 
             // Handle successful login.
             private function LoginResultEvent(event:ResultEvent,
                 token:Object=null):void  {
                     switch(event.result) {
                         case "success":
                             authenticatedCB.selected = true;
                             break;
                             default:
                     }
                 }
 
                 // Handle login failure.
                 private function LoginFaultEvent(event:FaultEvent,
                     token:Object=null):void {
                         switch(event.fault.faultCode) {
                             case "Client.Authentication":
                                 default:
                                 authenticatedCB.selected = false;
                                 Alert.show("Login failure: " + event.fault.faultString);
                     }
                 }
 
                 // Logout and handle success or failure.
                 private function ROLogout():void {
                     // Add result and fault handlers.
                     token = cs.logout();
                     token.addResponder(new
                         AsyncResponder(LogoutResultEvent,LogoutFaultEvent));
                 }
 
                 // Handle successful logout.
                 private function LogoutResultEvent(event:ResultEvent,
                     token:Object=null):void {
                         switch (event.result) {
                             case "success":
                                 authenticatedCB.selected = false;
                                 break;
                                 default:
                     }
                 }
 
                 // Handle logout failure.
                 private function LogoutFaultEvent(event:FaultEvent,
                     token:Object=null):void {
                         Alert.show("Logout failure: " + event.fault.faultString);
                 }
                 // Handle message recevied by RemoteObject component.
                 private function resultHandler(event:ResultEvent):void {
                     ta.text += "Server responded: "+ event.result + "\n";
                 }
 
                 // Handle fault from RemoteObject component.
                 private function faultHandler(event:FaultEvent):void {
                     ta.text += "Received fault: " + event.fault + "\n";
                 }
             ]]>
     </mx:Script>
     <mx:HBox>
         <mx:Label text="Enter a text for the server to echo"/>
         <mx:TextInput id="ti" text="Hello World!"/>
         <mx:Button label="Login"
             click="ROLogin();"/>
         <mx:Button label="Echo"
             enabled="{authenticatedCB.selected}"
             click="remoteObject.echo(ti.text);"/>
         <mx:Button label="Logout"
             click="ROLogout();"/>
         <mx:CheckBox id="authenticatedCB"
             label="Authenticated?"
             enabled="false"/>
     </mx:HBox>
     <mx:TextArea id="ta" width="100%" height="100%"/>
 
     <mx:RemoteObject id="remoteObject"
         destination="myDest"
         result="resultHandler(event);"
         fault="faultHandler(event);"/>
 </mx:Application>
```

De methoden `login` en `logout` retourneren een object AsyncToken. Wijs gebeurtenismanagers aan het voorwerp AsyncToken voor de resultaatgebeurtenis toe om een succesvolle vraag te behandelen, en voor de foutengebeurtenis om een mislukking te behandelen.

### Single Sign-On gebruiken {#using-single-sign-on}

Gebruikers van AEM-formulieren kunnen verbinding maken met meerdere AEM Forms-webtoepassingen om een taak uit te voeren. Wanneer gebruikers van de ene webtoepassing naar de andere gaan, is het niet efficiënt om van hen te verlangen dat zij zich afzonderlijk bij elke webtoepassing aanmelden. Met het AEM Forms-mechanisme voor eenmalige aanmelding kunnen gebruikers zich eenmaal aanmelden en vervolgens toegang krijgen tot alle AEM Forms-webtoepassingen. Omdat AEM Forms-ontwikkelaars clienttoepassingen kunnen maken voor gebruik met AEM Forms, moeten ze ook gebruik kunnen maken van het Single Sign-On mechanisme.

Elke AEM Forms-webtoepassing wordt verpakt in een eigen WAR-bestand (Web Archive), dat vervolgens wordt verpakt als onderdeel van een EAR-bestand (Enterprise Archive). Aangezien een toepassingsserver het delen van sessiegegevens in verschillende webtoepassingen niet toestaat, gebruikt AEM Forms HTTP-cookies om verificatiegegevens op te slaan. Met verificatiecookies kan een gebruiker zich aanmelden bij een Forms-toepassing en vervolgens verbinding maken met andere AEM Forms-webtoepassingen. Deze techniek wordt Single Sign-On genoemd.

AEM Forms-ontwikkelaars schrijven clienttoepassingen om de functionaliteit van formulierhulplijnen (afgekeurd) uit te breiden en Workspace aan te passen. Een Workspace-toepassing kan bijvoorbeeld een proces starten. De cliënttoepassing gebruikt dan een remoting eindpunt om gegevens van de dienst van Forms terug te winnen.

Wanneer een AEM Forms-service wordt aangeroepen met AEM Forms Remoting (Verouderd voor AEM-formulieren), geeft de clienttoepassing het verificatiecookie als onderdeel van de aanvraag door. Aangezien de gebruiker al is geverifieerd, is geen aanvullende aanmelding vereist om verbinding te maken van de clienttoepassing met de AEM Forms-service.

>[!NOTE]
>
>Als een cookie ongeldig is of ontbreekt, wordt niet impliciet omgeleid naar een aanmeldingspagina. Daarom kunt u nog een anonieme dienst roepen.

U kunt het AEM Forms-mechanisme voor eenmalige aanmelding omzeilen door een clienttoepassing te schrijven die zich zelfstandig aanmeldt en zich afmeldt. Als u het Single Sign-On mechanisme omzeilt, kunt u of basis of douaneauthentificatie met uw toepassing gebruiken.

Omdat dit mechanisme het AEM Forms Single Sign-On mechanisme niet gebruikt, wordt er geen verificatiecookie naar de client geschreven. Aanmeldingsgegevens worden opgeslagen in het `ChannelSet` -object voor het externe kanaal. Daarom worden alle `RemoteObject` aanroepen die u over dezelfde `ChannelSet` aanroept, uitgevoerd in de context van deze referenties.

### Single Sign-On instellen in AEM Forms {#setting-up-single-sign-on-in-aem-forms}

Als u Single Sign-On wilt gebruiken in AEM Forms, installeert u de component voor de formulierwerkstroom, die de gecentraliseerde aanmeldingsservice bevat. Nadat een gebruiker zich met succes heeft aangemeld, retourneert de gecentraliseerde aanmeldingsservice een verificatiecookie voor de gebruiker. Elke volgende aanvraag voor een Forms-webtoepassing bevat de cookie. Als het cookie geldig is, wordt de gebruiker beschouwd als zijnde geverifieerd en hoeft u zich niet opnieuw aan te melden.

### Een clienttoepassing schrijven die gebruikmaakt van Single Sign-On {#writing-a-client-application-that-uses-single-sign-on}

Wanneer u van het enige sign-on mechanisme voordeel haalt, verwacht u gebruikers om login door de gecentraliseerde login dienst te gebruiken alvorens een cliënttoepassing te beginnen. Een clienttoepassing kan zich dus niet aanmelden via de browser of door de methode `ChannelSet.login` aan te roepen.

Als u het enige sign-on mechanisme van AEM Forms gebruikt, vorm het Remoting eindpunt om douaneauthentificatie, niet basis te gebruiken. Anders, wanneer het gebruiken van basisauthentificatie, veroorzaakt een authentificatiefout een browser uitdaging, die u niet de gebruiker wilt zien. In plaats daarvan detecteert uw toepassing de verificatiefout en wordt een bericht weergegeven waarin de gebruiker wordt opgedragen zich aan te melden met de gecentraliseerde aanmeldingsservice.

Een clienttoepassing benadert AEM Forms via een extern eindpunt door de component `RemoteObject` te gebruiken, zoals in het volgende voorbeeld wordt getoond.

```java
 <?xml version="1.0"?>
 <mx:Application
        backgroundColor="#FFFFFF">
 
       <mx:Script>
          <![CDATA[
 
            import mx.controls.Alert;
            import mx.rpc.events.FaultEvent;
 
            // Prompt user to login on a fault.
            private function faultHandler(event:FaultEvent):void
            {
             if(event.fault.faultCode=="Client.Authentication")
             {
                 Alert.show(
                     event.fault.faultString + "\n" +
                     event.fault.faultCode + "\n" +
                     "Please login to continue.");
             }
         }
          ]]>
       </mx:Script>
 
       <mx:RemoteObject id="srv"
           destination="product"
           fault="faultHandler(event);"/>
 
       <mx:DataGrid
           width="100%" height="100%"
           dataProvider="{srv.getProducts.lastResult}"/>
 
       <mx:Button label="Get Data"
           click="srv.getProducts();"/>
 
 </mx:Application>
```

**het Aanmelden als nieuwe gebruiker terwijl de toepassing van Flex nog loopt**

Een toepassing die met Flex is ontwikkeld, bevat het verificatiecookie bij elke aanvraag naar een AEM Forms-service. Om prestatieredenen valideert AEM Forms de cookie niet op elk verzoek. AEM Forms detecteert echter wel wanneer een verificatiecookie wordt vervangen door een ander verificatiecookie.

U start bijvoorbeeld een clienttoepassing en wanneer de toepassing actief is, gebruikt u de gecentraliseerde aanmeldingsservice om u af te melden. Vervolgens kunt u zich aanmelden als een andere gebruiker. Aanmelden als een andere gebruiker vervangt het bestaande verificatiecookie door een verificatiecookie voor de nieuwe gebruiker.

Op het volgende verzoek van de clienttoepassing detecteert AEM Forms dat het cookie is gewijzigd en meldt het de gebruiker af. Daarom ontbreekt het eerste verzoek na een koekjesverandering. Alle volgende verzoeken worden gedaan in het kader van het nieuwe cookie en zijn succesvol.

**Logging uit**

Als u zich wilt afmelden bij AEM Forms en een sessie ongeldig wilt maken, moet het verificatiecookie worden verwijderd van de computer van de client. Omdat het doel van Single Sign-On is om een gebruiker toe te staan zich één keer aan te melden, wilt u geen cliënttoepassing om het koekje te schrappen. Met deze handeling wordt de gebruiker uitgelogd.

Daarom genereert het aanroepen van de methode `RemoteObject.logout` in een clienttoepassing een foutbericht op de client waarin wordt aangegeven dat de sessie niet wordt afgemeld. In plaats daarvan kan de gebruiker de gecentraliseerde aanmeldingsservice gebruiken om zich af te melden en het verificatiecookie te verwijderen.

**Logging uit terwijl de toepassing van Flex nog loopt**

U kunt een clienttoepassing starten die met Flex is gebouwd en de gecentraliseerde aanmeldingsservice gebruiken om u af te melden. Als onderdeel van het logout-proces wordt het verificatiecookie verwijderd. Als een verwijderingsaanvraag wordt ingediend zonder cookie of met een ongeldig cookie, wordt de gebruikerssessie ongeldig. Deze actie is in feite een logout. De volgende keer dat de clienttoepassing verbinding probeert te maken met een AEM Forms-service, wordt de gebruiker gevraagd zich aan te melden.

**zie ook**

[AEM Forms aanroepen met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Documenten verwerken met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Het AEM Forms Flex-bibliotheekbestand opnemen](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Beveiligde documenten doorgeven om processen aan te roepen met Verwijderen](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)

## Beveiligde documenten doorgeven om processen aan te roepen met Verwijderen {#passing-secure-documents-to-invoke-processes-using-remoting}

U kunt beveiligde documenten doorgeven aan AEM Forms wanneer u een proces aanroept waarvoor een of meer documenten vereist zijn. Door een beveiligd document door te geven, beschermt u bedrijfsinformatie en vertrouwelijke documenten. In dit geval kan een document verwijzen naar een PDF-document, een XML-document, een Word-document, enzovoort. Als AEM Forms is geconfigureerd voor beveiligde documenten, is het vereist dat een beveiligd document naar AEM Forms wordt verzonden vanuit een clienttoepassing die in Flex is geschreven. (Zie [ Vormend AEM Forms om veilige en onveilige documenten ](invoking-aem-forms-using-remoting.md#configuring-aem-forms-to-accept-secure-and-unsecure-documents) goed te keuren.)

Wanneer het overgaan van een veilig document, gebruik enig teken-op en specificeer een gebruiker van de vorm van AEM die het *Document heeft uploadt de rol van de Gebruiker van de Toepassing*. Zonder deze rol kan de gebruiker geen beveiligd document uploaden. U kunt een rol programmatically toewijzen aan een gebruiker. (Zie [ het Leiden Rollen en Toestemmingen ](/help/forms/developing/users.md#managing-roles-and-permissions).)

>[!NOTE]
>
>Wanneer u een rol maakt en u wilt dat leden van die rol beveiligde documenten uploaden, controleert u of u de machtiging Document uploaden hebt opgegeven.

AEM Forms ondersteunt een bewerking met de naam `getFileUploadToken` die een token retourneert dat is doorgegeven aan het uploadservlet. De methode `DocumentReference.constructRequestForUpload` vereist een URL naar AEM Forms, samen met het token dat door de methode `LC.FileUploadAuthenticator.getFileUploadToken` wordt geretourneerd. Deze methode retourneert een `URLRequest` -object dat wordt gebruikt in de aanroep naar het uploadservlet. De volgende code demonstreert deze toepassingslogica.

```java
     ...
         private function startUpload():void
         {
             fileRef.addEventListener(Event.SELECT, selectHandler);
             fileRef.addEventListener("uploadCompleteData", completeHandler);
             try
             {
         var success:Boolean = fileRef.browse();
             }
             catch (error:Error)
             {
                 trace("Unable to browse for files.");
             }
 
         }
 
          private function selectHandler(event:Event):void
             {
             var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator");
             authTokenService.addEventListener("result", authTokenReceived);
             authTokenService.channelSet = cs;
             authTokenService.getFileUploadToken();
             }
 
         private function authTokenReceived(event:ResultEvent):void
             {
             var token:String = event.result as String;
             var request:URLRequest = DocumentReference.constructRequestForUpload("http://localhost:8080", token);
 
             try
             {
           fileRef.upload(request);
             }
             catch (error:Error)
             {
             trace("Unable to upload file.");
             }
             }
 
         private function completeHandler(event:DataEvent):void
         {
 
             var params:Object = new Object();
             var docRef:DocumentReference = new DocumentReference();
             docRef.url = event.data as String;
             docRef.referenceType = DocumentReference.REF_TYPE_URL;
         }
         ...
```

)

### AEM Forms configureren voor het accepteren van beveiligde en onbeveiligde documenten {#configuring-aem-forms-to-accept-secure-and-unsecure-documents}

U kunt beheerconsole gebruiken om op te geven of documenten veilig zijn wanneer u een document doorgeeft van een Flex-clienttoepassing naar een AEM Forms-proces. AEM Forms is standaard geconfigureerd voor het accepteren van beveiligde documenten. U kunt AEM Forms configureren voor het accepteren van beveiligde documenten door de volgende stappen uit te voeren:

1. Log in bij de beheerconsole.
1. Klik **Montages**.
1. Klik **Montages van het Systeem van de Kern.**
1. Klik op Configuraties.
1. Zorg ervoor dat de optie Niet-beveiligde documenten mogen worden geüpload vanuit Flex-toepassingen is uitgeschakeld.

>[!NOTE]
>
>* Als u AEM Forms wilt configureren voor het accepteren van onbeveiligde documenten, selecteert u de optie Niet-beveiligde documenten mogen worden geüpload vanuit Flex-toepassingen. Start vervolgens een toepassing of service opnieuw om ervoor te zorgen dat de instelling van kracht wordt.
>* U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.


### Snel starten: Een kortstondig proces aanroepen door een beveiligd document door te geven met Verwijderen {#quick-start-invoking-a-short-lived-process-by-passing-a-secure-document-using-remoting}

Het volgende codevoorbeeld roept `MyApplication/EncryptDocument.` gebruiker A aan login om de Uitgezochte knoop van het Dossier te klikken die wordt gebruikt om een dossier van PDF te uploaden en het proces aan te halen. Dat wil zeggen dat zodra de gebruiker is geverifieerd, de knop Bestand selecteren is ingeschakeld. In de volgende afbeelding ziet u de Flex-clienttoepassing nadat een gebruiker is geverifieerd. Bericht dat Authenticated CheckBox wordt toegelaten.

![ iu_iu_securityemotelogin ](assets/iu_iu_secureremotelogin.png)

als AEM Forms wordt gevormd om veilige documenten slechts toe te staan om worden geupload en de gebruiker heeft niet het *Document de rol van de Gebruiker van de Toepassing van de Upload*, dan wordt een uitzondering geworpen. Als de gebruiker deze rol wel heeft, wordt het bestand geüpload en wordt het proces aangeroepen.

```java
 <?xml version="1.0" encoding="utf-8"?>
 <mx:Application  xmlns="*"
      creationComplete="initializeChannelSet();">
        <mx:Script>
        <![CDATA[
      import mx.rpc.livecycle.DocumentReference;
      import flash.net.FileReference;
      import flash.net.URLRequest;
      import flash.events.Event;
      import flash.events.DataEvent;
      import mx.messaging.ChannelSet;
      import mx.messaging.channels.AMFChannel;
      import mx.rpc.events.ResultEvent;
      import mx.collections.ArrayCollection;
      import mx.rpc.AsyncToken;
      import mx.controls.Alert;
      import mx.rpc.events.FaultEvent;
      import mx.rpc.AsyncResponder;
 
      // Classes used in file retrieval
      private var fileRef:FileReference = new FileReference();
      private var docRef:DocumentReference = new DocumentReference();
      private var parentResourcePath:String = "/";
      private var now1:Date;
      private var serverPort:String = "hiro-xp:8080";
 
      // Define a ChannelSet object.
      public var cs:ChannelSet;
 
      // Define an AsyncToken object.
      public var token:AsyncToken;
 
       // Holds information returned from AEM Forms
      [Bindable]
      public var progressList:ArrayCollection = new ArrayCollection();
 
 
      // Handles a successful login
     private function LoginResultEvent(event:ResultEvent,
         token:Object=null):void  {
             switch(event.result) {
                 case "success":
                     authenticatedCB.selected = true;
                     btnFile.enabled = true;
                     btnLogout.enabled = true;
                     btnLogin.enabled = false;
                         break;
                     default:
                 }
             }
 
 
 // Handle login failure.
 private function LoginFaultEvent(event:FaultEvent,
     token:Object=null):void {
     switch(event.fault.faultCode) {
                 case "Client.Authentication":
                         default:
                         authenticatedCB.selected = false;
                         Alert.show("Login failure: " + event.fault.faultString);
                 }
             }
 
 
      // Set up channel set to invoke AEM Forms
      private function initializeChannelSet():void {
        cs = new ChannelSet();
        cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));
        EncryptDocument2.channelSet = cs;
      }
 
     // Call this method to upload the file.
      // This creates a file picker and lets the user select a PDF file to pass to the EncryptDocument process.
      private function uploadFile():void {
        fileRef.addEventListener(Event.SELECT, selectHandler);
        fileRef.addEventListener(DataEvent.UPLOAD_COMPLETE_DATA,completeHandler);
        fileRef.browse();
      }
 
      // Gets called for selected file. Does the actual upload via the file upload servlet.
      private function selectHandler(event:Event):void {
              var authTokenService:RemoteObject = new RemoteObject("LC.FileUploadAuthenticator");
         authTokenService.addEventListener("result", authTokenReceived);
         authTokenService.channelSet = cs;
         authTokenService.getFileUploadToken();
      }
 
     private function authTokenReceived(event:ResultEvent):void
     {
     var token:String = event.result as String;
     var request:URLRequest = DocumentReference.constructRequestForUpload("https://hiro-xp:8080", token);
 
     try
     {
           fileRef.upload(request);
     }
     catch (error:Error)
     {
         trace("Unable to upload file.");
     }
 }
 
      // Called once the file is completely uploaded.
      private function completeHandler(event:DataEvent):void {
 
        // Set the docRef's url and referenceType parameters
        docRef.url = event.data as String;
        docRef.referenceType=DocumentReference.REF_TYPE_URL;
        executeInvokeProcess();
      }
 
     //This method invokes the EncryptDocument process
      public function executeInvokeProcess():void {
         //Create an Object to store the input value for the EncryptDocument process
           now1 = new Date();
 
         var params:Object = new Object();
         params["inDoc"]=docRef;
 
         // Invoke the EncryptDocument process
         var token:AsyncToken;
         token = EncryptDocument2.invoke(params);
         token.name = name;
      }
 
      // AEM Forms  login method
      private function ROLogin():void {
         // Make sure that the user is not already logged in.
 
         //Get the User and Password
         var userName:String = txtUser.text;
         var pass:String = txtPassword.text;
 
        if (cs.authenticated == false) {
             token = cs.login(userName, pass);
 
         // Add result and fault handlers.
         token.addResponder(new AsyncResponder(LoginResultEvent,    LoginFaultEvent));
                 }
             }
 
      // This method handles a successful process invocation
      public function handleResult(event:ResultEvent):void
      {
            //Retrieve information returned from the service invocation
          var token:AsyncToken = event.token;
          var res:Object = event.result;
          var dr:DocumentReference = res["outDoc"] as DocumentReference;
          var now2:Date = new Date();
 
           // These fields map to columns in the DataGrid
          var progObject:Object = new Object();
          progObject.filename = token.name;
          progObject.timing = (now2.time - now1.time).toString();
          progObject.state = "Success";
          progObject.link = "<a href='" + dr.url + "'> open </a>";
          progressList.addItem(progObject);
      }
 
      // Prompt user to login on a fault.
       private function faultHandler(event:FaultEvent):void
            {
             if(event.fault.faultCode=="Client.Authentication")
             {
                 Alert.show(
                     event.fault.faultString + "\n" +
                     event.fault.faultCode + "\n" +
                     "Please login to continue.");
             }
            }
 
       // AEM Forms  logout method
     private function ROLogout():void {
         // Add result and fault handlers.
         token = cs.logout();
         token.addResponder(new AsyncResponder(LogoutResultEvent,LogoutFaultEvent));
     }
 
     // Handle successful logout.
     private function LogoutResultEvent(event:ResultEvent,
         token:Object=null):void {
         switch (event.result) {
         case "success":
                 authenticatedCB.selected = false;
                 btnFile.enabled = false;
                 btnLogout.enabled = false;
                 btnLogin.enabled = true;
                 break;
                 default:
             }
     }
 
     // Handle logout failure.
     private function LogoutFaultEvent(event:FaultEvent,
             token:Object=null):void {
             Alert.show("Logout failure: " + event.fault.faultString);
     }
 
          private function resultHandler(event:ResultEvent):void {
          // Do anything else here.
          }
        ]]>
 
      </mx:Script>
      <mx:RemoteObject id="EncryptDocument" destination="MyApplication/EncryptDocument" result="resultHandler(event);">
          <mx:method name="invoke" result="handleResult(event)"/>
      </mx:RemoteObject>
 
       <!--//This consists of what is displayed on the webpage-->
      <mx:Panel id="lcPanel" title="EncryptDocument  (Deprecated for AEM forms) AEM Forms Remoting Example"
           height="25%" width="25%" paddingTop="10" paddingLeft="10" paddingRight="10"
           paddingBottom="10">
         <mx:Label width="100%" color="blue"
                text="Select a PDF file to pass to the EncryptDocument process"/>
        <mx:DataGrid x="10" y="0" width="500" id="idProgress" editable="false"
           dataProvider="{progressList}" height="231" selectable="false" >
          <mx:columns>
            <mx:DataGridColumn headerText="Filename" width="200" dataField="filename" editable="false"/>
            <mx:DataGridColumn headerText="State" width="75" dataField="state" editable="false"/>
            <mx:DataGridColumn headerText="Timing" width="75" dataField="timing" editable="false"/>
            <mx:DataGridColumn headerText="Click to Open" dataField="link" editable="false" >
             <mx:itemRenderer>
                <mx:Component>
                   <mx:Text x="0" y="0" width="100%" htmlText="{data.link}"/>
                </mx:Component>
             </mx:itemRenderer>
            </mx:DataGridColumn>
          </mx:columns>
        </mx:DataGrid>
        <mx:Button label="Select File" click="uploadFile()"  id="btnFile" enabled="false"/>
        <mx:Button label="Login" click="ROLogin();" id="btnLogin"/>
        <mx:Button label="LogOut" click="ROLogout();" enabled="false" id="btnLogout"/>
        <mx:HBox>
         <mx:Label text="User:"/>
         <mx:TextInput id="txtUser" text=""/>
         <mx:Label text="Password:"/>
         <mx:TextInput id="txtPassword" text="" displayAsPassword="true"/>
         <mx:CheckBox id="authenticatedCB"
             label="Authenticated?"
             enabled="false"/>
     </mx:HBox>
      </mx:Panel>
 </mx:Application>
```

**zie ook**

[AEM Forms aanroepen met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Documenten verwerken met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Het AEM Forms Flex-bibliotheekbestand opnemen](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Client-toepassingen verifiëren die zijn gemaakt met Flex](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

## Aanroepen van aangepaste componentenservices met Remoting {#invoking-custom-component-services-using-remoting}

U kunt services in een aangepaste component aanroepen met Verwijderen. Neem bijvoorbeeld de bankcomponent die de klantenservice bevat. U kunt bewerkingen die bij de klantenservice horen, aanroepen met een clienttoepassing die in Flex is geschreven. Voordat u de snelstartcomponent van deze sectie kunt uitvoeren, moet u de aangepaste component Bank maken.

De klantenservice stelt een bewerking met de naam `createCustomer` beschikbaar. In deze beschrijving wordt beschreven hoe u een Flex-clienttoepassing kunt maken die de klantenservice aanroept en een klant maakt. Voor deze bewerking is een complex object van het type `com.adobe.livecycle.sample.customer.Customer` vereist dat de nieuwe klant vertegenwoordigt. De volgende illustratie toont de cliënttoepassing die de dienst van de Klant aanhaalt en een nieuwe klant creeert. De bewerking `createCustomer` retourneert een waarde voor de klant-id. De identificatiewaarde wordt weergegeven in het tekstvak Customer Identifier.

![ iu_iu_flexnewcust ](assets/iu_iu_flexnewcust.png)

De volgende lijst maakt een lijst van de controles die deel van deze cliënttoepassing uitmaken.

<table>
 <thead>
  <tr>
   <th><p>Naam besturingselement</p></th>
   <th><p>Beschrijving</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>txtFirst</p></td>
   <td><p>Geeft de voornaam van de klant aan. </p></td>
  </tr>
  <tr>
   <td><p>txtLast</p></td>
   <td><p>Geeft de achternaam van de klant aan. </p></td>
  </tr>
  <tr>
   <td><p>txtPhone</p></td>
   <td><p>Hier geeft u het telefoonnummer van de klant op.</p></td>
  </tr>
  <tr>
   <td><p>txtStreet</p></td>
   <td><p>Geeft de straatnaam van de klant aan.</p></td>
  </tr>
  <tr>
   <td><p>txtState</p></td>
   <td><p>Geeft de status van de klant aan. </p></td>
  </tr>
  <tr>
   <td><p>txtZIP</p></td>
   <td><p>Geeft de postcode van de klant aan. </p></td>
  </tr>
  <tr>
   <td><p>txtCity</p></td>
   <td><p>Geeft de plaats van de klant aan.</p></td>
  </tr>
  <tr>
   <td><p>txtCustId</p></td>
   <td><p>Hiermee geeft u de id-waarde van de klant op waartoe de nieuwe account behoort. Dit tekstvak wordt gevuld door de geretourneerde waarde van de bewerking <code>createCustomer</code> van de klantenservice. </p></td>
  </tr>
 </tbody>
</table>

### Toewijzing van complexe AEM Forms-gegevenstypen {#mapping-aem-forms-complex-data-types}

Sommige AEM Forms-bewerkingen vereisen complexe gegevenstypen als invoerwaarden. Deze complexe gegevenstypen definiëren de runtimewaarden die door de bewerking worden gebruikt. De `createCustomer` -bewerking van de klantenservice vereist bijvoorbeeld een `Customer` -instantie die runtimewaarden bevat die door de service worden vereist. Zonder het complexe type, werpt de dienst van de Klant een uitzondering en voert niet de verrichting uit.

Wanneer u een AEM Forms-service aanroept, maakt u ActionScript-objecten die zijn toegewezen aan de vereiste complexe AEM Forms-typen. Voor elk complex gegevenstype dat een bewerking vereist, maakt u een afzonderlijk ActionScript-object.

In de ActionScript-klasse gebruikt u de metagegevenstag `RemoteClass` om het complexe type van AEM Forms toe te wijzen. Wanneer u bijvoorbeeld de bewerking `createCustomer` van de Klantenservice aanroept, maakt u een ActionScript-klasse die is toegewezen aan het gegevenstype `com.adobe.livecycle.sample.customer.Customer` .

De volgende ActionScript-klasse met de naam Klant laat zien hoe u het gegevenstype AEM Forms `com.adobe.livecycle.sample.customer.Customer` kunt toewijzen.

```java
 package customer
 
 {
     [RemoteClass(alias="com.adobe.livecycle.sample.customer.Customer")]
     public class Customer
     {
            public var name:String;
            public var street:String;
            public var city:String;
            public var state:String;
            public var phone:String;
            public var zip:int;
        }
 }
```

Het volledig gekwalificeerde gegevenstype van het complex type AEM Forms wordt toegewezen aan de alias-tag.

De velden van de ActionScript-klasse komen overeen met de velden die tot het complexe type AEM Forms behoren. De zes velden in de ActionScript-klasse van de Klant komen overeen met de velden die bij `com.adobe.livecycle.sample.customer.Customer` horen.

>[!NOTE]
>
>Een goede manier om de gebiedsnamen te bepalen die tot een complex type van Forms behoren is WSDL van de dienst in Webbrowser te bekijken. Een WSDL specificeert de complexe types van de dienst en de overeenkomstige gegevensleden. De volgende WSDL wordt gebruikt voor de klantenservice: `https://[yourServer]:[yourPort]/soap/services/CustomerService?wsdl.`

De klasse ActionScript van de Klant behoort tot een pakket genoemd klant. U wordt aangeraden alle ActionScript-klassen die zijn toegewezen aan complexe AEM Forms-gegevenstypen in een eigen pakket te plaatsen. Maak een map in de bronmap van het Flex-project en plaats het ActionScript-bestand in de map, zoals in de volgende afbeelding wordt getoond.

![ iu_iu_customeras ](assets/iu_iu_customeras.png)

### Snel starten: De aangepaste service van de klant aanroepen met Verwijderen {#quick-start-invoking-the-customer-custom-service-using-remoting}

Het volgende codevoorbeeld roept de dienst van de Klant aan en leidt tot een klant. Wanneer u dit codevoorbeeld in werking stelt, zorg ervoor dat u alle tekstvakjes invult. Zorg er ook voor dat u het bestand Customer.as maakt dat aan `com.adobe.livecycle.sample.customer.Customer` is toegewezen.

>[!NOTE]
>
>Voordat u deze snelle start kunt uitvoeren, moet u de aangepaste component Bank maken en implementeren.

```java
 <?xml version="1.0" encoding="utf-8"?>
 <mx:Application  layout="absolute" backgroundColor="#B1ABAB">
 
 <mx:Script>
            <![CDATA[
 
      import flash.net.FileReference;
      import flash.net.URLRequest;
      import flash.events.Event;
      import flash.events.DataEvent;
      import mx.messaging.ChannelSet;
      import mx.messaging.channels.AMFChannel;
      import mx.rpc.events.ResultEvent;
      import mx.collections.ArrayCollection;
      import mx.rpc.AsyncToken;
      import mx.managers.CursorManager;
      import mx.rpc.remoting.mxml.RemoteObject;
 
 
      // Custom class that corresponds to an input to the
      // AEM Forms encryption method
      import customer.Customer;
 
      // Classes used in file retrieval
      private var fileRef:FileReference = new FileReference();
      private var parentResourcePath:String = "/";
      private var serverPort:String = "hiro-xp:8080";
      private var now1:Date;
      private var fileName:String;
 
      // Prepares parameters for encryptPDFUsingPassword method call
      public function executeCreateCustomer():void
      {
 
        var cs:ChannelSet= new ChannelSet();
     cs.addChannel(new AMFChannel("remoting-amf", "https://" + serverPort + "/remoting/messagebroker/amf"));
 
     customerService.setCredentials("administrator", "password");
     customerService.channelSet = cs;
 
     //Create a Customer object required to invoke the Customer service's
     //createCustomer operation
     var myCust:Customer = new Customer();
 
     //Get values from the user of the Flex application
     var fullName:String = txtFirst.text +" "+txtLast.text ;
     var Phone:String = txtPhone.text;
     var Street:String = txtStreet.text;
     var State:String = txtState.text;
     var Zip:int = parseInt(txtZIP.text);
     var City:String = txtCity.text;
 
     //Populate Customer fields
     myCust.name = fullName;
     myCust.phone = Phone;
     myCust.street= Street;
     myCust.state= State;
     myCust.zip = Zip;
     myCust.city = City;
 
     //Invoke the Customer service's createCustomer operation
     var params:Object = new Object();
        params["inCustomer"]=myCust;
     var token:AsyncToken;
        token = customerService.createCustomer(params);
        token.name = name;
      }
 
      private function handleResult(event:ResultEvent):void
      {
          // Retrieve the information returned from the service invocation
          var token:AsyncToken = event.token;
          var res:Object = event.result;
          var custId:String = res["CustomerId"] as String;
 
          //Assign to the custId to the text box
          txtCustId.text = custId;
      }
 
 
      private function resultHandler(event:ResultEvent):void
      {
 
      }
            ]]>
 </mx:Script>
 <mx:RemoteObject id="customerService" destination="CustomerService" result="resultHandler(event);">
 <mx:method name="createCustomer" result="handleResult(event)"/>
 </mx:RemoteObject>
 
 
 <mx:Style source="../bank.css"/>
     <mx:Grid>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="New Customer" fontSize="16" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="First Name:" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtFirst"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:Button label="Create Customer" id="btnCreateCustomer" click="executeCreateCustomer()"/>
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Last Name" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtLast"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Phone" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtPhone"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Street" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtStreet"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="State" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtState"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="ZIP" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtZIP"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                     <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="City" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtCity"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                             <mx:GridRow width="100%" height="100%">
                         <mx:GridItem width="100%" height="100%">
                             <mx:Label text="Customer Identifier" fontSize="12" fontWeight="bold"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                             <mx:TextInput styleName="textField" id="txtCustId" editable="false"/>
                         </mx:GridItem>
                         <mx:GridItem width="100%" height="100%">
                         </mx:GridItem>
                     </mx:GridRow>
                 </mx:Grid>
 </mx:Application>
 
```

**Stijlblad**

Dit snelle begin bevat een stijlblad genoemd *bank.css*. De volgende code vertegenwoordigt de stijlpagina die wordt gebruikt.

```css
 /* CSS file */
 global
 {
          backgroundGradientAlphas: 1.0, 1.0;
          backgroundGradientColors: #525152,#525152;
          borderColor: #424444;
          verticalAlign: middle;
          color: #FFFFFF;
          font-size:12;
          font-weight:normal;
 }
 
 ApplicationControlBar
 {
          fillAlphas: 1.0, 1.0;
          fillColors: #393839, #393839;
 }
 
 .textField
 {
          backgroundColor: #393839;
          background-disabled-color: #636563;
 }
 
 
 .button
 {
          fillColors: #636563, #424242;
 }
 
 .dropdownMenu
 {
          backgroundColor: #DDDDDD;
          fillColors: #636563, #393839;
          alternatingItemColors: #888888, #999999;
 }
 
 .questionLabel
 {
 
 }
 
 ToolTip
 {
        backgroundColor: black;
        backgroundAlpha: 1.0;
        cornerRadius: 0;
        color: white;
 }
 
 DateChooser
 {
        cornerRadius: 0; /* pixels */
        headerColors: black, black;
        borderColor: black;
        themeColor: black;
        todayColor: red;
        todayStyleName: myTodayStyleName;
        headerStyleName: myHeaderStyleName;
        weekDayStyleName: myWeekDayStyleName;
        dropShadowEnabled: true;
 }
 
 .myTodayStyleName
 {
        color: white;
 }
 
 .myWeekDayStyleName
 {
        fontWeight: normal;
 }
 
 .myHeaderStyleName
 {
        color: red;
        fontSize: 16;
        fontWeight: bold;
 }
```

**zie ook**

[AEM Forms aanroepen met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-aem-forms-using-remoting)

[Documenten verwerken met (Vervangen voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#handling-documents-with-remoting)

[Het AEM Forms Flex-bibliotheekbestand opnemen](invoking-aem-forms-using-remoting.md#including-the-aem-forms-flex-library-file)

[Een kortstondig proces aanroepen door een onbeveiligd document door te geven met (Verouderd voor AEM-formulieren) AEM Forms Remoting](invoking-aem-forms-using-remoting.md#invoking-a-short-lived-process-by-passing-an-unsecure-document-using-remoting)

[Client-toepassingen verifiëren die zijn gemaakt met Flex](invoking-aem-forms-using-remoting.md#authenticating-client-applications-built-with-flex)

[Beveiligde documenten doorgeven om processen aan te roepen met Verwijderen](invoking-aem-forms-using-remoting.md#passing-secure-documents-to-invoke-processes-using-remoting)
