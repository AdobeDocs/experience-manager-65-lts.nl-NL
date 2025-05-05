---
title: AEM - Commerce-integratie met Commerce integration framework - Veelgestelde vragen
description: AEM - Commerce-integratie met Commerce integration framework - Veelgestelde vragen
solution: Experience Manager,Commerce
feature: Commerce Integration Framework
role: Admin, Developer
exl-id: fd5f4836-ecac-407c-a82e-5f6b47718902
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '958'
ht-degree: 0%

---

# AEM - Commerce-integratie met Commerce integration framework - Veelgestelde vragen

## 1. Wordt CIF GraphQL alleen gebruikt voor handel of is het beschikbaar voor het opvragen van inhoud die is geschreven op het JCR van AEM&#39;s?

Adobe heeft de GraphQL API&#39;s van Adobe Commerce aangenomen als de officiële API voor de handel voor alle handelsgerelateerde gegevens. Daarom gebruikt AEM GraphQL om handelsgegevens met Adobe Commerce en met om het even welke handelmotor via I/O Runtime uit te wisselen. Deze GraphQL API is onafhankelijk van de AEM GraphQL API voor toegang tot Content Fragments.

## 2. Kunnen de activa van het Product (beelden) van AEM via Adobe Commerce worden opgeslagen en van verwijzingen voorzien? Hoe kunnen middelen van Dynamische Media worden verbruikt?

Er is geen officiële AEM Assets - Adobe Commerce-integratie beschikbaar. Er is een partnerschakelaar beschikbaar op de [ markt ](https://marketplace.magento.com/partner/bounteous_ecomm).

Als tussenoplossing kunt u ook productelementen (afbeeldingen) opslaan in AEM Assets, maar u moet de URL&#39;s van de middelen handmatig opslaan in Adobe Commerce. Dynamic Media maakt deel uit van AEM Assets en werkt op dezelfde manier.

## 3. Maakt het uit waar de handelsoplossing wordt ingezet? (Op prem of in de cloud)

Nee, het maakt niet uit waar uw handelsoplossing wordt geïmplementeerd. CIF en de AEM storefront werken ongeacht het implementatiemodel. Als de oplossing echter wordt geïmplementeerd met de aanbevolen E2E-referentiearchitectuur, kunnen E2E-tests worden uitgevoerd met prestatie-KPI&#39;s die een typisch bedrijfsklantprofiel vertegenwoordigen. Dit proces biedt aanvullende informatie die als benchmark kan worden gebruikt.

## 4. Hoe worden in AEM cataloguspagina&#39;s of productpagina&#39;s gemaakt? Hoe blijven ze in AEM?

Cataloguspagina&#39;s en productpagina&#39;s worden dynamisch in AEM gemaakt en in cache geplaatst op basis van algemene catalogussjablonen en productpaginasjablonen. Er worden geen product- of catalogusgegevens geïmporteerd en opgeslagen in AEM.

## 5. Wanneer u productgegevens in uw handelsoplossing bijwerkt, is dat een druk in real time aan AEM? Of is het een batchproces?

Met de CIF-add-on die met AEM wordt gebruikt, kunnen gegevens van de handelsoplossing naar AEM op aanvraag worden verzonden. Daarom is deze workflow geen realtime-push of batchproces wanneer uw handelsoplossing wordt bijgewerkt.

## 6. Welke catalogusgrootte wordt door AEM met CIF ondersteund?

De ondersteuning voor catalogusgrootte is afhankelijk van een aantal aanvullende aspecten die u in overweging moet nemen. Wat is de cacheverhouding van uw catalogusgegevens en -pagina&#39;s? Hoeveel gezamenlijke verzoeken verwacht u tijdens piekuren? Hoe scalable zijn APIs van uw handelsoplossingen?

## 7. Hoe speelt PIM in dit kader?

PIM-gegevens worden door GraphQL-verzoeken aan AEM en clients beschikbaar gesteld. De aanbeveling van Adobe is om PIM te integreren met de motor van de handel (Adobe Commerce of anderen) zodat PIM-gegevens dan van de motor van de handel kunnen worden teruggewonnen.

## 8. Plaats de prijsbepaling en andere gegevens ook in cache via Dispatcher. Vormt dat een veelvuldige uitdaging voor het ongeldig maken van cache?

Dynamische gegevens zoals prijs of voorraad worden niet in de cache opgeslagen op de Dispatcher. Dynamische gegevens worden via GraphQL API&#39;s rechtstreeks via de client-side opgehaald met webcomponenten. Alleen statische gegevens (zoals product- of categoriegegevens) worden in cache geplaatst op de Dispatcher. Als de productgegevens veranderen, is de geheim voorgeheugenongeldigverklaring nodig.

## 9. Hoe werkt cachevalidatie voor AEM Dispatcher met AEM en handel?

Adobe raadt aan om op TTL gebaseerde cachevalidatie in te stellen voor pagina&#39;s die in cache zijn geplaatst op de Dispatcher. Voor dynamische informatie zoals prijs of voorraad raadt Adobe aan om de datum op de client weer te geven. Voor meer informatie over op TTL-Gebaseerde geheim voorgeheugenbevestiging, zie [ AEM Dispatcher ](https://experienceleague.adobe.com/docs/experience-cloud-kcs/kbarticles/KA-17458.html?lang=nl-NL)

## 10. Is er een aanbeveling voor een uniforme zoekactie in AEM-inhoud met Commerce?

Er is een verwijzingsimplementatie voor productzoekopdrachten beschikbaar, maar er is geen uniforme zoekopdracht met inhoud. Deze eigenschap is klant-specifiek en beter opgelost op een project-specifiek niveau.

## 11. Hoe werkt Zoeken met AEM en handel met CIF?

CIF biedt componenten van zoekbalken en zoekresultaten. De component van de bar van het Onderzoek verzendt een verzoek van GraphQL met de onderzoekstermijn naar de handelsoplossing die dan een productlijst terugkeert die productnaam, prijs, SLUG, etc. omvat. De component van het Resultaat van het Onderzoek toont dan de onderzoeksresultaten in een galeriemening op een pagina van het onderzoeksresultaat die in AEM wordt gecreeerd. De zoekfunctie ondersteunt standaard zoeken in volledige tekst. Gebruik de sleutel SLUG/url om een verwijzing naar PDP te bouwen.

## 12. Hoe kunnen productgegevens in MSM&#39;s of vertalingen worden gebruikt?

Productgegevens zijn al vertaald in PIM of in Adobe Commerce. De integratie AEM - Adobe Commerce ondersteunt de verbinding met meerdere Adobe Commerce-winkels en -winkelweergaven. In een MSM-instelling wordt doorgaans één AEM-site gekoppeld aan één Adobe Commerce-winkelweergave.

## 13. Is er een manier om de productgegevens te verbeteren met commerciële tekst? Zo ja, waar is dat gebeurd? In AEM of in de handelsoplossing?

Adobe raadt aan om marketinggerelateerde gegevens en inhoud in AEM te beheren. Decoreer productgegevens van uw handelsoplossing met extra attributen gebruikend de Fragmenten van de Inhoud of creeer en verbind de Fragmenten van de Ervaring voor ongestructureerde inhoud met uw producten.

## 14. Hoe zorgt een bedrijf ervoor dat de PCI-standaard wordt nageleefd wanneer AEM voor de gehele presentatielaag wordt gebruikt?

Adobe raadt aan om onttrekkende betalingsmethoden te gebruiken. Het doen van dit zet de browser cliënt in directe communicatie met de betaalgatewayleverancier zodat Adobe geen kaarthouddatum, noch de handelsoplossingen houdt of overgaat. Deze benadering vereist slechts niveau 3 naleving PCI. Nochtans, zijn er extra dingen om als volledig PCI-Volgzaam te beschouwen zoals hoe de werknemers met het systeem en de gegevens in wisselwerking staan. Voor meer informatie over de naleving van Adobe Commerce PCI, zie [ naleving PCI ](https://business.adobe.com/products/magento/pci-compliance.html)

## 15. Als ik AEM- en Adobe Commerce-cloudversies gebruik, is deze gezamenlijke oplossing PCI-compatibel?

Ja, de zelfbeoordelingsvragenlijst D en de verklaring van naleving zijn op verzoek beschikbaar.

## 16. Hoe kan ik een proeflicentie voor I/O-runtime aanvragen?

Zie [ het Krijgen Toegang ](https://developer.adobe.com/runtime/docs/guides/overview/getting_access/) voor details van het verzoeken van een proefvergunning om I/O Runtime te gebruiken.
