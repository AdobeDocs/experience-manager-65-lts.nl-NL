---
title: De complexiteit van upgrades beoordelen met de AEM Analyzer
description: Leer hoe u de AEM Analyzer gebruikt om de complexiteit van uw upgrade te beoordelen.
topic-tags: upgrading
content-type: reference
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 2645745a83477509bac81cb5e122eabc44db3961
workflow-type: tm+mt
source-wordcount: '2068'
ht-degree: 15%

---


# De complexiteit van upgrades beoordelen met de AEM Analyzer {#assessing-the-upgrade-complexity-with-the-aem-analyzer}

## Overzicht {#overview}

De AEM 6.5 LTS Analyzer verstrekt een beoordeling van uw huidige implementatie van AEM door op gebieden te wijzen die worden vereist om een naadloze verbeteringservaring aan 6.5 LTS te verstrekken.

Het hulpmiddel produceert een rapport dat gebieden van potentieel refactoring identificeert.

## AEM 6.5 LTS-analyserapport {#aem-65lts-analyzer-report}

Het AEM 6.5 LTS Analyzer-rapport wordt gebruikt om een beter inzicht te krijgen in de algemene gereedheid voor upgrades. Het verslag bevat bevindingen binnen categorieën van kwesties die moeten worden aangepakt om een succesvolle upgrade naar AEM 6.5 LTS te waarborgen.

Het AEM 6.5 LTS Analyzer-rapport bevat de volgende categorieën:

* Applicatiefunctionaliteit die moet worden geherstructureerd
* Repository-items die naar een ondersteunde locatie moeten worden verplaatst
* Configuratieproblemen
* AEM 6.5-functies die zijn verwijderd door nieuwe functionaliteit of die momenteel niet worden ondersteund door AEM 6.5 LTS
* Java- en Guava API-gebruik verwijderen

Aanvullende informatie over de categorieën en mogelijke implicaties en oplossingen die aan die categorieën zijn gekoppeld, wordt verstrekt via koppelingen vanuit het AEM 6.5 LTS Analyzer Report.

## Beschikbaarheid {#analyzer-availability}

De Analysator van AEM kan als zip dossier van het [ portaal van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aemcloud.html) worden gedownload. U kunt het pakket via [ Manager van het Pakket ](/help/sites-administering/package-manager.md) op uw bronAEM instantie installeren.

## Belangrijke overwegingen voor het gebruik van AEM Analyzer {#important-considerations-for-using-aem-analyzer}

Volg de onderstaande sectie om inzicht te krijgen in de belangrijke overwegingen voor het uitvoeren van de AEM Analyzer:

* Het rapport van de Analysator wordt gebouwd gebruikend de output van de Detector van het Patroon van AEM [ ](/help/sites-deploying/pattern-detector.md). De versie van Patroondetector die door Analyzer wordt gebruikt, is opgenomen in het installatiepakket voor AEM Analyzer
* De Analysator van AEM kan slechts door de **admin** gebruiker of een gebruiker in de **beheerders** groep worden in werking gesteld
* Analyzer wordt ondersteund op AEM-instanties met versie 6.5 en hoger.

>[!NOTE]
>
>Om een impact op bedrijfskritieke instanties te voorkomen, wordt u aangeraden AEM Analyzer uit te voeren in een werkgebiedomgeving die zich zo dicht mogelijk bij de productieomgeving bevindt op het gebied van aanpassingen, configuraties, inhoud en gebruikerstoepassingen. Het kan ook worden uitgevoerd op een kloon van de productieauteur-omgeving.

* Het genereren van AEM Analyzer-rapportinhoud kan een aanzienlijke hoeveelheid tijd in beslag nemen, van enkele minuten tot enkele uren. De hoeveelheid tijd die nodig is, is in hoge mate afhankelijk van de grootte en aard van de inhoud van de AEM-opslagplaats, de AEM-versie en andere factoren
* Wegens de significante tijd die kan worden vereist om de rapportinhoud te produceren, wordt het geproduceerd door een achtergrondproces en in een geheim voorgeheugen gehouden. Het bekijken en downloaden van het rapport gaat relatief snel, omdat hierbij de content in het cachegeheugen wordt opgehaald, totdat het geheugen verloopt of het rapport uitdrukkelijk wordt vernieuwd. Tijdens de generatie van rapportinhoud kunt u uw browser lusje sluiten en in een recentere tijd terugkeren om het rapport te bekijken zodra zijn inhoud in het geheime voorgeheugen beschikbaar is.

## Het AEM Analyzer-rapport weergeven {#viewing-the-aem-analyzer-report}

Voer de onderstaande stappen uit om het AEM Analyzer-rapport weer te geven:

1. Selecteer Adobe Experience Manager en navigeer aan **Hulpmiddelen - Verrichtingen - 6.5 Modernizer LTS**

   ![ Rapport 1 van de Analysator van de Mening ](/help/sites-deploying/assets/view-analyzer-report-1.png)

1. Klik **AEM 6.5 LTS Analyzer** om het te openen

   ![ Rapport 2 van de Analysator van de Mening ](/help/sites-deploying/assets/view-analyzer-report-2.png)

1. Klik **produceren Rapport** om de Analysator van AEM uit te voeren

   ![ Rapport 3 van de Analysator van de Mening ](/help/sites-deploying/assets/view-analyzer-report-3.png)

1. Terwijl de AEM Analyzer het rapport genereert, kunt u de voortgang van het hulpprogramma op het scherm zien. Het toont de vooruitgang in termen van het voltooide percentage. Ook wordt het aantal geanalyseerde items en het aantal bevindingen weergegeven

   ![ Rapport 4 van de Analysator van de Mening ](/help/sites-deploying/assets/view-analyzer-report-4.png)

1. Nadat het 6.5 rapport van de Analysator van LTS wordt geproduceerd, toont het een samenvatting en het aantal bevindingen in een tabelvorm die door het type van het vinden en het belangrijkheidsniveau wordt georganiseerd. Voor meer informatie over een bepaalde bevinding kunt u op het nummer klikken dat overeenkomt met het type bevinding in de tabel

   ![ Rapport 5 van de Analysator van de Mening ](/help/sites-deploying/assets/view-analyzer-report-5.png)

1. U hebt de optie om het rapport in een komma-gescheiden waarden (CSV) formaat te downloaden door op **Uitvoer naar CSV** te klikken. U kunt de Analysator dwingen om zijn geheime voorgeheugen te ontruimen en het rapport opnieuw te produceren door **te klikken verfrist Rapport**. Als het geheime voorgeheugen verloopt, moet u het rapport opnieuw produceren.

## Het AEM Analyzer-rapport interpreteren {#interpreting-the-aem-analyzer-report}

Wanneer het 6.5 hulpmiddel van de Analysator LTS in de instantie van AEM in werking wordt gesteld, wordt het rapport getoond als resultaten in het hulpmiddelvenster.

Het rapport is als volgt ingedeeld:

* **Overzicht van rapport**: Informatie over het rapport zelf. het overzicht biedt de volgende gegevens:

   * **Tijd van het Rapport**: Toen de rapportinhoud werd geproduceerd en eerst beschikbaar gemaakt
   * **Tijd van de Verloop**: Wanneer het geheime voorgeheugen van de rapportinhoud zal verlopen
   * **Periode van de Tijd van de Generatie**: De hoeveelheid tijd waarin het rapport werd geproduceerd
   * **het Vinden Telling**: Het totale aantal bevindingen inbegrepen in het rapport

* **Overzicht van het Systeem**: Informatie over het systeem van AEM waarop de Analyzer werd in werking gesteld
* **Categorieën voor bevindingen**: Meerdere secties waarin elk een of meer bevindingen van dezelfde categorie worden behandeld. Elke sectie bevat de volgende items: categorienaam, subtypen, aantal en belang, samenvatting, koppeling naar categoriedocumentatie en individuele informatie over de bevindingen.

  ![ Samenvatting van het Rapport van de Analysator ](/help/sites-deploying/assets/analyzer-report-summary.png)

  Aan elke bevinding wordt een belangniveau toegewezen als ruwe prioriteit voor de benodigde actie.

>[!NOTE]
>
>Meer over elke het Vinden Categorie leren, zie {de Categorieën van de Detector van 0} Patroon ](https://experienceleague.adobe.com/en/docs/experience-manager-pattern-detection/table-of-contents/aso).[

Om inzicht te krijgen in de belangrijkste niveaus, volgt u de onderstaande tabel:

| Belang | Beschrijving |
|---|---|
| INFO | Deze bevinding wordt alleen ter informatie verstrekt. |
| ADVISORY | Deze bevinding vormt mogelijk een upgradeprobleem. Vervolgonderzoek wordt aanbevolen. |
| CRITICAL | Deze bevinding is waarschijnlijk een upgradeprobleem dat moet worden aangepakt om functie- of prestatieverlies te voorkomen. |

## Het CSV-rapport van AEM 6.5 LTS Analyzer interpreteren {#interpreting-the-aem-65lts-analyzer-report}

Wanneer u de **CSV** optie van uw instantie van AEM klikt, wordt het formaat CSV van het rapport van de Analysator gebouwd van het inhoudsgeheime voorgeheugen en teruggekeerd aan uw browser. Afhankelijk van de browserinstellingen wordt dit rapport automatisch gedownload als een bestand met de standaardnaam `report.csv` .

Als het geheime voorgeheugen is verlopen, dan wordt het rapport opnieuw geproduceerd alvorens het Csv- dossier wordt gebouwd en gedownload.

De CSV-indeling van het rapport bevat informatie die wordt gegenereerd op basis van de Pattern Detector-uitvoer. Deze informatie is gesorteerd en ingedeeld op categorietype, subtype en belang. De indeling is geschikt voor weergave en bewerking in een applicatie zoals Microsoft Excel. Het is bedoeld om alle vindingsinformatie in een herhaalbaar formaat te verstrekken dat wanneer het vergelijken van rapporten in tijd kan nuttig zijn om vooruitgang te meten.

Het CSV-indelingsrapport bevat de volgende kolommen:

* **code**: De categoriecode
* **type**: De categorienaam
* **subtype**: Het subtype van de categorie
* **importance**: Het belang van de bevinding
* **identifier**: De primaire id van de bevinding
* **message**: Het bericht dat voor de bevinding wordt verstrekt
* **context**: Een JSON-tekenreeks voor het zoeken naar data

De waarde &quot;`\N`&quot;in een kolom voor een individueel vinden wijst erop dat geen gegevens werden verstrekt.

## HTTP-interface {#http-interface}

De 6.5 LTS Analyzer verstrekt een interface van HTTP die als alternatief voor zijn gebruikersinterface binnen AEM kan worden gebruikt. De interface ondersteunt zowel `HEAD` - als `GET` -opdrachten. Het kan worden gebruikt om het rapport Analyzer te produceren en het in één van drie formaten terug te keren: JSON, CSV, en lusje-gescheiden waarden (TSV).

De volgende URL&#39;s zijn beschikbaar voor HTTP-toegang, waarbij `<host>` de hostnaam is, zo nodig naast de poort, van de server waarop de Analyzer is geïnstalleerd:

* `http://<host>/apps/aem66-analyzer/analysis/report.json` voor de JSON-indeling
* `http://<host>/apps/aem66-analyzer/analysis/report.csv` voor de CSV-indeling
* `http://<host>/apps/aem66-analyzer/analysis/report.tsv` voor de TSV-indeling

### Een HTTP-aanvraag uitvoeren {#executing-an-http-request}

Een eenvoudige manier om een HTTP-aanvraag uit te voeren, is om een tabblad te openen in dezelfde browser waarin u zich al als beheerder hebt aangemeld bij AEM. U kunt de URL invoeren op het browsertabblad en de resultaten laten weergeven of downloaden door de browser.

U kunt ook een opdrachtregelprogramma gebruiken, zoals `curl` of `wget` , en elke HTTP-clienttoepassing. Wanneer u geen browsertabblad gebruikt met een geverifieerde sessie, moet u de naam en wachtwoord van een beheerder-gebruiker opgeven als onderdeel van de opmerking.

Hieronder ziet u hoe u dit kunt doen:

```shell
curl -u admin:admin 'http://localhost:4502/apps/aem66-analyzer/analysis/report.csv' > report.csv.
```

## De levensduur van de cache aanpassen {#adjusting-the-cache-lifetime}

De standaard AEM 6.5 LTS Analyzer cache-levensduur is 24 uur. Met de optie om een rapport te verfrissen, en het geheime voorgeheugen, in zowel de instantie van AEM als de interface van HTTP te regenereren, zal deze standaardwaarde waarschijnlijk aangewezen voor de meeste toepassingen van AEM 6.5 LTS Analyzer zijn. Als de tijd van de rapportgeneratie voor uw instantie van AEM bijzonder lang is, kunt u het geheim voorgeheugenleven willen aanpassen om de regeneratie van het rapport te minimaliseren.

De levenswaarde van de cache wordt opgeslagen als de eigenschap `maxCacheAge` op het volgende knooppunt in de opslagplaats:

```
/apps/aem66-analyzer/content/modernizer/analyzer/jcr:content
```

De waarde van deze eigenschap is de levensduur van de cache in seconden. Een beheerder kan de levensduur aanpassen met CRX/DE Lite.

## Inhoudstransformator gebruiken {#using-content-transformer}

### Beschikbaarheid {#content-transformer-availability}

De Content Transformer wordt gebundeld met de AEM 6.5 LTS Analyzer die als een zip-bestand kan worden gedownload van de Software Distribution Portal.

### Belangrijke overwegingen voor het gebruik van Content Transformer {#important-considerations-for-using-content-transformer}

Zie de sectie hieronder om de belangrijke overwegingen voor het gebruiken van de Transformator van de Inhoud (CT) te begrijpen:

* Als u de Content Transformer wilt gebruiken, moet u eerst de AEM Analyzer uitvoeren in uw AEM-omgeving
* Hoewel u de Transformer van de Inhoud op uw milieu van de Productie kunt in werking stellen, adviseert men dat u de Transformer van de Inhoud op een kloon van uw milieu van de Productie in werking stelt. Nog belangrijker is dat u ervoor zorgt dat de AEM Analyzer en de CT in dezelfde omgeving worden uitgevoerd
* U moet een beheerder op het milieu zijn waar u de Transformer van de Inhoud wilt in werking stellen
* Met een verwijderbewerking die de broninhoud kan wijzigen, wordt standaard vóór de transformatie een back-uppakket gemaakt van de bronpaden onder `/etc/packages/modernizer-content-transformation` . Hoewel het dialoogvenster voor verwijderen een optie bevat om het maken van het back-uppakket uit te schakelen of in te schakelen, wordt het ten zeerste aanbevolen om het maken van het pakket altijd inschakelen te selecteren
* Elke pagina in de Content Transformer is geconfigureerd om maximaal 50 bevindingen weer te geven. Daarom kunnen maximaal 50 bevindingen tegelijk worden getransformeerd. Dit wordt gedaan om een geschikte reactie in UI te verstrekken.

### De inhoudstransformator openen {#opening-the-content-transformer}

1. Login aan de bronAEM instantie als beheerder en ga naar de beginpagina in *https://host:port/aem/start.htm*
1. Navigeer aan **Hulpmiddelen - Verrichtingen - 6.5 Modernizer LTS**

   ![ het Openen Inhoud Transformer 1 ](/help/sites-deploying/assets/opening-content-transformer-1.png)

1. Klik op de **Transformer van de Inhoud voor 6.5 LTS het rapport van de Analysator** kaart

   ![ het Openen Inhoud Transformer 2 ](/help/sites-deploying/assets/opening-content-transformer-2.png)

1. Als het rapport van de Analysator niet wordt geproduceerd, zal de **pagina van de Inhoud van de Transformatie** **Geen Rapport** tonen. Het zelfde **Geen bericht van het Rapport** zal ook verschijnen als alle op inhoud betrekking hebbende bevindingen zijn verwijderd

   ![ het Openen Inhoud Transformer 3 ](/help/sites-deploying/assets/opening-content-transformer-3.png)

1. Hieronder ziet u een voorbeeld van hoe de pagina Overzicht van Content Transformer eruit zal zien als het maken van het AEM Analyzer-rapport is gelukt en als er inhoudgerelateerde problemen zijn aangetroffen.

De resterende tijd voor het AEM Analyzer-rapport is te zien op de zijspoor. Het wordt aanbevolen de Content Transformer uit te voeren met het meest recente AEM Analyzer-rapport om te voorkomen dat bevindingen met betrekking tot inhoud ontbreken

![ het Openen Inhoud Transformer 4 ](/help/sites-deploying/assets/opening-content-transformer-4.png)

1. U kunt de problemen filteren op basis van Patrooncode, Subtype, Importantie en Source

   ![ het Openen Inhoud Transformer 5 ](/help/sites-deploying/assets/opening-content-transformer-5.png)

### Paden verwijderen {#removing-paths}

1. U kunt alle of specifieke kwesties selecteren en **selecteren verwijdert** om hen op te lossen

   ![ het Verwijderen van Wegen 1 ](/help/sites-deploying/assets/removing-paths-1.png)

   >[!NOTE]
   >Met de bewerking Verwijderen wordt standaard vóór de transformatie een back-uppakket gemaakt van de bronpaden onder `/etc/packages/modernizer-content-transformation` . Hoewel het dialoogvenster voor verwijderen een optie bevat om het maken van het back-uppakket uit te schakelen of in te schakelen, wordt het ten zeerste aanbevolen om het maken van het pakket altijd in te schakelen.

   ![ het Verwijderen van Wegen 2 ](/help/sites-deploying/assets/removing-paths-2.png)

1. Hieronder ziet u een voorbeeld van een back-uppakket dat is gemaakt voor het verwijderen van paden. U kunt **klikken installeert** om de bronwegen terug te brengen

   ![ het Verwijderen van Wegen 3 ](/help/sites-deploying/assets/removing-paths-3.png)

   >[!CAUTION]
   >
   >Verwijder `/etc/packages/modernizer-content-transformation` niet, omdat dit de locatie is waar de back-uppakketten zich bevinden. U kunt deze locatie alleen verwijderen om de grootte van de opslagplaats te reduceren als u zeker weet dat u deze pakketten niet meer nodig hebt.

1. Desgewenst kunt u geselecteerde inhoud verpakken voor toekomstig gebruik. Om dit te doen, selecteer de bevindingen u, dan **Pakket** van bovenkant links wilt omvatten klikken. Ga een pakketnaam in, kies een pakketweg, en klik het **Pakket** knoop om het proces te voltooien.

   ![ het Verwijderen van Wegen 3 ](/help/sites-deploying/assets/removing-paths-4.png)

### Bekende problemen {#known-issues}

* Soms wordt bij de verwijderbewerking de melding *&quot;Sommige paden zijn niet verwijderd. Controleer de logbestanden en probeer het opnieuw.*&quot;. Als de paden echter zijn verwijderd, kunt u dit bericht veilig negeren
* Op dezelfde manier kan de bewerking Pakket mislukken met de fout: *&quot;Fout tijdens het uitvoeren van de gewenste bewerking, controleer de logboeken en probeer het opnieuw.*&quot;. Dit is waarschijnlijk te wijten aan het verlopen van de sessie. In dergelijke gevallen moet het probleem worden opgelost door de bewerking opnieuw te proberen.





