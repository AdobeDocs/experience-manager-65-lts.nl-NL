---
title: Hoe kan ik hashes genereren en ermee werken in dynamisch PDF forms?
description: Het produceren en het werken met Hashes in dynamische PDF forms.
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: 3fa1b6c9-fe73-4d76-aa72-20ce3e502941
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '1182'
ht-degree: 0%

---

# Hashes genereren en werken met dynamische PDF forms {#generate-work-with-hashes-dynamic-pdf-forms}

## Vereiste kennis {#prerequisite-knowledge}

Er is enige ervaring met AEM Forms op JEE Designer vereist, evenals de mogelijkheid om functies in scriptobjecten te openen en aan te roepen.

## Gebruikersniveau {#user-level}

Begin

Als u een wachtwoord in uw PDF-formulier wilt verbergen en u wilt het wachtwoord niet in duidelijke tekst in de broncode of elders in het PDF-document opnemen, is het van wezenlijk belang dat u weet hoe u hashes voor MD4, MD5, SHA-1 en SHA-256 kunt genereren en gebruiken.

Het idee is om het wachtwoord te verduisteren door een unieke knoeiboel te produceren en deze knoeiboel in het document van PDF op te slaan. Deze unieke hash kan worden gegenereerd door verschillende hash-functies. In dit artikel ziet u hoe u deze kunt genereren in het PDF-formulier en hoe u ermee kunt werken.

Een hashfunctie heeft een lange tekenreeks (of bericht) van elke lengte als invoer en produceert een tekenreeks met een vaste lengte als uitvoer, ook wel een berichtenoverzicht of een digitale vingerafdruk genoemd.

Met AEM Forms on JEE Designer kunt u de verschillende hashfuncties in scriptobjecten implementeren als JavaScript en deze uitvoeren in een dynamisch PDF-document. De voorbeeld-PDF&#39;s die worden opgenomen in de voorbeeldbestanden voor dit artikel, gebruiken opensource-implementaties van de volgende hashfuncties:

* MD4 en MD5 - ontworpen door Ronald Rivest

* SHA-1 en SHA-256 - zoals gedefinieerd door NIST

Het grootste voordeel van het gebruik van hashes is dat u wachtwoorden niet rechtstreeks hoeft te vergelijken door duidelijke teksttekenreeksen te vergelijken; in plaats daarvan kunt u de twee hashes van de twee wachtwoorden vergelijken. Omdat het onwaarschijnlijk is dat twee verschillende koorden de zelfde knoeiboel hebben, als beide knoeiboel identiek zijn, dan kunt u veronderstellen dat de vergeleken koorden (in dit geval, de wachtwoorden) ook identiek zijn.

>[!NOTE]
>
>Er zijn enkele bekende beveiligingsproblemen (zogenaamde hash-botsingen) met MD4 of MD5. Vanwege die hash-botsingen en andere SHA-1-hacks (inclusief regenboogtafels) besloot ik me te concentreren op de SHA-256 hash-functie in het tweede voorbeeld. Voor meer informatie, zie de [ Botsing ](https://en.wikipedia.org/wiki/Hash_collision) en [ Regenbooglijst ](https://en.wikipedia.org/wiki/Rainbow_table) pagina&#39;s van Wikipedia.

## Scriptobjecten onderzoeken {#examining-script-objects}

Wanneer u een van de twee beschikbare voorbeelden opent in AEM Forms op JEE Designer, vindt u de vier scriptobjecten in het palet Hiërarchie (zie onderstaande afbeelding).

![ Variabelen ](assets/variables.jpg)

Als u de JavaScript-implementatie van de hash-functies in deze scriptobjecten wilt bekijken, selecteert u het scriptobject en bekijkt u de code in de Scripteditor. U kunt zien hoe elk van de volgende knoeiboelfuncties is uitgevoerd:

* soHASHING_MD4.hex_md4()
* soHASHING_MD4.b64_md4()
* soHASHING_MD4.str_md4()
* soHASHING_MD5.hex_md5()
* soHASHING_MD5.b64_md5()
* soHASHING_MD5.str_md5()
* soHASHING_SHA1.hex_sha1()
* soHASHING_SHA1.b64_sha1( )
* soHASHING_SHA1.str_sha1()
* soHASHING_SHA256.hex_sha256()
* soHASHING_SHA256.b64_sha256()
* soHASHING_SHA256.str_sha256()

Zoals u in deze lijst kunt zien, zijn er verschillende functies beschikbaar voor de verschillende uitvoertypen van de hash. U kunt kiezen tussen `hex_` voor hexadecimale cijfers, `b64_` voor Base64-gecodeerde uitvoer of `str_` voor eenvoudige tekenreekscodering.

Afhankelijk van de gekozen hashfunctie varieert de lengte van de hash:

* MD4: 128 bits
* MD5: 128 bits
* SHA-1: 160 bits
* SHA-256: 256 bits

## Het voorbeeld PDF forms proberen {#try-sample-pdf-forms}

De voorbeeldbestanden voor dit artikel bevatten twee PDF forms. In het eerste voorbeeld kunt u een tekenreeks typen en vervolgens waarden voor de hashes van de tekenreeks genereren voor MD4, MD5, SHA-1 en SHA-256. Het tweede voorbeeld is een eenvoudig formulier waarmee tekstvelden worden ontgrendeld als een juist wachtwoord wordt ingevoerd.

### Voorbeeld 1: hashes genereren {#generating-dashes}

Voer de onderstaande stappen uit om het eerste voorbeeld te proberen:

1. Nadat u de voorbeeldbestanden hebt gedownload en uitgepakt, opent u hashing_forms_sample1.pdf met AEM Forms op JEE Designer. U kunt ook Adobe Reader of Adobe Acrobat Professional gebruiken om het voorbeeld te openen en weer te geven, maar u kunt de broncode niet zien.
1. Typ in het tekstveld [!UICONTROL clear text] een wachtwoord of een ander bericht dat u wilt hasheren.
1. Klik op een van de vier knoppen om de hash voor MD4, MD5, SHA-1 of SHA-256 te genereren. Afhankelijk van de knop die u hebt ingedrukt, wordt een van de vier hashfuncties die hexadecimale uitvoer produceren aangeroepen en wordt uw tekenreeks of bericht gehasht.

Het resultaat van de hash-bewerking wordt weergegeven in het veld met het label [!UICONTROL hash] . De lengte van de hash is afhankelijk van de gekozen hash-functie.

Alle steekproeven gebruiken hexadecimale cijfers als outputtype. U kunt de Redacteur van het Manuscript gebruiken om de steekproeven te wijzigen en het outputtype te veranderen in Base64 of eenvoudige Koord.

### Voorbeeld 2: overeenkomende wachtwoorden {#matching-passwords}

In het tweede voorbeeld ziet u hoe hashes op de achtergrond worden vergeleken, zonder dat het echte wachtwoord wordt onthuld. Het wachtwoord dat u invoert, wordt gehasht. Het echte wachtwoord, dat in een onzichtbaar veld wordt opgeslagen, wordt ook gehasht. Het wachtwoord is niet veilig omdat het onzichtbaar is, maar omdat het gehasht is. Omdat het onmogelijk is het wachtwoord van de gehakte waarde te reconstrueren, is het veilig om het wachtwoord in gehakt vorm bloot te stellen. De vergelijking wordt gemaakt slechts tussen de knoeiboel, niet tussen de wachtwoorden in duidelijke teksten. Als beide hashes het zelfde zijn, dan kunt u veronderstellen dat de wachtwoorden identiek zijn.

Voer de onderstaande stappen uit om het tweede voorbeeld te proberen:

1. Open `hashing_forms_sample2.pdf` met AEM Forms op JEE Designer. U kunt ook Adobe Reader of Adobe Acrobat Professional gebruiken om het voorbeeld te openen en weer te geven, maar u kunt de broncode niet zien.
1. Kies een van de twee wachtwoordvelden met het label [!UICONTROL Password MAN] of [!UICONTROL Password WOMAN] en typ de wachtwoorden:
   1. Het wachtwoord voor de man is `bob`
   1. Het wachtwoord voor de vrouw is `alice`
1. Wanneer u de focus uit de wachtwoordvelden verplaatst of op Enter drukt, wordt de hash van het ingevoerde wachtwoord automatisch gegenereerd en wordt deze vergeleken met de opgeslagen hash van het juiste wachtwoord op de achtergrond. De juiste, onderbroken wachtwoorden worden opgeslagen in de onzichtbare tekstvelden met de labels `passwd_man_hashed` en `passwd_woman_hashed` . Als u het juiste wachtwoord voor de man typt, worden de tekstvelden `Man 1` en `Man 2` toegankelijk gemaakt, zodat u er tekst in kunt typen. Hetzelfde gedrag geldt voor de velden van de vrouw.
1. U kunt ook op de knop met het label &quot;Wachtwoorden verwijderen&quot; klikken. Hiermee worden de tekstvelden uitgeschakeld en wordt de rand van de velden gewijzigd.

De code voor het vergelijken van de twee gehashte waarden en het inschakelen van de tekstvelden is eenvoudig:

```xml
if (soHASHING_SHA256.hex_sha256(this.rawValue) == passwd_man_hashed.rawValue){
     VAL_man_1.access = "open";
     VAL_man_2.access = "open";
     VAL_man_1.borderColor = "0,255,0";
     VAL_man_2.borderColor = "0,255,0";
}
```

## Hoe verder? {#next-steps}

Waar heb je zoiets nodig? Neem bijvoorbeeld een PDF-formulier met velden die alleen door geautoriseerde personen moeten worden ingevuld. Als u deze velden beveiligt met een wachtwoord, dat nergens in het document in duidelijke tekst staat, zoals in Sample_2.pdf, kunt u ervoor zorgen dat deze velden alleen toegankelijk zijn voor gebruikers die het wachtwoord weten.

Ik moedig u aan verder te gaan met het verkennen van de twee PDF-voorbeeldbestanden.  U kunt nieuwe knoeiboelwaarden met Sample_1.pdf produceren, en de geproduceerde waarden gebruiken om of het wachtwoord of de knoeiboelfunctie te veranderen die in Sample_2.pdf wordt gebruikt.  De middelen die in de sectie van Attributen worden vermeld verstrekken ook extra informatie over het hakken en de specifieke implementaties van JavaScript die in dit artikel worden gebruikt.

## Attributen {#attributions}

* [ Ronald Rivest ](https://en.wikipedia.org/wiki/Ron_Rivest)
* [ NIST ](https://csrc.nist.gov/projects/cryptographic-standards-and-guidelines)
* [ botsing van de Hash ](https://en.wikipedia.org/wiki/Hash_collision)
* [ Regenbooglijst ](https://en.wikipedia.org/wiki/Rainbow_table)
* [ JavaScript MD5 het projecthuis pagina ](https://pajhome.org.uk/crypt/md5/)
* [ jsSHA2 het projecthuis pagina ](https://anmar.eu.org/projects/jssha2/)
