---
title: Pagina's aanpassen die worden weergegeven door de fouthandler
description: Adobe Experience Manager wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: platform
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 4f98853d-306f-4d11-a3d8-83122b372b2d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '525'
ht-degree: 0%

---

# Pagina&#39;s aanpassen die worden weergegeven door de fouthandler{#customizing-pages-shown-by-the-error-handler}

Adobe Experience Manager (AEM) wordt geleverd met een standaardfouthandler voor de afhandeling van HTTP-fouten, bijvoorbeeld door het volgende weer te geven:

![ chlimage_1-67 ](assets/chlimage_1-67a.png)

Door het systeem verschafte scripts bestaan (onder `/libs/sling/servlet/errorhandler`) om te reageren op foutcodes. Standaard zijn de volgende scripts beschikbaar met een standaard CQ-instantie:

* 403.jsp
* 404.jsp

>[!NOTE]
>
>AEM is gebaseerd op Apache Sling. Als dusdanig, zie [ de Behandeling van de Fout ](https://sling.apache.org/documentation/the-sling-engine/errorhandling.html) voor gedetailleerde informatie over het Verdelen van fout behandeling.

>[!NOTE]
>
>Op een auteursinstantie, wordt [ CQ WCM zuivert Filter ](/help/sites-deploying/osgi-configuration-settings.md) toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Op publiceer instantie, is CQ WCM zuivert Filter *altijd* gehandicapt (zelfs als gevormd zoals toegelaten).

## Hoe te om Pagina&#39;s aan te passen die door de Handler van de Fout worden getoond {#how-to-customize-pages-shown-by-the-error-handler}

U kunt uw eigen scripts ontwikkelen om de pagina&#39;s aan te passen die door de fouthandler worden weergegeven wanneer een fout optreedt. De aangepaste pagina&#39;s worden gemaakt onder `/apps` en bedekken de standaardpagina&#39;s (onder `/libs` ).

>[!NOTE]
>
>Zie [ Gebruikend Bedekkingen ](/help/sites-developing/overlays.md) voor meer details.

1. Kopieer de standaardscripts in de opslagplaats:

   * Van `/libs/sling/servlet/errorhandler/`
   * tot `/apps/sling/servlet/errorhandler/`

   Aangezien het bestemmingspad niet standaard bestaat, moet u het creëren wanneer het doen dit voor het eerst.

1. Navigeer naar `/apps/sling/servlet/errorhandler` en voer een van de volgende handelingen uit:

   * bewerk het juiste bestaande script, zodat u de vereiste informatie kunt opgeven.
   * Maak en bewerk een nieuw script voor de vereiste code.

1. Sla de wijzigingen op en test u deze.

>[!CAUTION]
>
>De handlers 404.jsp en 403.jsp zijn ontworpen om voor authentificatie CQ5 te behandelen; in het bijzonder, om systeemlogin toe te staan als er deze fouten zijn.
>
>Daarom moeten deze twee handlers met grote zorg worden vervangen.

### De reactie op HTTP 500-fouten aanpassen {#customizing-the-response-to-http-errors}

HTTP 500 fouten worden veroorzaakt door server-zijuitzonderingen.

* **[500 Interne Fout van de Server ](https://www.w3.org/Protocols/rfc2616/rfc2616-sec10.html)**
De server heeft een onverwachte voorwaarde aangetroffen waardoor deze de aanvraag niet kan uitvoeren.

Wanneer de aanvraagverwerking resulteert in een uitzondering, is het Apache Sling-framework (waarop AEM is gebouwd):

* meldt de uitzondering
* retourneert:

   * de HTTP-antwoordcode 500
   * de spoor van de uitzonderingsstapel

  in het lichaam van de reactie.

Door [ aan te passen kunnen de pagina&#39;s die door de foutenmanager ](#how-to-customize-pages-shown-by-the-error-handler) worden getoond a `500.jsp` manuscript worden gecreeerd. Deze wordt echter alleen gebruikt als `HttpServletResponse.sendError(500)` expliciet wordt uitgevoerd, dat wil zeggen van een uitzonderingscatcher.

Anders is de antwoordcode ingesteld op 500, maar wordt het script `500.jsp` niet uitgevoerd.

Als u 500 fouten wilt afhandelen, moet de bestandsnaam van het script van de fouthandler gelijk zijn aan de uitzonderingsklasse (of superklasse). Om al dergelijke uitzonderingen te behandelen, kunt u een manuscript `/apps/sling/servlet/errorhandler/Throwable.js` p of `/apps/sling/servlet/errorhandler/Exception.jsp` tot stand brengen.

>[!CAUTION]
>
>Op een auteursinstantie, wordt [ CQ WCM zuivert Filter ](/help/sites-deploying/osgi-configuration-settings.md) toegelaten door gebrek. Dit resulteert altijd in reactiecode 200. De standaardfoutenmanager antwoordt door het volledige stapelspoor aan de reactie te schrijven.
>
>Voor een douane fout-manager, zijn de reacties met code 500 nodig - zodat moet de [ CQ WCM zuivert Filter ](/help/sites-deploying/osgi-configuration-settings.md) worden onbruikbaar gemaakt. Dit zorgt ervoor dat reactiecode 500 is teruggekeerd, die beurtelings de correcte fout-manager van het Sling teweegbrengt.
>
>Op publiceer instantie, is CQ WCM zuivert Filter *altijd* gehandicapt (zelfs als gevormd zoals toegelaten).
