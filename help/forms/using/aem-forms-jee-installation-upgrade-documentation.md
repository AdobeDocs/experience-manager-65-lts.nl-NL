---
title: Workflow voor installatie en upgrade voor AEM Forms op JEE
description: Workflow voor installatie en upgrade voor AEM Forms 6.5 LTS op JEE (JBoss), met een geconsolideerde lijst van relevante PDF's en het doel ervan.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: installing
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: AEM Forms on JEE,AEM Forms Upgrade
exl-id: 6d8c0e24-7f08-4e66-bb12-2cf1cfe1d5d3
source-git-commit: fb9f6ef794da7f3b242e9e81a6c2505692c16cd8
workflow-type: tm+mt
source-wordcount: '481'
ht-degree: 1%

---


# Workflow voor installatie en upgrade voor AEM Forms op JEE {#aem-forms-jee-installation-upgrade-documentation}

## Van toepassing op {#applies-to}

Deze documentatie is op **AEM 6.5 LTS Forms** van toepassing.

Gebruik de volgende workflow en tabellen om de juiste hulplijnen voor uw scenario te kiezen. Sommige documenten worden gepubliceerd als PDF&#39;s; aanvullende documenten kunnen in de loop der tijd worden toegevoegd zodra ze beschikbaar komen.

## Workflow voor installatie en upgrade {#installation-upgrade-workflow}

1. Het overzicht [ Ondersteunde platforms voor AEM Forms op JEE ](/help/forms/using/aem-forms-jee-supported-platforms.md) en verzekert uw systeem de vereiste software/hardwarecombinaties ontmoet.
2. Beslis of u a **verse installatie** of een **verbetering** uitvoert.
3. Voor het gekozen pad volgt u de hieronder beschreven volgorde (voor sommige scenario&#39;s zijn meer dan één hulplijn vereist).

## Pre-installatie en pre-upgrade stappen {#start-here}

| Hulplijn | Beschrijving |
| --- | --- |
| [ Ondersteunde platforms voor AEM Forms op JEE ](/help/forms/using/aem-forms-jee-supported-platforms.md) | Geeft ondersteunde software- en hardwarecombinaties voor AEM Forms op JEE weer. Gebruik dit om vereisten te bevestigen alvorens u met een installatie of een verbetering begint. |
| [ Architectuur en plaatsingstopologieën voor AEM Forms ](/help/forms/using/aem-forms-architecture-deployment.md) | Verklaart geadviseerde architecturen en plaatsingstopologieën zodat kunt u een benadering kiezen die uw milieu (bijvoorbeeld, enige server versus cluster) aanpast. |
| [ Kiekend een persistentietype voor een installatie van AEM Forms ](/help/forms/using/choosing-persistence-type-for-aem-forms.md) | Helpt u een aangewezen persistentietype voor uw installatietopologie selecteren alvorens u begint. |

## Hoe installeer ik Adobe Experience Manager Forms (AEM Forms) op JEE op JBoss? {#installing-aem-forms-jee-jboss}

### Turnkey {#install-jee-jboss-turnkey}

| Hulplijn | Beschrijving |
| --- | --- |
| [ het Installeren van en het Opstellen van AEM Forms 6.5 LTS op JEE Gebruikend Turnkey JBoss (PDF) ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-turnkey.pdf) | Gebruik voor a **verse turnkey installatie** op JBoss. Dit document bevat instructies voor het installeren en implementeren van AEM Forms op JEE met behulp van de JBoss-distributie. |

### Eén server (niet-turnkey) {#install-jee-jboss-single-server}

| Hulplijn | Beschrijving |
| --- | --- |
| [ voorbereidend om AEM Forms (Enige Server) (PDF) te installeren ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-install-single-server.pdf) | Het gebruik **vóór** a **verse enig-server (niet-runtime) installatie**. Dit document maakt een lijst van eerste vereisten en milieu voorbereidingsstappen voor het installeren van AEM Forms op JEE in een enig-servertopologie. |
| [ het Installeren van en het Opstellen van AEM Forms op JEE voor JBoss (PDF) ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/install-jboss.pdf) | Gebruik voor de **geleidelijke installatie en plaatsing** van AEM Forms op JEE op JBoss (**niet-turnkey**). Voor enig-serverinstallaties, volg deze gids **na** de voltooiing *voorbereidend om AEM Forms (Enige Server) te installeren*. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **fresh cluster installation**. Describes prerequisites and environment preparation steps for installing AEM Forms on JEE in a server cluster topology. *(Link will be added once the PDF is available.)* |
| [Configuring AEM Forms on JEE on JBoss Cluster (PDF)](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/cluster-jboss.pdf) | Use when setting up and configuring a **JBoss cluster topology** for AEM Forms on JEE. |
-->

## Hoe kan ik Adobe Experience Manager Forms (AEM Forms) upgraden op JEE op JBoss? {#upgrading-aem-forms-jee-jboss}

### Turnkey {#upgrade-jee-jboss-turnkey}

| Hulplijn | Beschrijving |
| --- | --- |
| [ Bevorderend aan AEM Forms 6.5 LTS op JEE voor JBoss Turnkey (PDF) ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-turnkey.pdf) | Gebruik voor a **runtime verbetering**. Dit document bevat instructies voor het upgraden van een bestaande AEM Forms bij JEE JBoss-installatie. |

### Eén server {#upgrade-jee-jboss-single-server}

| Hulplijn | Beschrijving |
| --- | --- |
| [ voorbereidend om AEM Forms (PDF) te bevorderen ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/prepare-upgrade.pdf) | Gebruik **vóór** a **enig-serververbetering**. Beschrijft hoe te om het milieu voor te bereiden alvorens aan AEM 6.5 LTS Forms te bevorderen. Dit is van toepassing op omgevingen waarin AEM Forms op JEE wordt uitgevoerd in de installatiemodus Eén server. |
| [ Bevorderend aan AEM Forms op JEE voor JBoss (PDF) ](https://helpx.adobe.com/content/dam/help/en/experience-manager/65LTS/forms/upgrade-jboss.pdf) | Gebruik voor de **geleidelijke verbeteringsprocedure** op JBoss op a **enig-server** installatiemodus. Volg deze gids **na** voltooiing *voorbereidend om AEM Forms* te bevorderen. |

<!--
| Preparing to Install AEM Forms (Server Cluster) (PDF) (**TBD**) | Use **before** a **cluster upgrade**. Describes how to prepare the environment for a server cluster before upgrading to AEM 6.5 LTS Forms. It applies to environments running AEM Forms on JEE in a server cluster installation mode. *(Link will be added once the PDF is available.)* |
| Upgrading to AEM Forms on JEE for JBoss (Cluster) (PDF) (**TBD**) | Use for the **step-by-step upgrade procedure** on JBoss in a **clustered** installation mode. Follow this guide **after** completing *Preparing to Install AEM Forms (Server Cluster)*. *(Link will be added once the PDF is available.)* | -->

