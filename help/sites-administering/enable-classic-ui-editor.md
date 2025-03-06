---
title: Editor
description: Leer hoe u terug kunt schakelen naar de klassieke UI-editor.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 54a97ac0-db9e-4903-b395-b1af87cfd151
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '108'
ht-degree: 0%

---

# Editor{#editor}

Door gebrek, is de capaciteit om op klassieke UI van de redacteur over te schakelen onbruikbaar gemaakt.

Om de optie **open in Klassieke UI** in het **menu van de Informatie van de Pagina** opnieuw toe te laten, volg deze stappen.

1. Zoek met CRXDE Lite naar het volgende knooppunt:

   `/libs/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`

   Bijvoorbeeld

   ` [https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui](https://localhost:4502/crx/de/index.jsp#/libs/wcm/core/content/editor/jcr%3Acontent/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui)`

1. Creeer een bedekking gebruikend de **optie van de Knoop van de Bedekking**; bijvoorbeeld:

   * **Weg**: `/apps/wcm/core/content/editor/jcr:content/content/items/content/header/items/headerbar/items/pageinfopopover/items/list/items/classicui`
   * **Plaats van de Bedekking**: `/apps/`
   * **de Types van Knoop van de Gelijke**: actief (selecteer checkbox)

1. Voeg de volgende teksteigenschap met meerdere waarden toe aan het bovenliggende knooppunt:

   `sling:hideProperties = ["granite:hidden"]`

1. **Open in Klassieke UI** optie is opnieuw beschikbaar in het **menu van de Informatie van de Pagina** wanneer het uitgeven van pagina&#39;s.

   ![ open in klassieke optie UI van paginainformatie ](assets/syui-03-2019-02-27-15-19-48.png)
