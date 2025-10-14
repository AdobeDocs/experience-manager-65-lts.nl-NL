---
title: Plaatsaanduidingstekst in AEM Forms
description: Plaatsaanduidingstekst is bedoeld om de gebruiker te helpen bij het invoeren van gegevens wanneer het besturingselement geen waarde heeft. Dit kan een samplewaarde of een korte beschrijving van de verwachte indeling zijn.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: author
docset: aem65
feature: Adaptive Forms,Foundation Components
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: 85ea442a-6e92-4fa8-aa0a-3076aac6f134
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '267'
ht-degree: 0%

---

# Plaatsaanduidingstekst in AEM Forms {#placeholder-text-in-aem-forms}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

De plaatsaanduidingstekst vertegenwoordigt een woord of korte woordgroep. Het is bedoeld om de gebruiker van gegevensingang te helpen wanneer de controle geen waarde heeft. Een plaatsaanduidingstekst kan een voorbeeldwaarde of een korte beschrijving van de verwachte indeling zijn. De tekst van de plaatsaanduiding wordt weergegeven voordat de gebruiker een waarde invoert. De tekst wordt verwijderd wanneer de gebruiker een waarde invoert of selecteert.

>[!NOTE]
>
>De plaatsaanduidingstekst moet, indien opgegeven, een waarde hebben die geen nieuwe regeltekens bevat.

![&#x200B; component van de Datum met en zonder placeholder tekst &#x200B;](assets/dat-picker-place-holder-text.png)

**A.** component van de Datum met placeholder tekst **B.** component van de Datum zonder placeholder tekst

AEM Forms biedt ondersteuning voor plaatsaanduidingstekst voor de velden Wachtwoord, Datumkiezer, Numeriek vak en Tekstvak.\
Plaatsaanduidingsteksten worden niet ondersteund voor de native HTML5-datumwidget. Een plaatsaanduidingstekst opgeven:

1. Klik met de rechtermuisknop op een component die Plaatsaanduidingstekst ondersteunt en klik op **Bewerken** . Het dialoogvenster Component bewerken wordt geopend.

1. Open de **Titel en tekst** tabel.
1. Specificeer een woord of een korte uitdrukking in het **Placeholder tekstvakje**. Klik **OK**.

>[!NOTE]
>
>Plaatsaanduidingstekst wordt niet ondersteund in Microsoft Internet Explorer 9.
