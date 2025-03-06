---
title: Audit Log Maintenance in AEM 6
description: Meer informatie over het onderhoud van controlelogbestanden in Adobe Experience Manager (AEM).
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: operations
content-type: reference
feature: Operations
solution: Experience Manager, Experience Manager Sites
role: Admin
exl-id: dd0f90f7-5e92-49d3-a5b4-17d99ed927b9
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '605'
ht-degree: 0%

---

# Audit Log Maintenance in AEM 6{#audit-log-maintenance-in-aem}

AEM-gebeurtenissen die in aanmerking komen voor accountlogboekregistratie genereren veel gearchiveerde gegevens. Deze gegevens kunnen na verloop van tijd snel groeien als gevolg van replicaties, het uploaden van bedrijfsmiddelen en andere systeemactiviteiten.

Het onderhoud van het controlelogboek omvat verscheidene delen van functionaliteit die de capaciteit toelaat om het onderhoud van het controlelogboek onder specifiek beleid te automatiseren.

Het wordt uitgevoerd als configureerbare wekelijkse onderhoudstaak en is toegankelijk via de de monitorconsole van het Dashboard van Verrichtingen.

Voor meer informatie, zie de [ Documentatie van het Dashboard van Verrichtingen ](/help/sites-administering/operations-dashboard.md).

Er zijn drie typen opties voor het opschonen van controlelogbestanden:

1. [Pagina-auditlogboek leegmaken](/help/sites-administering/operations-audit-log.md#configure-page-audit-log-purging)
1. [DAM-controlelogbestand leegmaken](/help/sites-administering/operations-audit-log.md#configure-dam-audit-log-purging)
1. [Controlelogboek replicatie](/help/sites-administering/operations-audit-log.md#configure-replication-audit-log-purging)

Elk kan worden gevormd door regels in de Console van het Web van AEM te creëren. Nadat zij zijn gevormd, kunt u hen teweegbrengen door naar **Hulpmiddelen - Verrichtingen - Onderhoud - het Venster van het Weekonderhoud** te gaan en de **Taak van het Onderhoud AuditLog** in werking te stellen.

## Logbestand voor controle van pagina configureren {#configure-page-audit-log-purging}

Voer de volgende stappen uit om het opschonen van controlelogbestanden te configureren:

1. Ga naar de webconsolebeheerder door uw browser naar `http://localhost:4502/system/console/configMgr/` te wijzen

1. Zoek naar een punt genoemd **de regel van de Woorden van het Logboek van de controle van Pagina&#39;s** en klik het.

   ![ chlimage_1-365 ](assets/chlimage_1-365.png)

1. Vervolgens configureert u de zuiveringsplanner op basis van uw vereisten. De beschikbare opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid;
   * **weg van de Inhoud:** de weg van de inhoud de regel zal toepassen op;
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden;
   * **het logboektype van de Controle:** het type van controlelogboek dat zou moeten worden gezuiverd.

   >[!NOTE]
   >
   >Het inhoudspad is alleen van toepassing op onderliggende items van het knooppunt `/var/audit/com.day.cq.wcm.core.page` in de opslagplaats.

1. Sla de regel op.
1. De regel u creeerde moet in het Dashboard van Verrichtingen worden blootgesteld opdat het wordt uitgevoerd. Om dit te doen, ga **Hulpmiddelen - Verrichtingen - Onderhoud** van het Welkome scherm van AEM.

1. Druk de **kaart van het Venster van het Weekonderhoud**.

1. U zult de onderhoudstaak reeds aanwezig onder de **kaart van het Onderhoud van AuditLog** vinden.

   ![ chlimage_1-366 ](assets/chlimage_1-366.png)

1. U kunt of de datum van de volgende uitvoering inspecteren, het vormen, of het manueel uitvoeren door de spelknoop te drukken.

Als het geplande onderhoudsvenster in AEM 6.3 wordt gesloten voordat de taak Logboek controleren kan worden voltooid, wordt de taak automatisch gestopt. Het wordt hervat wanneer het volgende onderhoudsvenster wordt geopend.

**met AEM 6.5**, kunt u een lopende Taak van de Wrijving van het Logboek van de Controle manueel tegenhouden door het **pictogram van het Einde** te klikken. Bij de volgende uitvoering wordt de taak veilig hervat.

>[!NOTE]
>
>Om een einde te maken aan de onderhoudstaak, moet de uitvoering worden opgeschort zonder dat het spoor van de reeds in uitvoering zijnde baan verloren gaat.

## DAM-controlelogbestand opschonen {#configure-dam-audit-log-purging}

1. Navigeer aan de Console van het Systeem in *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Onderzoek naar **DAM de regel van het de controlelogboek van het de controlelogboek zuivert** en klikt het resultaat.
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid;
   * **weg van de Inhoud:** de weg van de inhoud de regel op zal toepassen
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden
   * **de gebeurtenistypen van het Logboek van de Controle:** de types van de controlegebeurtenissen van DAM die zouden moeten worden gezuiverd.

1. Klik **sparen** om uw configuratie te bewaren

## Logboek voor replicatiecontrole configureren  {#configure-replication-audit-log-purging}

1. Navigeer aan de Console van het Systeem in *https://&lt;serveraddress>:&lt;serverport>/system/console/configMgr*
1. Onderzoek naar **de controleplank van het Logboek van de Replicatie** en klik het resultaat
1. In het volgende venster, vorm dienovereenkomstig uw regel. De opties zijn:

   * **Naam van de Regel:** de naam van de regel van het controlebeleid
   * **weg van de Inhoud:** de weg van de inhoud de regel op zal toepassen
   * **Minimale leeftijd:** de tijd in dagen de controlelogboeken moeten worden gehouden
   * **de gebeurtenistypen van de Replicatie van het Logboek van de Controle van de Controle:** de types van de controlegebeurtenissen van de Replicatie die zouden moeten worden ontladen

1. Klik **sparen** om uw configuratie te bewaren.
