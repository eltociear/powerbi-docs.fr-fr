---
title: Actualiser un jeu de données créé à partir d’un classeur Excel - local
description: Actualiser un jeu de données créé à partir d’un classeur Excel sur un lecteur local
author: davidiseminger
ms.author: davidi
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: pbi-data-sources
ms.topic: how-to
ms.date: 11/28/2018
LocalizationGroup: Data refresh
ms.openlocfilehash: d2dd08d087b8c4f878d9f74946c77e84dd8ba9e0
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96403947"
---
# <a name="refresh-a-dataset-created-from-an-excel-workbook-on-a-local-drive"></a>Actualiser un jeu de données créé à partir d’un classeur Excel sur un lecteur local
## <a name="whats-supported"></a>Qu’est-ce qui est pris en charge ?
Dans PowerBI, les commandes Actualiser maintenant et Planifier l’actualisation sont prises en charge pour les jeux de données créés à partir de classeurs Excel importés depuis un lecteur local où Power Query (Obtenir et Transformer les données dans Excel 2016) ou Power Pivot est utilisé pour se connecter à l’une des sources de données suivantes et pour charger des données dans le modèle de données Excel :  

### <a name="power-bi-gateway---personal"></a>Power BI Gateway - Personal
* Toutes les sources de données en ligne affichées dans Power Query.
* Toutes les sources de données locales affichées dans Power Query, excepté pour HDFS (Hadoop Distributed File System) et Microsoft Exchange.
* Toutes les sources de données en ligne affichées dans Power Pivot.\*
* Toutes les sources de données locales affichées dans Power Pivot, excepté pour HDFS (Hadoop Distributed File System) et Microsoft Exchange.

<!-- Refresh Data sources-->
[!INCLUDE [refresh-datasources](../includes/refresh-datasources.md)]

> **Remarques :**  
> 
> * Une passerelle doit être installée et en cours d’exécution pour que Power BI puisse se connecter aux sources de données locales et actualiser le jeu de données.
> * Si vous utilisez Excel 2013, veillez à mettre à jour Power Query afin de disposer de la dernière version.
> * L’actualisation n’est pas prise en charge pour les classeurs Excel importés à partir d’un lecteur local sur lequel les données existent uniquement dans des feuilles de calcul ou des tables liées. L’actualisation est prise en charge pour les données de feuille de calcul stockées sur OneDrive et importées à partir de OneDrive. Pour en savoir plus, consultez [Actualiser un jeu de données créé à partir d’un classeur Excel sur OneDrive ou SharePoint Online](refresh-excel-file-onedrive.md).
> * Lorsque vous actualisez un jeu de données créé à partir d’un classeur Excel importé d’un lecteur local, seules les données interrogées à partir des sources de données sont actualisées. Si vous modifiez la structure du modèle de données dans Excel ou Power Pivot, par exemple en créant une mesure ou en modifiant le nom d’une colonne, ces modifications ne sont pas copiées vers le jeu de données. Si vous apportez de telles modifications, vous devez charger ou publier à nouveau le classeur. Si vous prévoyez d’apporter régulièrement des modifications à la structure de votre classeur et souhaitez que celles-ci se reflètent dans le jeu de données dans Power BI sans qu’il soit nécessaire de les charger à nouveau, songez à placer votre classeur sur OneDrive. Power BI actualise automatiquement la structure et les données de la feuille de calcul à partir de classeurs stockés et importés de OneDrive.
> 
> 

## <a name="how-do-i-make-sure-data-is-loaded-to-the-excel-data-model"></a>Comment m’assurer que les données ont été chargées dans le modèle de données Excel ?
Lorsque vous utilisez Power Query (Obtenir et Transformer les données dans Excel 2016) pour vous connecter à une source de données, vous pouvez charger les données dans plusieurs emplacements. Pour vous assurer que vous chargez les données dans le modèle de données, vous devez sélectionner l’option **Ajouter ces données au modèle de données** dans la boîte de dialogue **Charger dans** .

> [!NOTE]
> Les images présentées ici correspondent à Excel 2016.
> 
> 

Dans le **navigateur**, cliquez sur **Charger dans...**  
    ![Capture d’écran de l’option Charger dans, dans le navigateur, montrant la sélection de ladite option.](media/refresh-excel-file-local-drive/refresh_loadtodm_1.png)

Vous pouvez aussi cliquer sur **Modifier** dans le navigateur pour ouvrir l’éditeur de requête. Dans celui-ci, vous pouvez cliquer sur **Fermer et charger dans...**  
    ![Capture d’écran de l’onglet Accueil dans le navigateur, montrant la sélection de l’option Fermer et charger dans.](media/refresh-excel-file-local-drive/refresh_loadtodm_2.png)

Ensuite, dans la fenêtre **Charger dans**, veillez à sélectionner **Ajouter ces données au modèle de données**.  
    ![Capture d’écran de la boîte de dialogue Charger dans, montrant que la case Ajouter ces données au modèle de données est cochée.](media/refresh-excel-file-local-drive/refresh_loadtodm_3.png)

### <a name="what-if-i-use-get-external-data-in-power-pivot"></a>Que se passe-t-il si j’utilise l’option Données externes dans Power Pivot ?
Aucun problème. Lorsque vous utilisez Power Pivot pour vous connecter à des données et les interroger à partir d’une source de données locale ou en ligne, les données sont automatiquement chargées dans le modèle de données.

## <a name="how-do-i-schedule-refresh"></a>Comment planifier l’actualisation ?
Lorsque vous configurez une planification de l’actualisation, Power BI se connecte directement aux sources de données en utilisant les informations de connexion et les informations d’identification du jeu de données pour interroger les données mises à jour, puis charger les données actualisées dans le jeu de données. Les visualisations des rapports et tableaux de bord basés sur ce jeu de données dans le service Power BI sont également mises à jour.

Pour plus d’informations sur la façon de planifier l’actualisation, consultez [Planifier l’actualisation](refresh-scheduled-refresh.md).

## <a name="when-things-go-wrong"></a>Quand des problèmes apparaissent
Quand des problèmes apparaissent, ceux-ci sont souvent dus au fait que Power BI ne parvient pas à se connecter aux sources de données ou, si le jeu de données se connecte à une source de données locale, que la passerelle est hors connexion. Veuillez donc vous assurer que Power BI peut se connecter aux sources de données. Si vous modifiez le mot de passe que vous utilisez pour vous connecter à une source de données ou que Power BI est déconnecté d’une source de données, essayez de vous reconnecter à vos sources de données dans Informations d’identification de la source de données.

Veillez à laisser l’option **M’envoyer une notification d’échec d’actualisation** activée. Vous voudrez en effet probablement être immédiatement informé en cas d’échec d’une actualisation planifiée.

>[!IMPORTANT]
>L’actualisation n’est pas prise en charge pour les flux OData connectés à Power Pivot et interrogés à partir de Power Pivot. En cas d’utilisation d’un flux OData comme source de données, utilisez Power Query.

## <a name="troubleshooting"></a>Résolution des problèmes
Parfois, l’actualisation des données peut ne pas fonctionner comme prévu. Cela est généralement dû à un problème avec une passerelle. Consultez les articles de résolution des problèmes de passerelle qui présentent des outils et les problèmes connus.

[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)

[Résolution des problèmes liés à Power BI Gateway - Personal](service-admin-troubleshooting-power-bi-personal-gateway.md)

## <a name="next-steps"></a>Étapes suivantes
D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
