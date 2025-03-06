---
title: Kan Experience Manager Forms niet gebruiken met bepaalde versies van Oracle JDK
description: Kan Experience Manager Forms niet gebruiken met bepaalde versies van Oracle JDK
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 4aa45f02-ff89-4e40-a15d-e62c5879a87d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '160'
ht-degree: 0%

---

# Kan Experience Manager Forms niet gebruiken met bepaalde versies van Oracle JDK {#unable-to-use-forms-with-certain-versions-of-oracle-jdk}

De kwestie is op de volgende versies van toepassing:

* Experience Manager 6.3 Forms
* Experience Manager 6.4 Forms
* Experience Manager 6.5 Forms

## Probleem {#issue}

De gebruiker ontmoet de volgende uitzondering:
`Caused by: javax.xml.xpath.XPathExpressionException: javax.xml.transform.TransformerException: JAXP0801002: the compiler encountered an XPath expression containing '101' operators that exceeds the '100' limit set by 'FEATURE_SECURE_PROCESSING'.`

## Reden {#reason}

De uitzondering treedt op wanneer u Experience Manager Forms uitvoert met een versie van Oracle JDK (Java Development Kit) die hoger is dan of gelijk is aan de volgende versies:

* [ JDK7u341 ](https://www.oracle.com/java/technologies/javase/7u341-relnotes.html)
* [ JDK8u331 ](https://www.oracle.com/java/technologies/javase/8u331-relnotes.html)
* [ JDK11u15 ](https://www.oracle.com/java/technologies/javase/11-0-15-relnotes.html)

Bovengenoemde en latere versies van Java bevatten nieuwe XML-verwerkingslimieten in de JVM (Java Virtual Machine), waardoor bepaalde Forms-specifieke bewerkingen mislukken.

## Workaround {#workaround}

1. Stop je Experience Manager Forms Server.
1. Configureer het volgende JVM-argument voor uw toepassingsserver:

   `-Djdk.xml.xpathExprOpLimit=2000`

   Het stelt de systeemeigenschap in JVM in op een redelijk hoge waarde, zodat de standaardlimiet niet wordt bereikt.

1. Start uw Experience Manager Forms-server.
