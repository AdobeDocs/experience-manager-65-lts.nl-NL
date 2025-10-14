---
title: Hoe wordt Turnstile gebruikt in een AEM Adaptive Form 6.5?
description: Verbeter de formulierbeveiliging met de Turnstile-service zonder moeite. Stap-voor-stap gids binnen!
feature: Adaptive Forms, Foundation Components
role: User, Developer
exl-id: cca80e8d-496b-4d67-a90d-2eadf2931986
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '798'
ht-degree: 0%

---

# Verbind uw AEM Forms-omgeving met Turnstift {#connect-your-forms-environment-with-turnstile-service}


<span class="preview"> Deze eigenschap wordt niet toegelaten door gebrek. U kunt van uw officieel adres aan aem-forms-ea@adobe.com schrijven om toegang tot de eigenschap te verzoeken.</span>

CAPTCHA (Complete Automated Public Turing test to tell Computers and Humans Apart) is een programma dat vaak wordt gebruikt bij online transacties om onderscheid te maken tussen mensen en geautomatiseerde programma&#39;s of bots. Het stelt een uitdaging en evalueert de reactie van de gebruiker om te bepalen of het een mens of bot is die met de site communiceert. Het verhindert de gebruiker om te werk te gaan als de test ontbreekt en de hulp maakt online transacties veilig door bots te houden spam of kwaadwillige doeleinden posten.

AEM Forms ondersteunt de volgende CAPTCHA-oplossingen:

* [Turnstile Captcha](/help/forms/using/integrate-adaptive-forms-turnstile.md)
* [Google reCAPTCHA](/help/forms/using/captcha-adaptive-forms.md)
* [&#x200B; hCaptcha &#x200B;](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)


<!-- ![Turnstile](assets/Turnstile-challenge.png)-->

## AEM Forms-omgeving integreren met Turnstile Captcha

Cloudflare Turnstile Captcha is een veiligheidsmaatregel die tot doel heeft formulieren en sites te beschermen tegen geautomatiseerde bots, kwaadaardige aanvallen, spam en ongewenst geautomatiseerd verkeer. Er wordt een selectievakje weergegeven bij het verzenden van formulieren om te controleren of het formulier menselijk is, voordat het formulier kan worden verzonden.

>[!VIDEO](https://video.tv.adobe.com/v/3440946?captions=dut)

### Vereisten om de AEM Forms-omgeving te integreren met Turnstile Captcha {#prerequisite}

Om Turnstile voor AEM Forms te vormen, moet u [&#x200B; Turnstile sitekey en geheime sleutel &#x200B;](https://developers.cloudflare.com/turnstile/get-started/) van de Website van Turnstile verkrijgen.

### Draaien configureren {#steps-to-configure-hcaptcha}

Voer de volgende stappen uit om AEM Forms te integreren met de Turnstile-service:

1. Maak een configuratiecontainer op uw AEM Forms-omgeving. Een configuratiecontainer bevat cloudconfiguraties waarmee AEM Forms wordt verbonden met externe services. Een configuratiecontainer maken:
   1. Open uw AEM Forms-omgeving.
   1. Ga naar **[!UICONTROL Tools > General > Configuration Browser]** .
   1. In Browser van de Configuratie, selecteert u een bestaande omslag of creeert een nieuwe omslag:
      * Om a **nieuwe omslag** tot stand te brengen en de Configuraties van de Wolk toe te laten:
         1. Klik op **[!UICONTROL Create]** in de Configuration Browser.
         1. Geef in het dialoogvenster Configuratie maken een naam, titel en controle op **[!UICONTROL Cloud Configurations]** .
         1. Klik op **[!UICONTROL Create]**.
      * Om de Configuratie van de Wolk voor een **bestaande omslag** toe te laten:
         1. Selecteer de map in de Configuration Browser en klik op **[!UICONTROL Properties]** .
         1. Schakel in het dialoogvenster Configuration Properties **[!UICONTROL Cloud Configurations]** in.
         1. Klik op **[!UICONTROL Save & Close]** om de configuratie op te slaan.

1. Uw cloudservices configureren:
   1. Op uw de auteursinstantie van AEM, ga ![&#x200B; hulpmiddelen-1 &#x200B;](assets/tools-1.png) > **[!UICONTROL Cloud Services]** en klik **[!UICONTROL Turnstile]**.

      ![&#x200B; Draai in de Diensten van de Wolk &#x200B;](assets/turnstile-in-ui.png)
   1. Selecteer een configuratiecontainer, gecreeerd of bijgewerkt, zoals die in de vorige sectie wordt beschreven. Klik op **[!UICONTROL Create]**.

      ![&#x200B; Turnstile van de Configuratie &#x200B;](assets/config-hcaptcha.png)
   1. Geef **[!UICONTROL Widget Type]** op als beheerd, niet-interactief of onzichtbaar.
   1. Geef andere gegevens op, zoals **[!UICONTROL Title]** , **[!UICONTROL Name]** .
   1. Specificeer **[!UICONTROL Site Key]**, en **[!UICONTROL Secret Key]** voor de Dienst van de Draai [&#x200B; in voorwaarde wordt verkregen die &#x200B;](#prerequisite).
   1. Klik op **[!UICONTROL Create]**.

      ![&#x200B; vorm Cloud Service om uw milieu van AEM Forms met Turnstile te verbinden &#x200B;](assets/config-turntstile.png)

   >[!NOTE]
   > Gebruikers hoeven de URL voor JavaScript-validatie aan de clientzijde en de URL voor validatie aan de serverzijde niet aan te passen, omdat deze al zijn voorgevuld voor Microsoft-validatie.

   Zodra de Turnstile Captcha dienst wordt gevormd, is het beschikbaar voor gebruik in uw AanpassingsVorm.

## Draaien in een adaptieve vorm gebruiken {#using-turnstile-aem-6.5}

1. Open uw AEM Forms-omgeving.
1. Ga naar **[!UICONTROL Forms]** > **[!UICONTROL Forms and Documents]** .
1. Selecteer een adaptief formulier en klik op **[!UICONTROL Properties]** . Selecteer in **[!UICONTROL Configuration Container]** de configuratiecontainer die de Cloud Configuration bevat die AEM Forms met Turnstile verbindt.
1. Klik op **[!UICONTROL Save & Close]**.

   Als u geen Container van de Configuratie hebt om de dienst te vormen Captcha, zie sectie [&#x200B; Draaien &#x200B;](#configure-turnstile-steps-to-configure-hcaptcha) om te leren hoe te om een Container van de Configuratie tot stand te brengen.

   ![&#x200B; Uitgezochte Container van de Configuratie &#x200B;](assets/captcha-properties.png)

1. Selecteer een adaptief formulier en klik op **[!UICONTROL Edit]** om het aangepaste formulier te openen in de editor.
1. Sleep de component **[!UICONTROL Captcha]** vanuit de componentbrowser naar het adaptieve formulier.
1. Selecteer de **[!UICONTROL Captcha]** component en klik eigenschappen ![&#x200B; pictogram van Eigenschappen &#x200B;](assets/configure-icon.svg). Hiermee wordt het dialoogvenster met eigenschappen geopend. Geef de volgende eigenschappen op:

   <!--![Turnstile v2](assets/turnstile-settings-v2.png)-->
   ![&#x200B; de Draai van de Wolk v1 &#x200B;](assets/turnstile-setting-v1.png)

   * **[!UICONTROL Title]:** specificeer de titel voor uw component Captcha. U kunt een formuliercomponent gemakkelijk herkennen met de unieke titel ervan, zowel in het formulier als in de regeleditor.
   * **[!UICONTROL Configuration Settings]:** selecteer een Cloud-configuratie die voor Turnstile is geconfigureerd.
   * **[!UICONTROL Validation Message]:** Geef een validatiebericht op voor het valideren van Captcha bij het verzenden van formulieren of voor een gebruikersactie.
   * **[!UICONTROL Captcha Service]:** Selecteer de CAPTCHA-service voor het verzenden van uw formulier, hier selecteert u Turnstile®.
   * **[!UICONTROL Configuration Settings]:** selecteer uw Configuratie van de Wolk die voor Turnstile® wordt gevormd.

     >[!NOTE]
     >U kunt voor een vergelijkbaar doel meerdere Cloud Configurations in uw omgeving gebruiken. Kies de service dus zorgvuldig. Als geen de dienst vermeld is, zie [&#x200B; uw milieu van AEM Forms met Turnstile &#x200B;](#connect-your-forms-environment-with-turnstile-service) verbinden om te leren hoe te om een Cloud Service tot stand te brengen die uw milieu van AEM Forms met de Dienst van Turnstile verbindt.

   * **[!UICONTROL Error Message]:** Geef het foutbericht op dat aan de gebruiker moet worden weergegeven wanneer het verzenden van Captcha is mislukt.
   * **Grootte Captcha:** U kunt de vertoningsgrootte van de hCaptcha® uitdagingsdialoog selecteren. Gebruik de optie **[!UICONTROL Compact]** om een klein formaat weer te geven en de optie **[!UICONTROL Normal]** om een relatief groot hCaptcha®-uitdagingsdialoogvenster weer te geven.

1. Selecteer **[!UICONTROL Done]** .


Alleen legitieme formulieren waarin de invuller van het formulier de uitdaging van de Turnstile-service met succes heeft verholpen, kunnen nu worden verzonden.

![&#x200B; Veranderlijke Uitdaging &#x200B;](assets/turnstile-challenge.png)


## Veelgestelde vragen

* **Q: Kan ik meer dan één component Captcha in een Aangepaste Vorm gebruiken?**
* **Ans:** het gebruiken van meer dan één component Captcha in een AanpassingsVorm wordt niet gesteund. Het wordt ook afgeraden een Captcha-component te gebruiken in een fragment of een deelvenster dat is gemarkeerd voor wazig laden.

## Zie ook {#see-also}

* [CAPTCHA gebruiken in aangepaste vormen](/help/forms/using/captcha-adaptive-forms.md)
* [Captcha gebruiken in adaptieve vormen](/help/forms/using/integrate-adaptive-forms-hcaptcha.md)
