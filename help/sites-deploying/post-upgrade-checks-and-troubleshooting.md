---
title: Controles en probleemoplossing na upgrade
description: Leer hoe u problemen kunt oplossen die na een upgrade kunnen optreden.
contentOwner: sarchiz
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: upgrading
content-type: reference
docset: aem65
feature: Upgrading
solution: Experience Manager, Experience Manager Sites
role: Admin
source-git-commit: 09b297721b08ef428f1ac8a26fec38d5a8bd34fd
workflow-type: tm+mt
source-wordcount: '1200'
ht-degree: 0%

---

# Controles en probleemoplossing na upgrade{#post-upgrade-checks-and-troubleshooting}

## Controles na upgrade {#post-upgrade-checks}

Na de [ Verbetering op plaats ](/help/sites-deploying/in-place-upgrade.md) de volgende activiteiten zouden moeten worden uitgevoerd om de verbetering te voltooien. Er wordt aangenomen dat AEM is gestart met de AEM 6.5 LTS-jar en dat de geüpgraded code base is geïmplementeerd.

* [Logbestanden controleren voor een upgrade](#verify-logs-for-upgrade-success)

* [OSGi-bundels verifiëren](#verify-osgi-bundles)

* [Oak-versie verifiëren](#verify-oak-version)

* [Oorspronkelijke validatie van pagina&#39;s](#initial-validation-of-pages)

* [Configuraties voor gepland onderhoud controleren](#verify-scheduled-maintenance-configurations)

* [Replication-agents inschakelen](#enable-replication-agents)

* [Aangepaste geplande taken inschakelen](#enable-custom-scheduled-jobs)

* [Testplan uitvoeren](#execute-test-plan)


### Logboeken controleren voor upgrade voltooid {#verify-logs-for-upgrade-success}

**upgrade.log**

In het verleden was voor het inspecteren van de status van uw instantie na de upgrade zorgvuldige inspectie vereist van verschillende logbestanden, onderdelen van de opslagplaats en het startpad. Het genereren van een rapport na de upgrade kan u helpen defecte upgrades te detecteren voordat u live gaat.

Het belangrijkste doel van deze functie is om de behoefte aan handmatige interpretatie of complexe parseringslogica over veelvoudige eindpunten te verminderen die worden vereist om het succes van een verbetering te kwalificeren. De oplossing is bedoeld om ondubbelzinnige informatie te verschaffen aan externe automatiseringssystemen die reageren op het welslagen of de vastgestelde mislukking van een update.

Meer specifiek zorgt het ervoor dat:

* De mislukkingen van de verbetering die door het verbeteringskader worden ontdekt worden gecentraliseerd in één enkel verbeteringsrapport.
* Het verbeteringsrapport bevat indicatoren voor noodzakelijke handmatige interventie.

Hiervoor zijn wijzigingen aangebracht in de manier waarop logbestanden worden gegenereerd in het `upgrade.log` -bestand.

**error.log**

error.log zou zorgvuldig tijdens en na het opstarten van AEM moeten worden herzien gebruikend de jar van de doelversie. Alle waarschuwingen of fouten moeten worden herzien. In het algemeen, is het best om kwesties aan het begin van het logboek te zoeken. Fouten die zich later in het logbestand voordoen, kunnen in feite bijwerkingen zijn van een hoofdoorzaak die vroeg in het bestand wordt aangeroepen. Als de herhaalde fouten en de waarschuwingen hieronder voor [ het Analyseren van Kwesties met de Verbetering ](/help/sites-deploying/post-upgrade-checks-and-troubleshooting.md#analyzing-issues-with-the-upgrade) voorkomen.

### OSGi-bundels verifiëren {#verify-osgi-bundles}

Navigeer naar de OSGi-console `/system/console/bundles` en kijk of er geen bundels zijn gestart. Als bundels zijn geïnstalleerd, raadpleegt u `error.log` om het hoofdprobleem te bepalen.

### Oak-versie verifiëren {#verify-oak-version}

Na de verbetering, zou u moeten zien dat de versie van Oak aan **1.68.1-B002** is bijgewerkt. Als u de Oak-versie wilt verifiëren, navigeert u naar de OSGi-console en bekijkt u de versie die is gekoppeld aan Oak-bundels: Oak Core, Oak Commons, Oak Segment Tar.

### Oorspronkelijke validatie van pagina&#39;s {#initial-validation-of-pages}

Voer een eerste validatie uit op meerdere pagina&#39;s in AEM. Als u een upgrade uitvoert naar een auteuromgeving, opent u de startpagina en welkomstpagina ( `/aem/start.html`, `/libs/cq/core/content/welcome.html` ). Open in zowel auteur- als publicatieomgevingen een aantal toepassingspagina&#39;s en rooktests die correct worden weergegeven. Raadpleeg `error.log` voor het oplossen van problemen.

### Configuraties voor gepland onderhoud controleren {#verify-scheduled-maintenance-configurations}

#### Opruiming van gegevensopslag inschakelen {#enable-data-store-garbage-collection}

Als het gebruiken van een Opslag van de Gegevens van het Dossier, zorg ervoor dat de taak van de Inzameling van de Opslag van Gegevens wordt toegelaten en aan de Wekelijkse lijst van het Onderhoud toegevoegd. De instructies worden geschetst onder [ Opruiming van de Revisie ](/help/sites-administering/data-store-garbage-collection.md).

>[!NOTE]
>
>Dit wordt niet geadviseerd voor de installaties van de douanegegevensopslag van S3 of wanneer het gebruiken van een gedeelde gegevensopslag.

#### Onlinerevisie-opruiming inschakelen {#enable-online-revision-cleanup}

Als u MongoMK of de nieuwe TarMK-segmentindeling gebruikt, dient u ervoor te zorgen dat de Revision Clean Up-taak is ingeschakeld en toegevoegd aan de lijst Dagelijks onderhoud. De instructies worden geschetst onder [ Opruiming van de Revisie ](/help/sites-deploying/revision-cleanup.md).

### Replication-agents inschakelen {#enable-replication-agents}

Zodra publicatiemilieu volledig is bevorderd en bevestigd, laat replicatieagenten op het Milieu van de Auteur toe. Verifieer dat de agenten met respectieve Publish instanties kunnen verbinden. Zie [ Procedure van de Verbetering ](/help/sites-deploying/upgrade-procedure.md) voor meer details op orde van gebeurtenissen.

### Aangepaste geplande taken inschakelen {#enable-custom-scheduled-jobs}

Om het even welke geplande banen als deel van de codebasis kunnen op dit punt worden toegelaten.

### Testplan uitvoeren {#execute-test-plan}

Voer gedetailleerd testplan uit zoals die in [ wordt bepaald Bevorderend Code en Aanpassingen onder de **Testende Procedure** sectie ](/help/sites-deploying/upgrading-code-and-customizations.md#testing-procedure-testing-procedure).

## Problemen analyseren met de upgrade {#analyzing-issues-with-the-upgrade}

Deze sectie bevat enkele probleemscenario&#39;s waarmee u tijdens de upgradeprocedure naar AEM 6.5 LTS kunt worden geconfronteerd.

### Pakketten en pakketten kunnen niet worden bijgewerkt  {#packages-and-bundles-fail-to-update}

Als pakketten niet tijdens de upgrade worden geïnstalleerd, worden de bundels in de pakketten ook niet bijgewerkt. Deze categorie van kwesties wordt veroorzaakt door wanconfiguratie van de gegevensopslag. Zij zullen ook verschijnen als **FOUT** en **WARN** berichten in error.log. Aangezien in de meeste van deze gevallen standaardlogin kan ontbreken om te werken, kunt u CRXDE direct gebruiken om de configuratieproblemen te inspecteren en te vinden.

### De upgrade is niet uitgevoerd {#the-upgrade-did-not-run}

Alvorens de voorbereidingsstappen te beginnen, zorg ervoor u de **bron** instantie eerst in werking stelt door het met het `java -jar aem-quickstart.jar` bevel uit te voeren. Dit is vereist om ervoor te zorgen dat het bestand quickstart.properties op de juiste wijze wordt gegenereerd. Als deze ontbreekt, werkt de upgrade niet. U kunt ook controleren of het bestand aanwezig is door onder `crx-quickstart/conf` te kijken in de installatiemap van de broninstantie. Wanneer AEM wordt gestart om de upgrade uit te voeren, moet deze worden uitgevoerd met de opdracht `java -jar <aem-quickstart-6.5-LTS.jar>` . Als u begint met een opstartscript, wordt AEM niet in de upgrademodus gestart.

### Sommige AEM-bundels schakelen niet naar de actieve staat {#some-aem-bundles-are-not-switching-to-the-active-state}

Als er bundels zijn die niet beginnen, controleer om het even welke ontevreden gebiedsdelen.

Als dit probleem zich voordoet, maar het is gebaseerd op een mislukte pakketinstallatie die ertoe heeft geleid dat bundels niet werden bijgewerkt, worden zij onverenigbaar geacht voor de nieuwe versie. Voor meer informatie over hoe te om dit problemen op te lossen, zie **de Ontslagen van Pakketten en van Bundels** hierboven bijwerken.

Het wordt ook aanbevolen de bundellijst van een nieuwe AEM 6.5 LTS-instantie te vergelijken met de bijgewerkte versie om de bundels te detecteren die niet zijn bijgewerkt. Hierdoor wordt het bereik vergroot van wat u zoekt in de `error.log` .

### Aangepaste bundels die niet overschakelen op de actieve staat {#custom-bundles-not-switching-to-the-active-state}

Als uw aangepaste bundels niet naar de actieve status overschakelen, is het zeer waarschijnlijk dat er code is die geen gewijzigde API importeert. Dit zal meestal leiden tot ontevreden afhankelijkheden.

Het is ook beter om te controleren of de verandering die het probleem heeft veroorzaakt noodzakelijk was en terug te keren als dat niet het geval is. Controleer ook of de versieverhoging van de pakketexport meer dan nodig is, na strikte semantische versiebewerking.

### Error.log en upgrade.log analyseren {#analyzing-the-error.log-and-upgrade.log}

In de meeste situaties, moeten de logboeken voor fouten worden geraadpleegd om de oorzaak van een probleem te vinden. Nochtans, met verbeteringen, is het ook noodzakelijk om afhankelijkheidskwesties te controleren aangezien de oude bundels niet behoorlijk zouden kunnen worden bevorderd.

De beste manier om dit te doen is onderaan error.log door van alle berichten te verwijderen die van geen verband met de kwestie worden verwacht u onder ogen ziet. U kunt dit doen door middel van hulpmiddel zoals grep, door te gebruiken:

```shell
grep -v UnrelatedErrorString
```

Sommige foutberichten zijn mogelijk niet direct explicatief. In dit geval kunt u door de context te bekijken waarin de fouten zich voordoen, beter begrijpen waar de fout is gemaakt. U kunt de fout scheiden met:

* `grep -B` voor het toevoegen van regels vóór de fout;

of

* `grep -A` voor het toevoegen van regels na.

In een paar gevallen kunnen er ook fouten worden gevonden in WARN-berichten, omdat er geldige gevallen kunnen zijn die tot deze status leiden en de toepassing niet altijd kan beslissen of dit een werkelijke fout is. Zorg ervoor dat u deze berichten ook raadpleegt.

### Contact opnemen met Adobe-ondersteuning {#contacting-adobe-support}

Neem contact op met Adobe Support als je het advies op deze pagina hebt doorlopen en nog steeds problemen ziet. Als u zoveel mogelijk informatie wilt verstrekken aan de ondersteuningstechnicus die aan uw dossier werkt, zorgt u ervoor dat u de `error.log` en `upgrade.log` bestanden van uw upgrade opneemt.
