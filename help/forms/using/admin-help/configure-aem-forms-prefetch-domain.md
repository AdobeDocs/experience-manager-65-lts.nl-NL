---
title: AEM-formulieren configureren voor Prefetchdomain-informatie
description: Configureer AEM-formulieren voor het vooraf instellen van domeininformatie als u een langzamere responstijd hebt vanwege diepgeneste groepen of als u lid bent van veel groepen.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_user_management
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 61328a32-d014-4a90-b142-169f4f73b35f
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '174'
ht-degree: 0%

---

# AEM-formulieren configureren voor Prefetchdomain-informatie {#configure-aem-forms-to-prefetchdomain-information}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

De gebruikers kunnen een langzamere reactietijd ervaren als zij tot vele groepen (bijvoorbeeld, 500 of meer) behoren of als de groepen diep worden genesteld (bijvoorbeeld, 30 niveaus). Als dit probleem optreedt, kunt u AEM-formulieren configureren om gegevens in bepaalde domeinen vooraf in te voeren.

1. Klik in de beheerconsole op **[!UICONTROL Settings > User Management > Configuration > Import And Export Configuration Files]** .
1. Als u de huidige configuratie-instelling naar een bestand wilt exporteren, klikt u op **[!UICONTROL Export]** en slaat u het configuratiebestand op een andere locatie op.
1. Voeg het volgende knooppunt toe (vet gemarkeerd):

   ```xml
    <node name="UM">
    <map/>
    <node name="PrincipalCache">
        <map>
            <entry key="principalCacheSize" value="1000"/>
            <entry key="principalCacheBatchFetchSize" value="10"/>
            <entry key="rebuildCacheAfterSync" value="true />
            <entry key="enableFullPrefetch" value="false"/>
            <entry key="principalCacheDomains" value="Domain_Name1/Domain_Name2/Domain_Name3"/>
        <map>
    </node>
    <node name="APSAuditService">
   ```

   In dit voorbeeld worden meerdere domeinen geconfigureerd voor prefetch. De domeinnamen worden gescheiden door een &quot;/&quot;. Dit wordt getoond in het voorbeeld hierboven met *Domain_Name1*, *Domain_Name2*, en *Domain_Name3*.

1. Klik in Gebruikersbeheer op **[!UICONTROL Configuration > Import And Export Configuration Files]** om het bijgewerkte bestand te importeren.
1. Klik op **[!UICONTROL Browse]** om het bestand te zoeken, klik op Importeren en klik vervolgens op **[!UICONTROL OK]** .
