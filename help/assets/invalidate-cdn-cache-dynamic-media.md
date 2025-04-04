---
title: De cache van het netwerk voor inhoudslevering ongeldig maken via Dynamic Media
description: Maak uw CDN (Content Delivery Network) caching inhoud ongeldig zodat u snel elementen kunt bijwerken die door Dynamic Media worden geleverd, in plaats van te wachten op het verlopen van de cache.
contentOwner: Rick Brough
products: SG_EXPERIENCEMANAGER/6.5.6/ASSETS
topic-tags: dynamic-media
content-type: reference
role: User, Admin
feature: CDN Cache
solution: Experience Manager, Experience Manager Assets
exl-id: bce11a49-bbbe-4dda-8144-7f135bb666d9
source-git-commit: 2e0cbe62754866d31de69547f9af1f2f63930f2c
workflow-type: tm+mt
source-wordcount: '1191'
ht-degree: 0%

---

# De CDN-cache ongeldig maken via Dynamic Media {#invalidating-cdn-cache-for-dm-assets}

De dynamische activa van Media worden in het voorgeheugen ondergebracht door CDN (het Netwerk van de Levering van de Inhoud) voor snelle levering aan uw klanten. Wanneer u echter updates van deze elementen uitvoert, wilt u dat deze wijzigingen onmiddellijk op uw website van kracht worden. Door de CDN-cache te wissen of ongeldig te maken, kunt u snel elementen bijwerken die door Dynamic Media worden geleverd. In plaats van te wachten op het verlopen van het geheime voorgeheugen gebruikend een waarde van TTL (Tijd aan Levend) (gebrek is tien uren), kunt u een verzoek van binnen Dynamische Media verzenden om het geheime voorgeheugen te hebben verlopen binnen notulen.


**om uw CDN caching inhoud voor Dynamische activa van Media ongeldig te maken:**

*Deel 1 van 2: Creërend een malplaatje van de Invalidatie CDN*

1. Navigeer naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** .

   ![ eigenschap van de Bevestiging CDN ](/help/assets/assets-dm/cdn-invalidation-template2.png)

1. Voer op de pagina **[!UICONTROL CDN Invalidation template]** op basis van uw scenario een van de volgende opties uit:

   | Scenario | Optie |
   | --- | --- |
   | Ik heb in het verleden al een CDN-validatiesjabloon gemaakt met Dynamic Media Classic. | Het tekstveld **[!UICONTROL Create Template]** wordt vooraf gevuld met uw sjabloongegevens. In dat geval kunt u de sjabloon bewerken of doorgaan met de volgende stap. |
   | Ik moet een sjabloon maken. Wat ga ik binnen? | Op het **[!UICONTROL Create Template]** tekstgebied, ga een beeld URL (met inbegrip van beeldvoorinstellingen of bepalingen) die `<ID>` van verwijzingen voorzien, in plaats van een specifieke beeldidentiteitskaart zoals in het volgende voorbeeld:<br>`https://my.publishserver.com/is/image/company_name/<ID>?$product$`<br> als het malplaatje enkel `<ID>` bevat, dan vult de Dynamische Media `https://<publishserver_name>/is/image/<company_name>/<ID>` in waar `<publishserver_name>` de naam van uw Publish Server is die in Algemene Montages in Dynamic Media Classic wordt bepaald. `<company_name>` is de naam van de hoofdmap van uw bedrijf die aan deze Experience Manager-instantie is gekoppeld. `<ID>` is de geselecteerde elementen via de elementenkiezer die ongeldig moeten worden gemaakt.<br> Om het even welke vooraf instelt/modifiers post `<ID>` wordt gekopieerd aangezien-is in de definitie URL.<br> slechts beelden - dat wil zeggen, `/is/image` - kunnen worden auto gevormd gebaseerd op het malplaatje.<br> Voor `/is/content/`, produceert het toevoegen van activa zoals video&#39;s of PDFs gebruikend de activa plukker geen automatisch URLs. In plaats daarvan, moet u dergelijke activa of in het malplaatje van de Invalidatie CDN specificeren, of u kunt URL aan dergelijke activa in *Deel 2 van 2 manueel toevoegen: Het plaatsen van CDN de opties van de Invalidatie*.<br>**Voorbeelden:**<br> In dit eerste voorbeeld, bevat het ongeldigingsmalplaatje `<ID>` samen met activa URL die `/is/content` hebben. Bijvoorbeeld `http://my.publishserver.com:8080/is/content/dms7snapshot/<ID>` . Dynamische media vormen de URL op basis van dit pad, waarbij `<ID>` de elementen is die zijn geselecteerd via de elementenkiezer die u ongeldig wilt maken.<br> In dit tweede voorbeeld, bevat het validatiesjabloon de volledige URL van het element dat in uw wegeigenschappen met `/is/content` wordt gebruikt (niet afhankelijk van de elementenkiezer). Bijvoorbeeld `http://my.publishserver.com:8080/is/content/dms7snapshot/backpack` , waarbij rugzak de element-id is.<br> formaten van Activa die in Dynamische Media worden gesteund zijn geschikt voor ongeldigverklaring. De dossiertypes van activa die *niet* voor CDN ongeldig worden gesteund omvatten PostScript®, Encapsulated PostScript®, Adobe Illustrator, Adobe InDesign, Microsoft® Powerpoint, Microsoft® Excel, Microsoft® Word, en Rich Text Format.<br><br>・ Wanneer u de sjabloon maakt, maar zorg ervoor dat u de syntaxis en typos goed in de gaten houdt. Dynamische media voert geen sjabloonvalidatie uit.<br>・ Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.<br>・ Specificeer URLs voor beeld slimme gewassen of in dit malplaatje van de Invalidatie CDN, of in het **[!UICONTROL Add URL]** tekstgebied in *Deel 2: Plaatsende opties van de Invalidatie CDN.*<br>・ Elk item in een CDN-validatiesjabloon moet op een aparte regel staan.<br>・ Het volgende voorbeeld van de CDN-validatiesjabloon is alleen bedoeld als demonstratie. |

   ![ CDN Sjabloon voor validatie - creeer ](/help/assets/assets-dm/cdn-invalidation-template-create-2.png)

   >[!NOTE]
   >
   >Met de CDN-validatiesjabloon kunt u maximaal 2500 tekens opslaan.

1. Selecteer **[!UICONTROL Save]** in de rechterbovenhoek van de pagina **[!UICONTROL CDN Invalidation template]** en selecteer vervolgens **[!UICONTROL OK]** . <br>
   *Deel 2 van 2: De plaatsende opties van de Invalidatie CDN*
   <br>

1. Selecteer in Experience Manager as a Cloud Service **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** .

   ![ eigenschap van de Bevestiging CDN ](/help/assets/assets-dm/cdn-invalidation-path2.png)

1. Selecteer op de pagina **[!UICONTROL CDN Invalidation - Add Details]** de elementen voor CDN-validatie.

   ![ CDN ongeldig - voeg Details ](/help/assets/assets-dm/cdn-invalidation-add-details-2.png) toe

   >[!NOTE]
   >
   >Als u besluit om de opties **[!UICONTROL Invalidate asset associated image presets in CDN]** *en* **[!UICONTROL Invalidate based on template]** ongecontroleerd te verlaten, dan wordt de basis URL van de geselecteerde activa gevormd voor ongeldigverklaring. Gebruik deze optie-indeling alleen voor afbeeldingen.


   | Optie | Beschrijving |
   | --- | --- |
   | **[!UICONTROL Invalidate asset associated image presets in CDN]** | (Optioneel) Wanneer u deze optie inschakelt, worden geselecteerde elementen en alle bijbehorende URL&#39;s met voorinstellingen voor afbeeldingen automatisch samengesteld voor cachevalidatie.<br> Assets en hun bijbehorende vooraf bepaalde vooraf bepaalde URLs worden auto gevormd voor ongeldigverklaring. Deze optie werkt alleen voor afbeeldingselementen. |
   | **[!UICONTROL Invalidation based on template]** | (Optioneel) Schakel deze optie in als u alleen de gedefinieerde sjabloon voor URL-formatie wilt gebruiken. |
   | **[!UICONTROL Add Assets]** | Gebruik de elementkiezer om elementen te selecteren die u ongeldig wilt maken. U kunt gepubliceerde of niet-gepubliceerde elementen selecteren.<br> Caching bij CDN is op URL-Gebaseerd, niet op activa-gebaseerd. Daarom is het noodzakelijk dat u op de hoogte bent van de volledige URL&#39;s die op uw website staan. Nadat u deze URL&#39;s hebt bepaald, kunt u ze aan de sjabloon toevoegen. Vervolgens kunt u deze elementen selecteren en toevoegen en de URL&#39;s in één stap ongeldig maken. <br> Gebruik deze optie met **[!UICONTROL Invalidate asset associated image presets in CDN]**, of **[!UICONTROL Invalidation based on template]**, of allebei. |
   | **[!UICONTROL Add URL]** | Voeg handmatig volledige URL-paden toe aan dynamische media-elementen waarvan u de CDN-cache wilt ongeldig maken. Gebruik deze optie als u geen Malplaatje van de Invalidatie CDN in ***Deel 1 van 2 creeerde: Creërend een malplaatje van de Invalidatie CDN***, en slechts een paar activa hebben om ongeldig te maken.<br>**Belangrijk:** Elke URL die u toevoegt moet op zijn eigen lijn zijn.<br> u kunt tot 1000 URLs in een bepaalde tijd ongeldig maken. Als het aantal URL&#39;s in het tekstveld **[!UICONTROL Add URL]** groter is dan 1000, kunt u **[!UICONTROL Next]** niet selecteren. In dergelijke gevallen moet u **[!UICONTROL X]** rechts van een geselecteerd element selecteren of een handmatig toegevoegde URL selecteren om het element uit de lijst met validaties te verwijderen.<br> specificeer URLs voor beeld slimme gewassen of in het malplaatje van de Invalidatie CDN, of in dit **[!UICONTROL Add URL]** tekstgebied. |

1. Selecteer **[!UICONTROL Next]** in de rechterbovenhoek van de pagina.
1. Op de pagina **[!UICONTROL CDN Invalidation - Confirm]** ziet u in de keuzelijst **[!UICONTROL URLs]** een lijst met een of meer URL&#39;s die zijn gegenereerd op basis van de CDN-validatiesjabloon die u eerder hebt gemaakt en de elementen die u zojuist hebt toegevoegd.

   Als u bijvoorbeeld het voorbeeld voor de CDN-validatiesjabloon gebruikt dat eerder in de stappen werd weergegeven, kunt u een enkel element met de naam `spinset` toevoegen. Wanneer u naar **[!UICONTROL Tools]** > **[!UICONTROL Assets]** > **[!UICONTROL CDN Invalidation]** navigeert, resulteert dit in de volgende vijf gegenereerde URL&#39;s in de gebruikersinterface van **[!UICONTROL CDN Invalidation - Confirm]** :

   ![ CDN ongeldig - bevestigt ](/help/assets/assets-dm/cdn-invalidation-confirm-2.png)

   Indien nodig, uitgezochte **X** rechts van een URL om het van het invalidatieproces te schrappen.

1. Selecteer **[!UICONTROL Submit]** in de rechterbovenhoek van de pagina om het CDN-validatieproces te starten.

## CDN-validatiefouten oplossen

In alle gevallen wordt de gehele batch voor ongeldigmaking verwerkt of is de hele batch mislukt.

| Fout | Toelichting |
| --- | --- |
| *Slaagde er niet in om URLs voor geselecteerde activa terug te winnen.* | Komt voor als om het even welke volgende scenario&#39;s worden voldaan:<br> - een Dynamische configuratie van Media wordt niet gevonden.<br> - Er is een uitzondering bij het ophalen van een servicegebruiker via welke de configuratie Dynamische media wordt gelezen.<br> - De publicatieserver of de hoofdmap van het bedrijf die wordt gebruikt om de URL&#39;s te maken, ontbreekt in de configuratie Dynamische media. |
| *sommige URLs wordt niet correct bepaald. Juist en opnieuw verzenden.* | Komt voor als IPS CDN geheim voorgeheugenbevestiging API een fout terugkeert die URL naar een verschillend bedrijf verwijst. Of als de URL niet geldig is volgens de validatie die wordt uitgevoerd door de IPS `cdnCacheInvalidation` -API. |
| *Slaagde er niet in om CDN geheime voorgeheugen ongeldig te maken.* | Komt voor als het CDN verzoek van de geheim voorgeheugenongeldigverklaring om een andere reden ontbreekt. |
| *Geen URLs inging om ongeldig te worden gemaakt.* | Vindt plaats als de pagina **[!UICONTROL CDN Invalidation - Confirm]** geen URL&#39;s bevat en u **[!UICONTROL Submit]** selecteert. |


<!--  | I do not want to create a template. | Near the upper-right corner of the page, select **[!UICONTROL Cancel]**, then continue with ***Part 2: Working with CDN Invalidation***. Note that while you are not required to create a template to use CDN Invalidation, Adobe recommends that you create one, especially if you have numerous assets that you need to update immediately, on a regular basis. The template is used at the time you set CDN invalidation options. | -->
