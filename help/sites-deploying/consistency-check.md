---
title: Consistentie- en reiscontroles
description: Leer hoe u consistentiecontroles en transversale controles uitvoert.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
feature: Configuring
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 6ed130d5-30b5-4864-8bea-dfe41bed5422
source-git-commit: 408f6aaedd2cc0315f6e66b83f045ca2716db61d
workflow-type: tm+mt
source-wordcount: '147'
ht-degree: 0%

---

# Consistentie- en reiscontroles{#consistency-and-traversal-checks}

Tijdens de upgrade kunnen er problemen optreden als gevolg van inconsistenties in de werkruimte. U kunt een testupgrade uitvoeren om te zien of dit een probleem is, of de consistentiecontroles uitvoeren als een preventieve actie.

Als u een testverbetering in werking stelt die wegens werkruimteinconsistenties ontbreekt, ziet u ingangen gelijkend op het volgende in crx-quickstart/logs/crx/error.log:

```xml
*ERROR* TarPersistenceManager: No bundle found for uuid 'deadbeef-cafe-babe-cafe-babecafebabe'
 ...
*ERROR* RepositoryImpl: Failed to initialize workspace 'crx.default'
javax.jcr.RepositoryException: Error indexing workspace: Error indexing workspace: Error indexing workspace
...
```

## Een consistentiecontrole uitvoeren {#perform-a-consistency-check}

Om een consistentiecontrole uit te voeren, navigeer aan de beleidspagina voor JMX Mbean **com.adobe.granite (Bewaarplaats)**. Ga in het hoofdscherm van AEM naar:

**Hulpmiddelen > de Console van het Web > Hoofd (op menubar) > JMX > com.adobe.granite (Bewaarplaats)**

Op een standaardinstallatie, wordt het hier gevonden: **[|Show me|](http://localhost:4502/system/console/jmx/com.adobe.granite%3Atype%3DRepository)**

In de **sectie van Verrichtingen** van de pagina, vindt u twee methodes: **`traversalCheck`** en **`consistencyCheck`**. Als u een controle wilt uitvoeren, klikt u op de bewerking en voert u de gewenste parameters in.

![ chlimage_1-117 ](assets/chlimage_1-117.png)
