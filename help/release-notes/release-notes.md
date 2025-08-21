---
title: De Nota's van de versie voor  [!DNL Adobe Experience Manager]  6.5 LTS
description: Hier vindt u de actuele release-informatie voor Adobe Experience Manager 6.5 LTS.
solution: Experience Manager
feature: Release Information
role: User,Admin,Architect,Developer
exl-id: 70436606-d95c-4208-94f6-e33f3eefdf66
source-git-commit: 7f9f24f173604640b454449b389da9fcdcf7017d
workflow-type: tm+mt
source-wordcount: '1068'
ht-degree: 1%

---

# Opmerkingen bij de huidige release voor Adobe Experience Manager 6.5 LTS {#release-notes}

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6,5 LTS |
| Type | Grote release |
| Algemene beschikbaarheid | 7 maart 2025 |

## Nieuwe functies {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS is een upgrade-release naar de [!DNL Adobe Experience Manager] 6.5 code base. Het verstrekt zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit, en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.5 Service Pack-releases tot SP22.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Het platform van [!DNL Adobe Experience Manager] 6.5 LTS bouwt voort op bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java™ Content Repository: Apache Jackrabbit Oak 1.68.x.

Eclipse Jetty 11.0.x wordt gebruikt als servletmotor voor QuickStart.

#### Java™-ondersteuning  {#java-support}

* Ondersteuning voor Java™ 17 en Java™ 21.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Voor meer informatie, zie [ installeer en werk ](/help/sites-deploying/custom-standalone-install.md) sectie bij.
* Adobe verspreidt updates voor Java™ 17- en Java™ 21-onderhoud voor gebruik door klanten in AEM-gerelateerde projecten, wanneer deze niet openbaar zijn vanuit Oracle.

#### Uberjar-verpakking {#uber-jar-packaging}

* Er is een klein verschil tussen de Uberjar-verpakking en de AEM 6,5 LTS. Voor meer informatie, zie [ Update de versie van AEM Uber Jar ](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version).

#### Upgrade {#upgrade}

* Voor details over de verbeteringsprocedure, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

## Installeren en bijwerken {#install-update}

Voor opstellingsvereisten, zie [ installatieinstructies ](/help/sites-deploying/custom-standalone-install.md).

Voor gedetailleerde instructies, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

>[!NOTE]
>
> Voor nieuwe AEM 6.5 LTS-installaties moeten indexdefinities afzonderlijk worden geïnstalleerd. Voor meer informatie, zie [ dit artikel ](/help/sites-deploying/pre-upgrade-maintenance-tasks.md#index-definitions).

## Ondersteunde platforms {#supported-platforms}

Vind de volledige matrijs van gesteunde platforms met inbegrip van steun-niveau op [ AEM 6.5 LTS technische vereisten ](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17/Java™ 21 zijn de aanbevolen versies voor gebruik met AEM 6.5 LTS.

## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe controleert voortdurend de productmogelijkheden om de waarde van klanten te verbeteren door oudere functies te moderniseren of te vervangen. Deze veranderingen worden gemaakt met zorgvuldige aandacht aan achterwaartse verenigbaarheid.

Om de aanstaande verwijdering of vervanging van Adobe Experience Manager (AEM) mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De daadwerkelijke streefdatum voor verwijdering is gepland voor bekendmaking later.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

### Verouderde functies {#deprecated-features}

In deze sectie worden de functies en mogelijkheden weergegeven die Adobe in AEM 6.5 LTS heeft vervangen. Adobe heeft doorgaans een lagere functie dan functies voordat deze in een toekomstige versie worden verwijderd. Bovendien is dit een alternatief.


Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Gebied | Functie | Vervanging | Versie (SP) |
|---|---|---|---|
| Sites | [ Redacteur van het KUUROORD ](/help/sites-developing/spa-overview.md) | De aangewezen redacteurs voor het beheren van hoofdloze inhoud in AEM zijn:<br> - [ de Universele Redacteur ](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven.<br> - [ de Redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) voor op vorm-gebaseerde het uitgeven. | 6,5 LTS GA |

### Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5 LTS. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging | Versie (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic wordt niet ondersteund. | Migreer aan [ AEM CIF ](/help/commerce/cif/migration.md). | 6,5 LTS GA |
| Oplossingen | Sociaal/Gemeenschappen worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Screens | Screens wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `dam-pim` en `dam-rating` worden niet ondersteund omdat bundels afhankelijk zijn van sociale componenten. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` is verwijderd. | Gebruik de alternatieve api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` die is toegevoegd. | 6,5 LTS GA |
| Portal | AEM Portal Director wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | Bundel `com.adobe.granite.socketio` wordt verwijderd. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `com.adobe.granite.crx-explorer` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `crx2oak` wordt niet ondersteund. | Kies de relevante versie van [ Oak-upgrade ](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6,5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Guava | Alle guave-afhankelijkheden worden nu verwijderd in AEM en daarom maakt de `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` -bundel geen deel uit van AEM. | Klanten kunnen alleen guave toevoegen als ze afhankelijk zijn van guave of de guave-code indien mogelijk vervangen door Java-verzamelingen of andere alternatieven. | 6,5 LTS GA |
| `We.Retail` | `We-retail` -voorbeeldsite wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `oak-solr-osgi` -bundel wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.servicemix.bundles.abdera-parser` , `org.apache.servicemix.bundles.jdom` en `org.apache.sling.atom.taglib` worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.commons.io` -pakketten worden nu geëxporteerd uit `org.apache.commons.commons-io` . | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `javax.mail` -pakketten worden geëxporteerd uit de `com.sun.javax.mail` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `org.apache.jackrabbit.api` -pakketten worden nu geëxporteerd uit de `org.apache.jackrabbit.oak-jackrabbit-api` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `com.github.jknack.handlebars` wordt niet ondersteund | Kies de relevante [ versie ](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6,5 LTS GA |

## Bekende problemen {#known-issues}

### Issue with JSP scripting bundle in AEM 6.5.21-6.5.23 and AEM 6.5 LTS GA

AEM 6.5.21, 6.5.22, 6.5.23 en AEM 6.5 LTS GA schip met de `org.apache.sling.scripting.jsp:2.6.0` bundel, die een bekende kwestie bevat. De kwestie komt typisch onder hoge lading voor wanneer de instantie van AEM vele gezamenlijke verzoeken behandelt.

Wanneer dit probleem optreedt, kan een van de volgende uitzonderingen voorkomen in de foutenlogboeken naast verwijzingen naar `org.apache.sling.scripting.jsp:2.6.0` :

* `java.io.IOException: classFile.delete() failed`
* `java.io.IOException: tmpFile.renameTo(classFile) failed`
* `java.lang.ArrayIndexOutOfBoundsException: Index 0 out of bounds for length 0`
* `java.io.FileNotFoundException`

Een hotfix [ cq-6.5.lts.0-hotfix-NPR-42640 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-NPR-42640-1.2.zip) is beschikbaar om dit probleem op te lossen.

### Dispatcher-verbindingsfout met SSL-functie {#ssl-only-feature}

Wanneer het toelaten van de SSL-enige eigenschap in de plaatsingen van AEM, is er een bekende kwestie die connectiviteit tussen de instanties van Dispatcher en van AEM beïnvloedt. Nadat u deze functie hebt ingeschakeld, kunnen de gezondheidscontroles mislukken en kan de communicatie tussen Dispatcher- en AEM-instanties worden verstoord. Dit probleem doet zich met name voor wanneer klanten `https + IP` proberen te doorlopen van de Dispatcher naar AEM-instanties. Het heeft betrekking op SNI (de Verwijzing van de Naam van de Server) bevestigingsproblemen.

**Effect:**

* Fouten in de health check met HTTP 400-responscodes
* Gebroken verkeer tussen Dispatcher en AEM
* Inhoud kan niet correct worden aangeboden via de Dispatcher
* Verbindingsfouten bij gebruik van HTTPS met IP-adressen in Dispatcher-configuratie
* HTTP 400 &quot;Ongeldige SNI&quot;fouten wanneer het verbinden via HTTPS + IP

**Betrokken milieu&#39;s:**

* AEM-implementaties met Dispatcher-configuraties
* Systemen waarbij de functie Alleen SSL is ingeschakeld
* Dispatcher-configuraties die gebruikmaken van de methode `https + IP` connection to AEM instances

**Oplossing:**
Neem contact op met Customer Support van Adobe als dit probleem zich voordoet. Een hotfix [ cq-6.5.lts.0-hotfix-CQ-4359803 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq660/hotfixes/cq-6.5.lts.0-hotfix-CQ-4359803-1.0.2.zip) is beschikbaar om dit probleem op te lossen. Probeer alleen SSL-functies in te schakelen voordat u de vereiste hotfix toepast.

## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [ download van het Product bij licensing.adobe.com ](https://licensing.adobe.com/)
* [ de Klantenondersteuning van Adobe van het Contact ](https://experienceleague.adobe.com/nl/docs/customer-one/using/home).