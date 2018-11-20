---
title: Surveiller les capacités de Power BI Premium dans votre organisation
description: Utiliser le portail d’administration Power BI et l’application Power BI Premium Capacity Metrics
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-admin
ms.topic: conceptual
ms.date: 11/06/2018
LocalizationGroup: Premium
ms.openlocfilehash: bb7527a197c9556509ebba721ee49a2d9817b6f5
ms.sourcegitcommit: b23fdcc0ceff5acd2e4d52b15b310068236cf8c7
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2018
ms.locfileid: "51266205"
---
# <a name="monitor-power-bi-premium-and-power-bi-embedded-capacities"></a>Surveiller les capacités de Power BI Premium et Power BI Embedded

Cet article fournit une vue d’ensemble de la surveillance des métriques pour vos capacités de Power BI Premium. Surveillance de l’utilisation de capacité vous permet d’adopter une approche informée de la gestion de vos capacités.

Vous pouvez surveiller la capacité avec l’application Power BI Premium Capacity Metrics, ou dans le portail d’administration. Nous vous recommandons l’application, car elle fournit des informations plus détaillées, bien que cet article traite les deux options. **La version actuelle de l’application est 1.8 (publiée le 7 novembre 2018).**

<iframe width="560" height="315" src="https://www.youtube.com/embed/UgsjMbhi_Bk?rel=0&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="install-the-premium-capacity-metrics-app"></a>Installer l’application Premium Capacity Metrics

Vous pouvez passer directement à l’[application Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou l’installer comme d’autres applications dans Power BI.

1. Dans Power BI, cliquez sur **Applications**.

    ![Accédez aux applications](media/service-admin-premium-monitor-capacity/apps.png)

1. Sur le côté droit, cliquez sur **Obtenir des application**.

1. Dans la catégorie **Applications**, recherchez l’**application Power BI Premium Capacity Metrics**.

1. Abonnez-vous pour installer l’application.

Maintenant que vous avez installé l’application, vous pouvez voir des métriques sur les capacités de votre organisation. Jetons un œil à certaines des métriques clés disponibles.

## <a name="use-the-metrics-app"></a>Utilisez l’application de métriques

Lorsque vous ouvrez l’application, un tableau de bord avec un résumé de toutes les capacités pour lesquelles vous disposez de droits d’administrateur s’affiche tout d’abord.

![Tableau de bord de l’application de métriques](media/service-admin-premium-monitor-capacity/app-dashboard.png)

Cliquez sur le tableau de bord pour accéder au rapport sous-jacent. Le rapport comporte six onglets, que nous allons décrire en détail dans les sections qui suivent.

* **Filtres** : vous permet de filtrer les autres pages du rapport sur une capacité spécifique.

* **Jeux de données** : métriques détaillées sur l’intégrité des jeux de données Power BI dans vos capacités.

* **Rapports paginés** : métriques détaillées sur l’intégrité des rapports paginés dans vos capacités.

* **Flux de données** : métriques d’actualisation détaillées pour les flux de données dans vos capacités.

* **Système** : métriques de capacité globale incluant l’utilisation élevée du processeur et de la mémoire.

* **Noms d’affichage et ID** : noms, ID et propriétaires des capacités, espaces de travail et charges de travail.

### <a name="filters-tab"></a>Onglet Filtres

L’onglet **Filtres** vous permet de sélectionner une capacité, une plage de dates et d’autres options. Les filtres sont ensuite appliqués à toutes les pages et vignettes concernées dans le rapport. Si aucun filtre n’est sélectionné, par défaut le rapport indique les métriques de la semaine écoulée sur chaque capacité que vous possédez.

![Onglet Filtres](media/service-admin-premium-monitor-capacity/filters-tab.png)

* **(A)**  Sélectionnez **Jeux de données**, **Rapports paginés**, ou **Flux de données** afin de définir des filtres pour chaque charge de travail.

* **(B)**  le nom et **(C)** les informations sont mis à jour en fonction de votre sélection dans **(A)**, ce qui vous permet de filtrer une charge de travail par nom. Par exemple, dans l’image ci-dessus, l’option **Flux de données** est sélectionnée, montrant ainsi les informations **Nom de flux de données** et **Informations de flux de données**.

* **(D)**  Informations sur la capacité, qui indiquent si des jeux de données, des rapports paginés ou des flux de données sont activés pour une capacité.

### <a name="datasets-tab"></a>onglet Jeux de données

Utilisez les boutons en haut de l’onglet **Jeux de données** pour accéder aux différentes zones : **Résumé**, **Actualisations**, **Durées des requêtes**, **Attentes des requêtes** et **Jeux de données**.

![onglet Jeux de données](media/service-admin-premium-monitor-capacity/datasets-tab.png)

#### <a name="summary-area"></a>Zone Résumé

La zone **Résumé** affiche une vue de vos capacités basée sur les entités, les ressources système et les charges de travail de jeux de données. Elle montre les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Entités** | * Le nombre de capacités que vous possédez<br> * Le nombre distinct de jeux de données dans votre capacité<br> * Le nombre distinct d’espaces de travail dans votre capacité |
| **Système** | * L’utilisation moyenne de la mémoire en Go au cours des sept derniers jours<br> * La consommation de mémoire la plus élevée au cours des sept derniers jours et l’heure locale où elle a eu lieu<br> * Le nombre de fois où l’UC a dépassé 80 % des seuils au cours des sept derniers jours, divisé en compartiments de trois minutes<br> * La plupart des fois où l’UC a dépassé 80 % au cours des sept derniers jours, divisé en compartiments d’une heure, et l’heure locale où cela a eu lieu<br> * Le nombre de fois où les requêtes directes/les connexions actives ont dépassé 80 % des seuils au cours des sept derniers jours, divisé en compartiments de trois minutes<br> * La plupart des fois où les requêtes directes/les connexions actives ont dépassé 80 % au cours des sept derniers jours, divisé en compartiments d’une heure, et l’heure locale où cela a eu lieu |
| **Charges de travail de jeux de données** | * Nombre total d’actualisations au cours des sept derniers jours<br> * Nombre total d’actualisations réussies au cours des sept derniers jours<br> * Nombre total d’actualisations ayant échoué au cours des sept derniers jours<br> * Nombre total d’actualisations ayant échoué en raison d’une mémoire insuffisante<br> * La durée moyenne de l’actualisation est le temps nécessaire pour terminer l’opération, en minutes<br> * Le temps d’attente d’actualisation moyen est le délai moyen entre l’heure planifiée et le début de l’opération, en minutes<br> * Nombre total de requêtes exécutées au cours des sept derniers jours<br> * Nombre total de requêtes réussies au cours des sept derniers jours<br> * Nombre total de requêtes ayant échoué au cours des sept derniers jours<br> * La durée moyenne des requêtes est le temps nécessaire pour terminer l’opération, en minutes<br> *Nombre total de modèles exclus en raison d’une sollicitation de la mémoire |
|  |  |

#### <a name="refreshes-area"></a>Zone Actualisations

La zone **Actualisations** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Fiabilité de l’actualisation** | * Nombre total : actualisations totales pour chaque jeu de données<br> * Fiabilité : pourcentage des actualisations terminées pour chaque jeu de données<br> * Temps d’attente moyen : délai moyen entre l’heure planifiée et le début d’une actualiser du jeu de données, en minutes<br> * Temps d’attente maximal : délai d’attente maximal du jeu de données, en minutes <br> * Durée moyenne : durée moyenne d’actualisation du jeu de données, en minutes<br> *Durée maximale : durée de l’actualisation la plus longue en cours d’exécution pour le jeu de données, en minutes |
| **5 principaux jeux de données par durée d’actualisation moyenne** | * Les cinq jeux de données affichant la durée d’actualisation moyenne la plus longue, en minutes |
| **5 principaux jeux de données par temps d’attente moyen** | * Les cinq jeux de données affichant le temps d’attente moyen le plus long, en minutes |
| **Temps d’attente moyen d’actualisation par heure** | * Temps d’attente moyen d’actualisation, divisé en intervalles d’une heure et exprimé en heure locale. Plusieurs pics élevés de temps d’attente d’actualisation indiquent une très forte sollicitation des capacités. |
| **Nombre d’actualisations horaires et consommation de mémoire** | * Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

#### <a name="query-durations-area"></a>Zone Durées des requêtes

La zone **Durées des requêtes** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Durées des requêtes** | * Les données de cette section sont segmentées par jeu de données, espace de travail et intervalles d’une heure au cours des sept derniers jours<br> * Total : nombre total de requêtes exécutées pour le jeu de données<br> * Moyenne : durée moyenne des requêtes pour le jeu de données, en millisecondes<br> * Max : durée de la requête en cours d’exécution la plus longue dans le jeu de données, en millisecondes|
| **Distribution des durées de requêtes** | * L’histogramme des durées de requêtes est regroupé par durées de requêtes (en millisecondes) dans les catégories suivantes : intervalles <= 30 ms, 30-100 ms, 100-300 ms, 300 ms-1 s, 1-3 s, 3-10 s, 10-30 s et >30 s. Des durées de requêtes et des temps d’attente longs indiquent que la capacité est en surchauffe. Cela peut également signifier qu’un seul jeu de données est à l’origine de problèmes et que des recherches plus approfondies sont nécessaires. |
| **5 principaux jeux de données par durée moyenne** | * Les cinq jeux de données affichant la durée de requête moyenne la plus longue, en minutes |
| **Requête directe / Connexions actives (> 80 % d’utilisation)** | * Nombre de fois où une requête directe ou une connexion active a dépassé 80 % d’utilisation du processeur, divisé en intervalles d’une heure et exprimé en heure locale |
| **Distributions des durées de requêtes par heure** | * Nombre et durée moyenne (en millisecondes) des requêtes par rapport à la consommation de mémoire en Go, divisé en intervalles d’une heure et exprimé en heure locale |
|  |  |

#### <a name="query-waits-area"></a>Zone Attentes des requêtes

La zone **Attentes des requêtes** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Temps d’attente de la requête** | * Les données de cette section sont segmentées par jeu de données, espace de travail et intervalles d’une heure au cours des sept derniers jours<br> * Total : nombre total de requêtes exécutées pour le jeu de données<br> * Nombre en attente : nombre de requêtes dans le jeu de données en attendu dans les ressources système avant le début de l’exécution <br> * Moyenne : temps d’attente moyen des requêtes pour le jeu de données, en millisecondes<br> * Max : durée de la requête en attente la plus longue dans le jeu de données, en millisecondes|
| **Distribution des temps d’attente** | * L’histogramme des temps d’attente regroupés par durées de requêtes (en millisecondes) dans les catégories suivantes : intervalles <= 50 ms, 50-100 ms, 100-200 ms, 200-400 ms, 400 ms-1 s, 1-5 s, et >5 s |
| **5 principaux jeux de données par temps d’attente moyen** | * Les cinq jeux de données avec le temps d’attente moyen le plus longue pour lancer l’exécution d’une requête, en millisecondes |
| **Nombres d’attentes et temps d’attente des requêtes par heure** | * Nombre d’attentes et temps d’attente moyen (en millisecondes) des requêtes par rapport à la consommation de mémoire en Go, divisé en intervalles d’une heure et exprimé en heure locale |
|  |  |

#### <a name="datasets-area"></a>Zone Jeux de données

La zone **Jeux de données** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Nombre d’éviction de jeux de données** | * Total : nombre total d’*évictions* de jeux de données pour chaque capacité. Quand une capacité est confrontée à une sollicitation de la mémoire, le nœud supprime un ou plusieurs jeux de données de la mémoire. Les jeux de données qui sont inactifs (ceux pour lesquels aucune opération d’interrogation ou d’actualisation n’est en cours d’exécution) sont supprimés en premier. Ensuite, l’ordre d’éviction est basé sur une mesure dite « dernier récemment utilisé (LRU) ».|
| **Évictions de jeux de données par heure et consommation de mémoire** | * Évictions de jeux de données et consommation de mémoire en Go, divisées en intervalles d’une heure et exprimé en heure locale |
|  |  |

### <a name="paginated-reports-tab"></a>Onglet Rapports paginés

L’onglet **Rapports paginés** affiche des métriques détaillées sur l’intégrité des rapports paginés dans vos capacités.

![Onglet Rapports paginés](media/service-admin-premium-monitor-capacity/paginated-reports-tab.png)

L’onglet **Rapports paginés** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Utilisation globale** | * Vues totales : nombre de fois où le rapport a été consulté par un utilisateur<br> * Nombre de lignes : nombre de lignes de données dans le rapport<br> * Extraction (moy) : délai moyen nécessaire pour récupérer des données pour le rapport, en millisecondes. De longs délais peuvent indiquer des requêtes lentes ou d’autres problèmes au niveau de la source de données. <br> * Traitement (moy) : délai moyen nécessaire pour traiter les données d’un rapport, en millisecondes<br>* Rendu (moy) : délai moyen nécessaire pour afficher un rapport dans le navigateur, en millisecondes<br> * Temps total : temps nécessaire pour exécuter toutes les phases du rapport, en millisecondes|
| **5 principaux rapports par délai moyen d’extraction de données** | * Les cinq rapports affichant le délai moyen d’extraction de données le plus long, en millisecondes |
| **5 principaux rapports par délai de traitement moyen** | * Les cinq rapports affichant le délai moyen de traitement le plus long, en millisecondes |
| **Durées toutes les heures** | * Délai d’extraction de données par rapport au délai de traitement et de rendu, divisé en intervalles d’une heure et exprimé en heure locale |
| **Résultats toutes les heures** | * Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

### <a name="dataflows-tab"></a>Onglet Flux de données

L’onglet **Flux de données** affiche des métriques d’actualisation détaillées pour les flux de données dans vos capacités.

![Onglet Flux de données](media/service-admin-premium-monitor-capacity/dataflows-tab.png)

L’onglet **Flux de données** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Actualisation** | * Total : actualisations totales pour chaque flux de données<br> * Fiabilité : pourcentage des actualisations terminées pour chaque flux de données<br> * Temps d’attente moyen : délai moyen entre l’heure planifiée et le début d’une actualiser du flux de données, en minutes<br> * Temps d’attente maximal : délai d’attente maximal du flux de données, en minutes <br> * Durée moyenne : durée moyenne d’actualisation du flux de données, en minutes<br> *Durée maximale : durée de l’actualisation la plus longue en cours d’exécution pour le flux de données, en minutes |
| **5 principaux flux de données par durée d’actualisation moyenne** | * Les cinq flux de données affichant la durée d’actualisation moyenne la plus longue, en minutes |
| **5 principaux flux de données par temps d’attente moyen** | * Les cinq flux de données affichant le délai d’attente d’actualisation moyen le plus long, en minutes |
| **Temps d’attente moyen d’actualisation par heure** | * Temps d’attente moyen d’actualisation, divisé en intervalles d’une heure et exprimé en heure locale. Plusieurs pics élevés de temps d’attente d’actualisation indiquent une très forte sollicitation des capacités. |
| **Nombre d’actualisations horaires et consommation de mémoire** | * Réussites, échecs et consommation de mémoire, divisés en intervalles d’une heure et exprimés en heure locale |
|  |  |

### <a name="system-tab"></a>Onglet Système

L’onglet **Système** affiche la consommation du processeur et de la mémoire dans l’ensemble des capacités et charges de travail.

![Onglet Système](media/service-admin-premium-monitor-capacity/system-tab.png)

L’onglet **Système** contient les métriques suivantes.

| **Section du rapport** | **Métriques** |
| --- | --- |
| **Métriques du processeur (> 80 % d’utilisation)** | * Le nombre de fois où l’UC a dépassé 80 % des seuils au cours des sept derniers jours, divisé en compartiments de trois minutes |
| **Consommation de mémoire** | * Consommation de mémoire au cours des sept derniers jours, divisée en intervalles de trois minutes |
|  |  |

### <a name="display-names-and-ids-tab"></a>Onglet Noms d’affichage et ID

L’onglet **Noms d’affichage et ID** contient les noms, ID et propriétaires des capacités, espaces de travail et charges de travail.

## <a name="monitor-power-bi-embedded-capacity"></a>Surveiller la capacité de Power BI Embedded

Vous pouvez également utiliser l’application Power BI Premium Capacity Metrics pour surveiller les capacités de la *référence SKU A* dans Power BI Embedded. Ces capacités apparaîtront dans le rapport tant que vous serez un administrateur de la capacité. Toutefois, l’actualisation du rapport échoue si vous n’accordez pas certaines autorisations à Power BI pour vos références SKU A :

1. Ouvrez votre capacité dans le portail Azure.

1. Cliquez sur **Contrôle d’accès (IAM)** et ajoutez l’application « Power BI Premium » au rôle de lecteur. Si vous ne parvenez pas à trouver l’application par son nom, vous pouvez également l’ajouter via son ID client : cb4dc29f-0bf4-402a-8b30-7511498ed654.

    ![Autorisations pour Power BI Embedded](media/service-admin-premium-monitor-capacity/embedded-permissions.png)

> [!NOTE]
> Vous pouvez surveiller l’utilisation de la capacité de Power BI Embedded dans l’application ou dans le portail Azure, mais pas dans le portail d’administration Power BI.

## <a name="basic-monitoring-in-the-admin-portal"></a>Surveillance de base dans le portail d’administration

La zone **Paramètres de capacité** du portail d’administration fournit quatre jauges qui indiquent les charges placées et les ressources utilisées par votre capacité au cours des sept derniers jours. Ces quatre vignettes fonctionnent sur une fenêtre de temps horaire qui indique le nombre d’heures où la métrique correspondante a été supérieure à 80 % au cours des sept derniers jours. Cette métrique indique une dégradation potentielle de l’expérience de l’utilisateur final.

![Utilisation en 7 jours](media/service-admin-premium-monitor-capacity/usage-in-days.png)

| **Métrique** | **Description** |
| --- | --- |
| Processeur |Nombre de fois où l’utilisation du processeur a dépassé 80 %. |
| Écroulement de la mémoire |Représente la sollicitation de la mémoire sur les cœurs du serveur principal. Plus précisément, cette métrique indique le nombre de fois où des jeux de données ont été supprimés de la mémoire en raison de la sollicitation de celle-ci résultant de l’utilisation de nombreux jeux de données. |
| Utilisation de la mémoire |Utilisation moyenne de la mémoire, indiquée en gigaoctets (Go). |
| Requêtes directes/s | Nombre de fois où le nombre de requêtes directes (DirectQuery) et de connexions actives ont dépassé 80 % de la limite. <br> * Nous limitons le nombre total de requêtes DirectQuery et de connexions actives par seconde.* Les limites sont 30/s pour P1, 60/s pour P2 et 120/s pour P3. * En ce qui concerne la limitation ci-dessus, les requêtes DirectQuery et les connexions actives sont comptabilisées ensemble. Par exemple, si vous avez 15 requêtes DirectQuerys et 15 connexions actives par seconde, vous avez atteint votre limite.<br>* Cela s’applique tant aux connexion locales qu’aux connexions cloud. |
|  |  |

Les métriques reflètent l’utilisation sur la dernière semaine.  Si vous souhaitez avoir une vue plus détaillée des métriques, cliquez sur les vignettes de résumé.  Des graphiques détaillés s’affichent pour chacune des métriques de votre capacité Premium. Le graphique suivant affiche les détails de la métrique de l’UC.

![Graphique d’utilisation détaillé - Processeur](media/service-admin-premium-monitor-capacity/premium-usage-detailed-chart-cpu.png)

Ces graphiques récapitulent les données de la dernière semaine par heure. Ils permettent d’isoler plus facilement les événements liés aux performances spécifiques dans votre capacité Premium.

Vous pouvez également exporter les données sous-jacentes de chacune des métriques dans un fichier csv.  Cette exportation fournit des informations détaillées par intervalle de trois minutes pour chaque jour de la dernière semaine.

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez compris comment surveiller les capacités de Power BI Premium, vous pouvez en savoir plus sur l’optimisation des capacités.

> [!div class="nextstepaction"]
> [Gestion et optimisation des ressources de capacité de Power BI Premium](service-premium-understand-how-it-works.md)
