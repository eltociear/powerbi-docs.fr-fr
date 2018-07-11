---
title: Fusionner ou ajouter des sources de données locales et cloud
description: Utilisez la passerelle de données locale pour fusionner ou ajouter des sources de données locales et cloud dans la même requête.
author: mgblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-gateways
ms.topic: conceptual
ms.date: 06/06/2018
ms.author: mblythe
LocalizationGroup: Gateways
ms.openlocfilehash: 2547be7f7bdadb7f991db54230d4fd791941838d
ms.sourcegitcommit: 127df71c357127cca1b3caf5684489b19ff61493
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/03/2018
ms.locfileid: "37600064"
---
# <a name="merge-or-append-on-premises-and-cloud-data-sources"></a>Fusionner ou ajouter des sources de données locales et cloud

La passerelle de données locale permet de fusionner ou d’ajouter des sources de données locales et cloud dans la même requête. C’est utile si vous souhaitez combiner des données provenant de plusieurs sources sans avoir à utiliser des requêtes distinctes.

## <a name="prerequisites"></a>Conditions préalables

- Une [passerelle installée](service-gateway-install.md) sur un ordinateur local.
- Un fichier Power BI Desktop avec des requêtes qui combinent des sources de données locales et cloud.

1. Dans l’angle supérieur droit du service Power BI, sélectionnez l’![icône d’engrenage Paramètres](media/service-gateway-mashup-on-premises-cloud/icon-gear.png) > **Gérer les passerelles**.

    ![Gérer les passerelles](media/service-gateway-mashup-on-premises-cloud/manage-gateways.png)

2. Sélectionnez la passerelle que vous souhaitez configurer.

3. Sous **Paramètres du cluster de passerelle**, sélectionnez **Autorisez les sources de données cloud de l’utilisateur à s’actualiser via ce cluster de passerelle** > **Appliquer**.

    ![Actualisation via ce cluster de passerelle](media/service-gateway-mashup-on-premises-cloud/refresh-gateway-cluster.png)

4. Sous ce cluster de passerelle, ajoutez les [sources de données locales](service-gateway-enterprise-manage-scheduled-refresh.md#add-a-data-source) utilisées dans vos requêtes. Vous n’avez pas besoin d’ajouter des sources de données cloud ici.

5. Chargez sur le service Power BI votre fichier Power BI Desktop avec des requêtes qui combinent des sources de données locales et cloud.

6. Dans la page **Paramètres du jeu de données** du nouveau jeu de données :

   - Pour la source locale, sélectionnez la passerelle associée à cette source de données.

   - Sous **Informations d’identification de la source de données**, modifiez les informations d’identification des sources de données cloud selon vos besoins.

     ![Paramètres du jeu de données](media/service-gateway-mashup-on-premises-cloud/dataset-settings.png)

7. Avec le jeu d’informations d’identification cloud, vous pouvez maintenant actualiser le jeu de données à l’aide de l’option **Actualiser maintenant** ou le planifier pour l’actualiser régulièrement.


## <a name="next-steps"></a>Étapes suivantes

Pour en savoir plus sur l’actualisation des données des passerelles, consultez [Utilisation de la source de données pour une actualisation planifiée](service-gateway-enterprise-manage-scheduled-refresh.md#using-the-data-source-for-scheduled-refresh).