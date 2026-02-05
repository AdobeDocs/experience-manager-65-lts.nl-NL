---
title: Database Credential Store Setup (gebaseerd op Elytron)
description: JBoss EAP 8 biedt ondersteuning voor Elytron-credentiewinkels voor veilig beheer van databasewachtwoorden in AEM Forms voor installatie van de domeinmodus.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '379'
ht-degree: 0%

---


# Database Credential Store Setup (gebaseerd op Elytron)

## Database Credential Store configureren met Elytron

JBoss EAP 8 gebruikt **de credentieopslag van Elytron** om gegevensbestandwachtwoorden voor de plaatsingen van AEM Forms veilig te beheren. Adobe verstrekt **geautomatiseerde manuscripten** om de verwezenlijking en de configuratie van de op Elytron-Gebaseerde credentieopslag op domeinwijze te vereenvoudigen.


Deze opstelling moet **worden voltooid alvorens het Controlemechanisme van het Domein JBoss** te beginnen.

### Vereisten

* De **server JBoss moet volledig worden tegengehouden** alvorens het credentiële manuscript van de archiefverwezenlijking in werking te stellen.
* De geloofwaardige opslagverwezenlijking moet op **off-line slechts wijze worden uitgevoerd**.

JBoss stoppen als het wordt uitgevoerd:

* **Vensters**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux / UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

### Scripts downloaden

Download het juiste script op basis van uw besturingssysteem:

| Scriptnaam | Besturingssysteem |
| -------------------------------- | ---------------- |
| `create-elytron-cred-domain.bat` | Windows |
| `create-elytron-cred-domain.sh` | Linux / UNIX |

Voor Linux moet u het script uitvoerbaar maken:

```
chmod +x create-elytron-cred-domain.sh
```

### Configuratiestappen

#### Stap 1: Het script downloaden en plaatsen

Download het juiste script en plaats het in de volgende map:

```
<JBOSS_HOME>/bin
```

#### Stap 2: Het script uitvoeren

* **Vensters**

  ```
  cd <JBOSS_HOME>\bin
  create-elytron-cred-domain.bat
  ```

* **Linux / UNIX**

  ```
  cd <JBOSS_HOME>/bin
  ./create-elytron-cred-domain.sh
  ```

#### Stap 3: Vereiste informatie verstrekken

Tijdens uitvoering, veroorzaakt het manuscript voor de volgende input:

1. **Weg JBOSS_HOME**
Voer het volledige pad naar de JBoss-installatiemap in.

2. **het Dossier van de Configuratie van het Gegevensbestand Naam**
Voer op basis van uw database een van de volgende handelingen in:

   * `domain_oracle.xml`
   * `domain_mysql.xml`
   * `domain_mssql.xml`

3. **Wachtwoord van de Opslag van de Referentie**
Voer een sterk wachtwoord in om de creditcardwinkel te beveiligen.

   > Dit wachtwoord is verborgen tijdens de invoer en moet voor latere stappen worden onthouden.

4. **Wachtwoord van het Gegevensbestand**
Voer het werkelijke wachtwoord voor de databaseverbinding in.

#### Stap 4: Scriptuitvoering en -validatie

Het script voert de volgende handelingen automatisch uit:

* Maakt `cred-store.p12` in:

  ```
  <JBOSS_HOME>/domain/configuration/
  ```

* Hiermee maakt u de volgende referentie-aliassen:

   * `EncryptDBPassword`
   * `EncryptDBPassword_IDP_DS`
   * `EncryptDBPassword_EDC_DS`
   * `EncryptDBPassword_AEM_DS`
* Hiermee wordt gecontroleerd of alle aliassen zijn toegevoegd

De succesvolle uitvoering bevestigt de creatie van een creditwinkel en de verificatie van aliassen.

#### Stap 5: JVM-opties configureren

Werk de JBoss configuratie van het domeinopstarten bij om het credentiële archiefwachtwoord te verstrekken.

* **Linux**
Bewerken:

  ```
  <JBOSS_HOME>/bin/domain.conf
  ```

  Toevoegen:

  ```
  JAVA_OPTS="$JAVA_OPTS -DCS_PASS=YourCredStorePassword"
  ```

* **Vensters**
Bewerken:

  ```
  <JBOSS_HOME>/bin/domain.conf.bat
  ```

  Toevoegen:

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DCS_PASS=YourCredStorePassword"
  ```

Vervang `YourCredStorePassword` door het wachtwoord dat is ingevoerd tijdens het maken van de referentie-winkel.

De domeinconfiguratiebestanden verwijzen naar deze waarde met behulp van de variabele `${CS_PASS}` .


#### Stap 6: Domeinconfiguratie verifiëren

Open het configuratiebestand van het databasedomein:

```
<JBOSS_HOME>/domain/configuration/<domain_*.xml>
```

Verifieer dat de gegevensbronnen verwijzen naar de de credentieopslag van Elytron:

```xml
<security>
    <user-name>your_database_username</user-name>
    <credential-reference store="db-creds" alias="EncryptDBPassword_IDP_DS"/>
</security>
```

Elke gegevensbron gebruikt een specifieke alias:

* **IDP_DS:** `EncryptDBPassword_IDP_DS`
* **EDC_DS:** `EncryptDBPassword_EDC_DS`
* **AEM_DS:** `EncryptDBPassword_AEM_DS`
* **DefaultDS / ExampleDS:** `EncryptDBPassword`

Alle aliassen verwijzen naar hetzelfde databasewachtwoord dat is opgeslagen in de referentieopslagruimte.

>[!NOTE]
>
>* Vorm de credentieopslag slechts op de primaire knoop.
>* De secundaire knopen gebruiken automatisch de domeinconfiguratie die van de primaire knoop wordt gesynchroniseerd.
