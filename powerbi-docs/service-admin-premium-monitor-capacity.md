---
title: Superviser les capacités Power BI Premium avec l’application Métriques de capacité Premium.
description: Utiliser le portail d’administration Power BI et l’application Power BI Premium Capacity Metrics
author: minewiskan
ms.author: owend
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 02/05/2019
LocalizationGroup: Premium
ms.openlocfilehash: c4e919de95c86051257ddc38b65c4dfda78dfc03
ms.sourcegitcommit: 54d44deb6e03e518ad6378656c769b06f2a0b6dc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/07/2019
ms.locfileid: "55794610"
---
# <a name="monitor-premium-capacities-with-the-app"></a>Superviser les capacités Premium avec l’application

La supervision de vos capacités est essentielle pour prendre des décisions avisées sur la meilleure utilisation de vos ressources de capacité Premium. Vous pouvez superviser les capacités dans le portail d’administration ou avec l’application **Métriques de capacité Power BI Premium**. Cet article décrit l’utilisation de l’application Métriques de capacité Premium. L’application fournit les informations les plus détaillées sur les performances de vos capacités. Pour une vue d’ensemble générale des métriques de l’utilisation moyenne sur les sept derniers jours, vous pouvez utiliser le portail d’administration. Pour plus d’informations sur la supervision dans le portail, consultez [Superviser les capacités Premium dans le portail d’administration](service-admin-premium-monitor-portal.md).

L’application est mise à jour régulièrement avec de nouvelles fonctionnalités. Vérifiez que vous exécutez la version la plus récente.
**La dernière version de l’application est 1.10.1.1 (au 5 février 2019)**.   
Si vous avez une version antérieure de l’application déjà installée, il est préférable de la supprimer de vos applications, puis d’appuyer sur Ctrl+F5 pour l’actualiser. 

## <a name="install-the-app"></a>Installer l’application

Vous pouvez accéder directement à l’[application Métriques de capacité Premium](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou bien l’installer comme vous le faites pour d’autres applications dans Power BI.


1. Dans Power BI, cliquez sur **Applications**.   
    ![Accéder aux applications](media/service-admin-premium-monitor-capacity/apps.png)

2. Sur le côté droit, cliquez sur **Obtenir des application**.
3. Dans la catégorie **Applications**, recherchez l’**application Power BI Premium Capacity Metrics**.
4. Abonnez-vous pour installer l’application.

Soyez patient. Quelques minutes sont nécessaires pour installer et actualiser les métriques. Si l’application affiche des métriques vides, appuyez sur F5 pour actualiser votre navigateur.


## <a name="get-app-refresh-history"></a>Obtenir l’historique d’actualisation de l’application

Pour vérifier quand votre application Métriques de capacité Premium a été actualisée pour la dernière fois, cliquez sur **Paramètres** > **Jeux de données** > **Métriques de capacité Power BI Premium** > **Historique des actualisations**. 

![Historique des actualisations dans Paramètres](media/settings-refresh-history.png)

La dernière actualisation est indiquée. Vous pouvez aussi cliquer sur **Historique des actualisations** pour voir les actualisations planifiées et à la demande.

![Dernière actualisation](media/service-admin-premium-monitor-capacity/settings-last-refresh.png)

## <a name="monitor-a-capacity-with-the-app"></a>Surveiller une capacité avec l’application

Maintenant que vous avez installé l’application, vous pouvez voir des métriques pour les capacités de votre organisation. Jetons un œil à certaines des métriques clés disponibles.

### <a name="metrics-dashboard"></a>Tableau de bord des métriques

Lorsque vous ouvrez l’application, un tableau de bord avec un résumé de toutes les capacités pour lesquelles vous disposez de droits d’administrateur s’affiche tout d’abord.

![Tableau de bord de l’application de métriques](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Le tableau de bord inclut les métriques suivantes :

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Résumé du système** |  Version de l’application<br>  Nombre de capacités dont vous êtes administrateur<br>  Nombre d’espaces de travail dans vos capacités qui signalent des métriques<br>  Consommation moyenne de la mémoire en Go au cours des sept derniers jours<br>  Consommation maximale de la mémoire en Go au cours des sept derniers jours<br>  Heure locale à laquelle a eu lieu la consommation maximale de la mémoire<br>  Nombre de fois où le processeur a dépassé 80 % des seuils au cours des sept derniers jours, divisés en compartiments de trois minutes<br>  Les heures où le processeur a dépassé 80 % le plus grand nombre de fois au cours des sept derniers jours, divisés en compartiments d’une heure<br>  Heure locale à laquelle le processeur a dépassé 80 % plusieurs fois en une heure |
| **Résumé du jeu de données** |  Nombre total de jeux de données sur tous les espaces de travail dans vos capacités<br>  Nombre de fois où les requêtes directes/les connexions actives ont dépassé 80 % des seuils au cours des sept derniers jours, divisés en compartiments de trois minutes<br>  Les heures où les requêtes directes/les connexions actives ont dépassé 80 % le plus grand nombre de fois au cours des sept derniers jours, divisés en compartiments d’une heure<br>  Heure locale à laquelle les requêtes directes/les connexions actives ont dépassé 80 % plusieurs fois en une heure<br>  Nombre total d’actualisations au cours des sept derniers jours<br>  Temps d’attente d’actualisation moyen : le délai moyen entre l’heure planifiée et le début de l’actualisation, en minutes<br>  Durée moyenne de l’actualisation : le temps nécessaire pour effectuer l’actualisation, en minutes<br>  Nombre total de requêtes exécutées au cours des sept derniers jours<br>  Temps d’attente moyen des requêtes : le temps qu’une requête reste en attente dans les ressources système avant le début de l’exécution, en millisecondes<br>  Durée moyenne des requêtes : le temps nécessaire pour effectuer la requête, en millisecondes<br>  Nombre total de modèles exclus en raison d’une forte sollicitation de la mémoire<br>  Taille moyenne des jeux de données <br>  Nombre moyen de jeux de données chargés en mémoire |
| **Résumé du flux de données** |  Nombre total de flux de données sur tous les espaces de travail dans vos capacités<br>  Nombre total d’actualisations au cours des sept derniers jours<br>  Temps d’attente d’actualisation moyen : le délai moyen entre l’heure planifiée et le début de l’actualisation, en minutes<br>  Durée moyenne de l’actualisation : le temps nécessaire pour effectuer l’actualisation, en minutes |
| **Résumé de rapport paginé** |  Nombre total de rapports paginés sur tous les espaces de travail dans vos capacités<br>  Nombre total de fois que tous les rapports ont été consultés par les utilisateurs<br>  Nombre total de lignes de données dans tous les rapports<br>  Temps total nécessaire pour exécuter toutes les phases (extraction, traitement et rendu des données) de tous les rapports, en millisecondes |
|  |  |

### <a name="metrics-report"></a>Rapport des métriques

Cliquez sur le tableau de bord pour accéder au rapport sous-jacent. En bas du rapport se trouvent cinq onglets :

* [**Jeux de données**](#datasets) : métriques détaillées sur l’intégrité des jeux de données Power BI dans vos capacités.

* [**Rapports paginés**](#paginated-reports) : métriques détaillées sur l’intégrité des rapports paginés dans vos capacités.

* [**Flux de données**](#dataflows) : métriques d’actualisation détaillées pour les flux de données dans vos capacités.

* [**Consommation des ressources**](#resource-consumption) : métriques de capacité globale incluant l’utilisation élevée du processeur et de la mémoire.

* [**ID et informations**](#ids-and-info) : noms, ID et propriétaires des capacités, des espaces de travail et des charges de travail.

Sous chaque onglet, vous pouvez filtrer les métriques par capacité et plage de dates. Si aucun filtre n’est sélectionné, le rapport indique par défaut les métriques de la semaine écoulée pour toutes les capacités qui signalent des métriques. 

#### <a name="datasets"></a>Jeux de données

Utilisez les boutons au-dessus de l’onglet **Jeux de données** pour accéder à différentes zones : **Actualisations**, **Durées des requêtes**, **Attentes des requêtes** et **Jeux de données**.

##### <a name="refreshes-area"></a>Zone Actualisations

La zone **Actualisations** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Fiabilité de l’actualisation** |  Nombre total : actualisations totales pour chaque jeu de données<br>  Fiabilité : pourcentage des actualisations terminées pour chaque jeu de données<br>  Temps d’attente moyen : délai moyen entre l’heure planifiée et le début d’une actualisation du jeu de données, en minutes<br>  Temps d’attente maximal : délai d’attente maximal du jeu de données, en minutes <br>  Durée moyenne : durée moyenne d’actualisation du jeu de données, en minutes<br>  Durée maximale : durée de l’actualisation la plus longue en cours d’exécution pour le jeu de données, en minutes |
| **5 principaux jeux de données par durée d’actualisation moyenne** |  Les cinq jeux de données avec la durée d’actualisation moyenne la plus longue, en minutes |
| **5 principaux jeux de données par temps d’attente moyen** |  Les cinq jeux de données avec le temps d’attente moyen le plus long, en minutes |
| **Temps d’attente moyen d’actualisation par heure** |  Temps d’attente moyen d’actualisation, divisé en intervalles d’une heure et exprimé en heure locale. Plusieurs pics élevés de temps d’attente d’actualisation indiquent une très forte sollicitation des capacités. |
| **Nombre d’actualisations horaires et consommation de mémoire** |  Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

##### <a name="query-durations-area"></a>Zone Durées des requêtes

La zone **Durées des requêtes** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Durées des requêtes** |  Les données de cette section sont segmentées par jeu de données, espace de travail et intervalles d’une heure au cours des sept derniers jours<br>  Total : nombre total de requêtes exécutées pour le jeu de données<br>  Moyenne : durée moyenne des requêtes pour le jeu de données, en millisecondes<br>  Max : durée de la requête en cours d’exécution la plus longue dans le jeu de données, en millisecondes|
| **Distribution des durées de requêtes** |  L’histogramme des durées de requêtes est segmenté par durées des requêtes (en millisecondes) selon les catégories suivantes : intervalles <= 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 s, 1-3 s, 3-10 s, 10-30 s et > 30 s. Des durées de requêtes et des temps d’attente longs indiquent que la capacité est en surchauffe. Cela peut également signifier qu’un seul jeu de données est à l’origine de problèmes et que des recherches plus approfondies sont nécessaires. |
| **5 principaux jeux de données par durée moyenne** |  Les cinq jeux de données avec la durée de requête moyenne la plus longue, en minutes |
| **Requête directe / Connexions actives (> 80 % d’utilisation)** |  Nombre de fois où une requête directe ou une connexion active a dépassé 80 % d’utilisation du processeur, divisé en intervalles d’une heure et exprimé en heure locale |
| **Distributions des durées de requêtes par heure** |  Nombre et durée moyenne (en millisecondes) des requêtes par rapport à la consommation de mémoire en Go, divisé en intervalles d’une heure et exprimé en heure locale |
|  |  |

##### <a name="query-waits-area"></a>Zone Attentes des requêtes

La zone **Attentes des requêtes** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Temps d’attente de la requête** |  Les données de cette section sont segmentées par jeu de données, espace de travail et intervalles d’une heure au cours des sept derniers jours<br>  Total : nombre total de requêtes exécutées pour le jeu de données<br>  Nombre d’attentes : nombre de requêtes dans le jeu de données en attente dans les ressources système avant le début de l’exécution <br>  Moyenne : temps d’attente moyen des requêtes pour le jeu de données, en millisecondes<br>  Max : durée de la requête en attente la plus longue dans le jeu de données, en millisecondes|
| **Distribution des temps d’attente** |  L’histogramme des temps d’attente segmenté par durées des requêtes (en millisecondes) selon les catégories suivantes : intervalles <= 50 ms, 50-100 ms, 100-200 ms, 200-400 ms, 400 ms-1 s, 1-5 s, et > 5 s |
| **5 principaux jeux de données par temps d’attente moyen** |  Les cinq jeux de données avec le temps d’attente moyen le plus long pour lancer l’exécution d’une requête, en millisecondes |
| **Nombres d’attentes et temps d’attente des requêtes par heure** |  Nombre d’attentes et temps d’attente moyen (en millisecondes) des requêtes par rapport à la consommation de mémoire en Go, divisé en intervalles d’une heure et exprimé en heure locale |
|  |  |

##### <a name="datasets-area"></a>Zone Jeux de données

La zone **Jeux de données** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Nombre d’éviction de jeux de données** |  Total : nombre total d’*évictions* de jeux de données pour chaque capacité. Quand une capacité est confrontée à une sollicitation de la mémoire, le nœud supprime un ou plusieurs jeux de données de la mémoire. Les jeux de données qui sont inactifs (ceux pour lesquels aucune opération d’interrogation ou d’actualisation n’est en cours d’exécution) sont supprimés en premier. Ensuite, l’ordre d’éviction est basé sur une mesure dite « dernier récemment utilisé (LRU) ».|
| **Évictions de jeux de données par heure et consommation de mémoire** |  Évictions de jeux de données et consommation de mémoire en Go, divisées en intervalles d’une heure et exprimées en heure locale |
| **Nombre de jeux de données chargés par heure** |  Nombre de jeux de données chargés en mémoire et consommation de mémoire en Go, divisé en intervalles d’une heure et exprimé en heure locale |
| **Pourcentages de mémoire consommée** |  Nombre total de jeux de données actifs en mémoire sous forme de pourcentage de la mémoire totale. Le delta entre Actifs et Tous définit les jeux de données qui peuvent être évincés. Affiché toutes les heures, pour les sept jours précédents. |
| **Tailles de données**  |  Taille maximale : taille maximale du jeu de données, en Mo, pour la période affichée |
|  |  |

#### <a name="paginated-reports"></a>Rapports paginés

L’onglet **Rapports paginés** affiche des métriques détaillées sur l’intégrité des rapports paginés dans vos capacités.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Utilisation globale** |  Nombre total de vues : nombre de fois où le rapport a été consulté par les utilisateurs<br>  Nombre de lignes : nombre de lignes de données dans le rapport<br>  Récupération (moyenne) : délai moyen nécessaire pour récupérer des données pour le rapport, en millisecondes. De longs délais peuvent indiquer des requêtes lentes ou d’autres problèmes au niveau de la source de données. <br>  Traitement (moyenne) : délai moyen nécessaire pour traiter les données d’un rapport, en millisecondes<br> Rendu (moyenne) : délai moyen nécessaire pour afficher un rapport dans le navigateur, en millisecondes<br>  Temps total : temps nécessaire pour exécuter toutes les phases du rapport, en millisecondes|
| **5 principaux rapports par délai moyen d’extraction de données** |  Les cinq rapports avec le délai moyen de récupération des données le plus long, en millisecondes |
| **5 principaux rapports par délai de traitement moyen** |  Les cinq rapports avec le délai moyen de traitement le plus long, en millisecondes |
| **Durées toutes les heures** |  Délai d’extraction des données par rapport au délai de traitement et de rendu, divisé en intervalles d’une heure et exprimé en heure locale |
| **Résultats toutes les heures** |  Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

#### <a name="dataflows"></a>Flux de données

L’onglet **Flux de données** affiche des métriques d’actualisation détaillées pour les flux de données dans vos capacités.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Actualisation** |  Total : actualisations totales pour chaque flux de données<br>  Fiabilité : pourcentage des actualisations effectuées pour chaque flux de données<br>  Temps d’attente moyen : délai moyen entre l’heure planifiée et le début d’une actualisation du flux de données, en minutes<br>  Temps d’attente maximal : délai d’attente maximal du flux de données, en minutes <br>  Durée moyenne : durée moyenne d’actualisation du flux de données, en minutes<br>  Durée maximale : durée de l’actualisation la plus longue en cours d’exécution pour le flux de données, en minutes |
| **5 principaux flux de données par durée d’actualisation moyenne** |  Les cinq flux de données avec la durée d’actualisation moyenne la plus longue, en minutes |
| **5 principaux flux de données par temps d’attente moyen** |  Les cinq flux de données avec le délai d’attente d’actualisation moyen le plus long, en minutes |
| **Temps d’attente moyen d’actualisation par heure** |  Temps d’attente moyen d’actualisation, divisé en intervalles d’une heure et exprimé en heure locale. Plusieurs pics élevés de temps d’attente d’actualisation indiquent une très forte sollicitation des capacités. |
| **Nombre d’actualisations horaires et consommation de mémoire** |  Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

#### <a name="resource-consumption"></a>Consommation des ressources

L’onglet **Consommation des ressources** affiche la consommation du processeur et de la mémoire dans l’ensemble des capacités et charges de travail.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Consommation du processeur** |  Consommation par charge de travail sous forme de pourcentage de la capacité totale de l’UC. Affiché toutes les heures, pour les sept jours précédents. |
| **Consommation de mémoire** |  Consommation de mémoire en Go par charge de travail (lignes pleines) au delà des limites des charges de travail (ligne en pointillés). Affiché toutes les heures, pour les sept jours précédents. |
|  |  |

#### <a name="ids-and-info"></a>ID et informations

L’onglet **ID et informations** contient les noms, ID et propriétaires des capacités, espaces de travail et charges de travail.


## <a name="monitor-power-bi-embedded-capacity"></a>Surveiller la capacité de Power BI Embedded

Vous pouvez également utiliser l’application Métriques de capacité Power BI Premium pour superviser les capacités de la *référence SKU A* dans Power BI Embedded. Ces capacités apparaîtront dans le rapport tant que vous serez un administrateur de la capacité. Toutefois, l’actualisation du rapport échoue si vous n’accordez pas certaines autorisations à Power BI pour vos références SKU A :

1. Ouvrez votre capacité dans le portail Azure.

1. Cliquez sur **Contrôle d’accès (IAM)** et ajoutez l’application « Power BI Premium » au rôle de lecteur. Si vous ne parvenez pas à trouver l’application par son nom, vous pouvez également l’ajouter via son ID client : cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Autorisations pour Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Vous pouvez surveiller l’utilisation de la capacité de Power BI Embedded dans l’application ou dans le portail Azure, mais pas dans le portail d’administration Power BI.


## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Gestion et optimisation des ressources de capacité de Power BI Premium](service-premium-understand-how-it-works.md)
