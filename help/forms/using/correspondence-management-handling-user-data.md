---
title: Correspondentenbeheer | Gebruikersgegevens verwerken
description: Meer informatie over Correspondence Management en het verwerken van gebruikersgegevens in een Adobe Experience Manager Forms-omgeving.
topic-tags: grdp
products: SG_EXPERIENCEMANAGER/6.5/FORMS
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Form Data Model
exl-id: 57385e88-9a3d-4d89-986b-9f254aa722ca
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 0%

---

# Correspondentenbeheer | Gebruikersgegevens verwerken {#correspondence-management-handling-user-data}

Met AEM Forms Correspondence Management kunt u veilige en persoonlijke klantcorrespondentie maken, beheren en stroomlijnen. Het verstrekt een intuïtieve gebruikersinterface voor bedrijfsgebruikers om correspondentie tot stand te brengen gebruikend vooraf goedgekeurde inhoudsblokken en media elementen. Voor meer informatie over het creëren van correspondentie, zie [&#x200B; Correspondentie &#x200B;](/help/forms/using/create-correspondence.md) creëren.

Wanneer een zakelijke gebruiker of een agent een correspondentie opslaat als concept of deze verzendt, wordt een brievenexemplaar opgeslagen in de AEM-opslagplaats. De brieveninstantie omvat brievengegevens en meta-gegevens.

>[!NOTE]
>
>In AEM 6.5 Forms is het correspondentiebeheer niet beschikbaar in de verpakking. Als u een upgrade uitvoert vanaf een eerdere AEM Forms-versie, installeert u het compatibiliteitspakket en migreert u de middelen voor correspondentiebeheer om deze te blijven gebruiken in AEM 6.5 Forms. Voor meer informatie, zie [&#x200B; pakket van de Verenigbaarheid &#x200B;](/help/forms/using/compatibility-package.md).

## Gebruikersgegevens en gegevensopslag {#data}

In het Correspondentiebeheer worden gegevens voor concept en verzonden brieven alleen opgeslagen in de AEM-opslagplaats als de publicatie-instantie is geconfigureerd voor het beheren van brievenexemplaren. Voor meer informatie over de configuratie, zie [&#x200B; de configuratieeigenschappen van het Beheer van de Correspondentie &#x200B;](/help/forms/using/cm-configuration-properties.md).

Afhankelijk van de persistentie van de gegevensopslag die voor uw plaatsing van AEM wordt gevormd, worden de concepten en de voorgelegde brievengegevens opgeslagen bij de volgende plaatsen.

<table>
 <tbody>
  <tr>
   <td><p><strong>Type persistentie</strong></p> </td>
   <td><p><strong>Gegevensopslag</strong></p> </td>
   <td><p><strong>Locatie</strong></p> </td>
  </tr>
  <tr>
   <td><p>Standaard</p> </td>
   <td><p>AEM-opslagplaats voor publicatie-instantie en auteurinstanties opgegeven in omgekeerde replicatieconfiguratie</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code><br /> </p> </td>
  </tr>
  <tr>
   <td><p>Extern</p> </td>
   <td><p>AEM-opslagplaats van de externe verwerkingsauteurinstantie</p> </td>
   <td><p><code>/content/apps/cm/letterInstances/[yyyy]/[mm]/[dd]/[node-id]/[letter-instance-name]/</code></p> </td>
  </tr>
 </tbody>
</table>

Op de hierboven vermelde locatie in de AEM-opslagplaats:

* `[yyyy]/[mm]/[dd]` is de nodestructuur die op de datum wordt gebaseerd waarop de brieveninstantie werd gecreeerd
* `[node-id]` is de id die is toegewezen aan de map met de letter
* `[letter-instance-name]` is de naam die is opgegeven bij het opslaan of verzenden van een letter

Onder de [ brief-instantie-naam ] knoop, wordt de volgende knoopstructuur gecreeerd en het gegeven voor elke brieveninstantie wordt opgeslagen in de bewaarplaats van AEM:

| Knooppunt | Beschrijving |
|---|---|
| `extendedProperties` | Hiermee worden eigenschappen van metagegevens van de letterinstantie opgeslagen. |
| `dataXML` | Hiermee wordt een downloadbaar dataXML-bestand opgeslagen dat de correspondentiegegevens in binaire indeling bevat. |
| `processedXDP` | Bevat de details van de XDP-sjabloon die wordt gebruikt om de verzonden letter te maken. Dit knooppunt wordt alleen gemaakt voor verzonden correspondentie. |
| `submittedLetter` | Slaat de voorgelegde brievengegevens in downloadbaar binair formaat op. Dit knooppunt wordt alleen gemaakt voor verzonden correspondentie. |

## Gebruikersgegevens openen en verwijderen {#access-and-delete-user-data}

U kunt tot ontwerp en voorgelegde brievengegevens in de gevormde gegevensopslag toegang hebben, en indien nodig, het schrappen.

### Gebruikersgegevens openen {#access-user-data}

Correspondentiebeheer biedt API&#39;s die u kunt gebruiken om concepten en verzonden brieven te zoeken en te openen. Met behulp van de API&#39;s kunt u lettervarianten zoeken en openen met de id van het lettertype of de gebruiker die de correspondentie heeft opgeslagen of verzonden. Voor meer informatie, zie [&#x200B; APIs om tot brieveninstanties &#x200B;](/help/forms/using/cm-apis-to-access-letter-instances.md) toegang te hebben.

U kunt ook naar de letter-instantie in de AEM-opslagplaats navigeren met CRXDE Lite. Zie [&#x200B; gegevens van de Gebruiker en gegevensopslag &#x200B;](/help/forms/using/correspondence-management-handling-user-data.md#data) voor informatie over opgeslagen gegevens en bewaarplaats.

### Gebruikersgegevens verwijderen {#delete-user-data}

Als u een letterinstantie wilt zoeken die de gegevens van een bepaalde gebruiker bevat, kunt u:

* Gebruik correspondentiebeheer-API&#39;s als de naam van een letter of de gebruiker die het concept heeft opgeslagen of de correspondentie heeft verzonden, bekend is
* Gebruik de zoekopdracht in de AEM-opslagplaats met persoonlijk identificeerbare gegevens, zoals de e-mailadres of naam, om het knooppunt te vinden waar de gegevens zijn opgeslagen

Als u gebruikersgegevens uit concepten en verzonden correspondentie volledig wilt verwijderen uit AEM-systemen, moet u het knooppunt voor de letter handmatig verwijderen uit alle toepasselijke AEM-instanties.
