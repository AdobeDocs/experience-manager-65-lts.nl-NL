---
title: Database Credential Store Setup Guide (standalone modus)
description: Zoek de database-credentiële store-setup voor AEM Forms JEE op JBoss/Red Hat EAP in zelfstandige modus.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '763'
ht-degree: 0%

---


# Database Credential Store Setup Guide (standalone modus)

## Overzicht

Deze gids behandelt de **opstelling van de gegevensbestandcredentieopslag** voor AEM Forms JEE op JBoss/Red Hat EAP op **standalone wijze**. Dit is vereist wanneer u handmatige installatie uitvoert.


**Deze gids behandelt:**

- Het creëren van de gegevensbestandcredentieopslag (`cred-store.p12`)
- Databasewachtwoordaliassen veilig toevoegen
- JBoss configureren voor gebruik van de referentiewinkel

**KRITISCH:** Deze manuscripten werken in **ALLEEN OFFLINE MODUS**. JBoss moet worden gestopt alvorens deze manuscripten in werking te stellen. De scripts gebruiken de modus `embed-server` , waarvoor de server moet worden gestopt.

**Nota:** dit is **niet** een volledige standalone installatiegids. Dit document gaat uit van:

- JBoss is al geïnstalleerd
- Standalone configuratiebestanden (`lc_oracle.xml`, `lc_mysql.xml` of `lc_mssql.xml`) zijn al geconfigureerd
- Database is ingesteld en toegankelijk

Raadpleeg de hoofdinstallatiegids als u volledige zelfstandige installatie-instructies nodig hebt.

## Vereisten

Controleer voordat u deze scripts uitvoert:

1. **JBoss MOET** worden tegengehouden
   - Deze manuscripten werken in **ALLEEN OFFLINE MODUS**
   - De scripts gebruiken `embed-server` , waarvoor de server moet worden gestopt
   - Als JBoss wordt uitgevoerd, mislukken de scripts
   - Controleren of JBoss wordt uitgevoerd:
      - Windows: Taakbeheer controleren op `java.exe` -proces
      - Linux: `ps aux | grep jboss` of `ps aux | grep java`
   - JBoss stoppen als deze wordt uitgevoerd:
      - Pers `Ctrl+C` in de terminal waar JBoss loopt
      - Of maak het proces handmatig af

2. **u hebt klaar het gegevensbestandwachtwoord**

3. **u op een veilig wachtwoord voor de credentieopslag** hebt beslist

4. **u weet welk dossier van de gegevensbestandconfiguratie u gebruikt:**
   - `lc_oracle.xml` (voor Oracle-database)
   - `lc_mysql.xml` (voor MySQL-database)
   - `lc_mssql.xml` (voor Microsoft SQL Server-database)

## Stappen instellen

### Stap 1: Database Credential Store maken

Gebruik de verstrekte manuscripten om de gegevensbestandcredentieopslag tot stand te brengen en alle vereiste wachtwoordaliassen toe te voegen.

#### In Windows:

**Plaats van het Manuscript:** `create-elytron-cred-standalone.bat`

`batch cd path\to\script\location create-elytron-cred-standalone.bat`

**het manuscript zal u voor vragen:**
1. **JBOSS_HOME weg** (b.v., `C:\Adobe\Adobe_Experience_Manager_Forms\jboss`)
2. **het dossier van de Configuratie naam** (b.v., `lc_oracle.xml`, `lc_mysql.xml`, of `lc_mssql.xml`)
3. **het Wachtwoord van de Credentiële opslag** (dit beschermt het sleutelarchiefdossier - herinner dit wachtwoord)
4. **wachtwoord van het Gegevensbestand** (uw eigenlijk gegevensbestandwachtwoord)

**wat het manuscript doet:**

- Creeert credentieopslag op: `JBOSS_HOME\standalone\configuration\cred-store.p12`
- Wijzigt tijdelijk het configuratiebestand om het maken van een referentieopslagruimte mogelijk te maken
- Voegt de volgende aliassen met uw gegevensbestandwachtwoord toe:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Hiermee herstelt u de oorspronkelijke staat van het configuratiebestand
- Hiermee wordt gecontroleerd of alle aliassen zijn toegevoegd

#### In Linux:

**Plaats van het Manuscript:** `create-elytron-cred-standalone.sh`

`bash cd /path/to/script/location chmod +x create-elytron-cred-standalone.sh./create-elytron-cred-standalone.sh`

**het manuscript zal u voor vragen:**

1. **JBOSS_HOME weg** (b.v., `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss`)
2. **het dossier van de Configuratie naam** (b.v., `lc_oracle.xml`, `lc_mysql.xml`, of `lc_mssql.xml`)
3. **het Wachtwoord van de Credentiële opslag** (dit beschermt het sleutelarchiefdossier - herinner dit wachtwoord)
4. **wachtwoord van het Gegevensbestand** (uw eigenlijk gegevensbestandwachtwoord)

**wat het manuscript doet:**

- Creeert credentieopslag op: `JBOSS_HOME/standalone/configuration/cred-store.p12`
- Wijzigt tijdelijk het configuratiebestand om het maken van een referentieopslagruimte mogelijk te maken
- Voegt de volgende aliassen met uw gegevensbestandwachtwoord toe:
   - `EncryptDBPassword`
   - `EncryptDBPassword_IDP_DS`
   - `EncryptDBPassword_EDC_DS`
   - `EncryptDBPassword_AEM_DS`
- Hiermee herstelt u de oorspronkelijke staat van het configuratiebestand
- Hiermee wordt gecontroleerd of alle aliassen zijn toegevoegd

**Verwachte Output:**

```
=== JBoss Elytron Credential Store Setup ===
Enter JBOSS_HOME path (e.g. /opt/jboss): /opt/Adobe/Adobe_Experience_Manager_Forms/jboss
Enter configuration file name (e.g. lc_oracle.xml): lc_oracle.xml
Enter credential store password: ********
Confirm credential store password: ********
Enter database password: ********
Creating credential store using JBoss CLI...
Adding aliases to credential store...
Verifying credential store aliases...

All 4 aliases verified successfully!
- EncryptDBPassword
- EncryptDBPassword_IDP_DS
- EncryptDBPassword_EDC_DS
- EncryptDBPassword_AEM_DS

Credential store setup completed successfully!
```

### Stap 2: standalone configuratiebestand bijwerken

Na het in werking stellen van het manuscript, moet u JBoss vormen om het credentiële opslagwachtwoord bij opstarten te lezen.

#### In Windows:

**Plaats van het Dossier:** `<JBOSS_HOME>\bin\standalone.conf.bat`

Voorbeeld: `C:\Adobe\Adobe_Experience_Manager_Forms\jboss\bin\standalone.conf.bat`

Voeg de volgende regel toe of werk deze bij:

```batch
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourActualPassword123"
```

Vervang `YourActualPassword123` met het **credentiële opslagwachtwoord** u in Stap 1 gebruikte.

#### In Linux:

**Plaats van het Dossier:** `<JBOSS_HOME>/bin/standalone.conf`

Voorbeeld: `/opt/Adobe/Adobe_Experience_Manager_Forms/jboss/bin/standalone.conf`

Voeg de volgende regel toe of werk deze bij:

```bash
JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourActualPassword123"
```

Vervang `YourActualPassword123` met het **credentiële opslagwachtwoord** u in Stap 1 gebruikte.

### Stap 3: JBoss starten

Nadat u de installatie van de referentieopslagruimte hebt voltooid, start u JBoss met het juiste configuratiebestand.

**Nota:** voor de nauwkeurige startbevelen en procedures om JBoss op standalone wijze te beginnen, gelieve te verwijzen naar de **belangrijkste installatiegids**. De opstartopdrachten kunnen afhankelijk van uw specifieke configuratie en gegevensbestandtype (`lc_oracle.xml`, `lc_mysql.xml`, of `lc_mssql.xml`) variëren.

## Verificatie

### Serverlogboeken controleren

**Plaats van het Logboek:**

- Windows: `<JBOSS_HOME>\standalone\log\server.log`
- Linux: `<JBOSS_HOME>/standalone/log/server.log`

**zoek succesvolle startberichten:**

```
INFO  [org.jboss.as.server] WFLYSRV0025: JBoss EAP started
INFO  [org.jboss.as.connector.deployers.jdbc] Bound data source [java:/AdobeDataSource]
```

**geen fouten met betrekking tot:**

- Laden van referentieopslagruimte
- Databaseverbinding
- Ontbrekende aliassen

## Problemen oplossen

### Issue 1: Credential Store niet gevonden

**Bericht van de Fout:**

```
ERROR Unable to load credential store
```

**Oplossing:**

1. Controleer of het referentieopslagbestand bestaat:
   - Windows: `dir <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `ls -l <JBOSS_HOME>/standalone/configuration/cred-store.p12`
2. Als deze optie ontbreekt, voert u het script voor het maken van de referentie-winkel opnieuw uit (stap 1)

### Versie 2: Onjuist wachtwoord van creditcardwinkel

**Bericht van de Fout:**

```
ERROR Unable to load credential store - Invalid password
```

**Oplossing:**
Controleer of het wachtwoord in `standalone.conf.bat` / `standalone.conf` (Stap 2) overeenkomt met het wachtwoord dat wordt gebruikt bij het maken van de referentieopslag (Stap 1).

**aan Reparatie:**
Bewerk `standalone.conf.bat` / `standalone.conf` en werk het wachtwoord bij:

```
set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=CorrectPassword"
```

### Probleem 3: Verbinding met database mislukt

**Bericht van de Fout:**

```
ERROR Failed to obtain connection
```

**Oplossing:**

1. Controleren of het databasewachtwoord dat in de referentieopslagruimte wordt gebruikt, correct is
2. Controleer of de configuratie van de gegevensbron naar de juiste alias verwijst
3. Netwerkconnectiviteit met de databaseserver verifiëren

**om Credentiële Opslag opnieuw te creëren:**

1. JBoss stoppen
2. Verwijder de bestaande referentieopslagruimte:
   - Windows: `del <JBOSS_HOME>\standalone\configuration\cred-store.p12`
   - Linux: `rm <JBOSS_HOME>/standalone/configuration/cred-store.p12`
3. Voer het script voor het maken van de referentie-winkel opnieuw uit met het juiste databasewachtwoord

### Probleem 4: script mislukt tijdens uitvoering

**Bericht van de Fout:**

```
ERROR: jboss-cli.bat is not found
```

**Oplossing:**
Verifieer dat de weg JBOSS_HOME correct is en aan de JBoss installatiemap richt.

**Bericht van de Fout:**

```
ERROR: Configuration file not found
```

**Oplossing:**

1. Controleren of de naam van het configuratiebestand correct is
2. Controleren of het bestand in de map `JBOSS_HOME\standalone\configuration\` staat
3. Verzeker u het correcte gegevensbestand-specifieke configuratiedossier gebruikt

## Snelle naslag

### Database Credential Store (zelfstandige modus)

**Doel:** veilig de gegevensbestandwachtwoorden van de opslag

**Manuscript:**

- Windows: `create-elytron-cred-standalone.bat`
- Linux: `create-elytron-cred-standalone.sh`

**creeert:**

- Bestand: `standalone/configuration/cred-store.p12`
- Aliassen: `EncryptDBPassword`, `EncryptDBPassword_IDP_DS`, `EncryptDBPassword_EDC_DS`, `EncryptDBPassword_AEM_DS`

**Configuratie:**

- Variabele: `-DCS_PASS=password`
- Bestand: `standalone.conf.bat` (Windows) of `standalone.conf` (Linux)

