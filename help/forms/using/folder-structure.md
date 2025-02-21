---
title: De mapstructuur begrijpen
description: Uitleg over de mapstructuur van de broncode van de AEM Forms-werkruimte die moet worden aangepast.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: HTML5 Forms,Adaptive Forms,Mobile Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '145'
ht-degree: 0%

---

# De mapstructuur begrijpen {#understanding-the-folder-structure}

AEM Forms-werkruimtecomponenten zijn ontworpen op MVC-architectuur met behulp van backbone. Elke component heeft een bestand voor:

* Model, dat bedrijfslogica bevat.
* Sjabloon, dat wil zeggen een HTML-bestand dat interfacebesturingselementen bevat.
* De mening, die als klasse van het Controlemechanisme aan Malplaatje dienst doet.

De elementen voor alle componenten worden in de hieronder beschreven mapstructuur geplaatst. Meld u aan bij CRXDE Lite en blader naar `/libs/ws/js/runtime/` om de elementen te openen.

**modellen** bevat backbonemodellen.

**meningen** bevat backbonemeningen.

**malplaatjes** bevat slechts de malplaatjes van HTML voor de componenten.

**routes** bevat universele routes. De omslag van malplaatjes binnen routes bevat de code van HTML en de verwijzingen naar de componenten.

**de diensten** bevat de dienstinterface om de server APIs van Adobe Experience Manager op REST eindpunt te roepen.

**util** bevat generische nut bruikbaar door veelvoudige componenten.
