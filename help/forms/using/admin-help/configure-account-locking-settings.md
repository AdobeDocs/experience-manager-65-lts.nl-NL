---
title: Instellingen voor accountvergrendeling configureren
description: Gebruik de optie Account vergrendelen inschakelen om gebruikersaccounts te vergrendelen na een opgegeven aantal opeenvolgende verificatiefouten.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_managing_domains
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: e78860dc-9375-465c-b1fa-2a4827ca8dce
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '202'
ht-degree: 0%

---

# Instellingen voor accountvergrendeling configureren {#configure-account-locking-settings}


>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Wanneer u een domein toevoegt, geeft u op of accountvergrendeling moet worden ingeschakeld. Als de optie Account vergrendelen inschakelen is geselecteerd, worden gebruikersaccounts vergrendeld na een opgegeven aantal opeenvolgende verificatiefouten. Na een opgegeven periode kan de gebruiker opnieuw proberen te verifiëren. Met deze functie voorkomt u dat gebruikers verschillende aanmeldingscombinaties proberen te openen.

De montages van het gebruik op de pagina van het Beheer van het Domein om het maximumaantal authentificatiemislukkingen en de tijdsduur te specificeren dat de rekeningen worden gesloten. Deze instellingen zijn van toepassing op alle domeinen waarvoor accountvergrendeling is ingeschakeld.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Domain Management]** .
1. Voer in het vak Maximum aantal opeenvolgende verificatiefouten het aantal opeenvolgende keren in dat een gebruiker zich zonder succes kan aanmelden voordat zijn account is vergrendeld. De standaardwaarde is 20.
1. Voer in het vak Account ontgrendelen na (minuten) het aantal minuten in dat de gebruikersaccount is vergrendeld. Na het opgegeven aantal minuten kan de gebruiker opnieuw proberen zich aan te melden. De standaardwaarde is 30.
1. Klik op **[!UICONTROL Save]**.
