---
title: Informatie uit gebruikersgegevens toevoegen aan metagegevens voor het verzenden van formulieren
description: Leer hoe u met door de gebruiker verstrekte gegevens informatie aan metagegevens van een verzonden formulier kunt toevoegen.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms,Foundation Components
discoiquuid: 2c971da0-5bd5-40d1-820d-4efc2a44b49d
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: c746c8a9-58d5-494b-9846-b84495ebe98b
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '740'
ht-degree: 0%

---

# Informatie uit gebruikersgegevens toevoegen aan metagegevens voor het verzenden van formulieren{#adding-information-from-user-data-to-form-submission-metadata}

<span class="preview"> Adobe adviseert het gebruiken van de moderne en verlengbare gegevens vangt [&#x200B; Componenten van de Kern &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-core-components/using/adaptive-forms/introduction.html?lang=nl-NL) voor [&#x200B; het creëren van nieuwe Aangepaste Forms &#x200B;](/help/forms/using/create-an-adaptive-form-core-components.md) of [&#x200B; het toevoegen van Aangepaste Forms aan de pagina&#39;s van AEM Sites &#x200B;](/help/forms/using/create-or-add-an-adaptive-form-to-aem-sites-page.md). Deze componenten betekenen een aanzienlijke vooruitgang in de aanmaak van Adaptive Forms en zorgen voor indrukwekkende gebruikerservaring. In dit artikel wordt een oudere aanpak beschreven voor de auteur Adaptive Forms die gebruikmaakt van stichtingscomponenten. </span>

U kunt waarden die zijn ingevoerd in een element van het formulier gebruiken om metagegevensvelden van een concept of een formulier te berekenen. Met metagegevens kunt u inhoud filteren op basis van gebruikersgegevens. Een gebruiker voert bijvoorbeeld Jan Smit in het naamveld van het formulier. U kunt deze informatie gebruiken om metagegevens te berekenen die deze verzending kunnen categoriseren onder de JD voor initialen.

Als u metagegevensvelden wilt berekenen met door de gebruiker ingevoerde waarden, voegt u elementen van het formulier toe aan de metagegevens. Wanneer een gebruiker een waarde in dat element invoert, gebruikt een script de waarde om informatie te berekenen. Deze informatie wordt toegevoegd aan de metagegevens. Wanneer u een element als meta-gegevensgebied toevoegt, verstrekt u een sleutel voor het. De sleutel wordt toegevoegd als gebied in de meta-gegevens, en de gegevens verwerkte informatie wordt geregistreerd tegen het.

Een ziekteverzekeringsbedrijf publiceert bijvoorbeeld een formulier. In dit formulier legt een veld de pagina van de eindgebruikers vast. De klant wil alle verzendingen in een bepaald leeftijdsbereik controleren nadat meerdere gebruikers het formulier hebben verzonden. In plaats van alle gegevens te doorlopen die gecompliceerd worden door een toenemend aantal formulieren, helpen extra metagegevens de klant. De auteur van het formulier kan configureren welke eigenschappen/gegevens door de eindgebruiker worden ingevuld op het hoogste niveau, zodat de zoekopdracht het gemakkelijkst is. De extra meta-gegevens zijn door de gebruiker ingevulde informatie die op het hoogste niveau van de meta-gegevensknoop wordt opgeslagen, aangezien de auteur het vormde.

Een ander voorbeeld van een formulier waarin e-mailadres en telefoonnummer worden vastgelegd. Wanneer een gebruiker dit formulier anoniem bezoekt en het formulier verlaat, kan de auteur het formulier zodanig configureren dat de e-mailadres en het telefoonnummer automatisch worden opgeslagen. Dit formulier wordt automatisch opgeslagen en het telefoonnummer en de e-mailadres worden opgeslagen in het metagegevensknooppunt van het concept. Een gebruik-geval van deze configuratie is het lood management dashboard.

## Formulierelementen toevoegen aan metagegevens {#adding-form-elements-to-metadata}

Voer de volgende stappen uit om een element toe te voegen aan de metagegevens:

1. Open het adaptieve formulier in de bewerkingsmodus.\
   Om uw vorm in te openen geef wijze, in de vormenmanager uit, selecteer uw vorm en selecteer **Open**.
1. Op geef wijze uit, selecteer een component, uitgezocht ![&#x200B; gebied-niveau &#x200B;](assets/field-level.png) > **Aangepaste Container van de Vorm**, en selecteer dan ![&#x200B; cmp &#x200B;](assets/cmppr.png).
1. In sidebar, klik **Meta-gegevens**.
1. In de sectie van Meta-gegevens, voegt de klik **&#x200B;**&#x200B;toe.
1. Voeg scripts toe in het veld Waarde van het tabblad Metagegevens. Met de scripts die u toevoegt, worden gegevens verzameld uit elementen op het formulier en worden waarden berekend die worden doorgegeven aan de metagegevens.

   Bijvoorbeeld, **waar** wordt het programma geopend in de meta-gegevens als de ingegane leeftijd groter is dan 21, en **vals** wordt geregistreerd als het minder dan 21 is. U voert het volgende script in op het tabblad Metagegevens:

   `(agebox.value >= 21) ? true : false`

   ![&#x200B; manuscript van Meta-gegevens &#x200B;](assets/add-element-metadata.png)

   Script ingevoerd op het tabblad Metagegevens

1. Klik **OK**.

Nadat een gebruiker gegevens in het element invoert dat als meta-gegevensgebied wordt geselecteerd, wordt de gegevens gegevens gegevens geregistreerd in de meta-gegevens. U kunt de metagegevens bekijken in de opslagplaats die u hebt geconfigureerd voor het opslaan van metagegevens.

## Metagegevens voor bijgewerkte formulierverzending bekijken: {#seeing-updated-form-nbsp-submission-metadata}

In het bovenstaande voorbeeld worden de metagegevens opgeslagen in de CRX-opslagplaats. De metagegevens zien er als volgt uit:

![&#x200B; Metagegevens &#x200B;](assets/metadata_entry_new.png)

Als u een element van het controlevakje in de meta-gegevens toevoegt, worden de geselecteerde waarden opgeslagen als een komma gescheiden koord. U voegt bijvoorbeeld een component CheckBox toe aan het formulier en geeft de naam op als `checkbox1` . In de eigenschappen van de component van het controlevakje, voegt u de punten Rijvergunning, het Aantal van de Sociale Veiligheid, en Paspoort voor waarden 0, 1, en 2 toe.

![&#x200B; Opstellend veelvoudige waarden van een controledoos &#x200B;](assets/checkbox-metadata.png)

U selecteert een adaptieve formuliercontainer en voegt in de formuliereigenschappen een metagegevenssleutel `cb1` toe waarin `checkbox1.value` wordt opgeslagen, en publiceert het formulier. Wanneer een klant het formulier invult, selecteert de klant de opties Paspoort en burgerservicenummer in het veld Selectievakje. De waarden 1 en 2 worden opgeslagen als 1, 2 in het cb1-veld van de metagegevens voor verzending.

![&#x200B; de ingang van Meta-gegevens voor veelvoudige waarden die op een checkbox gebied &#x200B;](assets/metadata-entry.png) worden geselecteerd

>[!NOTE]
>
>Het bovenstaande voorbeeld is alleen bedoeld voor leerdoeleinden. Zorg ervoor dat u naar metagegevens zoekt op de juiste locatie zoals deze is geconfigureerd in uw AEM Forms-implementatie.
