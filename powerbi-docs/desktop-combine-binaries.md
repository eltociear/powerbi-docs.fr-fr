---
title: Combiner des fichiers (binaires) dans Power BI Desktop
description: Associer facilement des sources de données de fichiers (binaires) dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/13/2020
ms.author: davidi
LocalizationGroup: Transform and shape data
ms.openlocfilehash: 07381461375ea7b9707b91c807e92cdb85c1d440
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "76161089"
---
# <a name="combine-files-binaries-in-power-bi-desktop"></a>Combiner des fichiers (binaires) dans Power BI Desktop

Voici une approche puissante de l’importation de données dans **Power BI Desktop** : Si vous avez plusieurs fichiers qui ont le même schéma, combinez-les dans une seule table logique. Cette technique populaire est désormais plus pratique et plus étendue.

Pour lancer le processus de combinaison de fichiers à partir du même dossier, sélectionnez **Obtenir les données**, choisissez **Fichier** > **Dossier**, puis sélectionnez **Se connecter**.

![Fichier Se connecter à un dossier, boîte de dialogue Obtenir les données, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_1.png)

Entrez le chemin d’accès au dossier, sélectionnez **OK**, puis sélectionnez **Transformer les données** pour afficher les fichiers du dossier dans l’éditeur Power Query.

## <a name="combine-files-behavior"></a>Comportement de la combinaison de fichiers

Pour combiner des fichiers binaires dans l’éditeur Power Query, sélectionnez **Contenu** (étiquette de la première colonne) et sélectionnez **Accueil** > **Combiner des fichiers**. Vous pouvez aussi simplement sélectionner l’icône **Combiner des fichiers** en regard de **Contenu**.

![Commande Combiner des fichiers, éditeur Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_2a.png)

La transformation *Combiner les fichiers* se comporte comme suit :

* La transformation Combiner des fichiers analyse chaque fichier d’entrée et détermine le format de fichier correct à utiliser, par exemple, *texte*, *classeur Excel* ou *fichier JSON*.
* La transformation vous permet de sélectionner un objet spécifique dans le premier fichier, par exemple un classeur Excel, à extraire.
  
  ![Boîte de dialogue Combiner des fichiers, éditeur Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_3.png)
* La transformation Combiner des fichiers effectue ensuite automatiquement ces actions :
  
  * Crée un exemple de requête qui effectue toutes les étapes d’extraction requises dans un seul fichier.
  * Crée une *requête de fonction* qui ajuste l’entrée de fichier/binaire pour l’*exemple de requête*. L’exemple de requête et la requête de fonction sont liés afin que les modifications apportées à l’exemple de requête soient répercutées dans la requête de fonction.
  * Applique la *requête de fonction* à la requête d’origine avec des fichiers binaires d’entrée, comme la requête *Dossier*. Elle applique la requête de fonction pour les entrées binaires sur chaque ligne, puis développe l’extraction de données obtenue en tant que colonnes de niveau supérieur.

    ![Résultats de la transformation Combiner des fichiers, éditeur Power Query, Power BI Desktop](media/desktop-combine-binaries/combine-binaries_4.png)

> [!NOTE]
> L’étendue de votre sélection dans un classeur Excel affecte le comportement de la combinaison de fichiers binaires. Par exemple, vous pouvez sélectionner une feuille de calcul spécifique pour combiner cette feuille de calcul ou sélectionner la racine pour combiner le fichier complet. La sélection d’un dossier combine les fichiers figurant dans ce dossier. 

Avec le comportement de Combiner des fichiers, il est facile de combiner tous les fichiers d’un dossier donné, s’ils ont le même type et la même structure de fichier (par exemple les mêmes colonnes).

En outre, vous pouvez appliquer des étapes de transformation ou d’extraction supplémentaires en modifiant l’exemple de requête créé automatiquement sans avoir à modifier ou à créer d’autres étapes de requête de fonction. Les modifications apportées à l’exemple de requête sont automatiquement générées dans la requête de fonction liée.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Qu’est-ce que Power BI Desktop ?](desktop-what-is-desktop.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des fichiers CSV dans Power BI Desktop](desktop-connect-csv.md)
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
