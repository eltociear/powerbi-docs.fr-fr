---
title: Correction de l’erreur « Votre certificat SSL d’entreprise n’est pas approuvé »
description: Lorsque vous vous connectez à une application Android pour Power BI, vous pouvez voir le message « Authentification impossible car votre certificat SSL d’entreprise n’est pas approuvé
.": ''
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 03/11/2020
ms.author: painbar
ms.openlocfilehash: a68644c63d3d5eaeb54a71683629af01817d62a7
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "79114599"
---
# <a name="fixing-corporate-ssl-certificate-is-untrusted---power-bi"></a>Correction de l’erreur « Votre certificat SSL d’entreprise n’est pas approuvé » - Power BI
Lorsque vous vous connectez à une application mobile Android pour Microsoft Power BI, vous pouvez voir le message « Authentification impossible car votre certificat SSL d’entreprise n’est pas approuvé par cet appareil. Contactez l’administrateur informatique de votre entreprise. » 

La procédure à suivre dépend généralement du système d’exploitation de votre appareil Android, mais quelques autres problèmes peuvent être à l’origine de cette erreur.

## <a name="on-android-7-or-later"></a>Sur Android 7 ou version ultérieure
Recherchez une mise à jour pour une application nommée **Chrome**, puis installez-la.

## <a name="on-android-6-and-earlier"></a>Sur Android 6 et versions antérieures
Votre appareil a peut-être besoin d’une version mise à jour de System Webview. Il se peut que ce dernier soit installé sur votre appareil et que vous deviez simplement cliquer sur **Mettre à jour**.

Si System Webview n’est pas installé sur votre appareil :

1. Sur votre téléphone Android, fermez Power BI.
2. Ouvrez Google Play Store et recherchez **System Webview**, par Google Inc.
3. Installez-le.
4. Redémarrez l’application Power BI et connectez-vous.

## <a name="time-zone-settings"></a>Paramètres de fuseau horaire
Il se peut que les paramètres de fuseau horaire de votre appareil soient erronés. 

Accédez à **Paramètres** > **Système** > **Date et heure** pour les vérifier.

## <a name="custom-authentication-server"></a>Serveur d’authentification personnalisé
Si vous utilisez un serveur d’authentification personnalisé, il se peut que le certificat SSL du serveur d’authentification d’entreprise ne soit pas valide. Collaborez avec le service informatique de votre organisation pour tester la configuration du serveur d’authentification d’entreprise, en suivant les instructions données dans [cet article](https://support.microsoft.com/help/3203929/using-adal-to-authenticate-from-android-devices-fails-if-additional-ce).

## <a name="next-steps"></a>Étapes suivantes
* [Téléchargez l’application Android](https://go.microsoft.com/fwlink/?LinkID=544867) à partir du magasin d’applications Android.
* Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/) 

