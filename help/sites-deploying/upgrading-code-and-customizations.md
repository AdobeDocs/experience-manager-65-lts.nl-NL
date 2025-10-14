---
title: Code en aanpassingen bijwerken
description: Meer weten over het upgraden van code en aanpassingen in AEM?
contentOwner: sarchiz
topic-tags: upgrading
products: SG_EXPERIENCEMANAGER/6.5/SITES
content-type: reference
docset: aem65
targetaudience: target-audience upgrader
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: 6b94caf1-97b7-4430-92f1-4f4d0415aef3
source-git-commit: f983fc1edc613feaa070c4e82a92aabab9d50cbb
workflow-type: tm+mt
source-wordcount: '1012'
ht-degree: 0%

---

# Code en aanpassingen bijwerken{#upgrading-code-and-customizations}

Bij het plannen van een upgrade moeten de volgende onderdelen van een implementatie worden onderzocht en aangepakt.

* [De basiscode bijwerken](#upgrade-code-base)
* [Testprocedure](#testing-procedure)

## Overzicht {#overview}

1. **de Analysator van AEM** - stel de Analysator van AEM in werking zoals die in verbeterings planning wordt beschreven, en die in detail op [&#x200B; wordt beschreven die de Complexiteit van de Verbetering met de Analysator van AEM &#x200B;](/help/sites-deploying/aem-analyzer.md) pagina beoordelen. Er verschijnt een AEM Analyzer-rapport met meer informatie over gebieden die moeten worden opgelost naast de niet-beschikbare API&#39;s/bundels in de doelversie van AEM. Het AEM Analyzer-rapport geeft een indicatie van incompatibiliteiten in uw code. Als er geen LTS bestaat, is uw implementatie al compatibel met 6,5 LTS. U kunt er nog steeds voor kiezen om nieuwe ontwikkelingen uit te voeren voor het gebruik van de 6.5 LTS-functionaliteit, maar dit is niet nodig voor het behoud van compatibiliteit.
1. **ontwikkelt de Basis van de Code voor 6.5 LTS** - creeer een specifieke tak of een bewaarplaats voor de codebasis voor de versie van het Doel. Gebruik info van Compatibiliteit vóór upgrade om gebieden met code te plannen die moeten worden bijgewerkt.
1. **compileert met 6.5 LTS Uber jar** - de basis POMs van de Update codebasis aan punt aan 6.5 LTS uber jar en compileert code tegen het.
1. **stelt aan 6.5 LTS Milieu** op - een schoon geval van AEM 6.5 LTS (Auteur + publiceer) zou omhoog in een milieu moeten worden gestaan Dev/QA. De bijgewerkte codebasis en een representatieve steekproef van inhoud (van huidige productie) zouden moeten worden opgesteld.
1. **QA- Bevestiging en Bug bevestigen** - QA zou de toepassing op zowel Auteur als publiceer instanties van 6.5 LTS moeten bevestigen. Alle gevonden fouten moeten worden gecorrigeerd en toegewezen aan de basis van de 6.5 LTS-code. Herhaal indien nodig de Dev-Cycle totdat alle bugs zijn opgelost.

Voordat u verdergaat met een upgrade, moet u beschikken over een stabiele basis voor toepassingscode die grondig is getest op AEM 6.5 LTS.

## De basiscode bijwerken {#upgrade-code-base}

### Creeer een Specifieke Tak voor 6.5 LTS Code in de Controle van de Versie {#create-a-dedicated-branch-for-6.5-lts-code-in-version-control}

Alle code en configuraties die vereist zijn voor uw AEM-implementatie, moeten met een of andere vorm van versiebeheer worden beheerd. Een specifieke tak in versiecontrole zou voor het beheren van om het even welke veranderingen nodig voor de codebasis in de doelversie van AEM moeten worden gecreeerd. Het iteratieve testen van de codebasis tegen de doelversie van AEM en de verdere insectenmoeilijke situaties wordt beheerd in deze tak.

### AEM Uber Jar-versie bijwerken {#update-the-aem-uber-jar-version}

De AEM Uber jar omvat alle AEM APIs als één enkele gebiedsdeel in uw Maven project `pom.xml`. Het is altijd verstandig om de Uber Jar op te nemen als één afhankelijkheid in plaats van afzonderlijke AEM API-afhankelijkheden op te nemen. Wanneer u de basiscode bijwerkt, wijzigt u de versie van Uber Jar zodat deze naar de 6.5 LTS-versie van AEM verwijst. Vervangen API&#39;s of methoden bijwerken zodat deze compatibel zijn met de doelversie van AEM. Compileer de codebasis opnieuw tegen de nieuwe versie van Uber Jar.

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>apis</classifier>
    <scope>provided</scope>
</dependency>
```

>[!NOTE]
>
>Er is een klein verschil in de manier waarop AEM 6.5 en AEM 6.5 LTS Uber Jars worden verpakt. Zie de volgende sectie:

**Jars van de Uber voor AEM 6.5**

1. `uber-jar-6.5.x.jar` - Bevat alle openbare API&#39;s van AEM 6.5.
1. `uber-jar-6.5.x-apis-with-deprecations.jar` - Bevat zowel openbare API&#39;s als verouderde API&#39;s van AEM 6.5.

**Jars van de Uber voor AEM 6.5 LTS**

Voor AEM 6.5 LTS zijn er weer twee soorten Uber Jars:

1. `uber-jar-6.6.x-apis.jar` - Bevat alle openbare API&#39;s van AEM 6.5 LTS.
1. `uber-jar-6.6.x-deprecated-apis.jar` - Alleen verouderde API&#39;s van AEM 6.5 LTS worden opgenomen.

**Zeer belangrijk Verschil: AEM 6.5 vs. AEM 6.5 LTS Uber Jars**

* Als u in AEM 6.5 zowel openbare als verouderde API&#39;s nodig hebt, kunt u de enkele jar `uber-jar-6.5.x-apis-with-deprecations.jar` in het `pom.xml` -bestand opnemen.
* Als u in AEM 6.5 LTS zowel openbare als verouderde API&#39;s nodig hebt, moet u twee aparte jars opnemen, `uber-jar-6.6.x-apis.jar` voor openbare API&#39;s en `uber-jar-6.6.x-deprecated-apis.jar` voor verouderde API&#39;s.

**Gemaakte coördinaten voor afgekeurde APIs Jar**

```
<dependency>
    <groupId>com.adobe.aem</groupId>
    <artifactId>uber-jar</artifactId>
    <version>6.6.0</version>
    <classifier>deprecated-apis</classifier>
    <scope>provided</scope>
</dependency>
```

### Notities ontwikkelaar {#developer-notes}

* AEM 6.5 LTS bevat geen Google guava-bibliotheek buiten de box, de vereiste versie kan naar behoefte worden geïnstalleerd.
* Sling XSS-bundel gebruikt nu de Java HTML Sanitizer-bibliotheek en het gebruik van de `XSSAPI#filterHTML()` -methode moet worden gebruikt voor het veilig renderen van HTML-inhoud en niet voor het doorgeven van gegevens naar andere API&#39;s.

## Testprocedure {#testing-procedure}

Er moet een uitgebreid testplan worden opgesteld voor het testen van upgrades. Het testen van de geüpgrade codebasis en de toepassing moet eerst in lagere omgevingen worden uitgevoerd. Eventuele fouten moeten op iteratieve wijze worden gecorrigeerd totdat de basis van de code stabiel is. Dit geldt alleen als omgevingen op een hoger niveau worden bijgewerkt.

### De upgradeprocedure testen {#testing-upgrade-procedure}

De verbeteringsprocedure zoals die hier wordt geschetst zou op Dev en milieu&#39;s QA zoals die in uw aangepast in werking gesteld boek worden gedocumenteerd (zie [&#x200B; plannend Uw Verbetering &#x200B;](/help/sites-deploying/upgrade-planning.md)). De verbeteringsprocedure zou moeten worden herhaald tot alle stappen in het verbeteringsloopboek worden gedocumenteerd en het verbeteringsproces is vlot.

### Testgebieden voor de implementatie  {#implementation-test-areas-}

Hieronder vindt u een aantal belangrijke onderdelen van een AEM-implementatie die onder uw testplan moeten vallen zodra de omgeving is bijgewerkt en de geüpgrade codebasis is geïmplementeerd.

<table>
 <tbody>
  <tr>
   <td><strong>Functioneel testgebied</strong></td>
   <td><strong>Beschrijving</strong></td>
  </tr>
  <tr>
   <td>Gepubliceerde sites</td>
   <td>Het testen van de implementatie van AEM en bijbehorende code op publiceren rij <br /> door Dispatcher. Neem criteria op voor pagina-updates en <br /> cachevalidatie.</td>
  </tr>
  <tr>
   <td>Authoring</td>
   <td>Testen van de AEM-implementatie en de bijbehorende code op de laag Auteur. Dit moet pagina, componentontwerp en dialoogvensters bevatten.</td>
  </tr>
  <tr>
   <td>Integratie met Experience Cloud-oplossingen</td>
   <td>Integraties met producten als Analytics valideren.</td>
  </tr>
  <tr>
   <td>Integraties met systemen van derden</td>
   <td>Valideer om het even welke derdeintegratie op zowel Auteur als Publish lijsten.</td>
  </tr>
  <tr>
   <td>Verificatie, beveiliging en machtigingen</td>
   <td>Eventuele verificatiemechanismen zoals LDAP/SAML moeten worden gevalideerd.<br /> De toestemmingen en de groepen zouden op zowel Auteur als Publish <br /> lijsten moeten worden getest.</td>
  </tr>
  <tr>
   <td>Zoekopdrachten</td>
   <td>De indexen en de vragen van de douane zouden samen met vraagprestaties moeten worden getest.</td>
  </tr>
  <tr>
   <td>UI-aanpassingen</td>
   <td>Extensies of aanpassingen van de gebruikersinterface van AEM in de ontwerpomgeving.</td>
  </tr>
  <tr>
   <td>Workflows</td>
   <td>Aangepast en/of uit de vakworkflows en -functionaliteit.</td>
  </tr>
  <tr>
   <td>Prestatietesten</td>
   <td>Het testen van de lading zou op zowel auteur als Publish rijen moeten worden uitgevoerd die real-world scenario's simuleren.</td>
  </tr>
 </tbody>
</table>

### Testplan en resultaten document {#document-test-plan-and-results}

Er moet een testplan worden opgesteld dat de bovengenoemde testgebieden voor de implementatie bestrijkt. Het is vaak zinvol om het testplan te scheiden van de taaklijsten Auteur en Publiceren. Dit testplan zou op Dev, QA, en de milieu&#39;s van het Stadium moeten worden uitgevoerd alvorens de milieu&#39;s van de Productie te bevorderen. Testresultaten en prestatiemetriek moeten in lagere omgevingen worden vastgelegd om vergelijkingen te kunnen maken bij het upgraden van de Stage- en Production-omgeving.
