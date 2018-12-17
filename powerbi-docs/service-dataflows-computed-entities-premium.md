---
title: Utilisation d’entités calculées sur Power BI Premium
description: Découvrez comment utiliser des entités calculées dans Power BI Premium
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 12/06/2018
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: b63b8a601040751cda81e022d571d3a0ed6d501f
ms.sourcegitcommit: f25464d5cae46691130eb7b02c33f42404011357
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53180665"
---
# <a name="using-computed-entities-on-power-bi-premium-preview"></a>Utilisation d’entités calculées sur Power BI Premium (préversion)

Vous pouvez effectuer des **calculs dans le stockage** lors de l’utilisation de **flux de données** avec un abonnement Power BI Premium. Ceci vous permet d’effectuer des calculs sur vos flux de données existants et de retourner des résultats qui vous permettent de vous concentrer sur la création et l’analyse de rapports. 

![Entités calculées dans Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Pour effectuer des **calculs dans le stockage** , vous devez tout d’abord créer le flux de données et amener des données dans le stockage de flux de données Power BI. Une fois que vous avez un flux de données qui contient des données, vous pouvez créer **des entités calculées**, qui effectuent des calculs dans le stockage. 

Il existe deux façons de connecter les données du flux de données à Power BI :

* [Utilisation de la création d’un flux de données en libre-service](service-dataflows-create-use.md)
* Utilisation d’un flux de données externe

Les sections suivantes décrivent comment créer des entités calculées sur vos données de flux de données.

> [!NOTE]
> La fonctionnalité de flux de données étant en préversion, elle est susceptible de changer et d’être mise à jour avant la disponibilité générale.


## <a name="how-to-create-computed-entities"></a>Comment créer des entités calculées 

Une fois que vous avez un flux de données avec une liste d’entités, vous pouvez effectuer des calculs sur ces entités.

Dans l’outil de création de flux de données du service Power BI, sélectionnez **Modifier des entités**, puis cliquez avec le bouton droit sur l’entité que vous souhaitez utiliser comme base pour votre entité calculée et sur laquelle vous souhaitez effectuer des calculs. Dans le menu contextuel, choisissez **Référence**.

Pour que l’entité soit éligible en tant qu’entité calculée, la sélection **Activer le chargement** doit être activée, comme le montre l’illustration suivante. Cliquez avec le bouton droit sur l’entité pour afficher ce menu contextuel.

![Activez Activer le chargement en cliquant avec le bouton droit dans le menu contextuel](media/service-dataflows-computed-entities-premium/computed-entities-premium_01.png)

En sélectionnant **Activer le chargement**, vous créez une entité dont la source est l’entité référencée. L’icône change et l’icône **calculée** s’affiche, comme le montre l’illustration suivante.

![Entités calculées dans Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_00.png)

Toute transformation que vous effectuez sur cette entité créée est exécutée sur les données qui résident déjà dans le stockage de flux de données Power BI. La requête ne sera donc pas exécutée sur la source de données externe d’où les données ont été importées (par exemple, la base de données SQL dont les données ont été extraites), mais plutôt sur les données qui résident dans le stockage de flux de données.

### <a name="example-use-cases"></a>Exemples de cas d’utilisation
Quelles sont les types de transformations pouvant être effectuées avec des entités calculées ? Toutes les transformations normalement définies avec l’interface utilisateur de transformation dans Power BI ou avec l’éditeur M sont prises en charge lors de l’exécution de calculs dans le stockage. 

Prenons l’exemple suivant : vous avez une entité *Compte* qui contient les données brutes de tous les clients de votre abonnement à Dynamics 365. Vous avez également des données brutes *ServiceCalls* du centre de service, avec des données issues des appels de support effectués depuis les différents comptes chaque jour de l’année.

Imaginez que vous souhaitez enrichir l’entité *Compte* avec des données issues de *ServiceCalls*. 

Vous devez tout d’abord agréger les données à partir de ServiceCalls pour calculer le nombre d’appels passés au support pour chaque compte de l’année dernière. 

![Exemple d’entité calculée dans Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_02.png)

Ensuite, vous souhaitez fusionner l’entité *Compte* avec l’entité *ServiceCallsAggregated* pour calculer la table **Compte** enrichie.

![Exemple d’entité calculée dans Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_03.png)

Vous pouvez alors voir les résultats sous forme d *EnrichedAccount* dans l’illustration suivante.

![Résultats d’une entité calculée dans Power BI Premium](media/service-dataflows-computed-entities-premium/computed-entities-premium_04.png)

Et voilà, la transformation est effectuée sur les données dans le flux de données qui réside dans votre abonnement Power BI Premium, pas sur les données source.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Il est important de noter que si vous supprimez l’espace de travail à partir de la capacité Power BI Premium, le flux de données associé n’est plus actualisé. 

Lorsque vous travaillez avec des flux de données spécifiquement créés dans le compte Azure Data Lake Storage Gen2 d’une organisation, les entités liées et les entités calculées ne fonctionnent correctement que lorsque les entités résident dans le même compte de stockage. Pour plus d’informations, consultez [Connecter Azure Data Lake Storage Gen2 pour le stockage de flux de données (préversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md).

En outre, les entités liées ne sont pas disponibles pour les flux de données qui sont créés à partir de dossiers CDM. Consultez [Ajouter un dossier CDM à Power BI en tant que flux de données (préversion)](service-dataflows-add-cdm-folder.md).

## <a name="next-steps"></a>Étapes suivantes

Cet article décrit les entités calculées et les flux de données disponibles dans le service Power BI. Voici quelques articles plus qui peuvent être utiles.

* [Préparation des données en libre-service avec des flux de données](service-dataflows-overview.md)
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation de flux de données avec des sources de données locales (préversion)](service-dataflows-on-premises-gateways.md)
* [Ressources du développeur pour les flux de données Power BI (préversion)](service-dataflows-developer-resources.md)
* [Configurer les paramètres de flux de données d’espace de travail (préversion)](service-dataflows-configure-workspace-storage-settings.md)
* [Ajouter un dossier CDM à Power BI comme en tant que flux de données (préversion)](service-dataflows-add-cdm-folder.md)
* [Connecter Azure Data Lake Storage Gen2 pour le stockage de flux de données (préversion)](service-dataflows-connect-azure-data-lake-storage-gen2.md)

Pour plus d’informations sur Power Query et l’actualisation planifiée, vous pouvez consulter ces articles :
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Configuration d’une actualisation planifiée](refresh-scheduled-refresh.md)

Pour plus d’informations sur le modèle Common Data Model, vous pouvez lire son article de présentation :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)

