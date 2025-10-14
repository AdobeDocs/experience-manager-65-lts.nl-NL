---
title: XCI-configuratieopties opgeven
description: Leer hoe u de XCI-configuratieopties opgeeft. U kunt aangepaste waarden voor XCI-bestanden opgeven voor Adaptief formulier, zodat dit kan worden gebruikt tijdens het genereren van formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_output
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 5fb6e6cc-6af7-4cf5-804b-bb3030079383
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '161'
ht-degree: 0%

---

# XCI-configuratieopties opgeven {#specify-xci-configuration-options}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Met Output kunt u een aangepast XCI-bestand opgeven dat wordt gebruikt voor rendering. Zie [&#x200B; dossierplaatsen voor Output &#x200B;](/help/forms/using/admin-help/specify-file-locations-output.md#specify-file-locations-for-output) specificeren.

Standaard overschrijft Output enkele opties die in het XCI-bestand zijn opgegeven, waaronder de volgende:

* `config/present/xdp/packets`
* `config/present/pdf/creator`
* `config/present/pdf/producer`
* `config/present/pdf/compression/compressObjectStream`

U kunt opties selecteren waarmee de overschrijving voor de bovenstaande opties wordt geannuleerd. In dat geval gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.

1. In beleidsconsole, klik **Diensten** > output.
1. Schakel het selectievakje Systeemstandaard XCI-opties gebruiken in of uit. Wanneer deze optie is geselecteerd, gebruikt Output de standaardwaarden voor de pakketten, de maker, de producent en de compressObjectStream-instellingen. Als deze optie is uitgeschakeld, gebruikt Output de waarden die zijn opgegeven in het aangepaste XCI-bestand.
1. Klik **sparen**.
