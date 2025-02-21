---
title: AEM-projecten ontwikkelen met Eclipse
description: In deze handleiding wordt beschreven hoe u Eclipse kunt gebruiken voor het ontwikkelen van op AEM gebaseerde projecten
contentOwner: msm-service
products: SG_EXPERIENCEMANAGER/6.5/SITES
topic-tags: development-tools
content-type: reference
solution: Experience Manager, Experience Manager Sites
feature: Developing,Developer Tools
role: Developer
source-git-commit: 29391c8e3042a8a04c64165663a228bb4886afb5
workflow-type: tm+mt
source-wordcount: '434'
ht-degree: 0%

---

# AEM-projecten ontwikkelen met Eclipse{#how-to-develop-aem-projects-using-eclipse}

In deze handleiding wordt beschreven hoe u Eclipse kunt gebruiken voor het ontwikkelen van op AEM gebaseerde projecten.

>[!NOTE]
>
>Adobe verstrekt nu de [ Hulpmiddelen van de Ontwikkeling van AEM voor Eclipse ](/help/sites-developing/aem-eclipse.md) die u helpt om de oplossingen van AEM met Eclipse te ontwikkelen.

## Overzicht {#overview}

Om aan de slag te gaan met AEM-ontwikkeling op Eclipse, zijn de volgende stappen vereist.

Elk van hen wordt meer in detail beschreven in de rest van dit hoe te.

* Eclipse 4.3 (Kepler) installeren
* AEM-project instellen op basis van Maven
* JSP-ondersteuning voorbereiden voor Eclipse in de Maven POM
* Geweven project importeren in Eclipse

>[!NOTE]
>
>Deze handleiding is gebaseerd op Eclipse 4.3 (Kepler) en AEM 5.6.1.

## Eclipse installeren {#install-eclipse}

Download winde van de &quot;Verduistering voor de Ontwikkelaars van Java EE&quot;van de [ pagina van de Downloads van de Verduistering ](https://www.eclipse.org/downloads/).

Installeer Verduistering na de [ Instructies van de Installatie ](https://wiki.eclipse.org/Eclipse/Installation).

## AEM-project instellen op basis van Maven {#set-up-your-aem-project-based-on-maven}

Daarna, opstelling uw project gebruikend Maven zoals die in [ wordt beschreven hoe te om de Projecten van AEM te bouwen gebruikend Apache Maven ](/help/sites-developing/ht-projects-maven.md).

## JSP-ondersteuning voorbereiden voor Eclipse {#prepare-jsp-support-for-eclipse}

Eclipse kan bijvoorbeeld ook ondersteuning bieden bij het werken met JSP.

* tagbibliotheken automatisch invullen
* Eclipsebewustzijn van objecten die worden gedefinieerd door &lt;cq:defineObjects /> en &lt;sling:defineObjects />

Om dat te doen:

1. Volg de instructies op [ hoe te met JSPs ](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) in [ hoe te om de Projecten van AEM te bouwen gebruikend Apache Maven ](/help/sites-developing/ht-projects-maven.md).
1. Voeg het volgende toe aan de &lt;build /> sectie in POM van uw inhoudsmodule.

   Met de Maven-supportplug-in van Eclipse, m2e, wordt de maven-jspc-plugin niet ondersteund. Met deze configuratie wordt aan m2e doorgegeven dat de plug-in en de bijbehorende taak om de resultaten van de tijdelijke compilatie op te schonen, moeten worden genegeerd.

   Dit is geen probleem: zoals vermeld in [ hoe te met JSPs ](/help/sites-developing/ht-projects-maven.md#how-to-work-with-jsps) te werken, wordt de maven-jspc-stop in deze opstelling slechts gebruikt om te bevestigen dat JSPs als deel van het bouwstijlproces compileert. Eclipse rapporteert al problemen in JSPs en vertrouwt niet op deze Maven plugin om dit te kunnen doen.

   **myproject/content/pom.xml**

   ```xml
   <build>
     <!-- ... -->
     <pluginManagement>
       <plugins>
         <!--This plugin's configuration is used to store Eclipse m2e settings only. It has no influence on the Maven build itself.-->
         <plugin>
           <groupId>org.eclipse.m2e</groupId>
           <artifactId>lifecycle-mapping</artifactId>
           <version>1.0.0</version>
           <configuration>
             <lifecycleMappingMetadata>
               <pluginExecutions>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.sling</groupId>
                     <artifactId>maven-jspc-plugin</artifactId>
                     <versionRange>[2.0.6,)</versionRange>
                     <goals>
                       <goal>jspc</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
                 <pluginExecution>
                   <pluginExecutionFilter>
                     <groupId>org.apache.maven.plugins</groupId>
                     <artifactId>maven-clean-plugin</artifactId>
                     <versionRange>[2.4.1,)</versionRange>
                     <goals>
                       <goal>clean</goal>
                     </goals>
                   </pluginExecutionFilter>
                   <action>
                     <ignore/>
                   </action>
                 </pluginExecution>
               </pluginExecutions>
             </lifecycleMappingMetadata>
           </configuration>
         </plugin>
       </plugins>
     </pluginManagement>
   </build>
   ```

### Geweven project importeren in Eclipse {#import-the-maven-project-into-eclipse}

1. Kies in Eclipse Bestand > Importeren...
1. Kies Geweven > Bestaande gefabriceerde projecten in het dialoogvenster Importeren en klik op Volgende.

   ![ chlimage_1-41 ](assets/chlimage_1-41a.png)

1. Voer het pad naar de map op het hoogste niveau van uw project in en klik op Alles selecteren en Voltooien.

   ![ chlimage_1-42 ](assets/chlimage_1-42a.png)

1. U bent nu allen klaar om Eclipse te gebruiken om uw AEM-project te ontwikkelen, met inbegrip van autocompletion JSP.

   ![ chlimage_1-43 ](assets/chlimage_1-43a.png)

   >[!NOTE]
   >
   >Als u `/libs/foundation/global.jsp` of andere JSPs in `/libs` omvat, moet u dat aan uw project kopiëren zodat kan de Verduistering de opneming oplossen. Tegelijkertijd moet u ervoor zorgen dat het pakket niet door Maven in het inhoudspakket wordt opgenomen. Hoe te om dit te bereiken wordt beschreven in [ hoe te om de Projecten van AEM te bouwen gebruikend Apache Maven ](/help/sites-developing/ht-projects-maven.md).
