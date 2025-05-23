---
title: Het CSRF-beschermingskader
description: Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: introduction
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: d6bd4028-56c9-4e09-9bba-1199a41b41b8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '247'
ht-degree: 0%

---

# Het CSRF-beschermingskader{#the-csrf-protection-framework}

Naast het filter Apache Sling Referrer biedt Adobe ook een nieuw CSRF-beschermingskader dat bescherming biedt tegen dit type aanvallen.

Het framework maakt gebruik van tokens om te garanderen dat het verzoek van de klant legitiem is. De tokens worden gegenereerd wanneer het formulier naar de client wordt verzonden en gevalideerd wanneer het formulier naar de server wordt teruggestuurd.

>[!NOTE]
>
>De publicatie-instanties bevatten geen tokens voor anonieme gebruikers.

## Vereisten {#requirements}

### Afhankelijkheden {#dependencies}

Elke component die afhankelijk is van `granite.jquery` , kan automatisch profiteren van het CSRF-beveiligingsframework. Als dat niet het geval is, moet u voor een van uw componenten een afhankelijkheid naar `granite.csrf.standalone` declareren voordat u het framework kunt gebruiken.

### De crypto-sleutel repliceren {#replicating-crypto-keys}

Om de tokens te gebruiken, moet u het binaire getal HMAC aan alle instanties in uw plaatsing herhalen. Zie [ het Repliceren van de sleutel HMAC ](/help/sites-administering/encapsulated-token.md#replicating-the-hmac-key) voor meer details.

>[!NOTE]
>
>Zorg ervoor u ook de noodzakelijke de configuratieveranderingen van Dispatcher aanbrengt om het Kader van de Bescherming te gebruiken CSRF:
>
>* [ Vormend Adobe Experience Manager Dispatcher om Aanvallen te verhinderen CSRF ](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/configuring/configuring-dispatcher-to-prevent-csrf)
>* [ het Overzicht van Dispatcher ](https://experienceleague.adobe.com/nl/docs/experience-manager-dispatcher/using/dispatcher)

>[!NOTE]
>
>Als u het duidelijke geheime voorgeheugen met uw Webtoepassing gebruikt, zorg ervoor u &quot;**&amp;ast toevoegt;**&quot;aan manifest om ervoor te zorgen het teken niet de symbolische generatievraag CSRF offline neemt. Voor meer informatie, raadpleeg deze [ verbinding ](https://www.w3.org/TR/offline-webapps/).
>
>Voor meer informatie over aanvallen CSRF en manieren om hen te verlichten, zie de [ pagina van OWASP van het Verzoek van de Versmeding van de Vergroting van de Deposito&#39;s van de Deposito&#39;s de ](https://owasp.org/www-community/attacks/csrf).
