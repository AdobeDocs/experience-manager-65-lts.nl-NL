---
title: Backbone-interactie
description: Conceptuele informatie over het gebruik van Backbone JavaScript-modellen in de AEM Forms-werkruimte.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
exl-id: c04d7d09-9d92-4a6c-b00f-7386a12ef5eb
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '436'
ht-degree: 0%

---

# Backbone-interactie{#backbone-interaction}

Backbone is een bibliotheek die helpt bij het maken en volgen van MVC-architectuur in webtoepassingen. Het basisidee van Backbone is uw interface te organiseren in logische meningen, gesteund door modellen, die elk onafhankelijk kunnen worden bijgewerkt wanneer het model verandert, zonder het moeten de pagina opnieuw tekenen. Voor meer informatie over Backbone, zie [ https://backbonejs.org ](https://backbonejs.org/).

Enkele belangrijke concepten zijn:

**backbonemodel** bevat gegevens, en de meeste logica met betrekking tot dit gegeven.

**de mening van de Backbone** die wordt gebruikt om de staat van het overeenkomstige model te vertegenwoordigen. Een backboneweergave gedraagt zich eigenlijk als een controller, luisterend naar gebruikersinterfacegebeurtenissen zoals klikken door de gebruiker of naar modelgebeurtenissen (zoals gewijzigde gegevens) en wijzigt de gebruikersinterface op de juiste wijze.

**het malplaatje van HTML** A omslag die placeholders heeft die door het model worden bevolkt.

**de werkruimte van AEM Forms** bevat verscheidene individuele componenten. Elke component:

* Vertegenwoordigt één logisch interface-element.
* Dit kan een verzameling van vergelijkbare componenten zijn.
* Opgemaakt uit het backbonemodel, de backboneweergave en de HTML-sjabloon.
* Bevat verwijzing naar de dienst.
* Bevat een verwijzing naar de vereiste hulpprogramma&#39;s.

Wanneer een component wordt geïnitialiseerd, worden de volgende objecten gemaakt:

* Er wordt een nieuwe instantie van het backbonemodel voor de component gemaakt. De service wordt in het model geïnjecteerd.
* Er wordt een nieuw exemplaar van de backboneweergave gemaakt.
* Instantie van het bijbehorende model, HTML-sjabloon en Hulpprogramma&#39;s worden in de weergave geïnjecteerd.

In de backboneweergave is er een gebeurteniskaart die de verschillende gebeurtenissen in kaart brengt die zich als gevolg van gebruikersinterfaceinteractie met een overeenkomstige manager kunnen voordoen. Deze toewijzing wordt in werking gesteld zodra een component wordt geïnitialiseerd.

Wanneer een mening wordt geïnitialiseerd, roept de mening zijn overeenkomstig model om gegevens van server te halen. Zodra alle gegevens die door een weergave worden vereist, beschikbaar zijn, worden de gegevens door de weergave gerenderd in de indeling die is opgegeven in de HTML-sjabloon. Meerdere weergaven kunnen hetzelfde model voor communicatie delen.

![ de vormenbackbonemening van AEM ](do-not-localize/aem_forms_workflow.png)

Een voorbeeld:

1. De gebruiker klikt een taakmalplaatje in de takenlijst.
1. De mening van de taak luistert aan de klik, en de vraag geeft functie op het taakmodel terug.
1. Het model van de taak roept daarna de dienst aan die een gemeenschappelijk punt voor al mededeling met de server van AEM Forms is.
1. De klasse van de dienst roept AEM Forms REST eindpunt voor teruggeeft methode via ajax.
1. De succescallback voor deze Ajax aanroeping wordt bepaald in het taakmodel.
1. Het model van de taak heft een backbonegebeurtenis als bericht op dat vraag teruggeeft volledig is.
1. In een andere weergave luistert de weergave met taakdetails naar deze gebeurtenis vanuit het taakmodel.
1. De mening van de details van de taak verandert dan het malplaatje van taakdetails om de teruggegeven taak (vorm, details, gehechtheid, nota&#39;s, etc.) aan de gebruiker te tonen.
