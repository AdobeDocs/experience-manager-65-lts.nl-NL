---
title: Upgrade naar AEM 6.5 Forms LTS op OSGi
description: U kunt een directe upgrade uitvoeren van AEM 6.5.22.0 Forms naar AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: b7aa877f9e782b0568adc7baa440dc630c690454
workflow-type: tm+mt
source-wordcount: '1512'
ht-degree: 0%

---

# Upgrade naar AEM 6.5 Forms LTS op OSGi {#upgrade-to-aem-forms-osgi}

Aan [&#x200B; verbetering van AEM 6.5 aan AEM 6.5 LTS &#x200B;](/help/sites-deploying/upgrade.md), verbetering aan AEM 6.5.22.0 Forms of later. Een directe upgrade van AEM 6.5.22.0 naar AEM 6.5 Forms LTS wordt ondersteund.

Als u AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms of AEM 6.5 Forms gebruikt, is een directe upgrade naar AEM 6.5 Forms LTS niet beschikbaar. Voor gedetailleerde verbeteringswegen, verwijs naar de [&#x200B; documentatie van de Wegen van de Verbetering &#x200B;](/help/forms/using/upgrade.md).

Na upgrade naar het servicepack AEM Forms 6.5.22.0 voert u de volgende stappen uit om te upgraden naar AEM 6.5 LTS Forms:

1. Installeer het AEM Forms-invoegtoepassingspakket. De stappen worden hieronder weergegeven:

   1. Open [&#x200B; Distributie van de Software &#x200B;](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
   1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
   1. In de sectie **[!UICONTROL Filters]** :
      1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
      1. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
   1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
   1. Open [&#x200B; Manager van het Pakket &#x200B;](/help/sites-administering/package-manager.md) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
   1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

      U kunt het pakket ook downloaden gebruikend de directe verbinding die in [&#x200B; wordt vermeld versies van AEM Forms &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) artikel.

      Nadat het pakket is geïnstalleerd, wordt u gevraagd om het AEM-exemplaar opnieuw te starten. **stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log en het logbestand stabiel is. Houd er rekening mee dat een aantal pakketten in de installatiestatus kunnen blijven staan. U kunt de status van deze verpakkingen veilig negeren.


      **begin de instantie van AEM met de volgende extra bevel-lijn JVM parameters** opnieuw:
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Als de server via een script of service wordt gestart, moet u de server overeenkomstig bijwerken zodat het bovenstaande wordt opgenomen zodat deze ook van kracht zijn nadat de server opnieuw is gestart.

      >[!NOTE]
      >
      > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. Nainstallatie uitvoeren.

   * **het Nut van de Migratie van de Looppas**

     Het migratiehulpprogramma maakt de adaptieve formulieren en het beheer van correspondentie van eerdere versies compatibel met AEM 6.5-formulieren. U kunt het hulpprogramma downloaden van AEM Software Distribution. Voor geleidelijke informatie om het migratienut te vormen en te gebruiken, zie [&#x200B; migratienut &#x200B;](../../forms/using/migration-utility.md).

     Als u [&#x200B; Steekproef voor het integreren van concepten &amp; voorleggingscomponent &#x200B;](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) met het gegevensbestand en de bevordering van een vorige versie gebruikt, dan stel de volgende SQL vragen na het uitvoeren van de verbetering in werking:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Adobe Sign opnieuw configureren**

     Als Adobe Sign was geconfigureerd in de vorige versie van AEM Forms, configureert u Adobe Sign vervolgens opnieuw vanuit de AEM Cloud-services. Voor meer details, zie [&#x200B; het Teken van Adobe met AEM Forms &#x200B;](../../forms/using/adobe-sign-integration-adaptive-forms.md) integreren.

   * **Steun voor jQuery**

     In AEM 6.5 Forms wordt de versie van jQuery bijgewerkt naar versie 3.2.1 en de versie van jQuery-gebruikersinterface naar versie 1.12.1. De Vorm van AEM gebruikt JQuery op **noConflict** wijze. Als u dus een andere jQuery-versie gebruikt, worden er geen problemen weergegeven tijdens het uitvoeren van een upgrade. Als u echter een upgrade uitvoert naar AEM 6.5 Forms:

      * Controleer of uw aangepaste componenten, indien aanwezig, compatibel zijn met ondersteunde jQuery-versies.
      * Verwijder niet-ondersteunde API&#39;s uit de aangepaste componenten. Zie [&#x200B; verbeteringsgids &#x200B;](https://jquery.com/upgrade-guide/3.0/) voor de lijst van verwijderde APIs. Ondersteuning voor de API&#39;s load(), .unload() en .error() wordt bijvoorbeeld verwijderd. Gebruik de methode .on() in plaats van de eerder genoemde API&#39;s. Wijzig bijvoorbeeld $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Analyses en rapporten opnieuw samenstellen**

     In AEM 6.4 Forms is de verkeersvariabele voor de bron- en succesgebeurtenis voor de indruk niet beschikbaar. Als u dus een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, stopt AEM Forms met het verzenden van gegevens naar de Adobe Analytics-server en zijn er geen analyserapporten voor adaptieve formulieren beschikbaar. Bovendien introduceert AEM 6.4 Forms een verkeersvariabele voor de versie van formulieranalyse en succesgebeurtenis voor de hoeveelheid tijd die aan een veld wordt doorgebracht. Configureer daarom analyses en rapporten voor uw AEM Forms-omgeving. Voor gedetailleerde stappen, zie [&#x200B; het Vormen analyses en rapporten &#x200B;](../../forms/using/configure-analytics-forms-documents.md).

1. Controleer of de upgrade van de server is geslaagd, of alle gegevens zijn gemigreerd en of deze op de normale manier kunnen werken.

   * **verifieer het statuut van de bundels:** zorg ervoor dat alle bundels in actieve staat zijn.
   * **verifieer replicatie en omgekeerde replicatie:** publiceer, vul, en verzend een paar gemigreerde vormen. Controleer ook de verzonden gegevens.
   * **verifieer toegang tot admin en het gebruikersinterfaces van de ontwikkelaar:** Login aan de instantie van AEM van een admin rekening en verifieer dat u toegang tot volgende URLs hebt:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms is de structuur van crx-repository veranderd. Als u een upgrade uitvoert van 6.3 Forms naar AEM 6.5 Forms, gebruikt u de gewijzigde paden voor aanpassing die u opnieuw maakt. Voor de volledige lijst van veranderde wegen, zie [&#x200B; de Herstructurering van de Bewaarplaats van Forms in AEM &#x200B;](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).


## AEM implementeren op JBoss EAP 8 (Windows)

### Overzicht

Deze handleiding bevat stapsgewijze instructies voor de implementatie van Adobe Experience Manager (AEM) als een zelfstandig OSGi WAR-bestand op het JBoss Enterprise Application Platform (EAP) 8 in een Windows-omgeving met JDK 21.

### Systeemvereisten

Voordat u met het implementatieproces begint, moet u ervoor zorgen dat uw omgeving aan de volgende vereisten voldoet:

| Component | Vereiste |
|-----------|-------------|
| Besturingssysteem | Windows Server 2016 of hoger (64-bits) |
| Java Development Kit | JDK 21 (Oracle of OpenJDK) |
| Toepassingsserver | JBoss EAP 8.x |
| AEM Distribution | AEM WAR-bestand (verkregen van Adobe) |

>[!NOTE]
>
> Controleer of de omgevingsvariabele `JAVA_HOME` naar de installatiemap van JDK 21 verwijst.

### Stap 1: JBoss EAP 8 installeren

#### JBoss EAP downloaden

1. Navigeer naar de portal Red Hat Developer:\
   [&#x200B; https://developers.redhat.com/products/eap/download](https://developers.redhat.com/products/eap/download)

2. Download de JBoss EAP 8 ZIP-distributie voor Windows.

#### JBoss EAP extraheren

1. Pak het gedownloade ZIP-bestand uit naar de gewenste installatiemap.

2. Maak een notitie van dit mappad als `<JBOSS_HOME>` voor gebruik in deze handleiding.

   **Voorbeeld:**\
   ```C:\jboss-eap-8.0```

### Stap 2: Het AEM WAR-bestand voorbereiden

#### AEM WAR verkrijgen

Haal het AEM WAR-bestand op bij Adobe Software Distribution of bij uw Adobe-vertegenwoordiger.

#### Naam WAR-bestand wijzigen

Wijzig de naam van het WAR-bestand om het gewenste URL-contextpad weer te geven:

```
cq-quickstart.war
```

>[!IMPORTANT]
>
> De WAR-bestandsnaam bepaalt de URL-context van de toepassing. `cq-quickstart.war` is bijvoorbeeld toegankelijk via `/cq-quickstart` .


### Stap 3: De AEM WAR configureren

Alle configuratiewijzigingen moeten worden voltooid **alvorens** opstellend aan JBoss.

#### Werkmap maken

1. Een tijdelijke werkmap maken:

   ```
   C:\aem\war-config
   ```

2. Kopieer `cq-quickstart.war` naar deze map.

#### WAR-inhoud extraheren

1. Open **Herinnering van het Bevel** en navigeer aan uw werkende folder:

   ```cmd
   cd C:\aem\war-config
   ```

2. Extraheer het WAR-bestand:

   ```cmd
   jar -xvf cq-quickstart.war
   ```

   Hiermee maakt u een mappenstructuur met `WEB-INF` en andere toepassingsbestanden.

### Stap 4: JBoss-implementatiebeschrijving configureren

#### Implementatiestructuurbestand maken

1. Navigeer naar de map `WEB-INF` in de geëxtraheerde WAR:

   ```cmd
   cd WEB-INF
   ```

2. Maak een nieuw bestand met de naam `jboss-deployment-structure.xml` .

3. Voeg de volgende XML-inhoud toe:

   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <jboss-deployment-structure xmlns="urn:jboss:deployment-structure:1.2">
       <deployment>
           <dependencies>
               <module name="jdk.unsupported" />
           </dependencies>
       </deployment>
   </jboss-deployment-structure>
   ```

4. Sla het bestand op en sluit het.

**Doel:** Deze configuratie verleent toegang tot interne modules JDK die door AEM worden vereist.

### Stap 5: Multipart-uploadinstellingen configureren

>[!NOTE]
>
> Stap 5 is van toepassing slechts op **AEM Forms**. Als u opstelling **slechts AEM** bent, kunt u deze stap overslaan.


#### Web.xml wijzigen

1. Open `WEB-INF\web.xml` in een teksteditor.

2. Zoek de sectie `<servlet>` met de configuratie van de uitvoeringsmodus:

   ```xml
   <!-- Set the runmode per default to author -->
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

3. Vervang de afsluitende tag `</servlet>` en de voorafgaande regel door:

   ```xml
   <init-param>
       <param-name>sling.run.modes</param-name>
       <param-value>author</param-value>
   </init-param>
   <multipart-config>
       <max-file-size>1048576000</max-file-size>
       <max-request-size>1048576000</max-request-size>
       <file-size-threshold>0</file-size-threshold>
   </multipart-config>
   <load-on-startup>100</load-on-startup>
   </servlet>
   ```

4. Opslaan en sluiten `web.xml` .

**Doel:** Deze montages laten grote dossieruploads (tot 1 GB) voor AEM Forms en het Beheer van Digitale Activa toe.

### Stap 6: Het WAR-bestand opnieuw verpakken

Nadat alle configuratiewijzigingen zijn voltooid, moet u het WAR-bestand opnieuw verpakken.

1. Ga terug naar de werkmap met de geëxtraheerde inhoud:

   ```cmd
   cd C:\aem\war-config
   ```

2. Maak het nieuwe WAR-bestand:

   ```cmd
   jar -cvf cq-quickstart.war *
   ```

>[!IMPORTANT]
>
> Voer deze stap slechts eenmaal uit, nadat alle configuraties zijn voltooid.

### Stap 7: AEM implementeren en starten

#### WAR implementeren in JBoss

1. Kopieer het opnieuw verpakte `cq-quickstart.war` naar de JBoss-implementatiemap:

   ```
   <JBOSS_HOME>\standalone\deployments
   ```

   **Voorbeeld:**
   ```C:\jboss-eap-8.0\standalone\deployments```

#### JVM-instellingen configureren (optioneel maar aanbevolen)

Voordat u JBoss start, configureert u JVM-geheugeninstellingen:

1. Open `<JBOSS_HOME>\bin\standalone.conf.bat` in een teksteditor.

1. Wijzig of voeg de volgende lijn toe om heapgeheugen te plaatsen:

   ```batch
   set "JAVA_OPTS=-Xms4096m -Xmx4096m -XX:MaxMetaspaceSize=512m"
   ```

>[!NOTE]
>
> Pas de geheugenwaarden aan op basis van uw servercapaciteit en AEM-vereisten.

1. Sla het bestand op en sluit het.

#### JBoss EAP starten

1. Open **Herinnering van het Bevel** als **Beheerder**.

1. Navigeer naar de map JBoss bin:

   ```cmd
   cd <JBOSS_HOME>\bin
   ```

   **Voorbeeld:**
   ```cmd cd C:\jboss-eap-8.0\bin```

1. Start de JBoss-server:

   ```cmd
   standalone.bat -b 0.0.0.0 -bmanagement 0.0.0.0
   ```

   **Parameters:**
   * `-b 0.0.0.0` — Bind de server aan alle netwerkinterfaces
   * `-bmanagement 0.0.0.0` — Bindt de beheerinterface aan alle netwerkinterfaces

#### Monitorimplementatie

Kijk naar de consoleuitvoer voor implementatieberichten. Succesvolle implementatie wordt aangegeven door:

```
Deployed "cq-quickstart.war" (runtime-name : "cq-quickstart.war")
```

### Stap 8: Toegang tot AEM

Zodra de implementatie is voltooid en AEM volledig is gestart:

**AEM Auteur URL:**
```http://<server-ip>:8080/cq-quickstart```

**StandaardReferenties:**

* Gebruikersnaam: `admin`
* Wachtwoord: `admin`

**Belangrijk:** verander onmiddellijk het standaardwachtwoord na eerste login.

### Problemen oplossen

#### Vaak voorkomende problemen

| Probleem | Oplossing |
|-------|----------|
| Implementatie mislukt met ClassNotFoundException | Controleren of `jboss-deployment-structure.xml` correct is geconfigureerd |
| OutOfMemoryError tijdens opstarten | Hoekgeheugen vergroten in `standalone.conf.bat` |
| AEM wordt niet gestart na implementatie | JBoss-aanmeldgegevens controleren `<JBOSS_HOME>\standalone\log\server.log` |
| Kan AEM niet openen in browser | Controleer of firewallinstellingen poort 8080 toestaan |

#### Logbestanden

* **JBoss Logboek van de Server:** `<JBOSS_HOME>\standalone\log\server.log`
* **Logboek van de Fout van AEM:** Beschikbaar door de Console van het Web van AEM na opstarten bij\
  `http://<server-ip>:8080/cq-quickstart/system/console`

### Aanvullende configuratie

#### Run-modi configureren

Als u AEM-uitvoeringsmodi wilt wijzigen (auteur/publicatie), wijzigt u de parameter `sling.run.modes` in `WEB-INF\web.xml` voordat u de WAR opnieuw verpakt:

```xml
<init-param>
    <param-name>sling.run.modes</param-name>
    <param-value>publish</param-value>
</init-param>
```

#### Productieaanbevelingen

Voor productieomgevingen:

* SSL/TLS-certificaten configureren in JBoss
* AEM-replicatieagents instellen
* Dispatcher configureren voor taakverdeling
* Automatische back-ups inschakelen
* Implementeren van toezicht en waarschuwingen

### Verwante documentatie

* [&#x200B; JBoss EAP 8 Documentatie &#x200B;](https://access.redhat.com/documentation/en-us/red_hat_jboss_enterprise_application_platform/8.0)
* [&#x200B; Documentatie van Adobe Experience Manager &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65.html)
* [&#x200B; de Gids van de Installatie en van de Plaatsing van AEM &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-65/deploying/deploying/deploy.html)

### Documentgegevens

| Veld | Waarde |
|-------|-------|
| Laatst bijgewerkt | februari 2026 |
| AEM-versie | 6.5+ (LTS) |
| JBoss-versie | EAP 8.x |
| JDK-versie | 21 |
| Platform | Windows |


