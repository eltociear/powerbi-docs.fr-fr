-- title: Mettre en forme et combiner des données dans Power BI Desktop description: Mettre en forme et combiner des données dans les services Power BI Desktop : powerbi documentationcenter: '' author: davidiseminger manager: kfile backup: '' editor: '' tags: '' qualityfocus: no qualitydate: ''

ms.service: powerbi ms.devlang: NA ms.topic: article ms.tgt_pltfrm: NA ms.workload: powerbi ms.date: 30/01/2018 ms.author: davidi

---
# <a name="shape-and-combine-data-in-power-bi-desktop"></a>Mettre en forme et combiner des données dans Power BI Desktop
Avec **Power BI Desktop**, vous pouvez vous connecter à différents types de sources de données, puis mettre en forme les données en fonction de vos besoins. *Mettre en forme* des données consiste à transformer les données, par exemple à renommer des colonnes ou des tables, à remplacer du texte par des nombres, à supprimer des lignes, à définir la première ligne comme en-têtes, etc. *Combiner* des données consiste à se connecter à plusieurs sources de données, à les mettre en forme en fonction des besoins, puis à les consolider dans une seule requête utile.

Ce document montre comment mettre en forme une requête à l’aide de Power BI Desktop, en mettant en lumière certaines des tâches les plus courantes. Pour plus d’informations sur la requête utilisée ici, notamment sur sa création de toutes pièces, consultez [Prise en main de Power BI Desktop](desktop-getting-started.md).

Il est utile de savoir que l’ **Éditeur de requête** dans Power BI Desktop propose un grand nombre de menus contextuels, en plus du ruban. La plupart des éléments que vous pouvez sélectionner dans la section **Transformer** du ruban est également disponible en cliquant avec le bouton droit sur un élément (par exemple, sur une colonne) et en choisissant une option dans le menu qui s’affiche.

## <a name="shape-data"></a>Mettre en forme les données
Quand vous mettez en forme des données dans l’Éditeur de requête, vous fournissez des instructions pas à pas (l’Éditeur de requête effectue cela pour vous) pour ajuster les données au fur et à mesure qu’elles sont chargées et présentées. La source de données d’origine n’est pas affectée. Seule cette vue particulière des données est ajustée ou *mise en forme*.

Les étapes que vous spécifiez (par exemple, renommer une table, transformer un type de données ou supprimer des colonnes) sont enregistrées par l’Éditeur de requête. Chaque fois que cette requête se connecte à la source de données, ces mêmes opérations sont effectuées afin que les données soient toujours mises en forme de la manière que vous spécifiez. Ce processus se produit chaque fois que vous utilisez la fonctionnalité Éditeur de requête dans Power BI Desktop ou pour toute personne qui utilise votre requête partagée, comme dans le service **Power BI**. Ces étapes sont capturées, de manière séquentielle, dans le volet **Paramètres d’une requête**, sous **Étapes appliquées**.

L’illustration suivante montre le volet **Paramètres d’une requête** pour une requête qui a été mise en forme. Nous passerons en revue chacune de ces étapes dans les paragraphes suivants.

![](media/desktop-shape-and-combine-data/shapecombine_querysettingsfinished.png)

Dans [Prise en main de Power BI Desktop](https://powerbi.uservoice.com/knowledgebase/articles/471664), nous avons récupéré des données sur la retraite en nous connectant à une source de données web ; nous allons à présent mettre en forme ces données en fonction de nos besoins.

Pour commencer, nous devons convertir les scores d’une colonne en nombres, car l’Éditeur de requête n’a pas automatiquement transformés les valeurs textuelles en nombres quand il a chargé la table. Pour cela, il suffit de cliquer avec le bouton droit sur l’en-tête de la colonne et de sélectionner **Modifier le type \> Nombre entier** pour les modifier. Pour sélectionner plusieurs colonnes, commencez par sélectionner une colonne, maintenez la touche **Maj**enfoncée pour sélectionner des colonnes adjacentes supplémentaires, puis cliquez avec le bouton droit sur un en-tête de colonne pour modifier toutes les colonnes sélectionnées. Vous pouvez également utiliser la touche **Ctrl** pour sélectionner des colonnes non adjacentes.

![](media/desktop-shape-and-combine-data/shapecombine_changetype.png)

Vous pouvez également *transformer* ces colonnes de texte pour les définir comme en-têtes à partir du ruban **Transformer** . Voici le ruban **Transformer** , avec une flèche pointant vers le bouton **Type de données** qui vous permet de modifier le type de données actuel.

![](media/desktop-shape-and-combine-data/queryoverview_transformribbonarrow.png)

Notez que dans **Paramètres d’une requête**, la section **Étapes appliquées** reflète toutes les étapes de mise en forme appliquées aux données. Pour supprimer une étape quelconque du processus de mise en forme, il suffit de sélectionner le **X** à gauche de l’étape. Dans l’image suivante, la section **Étapes appliquées** reflète les étapes effectuées jusqu’à présent : connexion au site web (**Source**) ; sélection de la table (**Navigation**) ; et, pendant le chargement de la table, conversion automatique, par l’Éditeur de requête, des colonnes de nombres du type de données *Texte* au type de données *Nombre entier* (**Type modifié**). Une colonne de classement n’a pas été automatiquement convertie en type numérique, et nous allons découvrir pourquoi dans les prochains paragraphes.

![](media/desktop-shape-and-combine-data/shapecombine_appliedstepsearly.png)

Avant d’utiliser cette requête, nous devons apporter quelques modifications pour réorganiser ses données :

* *Supprimez la première colonne* : nous n’en avons pas besoin. Elle inclut uniquement des lignes redondantes qui invitent l’utilisateur à découvrir le classement de son État en matière de retraite, ce qui découle directement du fait qu’il s’agit d’une table basée sur le web
* *Corrigez certaines erreurs* : l’une des colonnes, **Health care quality**, contient quelques égalités (« ties ») dans les classements des États, qui font écho à la mention *(tie)* présente après les nombres correspondants récupérés du site web. Bien que ces informations soient exploitables sur le site web, nous devons transformer manuellement la colonne de texte en données. Cette correction, facile à effectuer à l’aide de Power BI Desktop, fait appel à une fonction pratique de la section **Étapes appliquées** de l’Éditeur de requête.
* *Modifiez le nom de la table* : le nom **Table 0** n’est pas un descripteur utile, mais il est facile de le modifier.

Pour supprimer la première colonne, sélectionnez-la, cliquez sur l’onglet **Accueil** du ruban, puis cliquez sur **Supprimer les colonnes** , comme indiqué dans l’illustration suivante.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumnsretirement.png)

Ensuite, nous devons résoudre la colonne de texte et la transformer en nombres. À première vue, une simple modification du type de la colonne **Health care quality** de texte en nombre (par exemple, *Nombre entier* ou *Nombre décimal* ) semble suffire. Mais quand nous remplaçons le type **Texte** par le type **Nombre entier**, nous constatons que l’Éditeur de requête signale quelques erreurs parmi les valeurs de la colonne.

![](media/desktop-shape-and-combine-data/shapecombine_error.png)

Il existe plusieurs façons d’obtenir des informations sur chaque erreur. Vous pouvez sélectionner la cellule (sans cliquer sur le mot **Erreur**) ou cliquer sur le mot **Erreur** directement. Si vous sélectionnez la cellule *sans* cliquer directement sur le mot **Erreur**, l’Éditeur de requête affiche les informations sur l’erreur en bas de la fenêtre.

![](media/desktop-shape-and-combine-data/shapecombine_errorinfo.png)

Si vous cliquez sur le mot *Erreur* directement, l’Éditeur de requête crée une **étape appliquée** dans le volet **Paramètres d’une requête** et affiche des informations sur l’erreur.

![](media/desktop-shape-and-combine-data/shapecombine_errorselect.png)

Pour revenir à l’Éditeur de requête, vous devez supprimer cette étape en sélectionnant le **X** en regard de celle-ci.

Quand nous sélectionnons l’ **étape appliquée**la plus récente, l’erreur qui vient d’être décrite s’affiche, comme l’illustre l’image suivante.

![](media/desktop-shape-and-combine-data/shapecombine_querystep1.png)

Étant donné que l’Éditeur de requête enregistre les étapes séquentiellement, nous pouvons, dans **Étapes appliquées**, sélectionner l’étape qui précède le changement de type pour voir qu’elle était la valeur de cette cellule avant la transformation, comme l’illustre l’image suivante.

![](media/desktop-shape-and-combine-data/shapecombine_querystep2.png)

Bien, maintenant nous pouvons corriger ces valeurs, *puis* modifier le type. Étant donné que l’Éditeur de requête enregistre les étapes de manière séquentielle, mais indépendamment les unes des autres, vous pouvez déplacer chaque **étape appliquée** vers le haut ou vers le bas dans la séquence. Cliquez simplement avec le bouton droit sur n’importe quelle étape. L’Éditeur de requête vous propose alors un menu comportant les options suivantes : **Renommer**, **Supprimer**, **Supprimer****jusqu’à la fin** (supprimer l’étape actuelle, ainsi que toutes les étapes suivantes), **Monter** ou **Descendre**.

![](media/desktop-shape-and-combine-data/shapecombine_querystepreorder.png)

En outre, vous pouvez sélectionner n’importe quelle **étape appliquée** dans la liste et poursuivre la mise en forme des données à ce stade de la séquence. L’Éditeur de requête insère automatiquement une nouvelle étape après l’ **tape appliquée**actuellement sélectionnée. Faisons un essai.

Tout d’abord, sélectionnez l’ **étape appliquée** qui précède le changement du type de la colonne **Health care quality** . Ensuite, supprimez le texte « (tie) » de la cellule afin qu’elle ne contienne que le nombre. Cliquez avec le bouton droit sur la cellule qui contient « 35 (tie) » et sélectionnez *Remplacer les valeurs* dans le menu qui s’affiche. Comme vous pouvez le constater, l’ **étape appliquée** actuellement sélectionnée est l’étape qui précède le changement de type.

![](media/desktop-shape-and-combine-data/shapecombine_replacevalues.png)

Étant donné que nous allons insérer une étape, l’Éditeur de requête nous avertit que cette opération risque de provoquer une rupture de la requête. Nous devons être prudents et attentifs ! Dans la mesure où nous suivons un didacticiel qui montre comment créer, supprimer, insérer et réorganiser des étapes de façon conviviale grâce à l’Éditeur de requête, nous sélectionnons naturellement **Insérer**.

![](media/desktop-shape-and-combine-data/shapecombine_insertstep.png)

Il existe trois mentions « ties », chacune d’elles devant faire l’objet d’un remplacement de valeur. Quand vous créez une étape appliquée, l’Éditeur de requête lui attribue un nom basé sur l’action effectuée, en l’occurrence **Valeur remplacée**. Quand plusieurs étapes portent le même nom dans votre requête, l’Éditeur de requête ajoute un numéro séquentiel à chaque **étape appliquée** pour les différencier.

L’écran suivant montre les trois étapes **Valeur remplacée** dans **Paramètres d’une requête**, mais ce n’est pas tout : puisque nous avons supprimé chaque instance du texte « (tie) » de la colonne **Health care quality** , l’étape **Type modifié** s’exécute désormais *sans erreurs*.

![](media/desktop-shape-and-combine-data/shapecombine_replacedvaluesok.png)

> [!NOTE]
> Vous pouvez également utiliser la commande **Supprimer les erreurs** (depuis le ruban ou le menu contextuel), qui supprime toutes les lignes contenant des erreurs. Dans notre cas, cette opération aurait consisté à supprimer tous les États comportant la mention « *(tie)* » dans nos données, ce que nous n’avons pas fait, car tous les États nous intéressent et nous souhaitons les conserver dans la table.

Cet exemple est certes un peu complexe, mais il illustre bien la puissance et la polyvalence de l’Éditeur de requête.

Enfin, nous voulons modifier le nom de cette table par quelque chose de plus explicite. Au moment de créer des rapports, il est particulièrement utile d’avoir des noms de table descriptifs, notamment si nous nous connectons à plusieurs sources de données qui sont toutes répertoriées dans le volet **Champs** de la vue **Rapport** .

Il est facile de modifier le nom d’une table : dans le volet **Paramètres d’une requête** , sous **Propriétés**, tapez simplement le nouveau nom de la table, comme l’illustre l’image suivante, et appuyez sur **Entrée**. Appelons cette table *RetirementStats*.

![](media/desktop-shape-and-combine-data/shapecombine_renametable.png)

Bien, nous avons mis en forme ces données comme nous le souhaitions. À présent, connectons-nous à une autre source de données et combinons des données.

## <a name="combine-data"></a>Combiner des données
Les données relatives aux différents États sont intéressantes et peuvent être utiles pour la création de requêtes et d’efforts d’analyse supplémentaires. Toutefois, elles posent un problème : la plupart de ces données utilisent une abréviation à deux lettres pour les codes d’États, à la place du nom complet de l’État. Nous avons besoin d’un moyen d’associer les noms des États à leurs abréviations.

Par chance, il existe une autre source de données publiques qui a précisément cette fonction, mais un effort important de mise en forme sera nécessaire pour la connecter à la table relative à la retraite. Voici la ressource web dédiée aux abréviations des États :

<http://en.wikipedia.org/wiki/List_of_U.S._state_abbreviations>

Dans le ruban **Accueil** de l’Éditeur de requête, sélectionnez **Nouvelle source \> Web**, tapez l’adresse, puis sélectionnez OK. Le navigateur affiche alors ce qu’il a trouvé dans cette page web.

 ![](media/desktop-shape-and-combine-data/designer_gsg_usstateabbreviationsnavigator.png)

Sélectionnez **Table[edit]** , car cette table inclut les données que nous souhaitons, mais un gros effort de mise en forme est nécessaire pour alléger les données de cette table en fonction de nos besoins.

> [!TIP]
> Existe-t-il un moyen plus rapide ou plus facile d’effectuer les étapes suivantes ? Oui, il est possible de créer une *relation* entre les deux tables et de mettre en forme les données en fonction de cette relation. Les étapes suivantes restent importantes pour apprendre à travailler avec des tables. Sachez que les relations peuvent vous aider à rapidement utiliser les données provenant de plusieurs tables.
> 
> 

Pour mettre ces données en forme, procédez comme suit :

* Supprimez les deux lignes du haut : elles résultent de la façon dont la table de cette page web a été créée et nous n’en avons pas besoin. Sous l’onglet **Accueil** du ruban, sélectionnez **Réduire les lignes \>Supprimer les lignes \>Supprimer les lignes du haut**.

![](media/desktop-shape-and-combine-data/shapecombine_removetoprows.png)

La fenêtre **Supprimer les lignes du haut** s’affiche, dans laquelle vous pouvez spécifier le nombre de lignes à supprimer.

* Supprimez les 26 lignes du bas : elles concernent les territoires, que nous n’avons pas besoin d’inclure. Sous l’onglet **Accueil**du ruban, sélectionnez **Réduire les lignes \> Supprimer les lignes \> Supprimer les lignes du bas**.

![](media/desktop-shape-and-combine-data/shapecombine_removebottomrows.png)

* La table RetirementStats ne contenant pas d’informations pour Washington DC, nous devons la filtrer de notre liste. Sélectionnez la flèche déroulante en regard de la colonne Region Status (État de la région), puis désactivez la case à cocher en regard de **Federal district**(District fédéral).

![](media/desktop-shape-and-combine-data/shapecombine_filterdc.png)

* Supprimez quelques colonnes inutiles : nous avons besoin uniquement du mappage des États avec leurs abréviations à deux lettres officielles, si bien que vous pouvez supprimer les autres colonnes : **Column2**, **Column3**, puis **Column5** à **Column10**. Tout d’abord, sélectionnez Column2, puis maintenez la touche **Ctrl** enfoncée pour sélectionner les autres colonnes à supprimer (vous pouvez ainsi sélectionner plusieurs colonnes non contiguës). Sous l’onglet Accueil du ruban, sélectionnez **Supprimer les colonnes \> Supprimer les colonnes**.

![](media/desktop-shape-and-combine-data/shapecombine_removecolumns.png)

* Utilisez la première ligne comme en-têtes : comme vous avez supprimé les trois lignes du haut, la ligne actuellement en haut représente l’en-tête que nous voulons. Vous pouvez sélectionner **Use First Row As Headers** (Utiliser la première ligne pour les en-têtes) sous l’onglet **Home** (Accueil) ou sous l’onglet **Transform** (Transformer) du ruban.

![](media/desktop-shape-and-combine-data/shapecombine_usefirstrowasheaders.png)

>[!NOTE]
>Il est maintenant judicieux de souligner que la *séquence* des étapes appliquées dans l’Éditeur de requête est importante et peut affecter la manière dont les données sont mises en forme. Il est également important de savoir comment une étape peut avoir un impact sur une étape ultérieure. Si vous supprimez une étape de la section Étapes appliquées, les étapes suivantes peuvent ne pas se comporter comme prévu initialement, en raison de l’impact de la séquence des étapes de la requête.

>[!NOTE]
>Quand vous redimensionnez la fenêtre Éditeur de requête pour réduire sa largeur, certains éléments du ruban sont condensés pour tirer le meilleur parti de l’espace visible. Quand vous augmentez la largeur de la fenêtre Éditeur de requête, les éléments de ruban sont développés pour exploiter pleinement la zone agrandie du ruban.

* Renommez les colonnes, ainsi que la table ; comme d’habitude, il existe plusieurs façons de renommer une colonne : sélectionnez la colonne, puis cliquez sur **Rename** (Renommer) sous l’onglet **Transform** (Transformer) du ruban, ou cliquez avec le bouton droit, puis choisissez **Rename...** (Renommer...) dans le menu qui s’affiche. Dans l’image suivante, les flèches indiquent les deux options ; vous ne devez en choisir qu’une seule.

![](media/desktop-shape-and-combine-data/shapecombine_rename.png)

Nous allons les renommer *State Name* et *State Code*. Pour renommer la table, tapez simplement le nom dans la zone **Nom** du volet **Paramètres d’une requête** . Appelons cette table *StateCodes*.

Comme la table StateCodes présente désormais la forme qui nous convient, nous pouvons combiner ces deux tables ou requêtes en une seule. Étant donné que les tables dont nous disposons maintenant sont le résultat des requêtes que vous avez appliquées aux données, elles sont souvent appelées *requêtes*.

Il existe deux façons principales de combiner des requêtes : par *fusion* et par *ajout*.

Pour ajouter une ou plusieurs colonnes à une autre requête, vous **fusionnez** les requêtes. Pour ajouter des lignes de données à une requête existante, vous **ajoutez** la requête.

Dans le cas présent, nous souhaitons fusionner les requêtes. Pour commencer, dans le volet gauche de l’Éditeur de requête, sélectionnez la requête *dans laquelle* nous voulons que l’autre requête fusionne, dans ce cas *RetirementStats*. Ensuite, sélectionnez **Combine\>Merge Queries**(Combiner > Fusionner les requêtes) sous l’onglet **Home**(Accueil) du ruban.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeries.png)

Vous êtes invité à définir les niveaux de confidentialité pour vous assurer que les données sont combinées sans inclure ou transférer des données que vous ne voulez pas transférer.

![](media/desktop-shape-and-combine-data/shapecombine_mergequeriesb.png)

La fenêtre **Fusionner** apparaît ensuite. Celle-ci vous invite à sélectionner la table à fusionner dans la table déjà sélectionnée, puis les colonnes correspondantes à utiliser pour la fusion. Sélectionnez State dans la table (requête) *RetirementStats* , puis sélectionnez la requête *StateCodes* (opération simple ici, car il existe une seule autre requête, alors que quand vous vous connectez à de nombreuses sources de données, vous avez le choix entre de nombreuses requêtes). Quand vous sélectionnez les colonnes correspondantes appropriées ( **State** dans *RetirementStats* et **State Name** dans *StateCodes* ), la fenêtre **Fusionner** ressemble à l’illustration ci-dessous et le bouton **OK** est activé.

![](media/desktop-shape-and-combine-data/shapecombine_merge.png)

Une colonne ( **NewColumn** ) est créée à la fin de la requête, qui correspond au contenu de la table (requête) qui a été fusionnée avec la requête existante. Toutes les colonnes de la requête fusionnée sont condensées dans la colonne **NewColumn**, mais vous pouvez choisir de **développer** la table et d’inclure les colonnes de votre choix.

![](media/desktop-shape-and-combine-data/shapecombine_mergenewcolumn.png)

Pour développer la table fusionnée et sélectionner les colonnes à inclure, sélectionnez l’icône de développement (![Développer](media/desktop-shape-and-combine-data/icon.png)). La fenêtre **Développer** apparaît.

![](media/desktop-shape-and-combine-data/shapecombine_mergeexpand.png)

Dans le cas présent, comme nous voulons uniquement la colonne **State Code**, sélectionnez cette colonne, puis cliquez sur **OK**. Décochez la case Utiliser le nom de la colonne d’origine comme préfixe, car cette opération ne présente ici aucun intérêt. Si vous conservez cette option, la colonne fusionnée sera nommée **NewColumn.State Code** (nom de la colonne d’origine, ou **NewColumn**, suivi d’un point et du nom de la colonne insérée dans la requête).

>[!NOTE]
>Vous souhaitez explorer d’autres manières d’insérer la table **NewColumn** ? Vous pouvez faire des essais et si les résultats ne vous satisfont pas, supprimez simplement cette étape de la liste **Étapes appliquées** dans le volet **Paramètres d’une requête**. Votre requête retourne à l’état précédant l’application de l’étape **Développer**. Vous pouvez ainsi faire autant d’expérimentation que vous le souhaitez, jusqu’à ce que le processus de développement vous satisfasse.

Vous disposez à présent d’une requête (table) unique associant deux sources de données, dont chacune a été mise en forme pour répondre à nos besoins. Cette requête peut servir de base pour un grand nombre d’autres connexions de données intéressantes, telles que des statistiques de coût du logement, des données démographiques ou des opportunités de travail dans un État.

Pour appliquer les modifications et fermer l’Éditeur de requête, sélectionnez Fermer et Appliquer sous l’onglet **Accueil** du ruban. Le jeu de données transformé s’affiche dans Power BI Desktop, prêt à l’usage pour la création de rapports.

![](media/desktop-shape-and-combine-data/shapecombine_closeandapply.png)

## <a name="next-steps"></a>Étapes suivantes
Power BI Desktop vous permet d’effectuer des tâches très diverses. Pour plus d’informations sur ses fonctionnalités, passez en revue les ressources suivantes :

* [Prise en main de Power BI Desktop](desktop-getting-started.md)
* [Présentation des requêtes dans Power BI Desktop](desktop-query-overview.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Se connecter aux données dans Power BI Desktop](desktop-connect-to-data.md)
* [Tâches courantes relatives aux requêtes dans Power BI Desktop](desktop-common-query-tasks.md)   

