---
title: Naamgevingsconventies voor knooppunten in de Java Content Repository
description: Nodes in de opslagplaats zijn onderworpen aan naamconventies van de Java Content Repository
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 36025dac-890e-45ba-adea-a230a5231a0b
source-git-commit: a869ffbc6015fd230285838d260434d9c0ffbcb0
workflow-type: tm+mt
source-wordcount: '284'
ht-degree: 0%

---

# Naamgevingsconventies {#naming-conventions}

De knopen in de bewaarplaats zijn onderworpen aan noemende overeenkomsten van de [&#x200B; Bewaarplaats van de Inhoud van Java &#x200B;](/help/sites-developing/the-basics.md#java-content-repository). AEM stelt echter andere conventies voor de naam van paginaknooppunten op.

## Naamgevingsconventies voor pagina&#39;s {#naming-conventions-for-pages}

Deze naamconventies worden op verschillende niveaus geïmplementeerd:

* JcrUtil: de implementatie van AEM van de [&#x200B; nut JCR &#x200B;](#jcr-utilities).
* PageManager: de [&#x200B; Manager van de Pagina &#x200B;](#page-manager) verstrekt methodes voor de verrichtingen van het paginaniveau.
* Volgens de interface die wordt gebruikt:

   * [Standaardinterface met aanraakbediening](#standard-ui)
   * [Klassieke interface](#classic-ui)

### JCR-hulpprogramma&#39;s {#jcr-utilities}

[&#x200B; JcrUtil &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/index.html?com/day/cq/commons/jcr/JcrUtil.html) is de implementatie van AEM van de nut JCR. Vooral voor het valideren van namen zijn de tekstafbeeldingen die hierin staan en de volgende validaties van belang:

* `isValidName`

   * Controleert of de naam niet leeg is en alleen geldige tekens bevat.
   * Kan worden gebruikt om te controleren of een voorgestelde naam geldig is.

* `createValidName`

   * Hiermee wordt een geldig label gemaakt op basis van een willekeurige tekenreeks.
   * Deze kan worden gebruikt om een naam te maken op basis van een titel.

### Paginabeheer {#page-manager}

[&#x200B; PageManager &#x200B;](https://developer.adobe.com/experience-manager/reference-materials/6-5-lts/javadoc/com/day/cq/wcm/api/PageManager.html) verstrekt methodes voor de verrichtingen van het paginaniveau, die op [&#x200B; worden gebaseerd JCRUtil &#x200B;](#jcr-utilities).

### Standaardinterface {#standard-ui}

De standaardinterface met aanraakbediening:

* Valideert de naam volgens de beperkingen die door PageManager worden opgelegd wanneer:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

### Klassieke interface {#classic-ui}

De klassieke gebruikersinterface legt strengere beperkingen op:

* Valideert de naam wanneer een expliciete knooppuntnaam wanneer één van beiden:

   * er is een paginatitel opgegeven voor conversie naar de knooppuntnaam
   * een expliciete nodenaam wordt verstrekt

* Geldige tekens (alleen deze tekens zijn in feite geldig wanneer een pagina wordt gemaakt vanuit de klassieke gebruikersinterface, ook al staat `PageManagerImpl` extra tekens toe):

   * &#39;a&#39; naar &#39;z&#39;
   * &#39;A&#39; naar &#39;Z&#39;
   * 0 tot en met 9
   * _ (onderstrepingsteken)
   * `-` (streepje/min)
