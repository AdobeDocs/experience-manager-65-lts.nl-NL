---
title: Time-outwaarden instellen voor gebruik met Acrobat Reader DC Extensions
description: Leer hoe u time-outwaarden instelt voor gebruik met Acrobat Reader DC Extensions.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: eded255b54ff83f60f73cece8824c778d3a87680
workflow-type: tm+mt
source-wordcount: '189'
ht-degree: 0%

---

# Time-outwaarden instellen voor gebruik met Acrobat Reader DC Extensions  {#setting-timeout-values-for-use-with-acrobat-reader-dc-extensions}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Wanneer u met veel PDF-bestanden werkt in Acrobat Reader DC Extensions, moet u ervoor zorgen dat de volgende time-outwaarden op de juiste wijze zijn ingesteld om te voorkomen dat taken time-out en failed:

**Tijdslimiet van de Verplaatsing van het Document**

Deze waarde kan in de beleidsconsole worden geplaatst. Klik op Instellingen > Core System Settings > Configurations en geef een waarde op voor Default Document Disposal Timeout.

**de vormTimeout van AEM van de Manager van de Gebruiker:** Deze waarde kan worden geplaatst door het config.xml- dossier uit te geven. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren en klik vervolgens op Exporteren. Open het geëxporteerde bestand config.xml en bewerk de volgende regels:

&lt;entry key=&quot;assertionValidityInMinutes&quot; value=&quot;600&quot;/>

&lt;entry key=&quot;SessionTimeout&quot; value=&quot;600&quot;/>

Sla het bestand config.xml op en importeer het vervolgens weer in de beheerconsole.

**Time-out van de Zitting van de Server van de Toepassing:** Deze waarde kan op de toepassingsserver worden geplaatst. Raadpleeg de documentatie bij de toepassingsserver voor meer informatie.
