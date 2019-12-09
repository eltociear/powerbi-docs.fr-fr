---
title: Scénarios des capacités Premium de Microsoft Power BI
description: Décrit des scénarios communs des capacités Premium de Power BI.
author: davidiseminger
ms.author: davidi
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-admin
ms.topic: conceptual
ms.date: 04/09/2019
ms.custom: seodec18
LocalizationGroup: Premium
ms.openlocfilehash: 9b3e06172d29f218f9234cf1f3d7e1f623495001
ms.sourcegitcommit: f77b24a8a588605f005c9bb1fdad864955885718
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2019
ms.locfileid: "74697264"
---
# <a name="premium-capacity-scenarios"></a>Scénarios de capacité Premium

Cet article décrit des scénarios réels où des capacités Premium de Power BI ont été implémentées. Des problèmes et des défis courants sont décrits, ainsi que la façon d’identifier les problèmes et de les résoudre :

- [Maintien à jour des jeux de données](#keeping-datasets-up-to-date)
- [Identification des jeux de données avec réponse lente](#identifying-slow-responding-datasets)
- [Identification des causes pour les jeux de données avec réponse sporadiquement lente](#identifying-causes-for-sporadically-slow-responding-datasets)
- [Détermination du fait qu’il y a ou non suffisamment de mémoire](#determining-whether-there-is-enough-memory)
- [Détermination du fait qu’il y a ou non suffisamment de processeur](#determining-whether-there-is-enough-cpu)

Les étapes ainsi que les exemples de graphiques et de tableaux sont tirés de l’**application Métriques de capacité Power BI Premium** à laquelle un administrateur de Power BI aura accès.

## <a name="keeping-datasets-up-to-date"></a>Maintien à jour des jeux de données

Dans ce scénario, une investigation a été lancée quand des utilisateurs ont signalé que les données des rapports étaient parfois anciennes ou « obsolètes ».

Dans l’application, l’administrateur interagit avec le visuel **Actualisations**, en triant les jeux de données d’après la statistique **Temps d’attente maximal** dans l’ordre décroissant. Ce visuel permet de faire apparaître les jeux de données ayant les temps d’attente les plus longs, regroupés par nom d’espace de travail.

![Actualisations des jeux de données triées par ordre décroissant du temps d’attente maximal, regroupées par espace de travail](media/service-premium-capacity-scenarios/dataset-refreshes.png)

Dans le visuel **Temps d’attente moyen d’actualisation par heure**, il remarque que les temps d’attente d’actualisation atteignent tous les jours un pic aux alentours de 16h00.

![Pics d’attente d’actualisation apparaissant périodiquement à 16h00](media/service-premium-capacity-scenarios/peak-refresh-waits.png)

Il existe plusieurs explications possibles pour ces résultats :

- Un trop grand nombre de tentatives d’actualisation peuvent se produire en même temps, ce qui dépasse les limites définies par le nœud de la capacité. Dans le cas présent, six actualisations simultanées sur P1 avec une allocation de mémoire par défaut.

- Les jeux de données à actualiser peuvent être trop grands pour tenir dans la mémoire disponible (nécessitant au moins 2 fois la mémoire nécessaire pour une actualisation complète).
- Une logique Power Query inefficace peut aboutir à un pic d’utilisation de la mémoire lors de l’actualisation des jeux de données. Sur une capacité occupée, ce pic peut parfois atteindre la limite physique, faisant échouer l’actualisation et affectant potentiellement les autres opérations d’affichage de rapports sur la capacité.
- Les jeux de données fréquemment interrogés qui doivent rester en mémoire peuvent affecter la possibilité d’actualiser d’autres jeux de données en raison de la quantité limitée de mémoire disponible.

Pour étudier le problème, l’administrateur Power BI peut rechercher :

- Une mémoire disponible faible au moment de l’actualisation des données, quand cette mémoire disponible est inférieure à 2 fois la taille du jeu de données à actualiser.
- Des jeux de données qui ne sont pas actualisés et qui ne sont pas en mémoire avant l’actualisation, mais commençant néanmoins à montrer un trafic interactif lors des périodes d’actualisation intense. Pour voir quels jeux de données sont chargés en mémoire à un moment donné, un administrateur Power BI peut consulter la zone des jeux de données de l’onglet **Jeux de données** de l’application. L’administrateur peut ensuite effectuer un filtrage croisé pour un moment donné en cliquant sur une des barres de **Nombre de jeux de données chargés par heure**. Une crête locale, montrée dans l’image ci-dessous, indique une heure à laquelle plusieurs jeux de données ont été chargés en mémoire, ce qui a pu retarder le début des actualisations planifiées.
- Augmentation des évictions de jeux de données quand des actualisations de données doivent démarrer. Les évictions peuvent indiquer une forte sollicitation de la mémoire provoquée par le traitement d’un trop grand nombre de rapports interactifs différents avant le moment prévu pour l’actualisation. Le visuel **Évictions de jeux de données par heure et consommation de mémoire** peut indiquer clairement des pics dans les évictions.

L’image suivante montre un pic local dans les jeux de données chargés, ce qui suggère que des requêtes interactives ont retardé le démarrage des actualisations. La sélection d’une période dans le visuel **Nombre de jeux de données chargés par heure** va effectuer un filtrage croisé du visuel **Tailles des jeux de données** .

![Un pic local dans les jeux de données chargés suggère que des requêtes interactives ont retardé le démarrage des actualisations](media/service-premium-capacity-scenarios/hourly-loaded-dataset-counts.png)

L’administrateur Power BI peut tenter de résoudre le problème en prenant des mesures pour garantir que de la mémoire est disponible en suffisance pour que les actualisations de données démarrent :

- En contactant les propriétaires des jeux de données et en leur demandant d’échelonner et d’espacer les planifications d’actualisation des données.
- En réduisant la charge des requêtes sur les jeux de données en supprimant les tableaux de bord ou les vignettes de tableau de bord non nécessaires, en particulier ceux qui appliquent une sécurité au niveau des lignes.
- En accélérant les actualisations des données en optimisant la logique Power Query. Améliorez la modélisation des colonnes ou des tables calculées. Réduisez les tailles des jeux de données ou configurez des jeux de données plus grands pour effectuer une actualisation incrémentielle des données.

## <a name="identifying-slow-responding-datasets"></a>Identification des jeux de données avec réponse lente

Dans ce scénario, une investigation a débuté quand des utilisateurs se sont plaints de ce que certains rapports prenaient trop de temps pour s’ouvrir et que parfois ils se bloquaient.

Dans l’application, l’administrateur Power BI peut utiliser le visuel **Durées des requêtes** pour déterminer les jeux de données les moins performants en les triant par **Durée moyenne** en ordre décroissant. Ce visuel montre également le nombre de requêtes sur les jeux de données, ce qui vous permet de voir la fréquence à laquelle les jeux de données sont interrogés.

![Jeux de données les moins performants](media/service-premium-capacity-scenarios/worst-performing-datasets.png)

L’administrateur peut se référer au visuel **Distribution des durées de requêtes**, qui montre une distribution globale des performances des requêtes par compartiments (<= 30 ms, 0-100 ms) pour la période de temps filtrée. En règle générale, les requêtes qui prennent une seconde ou moins sont considérées comme suffisamment réactives par la plupart des utilisateurs ; les requêtes qui prennent plus de temps tendent à engendre la perception de mauvaises performances.

Le visuel **Distribution des durées de requêtes par heure** permet à l’administrateur Power BI d’identifier des périodes d’une heure où les performances de la capacité peuvent avoir été perçues comme médiocres. Plus les segments de la barre qui représentent les durées des requêtes sont grands, plus le risque d’une perception de performances médiocres par les utilisateurs est élevé.

Le visuel est interactif et, quand un segment de la barre est sélectionné, le visuel de table **Durées des requêtes** correspondant sur la page du rapport est filtré de façon croisée pour montrer les jeux de données qu’il représente. Ce filtrage croisé permet à l’administrateur Power BI d’identifier facilement les jeux de données qui répondent avec lenteur.

L’image suivante montre un visuel filtré par **Distributions des durées de requêtes par heure**, mettant l’accent sur les jeux de données les moins performants dans les compartiments d’une heure. 

![Le visuel Distributions des durées de requêtes par heure filtré montre les jeux de données les moins performants](media/service-premium-capacity-scenarios/hourly-query-duration-distributions.png)

Une fois que le jeu de données avec des performances médiocres dans un intervalle spécifique d’une heure est identifié, l’administrateur Power BI peut déterminer si les performances médiocres sont provoquées par une capacité surchargée, ou sont dues à un jeu de données ou un rapport mal conçu. Il peut se référer au visuel **Temps d’attente des requêtes** et trier les jeux de données par temps d’attente moyen des requêtes en ordre décroissant. Si un grand pourcentage des requêtes doivent attendre, une demande élevée pour le jeu de données est probablement la cause d’un trop grand nombre d’attentes pour les requêtes. Si le temps d’attente moyen des requêtes est important (> 100 ms), il peut être utile de passer en revue le jeu de données et le rapport pour déterminer si des optimisations peuvent être effectuées. Par exemple, moins de visuels sur les pages d’un rapport donné ou une optimisation des expressions DAX.

![Le visuel Temps d’attente des requêtes permet de faire apparaître les jeux de données peu performants](media/service-premium-capacity-scenarios/query-wait-times.png)

Plusieurs raisons peuvent expliquer l’accumulation des temps d’attente des requêtes dans les jeux de données :

- Une conception du modèle non optimale, des expressions de mesures ou même la conception du rapport - toutes circonstances qui peuvent contribuer à l’existence de requêtes dont l’exécution est longue et qui consomment des niveaux de processeur élevés. Ceci oblige les nouvelles requêtes à attendre que les threads du processeur deviennent disponibles et peut créer un effet de convoi (pensez à des embouteillages), généralement observé pendant les heures des pics d’activité. La page **Temps moyen d’attente des requêtes** est la ressource principale pour déterminer si des jeux de données ont des temps d’attente moyens élevés pour les requêtes.
- Un grand nombre d’utilisateurs simultanés de la capacité (de plusieurs centaines à plusieurs milliers) qui consomment le même rapport ou le même jeu de données. Même les jeux de données bien conçus peuvent avoir des performances médiocres au-delà d’un certain seuil d’accès simultanés. Ceci est généralement indiqué par le fait qu’un jeu de données montre un nombre de requêtes beaucoup plus élevé que les autres jeux de données (par exemple 300 000 requêtes pour un jeu de données, en comparaison de moins de 30 000 requêtes pour tous les autres jeux de données). À un moment donné, les temps d’attente des requêtes pour ce jeu de données vont commencer à s’allonger, ce qui peut se voir dans le visuel **Durées des requêtes**.
- De nombreux jeux de données ont été interrogés simultanément, ce qui provoque des encombrements dès lors que les jeux de données sont placés et supprimés de la mémoire de façon cyclique. Ainsi, les utilisateurs subissent un ralentissement des performances au moment où le jeu de données est chargé en mémoire. Pour vérifier cette hypothèse, l’administrateur Power BI peut se référer au visuel **Évictions de jeux de données par heure et consommation de mémoire**, qui peut indiquer qu’un grand nombre de jeux de données chargés en mémoire en sont supprimés de façon répétée.

## <a name="identifying-causes-for-sporadically-slow-responding-datasets"></a>Identification des causes pour les jeux de données avec réponse sporadiquement lente

Dans ce scénario, une investigation a commencé quand des utilisateurs ont indiqué que les visuels des rapports étaient parfois lents à répondre ou pouvaient cesser de répondre, mais qu’à d’autres moments, leur réactivité était acceptable.

Dans l’application, la section **Durées des requêtes** a été utilisée pour rechercher le jeu de données coupable de la façon suivante :

- Dans le visuel **Durées des requêtes**, l’administrateur a filtré jeu de données par jeu de données (en commençant par les jeux de données les plus interrogés) et a examiné les barres avec filtrage croisé dans le visuel **Distributions des durées de requêtes par heure**.
- Quand une barre correspondant à une heure montrait des changements significatifs dans le rapport entre tous les groupes des durées des requêtes et les autres barres d’une heure pour ce jeu de données (par exemple les rapports entre les couleurs changent radicalement), cela signifie que ce jeu de données a montré un changement sporadique des performances.
- Les barres d’une heure montrant une proportion irrégulière de requêtes à performances médiocres ont indiqué une période où ce jeu de données a été affecté par un effet de voisinage perturbateur, provoqué par les activités d’autres jeux de données.

L’image ci-dessous montre une certaine heure le 30 janvier, où un ralentissement significatif dans les performances d’un jeu de données s’est produit, indiqué par la taille du compartiment de la durée d’exécution « (3,10s] ». Le fait de cliquer sur cette barre d’une heure fait apparaître tous les jeux de données chargés en mémoire pendant cette période, révélant les jeux de données ayant potentiellement provoqué l’effet de voisinage perturbateur.

![Barre montrant les pires performances en grande proportion](media/service-premium-capacity-scenarios/worst-performing-queries.png)

Une fois qu’un intervalle de temps problématique est identifié (par exemple au cours du 30 janvier dans l’image ci-dessus), l’administrateur Power BI peut supprimer tous les filtres de jeux de données, puis filtrer seulement selon cette période de temps pour déterminer les jeux de données interrogés activement pendant cette période. Le jeu de données coupable de l’effet de voisinage perturbateur est généralement le jeu de données le plus interrogé ou celui ayant la durée moyenne des requêtes la plus longue.

Une solution à ce problème peut être de distribuer les jeux de données coupables sur différents espaces de travail sur des capacités Premium différentes, ou sur une capacité partagée si la taille du jeu de données, les exigences de consommation et les modèles d’actualisation des données y sont pris en charge.

L’inverse peut également être vrai. L’administrateur Power BI a pu identifier les moments où les performances des requêtes sur un jeu de données s’améliorent considérablement, puis rechercher ce qui a disparu. Si certaines informations sont manquantes à ce stade, cela peut aider à pointer vers le problème qui en est responsable.

## <a name="determining-whether-there-is-enough-memory"></a>Détermination du fait qu’il y a ou non suffisamment de mémoire

Pour déterminer s’il y a suffisamment de mémoire pour que la capacité traite ses charges de travail, l’administrateur Power BI peut se référer au visuel **Pourcentages de mémoire consommée** sous l’onglet **Jeux de données** de l’application. La mémoire totale (**Toute**) représente la mémoire consommée par les jeux de données chargés en mémoire, qu’ils soient activement interrogés ou traités. La mémoire **Active** représente la mémoire consommée par les jeux de données qui sont activement traités.

Dans une capacité saine, le visuel se présente comme ceci, montrant un écart entre la mémoire totale (Toute) et la mémoire Active :

![Une capacité saine montre un écart entre la mémoire totale (Toute) et la mémoire Active](media/service-premium-capacity-scenarios/memory-healthy-capacity.png)

Dans une capacité soumise à une forte sollicitation de la mémoire, le même visuel montre clairement que la mémoire active et la mémoire totale convergent, ce qui signifie qu’il est alors impossible de charger des jeux de données supplémentaires dans la mémoire. Dans ce cas, l’administrateur Power BI peut cliquer sur **Redémarrage de la capacité** (dans **Options avancées** de la zone des paramètres de capacité du portail d’administration). Le redémarrage de la capacité entraîne le vidage de tous les jeux de données de la mémoire et leur permet d’y être rechargées en fonction des besoins (des requêtes ou de l’actualisation des données).

![Mémoire **Active** convergeant avec la mémoire totale (**Toute**)](media/service-premium-capacity-scenarios/memory-unhealthy-capacity.png)

## <a name="determining-whether-there-is-enough-cpu"></a>Détermination du fait qu’il y a ou non suffisamment de processeur

En général, l’utilisation moyenne du processeur d’une capacité doit rester en dessous de 80 %. Le dépassement de cette valeur signifie que la capacité approche de la saturation du processeur.

Les effets de la saturation du processeur sont montrés par des opérations qui prennent plus de temps qu’elles ne le devraient, en raison du fait que la capacité exécute un grand nombre de changements de contexte du processeur quand il tente de traiter toutes les opérations. Dans une capacité Premium avec un nombre élevé de requêtes simultanées, ceci est indiqué par des temps d’attente élevés des requêtes. Une conséquence des temps d’attente élevés des requêtes est une réactivité plus lente que d’habitude. L’administrateur Power BI peut facilement identifier quand le processeur est saturé en regardant le visuel **Distributions horaires des temps d’attente des requêtes**. Les pics périodiques des temps d’attente des requêtes indiquent une possible saturation du processeur.

![Les pics périodiques d’attente de requêtes indiquent une possible saturation du processeur.](media/service-premium-capacity-scenarios/peak-query-wait-times.png)

Un modèle similaire peut parfois être détecté dans des opérations en arrière-plan si elles contribuent à la saturation du processeur. Un administrateur Power BI peut rechercher un pic périodique dans les temps d’actualisation pour un jeu de données spécifique, qui peut indiquer la saturation du processeur à ce moment-là (probablement en raison d’autres actualisations de jeu de données en cours et/ou de requêtes interactives). Dans ce cas, se référer à la vue **Système** dans l’application ne révèle pas nécessairement que le processeur est occupé à 100 %. La vue **Système** affiche des moyennes horaires, mais le processeur peut devenir saturé pendant plusieurs minutes à l’occasion d’opérations intensives, qui apparaissent sous forme de pics dans les temps d’attente.

Il y a plus de nuances pour visualiser l’effet de la saturation du processeur. Alors que le nombre de requêtes qui attendent est important, le temps d’attente des requêtes existera toujours dans une certaine mesure, sans entraîner une dégradation perceptible des performances. Certains jeux de données (avec une durée moyenne des requêtes plus longue, indiquant leur complexité ou leur taille) sont plus sujets que d’autres aux effets de la saturation du processeur. Pour identifier facilement ces jeux de données, l’administrateur Power BI peut rechercher des modifications dans la composition des couleurs des barres du visuel **Distributions horaires des temps d’attente**. Après avoir repéré une barre avec des valeurs hors norme, il peut rechercher les jeux de données pour lesquels les requêtes ont dû attendre pendant cette période, et aussi examiner le temps d’attente moyen des requêtes par rapport à la durée moyenne des requêtes. Quand ces deux métriques sont de même grandeur et que la charge de travail des requêtes pour le jeu de données n’est pas triviale, il est probable que le jeu de données soit affecté par une capacité insuffisante du processeur.

Cet effet peut être particulièrement apparent quand un jeu de données est consommé par des séquences courtes intensives de requêtes effectuées à une fréquence élevée par plusieurs utilisateurs (par exemple lors d’une session de formation), ce qui entraîne une saturation du processeur pendant chaque séquence intensive. Dans ce cas, des temps d’attente significatifs des requêtes sur ce jeu de données peuvent être rencontrés et avoir un impact sur d’autres jeux de données dans la capacité (effet de voisinage perturbateur).

Dans certains cas, les administrateurs Power BI peuvent demander aux propriétaires des jeux de données de créer une charge de travail de requêtes moins volatile en créant un tableau de bord (qui effectue périodiquement des requêtes avec une actualisation des jeux de données pour les vignettes mises en cache) au lieu d’un rapport. Ceci peut aider à éviter les pics quand un tableau de bord est chargé. Il se peut que cette solution ne soit pas toujours possible pour les besoins de l’entreprise, mais ce peut être un moyen efficace d’éviter la saturation du processeur sans qu’il soit nécessaire de modifier le jeu de données.

## <a name="acknowledgements"></a>Accusés de réception

Cet article a été écrit par Peter Myers, expert Data Plateform MVP et BI indépendant avec des solutions [Bitwise](https://www.bitwisesolutions.com.au/).

## <a name="next-steps"></a>Étapes suivantes

> [!div class="nextstepaction"]
> [Superviser les capacités Premium avec l’application](service-admin-premium-monitor-capacity.md)    
> [!div class="nextstepaction"]
> [Superviser les capacités dans le portail d’administration](service-admin-premium-monitor-portal.md)   

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)

||||||