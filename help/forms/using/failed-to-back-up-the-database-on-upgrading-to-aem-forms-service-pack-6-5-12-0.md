---
title: Er kan geen back-up van de database worden gemaakt tijdens de upgrade naar 6.5.12.0 for MySQL.
description: Wanneer een gebruiker een upgrade uitvoert naar Experience Manager 6.5.12.0 en op "Upgrade MySQL" klikt, kan de configuratiemanager geen back-up maken van de vorige Experience Manager Forms-database.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '101'
ht-degree: 0%

---

# Back-up maken van database mislukt tijdens upgrade naar 6.5.12.0 voor MySQL {#issue}

Wanneer een gebruiker een upgrade uitvoert naar Experience Manager 6.5.12.0 en op &quot;Upgrade MySQL&quot; klikt, kan de configuratiemanager geen back-up van de vorige Experience Manager Forms-database maken, wordt de fout weergegeven:

`Failed to backup the previous Adobe Experience Manager Forms Database`


## Van toepassing op {#applies-to}

* Experience Manager 6.5 Forms

## Oplossing {#solution}

Om de kwestie op te lossen, verhoog max_packet_size van het gegevensbestand aan 100 M of zoals vereist in het my.ini- dossier dat bij {AEM_HOME} wordt gevestigd/mysql.
