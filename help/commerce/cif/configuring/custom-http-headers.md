---
title: Aangepaste HTTP-headers
description: Leer hoe u aangepaste HTTP-headers configureert in Adobe Experience Manager Commerce.
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: f25cd95c-4235-4430-8a51-38be1f39b880
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '272'
ht-degree: 0%

---

# Aangepaste HTTP-headers {#custom-http-headers}

## Overzicht {#overview}

Om meer controle over hun achterkant te krijgen, kunnen de auteurs de kopballen van douaneHTTP vormen die naar de handelingsmotor, samen met degenen zouden worden verzonden die reeds door CIF worden verzonden. Veelvoorkomende gebruiks-gevallen omvatten multi-store montages waarin u de kopballen van HTTP kunt gebruiken om de reactie van de handel achterste-eind te controleren.

>[!NOTE]
>
>Ontwikkelaars kunnen aangepaste HTTP-headers altijd configureren met de GraphQL-clientconfiguratie.
>

## Configuratie {#configuration}

Om de kopballen van douaneHTTP te vormen, moet men hen eerst bepalen. De kopballen van douaneHTTP moeten eerst worden bepaald door hen aan de `com.adobe.cq.cif.http.internal.HttpHeadersConfigProviderImpl` de dienstconfiguratie toe te voegen gebruikend een OSGi config.

U kunt de waarden van de kopballen van HTTP in de pagina van de Configuratie van Cloud Service voor uw project vormen:

1. Ga naar de Cloud Service-configuratiepagina in Tools > Cloud Services > CIF Configuration.
1. Open een bestaande configuratie of maak een configuratie.
1. Ga naar het tabblad &quot;Geavanceerd&quot; en zoek het multiveld &quot;Aangepaste HTTP-headers&quot;. U kunt de eerder gedefinieerde kopteksten selecteren en er waarden aan toewijzen.

De componenten die de bovenstaande cloudserviceconfiguratie gebruiken, verzenden deze HTTP-headers met elke GraphQL-aanvraag.

## Beperkingen {#restrictions}

Terwijl de dienst voor om het even welke kopbalnamen om toestaat worden bepaald, met inbegrip van de standaarddegenen, zijn zij niet beschikbaar voor het vormen. Met andere woorden, u kunt de standaard HTTP-headers niet overschrijven met deze functie. Een lijst van beperkte kopbalnamen kan onder [ worden gevonden mdn- Webdocumenten - de kopballen van HTTP ](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers). Daarnaast zijn er nog twee headers die niet kunnen worden gebruikt:

* &quot;Winkel&quot; - wordt door CIF gebruikt om de Adobe Commerce-winkel te identificeren
* &quot;Voorvertoning-versie&quot; - wordt gebruikt door CIF om gefaseerde producten op te halen
