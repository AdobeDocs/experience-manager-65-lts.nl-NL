---
title: SOM-expressies gebruiken in aangepaste formulieren
description: Leer hoe u SOM-expressies extraheert van een deelvenster met een adaptieve vorm.
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: develop
feature: Adaptive Forms,Foundation Components
discoiquuid: 13f00bb2-561f-4d64-8829-292c663abeab
docset: aem65
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: a2a2a6f3-409e-44a2-a85b-9f0bc40cc800
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '344'
ht-degree: 0%

---

# SOM-expressies gebruiken in aangepaste formulieren{#using-som-expressions-in-adaptive-forms}

Aangepaste formulieren worden gemodelleerd als AEM Page, die wordt weergegeven als JCR-inhoudsstructuur in de AEM-opslagplaats. Het belangrijkste element van de inhoudsstructuur is guideContainer-knooppunt. Onder guideContainer, is er rootPanel die genestelde paneel en gebieden kan bevatten.

U kunt een scriptobjectmodel (SOM) gebruiken om te verwijzen naar waarden, eigenschappen en methoden binnen een bepaald DOM (Document Object Model). Een DOM organiseert de geheugenvoorwerpen en de eigenschappen in een boomhiërarchie. Een SOM-expressie verwijst naar Velden/Elementen en deelvensters tekenen.

In de volgende afbeelding ziet u een knooppuntstructuur waarnaar een adaptief formulier wordt geconverteerd wanneer u componenten aan een formulier toevoegt. U kunt bijvoorbeeld een deelvenster toevoegen aan het hoofddeelvenster en een keuzerondje in het deelvenster dat tijdens de runtime wordt getransformeerd naar DOM. De SOM-expressie voor het veld keuzerondje in adaptieve vorm wordt opgegeven als `guide[0].guide1[0].guideRootPanel[0].panel1[0].radiobutton[0]` .

![ boom DOM ](assets/hierarchy.png)

DOM-structuur

Een SOM-expressie voor een element in een adaptieve vorm wordt vooraf ingesteld door `guide[0].guide1[0]` . De positie van een component in de hiërarchie van de knoopstructuur wordt gebruikt om zijn uitdrukking SOM af te leiden.

![ BLOEM met twee radioknopen ](assets/hierarchy_radio_button.png)

DOM-structuur met twee keuzerondjes

De SOM-expressie verandert wanneer u de positie van de keuzerondjes in het adaptieve formulier wijzigt. In de ontwerpmodus kunt u de SOM-expressie van een veld of element in AEM Forms weergeven met de optie SOM-expressie weergeven. De optie wordt weergegeven in het deelvenster en wanneer u met de rechtermuisknop op het veld of element klikt.

![ het Extraheren van de Uitdrukkingen SOM in een Aangepaste vorm ](assets/som-expressions.png)

SOM-expressies extraheren in een adaptieve vorm

In deelvensters hebt u toegang tot de functie via de werkbalk van het deelvenster. Met deze functie kunnen auteurs van adaptieve formulieren scripts schrijven.

![ het Extraheren van uitdrukkingen SOM gebruikend paneeltoolbar ](assets/som-expression.png)

SOM-expressies extraheren met de werkbalk van het deelvenster

Sommige APIs die in [ worden vermeld GuideBridge ](https://helpx.adobe.com/nl/aem-forms/6/javascript-api/GuideBridge.html) gebruikt de uitdrukking SOM van een element. Als u bijvoorbeeld een bepaald veld in een adaptieve vorm de focus wilt geven, geeft u de overeenkomstige SOM-expressie door aan de `getFocus` API in `guideBridge` .
