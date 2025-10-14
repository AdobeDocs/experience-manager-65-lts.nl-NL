---
title: CRXDE Lite inschakelen in AEM
description: Leer hoe u CRXDE Lite inschakelt in Adobe Experience Manager.
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: Security
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 109ab777-c7be-4725-8b91-c4e5d6a735ab
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '261'
ht-degree: 0%

---

# CRXDE Lite inschakelen in AEM{#enabling-crxde-lite-in-aem}

Om ervoor te zorgen dat de installaties van AEM zo veilig mogelijk zijn, adviseert de veiligheid controlelijst [&#x200B; onbruikbaar makend WebDAV &#x200B;](/help/sites-administering/security-checklist.md#disable-webdav) in productiemilieu&#39;s.

CRXDE Lite is echter afhankelijk van de juiste werking van de `org.apache.sling.jcr.davex` -bundel. Als u WebDAV uitschakelt, wordt CRXDE Lite ook uitgeschakeld.

Wanneer dit gebeurt, wordt bij het bladeren naar `https://serveraddress:4502/crx/de/index.jsp` een leeg hoofdknooppunt weergegeven en mislukken alle HTTP-aanvragen naar CRXDE Lite-bronnen:

```xml
404 Resource at '/crx/server/crx.default/jcr:root/.1.json' not found: No resource found
```

Hoewel deze aanbeveling bedoeld is om aanvalsoppervlakken zoveel mogelijk te beperken, hebben systeembeheerders soms toegang tot CRXDE Lite nodig om inhoud te kunnen doorbladeren of problemen met de foutopsporing op productieinstanties op te lossen.

U kunt CRXDE Lite met of [&#x200B; montages OSGi &#x200B;](#enabling-crxde-lite-osgi) of met het bevel van a [&#x200B; cURL &#x200B;](#enabling-crxde-lite-curl) toelaten.

>[!WARNING]
>
>Wegens lichte verschillen in hoe deze methodes werken zou u ***of*** OSGI ***of*** cURL moeten gebruiken.
>
>De twee methodes zijn ***niet*** onderling verwisselbaar.

## CRXDE Lite inschakelen met OSGI {#enabling-crxde-lite-osgi}

Indien uitgeschakeld, kunt u CRXDE Lite inschakelen door de onderstaande procedure te volgen:

1. Ga naar de console OSGi Components op `http://localhost:4502/system/console/components`
1. Zoek naar de volgende component:

   * `org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet`

1. Klik op het moersleutelpictogram naast het pictogram om de configuratieopties weer te geven:

   ![&#x200B; chlimage_1-80 &#x200B;](assets/chlimage_1-80a.png)

1. Maak de volgende configuratie:

   * **Wortingspad:** `/crx/server`
   * Tik de doos onder **absolute URIs van het Gebruik**.

1. Als u klaar bent met het gebruik van CRXDE Lite, moet u WebDAV opnieuw uitschakelen.

## CRXDE Lite inschakelen met cURL {#enabling-crxde-lite-curl}

U kunt CRXDE Lite ook via cURL inschakelen door (beide) de volgende twee opdrachten uit te voeren:

* Enable `create-absolute-uri` :

  ```shell
  curl -u admin:admin 'http://localhost:4502/system/console/configMgr/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet' --data-raw 'apply=true&action=ajaxConfigManager&%24location=&dav.create-absolute-uri=true&propertylist=dav.create-absolute-uri'
  ```

* Definiëren `alias` :

  ```shell
  curl -u admin:admin 'http://localhost:4502/system/console/configMgr/org.apache.sling.jcr.davex.impl.servlets.SlingDavExServlet' --data-raw 'apply=true&action=ajaxConfigManager&%24location=&alias=/crx/server&propertylist=alias'
  ```

## Overige bronnen {#other-resources}

Raadpleeg de volgende pagina&#39;s voor meer informatie over de beveiligingsfuncties van AEM 6:

* [De AEM-beveiligingscontrolelijst](/help/sites-administering/security-checklist.md)
* [AEM uitvoeren in productielodus](/help/sites-administering/production-ready.md)
