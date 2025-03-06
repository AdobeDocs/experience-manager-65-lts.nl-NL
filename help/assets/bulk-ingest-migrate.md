---
title: Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen
description: Met Feature Pack 18912 kunt u middelen bulksgewijs invoeren via FTP of elementen migreren van Dynamic Media Classic naar Dynamic Media op Adobe Experience Manager. Dit optionele functiepakket is beschikbaar bij Adobe-ondersteuning.
contentOwner: Rick Brough
topic-tags: dynamic-media
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
content-type: reference
docset: aem65
feature: Asset Management
role: User, Admin
solution: Experience Manager, Experience Manager Assets
exl-id: 9d49d64b-fe90-4da6-a2db-19a69d1dc12c
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '400'
ht-degree: 0%

---

# Installeren van functiepak 18912 voor migratie van grote bedrijfsmiddelen{#installing-feature-pack-for-bulk-asset-migration}

De installatie van eigenschappak 18912 is facultatief **.

Met Feature Pack 18912 kunt u opgenomen elementen via FTP rechtstreeks in Dynamic Media - Scene7-modus op Adobe Experience Manager bulken. Het laat u ook activa van Dynamic Media Classic in Dynamische Media - wijze Scene7 op Experience Manager migreren. Het eigenschappak is beschikbaar bij [ Adobe Professional Services ](https://business.adobe.com/customers/consulting-services/main.html).

>[!IMPORTANT]
>
>Het is mogelijk voor u om het eigenschappak aan massa te gebruiken migrate activa op zich van Dynamic Media Classic aan Dynamische Media - wijze Scene7 in Experience Manager. Het is ook mogelijk om migratieactiva in bulk te migreren gebruikend de eigenschap van FTP in Dynamic Media Classic. Nochtans, adviseert Adobe *niet* dat u één van beiden van deze methodes toe te schrijven aan de betrokken ingewikkeldheid gebruikt.
>
>Als dusdanig, wordt dit pak van de migratieeigenschap *slechts* gesteund als deel van een migratieproject wanneer gedaan door [ Adobe Professional Services ](https://business.adobe.com/customers/consulting-services/main.html).

Voordat u het functiepakket installeert, moet u een servicegebruiker maken en die informatie doorgeven aan de ondersteuning van Adobe.

Zie ook [ Dynamische Media vormen - wijze Scene7 ](/help/assets/config-dms7.md).

**om eigenschappak 18912 voor bulkactiva migratie te installeren:**

1. Navigeer in uw Experience Manager-instantie naar **[!UICONTROL Tool]** > **[!UICONTROL Security]** > **[!UICONTROL Users]** en selecteer **[!UICONTROL Create User]** . Deze de dienstgebruiker moet *toestemmingen `/content/dam.` lezen/schrijven* hebben.
1. Op de **[!UICONTROL ID]** en **[!UICONTROL Password]** gebieden, ga een gebruikersnaam en wachtwoord in; bijvoorbeeld, **Gebruiker van FTP**. Deze naam wordt in de tijdlijn weergegeven als de gebruiker die het element heeft gemaakt. Wanneer een element wordt geüpload vanaf FTP, wordt een element beschouwd als gemaakt wanneer het naar de FTP-server wordt geüpload en naar Experience Manager wordt geduwd.
1. Contact [ de Klantensteun van Adobe voor Experience Manager ](https://experienceleague.adobe.com/?support-solution=General#support) om toegang tot eigenschappak 18912 voor het downloaden te verzoeken. U hebt mogelijk de volgende informatie nodig wanneer u contact opneemt met de ondersteuningsafdeling:

   * IP van de server adres voor uw instantie van de Auteur, met inbegrip van het havenaantal (door gebrek, is het havenaantal 4502.)
   * Gebruikersnaam en wachtwoord voor Experience Manager-service uit de vorige stap.

1. Adobe Customer Support for Experience Manager biedt u de FTP-gegevens en toegang tot het functiepakket 18912.
1. Wanneer u het functiepak 18912 ontvangt, installeer het.

   Zie [ hoe te met Pakketten ](/help/sites-administering/package-manager.md) voor meer informatie werken bij het gebruiken van de Distributie van de Software en de pakketten in Experience Manager.
