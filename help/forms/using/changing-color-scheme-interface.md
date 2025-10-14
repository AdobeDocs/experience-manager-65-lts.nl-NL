---
title: Het kleurenschema van de interface wijzigen
description: Het kleurenschema van de gebruikersinterfacegedeelten van de AEM Forms-werkruimte selectief aanpassen.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: f15ead5f-d48c-401c-98c5-b58f93776f82
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Het kleurenschema van de interface wijzigen {#changing-the-color-scheme-of-the-interface}

U kunt het kleurenschema van de gebruikersinterfacegedeelten van de AEM Forms-werkruimte aanpassen aan uw wensen. Hier volgen enkele voorbeelden van representatieve aanpassingen van kleurschema&#39;s. Naast de stappen die in dit artikel worden besproken, zie [&#x200B; Algemene stappen voor de de werkruimteaanpassing van AEM Forms &#x200B;](/help/forms/using/generic-steps-html-workspace-customization.md).

## Bovenste navigatiebalk {#top-navigation-bar}

### Achtergrondafbeelding gebruiken {#using-background-image}

De navigatiebalk boven in de AEM Forms-werkruimte bijwerken.

1. Maak een achtergrondafbeelding om de kleur bij te werken. Geef het bestand een naam als newBackground.jpg.
1. Upload het bestand met de achtergrondafbeelding in de map /apps/ws/images met een WebDAV-client.

   >[!NOTE]
   >
   >Voor meer informatie, zie [&#x200B; Toegang WebDAV &#x200B;](/help/sites-administering/webdav-access.md).

1. Verwijs naar de nieuwe achtergrondafbeelding in /apps/ws/css/newStyle.css door de volgende stijl toe te voegen.

   ```css
   #header {
       background:#292929 url(../images/newBackground.jpg) repeat-x;
   }
   ```

### Kleureigenschap gebruiken in CSS {#using-color-property-in-css}

1. Voeg de volgende stijl toe aan newStyle.css op /apps/ws/css

   ```css
   #header {
   background : none;
   background-color: gray;
   }
   ```

## Categorieonderdeel {#category-component}

De component van de categorie toont de diverse categorieën van uw taken in het linkerpaneel. Als u de kleur wilt wijzigen, definieert u de achtergrondkleur in het element `.category` van het CSS-bestand.

## Taakcomponent {#task-component}

De taken worden getoond in het middelste paneel genoemd de Component TaskList. Als u de kleur van de stijl wilt wijzigen, wijzigt u de stijl die is gekoppeld aan de taakkiezer in de stijlpagina.
