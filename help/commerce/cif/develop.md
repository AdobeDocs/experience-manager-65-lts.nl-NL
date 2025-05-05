---
title: AEM Commerce ontwikkelen
description: Leer hoe te om een handel-toegelaten project van AEM te produceren gebruikend het het projectarchetype van AEM. Leer hoe u het project bouwt en implementeert in een lokale ontwikkelomgeving.
topics: Commerce, Development
feature: Commerce Integration Framework
doc-type: tutorial
kt: 5826
thumbnail: 39476.jpg
solution: Experience Manager,Commerce
role: Admin, Developer
exl-id: 22fcdadf-12c0-4545-a854-76345806386f
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# AEM Commerce ontwikkelen {#develop}

Voor de ontwikkeling van AEM Commerce-projecten op basis van Commerce integration framework (CIF) voor AEM gelden dezelfde regels en beste praktijken als voor andere AEM-projecten. Bekijk eerst deze:

- [AEM Developing User Guide](/help/sites-developing/getting-started.md)
- [AEM Core Concepts](/help/sites-developing/the-basics.md)
- [AEM Development - Guidelines and Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md)
- [AEM-projecten bouwen met Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale ontwikkeling voor AEM Commerce {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor het werken met CIF-projecten.

>[!NOTE]
>
>De volgende instructies helpen u bij het instellen van een lokale AEM-ontwikkelomgeving voor AEM Commerce met CIF (met focus voor AEM 6.5 LTS). Als u AEM as a Cloud Service gebruikt, zie de [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content-and-commerce/home.html) documentatie van 0&rbrace; AEM Commerce as a Cloud Service.

De AEM Commerce Add-On voor AEM, de zogenaamde CIF Add-On, is ook beschikbaar voor lokale ontwikkeling en wordt geleverd als een AEM-pakket. Het kan van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) als eigenschappak worden gedownload.

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- Lokale AEM 6.5 LTS
- [ Java 17 ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [ Apache Maven ](https://maven.apache.org/) (3.3.9 of nieuwer)
- [ Knoop LTS ](https://nodejs.org/en/)
- [ npm 6+ ](https://www.npmjs.com/)
- [ Git ](https://git-scm.com/)

### Toegang tot de CIF Add-on

CIF toe:voegen-op kan van het [ portaal van de Distributie van de Software worden gedownload ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html), onderzoek naar &quot;toe:voegen-op van AEM Commerce&quot;.

>[!TIP]
>
>Gebruik altijd de nieuwste versie van CIF Add-On.

### Lokale instellingen

Voor de ontwikkeling van lokale CIF-projecten met de invoegtoepassing AEM en CIF gaat u als volgt te werk:

1. Pak de AEM .jar uit om de `crx-quickstart` -map te maken. Voer de volgende handelingen uit:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` -map maken

1. Kopieer de invoegtoepassing CIF naar alle pakketten die u hebt gedownload van de portal voor softwaredistributie naar de map `crx-quickstart/install` .

>[!TIP]
>
>U kunt het invoegpakket voor CIF ook installeren via Package Manager.

1. De AEM-snelstart starten

Controleer de installatie via de OSGI-console: `http://localhost:4502/system/console/osgi-installer` . De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI configuraties bevatten. Zorg ervoor dat alle bundels zijn gestart.

## Projectinstelling {#project}

Er zijn twee manieren om uw AEM Commerce-project met CIF te starten.

### AEM Project Archetype gebruiken

Het [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel om een vooraf gevormd project op te starten om met CIF te beginnen. CIF Core Components en alle vereiste configuraties kunnen met één extra optie in een gegenereerd project worden opgenomen.

>[!TIP]
>
>Gebruik [ Archetype 25 van het Project van AEM of later ](https://github.com/adobe/aem-project-archetype/releases) om het project te produceren.

Zie het Archieftype van het Project van AEM [ gebruiksinstructies ](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een project van AEM te produceren. Als u CIF wilt opnemen in het project, gebruikt u de optie `includeCommerce` .

Bijvoorbeeld:

```bash
mvn -B archetype:generate \
 -D archetypeGroupId=com.adobe.granite.archetypes \
 -D archetypeArtifactId=aem-project-archetype \
 -D aemVersion=6.5.5 \
 -D appTitle="My Site" \
 -D appId="mysite" \
 -D groupId="com.mysite" \
 -D frontendModule=general \
 -D includeExamples=n \
 -D includeCommerce=y
```

CIF Core Components kan in elk project worden gebruikt door het meegeleverde `all` -pakket op te nemen of door een individu te gebruiken met het CIF-inhoudspakket en verwante OSGI-bundels. Om de Componenten van de Kern van CIF aan een project manueel toe te voegen gebruiken de volgende gebiedsdelen:

```java
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-apps</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-config</artifactId>
    <type>zip</type>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>core-cif-components-core</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>graphql-client</artifactId>
    <version>x.y.z</version>
</dependency>
<dependency>
    <groupId>com.adobe.commerce.cif</groupId>
    <artifactId>magento-graphql</artifactId>
    <version>x.y.z</version>
</dependency>
```

### AEM Venia Reference Store gebruiken

Een tweede optie om een project van CIF te beginnen is de [ Opslag van de Verwijzing van AEM te klonen en te gebruiken Venia ](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Om met de Opslag van de Verwijzing van Venia eenvoudig te beginnen klonen de [ bewaarplaats van het Git ](https://github.com/adobe/aem-cif-guides-venia) en beginnen het project overeenkomstig uw behoeften aan te passen.

>[!NOTE]
>
>Het Venia Reference Store-project bevat twee buildprofielen voor AEM as a Cloud Service en AEM 6.5. Controleer [ project readme.md ](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt. Gebruik voor AEM 6.5 het profiel `classic` .

### AEM verbinden met het Commerce-systeem

Om uw project met het handelssysteem te verbinden moet AEM met het eindpunt van GraphQL van uw handelssysteem worden gevormd.

Zowel, omvat een project dat door het [ Archieftype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) of de [ Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt geproduceerd, reeds a [ gebrek config ](https://github.com/adobe/aem-cif-guides-venia/blob/main/ui.config/src/main/content/jcr_root/apps/venia/osgiconfig/config/com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json) dat moet worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt van GraphQL van uw handelsysteem dat door het project wordt gebruikt.

De AEM Commerce Add-On en CIF Core Components maken via de AEM-server en rechtstreeks via de browser verbinding met het GraphQL-eindpunt voor handel. CIF Core Components voor client-side en CIF Add-On ontwerpgereedschappen maken standaard verbinding met `/api/graphql` . Indien nodig kan dit worden aangepast via de CIF Cloud Service config (zie hieronder).

De invoegtoepassing CIF biedt een servlet voor GraphQL-proxy op `/api/graphql` . Als u geen lokale AEM Dispatcher wilt gebruiken, wordt u aangeraden ook de proxyserver van GraphQL te configureren.

Navigeer naar http://localhost:4502/system/console/configMgr en maak een OSGI-config voor de `Adobe CIF GraphQL Proxy Configuration` -service. Gebruik hetzelfde GraphQL-eindpunt van uw handelssysteem als hierboven voor de GraphQL-client.

## Aanvullende bronnen

- [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype)
- [ de Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia)
