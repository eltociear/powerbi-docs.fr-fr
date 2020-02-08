---
title: Dimensionnement de la passerelle de données locale
description: Aide au dimensionnement de la passerelle de données locale.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: conceptual
ms.date: 12/30/2019
ms.author: v-pemyer
ms.openlocfilehash: 4f289bf319bf29de8f8765d55bf3400048420af5
ms.sourcegitcommit: 0cc594ebb78a6d0e88784673ed09f8aefd10c7a7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829049"
---
# <a name="on-premises-data-gateway-sizing"></a>Dimensionnement de la passerelle de données locale

Cet article est destiné aux administrateurs Power BI qui souhaitent installer et gérer la [passerelle de données locale](../service-gateway-onprem.md).

La passerelle est requise chaque fois que Power BI doit accéder à des données qui ne sont pas directement accessibles sur Internet. Elle peut être installée sur un serveur local ou sur une infrastructure IaaS (infrastructure as a service) hébergée sur une machine virtuelle.

## <a name="gateway-workloads"></a>Charges de travail de la passerelle

La passerelle de données locale prend en charge deux charges de travail. Il est important de bien les comprendre avant d’aborder le dimensionnement de la passerelle et les recommandations.

### <a name="cached-data-workload"></a>Charge de travail Données en cache

La charge de travail _Données en cache_ récupère et transforme les données sources pour les charger dans des jeux de données Power BI. Ce processus comporte trois étapes :

1. **Connexion** : la passerelle se connecte aux données sources.
1. **Extraction et transformation de données** : les données sont récupérées et, si nécessaire, transformées. Dans la mesure du possible, le Moteur Mashup Power Query transmet les étapes de transformation à la source de données, selon un processus appelé _[Query Folding](power-query-folding.md)_ . Si ce n’est pas possible, les transformations doivent être effectuées par la passerelle. Dans ce cas, elle consomme plus de ressources de processeur et de mémoire.
1. **Transfert** : les données sont transférées au service Power BI. Une connexion Internet fiable et rapide est importante, en particulier pour les gros volumes de données.

![Diagramme illustrant la passerelle de données locale qui se connecte aux sources locales : base de données relationnelle, classeur Excel et fichiers CSV. La passerelle récupère et transforme les données.](media/gateway-onprem-sizing/gateway-onprem-workload-cached-data.png)

### <a name="live-connection-and-directquery-workloads"></a>Charges de travail Connexion active et DirectQuery

La charge de travail _Connexion active et DirectQuery_ fonctionne principalement en mode Intermédiaire (pass-through). Le service Power BI envoie des requêtes, ce à quoi la passerelle répond en donnant les résultats des requêtes. En règle générale, ces derniers sont peu volumineux.

- Pour plus d’informations sur la Connexion active, consultez [Jeux de données dans le service Power BI (modèles hébergés en externe)](../service-datasets-understand.md#external-hosted-models).
- Pour plus d’informations sur DirectQuery, consultez [Modes des jeux de données dans le service Power BI (mode DirectQuery)](../service-dataset-modes-understand.md#directquery-mode).

Cette charge de travail demande des ressources processeur pour le routage des requêtes et des résultats des requêtes. En général, la demande en processeur est bien moins importante que celle de la charge de travail Données du cache, en particulier s’il est nécessaire de transformer les données pour la mise en cache.

Une connectivité fiable, rapide et cohérente est importante pour que les utilisateurs des rapports bénéficient d’une expérience réactive.

![Diagramme illustrant la passerelle de données locale qui se connecte aux sources locales : base de données tabulaire Analysis Services et base de données relationnelle. La passerelle fonctionne principalement en mode Intermédiaire (passe-through).](media/gateway-onprem-sizing/gateway-onprem-workload-liveconnection-directquery.png)

## <a name="sizing-considerations"></a>Considération sur le dimensionnement

Le bon dimensionnement d’un ordinateur de passerelle peut dépendre des variables suivantes :

- Pour les charges de travail Données de cache :
  - nombre d’actualisations simultanées du jeu de données ;
  - type des sources de données (base de données relationnelle, base de données analytique, flux de données ou fichiers) ;
  - volume de données à récupérer à partir de sources de données ;
  - éventuelles transformations que doit effectuer le Moteur Mashup Power Query ;
  - volume de données à transférer au service Power BI.
- Pour les charges de travail Connexion active et DirectQuery :
  - nombre d’utilisateurs de rapports simultanés ;
  - nombre de visuels sur les pages de rapport (chaque visuel envoie au moins une requête) ;
  - fréquence des mises à jour du cache des requêtes du tableau de bord Power BI ;
  - nombre de rapports en temps réel avec la fonctionnalité [Actualisation automatique de la page](../desktop-automatic-page-refresh.md) ;
  - application (ou non) de la [Sécurité au niveau des lignes (SNL)](../desktop-rls.md).

En règle générale, les charges de travail Connexion active et DirectQuery demandent suffisamment de processeur, tandis que les charges de travail Données en cache nécessitent davantage de processeur et de mémoire. Les deux charges de travail dépendent d’une bonne connectivité avec le service Power BI et les sources de données.

> [!NOTE]
> Les capacités de Power BI imposent des limites sur le parallélisme de l’actualisation du modèle, ainsi que sur le débit Connexion active et DirectQuery. Il n’y a pas d’intérêt à dimensionner les passerelles au-delà de ce que prend en charge le service Power BI. Les limites varient selon la référence SKU Premium (et la référence SKU A de taille équivalente). Pour plus d’informations, consultez [Qu’est-ce que Power BI Premium ? (nœuds de capacité)](../service-premium-what-is.md#capacity-nodes).

## <a name="recommendations"></a>Recommandations

Les recommandations de dimensionnement de la passerelle dépendent de nombreuses variables. Dans cette section, nous vous donnons des recommandations générales que vous pouvez prendre en compte.

### <a name="initial-sizing"></a>Dimensionnement initial

Il peut être difficile d’estimer avec précision la taille appropriée. Nous vous recommandons de commencer avec un ordinateur disposant d’au moins 8 cœurs de processeur, 8 Go de RAM et plusieurs cartes réseau Gigabit. Vous pouvez ensuite mesurer une charge de travail de passerelle type en enregistrant les compteurs système de processeur et de mémoire. Pour plus d’informations, consultez [Surveiller et optimiser les performances de la passerelle de données locale](/data-integration/gateway/service-gateway-performance).

### <a name="connectivity"></a>Connectivité

Prévoyez la meilleure connectivité possible entre le service Power BI et votre passerelle, ainsi qu’entre votre passerelle et les sources de données.

- Visez la fiabilité, la rapidité et des latences faibles et cohérentes.
- Éliminez (ou réduisez) les sauts d’ordinateur entre la passerelle et vos sources de données.
- Supprimez toute limitation de bande passante imposée par la couche de proxy de votre pare-feu. Pour plus d’informations sur les points de terminaison Power BI, consultez [URL Power BI pour la liste verte](../power-bi-whitelist-urls.md).
- Configurez [Azure ExpressRoute](/azure/expressroute/expressroute-introduction) pour établir des connexions gérées privées avec Power BI.
- En ce qui concerne les sources de données dans les machines virtuelles Azure, vérifiez que ces machines virtuelles sont [colocalisées avec le service Power BI](../service-admin-where-is-my-tenant-located.md).
- Pour les charges de travail Connexion en direct à SQL Server Analysis Services (SSAS) impliquant une SNL dynamique, assurez une bonne connectivité entre l’ordinateur de passerelle et Active Directory en local.

### <a name="clustering"></a>Clustering

Pour les déploiements à grande échelle, vous pouvez créer une passerelle d’installations de cluster. Les clusters évitent les points de défaillance uniques et peuvent équilibrer la charge du trafic entre les passerelles. Vous pouvez :

- installer une ou plusieurs passerelles dans un cluster ;
- isoler les charges de travail dans des passerelles autonomes ou des clusters de serveurs de passerelle.

Pour plus d’informations, consultez [Gérer l’équilibrage de charge et les clusters à haute disponibilité de la passerelle de données locale](/data-integration/gateway/service-gateway-high-availability-clusters).

### <a name="dataset-design-and-settings"></a>Conception et paramètres du jeu de données

La conception du jeu de données et ses paramètres peuvent avoir un impact sur les charges de travail de la passerelle. Pour réduire cette charge de travail, vous pouvez effectuer les actions suivantes.

Pour les jeux de données d’importation :

- Configurez une actualisation des données moins fréquente.
- Configurez une [actualisation incrémentielle](../service-premium-incremental-refresh.md) pour réduire la quantité de données à transférer.
- Dans la mesure du possible, faites en sorte qu’un [Query Folding](power-query-folding.md) s’applique.
- En particulier pour les gros volumes de données ou les exigences de résultats à faible latence, convertissez la conception en modèle [DirectQuery](../service-dataset-modes-understand.md#composite-mode) ou Composite.

Pour les jeux de données DirectQuery :

- Optimisez la conception des sources de données, des modèles et des rapports. Pour plus d’informations, consultez [Aide du modèle DirectQuery dans Power BI Desktop](directquery-model-guidance.md).
- Créez des [agrégations](../desktop-aggregations.md) pour mettre en cache les résultats de niveau supérieur afin de réduire le nombre de demandes DirectQuery.
- Limitez les intervalles [d’Actualisation automatique de la page](../desktop-automatic-page-refresh.md), dans les conceptions de rapports et les paramètres de capacité.
- En particulier lorsque la SNL est appliquée, restreignez la fréquence de mise à jour du cache du tableau de bord.
- En particulier pour les petits volumes de données ou pour les données non volatiles, convertissez la conception en modèle Importation ou [Composite](../service-dataset-modes-understand.md#composite-mode).

Pour les jeux de données Connexion active :

- En particulier lorsque la SNL est appliquée, restreignez la fréquence de mise à jour du cache du tableau de bord.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Conseils sur le déploiement d’une passerelle de données pour Power BI](../service-gateway-deployment-guidance.md)
- [Configurer les paramètres de proxy de la passerelle de données locale](/data-integration/gateway/service-gateway-proxy)
- [Surveiller et optimiser les performances de la passerelle de données locale](/data-integration/gateway/service-gateway-performance)
- [Résoudre les problèmes liés aux passerelles - Power BI](../service-gateway-onprem-tshoot.md)
- [Résoudre les problèmes de passerelle de données locale](/data-integration/gateway/service-gateway-tshoot)
- [L’importance du Query Folding](power-query-folding.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com)
