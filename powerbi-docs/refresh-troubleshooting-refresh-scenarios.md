---
title: Scénarios de résolution de problèmes liés à l’actualisation
description: Scénarios de résolution de problèmes liés à l’actualisation
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 09/13/2019
ms.author: maggies
LocalizationGroup: Data refresh
ms.openlocfilehash: dcf8f3ca104e4caf749070b45cd47b0ca03f0dbd
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74699587"
---
# <a name="troubleshooting-refresh-scenarios"></a>Scénarios de résolution de problèmes liés à l’actualisation

Vous trouverez ici des informations concernant les différents scénarios auxquels vous pouvez être confronté au moment d’actualiser les données dans le service Power BI.

> [!NOTE]
> Si vous rencontrez un scénario ne figurant pas dans la liste ci-dessous alors qu’il vous pose problème, vous pouvez demander de l’aide sur le [site de la communauté](https://community.powerbi.com/) ou créer un [ticket de support](https://powerbi.microsoft.com/support/).
>
>

## <a name="email-notifications"></a>Notifications par e-mail

Si vous avez accédé à cet article à partir d’une notification par e-mail et si vous ne souhaitez plus recevoir d’e-mails concernant les problèmes d’actualisation, contactez votre administrateur Power BI. Demandez-lui de supprimer votre adresse e-mail ou la liste de messagerie à laquelle vous êtes abonné dans les jeux de données Power BI concernés. Il peut le faire sur le portail d’administration Power BI, dans la zone ci-dessous.

![E-mail de notification des actualisations](media/refresh-troubleshooting-refresh-scenarios/refresh-email.png)

## <a name="refresh-using-web-connector-doesnt-work-properly"></a>L’actualisation à l’aide du connecteur web ne fonctionne pas correctement

Si vous disposez d’un script de connecteur web qui utilise la fonction [**Web.Page**](https://msdn.microsoft.com/library/mt260924.aspx) et que vous avez mis à jour votre jeu de données ou rapport après le 18 novembre 2016, vous devez utiliser une passerelle pour que l’actualisation fonctionne correctement.

## <a name="unsupported-data-source-for-refresh"></a>Actualisation d’une source de données non prise en charge

Lorsque vous configurez un jeu de données, vous pouvez obtenir une erreur indiquant que le jeu de données utilise une source de données non prise en charge pour l’actualisation. Pour plus d’informations, consultez [Résolution des problèmes liés à la non-prise en charge d’une source de données pour l’actualisation](service-admin-troubleshoot-unsupported-data-source-for-refresh.md).

## <a name="dashboard-doesnt-reflect-changes-after-refresh"></a>Les modifications n’apparaissent pas dans le tableau de bord après l’actualisation

Veuillez patienter entre 10 et 15 minutes environ avant que l’actualisation ne soit visible dans les vignettes du tableau de bord. Si les modifications n’apparaissent toujours pas, épinglez à nouveau la visualisation au tableau de bord.

## <a name="gatewaynotreachable-when-setting-credentials"></a>Passerelle inaccessible pendant la définition d’informations d’identification

Vous pouvez obtenir l’erreur `GatewayNotReachable` quand vous essayez de définir les informations d’identification d’une source de données. Elle peut être le résultat d’une passerelle obsolète. Installez la passerelle la plus récente et réessayez.

## <a name="processing-error-the-following-system-error-occurred-type-mismatch"></a>Erreur de traitement : L’erreur système suivante s’est produite : Incompatibilité de type

Il peut s’agir d’un problème lié à votre script M qui se trouve dans votre fichier Power BI Desktop ou un classeur Excel. Cela peut aussi être dû à une version obsolète de Power BI Desktop.

## <a name="tile-refresh-errors"></a>Erreurs d’actualisation des vignettes

Pour obtenir la liste des erreurs que vous pouvez rencontrer avec les vignettes du tableau de bord et des explications, consultez [Résolution des erreurs de vignette](refresh-troubleshooting-tile-errors.md).

## <a name="refresh-fails-when-updating-data-from-sources-that-use-aad-oauth"></a>L’actualisation échoue lors de la mise à jour de données à partir de sources utilisant OAuth AAD

Le jeton OAuth Azure Active Directory (**AAD**) utilisé par de nombreuses sources de données expire après environ une heure. Vous pouvez rencontrer des situations où un chargement de données prend plus de temps que le délai d’expiration du jeton (plus d’une heure), car le service Power BI attend jusqu’à deux heures lors du chargement de données. Dans ce cas, le processus de chargement de données peut échouer avec une erreur d’informations d’identification.

Les sources de données qui utilisent OAuth AAD incluent **Microsoft Dynamics CRM Online** et **SharePoint Online** (SPO). Si vous vous connectez à de telles sources de données et obtenez une erreur d’informations d’identification quand le chargement de données prend plus d’une heure, cela peut en être la cause.

Microsoft étudie une solution qui permette au processus de chargement de données d’actualiser le jeton et de continuer. Toutefois, si votre instance Dynamics CRM Online ou SharePoint Online (ou autre source de données OAuth AAD) est si conséquente qu’elle peut atteindre le seuil de chargement de données de deux heures, vous risquez de rencontrer une expiration de délai d’attente de chargement de données également du côté du service Power BI.

Notez également que, pour que l’actualisation fonctionne correctement, lors de la connexion à une données source **SharePoint Online** à l’aide d’AAD OAuth, vous devez utiliser le compte que vous utilisez pour vous connecter au **service Power BI**.

## <a name="uncompressed-data-limits-for-refresh"></a>Limites des données non compressées pour l’actualisation

La taille maximale des jeux de données importés dans le **service Power BI** est de 1 Go. Ces jeux de données sont fortement compressés pour garantir des performances élevées. De plus, dans une capacité partagée, le service définit une limite de 10 Go de données non compressées traitées pendant l’actualisation. Cette limite compte dans la compression, et représente donc bien plus que 1 Go. Les jeux de données dans Power BI Premium ne sont pas soumis à cette limite. En cas d’échec de l’actualisation dans le service Power BI pour cette raison, réduisez la quantité de données importées dans Power BI et réessayez.

## <a name="scheduled-refresh-timeout"></a>Délai d’actualisation planifié

Actualisation planifiée après deux heures du délai d’expiration des jeux de données importés. Ce délai d’expiration est porté à cinq heures pour les jeux de données dans des espaces de travail **Premium**. Si vous atteignez cette limite, envisagez de réduire la taille ou la complexité de votre jeu de données, ou de diviser le jeu de données en plusieurs parties plus petites.

## <a name="scheduled-refresh-failures"></a>Échecs d’une actualisation planifiée

Si une actualisation planifiée échoue quatre fois en suivant, Power BI désactive l’actualisation. Corrigez le problème sous-jacent, puis réactivez l’actualisation planifiée.

## <a name="access-to-the-resource-is-forbidden"></a>L’accès à la ressource est interdit  

Cette erreur peut se produire en raison de l’expiration des informations d’identification mises en cache. Effacez le cache de votre navigateur Internet en vous connectant à Power BI et en accédant à https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Ceci force une mise à jour de vos informations d’identification.

## <a name="data-refresh-failure-because-of-password-change-or-expired-credentials"></a>Échec de l’actualisation des données en raison du changement du mot de passe ou de l’expiration des informations d’identification

L’actualisation des données peut également échouer en raison de l’expiration des informations d’identification mises en cache. Effacez le cache de votre navigateur Internet en vous connectant à Power BI et en accédant à https://app.powerbi.com?alwaysPromptForContentProviderCreds=true. Ceci force une mise à jour de vos informations d’identification.

## <a name="next-steps"></a>Étapes suivantes

- [Actualisation des données dans Power BI](refresh-data.md)  
- [Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
- [Résolution des problèmes liés à Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)  

D’autres questions ? [Essayez de demander à la communauté Microsoft Power BI](https://community.powerbi.com/)

