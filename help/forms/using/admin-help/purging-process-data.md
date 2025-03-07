---
title: Procesgegevens wissen
description: Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat leidt tot lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Zie hoe u procesgegevens kunt wissen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_aem_forms_database
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 53ce63a3-704a-4da6-b652-362a436f05a7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '199'
ht-degree: 0%

---

# Procesgegevens wissen {#purging-process-data}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat leidt tot lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Het is een goede gewoonte om procesgegevens te wissen wanneer records niet meer nodig zijn. AEM-formulieren bieden verschillende manieren om procesgegevens te wissen:

* U kunt beheerconsole gebruiken om een eenmalige verwijdering uit te voeren van verouderde records die verwant zijn aan langlevende processen, of om regelmatige automatische purges te plannen. (Zie [ verslagen van het gegevensbestand van de Manager van de Baan ](/help/forms/using/admin-help/purge-records-job-manager-database.md#purge-records-from-the-job-manager-database) zuiveren.)
* Met de Java API voor AEM-formulieren en de webservice-API kunt u procesgegevens met betrekking tot langlevende processen programmatisch wissen. (Zie &quot;het Opzuiveren Gegevens van het Proces&quot;in [ Programmering met de vormen van AEM ](https://www.adobe.com/go/learn_aemforms_programming_63).)
* Gebruik het gereedschap voor het verwijderen van processen om processen op basis van de procesnaam en andere parameters te wissen. Voor details, zie het dossier van het proceszuiveringshulpmiddel, in *[aem_forms wortel]* \sdk\misc\Foundation\ProcessPurgeTool\ReadMe.txt.
