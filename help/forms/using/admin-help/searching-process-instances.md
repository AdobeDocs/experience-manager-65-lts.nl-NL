---
title: Zoeken naar procesinstanties
description: Gebruik de pagina van het Onderzoek van het Proces om onderzoekscriteria in te gaan om een procesgeval te vinden.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_forms_workflow
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e358ee51-c23f-4737-9dcf-3193ed541bbb
source-git-commit: 51342861dd01e659999c19fbe0274e8d3cbcf8c4
workflow-type: tm+mt
source-wordcount: '458'
ht-degree: 0%

---

# Zoeken naar procesinstanties{#searching-for-process-instances}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Gebruik de pagina van het Onderzoek van het Proces om onderzoekscriteria in te gaan om een procesgeval te vinden. U kunt de pagina van het Onderzoek van het Proces van de pagina van Forms Workflow toegang hebben. Of, kunt u **Onderzoek** op de pagina van de Instantie van het Proces klikken.

U kunt basiscriteria invoeren om een algemene zoekopdracht uit te voeren, specifieke kenmerken om een gedetailleerde zoekopdracht uit te voeren of een combinatie van basiscriteria en specifieke kenmerken om een gecombineerde zoekopdracht uit te voeren.

## Een algemene zoekopdracht uitvoeren {#perform-a-general-search}

Een algemene zoekopdracht naar een proces is het meest geschikt als u de proces-id van de procesinstantie kent. Of als u op zoek bent naar een groep verwante procesinstanties of als slechts een paar procesinstanties actief zijn.

Voer de basiscriteria in voor het uitvoeren van een algemene zoekopdracht. Als u meerdere criteria invoert, wordt de zoekopdracht uitgevoerd met een impliciete AND-voorwaarde.

1. Klik in de beheerconsole op Services > Forms Workflow > Process Search.
1. Geef op de pagina Zoeken in proces onder Algemeen zoeken de volgende criteria op:

   * **identiteitskaart van het Proces:** het positieve geheel dat elke unieke procesinstantie identificeert.
   * **Status van het Proces:** selecteer een status van de lijst.
   * **Toepassing:** selecteer een toepassing van de lijst. Slechts worden de opgestelde toepassingen getoond.
   * **Naam van het Proces - Versie:** Selecteer een procesnaam van het menu. Slechts worden de opgestelde processen getoond.

1. Klik **Onderzoek**. De pagina Procesinstantie wordt weergegeven met een overzicht van de gevonden instanties.

## Gedetailleerde zoekopdrachten uitvoeren naar een proces {#perform-a-detailed-search-for-a-process}

U kunt specifieke kenmerken invoeren om een gedetailleerde zoekopdracht uit te voeren. Een gedetailleerde zoekopdracht is het meest geschikt als u veel procesinstanties uitvoert en u de mogelijke zoekopdrachten aan de hand van bepaalde criteria moet beperken.

1. Klik in de beheerconsole op Services > Forms Workflow > Process Search.
1. Geef op de pagina Zoeken in proces onder Gedetailleerd zoeken de eerste criteria op die u hebt ingesteld:

   * Selecteer een kenmerk in de lijst Kenmerk.
   * Selecteer een operator in de lijst Filter.
   * Typ in het vak Waarde een waarde die geschikt is voor het geselecteerde kenmerk.

1. Als u nog een rij wilt toevoegen, selecteert u Meer filters. Er wordt een andere set met kenmerken-, filter- en waardenlijsten weergegeven en een lijst met voorwaarden.
1. Selecteer AND of OR onder Voorwaarde. Herhaal desgewenst de stappen 1 tot en met 3 om uw zoekopdracht verder te beperken.
1. Als u rijen wilt toevoegen of verwijderen, klikt u op Meer filters of Minder filters. U kunt een tot vier rijen hebben.
1. Klik **Onderzoek**. De pagina Procesinstantie wordt weergegeven met een overzicht van de gevonden instanties.

Zie ook [&#x200B; Ongeveer de statussen van de procesinstantie &#x200B;](/help/forms/using/admin-help/processes.md#about-process-instance-statuses).

## Een gecombineerde zoekopdracht naar een proces uitvoeren {#perform-a-combined-search-for-a-process}

Als u een zoekopdracht wilt maken die zowel algemene als gedetailleerde criteria gebruikt, voert u waarden in in beide gebieden op de pagina Zoeken in proces. Het systeem past een impliciet `AND` toe tussen de twee gebieden.

Als de zoekopdracht te smal is, worden er geen exemplaren gevonden.
