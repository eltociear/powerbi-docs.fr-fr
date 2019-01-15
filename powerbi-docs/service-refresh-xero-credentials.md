---
title: Comment actualiser vos identifiants du pack de contenu Xero
description: Si vous utilisez le pack de contenu Xero Power BI, vous avez peut-être rencontré un problème relatif à l’actualisation quotidienne du pack de contenu en raison d’un incident récent du service Power BI.
author: SarinaJoan
manager: kfile
ms.reviewer: maggiesMSFT
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 08/10/2017
ms.author: sarinas
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 0e49f4b1260e293f0b6e496b06fbe5645c813c8b
ms.sourcegitcommit: c8c126c1b2ab4527a16a4fb8f5208e0f7fa5ff5a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/15/2019
ms.locfileid: "54278129"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Comment actualiser vos identifiants du pack de contenu Xerox si l’actualisation a échoué
Si vous utilisez le pack de contenu Xero Power BI, vous avez peut-être rencontré des problèmes relatifs à l’actualisation quotidienne du pack de contenu en raison d’un incident récent du service Power BI.

Pour voir si votre pack de contenu a été correctement actualisé, vérifiez le dernier état d’actualisation de votre jeu de données Xero, comme illustré dans la capture d’écran ci-dessous.

![](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Si vous voyez que l’actualisation a échoué comme indiqué ci-dessus, suivez ces étapes pour renouveler les informations d’identification de votre pack de contenu.

1. Cliquez sur le bouton de sélection (...) en regard de votre jeu de données Xero, puis sur **Planifier l’actualisation**. Cela ouvre la page de paramètres du pack de contenu Xero.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Dans la page **Paramètres pour Xero**, sélectionnez **Informations d’identification de la source de données** > **Modifier les informations d’identification**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Entrez le nom de votre organisation, puis sélectionnez **Suivant**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Connectez-vous avec votre compte Xero.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Maintenant que vos informations d’identification sont mises à jour, vérifiez que la planification de l’actualisation est définie sur une exécution quotidienne. Pour ce faire, cliquez sur le bouton de sélection (...) en regard de votre jeu de données Xero, puis de nouveau sur **Planifier l’actualisation**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Vous pouvez également choisir d’actualiser le jeu de données immédiatement. Cliquez sur le bouton de sélection (...) en regard de votre jeu de données Xero, puis sur **Actualiser maintenant**.
   
    ![](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Si vous rencontrez encore des problèmes d’actualisation, n’hésitez pas à nous contacter à l’adresse [http://support.powerbi.com](http://support.powerbi.com) 

Pour en savoir plus sur le pack de contenu Xero pour Power BI, consultez la [page d’aide sur le pack de contenu Xero](service-connect-to-xero.md).

### <a name="next-steps"></a>Étapes suivantes
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

