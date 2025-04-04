---
title: Geef geloofsbrieven door gebruikend WS-veiligheidskopballen
description: Leer hoe u referenties doorgeeft met WS-beveiligingskoppen
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 558d9b27-8734-4da2-b498-5bb2361ac65b
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '215'
ht-degree: 0%

---

# Gegevens doorgeven met WS-beveiligingskoppen {#using-execute-script-service-aem-forms-jee-workbench}

Wanneer u een AEM Forms op JEE-service aanroept met behulp van webservices, kunt u WS-Security-headers gebruiken om verificatie-informatie voor de client door te geven die AEM Forms op JEE vereist. WS-Security definieert SOAP-extensies voor het implementeren van clientverificatie, vertrouwelijkheid van berichten en integriteit van berichten. Dientengevolge, kunt u AEM Forms op de diensten van JEE aanhalen wanneer AEM Forms op JEE als stand-alone server of binnen een gegroepeerde milieu wordt opgesteld.

Hoe u WS-Veiligheid kopballen tot AEM Forms op JEE overgaat hangt van of u de as-geproduceerde klassen van Java of een .NET cliëntassemblage gebruikt die de inheemse stapel van SOAP van de dienst verbruikt.

>[!NOTE]
>
>Als voorbeeld om de dienst aan te halen gebruikend WS-Veiligheid kopballen, codeert dit onderwerp een document van PDF met een wachtwoord door de dienst van de Encryptie aan te halen.

In dit document worden de volgende onderwerpen behandeld:

* Clientverificatie doorgeven met Java-klassen die door As zijn gegenereerd

* Het produceren van de bibliotheekdossiers van de As die worden vereist om de dienst van de Encryptie aan te halen

* De coderingsservice aanroepen met een WS-Security-header

* Het overgaan van cliëntauthentificatie gebruikend een .NET cliëntassemblage

* De coderingsservice aanroepen met een WS-Security-header


## Vereisten {#requirements}

Om dit document optimaal te benutten, hebt u een goed begrip nodig van de AEM Forms op JEE-software.

>[!MORELIKETHIS]
>
>* [ het overgaan geloofsbrieven gebruikend WS-Veiligheid kopballen ](assets/passing-credentials-using-ws-security-headers.pdf)
