---
title: Afbeeldingstransformatiebibliotheek
description: Leer hoe u de Adobe Imaging Transcoding Library configureert en gebruikt, een oplossing voor beeldverwerking die kernfuncties voor het verwerken van afbeeldingen kan uitvoeren, zoals codering, transcodering, het resamplen van afbeeldingen en het vergroten of verkleinen van afbeeldingen.
contentOwner: AG
role: Admin
feature: Renditions,Developer Tools,Asset Processing
solution: Experience Manager, Experience Manager Assets
exl-id: fb24c331-55c3-4166-bd4f-c26cece902fc
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '927'
ht-degree: 0%

---

# Afbeeldingstransformatiebibliotheek {#imaging-transcoding-library}

Adobe Imaging Transcoding Library is een merkgebonden oplossing voor beeldverwerking die kernfuncties voor beeldverwerking kan uitvoeren, zoals:

* Codering
* Transcodering (ondersteunde indelingen converteren)
* Nieuwe beeldpixels berekenen, met PS- en Intel IPP-algoritmen
* Bitdiepte en kleurprofiel behouden
* JPEG-kwaliteitscompressie
* Afbeeldingsformaat wijzigen

Imaging Transcoding Library biedt CMYK-ondersteuning en volledige alfaondersteuning, behalve CMYK-Alpha.

Naast de ondersteuning van een groot aantal bestandsindelingen en profielen biedt de Imaging Transcoding Library aanzienlijke voordelen ten opzichte van andere oplossingen van derden op het gebied van prestaties, schaalbaarheid en kwaliteit. Hier volgen enkele belangrijke voordelen van het gebruik van de bibliotheek voor het transformeren van afbeeldingen:

* **Schalen met stijgende dossiergrootte of resolutie**: het schrapen wordt hoofdzakelijk bereikt door de gepatenteerde capaciteit van de Bibliotheek van de Transcodering van Beelden aan re-grootte terwijl het decoderen van dossiers. Hierdoor wordt gegarandeerd dat het runtimegeheugengebruik altijd optimaal is en geen kwadratische functie is om de bestandsgrootte of resolutie van megapixels te verhogen. De bibliotheek voor het transformeren van afbeeldingen kan grotere en hoge-resolutiebestanden (met hogere megapixels) verwerken. Gereedschappen van derden, zoals ImageMagick, kunnen grote bestanden en vastlopen niet verwerken tijdens het verwerken van dergelijke bestanden.
* **de kwaliteitscompressie van Photoshop en het resizing van algoritmen**: Consistentie met de industriestandaard in termen van kwaliteit van neer bemonstering (vlotte, scherpe en automatische bicubische) en compressiekwaliteit. De bibliotheek voor grafische transformatie beoordeelt verder de kwaliteitsfactor van de invoerafbeelding en gebruikt op intelligente wijze optimale tabellen en kwaliteitsinstellingen voor de uitvoerafbeelding. Hierdoor ontstaan bestanden van optimale grootte zonder dat dit ten koste gaat van de visuele kwaliteit.
* **Hoge productie:** De reactietijd is lager en de productie is constant hoger dan ImageMagick. Daarom moet de bibliotheek voor het transformeren van afbeeldingen de wachttijd voor gebruikers en de hostingkosten verlagen.
* **de Schaal beter met gezamenlijke lading:** het Beelden de Bibliotheek van de Transcodering presteert optimaal onder gezamenlijke ladingsvoorwaarden. Deze server biedt een hoge doorvoer met optimale CPU-prestaties, een optimaal geheugengebruik en een lage responstijd, wat de hostingkosten helpt te verlagen.

## Ondersteunde platforms {#supported-platforms}

Imaging Transcoding Library is alleen beschikbaar voor RHEL 8-, RHEL 7- en CentOS 7-distributies.

>[!NOTE]
>
>Mac OS en andere *nix-distributies (bijvoorbeeld Debian en Ubuntu) worden niet ondersteund.

## Gebruik {#usage}

De opdrachtregelargumenten voor de bibliotheek voor het transformeren van afbeeldingen kunnen het volgende bevatten:

```shell
 -destMime PNG/JPEG: Mime type of output rendition
 -BitDepth 8/16: Preserves Bit Depth. Bitdepth '4' is automatically converted to '8'
 -preserveBitDepth: Downscales Bit Depth (No upscaling)
 -preserveCMYK: Preserves CMYK color space
 -jpegQuality: Provides jpeg quality parameter (0-12 , corresponding to Photoshop qualities)
 -ResamplingMethod BiCubic/Lanczos/PSBicubic: Provides resampling methods. PSBicubic is a Photoshop quality resampling method.
 -resize
```

U kunt de volgende opties configureren voor de parameter `-resize` :

* `X`: werkt hetzelfde als [!DNL Experience Manager] . Bijvoorbeeld - resize 319.
* `WxH`: de hoogte-breedteverhouding blijft niet behouden, bijvoorbeeld `-resize 319x319` .
* `Wx` - Hiermee stelt u de breedte vast en berekent u de hoogte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize 319x` .
* `xH` - Hiermee stelt u de hoogte vast en berekent u de breedte met behoud van de hoogte-breedteverhouding. Bijvoorbeeld `-resize x319` .

```shell
 -AllowUpsampling (Resizes smaller images)
 -input <fileName>
 -output <fileName>
```

## Bibliotheek voor afbeeldingstransformatie configureren {#configuring-imaging-transcoding-library}

Om ITL verwerking te vormen, creeer een configuratiedossier en werk het werkschema bij om het uit te voeren.

### Configuratiebestand maken voor geëxtraheerde bundel {#create-conf-file}

Om de bibliotheek te vormen, creeer een CONF dossier om op de bibliotheken te wijzen gebruikend de volgende stappen. U hebt beheerder- of basismachtigingen nodig.

1. Download het [ Uitbeeldende Transcoding pakket van de Bibliotheek van de Distributie van de Software ](https://experience.adobe.com/#/downloads/content/software-distribution/en/aem.html?package=/content/software-distribution/en/details.html/content/dam/aem/public/adobe/packages/aem630/product/assets/aem-assets-imaging-transcoding-library-pkg) en installeer het gebruikend de Manager van het Pakket. Het pakket is compatibel met [!DNL Experience Manager] 6.5.

1. Als u een bundle-id voor `com.day.cq.dam.cq-dam-switchengine` wilt weten, meldt u zich aan bij de webconsole en klikt u op **[!UICONTROL OSGi]** > **[!UICONTROL Bundles]** . Als u de bundelconsole wilt openen, opent u ook de URL van `https://[aem_server:[port]/system/console/bundles/` . Zoek `com.day.cq.dam.cq-dam-switchengine` -bundel en de bijbehorende id.

1. Controleer met de opdracht `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` of alle vereiste bibliotheken zijn uitgepakt, waar de mapnaam is samengesteld met de bundle-id. De opdracht is bijvoorbeeld `ls -la /aem65/author/crx-quickstart/launchpad/felix/bundle588/data/binaries/` als bundle id `588` is.

1. Maak een `SWitchEngineLibs.conf` -bestand om een koppeling naar de bibliotheek te maken.

   ```shell
   cd `/etc/ld.so.conf.d`
   touch SWitchEngineLibs.conf
   vi SWitchEngineLibs.conf
   ```

1. Voeg `/aem65/author/crx-quickstart/launchpad/felix/bundle<id>/data/binaries/` -pad toe aan het conf-bestand met de opdracht `cat SWitchEngineLibs.conf` .

1. Voer de opdracht `ldconfig` uit om de benodigde koppelingen en cache te maken.

1. Bewerk het `.bash_profile` -bestand in de account die wordt gebruikt om [!DNL Experience Manager] te starten. Voeg `LD_LIBRARY_PATH` toe door het volgende toe te voegen.

   ```shell
   LD_LIBRARY_PATH=.
   export LD_LIBRARY_PATH
   ```

1. Gebruik de opdracht `echo $LD_LIBRARY_PATH` om ervoor te zorgen dat de waarde van het pad is ingesteld op `.` . De uitvoer moet gewoon `.` zijn. Start de sessie opnieuw als de waarde niet is ingesteld op `.` .

### Workflow [!UICONTROL DAM Update Asset] configureren {#configure-dam-asset-update-workflow}

Werk de [!UICONTROL DAM Update Asset] -workflow bij om de bibliotheek te gebruiken voor het verwerken van afbeeldingen.

1. Selecteer in de gebruikersinterface van [!DNL Experience Manager] de optie **[!UICONTROL Tools]** > **[!UICONTROL Workflow]** > **[!UICONTROL Models]** .

1. Open vanaf de pagina **[!UICONTROL Workflow Models]** het **[!UICONTROL DAM Update Asset]** -workflowmodel in de bewerkingsmodus.

1. Open de stap van het **[!UICONTROL Process Thumbnails]** workflowproces. Voeg op het tabblad **[!UICONTROL Thumbnails]** de MIME-typen toe waarvoor u het standaardgenereren van miniaturen in de lijst **[!UICONTROL Skip Mime Types]** wilt overslaan.
Als u bijvoorbeeld miniaturen wilt maken voor een TIFF-afbeelding met behulp van de afbeeldingstransformatiebibliotheek, geeft u `image/tiff` op in het veld **[!UICONTROL Skip Mime Types]** .

1. Voeg op het tabblad **[!UICONTROL Web Enabled Image]** de MIME-typen toe waarvoor u het standaardgenereren van webvertoningen in **[!UICONTROL Skip List]** wilt overslaan. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u `image/tiff` toe aan de lijst Overslaan.

1. Open de stap **[!UICONTROL EPS thumbnails (powered by ImageMagick)]** en navigeer naar de tab **[!UICONTROL Arguments]** . Voeg in de lijst **[!UICONTROL Mime Types]** de MIME-typen toe die u in de bibliotheek voor afbeeldingstransformatie wilt verwerken. Als u bijvoorbeeld het MIME-type `image/tiff` in de bovenstaande stap hebt overgeslagen, voegt u `image/jpeg` toe aan de lijst **[!UICONTROL Mime Types]** .

1. Verwijder de standaardopdrachten, indien aanwezig.

1. In-/uitschakelen in het zijvenster en toevoegen in de lijst met stappen **[!UICONTROL SWitchEngine Handler]** .

1. Voeg opdrachten toe aan de [!UICONTROL SwitchEngine Handler] op basis van uw aangepaste vereisten. Tune de parameters van bevelen die u specificeert om aan uw vereisten te voldoen. Als u bijvoorbeeld het kleurprofiel van uw JPEG-afbeelding wilt behouden, voegt u de volgende opdrachten toe aan de lijst **[!UICONTROL Commands]** :

   * `SWitchEngine -input ${file} -destMime PNG -resize 48 -output ${directory}cq5dam.thumbnail.48.48.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 140x100 -output ${directory}cq5dam.thumbnail.140.100.png`
   * `SWitchEngine -input ${file} -destMime PNG -resize 319 -output ${directory}cq5dam.thumbnail.319.319.png`
   * `SWitchEngine -input ${file} -destMime JPEG -resize 1280 -preserveCMYK -output ${directory}cq5dam.web.1280.1280.jpeg`

   ![ verandering ](assets/chlimage_1-199.png)

1. (Optioneel) Genereer miniaturen van een tussentijdse uitvoering met één opdracht. De tussenliggende vertoning fungeert als bron voor het genereren van statische weergaven en webuitvoeringen. Deze methode is sneller dan de eerdere methode. Met deze methode kunt u echter geen aangepaste parameters op miniaturen toepassen.

   ![ verandering ](assets/chlimage_1-200.png)

1. Als u webuitvoeringen wilt genereren, configureert u parameters op het tabblad **[!UICONTROL Web-Enabled Image]** .

1. Synchroniseer het bijgewerkte workflowmodel van [!UICONTROL DAM Update Asset] . Sla de workflow op.

Upload een TIFF-afbeelding en controleer het bestand error.log om de configuratie te controleren. `INFO` -berichten met vermeldingen van `SwitchEngineHandlingProcess execute: executing command line` worden weergegeven. In de logboeken worden de gegenereerde uitvoeringen vermeld. Nadat de workflow is voltooid, kunt u de nieuwe uitvoeringen weergeven in [!DNL Experience Manager] .

>[!MORELIKETHIS]
>
>* [ Gesteund MIME typeartikel ](assets-formats.md#supported-image-transcoding-library)
