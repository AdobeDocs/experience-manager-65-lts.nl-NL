---
title: Ondersteunde platforms voor AEM Forms op JEE
description: Lijst met infrastructuurcomponenten die vereist en ondersteund zijn voor installatie van AEM Forms op JEE
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
geptopics: SG_AEMFORMS/categories/jee
docset: aem65
role: Admin
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms,AEM Forms on JEE,Platform Matrix
source-git-commit: 4097adf1dd533bbf21c8635a1948f9ef4c294896
workflow-type: tm+mt
source-wordcount: '2982'
ht-degree: 0%

---


# Ondersteunde platforms voor AEM Forms op JEE {#supported-platforms-for-aem-forms-on-jee}

## Ondersteuningsniveaus {#support-levels}

AEM Forms on JEE-server kan worden ingesteld met elke combinatie van ondersteunde besturingssystemen, toepassingsservers, databases, databasestuurprogramma&#39;s, JDK, LDAP-servers en e-mailservers.

In dit document worden de ondersteunde client- en serverplatforms voor AEM Forms op JEE vermeld. Adobe biedt verschillende ondersteuningsniveaus, zowel voor door Adobe aanbevolen configuraties als voor andere configuraties. In het document worden ook andere ondersteunde software en de bijbehorende versie, uitzonderingen, patchdefinities en het ondersteuningsbeleid voor softwarepatches van derden vermeld.

>[!NOTE]
>
>- Voor een volledige lijst van uitzonderingen aan gesteunde serverplatforms, zie [&#x200B; Uitzonderingen aan gesteunde serverplatforms &#x200B;](../../forms/using/aem-forms-jee-supported-platforms.md#p-exceptions-to-supported-server-platforms-p).
>- AEM Forms on JEE biedt alleen ondersteuning voor Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.

### Beleid voor upgrades en ondersteuning

#### Volledig installatieprogramma

- **Steun van de Verbetering voor volledige installateurs**: Een volledig installatieprogramma wordt vrijgegeven met elk zesde Service Pack van AEM. Volledige upgrades op basis van installatieprogramma&#39;s worden alleen vanaf AEM 6.5.23.0 ondersteund.

- **Verdringing en Verwijdering**: De platformsteun wordt bijgewerkt met elke volledige installateursversie. Alle software die tijdens een volledige installateursrelease in de platformmatrix is afgekeurd, mag in een volgende volledige installateursrelease uit de ondersteunde platformmatrix worden verwijderd, wat het einde van de ondersteuning voor de software aangeeft.

#### Servicepacks

- **Coverage van het Pak van de Dienst**: Adobe verleent technische steun voor de milieu&#39;s van AEM Forms gebruikend om het even welke recentste zes de dienstpakken. Als uw huidige versie dateert van vóór de laatste zes servicepakketten, raadt Adobe u ten zeerste aan een upgrade uit te voeren naar de nieuwste versie voor optimale prestaties, beveiliging en continue ondersteuning.

- {de Richtlijnen van de Installateur van het 0} Patch **: Terwijl het gebruiken van de flardinstallateurs om bij te werken, is het cruciaal om te verifiëren dat de onderliggende volledige installateursversie niet meer dan twee oude versies is.** Zorg er bijvoorbeeld tijdens de installatie van het servicepack 6.5.19.0 voor dat de onderliggende volledige installatieversie 6.5.18.0 of 6.5.12.0 is.

- **Steun van de Verbetering van het Patch**: U kunt blijven bevordering aan het recentste de dienstpak, tot u aan de meest recente gesteunde platforms ook bevordert. U kunt bijvoorbeeld een upgrade uitvoeren van het servicepack 6.5.12.0 naar 6.5.19.0 , op voorwaarde dat u overschakelt naar een platformcombinatie die wordt ondersteund voor 6.5.19.0 .

### Aanbevolen configuraties {#recommendedconfigurations}

Adobe raadt deze configuraties aan en biedt volledige of beperkte ondersteuning als onderdeel van de standaard overeenkomst voor softwareonderhoud:

<table>
 <tbody>
  <tr>
   <th>Ondersteuningsniveau</th>
   <th>Beschrijving</th>
  </tr>
  <tr>
   <td>A: Ondersteund <br /> </td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie. Deze configuratie valt onder het kwaliteitsborgingsproces van Adobe.</td>
  </tr>
  <tr>
   <td>R: Beperkte ondersteuning</td>
   <td>Adobe biedt volledige ondersteuning voor deze configuratie als aan bepaalde voorwaarden is voldaan. Neem contact op met de Adobe Enterprise Support voor meer informatie over de voorwaarden en vraag om ondersteuning.</td>
  </tr>
  <tr>
   <td>L: Beperkte ondersteuning</td>
   <td>Adobe biedt volledige ondersteuning en onderhoud voor deze configuratie nadat aan bepaalde voorwaarden is voldaan. Niet zijn alle mogelijkheden beschikbaar op de configuratie. Contacteer de ondernemingssteun van Adobe om over de eerste vereisten te leren en een verzoek om de steun op te heffen.<br /> </td>
  </tr>
 </tbody>
</table>

### Niet-ondersteunde configuraties {#unsupported-configurations}

| Ondersteuningsniveau | Beschrijving |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------- |
| E: Naar verwachting werken | De configuratie zal naar verwachting werken en er zijn geen meldingen van het tegendeel. |
| Z: Niet ondersteund | De configuratie wordt niet ondersteund. Adobe legt geen verklaringen over of de configuratie werkt, en steunt het niet. |

>[!NOTE]
>
>Om klanten van AEM Forms te helpen de kosten van eigendom verminderen, de plaatsingsarchitectuur vereenvoudigen, en de ontwikkelingsstapel moderniseren, beweegt het ondernemingsplatform van Adobe Experience Manager zich van op toepassingsserver-gebaseerde plaatsingen in de plaats van op standalone op OSGi-Gebaseerde plaatsingen. Adobe blijft de AEM Forms JEE-stack ondersteunen met een beperkte matrix van infrastructuurcomponenten.
>Voor nieuwe installaties, waar mogelijk, wordt geadviseerd om AEM Forms op de moderne OSGi stapel op te stellen om de recentste innovaties rond ontvankelijke Adaptive Forms voor mobiele, multi-kanaals Interactieve Mededelingen, en backendgegevensintegratie te gebruiken gebruikend het Model van de Gegevens van de Vorm.
>
>Adobe erkent dat bestaande gebruikers AEM Forms moeten blijven implementeren in JEE-stack. In dergelijke scenario&#39;s vereist Adobe de implementatie van AEM Forms JEE op ondersteunde infrastructuur, zoals beschreven in deze documentatie. Als u een upgrade uitvoert naar AEM 6.5 Forzms en een niet-ondersteund platform gebruikt in de vorige AEM Forms-release, kunt u contact opnemen met de ondersteuning van Adobe voor hulp bij de upgrade naar een ondersteund platform.

### Java™ Virtual Machines (JVM) {#java-virtual-machines-jvm}

Adobe Experience Manager Forms vereist dat een Java™ Virtual Machine wordt uitgevoerd, die wordt geleverd door de JDK-distributie (Java™ Development Kit). Adobe Experience Manager werkt met de volgende versies van Java™ Virtual Machines:

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
   <tr> 
   <td><p>Oracle Java™ SE 21 (64-bits) <sup> [8] </sup> </p>  </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases en updates </p> </td>
  </tr>
  <tr> 
   <td><p>Oracle Java™ SE 17 (64-bits) <sup> [8] </sup> </p>  </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases en updates </p> </td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Volg de beveiligingsbulletins van de Java™-leverancier om de veiligheid en beveiliging van productieomgevingen te garanderen en installeer de nieuwste Java™-updates.
>- AEM Forms on JEE ondersteunt alleen 64-bits JVM&#39;s in productieomgevingen.

### Databases en CRX-persistentie {#databases-and-crx-persistence}

<table>
 <tbody>
  <tr>
   <td><p><strong>Platform</strong></p> </td>
   <td><p><strong> Beschrijving</strong></p> </td>
   <td><p><strong>Ondersteuningsniveau</strong></p> </td>
  </tr>
  <tr>
   <td><p>Bestandssysteem</p> </td>
   <td><p>Repository Microkernel (TAR MK-bestanden)</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td><p> MongoDB Enterprise 9.0 </p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td><p> MongoDB Enterprise 8.0</p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
    <tr>
   <td><p> MongoDB Enterprise 7.0 </p> </td>
   <td><p>Repository Microkernel</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
   <tr>
   <td>Oracle Database 19c (Standard, Real Application Clusters (RAC) en Enterprise-edities) </td>
   <td>-</td>
   <td>Ondersteund</td>
  </tr>
  <tr>
   <td><p>Microsoft® SQL Server 2022 </p> </td>
   <td><p>-</p> </td>
   <td><p>Ondersteund</p> </td>
  </tr>
  <tr>
   <td>MySQL 8.4</td>
   <td>-</td>
   <td>R: Beperkte ondersteuning</td>
  </tr>
 </tbody>
</table>

- MongoDB is software van derden en is niet opgenomen in het AEM-licentiepakket. Voor meer informatie, zie [&#x200B; MongoDB het verlenen van vergunningen beleid &#x200B;](https://www.mongodb.org/about/licensing/).
- Om optimaal gebruik te kunnen maken van uw AEM-implementatie, raadt Adobe aan een licentie te verlenen voor de MongoDB Enterprise-versie, zodat deze profiteert van professionele ondersteuning.
- De klantenservice van Adobe helpt kwalificerende problemen met betrekking tot het gebruik van MongoDB met AEM. Voor meer informatie, zie [&#x200B; MongoDB voor de pagina van Adobe Experience Manager &#x200B;](https://www.mongodb.com/lp/contact/mongodb-adobe-experience-manager).
- &#39;Bestandssysteem&#39; omvat blokopslag die voldoet aan POSIX. Dit omvat netwerkopslagtechnologie. Houd er rekening mee dat de prestaties van het bestandssysteem kunnen variëren en van invloed zijn op de algehele prestaties. Het wordt aanbevolen om test AEM te laden met het netwerk/externe bestandssysteem.
- Alleen MongoDB Storage Engine WiredTiger wordt ondersteund.
- Delen via MongoDB wordt niet ondersteund in AEM.
- De module Documentbeveiliging maakt geen gebruik van Inhoudsopslagruimte. Dit houdt in dat als u alleen Documentbeveiliging gebruikt en geen HTML Workspace-, HTML5-formulieren of adaptieve formulieren wilt gebruiken, u geen opslagplaats voor inhoud hoeft te installeren.

### Databasestuurprogramma&#39;s {#database-drivers}

<table>
 <tbody>
  <tr>
   <th>Database </th>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>MySQL</td>
   <td><p>MySQL Connector/J 8.4</p> </td>
   <td><p>Wordt geleverd bij AEM Forms op JEE-installatie</p> </td>
  </tr>
  <tr>
   <td>Microsoft® SQL Server <br /> </td>
   <td><p>Microsoft® SQL Server JDBC-stuurprogramma 12.10.0 <br /> </p> <p>sqljdbc12.10.0.jar</p> </td>
   <td><p>Downloaden vanaf Microsoft®-website.</p> </td>
  </tr>
  <tr>
   <td>Oracle</td>
   <td><p>Oracle Database 19.3.0.0.0 JDBC-stuurprogramma</p> <p>ojdbc8.jar (versie 19.3.0.0.0) <br /> </p> </td>
   <td><p>De download van <a href="https://www.oracle.com/database/technologies/appdev/jdbc-ucp-19c-downloads.html"> Website van Oracle </a>.</p> </td>
  </tr>
 </tbody>
</table>

### Toepassingsservers {#application-servers}

<table>
 <tbody>
  <tr>
   <td><p><strong> Platform</strong></p> </td>
   <td><p><strong>Ondersteuningsniveau</strong></p> </td>
   <td><p><strong>Ondersteunde patchdefinities</strong></p> </td>
  </tr>
  <tr>
   <td><p>JBoss® Enterprise Application Platform (EAP) 8.0.6 <sup>[2] [3] [7]</sup> </p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Patches en cumulatieve patches voor de ondersteunde EAP-versie</p> </td>
  </tr>
 </tbody>
</table>

### Serverbesturingssystemen {#server-operating-systems}

#### Productieomgevingen {#production-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong> Platform</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
     <tr>
   <td>Microsoft® Windows Server 2022 (64-bits)</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td>Ubuntu 20,04</td>
   <td>A: Ondersteund</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 9 (Kernel 5.x) (64-bits)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
  </tr>
  <tr>
   <td><p>Red Hat® Enterprise Linux® 8 (Kernel 4.x) (64-bits)</td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Kleine releases, cumulatieve updates en kritieke updates</p> </td>
  </tr>
  <tr>
   <td><p>SUSE® Linux® Enterprise Server 15-SP6 (64-bits)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Servicepacks, cumulatieve patches en kritieke beveiligingsupdates</p> </td>
  </tr>
 </tbody>
</table>

#### Gevirtualiseerde omgeving {#virtualized-environment}

U kunt AEM Forms op JEE op een fysieke machine of een virtuele omgeving uitvoeren. Als u echter een probleem tegenkomt met AEM Forms in een virtuele omgeving, probeert u het probleem te repliceren op een fysieke computer. Neem contact op met Adobe Support voor een oplossing als het probleem zich blijft voordoen op de fysieke computer. Voor de problemen die u niet op een fysieke machine kunt repliceren, contacteer uw virtuele milieuverkoper.

#### Ontwikkelomgevingen {#development-environments}

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform (basisversie)</strong></p> </th>
   <th>Ondersteuningsniveau</th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 64-bits</p> </td>
   <td>E: Naar verwachting werken</td>
   <td><p>Servicepack en kritieke updates</p> </td>
  </tr>
 </tbody>
</table>

### Uitzonderingen op ondersteunde serverplatforms {#exceptions-to-supported-server-platforms}

Houd rekening met de volgende uitzonderingen wanneer u een platform kiest voor het instellen van uw AEM Forms op de JEE-server.

1. CRX-repository ondersteunt persistentie van het type TarMK en MongoDB.
1. AEM Forms on JEE biedt geen ondersteuning voor JBoss® op rollen gebaseerde toegangsbeheer (RBAC).

<!-- 
1. [!DNL Microsoft&reg; Windows Server 2019] does not support [!DNL MySQL 5.7] and [!DNL JBoss&reg; EAP 7.1], [!DNL Microsoft&reg; Windows Server 2019] does not support turnkey installations for [!DNL Experience Manager Forms Service Pack 6.5.10.0 and later]. (CQDOC-18312) 
-->

Houd rekening met de volgende punten wanneer u software kiest voor Adobe AEM Forms bij JEE-implementaties:

- AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.
- Clustergebaseerde installaties ondersteunen TarMK-persistentie niet. Voor informatie over gesteunde persistentie, zie [&#x200B; het Kiezen van een persistentietype voor een installatie van AEM Forms &#x200B;](/help/forms/using/choosing-persistence-type-for-aem-forms.md).
- AEM Forms op JEE steunt diverse derdesoftware zoals per Adobe [&#x200B; het Beleid van de de softwaresteun van de Derde &#x200B;](../../forms/using/aem-forms-jee-supported-platforms.md#p-third-party-patch-support-policy-p).
- AEM Forms on JEE biedt ondersteuning voor platforms die overeenkomen met de ondersteuning van externe leveranciers. Sommige combinaties zijn mogelijk niet toegestaan door externe leveranciers. Veel leveranciers hebben hun toepassingsservers bijvoorbeeld niet gecertificeerd met Oracle. Als gevolg hiervan biedt AEM Forms op JEE ook geen ondersteuning voor deze combinaties. Om ervoor te zorgen dat u de gesteunde softwareversies kiest, controleer de steunmatrijs ook voor de derdeverkopers.
- AEM Forms op JEE ondersteunt TarMK Cold Standby niet.
- AEM Forms op JEE biedt geen ondersteuning voor verticale clustering.
- AEM Forms on JEE biedt geen ondersteuning voor MySQL-database in een geclusterde omgeving.

### LDAP-servers (optioneel) {#ldap-servers-optional}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product (basisversie)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Microsoft® Active Directory 2022</td>
   <td>Onderhoudsrelease en -reparatiepakketten</td>
  </tr>
  <tr>
   <td><p>IBM® Tivoli Directory Server 6.4</p> </td>
   <td><p>Functiepakketten en tussentijdse correcties</p> </td>
  </tr>
 </tbody>
</table>

### E-mailservers (optioneel) {#email-servers-optional}

| Product |
| ----------------------- |
| Microsoft® Exchange 2013 |
| Microsoft® Office 365 |

### Inhoudsmanagers en bijbehorende connectors {#content-managers-and-corresponding-connectors}

<table>
 <tbody>
  <tr>
   <td><strong>Product<br /> </strong></td>
   <td><strong>Versie</strong></td>
  </tr>
  <tr>
   <td>EMC Documentum®</td>
   <td>7,3</td>
  </tr>
  <tr>
   <td>IBM® FileNet</td>
   <td>5.5.2.</td>
  </tr>
  <tr>
   <td>IBM® Content Manager Server (afgekeurd) </td>
   <td>8.5 Fix pack 2</td>
  </tr>
  <tr>
   <td> IBM® Content Manager Client</td>
   <td>8,7 </td>
  </tr>
  <tr>
   <td> IBM® Content Manager Client (afgekeurd)</td>
   <td>8,5 </td>
  </tr>
   <td>Microsoft® Sharepoint </td>
   <td>2019 <br /> </td>
  </tr>
 </tbody>
</table>

### Steun voor Cordova {#support-for-cordova}

AEM Forms App ondersteunt nu de Apache Cordova. Hier volgen de platformspecifieke versies van Cordova die worden ondersteund:

- Apache Cordova 6.4.0
- Cordova iOS 4.3.0
- Cordova Android™ 6.0.0
- Cordova Windows 4.4.3

### Softwareondersteuning voor PDF Generator {#software-support-for-pdf-generator}

<table>
 <tbody>
  <tr>
   <th><p><strong>Product</strong></p> </th>
   <th><p><strong>Ondersteunde indelingen voor conversie naar PDF</strong></p> </th>
  </tr>
  <tr>
   <td><a href="https://helpx.adobe.com/acrobat/release-note/release-notes-acrobat-reader.html"> Acrobat Pro DC </a> recentste versie</td>
   <td>XPS, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML en HTM</td>
  </tr>

<tr>
   <td>Microsoft® Office 2021 Professional Plus-, retail- en volumelicenties</td>
   <td>DOC, DOCX, XLS, XLSX, PPT, PPTX, RTF en TXT</td>
  </tr>
  <tr>
   <td>
    <strong> OpenOffice 4.1.15 </strong>   </td>
   <td>
    ODT, ODP, ODS, ODG, ODF, SXW, SXC, SXD, XLS, XLSX, DOC, DOCX, PPT, PPTX, afbeeldingsindelingen (BMP, GIF, JPEG, JPG, TIF, TIFF, PNG, JPF, JPX, JP2, J2K, J2C, JPC), HTML, HTM F en TXT<br>

</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- PDF Generator ondersteunt alleen Engelse, Franse, Duitse en Japanse versies van de ondersteunde besturingssystemen en toepassingen.
>- Voor PDF Generator is Adobe Acrobat Pro DC (32-bits) vereist om de conversie uit te voeren.
>- PDF Generator ondersteunt alleen de 32-bits versie van Microsoft® Office Professional Plus en andere software die vereist is voor conversie.
>- Als een Microsoft® Office-installatie om welke reden dan ook gedeactiveerd of zonder licentie wordt, zoals een installatie met volumelicentie die binnen een bepaalde periode geen KMS-host kan vinden, kunnen conversies mislukken totdat de installatie opnieuw in licentie wordt gegeven en opnieuw wordt geactiveerd.
>- PDF Generator ondersteunt Microsoft® Office 365 niet.
>- PDF Generator-conversies voor OpenOffice worden zowel op Windows als op Linux® ondersteund.
>- De functies OCR PDF, Optimize PDF en Export PDF worden alleen ondersteund in Windows.
>- PDF Generator-service biedt geen ondersteuning voor Microsoft® Windows 11

<!-- Removed lines: >- PDF Generator fails to convert files using Microsoft&reg; Visio 2019. You can continue to use Microsoft&reg; Visio 2016 to convert .VSD and .VSDX files.
>- PDF Generator fails to convert files using Microsoft&reg; Project 2019. You can continue to use Microsoft&reg; Project 2016 to convert .MPP files.-->

### Uitzonderingen op toegankelijkheidsondersteuning {#exceptions-to-accessibility-support}

De volgende subsystemen van AEM Forms zijn niet [&#x200B; 508 &#x200B;](https://www.section508.gov/) volgzaam:

- Aangepaste Forms Authoring UI
- Gebruikersinterface voor Forms Manager
- Gebruikersinterface Correspondentenbeheer
- Admin UI (interface beheerconsole)

## Systeemvereisten voor AEM Forms op JEE {#system-requirements-for-aem-forms-on-jee}

### Minimale hardwarevereisten {#minimum-hardware-requirements}

<table>
 <tbody>
  <tr>
   <td>Platform</td>
   <td>Minimale hardwarevereisten</td>
  </tr>
  <tr>
   <td>Microsoft® Windows Server</td>
   <td>Intel Xeon® E5-2680, 2.4-GHz processor of equivalent <br /> VMWare ESX 5.1 of hoger <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 15 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE</td>
  </tr>
  <tr>
   <td>SUSE® Linux® Enterprise Server</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz processor <br /> AWS m3.medium (3 Ecu's) <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE</td>
  </tr>
  <tr>
   <td>Red Hat® Enterprise Linux®</td>
   <td>Intel Xeon® E5-2670v2, 1 vCPU, 2,5 GHz processor <br /> AWS m3.medium (3 Ecu's) <br /> RAM: 6 GB (64-bits besturingssysteem met 64-bits JVM) <br /> vrije schijfruimte: 6 GB tijdelijke ruimte plus 22 GB <br /> voor AEM Forms op JEE <br /> </td>
  </tr>
  <tr>
   <td>Hardwarevereisten voor een kleine productieomgeving</td>
   <td>
    <ul>
     <li><strong> Intel® aangedreven milieu </strong>: Intel Xeon® E5-2680, 2.4 GHz of groter. Het gebruik van een dual core processor zal de prestaties verder verbeteren</li>
     <li><strong> Geheugen: </strong> 4 GB <br /> </li>
    </ul> </td>
  </tr>
 </tbody>
</table>

Zie voor aanvullende vereisten:

- [&#x200B; vereisten van het Systeem voor enig-server AEM Forms op plaatsing JEE &#x200B;](https://www.adobe.com/go/learn_aemforms_sysreq_single_65)
- [&#x200B; vereisten van het Systeem voor gegroepeerde AEM Forms op plaatsing JEE &#x200B;](https://www.adobe.com/go/learn_aemforms_sysreq_cluster_65)

### Adobe Acrobat en Adobe Reader {#adobe-acrobat-and-adobe-reader}

<table>
 <tbody>
  <tr>
   <th><p><strong>Acrobat en Adobe Reader (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td>Acrobat 2020 (klassieke track)</td>
   <td>Versie 20.004.3006 of hoger <br /> </td>
  </tr>

</tbody>
</table>

>[!NOTE]
>
>De productfamilie van Acrobat DC introduceert twee tracks voor zowel Acrobat als Reader die verschillende producten zijn: &quot;Klassiek&quot; en &quot;Doorlopend&quot;. Voor details en een vergelijking van de twee sporen, zie [&#x200B; https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html &#x200B;](https://www.adobe.com/devnet-docs/acrobatetk/tools/AdminGuide/whatsnewdc.html).

## Ondersteunde clients voor AEM Forms op JEE {#supported-clients-for-aem-forms-on-jee}

### Workbench {#workbench}

<table>
 <tbody>
  <tr>
   <th><p><strong>Platform</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Windows® 10 (Enterprise, Pro, Basic)</p> <p>32-bits of 64-bits versie</p> <p> </p> </td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
  <tr>
   <td>Microsoft® Windows® 2022 Server</td>
   <td>Servicepacks en kritieke updates</td>
  </tr>
 </tbody>
</table>

- Schijfruimte voor installatie: 1,7 GB alleen voor Workbench, 2,7 GB op één station voor een volledige installatie van Workbench, Designer en de samplingverzameling 400 MB voor tijdelijke installatiemappen - 200 MB in de map met gebruikerstempels en 200 MB in de tijdelijke map van Windows. Als al deze locaties zich op één station bevinden, moet er tijdens de installatie 1,5 GB aan ruimte beschikbaar zijn. De naar de tijdelijke mappen gekopieerde bestanden worden verwijderd wanneer de installatie is voltooid.

- Geheugen voor het uitvoeren van Workbench: 2 GB RAM
- Hardwarevereisten: Intel® Pentium® 4- of AMD®-equivalent, 1-GHz processor
- Minimale monitorresolutie van 1024 x 768 pixels of hoger met 16-bits kleur of hoger
- TCP/IPv4- of TCP/IPv6-netwerkverbinding met de AEM Forms op JEE-server
- U moet over beheerdersrechten beschikken om Workbench in Windows te installeren. Als u een niet-beheerdersaccount installeert, vraagt het installatieprogramma u om de referenties voor een geschikte account.

### Designer {#designer}

- Microsoft® Windows® 2016 Server, Microsoft® Windows® 2019 Server, Microsoft® Windows® 10 of Windows® 11
- Processor van 1 GHz of sneller met ondersteuning voor PAE, NX en SSE2.
- 1 GB RAM voor 32-bits of 2 GB RAM voor 64-bits besturingssysteem
- 16 GB schijfruimte voor 32-bits of 20 GB schijfruimte voor 64-bits besturingssysteem
- Grafisch geheugen - 128 MB GPU (256 MB aanbevolen)
- 2,35 GB beschikbare ruimte op de vaste schijf
- Monitorresolutie van 1024 x 768 pixels of hoger
- Hardwareversnelling voor video (optioneel)
- Acrobat Pro DC, Acrobat Standard DC of Adobe Acrobat Reader DC
- Beheerdersrechten voor het installeren van Designer
- Microsoft® Visual C++ 2019 (VC 14.28 of hoger) 32-bits runtime

### Browsers {#browsers}

#### Desktops {#desktops}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (basis)</strong></p> </th>
   <th><p><strong>Ondersteuningsniveau</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Microsoft® Edge (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td><p>Servicepacks en -updates</p> </td>
  </tr>
  <tr>
   <td><p>Mozilla Firefox (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Mozilla Firefox ESR</td>
   <td>E: Naar verwachting werken</td>
   <td> Alle updates</td>
  </tr>
  <tr>
   <td><p>Google Chrome (Evergreen)</p> </td>
   <td><p>A: Ondersteund</p> </td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Apple Safari op macOS</td>
   <td>A: Ondersteund</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>Bepaalde browsergerelateerde uitzonderingen voor desktops zijn als volgt:
>
>- Safari wordt alleen ondersteund op Macintosh OS X.
>- Workspace biedt ondersteuning voor Safari 5.1 op Macintosh OS X 10.6 en 10.7 met Acrobat DC of hoger. Voor meer informatie over de verenigbaarheid van Safari 5.1 met de Lezer van Adobe, Acrobat, zie [&#x200B; https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html &#x200B;](https://helpx.adobe.com/x-productkb/multi/safari-5-1-incompatible-reader.html).
>- Beheerconsole wordt niet ondersteund in Safari.
>- Correspondence Management ondersteunt geen Windows® Internet Explorer 9.0 voor AEM 6.1-formulieren.
>- Forms Portal ondersteunt JAWS 14.0-schermlezersoftware in Internet Explorer 11 voor toegankelijkheid.

#### Mobiele clients {#mobile-clients}

<table>
 <tbody>
  <tr>
   <th><p><strong>Browser (basis)</strong></p> </th>
   <th><p><strong>Ondersteunde patchdefinities</strong></p> </th>
  </tr>
  <tr>
   <td><p>Chrome op Android™ 4.1.2 en hoger</p> </td>
   <td><p>Alle updates</p> </td>
  </tr>
  <tr>
   <td>Safari op iOS 15.1 en hoger</td>
   <td>Alle updates</td>
  </tr>
  <tr>
   <td>Microsoft® Edge <br /> </td>
   <td>Alle updates <br /> </td>
  </tr>
  <tr>
   <td>Systeemeigen Android™-browser op Android™ 4.4 en hoger</td>
   <td>Alle updates</td>
  </tr>
 </tbody>
</table>

>[!NOTE]
>
>- Forms Portal wordt alleen ondersteund op Safari op iPad.

### AEM Forms-app {#aem-forms-workspace-app}

#### Ondersteuning voor mobiele apparaten {#mobile-device-support}

De AEM Forms-app is beschikbaar op de volgende platforms:

| **Platform** | **Ondersteunde Apparaten** |
| --- | --- |
| Apple iOS | Apple iPhone, iPad, iPad Air en iPad mini met iOS 15.1 en hoger. |
| Google Android™ | Android™ 5.1 en hoger. De AEM Forms-app is gecertificeerd voor Samsung Galaxy-tablets van 7 en 10 inch en voor populaire smartphones. |
| Microsoft® Windows | Microsoft® Surface devices, tablets, notebooks en desktops met Microsoft® Windows 10 besturingssysteem. |

### Adobe Document Security Extension for Microsoft® Office {#adobe-rights-management-extension-for-microsoft-office}

Klik [&#x200B; hier &#x200B;](https://www.adobe.com/products/livecycle/rightsmanagement/extension/downloads.html) om de systeemvereisten voor de Uitbreiding van de Veiligheid van het Document van Adobe voor Microsoft® Office te zien.

### Uitzonderingen op clientondersteuning {#exceptions-to-client-support}

AEM Forms on JEE ondersteunt updates, patches en repareert pakketten boven op de opgegeven primaire en secundaire versie van ondersteunde software. Bijwerken naar de volgende hoofd- of subversie wordt echter alleen ondersteund als dit is opgegeven.

## Flardondersteuningsbeleid van derden {#third-party-patch-support-policy}

De softwarevereisten van derden voor AEM Forms op JEE worden beschreven in het gedeelte &quot;Systeemvereisten&quot; van hun respectieve productdocumenten. Heb toegang tot alle documentatie van [&#x200B; https://adobe.com/go/learn_aemforms_documentation_65 &#x200B;](https://adobe.com/go/learn_aemforms_documentation_65).

AEM Forms op de referentieplatforms van derden van JEE vermeldt het specifieke patchniveau van de infrastructuur van derden dat tijdens de ontwikkeling en release van AEM Forms op JEE actueel was, en van het minimale patchniveau/servicepack van de infrastructuur die door die versie van AEM Forms op JEE wordt ondersteund.

Adobe biedt bij de release ondersteuning voor urgente of aanbevolen patches die door externe leveranciers worden uitgegeven, ervan uitgaande dat externe leveranciers achterwaartse compatibiliteit met de versies garanderen die AEM Forms op JEE ondersteunt. Adobe biedt alleen ondersteuning voor patches die worden vrijgegeven na het minimale patchniveau dat in de AEM Forms in JEE-documentatie is vermeld.

Soms biedt Adobe geen ondersteuning voor updates van derden die belangrijke functionaliteit wijzigen en dus geen ondersteuning bieden voor volledige achterwaartse compatibiliteit. Voor details op de gesteunde updates, zie [&#x200B; Gesteunde flarddefinities &#x200B;](https://helpx.adobe.com/aem-forms/aem-forms-third-party-software-patch.html) voor specifieke verkopersproducten en de flardtypes Adobe steunen.

Onder omstandigheden buiten de controle van Adobe, kunnen de derdepatches die achterwaartse verenigbaarheid eisen negatieve gevolgen voor de producten van Adobe of klantenmilieu&#39;s hebben. In dergelijke gevallen raadt Adobe klanten aan de gevolgen van een noodpatch van een derde te beoordelen voordat ze deze op kritieke systemen toepassen. Adobe werkt met derden samen door redelijke zakelijke inspanningen te leveren om dergelijke problemen op te lossen, hetzij via normale Adobe-ondersteuningsprogramma&#39;s, hetzij door derden die het probleem in hun patch verhelpen. Dit garandeert niet dat een nieuw vrijgegeven patch van derden die door Adobe wordt ondersteund, werkt zoals wordt beschreven door de leverancier of met AEM Forms op JEE.

Adobe behoudt zich het recht voor om de referentieplatforms van derden die worden ondersteund door een AEM Forms bij JEE-release en de door hen ondersteunde patchdefinities op een bepaald punt te wijzigen.

Aanvullende informatie voor patches van derden vindt u ook op de website van Adobe Enterprise Support op de website van knowledgebase-artikelen over uw product.

<!--

## Platform updates {#platform-updates}

The following platforms are marked as deprecated with AEM Forms 6.5.18.0 release on August 31, 2023:

- Microsoft&reg; Windows Server 2019 (64-bit)
- Microsoft&reg; Active Directory 2016

The following platforms are marked as deprecated with AEM Forms 6.5.13.0 release on June 2, 2022:
- Microsoft&reg; SharePoint 2016

The following platforms are marked as deprecated with AEM Forms 6.5.10.0 release on September 7, 2021:

- Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
- Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
- Microsoft&reg; Windows Server 2016 (64-bit) 
- Microsoft&reg; Office 2016
- OpenOffice 4.1.2

-->


<!--## Revision History {#revision-history}-->

<!--

- 6.5.18.0 (Aug 31, 2023)
  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - MongoDB Enterprise 4.4
    - Oracle WebLogic Server 14c
    - My SQL JDBC connector 8
    - Active Directory 2022
    - Microsoft&reg; Windows Server 2022 (64-bit)

  - **Removed support**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
    - Windows Server 2016 (64-bit)
    - MongoDB Enterprise 4.0
    - Oracle Database 12c Release 2 (12.2.0.1.0)
    - MySQL 5.7.35
    - Microsoft&reg; SQL Server 2016
    - JBoss&reg; EAP 7.1.4
    - My SQL JDBC connector 5.1.44
    - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
    - Microsoft&reg; SQL Server JDBC driver 6.2.2.0
    - Microsoft&reg; JDBC Driver 8.x for SQL Server

    The release has also removed support for the following platforms for PDF Generator and in-general:
    - Microsoft&reg; Sharepoint 2016
    - Microsoft&reg; Office 2016
    - Microsoft&reg; Office Visio 2016 
    - Microsoft&reg; Publisher 2016
    - Microsoft&reg; Project 2016
    - OpenOffice 4.1.2
    - Acrobat 2017 (Classic track) Version 17.011.30078 or later

  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:
    - Microsoft&reg; Windows Server 2019 (64-bit)
    - Microsoft&reg; Active Directory 2016
    
- 6.5.13.0 (June 2, 2022)

  The following platforms are deprecated with AEM Forms 6.5.13.0 release on:
 
  - Microsoft&reg; SharePoint 2016

- 6.5.12.0 (March 3, 2022)

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has removed support for the following platforms:
      - IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0)
      - Oracle Database 12c Release 1
      - Oracle Database 18c
      - Oracle Unified Directory (OUD) 11g Release 2
      - IBM&reg; Lotus Domino 9.0
      - IBM&reg; FileNet 5.2
      - Adobe Flash Player

    - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

      - MongoDB Enterprise 4.0
      - MongoDB Enterprise 4.2
      - IBM&reg; DB2&reg; 11.1
      - Oracle Database 12c Release 2
      - MySQL 5.7.35
      - Microsoft&reg; SQL Server JDBC driver 6.2.1.0
      - JBoss&reg; Enterprise Application Platform (EAP) 7.1.4
      - IBM&reg; Content Manager Server 8.5 Fix pack 2
      - IBM&reg; Content Manager Client 8.5
      - Microsoft&reg; SQL Server 2016

- 6.5.10.0 (Sep 01, 2022)

  - **Added support**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platform:
  
    - Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4.
  - **Deprecated support**: [!DNL Adobe Experience Manager Forms] on JEE has deprecated the following platforms:

    - Adobe Acrobat 2017 - [Core support for Adobe Acrobat 2017 ends on June 6, 2022](https://helpx.adobe.com/support/programs/eol-matrix.html).
    - Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)
    - Microsoft&reg; Windows Server 2016 (64-bit) 
    - Microsoft&reg; Office 2016
    - OpenOffice 4.1.2


-->
<!--
### Release 6.5.19.1 (Dec 15, 2023)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 6.0 |MongoDB Enterprise 4.4   |  |
| MongoDB Enterprise 5.0 |  |  |
|  | |  |

### Release 6.5.18.0 (Aug 31, 2023)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| MongoDB Enterprise 4.4 | Windows Server 2016 (64-bit) | Microsoft&reg; Windows Server 2019 (64-bit) |
| Oracle WebLogic Server 14c | MongoDB Enterprise 4.0 | Microsoft&reg; Active Directory 2016 |
| My SQL JDBC connector 8 | Oracle Database 12c Release 2 (12.2.0.1.0) |  |
| Active Directory 2022 | MySQL 5.7.35 |  |
| Microsoft&reg; Windows Server 2022 (64-bit) | Microsoft&reg; SQL Server 2016 |  |
|  | JBoss&reg; EAP 7.1.4 |  |
|  | My SQL JDBC connector 5.1.44 |  |
|  | Microsoft&reg; SQL Server JDBC driver 6.2.1.0 |  |
|  | Microsoft&reg; SQL Server JDBC driver 6.2.2.0 |  |
|  | Microsoft&reg; JDBC Driver 8.x for SQL Server |  |
|  |  |  |
|  | **Removed Support (PDF Generator and In-General):** |  |
|  | Microsoft&reg; Sharepoint 2016 |  |
|  | Microsoft&reg; Office 2016 |  |
|  | Microsoft&reg; Office Visio 2016 |  |
|  | Microsoft&reg; Publisher 2016 |  |
|  | Microsoft&reg; Project 2016 |  |
|  | OpenOffice 4.1.2 |  |
|  | Acrobat 2017 (Classic track) Version 17.011.30078 or later |  |


### Release 6.5.13.0 (June 2, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
|  |  | Microsoft&reg; SharePoint 2016 |


### Release 6.5.12.0 (March 3, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
|  | IBM&reg; J9 Virtual Machine (build 2.8, JRE 1.8.0) | MongoDB Enterprise 4.0 |
|  | Oracle Database 12c Release 1 | MongoDB Enterprise 4.2 |
|  | Oracle Database 18c | IBM&reg; DB2&reg; 11.1 |
|  | Oracle Unified Directory (OUD) 11g Release 2 | Oracle Database 12c Release 2 |
|  | IBM&reg; Lotus Domino 9.0 | MySQL 5.7.35 |
|  | IBM&reg; FileNet 5.2 | Microsoft&reg; SQL Server JDBC driver 6.2.1.0 |
|  | Adobe Flash Player | JBoss&reg; Enterprise Application Platform (EAP) 7.1.4 |
|  | | IBM&reg; Content Manager Server 8.5 Fix pack 2 |
|  | | IBM&reg; Content Manager Client 8.5 |
|  | | Microsoft&reg; SQL Server 2016 |
|  | | Microsoft&reg; Windows Server 2016 |

### Release 6.5.10.0 (September 01, 2022)

| Added Support | Removed Support | Deprecated Support |
| -------------- | --------------- | ------------------- |
| Oracle Java&trade; SE 11 (64 bit) SDK for application server JBoss&reg; EAP 7.4. | | [Adobe Acrobat 2017 - Core support for Adobe Acrobat 2017 ends on June 6, 2022.](https://helpx.adobe.com/support/programs/eol-matrix.html)|
|  | Red Hat&reg; Enterprise Linux&reg; 7 (Kernel 3.x) (64-bit)| |
|  | | Microsoft&reg; Windows Server 2016 (64-bit)|
|  | | Microsoft&reg; Office 2016 |
|  | | OpenOffice 4.1.2 |


>[!NOTE]
>
> A deprecated platform continue to receive support until the next full installer release or until third-party vendor support for the platform reaches its end-of-life, whichever is earlier.
-->
<!-- 
- Oct 10, 2021

  - Changed supported version of iOS for AEM Forms App to iOS 15.1. The previous version was iOS 12.

- Sep 07, 2021
  - **Platform Updates**: [!DNL Adobe Experience Manager Forms] on JEE has added support for the following platforms:
    - [!DNL Adobe Acrobat 2020]
    - [!DNL Ubuntu 20.04]
    - [!DNL Open Office 4.1.10]
    - [!DNL Microsoft&reg;&reg; Office 2016]
    - [!DNL Microsoft&reg;&reg; Windows Server 2016]
    - [!DNL RHEL8]

- Dec 03, 2020
  - Support added with AEM Forms 6.5.7.0 or later for the following platform:
    - [!DNL Microsoft&reg;&reg; SQL Server 2019]

- Sep 09, 2020

    - Changed supported version of iOS for AEM Forms App to iOS 12. The previous version was iOS 11.

-->
