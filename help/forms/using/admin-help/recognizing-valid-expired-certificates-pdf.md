---
title: Geldige en verlopen certificaten in PDF-documenten herkennen
description: Leer hoe u geldige en verlopen certificaten in PDF-documenten herkent.
contentOwner: admin
content-type: reference
geptopics: SG_AEMFORMS/categories/configuring_acrobat_reader_dc_extensions
products: SG_EXPERIENCEMANAGER/6.5/FORMS
solution: Experience Manager, Experience Manager Forms
feature: Adaptive Forms
role: User, Developer
hide: true
hidefromtoc: true
exl-id: f7402f0d-7c19-4a56-8630-208faa197f94
source-git-commit: bc91f56d447d1f2c26c160f5c414fd0e6054f84c
workflow-type: tm+mt
source-wordcount: '197'
ht-degree: 0%

---

# Geldige en verlopen certificaten in PDF-documenten herkennen {#recognizing-valid-and-expired-certificates-in-pdf-documents}

Wanneer een PDF-document waarop gebruiksrechten zijn toegepast door Reader Extensions wordt geopend in Adobe Reader, wordt een statusbalk weergegeven met een beschrijving van de specifieke gebruiksrechten die zijn ingeschakeld in het PDF-document.

Wanneer het digitale certificaat dat de gebruiksrechten voor een PDF-document opgeeft, verloopt en het PDF-document wordt geopend in Adobe Reader, wordt de gebruiker in een dialoogvenster gewaarschuwd dat het PDF-document gebruiksrechten heeft, maar deze rechten zijn uitgeschakeld. Hoewel het bericht aangeeft dat het PDF-document is gewijzigd of gewijzigd, is dit niet altijd het geval. Dit bericht wordt weergegeven in Adobe Reader wanneer een certificaat verloopt of wanneer een document is gewijzigd. In Adobe Reader 7.0.x of hoger kunt u niet bepalen welk geval momenteel het probleem is.

Nadat u het dialoogvenster hebt gesloten, opent Adobe Reader het PDF-document. De gebruiksrechten die zijn toegepast met Acrobat Reader DC-extensies zijn niet beschikbaar, zoals u had verwacht. Als het PDF-document een interactief formulier is, worden de formuliervelden vergrendeld en kan de gebruiker de formuliergegevens niet wijzigen.
