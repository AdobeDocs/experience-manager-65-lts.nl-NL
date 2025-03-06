---
title: Het beheerderswachtwoord configureren bij installatie
description: Leer hoe u het beheerderswachtwoord bij Adobe Experience Manager-installatie wijzigt.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Security
role: Admin
exl-id: cab746a0-4f50-4a0b-8d3a-7140a710fbfa
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '304'
ht-degree: 0%

---

# Het beheerderswachtwoord configureren bij installatie{#configure-the-admin-password-on-installation}

## Overzicht {#overview}

Sinds versie 6.3 kan in Adobe Experience Manager (AEM) het beheerderswachtwoord via de opdrachtregel worden ingesteld wanneer een nieuwe instantie wordt geïnstalleerd.

In eerdere versies van AEM moesten het wachtwoord voor de beheerdersaccount en het wachtwoord voor verschillende andere consoles na de installatie worden gewijzigd.

Met deze functie wordt de mogelijkheid toegevoegd om een nieuw beheerderswachtwoord voor de repository en de Servlet Engine in te stellen tijdens de installatie van een AEM-instantie, waardoor de noodzaak om het daarna handmatig te doen wordt weggenomen.

>[!CAUTION]
>
>De functie is niet van toepassing op de Felix Console, waarvoor het wachtwoord handmatig moet worden gewijzigd. Voor meer informatie, zie de relevante [ sectie van Controlelijst van de Veiligheid ](/help/sites-administering/security-checklist.md#change-default-passwords-for-the-aem-and-osgi-console-admin-accounts).

## Hoe gebruik ik het? {#how-do-i-use-it}

Deze functie wordt automatisch geactiveerd als u ervoor kiest om AEM via de opdrachtregel te installeren in plaats van op de JAR te dubbelklikken vanuit een bestandssysteemverkenner.

De algemene syntaxis voor het uitvoeren van een AEM-instantie vanaf de opdrachtregel is:

```shell
java -jar aem6.3.jar
```

Nadat u de instantie via de opdrachtregel hebt uitgevoerd, kunt u het beheerderswachtwoord tijdens het installatieproces wijzigen:

![ chlimage_1-116 ](assets/chlimage_1-116a.png)

>[!NOTE]
>
>De vraag om het beheerderswachtwoord te wijzigen wordt alleen weergegeven tijdens de installatie van een nieuw AEM-exemplaar.

## De markering -nointeractive gebruiken {#using-the-nointeractive-flag}

U kunt ook het wachtwoord opgeven in een eigenschappenbestand. Dit wordt gedaan door de markering `-nointeractive` te gebruiken in combinatie met de eigenschap `-Dadmin.password.file` system.

Hieronder ziet u een voorbeeld:

```shell
java -Dadmin.password.file =/path/to/passwordfile.properties -jar aem6.3.jar -nointeractive
```

Het wachtwoord in het `passwordfile.properties` -bestand moet de volgende indeling hebben:

```xml
admin.password = 12345678
```

>[!NOTE]
>
>Als u de parameter `-nointeractive` gewoon gebruikt zonder de eigenschap `-Dadmin.password.file` system, gebruikt AEM het standaardbeheerderswachtwoord zonder dat u wordt gevraagd dit te wijzigen. Dit komt in feite overeen met het gedrag van eerdere versies. Deze niet-interactieve modus kan worden gebruikt voor geautomatiseerde installaties die de opdrachtregel in een installatiescript gebruiken.
