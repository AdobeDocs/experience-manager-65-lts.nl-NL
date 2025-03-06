---
title: Gebruikersinterface selecteren
description: Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface.
contentOwner: Chris Bohnert
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Authoring
role: User
exl-id: 781b580a-e4d1-419e-afb1-884c8fb634b9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '195'
ht-degree: 0%

---

# Gebruikersinterface selecteren{#selecting-your-ui}

Aangezien de interface met aanraakbediening de klassieke interface vervangt, moet de gebruiker of beheerder van de AEM-instantie een actief besluit nemen om de klassieke UI te blijven gebruiken. Omdat klassieke UI niet meer wordt gehandhaafd, is er geen manier voor de auteursgebruiker eenvoudig om van klassieke UI aan het equivalent in aan aanraking-toegelaten UI over te schakelen.

Voor het gemak waarmee gebruikers kunnen ontwerpen, maakt de interface met aanraakbediening het mogelijk om indien nodig over te schakelen op de klassieke interface. Zie [ Selecterend uw UI ](/help/sites-authoring/select-ui.md) in de standaardAuthoring documentatie voor details.

>[!NOTE]
>
>Instanties die zijn bijgewerkt vanaf een vorige versie behouden de klassieke interface voor het ontwerpen van pagina&#39;s.
>
>Na verbetering, zal de paginascreatie niet automatisch geschakeld worden aan aanraking-toegelaten UI, maar u kunt dit vormen gebruikend de [ configuratie OSGi ](/help/sites-deploying/configuring-osgi.md) van de **WCM Authoring UI van de Wijze van de Wijze** ( `AuthoringUIMode` dienst). Zie [ met voeten treedt UI voor de Redacteur ](#uioverridesfortheeditor).

## De standaardinterface voor uw instantie configureren {#configuring-the-default-ui-for-your-instance}

Een systeembeheerder kan UI vormen die bij opstarten en login door [ Toewijzing van de Wortel te gebruiken ](/help/sites-deploying/osgi-configuration-settings.md#daycqrootmapping) wordt gezien.

Dit kan door gebruikersgebreken of zittingsmontages worden met voeten getreden.
