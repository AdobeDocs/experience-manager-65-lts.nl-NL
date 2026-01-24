---
source-git-commit: 0deac9cb7fb13c6fec515739168eb2dbfd9a58c7
workflow-type: tm+mt
source-wordcount: '739'
ht-degree: 3%

---
# Richtlijnen voor het bijdragen aan de documentatie van Adobe Experience Manager

## Documentatiefilosofie

Adobe Experience Manager-gebruikers werken in zeer concurrerende omgevingen en streven naar het creëren van digitale ervaringen die hen onderscheiden van hun concurrenten. Daarom is het van essentieel belang dat wanneer Adobe geavanceerde nieuwe tools in AEM levert, deze tools worden aangevuld met nauwkeurige en duidelijke documentatie, zodat de klant onmiddellijk gebruik kan maken van zijn AEM-investering en zijn investeringsrendement kan maximaliseren.

Het doel van de documentatie van AEM is om documentatie zo snel mogelijk in de handen van AEM-gebruikers te brengen. Het AEM-documentatieteam geeft daarom prioriteit aan nauwkeurige, bruikbare documentatie en streeft ernaar deze voortdurend bij te werken en te verbeteren.

## Documentatiebijdragen

Om de documentatie van AEM voortdurend te verbeteren, is de hele gemeenschap van AEM-gebruikers welkom om aan de documentatie bij te dragen. Of het door trekkingsverzoeken of kwesties, de verbeteringen van de documentatie kunnen correcties, verduidelijkingen, uitbreidingen, en extra voorbeelden zijn.

## Documentatienormen

Hoewel het documentatieteam van Experience Manager de bijdragen aan de documentatie van Adobe toejuicht, moet elke bijdrage aan de documentatie van AEM - in de vorm van een pull-verzoek of een kwestie - in overeenstemming zijn met de bijdrage- en documentatienormen van het team.

Bijdragen die niet aan deze normen voldoen, kunnen worden afgewezen.

### Experience Manager-documentatieteam documenteert standaard gebruiksgevallen.

De documentatie van AEM behandelt standaardgebruiksgevallen. Gebruiksgevallen die buiten het bereik van de standaardinstallatie en het standaardgebruik van het product vallen, maken geen deel uit van de documentatie van AEM.

### Het Experience Manager-documentatieteam documenteert doorgaans geen bugs of de bijbehorende tijdelijke oorzaken.

De documentatie van AEM behandelt standaardgebruiksgevallen. Daarom zijn bugs, effecten die door bugs worden veroorzaakt, en de tijdelijke oorzaken van bugs niet gedocumenteerd.

Uitzonderingen op deze regel zijn van toepassing op de opmerkingen bij de release waar bekende problemen kunnen worden vermeld met mogelijke oplossingen die zijn goedgekeurd door AEM Product Management.

### De bijdragen van de documentatie zijn niet voor het beantwoorden van technische vragen.

Alle ideeën die u eventueel nodig hebt om de documentatie van AEM te verbeteren, zijn welkom als bijdragen. Nochtans zijn de commentaren, de kwesties, en trekkingsverzoeken voorgenomen voor *bijdragen* slechts. Ze zijn niet bedoeld om je vragen te beantwoorden over hoe je AEM kunt gebruiken, je AEM-project kunt implementeren of technische problemen kunt oplossen.

Om het even welke vragen over het gebruik van AEM of technische fouten u door het normale steunproces via het [&#x200B; portaal van de Steun van Experience Manager &#x200B;](https://experienceleague.adobe.com/nl?support-solution=Experience+Manager#home) zou kunnen moeten worden gemeld of in de [&#x200B; gemeenschap van Experience Manager &#x200B;](https://experienceleaguecommunities.adobe.com/t5/adobe-experience-manager/ct-p/adobe-experience-manager-community?profile.language=nl) besproken.

***de documentatiebijdragen van AEM zijn geen vervanging voor de Steun van de Klant van Adobe*** en om het even welke dergelijke bijdragen die antwoorden op steun-verwante vragen zoeken worden verworpen.

### Bijdragen moeten duidelijk verwijzen naar betrokken documentatiepagina&#39;s.

Als u een probleem maakt om verbeteringen in de documentatie voor te stellen, moet u koppelingen naar de betrokken pagina&#39;s opnemen. Als u een probleemmelding maakt met de koppeling **Deze pagina bewerken** op een documentatiepagina, wordt de probleemmelding automatisch gemaakt met een koppeling naar de pagina.

Dit is niet van toepassing op pull-aanvragen, omdat pull-aanvragen door hun aard verwijzen naar de betrokken pagina&#39;s.

## Documentatierichtlijnen

Eventuele bijdragen aan AEM-documentatie moeten aan bepaalde stijlrichtlijnen voldoen.

Met deze richtlijnen kunt u uw bijdrage gemakkelijker beoordelen en daarom is integratie in de documentatie van AEM sneller.

### Taal en stijl

#### Taal

* AEM-documentatie is geschreven en onderhouden in het Engels van de VS.
* Zin zo eenvoudig mogelijk houden.
* Houd de taal duidelijk en beknopt.

Alle lezers van AEM-documentatie zijn over de hele wereld beschikbaar en kunnen niet verwachten dat ze native of vloeiende Engelstalige luidsprekers zijn. Vermijd colloquialisme en houd de taal zo duidelijk en eenvoudig mogelijk.

#### Handleiding Microsoft® volgen

[&#x200B; het Handboek Microsoft® van Stijl &#x200B;](https://learn.microsoft.com/en-us/style-guide/welcome/) is een vrij beschikbare gids van de documentatiestijl die zich op softwaredocumentatie concentreert en de documentatie van AEM volgt deze gids waar mogelijk.

### Opmaak

| Item | Stijl |
|---|---|
| UI-element of -optie | **gewaagd** |
| Bestandsnaam, pad, gebruikersinvoer, parameterwaarden | `monospaced` |
| Code, opdrachtregel | ```Code Block``` |

### Screenshots

Schermafbeeldingen moeten met de nodige voorzichtigheid worden gebruikt en alleen wanneer een tekstbeschrijving niet volstaat.

Gebruik geen markeringen of andere annotaties in schermafbeeldingen (zoals rode kaders, pijlen of tekst). Op deze manier zijn de schermafbeeldingen gemakkelijker te hergebruiken of in gelokaliseerde versies van de documentatie te herhalen.

### Versiespecifieke verwijzingen

Probeer zo veel mogelijk directe verwijzingen naar een specifieke versie in de documentatie te voorkomen. Dit maakt de documentatie flexibeler en verlengbaar voor toekomstige versies.

### Gebruik van Dag, AEM, CQ, CRX

Het product zou altijd door zijn volledige naam **Adobe Experience Manager** voor het eerst in een artikel moeten worden geroepen en kan daarna als **AEM** worden bedoeld.

Gebruik geen Day, Day Software, CQ en CRX, tenzij dit onvermijdelijk is, bijvoorbeeld in klassenamen of met verwijzing naar de geschiedenis van AEM.