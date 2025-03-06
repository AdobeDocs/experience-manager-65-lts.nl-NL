---
title: Welke testomgevingen zijn nodig?
description: Verschillende omgevingen moeten worden beschouwd als onderdeel van tests
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: f74fbf2b-62bb-4fac-9ecb-5ace90ba0275
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '169'
ht-degree: 0%

---

# Welke testomgevingen zijn nodig?{#which-test-environments-will-be-needed}

Als u wilt definiëren welke configuraties voor tests moeten worden gebruikt, moet u het volgende in overweging nemen:

**Ontwikkeling** - voor Eenheid, en bepaalde tests van de Integratie.

**het Testen** - voor de meeste tests.

**Levend** - voor definitieve prestaties en stresstests. Ook voor goedkeuringstests met de klant.

Bepaal welke gevallen u nodig hebt en waar (gewoonlijk ten minste een van beide voor alle testniveaus):

**Auteur** - Deze instantie staat auteurs toe om, inhoud in te voeren en te publiceren.

**publiceer** - Deze instantie stelt de website in zijn gepubliceerde vorm voor toegang van bezoekers voor.

Getest met de Dispatcher.

Ten slotte moet de werkelijke hardware in overweging worden genomen: eventuele prestatietests moeten worden uitgevoerd op een systeem dat zo dicht mogelijk bij de uiteindelijke live omgeving ligt. Daarom wordt ook aanbevolen het project te starten in een:

**Zachte Lancering** - Verminderde beschikbaarheid; die tijd voor prestatietests, het stemmen, en optimalisering in realistische omstandigheden op het productiemilieu toestaat.

**Harde Lancering** - Volledige beschikbaarheid.
