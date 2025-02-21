---
title: Single Sign On en timeout handlers
description: Hoe kan ik de time-outwaarde voor sessies instellen voor de AEM Forms-werkruimte.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Single Sign On en timeout handlers {#single-sign-on-and-timeout-handlers}

AEM Forms-werkruimte is SSO ingeschakeld. Als een gebruiker zich bij een AEM Forms-toepassing zoals Forms Manager of de PDF Generator-gebruikersinterface heeft aangemeld en in dezelfde browsersessie toegang krijgt tot de AEM Forms-werkruimte, wordt de gebruiker aangemeld bij de AEM Forms-werkruimte en omgekeerd.

## Time-out van server afhandelen in AEM Forms-werkruimte {#handling-server-timeout-in-nbsp-aem-forms-workspace}

De onderbreking van de zitting voor een gebruiker kan in de Console van het Beleid worden gevormd.

Om de onderbreking te plaatsen, login aan `https://'[server]:[port]'/adminui`, navigeer aan **Montages > Beheer van de Gebruiker > Configuratie > Vorm Geavanceerde Attributen van het Systeem**, en maak de gewenste montages.

In de AEM Forms-werkruimte wordt de time-out verwerkt als:

* De sessieduur voor een gebruiker is beschikbaar als reactie op een aanroep van `initialize` waarmee een gebruikerssessie wordt geïnitialiseerd.
* Een pop-updialoogvenster geeft een melding aan de gebruiker dat de sessie bijna verlopen is, 15 seconden voor de sessievervaldatum.

In dit pop-updialoogvenster:

* Klik op OK om de gebruikerssessie te beëindigen.
* Klik op Annuleren om de gebruikerssessie opnieuw te initialiseren.

>[!NOTE]
>
>Als geen actie wordt ondernomen, wordt de gebruiker automatisch geregistreerd uit de werkruimte van AEM Forms drie seconden vóór de zittingsafloop.
