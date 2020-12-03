---
title: Afficher un aperçu des rapports dans le Générateur de rapports Power BI
description: Quand vous créez un rapport paginé du Générateur de rapports, il est utile d’afficher régulièrement un aperçu du rapport pour vérifier qu’il affiche ce que vous voulez.
author: maggiesMSFT
ms.author: maggies
ms.date: 06/06/2019
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.assetid: ba6b5bdd-d8c6-4aa8-ba32-3a10b11969d4
ms.openlocfilehash: d982174d814b3f1042e02dc9beda762848c48086
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96416206"
---
# <a name="previewing-reports-in-power-bi-report-builder"></a>Afficher un aperçu des rapports dans le Générateur de rapports Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Quand vous créez un rapport paginé du Générateur de rapports, il est utile d’afficher régulièrement un aperçu du rapport pour vérifier qu’il affiche ce que vous voulez. Cliquez sur **Exécuter** pour afficher un aperçu du rapport. Le rapport est restitué en mode Aperçu.  
  
 Le Générateur de rapports améliore l'expérience des utilisateurs en termes d'affichage de l'aperçu en utilisant des sessions d'édition lorsqu'il est connecté à un serveur de rapports. La session d'édition crée un cache de données et rend les datasets du cache disponibles pour afficher régulièrement un aperçu du rapport. Une session d'édition n'est pas une fonctionnalité avec laquelle vous interagissez directement, mais la compréhension du mécanisme d'actualisation du dataset mis en cache vous aidera à améliorer les performances de rendu du rapport lors de son affichage.  

  
> [!NOTE]  
> Il existe des différences entre l’aperçu dans le Générateur de rapports et l’affichage dans un navigateur. Par exemple, un contrôle de calendrier, qui est ajouté à un rapport lorsque vous spécifiez un paramètre de type Date/heure, est différent dans le Générateur de rapports et dans un navigateur. 
  
## <a name="improving-preview-performance"></a>Amélioration des performances d’aperçu  
 Le mode de création et de mise à jour d'un rapport affecte la rapidité de rendu de l'aperçu du rapport. La première fois que vous affichez l’aperçu d’un rapport qui dépend d’une référence de serveur, une session d’édition est créée pour vous et les données utilisées lors de l’exécution du rapport sont ajoutées à un cache de données qui est stocké. Lorsque vous apportez des modifications au rapport qui n'affectent pas les données, la copie mise en cache des données est utilisée par le rapport. Cela signifie que vous ne verrez pas vos données changer chaque fois que vous afficherez un aperçu du rapport. Si vous souhaitez afficher les nouvelles données, cliquez sur le bouton **Actualiser** sur le ruban.  
  
 Les actions suivantes provoquent l'actualisation du cache et ralentiront le rendu lors du prochain affichage de l'aperçu du rapport :  
  
-   Ajoutez, modifiez ou supprimez un dataset. Le dataset mis en cache contient tous les datasets utilisés par un rapport et toute modification apportée à un dataset rendra invalide le dataset mis en cache. Cela inclut la modification du nom, d'une requête ou de champs dans le dataset.  
  
    > [!NOTE]  
    >  Si le jeu de données a un grand nombre de champs que vous ne pensez pas utiliser, envisagez de mettre à jour le jeu de données pour omettre ces champs. Bien que la mise à jour crée une nouvelle session d'édition et ralentisse le premier aperçu du rapport, l'utilisation d'un dataset mis en cache plus petit améliore en général les performances du serveur de rapports.  
  
-   Ajoutez, modifiez ou supprimez une source de données. Cela inclut modifier le nom ou les propriétés de la source de données, l'extension de données de la source de données ou les propriétés de la connexion à la source de données.  
  
-   Remplacer la source de données qu’utilise le rapport par une autre source de données.  
  
-   Modifiez la langue du rapport.  
  
-   Modifiez les assemblys ou le code personnalisé que le rapport utilise.  
  
-   Ajoutez, modifiez ou supprimez les paramètres de requête dans le rapport ou les valeurs de paramètres.  
  
 Les changements apportés à la disposition du rapport et à la mise en forme des données n’affectent pas le jeu de données mis en cache. Vous pouvez effectuer les actions suivantes sans actualiser le dataset mis en cache :  
  
-   Ajoutez ou supprimez des régions de données telles que des tables, des matrices ou des graphiques.  
  
-   Ajoutez ou supprimez des colonnes du rapport. Tous les champs du dataset sont disponibles pour être utilisés dans le rapport. L'ajout ou la suppression de champs dans le rapport n'a aucun effet sur le dataset.  
  
-   Modifiez l'ordre des champs dans les tables et les matrices.  
  
-   Ajoutez, modifiez ou supprimez des groupes de lignes et de colonnes.  
  
-   Ajoutez, modifiez ou supprimez la mise en forme des valeurs de données dans les champs.  
  
-   Ajoutez, modifiez ou supprimez des images, des lignes ou des zones de texte.  
  
-   Modifiez les sauts de page.  
  
La session d'édition est créée la première fois que vous affichez l'aperçu d'un rapport. Par défaut, une session d'édition dure 7 200 secondes (2 heures). La session est réinitialisée à deux heures chaque fois que vous exécutez le rapport. Lorsque la session d'édition expire, le cache de données est supprimé. Si la session d'édition expire, une autre session est créée automatiquement la prochaine fois que vous affichez un aperçu du rapport.
  
Par défaut, le cache de données peut contenir jusqu'à cinq datasets. Si vous utilisez de nombreuses combinaisons différentes de valeurs de paramètres, le rapport peut nécessiter plus de données. Ceci requiert l'actualisation du cache et le rendu du rapport sera plus lent lors du prochain aperçu. 
  
## <a name="concurrency-of-report-updates"></a>Conflit des mises à jour du rapport  
Souvent, vous affichez un aperçu du rapport pour mettre à jour puis pour enregistrer le rapport sur le service Power BI. Quand vous mettez à jour un rapport, il est possible qu’une autre personne mette à jour puis enregistre le rapport en même temps. Le rapport enregistré en dernier représente la version de rapport qu'il est possible d'afficher et de mettre à jour ultérieurement. Cela signifie que la version du rapport dont vous avez affiché l'aperçu n'est peut-être pas la version que vous rouvrez. Vous disposez de l'option d'enregistrer le rapport sous un nouveau nom à l'aide de l'option **Enregistrer sous** du menu du Générateur de rapports.  
  
## <a name="external-report-items"></a>Éléments de rapport externes  
 Votre rapport peut inclure des éléments tels que des images externes qui sont stockés à part du rapport. Étant donné que les éléments sont stockés à part, il est possible de les déplacer dans un autre emplacement ou de les supprimer. Si cela se produit, il est possible que vous ne puissiez pas afficher un aperçu de votre rapport. Vous pouvez soit mettre à jour le rapport pour indiquer l'emplacement mis à jour de l'élément ou, si l'élément a été supprimé, le remplacer par un élément existant, soit supprimer la référence à l'élément dans le rapport.  
  
## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
  
