---
title: Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen
description: Leer hoe u met de functie voor meerdere huurders inhoud in de CRX-opslagplaats kunt scheiden op basis van de organisatie van de klant om ongeoorloofde toegang te voorkomen.
contentOwner: AG
role: Architect, Admin, Leader
feature: Collections
solution: Experience Manager, Experience Manager Assets
exl-id: 39e14f89-8e60-4b5e-8859-d69ebd51864e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '220'
ht-degree: 0%

---

# Meerdere paden voor verzamelingen, fragmenten en fragmentsjablonen {#multi-tenancy-for-collections-snippets-and-snippet-templates}

Met de functie voor meerdere huurders kunt u inhoud in CRX segregeren op basis van het organisatievoorvoegsel en de organisatie-id om de inhoud te beschermen tegen ongeoorloofde toegang door gebruikers van andere organisaties.

[!DNL Adobe Experience Manager Assets] slaat gegevens voor elke organisatie op in een ander pad. Elk organisatiespecifiek pad wordt geïdentificeerd door het organisatievoorvoegsel en organisatie-id
die is opgenomen op de traditionele locatie waar verschillende soorten activa worden opgeslagen in CRX.

Als u bijvoorbeeld een map met de naam `Demo` maakt, slaat [!DNL Experience Manager] de map traditioneel op in `../content/dam/Demo` . Als multi-tenancy is ingeschakeld, kunt u de gegevens nu opslaan op `../content/dam/<organization prefix>/<organization id>Demo`

Als u bijvoorbeeld [!DNL Adobe Marketing Cloud] gebruikers van [!DNL Assets] (op verzoek) die zijn toegewezen aan de `aodpremium` -organisatie, de functie voor meerdere paden kunt gebruiken om het `../content/dam/<mac>/<aodpremium>Demo` -pad te configureren voor het segregeren van hun inhoud. In dit voorbeeld is `mac` het voorvoegsel van de organisatie en is `aodpremium` de organisatie-id.

Gebaseerd op de organisatie en identiteitskaart van de gebruiker, wordt dit gekwalificeerde weg getoond in de [!DNL Assets] interface en diverse tovenaars, met inbegrip van de Beweging en de verwezenlijking van het Fragment tovenaars om segregatie af te dwingen.

Met de functie Multi-tenancy kunt u de volgende typen elementen en componenten scheiden:

* Verzamelingen
* Openbare verzamelingen
* Catalogi (inclusief de wizard Pagina toevoegen/selecteren)
* Sjablonen
* Fragmentsjablonen
* Lichtbak
