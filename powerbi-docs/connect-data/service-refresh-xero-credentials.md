---
title: Comment actualiser vos identifiants du pack de contenu Xero
description: Si vous utilisez le pack de contenu Xero Power BI, vous avez peut-être rencontré un problème relatif à l’actualisation quotidienne du pack de contenu en raison d’un incident récent du service Power BI.
author: paulinbar
ms.author: painbar
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 08/10/2017
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 972340d4c9cca4507308aaac4c07f410ff8fc6fe
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96392102"
---
# <a name="how-to-refresh-your-xero-content-pack-credentials-if-refresh-failed"></a>Comment actualiser vos identifiants du pack de contenu Xerox si l’actualisation a échoué
Si vous utilisez le pack de contenu Xero Power BI, vous avez peut-être rencontré des problèmes relatifs à l’actualisation quotidienne du pack de contenu en raison d’un incident récent du service Power BI.

Pour voir si votre pack de contenu a été correctement actualisé, vérifiez le dernier état d’actualisation de votre jeu de données Xero, comme illustré dans la capture d’écran ci-dessous.

![Capture d’écran de la boîte de dialogue Xero, montrant l’état d’actualisation de votre jeu de données Xero.](media/service-refresh-xero-credentials/powerbi-xero-refresh-failed.png)

Si vous voyez que l’actualisation a échoué comme indiqué ci-dessus, suivez ces étapes pour renouveler les informations d’identification de votre pack de contenu.

1. Cliquez sur **Autres options** (...) en regard de votre jeu de données Xero, puis cliquez sur **Planifier l’actualisation**. Cela ouvre la page de paramètres du pack de contenu Xero.
   
    ![Capture d’écran de la boîte de dialogue Xero, montrant la sélection de l’option Planifier l’actualisation.](media/service-refresh-xero-credentials/powerbi-xero-schedule-refresh.png)
2. Dans la page **Paramètres pour Xero**, sélectionnez **Informations d’identification de la source de données** > **Modifier les informations d’identification**.
   
    ![Capture d’écran de la boîte de dialogue Paramètres pour Xero, montrant les paramètres pour Xero avec l’option Modifier les informations d’identification sélectionnée.](media/service-refresh-xero-credentials/powerbi-xero-settings-page.png)
3. Entrez le nom de votre organisation, puis sélectionnez **Suivant**.
   
    ![Capture d’écran de la boîte de dialogue Configurer Xero, montrant le nom de l’organisation.](media/service-refresh-xero-credentials/powerbi-xero-configure.png)
4. Connectez-vous avec votre compte Xero.
   
    ![Capture d’écran de la boîte de dialogue de connexion à Xero, montrant comment se connecter à votre compte Xero.](media/service-refresh-xero-credentials/powerbi-xero-welcome.png)
5. Maintenant que vos informations d’identification sont mises à jour, vérifiez que la planification de l’actualisation est définie sur une exécution quotidienne. Pour ce faire, cliquez sur **Autres options** (...) à côté de votre jeu de données Xero, puis recliquez sur **Planifier l’actualisation**.
   
    ![Capture d’écran de la boîte de dialogue Planifier l’actualisation, montrant la fréquence d’actualisation et le fuseau horaire.](media/service-refresh-xero-credentials/powerbi-xero-refresh-schedule.png)
6. Vous pouvez également choisir d’actualiser le jeu de données immédiatement. Cliquez sur **Autres options** (...) à côté de votre jeu de données Xero, puis cliquez sur **Actualiser maintenant**.
   
    ![Capture d’écran de la boîte de dialogue Xero, montrant l’option Actualiser maintenant sélectionnée.](media/service-refresh-xero-credentials/powerbi-xero-refresh-now.png)

Si vous rencontrez encore des problèmes d’actualisation, n’hésitez pas à nous contacter à l’adresse [https://support.powerbi.com](https://support.powerbi.com) 

Pour en savoir plus sur le pack de contenu Xero pour Power BI, consultez la [page d’aide sur le pack de contenu Xero](service-connect-to-xero.md).

### <a name="next-steps"></a>Étapes suivantes
* D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)

