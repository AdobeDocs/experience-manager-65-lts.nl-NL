---
title: Een Correspondentiebeheeroplossing configureren
description: Leer hoe u een Correspondence Management-oplossing configureert in een AEM Forms-omgeving.
topic-tags: correspondence-management
content-type: reference
products: SG_EXPERIENCEMANAGER/6.3/FORMS
feature: Correspondence Management
solution: Experience Manager, Experience Manager Forms
role: Admin, User, Developer
exl-id: da668935-9d16-49e1-8e7a-772fc4040c1d
source-git-commit: c3e9029236734e22f5d266ac26b923eafbe0a459
workflow-type: tm+mt
source-wordcount: '283'
ht-degree: 0%

---

# Een Correspondentiebeheeroplossing configureren {#configuring-a-correspondence-management-solution}

## URL van auteurinstantie voor VersionRestoreManagerImpl bepalen {#defining-author-instance-url-for-versionrestoremanagerimpl}

Gebruik de volgende stappen om een instantie-URL van de auteur te definiëren voor het terugzetten van de auteurversie:

1. Ga naar *https://:&lt;PublishHost>:&lt;PublishPort>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Klik op het pictogram **[!UICONTROL Edit]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.VersionRestoreManagerImpl.name]** .
1. Geef in het veld **[!UICONTROL VersionRestoreManager Author URL]** de URL van de instantie Auteur van VersionRestoreManager op.

   **koord URL**:

   `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.VersionRestoreManager`

   >[!NOTE]
   >
   >Als er meerdere auteur-instanties (geclusterd) zijn met een taakverdeler, geeft u de URL voor het taakverdelingsmechanisme op in het veld **[!UICONTROL VersionRestoreManager Author URL]** .

1. Klik op **[!UICONTROL Save]**.

## De URL van de instantie Publish definiëren voor ActivationManagerImpl (public instance activation manager) {#defining-the-publish-instance-url-for-activationmanagerimpl-public-instance-activation-manager}

Voer de volgende stappen uit, zodat u de URL van de instantie Publiceren kunt definiëren voor het beheer voor activering van openbare instanties:

1. Ga naar *https://:&lt;auteurHost>:&lt;auteurshaven>/lc/system/console/configMgr*. Meld u aan met de gebruikersgegevens van de OSGi Management Console. De standaardreferenties zijn admin/admin.
1. Klik op het pictogram **[!UICONTROL Edit]** naast de instelling **[!UICONTROL com.adobe.livecycle.content.activate.impl.ActivationManagerImpl.name]** .
1. Geef in het veld **[!UICONTROL ActivationManager Publish URL]** de URL op voor toegang tot de instantie Publish ActivationManager. U kunt de volgende URL&#39;s opgeven.

   * **de Balancer URL van de Lading (geadviseerd)**: Verstrek ladingsverdeler URL, als u een webserver hebt die als ladingsverdelingsmiddel vóór publiceer landbouwbedrijf (veelvoudige niet-gegroepeerde publiceer instanties) dienst doet.
   * **publiceer instantie URL**: Verstrek om het even welk publiceer instantie URL, als u één enkel publiceer instantie hebt of webserver die het publiceer landbouwbedrijf voorafgaat niet toegankelijk van het auteursmilieu toe te schrijven aan om het even welke beperkingen. Als de opgegeven publicatie-instantie is ingedrukt, is er een fallback-mechanisme waarmee aan de auteurzijde moet worden omgegaan.
   * **koord URL**:

     `https://<hostname>:<port>:/libs/fd/fdm/content/crud/lc.content.remote.activate.activationManager`

1. Klik op **[!UICONTROL Save]**.

Voor meer informatie over het vormen van het Beheer van de Correspondentie, zie {de Eigenschappen van de Configuratie van het Beheer van de Correspondentie ](https://helpx.adobe.com/aem-forms/6-2/cm-configuration-properties.html).[
