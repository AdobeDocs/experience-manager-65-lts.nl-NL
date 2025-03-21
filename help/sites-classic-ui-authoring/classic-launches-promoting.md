---
title: Starten promoten
description: U moet opstartiepagina's promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina's vervangen door de inhoud van de gepromoveerde pagina.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: site-features
legacypath: /content/docs/en/aem/6-0/author/site-page-features/launches
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 1167735d-a13a-438e-bef8-205e27f59f4e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '315'
ht-degree: 0%

---

# Starten promoten{#promoting-launches}

U moet opstartiepagina&#39;s promoten om de inhoud vóór publicatie weer naar de bron (productie) te verplaatsen. Wanneer een startpagina wordt bevorderd, wordt de bijbehorende pagina van de bronpagina&#39;s vervangen door de inhoud van de gepromoveerde pagina. De volgende opties zijn beschikbaar bij het promoten van een startpagina:

* Of alleen de huidige pagina of de volledige lancering wordt bevorderd.
* Of de onderliggende pagina&#39;s van de huidige pagina worden bevorderd.
* Of de volledige lancering of slechts pagina&#39;s wordt bevorderd die zijn veranderd.

## Startpagina&#39;s promoten {#promoting-launch-pages}

Als u pagina&#39;s wilt promoten, voert u de volgende stappen uit tijdens het bewerken van de startpagina die u wilt promoten:

1. Op het **lusje van de Pagina** in Sidekick, klik **bevorderen Lanceer**.
1. Geef de pagina&#39;s op die u wilt promoten:

   * (Gebrek) om slechts de huidige pagina te bevorderen, uitgezochte **bevordert de Veranderingen van de Pagina in de Versie van de Productie**.
   * Om de kindpagina&#39;s van de huidige pagina ook te bevorderen, uitgezochte **omvat Subpagina&#39;s**.
   * Om alle pagina&#39;s in de lancering te bevorderen, uitgezochte **Bevordert Volledige Lancering aan de Versie van de Productie**.

1. Om de productiepagina&#39;s aan een werkschemapakket toe te voegen, selecteer **toevoegen aan het Pakket van het Werkschema** en dan het werkschemapakket selecteren.
1. Klik **bevorderen**.

## Promotiepagina&#39;s verwerken met AEM Workflow {#processing-promoted-pages-using-aem-workflow}

Gebruik workflowmodellen voor bulkverwerking van geconverteerde startpagina&#39;s:

1. Maak een workflowpakket.
1. Wanneer auteurs startpagina&#39;s promoten, slaan ze deze op in het workflowpakket.
1. Start een workflowmodel met het pakket als de payload.

Om een werkschema automatisch te beginnen wanneer de pagina&#39;s worden bevorderd, [ vormt een werkschemalancerer ](/help/sites-administering/workflows-starting.md#workflows-launchers) voor de pakketknoop.

U kunt bijvoorbeeld automatisch aanvragen voor paginanactivering genereren wanneer auteurs pagina&#39;s voor Starten promoten. Configureer een werkstroomstartprogramma om de workflow voor activering van aanvragen te starten wanneer het pakketknooppunt wordt gewijzigd.

![ chlimage_1-136 ](assets/chlimage_1-136.png)
