---
title: Scriptuitvoering mislukt bij AEM Forms 6.5 LTS met JBoss EAP 8 (Linux)
description: Het instellen van JBoss EAP 8.0 in een Linux-omgeving kan leiden tot een bepaalde fout tijdens het uitvoeren van shellscripts of opstartbestanden
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
hide: true
index: false
hidefromtoc: true
source-git-commit: d397e6a51ad2a52da5ccb0a690e1acd3fafcee3c
workflow-type: tm+mt
source-wordcount: '236'
ht-degree: 0%

---


# Scriptuitvoering mislukt bij AEM Forms 6.5 LTS met JBoss EAP 8 (Linux)

## Probleem

Wanneer vestiging **JBoss EAP 8.0 (AEM Forms 6.5.1 LTS)** op a **Linux** milieu, kunt u één van de volgende fouten terwijl het runnen van shell manuscripten of startdossiers ontmoeten:

```text
/bin/sh^M: bad interpreter
$'\r': command not found
```

Deze fouten komen voor wanneer shellmanuscripten of configuratiedossiers op het systeem van a **Vensters** werden gecreeerd of werden uitgegeven en **CRLF (de Terugkeer van het Vervoer + het Eind van de Lijn)** lijneindes bevatten.
De systemen van Linux steunen slechts **LF (het Eind van de Lijn)**, en de lijn van Windows-stijl eindings veroorzaken manuscriptuitvoeringsmislukkingen.

## Van toepassing op

* **JBoss EAP 8.0**
* **Linux/op UNIX-Gebaseerde werkende systemen**

## Stappen voor probleemoplossing

1. **identificeer het beïnvloede dossier**

   * Controleer de uitvoer van de fout om het script of configuratiebestand van `.sh` te identificeren dat de fout veroorzaakt.

2. **zet het dossier in formaat Unix** om

   * Met het hulpprogramma `dos2unix` kunt u regeleinden in Windows-stijl omzetten in Unix-indeling:

     ```bash
     dos2unix <file_name>
     ```

   * Vervang `<file_name>` door het script of configuratiebestand dat de fout genereert.

3. **Herhaal indien vereist**

   * Als het meerdere scripts betreft, herhaalt u de conversie voor alle relevante `.sh` -bestanden (bijvoorbeeld installer-, LCM- of JBoss-opstartscripts).

4. **re-run het manuscript**

   * Voer na de conversie het script opnieuw uit om te bevestigen dat het probleem is opgelost.

Nadat de bestanden zijn omgezet in Unix (LF), worden de fouten `/bin/sh^M` en `$'\r': command not found` opgelost en worden JBoss-scripts met succes uitgevoerd in Linux.
