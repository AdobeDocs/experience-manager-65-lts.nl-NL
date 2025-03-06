---
title: SAML-serviceleverinstellingen configureren
description: U kunt SAML-instellingen voor serviceproviders configureren, zodat gebruikers zich kunnen aanmelden en verifiëren voor AEM-formulieren via een opgegeven externe identiteitsprovider (IDP).
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 0f1b39e7-5de5-4b54-b622-61774ce839db
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '607'
ht-degree: 0%

---

# SAML-serviceleverinstellingen configureren{#configure-saml-service-provider-settings}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

SAML (Security Assertion Markup Language) is een van de opties die u kunt selecteren wanneer u een machtiging voor een onderneming of hybride domein configureert. SAML wordt hoofdzakelijk gebruikt om SSO over veelvoudige domeinen te steunen. Wanneer SAML is geconfigureerd als uw verificatieprovider, melden gebruikers zich aan en verifiëren ze zich bij AEM-formulieren via een opgegeven externe identiteitsprovider (IDP).

Voor een verklaring van SAML, zie [ Taal van de Prijsverhoging van de Bevestiging van de Veiligheid (SAML) V2.0 Technisch Overzicht ](https://docs.oasis-open.org/security/saml/Post2.0/sstc-saml-tech-overview-2.0.html).

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > SAML Service Provider Settings.
1. Typ in het vak Id van Service Provider een unieke id die u wilt gebruiken als id voor de implementatie van de AEM-formulierservice. U kunt deze unieke id ook opgeven bij het configureren van uw IDP (bijvoorbeeld `um.lc.com` .) U kunt ook de URL gebruiken die wordt gebruikt voor toegang tot AEM-formulieren (bijvoorbeeld `https://AEMformsserver` ).
1. Typ in het vak Basis-URL van serviceprovider de basis-URL voor uw Forms-server (bijvoorbeeld `https://AEMformsserver:8080` ).
1. (Optioneel) Als u wilt dat AEM-formulieren ondertekende verificatieaanvragen naar de IDP kunnen verzenden, voert u de volgende taken uit:

   * Gebruik Betrouwbaarheidsbeheer om een referentie in de PKCS #12-indeling te importeren, waarbij Referentie voor documenthandtekening is geselecteerd als Betrouwbaarheidswinkeltype. (Zie [ het Leiden lokale geloofsbrieven ](/help/forms/using/admin-help/local-credentials.md#managing-local-credentials).)
   * Selecteer in de lijst Referentietoets Service Provider de alias die u aan de referentie in Trust Store hebt toegewezen.
   * Klik op Exporteren als u de URL-inhoud in een bestand wilt opslaan en dat bestand vervolgens in uw IDP wilt importeren.

1. (Facultatief) in de lijst van het Beleid van de Naam van de Dienstverlener identiteitskaart, selecteer het naamformaat dat IDP gebruikt om de gebruiker in een bevestiging van SAML te identificeren. De opties zijn Niet opgegeven, E-mail, en Gekwalificeerde Naam van het Domein van Vensters.

   >[!NOTE]
   >
   >Naamnotaties zijn niet hoofdlettergevoelig.

1. (Optioneel) Selecteer Verificatieverzoek voor lokale gebruikers inschakelen. Als deze optie is geselecteerd, zien gebruikers twee koppelingen:

   * een koppeling naar de aanmeldingspagina van de externe SAML-identiteitsprovider, waar gebruikers die tot een Enterprise-domein behoren, zich kunnen verifiëren.
   * een koppeling naar de aanmeldingspagina voor AEM-formulieren, waar gebruikers die tot een lokaal domein behoren, zich kunnen verifiëren.

   Als deze optie niet is geselecteerd, worden gebruikers rechtstreeks doorgestuurd naar de aanmeldingspagina van de externe SAML-identiteitsprovider, waar gebruikers die tot een Enterprise-domein behoren, zich kunnen verifiëren.

1. (Optioneel) Selecteer Artefactbinding inschakelen om ondersteuning voor artefactbinding in te schakelen. Standaard wordt POST-binding gebruikt met SAML. Maar als u de Binding van Artefact hebt gevormd, selecteer deze optie. Als deze optie is geselecteerd, wordt de feitelijke gebruikersbewering niet doorgegeven via de Browser-aanvraag. In plaats daarvan, wordt een wijzer tot de bewering overgegaan en de bewering wordt teruggewonnen gebruikend een de dienstvraag van het achterste deel van het Web.
1. (Optioneel) Selecteer Enable Re-Direct Binding om SAML-bindingen te ondersteunen die omleidingen gebruiken.
1. (Optioneel) Geef in Aangepaste eigenschappen aanvullende eigenschappen op. De extra eigenschappen zijn name=value paren die door nieuwe lijnen worden gescheiden.

   * U kunt AEM-formulieren configureren om een SAML-bewering uit te geven voor een geldigheidsperiode die overeenkomt met de geldigheidsperiode van een bewering van derden. Als u de SAML-assertietime-out van derden wilt respecteren, voegt u de volgende regel toe in Aangepaste eigenschappen:

     `saml.sp.honour.idp.assertion.expiry=true`

   * Voeg het volgende douanebezit voor het gebruiken van RelayState toe om URL te bepalen waar de gebruiker na succesvolle authentificatie opnieuw zal worden gericht.

     `saml.sp.use.relaystate=true`

   * Voeg de volgende aangepaste eigenschap toe zodat u de URL voor de aangepaste Java™ Server Pages (JSP) kunt configureren, waarmee de geregistreerde lijst met identiteitsproviders wordt weergegeven. Als u geen aangepaste webtoepassing hebt geïmplementeerd, wordt de standaardpagina Gebruikersbeheer gebruikt om de lijst weer te geven.

   `saml.sp.discovery.url=/custom/custom.jsp`

1. Klik op Opslaan.
