---
title: Toegang tot documenten die met een beleid zijn beveiligd beheren
description: Zie hoe u de toegang tot documenten die met een beleid zijn beveiligd, kunt weergeven, beheren en beheren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 553c0a95-26e9-4d2c-b53d-846861c6a1d7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '2167'
ht-degree: 0%

---

# Toegang tot documenten die met een beleid zijn beveiligd beheren {#controlling-access-to-policy-protected-documents}

U kunt de manier controleren waarin de ontvangers uw beleid-beschermde documenten gebruiken ongeacht hoe wijd u hen verspreidt.

Met behulp van de pagina Documenten kunt u de volgende taken uitvoeren:

* Zoek naar en bekijk de details van beleid-beschermde documenten. U kunt informatie over de documentnaam, de uitgeversnaam, de beleidsnaam, en de datum zien het beleid werd toegepast. Als het beleid dat een document beschermde wordt geschrapt, kunt u schrapte beleidsidentiteitskaart onder de beleidsnaam ook zien. Gebruikers kunnen hun eigen documenten die met een beleid zijn beveiligd, weergeven en beheren. Beheerders kunnen alle documenten die met een beleid zijn beveiligd, weergeven en beheren.
* Wijzig de details van het beleid dat op een document wordt toegepast. De gebruikers kunnen hun eigen beleid uitgeven, de beheerders kunnen gedeeld en persoonlijk beleid uitgeven, en de coördinatoren van de beleidsreeks kunnen gedeeld beleid in de beleidsreeksen uitgeven zij toestemmingen voor hebben. U hebt rechtstreeks vanuit de pagina Documentdetails toegang tot het beleid dat aan een document is gekoppeld.
* De toegang tot een document dat met een beleid is beveiligd, intrekken en opnieuw instellen. Beheerders kunnen de toegang tot elk document intrekken en opnieuw instellen. Coördinatoren van beleidssets (die gemachtigd zijn om documenten te beheren) kunnen de toegang tot documenten die met een beleid zijn beveiligd en die gedeeld beleid uit hun beleidssets gebruiken, intrekken en herstellen. Gebruikers kunnen de toegang tot documenten die met een beleid zijn beveiligd, intrekken als zij het beleid hebben gemaakt dat het document beveiligt of als het beleid een gedeeld beleid is dat deze mogelijkheid toestaat.
* Van beleid veranderen dat op een document wordt toegepast. De gebruikers die beleid op documenten toepassen kunnen een beleid schakelen als zij het creeerden of als het een gedeeld beleid is dat dit vermogen toelaat. Coördinatoren van beleidssets kunnen van hun beleidsreeksen overschakelen. Beheerders kunnen een ander beleid kiezen dat op elk document wordt toegepast.

Wanneer een document door een beleid wordt beschermd en u toegangsvoorrechten intrekt of het toegepaste beleid verandert, worden de veranderingen van kracht als volgt:

* Als het document online is, worden de wijzigingen direct toegepast, tenzij het document voor de gebruiker is geopend. In dit geval moet de gebruiker het document sluiten voordat de wijzigingen van kracht worden.
* Als een ontvanger het document offline gebruikt (bijvoorbeeld op een laptop), worden de wijzigingen van kracht wanneer de ontvanger opnieuw synchroniseert met documentbeveiliging door een document te openen dat met een beleid is beveiligd.

## Informatie over een document weergeven {#view-information-about-a-document}

Voor elk document dat op de pagina Documenten wordt weergegeven, ziet u de documentnaam, de uitgeversnaam, de beleidsnaam en de datum waarop het document is beveiligd. Als het beleid dat een document beschermde is geschrapt, beleidsidentiteitskaart is vermeld onder de Naam van het Beleid.

U kunt ook meer details, die hieronder worden beschreven, weergeven over een bepaald document op de pagina Documentdetails:

>[!NOTE]
>
>Gebruik de koppeling Beleidsnaam op de pagina Documentdetails om toegang te krijgen tot beleid dat automatisch wordt gegenereerd in Microsoft Outlook voor ontvangers van een document dat aan een e-mailbericht is gekoppeld. Dit beleid wordt niet weergegeven op de pagina met beleidsregels.

**Naam van het Document:** De naam van het geselecteerde document.

**identiteitskaart van het Document:** een uniek herkenningsteken dat de documentveiligheid toewijst wanneer een beleid op het document wordt toegepast. In documentbeveiliging wordt dit nummer gebruikt om het document bij te houden.

**Status van het Document:** Status van het document (bijvoorbeeld, actief of ingetrokken.)

**Uitgever:** Naam van de gebruiker die het beleid aan het document vastmaakte.

**Naam van het Beleid:** De naam van het beleid dat wordt gebruikt om het document te beschermen. U kunt op de naam klikken om het beleid te openen. Met deze koppeling krijgt u toegang tot het beleid dat Acrobat genereert voor ontvangers van een document dat is gekoppeld aan een e-mailbericht in Outlook. Dit beleid wordt niet weergegeven op de pagina Beleid.

**Type van Beleid:** het type van beleid dat op het document werd toegepast.

**Gepubliceerde Datum:** de datum het beleid werd toegepast op het document.

**Verwante Herhalingen:** als het document verwante herhalingen heeft, verschijnt dit punt ook in de lijst. Klik op de koppeling om de lijst met verwante herhalingen voor het document weer te geven.

Gebruikers kunnen informatie over hun beveiligde documenten bekijken. Beheerders kunnen informatie weergeven over documenten die door elke gebruiker zijn beveiligd met een beleid. Coördinatoren van beleidssets kunnen informatie bekijken over documenten die door beleid worden beschermd tegen hun beleidssets.

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Klik in de lijst met documenten op het gewenste document. De pagina Documentdetails wordt geopend en er wordt gedetailleerde informatie over het document weergegeven. Deze pagina bevat ook opties voor het intrekken van de documenttoegang, het wijzigen van het beleid en het weergeven van gebeurtenissen die betrekking hebben op dit document.

## Gerelateerde herhalingen voor een document weergeven {#view-related-iterations-for-a-document}

Als het bijhouden van verwante herhalingen is ingeschakeld, kunt u versies bijhouden van een document dat door verschillende gebruikers is opgeslagen. Deze functie wordt alleen ondersteund door bepaalde toepassingen, zoals PTC Pro/ENGINEER Wildfire.

Deze functie is handig wanneer meerdere gebruikers samenwerken en verschillende versies van hetzelfde document opslaan. Met documentbeveiliging kunt u de verschillende versies bijhouden. Hierdoor kunt u gemakkelijk de documentgegevens voor de verschillende versies bekijken.

Als deze functie is ingeschakeld, kunt u de verwante versies van een document bekijken vanaf de pagina Documenten.

1. Bekijk de pagina Documentdetails voor een document. (Zie [ informatie van de Mening over een document ](controlling-access-policy-protected-documents.md#view-information-about-a-document).)
1. Klik op Verwante herhalingen weergeven. De optie is alleen beschikbaar als de functie is ingeschakeld. De lijst met verwante herhalingen wordt weergegeven. Voor elke herhaling kunt u de volgende informatie weergeven:

   * **Herhaling:** filename. De naam kan verschillen van de oorspronkelijke bestandsnaam en er wordt een versienummer aan het einde van de naam toegevoegd.
   * **Uitgever:** De uitgever van het originele document.
   * **die door wordt gecreeerd:** de gebruiker die de herhaling bewaarde.
   * **Gemaakte Datum:** de datum en de tijd dat de Herhaling werd bewaard.
   * **Beleid:** het beleid dat de herhaling beschermt. Verschillende herhalingen kunnen door verschillende beleidsregels worden beschermd.

1. Als u de pagina Documentdetails voor die herhaling wilt weergeven, klikt u op de bestandsnaam van een herhaling.

## Toegang tot documenten intrekken en opnieuw instellen {#revoking-and-reinstating-access-to-documents}

U kunt de toegang tot documenten die met een beleid zijn beveiligd, intrekken en opnieuw instellen:

**Gebruikers:** kan toegang tot documenten intrekken of herstellen die zij met hun eigen persoonlijk beleid of met gedeeld beleid beschermen waarvoor het herroepingsvermogen voor de gebruiker wordt toegelaten die het beleid toepast. Gebruikers die de toegang tot een document niet kunnen intrekken of van beleid kunnen veranderen, moeten contact opnemen met de beheerder.

**Beheerders:** kan toegangsvoorrechten aan om het even welk beleid-beschermd document, met inbegrip van die intrekken of opnieuw opnemen die door persoonlijk of gedeeld beleid worden beschermd. Als een beheerder de toegang tot een document herroept dat met een gedeeld beleid wordt beveiligd, kan alleen een beheerder de toegangsrechten voor dat document opnieuw instellen.

**de vastgestelde coördinatoren van het Beleid:** kan toegangsvoorrechten voor documenten intrekken of opnieuw opnemen die het beleid van hun beleidsreeksen beschermt.

Wanneer u toegangsrechten voor documenten intrekt of weer instelt, wordt de wijziging op de volgende tijdstippen van kracht:

* Als het document online en gesloten is, wordt de verandering van kracht de volgende tijd de ontvanger met documentveiligheid door een beleid-beschermd document te openen synchroniseert.
* Als het document online en open is, wordt de wijziging van kracht wanneer de ontvanger het document sluit.
* Als het document offline is (dus in gebruik zonder internetverbinding, bijvoorbeeld op een laptop), wordt de wijziging van kracht wanneer de ontvanger opnieuw synchroniseert met de documentbeveiliging.

**herhaal toegang tot een beleid-beschermd document**

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Schakel het selectievakje naast het desbetreffende document in en klik op Intrekken. U kunt de toegang tot meerdere documenten tegelijk intrekken.
1. Selecteer een bericht om weer te geven aan gebruikers die proberen het document te openen nadat het is ingetrokken:

   * **Algemeen Bericht:** wijst erop dat de auteur het document heeft ingetrokken
   * **Geëindigd Document:** wijst erop dat de auteur het document beëindigde
   * **Herzien Document**: Wijst erop dat de auteur het document herwerkte

1. (Optioneel) Als er een nieuwere versie van het document beschikbaar is, voert u de URL in en klikt u op Testen om de URL te controleren.
1. Klik op OK en klik nogmaals op OK om terug te keren naar de pagina Documenten.

**herstelt de voorrechten van de documenttoegang**

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Klik in de lijst met documenten op het gewenste document.
1. Klik op Verwijderen en vervolgens op OK.

## Een ander beleid toepassen op een document {#switch-a-policy-that-is-applied-to-a-document}

De gebruikers, de coördinatoren van de beleidsreeks, en de beheerders kunnen het beleid schakelen dat op een beleid-beschermd document wordt toegepast (u kunt slechts één beleid tegelijkertijd op een document toepassen). De gebruikers kunnen beleid schakelen dat op hun eigen beleid-beschermde documenten wordt toegepast als zij het beleid creeerden of als het beleid gedeelde is die deze toegelaten capaciteit heeft. Anders, moet de beheerder of de coördinator van de beleidsreeks het beleid schakelen. Beheerders kunnen van beleid wisselen voor documenten die met een beleid zijn beveiligd. Coördinatoren van beleidssets kunnen van hun beleidsreeksen overschakelen.

Wanneer u een beleid schakelt, wordt het nieuwe beleid als volgt afgedwongen:

* Als het document online en gesloten is, wordt de wijziging van kracht wanneer de ontvanger opnieuw synchroniseert met documentbeveiliging door een met een beleid beveiligd document online te openen.
* Als het document online en geopend is, wordt de wijziging van kracht wanneer de gebruiker het document sluit.
* Als het document offline is (in gebruik zonder actieve internet- of netwerkverbinding, zoals op een laptop), wordt de wijziging toegepast wanneer de gebruiker opnieuw synchroniseert met documentbeveiliging door een document dat met een beleid is beveiligd online te openen.

>[!NOTE]
>
>Om anonieme toegang tot een beleid-beschermd document toe te laten dat momenteel deze toegang niet heeft, verwijder het bestaande beleid in de cliënttoepassing en pas dan een beleid toe dat anonieme toegang toestaat. Als u van beleid verandert, moeten de gebruikers nog login om tot het document toegang te hebben.

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Klik in de lijst met documenten op het gewenste document.
1. Klik op Wisselbeleid. Er wordt een lijst met maximaal 100 beleidsregels weergegeven.
1. Als het gewenste beleid niet wordt weergegeven, selecteert u Beleidsnaam of Beleid-id in de lijst Zoeken, typt u de naam of id en klikt u op Zoeken.
1. Klik op een nieuw beleid in de lijst.
1. Klik op Beleid wisselen en klik vervolgens op OK om terug te keren naar de pagina Documenten.

## Zoeken naar een document {#search-for-a-document}

U kunt naar documenten op de pagina van Documenten zoeken door een combinatie criteria van het datumbereik en de onderzoekscriteria te gebruiken die in de lijst beschikbaar zijn. Deze criteria zijn onder andere de documentnaam, de beleidsnaam of alle documenten.

Enkele aanvullende zoekopties zijn alleen beschikbaar voor beheerders:

**identiteitskaart van het Document:** Uniek aantal van identiteitskaart dat documentveiligheid aan het document toewijst wanneer het beleid wordt toegepast.

**Naam van het Document:** Naam van het document.

**naam van de Uitgever:** Naam van de gebruiker die het beleid aan het document vastmaakte. U kunt de gebruiker uit alle domeinen of een gespecificeerd domein selecteren.

**identiteitskaart van het Beleid:** Aantal van identiteitskaart van het beleid dat aan het document in bijlage is.

**Naam van het Beleid:** Naam van het beleid dat aan het document in bijlage is.

**Alle documenten:** Alle documenten die door beheerders en gebruikers worden beschermd. Als u de optie Alle documenten gebruikt om te zoeken, wordt mogelijk een lange lijst met documenten geretourneerd.

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Selecteer de vereiste zoekcriteria in de lijst Zoeken.

   U kunt de criteria opgeven als document-id, documentnaam, uitgeversnaam, beleids-id, beleidsnaam of alle documenten.

   Als u de uitgeversnaam opgeeft, klikt u op het pictogram Adresboek en geeft u het domein op waar u de gebruiker wilt doorzoeken. Klik vervolgens op OK om terug te keren naar de zoekpagina Documenten.

1. (Optioneel) Selecteer in de lijst Datum een optie voor het datumbereik. Als u Aangepaste datums selecteert, typt u de datum in de notatie jjjj/mm/dd in de vakken die worden weergegeven of gebruikt u de Datumkiezer om het datumbereik op te geven:

   * Klik op de kalender om de Datumkiezer te openen.
   * Gebruik de pijlen om een jaar en een maand te vinden.
   * Klik op een dag van de maand in de kalender.
   * Klik op OK om de Datumkiezer te sluiten.

1. Klik op Zoeken.

## De documentlijst sorteren {#sort-the-document-list}

U kunt de lijst met documenten sorteren op kolomkop. De driehoekspictogrammen naast de kolomkop geven aan welke kolom momenteel wordt gebruikt om te sorteren. Een naar boven wijzend driehoekje geeft de oplopende volgorde aan, terwijl een naar beneden wijzend driehoekje de aflopende volgorde aangeeft.

1. Klik op Documenten op de pagina Documentbeveiliging.
1. Klik op de gewenste kolomkop.
1. Klik nogmaals op de kolom om de sorteervolgorde te wijzigen.

## Voorblad toevoegen aan documenten die met een beleid zijn beveiligd {#add-cover-page-to-policy-protected-documents}

Als er de meeste niet-Adobe PDF-viewers zijn, als u een met documentbeveiliging beveiligd document opent, wordt de eerste pagina als een lege pagina weergegeven of wordt de toepassing afgebroken zonder het document te openen.

Met de ondersteuning Pagina 0 (Omsluitend document) kunnen niet-Adobe PDF-viewers een beveiligd document openen en een omslagpagina in het document weergeven.

>[!NOTE]
>
>Als u dergelijke documenten (met een pagina 0) weergeeft in Adobe Reader/Acrobat of Mobile Reader, wordt het beveiligde document standaard geopend.

**om omslagpagina aan een beleid beschermd document toe te voegen**

Gebruik de volgende processen in Workbench:

**Beschermen
Document met omslagpagina:** beveiligt een PDF-document met het opgegeven beleid en voegt een omslagpagina toe aan het document

**Extraheert Beschermd Document:** trekt het beleid-beschermde document van PDF uit het document van PDF met omslag pagina

Gebruik de volgende API&#39;s voor documentbeveiliging:

**protectDocumentWithCoverPage:** beveiligt een bepaalde PDF met het gespecificeerde beleid, en keert een document met een omslag en het beschermde document als gehechtheid terug
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a PDF document to which a policy is applied FileInputStream fileInputStream = new FileInputStream("C:\\testFile.pdf"); Document inPDF = new Document(fileInputStream); //Reference a Cover Page document FileInputStream coverPageInputStream = new FileInputStream("C:\\CoverPage.pdf"); Document inCoverDoc = new Document(coverPageInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document RMSecureDocumentResult rmSecureDocument = documentManager.protectDocumentWithCoverPage( inPDF, "ProtectedPDF.pdf", "PolicySetName", "PolicyName", null, null, inCoverDoc, true); //Retrieve the policy-protected PDF document Document protectPDF = rmSecureDocument.getProtectedDoc(); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); protectPDF.copyToFile(myFile);` **extractProtectedDocument:** trekt het beschermde document uit dat een gehechtheid in het document met omslagpagina is. Het document met de omslagpagina kan worden gemaakt met de methode protectDocumentWithCoverPage
`//Create a ServiceClientFactory instance ServiceClientFactory factory = ServiceClientFactory.createInstance(connectionProps); //Create a RightsManagementClient object RightsManagementClient rightsClient = new RightsManagementClient(factory); //Reference a protected PDF document with a Cover Page FileInputStream fileInputStream = new FileInputStream("C:\\policyProtectedDocWithCoverPage.pdf"); Document inPDF = new Document(fileInputStream); //Create a Document Manager object DocumentManager documentManager = rightsClient.getDocumentManager(); //Apply a policy to the PDF document Document extractedDoc = documentManager.extractProtectedDocument(inPDF); //Save the policy-protected PDF document File myFile = new File("C:\\PolicyProtectedDoc.pdf"); extractedDoc.copyToFile(myFile);`
