---
title: Overzicht van het configureren van SSL
description: Leer over hoe te om veiligheid van mededeling te verbeteren door SSL te vormen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_ssl
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '211'
ht-degree: 0%

---

# Overzicht van het configureren van SSL {#overview-of-configuring-ssl}

U kunt SSL-referenties (Secure Sockets Layer) maken en SSL op de toepassingsserver configureren om de communicatie met uw toepassingsserver te verbeteren.

Als beveiligingsproduct vereist Rights Management de configuratie van SSL. Wanneer het vormen van SSL certificaten, zorg ervoor dat u slechts sleutels RSA gebruikt. SSL-certificaten met DSA-sleutels worden niet ondersteund.

De verstrekte informatie is van toepassing op kant-en-klare, automatische en handmatige installaties. Het biedt een voorbeeld van een methode om SSL te vormen. U kunt andere methodes ook gebruiken die voor uw netwerk of organisatie geschikter zijn.

>[!NOTE]
>
>U wordt aangeraden de installatie, configuratie en implementatie van uw AEM-formuliermodules te voltooien en ervoor te zorgen dat de producten correct worden uitgevoerd voordat u SSL configureert op de toepassingsserver.

>[!NOTE]
>
>Wanneer u SSL-beveiligingscertificaten en -referenties maakt, gebruikt u dezelfde gebruikersaccountrechten als waarmee u de toepassingsserver hebt uitgevoerd. Als de toepassingsserver wordt uitgevoerd met andere gebruikersrechten, wordt het formulier mogelijk niet correct weergegeven voor PDFForm-uitvoeringen wanneer ContentRootURI naar https wijst.

Als u een LDAP-server met SSL-functionaliteit hebt, configureert u Gebruikersbeheer voor samenwerking met deze server. (Zie [ Gebruikersbeheer voor een SSL-Toegelaten server LDAP ](/help/forms/using/admin-help/configure-user-management-ssl-enabled.md#configure-user-management-for-an-ssl-enabled-ldap-server) vormen.)
