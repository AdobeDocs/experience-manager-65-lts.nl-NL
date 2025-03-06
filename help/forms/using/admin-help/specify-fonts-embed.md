---
title: Te insluiten fonts opgeven
description: Leer hoe u fonts kunt opgeven die u wilt insluiten in een adaptief formulier. U kunt opgeven welke lettertypen worden ingesloten of nooit worden ingesloten met formulieren die door Forms Service worden gegenereerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 374f9425-b596-4481-8fd0-6df07c521a19
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Te insluiten fonts opgeven{#specify-fonts-to-embed}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

U kunt opgeven welke fonts altijd worden ingesloten of nooit worden ingesloten met de formulieren die worden gebruikt door Output. Als u fonts insluit, neemt de bestandsgrootte van de formulieren toe. Ongebruikelijke lettertypen insluiten die gebruikers waarschijnlijk niet op hun systeem hebben en geen gemeenschappelijke lettertypen insluiten die zij hebben geïnstalleerd.

>[!NOTE]
>
>Als u een aangepast XCI-bestand hebt opgegeven voor Output, overschrijft de optie voor het insluiten van lettertypen in het XCI-bestand deze instellingen. (Zie [ dossierplaatsen voor Output ](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output) specificeren.)

1. Klik in de beheerconsole op Services > Uitvoer.
1. Typ onder Instellingen voor lettertype insluiten in het vak Fonts altijd insluiten de namen van de fonts die u wilt insluiten met de formulieren, gescheiden door komma&#39;s. De fonts die u opgeeft, worden alleen ingesloten in het gegenereerde formulier als ze in het formulier worden gebruikt. Deze instelling wordt genegeerd als de optie Lettertype insluiten is ingeschakeld in het XCI-bestand dat aan de service is doorgegeven. In dat geval worden alle lettertypen die in de PDF worden gebruikt, altijd ingesloten.
1. Typ in het vak Fonts nooit insluiten de namen van de fonts die u niet wilt insluiten met de formulieren, gescheiden door komma&#39;s. De lettertypen die u opgeeft, worden niet ingesloten in de PDF, zelfs niet als ze worden gebruikt in de gegenereerde PDF. Deze instelling wordt genegeerd als de optie voor het insluiten van lettertypen is uitgeschakeld in het XCI-bestand dat aan de service is doorgegeven. In dat geval worden geen van de in de PDF gebruikte lettertypen ingesloten.
1. Klik op Opslaan.
