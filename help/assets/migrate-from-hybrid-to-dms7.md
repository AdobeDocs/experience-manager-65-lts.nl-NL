---
title: Migreren van dynamische media - hybride modus naar dynamische media - S7-modus
description: Leer hoe u uw instantie van Dynamische media - hybride modus naar Dynamische media - S7-modus migreert
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: dynamic-media
content-type: reference
docset: aem65
role: User, Admin
feature: Scene7 Mode,Hybrid Mode
solution: Experience Manager, Experience Manager Assets
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '527'
ht-degree: 2%

---

# Info over de overgang van dynamische media-hybride naar dynamische media-Scene7 {#about-migrating}

Dynamic Media-Hybrid is een oudere versie van Dynamic Media-integratie met Adobe Experience Manager. De Hybride versie werd voor het eerst geïntroduceerd in Adobe Experience Manager 6.1. Hoewel Adobe de hybride modus blijft ondersteunen, heeft deze de voorkeur en is Dynamic Media-Scene7 de voorkeursmodus. De hybride wijze steunt ook geen nieuwe eigenschappen zoals Slim Gewas en panoramische beelden, terwijl de Dynamische media-Scene7 hen steunt.

De extra belangrijkste verschillen tussen Dynamische media-Hybride en Dynamische media-Scene7 omvatten het volgende:

* Structuur van URL&#39;s.
* Ingestie van video&#39;s.
* Het maken en opslaan van afbeeldingsuitvoeringen.
* Configuratie en referenties van de cloud (provisioning).

Er zijn twee opties beschikbaar wanneer u van Dynamische media-Hybride naar Dynamische media-Scene7 beweegt. De eerste optie is eenvoudig een nieuw geval van Dynamische Media-Scene7 op Experience Manager te verstrekken. De tweede optie moet uw bestaande instantie van Dynamische media-Hybride aan Dynamische media-Scene7 migreren. Met deze optie geeft u een overzicht van het tabelformulier onder de stappen en overwegingen die u tijdens het verplaatsen wilt uitvoeren.

>[!IMPORTANT]
>
>Adobe raadt aan dat u een dynamische media-hybride implementatie niet naar Dynamic Media-Scene7 migreert op live productieinstanties.

## Optie 1 - Voorziening een nieuw geval van Dynamische Media-Scene7 op Experience Manager {#provision-new-dms7}

Overweeg eenvoudig beginnend vers met een nieuwe, provisioned instantie van Dynamic Media-Scene7 op Adobe Experience Manager. Naast het opnemen en verwerken van middelen via Dynamic Media Cloud Service wordt een Adobe-controle van het gebruik van middelen, workflows en componenten met klem aanbevolen. Vaak kunt u aangepaste componenten en workflows vervangen door gebruik te maken van nieuwere, out-of-the-box functies.

## Optie 2 - Migreer uw bestaande instantie van Dynamische media-Hybride aan Dynamische media-Scene7 {#process-for-migrating}

| Stap | Taak | Overwegingen |
|---|---|---|
| 1 | Clone Dynamic Media-Hybrid Author-instantie. | Behoud uw bestaande instantie van Dynamic Media-Hybrid Author voor terugvaldoeleinden tot de resterende stappen in dit migratieproces met succes zijn voltooid. |
| 2 | De gekloonde instantie van de Auteur van het begin op Dynamische media-Scene7 wijze. |  |
| 3 | In de Diensten van de Wolk van Adobe Experience Manager, vorm Dynamische Media met Dynamische media-Scene7 geloofsbrieven. | Adobe moet Dynamische media-Scene7 levering goedkeuren. Als dusdanig, hebt u gelijktijdig Dynamic MediaM-Hybrid en Dynamische media-Scene7 milieu&#39;s die door Adobe, maar slechts voor een beperkte tijd worden gesteund. |
| 4 | Maak een migratiebundel, zodat u elementen naar wens kunt invoeren.<br> Schrap lokale PTIFFs die tijdens aanvankelijke opname in Dynamische media-Hybrid werden gecreeerd. | Als alle elementen momenteel beschikbaar zijn in de instantie Dynamic Media-Hybrid, bevat een kloon van die elementen al deze elementen. Daarom is geen bundel nodig. |
| 5 | Werk de workflow voor het bijwerken van elementen uit, zodat u elementen kunt synchroniseren met Dynamic Media Cloud Service. | Adobe raadt u aan de updateworkflow batchgewijs uit te voeren, zodat u deze kunt comprimeren. |
| 6 | Viewer-, afbeeldings- en videovoorinstellingen migreren. |  |
| 7 | Doorloop de elementen waarnaar wordt verwezen in het beheer van webinhoud en werk de bijbehorende URL&#39;s bij. |  |
| 8 | Migreer om het even welke douanewerkschema&#39;s die u de nieuwe Dynamische media-Scene7 wijze (handupdates) wilt steunen. |  |
| 9 | Verifieer uw upload en configuratie van het Beheer van de Inhoud van het Web. |  |
| 10 | Na controle, krijg goedkeuring om Dynamische media-Hybride Auteur onbruikbaar te maken (handhaaf als reserve). |  |
| 11 | Verwijder de Dynamic Media-Hybrid Author-instantie na ongeveer een maand succesvol gebruik van Dynamic Media-Scene7. |  |
