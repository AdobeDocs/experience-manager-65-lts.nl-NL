---
title: 'Correspondentenbeheer: Problemen oplossen'
description: Leer hoe u fouten kunt verwerken die optreden tijdens het opslaan van een brief in een AEM Forms-omgeving.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '217'
ht-degree: 0%

---

# Correspondentenbeheer: Problemen oplossen {#correspondence-management-troubleshooting}

## Fouten bij het opslaan van een letter {#errors-when-saving-a-letter}

### Probleem {#issue}

Een van de volgende fouten wordt weergegeven bij het opslaan van een letter:

* Gegevensbinding niet aanwezig voor de tekstmodule
* Verstrek bezitsinformatie nodig voor het volgende

### Reden {#reason}

Deze fouten kunnen optreden als gevolg van een van de volgende:

* Een gegevenswoordenboek is gebonden aan de letter, maar is niet aanwezig op de server.
* Een gegevenswoordenboek is gebonden aan de letter, maar heeft een onderstrepingsteken (_) in de naam.

### Workaround {#workaround}

Zorg ervoor dat het gegevenswoordenboek dat u in de letter gebruikt, aanwezig is op de server en geen onderstrepingsteken (_) in de naam heeft.

## Fout bij voorvertonen van een letter {#error-when-previewing-a-letter}

### Probleem {#issue-1}

Tijdens het voorvertonen van een letter wordt de fout &#39;&#39;Fout bij het laden van de letter: kan element niet importeren uit XML-invoer&#39;&#39; weergegeven, zelfs wanneer een eerder niet-gepubliceerd tekstelement in de letter wordt gepubliceerd.

### Workaround {#workaround-1}

Stel de lettercache op de publicatieinstantie opnieuw in door de volgende stappen uit te voeren en probeer de letter vervolgens opnieuw weer te geven:

1. Ga naar **`https://'[server]:[port]'/[contextPath]/system/console/configMgr`** en meld u aan als Admin.
1. Selecteer **Configuraties van het Beheer van de Correspondentie**.
1. In **Configuraties van het Beheer van de Correspondentie**, maak **onbruikbaar toelaten het Geheime voorgeheugen van de Brief** en klik dan **sparen.**
1. Controle **laat het Geheime voorgeheugen van de Brief** toe en klik dan **sparen**.
1. Bekijk de brief opnieuw.
