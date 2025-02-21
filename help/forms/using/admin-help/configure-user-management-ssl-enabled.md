---
title: Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL
description: Leer hoe u gebruikersbeheer configureert voor een LDAP-server die geschikt is voor SSL, zodat synchronisatie correct werkt via LDAPS.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '279'
ht-degree: 0%

---

# Gebruikersbeheer configureren voor een LDAP-server die geschikt is voor SSL {#configure-user-management-for-an-ssl-enabled-ldap-server}

Synchronisatie werkt alleen correct via LDAPS als de LDAP-certificaten die de certificeringsinstantie (CA) heeft uitgegeven, aanwezig zijn in de JRE-omgeving (Java Runtime Environment) van de toepassingsserver. Importeer het certificaat in het JRE van de toepassingsserver dossier, dat gewoonlijk in de *[JAVA_HOME]* /jre/lib/security/cacerts folder is.

1. Schakel SSL in op de directoryserver. Zie de documentatie die is geleverd door de leverancier van de directory voor meer informatie.
1. Een clientcertificaat exporteren vanuit de directoryserver.
1. Gebruik het hulpprogramma Keytool om het clientcertificaatbestand te importeren in het standaard Java Virtual Machine (JVM™)-certificaatarchief van de AEM Forms Application Server. De procedure voor deze taak varieert, afhankelijk van uw JVM en de installatiepaden van de client. Als u bijvoorbeeld BEA WebLogic Server met JDK 1.5 gebruikt, typt u deze tekst via een opdrachtprompt:

   `keytool -import -alias`*alias* `-file certificatename -keystore C:\bea\jdk15_04\jre\lib\security\cacerts`

1. Typ desgevraagd het wachtwoord. (Voor Java is het standaardwachtwoord `changeit` .) Er wordt een bericht weergegeven met de mededeling dat het certificaat is geïmporteerd.
1. Typ `Yes` als u hierom wordt gevraagd om het certificaat te vertrouwen.
1. Schakel SSL in Gebruikersbeheer in en selecteer bij het configureren van de directory-instellingen Ja voor de SSL-optie en wijzig de poortinstelling dienovereenkomstig. Het standaardpoortnummer is 636.

>[!NOTE]
>
>Als u problemen ondervindt met SSL, gebruikt u een LDAP-browser om te controleren of deze toegang heeft tot het LDAP-systeem wanneer SSL wordt gebruikt. Als de LDAP-browser geen toegang kan krijgen, is uw certificaat- of toepassingsserver niet correct geconfigureerd. Als de LDAP-browser correct werkt en u nog steeds problemen ondervindt, wordt Gebruikersbeheer niet correct geconfigureerd.
