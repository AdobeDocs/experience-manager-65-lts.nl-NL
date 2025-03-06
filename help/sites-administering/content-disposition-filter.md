---
title: Filter voor inhoudsafzetting
description: Leer hoe te om de Filter van de Verplaatsing van de Inhoud te gebruiken om aanvallen van XSS te verhinderen.
contentOwner: trushton
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: Security
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: 997cb6f3-1ef8-409c-acea-157d5b27a6b2
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '225'
ht-degree: 0%

---

# Filter voor inhoudsafzetting {#content-disposition-filter}

Inhoudsverwijderingsfilter is een beveiligingsfunctie tegen XSS-aanvallen op SVG-bestanden.

Na installatie blokkeert het filter de toegang tot alle elementen. U kunt bijvoorbeeld geen PDF online bekijken. In deze sectie wordt beschreven hoe u het filter naar wens kunt configureren.

## Filter voor inhoudsafzetting configureren {#configure-content-disposition-filter}

U kunt [ Apache bekijken die de Filter van de Verplaatsing van de Inhoud in GitHub ](https://github.com/apache/sling-org-apache-sling-security/blob/master/src/main/java/org/apache/sling/security/impl/ContentDispositionFilterConfiguration.java) schikt.

De opties voor het filter voor het verplaatsen van inhoud bieden de volgende functionaliteit:

* **de Wegen van de Verplaatsing van de Inhoud:** een lijst van wegen waar de filter wordt toegepast gevolgd door een lijst van mime-types om op die weg uit te sluiten. Dit pad moet een absoluut pad zijn en kan aan het einde een jokerteken (`*`) bevatten, zodat elk bronnenpad overeenkomt met het opgegeven padvoorvoegsel. `/content/*:image/jpeg,image/svg+xml` past het filter bijvoorbeeld toe op elk knooppunt in `/content?` , behalve op JPG- en SVG-afbeeldingen.

* **Uitgesloten Wegen van het Middel:** Een lijst van uitgesloten middelen, moet elk middelweg als absolute en volledig gekwalificeerde weg worden gegeven. Overeenkomende voorvoegsels/jokertekens worden niet ondersteund.

* **laat voor Alle Wegen van het Middel toe:** Deze vlag controleert of om deze filter voor alle wegen toe te laten, behalve de uitgesloten die wegen door Uitgesloten Wegen van het Middel worden bepaald. Als u deze markering instelt op &#39;true&#39;, worden paden voor het verwijderen van inhoud genegeerd. Onafhankelijk van de configuratie worden alleen bronpaden bedekt die een eigenschap met de naam `jcr:data` of `jcr:content/jcr:data` bevatten.
