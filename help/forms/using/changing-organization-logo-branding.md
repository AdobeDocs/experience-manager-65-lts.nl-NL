---
title: Het bedrijfslogo voor branding wijzigen
description: Als u een merk wilt aanbrengen in de AEM Forms-werkruimte, kunt u het logo van uw organisatie opgeven door het standaardlogo aan te passen.
contentOwner: robhagat
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: forms-workspace
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
exl-id: 3aa4aca3-3c94-4936-ba9c-484bbb196256
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '119'
ht-degree: 0%

---

# Het bedrijfslogo voor branding wijzigen {#changing-the-organization-logo-for-branding}

Het bedrijfslogo wordt linksboven in de AEM Forms-werkruimte weergegeven. Om het embleem bij te werken, volg de [ Algemene stappen van de aanpassing van de werkruimte van AEM Forms ](/help/forms/using/generic-steps-html-workspace-customization.md#generic-steps-for-html-workspace-customization) en toen de volgende stappen.

1. Maak een logo en noem het bestand als `NewWorkspace.png` . Plaats het afbeeldingsbestand in de map /apps/ws/images met een WebDAV-client.

   >[!NOTE]
   >
   >De aanbevolen grootte van de logoafbeelding is 218 px × 20 px.

   >[!NOTE]
   >
   >Voor meer informatie, zie [ Toegang WebDAV ](https://experienceleague.adobe.com/docs/experience-manager-65-lts/administering/contentmanagement/webdav-access.html?lang=en).

   [ WebDAV Toegang ](https://experienceleague.adobe.com/docs/experience-manager-65-lts/administering/contentmanagement/webdav-access.html?lang=en)

1. Verwijs naar de nieuwe logoafbeelding in stijlblad op /apps/ws/css/newStyle.css door volgende stijl toe te voegen.

   ```css
   #logo {
   
          background: url(../images/NewWorkspace.png) no-repeat 14px 11px;
   
   }
   ```
