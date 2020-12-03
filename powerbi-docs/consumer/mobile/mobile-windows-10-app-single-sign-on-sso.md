---
title: Authentification unique dans l’application Power BI Mobile Windows
description: Découvrez l’authentification unique dans l’application Power BI Mobile Windows. Avec l’authentification unique, vous vous connectez une seule fois avec un seul et même compte d’utilisateur pour accéder à toutes les applications et les ressources dont vous avez besoin pour travailler.
author: paulinbar
ms.author: painbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 03/11/2020
ms.openlocfilehash: b316c7b95b28ecb31561b3fbb99eeafa6ffabdb5
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96415263"
---
# <a name="single-sign-on-in-the-power-bi-mobile-windows-app"></a>Authentification unique dans l’application Power BI Mobile Windows

Découvrez l’authentification unique dans l’application Power BI Mobile Windows. Avec l’authentification unique, vous vous connectez une seule fois avec un seul et même compte d’utilisateur pour accéder à toutes les applications et les ressources dont vous avez besoin pour travailler. Une fois que vous êtes connecté, vous pouvez accéder à toutes ces applications sans avoir à vous authentifier de nouveau. 

Parce que l’application Power BI Windows est intégrée à Azure Active Directory, vous pouvez utiliser votre compte professionnel principal pour vous connecter non seulement à vos appareils joints à un domaine, mais aussi au service Power BI. Si vous consultez Power BI sur un téléphone Windows, vérifiez que le compte que vous utilisez pour Power BI est configuré comme compte professionnel ou scolaire dans les paramètres de l’appareil.  

L’authentification unique est activée uniquement pour les appareils Windows gérés par Azure Active Directory.

>[!NOTE]
>La prise en charge des applications mobiles Power BI pour les **téléphones utilisant Windows 10 Mobile** ne sera plus disponible après le 16 mars 2021. [En savoir plus](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="sign-in-with-sso"></a>Connexion avec l’authentification unique

Pour simplifier le processus de connexion, quand vous installez l’application pour la première fois, l’application essaie automatiquement de vous authentifier auprès du service Power BI à l’aide de l’authentification unique. L’application vous demande de fournir vos informations d’identification pour Power BI seulement si ce processus ne fonctionne pas.  

Si vous utilisez déjà l’application mobile Power BI pour Windows, quand vous effectuez une mise à niveau avec la nouvelle version de l’application, vous pouvez aussi utiliser l’authentification unique. Déconnectez-vous de l’application, fermez-la et rouvrez-la. Lorsque l’application se rouvre, elle essaie automatiquement d’utiliser vos informations d’identification Windows actuelles pour vous authentifier auprès du service Power BI. 

Si vous ne souhaitez pas utiliser les informations d’identification de votre session active Windows pour vous connecter à Power BI, accédez simplement aux **Paramètres**, déconnectez-vous et connectez-vous avec d’autres informations d’identification. 
 
## <a name="next-steps"></a>Étapes suivantes

- [Prise en main de l’application mobile Power BI pour Windows 10](mobile-windows-10-phone-app-get-started.md)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
