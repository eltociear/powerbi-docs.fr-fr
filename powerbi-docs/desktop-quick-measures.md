---
title: Utiliser les mesures rapides pour effectuer des calculs courants et puissants
description: La fonctionnalité Mesures rapides fournit des formules DAX prêtes à l’emploi qui accélèrent l’exécution de calculs courants.
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/22/2019
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 4e5ea5e5fcbffb5c61434ecc26a90d80d1cd1736
ms.sourcegitcommit: 8e3d53cf971853c32eff4531d2d3cdb725a199af
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2020
ms.locfileid: "74415274"
---
# <a name="use-quick-measures-for-common-calculations"></a>Utiliser les mesures rapides pour effectuer des calculs courants
Les *Mesures rapides* permettent d’effectuer rapidement et facilement des calculs courants et puissants. Une mesure rapide exécute un ensemble de commandes DAX (Data Analysis Expressions) en arrière-plan, puis vous présente les résultats pour que vous puissiez les utiliser dans votre rapport. Vous n’avez pas à écrire les commandes DAX, car celles-ci sont créées automatiquement avec les informations que vous entrez dans la boîte de dialogue. Il existe de nombreuses catégories de calculs disponibles et différentes manières de modifier chacun d’entre eux selon vos besoins. Mieux encore, sans doute : vous pouvez voir la commande DAX exécutée par la mesure rapide, et ainsi vous lancer ou étendre vos propres connaissances concernant DAX.

## <a name="create-a-quick-measure"></a>Créer une mesure rapide

Pour créer une mesure rapide dans Power BI Desktop, cliquez avec le bouton droit ou sélectionnez les points de suspension **...** à côté d’un des éléments du volet **Champs**, puis sélectionnez **Nouvelle mesure rapide** dans le menu qui s’affiche. 

![Sélectionner Nouvelle mesure rapide](media/desktop-quick-measures/quick-measures_01.png)

Vous pouvez également cliquer avec le bouton droit ou sélectionner la flèche déroulante à côté d’une des valeurs de la zone **Valeurs** qui sont associées à un visuel existant, puis sélectionner **Nouvelle mesure rapide** dans le menu. 

Quand vous sélectionnez **Nouvelle mesure rapide**, la fenêtre **Mesures rapides** s’affiche, vous permettant de sélectionner le calcul souhaité et les champs à partir desquels exécuter le calcul. 

Sélectionnez le champ **Sélectionner un calcul** pour voir la liste complète des mesures rapides disponibles. 

![Calculs - Mesures rapides disponibles](media/desktop-quick-measures/quick-measures_04.png)

Voici les cinq catégories de calculs de mesures rapides :

* **Agréger par catégorie**
  * Moyenne par catégorie
  * Écart par catégorie
  * Maximum par catégorie
  * Minimum par catégorie
  * Moyenne pondérée par catégorie
* **Filtres**
  * Valeur filtrée
  * Différence par rapport à la valeur filtrée
  * Différence en pourcentage par rapport à la valeur filtrée
  * Ventes provenant des nouveaux clients
* **Time intelligence**
  * Cumul annuel jusqu’à ce jour
  * Cumul trimestriel jusqu’à ce jour
  * Cumul mensuel jusqu’à ce jour
  * Variation d’une année à l’autre
  * Variation d’un trimestre à l’autre
  * Variation d’un mois à l’autre
  * Moyenne mobile
* **Totaux**
  * Résultat cumulé
  * Total de la catégorie (filtres appliqués)
  * Total de la catégorie (filtres non appliqués)
* **Opérations mathématiques**
  * Addition
  * Soustraction
  * Multiplication
  * Division
  * Différence en pourcentage
  * Coefficient de corrélation
* **Texte**
  * Nombre d’étoiles
  * Liste concaténée de valeurs

Pour soumettre vos idées de nouvelles mesures rapides, de nouvelles formules DAX sous-jacentes ou autres, reportez-vous à la fin de cet article.

> [!NOTE]
> Lorsque vous utilisez des connexions actives SSAS (SQL Server Analysis Services), certaines mesures rapides sont disponibles. Power BI Desktop affiche uniquement les mesures rapides qui sont prises en charge par la version de SSAS à laquelle vous êtes connecté. Si une mesure rapide ne figure pas dans la liste malgré une connexion à une source de données active SSAS, cela signifie que la version SSAS à laquelle vous êtes connecté ne prend pas en charge les commandes DAX permettant d’implémenter ces mesures rapides.

Après avoir sélectionné les calculs et les champs souhaités pour votre mesure rapide, sélectionnez **OK**. La nouvelle mesure rapide s’affiche dans le volet **Champs** et la formule DAX sous-jacente s’affiche dans la barre de formule. 

## <a name="quick-measure-example"></a>Exemple de mesure rapide
Voyons à quoi ressemble une mesure rapide.

Le visuel de matrice suivant présente un tableau des ventes de différents produits. Il s’agit d’un tableau de base incluant le total des ventes pour chaque catégorie de produits.

![Visuel de matrice montrant le tableau des ventes](media/desktop-quick-measures/quick-measures_05.png)

Une fois le visuel de matrice sélectionné, sélectionnez la flèche déroulante à côté de **TotalSales** dans la zone **Valeurs**, puis sélectionnez **Nouvelle mesure rapide**. 

Dans la fenêtre **Mesures rapides**, sous **Calcul**, sélectionnez **Moyenne par catégorie**. 

Faites glisser le **Prix unitaire moyen** du volet **Champs** vers le champ **Valeur de base**. Laissez **Catégorie** dans le champ **Catégorie**, puis sélectionnez **OK**. 

![](media/desktop-quick-measures/quick-measures_06.png)

Quand vous sélectionnez **OK**, plusieurs événements intéressants se produisent.

![Nouvelle mesure rapide dans le visuel, la barre de formule et la liste Champs](media/desktop-quick-measures/quick-measures_07.png)

1. Le visuel de matrice contient une nouvelle colonne qui indique le calcul du **Prix unitaire moyen par catégorie**.
   
2. La formule DAX de la nouvelle mesure rapide s’affiche dans la barre de formule. Pour plus d’informations sur la formule DAX, consultez la [section suivante](#learn-dax-by-using-quick-measures).
   
3. La nouvelle mesure rapide est sélectionnée et mise en surbrillance dans le volet **Champs**. 

La nouvelle mesure rapide est disponible pour tous les visuels du rapport, et non uniquement pour le visuel qui lui est associé. L’image suivante montre un visuel d’histogramme rapide créé à l’aide du champ Nouvelle mesure rapide.

![Nouveau visuel de graphique à barres basé sur le champ Mesure rapide](media/desktop-quick-measures/quick-measures_09.png)

## <a name="learn-dax-by-using-quick-measures"></a>Découvrir DAX à l’aide des mesures rapides
L’un des grands avantages des mesures rapides est qu’elles montrent la formule DAX qui les implémente. Lorsque vous sélectionnez une mesure rapide dans le volet **Champs**, la **barre de formule** s’affiche avec la formule DAX que Power BI a créée pour implémenter la mesure.

![Formule de la mesure rapide dans la barre de formule](media/desktop-quick-measures/quick-measures_10.png)

La barre de formule affiche non seulement la formule à l’origine de la mesure, mais encore plus important, elle vous permet de savoir comment créer les formules DAX sous-jacentes des mesures rapides.

Imaginons que vous deviez effectuer un calcul de variation d’une année sur l’autre, mais que vous hésitiez sur la manière de structurer la formule DAX, ou ignoriez tout simplement par où commencer. Au lieu de vous arracher les cheveux, vous pouvez créer une mesure rapide à l’aide du calcul **Variation d’une année à l’autre** afin d’observer ce qui se passe dans votre visuel et comment la formule DAX fonctionne. Vous pouvez ensuite apporter des modifications directement à la formule DAX ou créer une mesure similaire répondant à vos besoins et à vos attentes. C’est comme si vous étiez assisté par un professeur qui répondrait immédiatement à vos questions en quelques clics. 

Vous pouvez toujours supprimer les mesures rapides de votre modèle si vous ne les aimez pas. C’est aussi simple que de sélectionner ou de cliquer avec le bouton droit sur les points de suspension **...** en regard de la mesure, puis de sélectionner **Supprimer**. Vous pouvez également renommer une mesure rapide de votre choix en sélectionnant **Renommer** dans le menu. 

![Supprimer ou renommer une mesure rapide](media/desktop-quick-measures/quick-measures_11.png)

## <a name="limitations-and-considerations"></a>Considérations et limitations
Gardez à l’esprit les considérations et les limitations suivantes.

- Vous pouvez utiliser les mesures rapides ajoutées au volet **Champs** avec n’importe quel visuel du rapport.
- Vous pouvez toujours voir la commande DAX associée à une mesure rapide en sélectionnant cette dernière dans la liste **Champs** et en regardant la formule dans la barre de formule.
- Les mesures rapides ne sont disponibles que si vous pouvez modifier le modèle. Ce n’est pas le cas si vous utilisez des connexions actives. Les connexions actives tabulaires SSAS sont prises en charge, comme nous l’avons vu précédemment.
- Vous ne pouvez pas créer des mesures rapides Time Intelligence lorsque vous travaillez en mode DirectQuery. Les fonctions DAX utilisées dans ces mesures rapides ont un impact sur les performances quand elles sont converties en instructions T-SQL pour être envoyées à votre source de données.

> [!IMPORTANT]
> Les instructions DAX des mesures rapides utilisent uniquement des virgules comme séparateurs d’arguments. Si votre version de Power BI Desktop est traduite dans une langue qui utilise la virgule comme séparateur décimal, les mesures rapides ne fonctionneront pas correctement.

### <a name="time-intelligence-and-quick-measures"></a>Time Intelligence et mesures rapides
Vous pouvez utiliser vos propres tables de dates personnalisées avec les mesures rapides Time Intelligence. Si vous utilisez un modèle tabulaire externe, vérifiez que la colonne de date principale de la table a été marquée en tant que table de dates lors de la création du modèle, comme décrit dans [Spécifier l’option Marquer en tant que table de dates en vue d’une utilisation de Time Intelligence](https://docs.microsoft.com/sql/analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular). Si vous importez votre propre table de dates, marquez-la en tant que table de dates, comme décrit dans [Définir et utiliser des tables de dates dans Power BI Desktop](desktop-date-tables.md).

### <a name="additional-information-and-examples"></a>Exemples et informations supplémentaires
Vous avez une idée de mesure rapide ? Great! Accédez à la page [Power BI Ideas](https://go.microsoft.com/fwlink/?linkid=842906) et envoyez-nous vos idées et vos formules DAX pour les mesures rapides que vous aimeriez voir dans Power BI Desktop. Nous verrons si nous pouvons les ajouter à la liste des mesures rapides dans une prochaine version.

