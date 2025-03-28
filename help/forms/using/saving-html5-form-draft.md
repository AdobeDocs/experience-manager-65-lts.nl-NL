---
title: Een HTML5-formulier opslaan als concept
description: Sla een HTML5-formulier op als concept en hervat het invullen van het formulier in een later stadium.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 445e24af-cd1a-414d-bd01-9feb6631bbef
feature: HTML5 Forms,Mobile Forms
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: d03ea16d-0012-4f14-982a-70e2803ea211
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '299'
ht-degree: 0%

---

# Een HTML5-formulier opslaan als concept {#saving-an-html-form-as-a-draft}

U kunt een HTML5-formulier opslaan als concept en het invullen van het formulier later hervatten. Met Forms Portal kan elke gebruiker een HTML5-formulier opslaan en herstellen. Voeg de volgende configuraties toe aan het profielknooppunt om de functie Opslaan als concept in te schakelen:

## Aangepast profiel om de functie Opslaan als concept toe te staan {#custom-profile-to-allow-save-as-draft-feature}

Uit de doos, verstrekt AEM Forms a **sparen als Ontwerp** profiel. U kunt een formulier weergeven met het profiel Opslaan als concept om de conceptfunctionaliteit voor een HTML5-formulier in te schakelen. U kunt HTML specificeren teruggeeft profiel voor een vorm in [ Manager van Forms ](/help/forms/using/introduction-managing-forms.md).

Om sparen als functionaliteit van het Ontwerp voor uw bestaand [ douaneprofiel ](/help/forms/using/custom-profile.md) toe te laten, voeg de volgende eigenschappen aan uw knoop van het douaneprofiel toe:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschapnaam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>mfAllowFPDraft</td>
   <td>String</td>
   <td>true</td>
   <td><p>Hiermee wordt het opslaan als concept ingeschakeld</p> <p>voor dit profiel.</p> </td>
  </tr>
  <tr>
   <td>mfAllowAttachments</td>
   <td>String</td>
   <td>true</td>
   <td><p>Hiermee kunt u bijlagen uploaden</p> <p>met dit profiel.</p> </td>
  </tr>
 </tbody>
</table>

## Opslag en aanbieding opstellen {#drafts-storage-and-listing}

Na het toelaten sparen als functionaliteit van het Ontwerp voor een vorm; wanneer de vorm wordt bewaard, is het vermeld in de [ Concepten en component van de Verzending ](/help/forms/using/draft-submission-component.md). U kunt het opgeslagen formulier ophalen en invullen met de component Concept en Verzending.

Voeg de volgende eigenschap toe aan het profielknooppunt om formuliervermelding in te schakelen voor de component Concept en Verzending:

<table>
 <tbody>
  <tr>
   <td><strong>Eigenschapnaam</strong></td>
   <td><strong>Type</strong></td>
   <td><strong>Waarde</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>fp.enablePortalSubmit</td>
   <td>String</td>
   <td>true</td>
   <td>Concepten en formulieren na verzending in <br /> Forms Portal-component Concepten en verzenden weergeven</td>
  </tr>
 </tbody>
</table>

Standaard slaat AEM Forms de gebruikersgegevens die zijn gekoppeld aan het concept en de verzending van een formulier op in het knooppunt /content/forms/fp in het exemplaar Publish. U kunt uw leverancier van de douaneopslag toevoegen, voor details zie [ de opslag van de Douane voor de componenten van Concepten en van Verzending ](/help/forms/using/adding-custom-storage-provider-forms.md).
