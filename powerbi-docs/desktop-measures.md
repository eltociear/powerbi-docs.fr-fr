---
title: Utiliser des mesures dans Power BI Desktop
description: Mesures dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 3246f13291b3dd46f60db9403b1b69029c65a513
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="measures-in-power-bi-desktop"></a>Mesures dans Power BI Desktop
**Power BI Desktop** vous aide à créer des analyses de vos données en quelques clics seulement. Mais parfois, ces données n’incluent pas tout ce dont vous avez besoin pour répondre à certaines de vos questions les plus importantes. Les mesures peuvent vous y aider.

Les mesures sont utilisées dans certaines analyses de données les plus courantes. Par exemple, les sommes, les moyennes, les valeurs minimales ou maximales, les décomptes ou des calculs plus avancés que vous créez vous-même à l’aide d’une formule DAX. Les résultats calculés des mesures changent toujours en réponse à votre interaction avec vos rapports, favorisant ainsi l’exploration rapide et dynamique des données appropriées. Examinons cela de plus près.

## <a name="understanding-measures"></a>Présentation des mesures
Dans **Power BI Desktop**, les mesures sont créées et utilisées dans la **vue Rapport** ou dans la **vue Données**. Les mesures que vous créez vous-même apparaissent dans la liste Champs avec une icône de calculatrice. Vous pouvez nommer les mesures comme vous le souhaitez et les ajouter à une visualisation nouvelle ou existante comme tout autre champ.

![](media/desktop-measures/measuresinpbid_measinfieldlist.png)

> [!NOTE]
> Les **mesures rapides** peuvent également vous intéresser. Il s’agit de mesures prédéfinies que vous pouvez sélectionner à partir de boîtes de dialogue. C’est un bon moyen de créer rapidement des mesures et également d’apprendre la syntaxe DAX, car les formules DAX créées automatiquement sont disponibles pour révision. Consultez l’article : [Mesures rapides](desktop-quick-measures.md).
> 
> 

## <a name="data-analysis-expressions"></a>Langage DAX (Data Analysis Expressions)
Les mesures calculent un résultat à partir d’une formule d’expression. Vous utilisez le langage de formule DAX ([Data Analysis Expressions](https://msdn.microsoft.com/library/gg413422.aspx)) pour créer vos propres mesures. Le langage DAX inclut une bibliothèque de plus de 200 fonctions, opérateurs et constructions. Il offre ainsi une flexibilité considérable pour créer des mesures afin d’effectuer les calculs nécessaires pour quasiment tout type d’analyse de données.

Les formules DAX sont similaires aux formules Excel. DAX possède même de nombreuses fonctions identiques, telles que DATE, SUM et LEFT. Toutefois, les fonctions DAX sont censées fonctionner avec des données relationnelles, comme celles figurant dans Power BI Desktop.

## <a name="lets-look-at-an-example"></a>Examinons un exemple.
Diane est responsable des ventes chez Contoso. Elle a été chargée de fournir les prévisions de ventes des revendeurs au cours du prochain exercice. Elle décide de baser ses estimations sur les montants des ventes de l’année précédente, en appliquant une augmentation annuelle de 6 % résultant des diverses promotions planifiées au cours des six prochains mois.

Pour communiquer ces estimations, elle importe les données de ventes de l’année précédente dans Power BI Desktop. Elle trouve le champ SalesAmount dans la table Reseller Sales (Ventes des revendeurs). Comme les données qu’elle a importées contiennent uniquement les montants des ventes de l’année précédente, elle renomme le champ SalesAmount Last Years Sales (Ventes de l’année précédente). Ensuite, elle fait glisser le champ Last Years Sales sur le canevas du rapport. Il apparaît dans une visualisation de graphique en tant que valeur unique correspondant à la somme de toutes les ventes des revendeurs réalisées l’année précédente.

Elle remarque que même si elle n’a pas spécifié de calcul elle-même, un calcul a été fourni automatiquement. Power BI Desktop a créé sa propre mesure en cumulant toutes les valeurs du champ Last Years Sales.

Toutefois, Diane a besoin d’une mesure pour calculer les prévisions de ventes pour l’année à venir, qui sont basées sur les ventes de l’année précédente multipliées par 1,06 pour tenir compte de la hausse de 6 % attendue de l’activité. Pour ce calcul, elle crée sa propre mesure. Elle utilise la fonctionnalité Nouvelle mesure pour créer une nouvelle mesure, puis entre la formule DAX suivante :

    Projected Sales = SUM('Sales'[Last Years Sales])*1.06

Ensuite, Diane fait glisser sa nouvelle mesure Projected Sales (Ventes prévues) dans le graphique.

![](media/desktop-measures/measuresinpbid_lastyearsales.png)

Très rapidement et avec un minimum d’efforts, Diane a obtenu une mesure pour calculer les ventes prévues. Elle peut aller plus loin dans l’analyse de ses prévisions en filtrant sur des revendeurs spécifiques ou en ajoutant d’autres champs à son rapport.

## <a name="learn-more"></a>En savoir plus
Nous vous avons présenté ici une brève introduction aux mesures, mais de nombreuses informations complémentaire pourront vous aider à apprendre à créer vos propres mesures. Veillez à consulter le [Didacticiel : création de mesures personnalisées dans Power BI Desktop](desktop-tutorial-create-measures.md), où vous pourrez télécharger un exemple de fichier et bénéficier de leçons pas à pas sur la création de mesures supplémentaires.  

Pour approfondir un peu plus votre connaissance du langage DAX, veillez à consulter [Principes fondamentaux de DAX dans Power BI Desktop](desktop-quickstart-learn-dax-basics.md). La page [Informations de référence sur DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx) propose des articles détaillés sur chaque fonction, syntaxe, opérateur et convention d’affectation de noms. Le langage DAX est présent déjà depuis plusieurs années dans Power Pivot dans Excel et SQL Server Analysis Services, et de nombreuses autres ressources utiles sont disponibles. Veillez à consulter [DAX Resource Center Wiki](http://social.technet.microsoft.com/wiki/contents/articles/1088.dax-resource-center.aspx), où des membres influents de la communauté BI partagent leurs connaissances sur DAX.



