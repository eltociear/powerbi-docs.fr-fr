Il existe une différence significative entre les langages de formule **DAX** et Excel : DAX vous permet de faire passer des *tables entières* entre expressions, plutôt que d’avoir à utiliser une seule valeur. Un effet très positif de cette différence est que DAX vous permet de filtrer les tables de ses expressions, puis de travailler avec l’ensemble filtré de valeurs.

![](media/7-6-dax-tables-and-filtering/dax-tables-filtering_1.png)

Avec DAX, vous pouvez créer des tables calculées entièrement nouvelles, puis les traiter comme n’importe quelle autre table, notamment créer des relations entre ces tables et d’autres tables de votre modèle de données.

## <a name="dax-table-functions"></a>Fonctions de table DAX
DAX possède un jeu complet de fonctions de **table**, notamment les éléments suivants :

* FILTER
* ALL
* VALUES
* DISTINCT
* RELATEDTABLE

Ces fonctions renvoient une table complète plutôt qu’une valeur. Généralement, vous utilisez les résultats d’une fonction de **table** dans une analyse approfondie dans le cadre d’une plus grande expression, plutôt que la table renvoyée. Il est important de noter que quand vous utilisez une fonction de table, les résultats héritent des relations de ses colonnes.

Vous pouvez combiner des fonctions de table dans votre expression, à condition que chaque fonction utilise une table et renvoie une table. Par exemple, considérez l’expression DAX suivante :

    FILTER (ALL (Table), Condition)

Cette expression place un filtre sur l’intégralité de la *table*, en ignorant tout contenu de filtre actuel.

La fonction DISTINCT retourne les valeurs distinctes d’une colonne qui sont également visibles dans le contexte actuel. Ainsi, dans l’exemple d’expression DAX ci-dessus, si vous utilisez la fonction **ALL** dans l’expression, les filtres sont ignorés, et si vous remplacez la fonction **ALL** par la fonction **DISTINCT**, les filtres sont observés.

## <a name="counting-values-with-dax"></a>Compter les valeurs avec DAX
Une question courante à laquelle les générateurs de rapports Power BI veulent répondre est la suivante :

* « Combien de valeurs ai-je pour cette colonne ? ».

Il est certes facile de répondre à cette question avec une table affichée devant vous, mais DAX l’aborde différemment, en particulier quand il existe une relation entre des tables.

Par exemple, Power BI et DAX incluent des valeurs dont les index croisés sont incorrects. Si la relation entrante est interrompue, DAX ajoute une nouvelle ligne à la table associée qui a des espaces dans chaque champ et lie cette nouvelle ligne à la ligne non indexée pour garantir l’intégrité référentielle. Si votre fonction inclut des lignes vides, comme c’est souvent le cas lors de l’utilisation de **ALL**, celles-ci sont alors incluses dans le nombre de valeurs renvoyées pour cette colonne.

Vous pouvez également créer des tables calculées entières à l’aide de fonctions DAX. Les tables calculées créées à l’aide de DAX requièrent un **NOM** et une fonction **TABLE**. Les tables calculées peuvent être utilisées comme n’importe quelle autre table, notamment en établissant des relations.

> Contenu vidéo fourni par [Alberto Ferrari, SQLBI](http://www.sqlbi.com/learning-dax/?utm_source=powerbi&utm_medium=marketing&utm_campaign=after-summit)
> 
> 

