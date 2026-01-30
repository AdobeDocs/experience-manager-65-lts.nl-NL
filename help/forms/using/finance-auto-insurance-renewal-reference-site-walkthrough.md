---
title: We.Doorloop van de referentiewebsite voor Verzekering van financiële automatische vernieuwing
description: Leer over de "Wij.Finance"AutoVerzekering Verlenging verwijzingsplaats door een analyse te nemen.
contentOwner: dekalra
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Foundation Components
role: User, Developer
exl-id: 3f9f1a20-9029-4e30-9c9d-ef452512f7e9
source-git-commit: c0bf6864bb344e582c4f88371c892d401ce2827c
workflow-type: tm+mt
source-wordcount: '744'
ht-degree: 0%

---

# `We.Finance` Doorloop van de verwijzingssite voor automatisch vernieuwen van verzekering{#we-finance-auto-insurance-renewal-reference-site-walkthrough}

## `We.Finance` Referentiescenario  {#we-finance-reference-site-scenario}

De website van `We.Finance` is een site voor financiële services die u helpt de interactieve communicatiemogelijkheden van AEM Forms te leren kennen.

Lees een uitgebreide analyse van een `We.Finance` Auto Insurance use case die laat zien hoe AEM-formulieren en de integratie ervan met Microsoft® Dynamics de klantervaring in een bedrijf voor financiële services kunnen personaliseren. De interactieve analyse wordt ontworpen om implementatie van complexe digitale transacties en klantenmededeling in een financieel bedrijf te vergemakkelijken.

**de reis begint met het gebruiksgeval:**

Sarah Rose is een bestaande `We.Finance` klant en heeft een automatisch verzekeringsbeleid gekocht. Het is die tijd van het jaar dat Sarah haar verzekeringspolis vernieuwt. Gloria Rios is haar verzekeringsagent. De website van `We.Finance` brengt een herinnering aan Sarah over haar beleidsvernieuwing in een e-mail. Sarah volgt de instructies in de e-mail en voltooit het proces.

## Doorloop van toepassing voor automatische verzekering {#auto-insurance-application-walkthrough}

Het toepassingsscenario `We.Finance` Automatische verzekering is een visueel commentaar voor de gebruiker en is gebaseerd op twee personen:

* Sarah Rose, een `We.Finance` klant
* Gloria Rios, verzekeringsagent, `We.Finance`

### Gloria verzendt een mededeling van de vernieuwing van het Verzekeringsbeleid van `We.Finance` {#gloria-sends-an-insurance-policy-renewal-communication-from-we-finance}

Gloria registreert in de instantie van AEM, klikt **Auto Verzekering Vernieuwen,** en klikt dan **Open Agent UI**. Klik vooraf vult het verzekeringsdocument met beleidsdetails van Sarah Rose. Gloria klikt **voorlegt** en een bericht wordt getoond op het scherm &quot;Verzending geïnitieerd&quot;en dan in een paar seconden &quot;met succes voorgelegd.&quot;

Sarah ontvangt een e-mail met het onderwerp &quot;Uw automatische Verzekering Verlenging.&quot;

![ Agent UI ](assets/agent_ui_email_new.png)

#### Zie het zelf {#see-it-yourself}

Ga naar **Adobe Experience Manager** > **Forms** > **Forms &amp; Documenten** > **`We.Finance`** > **Auto Verzekering**. Selecteer de Auto Verzekering Verlenging **interactieve mededeling** en klik **Open Agent UI**. De interactieve mededeling opent omhoog in de Agent UI. Voer een geldig e-mailadres in, zodat ze het e-mailbericht kunnen ontvangen met het bijgevoegde beleidsdocument en op Verzenden kunnen klikken.

U hebt rechtstreeks vanuit `https://[authorHost]: authorPort]/aem/formdetails.html/content/dam/formsanddocuments/we-finance/autoinsurance/auto-insurance-renewal.` toegang tot de interactieve communicatie voor automatisch vernieuwen en deze reviseren

### Sarah ontvangt een mededeling over de verlenging van een verzekeringspolis van `We.Finance` en besluit te verlengen {#sarah-receives-an-insurance-policy-renewal-communication-from-we-finance-and-decides-to-renew}

Sarah ontvangt een e-mail met een bijlage van `We.Finance` en herinnert Sarah eraan dat haar beleid voor automatische verzekering op het punt staat te verlopen. De bijlage is de afdrukversie van Sarah&#39;s Auto Insurance letter.

Sarah klikt de optie **nu Verlengen** en wordt gericht aan de Webversie van haar Auto brief van de Verzekering. Naast deze brief, vindt Sarah de hoeveelheid tijd in het beleid alvorens het verloopt. De pagina geeft een overzicht van de verzekeringspolis. Het detailleert het Aantal van het Beleid, het Verschuldigde Bedrag, kortingsaanbiedingen, en loyaliteitsbeloningen. **vernieuw nu** wordt geklikt bij de bodem van het beleid.

![ ref1 ](assets/ref1.png)

#### Hoe werkt het {#how-it-works}

Het web en de afdrukuitvoer van de brief voor automatische verzekering worden gemaakt met behulp van de multikanaalsmogelijkheden van interactieve communicatie.

De knop Nu vernieuwen in de e-mail is gekoppeld aan de toepassing voor automatisch vernieuwen van verzekeringen. Dit is een interactieve communicatie over een publicatie-instantie.

#### Zie het zelf {#see-it-yourself-1}

U moet een e-mail hebben ontvangen met een bijgevoegde PDF. De PDF is een afdrukversie van je brief voor automatische verzekering. Klik **nu Verlengen** om aan de Webversie van het beleid te bereiken. Controleer uw persoonlijke informatie en beleidsdetails en klik **nu Vernieuwen** die u aan een andere interactieve mededeling neemt.

De **verlengt nu** knoop in e-mail leidt Sarah aan het beleid op het Web. U kunt de volgende URL bezoeken:

`https://[authorServer]:[authorPort]/content/document.html?schema=fdm&documentId=/content/forms/af/we-finance/autoinsurance/auto-insurance-renewal/channels/web.html&customerId=1`

U kunt de gedetailleerde samenvatting van uw Auto Verzekering Verlenging controleren en **klikken nu** bij de bodem van de pagina vernieuwen.

### Sarah bereikt de betalingspagina {#sarah-reaches-the-payment-page}

De `We.Finance` -website neemt Sarah naar de betalingspagina. Sarah controleert haar Aantal van het Beleid en Datum van Vervalsing met haar verslagen opnieuw. Aan de rechterkant van de pagina controleert Sarah het Betalingsoverzicht van de verlenging met een premiekorting van 10% op het totale bedrag.

#### Hoe werkt het {#how-it-works-1}

Met de knop Nu vernieuwen wordt Sarah naar de betalingspagina geleid. De betalingspagina is een adaptief formulier.

#### Zie het zelf {#see-it-yourself-2}

Klik **nu Verlengen** om aan de pagina van de Betaling te bereiken. Vul uw informatie van de Creditcard in, en klik **maak Betaling**.

U kunt de betalingspagina bereiken in de ontwerpinstantie op

`https://[authorServer]:[authorPort]/content/document.html?documentId=/content/forms/af/we-finance/credit-card/ccbillpayment.html&schema=fdm&customerId=1`

### Sarah doet de betaling en voltooit het proces {#sarah-makes-the-payment-and-completes-the-process}

Sarah vult haar details van de Creditcard en klikt **Betaling** maken.

#### Hoe werkt het {#how-it-works-2}

Wanneer Sarah de creditcardgegevens invult en op Indienen klikt, wordt de betaling van haar creditcard verwerkt en verschijnt een bedankbericht dat in het adaptieve formulier is geconfigureerd, op het scherm.

#### Zie het zelf {#see-it-yourself-3}

Je kunt het bevestigingsbericht bekijken nadat je op Betaling maken hebt geklikt op

`https://[authorServer]:[authorPort]/content/forms/af/we-finance/credit-card/ccbillpayment/jcr:content/guideContainer.guideThankYouPage.html?owner=admin&status=Submitted`
