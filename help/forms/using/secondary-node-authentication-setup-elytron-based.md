---
title: Secundaire instellingen voor knooppuntverificatie (gebaseerd op Elytron)
description: JBoss EAP 8 gebruikt Elytron om veilige communicatie en registratie van secundaire knopen met het primaire Controlemechanisme van het Domein toe te laten.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: f093f39fb535209297940cff13a99c7631812152
workflow-type: tm+mt
source-wordcount: '471'
ht-degree: 0%

---


# Secundaire instellingen voor knooppuntverificatie (gebaseerd op Elytron)

## Secundaire knooppuntverificatie configureren met Elytron

JBoss EAP 8 gebruikt **Elytron** om mededeling tussen **primaire en secundaire knopen** in een gegroepeerde plaatsing voor authentiek te verklaren. Deze configuratie verzekert veilige registratie en mededeling van secundaire knopen met het primaire Controlemechanisme van het Domein.

Er zijn twee instellingsopties beschikbaar, afhankelijk van de omgeving en de beveiligingsvereisten.


## Vereisten

* A **genoemde beheersgebruiker`secondary`** moet op de **primaire knoop** worden gecreeerd.
* Voer deze configuratie **slechts op secundaire knoop(s) uit**.
* Herhaal de configuratie voor **elke secundaire knoop** in de cluster.
* **JBoss moet volledig** op zowel primaire als secundaire knopen worden tegengehouden.
* Alle credentiële opslagverrichtingen moeten op **off-line wijze** worden uitgevoerd.

JBoss stoppen als het wordt uitgevoerd:

* **Vensters**

  ```
  <JBOSS_HOME>\bin\jboss-cli.bat --connect command=:shutdown
  ```

* **Linux / UNIX**

  ```
  <JBOSS_HOME>/bin/jboss-cli.sh --connect command=:shutdown
  ```

## Een instellingsoptie kiezen

* **Optie 1: Snelle Opstelling die Standaard Credentiële Opslag gebruikt**
Aanbevolen voor lagere omgevingen en tests.

* **Optie 2: De Opstelling van de Opslag van de Aangepaste Referentie**
Aanbevolen voor productie en veilige omgevingen.

## Optie 1: Snel instellen met gebruik van de standaardopslag van referentie

**het meest geschikt voor:** Ontwikkeling, het testen, en snelle opstellingsscenario&#39;s.

### Overzicht

* Een standaard credentieopslagdossier (`cs_secondary_hc.p12`) wordt preconfigured.
* Het standaardwachtwoord voor de referentie-winkel is al ingesteld in `domain.conf` .
* Alleen de alias voor het verificatiewachtwoord hoeft te worden toegevoegd.

### Configuratiestappen

#### Stap 1: Standaardcreditcardwinkel verifiëren

Bevestig dat het standaard credentiearchiefbestand bestaat:

* **Vensters**

  ```
  <JBOSS_HOME>\domain\configuration\cs_secondary_hc.p12
  ```

* **Linux**

  ```
  <JBOSS_HOME>/domain/configuration/cs_secondary_hc.p12
  ```

Als het dossier niet bestaat, gebruik **Optie 2**.

#### Stap 2: Alias voor verificatiewachtwoord toevoegen

Voer de volgende opdracht uit vanaf `<JBOSS_HOME>/bin` :

* **Vensters**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "password" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

> De geheime waarde moet overeenkomen met het wachtwoord dat wordt gebruikt bij het maken van de `secondary` -gebruiker op het primaire knooppunt.

#### Stap 3: Verifieer de Configuratie van domain.conf

Controleer of het volgende item al bestaat (geen wijzigingen vereist):

* **Vensters**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=password"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=password"
  ```

#### Stap 4: De knooppunten starten

1. Begin de **primaire knoop** en wacht op het volledig te initialiseren.
2. Begin de **secundaire knoop**.

### Verificatie

Controleer de logbestanden:

* **Primaire Knoop**

  ```
  <JBOSS_HOME>/domain/log/host-controller.log
  ```

  ```
  Registered remote secondary host "secondary"
  ```

* **Secundaire Knoop**

  ```
  Connected to primary host controller
  ```

## Optie 2: Aangepaste installatie van referentie-winkel (productie)

**het meest geschikt voor:** de milieu&#39;s van de Productie die verbeterde veiligheid vereisen.

### Configuratiestappen

#### Stap 1: Standaardopslag verwijderen (indien aanwezig)

Als de standaardreferentieopslagruimte bestaat, wijzigt u de naam ervan:

* **Vensters**

  ```
  rename cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

* **Linux**

  ```
  mv cs_secondary_hc.p12 cs_secondary_hc.p12.bak
  ```

#### Stap 2: Aangepaste creditcardwinkel maken

Van `<JBOSS_HOME>/bin`:

* **Vensters**

  ```
  elytron-tool.bat credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --create --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12"
  ```

#### Stap 3: Alias voor verificatiewachtwoord toevoegen

* **Vensters**

  ```
  elytron-tool.bat credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

* **Linux**

  ```
  ./elytron-tool.sh credential-store --location "../domain/configuration/cs_secondary_hc.p12" --password "YourCustomPassword" --type KeyStoreCredentialStore --properties "keyStoreType=PKCS12" --add "secondary_hc_auth" --secret "ActualSecondaryUserPassword"
  ```

#### Stap 4: domein.conf bijwerken

Werk de referentie van het wachtwoord voor de referentie van het credentiearchief bij:

* **Vensters**

  ```
  set "JAVA_OPTS=%JAVA_OPTS% -DSec_Auth_PASS=YourCustomPassword"
  ```

* **Linux**

  ```
  JAVA_OPTS="$JAVA_OPTS -DSec_Auth_PASS=YourCustomPassword"
  ```

#### Stap 5: controleer de Configuratie van XML

Zorg ervoor dat `host-secondary.xml` de geconfigureerde vermeldingen voor het referentiearchief en de verificatieclient bevat.
Er zijn geen wijzigingen vereist als de standaardconfiguratie aanwezig is.


#### Stap 6: De knooppunten starten

1. Begin de **primaire knoop** en wacht tot volledig begonnen.
2. Begin de **secundaire knoop**.

### Verificatie

Bevestig succesvolle registratie gebruikend gastheer-controlemechanisme het programma opent beide knopen.

## Samenvatting

* **Optie 1** verstrekt een snelle opstelling gebruikend een preconfigured credentieopslag.
* **Optie 2** laat sterkere veiligheid toe gebruikend een wachtwoord van de douanecredentieopslag.
* De configuratie moet **op secundaire knopen slechts** worden voltooid.
* De primaire knoopconfiguratie wordt automatisch opnieuw gebruikt over het domein.

