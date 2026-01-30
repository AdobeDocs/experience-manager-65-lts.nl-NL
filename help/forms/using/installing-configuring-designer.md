---
title: Designer installeren en configureren
description: Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met Workbench. Leer hoe u een zelfstandige Designer installeert.
role: Admin, User, Developer
feature: Forms Designer,Designer
solution: Experience Manager, Experience Manager Forms
exl-id: 526bbc59-62c3-4e6d-a938-e368d07fe6b0
source-git-commit: eb6f6b994fdd3b2b01e77700d2deb7bd2830ac8f
workflow-type: tm+mt
source-wordcount: '801'
ht-degree: 0%

---

# Designer installeren en configureren{#installing-and-configuring-designer}

## Voorwaarden {#pre-requisites}

+++ Voor 64-bits AEM Forms Designer (aanbevolen)

* Installeer een versie met 64 bits van [ Visuele C++ 2019 Redistributable (x64) ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.

+++

+++ Voor 32-bits AEM Forms Designer

* Installeer een versie met 32 bits van [ Visuele C++ 2019 Redistributable (x64) ](https://learn.microsoft.com/en-us/cpp/windows/latest-supported-vc-redist?view=msvc-170). Zorg ervoor dat de eerder vermelde herdistribueerbare runtimepakketten zijn geïnstalleerd voordat u de installatie start.
* Een gebruiker met beheerdersrechten om AEM Forms Designer te installeren of verwijderen.

+++

>[!NOTE]
>
>* De 64-bits versie van de Designer werd geïntroduceerd met AEM 6.5 Forms Service Pack 19 (6.5.19.0).
>* De versie met 32 bits van Designer wordt afgekeurd sinds de versie van [ AEM Forms Service Pack 21 (6.5.21.0) ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases).
> * De ondersteunde platformen voor Forms Designer worden uitgelijnd met de door AEM Forms ondersteunde platforms. Over de gesteunde platforms voor Forms Designer leren, [ klik hier ](/help/sites-deploying/technical-requirements.md)

Voor meer informatie betreffende installatie van Forms Designer, bezoek [ vaak gestelde vragen ](#fandq).

## AEM Forms Designer installeren {#install-designer}

Designer is beschikbaar als zelfstandig installatieprogramma en is ook gebundeld met WorkBench. Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Verwijder de vorige versie van AEM Forms Designer als deze al is geïnstalleerd.
1. Download op basis van uw vereisten de 64-bits AEM Forms Designer (aanbevolen) of de 32-bits AEM Forms Designer.

   >[!NOTE]
   > 
   >* 32-bits Forms Designer zal volgens de planning worden vervangen door de AEM 6.5 Forms Service Packs 20 (6.5.20.0)-release. Adobe raadt u aan een upgrade uit te voeren naar de 64-bits Forms Designer.
   >* 64-bits Forms Designer is alleen beschikbaar voor AEM 6.5 Forms Service Packs 19 (6.5.19.0) of hoger.
   >* Adobe Experience Manager 6.5 Forms Service Pack 15 (6.5.15.0) vanaf Forms Designer versie omvat ook de versie Service Pack. Voor Service Pack 15 is het versienummer bijvoorbeeld 6.5.15.20221112.1.0. In dit voorbeeld, is 6.5.15 de versie van Service Pack.

1. Start het installatieprogramma van AEM Forms Designer door te dubbelklikken op setup.exe.
1. Ga verder en geef uw gegevens en het serienummer op het Personalization-scherm op.

   >[!NOTE]
   >
   >* Verkrijg uw Forms Designer vergunningssleutel van de [ Adobe Vergunnende Website ](https://licensing.adobe.com/).

1. Als u de licentieovereenkomst accepteert, klikt u op Volgende om door te gaan.
1. (Optioneel) Wijzig het standaardinstallatiepad als u Designer op een door u gekozen locatie wilt installeren. Klik op Volgende.
1. Klik op Vorige om voorkeuren te wijzigen. Klik op Installeren om Designer te installeren.
1. Klik op Voltooien als de installatie is voltooid.

U kunt de AEM Forms Designer ook via de opdrachtregel installeren in de passieve of stille modus.

* Passieve opdrachtregelinstallatie: in het installatieprogramma wordt een voortgangsbalk weergegeven die aangeeft dat de installatie wordt uitgevoerd, maar dat er geen aanwijzingen of foutberichten worden weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /passive SERIALNUMBER=****-****-****-****-****-****
```

* Stille opdrachtregelinstallatie: het installatieprogramma voert de installatie uit zonder een gebruikersinterface weer te geven. Er worden geen aanwijzingen, berichten of dialoogvensters weergegeven. Nadat de installatie is gestart, kunt u de installatie niet annuleren.

```shell
msiexec /i "<absolute path>\Designer.msi" /quiet SERIALNUMBER=****-****-****-****-****-****
```

## AEM Forms Designer bijwerken {#update-forms-designer}

Er zijn twee gevallen bij het bijwerken van de nieuwste versie van AEM Forms Designer 6.5.16.0 :

* **Geval 1**: Wanneer de gebruiker de versie van AEM Forms Designer vroeger dan 6.5.15.0 heeft.
* **Geval 2**: Wanneer de gebruiker 6.5.15.0 versie van AEM Forms Designer heeft.

+++**wanneer de gebruiker de versie van AEM Forms Designer vroeger dan 6.5.15.0 heeft.**

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Alvorens **AEM Forms Designer6.5.16.0** te installeren, moeten de gebruikers om het even welke vorige versies verwijderen.
1. De download en installeert [ AEM Forms Designer 6.5.15.0 ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) van de Pagina van de Versies van de Vorm van AEM.
1. Na succesvolle installatie van **AEM Forms Designer6.5.15.0**, download en installeer [ AEM Forms Designer 6.5.16.0 ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#) door op het gedownloade installatiedossier tweemaal te klikken.

+++

+++**wanneer de gebruiker 6.5.15.0 versie van AEM Forms Designer** heeft

Voer de volgende stappen uit als u een zelfstandig installatieprogramma voor AEM Forms Designer gebruikt:

1. Download de recentste versie van AEM Forms Designer van het [ Portaal van de Distributie van de Software ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases#).
1. Installeer de nieuwste versie van AEM Forms Designer door te dubbelklikken op het gedownloade installatiebestand.

+++

## Veelgestelde vragen {#fandq}

* **kan een gebruiker direct bevorderen of met 64 bits Designer installeren?**
   * Ja, gebruikers kunnen rechtstreeks een upgrade uitvoeren of 64-bits Designer installeren. Om te bevorderen, installeer [ SP19 ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/cq650/servicepack/fd/Designer-Patch/sp19_x64/aemforms_designer_6_5_0_wwe_win.zip) volledige installateur van Designer en pas de verdere de flardversie van Designer over het toe.

     >[!NOTE]
     > Voordat u een upgrade uitvoert naar 64-bits Designer, moet u eerst de 32-bits Designer verwijderen als deze bestaat.

* **kunnen de gebruikers zowel met 32 bits als met 64 bits geïnstalleerd op hun systeem houden?**
   * Nee. Een 32-bits en 64-bits installatie werkt niet op dezelfde computer. Gebruikers kunnen een 32-bits Designer of een 64-bits Designer hebben.

* **hoe controleert u als een gebruiker met 64 bits Designer of met 32 bits Designer is?**
   * Er zijn twee manieren om de Forms Designer-versie te controleren:

      1. Open Designer.
      1. Klik **Hulp** > **Ongeveer Designer** om de versie van Designer en bittheidsinformatie te bekijken.
Bijvoorbeeld, beëindigt het versiekoord met **64 beetje**, zoals gezien in het volgende voorbeeld:
         `6.5.21.20240522.1.161 | 64 bit`
      1. Open Designer en linksboven ziet u een brandpictogram dat 64-bits informatie met de productnaam bevat.
