---
title: Utiliser les Mesures rapides pour effectuer facilement des calculs courants et puissants dans Power BI
description: La fonctionnalité Mesures rapides fournit des formules DAX prêtes à l’emploi qui accélèrent l’exécution de calculs courants
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: f8eb978aaacd345a29f2d9e2395fad419a651be0
ms.sourcegitcommit: 638de55f996d177063561b36d95c8c71ea7af3ed
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="use-quick-measures-to-easily-perform-common-and-powerful-calculations"></a>Utiliser les Mesures rapides pour effectuer facilement des calculs courants et puissants
Les **Mesures rapides** permettent d’effectuer rapidement et facilement des calculs courants et puissants. Une **mesure rapide** exécute un ensemble de commandes DAX (créées automatiquement) en arrière-plan en fonction des données entrées dans une boîte de dialogue, puis affiche les résultats, que vous pourrez utiliser dans votre rapport. Mieux encore, vous pouvez voir la commande DAX exécutée par la mesure rapide, et ainsi vous lancer ou développer vos propres connaissances concernant DAX.

![](media/desktop-quick-measures/quick-measures_01.png)

Pour créer des **mesures rapides**, double-cliquez sur un champ dans le puits **Champs**, puis sélectionnez **Mesures rapides** dans le menu qui s’affiche. Vous pouvez également cliquer avec le bouton droit sur toute valeur dans le volet **Valeurs** d’un visuel existant (par exemple, le champ *Valeurs* dans un visuel *Graphique à barres*). Il existe de nombreuses catégories de calculs disponibles et différentes manières de modifier chacun d’entre eux selon vos besoins.

### <a name="quick-measures-now-generally-available"></a>Mesures rapides désormais accessibles à tous

À partir de la version de février 2018 de **Power BI Desktop**, les mesures rapides sont accessibles à tous (et non plus en préversion). Si vous utilisez une version plus ancienne de **Power BI Desktop**, vous pouvez essayer la fonctionnalité **Mesures rapides** à partir de la version **d’avril 2017** de **Power BI Desktop** en sélectionnant **Fichier > Options et paramètres > Options > Fonctionnalités en préversion**, puis en cochant la case **Mesures rapides**.

![](media/desktop-quick-measures/quick-measures_02b.png)

Après avoir effectué la sélection, vous devez redémarrer **Power BI Desktop**.

## <a name="using-quick-measures"></a>Utilisation de la fonctionnalité Mesures rapides
Pour créer une **mesure rapide**, dans **Power BI Desktop** cliquez avec le bouton droit sur un champ (quelconque) dans le puits **Champs**, puis, dans le menu contextuel qui s’affiche, sélectionnez **Mesure rapide**.

![](media/desktop-quick-measures/quick-measures_01.png)

Lors de l’utilisation de connexions actives SSAS (SQL Server Analysis Services), certaines **mesures rapides** sont disponibles. **Power BI Desktop** affiche uniquement les **mesures rapides** prises en charge pour la version de SSAS à laquelle la connexion est établie. Par conséquent, si une certaine **mesure rapide** n’apparaît pas dans la liste malgré une connexion à une source de données active SSAS, cela signifie que la version SSAS utilisée ne prend pas en charge la mesure DAX permettant d’implémenter cette **mesure rapide**.

Une fois sélectionnée dans le menu contextuel, la fenêtre **Mesures rapides** suivante s’affiche : vous pouvez y sélectionner le calcul de votre choix, ainsi que les champs sur lesquels il devra s’exécuter.

![](media/desktop-quick-measures/quick-measures_03.png)

Lorsque vous sélectionnez le menu déroulant, la longue liste des **Mesures rapides** disponibles s’affiche.

![](media/desktop-quick-measures/quick-measures_04.png)

Il existe cinq groupes distincts de types de calculs de mesure rapide, chacun comprenant un ensemble spécifique de calculs. Ces groupes et calculs sont les suivants :

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
  * Ventes provenant des nouvelles catégories
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

Nous prévoyons d’ajouter des compléments à ces calculs. Nous aimerions donc que vous nous indiquiez de quelles **Mesures rapides** vous avez besoin, et que vous nous soumettiez vos éventuelles idées de **Mesures rapides** (y compris de formules DAX sous-jacentes). Vous trouverez davantage d’informations à ce sujet à la fin de cet article.

## <a name="example-of-quick-measures"></a>Exemple relatifs à la fonctionnalité Mesures rapides
Examinons un exemple de cette fonctionnalité **Mesures rapides** en action.

Le visuel **Matrice** suivant présente un tableaux des ventes de différents produits. Il s’agit d’un tableau de base incluant le total de chaque catégorie.

![](media/desktop-quick-measures/quick-measures_05.png)

Lorsque l’on clique avec le bouton droit sur le puits du champ **Valeurs** et que l’on sélectionne **Mesures rapides**, on peut sélectionner *Moyenne par catégorie* comme *Calcul* et *Somme de SalesAmount* comme *Valeur de base*, puis spécifier *SalesAmount* en faisant glisser ce champ de la zone *Champs* du volet droit vers la section *Catégorie* sur la gauche.

![](media/desktop-quick-measures/quick-measures_06.png)

Lorsque nous sélectionnons **OK**, nous observons que des comportements intéressants se produisent, comme illustré dans l’image suivant cette liste :

1. Le visuel **Matrice** comporte maintenant une nouvelle colonne qui affiche notre calcul, en l’occurrence, *SalesAmount moyen dans SalesAmount*.
2. Une nouvelle **mesure** a été créée, qui est disponible dans le puits **Champs** en évidence (Power BI l’entoure d’un cadre de couleur jaune). Cette mesure est disponible pour tout autre visuel dans le rapport, pas seulement pour celui pour lequel elle a été créée.
3. La formule DAX créée pour la **mesure rapide** s’affiche dans la barre de formule.

![](media/desktop-quick-measures/quick-measures_07.png)

Pour commencer par le premier élément, vous pouvez observer que la **mesure rapide** a été appliquée au visuel. Une nouvelle colonne et une valeur associée s’affichent, toutes deux basées sur la **mesure rapide** créée.

![](media/desktop-quick-measures/quick-measures_08.png)

Ensuite, la **mesure rapide** s’affiche dans le puits **Champs** du modèle de données, que vous pouvez utiliser comme tout autre champ du modèle, pour tout autre visuel. Dans l’image suivante, un visuel rapide de type **graphique à barres** a été généré à l’aide du champ créé par la **mesure rapide**.

![](media/desktop-quick-measures/quick-measures_09.png)

Passons à la section suivante pour discuter de ce troisième élément, à savoir celui des formules DAX.

## <a name="learn-dax-using-quick-measures"></a>Découvrir DAX à l’aide de la fonctionnalité Mesures rapides
Un autre avantage de la fonctionnalité **Mesures rapides** est qu’elle affiche directement la formule DAX créée pour implémenter la mesure. Dans l’image suivante, nous avons sélectionné la mesure créée par la **mesure rapide**. Comme elle figure à présent dans le puits **Champs**, il nous suffit de cliquer dessus. Lorsque nous procédons de la sorte, la **barre de formule** apparaît, affichant la formule DAX que Power BI a créée pour implémenter la mesure.

![](media/desktop-quick-measures/quick-measures_10.png)

Cela est intéressant en soi, puisque vous pouvez ainsi voir la formule sous-jacente à la mesure. Mais, et c’est peut-être plus important encore, cela vous permet d’utiliser la fonctionnalité **Mesures rapides** pour voir comment les formules DAX sous-jacentes doivent être créées.

Imaginons que vous devez effectuer un calcul de variation d’une année à l’autre mais que vous hésitez sur la manière de structurer la formule DAX, ou ignorez tout simplement par où commencer. Au lieu de vous arracher les cheveux, vous pouvez créer une **mesure rapide** à l’aide du calcul **Variation d’une année à l’autre** et observer ce qui se passe. Créez la **mesure rapide** pour voir comment elle apparaît dans votre visuel, observez le fonctionnement de la formule DAX, puis modifiez-la directement ou créez-en une autre jusqu’à ce que les calculs répondent à vos besoins ou à vos attentes.

C’est comme si vous étiez assisté par un professeur qui répondrait immédiatement à vos hypothèses en quelques clics. Si une mesure ne vous plaît pas, vous pouvez toujours l’écarter de votre modèle en cliquant dessus avec le bouton droit, puis en sélectionnant **Supprimer**.

![](media/desktop-quick-measures/quick-measures_11.png)

Dès que votre mesure est au point, vous pouvez la renommer à votre guise en utilisant le même menu contextuel.

## <a name="limitations-and-considerations"></a>Considérations et limitations
Gardez à l’esprit les considérations et les limitations suivantes.

* Les **mesures rapides** sont disponibles uniquement si le modèle est modifiable, ce qui n’est pas le cas lorsque vous utilisez certaines connexions actives (comme expliqué précédemment, les connexions actives tabulaires SSAS sont prises en charge).
* La mesure ajoutée au puits **Champs** peut être utilisée avec n’importe quel visuel inclus dans le rapport.
* Vous pouvez toujours voir la commande DAX associée à une **mesure rapide** en sélectionnant la mesure créée dans le puits **Champs**. La formule s’affiche alors dans la **barre de formule**.
* Vous ne pouvez pas créer des mesures rapides Time Intelligence lorsque vous travaillez en mode DirectQuery. Les fonctions DAX utilisées dans ces mesures rapides ont un impact sur les performances quand elles sont converties en instructions T-SQL pour être envoyées à votre source de données.

> [!WARNING]
> Les mesures rapides ne génèrent actuellement *que* des instructions DAX avec des virgules comme séparateurs d’arguments. Si votre version de **Power BI Desktop** est traduite dans une langue qui utilise la virgule comme séparateur décimal, les mesures rapides ne fonctionnent pas correctement.
> 
> 

### <a name="time-intelligence-and-quick-measures"></a>Time intelligence et Mesures rapides
Depuis la mise à jour d’octobre 2017 de **Power BI Desktop**, vous pouvez utiliser vos propres tables de dates personnalisées avec les **mesures rapides** Time Intelligence. Si vous utilisez un modèle tabulaire externe, vérifiez que lorsque le modèle a été créé, la colonne de date principale de cette table a été marquée en tant que table de dates, comme décrit dans [cet article](https://docs.microsoft.com/sql/analysis-services/tabular-models/specify-mark-as-date-table-for-use-with-time-intelligence-ssas-tabular). Si vous importez votre propre table de dates, marquez-la en tant que table de dates, comme décrit dans [cet article](https://docs.microsoft.com/power-bi/desktop-date-tables)

### <a name="additional-information-and-examples"></a>Exemples et informations supplémentaires
Nous prévoyons de fournir des exemples et des conseils pour chacun des calculs de la fonctionnalité **Mesures rapides**. Nous vous invitons par conséquent à consulter cet article de temps à autre afin de voir s’il contient des mises à jour.

Vous avez une idée de **mesure rapide** non encore disponible ? Excellent ! Visitez [cette page](https://go.microsoft.com/fwlink/?linkid=842906) et soumettez vos idées (et formules DAX) pour la **mesure rapide** que vous aimeriez voir dans **Power BI Desktop**. Nous envisagerons d’ajouter celle-ci à la liste fournie de **mesures rapides** dans une prochaine publication.

