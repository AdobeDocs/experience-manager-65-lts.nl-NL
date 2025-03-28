---
title: Back-up- en herstelstrategie voor AEM-formulieren
description: Leer hoe u een strategie implementeert voor het maken van back-ups van gegevens en hoe u ervoor zorgt dat deze consistent blijft met de gegevens van AEM-formulieren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/aem_forms_backup_and_recovery
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 2f34b48a-0b95-4994-ac4f-616620a5b211
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1518'
ht-degree: 0%

---

# Back-up- en herstelstrategie voor AEM-formulieren{#backup-and-recovery-strategy-for-aem-forms}

Als in de implementatie van uw AEM-formulieren aanvullende aangepaste gegevens worden opgeslagen in een andere database, bent u verantwoordelijk voor het implementeren van een strategie om back-ups van deze gegevens te maken en ervoor te zorgen dat deze consistent blijven met de AEM-formuliergegevens. Bovendien moet de toepassing zo zijn ontworpen dat deze robuust genoeg is om een scenario af te handelen waarbij de extra databases niet meer synchroon zijn. Het wordt hoogst geadviseerd dat om het even welke gegevensbestandverrichting die wordt uitgevoerd in de context van een transactie wordt gedaan helpen een verenigbare staat handhaven.

Nadat u hebt vastgesteld hoe AEM-formulieren worden gebruikt, bepaalt u welke bestanden een back-up moeten maken, hoe vaak en welk back-upvenster beschikbaar moet worden gemaakt.

>[!NOTE]
>
>Net als bij elk ander aspect van de implementatie van AEM-formulieren, moet uw back-up- en herstelstrategie worden ontwikkeld en getest in een ontwikkelings- of testomgeving voordat deze in de productie wordt gebruikt om ervoor te zorgen dat de volledige oplossing werkt zoals u had verwacht zonder gegevensverlies.

Adobe Experience Manager (AEM) maakt integrerend deel uit van AEM-formulieren. Daarom moet u AEM ook synchroniseren met AEM-formulieren voor back-ups, aangezien Correspondence Management Solution en -services, zoals formulierbeheer, zijn gebaseerd op gegevens die zijn opgeslagen in AEM-onderdelen van AEM-formulieren.Om gegevensverlies te voorkomen, moet een back-up worden gemaakt van de specifieke gegevens van de AEM-formulieren, zodat GDS en AEM (gegevensopslagruimte) correleren met databaseverwijzingen.De directory&#39;s database, GDS, AEM en Content Storage Root moeten worden hersteld naar een DNS op een computer met dezelfde DNS Geef het origineel een naam.

## Typen back-ups {#types-of-backups}

De back-upstrategie voor AEM-formulieren omvat twee typen back-ups:

**beeld van het Systeem:** een volledige systeemsteun die u kunt gebruiken om de inhoud van uw computer te herstellen als uw harde aandrijving of volledige computer ophoudt werkend. Een back-up van het systeemimage is alleen nodig voordat u AEM-formulieren voor de productie gaat implementeren. Het interne bedrijfsbeleid bepaalt dan hoe vaak de steunen van het systeembeeld worden vereist.

**AEM vormt specifieke gegevens:** de gegevens van de Toepassing bestaan in gegevensbestand, de Globale Opslag van het Document (GDS), en bewaarplaats van AEM, en moeten in echt - tijd worden gesteund. GDS is een map waarin bestanden van lange duur worden opgeslagen die in een proces worden gebruikt. Deze bestanden kunnen PDF&#39;s, beleidsregels of formuliersjablonen bevatten.

>[!NOTE]
>
>Als Content Services (Afgekeurd) is geïnstalleerd, maakt u ook een back-up van de hoofdmap van de Content Storage Root. Zie [ de folder van de Wortel van de Opslag van de Inhoud (de Diensten van de Inhoud slechts) ](/help/forms/using/admin-help/files-back-recover.md#content-storage-root-directory-content-services-only).

De database wordt gebruikt om formulierartefacten, serviceconfiguraties, processtatus en databaseverwijzingen naar GDS-bestanden op te slaan. Als u de opslag van documenten in de database hebt ingeschakeld, worden permanente gegevens en documenten in de GDS ook in de database opgeslagen. U kunt een back-up van de database maken en deze herstellen met de volgende methoden:

* **de reservewijze van de Momentopname** wijst erop dat het de vormensysteem van AEM of voor een gespecificeerd aantal minuten voor onbepaalde tijd of is, waarna reservewijze niet meer wordt toegelaten. U kunt een van de volgende opties gebruiken om de back-upmodus voor momentopnamen in of uit te schakelen. Na een terugwinningsscenario, zou de wijze van de momentopname steun niet moeten worden toegelaten.

   * Gebruik de pagina Back-upinstellingen in de beheerconsole. Schakel het selectievakje Bewerken in veilige back-upmodus in om de modus voor momentopnamen in te schakelen. Schakel het selectievakje uit om de modus voor momentopnamen af te sluiten.
   * Gebruik het manuscript LCBackupMode (zie [ file het gegevensbestand, GDS, en de folders van de Root van de Opslag van de Inhoud ](/help/forms/using/admin-help/backing-aem-forms-data.md#back-up-the-database-gds-aem-repository-and-content-storage-root-directories)). Als u de modus voor momentopnamen wilt afsluiten, stelt u in het scriptargument de parameter `continuousCoverage` in op `false` of gebruikt u de optie `leaveContinuousCoverage` .
   * Gebruik de meegeleverde API voor back-up/herstel. <!-- Fix broken link(see AEM forms API Reference section on AEM Forms Help and Tutorials page).-->

* **Rolling reserve** wijze wijst erop dat het systeem altijd op reservewijze is, met een nieuwe reservewijzesessie die wordt in werking gesteld zodra de vorige zitting wordt vrijgegeven. Er is geen time-out gekoppeld aan de schuifmodus. Wanneer het manuscript LCBackupMode of APIs worden geroepen om het rollen reservewijze te verlaten, begint een nieuwe het rollen reservewijze zitting. Deze modus is handig voor het ondersteunen van continue back-ups, maar nog steeds voor het verwijderen van oude en overbodige documenten uit de GDS-directory. De modus Rolling Backup wordt niet ondersteund via de pagina Backup and Recovery. Na een terugwinningsscenario, wordt het rollen reservewijze nog toegelaten. U kunt de modus voor continue back-up (schuifmodus) verlaten door het LCBackupMode-script te gebruiken met de optie `leaveContinuousCoverage` .

>[!NOTE]
>
>Als u de schuifmodus onmiddellijk verlaat, wordt een nieuwe back-upmodussessie gestart. Als u de schuifmodus volledig wilt uitschakelen, gebruikt u de optie `leaveContinuousCoverage` in het script, dat de bestaande rolback-upsessie overschrijft. In de back-upmodus voor momentopnamen kunt u de back-upmodus zoals gewoonlijk verlaten.

Om gegevensverlies te voorkomen, moeten de specifieke gegevens van AEM-formulieren zodanig worden opgeslagen dat GDS- en Content Storage Root-documenten correleren met databasereferenties.

>[!NOTE]
>
>Wanneer de GDS is opgeslagen in het bestandssysteem en niet in de database, voert u de databaseback-up uit vóór de GDS-back-up.

## Speciale overwegingen voor back-up en herstel {#special-considerations-for-backup-and-recovery}

Gebruik de volgende richtlijnen als u AEM-formulieren in een andere omgeving moet herstellen vanwege de volgende wijzigingen:

* Wijziging in het IP-adres, de hostnaam of de poort van de AEM Forms-server
* Wijziging in stationsletters of mappad
* Wijzigen in een andere databasehost, -poort of -naam

Dergelijke herstelscenario&#39;s worden doorgaans veroorzaakt door hardwarestoringen van de server die de toepassingsserver, databaseserver of Forms Server host. Naast de AEM formulieren-specifieke configuraties die in deze sectie worden beschreven, zou u ook de noodzakelijke veranderingen voor andere delen van de de vormenplaatsing van AEM zoals ladingsbalancers en firewalls moeten aanbrengen, als hostname of IP adres van een Server van AEM Forms verandert.

### Wat niet kan worden gewijzigd {#what-cannot-be-changed}

Hoewel u de databaseserver en veel andere parameters kunt wijzigen, kunt u het servertype of databasetype van de toepassing niet wijzigen wanneer u AEM-formulieren uit een back-up herstelt. Als u bijvoorbeeld een back-up van een AEM-formulier herstelt, kunt u de toepassingsserver niet van JBoss naar WebLogic of van de database wijzigen van Oracle naar DB2. Bovendien moeten herstelde AEM-formulieren dezelfde bestandssysteempaden gebruiken, zoals de lettertypemap.

### Opnieuw opstarten na herstel {#restarting-after-a-recovery}

Ga als volgt te werk voordat u de Forms Server opnieuw start na een herstelbewerking:

1. Start het systeem in de onderhoudsmodus.
1. Ga als volgt te werk om ervoor te zorgen dat Form Manager in de onderhoudsmodus wordt gesynchroniseerd met AEM-formulieren:

   1. Ga naar https://&lt; *server*>:&lt; *haven*>/lc/fm en login gebruikend beheerder/wachtwoordgeloofsbrieven.
   1. Klik op de naam van de gebruiker (in dit geval Super Administrator) in de rechterbovenhoek.
   1. Klik **Admin Opties**.
   1. Klik **Begin** om activa van de bewaarplaats te synchroniseren.

1. In een gegroepeerde omgeving, zou de primaire knoop (met betrekking tot AEM) omhoog vóór de secundaire knopen moeten zijn.
1. Zorg ervoor dat geen processen van of interne of externe bronnen zoals het Web, SOAP, of EJB procesinitiators in werking worden gesteld tot de normale verrichting van het systeem wordt bevestigd.

Als de hoofddatabase voor AEM-formulieren wordt verplaatst of gewijzigd, raadpleegt u de installatiegidsen die relevant zijn voor uw toepassingsserver voor informatie over het bijwerken van de databaseverbindingsgegevens voor de AEM-formuliergegevensbronnen IDP_DS en EDC_DS.

>[!NOTE]
> 
> U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

### De hostnaam of het IP-adres van AEM-formulieren wijzigen {#changing-the-aem-forms-hostname-or-ip-address}

Als u in een cluster TCP-caching gebruikt in plaats van UDP, moet u de configuratie van de cachelocator bijwerken. Zie &quot;Vormend de caching locators (caching die slechts TCP gebruiken)&quot;in de configuratiegids relevant voor uw toepassingsserver.

### De systeempaden van het AEM-knooppunt voor formulieren wijzigen {#changing-the-aem-forms-node-file-system-paths}

Als u de paden van het bestandssysteem wijzigt voor een zelfstandig knooppunt, moet u de desbetreffende verwijzingen bijwerken in de voorkeuren, andere systeemconfiguraties, aangepaste toepassingen en geïmplementeerde AEM-formuliertoepassingen. Voor een cluster moeten daarentegen alle knooppunten dezelfde padconfiguratie van het bestandssysteem gebruiken. Stel de hoofdmap van de algemene documentopslag (GDS) in en zorg ervoor dat deze verwijst naar een kopie van de herstelde GDS die synchroon is met de herstelde database. Het instellen van het GDS-pad is belangrijk omdat de GDS gegevens kunnen bevatten die moeten blijven bestaan over het opnieuw opstarten van de toepassingsserver.

In een geclusterde omgeving moet de padconfiguratie van het bestandssysteem van de opslagplaats gelijk zijn voor alle clusterknooppunten vóór de back-up en na de herstelbewerking.

Gebruik het `LCSetGDS` manuscript in de `[*aem-forms root]*\sdk\misc\Foundation\SetGDSCommandline` omslag om de weg te plaatsen GDS nadat u de wegen van het dossiersysteem verandert. Zie het bestand `ReadMe.txt` in dezelfde map voor meer informatie. Als het oude GDS-directorypad niet kan worden gebruikt, moet `LCSetGDS` -script worden gebruikt om het nieuwe pad in te stellen op de GDS voordat u AEM-formulieren start.

>[!NOTE]
>
>Deze omstandigheid is de enige waaronder u dit script moet gebruiken om de GDS-locatie te wijzigen. Als u de GDS-locatie wilt wijzigen terwijl AEM-formulieren worden uitgevoerd, gebruikt u de beheerconsole. (Zie [ algemene de vormmontages van AEM ](/help/forms/using/admin-help/configure-general-aem-forms-settings.md#configure-general-aem-forms-settings)*.) * vormen

Nadat u het GDS-pad hebt ingesteld, start u de Forms-server in de onderhoudsmodus en gebruikt u de beheerconsole om de resterende bestandsysteempaden voor het nieuwe knooppunt bij te werken. Nadat u hebt gecontroleerd of alle benodigde configuraties zijn bijgewerkt, start u AEM-formulieren opnieuw en test u deze.
