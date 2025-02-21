---
title: Overwegingen bij het uitvoeren van beheerconsole
description: Dit document bevat een aantal punten waarmee u rekening kunt houden wanneer u de beheerconsole uitvoert.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Overwegingen bij het uitvoeren van beheerconsole {#considerations-when-running-administrationconsole}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Dit zijn sommige dingen om te overwegen wanneer het runnen van de Console van het Beleid:

* Als u beheerconsole opent met de URL `https://[hostname]:'port'/adminui` , mag de opgegeven hostnaam geen onderstrepingstekens bevatten. Anders, werken de verbindingen aan sommige gebieden van de beleidsconsole misschien niet behoorlijk.
* Als u een beleidsconsole in de Ontdekkingsreiziger van Vensters op Japans OS in werking stelt, kunt u deze problemen ontmoeten:

   * Als u op een koppeling klikt, keert u terug naar de aanmeldingspagina in plaats van naar de verwachte koppeling.
   * Als u op een koppeling klikt, wordt een machtigingsfout weergegeven.

  De beste praktijken moeten de beleidsconsole van andere browser, zoals Mozilla Firefox in werking stellen, om ervoor te zorgen dat geen verbindingen ontbreken.

* Gebruik geen backslash-tekens () wanneer u zoekopdrachten uitvoert in de beheerconsole.
