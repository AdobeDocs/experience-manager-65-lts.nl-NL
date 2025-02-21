---
title: AEM uitvoeren in productielodus
description: Leer hoe u AEM kunt uitvoeren in de productielodus.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Deploying
role: Admin
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# AEM uitvoeren in productielodus{#running-aem-in-production-ready-mode}

Met AEM 6.1 introduceert Adobe de nieuwe `"nosamplecontent"` -uitvoeringsmodus die de stappen moet automatiseren die nodig zijn om een AEM-instantie voor te bereiden voor implementatie in een productieomgeving.

De nieuwe looppaswijze zal niet alleen automatisch de instantie vormen om aan de veiligheid beste praktijken te houden die in veiligheidscontrolelijst worden beschreven, maar zal ook alle toepassingen en configuraties van steekproefGeometrixx in het proces verwijderen.

>[!NOTE]
>
>Aangezien, wegens praktische redenen, de Klaar Wijze van de Productie van AEM slechts de meeste taken nodig zal behandelen om een instantie te beveiligen, adviseert men hoogst u [ Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md) alvorens met uw productiemilieu te leven.
>
>Houd er ook rekening mee dat het uitvoeren van AEM in de productieklaar de toegang tot CRXDE Lite in feite uitschakelt. Als u het voor het zuiveren doeleinden nodig hebt, zie [ toelatend CRXDE Lite in AEM ](/help/sites-administering/enabling-crxde-lite.md).

![ chlimage_1-83 ](assets/chlimage_1-83a.png)

Als u AEM wilt uitvoeren in de modus gereed voor productie, hoeft u alleen maar de `nosamplecontent` via de `-r` -schakelaar voor de uitvoeringsmodus toe te voegen aan uw bestaande opstartargumenten:

```shell
java -jar aem-quickstart.jar -r nosamplecontent
```

U kunt bijvoorbeeld de productie gebruiken die klaar is om een auteurinstantie te starten met MongoDB-persistentie zoals deze:

```shell
java -jar aem-quickstart.jar -r author,crx3,crx3mongo,nosamplecontent -Doak.mongo.uri=mongodb://remoteserver:27017 -Doak.mongo.db=aem-author
```

## Verandert een deel van de Productie Klaar Wijze {#changes-part-of-the-production-ready-mode}

Meer specifiek, worden de volgende configuratieveranderingen uitgevoerd wanneer AEM op productie klaar wijze in werking wordt gesteld:

1. De **bundel van de Steun CRXDE** ( `com.adobe.granite.crxde-support`) wordt onbruikbaar gemaakt door gebrek op productie klaar wijze. Het kan op elk moment worden geïnstalleerd vanaf de openbare Maven-opslagplaats van Adobe. Versie 3.0.0 is vereist voor AEM 6.1.

1. De **Apache die Eenvoudige Toegang WebDAV van WebDAV tot bewaarplaatsen** ( `org.apache.sling.jcr.webdav`) bundel zal slechts op **auteur** instanties beschikbaar zijn.

1. Nieuwe gebruikers moeten het wachtwoord wijzigen bij de eerste aanmelding. Dit is niet van toepassing op de beheerder.
1. **produceert zuivert info** wordt onbruikbaar gemaakt voor **Apache Sling JavaScript Handler**.

1. **In kaart gebrachte inhoud** en **produceren zuivert info** wordt onbruikbaar gemaakt voor **Apache die de Behandelaar van JSP Manuscript** schrapt.

1. De **filter van de Dag CQ WCM** wordt geplaatst aan `edit` op **auteur** en `disabled` op **publiceert** instanties.

1. De **Manager van de Bibliotheek van Adobe Granite HTML** wordt gevormd met de volgende montages:

   1. **Minify:** `enabled`
   1. **zuivert:** `disabled`
   1. **Gzip:** `enabled`
   1. **Timing:** `disabled`

1. **Apache Sling GET Servlet** wordt geplaatst om veilige configuraties door gebrek te steunen, als volgt:

| **Configuratie** | **Auteur** | **publiceer** |
|---|---|---|
| TXT-uitvoering | uitgeschakeld | uitgeschakeld |
| HTML-uitvoering | uitgeschakeld | uitgeschakeld |
| JSON-uitvoering | enabled | enabled |
| XML-uitvoering | uitgeschakeld | uitgeschakeld |
| json.maximumresults | 1000 | 100 |
| Automatische index | uitgeschakeld | uitgeschakeld |
