---
title: "Combiner des fichiers binaires dans Power BI Desktop"
description: "Associer facilement des sources de données binaires dans Power BI Desktop"
services: powerbi
documentationcenter: 
author: davidiseminger
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 12/06/2017
ms.author: davidi
ms.openlocfilehash: d0c4f3afb7b8b103dfa59a982b067bbad24251fb
ms.sourcegitcommit: d91436de68a0e833ecff18d976de9d9431bc4121
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/06/2017
---
# <a name="combine-binaries-in-power-bi-desktop"></a>Combiner des fichiers binaires dans Power BI Desktop
Une approche intéressante pour l’importation de données dans **Power BI Desktop** est de combiner plusieurs fichiers ayant le même schéma dans une seule table logique. Avec la version de novembre 2016 de **Power BI Desktop** (et les versions ultérieures), cette approche populaire et pratique a été étendue comme décrit dans cet article.

Pour démarrer le processus de combinaison de fichiers binaires à partir du même dossier, sélectionnez **Obtenir des données > Fichier > Dossier**.

![](media/desktop-combine-binaries/combine-binaries_1.png)

## <a name="previous-combine-binaries-behavior"></a>Ancien comportement de la combinaison de fichiers binaires
Avant la version de novembre 2016 de **Power BI Desktop**, vous pouviez combiner certains types de fichiers à l’aide de la transformation **Combiner les fichiers binaires**, avec des limitations toutefois :

* Les transformations n’étaient pas considérées pour chaque fichier tant que les fichiers n’étaient pas combinés dans une seule table. Par conséquent, vous deviez souvent combiner des fichiers, puis filtrer les *valeurs d’en-tête* en filtrant les lignes dans le cadre du processus de modification.
* La transformation **Combiner les fichiers binaires** fonctionnait pour les fichiers *texte* ou *CSV*, mais pas pour les autres formats de fichiers pris en charge tels que les classeurs Excel, les fichiers JSON, etc.

Comme les clients demandaient un fonctionnement plus intuitif de l’opération **Combiner les fichiers binaires**, la transformation a été améliorée.

## <a name="current-combine-binaries-behavior"></a>Comportement actuel de la combinaison de fichiers binaires
**Power BI Desktop** gère à présent plus efficacement l’opération **Combiner les fichiers binaires**. Pour commencer, sélectionnez **Combiner les fichiers binaires** à partir de l’onglet **Accueil** du ruban dans l’**éditeur de requête** ou à partir de la colonne elle-même.

![](media/desktop-combine-binaries/combine-binaries_2a.png)

La transformation **Combiner les fichiers binaires** se comporte maintenant comme suit :

* La transformation **Combiner les fichiers binaires** analyse chaque fichier d’entrée et détermine le format de fichier approprié à utiliser, tel que *texte*, *classeur Excel* ou *JSON*.
* La transformation vous permet de sélectionner un objet spécifique dans le premier fichier, par exemple un *classeur Excel*, à extraire.
  
  ![](media/desktop-combine-binaries/combine-binaries_3.png)
* La transformation **Combiner les fichiers binaires** effectue ensuite automatiquement les opérations suivantes :
  
  * Crée un exemple de requête qui effectue toutes les étapes d’extraction requises dans un seul fichier.
  * Crée une *requête de fonction* qui ajuste l’entrée de fichier/binaire pour l’*exemple de requête*. L’exemple de requête et la requête de fonction sont liés afin que les modifications apportées à l’exemple de requête soient répercutées dans la requête de fonction.
  * Applique la *requête de fonction* à la requête d’origine avec les fichiers binaires d’entrée (par exemple la requête *Dossier*) : applique donc la requête de fonction pour les entrées binaires sur chaque ligne, puis développe l’extraction de données qui en résulte en tant que colonnes de niveau supérieur.
    
    ![](media/desktop-combine-binaries/combine-binaries_4.png)

Avec le nouveau comportement **Combiner les fichiers binaires**, vous pouvez facilement combiner tous les fichiers binaires dans un dossier donné à condition qu’ils aient le même type de fichier et la même structure (par exemple, les mêmes colonnes).

En outre, vous pouvez facilement appliquer des étapes supplémentaires de transformation ou d’extraction en modifiant l’*exemple de requête* créé automatiquement sans avoir à vous soucier de la modification ou de la création d’autres étapes de la *requête de fonction*. Les modifications apportées à l’*exemple de requête* sont automatiquement générées dans la *requête de fonction* associée.

## <a name="next-steps"></a>Étapes suivantes
Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des fichiers CSV dans Power BI Desktop](desktop-connect-csv.md)   
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)   

