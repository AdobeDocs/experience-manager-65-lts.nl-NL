---
title: Starten en stoppen van services
description: Leer hoe u services die aan AEM Forms-modules en de toepassingsserver en -database zijn gekoppeld, kunt starten en stoppen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/managing_services
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a4ff69d2-a429-49b9-ba48-9dd56ccdf23e
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '311'
ht-degree: 0%

---

# Starten en stoppen van services {#starting-and-stopping-services}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Er zijn twee soorten services die deel uitmaken van AEM-formulieren:

* Services die de AEM-toepassingsserver en -database voor formulieren besturen.
* Services voor het besturen van AEM-formuliermodules

## De services die zijn gekoppeld aan AEM-formuliermodules starten of stoppen {#start-or-stop-the-services-associated-with-aem-forms-modules}

AEM-formuliermodules (bijvoorbeeld Forms, Rights Management, Output) werken als services. Het kan gebeuren dat u de services voor deze AEM-formuliermodules moet stoppen of starten. U moet bijvoorbeeld een AEM-formulierservice stoppen en opnieuw starten nadat u een instelling voor de service hebt gewijzigd.

>[!NOTE]
>
> U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. In beleidsconsole klik **de Diensten van 0} >** Toepassingen en de Diensten **>** Beheer van de Dienst **.**
1. Voor de pagina van het Beheer van de Dienst, selecteer de controledoos naast de dienst om te stoppen of te beginnen en Einde of Begin te klikken.

## De diensten van het begin of van het einde voor de toepassingsserver en gegevensbestand {#start-or-stop-services-for-the-application-server-and-database}

Een volledige implementatie van AEM-formulieren omvat een toepassingsserver en databaseservices:

* *`[application server]`* voor AEM-formulieren
* *`[database]`* voor AEM-formulieren

Op Vensters, zijn deze diensten toegankelijk door **Administratieve Hulpmiddelen** > **het paneel van de Diensten**. Als u bijvoorbeeld AEM-formulieren op JBoss hebt geïnstalleerd met de methode key turnkey, zijn de volgende services beschikbaar op uw systeem:

* JBoss voor Adobe Experience Manager-formulieren
* MySQL voor Adobe Experience Manager-formulieren

Start of stop deze services door deze te selecteren in de lijst in het deelvenster Services en vervolgens op de desbetreffende actieknop in het deelvenster te klikken.

Voer in UNIX® of Linux de volgende tekst in vanaf een opdrachtregel, waarbij *`[service name]`* de naam is van de service die u controleert:

```java
     ps -A | grep [service name]
```
