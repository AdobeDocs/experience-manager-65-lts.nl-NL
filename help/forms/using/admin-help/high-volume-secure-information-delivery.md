---
title: Beveiligde informatieverstrekking voor grote volumes
description: Documentbeveiliging ondersteunt het koppelen van licenties aan gebruikers, in plaats van aan documenten in omgevingen waar veel materiaal wordt geproduceerd.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5df8c609-8007-4422-9bf8-5bae6d53b9b7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '320'
ht-degree: 0%

---

# Beveiligde informatieverstrekking voor grote volumes {#high-volume-secure-information-delivery}

In een massaproductieomgeving, zoals een omgeving die beveiligde maandelijkse facturen voor een telecombedrijf genereert, kan het maken van licenties die specifiek zijn voor elk document een hulpbronnenintensief proces worden. In dergelijke gevallen ondersteunt documentbeveiliging het koppelen van licenties aan gebruikers in plaats van aan de documenten. De licentie die voor een gebruiker wordt gegenereerd, wordt gebruikt voor alle documenten die voor die gebruiker zijn beveiligd.

Een voordeel van deze aanpak is dat de grootte van de documentbeveiligingsdatabase niet lineair met de documenten toeneemt, maar met het aantal gebruikers. Omdat u de licentie slechts één keer voor een gebruiker moet maken, wordt de verdere beveiliging van documenten via dit beleid bovendien sneller. Functies zoals offline toegang, verlopen van documenten en intrekking worden voor al dergelijke documenten ondersteund.

Documentbeveiliging ondersteunt ook Abstract beleid. Abstract beleid is beleidssjablonen die alle beleidskenmerken bevatten, zoals documentbeveiligingsinstellingen en gebruiksrechten, maar die geen lijst met principes bevatten. De beheerders kunnen om het even welk aantal beleid van het abstracte beleid met verschillende hoofden tot stand brengen die toegang tot de documenten zouden moeten hebben. Wijzigingen in het abstracte beleid hebben geen invloed op het feitelijke beleid dat wordt gegenereerd op basis van het abstracte beleid.

Als er een maandelijkse factuurgeneratie voor een telecombedrijf is, creeert u een abstract beleid, creeert gebruikers, en produceert dan unieke vergunningen voor elke gebruiker. De licenties worden later toegepast op documenten voor elke gebruiker.

Het maken van een abstract beleid wordt alleen ondersteund door documentbeveiliging in Java SDK. U kunt echter wel het beleid beheren dat u maakt op basis van het abstracte beleid van de webpagina&#39;s voor documentbeveiliging. Beleid dat met deze methode wordt gemaakt, werkt hetzelfde als het beleid dat op basis van webpagina&#39;s voor documentbeveiliging wordt gemaakt.

Zie [ Programmering met de vormen van AEM ](https://www.adobe.com/go/learn_aemforms_programming_63) voor meer informatie.
