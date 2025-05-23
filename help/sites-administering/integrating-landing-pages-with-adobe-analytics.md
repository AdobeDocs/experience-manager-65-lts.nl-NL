---
title: Openingspagina's integreren met Adobe Analytics
description: Leer hoe u bestemmingspagina's kunt integreren met Adobe Analytics.
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: personalization
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: 24ab494d-4a11-408e-8dc0-de16508edfac
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '369'
ht-degree: 0%

---

# Openingspagina&#39;s integreren met Adobe Analytics{#integrating-landing-pages-with-adobe-analytics}

AEM heeft de het landen paginaoplossing met [ Adobe Analytics ](https://www.omniture.com/en/products/analytics/sitecatalyst) door de volgende vraag-aan-actie (CTA) componenten te gebruiken geïntegreerd:

1. Klikken door component
1. Grafische koppelingscomponent

Deze componenten maken bepaalde kenmerken beschikbaar die via Adobe Analytics-variabelen (Verkeer, Conversievariabelen) en succesgebeurtenissen kunnen worden toegewezen om informatie naar Adobe Analytics te verzenden.

## Vereisten {#prerequisites}

Adobe adviseert dat u door de [ bestaande integratie AEM-Adobe Analytics ](/help/sites-administering/adobeanalytics.md) gaat om te begrijpen hoe deze integratie werkt.

## Componenten beschikbaar voor toewijzing {#components-available-for-mapping}

In AEM, kan de **Vraag aan de componenten van de Actie** - **ClickThroughLink** en **GraphicalLink** - hier getoond in sidekick, aan de variabelen van Adobe Analytics worden in kaart gebracht.

![ chlimage_1-21 ](assets/chlimage_1-21a.jpeg)

### Onderdelen van bestemmingspagina aan Adobe Analytics toewijzen {#mapping-landing-page-components-to-adobe-analytics}

U kunt landingspaginacomponenten toewijzen aan Adobe Analytics:

1. Nadat u de Adobe Analytics-configuratie hebt gemaakt en een framework hebt gemaakt, selecteert u de gewenste rapportsuite in het keuzemenu. Hierdoor worden de Adobe Analytics-variabelen opgehaald en weergegeven in de zoekfunctie voor inhoud.
1. De belemmering en laat vallen Vraag aan de componenten van de Actie (CTA) van sidekick in het kaartingsgebied in het midden van de pagina, zoals aangewezen.

<table>
 <tbody>
  <tr>
   <td><strong>Componentnaam</strong></td>
   <td><strong>Kenmerken beschikbaar</strong></td>
   <td><strong>Betekenis van kenmerk</strong></td>
  </tr>
  <tr>
   <td><strong>CTA doorklikken via koppeling</strong></td>
   <td><i> eventdata.clickLinkLabel </i> <br /> </td>
   <td>Het label op de koppeling of de tekst van de koppeling </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i> eventdata.clickLinkTarget </i> <br /> </td>
   <td>Het doel waar u naartoe gaat wanneer u op de koppeling klikt </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i> eventdata.events.clickLinkClick </i> <br /> </td>
   <td>De gebeurtenis click </td>
  </tr>
  <tr>
   <td><strong>CTA Graphical Link</strong></td>
   <td><i> eventdata.clickroughImageLabel </i> <br /> </td>
   <td>De titel van de CTA-afbeelding </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i> eventdata.clickroughImageTarget </i> <br /> </td>
   <td>Het doel waar u naartoe gaat wanneer u op de afbeelding met een koppeling klikt</td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i> eventdata.clickroughImageAsset </i> <br /> </td>
   <td>Het pad naar het afbeeldingselement in de repository </td>
  </tr>
  <tr>
   <td><br type="_moz" /> </td>
   <td><i> eventdata.events.clickroughImageClick </i> <br /> </td>
   <td>De gebeurtenis click</td>
  </tr>
 </tbody>
</table>

1. Wijs deze belichte kenmerken toe aan alle Adobe Analytics-variabelen van de zoeker naar inhoud. Het framework is nu gebruiksklaar.
1. U kunt een het landen pagina of een bestaande het landen pagina met bestaande componenten van CTA nu tot stand brengen en **lusje van de Diensten van de Wolk van de 1&rbrace; in** Eigenschappen van de Pagina **van sidekick (in aanraking-geoptimaliseerde UI, selecteer** Open Eigenschappen **en klik** de Diensten van de Wolk **) en vorm het kader om met het landen pagina te gebruiken.** Selecteer het framework in de vervolgkeuzelijst.

   ![ chlimage_1-25 ](assets/chlimage_1-25a.png)

1. Nadat u het framework hebt geconfigureerd met de bestemmingspagina, kunt u nu de van instrumenten voorziene componenten gebruiken en worden eventuele klikken op CTA opgenomen in Adobe Analytics.
