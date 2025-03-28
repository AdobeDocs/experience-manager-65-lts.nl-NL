---
title: Analyse aanvragen
description: Het manuscript van de verzoekanalyse wordt gemaakt om de analyse van de access.log dossiers te verlichten die een leesbaar rapport voor recentere verwerking produceren
contentOwner: Guillaume Carlino
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: testing
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing
role: Developer
exl-id: 9fe575ad-1e8d-460f-a933-ddc2e927a6e8
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '171'
ht-degree: 0%

---

# Analyse aanvragen{#request-analysis-script}

## Downloaden {#download}

Dit script is gemaakt om de analyse te vereenvoudigen van de `access.log` -bestanden die een leesbaar rapport produceren voor latere verwerking.

[Bestand ophalen](assets/analyse-access.sh)

## Beschrijving {#description}

Dit script is gemaakt om de analyse te vereenvoudigen van de `access.log` -bestanden die een leesbaar rapport produceren voor latere verwerking.

Het produceert het algemene verzoekaantal, GET versus POST, Verzoek verdeling over tijd en meer.

De uitvoer wordt uitgevoerd in de syntaxis Markdown. Het is daarom gemakkelijker om de uitvoer te converteren naar PDF met gereedschappen zoals een pandoc-bestand of de uitvoer weer te geven in een browser met plug-ins zoals een Markeringen-viewer.

Een aangepast pad op de opdrachtregel kan worden geanalyseerd.

Maak kennis met de opmerking in het bestand die u vertelt hoe u de opmerking moet uitvoeren:

Analyseer CQ `access.log` verschillende informatie en produceer een output van de Prijsverlaging op `stdout`.

## Gebruik {#usage}

`./analyse-access.sh access.log.2013-&ast;`

u kunt aanvullende aangepaste paden opgeven die u wilt analyseren op de opdrachtregel

`/analyse-access.sh access.log.2013-&ast; /my/custom/path/1 /my/custom/path/2`

u kunt de output bewaren door eenvoudige pijpleiding

`./analyse-access.sh access.log.2013-&ast; | tee yr2013.md`
