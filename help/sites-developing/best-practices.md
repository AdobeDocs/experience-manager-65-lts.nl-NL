---
title: Aanbevolen procedures voor AEM-ontwikkelaars
description: Adobe Engineering- en Consulting-teams hebben een uitgebreide reeks best practices ontwikkeld voor AEM-ontwikkelaars.
contentOwner: Justin Edelson
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
source-git-commit: 2a406ca2870e241539819ae62c6a14904ee71211
workflow-type: tm+mt
source-wordcount: '390'
ht-degree: 0%

---

# Aanbevolen procedures{#best-practices}

## Aanbevolen procedures voor ontwikkelaars - Aan de slag {#best-practices-for-developers-getting-started}

Adobe Engineering- en Consulting-teams hebben een uitgebreide reeks best practices ontwikkeld voor AEM-ontwikkelaars. Adobe-ontwikkelaars volgen deze best practices bij het ontwikkelen van belangrijke AEM-productupdates en klantcode voor de implementatie door klanten.

Voordat u uw AEM-ontwikkelingsproject start, moet u eerst de volgende aanbevolen procedures doornemen:

* [Ontwikkelspraktijken](/help/sites-developing/development-practices.md)
* [Inhoud architectuur](/help/sites-developing/content-architecture.md)
* [Softwarearchitectuur](/help/sites-developing/software-architecture.md)
* [Codetips](/help/sites-developing/coding-tips.md)
* [Codepitten](/help/sites-developing/code-pitfalls.md)
* [JCR-interactie](/help/sites-developing/jcr-integration.md)
* [OSGi-bundels](/help/sites-developing/osgi-bundles.md)
* [ Java API Beste praktijken ](https://experienceleague.adobe.com/docs/experience-manager-learn/foundation/development/understand-java-api-best-practices.html)

### Aanvullende informatie over aanbevolen procedures {#additional-best-practices-information}

Op de volgende gebieden is documentatie beschikbaar die specifiek is voor de ontwikkeling van beste praktijken:

* [Sites](#sites)
* [Tooling/HTL](#tooling-htl)

In de volgende tabellen worden specifieke documenten beschreven en aan deze documenten gekoppeld.

Voor beste praktijken bij het beheren, het opstellen en het handhaven, of het ontwerpen, zie één van het volgende:

* [Aanbevolen werkwijzen beheren](/help/sites-administering/administer-best-practices.md)
* [Aanbevolen werkwijzen ontwerpen](/help/sites-authoring/best-practices.md)
* [Tips en trucs implementeren](/help/sites-deploying/best-practices.md)

## Sites {#sites}

Voor het beheren en ontwerpen van uw website-inhoud gelden enkele aanbevolen procedures die als volgt worden beschreven:

<table>
 <tbody>
  <tr>
   <td>Een deel van de theorie achter de standaard, aanraakinterface.</td>
   <td><p><a href="/help/sites-developing/touch-ui-concepts.md">Interface met aanraakbediening: concepten</a></p> <p><a href="/help/sites-developing/touch-ui-structure.md">Interface voor touch-functies: structuur</a></p> </td>
   <td>Deze documenten bieden een overzicht van de concepten en structuur van de interface met aanraakbediening.</td>
  </tr>
  <tr>
   <td>Interface met aanraakbediening: consoles aanpassen </td>
   <td><a href="/help/sites-developing/customizing-consoles-touch.md">UI-consoles met aanraakbediening aanpassen</a></td>
   <td>In dit document wordt beschreven hoe u de consoles voor de interface met aanraakbediening het beste kunt uitbreiden.</td>
  </tr>
  <tr>
   <td>Interface met aanraakbediening: pagina's ontwerpen aanpassen</td>
   <td><a href="/help/sites-developing/customizing-page-authoring-touch.md">UI-pagina's met aanraakbediening aanpassen</a></td>
   <td>Beschrijft hoe te om paginaontwerp voor aanraking-toegelaten UI uit te breiden.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td><a href="/help/sites-developing/workflows-best-practices.md">Workflows ontwikkelen en uitbreiden</a></td>
   <td><p>Met workflows kunt u Adobe Experience Manager-activiteiten (AEM) automatiseren en een groot deel van de verwerking in een AEM-omgeving uitvoeren. Daarom wordt u ten zeerste aangeraden de implementatie van workflows zorgvuldig te plannen.</p> </td>
  </tr>
 </tbody>
</table>

## Tooling/HTL {#tooling-htl}

HTML Template Language (HTL) is een nieuw HTML-sjabloonsysteem dat is geïntroduceerd met AEM 6.0. Het vervangt JSP en ESP als het voorkeurssjabloonsysteem van AEM.

|  |  |  |
|---|---|---|
| HTML-overzicht | [ overzicht en syntaxis HTML ](https://experienceleague.adobe.com/docs/experience-manager-htl/content/overview.html) | In dit document wordt beschreven wat HTML is, hoe u naar HTML kunt gaan, een voorbeeldproject, syntaxis, expressies en instructies |
| API gebruiken in Java | [ HTML Java gebruiken-API ](https://helpx.adobe.com/experience-manager/htl/using/use-api.html) | De HTML Java Use-API stelt een HTML-bestand in staat toegang te krijgen tot hulplijnmethoden in een aangepaste Java-klasse. |

>[!NOTE]
>
>De volgende meerdelige zelfstudie kan van belang zijn voor de beste praktijk om een nieuw AEM-project op te zetten, waarin de kerncomponenten, bewerkbare sjablonen, clientbibliotheken en de ontwikkeling van componenten worden beschreven:
>[Aan de slag met AEM Sites - WKND-zelfstudie ](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop.html)
