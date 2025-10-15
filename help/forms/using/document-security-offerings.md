---
title: Beveiligingsaanbod van documenten
description: Meer informatie over de verschillende gereedschappen en functies van AEM Document Security.
contentOwner: khsingh
geptopics: SG_AEMFORMS/categories/working_with_document_security
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
docset: aem65
feature: Document Security
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: 6653649a-5076-48e3-a7ed-5b74d4d2e8e1
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '1161'
ht-degree: 0%

---

# Beveiligingsaanbod van documenten{#document-security-offerings}

Met de beveiliging van Adobe Experience Manager Forms-documenten kunt u ervoor zorgen dat alleen geautoriseerde gebruikers uw documenten kunnen gebruiken. Met documentbeveiliging kunt u veilig alle informatie verspreiden die u in een ondersteunde indeling hebt opgeslagen. Tot de ondersteunde bestandsindelingen behoren Adobe Portable Document Format (PDF) en Microsoft® Word-, Excel- en PowerPoint-bestanden.

U kunt documenten beschermen door beleid te gebruiken. De vertrouwelijkheidsmontages die u in een beleid specificeert bepalen hoe een ontvanger een document kan gebruiken waarop u het beleid toepast. U kunt bijvoorbeeld opgeven of ontvangers tekst kunnen afdrukken of kopiëren, tekst kunnen bewerken of handtekeningen en opmerkingen kunnen toevoegen aan beveiligde documenten.

Het beleid wordt opgeslagen op de Document Security-server. U past het beleid toe op documenten via de clienttoepassing. Wanneer u een beleid op een document toepast, beschermen de vertrouwelijkheidsmontages die in het beleid worden gespecificeerd de informatie die het document bevat. U kunt het document dat met een beleid is beveiligd, verspreiden onder ontvangers die door het beleid zijn gemachtigd.

In het volgende diagram ziet u de typische architectuur voor AEM Forms Document Security:

![&#x200B; Veiligheid van het Document - Geadviseerde architectuur &#x200B;](do-not-localize/document_security_architecture.png)

## Documentbeveiligingsclients {#document-security-clients}

Documentbeveiliging biedt verschillende clients om documenten te beveiligen, beveiligde documenten weer te geven en te bewerken, en indexeerders om zoeken in volledige tekst op beveiligde documenten mogelijk te maken. U kunt een client kiezen op basis van uw vereisten en de mogelijkheden van de client.

De server van de Veiligheid van het Document is de centrale component waardoor de Veiligheid van het Document transacties zoals gebruikersauthentificatie, beheer in real time van beleid, en toepassing van vertrouwelijkheid uitvoert. De server biedt ook een centrale opslagplaats voor beleidsregels, auditrecords en andere gerelateerde informatie.

De server van de Veiligheid van het Document verstrekt een web-based interface (Web-pagina) om beleid tot stand te brengen, beleid-beschermde documenten te beheren, en gebeurtenissen te controleren die met beleid-beschermde documenten worden geassocieerd. Beheerders kunnen ook globale opties configureren, zoals gebruikersverificatie, controle en berichten voor uitgenodigde gebruikers, en uitgenodigde gebruikersaccounts beheren.

De server is opgenomen in de add-on service voor documentbeveiliging van AEM Forms. U kunt AEM Forms [&#x200B; verkoopteam &#x200B;](https://business.adobe.com/nl/request-consultation/experience-cloud.html?s_osc=70114000002JNwKAAW&s_iid=70114000002JHs3AAG) contacteren om de Veiligheid toe:voegen-op van het Document te kopen.

### Documenten beveiligen {#protect-documents}

AEM Forms Document Security biedt verschillende gereedschappen om beveiligingsbeleid toe te passen. U kunt een gereedschap kiezen op basis van uw vereisten en specificaties.

![&#x200B; document-veiligheid-dienstenaanbod &#x200B;](assets/document-security-offerings.png)

Met Document Security SDK, Adobe Acrobat, Document Security Extension for Microsoft® Office of Portable Protection Library kunt u het beveiligingsbeleid toepassen en volgen:

* **de Veiligheid SDK van het Document:** SDK is een eigenschap-rijke cliënt. Met de Document Security SDK kunt u toegang krijgen tot de functionaliteit van de documentserver, documenten die met een beleid zijn beveiligd openen en aangepaste extensies, plug-ins of toepassingen ontwikkelen. U kunt bijvoorbeeld extensies ontwikkelen om aangepaste bestandsindelingen te beschermen of de SDK met DLP-oplossingen (Data Loss Prevention) te integreren. Extensies, toepassingen en insteekmodules die zijn ontwikkeld met de Document Security SDK om documenten naar de aangewezen AEM Forms Server te verzenden en het beleid wordt toegepast op de server. De AEM Forms-documentbeveiligingsclient SDK (CSDK) kan de beveiliging van documenten die zijn beveiligd met de Portable Protection Library (PPL), niet opheffen, en omgekeerd.

  De Document Security SDK is beschikbaar voor zowel Java™ als C++. Java™ SDK is inbegrepen in het AEM Forms Document Security-aanbod en is geïnstalleerd bij het implementeren van AEM-formulieren op JEE. Contact [&#x200B; de Klantenondersteuning van AEM &#x200B;](https://experienceleague.adobe.com/nl?support-solution=General&support-tab=home#support) om C++ SDK te kopen. C++ SDK kan met Microsoft® Visual Studio 2013 worden gecompileerd. Bezoek de [&#x200B; API van de Veiligheid van het Document documentatie &#x200B;](https://help.adobe.com/en_US/livecycle/11.0/Services/WS92d06802c76abadb76c48dfe12dbeb3e281-7ff0.2.html) plaats waar u eigenschappen van SDK kunt leren en gebruiken.

* **Adobe Acrobat:** u kunt Adobe Acrobat gebruiken om veiligheidsbeleid op de documenten van PDF toe te passen die gebruikend populaire Desktoptoepassingen, zoals Microsoft® Office, Webbrowsers, of om het even welke toepassing worden gecreeerd die druk in formaat van PDF steunt.

  U kunt Adobe Acrobat van de [&#x200B; Website van Adobe kopen en downloaden &#x200B;](https://www.adobe.com/acrobat/free-trial-download.html). Het artikel van Adobe Acrobat [&#x200B; opstellend veiligheidsbeleid voor PDFs &#x200B;](https://helpx.adobe.com/nl/acrobat/using/setting-security-policies-pdfs.html) verstrekt gedetailleerde informatie over het creëren van en het toepassen van beleid in Adobe Acrobat.

* **Uitbreiding van de Veiligheid van het Document voor Microsoft® Office**: U kunt de Uitbreiding van de Veiligheid van het Document voor Microsoft® Office gebruiken om vooraf bepaald beleid op uw Microsoft® Office dossiers van binnen de programma&#39;s van Microsoft® Office toe te passen. De extensie zorgt ervoor dat alleen geautoriseerde personen Microsoft® Word-, Excel- en PowerPoint-bestanden die met een beleid zijn beveiligd, kunnen gebruiken. Alleen geautoriseerde gebruikers die de plug-in hebben geïnstalleerd, kunnen de bestanden gebruiken die met een beleid zijn beveiligd.

  De extensie Documentbeveiliging is beschikbaar als een Microsoft® Office-plug-in. Contact [&#x200B; de Klantenondersteuning van AEM &#x200B;](https://helpx.adobe.com/ca/marketing-cloud/contact-support.html) om de uitbreiding te verwerven. Later, kunt u {de Uitbreiding van de Veiligheid van het 0} Document voor Microsoft® Office [&#128279;](https://experienceleague.adobe.com/docs/experience-manager-document-security/using/download-installer.html?lang=nl-NL) hulp bezoeken om over het installeren, het vormen, en het gebruiken van de uitbreiding te leren.

* **Portable Protection Library:** PPL beschermt plaatselijk een document, zonder het document naar de Server van AEM Forms te verzenden. Alleen beveiligingsgegevens en beleidsdetails reizen over het netwerk. PPL laat u ook de toegang van de beleidsherwinning tot slechts het programma geopende gebruikers beperken. U kunt beleid ophalen met de context van de gebruiker die is aangemeld bij AEM.

  Samen met het bovenstaande heeft de PPL alle functies van Document Security SDK. Met de Document Security SDK kunt u toegang krijgen tot de functionaliteit van de documentserver, documenten die met een beleid zijn beveiligd openen en aangepaste extensies, plug-ins of toepassingen ontwikkelen. De PPL kan de beveiliging van documenten die zijn beveiligd met AEM Forms-documentbeveiligingsclient SDK (CSDK) en omgekeerd niet opheffen.

  De PPL is beschikbaar voor Java™- en C++-talen in 32-bits en 64-bits versies. Het is ook beschikbaar als OSGi-bundel voor AEM Forms op OSGi. C++ PPL kan met Microsoft® Visual Studio 2013 worden gecompileerd. Als u de Veiligheid van het Document van AEM Forms toe:voegen-op in licentie hebt gegeven, kunt u het [&#128279;](https://experienceleague.adobe.com/nl?support-solution=General&support-tab=home#support) ondersteuningsteam van de Veiligheid van het Document van 0&rbrace; AEM Forms contacteren om PPL te verwerven.  Later kunt u de PPL Help (meegeleverd bij de bibliotheek) gebruiken om de PPL in te stellen en te gebruiken.

### Beveiligde documenten weergeven of bewerken {#view-or-edit-protected-documents}

* Voor **documenten van PDF**, kunt u Adobe Acrobat DC, Acrobat Reader, en Acrobat Reader Mobile gebruiken om de beschermde documenten van PDF te bekijken. De meeste gebruikers hebben Acrobat Reader al op hun apparaten geïnstalleerd, zodat zij geen extra software hoeven te verkrijgen of te leren om beschermde documenten te bekijken. U kunt Acrobat Reader van de [&#x200B; downloadwebsite van Acrobat Reader &#x200B;](https://get.adobe.com/reader/) ook downloaden.

* Voor **Microsoft® Office documenten**, vereist u de uitbreiding van de Veiligheid van het Document van Microsoft® Office en van AEM Forms voor Microsoft® Office. De extensie Documentbeveiliging is beschikbaar als een Microsoft® Office-plug-in. U kunt de extensie downloaden van de Adobe-website.

### Beveiligde documenten indexeren {#index-protected-documents}

Microsoft® Windows full-text zoekprogramma&#39;s (SharePoint Index Server) en Adobe Experience Manager (AEM) kunnen full-text zoekopdrachten uitvoeren op veelgebruikte documentindelingen, zoals bestanden in onbewerkte tekst, Microsoft® Office-documenten en PDF-documenten. U kunt indexen van de Veiligheid van het Document gebruiken om fullText onderzoeksmotoren toe te laten om beschermde documenten van PDF te zoeken:

* **iFilter indexer:** u kunt de indexeerder gebruiken iFilter om beschermde documenten van PDF te indexeren en Microsoft® Windows full-text onderzoeksmotoren (de Indexerende Dienst van de Desktop en de server van de Index van SharePoint) toe te laten om beschermde documenten van PDF te zoeken. Voor gedetailleerde informatie, zie [&#x200B; AEM SharePoint IFilter voor Beschermde Documenten &#x200B;](assets/sharepoint-ifilter-doc-security.pdf).

* **Indexer van de Veiligheid van het Document van AEM Forms:** u kunt de indexeerder van de Veiligheid van het Document van AEM Forms gebruiken om beschermde documenten van PDF te indexeren en Adobe Experience Manager toe te laten om beschermde documenten van PDF te zoeken. De indexen maken deel uit van het AEM Forms Document Security-aanbod. Deze zijn opgenomen in AEM Forms op JEE-installatieprogramma&#39;s.
