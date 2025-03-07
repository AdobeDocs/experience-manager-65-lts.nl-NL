---
title: Upgrade naar AEM 6.5 Forms LTS op OSGi
description: U kunt een directe upgrade uitvoeren van AEM 6.5.22.0 Forms naar AEM 6.5 Forms LTS.
content-type: reference
role: Admin, User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms, AEM Forms on OSGi, AEM Forms Upgrade
exl-id: 9233d4b7-441c-4cbd-86f8-2c52b99c3330
source-git-commit: dd45dfe953a111ccbbc71e8e25a8a2577037587a
workflow-type: tm+mt
source-wordcount: '822'
ht-degree: 0%

---

# Upgrade naar AEM 6.5 Forms LTS op OSGi {#upgrade-to-aem-forms-osgi}

Aan [ verbetering van AEM 6.5 aan AEM 6.5 LTS ](/help/sites-deploying/upgrade.md), verbetering aan AEM 6.5.22.0 Forms of later. Een directe upgrade van AEM 6.5.22.0 naar AEM 6.5 Forms LTS wordt ondersteund.

Als u AEM 6.0 Forms, AEM 6.1 Forms, AEM 6.2 Forms, AEM 6.3 Forms, AEM 6.4 Forms of AEM 6.5 Forms gebruikt, is een directe upgrade naar AEM 6.5 Forms LTS niet beschikbaar. Voor gedetailleerde verbeteringswegen, verwijs naar de [ documentatie van de Wegen van de Verbetering ](/help/forms/using/upgrade.md).

Na upgrade naar het servicepack AEM Forms 6.5.22.0 voert u de volgende stappen uit om te upgraden naar AEM 6.5 LTS Forms:

1. Installeer het AEM Forms-invoegtoepassingspakket. De stappen worden hieronder weergegeven:

   1. Open [ Distributie van de Software ](https://experience.adobe.com/downloads). U hebt een Adobe ID nodig om u aan te melden bij de softwaredistributie.
   1. Selecteer **[!UICONTROL Adobe Experience Manager]** beschikbaar in het koptekstmenu.
   1. In de sectie **[!UICONTROL Filters]** :
      1. Selecteer **[!UICONTROL Forms]** in de vervolgkeuzelijst **[!UICONTROL Solution]** .
      1. Selecteer de versie en typ voor het pakket. U kunt de optie **[!UICONTROL Search Downloads]** ook gebruiken om de resultaten te filteren.
   1. Selecteer de pakketnaam die van toepassing is op het besturingssysteem, selecteer **[!UICONTROL Accept EULA Terms]** en selecteer **[!UICONTROL Download]** .
   1. Open [ Manager van het Pakket ](/help/sites-administering/package-manager.md) en klik **[!UICONTROL Upload Package]** om het pakket te uploaden.
   1. Selecteer het pakket en klik op **[!UICONTROL Install]** .

      U kunt het pakket ook downloaden gebruikend de directe verbinding die in [ wordt vermeld versies van AEM Forms ](https://experienceleague.adobe.com/en/docs/experience-manager-release-information/aem-release-updates/forms-updates/aem-forms-releases) artikel.

      Nadat het pakket is geïnstalleerd, wordt u gevraagd om het AEM-exemplaar opnieuw te starten. **stop niet onmiddellijk de server.** Voordat u de AEM Forms-server stopt, wacht u tot de berichten ServiceEvent REGISTERED en ServiceEvent UNREGISTERED niet meer worden weergegeven in het bestand &lt;crx-repository>/error.log en het logbestand stabiel is. Houd er rekening mee dat een aantal pakketten in de installatiestatus kunnen blijven staan. U kunt de status van deze verpakkingen veilig negeren.


      **begin de instantie van AEM met de volgende extra bevel-lijn JVM parameters** opnieuw:
      `--add-opens java.base/java.util=ALL-UNNAMED --add-exports=java.xml/com.sun.org.apache.xml.internal.serialize=ALL-UNNAMED`

      Als de server via een script of service wordt gestart, moet u de server overeenkomstig bijwerken zodat het bovenstaande wordt opgenomen zodat deze ook van kracht zijn nadat de server opnieuw is gestart.

      >[!NOTE]
      >
      > U wordt aangeraden de SDK opnieuw op te starten met de opdracht &#39;Ctrl + C&#39;. Het opnieuw opstarten van de AEM SDK met behulp van alternatieve methoden, bijvoorbeeld het stoppen van Java-processen, kan leiden tot inconsistenties in de AEM-ontwikkelomgeving.

1. Nainstallatie uitvoeren.

   * **het Nut van de Migratie van de Looppas**

     Het migratiehulpprogramma maakt de adaptieve formulieren en het beheer van correspondentie van eerdere versies compatibel met AEM 6.5-formulieren. U kunt het hulpprogramma downloaden van AEM Software Distribution. Voor geleidelijke informatie om het migratienut te vormen en te gebruiken, zie [ migratienut ](../../forms/using/migration-utility.md).

     Als u [ Steekproef voor het integreren van concepten &amp; voorleggingscomponent ](https://helpx.adobe.com/experience-manager/6-3/forms/using/integrate-draft-submission-database.html) met het gegevensbestand en de bevordering van een vorige versie gebruikt, dan stel de volgende SQL vragen na het uitvoeren van de verbetering in werking:

     ```sql
     UPDATE metadata m, additionalmetadatatable am
     SET m.dataType = am.value
     WHERE m.id = am.id
     AND am.key = 'dataType'
     ```

     ```sql
     DELETE from additionalmetadatatable
     WHERE `key` = 'dataType'
     ```

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Adobe Sign opnieuw configureren**

     Als Adobe Sign was geconfigureerd in de vorige versie van AEM Forms, configureert u Adobe Sign vervolgens opnieuw vanuit de AEM Cloud-services. Voor meer details, zie [ het Teken van Adobe met AEM Forms ](../../forms/using/adobe-sign-integration-adaptive-forms.md) integreren.

   * **Steun voor jQuery**

     In AEM 6.5 Forms wordt de versie van jQuery bijgewerkt naar versie 3.2.1 en de versie van jQuery-gebruikersinterface naar versie 1.12.1. De Vorm van AEM gebruikt JQuery op **noConflict** wijze. Als u dus een andere jQuery-versie gebruikt, worden er geen problemen weergegeven tijdens het uitvoeren van een upgrade. Als u echter een upgrade uitvoert naar AEM 6.5 Forms:

      * Controleer of uw aangepaste componenten, indien aanwezig, compatibel zijn met ondersteunde jQuery-versies.
      * Verwijder niet-ondersteunde API&#39;s uit de aangepaste componenten. Zie [ verbeteringsgids ](https://jquery.com/upgrade-guide/3.0/) voor de lijst van verwijderde APIs. Ondersteuning voor de API&#39;s load(), .unload() en .error() wordt bijvoorbeeld verwijderd. Gebruik de methode .on() in plaats van de eerder genoemde API&#39;s. Wijzig bijvoorbeeld $(&quot;img&quot;).load(fn) in $(&quot;img&quot;).on(&quot;load&quot;, fn).

   * **(Als u een upgrade uitvoert van alleen AEM 6.2 Forms of eerdere versies) Analyses en rapporten opnieuw samenstellen**

     In AEM 6.4 Forms is de verkeersvariabele voor de bron- en succesgebeurtenis voor de indruk niet beschikbaar. Als u dus een upgrade uitvoert van AEM 6.2 Forms of eerdere versies, stopt AEM Forms met het verzenden van gegevens naar de Adobe Analytics-server en zijn er geen analyserapporten voor adaptieve formulieren beschikbaar. Bovendien introduceert AEM 6.4 Forms een verkeersvariabele voor de versie van formulieranalyse en succesgebeurtenis voor de hoeveelheid tijd die aan een veld wordt doorgebracht. Configureer daarom analyses en rapporten voor uw AEM Forms-omgeving. Voor gedetailleerde stappen, zie [ het Vormen analyses en rapporten ](../../forms/using/configure-analytics-forms-documents.md).

1. Controleer of de upgrade van de server is geslaagd, of alle gegevens zijn gemigreerd en of deze op de normale manier kunnen werken.

   * **verifieer het statuut van de bundels:** zorg ervoor dat alle bundels in actieve staat zijn.
   * **verifieer replicatie en omgekeerde replicatie:** publiceer, vul, en verzend een paar gemigreerde vormen. Controleer ook de verzonden gegevens.
   * **verifieer toegang tot admin en het gebruikersinterfaces van de ontwikkelaar:** Login aan de instantie van AEM van een admin rekening en verifieer dat u toegang tot volgende URLs hebt:

      * `https://'[server]:[port]'/crx/packmgr`
      * `https://'[server]:[port]'/crx/de`
      * `https://'[server]:[port]'/aem/forms.html/content/dam/formsanddocuments`

   >[!NOTE]
   >
   >In AEM 6.4 Forms is de structuur van crx-repository veranderd. Als u een upgrade uitvoert van 6.3 Forms naar AEM 6.5 Forms, gebruikt u de gewijzigde paden voor aanpassing die u opnieuw maakt. Voor de volledige lijst van veranderde wegen, zie [ de Herstructurering van de Bewaarplaats van Forms in AEM ](https://experienceleague.adobe.com/en/docs/experience-manager-65/content/implementing/deploying/restructuring/forms-repository-restructuring-in-aem-6-5).
