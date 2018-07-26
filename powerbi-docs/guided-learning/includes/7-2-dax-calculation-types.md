Vous pouvez créer deux calculs principaux à l’aide de DAX :

* **Colonnes calculées**
* **Mesures calculées**

Avant d’entrer dans les détails avec ces deux calculs, il est judicieux de bien comprendre la syntaxe DAX des tables et des colonnes que vous utiliserez lors de la création de **colonnes calculées** ou de **mesures calculées**.

## <a name="dax-table-and-column-name-syntax"></a>Syntaxe des noms de colonne et de table DAX
Lors de la création d’une colonne ou mesure, il est important de connaître le format général des noms de table DAX :

    'Table Name'[ColumnName]

Si le nom de la table comprend des espaces (comme indiqué ci-dessus), les guillemets simples de part et d’autre du nom de la table sont obligatoires. Si le nom de la table ne comprend pas d’espaces, vous pouvez omettre les guillemets simples. La syntaxe se présente alors comme suit :

    TableName[ColumnName]

L’illustration suivante représente une formule DAX créée dans Power BI :

![](media/7-2-dax-calculation-types/dax-calc-types_1.png)

Vous pouvez également omettre complètement le nom de la table et utiliser seulement le nom de colonne, mais cette pratique n’est pas adaptée pour l’écriture de fonctions claires (et donc ni pour l’écriture d’un code DAX clair). Les noms de colonnes doivent toujours inclure les crochets.

Il est recommandé de *toujours* procéder comme suit :

* Aucun espace dans les noms de table
* Inclusion systématique du nom de la table dans les formules (ne l’omettez pas, même si DAX le permet)

## <a name="creating-calculated-columns"></a>Créer des colonnes calculées
Les **colonnes calculées** s’avèrent utiles quand vous voulez segmenter ou filtrer la valeur ou si vous voulez un calcul pour chaque ligne de votre table.

Vous pouvez créer des colonnes calculées dans Power BI Desktop en sélectionnant **Nouvelle colonne** dans l’onglet **Modélisation**. Il est préférable d’être dans la vue **Données** (plutôt que dans la vue **Rapport** ou **Relations**) car vous pouvez voir la colonne créée, et **la barre de formule** est renseignée et prête pour votre formule DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_2a.png)

Une fois que vous appuyez sur le bouton **Nouvelle colonne**, la **barre de formule** est renseignée avec un nom de colonne de base (que vous modifiez en fonction de votre formule, bien sûr) et l’opérateur **=**, et la nouvelle colonne apparaît dans la grille de données, comme illustré dans l’image suivante.

![](media/7-2-dax-calculation-types/dax-calc-types_3.png)

Les éléments requis pour une colonne calculée sont les suivants :

* un nouveau nom de colonne ;
* au moins une fonction ou une expression.

Si vous référencez une table ou une colonne dans votre formule de colonne calculée, vous n’avez pas besoin de spécifier de ligne de la table : Power BI calcule la colonne pour la ligne actuelle et pour chaque calcul.

## <a name="creating-calculated-measures"></a>Créer des mesures calculées
Utilisez une **mesure calculée** quand vous calculez des pourcentages ou des taux ou quand vous avez besoin d’agrégations complexes. Pour créer une mesure à l’aide d’une formule DAX, sélectionnez le bouton **Nouvelle mesure** dans l’onglet **Modélisation**. Là encore, il est préférable d’être dans la vue **Données** de Power BI Desktop car elle comprend la **barre de formule** et facilite l’écriture de votre formule DAX.

![](media/7-2-dax-calculation-types/dax-calc-types_4.png)

Avec les **mesures**, une nouvelle icône de mesure portant le nom de la mesure s’affiche dans le volet **Champs**. La **barre de formule** est là aussi renseignée avec le nom de votre formule DAX (cette fois-ci, avec votre mesure).

![](media/7-2-dax-calculation-types/dax-calc-types_5.png)

Les éléments requis pour une mesure calculée sont identiques à ceux d’une colonne calculée :

* un nouveau nom de mesure ;
* au moins une fonction ou une expression.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax)
> 
> 

