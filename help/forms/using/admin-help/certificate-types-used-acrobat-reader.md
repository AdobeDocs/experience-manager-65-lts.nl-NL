---
title: Certificaattypen die worden gebruikt door Acrobat Reader DC-extensies
description: Leer meer over de certificaattypen die worden gebruikt door Acrobat Reader DC-extensies.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: ca919915-c37b-4793-b5e2-21a464c5dcdf
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '944'
ht-degree: 0%

---

# Certificaattypen die worden gebruikt door Acrobat Reader DC-extensies {#certificate-types-used-by-acrobat-reader-dc-extensions}

De Certificate Viewer biedt de volgende informatie over het certificaat:

* Naam van certificaat &quot;vriendelijk&quot;
* Certificaatprofielen
* Geldigheidsperiode
* Gebruiksrechten voor Acrobat Reader DC-extensies

## Naam van certificaat &quot;vriendelijk&quot; {#certificate-friendly-name}

De &quot;vriendelijke&quot; naam van een Acrobat Reader DC-extensiecertificaat is een tekenreeks die de eigenschappen van het certificaat beschrijft, zoals in het volgende voorbeeld:

2D-streepjescode volledige productie V6.1 P8 0002054

De tekenreeks bevat de volgende elementen:

**Type van Certificaat:** beschrijft de AEM vormmodules die het certificaat activeert, en het niveau van activering, zoals ARE 2D Hoogtepunt Streepjescode. Zie de kolom Type in de tabel in de sectie Certificaatprofielen voor een lijst met beschikbare certificaattypen.

**Type van Plaatsing:** wijst op het voorgenomen gebruik van het certificaat, zoals Productie. De waarde kan Evaluatie of Productie zijn. Voor een lijst van plaatsingstypes verbonden aan elk certificaattype, zie de kolom van het type van Plaatsing in de lijst in de sectie van de Profielen van het Certificaat.

**versie van de rechten van het Gebruik:** beschrijft de versie van het algoritme van gebruiksrechten dat het certificaat kan worden gebruikt, zoals V6.1. Deze versie betekent niet de versie van Acrobat of Acrobat Reader DC-extensies.

**code van het Profiel:** de profielcode is een korte beschrijving van volledige certificaateigenschappen, zoals voorbeeld, P8. Zie de kolom Profielcode in de tabel in de sectie Certificaatprofielen voor een lijst met profielcodes die aan elk bestandstype zijn gekoppeld.

**Serie aantal:** een serienummer wordt toegewezen aan elk certificaat dat door Adobe, zoals 0002054 wordt uitgegeven. Adobe Enterprise Support of een Adobe Enterprise-accountvertegenwoordiger kan dit serienummer gebruiken om het certificaat te traceren naar een specifieke productorder of naar een OEM-relatie.

## Certificaatprofielen {#certificate-profiles}

In de volgende tabel worden de certificaatprofielen weergegeven die u kunt tegenkomen bij het analyseren van certificaten voor Acrobat Reader DC-extensies.

<table>
 <thead>
  <tr>
   <th><p>Profielcode</p></th>
   <th><p>Type</p></th>
   <th><p>Geldigheidsperiode</p></th>
   <th><p>Type implementatie</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>P1</p></td>
   <td><p>SAP-productie</p></td>
   <td><p>Max</p></td>
   <td><p>Productie</p></td>
  </tr>
  <tr>
   <td><p>P2</p></td>
   <td><p>Interne SAP-test</p></td>
   <td><p>2 jaar</p></td>
   <td><p>Evaluatie en test</p></td>
  </tr>
  <tr>
   <td><p>P3</p></td>
   <td><p>Acrobat Reader DC-extensies, productie</p></td>
   <td><p>Max</p></td>
   <td><p>Productie</p></td>
  </tr>
  <tr>
   <td><p>P4</p></td>
   <td><p>Acrobat Reader DC-extensies, Intern Adobe-gebruik</p></td>
   <td><p>2 jaar</p></td>
   <td><p>Productie</p></td>
  </tr>
  <tr>
   <td><p>P5</p></td>
   <td><p>Acrobat Reader DC-extensies, partnerintegratie</p></td>
   <td><p>2 jaar</p></td>
   <td><p>Evaluatie en test</p></td>
  </tr>
  <tr>
   <td><p>P6</p></td>
   <td><p>Acrobat Reader DC-extensies, evaluatie</p></td>
   <td><p>60 dagen</p></td>
   <td><p>Evaluatie</p></td>
  </tr>
  <tr>
   <td><p>P8</p></td>
   <td><p>Forms, Productie</p></td>
   <td><p>Max</p></td>
   <td><p>Productie</p></td>
  </tr>
  <tr>
   <td><p>P9</p></td>
   <td><p>Adobe Acrobat 7.x, Productie</p></td>
   <td><p>Max</p></td>
   <td><p>Productie</p></td>
  </tr>
  <tr>
   <td><p>I10</p></td>
   <td><p>Forms; kan door OEM's worden gebruikt</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
  <tr>
   <td><p>I11</p></td>
   <td><p>Forms; kan door OEM's worden gebruikt</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
  <tr>
   <td><p>I12</p></td>
   <td><p>Alleen handtekening; mag door OEM's worden gebruikt</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
  <tr>
   <td><p>I13</p></td>
   <td><p>Offline opmerkingen alleen; kan door OEM's worden gebruikt</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
  <tr>
   <td><p>I14</p></td>
   <td><p>Alleen opmerkingen; kan door OEM's worden gebruikt</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
  <tr>
   <td><p>I15</p></td>
   <td><p>Volledige machtigingen; kunnen worden gebruikt door OEM's</p></td>
   <td><p>Max</p></td>
   <td><p>Productie en evaluatie</p></td>
  </tr>
 </tbody>
</table>

## Geldigheidsperiode {#validity-period}

De certificaten van de evaluatie worden uitgegeven aan klanten en ontwikkelaars zodat zij steekproeftoepassingen voor producten kunnen evalueren en ontwikkelen. De geldigheidsduur van deze certificaten ligt tussen 60 en 90 dagen. Zij verstrijken aan het einde van de tweede maand volgende op de uitgiftegegevens.

De certificaten van de Integratie van de partner worden uitgegeven aan de bedrijfspartners van Adobe om softwareontwikkeling, integratie, prototyping, en demonstratie te steunen. Deze certificaten zijn twee jaar geldig vanaf de datum van afgifte.

Adobe Internal Use-certificaten worden in Adobe gebruikt ter ondersteuning van softwareontwikkeling, -integratie, -prototypen en -demonstratie. Deze certificaten zijn twee jaar geldig vanaf de datum van afgifte.

Productiecertificaten worden uitgegeven aan klanten die Acrobat Reader DC-extensies hebben aangeschaft. Deze certificaten zijn geldig voor de maximumperiode die door het certificaatgezag (CA) wordt toegelaten, die als *Max* in de lijst van Profielen van het Certificaat wordt getoond.

## Gebruiksrechten voor Acrobat Reader DC-extensies {#acrobat-reader-dc-extensions-usage-rights}

Wanneer u het certificaat voor Acrobat Reader DC-extensies in de certificaatviewer bekijkt, kunt u de optie met gebruiksrechten selecteren op het tabblad Details (indien geconfigureerd) om een gedetailleerde lijst weer te geven van de gebruiksrechten van Adobe Reader die het certificaat kan inschakelen. De gebruiksrechten die op een bepaald document zijn ingeschakeld, kunnen een subset zijn van de gebruiksrechten die door het certificaat worden ingeschakeld.

Als online opmerkingen vereist zijn in een omgeving zonder samenwerkingsverband, neemt u contact op met Adobe Support voor meer informatie. Het bezit van de Wijze past het plaatsingstype aan en is of *productie* of *evaluatie*.

De toegestane gebruiksrechten voor Acrobat Reader DC-extensies bestaan uit een of meer specifieke elementen. Deze elementen worden in verschillende combinaties gebruikt om verschillende productfuncties met een licentie te verkrijgen.

<table>
 <thead>
  <tr>
   <th><p>Gebruiksrechten-element</p></th>
   <th><p>Mogelijkheid ingeschakeld in Adobe Reader bij weergave van een PDF-document waarvoor rechten zijn ingeschakeld</p></th>
  </tr>
 </thead>
 <tbody>
  <tr>
   <td><p>FormFillInAndSave</p></td>
   <td><p>Formuliervelden invullen en bestanden lokaal opslaan.</p></td>
  </tr>
  <tr>
   <td><p>FormImportExport</p></td>
   <td><p>U kunt formuliergegevens importeren en exporteren als FDF-, XFDF-, XML- en XDP-bestanden.</p></td>
  </tr>
  <tr>
   <td><p>FormAddDelete</p></td>
   <td><p>Velden en veldeigenschappen toevoegen, wijzigen of verwijderen op het PDF-formulier.</p></td>
  </tr>
  <tr>
   <td><p>SubmitStandalone</p></td>
   <td><p>Gegevens verzenden via e-mail of offline naar een server wanneer deze niet worden uitgevoerd in een browsersessie.</p></td>
  </tr>
  <tr>
   <td><p>SpawnTemplate</p></td>
   <td><p>Pagina's maken van sjabloonpagina's in hetzelfde PDF-formulier.</p></td>
  </tr>
  <tr>
   <td><p>Ondertekenen</p></td>
   <td><p>PDF-documenten digitaal ondertekenen en opslaan, en digitale handtekeningen wissen.</p></td>
  </tr>
  <tr>
   <td><p>AnnotModify</p></td>
   <td><p>Documentannotaties zoals opmerkingen maken en wijzigen.</p></td>
  </tr>
  <tr>
   <td><p>AnnotImportExport</p></td>
   <td><p>Sla notities, zoals opmerkingen, op in een afzonderlijk gegevensbestand en laad opmerkingen uit een bestand.</p></td>
  </tr>
  <tr>
   <td><p>BarcodePlaintext</p></td>
   <td><p>Een document afdrukken met formuliergegevens die in een niet-gecodeerd formulier zijn gecodeerd en waarvoor geen geautoriseerde serversoftware nodig is om te decoderen.</p></td>
  </tr>
  <tr>
   <td><p>AnnotOnline</p></td>
   <td><p>Annotaties zoals opmerkingen uploaden naar en downloaden van een online documentrevisie en opmerkingenserver.</p></td>
  </tr>
  <tr>
   <td><p>FormOnline</p></td>
   <td><p>Maak verbinding met webservices of databases die zijn gedefinieerd in een PDF-formulier.</p></td>
  </tr>
  <tr>
   <td><p>EFModif</p></td>
   <td><p>Ingesloten bestandsobjecten die aan het PDF-document zijn gekoppeld, wijzigen.</p></td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Acrobat Reader DC-extensierechten kunnen alleen in licentie worden gegeven door Adobe in bepaalde combinaties die samenwerken. Het is niet mogelijk om deze mogelijkheden onafhankelijk te verlenen. Neem voor informatie over de beschikbare combinaties van gebruiksrechten contact op met een accountvertegenwoordiger van AEM-formulieren.
