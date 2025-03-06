---
title: Watermerk toevoegen aan uw digitale elementen
description: Leer hoe u met de functie Watermerken een digitaal watermerk aan elementen kunt toevoegen.
contentOwner: AG
role: User, Admin
feature: Asset Management
hide: true
solution: Experience Manager, Experience Manager Assets
exl-id: 6c8b4ff5-28ac-4655-b310-4f0b0417bd63
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '278'
ht-degree: 1%

---

# Watermerk uw digitale elementen {#watermarking}

| Versie | Artikelkoppeling |
| -------- | ---------------------------- |
| AEM as a Cloud Service | [ klik hier ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/assets/manage/watermark-assets.html?lang=en) |
| AEM 6.5 | Dit artikel |

Met [!DNL Adobe Experience Manager Assets] kunt u een digitaal watermerk toevoegen aan elementen waarmee gebruikers de authenticiteit en de copyrighteigendom van de elementen kunnen controleren. [!DNL Experience Manager Assets] ondersteunt tekst die als watermerk moet worden gebruikt in PNG- en JPEG-bestanden.

Als u een watermerk op elementen wilt toepassen, voegt u de stap Watermerken toe in de [!UICONTROL DAM Update Asset] -workflow.

1. Open de gebruikersinterface van [!DNL Experience Manager] en ga naar **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .
1. Selecteer op de pagina **[!UICONTROL Workflow Models]** de **[!UICONTROL DAM Update Asset]** workflow en klik op **[!UICONTROL Edit]** .

1. Sleep vanuit het zijpaneel de stap **[!UICONTROL Add Watermark]** naar de [!UICONTROL DAM Update Asset] -workflow.

   ![ belemmering de [!UICONTROL Add Watermark] stap en voeg aan het [!UICONTROL DAM Update Asset] werkschema ](assets/add_watermark_step_aem_assets.png) toe

   *Figuur: Sleep de [!UICONTROL Add Watermark] stap en voeg aan het [!UICONTROL DAM Update Asset] werkschema toe.*

   >[!NOTE]
   >
   >Plaats de stap [!UICONTROL Add Watermark] ergens vóór de stap [!UICONTROL Process Thumbnail] .

1. Open de stap **[!UICONTROL Add Watermark]** om de eigenschappen ervan weer te geven.
1. Geef op het tabblad **[!UICONTROL Arguments]** geldige waarden op in de verschillende velden, zoals tekst, lettertype, grootte, kleur, positie, richting enzovoort. Klik op **[!UICONTROL Done]** om de wijzigingen te bevestigen.

   ![ Geef de argumenten op in de stap Watermerk toevoegen in [!DNL Assets]](assets/arguments_add_watermark_aem_assets.png)

   *Cijfer: Verstrek de argumenten in toevoegen watermerkstap in [!DNL Assets].*

1. Sla de **[!UICONTROL DAM Update Asset]** -workflow op met het watermerk.
1. Upload een voorbeeldelement vanuit de gebruikersinterface van [!DNL Assets] . Het watermerk wordt weergegeven met de tekengrootte, kleur, enzovoort, op de positie die u in de bovenstaande stappen hebt geconfigureerd.

Om de documenten van PDF programmatically of met dynamische informatie te voorzien, denk na gebruikend ](/help/forms/using/overview-aem-document-services.md) het aanbieden van de Diensten van het Document van 0} Experience Manager.[

## Tips en beperkingen {#tips-limitations}

* Alleen op tekst gebaseerde watermerken worden ondersteund. Afbeeldingen worden niet gebruikt als watermerken, ook al kunt u afbeeldingen uploaden wanneer u de [!UICONTROL Add Watermark Process] maakt.
* Alleen PNG- en JPEG-bestanden worden ondersteund voor een watermerk. Andere indelingen van elementen zijn niet van een watermerk voorzien.
