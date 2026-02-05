---
title: Integratie van de Create Oplossing van de Correspondentie met uw Portaal van de Douane
description: Leer hoe u het maken van correspondentie-UI kunt integreren met uw aangepaste portal
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
docset: aem65
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 496b125b-b091-4843-ba9f-2479dbeba07b
source-git-commit: 16f57ae1663f035d1dc39005d37426c7a0d8dc16
workflow-type: tm+mt
source-wordcount: '403'
ht-degree: 0%

---

# Integratie van de `Create Correspondence` -oplossing met uw aangepaste portal{#integrating-create-correspondence-ui-with-your-custom-portal}

## Overzicht {#overview}

In dit artikel wordt beschreven hoe u de `Create Correspondence` -oplossing kunt integreren met uw omgeving.

## Oproepen op basis van URL {#url-based-invocation}

U kunt de toepassing `Create Correspondence` aanroepen vanuit een aangepast portaal door de URL voor te bereiden met de volgende aanvraagparameters:

* de id voor de lettersjabloon (met de parameter cmLetterId).

* de URL naar de XML-gegevens die van de gewenste gegevensbron worden opgehaald (met de parameter cmDataUrl).

Het aangepaste portaal bereidt bijvoorbeeld de URL voor als\
`https://'[server]:[port]'/[contextPath]/aem/forms/createcorrespondence.html?random=[timestamp]&cmLetterId=[letter identifier]&cmDataUrl=[data URL]` , wat de href zou kunnen zijn van een koppeling op het portaal.

>[!NOTE]
>
>Op deze manier aanroepen is niet veilig omdat de noodzakelijke parameters als GET-verzoek worden doorgegeven, door dezelfde (duidelijk zichtbare) waarde in de URL aan te geven.

>[!NOTE]
>
>Voordat u de `Create Correspondence` -toepassing aanroept, slaat u de gegevens op en uploadt u deze om de `Create Correspondence` -gebruikersinterface op de opgegeven dataURL aan te roepen. Dit proces kan of van het douaneportaal zelf of door een ander achtereindeproces worden gedaan.

## Inline op gegevens gebaseerde aanroeping {#inline-data-based-invocation}

Een andere, veiliger, manier om de `Create Correspondence` toepassing te roepen moet naar URL in https://&#39; [ server ] gaan:[ haven ]&#39;/[ contextPath ] /aem/forms/createcorrespondence.html. Voer deze URL uit terwijl u de parameters en gegevens verzendt om de `Create Correspondence` -toepassing als een POST-aanvraag aan te roepen en deze voor de eindgebruiker verbergt. Deze workflow betekent ook dat u nu de XML-gegevens voor de `Create Correspondence` -toepassing inline kunt doorgeven (als onderdeel van dezelfde aanvraag, met de parameter `cmData` ). Deze workflow was niet mogelijk of ideaal in de vorige aanpak.

### Parameters voor het opgeven van de letter {#parameters-for-specifying-letter}

| **Naam** | **Type** | **Beschrijving** |
| --- | --- | --- |
| cmLetterInstanceId | String | De id voor de letter-instantie. |
| cmLetterId | String | De naam van de Letter-sjabloon. |

De volgorde van parameters in de tabel geeft de voorkeur aan parameters die worden gebruikt voor het laden van de letter.

### Parameters voor het opgeven van de XML-gegevensbron {#parameters-for-specifying-the-xml-data-source}

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Beschrijving</strong></td> 
  </tr>
  <tr>
   <td>cmDataUrl <br /> </td> 
   <td>URL</td> 
   <td>De gegevens van XML van een brondossier gebruikend basisprotocollen, zoals cq, ftp, http, of dossier.<br /> </td> 
  </tr>
  <tr>
   <td>cmLetterInstanceId</td> 
   <td>String</td> 
   <td>XML-gegevens gebruiken die beschikbaar zijn in letter-instantie.</td> 
  </tr>
  <tr>
   <td>cmUseTestData</td> 
   <td>Boolean</td> 
   <td>De testgegevens in een gegevenswoordenboek opnieuw gebruiken.</td> 
  </tr>
 </tbody>
</table>

De volgorde van parameters in de tabel geeft de voorkeur aan parameters die worden gebruikt voor het laden van de XML-gegevens.

### Andere parameters {#other-parameters}

<table>
 <tbody>
  <tr>
   <td><strong>Naam</strong></td> 
   <td><strong>Type</strong></td> 
   <td><strong>Beschrijving</strong></td> 
  </tr>
  <tr>
   <td>cmPreview<br /> </td> 
   <td>Boolean</td> 
   <td>True to open the letter in preview mode <br /> </td> 
  </tr>
  <tr>
   <td>Willekeurig</td> 
   <td>Tijdstempel</td> 
   <td>Oplossen van problemen met het in cache plaatsen van de browser.</td> 
  </tr>
 </tbody>
</table>

Als u het http- of cq-protocol gebruikt voor `cmDataURL` , moet de URL van `http/cq` anoniem toegankelijk zijn.
