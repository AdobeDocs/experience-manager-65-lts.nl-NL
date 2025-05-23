---
title: Activiteitsstroom van digitale elementen in de tijdlijnweergave
description: In dit artikel wordt beschreven hoe u activiteitenlogboeken voor elementen op de tijdlijn kunt weergeven.
contentOwner: AG
feature: Asset Management
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: 453331b3-41f7-4bf1-90fc-afeaf40577c8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '200'
ht-degree: 7%

---

# Activiteitsstroom in tijdlijn {#activity-stream-in-timeline}

Deze functie geeft activiteitenlogboeken voor elementen op de tijdlijn weer. Als u een van de volgende bewerkingen met betrekking tot elementen uitvoert in [!DNL Adobe Experience Manager Assets] , wordt de tijdlijn door de functie voor de activiteitsstroom bijgewerkt met de activiteit.

De volgende bewerkingen worden in de activiteitsstroom aangemeld:

* Maken
* Verwijderen
* Downloaden (inclusief uitvoeringen)
* Publiceren
* Publiceren ongedaan maken
* Goedkeuren
* Afwijzen
* Verplaatsen

De activiteitenlogboeken die in de tijdlijn moeten worden weergegeven, worden opgehaald van de locatie `/var/audit/com.day.cq.dam/content/dam` in CRX, waar de logbestanden worden opgeslagen. Bovendien wordt de chronologieactiviteit geregistreerd wanneer de nieuwe activa worden geupload of de bestaande activa worden gewijzigd en in [!DNL Experience Manager] gecontroleerd via [ de Verbinding van Activa van Adobe ](https://helpx.adobe.com/nl/enterprise/admin-guide.html/enterprise/using/manage-assets-using-adobe-asset-link.ug.html) of [ Desktop app van Experience Manager ](https://experienceleague.adobe.com/docs/experience-manager-desktop-app/using/release-notes.html?lang=nl-NL).

>[!NOTE]
>
>Tijdelijke workflows worden niet weergegeven in de tijdlijn, omdat er voor deze workflows geen historiegegevens worden opgeslagen.

Als u de activiteitsstroom wilt weergeven, voert u een of meer bewerkingen uit op het element, selecteert u het element en kiest u vervolgens **[!UICONTROL Timeline]** in de lijst GlobalNav.

![ chronologie-2 ](assets/timeline-2.png)

De tijdlijn geeft de activiteitsstroom weer voor de bewerkingen die u uitvoert op de elementen.

![ activity_stream ](assets/activity_stream.png)

>[!NOTE]
>
>De standaardopslaglocatie voor logboekbestanden voor de taken **[!UICONTROL Publish]** en **[!UICONTROL Unpublish]** is `/var/audit/com.day.cq.replication/content`. Voor de taken **[!UICONTROL Move]** is de standaardlocatie `/var/audit/com.day.cq.wcm.core.page`.
