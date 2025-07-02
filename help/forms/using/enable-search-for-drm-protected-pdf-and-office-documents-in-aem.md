---
title: AEM toestaan te zoeken naar documenten die zijn beveiligd door PDF en Microsoft Office
description: Leer hoe u native AEM-zoekopdrachten kunt uitvoeren voor full-text zoekopdrachten in met DRM beveiligde PDF-documenten.
noindex: true
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 5e9d3f3c-8fc4-4d01-9f1e-62d3c29ab9e5
source-git-commit: cd6caaf9de907488db14df2a6396fa60efa2d42c
workflow-type: tm+mt
source-wordcount: '664'
ht-degree: 0%

---

# AEM toestaan te zoeken naar documenten die zijn beveiligd door PDF en Microsoft Office{#enable-aem-to-search-document-security-protected-pdf-and-microsoft-office-documents}

Adobe Experience Manager biedt een gebruikersinterface voor het zoeken naar en zoeken naar verschillende middelen die zijn opgeslagen in AEM. De native zoekopdracht is geschikt voor het zoeken naar en zoeken naar AEM-elementen en voor het uitvoeren van tekstzoekopdrachten in verschillende veelgebruikte documentindelingen, zoals bestanden met normale tekst, Microsoft Office-documenten en PDF-documenten. U kunt de native zoekopdracht ook uitbreiden en inschakelen om full-text zoekopdrachten uit te voeren in met DRM beveiligde PDF- en Microsoft Office-documenten.

Voer de volgende stappen uit om AEM in staat te stellen te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten:

## Voordat u begint {#before-you-start}

* Installeer en configureer de beveiliging van AEM Forms-documenten.
* Voeg pakket sun.util.agenda aan de lijst van gewenste personen van de **Configuratie van de Firewall Deserialization toe.** De configuratie wordt weergegeven in `https://'[server]:[port]'/system/console/configMgr` .
* Zorg ervoor dat alle AEM-pakketten actief zijn. De bundels worden weergegeven bij `https://'[server]:[port]'/system/console/bundles` . Als alle bundels niet actief zijn, wacht u en controleert u de status van de bundels na een paar minuten.

## Een veilige verbinding tot stand brengen binnen de AEM Forms-workflow (AEM Forms op JEE) {#establish-a-secure-connection-within-aem-forms-workflow-aem-forms-on-jee}

Een veilige verbinding laat naadloze stroom van informatie tussen AEM Forms op JEE en de diensten OSGi toe die op de zelfde server lopen. Gebruik een van de volgende methoden om een veilige verbinding tot stand te brengen:

* AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* AEM Forms Client SDK-bundel configureren met wederzijdse verificatie

### AEM Forms Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-aem-forms-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM Configuration Manager en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server URL:** specificeer HTTP URL van AEM Forms op server JEE. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   * **Gebruikersnaam:** specificeer gebruikersbenaming van AEM Forms op JEE rekening om vraag van AEM Forms op server in werking te stellen JEE. De opgegeven account moet gemachtigd zijn om documentservices aan te roepen op de AEM Forms op de JEE-server.
   * **Wachtwoord**: specificeer wachtwoord van AEM Forms op JEE rekening die op het gebied van de Gebruikersnaam wordt vermeld.

   Klik **sparen**. AEM is ingeschakeld om te zoeken naar documenten die zijn beveiligd door PDF en Microsoft Office.

### AEM Forms Client SDK-bundel configureren met wederzijdse verificatie {#configure-aem-forms-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE.
1. Open AEM Configuration Manager en meld u aan als beheerder. De standaard-URL is https://&lt;serverName>:&lt;port>/lc/system/console/configMgr.
1. Zoek en open de AEM Forms Client SDK-bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server URL:** specificeer HTTPS URL van AEM Forms op server JEE. Als u communicatie via https wilt inschakelen, start u de AEM Forms op de JEE-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file>.
   * **laat 2-wegs SSL** toe: Laat 2-wegsSSL optie toe.
   * **het Dossier URL van KeyStore**: Specificeer URL van het keystore dossier.
   * **TrustStore FIle URL**: Specificeer URL van het truststore dossier.
   * **Wachtwoord KeyStore**: Specificeer het wachtwoord voor het keystore dossier.
   * **TrustStorePassword**: Specificeer het wachtwoord voor het truststore dossier.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.

   Klik **sparen**. AEM is ingeschakeld om te zoeken naar met documentbeveiliging beveiligde PDF- en Microsoft Office-documenten

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

## Een voorbeelddocument indexeren dat door een beleid beveiligd is PDF- of Microsoft Office-document {#index-a-sample-policy-protected-pdf-or-microsoft-office-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload een met beleid beveiligd PDF- of Microsoft Office-document naar de nieuwe map. Zoek nu de inhoud van documenten die met een beleid zijn beveiligd met AEM. Het moet het document met gezochte tekst terugkeren.
