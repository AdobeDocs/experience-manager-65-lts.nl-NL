---
title: WebSphere-toepassingsserver starten en stoppen
description: Bij verschillende procedures moet u de instantie van WebSphere stoppen of starten waar u AEM-formulierproducten wilt implementeren. In dit document wordt beschreven hoe u de WebSphere-toepassingsserver start en stopt.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/maintaining_the_application_server
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 20cd6efb-edcf-4c87-b0f5-bdec5a0f6280
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '180'
ht-degree: 0%

---

# WebSphere-toepassingsserver starten en stoppen {#starting-and-stopping-websphere-application-server}

Bij verschillende procedures moet u de instantie van WebSphere stoppen of starten waar u AEM-formulierproducten wilt implementeren. Als u niet zeker bent of de toepassingsserver is begonnen, kunt u het statuut van de Server van de Toepassing eerst bekijken WebSphere.

## De status van WebSphere Application Server weergeven {#view-the-status-of-websphere-application-server}

1. Ga vanaf een opdrachtprompt naar de map `[appserver root]/bin` .
1. Ga het volgende bevel in, dat *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Vensters) `serverStatus.bat`*server_name*
   * (Linux, UNIX) ./ `serverStatus.sh`*server_name*

## WebSphere-toepassingsserver starten {#start-websphere-application-server}

1. Ga vanaf een opdrachtprompt naar de map `[appserver root]/bin` .
1. Ga het volgende bevel in, dat *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Vensters) `startServer.bat`*server_name*
   * (Linux, UNIX) ./ `startServer.sh`*server_name*

## WebSphere-toepassingsserver stoppen {#stop-websphere-application-server}

1. Ga vanaf een opdrachtprompt naar de map `[appserver root]/bin` .
1. Ga het volgende bevel in, dat *server_name* met de naam van uw Server van de Toepassing WebSphere vervangt:

   * (Vensters) `stopServer.bat`*server_name*
   * (Linux, UNIX) ./ `stopServer.sh`*server_name*
