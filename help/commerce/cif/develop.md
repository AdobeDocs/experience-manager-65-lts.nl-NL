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
source-git-commit: 5995dda0aac101e6c0d506ac5bba786674b0735b
workflow-type: tm+mt
source-wordcount: '765'
ht-degree: 0%

---

# AEM Commerce ontwikkelen {#develop}

Voor de ontwikkeling van AEM Commerce-projecten op basis van Commerce integration framework (CIF) voor AEM gelden dezelfde regels en beste praktijken als voor andere AEM-projecten. Lees eerst het volgende:

- [AEM Developing User Guide](/help/sites-developing/getting-started.md)
- [AEM Core Concepts](/help/sites-developing/the-basics.md)
- [AEM Development - Guidelines and Best Practices](/help/sites-developing/dev-guidelines-bestpractices.md)
- [AEM-projecten bouwen met Apache Maven](/help/sites-developing/ht-projects-maven.md)

## Lokale ontwikkeling voor AEM Commerce {#local}

Een lokale ontwikkelomgeving wordt aanbevolen voor het werken met CIF-projecten.

>[!NOTE]
>
>De volgende instructies helpen u bij het instellen van een lokale AEM-ontwikkelomgeving voor AEM Commerce met CIF (met focus voor AEM 6.5 LTS). Als u AEM as a Cloud Service gebruikt, zie de [ documentatie van 0} AEM Commerce as a Cloud Service.](https://experienceleague.adobe.com/en/docs/experience-manager-cloud-service/content/content-and-commerce/introduction#)

De invoegtoepassing AEM Commerce voor AEM, de zogenaamde CIF Add-on, is ook beschikbaar voor lokale ontwikkeling en wordt geleverd als een AEM-pakket. Het kan van het [ Portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html) als eigenschappak worden gedownload.

### Vereiste software

Het volgende moet lokaal worden geïnstalleerd:

- Lokale AEM 6.5 LTS
- [ Java 17/Java 21 ](https://downloads.experiencecloud.adobe.com/content/software-distribution/en/general.html)
- [ Apache Maven ](https://maven.apache.org/) (3.3.9 of nieuwer)
- [ Knoop LTS ](https://nodejs.org/en/)
- [ npm 6+ ](https://www.npmjs.com/)
- [ Git ](https://git-scm.com/)

### De CIF-invoegtoepassing openen

CIF toe:voegen-op kan van het [ portaal van de Distributie van de Software worden gedownload ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html), onderzoek naar `AEM Commerce add-on`.

>[!TIP]
>
>Zorg ervoor dat u altijd de nieuwste CIF-invoegtoepassing gebruikt.

### Lokale instellingen

Ga als volgt te werk voor de ontwikkeling van lokale CIF-projecten met AEM en de add-on CIF:

1. Pak de AEM .jar uit om de `crx-quickstart` -map te maken. Voer de volgende handelingen uit:

   ```bash
   java -jar <jar name> -unpack
   ```

1. Een `crx-quickstart/install` -map maken

1. Kopieer de invoegtoepassing CIF naar alle pakketten die u hebt gedownload van de portal voor softwaredistributie naar de map `crx-quickstart/install` .

>[!TIP]
>
>U kunt de invoegtoepassing voor CIF ook installeren met Package Manager.

1. De AEM-snelstart starten

Verifieer de opstelling door de console OSGI: `http://localhost:4502/system/console/osgi-installer`. De lijst moet de CIF add-on gerelateerde bundels, content-package en OSGI configuraties bevatten. Zorg ervoor dat alle bundels zijn gestart.

## Projectinstelling {#project}

Er zijn twee manieren om uw AEM Commerce-project met CIF te starten.

### AEM Project Archetype gebruiken

Het [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) is het belangrijkste hulpmiddel aan Bootstrap een vooraf gevormd project om met CIF te beginnen. CIF Core Components en alle vereiste configuraties kunnen met één extra optie in een gegenereerd project worden opgenomen.

>[!TIP]
>
>Gebruik [ Archetype 25 van het Project van AEM of later ](https://github.com/adobe/aem-project-archetype/releases) om het project te produceren.

Zie het Archieftype van het Project van AEM [ gebruiksinstructies ](https://github.com/adobe/aem-project-archetype#usage) op hoe te om een project van AEM te produceren. Als u CIF in het project wilt opnemen, gebruikt u de optie `includeCommerce` .

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

U kunt CIF Core-componenten in elk project gebruiken. Neem alleen het meegeleverde `all` -pakket op of gebruik het CIF-inhoudspakket en de gerelateerde OSGi-bundels afzonderlijk. Voeg de Componenten van de Kern van CIF aan een project manueel toe door de volgende gebiedsdelen te gebruiken:

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

### AEM Venia-referentiearchief gebruiken

Een tweede optie om een project van CIF te beginnen is de [ Opslag van de Verwijzing van AEM te klonen en te gebruiken Venia ](https://github.com/adobe/aem-cif-guides-venia). De AEM Venia Reference Store is een voorbeeldtoepassing die het gebruik van CIF Core Components voor AEM aantoont. Het is bedoeld als een set voorbeelden van best practices en een mogelijk beginpunt voor het ontwikkelen van uw eigen functionaliteit.

Krijg begonnen met de Opslag van de Verwijzing van Venia door de [ bewaarplaats van het Git ](https://github.com/adobe/aem-cif-guides-venia) te klonen en begin het project overeenkomstig uw behoeften aan te passen.

>[!NOTE]
>
>Het Venia Reference Store-project bevat twee buildprofielen voor AEM as a Cloud Service en AEM 6.5. Controleer [ project readme.md ](https://github.com/adobe/aem-cif-guides-venia/blob/main/README.md) om te zien hoe zij worden gebruikt. Gebruik voor AEM 6.5 het profiel `classic` .

### AEM verbinden met het Commerce-systeem

Om uw project met het handelssysteem te verbinden, moet AEM met het eindpunt van GraphQL van uw handelssysteem worden gevormd.

Zowel, omvat een project dat door het [ Archieftype van het Project van AEM ](https://github.com/adobe/aem-project-archetype) of de [ Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia) wordt geproduceerd, reeds een standaardconfiguratie die moet worden aangepast.

Vervang de waarde van `url` in `com.adobe.cq.commerce.graphql.client.impl.GraphqlClientImpl~default.cfg.json` met het eindpunt van GraphQL van uw handelsysteem dat door het project wordt gebruikt.

De AEM Commerce add-on en CIF Core Components maken via de AEM-server verbinding met het Commerce GraphQL-eindpunt. Of rechtstreeks vanuit de browser. CIF Core Components aan de clientzijde en de CIF add-on ontwerpgereedschappen maken standaard verbinding met `/api/graphql` . Indien nodig, kunt u het aanpassen door CIF Cloud Service config (zie hieronder).

De invoegtoepassing CIF biedt een servlet voor GraphQL-proxy op `/api/graphql` . Als u geen lokale AEM Dispatcher wilt gebruiken, wordt u aangeraden ook de proxyserver van GraphQL te configureren.

Navigeer naar http://localhost:4502/system/console/configMgr en maak een OSGI-config voor de `Adobe CIF GraphQL Proxy Configuration` -service. Gebruik hetzelfde GraphQL-eindpunt van uw handelssysteem als hierboven voor de GraphQL-client.

## Aanvullende bronnen

- [ Archetype van het Project van AEM ](https://github.com/adobe/aem-project-archetype)
- [ de Opslag van de Verwijzing van AEM Venia ](https://github.com/adobe/aem-cif-guides-venia)
