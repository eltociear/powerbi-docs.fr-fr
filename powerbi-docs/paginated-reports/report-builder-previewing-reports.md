---
title: Afficher un aperçu des rapports dans le Générateur de rapports Power BI
description: Quand vous créez un rapport paginé du Générateur de rapports, il est utile d’afficher régulièrement un aperçu du rapport pour vérifier qu’il affiche ce que vous voulez.
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: afbc31e3ece8bc72ad52bb2fe7c3d871b2f68e1b
ms.sourcegitcommit: ced8c9d6c365cab6f63fbe8367fb33e6d827cb97
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/07/2020
ms.locfileid: "78922939"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Afficher un aperçu des rapports dans le Générateur de rapports Power BI
  Quand vous créez un rapport paginé du Générateur de rapports, il est utile d’afficher régulièrement un aperçu du rapport pour vérifier qu’il affiche ce que vous voulez. Pour afficher un aperçu de votre rapport, cliquez sur **Exécuter**. Le rapport est restitué en mode Aperçu.  
  
 Le Générateur de rapports améliore l’expérience d’aperçu à l’aide de sessions d’édition quand il est connecté à un serveur de rapports. La session d’édition crée un cache de données et permet de disposer des jeux de données du cache pour les prochains aperçus de rapport. Une session d’édition n’est pas une fonctionnalité avec laquelle vous interagissez directement, mais comprendre quand le jeu de données mis en cache est actualisé vous aidera à améliorer les performances quand vous afficherez l’aperçu d’un rapport et à savoir pourquoi le rapport s’affiche plus rapidement ou plus lentement.  

  
> [!NOTE]  
> Il existe des différences entre l’aperçu dans le Générateur de rapports et l’affichage dans un navigateur. Par exemple, un calendrier, qui est ajouté à un rapport quand vous spécifiez un paramètre de type Date/heure, est différent dans le Générateur de rapports et dans un navigateur. 
  
## <a name="improving-preview-performance"></a>Amélioration des performances d’aperçu  
 La façon dont vous créez et mettez à jour les rapports affecte la rapidité d’affichage de leur aperçu. La première fois que vous affichez l’aperçu d’un rapport qui dépend d’une référence de serveur, une session d’édition est créée pour vous et les données utilisées lors de l’exécution du rapport sont ajoutées à un cache de données qui est stocké. Lorsque vous apportez des changements au rapport qui n’affectent pas les données, la copie mise en cache des données est utilisée par le rapport. Cela signifie que vous ne verrez pas les données changer chaque fois que vous afficherez un aperçu du rapport. Si vous voulez les nouvelles données, cliquez sur le bouton **Actualiser** sur le ruban.  
  
 Les actions suivantes entraînent l’actualisation du cache et ralentissent l’affichage du rapport la prochaine fois que vous en afficherez un aperçu :  
  
-   Ajouter, changer ou supprimer un jeu de données. Le jeu de données mis en cache contient tous les jeux de données qu’utilise un rapport et toute modification apportée à un jeu de données invalide le jeu de données mis en cache. Cela comprend le changement du nom, de la requête ou des champs du jeu de données.  
  
    > [!NOTE]  
    >  Si le jeu de données a un grand nombre de champs que vous ne pensez pas utiliser, envisagez de mettre à jour le jeu de données pour omettre ces champs. Bien que cette opération crée une nouvelle session d’édition et que le premier aperçu du rapport soit plus lent, un plus petit jeu de données mis en cache est globalement bénéfique pour les performances du serveur de rapports.  
  
-   Ajouter, changer ou supprimer une source de données. Cela comprend le changement du nom ou des propriétés de la source de données, l’extension de données de la source de données ou les propriétés de la connexion à la source de données.  
  
-   Remplacer la source de données qu’utilise le rapport par une autre source de données.  
  
-   Changer la langue du rapport.  
  
-   Changer les assemblys ou le code personnalisé qu’utilise le rapport.  
  
-   Ajouter, changer ou supprimer les paramètres de requête dans les valeurs de paramètre ou de rapport.  
  
 Les changements apportés à la disposition du rapport et à la mise en forme des données n’affectent pas le jeu de données mis en cache. Vous pouvez effectuer les actions suivantes sans actualiser le jeu de données mis en cache :  
  
-   Ajouter ou supprimer des régions de données comme des tableaux, des matrices ou des graphiques.  
  
-   Ajouter ou supprimer des colonnes dans le rapport. Tous les champs du jeu de données peuvent être utilisés dans le rapport. L’ajout ou la suppression de champs dans le rapport n’ont aucun effet sur le jeu de données.  
  
-   Changer l’ordre des champs dans les tableaux et les matrices.  
  
-   Ajouter, changer ou supprimer des groupes de lignes et de colonnes.  
  
-   Ajouter, changer ou supprimer la mise en forme des valeurs de données dans les champs.  
  
-   Ajouter, changer ou supprimer des images, des lignes ou des zones de texte.  
  
-   Changer des sauts de page.  
  
La session d’édition est créée quand vous affichez un aperçu du rapport pour la première fois. Par défaut, une session d’édition dure 7 200 secondes (2 heures). La session est réinitialisée sur deux heures chaque fois que vous exécutez le rapport. Lorsque la session d’édition expire, le cache de données est supprimé. Si la session d’édition expire, une autre est créée automatiquement la prochaine fois que vous affichez un aperçu du rapport.
  
Par défaut, le cache de données peut contenir jusqu’à cinq jeux de données. Si vous utilisez différentes combinaisons de valeurs de paramètre, le rapport risque d’avoir besoin de davantage de données. Par conséquent, l’actualisation du cache et l’affichage du rapport seront plus lents la prochaine fois que vous afficherez un aperçu. 
  
## <a name="concurrency-of-report-updates"></a>Conflit des mises à jour du rapport  
Souvent, vous affichez un aperçu du rapport pour mettre à jour puis pour enregistrer le rapport sur le service Power BI. Quand vous mettez à jour un rapport, il est possible qu’une autre personne mette à jour puis enregistre le rapport en même temps. Le rapport qui est enregistré en dernier est la version du rapport disponible pour les futures visualisations et mises à jour. Cela signifie que la version du rapport que vous avez prévisualisée risque de ne pas être la version que vous rouvrez. Vous avez la possibilité d’enregistrer le rapport sous un nouveau nom en utilisant l’option **Enregistrer sous** dans le menu du Générateur de rapports.  
  
## <a name="external-report-items"></a>Éléments de rapport externes  
 Votre rapport peut inclure des éléments tels que des images externes qui sont stockés à part du rapport. Étant donné que les éléments sont stockés à part, il est possible de les déplacer dans un autre emplacement ou de les supprimer. Si cela se produit, vous risquez de ne pas pouvoir afficher un aperçu de votre rapport. Vous pouvez mettre à jour le rapport pour indiquer le nouvel emplacement de l’élément ou si l’élément a été supprimé, vous pouvez le remplacer par un élément existant ou supprimer du rapport la référence à l’élément.  
  
## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
  
