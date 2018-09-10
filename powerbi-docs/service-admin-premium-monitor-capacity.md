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
ms.date: 08/29/2018
LocalizationGroup: Premium
ms.openlocfilehash: 8e19bc596bef3862dca79ac92ffbd74954a9c756
ms.sourcegitcommit: 6be2c54f2703f307457360baef32aee16f338067
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43300158"
---
# <a name="monitor-power-bi-premium-capacities-in-your-organization"></a>Surveiller les capacités de Power BI Premium dans votre organisation

Cet article fournit une vue d’ensemble de la surveillance des métriques pour vos capacités de Power BI Premium. Surveillance de l’utilisation de capacité vous permet d’adopter une approche informée de la gestion de vos capacités. 

Vous pouvez surveiller la capacité avec l’application Power BI Premium Capacity Metrics, ou dans le portail d’administration. Nous vous recommandons l’application, car elle fournit des informations plus détaillées, bien que cet article traite les deux options.

## <a name="install-the-premium-capacity-metrics-app"></a>Installer l’application Premium Capacity Metrics

Vous pouvez passer directement à l’[application Premium Capacity Metrics](https://app.powerbi.com/groups/me/getapps/services/capacitymetrics) ou l’installer comme d’autres applications dans Power BI.

> [!IMPORTANT]
> Pour installer et utiliser cette application, vous devez être un administrateur de capacité pour au moins une capacité. Être un administrateur Power BI n’est pas suffisant. 

1. Dans Power BI, cliquez sur **Applications**.

    ![Accédez aux applications](media/service-admin-premium-monitor-capacity/apps.png)

2. Sur le côté droit, cliquez sur **Obtenir des application**.

3. Dans la catégorie **Applications**, recherchez l’**application Power BI Premium Capacity Metrics**.

4. Abonnez-vous pour installer l’application.

Maintenant que vous avez installé l’application, vous pouvez voir des métriques sur les capacités de votre organisation. Jetons un œil à certaines des métriques clés disponibles.

## <a name="use-the-metrics-app"></a>Utilisez l’application de métriques 
Lorsque vous ouvrez l’application, un tableau de bord avec un résumé de toutes les capacités pour lesquelles vous disposez de droits d’administrateur s’affiche tout d’abord.

![Vue d’ensemble du rapport Premium](media/service-admin-premium-monitor-capacity/app-dashboard.png)

### <a name="filtering"></a>Filtrage

L’onglet **Filtres appliqués à toutes les pages** vous permet de sélectionner une capacité, un jeu de données et/ou une plage de dates au cours des sept derniers jours. Ces filtres s’appliquent à la sélection pour toutes les pages et vignettes concernées dans ce rapport. Si rien n’est sélectionné, le rapport par défaut indique les métriques de la semaine écoulée sur chaque capacité que vous possédez.

![Vue d’ensemble du rapport Premium](media/service-admin-premium-monitor-capacity/premium-report-overview.png)

### <a name="summary-tab"></a>Onglet Résumé

L’onglet **Résumé** affiche une vue de la capacité basée sur des entités, sur le système et sur des jeux de données.

![Filtres qui s’appliquent à toutes les pages](media/service-admin-premium-monitor-capacity/premium-summary-report.png)

| **Zone** | **Métriques** |
| --- | --- |
| **Entités** | * Le nombre de capacités que vous possédez<br> * Le nombre distinct de jeux de données dans votre capacité<br> * Le nombre distinct d’espaces de travail dans votre capacité |
| **Système** | * L’utilisation moyenne de la mémoire en Go au cours des sept derniers jours<br> * La consommation de mémoire la plus élevée au cours des sept derniers jours et l’heure locale où elle a eu lieu<br> * Le nombre de fois où l’UC a dépassé 80 % des seuils au cours des sept derniers jours, divisé en compartiments de trois minutes<br> * La plupart des fois où l’UC a dépassé 80 % au cours des sept derniers jours, divisé en compartiments d’une heure, et l’heure locale où cela a eu lieu<br> * Le nombre de fois où les requêtes directes/les connexions actives ont dépassé 80 % des seuils au cours des sept derniers jours, divisé en compartiments de trois minutes<br> * La plupart des fois où les requêtes directes/les connexions actives ont dépassé 80 % au cours des sept derniers jours, divisé en compartiments d’une heure, et l’heure locale où cela a eu lieu |
| **Charges de travail de jeux de données** | * Nombre total d’actualisations au cours des sept derniers jours<br> * Nombre total d’actualisations réussies au cours des sept derniers jours<br> * Nombre total d’actualisations ayant échoué au cours des sept derniers jours<br> * Nombre total d’actualisations ayant échoué en raison d’une mémoire insuffisante<br> * Durée moyenne de l’actualisation en minutes, le temps nécessaire pour terminer l’opération<br> * Le temps d’attente d’actualisation moyen est mesuré en minutes, délai moyen entre l’heure planifiée et le début de l’opération<br> * Nombre total de requêtes exécutées au cours des sept derniers jours<br> * Nombre total de requêtes réussies au cours des sept derniers jours<br> * Nombre total de requêtes ayant échoué au cours des sept derniers jours<br> * Durée moyenne des requêtes en minutes, le temps nécessaire pour terminer l’opération<br> *Nombre total de modèles exclus en raison d’une sollicitation de la mémoire |
|  |  |

### <a name="refreshes-tab"></a>Onglet Actualisations

L’onglet **Actualisations** répertorie la totalité des actualisations, les mesures de réussite, le temps d’attente d’actualisation moyen/maximal et la durée d’actualisation moyenne/maximale en tranches de jeux de données au cours des sept derniers jours. Les deux graphiques du bas montrent une comparaison des actualisations et de la consommation de mémoire en Go, ainsi que les temps d’attente moyens divisés en compartiments d’une heure, signalés à l’heure locale. Les graphiques à barres du haut répertorient les cinq jeux de données principaux par le total de la durée maximale nécessaire pour terminer l’actualisation du jeu de données (durée d’actualisation) et la durée d’attente d’actualisation maximale. Plusieurs pics élevés de temps d’attente d’actualisation indiquent une très forte sollicitation des capacités.

![Rapport d'actualisation Premium](media/service-admin-premium-monitor-capacity/premium-refresh-report.png)

### <a name="datasets-tab"></a>onglet Jeux de données

L’onglet **Jeux de données** affiche les jeux de données complets exclus par heure en raison d’une sollicitation de la mémoire.

![Rapport de jeux de données Premium](media/service-admin-premium-monitor-capacity/premium-datasets-report.png)

### <a name="system-tab"></a>Onglet Système

L’onglet **Système** affiche l’utilisation élevée de l’UC (nombre de fois où l’utilisation a dépassé 80 %), l’utilisation élevée des requêtes directes/des connexions actives et la consommation de mémoire.

![Rapport système Premium](media/service-admin-premium-monitor-capacity/premium-system-report.png)

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
