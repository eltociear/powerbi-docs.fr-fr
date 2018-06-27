---
title: Utilisation et optimisation de la mémoire capacité Power BI Premium
description: Comprendre l’optimisation et la gestion de la mémoire capacité Power BI Premium.
ms.date: 04/30/2018
ms.topic: conceptual
ms.service: powerbi
ms.component: powerbi-admin
ms.author: susuresh
ms.reviewer: susuresh
author: suds001
manager: kfile
ms.openlocfilehash: 03c5e56c5f516bb1f09f51463d4c533185fbb63c
ms.sourcegitcommit: 2a7bbb1fa24a49d2278a90cb0c4be543d7267bda
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "34298455"
---
# <a name="power-bi-premium-capacity-resource-management-and-optimization"></a>Optimisation et gestion des ressources capacité Power BI Premium

Cet article décrit comment le service Power BI Premium gère les ressources et fournit des conseils sur la planification et l’optimisation de votre solution.

## <a name="premium-capacity-memory-management"></a>Gestion de la mémoire de capacité Premium

 La mémoire de capacité Premium est consommée par :

* Mémoire utilisée par les jeux de données chargés
* Mémoire utilisée par l’actualisation du jeu de données (planifiée et à la demande)
* Mémoire utilisée par les requêtes de rapport

Lorsqu’une requête est émise sur un jeu de données publié dans votre capacité, ce jeu de données est chargé en mémoire à partir du stockage persistant (également appelé chargement d’image). Le fait de conserver le jeu de données chargé en mémoire aide à répondre rapidement aux requêtes ultérieures sur ce jeu de données. En plus de la mémoire nécessaire pour conserver le jeu de données chargé en mémoire, les requêtes de rapport et les actualisations du jeu de données consomment également de la mémoire supplémentaire.

### <a name="dataset-memory-estimation"></a>Estimation de la mémoire pour le jeu de données

Lorsque vous tentez de charger un jeu de données en mémoire, Power BI estime la quantité de mémoire requise par ce jeu de données pour exécuter la commande demandée. Les jeux de données en mémoire ont tendance à être plus volumineux qu’ils ne le sont lorsqu’ils sont enregistrés sur le disque. Lors de l’actualisation d’un jeu de données, la capacité de mémoire nécessite au moins deux fois la quantité de mémoire par rapport à lorsqu’elle est inactive.

### <a name="overcommitting-capacity-eviction-and-reloading-of-datasets"></a>Sollicitation excessive de la capacité, éviction et rechargement des jeux de données

Power BI Premium vous offre l’avantage de la sollicitation excessive de votre capacité. Par exemple, vous pouvez publier plus de jeux de données que la capacité de mémoire peut en contenir. Si les jeux de données publiés dans votre capacité ont besoin de davantage de mémoire que ce que la capacité peut contenir, alors certains jeux de données sont stockés séparément dans un stockage persistant. Le stockage persistant fait partie des 100 To de stockage associés à chacune de vos capacités.

Donc, quels jeux de données restent en mémoire et que se passe-t-il pour les autres jeux de données ? Comme décrit précédemment, lorsqu’une requête est émise sur un jeu de données, celui-ci est chargé en mémoire (chargement d’image). La requête peut être une requête de rapport ou une opération d’actualisation.

Étant donné que vous pouvez solliciter de manière excessive votre capacité, celle-ci peut également être confrontée à une sollicitation de la mémoire. Lorsque la capacité fait face à une sollicitation de la mémoire (car un nouveau jeu de données doit être chargé ou les requêtes sur des jeux de données chargés augmentent les besoins en mémoire), le nœud *supprime un ou plusieurs jeux de données* occupant la capacité de mémoire. Les jeux de données inactifs (autrement dit, aucune requête/opération d’actualisation n’est en cours) sont supprimés en premier, et l’ordre de suppression commence par l’élément « utilisé le moins récemment ». Si de nouvelles commandes sont émises sur le jeu de données supprimé, le service tente de le recharger en mémoire, supprimant potentiellement d’autres jeux de données. Ce comportement permet une utilisation plus efficace en autorisant la capacité à répondre à davantage jeux de données que la mémoire ne peut en contenir.

Le chargement d’un jeu de données en mémoire est une opération relativement coûteuse. Selon la taille du jeu de données, l’opération peut durer quelques secondes pour les petits jeux de données ou des dizaines de secondes ou même de minutes pour les jeux de données volumineux, tels que des jeux de données de 10 Go. La capacité Premium tente de réduire le nombre de fois où la capacité devra être chargée en conservant en mémoire les jeux de données utilisés le moins récemment aussi longtemps que possible. Lorsque de la mémoire supplémentaire est nécessaire, certains jeux de données devront être supprimés et le système tentera de choisir celui qui a le moins d’impact sur l’expérience utilisateur. Lorsque de la mémoire supplémentaire est nécessaire, certains jeux de données devront être supprimés et le système tentera de choisir celui qui a le moins d’impact sur l’expérience utilisateur. Par exemple, le système évitera de supprimer les jeux de données qui ont été utilisés activement au cours des dernières minutes, car ils sont susceptibles d’être à nouveau interrogés très bientôt.

Le processus de suppression lui-même est une opération rapide. Si le jeu de données n’est pas en cours d’utilisation au moment de la suppression, celle-ci n’aura pas d’impact sur l’utilisateur. Toutefois, si trop de jeux de données sont en cours d’utilisation simultanément et que la mémoire n’est pas suffisante pour tous les contenir, un grand nombre de suppressions peut se produire. Cela peut conduire à une situation « d’écroulement », où les jeux de données sont constamment supprimés et rechargés, et les utilisateurs pourraient subir une baisse perceptible des temps de réponse et des performances.

### <a name="dataset-refresh-memory-requirement-competing-with-an-active-dataset-memory-requirement"></a>Quantité de mémoire demandée pour l’actualisation du jeu de données en concurrence avec la quantité de mémoire demandée pour le jeu de données actif

Les jeux de données peuvent être actualisés selon une planification ou à la demande des utilisateurs. Comme décrit précédemment, la mémoire requise pour les actualisations complètes est d’au moins deux fois la taille de la mémoire des jeux de données chargés et inactifs. Avant le démarrage de l’actualisation, la quantité de mémoire demandée pour l’actualisation est estimée. Si la quantité de mémoire demandée totale est supérieure à la mémoire disponible dans la capacité, certains jeux de données sont supprimés. Les candidats à la suppression sont choisis dans l’ordre des jeux de données les moins récemment utilisés ; par exemple, le service essaie de conserver en mémoire autant de jeux de données récemment utilisés que possible.

Si la mémoire requise n’est pas disponible en dépit de la suppression, l’actualisation est placée en file d’attente pour être retentée ultérieurement. Le service réessaye d’effectuer l’actualisation jusqu’à ce qu’il réussisse ou une nouvelle action d’actualisation commence.

Si une requête interactive est émise sur n’importe quel jeu de données dans la capacité et que la mémoire disponible n’est pas suffisante en raison d’une actualisation en cours, cette requête échoue et doit être retentée par l’utilisateur.

## <a name="cpu-resource-management-in-premium-capacity"></a>Gestion des ressources du processeur dans la capacité Premium

Il existe deux principaux consommateurs des ressources du processeur :

- Requêtes à partir de rapports
- Actualisation (traitement)

### <a name="queries-from-reports"></a>Requêtes à partir de rapports

Les requêtes de rapport consomment des ressources de processeur de votre capacité. Si le rapport contient des requêtes qui sont inefficaces ou si vous avez plusieurs utilisateurs simultanés, il peut consommer beaucoup de ressources processeur et la capacité existante peut ne pas suffire pour gérer la charge.

### <a name="refresh-parallelization-policy"></a>Stratégie de parallélisation de l’actualisation

La mémoire n’est pas la seule ressource qui peut contraindre l’actualisation des jeux de données. Le nombre de cœurs v-core sur un serveur peut également être un facteur. Étant donné que chaque opération d’actualisation nécessite un certain nombre de cœurs v-core, il existe une limite du nombre d’actualisations qui peuvent s’exécuter en parallèle. La limite par référence SKU est détaillée dans le tableau suivant. Les actualisations supplémentaires qui vont au-delà de ces limites sont mises en attente.

 | Référence  | V-cores du principal  | Parallélisme de l’actualisation de modèle   |
 | --- | --- | --- |
 | A1  | 0.5  | 1  |
 | A2  | 1  | 2  |
 | A3  | 2  | 3  |
 | A4  | 4  | 6  |
 | A5  | 8  | 12  |
 | A6  | 16  | 24  |
 | EM1  | 0.5  | 1  |
 | EM2  | 1  | 2  |
 | EM3  | 2  | 3  |
 | P1  | 4  | 6  |
 | P2  | 8  | 12  |
 | P3  | 16  | 24  |
 | P4  | 32  | 48  |
 | P5  | 64  | 96  |

 > [!TIP]
> Si vos actualisations sont retardées, vérifiez le nombre d’actualisations parallèles prises en charge par votre capacité.

## <a name="example-scenarios"></a>Exemples de scénarios

Les éléments suivants décrivent certains scénarios courants et les actions effectuées par le service :

 **Vingt actualisations planifiées soumises en même temps** – Power BI tente de démarrer les premières *x* actualisations en même temps. La valeur de *x* est déterminée par la stratégie de parallélisation d’actualisation pour cette référence SKU. Si Power BI ne peut pas obtenir suffisamment de mémoire en supprimant des jeux de données inactifs (jeux de données non utilisés récemment), les *x* actualisations ne démarreront pas toutes en même temps. Toute actualisation qui ne peut pas démarrer est placée en file d’attente jusqu’à ce qu’elle puisse commencer.

 **Deux actualisations en cours d’exécution en même temps et la mémoire disponible n’est suffisante que pour terminer une seule actualisation** - L’actualisation qui peut se terminer démarre. L’autre est retentée ultérieurement.

 **Un grand nombre de jeux de données sont interrogés pendant l’actualisation de plusieurs jeux de données** - Si la mémoire disponible n’est pas suffisante, Power BI essaie d’arrêter les actualisations actives pour donner la priorité aux requêtes interactives. Cela diminue les performances de l’actualisation.

 **Le jeu de données nécessite trop de mémoire pour être actualisé avec la taille actuelle de la capacité** - L’actualisation échoue. Aucune tentative n’est effectuée pour obtenir plus de mémoire par suppression.

 **Actualisation d’un jeu de données unique avec un pic important dans la mémoire** - Si le pic est supérieur à la quantité de mémoire qui peut être obtenue par la suppression des jeux de données inactifs, l’actualisation est retentée ultérieurement jusqu’à ce que la mémoire soit suffisante pour gérer le pic.

 **Requête exécutée pour un jeu de données qui ne peut pas obtenir suffisamment de mémoire en supprimant tous les jeux de données inactifs et les actualisations** - Ces requêtes échouent. Pour ces types de charges de travail, vous devez acheter une capacité supérieure.

## <a name="troubleshooting-and-testing"></a>Résolution des problèmes et test

Si les rapports sont lents ou ne répondent pas, commencez par tester pour un seul utilisateur dans votre rapport. Ensuite, augmentez la charge d’utilisateurs simultanés pour rechercher la limite. Dans de nombreux cas, le paramétrage de votre DAX (requêtes de rapport) peut modifier considérablement les performances de vos rapports (et augmenter le nombre d’utilisateurs simultanés pris en charge par votre capacité).

Utilisez la capacité Power BI Embedded dans Azure pour tester différentes références SKU et déterminer la meilleure référence SKU Premium pour votre charge de travail attendue. La référence SKU A4 Power BI Embedded est égale à P1, A5 = P2 et A6 = P3. Dans Azure, vous pouvez basculer facilement entre les références SKU en appliquant la montée (scale up) et la descente (scale down) en puissance dans le portail Azure. Lorsque vous trouvez la référence SKU qui convient le mieux à votre charge de travail et que vos tests sont terminés, vous pouvez supprimer la référence SKU.

Dans certains cas, le fait d’ouvrir d’un fichier PBIX du modèle sur votre ordinateur et de vérifier la consommation de la mémoire et du processeur offre beaucoup d’informations sur le problème. Cela n’est pas utile pour les modèles très volumineux, mais pour certains modèles plus petits, essayez d’ouvrir, d’actualiser et d’interroger le modèle à partir de votre ordinateur. Vérifiez la taille du modèle, la mémoire et le processeur consommés lorsque vous ouvrez le modèle. Essayez de réactualiser et d’interroger. Utilisez le Gestionnaire des tâches pour vérifier la consommation de mémoire et de processeur pour le fichier PBIX local. Parfois, les métriques sur votre ordinateur peuvent indiquer qu’une capacité Premium inférieure comme P1 / P2 ne fonctionnera pas pour votre solution.
