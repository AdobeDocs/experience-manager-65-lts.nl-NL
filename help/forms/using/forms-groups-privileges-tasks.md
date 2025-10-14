---
title: AEM Forms over OSGi-groepen en -voorrechten
description: Gebruikers toewijzen aan groepen om Adobe Experience Manager (AEM) Forms te beheren op OSGi
contentOwner: anujkapo
products: SG_EXPERIENCEMANAGER/6.5/FORMS
content-type: reference
topic-tags: Configuration
docset: aem65
role: Admin,User
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
exl-id: 1681e92b-2d88-4b10-a700-a516aa5a02c8
source-git-commit: 30ec8835be1af46e497457f639d90c1ee8b9dd6e
workflow-type: tm+mt
source-wordcount: '298'
ht-degree: 0%

---

# AEM Forms over OSGi-groepen en -voorrechten{#aem-forms-on-osgi-groups-and-privileges}

## Van toepassing op {#applies-to}

Deze documentatie is op **AEM 6.5 LTS Forms** van toepassing.

Voor de documentatie van AEM as a Cloud Service, zie [&#x200B; AEM Forms op Cloud Service &#x200B;](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/forms/setup-configure-migrate/forms-groups-privileges-tasks.html?lang=nl-NL).

U kunt [&#x200B; groepen &#x200B;](/help/sites-administering/user-group-ac-admin.md#group-administration) tot stand brengen en beleid en [&#x200B; gebruikers &#x200B;](/help/sites-administering/user-group-ac-admin.md#user-administration) toewijzen aan de groepen in Adobe Experience Manager (AEM). Dit beleid controleert de voorrechten van de gebruikers die deel van de groep uitmaken.

Nadat u het [&#x200B; toe:voegen-op pakket van AEM Forms &#x200B;](../../forms/using/installing-configuring-aem-forms-osgi.md) installeert, zijn de groepen die in dit artikel, zoals vorm-gebruikers en vorm-macht-gebruiker worden vermeld, automatisch beschikbaar voor taak. De volgende lijst maakt een lijst van de taken die een gebruiker voor AEM Forms op OSGi kan uitvoeren die op de groepstoewijzingen wordt gebaseerd:

<table>
 <tbody>
  <tr>
   <td>Groep</td> 
   <td>Taken</td> 
  </tr>
  <tr>
   <td>forms-users <sup>[1] </sup></td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren maken, voorvertonen, publiceren en verzenden</li> 
     <li>Interactieve communicatie en documentfragmenten maken, voorvertonen en publiceren</li> 
     <li>Elementen uploaden naar een AEM-instantie</li> 
     <li>Thema's maken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>formulieren-grootgebruikers</td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren maken, voorvertonen, publiceren en verzenden</li> 
     <li>Interactieve communicatie en documentfragmenten maken, voorvertonen en publiceren</li> 
     <li>Scripts maken voor adaptieve formulieren met behulp van een code-editor</li> 
     <li>Elementen uploaden, inclusief scripts</li> 
     <li>Thema's maken</li> 
     <li>Pakketten importeren die XDP bevatten</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>formulierverzendingsrevisoren</td> 
   <td>
    <ul> 
     <li>Herziening</li> 
     <li>Indieningen goedkeuren of afwijzen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>template-auteurs <sup> [2] </sup></td> 
   <td>
    <ul> 
     <li>Aangepaste formulieren of interactieve communicatiesjablonen maken en hiervan een voorbeeld bekijken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>fdm-auteurs</p> </td> 
   <td>
    <ul> 
     <li>Een formuliergegevensmodel maken en wijzigen</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>cm-agent-gebruikers</td> 
   <td>
    <ul> 
     <li>Toegang tot correspondentiebeheerbrieven of interactieve communicatie met de gebruikersinterface van de Agent</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td><p>workfloweditors</p> </td> 
   <td>
    <ul> 
     <li>Een inbox-toepassing maken</li> 
     <li>Een workflowmodel maken</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>workflowgebruikers</td> 
   <td>
    <ul> 
     <li>De toepassingen van AEM Inbox van het gebruik <br /> <strong> Nota: </strong> u moet cm-agent-gebruikers en werkschema-gebruikers groepstaken hebben om tot de Interactieve Communicatie Agent UI in AEM Inbox toegang te hebben.</li> 
     <li>Workflowinstanties beheren</li> 
    </ul> </td> 
  </tr>
  <tr>
   <td>fd-beheerders</td> 
   <td>
    <ul> 
     <li>PDF Generator configureren</li> 
     <li>De map Gecontroleerd configureren</li> 
     <li>Workflowtoepassingen beheren</li> 
    </ul> </td> 
  </tr>
 </tbody>
</table>

1. De gebruiker met groepsrechten voor formulieren kan geen scripts schrijven voor adaptieve formulieren.
1. De gebruiker met de groepsrechten voor sjabloonauteurs kan geen scripts voor sjablonen schrijven.
