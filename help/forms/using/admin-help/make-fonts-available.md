---
title: Lettertypen beschikbaar maken
description: Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 2861bde5-b373-4ab2-9808-7d32ef1dc925
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '228'
ht-degree: 0%

---

# Lettertypen beschikbaar maken {#make-fonts-available}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Zorg ervoor dat de fonts die in een formulier worden gebruikt, beschikbaar zijn voor gebruik op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren. Neem bijvoorbeeld het volgende scenario. Een formulierontwerper voegt een lettertype toe aan de lettertypemap die door Designer wordt gebruikt en maakt een formulier dat dat lettertype gebruikt op een andere computer. Plaats het lettertype in de lettertypenmap van de klant, zodat de Output-service het lettertype kan gebruiken. Als de map met lettertypen voor de klant niet bestaat, maakt u een directory op de J2EE-toepassingsserver die als host fungeert voor AEM-formulieren.

Voor informatie over extra doopvontmontages, zie [ algemene de vormmontages van AEM ](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings) vormen.

**specificeer de plaats van de folder van de doopvonten van de Klant**

1. Klik in de beheerconsole op Instellingen > Core Systems Settings > Configurations.
1. Typ in het vak Locatie van de map Systeemlettertypen het pad naar de map Klantlettertypen. U kunt meerdere mappen toevoegen, gescheiden door een puntkomma **;**
1. Klik op OK.
1. Start het systeem opnieuw waarop AEM-formulieren zijn geïnstalleerd.

>[!NOTE]
>
>De lettertypen worden gekozen uit de cache van het Windows-systeemlettertype en het systeem moet opnieuw worden opgestart om de cache bij te werken. Nadat u de lettertypemap voor de klant hebt opgegeven, dient u het systeem waarop AEM-formulieren zijn geïnstalleerd opnieuw te starten.
