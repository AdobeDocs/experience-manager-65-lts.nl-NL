---
title: Records uit de taakbeheerdatabase wissen
description: Grote procesgegevens kunnen resulteren in lagere prestaties voor AEM-formulieren. Het is een goede gewoonte om procesgegevens te wissen wanneer records niet meer nodig zijn.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/health_monitor
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: a5e6b09a-c4c7-41c0-8221-d563cb74b3b7
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '483'
ht-degree: 0%

---

# Records uit de taakbeheerdatabase wissen {#purge-records-from-the-job-manager-database}

>[!NOTE]
> 
> Zorg ervoor dat de gebruiker beheerdersrechten heeft om toegang te krijgen tot de beheerdersconsole.

Procesgegevens die worden gegenereerd wanneer een langdurig proces wordt aangeroepen, kunnen te groot worden, wat leidt tot lagere prestaties van AEM-formulieren en het gebruik van overbodige schijfruimte. Het is een goede gewoonte om procesgegevens te wissen wanneer records niet meer nodig zijn.

U kunt beheerconsole gebruiken om een eenmalige verwijdering van verouderde records uit te voeren of om regelmatige automatische verwijdering te plannen. Andere methodes om verouderde verslagen te zuiveren worden besproken in [ het zuiveren procesgegevens ](/help/forms/using/admin-help/purging-process-data.md#purging-process-data).

**heb toegang tot de pagina van de Planner van de Weigering van de Baan**

1. Klik in de beheerconsole op Health Monitor rechtsboven op de pagina.
1. Klik op het tabblad Planfunctie voor taakverwijdering.

De informatie over om het even welke momenteel geplande zuiveringen wordt getoond in de doos van de Informatie van de Planner van de Woorden van de Weg.

>[!NOTE]
>
>Als u op Planner stoppen klikt, worden in de toekomst geplande reinigingsprogramma&#39;s gestopt, maar wordt een taak die al wordt uitgevoerd, niet gestopt.

**Plan een eenmalige zuivering**

1. Selecteer slechts één keer.
1. Geef in het gebied Filter Voltooide records wissen het aantal dagen of weken op waarna een record als verouderd en gereed voor verwijdering wordt beschouwd.

   >[!NOTE]
   >
   >Records die betrekking hebben op processen die niet zijn voltooid, worden niet gezuiverd, zelfs niet als ze ouder zijn dan de opgegeven leeftijd.

1. Geef op wanneer het leegmaken moet plaatsvinden. Schakel het selectievakje Huidige datum en tijd gebruiken in of schakel het selectievakje uit en klik op de pictogrammen Kalender en Klok om de datum en tijd op te geven waarop het leegmaken wordt uitgevoerd.

   >[!NOTE]
   >
   >Als u een begindatum en tijd opgeeft die in het verleden liggen, wordt de verwijdering onmiddellijk uitgevoerd wanneer u op Planner starten klikt.

1. Klik op Start Scheduler. Om het even welke eerder geplande plannermontages worden vervangen met de nieuwe montages.

**vorm een automatisch zuiveringsprogramma**

1. Selecteer Opnieuw uitvoeren om en geef het aantal dagen of weken tussen de purges op.
1. Geef in het gebied Filter Voltooide records wissen het aantal dagen of weken op waarna een record als verouderd en gereed voor verwijdering wordt beschouwd. U kunt de waarde niet instellen op `0` .

   >[!NOTE]
   >
   >Records die betrekking hebben op processen die niet zijn voltooid, worden niet gezuiverd, zelfs niet als ze ouder zijn dan de opgegeven leeftijd.

1. Geef op wanneer de purges moeten beginnen. Schakel het selectievakje Huidige datum en tijd gebruiken in of schakel het selectievakje uit en klik op de pictogrammen Kalender en Klok om de datum en tijd op te geven waarop het leegmaken wordt uitgevoerd.

   >[!NOTE]
   >
   >Als u een begindatum en -tijd opgeeft die in het verleden liggen, berekent AEM-formulieren de logische volgende begindatum op basis van de opgegeven datum. Als u bijvoorbeeld plant dat de taak wekelijks wordt leeggemaakt vanaf 7 april en dat nu 9 april is, vindt de eerste leegloop plaats op 14 april.

1. Klik op Start Scheduler. Om het even welke eerder geplande plannermontages worden vervangen met de nieuwe montages.
