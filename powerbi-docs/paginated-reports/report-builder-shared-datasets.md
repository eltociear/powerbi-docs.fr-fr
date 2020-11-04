---
title: Créer un rapport paginé avec un jeu de données partagé Power BI – Power BI Report Builder
description: Créez un rapport paginé dans Power BI Report Builder sur la base d’un jeu de données partagé Power BI.
ms.date: 07/08/2020
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 44f1c1280e176d99ab909402a77804074e7d8cbd
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298107"
---
# <a name="create-a-paginated-report-based-on-a-power-bi-shared-dataset"></a>Créer un rapport paginé sur la base d’un jeu de données partagé Power BI

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [yes-desktop](../includes/yes-desktop.md)] 

Vous pouvez utiliser un jeu de données créé dans Power BI Desktop comme source de données pour des rapports paginés du générateur de rapports Power BI. Imaginez ce scénario : Vous avez créé un rapport de Power BI dans Power BI Desktop. Vous avez passé beaucoup de temps à concevoir le modèle de données, créé un beau rapport Power BI avec toutes sortes d’excellents éléments visuels. Votre rapport possède une matrice avec de nombreuses lignes. vous devez donc les faire défiler pour les afficher tous. Les lecteurs de votre rapport veulent un rapport qu’ils peuvent imprimer, qui affiche toutes les lignes de cette matrice. Un rapport paginé Power BI peut le faire : imprimer une table ou une matrice qui s’exécute sur plusieurs pages, avec des en-têtes et des pieds de page et une mise en page parfaite que vous concevez vous-même. Il complète le rapport de Power BI Desktop. Vous souhaitez qu’ils soient basés sur les mêmes données, aucune incohérence, afin d’utiliser le même jeu de données.

![Rapport paginé Power BI Desktop vers un générateur de rapports](media/report-builder-shared-datasets/power-bi-desktop-report-builder-arrow-26-pgs.png)

Le jeu de données ne doit pas nécessairement se trouver dans un espace de travail d’une capacité Premium, et vous n’avez pas besoin d’être membre de cet espace de travail. Vous devez simplement disposer de [l’autorisation Build](../connect-data/service-datasets-build-permissions.md) pour le jeu de données. Pour publier votre rapport paginé, vous avez besoin d’une licence Power BI Pro. Vous avez également besoin d’un rôle contributeur au minimum pour un espace de travail dans une capacité Premium.

## <a name="what-you-need"></a>Ce dont vous avez besoin

Voici une liste de ce dont vous avez besoin et ce dont vous n’avez pas besoin pour utiliser un jeu de données partagé dans un générateur de rapports Power BI.

- Générateur de rapports Power BI. [Télécharger et installer le générateur de rapports Power BI](https://aka.ms/pbireportbuilder).
- Pour accéder à un jeu de données Power BI, vous devez disposer de l’autorisation Build pour le jeu de données. En savoir plus sur [l’autorisation de génération](../connect-data/service-datasets-build-permissions.md).
- Vous n’avez pas besoin d’une licence Power BI Pro pour créer un rapport paginé dans le générateur de rapports. 
- Pour publier votre rapport paginé, vous avez besoin d’une licence Power BI Pro. Vous avez également besoin d’un rôle contributeur au minimum pour un espace de travail dans une capacité Premium. 
- Facultatif : Si vous souhaitez suivre cet article, téléchargez le fichier exemple [Retail Analysis sample.pbix](https://download.microsoft.com/download/9/6/D/96DDC2FF-2568-491D-AAFA-AFDD6F763AE3/Retail%20Analysis%20Sample%20PBIX.pbix) de Power BI Desktop, ouvrez-le dans Power BI Desktop et ajoutez une table avec un grand nombre de colonnes. Dans le volet **Format** , désactivez **Totals**. Publiez-le ensuite dans un espace de travail du service Power BI.

    ![Totals désactivé](media/report-builder-shared-datasets/power-bi-desktop-totals-off.png)

## <a name="connect-to-the-power-bi-dataset"></a>Se connecter au jeu de données Power BI

1. Ouvrez le Générateur de rapports Power BI.
1. Sélectionnez **Se connecter** dans le coin supérieur droit du générateur de rapports pour vous connecter à votre compte Power BI.
1. Dans le volet des données de rapport, sélectionnez **Nouveau** > **Connexion de jeu de données Power BI**.

    ![Nouveau jeu de données dans le volet des données de rapport](media/report-builder-shared-datasets/power-bi-report-builder-new-dataset.png)

    > [!NOTE]
    > Vous ne pouvez pas créer la source de données ou un jeu de données pour un jeu de données Power BI à l’aide des assistants de table, de matrice ou de graphique du générateur de rapports. Une fois que vous les avez créés, vous pouvez utiliser les assistants pour créer des tables, des matrices ou des graphiques basés sur ces derniers.

1. Recherchez ou naviguez jusqu’au jeu de données ou à l’espace de travail où il réside > **Sélectionner**.
    Le générateur de rapports remplit le nom du jeu de données.

    ![Sélectionner un jeu de données](media/report-builder-shared-datasets/power-bi-report-builder-select-dataset.png)
    
1. Le jeu de données est listé sous Sources de données dans le volet des données de rapport.

    ![Jeu de données sous Sources de données dans le volet des données de rapport](media/report-builder-shared-datasets/power-bi-report-builder-data-source.png)

    N’oubliez pas que vous pouvez vous connecter à plusieurs jeux de données Power BI et à d’autres sources de données dans le même rapport paginé.


## <a name="get-the-dax-query-for-the-dataset"></a>Obtenir la requête DAX pour le jeu de données

Lorsque vous souhaitez que les données présentes dans votre rapport Power BI et dans votre rapport du générateur de rapports soient identiques, il ne suffit pas de vous connecter au jeu de données. Vous avez également besoin de la requête générée sur ce jeu de données.

### <a name="video-get-the-dax-query"></a>Vidéo : Obtenir la requête DAX

Dans la vidéo suivante, Chris Finlan montre comment obtenir la requête DAX dont vous avez besoin pour votre rapport paginé.

<iframe width="400" height="450" src="https://www.youtube.com/embed/NfoOK4QRkhI" frameborder="0" allowfullscreen></iframe>

### <a name="steps-to-get-the-dax-query"></a>Étapes à suivre pour obtenir la requête DAX

Voici à présent les étapes à suivre pour obtenir la requête.

1. Ouvrez le rapport Power BI (.pbix) dans Power BI Desktop.
1. Vérifiez que vous disposez d’une table dans votre rapport contenant toutes les données que vous souhaitez dans votre rapport paginé. La table doit répondre à ces deux exigences :
    - Il doit s’agir d’une table plate, et non d’une matrice ou d’un autre visuel. S’il ne s’agit pas d’une table, effectuez une conversion en table, suivez les étapes de l’Analyseur de performances ci-après, puis reconvertissez-la en visuel de votre choix.
    - Pour vos champs numériques, vous devez utiliser des *mesures prédéfinies*. Ils ont un symbole de calculatrice affiché en regard de chacun d’eux. Apprenez-en plus sur la [création de mesures](../transform-model/desktop-measures.md). 

        ![Icône de mesure](media/report-builder-shared-datasets/power-bi-measure-icon.png)

1. Sur le ruban **Affichage** , sélectionnez **Analyseur de performances**.

    ![Ouvrez l’analyseur de performances](media/report-builder-shared-datasets/power-bi-performance-analyzer.png)

1. Dans le volet **Analyseur de performances** , sélectionnez **Démarrer l’enregistrement** , puis **Actualiser les éléments visuels**.

    ![Actualiser les visuels](media/report-builder-shared-datasets/power-bi-performance-analyzer-refresh-visuals.png)

1. Développez le signe plus ( **+** ) à côté du nom de la table, puis sélectionnez **Copier une requête**. La requête est la formule DAX dont vous avez besoin pour le jeu de données dans le générateur de rapports Power BI.

    ![Copier la requête](media/report-builder-shared-datasets/power-bi-performance-analyzer-copy-query.png)

## <a name="create-the-dataset-with-the-query"></a>Créer le jeu de données avec la requête

1. Retournez au générateur de rapports Power BI.
1. Faites un clic droit sur le jeu de données sous **Source de données** , puis sélectionnez **Ajouter un jeu de données**.

    ![Ajouter un jeu de données](media/report-builder-shared-datasets/power-bi-report-builder-add-dataset.png)

1. Dans les propriétés du jeu de données, attribuez-lui un nom et sélectionnez **Concepteur de requêtes**.

4. Vérifiez que **DAX** est sélectionné, puis désélectionnez l’icône **Mode Création**.

    ![Concepteur de requêtes du générateur de rapports](media/report-builder-shared-datasets/power-bi-report-builder-query-designer.png)

1. Dans la zone supérieure, collez la requête que vous avez copiée depuis Power BI Desktop.

    > [!NOTE]
    > Si votre requête contient la fonction TOPN, supprimez-la de votre requête.

1. Sélectionnez **Exécuter la requête** (le point d’exclamation rouge, !) pour vous assurer que votre requête fonctionne. 

    ![Exécuter la requête](media/report-builder-shared-datasets/power-bi-report-builder-run-query.png)

    Les résultats de la requête s’affichent dans la zone inférieure.

    ![Résultats de la requête](media/report-builder-shared-datasets/power-bi-report-builder-query-results.png)

1. Sélectionnez **OK**.

    Vous voyez votre requête dans la fenêtre **Requête** de la boîte de dialogue **Propriétés du jeu de données**.

    ![Boîte de dialogue Propriétés du jeu de données](media/report-builder-shared-datasets/power-bi-report-builder-dataset-properties.png)

1. Sélectionnez **OK**.

    Vous voyez maintenant votre nouveau jeu de données avec une liste de ses champs dans le volet des données de rapport.

    ![Jeu de données dans le volet des données de rapport](media/report-builder-shared-datasets/power-bi-report-builder-dataset.png)

## <a name="create-a-table-in-the-report"></a>Créer une table dans le rapport

Un moyen rapide de créer une table consiste à utiliser l’Assistant Table.

1. Dans le ruban **Insertion** , sélectionnez **Table** > **Assistant Table**.

    ![Démarrer l’assistant Table](media/report-builder-shared-datasets/power-bi-report-builder-table-wizard.png)

1. Choisissez le jeu de données que vous avez créé avec la requête DAX > **Suivant**.

    ![Choisir un jeu de données](media/report-builder-shared-datasets/power-bi-report-builder-choose-dataset.png)

1. Pour créer un tableau à deux dimensions, sélectionnez les champs souhaités dans les **champs disponibles**. Vous pouvez sélectionner plusieurs champs à la fois en sélectionnant le premier que vous souhaitez, en maintenant la touche Maj enfoncée et en sélectionnant le dernier.

    ![Sélectionner plusieurs champs](media/report-builder-shared-datasets/power-bi-report-builder-select-fields.png)

1. Faites glisser les champs vers la zone **Valeurs** > **Suivant**.

    ![Assistant Table](media/report-builder-shared-datasets/power-bi-report-builder-value-fields.png)

1. Choisissez les options de disposition souhaitées > **Suivant**.

1. Sélectionnez **Terminer**.
    Vous voyez votre table en mode Conception.

    ![Mode Création de rapport](media/report-builder-shared-datasets/power-bi-report-builder-design-view.png)

1. Sélectionnez **Cliquer pour ajouter un titre** et ajoutez un titre.

1. Sélectionnez **Exécuter** pour afficher un aperçu de votre rapport.

    ![Aperçu du rapport](media/report-builder-shared-datasets/power-bi-report-builder-preview.png)

1. Sélectionnez **Disposition d’impression** pour afficher l’apparence de votre rapport. 

    Cette mise en page du rapport nécessite un travail. Il contient 54 pages, car les colonnes et les marges engendrent une table de deux pages de largeur.

    ![Mise en page du rapport](media/report-builder-shared-datasets/power-bi-report-builder-print-layout-2-p1-p2.png)

## <a name="format-the-report"></a>Mettre en forme le rapport

Vous avez plusieurs options de mise en forme pour que votre tableau tienne sur une seule page. 

1. Vous pouvez affiner les marges de page dans le volet Propriétés. Si vous ne voyez pas le volet Propriétés, dans le ruban **Affichage** , activez la case à cocher **Propriétés**.

1. Sélectionnez le rapport, et non la table ou le titre.
1. Dans le volet **Propriétés du rapport** , sous **Page** , développez **Marges** et remplacez-les par **0,75 pouce**.

    ![Définir les marges de page](media/report-builder-shared-datasets/power-bi-report-builder-page-margins.png)

1. Vous pouvez également rendre les colonnes plus étroites. Sélectionnez la bordure de la colonne et faites glisser le côté droit vers la gauche.

    ![Définir une largeur de colonne](media/report-builder-shared-datasets/power-bi-report-builder-column-width.png)

1. Une autre option consiste à s’assurer que les valeurs numériques sont correctement mises en forme. Sélectionnez une cellule avec une valeur numérique. 
    > [!TIP]
    > Vous pouvez mettre en forme plusieurs cellules à la fois en maintenant la touche Maj enfoncée tout en sélectionnant les autres cellules.

    ![Sélectionner plusieurs cellules](media/report-builder-shared-datasets/power-bi-report-builder-select-cells.png)

1. Sur le ruban **Accueil** , dans la section **Nombre** , remplacez le format **Par défaut** par un format numérique tel que **Devise**.

    ![Définir un format de nombre](media/report-builder-shared-datasets/power-bi-report-builder-number-format.png)

1. Remplacez le style **Espace réservé** par **Exemples de valeurs** pour afficher la mise en forme dans la cellule. 

    ![Afficher les exemples de valeurs](media/report-builder-shared-datasets/power-bi-report-builder-sample-values.png)

1. Le cas échéant, dans la section **Nombre** , diminuez les décimales pour économiser de l’espace.

### <a name="getting-rid-of-blank-pages"></a>Récupération des pages vides

Même si vous avez rendu les marges et les colonnes de table plus étroites, vous risquez de vous retrouver avec des pages vierges. Pourquoi ? C’est mathématique. 

Lorsque vous ajoutez les marges de page que vous définissez, en plus de la largeur du *corps* du rapport, elle doit être inférieure à la largeur du format du rapport.

Par exemple, imaginons que votre rapport a un format 8,5 pouces x 11 pouces et que vous avez défini les marges latérales sur 0,75 pouce chacune. Les deux marges forment 1,5 pouce ensemble, de sorte que la largeur du corps doit être inférieure à 7 pouces.

1. Sélectionnez le bord droit de la surface de conception du rapport, puis faites-le glisser afin qu’il soit inférieur au nombre souhaité sur la règle. 

    > [!TIP]
    > Vous pouvez le définir de manière plus précise dans les propriétés du **corps**. Sous **Taille** , définissez la propriété **largeur**.

    ![Définir la taille du corps](media/report-builder-shared-datasets/power-bi-report-builder-body-size.png)

1. Sélectionnez **Exécuter** pour afficher un aperçu de votre rapport et vous assurer que vous avez bien éliminé les pages vides. Ce rapport ne contient désormais 26 pages, et non plus 54 comme au départ. Opération réussie.

    ![Imprimer aucune page vide](media/report-builder-shared-datasets/power-bi-report-builder-print-26-pgs.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations 

- Pour les jeux de données qui utilisent une connexion active à Analysis Services, vous pouvez vous connecter directement à l’aide de la connexion Analysis Services sous-jacente au lieu d’un jeu de données partagé.
- Les jeux de données avec des mentions Promues ou Certifiées apparaissent dans la liste des jeux de données disponibles, mais ils ne sont pas marqués comme tels. 
- Vous ne pouvez pas incorporer des rapports paginés basés sur des jeux de données partagés Power BI dans le scénario « App Owns Data ».

## <a name="next-steps"></a>Étapes suivantes

- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
