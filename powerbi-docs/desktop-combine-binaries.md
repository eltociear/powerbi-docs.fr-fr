---
title: Combiner des fichiers (binaires) dans Power BI Desktop
description: Associer facilement des sources de données de fichiers (binaires) dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 4996b7485cb9514b9378982d2149ef5380e8fdc9
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combiner des fichiers (binaires) dans Power BI Desktop
Une approche intéressante pour l’importation de données dans **Power BI Desktop** est de combiner plusieurs fichiers ayant le même schéma dans une seule table logique. Avec la version de novembre 2016 de **Power BI Desktop** (et les versions ultérieures), cette approche populaire et pratique a été étendue comme décrit dans cet article.

Pour lancer le processus de combinaison de fichiers à partir du même dossier, sélectionnez **Obtenir des données > Fichier > Dossier**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-files-binaries-behavior"></a>Ancien comportement de la combinaison de fichiers (binaires)
Avant la version de novembre 2016 de **Power BI Desktop**, cette fonctionnalité s’appelait **Combiner des binaires** ; elle permettait de combiner certains types de fichiers à l’aide de la transformation **Combiner des binaires**, avec quelques limitations toutefois :

* Les transformations n’étaient pas considérées pour chaque fichier tant que les fichiers n’étaient pas combinés dans une seule table. Par conséquent, vous deviez souvent combiner des fichiers, puis filtrer les *valeurs d’en-tête* en filtrant les lignes dans le cadre du processus de modification.
* La transformation **Combiner les fichiers binaires** fonctionnait pour les fichiers *texte* ou *CSV*, mais pas pour les autres formats de fichiers pris en charge tels que les classeurs Excel, les fichiers JSON, etc.

Comme les clients demandaient un fonctionnement plus intuitif de l’opération **Combiner des binaires**, la transformation a été améliorée et renommée **Combiner des fichiers**.

## <a name="current-combine-files-behavior"></a>Comportement actuel de la combinaison de fichiers
**Power BI Desktop** gère à présent plus efficacement l’opération **Combiner des fichiers (binaires)**. Pour commencer, sélectionnez **Combiner des fichiers** dans l’onglet de ruban **Accueil** de **l’Éditeur de requête**, ou dans la colonne elle-même.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

La transformation **Combiner des fichiers** se comporte maintenant ainsi :

* La transformation **Combiner des fichiers** analyse chaque fichier d’entrée et détermine le format de fichier à utiliser, par exemple, *texte*, *classeur Excel* ou *JSON*.
* La transformation vous permet de sélectionner un objet spécifique dans le premier fichier, par exemple un *classeur Excel*, à extraire.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* La transformation **Combiner des fichiers** effectue alors automatiquement les requêtes suivantes :
  
  * Crée un exemple de requête qui effectue toutes les étapes d’extraction requises dans un seul fichier.
  * Crée une *requête de fonction* qui ajuste l’entrée de fichier/binaire pour l’*exemple de requête*. L’exemple de requête et la requête de fonction sont liés afin que les modifications apportées à l’exemple de requête soient répercutées dans la requête de fonction.
  * Applique la *requête de fonction* à la requête d’origine avec les fichiers binaires d’entrée (par exemple la requête *Dossier*) : applique donc la requête de fonction pour les entrées binaires sur chaque ligne, puis développe l’extraction de données qui en résulte en tant que colonnes de niveau supérieur.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Avec le nouveau comportement **Combiner des fichiers**, il est facile de combiner tous les fichiers dans un dossier donné à condition qu’ils aient le même type et la même structure (par exemple, les mêmes colonnes).

En outre, vous pouvez appliquer des étapes de transformation ou d’extraction supplémentaires en modifiant *l’exemple de requête* créé automatiquement sans avoir à modifier ou à créer d’autres étapes de *requête de fonction*. Les modifications apportées à *l’exemple de requête* sont automatiquement générées dans la *requête de fonction* liée.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des fichiers CSV dans Power BI Desktop](desktop-connect-csv.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

