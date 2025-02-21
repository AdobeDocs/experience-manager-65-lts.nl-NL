---
title: AEM toestaan te zoeken naar met documentbeveiliging beveiligde PDF-documenten
description: Leer hoe u native AEM-zoekopdrachten kunt uitvoeren voor full-text zoekopdrachten in met DRM beveiligde PDF-documenten.
contentOwner: khsingh
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/working_with_document_security
docset: aem65
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '718'
ht-degree: 0%

---

# AEM toestaan te zoeken naar met documentbeveiliging beveiligde PDF-documenten{#enable-aem-to-search-document-security-protected-pdf-documents}

Bij zoeken in AEM kunt u zoeken naar AEM-elementen en zoeken naar tekst op verschillende veelgebruikte documentindelingen, zoals bestanden met normale tekst, Microsoft Office-documenten en PDF-documenten. U kunt het inheemse onderzoek ook uitbreiden om full-text onderzoek op [ documenten uit te voeren PDF die met de veiligheid van het Document van AEM ](../../forms/using/admin-help/document-security.md) worden beschermd. Voer de volgende stappen uit om AEM in staat te stellen full-text zoekopdrachten uit te voeren voor dergelijke documenten:

1. Een veilige verbinding tot stand brengen
1. Een PDF-document indexeren dat met een voorbeeldbeleid is beveiligd

## Vereisten {#prerequisites}

* Als u AEM Forms gebruikt op OSGi:

   * Installeer [ het pakket van de Indexer van de Veiligheid van het Document van AEM Forms ](https://helpx.adobe.com/aem-forms/kb/aem-forms-releases.html) op de server van AEM Forms.

   * Controleer of een AEM Forms op de JEE-server actief is en of documentbeveiliging op de overeenkomstige AEM Forms op de JEE-server is geïnstalleerd. Het AEM-formulier op de JEE-server is vereist om het beveiligde document te indexeren.

* Als u alleen AEM Forms op de JEE-server gebruikt, is het indexeerpakket al geïnstalleerd.
* Zorg ervoor dat alle bundels aan de slag zijn. Als alle bundels niet actief zijn, wacht u tot alle bundels actief zijn.

   * Voor AEM Forms op OSGi, zijn de bundels vermeld in https://&#39; [ server ]:[ haven ]&#39;/system/console/bundels.
   * Voor AEM Forms op JEE, zijn de bundels vermeld in https://&#39; [ server ]:[ haven ]&#39;/[ context-weg ]/system/console/bundels. Bijvoorbeeld https://localhost:8080/lc/system/console/bundles.

* Voeg het {*pakket 0} sun.util.endar aan de lijst van gewenste personen toe.* Voer de volgende stappen uit om het pakket aan de lijst van gewenste personen toe te voegen:

   1. Open AEM-webconsole. URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.
   1. Bepaal en open **Configuratie van de Firewall 0} Deserialization.**

   1. Voeg het pakket sun.util.agenda aan de Gevoegde op lijst van gewenste personen klassen of het pakket prefixes gebied toe en klik **sparen**.

### Een veilige verbinding tot stand brengen tussen AEM Forms JEE- en OSGi-stapels {#establish-a-secure-connection-between-aem-forms-jee-and-osgi-stacks}

U kunt een van de volgende methoden gebruiken om de beveiligde verbinding tot stand te brengen:

* Adobe LiveCycle Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties
* Adobe LiveCycle Client SDK-bundel configureren met wederzijdse verificatie

#### Adobe LiveCycle Client SDK-bundel configureren met AEM Forms op JEE-beheerdersreferenties {#configure-adobe-livecycle-client-sdk-bundle-with-aem-forms-on-jee-admin-credentials}

1. Open AEM-webconsole. URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.
1. Zoek en open de **Bundel van SDK van de Cliënt van Adobe LiveCycle**. Geef waarde op voor de volgende velden:

   * **Server URL:** specificeer HTTPS URL van AEM Forms op server JEE. Start de server opnieuw op met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file> om communicatie via https mogelijk te maken.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.
   * **Gebruikersnaam:** specificeer gebruikersnaam van AEM Forms op JEE rekening om vraag van de server van AEM in werking te stellen. De opgegeven account moet beschikken over machtigingen om documentservices te starten op de AEM Forms op de JEE-server.
   * **Wachtwoord**: specificeer wachtwoord van AEM Forms op JEE rekening die op het gebied van de Gebruikersnaam wordt vermeld.

   Klik **sparen**. AEM is ingeschakeld om te zoeken in met documentbeveiliging beveiligde PDF-documenten.

#### Adobe LiveCycle Client SDK-bundel configureren met wederzijdse verificatie {#configure-adobe-livecycle-client-sdk-bundle-using-mutual-authentication}

1. Schakel wederzijdse verificatie in voor AEM Forms op JEE. Voor gedetailleerde informatie, zie [ CAC en Wederzijdse Authentificatie ](https://helpx.adobe.com/livecycle/kb/cac-mutual-authentication.html).
1. Open AEM-webconsole. URL is https://&#39; [ server ]:[ haven ]&#39;/system/console/configMgr.
1. Bepaal en open de plaats van **Adobe LiveCycle Cliënt SDK** Bundel. Geef waarde op voor de volgende eigenschappen:

   * **Server URL**: specificeer HTTPS URL van AEM Forms op server JEE. Start de AEM-server opnieuw met de parameter -Djavax.net.ssl.trustStore=&lt;path of AEM Forms on JEE keystore file> om communicatie via https mogelijk te maken.
   * **laat 2-wegs SSL** toe: Laat 2-wegsSSL optie toe.
   * **het Dossier URL van KeyStore**: Specificeer URL van het keystore dossier.
   * **TrustStore FIle URL**: Specificeer URL van het truststore dossier.
   * **Wachtwoord KeyStore**: Specificeer het wachtwoord voor het keystore dossier.
   * **TrustStorePassword**: Specificeer het wachtwoord voor het truststore dossier.
   * **Naam van de Dienst**: Voeg de RightsManagementService aan de lijst van de gespecificeerde diensten toe.

   Klik **sparen**. AEM is ingeschakeld om te zoeken naar met documentbeveiliging beveiligde PDF-documenten

### Een PDF-document indexeren dat met een voorbeeldbeleid is beveiligd {#index-a-sample-policy-protected-pdf-document}

1. Meld u als beheerder aan bij AEM Assets.
1. Maak een map in AEM Digital Asset Manager en upload de met beleid beveiligde PDF-documenten naar de nieuwe map.

   U kunt nu zoeken in documenten die met een beleid zijn beveiligd met AEM.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.
