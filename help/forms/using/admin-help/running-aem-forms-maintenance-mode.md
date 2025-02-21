---
title: AEM-formulieren uitvoeren in de onderhoudsmodus
description: De onderhoudsmodus is handig wanneer u taken uitvoert zoals het patchen van een DSC, het upgraden van AEM-formulieren of het toepassen van een servicepack. Meer informatie over het uitvoeren van AEM-formulieren in de onderhoudsmodus.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_aem_forms
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '256'
ht-degree: 0%

---

# AEM-formulieren uitvoeren in de onderhoudsmodus {#running-aem-forms-in-maintenance-mode}

De onderhoudsmodus is handig wanneer u taken uitvoert zoals het patchen van een DSC, het upgraden van AEM-formulieren of het toepassen van een servicepack.

U moet voorkomen dat processen worden aangeroepen terwijl de server zich in de onderhoudsmodus bevindt. Dit is wat gebeurt als een proces wordt aangehaald terwijl de server op onderhoudswijze is:

* Als het proces van lange duur is, wordt het toegevoegd aan het baangegevensbestand, maar is niet begonnen. Wanneer u de onderhoudsmodus afsluit, verwerkt AEM de taken met een lange levensduur in de wachtrij, zelfs als de server opnieuw is gestart in de onderhoudsmodus.
* Als het proces van korte duur is, wordt het meteen verwerkt.

**Zet de vormen van AEM op onderhoudswijze**

1. Voer in een webbrowser de volgende gegevens in:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=pause&user=[administrator username]&password=[password]`

   Een bericht &quot;nu gepauzeerd&quot;wordt getoond in het browser venster.

   >[!NOTE]
   >
   >Als u de server sluit terwijl het onderhoudswijze is, is het nog op onderhoudswijze wanneer het opnieuw wordt begonnen. Schakel de onderhoudsmodus uit wanneer u klaar bent met uw onderhoudstaken.

**Controle of de vormen van AEM op onderhoudswijze** lopen

1. Voer in een webbrowser de volgende gegevens in:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=isPaused&user=[administrator username]&password=[password]`

   De status wordt weergegeven in het browservenster. De status &quot;true&quot; geeft aan dat de server wordt uitgevoerd in de onderhoudsmodus en &quot;false&quot; geeft aan dat de server niet in de onderhoudsmodus staat.

**Draai van onderhoudswijze**

1. Voer in een webbrowser de volgende gegevens in:

   `https://[hostname]:[port]/dsc/servlet/DSCStartupServlet?maintenanceMode=resume&user=[administrator username]&password=[password]`

   Er wordt een bericht &quot;now running&quot; weergegeven in het browservenster.
