---
title: Regels voor gegevensbescherming en gegevensbescherming - Adobe Experience Manager-gereedheid
description: Meer informatie over Adobe Experience Manager-ondersteuning voor de verschillende Data Protection and Data Privacy Regulations. Het omvat de algemene gegevensbeschermingsverordening van de EU (GDPR), de California Consumer Privacy Act en de wijze waarop een nieuw AEM-project moet worden uitgevoerd.
contentOwner: AEM Docs
topic-tags: introduction, grdp
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/MANAGING
docset: aem65
solution: Experience Manager, Experience Manager 6.5
feature: Compliance
role: Developer,Leader,Architect,Data Architect,User
source-git-commit: d1297182b801ff4db163b8ae91332f5aebb94b9b
workflow-type: tm+mt
source-wordcount: '745'
ht-degree: 0%

---

# Adobe Experience Manager Readiness for Data Protection and Data Privacy Regulations {#aem-readiness-for-data-protection-and-data-privacy-regulations}

>[!WARNING]
>
>De inhoud van dit document is geen juridisch advies en is niet bedoeld als vervanging van juridisch advies.
>
>Raadpleeg de juridische afdeling van uw bedrijf voor advies over regelgeving inzake gegevensbescherming en gegevensbescherming.

>[!NOTE]
>
>Voor meer informatie over de reactie van Adobe op privacykwesties, en wat het voor u als klant van Adobe betekent, zie [ het Centrum van de Privacy van Adobe ](https://www.adobe.com/privacy.html).

Adobe biedt documentatie en procedures (met API&#39;s, indien beschikbaar), waarmee de privacybeheerder van de klant of de AEM-beheerder gegevensbeschermings- en privacyverzoeken kan verwerken. Het kan u helpen om aan deze verordeningen te voldoen. De gedocumenteerde procedures laten klanten de regelgevende verzoeken manueel in werking stellen of door in APIs, waar beschikbaar, van een extern portaal of de dienst te roepen.

>[!CAUTION]
>
>De hier gedocumenteerde details zijn beperkt tot Adobe Experience Manager.
>
>Gegevens van een andere Adobe On-demand Service, samen met eventuele gerelateerde privacyverzoeken, vereisen dat op die service actie wordt ondernomen.
>
>Voor meer informatie, zie [ het Centrum van de Privacy van Adobe ](https://www.adobe.com/privacy.html).

## Inleiding {#introduction}

Exemplaren van Adobe Experience Manager, en de toepassingen die erop draaien, zijn eigendom van en worden geëxploiteerd door klanten van Adobe.

Bijgevolg vallen gegevensbeschermingsvoorschriften, zoals GDPR, CCPA en andere, grotendeels onder de verantwoordelijkheid van de klanten.

In een korte inleiding bevatten de verordeningen betreffende de privacy en bescherming van gegevens nieuwe regels die moeten worden gevolgd door de taken van:

* Bedrijfsentiteiten (CCPA) en/of gegevensverwerkingsverantwoordelijken (GDPR)

* Dienstverleners (CCPA) en/of gegevensverwerkers (GDPR)

De belangrijkste bepalingen van deze verordeningen zijn:

1. Uitgebreide definitie van persoonsgegevens zodat deze alle unieke id&#39;s omvat, zoals direct en indirect identificeerbare gegevens.

2. Versterking van de toestemmingseisen.

3. Meer aandacht voor verwijderingsrechten (gegevenswissing).

4. Uitschakelen van verkoop van gegevens.

Voor Adobe Experience Manager:

* De instanties en toepassingen die erop worden uitgevoerd, zijn eigendom van en worden beheerd door de klant.

   * De klant beheert de regulerende rollen, met inbegrip van BedrijfsEntiteiten en Dienstverlener, het Controlemechanisme van Gegevens, en de Bewerker van Gegevens, onder andere.

   * De Adobe Experience Platform Privacy Service maakt geen deel uit van de workflow voor AEM, zoals in het onderstaande diagram wordt geïllustreerd.

* AEM bevat documentatie en procedures waarmee de privacybeheerder van de klant en/of de AEM-beheerder de privacyregelgevingsaanvragen kunnen uitvoeren; handmatig of via API&#39;s, indien beschikbaar.

* Er is geen nieuwe service of interface toegevoegd.

   * In plaats daarvan worden procedures en APIs gedocumenteerd voor gebruik door klant UIs/portals die verzoeken van de privacyverordening behandelen.

* AEM biedt geen kant-en-klare gereedschappen ter ondersteuning van de workflow voor privacyverzoeken.

   * Adobe biedt documentatie en procedures voor de privacybeheerder van de klant en de AEM-beheerder, zodat deze handmatig aanvragen kunnen uitvoeren die betrekking hebben op de privacyregels.

Adobe biedt procedures voor het verwerken van privacyverzoeken met betrekking tot Access, Delete en Opt-Out voor Adobe Experience Manager. Soms zijn er API&#39;s beschikbaar die kunnen worden aangeroepen via een door de klant ontwikkeld portaal of scripts om te helpen met automatisering.

In het volgende diagram ziet u hoe een workflow voor privacyverzoeken eruit kan zien (geïllustreerd met Adobe Experience Manager 6.5):

![ de Bescherming van Gegevens en Privacy ](assets/data-protection-and-privacy-01.png)

## Adobe Experience Manager en gereedheid voor regelgeving {#aem-and-regulatory-readiness}

Zie de volgende secties voor documentatie over regelgeving voor productgebieden van AEM.

## AEM Foundation {#aem-foundation}

Zie [ Behandelende de Bescherming van Gegevens en de Verzoeken van de Privacy voor de Stichting van AEM ](/help/sites-administering/handling-gdpr-requests-for-aem-platform.md).

## AEM die in de inzameling van de statistieken van het samengevoegde gebruik kiest {#aem-opting-into-aggregate-usage-statistics-collection}

Zie [ Geaggregeerde de Verzameling van de Statistieken van het Gebruik ](/help/sites-deploying/opt-in-aggregated-usage-statistics.md).

## AEM Sites {#aem-sites}

Zie [ AEM Sites - de Beveiliging van Gegevens en Readiness van de Privacy.](/help/sites-administering/gdpr-compliance-sites.md)

## AEM-integratie met Adobe Target en Adobe Analytics {#aem-integration-with-adobe-target-adobe-analytics}

Deze Adobe Experience Manager-integratie is mogelijk met services die geschikt zijn voor gegevensbescherming en privacy (bijvoorbeeld GDPR of CCPA). In AEM worden geen persoonsgegevens van Adobe Target of Adobe Analytics met betrekking tot de integratie opgeslagen.

Raadpleeg de volgende secties voor meer informatie:

* [ Adobe Target - het Overzicht van de Privacy ](https://developer.adobe.com/target/before-implement/privacy/cmp-privacy-and-general-data-protection-regulation/?lang=en)

* [ Workflow van de Privacy van Gegevens van Adobe Analytics ](https://experienceleague.adobe.com/docs/analytics/admin/admin-tools/data-governance/an-gdpr-workflow.html)

## AEM Forms {#aem-forms}

AEM Forms omvat componenten en workflows die gegevens vastleggen, verwerken en opslaan om bedrijfsprocessen te ordenen en digitale transacties te voltooien. De verschillende componenten gebruiken verschillende gegevensopslag en staan integratie met douanegegevensopslag eveneens toe. In de volgende documentatie worden de procedures en richtlijnen beschreven voor de toegang tot en de verwerking van gebruikersgegevens ter ondersteuning van gegevensbeveiliging en privacyworkflows (bijvoorbeeld GDPR of CCPA) voor een component.

* [Forms Portal](/help/forms/using/forms-portal-handling-user-data.md)
* [Correspondentenbeheer](/help/forms/using/correspondence-management-handling-user-data.md)
* [Integratie met Adobe Sign](/help/forms/using/integration-adobe-sign-handling-user-data.md)
* [Forms-gecentreerde workflows op OSGi](/help/forms/using/forms-workflow-osgi-handling-user-data.md)
* [ de werkschema&#39;s van Forms JEE ](/help/forms/using/forms-workflow-jee-handling-user-data.md) (slechts AEM Forms JEE)
* [ Veiligheid van het Document ](/help/forms/using/document-security-handling-user-data.md) (AEM Forms JEE slechts)
* [ Beheer van de Gebruiker ](/help/forms/using/user-management-handling-user-data.md) (AEM Forms JEE slechts)
