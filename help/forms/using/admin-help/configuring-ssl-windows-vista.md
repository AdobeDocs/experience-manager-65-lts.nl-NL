---
title: SSL configureren onder Windows Vista
description: Leer hoe te om SSL op Windows Vista te vormen. Gebruik en voer het Java Keytool uit om het SSL-certificaat te genereren met RSA-sleutels voor de verificatie.
solution: Experience Manager, Experience Manager Forms
feature: Document Security
role: User, Developer
hide: true
hidefromtoc: true
exl-id: ee73f6a1-712c-461f-95e8-85f8c5694293
source-git-commit: d0f29cb177e98315cd50c2d7e96c3605eec14885
workflow-type: tm+mt
source-wordcount: '173'
ht-degree: 0%

---

# SSL configureren onder Windows Vista {#configuring-ssl-on-windows-vista}

Om SSL op Windows Vista™ te vormen, hebt u een SSL certificaat met sleutels van RSA voor authentificatie nodig. U kunt het Java-sleutelgereedschap gebruiken om het certificaat te maken.

>[!NOTE]
>
>Windows Vista werkt niet met DSA-toetsen.

U kunt keytool uitvoeren met één opdracht die alle informatie bevat die nodig is om het certificaat en sleutelarchief te maken.

**creeer een SSL certificaat**

1. In een bevelherinnering, navigeer aan *`[JAVA HOME]`*/bin en typ het volgende bevel om het certificaat en keystore tot stand te brengen:

   *`, OU=`* de Naam van de Groep *`, O=`* Naam van het Bedrijf *`,L=`* Naam van de Stad *`, S=`* Staat *`, C=`* Code van het Land *`" -alias`* &quot;Cert LC&quot;*`-keypass` `key`* _ **&#x200B; sleutelwoord `-keystore`*storename* `.keystore` `keytool -genkey -keyalg RSA -dname "CN=`**

   >[!NOTE]
   >
   >Vervang *`[JAVA_HOME]`door de map waarin de JDK is geïnstalleerd en vervang de cursieve tekst door waarden die overeenkomen met uw omgeving.*

1. Typ `changeit` als wachtwoord. Dit wachtwoord is de standaardinstelling voor een Java-installatie en de systeembeheerder kan deze hebben gewijzigd.
