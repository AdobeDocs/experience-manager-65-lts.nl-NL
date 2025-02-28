---
title: Opmerkingen bij de huidige release voor Adobe Experience Manager 6.5 LTS
description: Dit zijn de huidige Release-aantekeningen voor Adobe Experience Manager 6.5 LTS.
source-git-commit: 54f3f3019dcceda4307160aa2126c37835f6626e
workflow-type: tm+mt
source-wordcount: '783'
ht-degree: 4%

---


# Opmerkingen bij de huidige release voor Adobe Experience Manager 6.5 LTS {#release-notes}

## Gegevens vrijgeven {#release-information}

| Product | [!DNL Adobe Experience Manager] |
|---|---|
| Versie | 6,5 LTS |
| Type | Grote release |
| Algemene beschikbaarheidsdatum | 7 maart 2025 |

## Wat is er nieuw? {#what-s-new}

[!DNL Adobe Experience Manager] 6.5 LTS is een upgrade-release naar de [!DNL Adobe Experience Manager] 6.5 code base. Het verstrekt nieuwe en verbeterde functionaliteit, zeer belangrijke klantenmoeilijke situaties, de verhogingen van de hoge prioriteit, en algemene insectenmoeilijke situaties die op productstabilisatie gericht zijn. Het omvat ook [!DNL Adobe Experience Manager] 6.5 Service Pack-releases tot SP22.

De onderstaande lijst biedt een overzicht, terwijl op de volgende pagina&#39;s alle details worden weergegeven.

### [!DNL Experience Manager Foundation] {#experience-manager-foundation}

Het platform van [!DNL Adobe Experience Manager] 6.5 LTS bouwt voort op bijgewerkte versies van het op OSGi gebaseerde framework (Apache Sling en Apache Felix) en de Java™ Content Repository: Apache Jackrabbit Oak 1.68.0.

De QuickStart gebruikt Eclipse Jetty 11.0.x als servlet-engine.

#### Java™-ondersteuning  {#java-support}

* Ondersteuning voor Java™ 17.
* Overschrijf voor optimale prestaties de standaard GC-waarden met andere waarden. Voor meer informatie, zie [ installeer en werk ](/help/sites-deploying/custom-standalone-install.md) sectie bij.
* Java™ 17 onderhoudsupdates worden door Adobe gedistribueerd voor gebruik door klanten in AEM-gerelateerde projecten, wanneer deze niet openbaar zijn vanuit Oracle.

#### Uberjar Packaging {#uber-jar-packaging}

* Er is een klein verschil tussen de Uberjar-verpakking en de AEM 6,5 LTS. Voor meer informatie [ verwijs ](/help/sites-deploying/upgrading-code-and-customizations.md#update-the-aem-uber-jar-version-update-the-aem-uber-jar-version).

#### Upgrade {#upgrade}

* Voor details over de verbeteringsprocedure, zie de [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

## Installeren en bijwerken {#install-update}

Voor opstellingsvereisten, zie [ installatieinstructies ](/help/sites-deploying/custom-standalone-install.md).

Voor gedetailleerde instructies, zie [ verbeteringsdocumentatie ](/help/sites-deploying/upgrade.md).

## Ondersteunde platforms {#supported-platforms}

Vind de volledige matrijs van gesteunde platforms met inbegrip van steun-niveau op [ AEM 6.5 LTS technische vereisten ](/help/sites-deploying/technical-requirements.md).

>[!NOTE]
>
>Java™ 17 is de aanbevolen versie voor gebruik met AEM 6.5 LTS.


## Verouderde en verwijderde functies {#deprecated-and-removed-features}

Adobe evalueert continu de productfuncties, zodat oudere functies na verloop van tijd kunnen worden bijgewerkt of vervangen door modernere alternatieven om de algehele waarde voor de klant te verbeteren. Hierbij wordt altijd zorgvuldig gekeken naar compatibiliteit met oudere versies.

Om de aanstaande verwijdering of vervanging van Adobe Experience Manager (AEM) mogelijkheden mee te delen, zijn de volgende regels van toepassing:

1. Aankondiging van afkeuring komt voorop. Hoewel afgekeurd, zijn de mogelijkheden nog beschikbaar maar niet verder verbeterd.
1. Het verwijderen van verouderde mogelijkheden komt in de volgende belangrijkste versie op zijn vroegst voor. De werkelijke streefdatum voor verwijdering wordt later bekendgemaakt.

Dit proces biedt klanten minstens één releasecyclus om hun implementatie aan een nieuwe versie of opvolger van een vervangen capaciteit aan te passen, alvorens daadwerkelijke verwijdering.

### Verouderde functies {#deprecated-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn gemarkeerd als verouderd in AEM 6.5 LTS. In het algemeen worden functies die in een toekomstige versie moeten worden verwijderd, eerst vervangen, met een alternatief dat beschikbaar is.

Klanten wordt aangeraden na te gaan of zij de functie/functionaliteit in hun huidige implementatie gebruiken en plannen te maken om hun implementatie te wijzigen en het meegeleverde alternatief te gebruiken.

| Gebied | Functie | Vervanging | Versie (SP) |
|---|---|---|---|
| Sites | [ Redacteur van het KUUROORD ](/help/sites-developing/spa-overview.md) | De aangewezen redacteurs voor het beheren van hoofdloze inhoud in AEM zijn:<br> - [ de Universele Redacteur ](/help/sites-developing/universal-editor/introduction.md) voor het visuele uitgeven.<br> - [ de Redacteur van het Fragment van de Inhoud ](/help/assets/content-fragments/content-fragments-managing.md) voor op vorm-gebaseerde het uitgeven. | 6,5 LTS GA |

### Verwijderde functies {#removed-features}

Deze sectie bevat een lijst met functies en mogelijkheden die zijn verwijderd uit AEM 6.5 LTS. In eerdere versies waren deze mogelijkheden gemarkeerd als afgekeurd.

| Gebied | Functie | Vervanging | Versie (SP) |
|--- |--- |--- |--- |
| Commerce | AEM CIF Classic wordt niet ondersteund. | U zou aan [ AEM CIF ](/help/commerce/cif/migration.md) moeten migreren. | 6,5 LTS GA |
| Oplossingen | Sociaal/Gemeenschappen worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Screens | Screens wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `dam-pim` en `dam-rating` worden niet ondersteund omdat bundels afhankelijk zijn van sociale componenten. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Assets | `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettings()` is verwijderd. | Gebruik de alternatieve api `com.day.cq.dam.scene7.api.model.Scene7ViewerConfig#getSettingsList()` die is toegevoegd. | 6,5 LTS GA |
| Graniet | Bundel `com.adobe.granite.socketio` wordt verwijderd. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `com.adobe.granite.crx-explorer` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Graniet | `crx2oak` wordt niet ondersteund. | Kies relevante versie van [ eik-verbetering ](https://mvnrepository.com/artifact/org.apache.jackrabbit/oak-upgrade) | 6,5 LTS GA |
| Adobe | `com.adobe.cq.cq-searchpromote-integration` wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Guava | Alle guave-afhankelijkheden worden nu verwijderd in AEM en daarom maakt de `com.adobe.granite.osgi.wrapper.guava-15.0.0-0002` -bundel geen deel uit van AEM. | Klanten kunnen alleen guave toevoegen als ze afhankelijk zijn van guave of de guave-code indien mogelijk vervangen door Java-verzamelingen of andere alternatieven. | 6,5 LTS GA |
| We.Retail | De voorbeeldsite van de webwinkel wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `oak-solr-osgi` -bundel wordt niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.servicemix.bundles.abdera-parser` , `org.apache.servicemix.bundles.jdom` en `org.apache.sling.atom.taglib` worden niet ondersteund. | Geen vervanging beschikbaar. | 6,5 LTS GA |
| Source openen | `org.apache.commons.io` -pakketten worden nu geëxporteerd uit `org.apache.commons.commons-io` . | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `javax.mail` -pakketten worden geëxporteerd uit de `com.sun.javax.mail` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `org.apache.jackrabbit.api` -pakketten worden nu geëxporteerd uit de `org.apache.jackrabbit.oak-jackrabbit-api` -bundel. | Geen wijziging vereist. | 6,5 LTS GA |
| Source openen | `com.github.jknack.handlebars` wordt niet ondersteund | De relevante [ versie van de keuze ](https://mvnrepository.com/artifact/com.github.jknack/handlebars) | 6,5 LTS GA |


## Beperkte websites{#restricted-sites}

Deze websites zijn alleen beschikbaar voor klanten. Neem contact op met uw Adobe-accountmanager als u een klant bent en toegang nodig hebt.

* [ download van het Product bij licensing.adobe.com ](https://licensing.adobe.com/)
* [ de Klantenondersteuning van Adobe van het Contact ](https://experienceleague.adobe.com/en/docs/customer-one/using/home).
