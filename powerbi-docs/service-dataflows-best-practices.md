---
title: Meilleures pratiques pour les dataflows Power BI
description: Meilleures pratiques pour les dataflows Power BI
author: mohaali
manager: mohaali
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 09/19/2019
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: c499a83b87eb15031d75974084468f418a17804a
ms.sourcegitcommit: 200291eac5769549ba5c47ef3951e2f3d094426e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71142309"
---
# <a name="dataflows-best-practice"></a>Meilleures pratiques pour les dataflows

Cet article fournit les meilleures pratiques en matière de conception de dataflows dans Power BI. Vous pouvez utiliser ce guide pour apprendre à créer des dataflows et appliquer ces pratiques à vos propres dataflows.

> [!NOTE]
> Les recommandations de cet article sont des instructions générales. Pour chaque meilleure pratique de cet article, il peut y avoir des raisons légitimes de dériver de ces instructions. 
> 
> 

### <a name="split-ingestion-and-transformation-to-use-the-enhanced-compute-engine"></a>Fractionner l’ingestion et la transformation pour utiliser le moteur de calcul amélioré

Lors de la création de dataflows, vous pouvez être tenté de créer un dataflow unique avec l’ensemble des entités, transformations, jointures et améliorations en un seul endroit. Pour les jeux de données plus petits, un dataflow unique peut bien fonctionner. Toutefois, lorsque vous traitez des volumes de données plus grands, l’exécution de jointures ou de certaines transformations peut parfois rencontrer des restrictions ou des limites de mémoire. Pour résoudre ces problèmes, un moteur amélioré a été publié pour les utilisateurs Power BI Premium ; il s’étend à des volumes de données bien plus importants. Le moteur de calcul amélioré fonctionne uniquement sur les entités calculées ou liées. Par conséquent, la création séparée d’un dataflow pour l’ingestion et d’un autre lié pour effectuer toutes les fusions et transformations complexes peut bénéficier du moteur amélioré.

Le fractionnement de dataflows est également bénéfique pour le diagnostic et le débogage des problèmes d’actualisation, en particulier lors de l’utilisation de sources qui ont des limites.

### <a name="perform-actions-that-can-use-the-enhanced-compute-engine"></a>Effectuer des actions qui peuvent utiliser le moteur de calcul amélioré

Veillez à bien utiliser le moteur de calcul amélioré en effectuant d’abord les jointures et transformations de filtre dans une entité calculée avant d’effectuer d’autres types de transformations.

### <a name="split-dataflows-when-connecting-to-sharepoint"></a>Fractionner les dataflows lors de la connexion à SharePoint

Lorsque vous travaillez avec SharePoint et que vous vous connectez à plusieurs fichiers, vous pourriez remarquer des échecs occasionnels. SharePoint limite les demandes pour assurer sa fiabilité et sa réactivité. Par conséquent, lors de la connexion à des fichiers Excel à partir de SharePoint, vous pouvez être incité à télécharger tous les fichiers dans un dataflow unique. Si vous téléchargez de nombreux fichiers, plus de 20, créez deux dataflows ou plus pour fractionner la charge d’actualisation et contourner la limitation de SharePoint.

### <a name="avoid-scheduling-refresh-for-linked-entities-inside-the-same-workspace"></a>Éviter la planification de l’actualisation des entités liées dans le même espace de travail

Si vous êtes régulièrement verrouillé hors de vos dataflows qui contiennent des entités liées, cela peut être le résultat d’un dataflow dépendant correspondant dans le même espace de travail qui est verrouillé pendant l’actualisation du dataflow. Ce verrouillage assure la précision transactionnelle et garantit que les dataflows sont actualisés correctement, mais il peut vous empêcher de les modifier. 

Si vous configurez une planification séparée pour le dataflow lié, les dataflows peuvent s’actualiser inutilement et vous empêcher de modifier le dataflow. Il existe deux recommandations pour éviter ce problème : 

* Évitez de définir une planification d’actualisation pour un dataflow lié dans le même espace de travail que le dataflow source
* Si vous souhaitez configurer une planification d’actualisation séparément et que vous souhaitez éviter le comportement de verrouillage, séparez le dataflow dans un espace de travail distinct.

### <a name="create-a-separate-workspace-for-ingestion-transformation"></a>Créer un espace de travail distinct pour l’ingestion et la transformation

Pour fournir un accès aux données de dataflow sous-jacentes à de nombreux utilisateurs sans autoriser l’accès aux données brutes du système source sous-jacent, créez un espace de travail distinct contenant toutes les données que vous devez partager, et attribuez des autorisations. Les autorisations individuelles pour les dataflows ne sont actuellement pas prises en charge.

### <a name="ensure-capacity-is-in-the-same-region"></a>S’assurer que la capacité est dans la même région

Les dataflows ne prennent actuellement pas en charge les régions à plusieurs zones géographiques. La capacité Premium doit se trouver dans la même région que votre locataire Power BI.

### <a name="separate-on-premises-sources-from-cloud-sources"></a>Séparer les sources locales des sources cloud

Outre les meilleures pratiques décrites précédemment, vous pouvez créer un dataflow distinct pour chaque type de source, par exemple local, cloud, SQL Server, Spark, Dynamics, etc. Il est fortement recommandé de fractionner votre dataflow par type de source de données. Une telle séparation par type de source facilite la résolution rapide des problèmes et évite les limites internes lors de l’actualisation de vos dataflows.

### <a name="separate-dataflows-into-a-separate-capacity"></a>Séparer les dataflows dans une capacité distincte

Si vous rencontrez des limites ou si vous observez des défaillances régulières de vos dataflows en raison de limites de mémoire sur votre capacité, envisagez de séparer votre dataflow ou de mettre à l’échelle votre capacité Premium pour obtenir de la mémoire supplémentaire.

## <a name="next-steps"></a>Étapes suivantes

Cet article fournit des informations sur les meilleures pratiques pour les dataflows. Pour plus d’informations sur les flux de données, les articles suivants peuvent être utiles :

* [Préparation des données en libre-service avec des flux de données](service-dataflows-overview.md)
* [Créer et utiliser des flux de données dans Power BI](service-dataflows-create-use.md)
* [Utilisation d’entités calculées sur Power BI Premium](service-dataflows-computed-entities-premium.md)
* [Utilisation de flux de données avec des sources de données locales](service-dataflows-on-premises-gateways.md)

Pour plus d’informations sur le développement CDM et le tutoriel, consultez les rubriques suivantes :
* [Vue d’ensemble du modèle CMD (Common Data Model) ](https://docs.microsoft.com/powerapps/common-data-model/overview)
* [Dossiers CDM](https://go.microsoft.com/fwlink/?linkid=2045304)
* [Définition du fichier modèle CDM](https://go.microsoft.com/fwlink/?linkid=2045521)


Pour plus d’informations sur Power Query et l’actualisation planifiée, vous pouvez consulter ces articles :
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Configuration d’une actualisation planifiée](refresh-scheduled-refresh.md)
