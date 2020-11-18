---
title: Limitations et restrictions des dataflows ; fonctionnalités et connecteurs pris en charge
description: Vue d’ensemble de toutes les capacités des dataflows
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 10/01/2020
ms.author: davidi
LocalizationGroup: Data from files
ms.openlocfilehash: 2d58fe71b7ceb27afe5d52a55ed57ae162622b06
ms.sourcegitcommit: bd133cb1fcbf4f6f89066165ce065b8df2b47664
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/17/2020
ms.locfileid: "94668163"
---
# <a name="dataflows-limitations-and-considerations"></a>Considérations et limitations des dataflows

Les dataflows sont soumis à des limitations en matière de création, d’actualisation et de gestion de capacité que les utilisateurs doivent garder à l’esprit, comme décrit dans les sections suivantes.

## <a name="dataflow-authoring"></a>Création de dataflows

Au moment de créer des dataflows, les utilisateurs doivent prendre en considération les points suivants :

* La création de dataflows s’effectue dans l’environnement Power Query Online (PQO) ; prenez connaissance des limitations décrites dans [Limites de Power Query](/power-query/power-query-online-limits).
Les dataflows étant créés dans l’environnement Power Query Online (PQO), les mises à jour dont font l’objet les configurations de charge de travail Dataflows agissent uniquement sur les actualisations et n’ont pas d’impact sur l’expérience de création

* Les dataflows ne peuvent être modifiés que par leurs propriétaires

* Les dataflows ne sont pas disponibles dans *Mon espace de travail*

* Les dataflows utilisant des sources de données de passerelle ne prennent pas en charge des informations d’identification différentes pour une même source de données

* Le connecteur Web.Page doit être utilisé avec une passerelle

## <a name="api-considerations"></a>Considérations sur les API

Vous trouverez des informations supplémentaires sur les API REST Dataflows prises en charge dans la documentation de [référence sur les API REST](/rest/api/power-bi/dataflows). Voici quelques points à prendre en considération et à garder à l’esprit :

* L’exportation et l’importation d’un dataflow confèrent à celui-ci un nouvel ID

* À l’issue de l’importation d’un dataflow contenant des entités liées, les références présentes dans le flux de données ne sont pas corrigées (ces requêtes doivent être corrigées manuellement avant l’importation du dataflow)

* Les dataflows peuvent être remplacés par le paramètre *CreateOrOverwrite* s’ils ont été initialement créés à l’aide de l’API d’importation

## <a name="dataflows-in-shared"></a>Dataflows en mode Partagé

Les dataflows dans les capacités partagées présentent des limitations :

* Lors de l’actualisation des dataflows, les délais d’attente en mode Partagé sont de deux heures par entité et de trois par dataflow
* Il n’est pas possible de créer des entités liées dans les dataflows partagés, même s’ils peuvent en contenir, tant que la propriété *Load Enabled* (Chargement activé) est désactivée au niveau de la requête
* Il n’est pas possible de créer des entités calculées dans les dataflows partagés
* AutoML et Cognitive Services ne sont pas disponibles dans les dataflows partagés
* L’actualisation incrémentielle ne fonctionne pas dans les dataflows partagés

## <a name="dataflows-in-premium"></a>Dataflows en mode Premium

Les dataflows qui existent en mode Premium présentent les limitations et considérations suivantes.

**Considérations relatives aux actualisations et aux données :**

* Lors de l’actualisation des dataflows, les délais d’attente sont de 24 heures (sans distinction pour les entités et/ou les dataflows)

* Le fait de faire passer la stratégie d’actualisation d’un dataflow d’une actualisation incrémentielle à une actualisation normale (et inversement) a pour effet de supprimer toutes les données

* Le fait de modifier le schéma d’un dataflow a pour effet de supprimer toutes les données

**Entités liées et calculées :**

* Les entités liées peuvent atteindre une profondeur de 32 références

* Les dépendances cycliques d’entités liées ne sont pas autorisées

* Une entité liée ne peut pas être jointe à une entité standard qui obtient ses données à partir d’une source de données locale

* Quand une requête (par exemple, la requête *A*) est utilisée dans le calcul d’une autre requête (requête *B*) dans des dataflows, la requête *B* devient une entité calculée. Les entités calculées ne peuvent pas faire référence à des sources locales.


**Moteur de calcul :**

* Quand le moteur de calcul est utilisé, le temps nécessaire à l’ingestion de données augmente initialement d’environ 10 à 20 %.

  1. Cela vaut uniquement pour le premier dataflow qui se trouve dans le moteur de calcul et qui lit les données de la source de données
  2. Les dataflows suivants qui utilisent la source n’encourent pas la même pénalité

* Seules certaines opérations utilisent le moteur de calcul et seulement quand elles sont utilisées par l’intermédiaire d’une entité liée ou en tant qu’entité calculée. La liste complète de ces opérations est consultable dans [ce billet de blog](http://petcu40.blogspot.com/2019/06/m-folding-in-enhanced-engine-of-power.html).


**Gestion de capacité :**

* Par défaut, les capacités Power BI Premium intègrent un gestionnaire de ressources interne qui limite les charges de travail de différentes façons quand la capacité est à court de mémoire.

  1. Pour les dataflows, la pression exercée par cette limitation réduit le nombre de conteneurs M disponibles
  2. La mémoire réservée aux dataflows peut être définie sur 100 %, avec une taille de conteneur adaptée à vos volumes de données ; la charge de travail gère alors le nombre de conteneurs de manière appropriée

* Le nombre approximatif de conteneurs peut être déterminé en divisant la mémoire totale allouée à la charge de travail par la quantité de mémoire allouée à un conteneur

## <a name="dataflow-usage-in-datasets"></a>Utilisation de dataflows dans les jeux de données

* Quand vous créez un jeu de données dans Power BI Desktop et que vous le publiez ensuite sur le service Power BI, veillez à ce que les informations d’identification utilisées dans Power BI Desktop pour la source de données des dataflows soient les mêmes que celles utilisées au moment de publier le jeu de données dans le service.
  1. Faute de quoi, vous obtiendrez une erreur de type *Clé introuvable* pendant l’actualisation du jeu de données

## <a name="next-steps"></a>Étapes suivantes
Les articles suivants vous permettront d’en savoir plus sur les dataflows et Power BI :

* [Introduction aux dataflows et à la préparation des données en libre-service](dataflows-introduction-self-service.md)
* [Création d’un flux de données](dataflows-create.md)
* [Configurer et consommer un dataflow](dataflows-configure-consume.md)
* [Configuration du stockage de dataflows pour utiliser Azure Data Lake Gen 2](dataflows-azure-data-lake-storage-integration.md)
* [Fonctionnalités Premium des dataflows](dataflows-premium-features.md)
* [IA et dataflows](dataflows-machine-learning-integration.md)
* [Bonnes pratiques pour les dataflows](dataflows-best-practices.md)