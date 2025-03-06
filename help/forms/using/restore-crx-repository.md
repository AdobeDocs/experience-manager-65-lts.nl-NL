---
title: Kan beschadigde CRX-opslagplaats die van toepassing is op JEE-clusterserver niet herstellen
description: Leer de stappen voor het herstellen van een beschadigde CRX-opslagplaats.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 716d8eb2-2010-4d55-b8fe-bd4f6f256a4d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '179'
ht-degree: 0%

---

# Kan beschadigde CRX-opslagplaats niet herstellen {#unable-to-restore-corrupt-crx-repository}

## Probleem {#issue}

Voor AEM Forms on JEE die een relationele gegevensbank gebruikt, zou de tijd op de machine die AEM Forms en relationele gegevensbank ontvangt altijd in absolute synchronisatie moeten zijn. Als de tijd op deze computers niet meer synchroon is, kan de CRX-opslagplaats van AEM Forms op de JEE-server ontoegankelijk worden. Het kan beschadigd lijken en ontoegankelijk worden via URL. De fout `AuthenticationsupportService missing` wordt geregistreerd.

## Vereisten {#prerequisites}

Maak een back-up van uw CRX-opslagplaats voordat u de onderstaande stappen uitvoert.

## Oplossing {#solution}

1. Ga naar `https://[AEM Forms Server]:[port]/system/console/bundles` .

1. Zoek de `oak-core` -bundel en controleer of deze wordt uitgevoerd.

1. Start de `oak-core` -bundel opnieuw als deze niet wordt uitgevoerd. Als ![ de knoop van de Pauze ](/help/forms/using/assets/stop.png) pictogram vóór de `oak-core` bundel aanwezig is, dan wijst het erop dat de bundel in lopende staat is.

1. Als het probleem nog steeds niet is opgelost, kunt u het herstellen vanaf de CRX-opslagplaats via de back-up of de CRX-opslagplaats opnieuw opbouwen als er geen back-up beschikbaar is.


## Van toepassing op {#applies-to}

Deze oplossing geldt voor AEM Forms op JEE Cluster.
