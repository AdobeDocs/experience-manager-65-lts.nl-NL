---
title: Verzamelingen publiceren naar Brand Portal
description: Leer hoe u verzamelingen publiceert en publiceert naar Brand Portal.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/ASSETS
topic-tags: brand-portal
content-type: reference
docset: aem65
feature: Brand Portal
role: User
solution: Experience Manager, Experience Manager Assets
exl-id: 1456a32e-c98f-4106-8546-799614c51a59
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '321'
ht-degree: 22%

---

# Verzamelingen publiceren naar Brand Portal {#publish-collections-to-brand-portal}

Als Adobe Experience Manager (AEM) Assets-beheerder kunt u verzamelingen publiceren naar het AEM Assets Brand Portal-exemplaar voor uw organisatie. U moet echter eerst AEM Assets integreren met Brand Portal. Zie [AEM Assets configureren met Brand Portal](/help/assets/configure-aem-assets-with-brand-portal.md) voor meer informatie.

Als u de oorspronkelijke verzameling in AEM Assets daarna wijzigt, worden de wijzigingen pas in Brand Portal doorgevoerd als u de verzameling opnieuw publiceert. Dit kenmerk zorgt ervoor dat wijzigingen in onderhanden werk niet beschikbaar zijn in Brand Portal. Alleen goedgekeurde wijzigingen die door een beheerder zijn gepubliceerd, zijn beschikbaar in Brand Portal.

>[!NOTE]
>
>Contentfragmenten kunnen niet naar Brand Portal worden gepubliceerd. Daarom als u inhoudsfragment(s) op de Auteur van AEM selecteert, dan **publiceer aan Brand Portal** actie is niet beschikbaar.
>
>Als verzamelingen met inhoudsfragmenten worden gepubliceerd van AEM Author naar Brand Portal, wordt alle inhoud van de map, behalve inhoudsfragmenten, gerepliceerd naar de Brand Portal-interface.

## Een verzameling publiceren naar Brand Portal {#publish-a-collection-to-brand-portal}

1. Klik in de AEM Assets-gebruikersinterface op het AEM-logo.
1. Van **Navigatie** pagina, ga **Assets > Verzamelingen**.
1. Selecteer in de console Verzamelingen de verzameling die u naar Brand Portal wilt publiceren.

   ![select_collection](assets/select_collection.png)

1. Van de toolbar, klik **publiceren aan Brand Portal**.
1. In de bevestigingsdialoog, klik **publiceren**.
1. Sluit het bevestigingsbericht.
1. Meld u als beheerder aan bij Brand Portal. De gepubliceerde verzameling is beschikbaar in de Collections-console.

   ![published collection](assets/published_collection.png)

## Publicatie van verzamelingen ongedaan maken {#unpublish-collections}

U kunt de publicatie van verzamelingen die u van AEM Assets naar Brand Portal publiceert, ongedaan maken. Nadat u de publicatie van de oorspronkelijke verzameling hebt ongedaan gemaakt, is de kopie ervan niet meer beschikbaar voor Brand Portal-gebruikers.

1. Selecteer in de Collections-console van uw AEM Assets-instantie de verzameling die u wilt verwijderen.

   ![select_collection-1](assets/select_collection-1.png)

1. Van de toolbar, klik **verwijderen uit het pictogram van Brand Portal**.
1. In de dialoog, klik **unpublish**.
1. Sluit het bevestigingsbericht. De verzameling wordt verwijderd uit de Brand Portal-interface.
