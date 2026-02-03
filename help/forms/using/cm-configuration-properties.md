---
title: Eigenschappen van Correspondentenbeheer
description: Dit onderwerp verklaart hoe u de Composer van Activa met oplossing-specifieke configuraties kunt uitgeven.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: correspondence-management
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 23be6248-1013-488e-91e6-ac1f6fb7da50
source-git-commit: c714e51f0c0368988ce552969747ab5fce5c186f
workflow-type: tm+mt
source-wordcount: '807'
ht-degree: 0%

---

# Eigenschappen van Correspondentenbeheer {#correspondence-management-configuration-properties}

Om deze eigenschappen te vormen, open volgende URL in browser: `https://<server>:<port>/<contextPath>/system/console/configMgr` en selecteer **Configuraties van het Beheer van de Correspondentie**.

Correspondentiebeheer heeft de volgende configuratie-eigenschappen:

<table>
 <tbody>
  <tr>
   <th><p><strong>Eigenschap</strong></p> </th>
   <th><p><strong>Beschrijving</strong></p> </th>
   <th><p><strong>Standaard</strong></p> </th>
   <th><p><strong>Acceptabele waarden</strong></p> </th>
  </tr>
  <tr>
   <td><p>Inspringing</p> </td>
   <td>Inspringing op modules<p> </p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td>Minimumbreedte aantal</td>
   <td>Minimumbreedte die moet worden toegepast op het veld Opsommingsteken/nummer wanneer u genummerde lijsten gebruikt, met uitzondering van Romeinse nummers.</td>
   <td>8,0 mm</td>
   <td>Willekeurig getal</td>
  </tr>
  <tr>
   <td><p>Roman Numbers Minimum Width</p> </td>
   <td><p>Minimumbreedte die moet worden toegepast op het veld Opsommingsteken/Nummer bij gebruik van Romeinse getallen.</p> </td>
   <td><p>12,7 mm</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td>Type vertoning</td>
   <td>Het type uitvoering dat de toepassing gebruikt om de lettervoorvertoning weer te geven. </td>
   <td>HTML Rendition</td>
   <td>HTML Rendition / PDF Rendition</td>
  </tr>
  <tr>
   <td><p>CCR PDF-markering inschakelen</p> </td>
   <td><p>Hiermee wordt markering op PDF in de toepassing ingeschakeld.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Type markeerteken doel</p> </td>
   <td><p>Doel markeertype in de toepassing.</p> </td>
   <td><p>border</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Doelmarkeringskleur</p> </td>
   <td><p>Markeringskleur voor doelframes in de toepassing.</p> </td>
   <td><p>90;155;245</p> </td>
   <td><p>Elke RGB-kleur in formaat R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Type markering van inhoud</p> </td>
   <td><p>Inhoud markeert tekst in de toepassing.</p> </td>
   <td><p>Vullen</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Markeerkleur inhoud</p> </td>
   <td><p>Inhoud markeert kleur in de toepassing.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Elke RGB-kleur in formaat R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Type markering veld</p> </td>
   <td><p>Type veldmarkering in de toepassing.</p> </td>
   <td><p>vullen</p> </td>
   <td><p>border / fill / none</p> </td>
  </tr>
  <tr>
   <td><p>Markeerkleur veld</p> </td>
   <td><p>Markeringskleur van velden in de toepassing.</p> </td>
   <td><p>210;225;245</p> </td>
   <td><p>Elke RGB-kleur in formaat R;G;B</p> </td>
  </tr>
  <tr>
   <td><p>Time-out toepassing</p> </td>
   <td><p>Toepassingstijd in seconden.</p> </td>
   <td><p>1200</p> </td>
   <td><p>Willekeurig getal</p> </td>
  </tr>
  <tr>
   <td><p>Naam PDF-documentparameter</p> </td>
   <td><p>Parameternaam voor PDF-document na verwerking.</p> </td>
   <td><p>inPDFDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam XML-gegevensparameter</p> </td>
   <td><p>Parameternaam voor XML-document (gegevens) na verwerking.</p> </td>
   <td><p>inXMLDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam van XDP-documentparameter</p> </td>
   <td><p>Parameternaam voor XDP-document dat naar het postproces wordt verzonden.</p> </td>
   <td><p>inXDPDoc</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>Naam URL-parameter omleiden</p> </td>
   <td><p>Parameternaam voor de omleidings-URL die vanuit het postproces wordt verzonden. Deze waarde kan elke naam van een tekenreeksvariabele zijn.</p> </td>
   <td><p>redirectURL</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>PDF-verzendtype</p> </td>
   <td><p>PDF Submit Type (type PDF dat wordt gegenereerd bij verzending vanuit de toepassing).</p> </td>
   <td><p>nonInteractive</p> </td>
   <td><p>interactief/niet-interactief</p> </td>
  </tr>
  <tr>
   <td><p>Gegevenswoordenboekinstantie optimaliseren</p> </td>
   <td><p>Schakelt geoptimaliseerde overdracht van gegevenswoordenboekinstantie b/w-server en -client in.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Inconsistentie automatisch corrigeren </p> </td>
   <td><p>Wanneer toegelaten, behandelt het automatisch de mogelijke inconsistenties in de Taken van de Brief.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Gevormde gegevensindelingen gebruiken</p> </td>
   <td><p>Controls whether to Use Configured Data Edit Formats and Data Display Format.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Indelingen voor gegevensweergave</p> </td>
   <td><p>Hiermee geeft u een landspecifieke weergave-indeling voor gegevens op.</p> </td>
   <td><p>locale=nl_NL; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=truelocale=de_DE; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator=.; numberUseGroupSeparator=truelocale=fr_FR; dateFormat=dd-MM-yyyy; numberDecimalSeparator=,; numberGroupSeparator= ; numberUseGroupSeparator=truelocale=ja_JP; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td><p>—</p> </td>
  </tr>
  <tr>
   <td><p>Gegevensbewerkingsindeling</p> </td>
   <td><p>Opmaak voor gegevens bewerken. Wordt gebruikt wanneer gegevens als tekenreeks worden geschreven of gegevens uit tekenreeks worden geparseerd.</p> </td>
   <td><p>locale=nl_NL; dateFormat=dd-MM-yyyy; numberDecimalSeparator=.; numberGroupSeparator=,; numberUseGroupSeparator=true</p> </td>
   <td>—<p> </p> </td>
  </tr>
  <tr>
   <td><p>Lettervarianten beheren bij publicatie</p> </td>
   <td><p>De letterfunctionaliteit inschakelen/uitschakelen (alleen van toepassing op de publicatieserver).</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit inschakelen</p> </td>
   <td><p>De auditfunctie in-/uitschakelen. Indien onwaar, worden de controlelogboeken voor alle acties onbruikbaar gemaakt.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Controle lezen inschakelen</p> </td>
   <td><p>De auditfunctie voor het lezen van elementen in-/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit maken</p> </td>
   <td><p>De auditfunctionaliteit inschakelen/uitschakelen voor het maken van elementen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Update Audit inschakelen</p> </td>
   <td><p>De auditfunctie voor het bijwerken van elementen in-/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Audit herstellen inschakelen</p> </td>
   <td><p>De auditfunctie voor het terugzetten van elementen in-/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Publicatie-controle inschakelen</p> </td>
   <td><p>De auditfunctie voor het publiceren van elementen in-/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>SaveAsDraft-controle inschakelen</p> </td>
   <td><p>Schakel de auditfunctie voor het opslaan van letterconcepten in of uit.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Controle verzenden inschakelen</p> </td>
   <td><p>De auditfunctie inschakelen/uitschakelen voor verzenden van brief.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>E-mailcontrole inschakelen</p> </td>
   <td><p>De auditfunctie voor e-mailbrieven inschakelen/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Afdrukcontrole inschakelen</p> </td>
   <td><p>De auditfunctie voor het afdrukken van letters in-/uitschakelen.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Aangepaste leveringscontrole inschakelen</p> </td>
   <td><p>Schakel de auditfunctie voor aangepaste levering van letters in of uit.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Naam van parameter voor bijlagen</p> </td>
   <td><p>Parameternaam voor bijlagen die naar het postproces worden verzonden.</p> </td>
   <td><p>inBijlageDocs</p> </td>
   <td><p>Willekeurige naam van tekenreeksvariabele</p> </td>
  </tr>
  <tr>
   <td><p>CM-gebruikersbasis</p> </td>
   <td><p>URL van de map met alle Correspondence Management-gebruikerselementen.</p> </td>
   <td><p>—</p> </td>
   <td><p>Geldige maplocatie</p> </td>
  </tr>
  <tr>
   <td><p>Grootte lettercache</p> </td>
   <td><p>Geef het maximumaantal letters op dat in de cache moet worden opgeslagen.</p> <p>Als u deze waarde wijzigt, wordt de cache van <code>in-memory</code> opgeschoond.</p> </td>
   <td><p>100</p> </td>
   <td><p>Willekeurige numerieke waarde</p> </td>
  </tr>
  <tr>
   <td><p>Lettercache inschakelen</p> </td>
   <td><p>De lettercache in-/uitschakelen.</p> <p>Als u deze waarde wijzigt, wordt de cache van <code>in-memory </code> opgeschoond.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Volgorde gegevenselementen</p> </td>
   <td><p>Houdt gegevenselementen die in de interface zoals volgens hun opeenvolging in Brief opdracht geven tot.</p> </td>
   <td><p>true</p> </td>
   <td><p>true / false</p> </td>
  </tr>
  <tr>
   <td><p>Ondersteuning voor opnieuw laden</p> </td>
   <td><p>Ondersteuning voor opnieuw laden inschakelen/uitschakelen in letters die op de server worden weergegeven.</p> <p>Als u deze optie uitschakelt, worden de prestaties van het renderen van letters verbeterd.</p> </td>
   <td><p>false</p> </td>
   <td><p>true / false</p> <p> </p> </td>
  </tr>
  <tr>
   <td>Temp-map</td>
   <td>Locatie van de tijdelijke map.</td>
   <td>acm.tpmFolder</td>
   <td> </td>
  </tr>
  <tr>
   <td>Extern opslaan</td>
   <td>Hiermee worden de Letter-instanties opgeslagen op de opgegeven auteur.</td>
   <td> </td>
   <td> </td>
  </tr>
  <tr>
   <td>Compatibiliteitsopties</td>
   <td>Compatibiliteitsopties van de indeling configname: configurewaarde gescheiden door komma.</td>
   <td>acm.compatibilityOptions</td>
   <td> </td>
  </tr>
  <tr>
   <td><p>Foutopsporingsdirectory </p> <p> </p> </td>
   <td>Locatie bestandssysteemmap voor foutopsporing. Als de map niet <code>exists</code> is, worden er geen foutopsporingsdumps gegenereerd.</td>
   <td>acm.debugDirectory</td>
   <td> </td>
  </tr>
 </tbody>
</table>
