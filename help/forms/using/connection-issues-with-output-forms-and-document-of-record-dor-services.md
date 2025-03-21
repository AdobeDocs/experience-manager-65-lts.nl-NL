---
title: Verbindingsproblemen met Output, Forms en (Document of Record) DoR Services
description: Los AEM Forms-verbindingsfouten na SP19 op. Stop, installeer Microsoft Visual C++, herstart server voor een naadloze oplossing. Problemen met uitvoer, Forms en DoR oplossen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Services
hide: true
hidefromtoc: true
exl-id: c84ba536-a78d-4cf9-a480-59cb18e41076
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '168'
ht-degree: 0%

---

# Kan de Output-service, Forms-service of Document of Record-service (DoR) niet gebruiken {#unable-to-use-output-service-forms-service-or-document-of-record-service}

## Probleem

Nadat u AEM Forms 6.5 Service Pack 19 hebt geïnstalleerd, kan een `Connection to failed service` -fout optreden als u probeert de service Uitvoer, Forms of Document of Record (DoR) te gebruiken.

## Oplossing

Het probleem oplossen:

1. Stop je AEM 6.5 Forms-exemplaar.
1. De download en installeert [ versie met 64 bits van Microsoft Visual C++ Redistributable pakketten voor Visual Studio 2015, 2017, 2019, en 2022 ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170#visual-studio-2015-2017-2019-and-2022) op de computer waar AEM 6.5 Forms geïnstalleerd is.
1. Start de AEM Forms-server opnieuw.

   >[!NOTE]
   >
   > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.


>[!NOTE]
>
>
> Zorg ervoor dat u Redistributable installeert, zelfs als een vorige versie geïnstalleerd is.
