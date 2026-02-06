---
title: Vereisten voor integratie met Adobe Target
description: Leer meer over de voorwaarden voor integratie met Adobe Target.
contentOwner: User
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: integration
content-type: reference
docset: aem65
solution: Experience Manager, Experience Manager Sites
feature: Integration
role: Admin
exl-id: e1771229-b2ce-406a-95a5-99b11fafbe34
source-git-commit: 24bd1f57da3f9ce613ee28276d1ae9465b6dfba6
workflow-type: tm+mt
source-wordcount: '511'
ht-degree: 0%

---

# Voorwaarden voor integratie met Adobe Target{#prerequisites-for-integrating-with-adobe-target}

Als deel van de [&#x200B; integratie van AEM en Adobe Target &#x200B;](/help/sites-administering/target.md), moet u met Adobe Target registreren, de replicatieagent, en veilige activiteitenmontages op publiceren knoop vormen.

## Registreren met Adobe Target {#registering-with-adobe-target}

Als u AEM wilt integreren met Adobe Target, hebt u een geldig Adobe Target-account nodig. Deze rekening moet **het niveautoestemmingen van de goedkeuraar** op een minimum hebben. Wanneer u zich bij Adobe Target registreert, ontvangt u een clientcode. U hebt de clientcode en uw Adobe Target-aanmeldingsnaam en -wachtwoord nodig om AEM te verbinden met Adobe Target.

De clientcode identificeert de Adobe Target-klantenaccount wanneer de Adobe Target-server wordt aangeroepen.

>[!NOTE]
>
>Het team van Doel moet uw account inschakelen om de integratie te kunnen gebruiken.
>
>Als het niet het geval is, contacteer [&#x200B; de Zorg van de Klant van Adobe &#x200B;](https://experienceleague.adobe.com/nl/docs/target/using/cmp-resources-and-contact-information).

## Enable the Target Replication Agent {#enabling-the-target-replication-agent}

De Test en van het Doel [&#x200B; replicatieagent &#x200B;](/help/sites-deploying/replication.md) moet op de auteursinstantie worden toegelaten. Merk op dat deze replicatieagent niet door gebrek wordt toegelaten als u de [&#x200B; nosamplcontent &#x200B;](/help/sites-deploying/configure-runmodes.md#using-samplecontent-and-nosamplecontent) looppaswijze gebruikte om AEM te installeren. Voor meer informatie over het beveiligen van uw productiemilieu, zie [&#x200B; Controlelijst van de Veiligheid &#x200B;](/help/sites-administering/security-checklist.md).

1. Op de homepage van AEM, klik **Hulpmiddelen** > **Plaatsing** > **Replicatie**.
1. Klik **Agenten op Auteur**.
1. Klik de **Test en Doel (test en doel)** replicatieagent, en klik dan **uitgeven**.
1. Selecteer de Toegelaten optie, dan klik O.K. **&#x200B;**.

   >[!NOTE]
   >
   >Wanneer u de Test en de replicatieagent van het Doel vormt, in het **Vervoer** lusje, wordt URI geplaatst door gebrek aan `tnt:///`. Vervang deze URI niet door `https://admin.testandtarget.omniture.com` .
   >
   >Als u de verbinding probeert te testen met `tnt:///` , wordt een fout weergegeven die het verwachte gedrag is. De reden hiervoor is dat de URI alleen voor intern gebruik is. Gebruik niet met **Verbinding van de Test**.

## Het knooppunt met activiteiteninstellingen beveiligen {#securing-the-activity-settings-node}

Beveilig de knoop van activiteitenmontages **cq:ActivitySettings** op de het publiceren instantie zodat het voor normale gebruikers ontoegankelijk is. Het knooppunt activity settings mag alleen toegankelijk zijn voor de service die de activiteitensynchronisatie afhandelt voor Adobe Target.

De **cq:ActivitySettings** knoop is beschikbaar in CRXDE Lite onder `/content/campaigns/*nameofbrand*` * *under de activiteiten `jcr:content` knoop. Bijvoorbeeld `/content/campaign/we-retail/master/myactivity/jcr:content/cq:ActivitySettings` . Dit knooppunt wordt alleen gemaakt nadat u een component als doel hebt ingesteld.

De **cq:ActivitySettings** knoop onder de activiteit `jcr:content` wordt beschermd door volgende ACLs:

* Allemaal weigeren.
* `jcr:read,rep:write` for `target-activity-authors` toestaan (de auteur is lid van deze groep uit het vak).
* `jcr:read,rep:write` for `targetservice` toestaan.

Met deze instellingen zorgt u ervoor dat normale gebruikers geen toegang hebben tot de knoopeigenschappen. Gebruik zelfde ACLs op auteur en bij publiceren. Zie [&#x200B; Beleid van de Gebruiker en Veiligheid &#x200B;](/help/sites-administering/security.md) voor meer informatie.

## De AEM Link Externalzer configureren {#configuring-the-aem-link-externalizer}

Wanneer het uitgeven van een activiteit in Adobe Target, richt URL aan **localhost** tenzij u URL op de de auteursknoop van AEM verandert. U kunt de Verbinding van AEM uiterlijk vormen als u de uitgevoerde inhoud aan specifiek *wilt richten publiceert* domein.

>[!NOTE]
>
>Zie ook [&#x200B; de Configuratie van de Wolk &#x200B;](/help/sites-administering/experience-fragments-target.md#add-the-cloud-configuration) toevoegen.

U configureert als volgt de AEM-externalizer:

>[!NOTE]
>
>Voor meer details, zie [&#x200B; het Extern stellen URLs &#x200B;](/help/sites-developing/externalizer.md).

1. Navigeer aan de OSGi Webconsole in **https://&lt;server>:&lt;port>/system/console/configMgr.**
1. Vind **de Verbinding van CQ van de Dag uiterlijk** en ga het domein voor de auteursknoop in.

   ![&#x200B; CQ van de Dag Verbinding Externalzer &#x200B;](assets/aem-externalizer-01.png)
