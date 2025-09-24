---
title: portalcomponenten voor formulieren inschakelen
description: Forms Portal-componenten zijn uitgeschakeld. Schakel Document Services en Document Services Predicates-groepen in om Forms Portal-componenten in te schakelen.
content-type: reference
products: SG_EXPERIENCEMANAGER/6.5/FORMS
topic-tags: publish
feature: Forms Portal
solution: Experience Manager, Experience Manager Forms
role: User, Developer
exl-id: a537fc63-b894-4e47-a71f-98ea07747baa
source-git-commit: 30ec8835be1af46e497457f639d90c1ee8b9dd6e
workflow-type: tm+mt
source-wordcount: '333'
ht-degree: 0%

---

# portalcomponenten voor formulieren inschakelen {#enabling-forms-portal-components}

## Van toepassing op {#applies-to}

Deze documentatie is op **AEM 6.5 LTS Forms** van toepassing.

Voor de documentatie van AEM as a Cloud Service, zie [ AEM Forms op Cloud Service ](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/adaptive-forms-authoring/authoring-adaptive-forms-foundation-components/configure-forms-portal.html).

De onderdelen van de portal Formulieren zijn niet beschikbaar voor gebruik. Voer de volgende stappen uit om de componenten weer te geven in de lijst met beschikbare componenten in AEM Help:

1. Meld u aan bij de auteur van uw website en open een AEM Sites-pagina.

1. Voer de volgende stappen uit voor de pagina&#39;s die een statische sjabloon gebruiken:

   1. In de paginakop, uitgezochte ![ canvas-drop-down ](assets/canvas-drop-down.png) > **Ontwerp** om de pagina op de wijze van het Ontwerp te openen.
   1. Selecteer om het even welke component (met een blauwe grens) en selecteer dan ![ gebied-niveau ](assets/field-level.png) om het paragraafsysteem te selecteren dat de huidige component bevat.
   1. In het paragraafsysteem, uitgezochte ![ settings_icon ](assets/settings_icon.png) om de Edit dialoog voor het paragraafsysteem te openen.
   1. Schakel in de lijst van **[!UICONTROL Allowed Components]** selectievakjes in voor **[!UICONTROL Document Services]** - en **[!UICONTROL Document Services Predicates]** -componenten. Selecteer **[!UICONTROL OK]** .

1. Voer de volgende stappen uit voor de pagina&#39;s die een dynamische sjabloon gebruiken:

   1. In de paginakop, uitgezocht ![ eigenschappen ](assets/properties.png) > **geef Malplaatje** uit om het malplaatje van de pagina te openen.
   1. Selecteer **Container van de Lay-out** en selecteer ![ FeedManagement ](/help/forms/using/assets/feedmanagement.png). In het **Toegestane lusje van Componenten**, laat de **Diensten van het Document en de Predicates van de Diensten van het Document** opties toe, en selecteert ![ aem_6_3_forms_save ](assets/aem_6_3_forms_save.png).

>[!NOTE]
>
>U kunt ook specifieke componenten van deze categorieën inschakelen door de componenten te selecteren. Voor meer informatie over de componenten en hun gebruik, zie [ Creërend een pagina van het vormportaal ](/help/forms/using/creating-form-portal-page.md) en [ het Inbedden van verbindingscomponent in een pagina ](/help/forms/using/embedding-link-component-page.md).

De componentcategorieën Document Services en Document Services Predicates zijn nu beschikbaar in de componentbrowser. De componenten worden ingeschakeld voor alle pagina&#39;s die dezelfde sjabloon gebruiken.

## Verwante artikelen

* [Formulierportonderdelen inschakelen](/help/forms/using/enabling-forms-portal-components.md)
* [Pagina Formulierportal maken](/help/forms/using/creating-form-portal-page.md)
* [Formulieren op een webpagina weergeven met API&#39;s](/help/forms/using/listing-forms-webpage-using-apis.md)
* [Concepten en verzendingscomponent gebruiken](/help/forms/using/draft-submission-component.md)
* [Opslag van concepten en verzonden formulieren aanpassen](/help/forms/using/draft-submission-component.md)
* [Voorbeeld voor het integreren van concepten en verzendingen in de database](/help/forms/using/integrate-draft-submission-database.md)
* [Sjablonen aanpassen voor componenten van een formulierportal](/help/forms/using/customizing-templates-forms-portal-components.md)
* [Inleiding tot het publiceren van formulieren op een portal](/help/forms/using/introduction-publishing-forms.md)
