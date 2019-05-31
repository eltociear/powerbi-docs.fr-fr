---
title: Scénarios de capacité de Microsoft Power BI Premium
description: Décrit des scénarios courants de capacité Power BI Premium.
author: mgblythe
ms.author: mblythe
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 1d666a6702515a935d93549d026f207848f2bca8
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "65565360"
---
# <a name="premium-capacity-scenarios"></a>Scénarios de capacité Premium

Cet article décrit des scénarios concrets où les capacités de Power BI premium ont été implémentées. Problèmes courants et les défis sont décrits, également comment identifier les problèmes et vous aider à les résoudre :

- [Mise à jour des jeux de données](#keeping-datasets-up-to-date)
- [Identification des jeux de données lente de répondre](#identifying-slow-responding-datasets)
- [Identification des causes pour sporadique ralentir la réponse des jeux de données](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Déterminant s’il existe suffisamment de mémoire](#determining-whether-there-is-enough-memory)
- [Déterminant s’il existe suffisamment d’UC](#determining-whether-there-is-enough-cpu)

Les étapes, ainsi que des exemples de graphique et tableau sont issues les **métriques de capacité Power BI Premium application** qu’un administrateur de Power BI aura accès à.

## <a name="keeping-datasets-up-to-date"></a>Mise à jour des jeux de données

Dans ce scénario, une enquête a été déclenchée lorsque les utilisateurs plaignent du fait que les données du rapport apparaissent parfois ancien ou « obsolètes ».

Dans l’application, l’administrateur interagit avec le **actualise** visuel, le tri des jeux de données par le **le temps d’attente maximal** statistiques dans l’ordre décroissant. Cet élément visuel les aide à révéler des jeux de données ayant les temps d’attente plus longs, regroupées par nom de l’espace de travail.

![Actualisations du jeu de données triées par ordre décroissant du temps d’attente maximal, regroupés par espace de travail](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Dans le **horaire actualiser attendre durées moyennes** visual, il remarque que les temps d’actualisation des pics de manière cohérente environ 16 h 00 chaque jour.

![Actualisation attend pointe régulièrement à 16 h 00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Il existe plusieurs explications possibles pour ces résultats :

- Trop de tentatives d’actualisation ont pu se produire en même temps, dépassant les limites définies par le nœud de capacité. Dans ce cas, il s’agit de six actualisations simultanées sur une P1 avec allocation de mémoire par défaut.

- Jeux de données à actualiser est peut-être trop grand pour tenir en mémoire disponible (ce qui nécessite au moins 2 x la mémoire requise pour l’actualisation complète).
- Logique de Power Query inefficace peut être ce qui entraîne un pic d’utilisation de mémoire pendant l’actualisation du jeu de données. Sur une capacité occupée, ce pic permettre occasionnellement atteindre la limite physique, Échec de l’actualisation et potentiellement affecter d’autres opérations de vue de rapport sur la capacité.
- Jeux de données fréquemment interrogées qui ont besoin pour rester en mémoire peut affecter la capacité d’autres jeux de données à actualiser en raison de la mémoire disponible limitée.

Pour vous aider à étudier, l’administrateur de Power BI peut rechercher :

- Insuffisance de mémoire disponible au moment de données actualisées lors de la mémoire disponible est inférieure à 2 fois la taille du jeu de données à actualiser.
- Jeux de données ne pas actualisé et pas dans la mémoire avant d’actualiser, encore démarré pour afficher le trafic d’interactif pendant les heures d’actualisation lourd. Pour afficher les jeux de données est chargées en mémoire à un moment donné, un administrateur Power BI peut observer la zone de jeux de données de **jeux de données** onglet dans l’application. L’administrateur peut ensuite appliquer un filtre croisé à un moment donné en cliquant sur une des barres dans le **horaire chargé Dataset compte**. Un pic local, illustré dans l’image ci-dessous, indique une heure lorsque plusieurs jeux de données ont été chargées en mémoire, ce qui pourrait retarder le début de l’actualisation planifiée.
- Évictions de jeu de données accrue en tenant placer lors des actualisations de données sont planifiées pour démarrer. Évictions peuvent indiquer il causée pression de mémoire élevée en répondant à des rapports interactifs différents trop avant le délai d’actualisation. Le **horaire Évictions de jeu de données et la consommation de mémoire** visual peut indiquer clairement les pics de suppressions.

L’illustration suivante montre un pic local dans les jeux de données chargées, ce qui suggère des requêtes interactives retardée début des actualisations. Sélection d’une période de temps dans le **chargé Dataset compte toutes les heures** visual traversera filtre le **tailles de jeu de données** visual.

![Un pic local dans les jeux de données chargés suggère interactive démarrage retardé interrogation des actualisations](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

L’administrateur de Power BI peut tenter de résoudre le problème en prenant des mesures pour vous assurer que suffisamment de mémoire est disponible pour les actualisations des données de commencer par :

- Contacter le jeu de données propriétaires et demander à échelonner et espacer les données planifications d’actualisation.
- Réduction du jeu de données charge de requête en supprimant des tableaux de bord inutiles ou tableau de bord les vignettes, en particulier ceux qui appliquent la sécurité de niveau ligne.
- Accélérer les actualisations des données en optimisant la logique de Power Query. Améliorer la modélisation des colonnes calculées ou des tables. Réduire la taille du jeu de données ou configurer des jeux de données volumineux pour effectuer l’actualisation des données incrémentielles.

## <a name="identifying-slow-responding-datasets"></a>Identification des jeux de données lente de répondre

Dans ce scénario, une enquête a commencé lorsque les utilisateurs plaignent du fait que certains rapports a pris trop de temps à ouvrir et parfois se bloquait.

Dans l’application, l’administrateur de Power BI peut utiliser le **durées de requête** visual pour déterminer les jeux de données moins performant en triant les jeux de données par ordre décroissant **durée moyenne**. Cet élément visuel affiche également dataset les nombres de requêtes, afin que vous puissiez voir la fréquence d’interrogation des jeux de données.

![Jeux de données moins performant](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

L’administrateur peut faire référence à la **Distribution de durée de requête** visual, qui montre une distribution globale des performances des requêtes compartimentées (< = 30 ms, 0-100 ms) pour la période filtrées. En règle générale, les requêtes que prennent une seconde ou moins sont considérés comme réactif par la plupart des utilisateurs ; les requêtes qui durent plus longtemps ont tendance à créer une perception de mauvaises performances.

Le **horaire Distribution de durée de requête** visual permet à l’administrateur de Power BI identifier les périodes d’une heure ont été perçue lorsque la capacité de performances faibles. Plus la barre segmente cette requête représentent durées une seconde, plue le risque que les utilisateurs constatent des performances médiocres.

L’élément visuel est interactif, et quand un segment de la barre est sélectionné, le correspondantes **durées de requête** visuel sur la page de rapport de table est le filtrage croisé pour afficher les jeux de données qu’il représente. Ce filtrage croisé permet de l’administrateur de Power BI identifier facilement ce qui répondre lentement des jeux de données.

L’illustration suivante montre un visuel filtré par **horaire Distributions de durée de requête**, focalisation sur les jeux de données moins performant des compartiments d’une heure. 

![Filtré Distributions de durée de requête toutes les heures visual montre la pire effectuant des jeux de données](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Une fois que le jeu de données de performance médiocre dans un intervalle de temps spécifique d’une heure est identifié, l’administrateur de Power BI peut examiner si des performances médiocres sont dû à une capacité surchargée ou en raison de mal conçu le jeu de données ou un rapport. Elles peuvent faire référence à la **temps d’attente de requêtes** visuel et des jeux de données de tri par ordre décroissant du temps d’attente moyenne des requêtes. Si un grand pourcentage des requêtes est en attente, une demande élevée pour le jeu de données est probablement la cause des attentes de requête trop grand nombre. Si le temps d’attente de la requête moyenne est importante (> 100 ms), il peut être nécessaire de revoir le jeu de données et d’un rapport pour voir si les optimisations peuvent être effectuées. Par exemple, moins visuels sur les pages de rapport ou attribué une optimisation de l’expression DAX.

![Le visuel de délais d’attente de requêtes permet de révéler des jeux de données ne fonctionnent pas correctement](media/service-premium-capacity-scenarios/query-wait-times.png)

Il existe plusieurs raisons possibles à l’accumulation de temps d’attente requête dans les jeux de données :

- Une conception de modèle non optimal, les expressions de mesure ou même conception de rapports - toutes les circonstances qui peuvent contribuer à long terme des requêtes qui consomment des niveaux élevés de processeur. Cela force les nouvelles requêtes à attendre jusqu'à ce que les threads d’UC devient disponibles et peuvent de créer un effet de convoi (réflexion embouteillage), plus fréquemment rencontré pendant les heures de pointe. Le **attentes de requête** page se trouve la ressource principale pour déterminer si des jeux de données ont des temps d’attente moyen élevées pour les requêtes.
- Un nombre élevé d’utilisateurs simultanés de capacité (des centaines de milliers) consommant le même rapport ou jeu de données. Jeux de données même bien conçu peut effectuer mal dépasse un seuil d’accès concurrentiel. Cela est généralement indiqué par un seul jeu de données indiquant une valeur nettement plus élevée pour la requête compte que les autres jeux de données apparaissent (par exemple, 300 K interroge pour un jeu de données par rapport à < 30K des requêtes pour toutes les autres jeux de données). À un moment donné les attentes de requête pour ce jeu de données commenceront à échelonner, qui peut être consultée dans le **durées de requête** visual.
- Nombreux disparates des jeux de données interrogées simultanément, à l’origine écroulement comme jeux de données fréquemment cycle en mémoire. Ainsi, les utilisateurs qui rencontrent le ralentissement des performances lorsque le jeu de données est chargé en mémoire. Pour confirmer, l’administrateur de Power BI peut faire référence à la **horaire Évictions de jeu de données et la consommation de mémoire** visual, ce qui peut indiquer qu’un grand nombre de jeux de données est chargé en mémoire sont en cours exclue à plusieurs reprises.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identification des causes pour sporadique ralentir la réponse des jeux de données

Dans ce scénario, une enquête a commencé pour les utilisateurs décrit les visuels de rapport parfois mettaient du temps à répondre ou peut cesser de répondre qu’à d’autres moments, il s’agissait acceptable réactives.

Dans l’application, le **durées de requête** section a été utilisée pour rechercher le jeu de données coupable de la façon suivante :

- Dans le **durées de requête** visual l’administrateur filtré de jeu de données par jeu de données (à partir des principaux jeux de données interrogées) et examiné les barres filtrés croisées dans le **horaire Distributions de requête** visual.
- Quand une barre d’une heure unique a montré des modifications importantes dans le rapport entre tous les groupes de durée de requête et les autres barres d’une heure pour ce jeu de données (par exemple, les rapports entre les couleurs change radicalement), cela signifie que ce jeu de données illustré une modification sporadique dans performances.
- Les barres d’une heure affichant une partie anormale des requêtes peu performantes, indiqué un intervalle de temps dans laquelle ce jeu de données a été affecté par un effet de voisin bruyant, provoqué par les activités d’autres jeux de données.

L’image ci-dessous montre une heure sur le 30 janvier, où vraiment un handicap significatif des performances d’un jeu de données s’est produite, indiquée par la taille de la « (3,10s] « l’exécution du compartiment de durée. Cliquer sur cette barre d’une heure, vous affichez tous les jeux de données chargées en mémoire pendant ce temps, en exposant les jeux de données possible à l’origine de l’effet de voisin bruyant.

![Affichage Pire performance par une grande partie de la barre](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Une fois qu’un intervalle de temps problématique est identifiée (par exemple, durant 30 janvier dans l’image ci-dessus) l’administrateur Power BI peut supprimer tous les filtres de dataset, puis filtrer uniquement par cet intervalle de temps pour déterminer quels jeux de données ont été interrogés activement pendant ce temps. Le jeu de données coupable pour l’effet de voisin bruyant est généralement le jeu de données interrogée supérieur ou celle présentant la durée moyenne des requêtes plus longue.

Une solution à ce problème peut consister à distribuer le coupable de jeux de données sur différents espaces de travail sur différentes capacités Premium, ou sur une capacité partagée si la taille du jeu de données, les exigences de la consommation et actualisation des données modèles est pris en charge.

L’inverse peut être true. L’administrateur de Power BI peut identifient les heures lorsque une performance de requête de jeu de données améliore considérablement et recherchez ce qui a disparu. Si certaines informations sont manquantes sur ce point, qui peut aider pour pointer vers le problème à l’origine.

## <a name="determining-whether-there-is-enough-memory"></a>Déterminant s’il existe suffisamment de mémoire

Pour déterminer s’il existe suffisamment de mémoire pour la capacité de terminer ses charges de travail, l’administrateur de Power BI peut faire référence à la **pourcentages de mémoire consommée** visuel dans le **jeux de données** onglet de l’application. **Tous les** mémoire (totale) représente la mémoire consommée par les jeux de données chargées en mémoire, qu’ils sont activement interrogées ou traitées. **Active** mémoire représente la mémoire consommée par les jeux de données qui est en cours de traitement.

Dans une capacité intègre l’élément visuel doit ressembler à cette, montrant un écart entre tous les (total) et de la mémoire Active :

![Une capacité intègre affiche un écart entre tous les (total) et de la mémoire Active](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Dans une capacité rencontre la sollicitation de la mémoire, le même élément visuel indique clairement mémoire active et la mémoire totale convergentes, ce qui signifie qu’il est impossible de charger les jeux de données supplémentaires dans la mémoire puis. Dans ce cas, l’administrateur de Power BI pouvez cliquer sur **capacité redémarrer** (dans **Options avancées** de la zone de paramètres de capacité du portail d’administration). Redémarrage les résultats de la capacité en cours de tous les jeux de données de la mémoire et de les autoriser à recharger en mémoire en fonction des besoins (par les requêtes ou actualisation des données).

![** Active mémoire converge avec ** mémoire All **](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Déterminant s’il existe suffisamment d’UC

En règle générale, utilisation moyenne du processeur d’une capacité doit rester au-dessous de 80 %. En cas de dépassement signifie la que saturation de l’UC est proche de la capacité.

Effets de la saturation de l’UC sont exprimées par des opérations plus longue que doivent, en raison de la capacité d’effectuer des nombreux changements de contextes d’UC, car il tente de traiter toutes les opérations. Dans une capacité Premium avec un grand nombre de requêtes simultanées, cela est indiqué par les temps d’attente élevées pour les requêtes. Une conséquence élevées pour les requêtes des temps d’attente est le temps de réponse plus lent que d’habitude. L’administrateur de Power BI peut facilement identifier lors de l’UC est saturée en consultant le **horaire Distributions de temps attendre requête** visual. Nombres indiquent la saturation de l’UC potentielle des temps d’attente de pics périodiques de requête.

![Nombres indiquent la saturation de l’UC potentielle des temps d’attente de pics périodiques de requête](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Un modèle similaire peut parfois être détecté dans les opérations d’arrière-plan si elles contribuent à la saturation de l’UC. Un administrateur Power BI peut rechercher une crête périodique dans le temps d’actualisation pour un jeu de données spécifique, ce qui peut indiquer la saturation au moment de l’UC (probablement en raison d’autres actualisations du jeu de données en continu et/ou de requêtes interactives). Dans cette instance, en faisant référence à la **système** vue dans l’application ne révèle pas nécessairement que le processeur est à 100 %. Le **système** vue affiche les moyennes de toutes les heures, mais l’UC peut être saturée pendant plusieurs minutes des opérations lourdes, qui s’affiche en tant que des pics dans le temps d’attente.

Il n’y a plus de nuances de voir l’effet de saturation de l’UC. Tandis que le nombre de requêtes qui attendent est important, les temps d’attente de requête se produira toujours dans une certaine mesure sans provoquer une dégradation des performances notable. Certains jeux de données (avec la plus longue durée des requêtes moyenne, indiquant la taille ou complexité) est plus susceptibles d’engendrer aux effets de la saturation de l’UC que d’autres. Pour identifier facilement ces jeux de données, l’administrateur de Power BI puisse rechercher des modifications dans la composition de la couleur des barres dans le **Distribution des durées d’attente toutes les heures** visual. Après la détection d’une barre de valeurs hors norme, ils peuvent rechercher les jeux de données ayant des attentes de requête pendant cette période et également consulter le temps d’attente moyenne des requêtes par rapport à la moyenne de durée de la requête. Lorsque ces deux mesures sont de la même ampleur et la charge de travail de requête pour le jeu de données est non négligeable, il est probable que le jeu de données est affecté par processeur insuffisantes.

Cet effet peut être particulièrement évident lorsqu’un jeu de données est consommé en rafales courts de haute fréquence des requêtes par plusieurs utilisateurs (par exemple, dans une session de formation), ce qui entraîne une saturation de l’UC pendant chaque intégration. Dans ce cas, vous peuvent rencontrer des temps d’attente de requête significative sur ce jeu de données, ainsi que d’affecter les autres jeux de données de la capacité (effet de voisin bruyant).

Dans certains cas, les administrateurs Power BI peuvent demander que les propriétaires de jeu de données crée un inférieur charge de travail de requêtes volatile en créant un tableau de bord (Actualiser le qui interroge régulièrement avec n’importe quel jeu de données pour les vignettes mises en cache) au lieu d’un rapport. Cela peut aider à éviter des pics lors du chargement du tableau de bord. Cette solution n'est pas toujours possible pour étant donné les besoins de l’entreprise, cependant, elle peut être un moyen efficace pour éviter la saturation de l’UC, sans apporter de modification au jeu de données.

## <a name="acknowledgements"></a>Accusés de réception

Cet article a été écrit par Peter Myers, données plateforme MVP et expert BI indépendant avec [Solutions au niveau du bit](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Surveiller les capacités Premium avec l’application](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Capacités d’analyse dans le portail d’administration](service-admin-premium-monitor-portal.md)   

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

||||||