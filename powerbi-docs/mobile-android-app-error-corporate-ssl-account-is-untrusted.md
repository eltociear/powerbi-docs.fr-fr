---
title: "Erreur : "
corporate: 
ssl: 
certificate: 
is: 
untrusted": 
'-': 
power: 
bi": 
description: "Lorsque vous vous connectez à une application Android pour Power BI, vous pouvez voir le message « Authentification impossible car votre certificat SSL d’entreprise n’est pas approuvé"
.": 
services: powerbi
documentationcenter: 
author: maggiesMSFT
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 10/13/2017
ms.author: maggies
ms.openlocfilehash: 4ef29c0cab96e21045f30805d7445aa34d37697a
ms.sourcegitcommit: 99cc3b9cb615c2957dde6ca908a51238f129cebb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2017
---
# <a name="error-corporate-ssl-certificate-is-untrusted---power-bi"></a>Erreur « Votre certificat SSL d’entreprise n’est pas approuvé » - Power BI
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
Si vous utilisez un serveur d’authentification personnalisé, il se peut que le certificat SSL du serveur d’authentification d’entreprise ne soit pas valide. Pour obtenir de l’aide, contactez l’administrateur de votre organisation.

## <a name="next-steps"></a>Étapes suivantes
* [Téléchargez l’application Android](http://go.microsoft.com/fwlink/?LinkID=544867) à partir du magasin d’applications Android.
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

