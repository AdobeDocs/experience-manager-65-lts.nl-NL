---
title: PDF Generator-configuratiebestanden importeren en exporteren
description: Leer hoe u PDF Generator-configuratiebestanden kunt importeren en exporteren.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_pdf_generator
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: PDF Generator
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 3bd5ef75-7e35-4398-a7a3-0178a9c06db0
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '384'
ht-degree: 0%

---

# PDF Generator-configuratiebestanden importeren en exporteren {#importing-and-exporting-pdf-generator-configuration-files}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Het configuratiebestand bevat de conversiegegevens van PDF Generator, zoals de PDF, het bestandstype en de beveiligingsinstellingen.

>[!NOTE]
>
>U kunt de time-out-instelling voor PDF Generator niet wijzigen door een aangepast native2pdfconfig.xml-bestand te importeren. De time-out-instelling in dat bestand is alleen ter informatie en geeft de huidige instelling weer in PDF Generator. Om onderbreking te veranderen die, zie &quot;het Plaatsen van de prestatieparameters van PDF Generator&quot;in [ plaatst die en de vormen van AEM opstelt ](https://www.adobe.com/go/learn_aemforms_installJBoss_63).

## Het huidige configuratiebestand exporteren {#export-your-current-configuration-file}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Als u de instellingen wilt exporteren, selecteert u de gewenste optie:

   * Selecteer Volledige configuratie downloaden om alle benoemde instellingen te exporteren.
   * Als u slechts één Adobe PDF-instelling, beveiligingsinstelling of bestandstype-instelling wilt exporteren, selecteert u Minimale configuratie downloaden.

     Als u een minimale configuratie exporteert, selecteert u de instellingen voor Adobe PDF, beveiliging en bestandstype die u wilt exporteren.

1. Klik op Downloaden en sla het XML-bestand op de gewenste locatie op.

## Een configuratiebestand importeren {#import-a-configuration-file}

>[!NOTE]
>
>Uw systeem wordt opnieuw geconfigureerd op basis van de gegevens in het geïmporteerde bestand.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren.
1. Om de dossierplaats in het vakje van het Dossier van de Configuratie te specificeren, doorbladert de klik en selecteert het dossier, en klikt dan **de Invoer**.

## Alle lagen in AutoCAD-bestanden converteren {#convert-all-layers-within-autocad-files}

PDF Generator converteert standaard alleen de standaardlaag AutoCAD-bestanden naar PDF in plaats van alle lagen in het bestand. Volg deze procedure om alle lagen om te zetten.

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Export Configuration.
1. Selecteer Volledige configuratie downloaden en klik op Downloaden.
1. Open het gedownloade bestand in een teksteditor en voeg de tekst toe onder de tag `AutoCAD` in de tag `PDFMaker` `convertAllPages="true"` .
1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Een bestaand configuratiebestand importeren, geef het bijgewerkte bestand op en klik op Importeren.

   Alle lagen worden omgezet in AutoCAD-bestanden die met het gewijzigde configuratiebestand worden omgezet.

## De configuratie herstellen naar de oorspronkelijke instellingen die bij PDF Generator zijn geïnstalleerd {#reset-your-configuration-to-the-original-settings-installed-with-pdf-generator}

1. Klik in de beheerconsole op Services > PDF Generator > Configuration Files > Import Configuration.
1. Selecteer Standaardinstellingen configuratie herstellen en klik op Importeren.
