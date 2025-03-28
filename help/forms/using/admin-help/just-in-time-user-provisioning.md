---
title: Just-in-Time gebruikersprovisioning
description: Gebruik just-in-time levering om gebruikers aan het Beheer van de Gebruiker toe te voegen na succesvolle authentificatie en dynamisch relevante rollen en groepen aan de nieuwe gebruiker toe te wijzen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/setting_up_and_organizing_users
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a7c566f0-ec89-4e98-b31d-e3f23f7e3524
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '575'
ht-degree: 0%

---

# Just-in-Time gebruikersprovisioning {#just-in-time-user-provisioning}

AEM-formulieren ondersteunen de just-in-time levering van gebruikers die nog niet in Gebruikersbeheer bestaan. Met just-in-time levering, worden de gebruikers automatisch toegevoegd aan het Beheer van de Gebruiker nadat hun geloofsbrieven met succes worden verklaard. Daarnaast worden relevante rollen en groepen dynamisch toegewezen aan de nieuwe gebruiker.

## De behoefte aan just-in-time gebruikerslevering {#need-for-just-in-time-user-provisioning}

Zo werkt traditionele verificatie:

1. Wanneer een gebruiker zich probeert aan te melden bij AEM-formulieren, geeft het Gebruikersbeheer de gebruikersgegevens opeenvolgend door aan alle beschikbare verificatieproviders. (De login geloofsbrieven omvatten een gebruikersbenaming/wachtwoordcombinatie, kaartje Kerberos, handtekening PKCS7, etc.)
1. De verificatieprovider valideert de referenties.
1. De authentificatieleverancier controleert dan of de gebruiker in het gegevensbestand van het Beheer van de Gebruiker bestaat. De volgende resultaten zijn mogelijk:

   **bestaat:** als de gebruiker huidig en ontgrendeld is, keert het Beheer van de Gebruiker authentificatiesucces terug. Als de gebruiker echter niet actief is of is vergrendeld, retourneert het Gebruikersbeheer een verificatiefout.

   **bestaat niet:** het Beheer van de Gebruiker keert authentificatiefout terug.

   **ongeldig:** de terugkeert van het Beheer van de Gebruiker authentificatiefout.

1. Het resultaat dat door de authentificatieleverancier is teruggekeerd wordt geëvalueerd. Als de verificatieprovider het succes van de verificatie heeft geretourneerd, mag de gebruiker zich aanmelden. Anders, controleert het Beheer van de Gebruiker met de volgende authentificatieleverancier (stappen 2-3).
1. Verificatiefout wordt geretourneerd als geen enkele verificatieprovider de gebruikersgegevens valideert.

Wanneer just-in-time levering wordt uitgevoerd, wordt een nieuwe gebruiker dynamisch gecreeerd in het Beheer van de Gebruiker als één van de authentificatieleveranciers de geloofsbrieven van de gebruiker bevestigt. (Na stap 3 van de traditionele authenticatieprocedure hierboven.)

## Implementeer just-in-time gebruikersprovisioning {#implement-just-in-time-user-provisioning}

### API&#39;s voor instelbare provisioning {#apis-for-just-in-time-provisioning}

AEM-formulieren bieden de volgende API&#39;s voor just-in-time provisioning:

```java
package com.adobe.idp.um.spi.authentication  ;
publ ic interface IdentityCreator {
/**
* Tries  to create a user with the  in formation  provided in the <code>UserProvisioningBO</code> object.
* If the user is successfully created, a valid AuthResponse is returned along with the information using which the user was created.
* It is the responsibility of the IdentityCreator to set the User obje ct  in the cre dential map with th e  ke y  <code>UMA u thenticationUtil.authenticatedUserKey</code>
* The credentials are available in the <code>UserProvisioningBO</code> object in the 'credentials' property.
* If the IdentityCreator is unable to create a user due to any reason, it returns <code>null</code>
* @param userBO An object of <code>com.adobe. i dp.um . spi.authenti c ationUserProvisioningBO</code>
* @return */public AuthResponse create(UserProvisioningBO userBO);
/**
* Returns the name of the IdentityCreator which will be registered in preferences.
* This name is used to associate the IdentityProvider with the Auth Provider Configuration in the domain.
* @return The name of the Identity Creator which is recognized in Configuration.
*/
public String getName();
}
package com.adobe.idp.um.spi.authentication;
import com.adobe.idp.um.api.infomodel.User;
public interface AssignmentProvider {
/**
* Tries to assign roles or permissions or group memberships to users created via Just-in-time provisioning.
* @param user The User created via the Just-in-time provisioning process.
* @return a Boolean flag indicating whether the assignment was successful or not.
*/
public Boolean assign(User user);
/**
* Returns the name of the AssignmentProvider through which it is registered under preferences.
* This name is used to associate the AssignmentProvider with the Auth Provider Configuration in the domain.
* @return The name of the AssignmentProvider which is recognized in Configuration.
*/public String getName();
}
```

### Overwegingen bij het creëren van een just-in-tijd-toegelaten domein {#considerations-while-creating-a-just-in-time-enabled-domain}

* Zorg tijdens het maken van een aangepaste `IdentityCreator` voor een hybride domein dat er een dummywachtwoord is opgegeven voor de lokale gebruiker. Laat dit wachtwoordveld niet leeg.
* Aanbeveling: gebruik `DomainSpecificAuthentication` om gebruikersgegevens voor een bepaald domein te valideren.

### Een alleen-in-tijd-geschikt domein maken {#create-a-just-in-time-enabled-domain}

1. Schrijf een DSC die APIs in &quot;APIs voor just-in-time levering&quot;sectie uitvoert.
1. Implementeer de DSC op de Forms-server.
1. Creeer een just-in-time-Toegelaten domein:

   * Klik in Beheerconsole op Instellingen > Gebruikersbeheer > Domeinbeheer > Nieuw Enterprise-domein.
   * Configureer het domein en selecteer Enable Just In Time Provisioning. <!--Fix broken link (See Setting up and managing domains).-->
   * Voeg verificatieproviders toe. Tijdens het toevoegen van authentificatieleveranciers, op het Nieuwe scherm van de Authentificatie, selecteer een geregistreerde Maker van de Identiteit en een Leverancier van de Toewijzing.

1. Sla het nieuwe domein op.

## Achter de schermen {#behind-the-scenes}

Stel dat een gebruiker zich probeert aan te melden bij AEM-formulieren en dat een verificatieprovider de gebruikersgegevens accepteert. Als de gebruiker nog niet bestaat in de gebruikersbeheerdatabase, mislukt de identiteitscontrole voor de gebruiker. AEM-formulieren voeren nu de volgende handelingen uit:

1. Maak een `UserProvisioningBO` -object met de verificatiegegevens en plaats dit in een referentie-overzicht.
1. Haal op basis van domeininformatie die door `UserProvisioningBO` wordt geretourneerd de geregistreerde `IdentityCreator` en `AssignmentProvider` voor het domein op en activeer deze.
1. Roep `IdentityCreator` aan. Als het resultaat `AuthResponse` is, extraheert u `UserInfo` van de referentie-kaart. Geef deze door aan de `AssignmentProvider` voor groep-/roltoewijzing en eventuele andere naverwerkingen nadat de gebruiker is gemaakt.
1. Als de gebruiker met succes is gemaakt, retourneert u de aanmeldingspoging van de gebruiker als geslaagd.
1. Voor hybride domeinen, trek gebruikersinformatie van de authentificatiegegevens die aan de authentificatieleverancier worden verstrekt. Als deze gegevens correct zijn opgehaald, maakt u de gebruiker ter plekke.

>[!NOTE]
>
>De just-in-time inrichtingsfunctie wordt geleverd met een standaardimplementatie van `IdentityCreator` die u kunt gebruiken om dynamisch gebruikers te maken. De gebruikers worden gecreeerd met de informatie verbonden aan de folders in het domein.
