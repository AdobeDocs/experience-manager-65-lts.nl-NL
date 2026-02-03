---
title: Kan JBoss Domain Controller niet starten
description: In AEM Forms 6.5.1 LTS-clusterimplementaties die gebruikmaken van JBoss EAP 8, kan het configuratiebestand dubbele tags bevatten.
solution: Experience Manager
feature: Deploying
role: User,Admin,Developer
source-git-commit: 259cb81eb9652405dc7270535cbf9deb996ad2ac
workflow-type: tm+mt
source-wordcount: '153'
ht-degree: 0%

---


# Kan JBoss Domain Controller niet starten

## Probleem

In **AEM Forms 6.5.1 LTS** clusterplaatsingen die **JBoss EAP 8** gebruiken, het configuratiedossier
`<JBOSS_HOME>/domain/configuration/domain_oracle.xml` (en gegevensbestand-specifieke varianten) kunnen a **dubbele het openen `<security>` markering** bevatten.

Dit veroorzaakt een **ongeldige configuratie van XML**, resulterend in **JBoss het startmislukking van het Controlemechanisme van het Domein** en verhinderend succesvolle clusterinitialisatie.

## Van toepassing op

* **Product:** AEM Forms 6.5.1 LTS
* **Type van Plaatsing:** Cluster
* **de Server van de Toepassing:** JBoss EAP 8.x
* **de Dossiers van de Configuratie:**

   * `<JBOSS_HOME>/domain/configuration/domain_oracle.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mysql.xml`
   * `<JBOSS_HOME>/domain/configuration/domain_mssql.xml`

## Stappen voor probleemoplossing

1. Tijdens het opstarten van het Controlemechanisme van het Domein, kunnen de volgende fouten worden waargenomen:

   * `WFLYCTL0198: Unexpected element 'security'`
   * `IJ010061: Unexpected element: security`

2. Open het relevante configuratiebestand:

   ```
   <JBOSS_HOME>/domain/configuration/domain_oracle.xml
   (or domain_mysql.xml / domain_mssql.xml)
   ```

3. Zoek de dubbele `<security>` openingstag.

   **Onjuiste configuratie:**

   ```xml
   <security>
       <security>
           <user-name>adobe</user-name>
           <credential-reference store="db-creds" alias="EncryptDBPassword"/>
       </security>
   ```

4. Verwijder de extra openingstag `<security>` zodat de configuratie wordt gecorrigeerd zoals hieronder wordt getoond:

   **Correcte configuratie:**

   ```xml
   <security>
       <user-name>adobe</user-name>
       <credential-reference store="db-creds" alias="EncryptDBPassword"/>
   </security>
   ```

5. Sla het bestand op en start de JBoss Domain Controller.

6. Zorg ervoor dat dezelfde gevalideerde configuratie consistent wordt toegepast op alle clusterknooppunten.
