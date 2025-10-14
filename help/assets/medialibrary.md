---
title: Mediabibliotheek gebruiken voor elementair beheer van digitale elementen
description: '[!DNL Experience Manager Assets] en Mediabibliotheek voor middelenbeheer.'
contentOwner: AG
role: Architect, Leader
feature: Asset Management
hide: true
solution: Experience Manager, Experience Manager Assets
exl-id: 50a980e5-3b35-4485-9a5b-44d1a42a837c
source-git-commit: 51f6da4da0bb3f79aa6fa17371b8084b72de7546
workflow-type: tm+mt
source-wordcount: '553'
ht-degree: 0%

---

# Mediabibliotheek gebruiken voor elementair middelenbeheer {#manage-assets-using-media-library}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [&#x200B; klik hier &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/admin/medialibrary.html?lang=nl-NL) |
| AEM 6.5 | Dit artikel |

[!DNL Adobe Experience Manager] biedt verschillende mogelijkheden om elementen te beheren. Met de mediabibliotheek kunnen gebruikers een klein aantal elementen uploaden naar de opslagplaats, zoeken en gebruiken in de webpagina&#39;s en eenvoudige taken uitvoeren voor middelenbeheer op de middelen.

Mediabibliotheek is een lichte DAM-oplossing (Digital Asset Management) die gratis wordt geleverd met [!DNL Adobe Experience Manager Sites] -licentie. [!DNL Sites] is een WCM-service (Web Content Management). Mediabibliotheek werkt met alle mogelijkheden van Experience Manager.

[!DNL Adobe Experience Manager Assets] -licentie is apart verkrijgbaar. [!DNL Experience Manager Assets] biedt een robuuste verwerking van bedrijfsmiddelen via praktijkgevallen, aanpassingen voor metagegevens, schema&#39;s, zoekopdrachten en gebruikersinterface, en vele andere mogelijkheden die verder gaan dan wat de mediabibliotheek biedt.

## Vergunningsvereisten {#avail-media-library-license}

Klanten met een [!DNL Sites] -licentie hebben het recht om de Media Library te gebruiken. Het werkt met alle componenten van [!DNL Experience Manager].

Mediabibliotheek wordt geïnstalleerd als onderdeel van sites. Naast de licentie en installatie van Sites is geen extra licentie of pakket vereist.

## [!DNL Assets] versus mediabibliotheek {#assets-and-media-library}

Experience Manager Assets biedt DAM-functionaliteit op bedrijfsniveau. Assets-functionaliteit wordt geleverd met [!DNL Experience Manager] in één pakket. Gebruikers die geen Assets-licentie hebben aangeschaft, mogen de geavanceerde DAM-functies echter niet gebruiken. Zonder de vergunning van Assets, slechts zijn de [&#x200B; eigenschappen van de Bibliotheek van Media &#x200B;](#use-media-library) beschikbaar.

Als u wilt voorkomen dat [!DNL Assets] -functies waarvoor u geen licentie hebt, onbedoeld worden gebruikt, verwijdert u alle [!DNL Assets] -specifieke workflows, componenten, taxonomieën, opties en de [!DNL Assets] -beheerder uit [!DNL Experience Manager] . Zo voorkomt u dat uw gebruikers per ongeluk [!DNL Assets] -functies gebruiken waarvoor u geen licentie hebt verleend.

## Mediabibliotheek gebruiken {#use-media-library}

De mediabibliotheek biedt standaard DAM-functies voor de volgende gebruiksgevallen:

* Webpagina&#39;s die zijn gemaakt met [!DNL Adobe Experience Manager Sites] .
* Adaptieve formulieren en communicatie die zijn gemaakt met [!DNL Adobe Experience Manager Forms] .
* Ervaring met digitaal scherm die is gemaakt met [!DNL Adobe Experience Manager Screens] .
* [!DNL Assets] HTTP REST-API&#39;s voor bewerkingen zonder kop.

<!--
 TBD: Remove this after confirmation. May need to merge this list with the list provided by PMs.
* Static renditions

-->

Als u de functionaliteit van de mediabibliotheek wilt gebruiken, kunt u de standaardgebruikersinterface van [!DNL Experience Manager] gebruiken. De mediabibliotheek maakt deel uit van de installatie van [!DNL Experience Manager Sites] en er is geen aparte interface of invoegtoepassing vereist. Met behulp van de bestaande interface hebben de gebruikers van de Mediabibliotheek het recht om de volgende taken uit te voeren:

* Maak mappen om elementen te ordenen.
* Elementen uploaden.
* Elementen publiceren.
* Elementen bewerken, verplaatsen en kopiëren.
* Blader naar de elementen die u wilt gebruiken, filter en zoek (inclusief zoeken op basis van gelijkenis).
* Voeg waarden toe aan en bewerk de waarden in de metagegevensvelden, behalve het veld Slimme tags, die standaard beschikbaar zijn op het tabblad [!UICONTROL Basic] van de pagina [!UICONTROL Properties] van een element.
* Statische vertoningen toevoegen en verwijderen.
* Download mappen, elementen en elementenuitvoeringen.
* Elementversies maken.
* Revisietaken voor elementen maken en uitvoeren.
* Annoteer elementen.
* Voeg elementen aan [!DNL Sites] pagina&#39;s toe via de Inhoudszoeker.
* Gebruik [!DNL Content Fragments] .
* Gebruik HTTP REST- en GraphQL-API&#39;s voor [!DNL Content Fragments] en media-elementen waarnaar wordt verwezen, onder Sites-licentie.
* Marketing Cloud-integratie.
* Gebruikersinterface voor middelenbeheer aanpassen en uitbreiden.
* Heb toegang tot de Bouwer van de Vraag (API) om de onderzoeksfunctionaliteit uit te breiden.
* Statische tags maken.
* Projecten en taken van auteurs.
* Activiteitsstroom (tijdlijn).
* Opmerkingen en annotaties.

<!-- TBD: Define exactly which basic Assets workflow are available for use with Media Library?

As per PM, we must avoid stating such a list, as we do not have a list that makes sense in Cloud Service.
-->

>[!IMPORTANT]
>
>Vele geavanceerde gevallen van gebruik door DAM worden vervuld door [!DNL Experience Manager Assets]. Met de mediawisselaarlicentie kunt u alleen de vermelde gebruiksgevallen afhandelen via de mediawisselaar. Als een gebruiksgeval niet vermeld is, gebruik het niet met de vergunning van de Bibliotheek van Media. Neem contact op met Customer Support van Adobe als je vragen hebt.

U kunt geen slimme tags, [!DNL Asset] koppeling, [!DNL Asset] kiezer, bulksgewijs labelen, workflows van elementen of de standaard [!DNL Adobe Experience Manager] gebruikersinterface gebruiken voor toegang tot de mediabibliotheek zonder [!DNL Assets] licentie.

<!-- TBD: Add a CTA - how to contact Adobe for queries. -->

>[!MORELIKETHIS]
>
>* [&#x200B; DAM eigenschappen in  [!DNL Experience Manager Assets] &#x200B;](https://experienceleague.adobe.com/nl/docs/experience-manager-65-lts/content/assets/assets)
>* [[!DNL Experience Manager]  6.5 het productbeschrijving van Managed Services &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-experience-manager-managed-services.html)
>* [[!DNL Experience Manager]  6.5 on-premise productbeschrijving &#x200B;](https://helpx.adobe.com/nl/legal/product-descriptions/adobe-experience-manager-on-premise.html)
