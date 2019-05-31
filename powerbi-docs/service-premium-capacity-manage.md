---
title: Gérer les capacités de Microsoft Power BI Premium
description: Décrit les tâches de gestion des capacités Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/10/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: e4bb907e12d3c0b07408f069d9b238599756e8e0
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565246"
---
# <a name="managing-premium-capacities"></a>La gestion des capacités Premium

La gestion de Power BI Premium implique la création, la gestion et la surveillance des capacités Premium.

## <a name="creating-and-managing-capacities"></a>Création et la gestion des capacités

Le **les paramètres de capacité** page du portail d’administration Power BI affiche le nombre de v-cores achetés et capacités Premium disponibles. La page permet aux administrateurs généraux Office 365 ou les administrateurs de service Power BI pour créer des capacités Premium à partir de v-cores disponibles, ou pour modifier les capacités Premium existantes.

Lorsque vous créez une capacité Premium, les administrateurs doivent définir :

- Nom de capacité (unique au sein du locataire).
- Aux administrateurs de capacité.
- Taille de la capacité.
- Région de résidence des données.

Au moins un administrateur de capacité doit être affecté. Les utilisateurs désignés comme administrateurs de capacité peuvent :

- Affecter des espaces de travail à la capacité.
- Gérer les autorisations utilisateur, pour ajouter des administrateurs de capacité ou des utilisateurs avec des autorisations d’affectation (pour leur permettre d’affecter des espaces de travail à la capacité) supplémentaires.
- Gérer les charges de travail, pour configurer l’utilisation de mémoire maximale pour les charges de travail de flux de données et les rapports paginés.
- Redémarrez la capacité, pour réinitialiser toutes les opérations en raison d’une surcharge du système.

Administrateurs de capacité ne peut pas accéder aux contenu de l’espace de travail, sauf si explicitement affecté dans les autorisations de l’espace de travail. Ils également n’ont pas accès à toutes les zones d’administration Power BI (sauf s’il est explicitement affectée) tels que les métriques d’utilisation, les journaux d’audit ou les paramètres du locataire. Plus important encore, les administrateurs de capacité n’avez pas les autorisations pour créer des nouvelles capacités ou de mettre à l’échelle des capacités actuelles. Administrateurs sont affectées sur une base par capacité, de s’assurer qu’ils peuvent uniquement afficher et gérer les capacités auxquels elles sont affectées.

Taille de la capacité est sélectionné à partir d’une liste des options de la référence (SKU), disponibles qui est limitée par le nombre de v-cores disponibles dans le pool. Il est possible de créer plusieurs capacités du pool, ce qui peut provenir d’une ou plusieurs acheté références (SKU). Par exemple, une référence SKU P3 (32 cœurs) peut servir à créer des capacités de trois : une P2 (16 cœurs) et P1 deux (2 x 8 v-cores). Amélioration des performances et mise à l’échelle est possible en créant de plus petite taille capacités, comme décrit dans la [optimisation des capacités Premium](service-premium-capacity-optimize.md) article. L’illustration suivante montre un exemple de configuration de l’organisation Contoso fictive composée de cinq capacités Premium (3 x P1 et 2 x P3) avec chaque espace de travail d’application conteneur et plusieurs espaces de travail dans une capacité partagée.

![Un exemple de configuration pour l’entreprise fictive Contoso](media/service-premium-capacity-manage/contoso-organization-example.png)

Une capacité Premium peut être affectée à une région autre que la région d’origine du client Power BI, appelé zone géographique multiple. Fonctionnalités multigéographiques fournit un contrôle administratif sur les centres de données dans des régions géographiques définies réside votre contenu Power BI. La logique pour un déploiement de plusieurs zones géographiques est généralement utilisé pour d’entreprise ou de respect des réglementations, plutôt que de performances et mise à l’échelle. Rapport et le chargement du tableau de bord implique tout de même les demandes vers la région d’origine pour les métadonnées. Pour plus d’informations, consultez [prise en charge de plusieurs zones géographiques pour Power BI Premium](service-admin-premium-multi-geo.md).

Les administrateurs de service Power BI et les administrateurs généraux Office 365 peuvent modifier les capacités Premium. Plus précisément, ils peuvent :

- Modifier la taille de la capacité à monter en puissance ou les ressources de mise à l’échelle vers le bas.
- Ajouter ou supprimer des administrateurs de capacité.
- Ajouter ou supprimer des utilisateurs qui ont des autorisations d’affectation.
- Ajouter ou supprimer des charges de travail supplémentaires.
- Modifier les régions.

Autorisations d’affectation sont nécessaires pour affecter un espace de travail à une capacité Premium spécifique. Les autorisations peuvent être accordées à l’ensemble de l’organisation, utilisateurs ou groupes spécifiques.

Par défaut, les capacités Premium prend en charge les charges de travail associées de l’exécution de requêtes de Power BI. Capacités Premium prennent également en charge les charges de travail supplémentaires : **Intelligence artificielle (Services cognitifs)** , **paginés**, et **flux de données**. Chaque charge de travail nécessite la configuration de la mémoire maximale (en pourcentage de mémoire totale disponible) qui peut être utilisée par la charge de travail. Il est important de comprendre qu’augmenter les allocations de mémoire maximale peut avoir un impact sur le nombre de modèles actifs qui peut être hébergé et le débit des actualisations. 

Mémoire est allouée dynamiquement à un flux de données, mais elle est allouée de façon statique pour les rapports paginés. Pour allouer de la mémoire maximale la statiquement parce que les rapports paginés s’exécutent dans un espace de relation contenant-contenu sécurisé de la capacité. Être vigilant lorsque paramètre paginé rapports mémoire car il réduit la mémoire disponible pour le chargement des modèles. Pour plus d’informations, consultez le [les paramètres de mémoire par défaut](service-admin-premium-workloads.md#default-memory-settings).

Suppression d’une capacité Premium est possible et ne sont pas entraîner la suppression de ses espaces de travail et de contenu. Au lieu de cela, il déplace les espaces de travail affectés à une capacité partagée. Lorsque la capacité Premium a été créée dans une autre région, l’espace de travail est déplacé vers une capacité partagée de la région d’origine.

### <a name="assigning-workspaces-to-capacities"></a>Affectation d’espaces de travail à des capacités

Espaces de travail peuvent être assignés à une capacité Premium dans le portail d’administration Power BI ou, pour un espace de travail d’application, dans le **espace de travail** volet.

Administrateurs de capacité, ainsi que les administrateurs généraux Office 365 ou les administrateurs de service Power BI, vous peuvent en bloc affecter des espaces de travail dans le portail d’administration Power BI. En bloc affecté peut s’appliquent à :

- **Espaces de travail par les utilisateurs** -tous les espaces de travail appartenant à ces utilisateurs, y compris les espaces de travail personnels, sont affectées à la capacité Premium. Cela inclura la réaffectation des espaces de travail lorsqu’ils sont déjà attribués à une autre capacité Premium. En outre, les utilisateurs sont affectés également les autorisations d’affectation espace de travail.

- **Espaces de travail spécifiques**
- **Espaces de travail de toute l’organisation** -tous les espaces de travail, y compris les espaces de travail personnels, sont affectées à la capacité Premium. Autorisations de l’attribution d’espace de travail sont affectées à tous les utilisateurs actuels et futurs. Cette approche n’est pas recommandée. Une approche plus ciblée est préférée.

Un espace de travail peut être ajouté à une capacité Premium à l’aide de la **espace de travail** volet fournissant l’utilisateur est à la fois un administrateur de l’espace de travail et dispose des autorisations d’attribution.

![À l’aide du volet de l’espace de travail pour affecter un espace de travail à une capacité Premium](media/service-premium-capacity-manage/assign-workspace-capacity.png)

Administrateurs de l’espace de travail peuvent supprimer un espace de travail à partir d’une capacité (capacité partagée) sans nécessiter d’autorisation de l’affectation. Suppression des espaces de travail à partir des capacités dédiées efficacement déplace l’espace de travail à une capacité partagée. Notez que la suppression d’un espace de travail à partir d’une capacité Premium peut avoir des conséquences négatives résultant, par exemple, dans le contenu partagé indisponible à Power BI gratuit d’une licence aux utilisateurs, ou l’interruption d’une actualisation planifiée lorsqu’ils dépassent les allocations pris en charge capacités de partagé.

Dans le service Power BI, un espace de travail affecté à une capacité Premium est facilement identifié par l’icône en forme de losange qui orne le nom de l’espace de travail.

![Identification d’un espace de travail affecté à une capacité Premium](media/service-premium-capacity-manage/premium-diamond-icon.png)

## <a name="monitoring-capacities"></a>Capacités de surveillance

Surveillance des capacités Premium fournit aux administrateurs le fonctionnement de la façon dont fonctionnent les capacités. Capacités peuvent être surveillées à l’aide du portail d’administration Power BI ou le **métriques de capacité Power BI Premium** application (Power BI).

### <a name="power-bi-admin-portal"></a>Portail d’administration Power BI

Dans le portail d’administration, pour chaque capacité, le **intégrité** onglet fournit des métriques de résumé pour la capacité et de chaque charge de travail est activée. Les métriques indiquent une moyenne au cours des sept derniers jours.  

Au niveau de la capacité, les mesures sont cumulatives de toutes les charges de travail est activées. les métriques suivantes sont fournies :

- **L’utilisation du processeur** -fournit l’utilisation moyenne du processeur en pourcentage d’UC totale disponible pour la capacité.  
- **UTILISATION de la mémoire** -fournit moyenne utilisation de la mémoire (en Go) en tant qu’un total de mémoire disponible pour la capacité. 

Pour chaque charge de travail est activée, l’utilisation du processeur et utilisation de la mémoire sont fournis, ainsi que d’un nombre de mesures spécifiques de la charge de travail. Par exemple, pour la charge de travail de flux de données, **nombre Total de** affiche le nombre total pour chaque flux de données, les actualisations et **durée moyenne** affiche la durée moyenne d’actualisation pour le flux de données.

![La capacité onglet intégrité dans le portail](media/service-premium-capacity-manage/admin-portal-health-dataflows.png)

Pour en savoir plus sur toutes les mesures disponibles pour chaque charge de travail, consultez [surveiller les capacités dans le portail d’administration](service-admin-premium-monitor-portal.md).

Les capacités d’analyse dans le portail d’administration Power BI sont conçues pour fournir un résumé rapide des métriques de capacité de clé. Pour plus d’une surveillance détaillée, il est recommandé d’utiliser le **métriques de capacité Power BI Premium** application.

### <a name="power-bi-premium-capacity-metrics-app"></a>Power BI Premium app de métriques de capacité

Le [métriques de capacité Power BI Premium application](https://appsource.microsoft.com/product/power-bi/pbi_pcmm.pbi-premiumcapacitymonitoring?tab=Overview) est une application Power BI disponibles pour les administrateurs de capacité et est installé comme toute autre application de Power BI. Il contient un tableau de bord et un rapport.

![Power BI Premium app de métriques de capacité](media/service-premium-capacity-manage/capacity-metrics-app.png)

Lorsque l’application s’ouvre, le tableau de bord est chargé pour présenter les nombreuses vignettes exprimant une vue agrégée sur toutes les capacités dont l’utilisateur est un administrateur de capacité. La mise en page du tableau de bord inclut cinq sections principales :

- **Vue d’ensemble** -version de l’application, le nombre de capacités et les espaces de travail
- **Résumé système** -métriques de mémoire et de processeur
- **Résumé du jeu de données** : nombre de jeux de données, DQ/LC, actualisation et les métriques de requête
- **Résumé du flux de données** : nombre de flux de données et les mesures du jeu de données
- **Paginé résumé du rapport** - actualiser et afficher les mesures

Le rapport sous-jacent, à partir de laquelle les vignettes de tableau de bord ont été épinglées, sont accessibles en cliquant sur une vignette de tableau de bord. Il fournit un point de vue plus détaillée de chacune des sections du tableau de bord et prend en charge le filtrage interactif. 

De filtrage est possible en définissant les segments par plage de dates, de capacité, d’espace de travail et de charge de travail (rapport, jeu de données, de flux de données), et en sélectionnant les éléments dans le rapport croisé des visuels filtrer la page de rapport. Filtrage croisé est une technique puissante pour réduire les périodes de temps spécifique, capacités, espaces de travail, jeux de données, etc. et peut être très utile lors de l’analyse de cause racine.

Pour plus d’informations sur les métriques de tableau de bord et rapports dans l’application, consultez [capacités Premium de moniteur avec l’application](service-admin-premium-monitor-capacity.md).

### <a name="interpreting-metrics"></a>L’interprétation de mesures

Mesures doivent être surveillés pour établir une compréhension de base de l’activité des ressources de l’utilisation et la charge de travail. Si la capacité est lente, il est important de comprendre les mesures à surveiller, et les conclusions que vous pouvez apporter.

Dans l’idéal, les requêtes doivent s’exécuter au sein d’une seconde pour offrir des expériences réactives aux utilisateurs des rapports et de permettre un débit plus élevé requête. Il est généralement moindre problème lorsque les processus en arrière-plan, y compris les actualisations - prennent fois plus de temps pour terminer.

En général, les rapports lentes peuvent être une indication d’une capacité de surchauffe. Lors de l’échouent du chargement des rapports, il s’agit d’une indication d’une capacité excédentaire animée. Dans chacune de ces situations, la cause peut être imputable à nombreux facteurs, notamment :

- **Requêtes ayant échoué** certainement indiquer une sollicitation de la mémoire et d’un modèle n’a pas pu être chargé en mémoire. Le service Power BI tente de charger un modèle pendant 30 secondes avant d’échouer.

- **Temps d’attente de requête excessif** peut être dû à plusieurs raisons :
  - La nécessité pour le service Power BI d’abord supprimer ou les modèles et puis charger le modèle à interroger (n’oubliez pas que plus élevées taux d’éviction jeu de données autonomes ne sont pas une indication de la contrainte de capacité, sauf si accompagné par requête temps d’attente qui indiquent l’écroulement de la mémoire).
  - Modèle des temps de chargement (en particulier l’attente pour charger un modèle de grande taille en mémoire).
  - Requêtes à exécution longue.
  - Trop de connexions LC\DQ (dépassement des limites de capacité).
  - Saturation de l’UC.
  - Conceptions de rapport complexe avec un nombre excessif d’éléments visuels sur une page (n’oubliez pas que chaque visuel est une requête).

- **Des requêtes longues durées** peut indiquer que les conceptions de modèle ne sont pas optimisées, en particulier lorsque plusieurs jeux de données est actives dans une capacité, et qu’un seul jeu de données produit longue durée des requêtes. Cela suggère que la capacité est suffisamment petite, et que le jeu de données en question est optimale ou tout simplement lent. Requêtes longues peuvent être problématique car ils peuvent bloquer l’accès aux ressources requises par d’autres processus.
- **Actualiser long temps d’attente** indiquer une mémoire insuffisante en raison des nombreux modèles actives consomment de la mémoire, ou qu’une actualisation de la problématique ne bloque autres actualise (dépassant actualisation parallèle limites).

Une explication plus détaillée de l’utilisation de la métrique est couvert dans le [capacités Premium optimisation](service-premium-capacity-optimize.md) article.

## <a name="acknowledgements"></a>Accusés de réception

Cet article a été écrit par Peter Myers, données plateforme MVP et expert BI indépendant avec [Solutions au niveau du bit](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Optimisation des capacités Premium](service-premium-capacity-optimize.md)   
> [!div class="nextstepaction"]
> [Configurer des charges de travail dans une capacité Premium](service-admin-premium-workloads.md)   

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

||||||
