---
title: Ontwikkelingsinstrumenten
description: Voor het ontwikkelen van uw JCR-, Apache Sling- of Adobe Experience Manager-toepassingen zijn verschillende gereedschapssets beschikbaar.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
exl-id: 46db0690-03e9-4b31-aa44-200f224f3707
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '365'
ht-degree: 0%

---

# Ontwikkelingsinstrumenten{#development-tools}

Voor het ontwikkelen van JCR-, Apache Sling- of Adobe Experience Manager-toepassingen (AEM) zijn de volgende gereedschapssets beschikbaar:

* één reeks die uit [&#x200B; CRXDE Lite &#x200B;](/help/sites-developing/developing-with-crxde-lite.md) en WebDAV bestaat. CRXDE Lite is ingesloten in CRX/AEM en biedt u de mogelijkheid om standaard ontwikkelingstaken uit te voeren in de browser. Met CRXDE Lite kunt u bestanden (zoals .jsp en .java), mappen, sjablonen, componenten, dialoogvensters, knooppunten, eigenschappen en bundels maken en bewerken terwijl u zich aanmeldt en integreert met SVN.

  CRXDE Lite wordt aanbevolen wanneer u geen directe toegang hebt tot de CRX/AEM-server, wanneer u een toepassing ontwikkelt door de componenten en Java™-bundels buiten de box uit te breiden of te wijzigen of wanneer u geen speciale foutopsporing, codevoltooiing en syntaxismarkering nodig hebt.

* één stel bestaande uit:
   * Een geïntegreerde ontwikkelomgeving. Bijvoorbeeld, [&#x200B; Verduistering &#x200B;](/help/sites-developing/howto-projects-eclipse.md) of [&#x200B; IntelliJ &#x200B;](/help/sites-developing/ht-intellij.md).
   * Een bouwstijlhulpmiddel. Bijvoorbeeld, [&#x200B; Apache Maven &#x200B;](/help/sites-developing/ht-projects-maven.md).
   * FileVault die door Adobe is ontwikkeld om een opslagplaats toe te wijzen aan een bestandssysteem, een versiecontrolesysteem. Bijvoorbeeld Subversion.
   * Een systeem voor foutopsporing. Bijvoorbeeld Jira.
   * Een centraal systeem voor afhankelijkheidsbeheer. Bijvoorbeeld Apache Archiva.
   * En een systeem voor automatisering. Bijvoorbeeld Apache Continuum.

  Met deze setup kunt u uw toepassing (inhoud, code, configuratie) volledig integreren in elke ontwikkelomgeving en elk ontwikkelingsproces. De koppeling tussen de verschillende elementen is de representatie van het bestandssysteem van de gegevensopslagruimte via FileVault, aangezien alle eerder genoemde ontwikkelingsprogramma&#39;s met bestanden kunnen werken.

## Uitbreidingen voor geïntegreerde ontwikkelomgevingen {#extensions-for-integrated-development-environments}

Adobe heeft de volgende extensies uitgebracht:

* [AEM Eclipse-extensie](/help/sites-developing/aem-eclipse.md)
* [AEM Brackets-extensie](/help/sites-developing/aem-brackets.md)

### Overige gereedschappen {#other-tools}

AEM wordt geleverd met andere instrumenten die de ontwikkeling bevorderen:

* [Dialoogeditor](/help/sites-developing/dialog-editor.md)
* [Woordenboeken beheren met Vertaler](/help/sites-developing/i18n-translator.md)
* [Pakketten beheren met Maven](/help/sites-developing/vlt-mavenplugin.md)
* [AEM-projecten ontwikkelen met Eclipse](/help/sites-developing/howto-projects-eclipse.md)
* [AEM-projecten bouwen met Apache Maven](/help/sites-developing/ht-projects-maven.md)
* [Hoe te om AEM Projecten te ontwikkelen gebruikend IntelliJ IDEA](/help/sites-developing/ht-intellij.md)
* [Het gereedschap VLT gebruiken](/help/sites-developing/ht-vlttool.md)
* [Het gereedschap Proxyserver gebruiken](/help/sites-developing/ht-proxy-server.md)
* [AEM-moderniseringstools](/help/sites-developing/modernization-tools.md)
* [AEM Repo](/help/sites-developing/aem-repo-tool.md)

Instrumenten die het opzetten van nieuwe projecten vergemakkelijken:

* [&#x200B; Archetype van het Project van AEM &#x200B;](https://github.com/adobe/aem-project-archetype)
* [&#x200B; de Malplaatjes van AEM Lazybones &#x200B;](https://github.com/Adobe-Consulting-Services/lazybones-aem-templates)

>[!NOTE]
>
>De volgende zelfstudie kan van belang zijn voor het starten van een nieuw AEM-project:
>[Aan de slag met AEM Sites Deel 1 - de Opstelling van het Project &#x200B;](https://helpx.adobe.com/experience-manager/kt/sites/using/getting-started-wknd-tutorial-develop/part1.html)
