---
title: Toegankelijke complexe tabellen maken in HTML5-formulieren
description: Leer hoe u toegankelijke tabellen maakt in HTML5-formulieren.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: hTML5_forms
discoiquuid: 3504afe1-abf5-4fbf-a0d2-e093361764bd
feature: HTML5 Forms,Mobile Forms
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '265'
ht-degree: 0%

---

# Toegankelijke complexe tabellen maken in HTML5-formulieren {#create-accessible-complex-tables-in-html-forms}

Bij de standaardimplementatie van tabellen in HTML5 Forms worden HTML DIV-elementen gebruikt om een tabel te renderen. Bij het renderen worden ARIA-rollen gebruikt om aan de toegankelijkheidsvereisten te voldoen.

HTML5 Forms biedt een alternatieve uitvoering voor de tabellen om toegankelijkheidsproblemen met schermlezers te voorkomen die de ARIA-rollen die worden gebruikt bij datatabellen, niet volledig ondersteunen. Deze tabellen zijn gebaseerd op de nieuwe tabelindeling die in Designer is geïntroduceerd en die ook ondersteuning biedt voor:

* Rijkoppen
* Rijbereik

Als u de nieuwe indeling wilt gebruiken in HTML5 Forms, markeert u de tabel als complex. Als u de tabel als complex wilt markeren, voegt u als volgt `extras` -tag toe aan de XML-bron van het tabelsubformulier:

```xml
</extras>
 <text name="complexTable">1</text>
 </extras>
```

De lijsten die als *complexTable* duidelijk zijn volgen de inheemse vertoning van HTML, en verstrekken betere toegankelijkheidssteun voor bepaalde het schermlezers.  Als u een rijbereik wilt maken, selecteert u opeenvolgende cellen van een tabel in dezelfde kolom, klikt u met de rechtermuisknop op de selectie en klikt u op **[!UICONTROL Merge Cells]** .

>[!NOTE]
>
>Het maken van een rijbereik werkt alleen voor uiterst linkse cellen.

Als u een rij als rijkop wilt markeren, selecteert u alle cellen in de rij, klikt u met de rechtermuisknop op de selectie en klikt u op **[!UICONTROL Mark Header]** .

Als u een cel als kolomkop wilt markeren, selecteert u een willekeurige cel in de kolom, klikt u met de rechtermuisknop op de selectie en klikt u vervolgens op **[!UICONTROL Mark Header]** .

Beperkingen in nieuw *AccessibleTable* formaat:

* Gebrek aan steun voor kweekbare gebieden als het rowspan in de lijst wordt gebruikt
* Geen ondersteuning voor geneste tabellen (tabellen in tabelcellen)
* De ondersteuning voor de rowspan is beperkt tot de koptekstrijen en kopcellen
* De ondersteuning is beperkt tot reguliere tabellen
* Geen ondersteuning voor gegevensvooraf ingevulde tabellen met rowspan > 1
