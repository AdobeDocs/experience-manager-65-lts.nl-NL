---
title: Behandeling van GDPR-verzoeken voor de Adobe Experience Manager Foundation
description: Behandeling van GDPR-verzoeken voor de Adobe Experience Manager Foundation
contentOwner: sarchiz
solution: Experience Manager, Experience Manager Sites
feature: Administering
role: Admin
exl-id: 9445c51a-eb0b-41d0-9a23-ed75a5cd879e
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '453'
ht-degree: 0%

---

# Behandeling van GDPR-verzoeken voor de Adobe Experience Manager (AEM) Foundation{#handling-gdpr-requests-for-the-aem-foundation}

>[!IMPORTANT]
>
>GDPR wordt in de onderstaande secties als voorbeeld gebruikt, maar de betreffende details zijn van toepassing op alle regels inzake gegevensbescherming en privacy, zoals GDPR, CCPA, enzovoort.

## AEM Foundation GDPR-ondersteuning {#aem-foundation-gdpr-support}

Op het niveau van de Stichting van AEM, zijn de Persoonlijke Gegevens die wordt opgeslagen het Profiel van de Gebruiker. Daarom richt de informatie in dit artikel hoofdzakelijk hoe te om tot gebruikersprofielen toegang te hebben en te schrappen, om de Toegang te richten GDPR, en verzoeken te schrappen.

## Een gebruikersprofiel openen {#accessing-a-user-profile}

### Handmatige stappen {#manual-steps}

1. Open de gebruikersbeheerconsole door naar **[!UICONTROL Settings - Security - Users]** te bladeren of door rechtstreeks naar `https://<serveraddress>:<serverport>/libs/granite/security/content/useradmin.html` te bladeren

   ![ useradmin2 ](assets/useradmin2.png)

1. Zoek vervolgens naar de desbetreffende gebruiker door de naam in de zoekbalk boven aan de pagina te typen:

   ![ gebruikersonderzoek ](assets/usersearch.png)

1. Open ten slotte het gebruikersprofiel door erop te klikken en controleer het vervolgens onder de tab **[!UICONTROL Details]** .

   ![ userprofile_small ](assets/userprofile_small.png)

### HTTP-API {#http-api}

Zoals vermeld, verstrekt Adobe APIs voor de toegang tot van gebruikersgegevens, om automatisering te vergemakkelijken. Er zijn verschillende typen API&#39;s die u kunt gebruiken:

**UserProperties API**

```shell
curl -u user:password http://localhost:4502/libs/granite/security/search/profile.userproperties.json\?authId\=cavery
```

**het Verdelen API**

*het ontdekken van het gebruikershuis:*

```xml
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

*het Terugwinnen van gebruikersgegevens*

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile.-1.json'
```

```shell
curl -u user:password  'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profiles.-1.json'
```

## Een gebruiker uitschakelen en de bijbehorende profielen verwijderen {#disabling-a-user-and-deleting-the-associated-profiles}

### Gebruiker uitschakelen {#disable-user}

1. Open de console van het Beleid van de Gebruiker en onderzoek naar de gebruiker in kwestie, zoals hierboven beschreven.
1. Houd de muisaanwijzer boven de gebruiker en klik op het pictogram Selecteren. Het profiel wordt grijs weergegeven om aan te geven dat het is geselecteerd.

1. Druk op de knop Uitschakelen in het bovenste menu om de gebruiker uit te schakelen:

   ![ gebruikersdisable ](assets/userdisable.png)

1. Bevestig ten slotte de actie:

   ![ image2018-2-6_1-40-58 ](assets/image2018-2-6_1-40-58.png)

   De gebruikersinterface geeft aan dat de gebruiker is gedeactiveerd door de profielkaart te verslepen en er een vergrendeling aan toe te voegen:

   ![ gehandicapte gebruiker ](assets/disableduser.png)

### Gebruikersprofielgegevens verwijderen {#delete-user-profile-information}

1. Meld u aan bij CRXDE Lite en zoek vervolgens naar `[!UICONTROL userId]` :

   ![ image2018-2-6_1-57-11 ](assets/image2018-2-6_1-57-11.png)

1. Open het gebruikersknooppunt dat zich standaard onder `[!UICONTROL /home/users]` bevindt:

   ![ image2018-2-6_1-58-25 ](assets/image2018-2-6_1-58-25.png)

1. Verwijder profielknooppunten en alle onderliggende knooppunten. Afhankelijk van de AEM-versie zijn er twee indelingen voor de profielknooppunten:

   1. Het standaard privéprofiel onder `[!UICONTROL /profile]`
   1. `[!UICONTROL /profiles]` voor nieuwe profielen die zijn gemaakt met AEM 6.5.

   ![ image2018-2-6_2-0-4 ](assets/image2018-2-6_2-0-4.png)

### HTTP-API {#http-api-1}

In de volgende procedures wordt het opdrachtregelprogramma `curl` gebruikt om te tonen hoe u de gebruiker kunt uitschakelen met de profielen **[!UICONTROL cavery]** `userId` en delete `cavery` die beschikbaar zijn op de standaardlocatie.

* *het ontdekken van het gebruikershuis*

```shell
curl -g -u user:password 'http://localhost:4502/libs/granite/security/search/authorizables.json?query={"condition":[{"named":"cavery"}]}'
     {"authorizables":[{"type":"user","authorizableId_xss":"cavery","authorizableId":"cavery","name_xss":"Carlene Avery","name":"Carlene Avery","home":"/home/users/we-retail/DSCP-athB1NYLBXvdTuN"}],"total":1}
```

* *onbruikbaar makend de gebruiker*

Gebruikend de knoopweg van het huisbezit van de nuttige lading JSON die van het bovengenoemde bevel is teruggekeerd:

```shell
curl -X POST -u user:password -FdisableUser="describe the reasons for disabling this user (GDPR in this case)" 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN.rw.userprops.html'
```

* *het Schrappen van gebruikersprofielen*

Het gebruiken van de knoopweg van het huisbezit van de nuttige lading JSON die van het bevel van de rekeningsontdekking en het gekende uit de knoopplaatsen van het kaderprofiel is teruggekeerd:

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```

```shell
curl -X POST -u user:password -H "Accept: application/json,**/**;q=0.9" -d ':operation=delete' 'http://localhost:4502/home/users/we-retail/DSCP-athB1NYLBXvdTuN/profile'
```
