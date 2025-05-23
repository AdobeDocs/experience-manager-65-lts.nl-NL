---
title: client- en serveropties configureren
description: Leer hoe u de diverse cliënt en serveropties, zoals de montages van de serverconfiguratie, de rollen van de documentveiligheid, en gebeurtenis controle kunt vormen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/working_with_document_security
products: SG_EXPERIENCEMANAGER/6.5/FORMS
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 72c31f40-d1b0-47ae-bdeb-e9b92c3d27e1
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '10278'
ht-degree: 0%

---

# De beveiligingsserver voor het document configureren {#configure-the-document-security-server}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Serverconfiguratie.
1. Configureer de instellingen en klik op OK.

## Serverconfiguratie-instellingen {#server-configuration-settings}

**Basis URL:** de veiligheid URL van het basisdocument, die de servernaam en de haven bevatten. Aan de basis toegevoegde informatie maakt verbinding-URL&#39;s. Bijvoorbeeld: /edc/Main.do wordt toegevoegd om toegang te krijgen tot de webpagina&#39;s. Gebruikers reageren via deze URL ook op uitnodigingen voor externe gebruikersregistratie.

Als u IPv6 gebruikt, ga de Basis URL als computernaam of DNS naam in. Als u een numeriek IP adres gebruikt, zal Acrobat er niet in slagen om beleid beschermde dossiers te openen. Gebruik ook HTTP Secure (HTTPS) URL voor uw server.

>[!NOTE]
>
>De basis-URL is ingesloten in bestanden die met een beleid zijn beveiligd. Clienttoepassingen gebruiken de basis-URL om weer verbinding te maken met de server. Beveiligde bestanden blijven de basis-URL bevatten, zelfs als deze later wordt gewijzigd. Als u de basis-URL wijzigt, moeten de configuratiegegevens voor alle verbindende clients worden bijgewerkt.

**Standaard Off-line Periode van de Verhuur:** De standaardlengte van tijd dat een gebruiker een beschermd document offline kan gebruiken. Deze instelling bepaalt de aanvankelijke waarde van de instelling voor de automatisch offline leaseperiode wanneer u een beleid maakt. (Zie Beleid maken en bewerken.) Wanneer de huurperiode verloopt, moet de ontvanger het document opnieuw synchroniseren om het te blijven gebruiken.

Voor een bespreking van hoe de off-line huur en synchronisatie werken, zie [ Primer bij het vormen van off-line huur en synchronisatie ](https://blogs.adobe.com/security/2009/05/primer_on_configuring_offline.html).

**Standaard Off-line Periode van de Synchronisatie:** De maximumtijd om het even welk document kan offline van worden gebruikt wanneer het aanvankelijk beschermd is.

**Time-out van de Zitting van de Cliënt:** de tijdsduur, in notulen, waarna de documentveiligheid losmaakt als een gebruiker die door een cliënttoepassing het programma wordt geopend niet met documentveiligheid interactie aangaat.

**staat de Anonieme Toegang van Gebruikers toe:** selecteer deze optie om de capaciteit toe te laten om gedeeld en persoonlijk beleid tot stand te brengen dat anonieme gebruikers toestaan om beleid-beschermde documenten te openen. (Gebruikers die geen accounts hebben, hebben wel toegang tot het document, maar kunnen zich niet aanmelden voor documentbeveiliging of andere documenten die met een beleid zijn beveiligd.)

**maak Toegang tot Versie 7 Clients onbruikbaar:** specificeert of de gebruikers Acrobat of Reader 7.0 kunnen gebruiken om met de server te verbinden. Als deze optie is geselecteerd, moeten gebruikers Acrobat of Reader 8.0 en hoger gebruiken om de beveiligingsbewerkingen van documenten in PDF-documenten te voltooien. Als het beleid vereist dat Acrobat of Reader 8.0 en later in verklaarde wijze in werking stellen wanneer het openen van beleid-beschermde documenten, zou u toegang tot Acrobat of Reader 7 moeten onbruikbaar maken. (Zie Documentmachtigingen opgeven voor gebruikers en groepen.)

**staat off-line toegang per document toe** selecteer deze optie om off-line toegang per document te specificeren. Als deze instelling is ingeschakeld, heeft de gebruiker alleen offline toegang tot de documenten die de gebruiker minstens één keer online heeft geopend.

**staat de Authentificatie van het Wachtwoord van de Gebruikersnaam toe:** selecteer deze optie om cliënttoepassingen toe te laten om gebruikersnaam/wachtwoordauthentificatie te gebruiken wanneer het verbinden met de server.

**staat Authentificatie Kerberos toe:** selecteer deze optie om cliënttoepassingen toe te laten om authentificatie te gebruiken Kerberos wanneer het verbinden met de server.

**staat de Authentificatie van het Certificaat van de Cliënt toe:** selecteer deze optie om cliënttoepassingen toe te laten om certificaatauthentificatie te gebruiken wanneer het verbinden met de server.

**staat Uitgebreide Authentificatie** Uitgebreide Uitgebreide authentificatie toe om uitgebreide authentificatie toe te laten en dan Uitgebreide het Plaatsen URL van de Authentificatie in te gaan.

Als u deze optie selecteert, kunnen clienttoepassingen uitgebreide verificatie gebruiken. Uitgebreide verificatie biedt aangepaste verificatieprocessen en verschillende verificatieopties die op de AEM Forms-server zijn geconfigureerd. Gebruikers kunnen nu bijvoorbeeld de op SAML gebaseerde verificatie ervaren in plaats van de gebruikersnaam/het wachtwoord voor AEM-formulieren, vanuit Acrobat en Reader Client. Door gebrek, bevat het Openen URL *localhost* als servernaam. Vervang de servernaam door een volledig gekwalificeerde hostnaam. De hostnaam in de bestemmings-URL wordt automatisch ingevuld vanaf de basis-URL als uitgebreide verificatie nog niet is ingeschakeld. Zie [ de uitgebreide authentificatieleverancier ](configuring-client-server-options.md#add-the-extended-authentication-provider) toevoegen.

***nota &#x200B;**: Uitgebreide authentificatie wordt gesteund op Apple Mac OS X met versie 11.0.6 van Adobe Acrobat en hierboven.*

**VoorkeurBreedte van de Controle van HTML voor Uitgebreide Authentificatie** specificeert de breedte van de uitgebreide authentificatiedialoog die in Acrobat voor het ingaan van gebruikersgeloofsbrieven opent.

**Voorkeur HTML Control Height voor Uitgebreide Authentificatie** specificeert de hoogte van de uitgebreide authentificatiedialoog die in Acrobat voor het ingaan van gebruikersgeloofsbrieven opent.

***nota &#x200B;**: De grenzen van de breedte en de hoogte voor dit dialoogvakje zijn als volgt:*
Breedte: minimaal = 400, maximaal = 900

Hoogte: minimaal = 450; maximaal = 800

**laat de Credentiële Caching van de Cliënt toe:** selecteer deze optie om gebruikers toe te staan om hun geloofsbrieven (gebruikersnaam en wachtwoord) in het voorgeheugen onder te brengen. Wanneer de gebruikersgegevens in het cachegeheugen worden opgeslagen, hoeven ze niet telkens hun gegevens in te voeren wanneer ze een document openen of op de knop Vernieuwen op de pagina Beveiligingsbeleid beheren in Adobe Acrobat klikken. U kunt het aantal dagen opgeven voordat gebruikers hun gegevens opnieuw moeten opgeven. Als u het aantal dagen instelt op 0, kunnen referenties voor onbepaalde tijd in het cachegeheugen worden opgeslagen.

## Gebruikers en beheerders voor documentbeveiliging configureren {#configuring-document-security-users-and-administrators}

### Documentbeveiligingsrollen toewijzen aan beheerders {#assigning-document-security-roles-to-administrators}

Uw AEM-formulieromgeving bevat een of meer beheerdergebruikers die de juiste rechten hebben voor het maken van gebruikers en groepen. Als uw organisatie documentbeveiliging gebruikt, moet ten minste één beheerder ook het recht krijgen om uitgenodigde en lokale gebruikers te beheren.

De beheerders moeten de rol van de Gebruiker van de beleidsconsole ook hebben om tot beleidsconsole toegang te hebben. (Zie [ Creërend en vormend rollen ](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).)

### Zichtbare gebruikers en groepen configureren {#configuring-visible-users-and-groups}

Om gebruikers en groepen in geselecteerde domeinen tijdens de onderzoeken van de beleidsgebruiker te bekijken, moet een superbeheerder of beheerder van de beleidsreeks domeinen (die in Beheer van de Gebruiker worden gecreeerd) aan de zichtbare gebruiker en de groepslijst voor elke beleidsreeks selecteren en toevoegen.

De zichtbare gebruiker en de groepslijst zijn zichtbaar aan de coördinator van de beleidsreeks en gebruikt om te beperken welke domeinen de eindgebruiker kan doorbladeren wanneer het kiezen van gebruikers of groepen om aan beleid toe te voegen. Als deze taak niet wordt uitgevoerd, zal de coördinator van de beleidsreeks geen gebruikers of groepen vinden om aan het beleid toe te voegen. Er kunnen voor elke beleidsset meerdere beleidssetcoördinatoren zijn.

1. Nadat u de AEM-formulieromgeving hebt geïnstalleerd en geconfigureerd met documentbeveiliging, stelt u alle relevante domeinen in Gebruikersbeheer in. <!-- Fix broken link (See Setting up and managing domains) -->

   ***nota &#x200B;**: Creërend domeinen moet worden gedaan alvorens om het even welk beleid kan worden gecreeerd.*

1. Klik in de beheerconsole op Services > Documentbeheer > Beleid en klik vervolgens op het tabblad Beleidssets.
1. Selecteer Globale beleidsset en klik op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.
1. Navigeer naar Services > Documentbeveiliging > Configuratie > Mijn beleid en klik op het tabblad Zichtbare gebruikers en groepen.
1. Klik op Domein(s) toevoegen en voeg desgewenst bestaande domeinen toe.

## De uitgebreide verificatieprovider toevoegen {#add-the-extended-authentication-provider}

AEM-formulieren bieden een voorbeeldconfiguratie die u kunt aanpassen aan uw omgeving. Voer de volgende stappen uit:

>[!NOTE]
>
>Uitgebreide verificatie wordt ondersteund op Apple Mac OS X met Adobe Acrobat versie 11.0.6 en hoger.

1. Vraag het WAR-voorbeeldbestand aan om dit te implementeren. Raadpleeg de installatiegids die geschikt is voor uw toepassingsserver.
1. Zorg ervoor dat de Forms-server een volledig gekwalificeerde naam heeft in plaats van IP-adressen als de basis-URL en dat het een HTTPS-URL is. Zie [ de configuratiemontages van de Server ](configuring-client-server-options.md#server-configuration-settings).
1. Schakel Uitgebreide verificatie in vanaf de pagina Serverconfiguratie. Zie [ de configuratiemontages van de Server ](configuring-client-server-options.md#server-configuration-settings).
1. Voeg de vereiste URL&#39;s voor omleiding naar SSO toe in het configuratiebestand voor gebruikersbeheer. Zie [ SSO omleiden URLs voor uitgebreide authentificatie ](configuring-client-server-options.md#add-sso-redirect-urls-for-extended-authentication) toevoegen.

### URL&#39;s voor doorsturen naar SSO toevoegen voor uitgebreide verificatie {#add-sso-redirect-urls-for-extended-authentication}

Als uitgebreide verificatie is ingeschakeld, krijgen gebruikers die een met beleid beveiligd document openen in Acrobat XI of Reader XI een dialoogvenster voor verificatie. In dit dialoogvenster wordt de HTML-pagina geladen die u hebt opgegeven als de URL voor het landen van de uitgebreide verificatie bij de instellingen van de documentbeveiligingsserver. Zie [ de configuratiemontages van de Server ](configuring-client-server-options.md#server-configuration-settings).

>[!NOTE]
>
>Uitgebreide verificatie wordt ondersteund op Apple Mac OS X met Adobe Acrobat versie 11.0.6 en hoger.

1. Klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren.
1. Klik op Exporteren en sla het configuratiebestand op uw schijf op.
1. Open het bestand in een editor en zoek het knooppunt AllowedUrls.
1. Voeg de volgende regels toe aan het knooppunt `AllowedUrls` : `<entry key="sso-l" value="/ssoexample/login.jsp"/> <entry key="sso-s" value="/ssoexample"/> <entry key="sso-o" value="/ssoexample/logout.jsp"/>`

   ```xml
   <entry key="sso-l" value="/ssoexample/login.jsp"/>
   <entry key="sso-s" value="/ssoexample"/>
   <entry key="sso-o" value="/ssoexample/logout.jsp"/>
   ```

1. Sla het bestand op en importeer het bijgewerkte bestand vanaf de pagina Handmatige configuratie: klik in de beheerconsole op Instellingen > Gebruikersbeheer > Configuratie > Configuratiebestanden importeren en exporteren.

## Offlinebeveiliging configureren {#configuring-offline-security}

Met documentbeveiliging kunt u met beleid beveiligde documenten offline gebruiken zonder een internet- of netwerkverbinding. Deze capaciteit vereist dat het beleid off-line toegang toestaat, zoals die in [ wordt beschreven specificeer de documenttoestemmingen voor gebruikers en groepen ](/help/forms/using/admin-help/creating-policies.md#specify-the-document-permissions-for-users-and-groups). Voordat een document met een dergelijk beleid offline kan worden gebruikt, moet de ontvanger het document openen terwijl het online is en offline toegang inschakelen door op Ja te klikken wanneer hierom wordt gevraagd. De ontvanger kan ook worden verzocht zijn identiteit te verifiëren. De ontvanger kan dan documenten offline gebruiken voor de duur van de offline huurperiode die in het beleid wordt gespecificeerd.

Wanneer de offline leaseperiode afloopt, moet de ontvanger opnieuw synchroniseren met de documentbeveiliging door een document online te openen of door een menuopdracht voor Acrobat- of Acrobat Reader DC-extensies te gebruiken om te synchroniseren. (Zie *Hulp van Acrobat* of aangewezen *de uitbreidingen van de Uitbreidingen van de Lezer van de Acrobaat Hulp*.)

Omdat documenten die offline toegang toestaan, sleutelmateriaal in cache moeten plaatsen op de computer waarop de bestanden offline zijn opgeslagen, kan het bestand mogelijk in gevaar worden gebracht als een onbevoegde gebruiker het sleutelmateriaal kan verkrijgen. Om deze mogelijkheid te compenseren, worden de geplande en handzeer belangrijke het omvergooienopties verstrekt die u kunt vormen om een onbevoegd persoon te verhinderen de sleutel te gebruiken om tot het document toegang te hebben.

### Een standaard offline leaseperiode instellen {#set-a-default-offline-lease-period}

Ontvangers van documenten die met een beleid zijn beveiligd, kunnen de documenten offline nemen gedurende het aantal dagen dat in het beleid is opgegeven. Nadat het document eerst met documentbeveiliging is gesynchroniseerd, kan de ontvanger het offline gebruiken tot de offline leaseperiode verloopt. Wanneer de leaseperiode verloopt, moet de ontvanger het document online openen en zich aanmelden om het te synchroniseren met de documentbeveiliging om het document te kunnen blijven gebruiken.

U kunt een standaard offline huurperiode configureren. De leaseperiode kan worden gewijzigd ten opzichte van de standaardperiode wanneer iemand een beleid maakt of bewerkt.

1. Voor de pagina van de documentveiligheid, klik Configuratie > de Configuratie van de Server.
1. Typ in het vak Offline standaardleaseperiode het aantal dagen voor de offline leaseperiode.
1. Klik op OK.

### Toetsrollovers beheren {#manage-key-rollovers}

Documentbeveiliging gebruikt versleutelingsalgoritmen en -licenties om documenten te beveiligen. Wanneer het een document codeert, produceert de documentveiligheid en beheert een decryptiesleutel genoemd a *DocKey* die het tot de cliënttoepassing overgaat. Als het beleid dat een document beschermt off-line toegang toelaat, wordt een off-line sleutel genoemd a *belangrijkste sleutel* ook geproduceerd voor elke gebruiker die off-line toegang tot het document heeft.

>[!NOTE]
>
>Als een hoofdsleutel niet bestaat, genereert documentbeveiliging een sleutel om een document te beveiligen.

Als u een document dat met een beleid is beveiligd offline wilt openen, moet de computer van de gebruiker over de juiste hoofdsleutel beschikken. De computer verkrijgt de belangrijkste sleutel wanneer de gebruiker met documentveiligheid synchroniseert (opent een beschermd document online). Als deze belangrijkste sleutel wordt gecompromitteerd, zou om het even welk document waaraan de gebruiker off-line toegang heeft ook kunnen worden gecompromitteerd.

Een manier om de bedreiging van offlinedocumenten te verminderen, is door het toestaan van offline toegang tot bijzonder gevoelige documenten te vermijden. Een andere methode is om de belangrijkste sleutels periodiek te rollen. Wanneer de sleutel door de documentbeveiliging wordt omgedraaid, hebben bestaande toetsen geen toegang meer tot documenten die met een beleid zijn beveiligd. Bijvoorbeeld, als een dader een belangrijkste sleutel van een gestolen laptop verkrijgt, kan die sleutel niet worden gebruikt om tot de documenten toegang te hebben die worden beschermd nadat het omvergooien voorkomt. Als u vermoedt dat een bepaalde hoofdsleutel is gecompromitteerd, kunt u manueel over de sleutel rollen.

Een sleutelrollover beïnvloedt echter alle hoofdtoetsen, niet slechts één. Het vermindert ook de scalability van het systeem omdat de cliënten meer sleutels voor off-line toegang moeten opslaan. De standaardfrequentie voor rollover is 20 dagen. Het wordt aanbevolen deze waarde niet in te stellen op een lagere waarde dan 14 dagen, omdat mensen mogelijk geen offline documenten kunnen bekijken en de systeemprestaties mogelijk worden beïnvloed.

In het volgende voorbeeld, is Key1 de ouder van de twee belangrijkste sleutels, en Key2 is nieuwere. Wanneer u de eerste keer op de knop Rollover-sleutels nu klikt, wordt Key1 ongeldig en wordt een nieuwere, geldige hoofdtoets (Key3) gegenereerd. Gebruikers krijgen Key3 wanneer ze synchroniseren met documentbeveiliging, meestal door een beveiligd document online te openen. Gebruikers worden echter niet gedwongen te synchroniseren met documentbeveiliging totdat ze de maximale offline leaseperiode bereiken die in een beleid is opgegeven. Na de eerste sleutelomvergooien, kunnen de gebruikers die offline blijven offline documenten, met inbegrip van die nog openen die door Key3 worden beschermd, tot zij de maximumoff-line huurperiode bereiken. Wanneer u nogmaals op de knop Rollover-toetsen klikt, wordt Key2 ongeldig en wordt Key4 gemaakt. Gebruikers die offline blijven tijdens de twee sleutelrollovers, kunnen documenten die met Key3 of Key4 zijn beveiligd, pas openen nadat ze zijn gesynchroniseerd met documentbeveiliging.

**verander de zeer belangrijke het omvergooiefrequentie**

Als u offlinedocumenten gebruikt, biedt documentbeveiliging u uit vertrouwelijkheidsoverwegingen een automatische sleutelrolloveroptie met een standaardfrequentieperiode van 20 dagen. U kunt de rollover-frequentie wijzigen. Stel de waarde echter niet in op minder dan 14 dagen, omdat mensen mogelijk geen offlinedocumenten kunnen bekijken en de systeemprestaties mogelijk worden beïnvloed.

1. Voor de pagina van de documentveiligheid, klik Configuratie > Zeer belangrijk Beheer.
1. Typ in het vak Frequentie sleutelrollover het aantal dagen voor de rolloverperiode.
1. Klik op OK.

**rol manueel over belangrijkste sleutels**

Om de vertrouwelijkheid van offlinedocumenten te handhaven, kunt u manueel over belangrijkste sleutels rollen. Mogelijk vindt u het nodig om handmatig over een sleutel te rollen (bijvoorbeeld als de sleutel is gecompromitteerd door iemand die deze van een computer verkrijgt waar deze in cache is geplaatst om offline toegang tot een document in te schakelen).

>[!NOTE]
>
>Vermijd vaak het gebruik van handmatige rollover, omdat hierdoor niet slechts één hoofdtoets overheen schuift en gebruikers tijdelijk de mogelijkheid wordt ontnomen nieuwe documenten offline weer te geven.

De belangrijkste sleutels moeten tweemaal over worden gerold alvorens eerder bestaande sleutels op cliëntcomputers ongeldig worden gemaakt. Clientcomputers met ongeldig gemaakte hoofdsleutels moeten opnieuw synchroniseren met de documentbeveiligingsservice om de nieuwe hoofdtoetsen te verkrijgen.

1. Voor de pagina van de documentveiligheid, klik Configuratie > Zeer belangrijk Beheer.
1. Klik op Rollover-toetsen nu en klik op OK.
1. Wacht ongeveer 10 minuten. Het volgende logboekbericht verschijnt in het serverlogboek: `Done RightsManagement key rollover for`*N* `principals`. Waar *N* het aantal gebruikers in het systeem van de documentveiligheid is.
1. Klik op Rollover-toetsen nu en klik op OK.
1. Wacht ongeveer 10 minuten.

## Gebeurteniscontrole en privacy-instellingen configureren {#configuring-event-auditing-and-privacy-settings}

De veiligheid van het document kan informatie over gebeurtenissen controleren en registreren die met beleid-beschermde documenten, beleid, beheerders, en de server verwant zijn. U kunt gebeurtenis controleren vormen, en u kunt de types van gebeurtenissen specificeren om te controleren. Om gebeurtenissen voor een bepaald document te controleren, moet de controleoptie op het beleid ook worden toegelaten.

Wanneer controle wordt toegelaten, kunt u details van de gecontroleerde gebeurtenissen op de pagina van Gebeurtenissen bekijken. gebruikers van documentbeveiliging kunnen ook gebeurtenissen weergeven die specifiek betrekking hebben op documenten die met een beleid zijn beveiligd en die zij gebruiken of maken.

U kunt de volgende gebeurtenistypen selecteren voor controle:

* Met beleid beveiligde documentgebeurtenissen, zoals pogingen van geautoriseerde of onbevoegde gebruikers om documenten te openen
* Beleidsgebeurtenissen, zoals het maken, wijzigen, verwijderen, inschakelen en uitschakelen van beleid
* Gebruikersgebeurtenissen, zoals externe gebruikersuitnodigingen en registraties, geactiveerde en gedeactiveerde gebruikersaccounts, wijzigingen in gebruikerswachtwoorden en profielupdates
* AEM-formuliergebeurtenissen, zoals niet-overeenkomende versies, niet-beschikbare directoryserver- en verificatieproviders en wijzigingen in de serverconfiguratie

### Gebeurteniscontrole in- of uitschakelen {#enable-or-disable-event-auditing}

U kunt controle van gebeurtenissen met betrekking tot de server, beleid-beschermde documenten, beleid, beleidsreeksen, en gebruikers toelaten en onbruikbaar maken. Wanneer u gebeurteniscontrole inschakelt, kunt u alle mogelijke gebeurtenissen controleren of kunt u specifieke gebeurtenissen selecteren die u wilt controleren.

Wanneer u de servercontrole toelaat, kunt u de gecontroleerde gebeurtenissen op de pagina van Gebeurtenissen bekijken.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuration > Audit and Privacy Settings.
1. Selecteer Ja of Nee onder Servercontrole inschakelen om servercontrole te configureren.
1. Als u Ja hebt geselecteerd, voert u onder elke gebeurteniscategorie een van de volgende handelingen uit om de opties te selecteren die u wilt controleren:

   * Als u alle gebeurtenissen in de categorie wilt controleren, selecteert u Alles.
   * Als u alleen bepaalde gebeurtenissen wilt controleren, schakelt u Alles uit en schakelt u de selectievakjes naast de gebeurtenissen die u wilt controleren in.

     (Zie [ de controleopties van de Gebeurtenis ](configuring-client-server-options.md#event-auditing-options).)

1. Klik op OK.

>[!NOTE]
>
>Wanneer u met de webpagina&#39;s werkt, vermijd dan de browserknoppen, zoals de knop Vorige, de knop Vernieuwen en de pijl Vorige of Volgende, omdat deze actie ongewenste problemen bij het vastleggen van gegevens en het weergeven van gegevens kan veroorzaken.

### Persoonlijke meldingen in- of uitschakelen {#enable-or-disable-privacy-notification}

U kunt een privacymeldingsbericht in- en uitschakelen. Wanneer u privacymeldingen inschakelt, wordt een bericht weergegeven wanneer een ontvanger een document probeert te openen dat met een beleid is beveiligd. De kennisgeving informeert de gebruiker dat het documentgebruik wordt gecontroleerd. U kunt ook een URL opgeven die de gebruiker kan gebruiken om uw pagina met privacybeleid weer te geven als die beschikbaar is.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuration > Audit and Privacy Settings.
1. Selecteer Ja of Nee onder Aankondiging privacy inschakelen om het privacybericht te configureren.

   Als het beleid verbonden aan een document anonieme gebruikerstoegang toestaat en de Bericht van de Privacy toelaat wordt geplaatst aan Nr, wordt de gebruiker niet ertoe aangezet om binnen te registreren en het privacybericht wordt niet getoond.

   Als het beleid verbonden aan een document geen anonieme gebruikerstoegang toestaat, zal de gebruiker het privacyberichtbericht zien.

1. Typ, indien van toepassing, in het vak Privacy URL de URL naar de pagina voor privacybeleid. Als het vak Privacy-URL leeg blijft, wordt de privacypagina van adobe.com weergegeven.
1. Klik op OK.

>[!NOTE]
>
>Als u de privacyverklaring uitschakelt, wordt het controleren van het documentgebruik niet uitgeschakeld. Uit de doos controleacties en douaneacties die via uitgebreide gebruik het volgen worden gesteund kunnen nog informatie van het gebruikersgedrag verzamelen.

### Een aangepast type auditgebeurtenis importeren {#import-a-custom-audit-event-type}

Als u een toepassing gebruikt die voor documentbeveiliging geschikt is en die het controleren van extra gebeurtenissen ondersteunt, zoals gebeurtenissen die specifiek zijn voor een bepaald bestandstype, kan een Adobe-partner u aangepaste auditgebeurtenissen bieden die u in documentbeveiliging kunt importeren. Gebruik deze functie alleen als u aangepaste gebeurtenistypen hebt ontvangen van een Adobe-partner.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Gebeurtenisbeheer.
1. Klik op Bladeren om naar het te importeren XML-bestand te gaan en klik op Importeren.
1. Bij het importeren worden bestaande aangepaste auditgebeurtenistypen op de server overschreven als identieke gebeurteniscode en naamruimtecombinaties worden gevonden.
1. Klik op OK.

### Een aangepast type auditgebeurtenis verwijderen {#delete-a-custom-audit-event-type}

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Gebeurtenisbeheer.
1. Schakel het selectievakje naast het type aangepaste auditgebeurtenis dat u wilt verwijderen in en klik op Verwijderen.
1. Klik op OK.

### Controles exporteren {#export-audit-events}

U kunt auditgebeurtenissen exporteren naar een bestand voor archiveringsdoeleinden.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Gebeurtenisbeheer.
1. Bewerk desgewenst de instellingen onder Controlegebeurtenissen exporteren. U kunt het volgende opgeven:

   * de minimumleeftijd waarop de uit te voeren auditgebeurtenissen moeten worden uitgevoerd
   * het maximumaantal auditgebeurtenissen dat in één bestand mag worden opgenomen. De server genereert een of meer bestanden op basis van deze waarde.
   * de map waarin het bestand wordt gemaakt. Deze map staat op de Forms Server. Als het mappad relatief is, is dit relatief ten opzichte van de hoofdmap van de toepassingsserver.
   * het voorvoegsel van het bestand dat moet worden gebruikt voor de bestanden met auditgebeurtenissen
   * de indeling van het bestand, ofwel een CSV-bestand (comma-separated values, door komma&#39;s gescheiden waarden) dat compatibel is met Microsoft Excel of een XML-bestand.

1. Klik op Export. Klik op Exporteren annuleren als u het exporteren wilt annuleren. Als een andere gebruiker een exportbewerking heeft gepland, is de knop Exporteren annuleren niet beschikbaar totdat het exporteren is voltooid. De knop Exporteren annuleren is niet beschikbaar als een andere gebruiker een exportbewerking heeft gepland. Klik op Vernieuwen om te controleren of de geplande export of verwijdering is gestart of voltooid.

### Auditgebeurtenissen verwijderen {#delete-audit-events}

U kunt controlegebeurtenissen verwijderen die ouder zijn dan een opgegeven aantal dagen.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Gebeurtenisbeheer.
1. Geef onder Controlegebeurtenissen verwijderen het aantal dagen op in het vak Auditgebeurtenissen ouder dan verwijderen.
1. Klik op Verwijderen. Klik op Export. Klik op Verwijderen annuleren als u het verwijderen wilt annuleren. Als een andere gebruiker een verwijdering heeft gepland, is de knop Verwijderen annuleren niet beschikbaar totdat het exporteren is voltooid. De knop Verwijderen annuleren is niet beschikbaar als een andere gebruiker een exportbewerking heeft gepland. Klik op Vernieuwen om te controleren of een geplande verwijdering is gestart of voltooid.

### Opties voor gebeurteniscontrole {#event-auditing-options}

U kunt gebeurteniscontrole in- en uitschakelen en de typen gebeurtenissen opgeven die moeten worden gecontroleerd.

**de gebeurtenissen van het Document**

**Document van de Mening:** Ontvangt bekijkt een beleid-beschermd document.

**dicht Document:** Een ontvanger sluit een beleid-beschermd document.

**de Laag resolutie van de Druk** Ontvanger A drukt een beleid-beschermd document met de laag-resolutiegespecificeerde optie.

**Druk Hoge resolutie:** De ontvanger drukt een beleid-beschermd document met gespecificeerde high-resolution optie.

**voeg Annotatie aan Document toe:** Ontvanger voegt een aantekening aan een document van PDF toe.

**trekt Document in:** een gebruiker of een beheerder trekt toegang tot een beleid-beschermd document terug.

**trekt Document ongedaan:** een gebruiker of een beheerder herstelt toegang tot een beleid-beschermd document.

**het Vullen van de Vorm:** Een ontvanger gaat informatie in een document van PDF in dat een invulbare vorm is.

**Verwijderd Beleid:** De uitgever van A verwijdert een beleid uit een document om de veiligheidsbescherming terug te trekken.

**Revocation URL van het Document van de Verandering:** Een vraag van het API niveau verandert de herroeping URL die wordt gespecificeerd om tot een nieuw document toegang te hebben dat een ingetrokken document vervangt.

**wijzig Document:** De ontvanger van A verandert de inhoud van een beleid-beschermd document.

**Onderteken Document:** de ontvanger ondertekent een document.

**beveilig een Nieuw Document:** een gebruiker past een beleid toe om een document te beschermen.

**Beleid van de Schakelaar op Document:** een gebruiker of een beheerder schakelt het beleid dat aan een document in bijlage is.

**publiceer Document als:** een nieuw document de waarvan documentName en vergunning identiek aan een bestaand document zijn wordt geregistreerd op de server, en de documenten hebben geen ouder-kind verhouding. Deze gebeurtenis kan worden geactiveerd met de AEM-formulieren SDK.

**Interactief Document:** een nieuw document de waarvan documentName en vergunning identiek aan een bestaand document zijn wordt geregistreerd op de server, en de documenten hebben een ouder-kind verhouding. Deze gebeurtenis kan worden geactiveerd met de AEM-formulieren SDK.

**de gebeurtenissen van het Beleid**

**Created Beleid:** een gebruiker of een beheerder leidt tot een beleid.

**Toegelaten Beleid:** een beheerder stelt een beleid beschikbaar.

**Gewijzigd Beleid:** een gebruiker of een beheerder verandert een beleid.

**Gehandicapte Beleid:** een beheerder maakt een beleid niet beschikbaar.

**Geschrapt Beleid:** een gebruiker of een beheerder schrapt een beleid.

**de Eigenaar van het Beleid van de Verandering:** Een vraag van het API niveau verandert de beleidseigenaar.

**de gebeurtenissen van de Gebruiker**

**Geschrapte Gebruiker:** een beheerder schrapt een gebruikersrekening.

**Uitgenodigde Gebruiker van het Register:** Een externe gebruikersregisters met documentveiligheid.

**Succesvolle Login:** Succesvolle login pogingen door beheerders of gebruikers.

**Uitgenodigde Gebruikers:** de veiligheid van het Document nodigt een gebruiker uit om te registreren.

**Geactiveerde Gebruikers:** de Externe gebruikers activeren hun rekeningen door URL in activeringse-mail te gebruiken, of een beheerder laat een rekening toe.

**Wachtwoord van de Verandering:** Uitgenodigde gebruikers veranderen hun wachtwoorden of een beheerder stelt een wachtwoord voor een lokale gebruiker terug.

**Ontbroken Login:** Ontbroken login pogingen door beheerders of gebruikers.

**Gedeactiveerde Gebruikers:** een beheerder maakt een lokale gebruikersrekening onbruikbaar.

**Update van het Profiel:** Uitgenodigde gebruikers veranderen hun naam, organisatienaam, en wachtwoord.

**Vergrendelde Rekening:** een beheerder sluit een rekening.

**Beleid plaatste Gebeurtenissen**

**Gemaakt
Beleidsset:** een beheerder of beleidssetcoördinator maakt een beleidsset.

**Geschrapte Reeks van het Beleid:** een beheerder of een coördinator van de beleidsreeks schrapt een beleidsreeks.

**Gewijzigd Beleid plaatste:** een beheerder of een coördinator van de beleidsreeks verandert een beleidsreeks.

**de gebeurtenissen van het Systeem**

**Directory
Synchronisatie voltooid:** Deze informatie is niet beschikbaar op de pagina Gebeurtenissen. De huidige informatie van de foldersynchronisatie, met inbegrip van de huidige synchronisatiestatus en de tijd van de laatste synchronisatie, wordt getoond op de pagina van het Beheer van het Domein. Klik op Instellingen > Gebruikersbeheer > Domeinbeheer om de pagina Domeinbeheer in de beheerconsole te openen.

**de Cliënt laat Offline Toegang toe:** een gebruiker liet off-line toegang tot documenten toe die tegen de server op de computer van de gebruiker worden beveiligd.

**Gesynchroniseerde de toepassing van de Cliënt** moet informatie met de server synchroniseren om voor off-line toegang toe te staan.

**Verkeerde Versie:** Een versie van AEM vormt SDK die met de server onverenigbaar is probeerde om met de server te verbinden.

**Informatie van de Synchronisatie van de Folder:** Deze informatie is niet beschikbaar bij de pagina van Gebeurtenissen. De huidige informatie van de foldersynchronisatie, met inbegrip van de huidige synchronisatiestatus en de tijd van de laatste synchronisatie, wordt getoond op de pagina van het Beheer van het Domein. Klik op Instellingen > Gebruikersbeheer > Domeinbeheer om de pagina Domeinbeheer in de beheerconsole te openen.

**Verandering van de Configuratie van de Server:** Veranderingen in de serverconfiguratie die of door de Web-pagina&#39;s of manueel door een config.xml- dossier in te voeren worden gedaan. Hieronder vallen wijzigingen in de basis-URL, sessietime-outs, inlogvergrendelingen, directory-instellingen, sleutelrollovers, SMTP-serverinstellingen voor externe registratie, watermerkconfiguratie, weergaveopties, enzovoort.

## Uitgebreide gebruiksregistratie configureren {#configuring-extended-usage-tracking}

Met documentbeveiliging kunt u verschillende aangepaste gebeurtenissen bijhouden die op een beveiligd document kunnen worden uitgevoerd. U kunt het volgen van gebeurtenissen van de server van de documentveiligheid op globaal niveau of op een beleidsniveau toelaten. Vervolgens kunt u een JavaScript instellen om specifieke handelingen vast te leggen die in het beveiligde PDF-document zijn uitgevoerd, zoals klikken op een knop of het document opslaan. Deze gebruiksgegevens worden verzonden als een XML-bestand in sleutelwaardeparen, dat u kunt gebruiken voor verdere analyse. Eindgebruikers die de beveiligde documenten openen, kunnen deze tracering toestaan of weigeren vanuit de clienttoepassing.

Als het volgen op het globale niveau wordt toegelaten, kunt u dit het plaatsen op het beleidsniveau met voeten treden en het voor een bepaald beleid onbruikbaar maken. Overschrijven op beleidsniveau is niet mogelijk als tracering op mondiaal niveau is uitgeschakeld. De lijst met bijgehouden gebeurtenissen wordt automatisch naar de server geduwd wanneer het aantal gebeurtenissen 25 bereikt of wanneer het document wordt gesloten. U kunt uw manuscript ook vormen om de gebeurtenislijst volgens uw vereisten uitdrukkelijk te duwen. U kunt de functie voor het bijhouden van gebeurtenissen aanpassen door de eigenschappen en methoden van het beveiligingsobject van het document te openen.

Nadat u het bijhouden van wijzigingen hebt ingeschakeld, is het bijhouden van wijzigingen standaard ingeschakeld voor alle beleidsregels die daarna worden gemaakt. Het beleid dat vóór het volgen wordt gecreeerd die op de server wordt toegelaten zal handupdates vereisen.

### Uitgebreide gebruiksregistratie inschakelen of uitschakelen {#enable-or-disable-extended-usage-tracking}

Voordat u begint, moet u ervoor zorgen dat Servercontrole is ingeschakeld. Zie [ het Vormen gebeurtenis controle en privacy montages ](configuring-client-server-options.md#configuring-event-auditing-and-privacy-settings) voor meer informatie bij controle.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuration > Audit and Privacy Settings.
1. Selecteer Ja of Nee onder Bijhouden inschakelen om uitgebreide gebruiksregistratie te configureren.
1. Selecteer Ja of Nee als u de selectie van het selectievakje Verzameling van gedetailleerde gebruiksgegevens toestaan op de aanmeldingspagina wilt inschakelen, onder de standaardinstelling Bijhouden inschakelen.

Als u de bijgehouden gebeurtenissen wilt weergeven, kunt u het filter Documentgebeurtenissen op de pagina Gebeurtenissen gebruiken. De gebeurtenissen die worden bijgehouden met JavaScript, worden aangeduid als Gedetailleerd gebruik bijhouden. Verwijs naar [ de gebeurtenissen van de Controle ](/help/forms/using/admin-help/monitoring-events.md#monitoring-events) voor meer informatie over gebeurtenissen.

## Beveiligingsweergave-instellingen voor documenten configureren {#configure-document-security-display-settings}

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Weergaveopties.
1. Configureer de instellingen en klik op OK.

### Weergave-instellingen {#display-settings}

**Rijen aan vertoning voor onderzoeksresultaten:** Aantal rijen die op een pagina verschijnen wanneer de onderzoeken worden uitgevoerd.

**Aanpassing voor cliëntlogin dialoog**

Deze instellingen bepalen de tekst die wordt weergegeven in de aanmeldingsprompt die wordt weergegeven wanneer een gebruiker zich via een clienttoepassing aanmeldt bij documentbeveiliging.

**Welkome Tekst:** De welkome berichttekst, zoals &quot;gelieve login met Uw Naam en Wachtwoord van de Gebruiker&quot;. De welkomstberichttekst moet informatie bevatten over hoe u zich kunt aanmelden bij de documentbeveiliging en hoe u contact kunt opnemen met een beheerder of een andere aangewezen ondersteuningspersoon in uw organisatie voor hulp. Externe gebruikers moeten bijvoorbeeld mogelijk contact opnemen met een beheerder als ze hun wachtwoorden vergeten of hulp nodig hebben bij het registratie- of aanmeldingsproces. De welkomsttekst mag maximaal 512 tekens lang zijn.

**Tekst van de Naam van de Gebruiker:** het tekstetiket voor het vakje van de gebruikersnaam.

**Tekst van het Wachtwoord:** het tekstetiket voor het wachtwoordvakje.

**Aanpassing voor de dialoog van de authentificatie van het cliëntcertificaat**

Deze instellingen bepalen de tekst die wordt weergegeven in het dialoogvenster voor certificaatverificatie.

**Kies
Tekst van het Type van authentificatie:** de tekst die aan een gebruiker wordt getoond om een authentificatietype te selecteren.

**kies de Tekst van het Certificaat:** de tekst die wordt getoond om een gebruiker te leiden om een certificaattype te selecteren.

**Certificaten niet Beschikbare Tekst van de Fout:** Bericht van maximaal 512 karakters aan vertoning wanneer het geselecteerde certificaat niet beschikbaar is.

**Aanpassing voor de vertoning van het cliëntcertificaat**

**slechts Vertrouwde Vertrouwde op Vertrouwde Uitgevers van de Vertoning:** wanneer deze optie wordt geselecteerd, stelt de cliënttoepassing de gebruiker met slechts certificaten van crediteurenuitgevers voor die de vormen van AEM worden gevormd om te vertrouwen (Zie het Leiden certificaten en geloofsbrieven.) Als deze optie niet is geselecteerd, wordt de gebruiker een lijst met alle certificaten op het systeem van de gebruiker weergegeven.

## Dynamische watermerken configureren {#configure-dynamic-watermarks}

Met documentbeveiliging kunt u standaardinstellingen configureren voor de optie voor dynamisch watermerk die u kunt toepassen wanneer u beleid maakt. A *watermerk* is een beeld dat over tekst in het document wordt geplaatst. Dit is handig voor het bijhouden van de inhoud van een document en kan helpen bij het identificeren van illegaal gebruik van de inhoud.

Een dynamisch watermerk kan bestaan uit tekst die bestaat uit gedefinieerde variabelen zoals de gebruikersnaam en de datum en aangepaste tekst, of uit rijke inhoud binnen een PDF. U kunt watermerken met verscheidene elementen vormen elk met zijn eigen het plaatsen en het formatteren.

Watermerken kunnen niet worden bewerkt en zijn daarom een veiligere methode om de vertrouwelijkheid van de documentinhoud te waarborgen. Dynamische watermerken zorgen er ook voor dat een watermerk voldoende gebruikersspecifieke informatie bevat om te voorkomen dat het document verder wordt verspreid.

Het watermerk dat een beleid specificeert verschijnt in het beleid-beschermde document wanneer een ontvanger het document bekijkt of drukt. In tegenstelling tot permanente watermerken, wordt een dynamisch watermerk nooit bewaard in het document, dat de flexibiliteit verstrekt die wanneer het opstellen van een document in een Intranetmilieu noodzakelijk is om ervoor te zorgen dat de het bekijken toepassing de identiteit van de specifieke gebruiker toont. Als een document meerdere gebruikers heeft, betekent het gebruik van het dynamische watermerk ook dat u één document kunt gebruiken in plaats van meerdere versies, elk met een ander watermerk. Het watermerk dat wordt weergegeven, weerspiegelt de identiteit van de huidige gebruiker.

Dynamische watermerken verschillen van de watermerken die gebruikers rechtstreeks aan het document in Acrobat kunnen toevoegen. Het resultaat is dat u twee watermerken kunt hebben in een document dat met een beleid is beveiligd.

### Overwegingen bij het maken van watermerken {#considerations-when-creating-watermarks}

U kunt dynamische watermerken maken met verschillende watermerkelementen waarbij elk element is opgegeven als tekst of als PDF. U kunt maximaal vijf elementen in een watermerk opnemen.

Als u een watermerk op basis van tekst kiest, kunt u verschillende elementen in het watermerk opgeven met meerdere tekstitems en de positie van elk element opgeven. Wijs betekenisvolle namen toe aan deze elementen, zoals kop- en voettekst, enzovoort.

Als u bijvoorbeeld verschillende tekst in de kop- en voettekst, op de marges en in het hele document als watermerk wilt opgeven, maakt u verschillende watermerkelementen en geeft u de positie ervan op. Als u wilt dat de gebruikers-id van de gebruiker en de huidige datum waarop het document wordt geopend, worden weergegeven in de koptekst, de naam van het beleid in de rechtermarge en de aangepaste tekst &quot;CONFIDENTIAL&quot; diagonaal in het document, definieert u afzonderlijke watermerkelementen met tekst als het type en geeft u de opmaak en positionering ervan op. Wanneer het watermerk op een document wordt toegepast, worden alle elementen in het watermerk tegelijkertijd op het document toegepast, in de volgorde waarin ze aan het watermerk worden toegevoegd.

Gewoonlijk gebruikt u watermerken op basis van PDF om grafische inhoud op te nemen, zoals logo&#39;s of speciale symbolen, zoals copyright of geregistreerd handelsmerk.

U kunt de limieten voor het aantal watermerkelementen en de PDF-bestandsgrootte wijzigen door het configuratiebestand voor documentbeveiliging te wijzigen. Zie [ Verandering de parameters van de watermerkconfiguratie ](configuring-client-server-options.md#change-the-watermark-configuration-parameters).

Houd rekening met het volgende wanneer u watermerken configureert:

* U kunt een PDF-document dat met een wachtwoord is beveiligd, niet als watermerkelement gebruiken. Als het watermerk dat u maakt echter andere elementen bevat die niet met een wachtwoord zijn beveiligd, worden deze toegepast als onderdeel van het watermerk.
* U kunt de maximale PDF-bestandsgrootte wijzigen die u als watermerkelement wilt gebruiken. Grote PDF-documenten die als watermerken worden gebruikt, verlagen de prestaties echter tijdens offlinesynchronisatie van documenten die met dergelijke watermerken zijn toegepast. Zie [ Verandering de parameters van de watermerkconfiguratie ](configuring-client-server-options.md#change-the-watermark-configuration-parameters).
* Alleen de eerste pagina van de geselecteerde PDF wordt gebruikt als watermerk. Zorg ervoor dat de informatie die u als watermerk wilt weergeven, beschikbaar is op de eerste pagina zelf.
* Hoewel u de schaling van het PDF-document kunt opgeven, moet u rekening houden met het paginaformaat en de lay-out van het PDF-document als u het als watermerk wilt gebruiken in de kop-, voettekst- of marges.
* Voer de naam correct in wanneer u de naam van het lettertype opgeeft. AEM-formulieren vervangen het font dat u hebt opgegeven als het niet aanwezig is op de clientcomputer waar het document wordt geopend.
* Als u tekst hebt geselecteerd als watermerkinhoud, werkt het opgeven van de schaaloptie Aanpassen aan pagina niet voor pagina&#39;s met een afwijkende breedte.
* Wanneer u de plaatsing van de elementen van het watermerk opgeeft, moet u ervoor zorgen dat niet meer dan één element dezelfde positionering heeft. Als twee watermerkelementen dezelfde positie hebben, zoals het midden, lijken ze overlappend te zijn op het document en in de volgorde waarin ze aan het watermerk zijn toegevoegd.
* Wanneer u de tekengrootte en het type opgeeft, moet u ervoor zorgen dat de lengte van de tekst volledig zichtbaar is binnen de pagina. De inhoud van de tekst wordt over nieuwe regels verdeeld, zodat de inhoud van het watermerk die u in de marges wilt opnemen, kan overlappen in de inhoudsgebieden op pagina&#39;s. Als het document echter in Acrobat 9 wordt geopend, wordt de tekst na de enkele regel afgekapt.

### Beperkingen van dynamische watermerken {#limitations-of-dynamic-watermarks}

Dynamische watermerken worden mogelijk niet door alle clienttoepassingen ondersteund. Raadpleeg de desbetreffende Help bij Acrobat Reader DC-extensies. Houd rekening met het volgende over de versies van Acrobat die dynamische watermerken ondersteunen:

* U kunt een PDF-document dat met een wachtwoord is beveiligd, niet als watermerkelement gebruiken.
* Acrobat- en Adobe Reader-versies ouder dan 10 bieden geen ondersteuning voor de volgende functies voor watermerken:

   * PDF-watermerken
   * Meerdere elementen in het watermerk (Text/PDF)
   * Geavanceerde opties, zoals paginabereik of weergaveopties
   * Opties voor tekstopmaak, zoals opgegeven lettertype, lettertypenaam en -kleur. Eerdere versies van Acrobat en Reader geven de tekstinhoud echter weer in het standaardlettertype en de standaardkleur.

* Acrobat 9.0 en eerdere versies: Acrobat 9.0 en lager ondersteunen geen beleidsnamen in dynamische watermerken. Als in Acrobat 9.0 een document wordt geopend dat met een beleid is beveiligd en een dynamisch watermerk heeft dat een beleidsnaam en andere dynamische gegevens bevat, wordt het watermerk weergegeven zonder de naam van het beleid. Als het dynamische watermerk alleen de beleidsnaam bevat, geeft Acrobat een foutbericht weer

### Een dynamische watermerksjabloon toevoegen {#add-a-dynamic-watermark-template}

U kunt dynamische watermerksjablonen maken. Deze sjablonen blijven beschikbaar als configuratieoptie voor beleid dat beheerders of gebruikers maken.

>[!NOTE]
>
>De dynamische informatie van de watermerkconfiguratie wordt niet gevangen met de andere configuratieinformatie wanneer u een configuratiedossier uitvoert.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Watermerken.
1. Klik op Nieuw.
1. Typ in het vak Naam een naam voor het nieuwe watermerk.

   ***nota &#x200B;**: U kunt sommige speciale karakters in de namen of de beschrijvingen van watermerken of watermerkelementen niet gebruiken. Zie de beperkingen die in [ worden vermeld Overwegingen voor het uitgeven van beleid ](/help/forms/using/admin-help/creating-policies.md#considerations-for-editing-policies).*

1. Voer onder Naam naast het plusteken een betekenisvolle naam in voor het watermerkelement, zoals Koptekst, voeg een beschrijving toe en vouw het plusteken uit om de opties weer te geven.
1. Selecteer onder Source het type watermerk als Tekst of PDF.
1. Voer de volgende handelingen uit als u Tekst hebt geselecteerd:

   * Selecteer de typen watermerken die u wilt opnemen. Als u Aangepaste tekst selecteert, typt u in het aangrenzende vak de tekst die u voor het watermerk wilt weergeven. Onthoud de tekstlengte die als watermerk wordt weergegeven.
   * Geef de tekstopmaakeigenschappen op, zoals lettertypenaam, tekengrootte, voorgrondkleur en achtergrondkleur voor de tekstinhoud van de watermerktekst. Geef de voor- en achtergrondkleur op als hexadecimale waarden.

     ***nota &#x200B;**: Als u de het schrapen optie zoals Aanpassen aan Pagina selecteert, is het bezit van de doopvontgrootte niet beschikbaar voor het uitgeven.*

1. Als u PDF voor rijke watermerkopties selecteerde, doorbladert de klik **&#x200B;**&#x200B;naast Uitgezochte PDF van het Watermerk om het document van PDF te selecteren dat u als watermerk wilt gebruiken.

   ***nota &#x200B;**: Gebruik geen wachtwoord-beschermd document van PDF. Als u een wachtwoord-beschermde PDF als watermerkelement specificeert, wordt het watermerk niet toegepast.*

1. Selecteer Ja of Nee onder Als achtergrond gebruiken.

   **nota**: Momenteel, verschijnt het watermerk in de voorgrond ongeacht dit het plaatsen.

1. Als u wilt bepalen waar het watermerk in het document wordt weergegeven, configureert u de opties Verticaal uitlijnen en Horizontaal uitlijnen.
1. Selecteer Aanpassen aan pagina of selecteer % en typ een percentage in het vak. De waarde moet een geheel getal zijn, niet een breuk. Als u de grootte van het watermerk wilt configureren, gebruikt u een waarde die het percentage van de pagina aangeeft of stelt u het watermerk zo in dat het de grootte van de pagina aanpast.
1. Typ in het vak Rotatie de graden waarmee u het watermerk wilt roteren. Het bereik loopt van -180 tot 180. Gebruik een negatieve waarde om het watermerk linksom te roteren. De waarde moet een geheel getal zijn, niet een breuk.
1. Typ een percentage in het vak Dekking. Gebruik een geheel getal, geen breuk.
1. Stel onder Geavanceerde opties het volgende in:

   **Opties van de Waaier van de Pagina**

   Stel het paginabereik in waarin het watermerk moet worden weergegeven. Voer de startpagina in als 1 en de eindpagina als -1 om alle pagina&#39;s te laten markeren met het watermerk.

   **Opties van de Vertoning**

   Selecteer waar u het watermerk wilt laten verschijnen. Standaard wordt het watermerk zowel op elektronische (online) als op papier (afdrukken) weergegeven.

1. Klik **Nieuw** onder watermerkelementen om meer watermerkelementen indien nodig toe te voegen.
1. Klik op OK.

### Een sjabloon voor een dynamisch watermerk bewerken {#edit-a-dynamic-watermark-template}

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Watermerken.
1. Klik op het desbetreffende watermerk in de lijst.
1. Wijzig desgewenst de instellingen op de pagina Watermerken bewerken.
1. Klik op OK.

### Een sjabloon voor een dynamisch watermerk verwijderen {#delete-a-dynamic-watermark-template}

Wanneer u een dynamisch watermerk verwijdert, kunt u dit niet meer toevoegen aan een nieuw beleid. Nochtans, blijft het watermerk op bestaand beleid dat momenteel het gebruikt, en de documenten die het beleid momenteel beschermt blijven het dynamische watermerk tonen tot u of een gebruiker het beleid uitgeeft dat het geschrapte watermerk bevat. Nadat het beleid is bewerkt, wordt het watermerk niet meer toegepast. Er wordt een bericht weergegeven waarin wordt aangegeven dat het bestaande watermerk in het beleid wordt verwijderd en dat de gebruiker een ander watermerk kan selecteren om het te vervangen.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Watermerken.
1. Schakel het selectievakje naast het desbetreffende watermerk in en klik op Verwijderen.
1. Klik op OK.

## Opgeroepen gebruikersregistratie configureren {#configuring-invited-user-registration}

Gebruikers die zich buiten uw organisatie bevinden, kunnen zich registreren met documentbeveiliging. Uitgenodigde gebruikers die hun accounts registreren en activeren, kunnen zich aanmelden bij de documentbeveiliging met hun e-mailadres en het wachtwoord dat ze hebben gemaakt tijdens de registratie. Geregistreerde uitgenodigde gebruikers kunnen met beleid beveiligde documenten gebruiken waarvoor zij machtigingen hebben.

Wanneer uitgenodigde gebruikers worden geactiveerd, worden ze lokale gebruikers. De lokale gebruikers kunnen worden gevormd en worden geleid door het Uitgenodigde en Lokale gebied van Gebruikers te gebruiken. (Zie [ het Leiden uitgenodigde en lokale gebruikersrekeningen ](/help/forms/using/admin-help/invited-local-user-accounts.md#managing-invited-and-local-user-accounts).)

Afhankelijk van de mogelijkheden die u inschakelt voor uitgenodigde gebruikers, kunnen zij ook gebruikmaken van de volgende documentbeveiligingsfuncties:

* Beleid toepassen op documenten
* Beleid maken
* uitgenodigde gebruikers toevoegen aan beleid

Met documentbeveiliging wordt automatisch een e-mailuitnodiging voor een registratie gegenereerd wanneer de volgende gebeurtenissen plaatsvinden, tenzij de gebruiker zich al in de LDAP-brondirectory bevindt of eerder is uitgenodigd om zich te registreren:

* Een bestaande gebruiker voegt een uitgenodigde gebruiker aan een beleid toe
* Een beheerder voegt een uitgenodigde gebruikersrekening op de Uitgenodigde pagina van de Registratie van de Gebruiker toe

Het registratiebericht bevat een koppeling naar een registratiepagina en informatie over de manier waarop u zich kunt registreren. Nadat de uitgenodigde gebruiker zich heeft geregistreerd, geeft de documentveiligheid een activeringse-mail met een verbinding aan een pagina van de Activering uit. Als de account is geactiveerd, blijft deze geldig totdat u de account deactiveert of verwijdert.

Als u ingebouwde registratie toelaat, specificeert u uw server SMTP, registratie e-maildetails, toegangsmogelijkheden, en stelt wachtwoord-e-mailinformatie slechts eenmaal in. Voordat u ingebouwde registratie inschakelt, moet u ervoor zorgen dat u een lokaal domein in Gebruikersbeheer hebt gemaakt en de rol &quot;Gebruiker uitnodigen voor documentbeveiliging&quot; hebt toegewezen aan de juiste gebruikers en groepen in uw organisatie. (Zie [ een lokaal domein ](/help/forms/using/admin-help/adding-domains.md#add-a-local-domain) en [ toevoegen Creërend en vormend rollen ](/help/forms/using/admin-help/creating-configuring-roles.md#creating-and-configuring-roles).) Als u geen ingebouwde registratie gebruikt, moet u uw eigen systeem hebben van de gebruikersregistratie die gebruikend de vormen SDK van AEM wordt gecreeerd. Zie de hulp bij het &quot;Ontwikkelen van SPIs voor de vormen van AEM&quot;in [ Programmering met de vormen van AEM ](/help/forms/developing/introducing-java-api-soap-quick.md). Als u de optie Ingebouwde registratie niet gebruikt, wordt u aangeraden een bericht te configureren in de activerings-e-mail en in het aanmeldingsscherm van de client om gebruikers te laten weten hoe ze contact kunnen opnemen met de beheerder voor een nieuw wachtwoord of voor andere informatie.

**laat en vormt uitgenodigde gebruikersregistratie** toe

Standaard is het registratieproces voor uitgenodigde gebruikers uitgeschakeld. U kunt de uitgenodigde gebruikersregistratie voor documentveiligheid, zoals vereist toelaten en onbruikbaar maken.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuration > Invited User Registration.
1. Selecteer Uitgenodigde gebruikersregistratie inschakelen.
1. (Optioneel) Werk desgewenst de instellingen voor de registratie van uitgenodigde gebruikers bij:

   * [Een externe gebruiker of groep uitsluiten of opnemen](configuring-client-server-options.md#exclude-or-include-an-external-user-or-group)
   * [Parameters van server- en registratierekeningen](configuring-client-server-options.md#server-and-registration-account-parameters)
   * [E-mailinstellingen voor uitnodiging registreren](configuring-client-server-options.md#registration-invitation-email-settings)
   * [Instellingen voor e-mail activeren](configuring-client-server-options.md#activation-email-settings)
   * [E-mail voor opnieuw instellen van wachtwoord configureren](configuring-client-server-options.md#configure-a-password-reset-email)

1. (Optioneel) Selecteer Ja onder Ingebouwde registratie om deze optie in te schakelen. Als u ingebouwde registratie niet inschakelt, moet u een eigen gebruikersregistratiesysteem instellen.
1. Klik op OK.

### Een externe gebruiker of groep uitsluiten of opnemen {#exclude-or-include-an-external-user-or-group}

U kunt de registratie met documentbeveiliging voor bepaalde externe gebruikers of gebruikersgroepen beperken. Deze optie is bijvoorbeeld handig om toegang tot een bepaalde gebruikersgroep toe te staan, maar om specifieke personen uit te sluiten die deel uitmaken van de groep.

De volgende instellingen bevinden zich in het gebied Filter e-mailbeperking van de pagina Invited User Registration.

**Uitsluiting:** Type het e-mailadres van een gebruiker of een groep om uit te sluiten. Als u meerdere gebruikers of groepen wilt uitsluiten, typt u elk e-mailadres op een nieuwe regel. Als u alle gebruikers wilt uitsluiten die tot een bepaald domein behoren, voert u een jokerteken en de domeinnaam in. Als u bijvoorbeeld alle gebruikers in het domein example.com wilt uitsluiten, typt u &ast;.example.com.

**Opname:** Type het e-mailadres van een gebruiker of een groep om te omvatten. Als u meerdere gebruikers of groepen wilt opnemen, typt u elk e-mailadres op een nieuwe regel. Als u alle gebruikers wilt opnemen die tot een bepaald domein behoren, voert u een jokerteken en de domeinnaam in. Als u bijvoorbeeld alle gebruikers in het domein example.com wilt opnemen, typt u &ast;.example.com.

### Parameters van server- en registratierekeningen {#server-and-registration-account-parameters}

De volgende instellingen bevinden zich in het gedeelte Algemene instellingen van de pagina Uitgenodigde gebruikersregistratie.

**SMTP Gastheer:** de gastheernaam van de server SMTP. De SMTP-server beheert de uitgaande e-mailberichten om uitgenodigde gebruikersaccounts te registreren en activeren.

Indien nodig door uw gastheer SMTP, typ de vereiste informatie in de dozen van de Naam van de Rekening van de Server SMTP en van het Wachtwoord van de Rekening SMTP om met de server te verbinden SMTP. Sommige organisaties handhaven deze eis niet. Als u informatie nodig hebt, zie uw systeembeheerder.

**SMTP de klassennaam van de servercontactdoos:** de klassennaam van de Contactdoos voor de server SMTP. Bijvoorbeeld javax.net.ssl.SSLSocketFactory.

**Type van Inhoud E-mail:** Accepteerde MIME type zoals tekst/onbewerkt of tekst/html.

**E-mail het Coderen:** Coderend formaat te gebruiken wanneer het verzenden van e-mailberichten. U kunt elke codering opgeven, bijvoorbeeld UTF-8 voor Unicode of ISO-8859-1 voor Latijn. De standaardwaarde is UTF-8.

**e-mailadres opnieuw richten:** Wanneer u een e-mailadres voor dit het plaatsen specificeert, worden om het even welke nieuwe uitnodiging verzonden naar het verstrekte adres. Deze instelling kan handig zijn voor testdoeleinden.

**Lokale Domeinen van het Gebruik:** selecteer het aangewezen domein. Voor een nieuwe installatie, zorg ervoor dat u het domein door Beheer van de Gebruiker creeerde te gebruiken. Als dit een verbetering is, werd een extern gebruikersdomein gecreeerd tijdens de verbetering en kan worden gebruikt.

**SSL van het Gebruik voor server SMTP:** selecteer deze optie om SSL voor de server toe te laten SMTP.

**login van de Vertoning verbinding op registratiepagina:** toont een login verbinding op de registratiepagina die voor uitgenodigde gebruikers wordt getoond.

**om de Veiligheid van de Laag van het Vervoer (TLS) voor de server toe te laten SMTP**

1. Open de beheerconsole.

   De standaardplaats van de console van het Beleid is `https://<server>:<port>/adminui`.

1. Ga naar Home > Services > Documentbeveiliging > Configuration > Invited User Registration.
1. Voor Uitgenodigde Registratie van de Gebruiker, specificeer alle configuratiemontages en klik dan O.K.

   >[!NOTE]
   >
   >Als u Microsoft Office 365 als server SMTP voor het verzenden van de uitnodigingen voor gebruikersregistratie gebruikt, gebruik de volgende montages:
   >
   >**SMTP Gastheer:** smtp.office365.com
   >**Haven:** 587

1. Daarna, moet u config.xml bijwerken. Zie [ Configuratie om SMTP voor de Veiligheid van de Laag van het Vervoer (TLS) toe te laten ](configuring-client-server-options.md#configuration-to-enable-smtp-for-transport-layer-security-tls)

>[!NOTE]
>
>Als u wijzigingen aanbrengt in de opties voor de uitgenodigde gebruikersregistratie, wordt het bestand config.xml overschreven en wordt TLS gedeactiveerd. Als u de wijzigingen overschrijft, moet u de bovenstaande stap uitvoeren om TLS-ondersteuning voor Uitgenodigde gebruikersregistratie opnieuw te activeren.

### E-mailinstellingen voor uitnodiging registreren {#registration-invitation-email-settings}

Met documentbeveiliging wordt automatisch een e-mailuitnodiging tot inschrijving verzonden wanneer u een uitgenodigde gebruikersaccount maakt of wanneer een bestaande gebruiker een externe ontvanger toevoegt die zich nog niet heeft geregistreerd of die is uitgenodigd om zich te registreren voor een beleid. Het e-mailbericht bevat een koppeling die de ontvanger kan gebruiken om toegang te krijgen tot de registratiepagina en persoonlijke accountgegevens in te voeren, zoals gebruikersnaam en wachtwoord. Het wachtwoord kan elke combinatie van acht tekens zijn.

Wanneer de ontvanger de account activeert, wordt de gebruiker een lokale gebruiker.

De volgende instellingen bevinden zich in het gedeelte Invitation Email Configuration van de pagina Invited User Registration.

**van:** Het e-mailadres waarvan uitnodigingsE-mail wordt verzonden. Het standaardformaat van Van e-mailadres is postmaster@ [ your_installation_domain ].com.

**Onderwerp:** Standaard onderwerp voor het uitnodigingse-mailbericht.

**Onderbreking:** het aantal dagen waarna de registratieuitnodiging verloopt als de externe gebruiker niet registreert. De standaardwaarde is 30 dagen.

**Bericht:** de tekst die in het lichaam van het bericht verschijnt uitnodigend de gebruiker om te registreren.

### Instellingen voor e-mail activeren {#activation-email-settings}

Nadat uitgenodigde gebruikers zich hebben geregistreerd, verzendt de documentbeveiliging een activeringse-mail. Het activeringsbericht bevat een koppeling naar de pagina voor accountactivering waar gebruikers hun account kunnen activeren. Wanneer de accounts zijn geactiveerd, kunnen gebruikers zich aanmelden bij de documentbeveiliging met hun e-mailadres en het wachtwoord dat ze hebben gemaakt bij de registratie.

Wanneer de ontvanger de gebruikersaccount activeert, wordt de gebruiker een lokale gebruiker.

De volgende instellingen bevinden zich in het gedeelte Configuratie via e-mail activeren van de pagina Uitgenodigde gebruikersregistratie.

>[!NOTE]
>
>Het wordt ook aanbevolen dat u een bericht op het aanmeldingsscherm configureert om externe gebruikers te adviseren hoe zij hun beheerder kunnen raadplegen voor een nieuw wachtwoord of voor andere informatie.

**van:** Het e-mailadres waarvan activeringse-mail wordt verzonden. Dit e-mailadres ontvangt berichten over mislukte levering van de e-mailhost van de registrant en ook alle berichten die de ontvanger verzendt als antwoord op de registratie-e-mail. Het standaardformaat van Van e-mailadres is postmaster@ [ your_installation_domain ].com.

**Onderwerp:** Standaardonderwerp voor het activeringse-mailbericht.

**Onderbreking:** het aantal dagen waarna de activeringsuitnodiging verloopt als de gebruiker niet de rekening activeert. De standaardwaarde is 30 dagen.

**Bericht:** de tekst die in het lichaam van het bericht verschijnt een bericht erop wijzend dat de de gebruikersrekening van de ontvanger moet worden geactiveerd. Mogelijk wilt u ook informatie opnemen, zoals hoe u contact opneemt met een beheerder om een nieuw wachtwoord te verkrijgen.

### E-mail voor opnieuw instellen van wachtwoord configureren {#configure-a-password-reset-email}

Als u het wachtwoord van een uitgenodigde gebruiker opnieuw moet instellen, wordt een bevestigingsmail geproduceerd die de gebruiker uitnodigt om een nieuw wachtwoord te kiezen. Het wachtwoord van een gebruiker kan niet worden bepaald; als de gebruiker het vergeet, moet u het terugstellen.

De volgende instellingen bevinden zich in het gebied Wachtwoord opnieuw instellen in de pagina Uitgenodigde gebruikersregistratie.

**van:** Het e-mailadres waarvan het wachtwoord terugstellende e-mail wordt verzonden. Het standaardformaat van Van e-mailadres is postmaster@ [ your_installation_domain ].com.

**Onderwerp:** Standaardonderwerp voor het terugstellings e-mailbericht.

**Bericht:** de tekst die in het lichaam van het bericht verschijnt een bericht erop wijzend dat het externe gebruikerswachtwoord van de ontvanger wordt teruggesteld.

## Gebruikers en groepen toestaan beleidsregels te maken {#enable-users-and-groups-to-create-policies}

De pagina van de Configuratie heeft een verbinding aan de Mijn pagina van Beleid, waar u specificeert welke eind - gebruikers mijn beleid kunnen tot stand brengen en welke gebruikers en groepen in onderzoeksresultaten zichtbaar zijn. De pagina Mijn beleid heeft twee tabbladen:

**creeer Beleid tabel:** Gebruik om gebruikerstoestemmingen te vormen om douanebeleid tot stand te brengen.

**Zichtbare Gebruikers en Groepen tabel:** Gebruik om te controleren welke gebruikers en groepen in de resultaten van het gebruikersonderzoek zichtbaar zijn. De supergebruiker of de beheerder van de beleidsreeks wordt vereist om domeinen, die in Beheer van de Gebruiker worden gecreeerd, aan de zichtbare gebruiker en de groep voor elke beleidsreeks te selecteren en toe te voegen. Deze lijst is zichtbaar aan de coördinator van de beleidsreeks en wordt gebruikt om grenzen te zetten op welke domeinen de coördinator van de beleidsreeks kan doorbladeren wanneer het kiezen van gebruikers om aan beleid toe te voegen.

Alvorens gebruikers toestemming te geven om douanebeleid tot stand te brengen, overweeg hoeveel toegang of controle u individuele gebruikers wilt hebben. Overweeg bovendien hoe zichtbaar u uw gebruikers en groepen wilt maken wanneer u ze zichtbaar maakt voor zoekopdrachten.

### Gebruikers en groepen opgeven die beleidsregels kunnen maken {#specify-users-and-groups-who-can-create-policies}

Als beheerder, specificeer welke gebruikers en groepen douanebeleid kunnen tot stand brengen. Deze machtiging kan op gebruiker- en groepsniveau worden ingesteld. De zoekfunctionaliteit zoekt in de gebruikersbeheerdatabase naar gebruikers en groepen.

1. Klik in de beheerconsole op Services > Documentbeveiliging > Configuratie > Mijn beleid.
1. Voor de Mijn pagina van Beleid, klik het Create lusje van Beleid en klik toevoegen Gebruikers en Groepen.
1. Typ in het vak Zoeken de gebruikersnaam of het e-mailadres van de gebruiker of groep waarnaar u zoekt. Als u deze informatie niet hebt, laat u het vakje leeg. U kunt ook een gedeeltelijke naam of een e-mailadres typen, bijvoorbeeld wanneer u alleen de eerste twee letters van een gebruikersnaam kent.
1. Selecteer in de lijst Gebruiken de naam van uw zoekparameters of E-mail.
1. Selecteer in de lijst Type de optie Groep of Gebruiker om uw zoekopdracht te beperken.
1. Selecteer in de lijst In het domein dat u wilt zoeken. Selecteer Alle domeinen als u het domein van de gebruiker of groep niet kent.
1. Geef in de lijst Weergave het aantal zoekresultaten op dat per pagina moet worden weergegeven en klik op Zoeken.
1. Om Mijn gebruikers en groepen van Beleid toe te voegen, selecteer de controledoos voor elke gebruiker en groep om toe te voegen.
1. Klik op Toevoegen en vervolgens op OK.

De geselecteerde gebruikers en groepen hebben nu toestemming om aangepast beleid te maken.

### De machtiging Aangepast beleid maken van een gebruiker of groep verwijderen {#remove-the-create-custom-policies-permission-from-a-user-or-group}

1. Voor de pagina van de documentveiligheid, klik Configuratie > Mijn Beleid.
1. Klik op het tabblad Beleid maken op de pagina Mijn beleid. Gebruikers en groepen met machtigingen om aangepaste beleidsregels te maken, worden weergegeven.
1. Schakel het selectievakje in naast de gebruikers en groepen die u van deze machtiging wilt verwijderen.
1. Klik op Verwijderen en vervolgens op OK.

### Gebruikers en groepen opgeven die zichtbaar zijn in zoekopdrachten {#specify-users-and-groups-that-are-visible-in-searches}

Wanneer gebruikers hun douanebeleid beheren, kunnen zij naar gebruikers en groepen zoeken om aan hun beleid toe te voegen. Geef de domeinen op waaruit gebruikers en groepen zichtbaar zijn in deze zoekopdrachten.

1. Voor de pagina van de documentveiligheid, klik Configuratie > Mijn Beleid.
1. Voor de Mijn pagina van Beleid, klik de Zichtbare Gebruikers en de Groepen tabel.
1. Als u de gebruikers en groepen in een domein zichtbaar wilt maken, klikt u op Domeinen toevoegen, selecteert u de domeinen en klikt u op Toevoegen. Als u een domein wilt verwijderen, schakelt u het selectievakje naast de domeinnaam in en klikt u op Verwijderen.

## Het configuratiebestand voor documentbeveiliging handmatig bewerken {#manually-editing-the-document-security-configuration-file}

U kunt de configuratiegegevens die in de documentbeveiligingsdatabase zijn opgeslagen, importeren en exporteren. U kunt bijvoorbeeld een reservekopie maken van de configuratiegegevens wanneer u overschakelt van een testomgeving naar een productieomgeving, of u kunt geavanceerde opties bewerken die alleen kunnen worden geconfigureerd om dit bestand te bewerken.

U kunt de volgende wijzigingen aanbrengen met behulp van het configuratiebestand:

[CATIA-machtigingen weergeven bij het maken en bewerken van beleid](configuring-client-server-options.md#display-catia-permissions-when-creating-and-editing-policies)

[Een time-outperiode voor offline synchronisatie opgeven](configuring-client-server-options.md#specify-a-timeout-period-for-offline-synchronization)

[Documentbeveiligingsservices weigeren voor specifieke toepassingen](configuring-client-server-options.md#denying-document-security-services-for-specific-applications)

[De configuratieparameters van het watermerk wijzigen](configuring-client-server-options.md#change-the-watermark-configuration-parameters)

[Externe koppelingen uitschakelen](configuring-client-server-options.md#disabling-external-links)

>[!NOTE]
>
>Wanneer u het configuratiebestand importeert, wordt uw systeem op basis van de gegevens in het bestand opnieuw geconfigureerd. De uitzonderingen zijn dynamische watermerkconfiguratie en informatie van douanegebeurtenissen, die niet met het uitgevoerde configuratiedossier worden bewaard. Configureer deze gegevens handmatig in uw nieuwe systeem. Slechts zou een systeembeheerder of een professionele de dienstenconsultant die met documentveiligheid en XML vertrouwd is de inhoud van een configuratiedossier, zoals om een bedorven plaatsen opnieuw te vormen of parameters voor een bepaald scenario van de ondernemingsplaatsing te stemmen moeten wijzigen.

**Uitvoer een configuratiedossier**

1. Klik in de beheerconsole op Services > Documentbeveiliging 11 > Configuratie > Handmatige configuratie.
1. Klik op Exporteren en sla het configuratiebestand op een andere locatie op. De standaardbestandsnaam is config.xml.
1. Klik op OK.
1. Voordat u het configuratiebestand wijzigt, moet u een reservekopie maken voor het geval u het bestand moet herstellen.

**de Invoer een configuratiedossier**

1. Klik in de beheerconsole op Services > Documentbeveiliging 11 > Configuratie > Handmatige configuratie.
1. Klik doorbladeren om naar het configuratiedossier te gaan en dan de Invoer te klikken. U kunt het pad niet rechtstreeks in het vak Bestandsnaam typen.
1. Klik op OK.

### Een time-outperiode voor offline synchronisatie opgeven {#specify-a-timeout-period-for-offline-synchronization}

Met documentbeveiliging kunnen gebruikers beveiligde documenten openen en gebruiken als ze geen verbinding hebben met de documentbeveiligingsserver. De clienttoepassing van de gebruiker moet regelmatig synchroniseren met de server om documenten geldig te houden voor offline gebruik. De eerste keer dat gebruikers een beveiligd document openen, wordt hen gevraagd of hun computer geautoriseerd moet zijn om periodieke clientsynchronisatie uit te voeren.

Standaard vindt de synchronisatie automatisch om de vier uur plaats en zo nodig wanneer een gebruiker is verbonden met de documentbeveiligingsserver. Als de offlineperiode voor een document verloopt terwijl de gebruiker offline is, moet de gebruiker opnieuw verbinding maken met de server om de clienttoepassing in staat te stellen met de server te synchroniseren.

In het configuratiebestand voor documentbeveiliging kunt u de standaardfrequentie van de automatische achtergrondsynchronisatie opgeven. Deze instelling fungeert als de standaardtime-outperiode voor clienttoepassingen, tenzij de client expliciet een eigen time-outwaarde instelt.

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het knooppunt `PolicyServer` . Zoek onder dat knooppunt het knooppunt `ServerSettings` .
1. Voeg de volgende vermelding toe aan het knooppunt `ServerSettings` en sla het bestand op:

   `<entry key="BackgroundSyncFrequency" value="`*tijd* `"/>`

   waar *tijd* het aantal seconden tussen automatische achtergrondsynchronisaties is. Als u deze waarde naar `0` hebt verzonden, vindt synchronisatie altijd plaats. De standaardwaarde is `14400` seconden (elke vier uur).

1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Documentbeveiligingsservices weigeren voor specifieke toepassingen {#denying-document-security-services-for-specific-applications}

U kunt documentveiligheid vormen om de diensten aan toepassingen te ontkennen die aan specifieke criteria voldoen. De criteria kunnen één enkel attribuut zoals een platformnaam specificeren of het kan veelvoudige reeksen attributen specificeren. Deze functie kan u helpen de verzoeken te controleren documentveiligheid moet behandelen. Hier volgen enkele toepassingen van deze functie:

* **de bescherming van de Inkomsten:** u kunt toegang tot om het even welke cliënttoepassing willen ontkennen die uw opbrengstovereenkomsten niet steunt.
* **de verenigbaarheid van de Toepassing:** sommige toepassing kan met het beleid of het gedrag van uw server van de documentveiligheid onverenigbaar zijn.

Wanneer clienttoepassingen proberen een koppeling tot stand te brengen met documentbeveiliging, bieden ze toepassings-, versie- en platforminformatie. Bij documentbeveiliging wordt deze informatie vergeleken met de instellingen voor weigeringen die worden verkregen uit het configuratiebestand voor documentbeveiliging.

De ontkenningsinstellingen kunnen verschillende sets ontkenningsvoorwaarden bevatten. Als alle kenmerken van een set overeenkomen, krijgt de toepassing die het verzoek indient, geen toegang tot de documentbeveiligingsservices.

De ontkenning-van-dienst eigenschap vereist dat de cliënttoepassingen de document veiligheid C++ versie van SDK 8.2 of later gebruiken. De volgende Adobe-producten bieden productinformatie wanneer u beveiligingsservices voor documenten aanvraagt:

* Adobe Acrobat 9.0 Professional/Acrobat 9.0 Standard of hoger
* Adobe Reader 9.0 of hoger
* Acrobat Reader DC-extensies voor Microsoft Office 8.2 en hoger

Clienttoepassingen gebruiken de client-API van de C++ Client SDK voor documentbeveiliging om services aan te vragen bij documentbeveiliging. De client-API-aanvragen bevatten platform- en SDK-versiegegevens (vooraf gecompileerd in de client-API) en productgegevens die zijn verkregen van de clienttoepassing.

De toepassingen of stop-ins van de cliënt verstrekken productinformatie in hun implementatie van een callback functie. De toepassing biedt de volgende informatie:

* Integrator-naam
* Integrator-versie
* Toepassingsfamilie
* Toepassingsnaam
* Toepassingsversie

Als er geen informatie van toepassing is, laat de clienttoepassing het desbetreffende veld leeg.

Verschillende Adobe-toepassingen bevatten productinformatie wanneer u documentbeveiligingsservices aanvraagt, waaronder Acrobat, Adobe Reader en Acrobat Reader DC-extensies voor Microsoft Office.

**Acrobat en de Lezer van Adobe**

Wanneer Acrobat of Adobe Reader een aanvraag indienen voor een documentbeveiliging, wordt de volgende productinformatie verschaft:

* **Integrator:** Adobe Systems, Inc.
* **versie van de Integrator:** 1.0
* **familie van de Toepassing:** Acrobat
* **naam van de Toepassing:** Acrobat
* **versie van de Toepassing:** 9.0.0

**de uitbreidingen van gelijkstroom van de Reader van de Acrobaat voor Microsoft Office**

Acrobat Reader DC-extensies voor Microsoft Office is een insteekmodule die wordt gebruikt met de Microsoft Office-producten Microsoft Word, Microsoft Excel en Microsoft PowerPoint. Wanneer het om de dienst verzoekt, verstrekt het de volgende informatie:

* **Integrator:** Adobe Systems Incorporated
* **versie van de Integrator:** 8.2
* **de familie van de Toepassing:** de uitbreidingen van de Reader van de Acrobaat gelijkstroom voor Microsoft Office
* **naam van de Toepassing:** Microsoft Word, Microsoft Excel, of Microsoft PowerPoint
* **versie van de Toepassing:** 2003 of 2007

**vorm documentveiligheid om de diensten voor specifieke toepassingen te ontkennen**

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het knooppunt `PolicyServer` . Voeg een knooppunt `ClientVersionRules` toe als een direct onderliggend knooppunt van het knooppunt `PolicyServer` , als dat niet bestaat:

   ```xml
    <node name="ClientVersionRules">
        <map>
            <entry key="infoURL" value="URL"/>
        </map>
        <node name="Denials">
            <map/>
            <node name="MyEntryName">
                <map>
                    <entry key="SDKPlatforms" value="platforms"/>
                    <entry key="SDKVersions" value="versions"/>
                    <entry key="AppFamilies" value="families"/>
                    <entry key="AppNames" value="names"/>
                    <entry key="AppVersions" value="versions"/>
                    <entry key="Integrators" value="integrators"/>
                    <entry key="IntegratorVersions" value="versions"/>
                </map>
            </node>
            <node name="MyOtherEntryName"
                <map>
                    [...]
                </map>
            </node>
            [...]
        </node>
    </node>
   ```

   waarbij:

   `SDKPlatforms` geeft het platform aan dat als host fungeert voor de clienttoepassing. Mogelijke waarden zijn:

   * Microsoft Windows
   * APPLE OS X
   * Sun Solaris
   * HP-UX

   `SDKVersions` geeft de versie op van de C++-client-API voor documentbeveiliging die door de clienttoepassing wordt gebruikt. Bijvoorbeeld `"8.2"` .

   `APPFamilies` wordt gedefinieerd door de client-API.

   `AppName` specificeert de naam van de cliënttoepassing. Komma&#39;s worden gebruikt als naamscheidingstekens. Als u een komma in een naam wilt opnemen, plaatst u een backslash (\) als escape-teken. Bijvoorbeeld, *&quot;Adobe Systems\, Inc.&quot;*.

   `AppVersions` geeft de versie van de clienttoepassing aan.

   `Integrators` geeft de naam op van het bedrijf of de groep die de plug-in of geïntegreerde toepassing heeft ontwikkeld.

   `IntegratorVersions` is de versie van de plug-in of de geïntegreerde toepassing.

1. Voor elke extra reeks ontkenningsgegevens, voeg een ander *MyEntryName* element toe.
1. Sla het configuratiebestand op.
1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

**Voorbeelden**

In dit voorbeeld worden alle Windows-clients toegang geweigerd.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://www.dont.use/windows.html"/>
     </map>
     <node name="Denials">
         <map/>
         <node name="Entry_1">
             <map>
                 <entry key="SDKPlatforms" value="Microsoft Windows"/>
             </map>
         </node>
     </node>
 </node>
```

In dit voorbeeld wordt mijn toepassingsversie 3.0 en Mijn andere toepassingsversie 2.0 toegang geweigerd. De zelfde ontkenningsinformatie URL wordt gebruikt ongeacht de reden voor ontkenning.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://get.a.new/version.html"/>
     </map>
     <node name="Denials">
         <map/>
         <node name="FirstDenialSettings">
             <map>
                 <entry key="AppNames" value="My Application"/>
                 <entry key="AppVersions" value="3.0"/>
             </map>
         </node>
         <node name="SecondDenialSettings">
             <map>
                 <entry key="AppNames" value="My Other Application"/>
                 <entry key="AppVersions" value="2.0"/>
             </map>
         </node>
     </node>
 </node>
```

In dit voorbeeld worden alle aanvragen van een Microsoft PowerPoint 2007- of Microsoft PowerPoint 2010-installatie van Acrobat Reader DC-extensies voor Microsoft Office afgewezen.

```xml
 <node name="ClientVersionRules">
     <map>
         <entry key="infoURL" value="https://get.a.new/version.html"/>
     </map>
     <node name="Denials">
         <map/>
         <node name="Entry_1">
             <map>
                 <entry key="AppFamilies" value=
     "document security Extension for Microsoft Office"/>
                 <entry key="AppNames" value= "Microsoft PowerPoint"/>
                 <entry key="AppVersions" value="2007,2010"/>
             </map>
         </node>
     </node>
 </node
```

### De configuratieparameters van het watermerk wijzigen {#change-the-watermark-configuration-parameters}

Standaard kunt u maximaal vijf elementen in een watermerk opgeven. Bovendien is de maximale bestandsgrootte van het PDF-document dat u als watermerk wilt gebruiken, beperkt tot 100 kB. U kunt deze parameters in het config.xml- dossier veranderen.

***nota &#x200B;**: U zou deze parameters met voorzichtigheid moeten veranderen.*

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het knooppunt `ServerSettings` .
1. Voeg in het knooppunt `ServerSettings` de volgende items toe en sla het bestand op: `<entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/> <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>`

   De eerste ingang, *maximum dossiergrootte* is de maximumdossiergrootte (in KB) die voor een element van het watermerk van PDF wordt toegestaan. De standaardwaarde is 100 kB.

   De tweede ingang, *maximum elementen* is het maximumaantal elementen dat in een watermerk wordt toegestaan. De standaardwaarde is 5.

   ```xml
   <entry key="maximumSizeOfWatermarkElement" value="max filesize in KB"/>
   <entry key="maximumWatermarkElementsPerWatermark" value="max elements"/>
   ```

1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Externe koppelingen uitschakelen {#disabling-external-links}

Vele gebruikers van de documentveiligheid hebben geen toegang tot externe verbindingen zoals **www.adobe.com** terwijl zij het juiste gebruikersinterface van het Beheer gebruiken:

* `https://[host]:'port'/adminui`
* `https://[host]:'port'/edc`.

De volgende veranderingen in config.xml schakelen alle externe verbindingen van het Juiste gebruikersinterface van het Beheer uit.

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het knooppunt `DisplaySettings` .
1. Als u alle externe koppelingen wilt uitschakelen, voegt u in het knooppunt `DisplaySettings` de volgende vermelding toe en slaat u het bestand op: `<entry key="ExternalLinksAllowed" value="false"/>`

   ```xml
   <entry key="ExternalLinksAllowed" value="false"/>
   ```

1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### Configuratie om SMTP voor de Veiligheid van de Laag van het Vervoer (TLS) toe te laten {#configuration-to-enable-smtp-for-transport-layer-security-tls}

De volgende veranderingen in config.xml laten TLS steun voor de Uitgenodigde eigenschap van de Registratie van de Gebruiker toe.

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het knooppunt `DisplaySettings` .
1. Zoek het volgende knooppunt: `<node name="ExternalUser">`

   ```xml
   <node name="ExternalUser">
   ```

1. Plaats de waarde van de `SmtpUseTls` sleutel in de `ExternalUser` knoop aan **waar**.
1. Plaats de waarde van de `SmtpUseSsl` sleutel in de `ExternalUser` knoop aan **vals**.
1. Sla de `config.xml` op.
1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### SOAP-eindpunten uitschakelen voor documenten met documentbeveiliging {#disable-soap-endpoints-for-document-security-documents}

De volgende veranderingen in config.xml om SOAP eindpunten voor documenten van de documentveiligheid onbruikbaar te maken.

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiebestand in een editor en zoek het volgende knooppunt: `<node name="DRM">`

   ```xml
   <node name="DRM">
   ```

1. Zoek in het DRM-knooppunt het knooppunt `entry` :

   `<entry key="AllowUnencryptedVoucher" value="true"/>`

1. Om SOAP eindpunten voor documenten van de documentveiligheid onbruikbaar te maken, plaats de waardeattributen aan **vals**.

   ```xml
   <node name="DRM">
       <map>
           <entry key="AllowUnencryptedVoucher" value="false"/>
       </map>
   </node>
   ```

1. Sla de `config.xml` op.
1. Importeer het configuratiebestand. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)

### De schaalbaarheid van de documentbeveiligingsserver verhogen {#increasingscalability}

Door gebrek, terwijl het synchroniseren van een document voor off-line gebruik, samen met de informatie voor huidig document, halen de cliënten van de documentveiligheid beleid, watermerken, vergunningen en herroeping bijgewerkte informatie voor alle andere documenten die de gebruiker toegang heeft tot. Als deze updates en informatie niet met de cliënt wordt gesynchroniseerd, dan kan een document dat op off-line wijze wordt geopend nog met ouder beleid, watermerk, en intrekkingsinformatie openen.

U kunt de scalability van de server van de documentveiligheid verhogen door de informatie te beperken die naar de cliënt wordt verzonden. De vermindering van de hoeveelheid informatie die naar de client wordt verzonden, resulteert in een verbeterde schaalbaarheid, een kortere responstijd en betere prestaties van de server. Voer de volgende stappen uit om de schaalbaarheid te verhogen:

1. Exporteer het configuratiebestand voor documentbeveiliging. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
1. Open het configuratiedossier in een redacteur en bepaal de plaats van de knoop ServerSettings.
1. In de knoop ServerSettings, plaats de waarde van het `DisableGlobalOfflineSynchronizationData` bezit aan `true`.

   `<entry key="DisableGlobalOfflineSynchronizationData" value="true"/>`

   Wanneer ingesteld op true, verzendt de documentbeveiligingsserver alleen informatie voor het huidige document en wordt de informatie voor de rest van de documenten (de andere documenten waartoe een gebruiker toegang heeft) niet naar de client verzonden.

   >[!NOTE]
   >
   >Standaard wordt de waarde van de `DisableGlobalOfflineSynchronizationData` -toets ingesteld op `false` .

1. Sla het configuratiebestand op en importeer het. (Zie [ manueel het uitgeven van het dossier van de documentveiligheidsconfiguratie ](/help/forms/using/admin-help/configuring-client-server-options.md#manually-editing-the-document-security-configuration-file).)
