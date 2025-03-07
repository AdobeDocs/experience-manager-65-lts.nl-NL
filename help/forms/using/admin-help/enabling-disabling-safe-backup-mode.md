---
title: Beveiligde back-upmodus in- en uitschakelen
description: Op de pagina Back-upinstellingen kunt u AEM-formulieren gebruiken in de veilige back-upmodus, zodat u op betrouwbare wijze een back-up kunt maken van uw database en de GDS-map (Global Document Storage). Leer hoe u de veilige back-upmodus in- en uitschakelt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 34381caa-154e-479c-b475-7b3549909e9a
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '208'
ht-degree: 0%

---

# Beveiligde back-upmodus in- en uitschakelen {#enabling-and-disabling-safe-backup-mode}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Op de pagina Back-upinstellingen kunt u AEM-formulieren gebruiken in de veilige back-upmodus, zodat u op betrouwbare wijze een back-up kunt maken van uw database en de GDS-map (Global Document Storage).

In AEM-formulieren in de veilige back-upmodus werkt dit normaal, maar worden bestanden niet actief uit de GDS-map verwijderd.

>[!NOTE]
>
>Als u deze optie instelt, wordt er geen back-up van uw systeem gemaakt; het systeem wordt voorbereid op back-up.

## Veilige back-upmodus inschakelen {#enable-safe-backup-mode}

1. Klik in de beheerconsole op Instellingen > Core Systems Settings > Backup Settings.
1. Selecteer in de pagina Back-upinstellingen de optie Werken in veilige back-upmodus en klik op OK.

>[!NOTE]
>
>Als het systeem al wordt uitgevoerd in de veilige back-upmodus, wordt er geen nieuwe reservatie gemaakt wanneer u op OK klikt.

## Veilige back-upmodus uitschakelen {#disable-safe-backup-mode}

1. Klik in de beheerconsole op Instellingen > Core Systems Settings > Backup Settings.
1. Schakel op de pagina Back-upinstellingen de optie Bewerken in veilige back-upmodus uit en klik op OK.
