---
title: Het programmatisch beheren van PreferencesNodes
description: Gebruik de API (Java) van de Dienst van de Manager van de Voorkeur om de Knoop van de Voorkeur programmatically te beheren.
contentOwner: admin
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: operations
role: Developer
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,APIs & Integrations
hide: true
hidefromtoc: true
exl-id: 95a83858-c0b7-4c68-b4a9-d525bfc663c0
source-git-commit: 51342861dd01e659999c19fbe0274e8d3cbcf8c4
workflow-type: tm+mt
source-wordcount: '239'
ht-degree: 0%

---

# Het programmatisch beheren van de Knooppunten van de Voorkeur {#programmatically-managing-the-preferencesnodes}

**de Steekproeven en de voorbeelden in dit document zijn slechts voor AEM Forms op het milieu JEE.**

Dit onderwerp beschrijft hoe u de Dienst API van de Manager van de Voorkeur (Java) kunt gebruiken om de Knoop van de Voorkeur programmatically te beheren.

U kunt de configuratie-instellingen handmatig wijzigen via de gebruikersinterface van de beheerder. Navigeer naar `Home>Settings>User Management> Configuration>Manual Configuration` om de opties te wijzigen. Importeren `config.xml` nadat u de wijzigingen hebt aangebracht, gaan alle wijzigingen verloren, behalve de wijzigingen die op het knooppunt `/Adobe/Adobe Experience Manager Forms/Config/UM persist` zijn aangebracht. De voorvertoning van de import- en exportfuncties van Gebruikersbeheer biedt geen ondersteuning voor het wijzigen van configuratie-instellingen voor andere componenten. Deze wijzigingen kunnen nu worden aangebracht met API&#39;s van `PreferencesManagerServiceClient` .

**Samenvatting van stappen**
Ga als volgt te werk om de knooppunten van voorkeuren programmatisch te beheren:

1. Neem de projectbestanden op.
1. Creeer a `PreferencesManagerService` cliënt.
1. Roep de juiste rol- of machtigingsbewerkingen aan.

**omvat de projectdossiers**

Neem de benodigde bestanden op in uw ontwikkelingsproject. Als u een clienttoepassing maakt met Java, neemt u de benodigde JAR-bestanden op. Als u webservices gebruikt, moet u ervoor zorgen dat u de proxybestanden opneemt.

**creeer a `PreferencesManagerService` cliënt**

Voordat u via programmacode een bewerking Gebruikersbeheer `PreferencesManagerService` kunt uitvoeren, moet u een `PreferencesManagerService` -client maken. Maak een `PreferencesManagerServiceClient` -object met de Java API.

**voke de aangewezen rol of toestemmingsverrichtingen**

Zodra u de de dienstcliënt hebt gecreeerd, kunt u de verrichtingen van de Manager van de Voorkeur dan aanhalen. Met de serviceclient kunt u machtigingen lezen en instellen.
