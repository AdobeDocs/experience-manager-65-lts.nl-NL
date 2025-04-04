---
title: Het licentietype voor de implementatie bijwerken
description: Werk het licentietype voor de implementatie bij met behulp van de pagina Change License in de beheerconsole.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/get_started_with_administering_aem_forms_on_jee
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 21f062c6-bb9a-4e18-9fb2-2bb7f0050c9c
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '282'
ht-degree: 0%

---

# Het licentietype voor de implementatie bijwerken {#update-the-license-type-for-the-deployment}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Tijdens de installatie van AEM-formulieren hebt u Configuration Manager gebruikt om de benodigde AEM-formuliermodules te configureren en implementeren. Door gebrek, worden die modules gevormd met een vergunning van de 60 dagevaluatie. Gebruik de pagina van de Vergunning van de Verandering in beleidsconsole om het licentietype voor de plaatsing te veranderen. De momenteel opgestelde modules worden getoond op de pagina van de Vergunning van de Verandering.

Op de pagina Licentie wijzigen wordt informatie over uw licentie weergegeven:

* Het huidige type licentie
* De datum en tijd waarop de licentie voor het laatst is bijgewerkt
* Wie de laatste update heeft uitgevoerd
* Huidige status van de vergunning
* De datum waarop AEM-formulieren zijn geïnstalleerd
* De datum waarop de huidige licentie vervalt

>[!NOTE]
>
>De vergunningsverandering is op alle opgestelde modules van toepassing. Voordat u het licentietype wijzigt, moet u de implementatie van modules die geen licentie hebben. Selecteer niet het licentietype Productie als de lijst met geïmplementeerde modules andere modules bevat dan de modules die u van Adobe hebt aangeschaft.

## Het licentietype bijwerken {#update-the-license-type}

1. Klik op Licentie verlenen in de beheerconsole.
1. Lees de gebruiksrechtovereenkomst voor AEM-formulieren, selecteer Ik accepteer als u akkoord gaat met de voorwaarden van de overeenkomst en klik op Volgende.
1. Selecteer op de pagina Licentie wijzigen een licentietype:

   * **EVAL:** vergunning van de 60-dagevaluatie
   * **DEV:** Perpetual ontwikkelingsvergunning
   * **NFR:** vergunning van de 2 jaar evaluatie
   * **IDEV:** 1 jaar abonnement op het Programma van Adobe Developer
   * **Productie:** Perpetual vergunning

1. Selecteer Ja, wijziging van licentie is geldig voor alle geïmplementeerde modules.
1. Klik op Licentiewijziging bevestigen. Er wordt een bericht weergegeven met de mededeling dat de licentie is bijgewerkt.
