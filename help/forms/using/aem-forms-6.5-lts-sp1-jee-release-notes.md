---
title: De Nota's van de versie voor  [!DNL Adobe Experience Manager]  6.5 LTS SP1
description: Vind versieinformatie, wat nieuw is, installeer hoe-te, en een gedetailleerde veranderingslijst voor  [!DNL Adobe Experience Manager]  6.5 LTS SP1
solution: Experience Manager
feature: Release Information
role: User,Admin,Developer
exl-id: 811fccbc-6f63-4309-93c8-13b7ace07925
source-git-commit: c13c6c3d5511a5355570e999e378e4bdf0d7a88f
workflow-type: tm+mt
source-wordcount: '566'
ht-degree: 0%

---


# Adobe Experience Manager (AEM) Forms 6.5 LTS SP1 in Opmerkingen bij de release JEE

## Gegevens vrijgeven

| **Product** | Adobe Experience Manager Forms |
| -------------------- | ------------------------------------ |
| **Versie** | 6,5 LTS SP1 |
| **Type** | Long-Term Support Service Pack (JEE) |
| **Categorie van de Versie** | Upgradeversie |
| **Download URL** | Softwaredistributie |

## Wat is inbegrepen in [!DNL Experience Manager] 6.5 LTS SP1 {#what-is-included-in-aem-65ltssp1}

Adobe Experience Manager (AEM) Forms **6.5 LTS SP1 op JEE** levert nieuwe eigenschappen, zeer klant-gevraagde platformupdates, en algemene insectenmoeilijke situaties, met een sterke nadruk op productstabiliteit en steun op lange termijn.

## Wat is inbegrepen in AEM Forms 6.5 LTS SP1

### &#x200B;1. Updates voor Java-ondersteuning

Er is ondersteuning voor nieuwere Java-versies geïntroduceerd:

* **Java™ 17**
* **Java™ 21**

### &#x200B;2. Updates voor toepassingsserverondersteuning

#### Ondersteuning voor JBoss EAP 8

* De steun voor **JBoss EAP 8** is toegevoegd.
* Het erfenis **PicketBox** veiligheidskader is verwijderd.
* **op elytron-Gebaseerde credentieopslag** wordt nu gesteund voor veilig credentiebeheer.

##### Configuration: Credential Store (gebaseerd op Elytron)

AEM Forms op JBoss EAP 8 gebruikt Elytron voor het beheren van beveiligde referenties. Klanten moeten een op Elytron gebaseerde Credential Store configureren om ervoor te zorgen dat de server correct wordt gestart en dat de database wordt beveiligd.

Voor configuratiedetails, verwijs naar de installatie en configuratiegids.

### &#x200B;3. Wijzigingen in platform en compatibiliteit

#### Ondersteuning voor servlet-specificaties

* Steun voor **Specificatie 5+ van Servlet**
* Gebaseerd op **Jakarta EE 9** naleving

#### Migratievereiste voor naamruimte

* Jakarta EE 9 introduceert een naamruimtewijziging van `javax.*` in `jakarta.*`
* Alle **douane DSCs** moet aan `jakarta.*` namespace worden gemigreerd
* AEM Forms 6.5 LTS SP1 steunt **slechts Jakarta EE 9+-Gebaseerde toepassingsservers**

Voor meer informatie, zie **Migratie van javax aan jakarta Namespace**.

## Upgrade

Voor gedetailleerde verbeteringsinstructies, zie de [ Gids van de Verbetering voor AEM Forms 6.5 LTS SP1 op JEE ](https://experienceleague.adobe.com/en/docs/experience-manager-65-lts/content/forms/upgrade-aem-forms/upgrade)

## Installatie

Voor installatiestappen en eerste vereisten, verwijs naar de **Gids van de Installatie voor AEM Forms 6.5 LTS SP1 (JEE)**.

## Ondersteunde platforms

Voor de volledige lijst van gesteunde platforms, werkende systemen, gegevensbestanden, en toepassingsservers, zie:

**Gesteunde Matrijs van Platforms - AEM Forms 6.5 LTS SP1 (JEE)**

## Verouderde en verwijderde functies

* De steun voor **RDBMK** voor de bewaarplaats van CRX is persistentie verwijderd.
* Voor gegroepeerde milieu&#39;s, **slechts wordt MongoMK** gesteund voor bewaarplaatspersistentie.

## Migratie van javax naar jakarta-naamruimte

### Migratie van `javax` naar `jakarta` naamruimte

Beginnend met **AEM Forms 6.5 LTS SP1**, slechts toepassingsservers die **Servlet API 5/6 van Jakarta uitvoeren** worden gesteund. Met **Jakarta EE 9 en recenter**, overgangen alle APIs van `javax.{}` namespace aan `jakarta.`.

Dientengevolge, **alle douaneDSCs moet `jakarta` gebruiken namespace**. De componenten van de douane die gebruikend `javax.{}` worden gebouwd APIs zijn **niet compatibel** met de gesteunde toepassingsservers.

### Migratieopties voor aangepaste DSC&#39;s

U kunt bestaande aangepaste DSC&#39;s migreren op een van de volgende manieren:

#### Optie 1: Migratie van Source-code (aanbevolen)

* Alle instructies voor importeren van `javax.{}` naar `jakarta.` bijwerken
* De aangepaste DSC-projecten opnieuw samenstellen en opnieuw compileren
* Implementeer de bijgewerkte componenten opnieuw op de toepassingsserver

**Voordelen:**

* Zorgt voor compatibiliteit op lange termijn met Jakarta EE 9+
* Het meest geschikt voor actief onderhouden projecten

#### Optie 2: Binaire migratie met Eclipse Transformer

* Gebruik het **hulpmiddel van de Transformator van de Verduistering** om gecompileerde binaire getallen (`.jar`, `.war`) van `javax` in `jakarta` om te zetten
* Er zijn geen wijzigingen in de broncode of opnieuw compileren vereist
* Implementeer de getransformeerde binaire bestanden opnieuw op de toepassingsserver

>[!NOTE]
>
> De binaire transformatie wordt uitgevoerd op het **bytecodeniveau**.

Voorbeeldimporttoewijzingen

Hieronder volgen algemene voorbeelden van naamruimtewijzigingen die tijdens de migratie zijn vereist:

Voor (javax)    Na (jakarta)
javax.servlet.*    jakarta.servlet.*
javax.servlet.http.*    jakarta.servlet.http.*

### Voorbeeldimporttoewijzingen

In de volgende tabel worden de algemene naamruimtewijzigingen weergegeven die zijn vereist voor het migreren van `javax` naar `jakarta` :

| Voor (`javax`) | Na (`jakarta`) |
| ---------------------- | ------------------------ |
| `javax.servlet.*` | `jakarta.servlet.*` |
| `javax.servlet.http.*` | `jakarta.servlet.http.*` |

Gebruik deze toewijzingen als referentie bij het bijwerken van aangepaste DSC-broncode of het valideren van getransformeerde binaire bestanden.

