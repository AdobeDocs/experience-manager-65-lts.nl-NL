---
title: Inhoud architectuur
description: 'Tips voor het ontwerpen van uw inhoud (tip: alles is inhoud)'
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
topic-tags: best-practices
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: eb47f730-ac26-47a0-9bd7-3b7e94c79ecd
source-git-commit: cc96a14ebaf9f895a798b5f4904f5b4769b990bb
workflow-type: tm+mt
source-wordcount: '407'
ht-degree: 0%

---

# Inhoudsarchitectuur{#content-architecture}

## Volg David&#39;s model {#follow-david-s-model}

David Nuescheler schreef al jaren geleden het model van David, maar zijn ideeën zijn nog steeds actueel. De belangrijkste uitgangspunten van David&#39;s Model zijn:

* Gegevens komen als eerste, structuur later. Misschien.
* Geef de inhoudshiërarchie een impuls; laat deze niet gebeuren.
* Werkruimten zijn voor `clone()`, `merge()` en `update()` .
* Let op dat u dezelfde naam hebt als op hetzelfde vel.
* Verwijzingen kunnen als schadelijk worden beschouwd.
* Bestanden zijn bestanden.
* Id&#39;s zijn slecht.

Het Model van David kan op de wiki van het Jasje in [ https://wiki.apache.org/jackrabbit/DavidsModel ](https://wiki.apache.org/jackrabbit/DavidsModel) worden gevonden.

### Alles is inhoud {#everything-is-content}

Alles moet in de gegevensopslagruimte worden opgeslagen in plaats van te vertrouwen op afzonderlijke gegevensbronnen van derden, zoals databases. Een dergelijke benadering is van toepassing op geschreven inhoud, binaire gegevens zoals afbeeldingen, code en configuraties. Hiermee kunnen we één set API&#39;s gebruiken om alle inhoud te beheren en de promotie van deze inhoud via replicatie te beheren. U krijgt ook één bron van steun, registreren, etc.

### Het ontwerpbeginsel &quot;inhoudsmodel eerst&quot; gebruiken {#use-the-content-model-first-design-principle}

Wanneer u een nieuwe functie maakt, begint u altijd eerst met het ontwerpen van de JCR-inhoudsstructuur. Daarna leest u eerst de inhoud en schrijft u deze met de standaard Sling-servlets. Met een dergelijke benadering kunt u ervoor zorgen dat uw implementatie goed werkt met de toegangsbeheermechanismen buiten de box en kunt u voorkomen dat u overbodige CRUD-servlets genereert.

### Wees RESTful {#be-restful}

Bepaal servlets die op resourceTypes in plaats van wegen worden gebaseerd. Deze benadering maakt het mogelijk om de toegangscontroles van het JCR te gebruiken, aan de principes van REST te houden, en de middel en middeloplosser te gebruiken die aan ons in het verzoek worden verstrekt. Met deze methode kunt u de scripts wijzigen die URL&#39;s renderen aan de serverzijde zonder dat u URL&#39;s aan de clientzijde wijzigt. Bovendien worden de implementatiedetails van de server-side van de client verborgen voor extra beveiliging.

### Vermijd het definiëren van nieuwe knooppunttypen {#avoid-defining-new-node-types}

De types van knoop werken op een laag niveau in de infrastructuurlaag. Aan de meeste vereisten wordt voldaan door een `sling:resourceType` te gebruiken die is toegewezen aan een knooppunttype `nt:unstructured`, `oak:Unstructured`, `sling:Folder` of `cq:Page` . De types van knoop komen aan schema in de bewaarplaats overeen en het veranderen van knooptypes kan in de weg duur zijn.

### Naleving van naamgevingsconventies in het JCR {#adhere-to-naming-conventions-in-the-jcr}

Het naleven van noemende overeenkomsten voegt consistentie aan uw codebasis toe, verlaagt het veelvoud van onvolkomenheden en verhoogt de snelheid van ontwikkelaars die in het systeem werken. Adobe gebruikt de volgende conventies voor de ontwikkeling van AEM:

* Node-namen

   * Alles met kleine letters.
   * Woordscheiding met afbreekstreepjes.

* Namen van eigenschappen

   * Camel case, beginnend met een kleine letter.

* Componenten (JSP/HTML)

   * Alles met kleine letters.
   * Woordscheiding met afbreekstreepjes.
