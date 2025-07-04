---
title: Opstelling het project van Visual Studio en bouwt Windows app
description: Leer hoe te opstelling een project van Visual Studio om AEM Forms Windows mobiele apparatenapp te bouwen.
topic-tags: forms-app
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: c2e9200f-a4b7-46fc-9dde-425329e5365d
source-git-commit: b8576049fba41b3bec16046316938274a5046513
workflow-type: tm+mt
source-wordcount: '880'
ht-degree: 0%

---

# Opstelling het project van Visual Studio en bouwt Windows app{#set-up-the-visual-studio-project-and-build-the-windows-app}

AEM Forms biedt de volledige broncode van de AEM Forms-app. De bron bevat alle componenten om een toepassing van de douanewerkruimte te bouwen. Het broncodearchief, `adobe-lc-mobileworkspace-src-<version>.zip` is een deel van het `adobe-aemfd-forms-app-src-pkg-<version>.zip` pakket op de Distributie van de Software.

Voer de volgende stappen uit om de AEM Forms-toepassingsbron op te halen:

1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
1. In de sectie **[!UICONTROL Filters]** :
   1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
   2. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
1. Open [ Manager van het Pakket ](/help/sites-administering/package-manager.md) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

1. Als u het broncodearchief wilt downloaden, opent u `https://<server>:<port>/crx/de/content/forms/mobileapps/src/adobe-lc-mobileworkspace-src-<version>.zip` in uw browser.\
   Het bronpakket wordt gedownload op uw apparaat.

In de volgende afbeelding wordt de geëxtraheerde inhoud van de `adobe-lc-mobileworkspace-src-<version>.zip` weergegeven.

![ mws-content-1 ](assets/mws-content-1.png)

In de volgende afbeelding wordt de mapstructuur van de map `windows` in de map `src` weergegeven.

![ win-dir ](assets/win-dir.png)

## Het milieu instellen {#setting-up-the-environment}

Voor Windows-apparaten hebt u het volgende nodig:

* Microsoft Windows 8.1 of Windows 10
* Microsoft Visual Studio 2015
* Microsoft Visual Studio Tools for Apache Cordova

## Visual Studio Project instellen voor AEM Forms-app {#setting-up-visual-studio-project-for-aem-forms-app}

Voer de volgende stappen aan opstelling uit AEM Forms app project in Visual Studio.

1. Kopieer het archief van `adobe-lc-mobileworkspace-src-<version>.zip` naar de map van `%HOMEPATH%\Projects` in Windows 8.1 of Windows 10 met Visual Studio 2015 geïnstalleerd en geconfigureerd.
1. Extraheer het archief in de map `%HOMEPATH%\Projects\MobileWorkspace` .
1. Navigeer naar de map `%HOMEPATH%\Projects\MobileWorkspace\adobe-lc-mobileworkspace-src-[versionsrc]\windows` .
1. Open het `CordovaApp.sln` -bestand met Visual Studio 2015 en ga verder met het ontwikkelen van de AEM Forms-app.

## AEM Forms-app ontwikkelen {#build-aem-forms-app}

Voer de volgende stappen uit om AEM Forms-app te maken en te implementeren.

>[!NOTE]
>
>Gegevens die zijn opgeslagen in het Windows-bestandssysteem voor de AEM Forms-toepassing, worden niet gecodeerd. Het wordt geadviseerd dat u een derdehulpmiddel zoals de Encryptie van de Aandrijving van Windows BitLocker gebruikt om schijfgegevens te coderen.

1. In de StandaardToolbar van Visual Studio, uitgezochte **Versie** van drop-down voor bouwstijlwijze.

1. Selecteer Windows-AnyCPU, Windows-x64 of Windows-x86 op basis van uw platform. Windows-AnyCPU wordt aanbevolen.
1. In de Ontdekkingsreiziger van de Oplossing van Visual Studio, klik het project **CordovaApp.Windows** met de rechtermuisknop aan en selecteer **Opslag > Create AppPackages**.

   ![ createapppackages ](assets/createapppackages.png)

   De wizard App Packages maken wordt weergegeven.

   Het installatiebestand van CordovaApp.Windows_3.0.2.0_anycpu.appx wordt gemaakt in de map platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test.

   Als u de fout `Retarget to windows 8.1 required` ontmoet, klik de fout en in pop-up menu met de rechtermuisknop aan, uitgezochte **Winst aan Vensters 8.1**.

   ![ retarget-solution ](assets/retarget-solution.png)

1. In Create App Packages tovenaar, selecteer weer of niet wilt u uw app aan de venstersopslag uploaden en dan **daarna** klikken.

   ![ createapppackageswizard1 ](assets/createapppackageswizard1.png)

1. Breng de gewenste wijzigingen aan in de parameters, zoals de versie en uitvoerlocatie van de build van de app.

   ![ createapppackageswizard2 ](assets/createapppackageswizard2.png)

1. Nadat het project is gemaakt, kunt u de app installeren met:

   * Windows PowerShell
   * Visual Studio

   Voor het `.appx` -pakket moeten de volgende items zijn geïnstalleerd:

   1. WinJS-bibliotheek
   1. Zorg ervoor dat het pakket wordt geleverd met een zelfondertekend certificaat of een door een vertrouwde instantie ondertekend openbaar certificaat, zoals VeriSign.
   1. Licentie voor ontwikkelaars

   De map Platforms\windows\AppPackages\CordovaApp.Windows_3.0.2.0_anycpu_Test bevat de vier hoofdcomponenten ervan:

   1. `.appx` -bestand
   1. Certificaat (momenteel is het een zelfondertekend certificaat van Apache Cordova)
   1. Afhankelijkheidsmap
   1. PowerShell-bestand (.ps1-extensie)

## Het opstellen van een app die Vensters PowerShell gebruikt {#deploying-an-app-using-windows-powershell}

Er zijn twee manieren om de toepassing op een apparaat van Vensters te installeren.

### Door de ontwikkelaarslicentie aan te schaffen {#by-acquiring-the-developer-license}

1. Klik het dossier PowerShell met de rechtermuisknop aan ( `Add-AppDevPackage.ps1)`, en kies **Looppas met PowerShell**.

1. De opstelling zet u ertoe aan om een ontwikkelaarvergunning te krijgen. Gebruik Microsoft-accountgegevens om een ontwikkelaarslicentie te verkrijgen.\
   Deze licentie is 30 dagen geldig en u kunt deze gratis verlengen.
1. Wanneer u de ontwikkelaarslicentie aanschaft, wordt het zelfondertekende certificaat geïnstalleerd op het systeem en wordt de toepassing correct geïnstalleerd.

### Door apparaten in bedrijfsbezit te gebruiken {#by-using-enterprise-owned-devices}

Voor apparaten die eigendom zijn van een onderneming en die zijn aangesloten bij het domein van de onderneming, is het niet nodig een ontwikkelaarslicentie aan te schaffen.

Apparaten in bedrijfsbezit gebruiken Professional- en Enterprise-versies van Windows.

Microsoft raadt u aan een door een vertrouwde instantie uitgegeven openbaar certificaat, zoals VeriSign, te installeren.

De app implementeren:

* Zorg ervoor dat het apparaat wordt aangesloten bij het domein van de onderneming.
* Groepsbeleid instellen inschakelen.

**om het plaatsen van het groepsbeleid toe te laten:**

1. Voer `gpedit.msc` uit op uw apparaat.
1. Navigeer aan **Configuratie van de Computer > Administratieve Malplaatjes > de Component van Vensters > de Plaatsing van het Pakket van de Toepassing**.
1. Klik met de rechtermuisknop **Toestaan alle vertrouwde op apps om** te installeren.
1. Klik **uitgeven** en selecteren **Toegelaten**.

1. Klik **OK**.

Bewerk het Visual Studio-script dat PowerShell heeft gegenereerd om te voorkomen dat het ontwikkelaarslicentie verwerft.

Stel in het PowerShell-script de variabele in: `$NeedDeveloperLicense = $false` .

Voor apparaten die geen domeinverbinding hebben, is de sideladende sleutel van de productactivering vereist. U kunt deze aanschaffen bij een Windows-leverancier.

Voor Windows 8.1 Home Edition, is er geen groepsbeleid, wordt de onderneming zijladen niet toegestaan, en u kunt zich niet bij het met het ondernemingsdomein aansluiten. Implementeer de app op een Windows 8.1 Home Edition-apparaat met een ontwikkelaarslicentie.

Voor meer informatie, klik [ hier ](https://blogs.msdn.com/b/mvpawardprogram/archive/2014/03/24/side-loading-deployment-of-windows-store-apps-in-enterprises-step-by-step.aspx).

## Het opstellen van een app die Visual Studio gebruikt {#deploying-an-app-using-visual-studio}

Om app op Vensters te installeren gebruikend Visual Studio:

1. Sluit het apparaat aan met extern foutopsporingsprogramma.\
   Voor meer informatie, zie [ apps van de Opslag van Vensters van de Looppas op een verre machine ](https://docs.microsoft.com/en-us/visualstudio/debugger/run-windows-store-apps-on-a-remote-machine).

1. Met uw open app in Visual Studio, kies Vensters-x64, Vensters-x86, of Vensters-AnyCPU van de lijst van de Platforms van de Oplossing, en selecteer **Verre Machine**.
1. Uw app wordt geïmplementeerd op de externe computer.
