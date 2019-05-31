---
title: Créer et gérer des relations dans Power BI Desktop
description: Créer et gérer des relations dans Power BI Desktop
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 04/19/2019
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: f2102ad654a056832f7890dc506acc99eb5ef26f
ms.sourcegitcommit: 60dad5aa0d85db790553e537bf8ac34ee3289ba3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/29/2019
ms.locfileid: "61312493"
---
# <a name="create-and-manage-relationships-in-power-bi-desktop"></a>Créer et gérer des relations dans Power BI Desktop
Quand vous importez plusieurs tables, vous êtes souvent amené à effectuer des analyses impliquant les données de ces tables. Les relations entre ces tables sont nécessaires pour obtenir des résultats précis et afficher les informations correctes dans vos rapports. Power BI Desktop facilite la création de ces relations. Dans la plupart des cas, vous n’avez rien à faire ; la fonctionnalité Détection automatique se charge de tout. Toutefois, dans certains cas, vous pouvez être amené à créer des relations vous-même ou à apporter des modifications à une relation. Dans les deux cas, il est important de comprendre le fonctionnement des relations dans Power BI Desktop et comment les créer et les modifier.

## <a name="autodetect-during-load"></a>Détection automatique pendant le chargement
Si vous interrogez plusieurs tables en même temps, lorsque les données sont chargées, Power BI Desktop tente de rechercher et créer des relations pour vous. Les propriétés Cardinalité, Direction du filtrage croisé et Active sont automatiquement définies. Power BI Desktop examine les noms des colonnes des tables que vous interrogez pour déterminer s’il existe des relations potentielles. S’il en existe, ces relations sont automatiquement créées. Si Power BI Desktop ne peut pas déterminer avec un niveau de confiance élevé, il existe une correspondance, il ne crée pas automatiquement la relation. Vous pouvez néanmoins utiliser la boîte de dialogue Gérer les relations pour créer ou modifier des relations.

## <a name="create-a-relationship-by-using-autodetect"></a>Créer une relation à l’aide de la fonctionnalité Détection automatique
Sous l’onglet **Accueil**, cliquez sur **Gérer les relations**\>**Détection automatique**.

![](media/desktop-create-and-manage-relationships/automaticrelationship.gif)

## <a name="create-a-relationship-manually"></a>Créer une relation manuellement
1. Sous l’onglet **Accueil**, cliquez sur **Gérer les relations**\>**Nouveau**.
2. Dans le **créer une relation** boîte de dialogue, dans la première liste déroulante de table, sélectionnez une table, puis sélectionnez la colonne que vous souhaitez utiliser dans la relation.
3. Dans la seconde liste déroulante de tables, sélectionnez la table voulue dans la relation, puis l’autre colonne que vous souhaitez utiliser, puis cliquez sur **OK**.

![](media/desktop-create-and-manage-relationships/manualrelationship2.gif)

Par défaut, Power BI Desktop configure automatiquement la cardinalité (direction), la direction du filtrage et propriétés Active pour votre nouvelle relation ; Toutefois, vous pouvez modifier les paramètres si nécessaire. Pour plus d’informations, consultez la section Présentation des options supplémentaires plus loin dans cet article.

Vous verrez une erreur indiquant que *une des colonnes doit avoir des valeurs uniques* si aucune des tables sélectionnées pour la relation a des valeurs uniques. Au moins une table dans une relation *doit* avoir une liste distincte et unique de valeurs de clés. C’est une exigence commune à toutes les technologies de base de données relationnelle. 

Si vous rencontrez cette erreur, vous pouvez la résoudre de différentes manières :

* Utilisez « Supprimer les lignes en doublon » pour créer une colonne avec des valeurs uniques. L’inconvénient de cette approche est que des informations sont perdues lors de la suppression des lignes en double, car souvent une clé (ligne) est dupliquée dans un but précis.
* Ajoutez une table intermédiaire composée de la liste des valeurs de clés distinctes dans le modèle, qui sera ensuite liée aux deux colonnes d’origine de la relation.

Pour plus d’informations, consultez le [billet de blog](https://blogs.technet.microsoft.com/cansql/2016/12/19/relationships-in-power-bi-fixing-one-of-the-columns-must-have-unique-values-error-message/).


## <a name="edit-a-relationship"></a>Modifier une relation
1. Sous l’onglet **Accueil**, cliquez sur **Gérer les relations**.
2. Dans la boîte de dialogue **Gérer les relations**, sélectionnez la relation, puis cliquez sur **Modifier**.

## <a name="configure-additional-options"></a>Configurer des options supplémentaires
Quand vous créez ou modifiez une relation, vous pouvez configurer des options supplémentaires. Par défaut, des options supplémentaires sont configurées automatiquement d’après une estimation, qui peut être différente pour chaque relation basée sur les données dans les colonnes.

## <a name="cardinality"></a>Cardinalité
**Plusieurs à un (\*: 1)** - le plus commun, type par défaut, ce qui signifie que la colonne dans une table peut avoir plusieurs instances d’une valeur et la table connexe, souvent connaître en tant que table de recherche, n'a qu’une seule instance d’une valeur.

**Un à un (1:1)** : la colonne dans une table n’a qu’une seule instance d’une valeur particulière, et la table connexe n’a qu’une seule instance d’une valeur particulière.

**Relations plusieurs à plusieurs** : Avec les modèles composites, vous pouvez établir des relations plusieurs-à-plusieurs entre des tables, ce qui supprime la configuration requise pour les valeurs uniques dans les tables. Les solutions de contournement précédentes, comme la présentation de nouvelles tables uniquement pour établir des relations, sont également supprimées. Pour plus d’informations, consultez [Relations avec une cardinalité plusieurs à plusieurs](https://docs.microsoft.com/power-bi/desktop-many-to-many-relationships). 

Pour plus d’informations sur la modification de la cardinalité, consultez la section Présentation des options supplémentaires plus loin dans cet article.

## <a name="cross-filter-direction"></a>Direction du filtrage croisé
**Les deux** - les plus courants, direction par défaut, ce qui signifie que pour le filtrage à des fins, les deux tables sont traitées comme s’ils faisaient une seule table. **Les deux** fonctionne bien avec une seule table qui a un nombre de tables de recherche qui l’entourent. Une table de valeurs de ventes réelles avec une table de choix pour le service constitue un bon exemple. On parle souvent de configuration de schéma en étoile (une table centrale avec plusieurs tables de choix.) Toutefois, si vous avez plusieurs tables qui possèdent aussi des tables de choix (certaines en commun), vous ne devez pas utiliser le paramètre À double sens. Pour continuer avec l’exemple précédent, vous avez également une table de ventes budgétées qui enregistre le budget cible pour chaque service. Et la table des services est connectée à la fois à la table des ventes et à la table du budget. Évitez le paramètre À double sens pour ce type de configuration.

**Seul** -options de filtrage dans les tables connectées agissent sur la table dans laquelle les valeurs sont agrégées. Si vous importez un modèle de données Power Pivot dans Excel 2013 ou version antérieure, toutes les relations ont une seule direction. 

Pour plus d’informations sur le changement de direction du filtrage croisé, consultez la section Présentation des options supplémentaires plus loin dans cet article.

## <a name="make-this-relationship-active"></a>Rendre cette relation active
Quand cette option est cochée, la relation fait office de relation par défaut active. S’il existe plusieurs relations entre deux tables, la relation active offre un moyen à Power BI Desktop de créer automatiquement des visualisations qui incluent les deux tables.

Pour plus d’informations sur la façon de rendre une relation active, consultez la section Présentation des options supplémentaires plus loin dans cet article.

## <a name="understanding-relationships"></a>Présentation des relations
Une fois que vous avez connecté deux tables avec une relation, vous pouvez utiliser les données des deux tables comme s’il s’agissait d’une table unique ; ainsi, vous n’avez pas à vous soucier des détails de la relation et vous n’avez pas besoin d’aplatir ces tables dans une table unique avant de les importer. Dans de nombreuses situations, Power BI Desktop peut créer automatiquement des relations à votre place. Toutefois, si Power BI Desktop ne peut pas déterminer avec un degré élevé de certitude qu’une relation entre deux tables doit exister, il ne crée pas automatiquement la relation. Dans ce cas, vous devez créer la relation. 

Passons en revue un didacticiel rapide, pour mieux illustrer le fonctionnement des relations dans Power BI Desktop.

>[!TIP]
>Vous pouvez effectuer cette leçon vous-même. Copiez la table HeuresProjet ci-dessous dans une feuille de calcul Excel, sélectionnez toutes les cellules, puis cliquez sur **Insertion**\>**Tableau**. Dans la boîte de dialogue **Créer un tableau**, cliquez sur **OK**. Dans **Nom du tableau**, tapez **HeuresProjet**. Faites de même pour la table ProjetEntreprise. Vous pouvez ensuite importer les données avec l’option **Obtenir des données** dans Power BI Desktop. Sélectionnez votre classeur et le tables comme source de données.

La première table, HeuresProjet, contient les tickets de travail qui enregistrent le nombre d’heures qu’une personne a travaillé sur un projet particulier. 

**HeuresProjet**

| **Ticket** | **SoumisPar** | **Heures** | **Projet** | **DateSoumission** |
| ---:|:--- | ---:|:--- | ---:|
| 1001 |Brewer, Alan |22 |Bleu |1/1/2013 |
| 1002 |Brewer, Alan |26 |Rouge |2/1/2013 |
| 1003 |Ito, Shu |34 |Jaune |12/4/2012 |
| 1004 |Brewer, Alan |13 |Orange |1/2/2012 |
| 1005 |Bowen, Eli |29 |Violet |10/1/2013 |
| 1006 |Bento, Nuno |35 |Vert |2/1/2013 |
| 1007 |Hamilton, David |10 |Jaune |10/1/2013 |
| 1008 |Han, Mu |28 |Orange |1/2/2012 |
| 1009 |Ito, Shu |22 |Violet |2/1/2013 |
| 1010 |Bowen, Eli |28 |Vert |10/1/2013 |
| 1011 |Bowen, Eli |9 |Bleu |10/15/2013 |

La seconde table, ProjetEntreprise, est une liste de projets affectés d’une priorité (A, B ou C). 

**ProjetEntreprise**

| **NomProjet** | **Priorité** |
| --- | --- |
| Bleu |A |
| Rouge |B |
| Vert |C |
| Jaune |C |
| Violet |B |
| Orange |C |

Notez que chaque table possède une colonne de projet. Chacune a un nom légèrement différent, mais les valeurs semblent identiques. Ce point est important, et nous y reviendrons dans bientôt.

Nos deux tables étant importées dans un modèle, nous allons maintenant créer un rapport. La première chose que nous voulons obtenir est le nombre d’heures soumises par priorité de projet ; nous sélectionnons donc les champs **Priorité** et **Heures**.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfiltersnorel.png)

Si nous regardons notre table dans le canevas de rapport, nous constatons que le nombre d’heures est **256,00** pour chaque projet et que c’est également le total. C’est clairement incorrect. Pourquoi ? Car nous ne pouvons pas calculer une somme de valeurs à partir d’une table (champ Heures de la table Projet), ventilées en fonction des valeurs d’une autre table (champ Priorité de la table ProjetEntreprise) sans qu’il existe une relation entre ces deux tables.

Nous allons donc créer une relation entre ces deux tables.

Vous vous souvenez de ces colonnes communes aux deux tables avec un nom de projet et comportant des valeurs similaires ? Nous allons utiliser ces deux colonnes pour créer une relation entre nos tables.

Pourquoi ces colonnes ? Si nous observons la colonne Projet du tableau HeuresProjet, nous y trouvons des valeurs telles que Bleu, Rouge, Jaune et Orange. Comme vous pouvez le constater, plusieurs lignes contiennent la même valeur. Nous avons donc de nombreuses valeurs de couleur pour Projet.

Par contre, la colonne NomProjet du tableau ProjetEntreprise ne contient qu’une occurrence de chaque valeur de couleur de projet. Chaque valeur de couleur de cette table est unique ; cela est important, car nous pouvons créer une relation entre les deux tables. Dans ce cas, il s’agit d’une relation plusieurs-à-un. Dans une relation plusieurs-à-un, au moins une colonne d’une des tables doit contenir des valeurs uniques. Il existe des options supplémentaires pour certaines relations, que nous verrons plus tard, mais pour l’instant nous allons créer une relation entre les colonnes Projet de chaque table.

### <a name="to-create-the-new-relationship"></a>Pour créer la relation
1. Cliquez sur **Gérer les relations**.
2. Dans **gérer les relations**, cliquez sur **New** pour ouvrir le **créer une relation** boîte de dialogue, dans laquelle nous pouvons sélectionner les tables, colonnes et tous les autres paramètres que nous souhaitons pour notre relation.
3. Dans la première table, sélectionnez **HeuresProjet**, puis la colonne **Projet**. Il s’agit du côté « plusieurs » de notre relation.
4. Dans la seconde table, sélectionnez **ProjetEntreprise**, puis la colonne **NomProjet**. Il s’agit du côté « un » de notre relation. 
5. Cliquez sur **OK** dans les boîtes de dialogue **Créer une relation** et **Gérer les relations**.

![](media/desktop-create-and-manage-relationships/candmrel_create_compproj.png)

Démonstration, vous venez de créer cette relation dépens. Vous pouvez cliquer simplement sur le bouton de la détection automatique dans la boîte de dialogue Gérer les relations. En fait, la fonctionnalité Détection automatique l’aurait déjà fait pour vous quand vous avez chargé les données si les deux colonnes avaient le même nom. Mais nous n’aurions eu aucun mérite.

À présent, réexaminons la table dans le Canevas de rapport.

 ![](media/desktop-create-and-manage-relationships/candmrel_reportfilterswithrel.png)

Ça va beaucoup mieux maintenant, non ?

Quand nous additionnons les heures par priorité, Power BI Desktop recherche chaque instance des valeurs de couleur uniques dans la table de recherche Projetentreprise, puis recherche chaque instance de chacune de ces valeurs dans la table Projetentreprise et calcule une somme totale pour chaque valeur unique .

C’était facile, en fait, avec détection automatique, vous pouvez même pas faire ce travail.

## <a name="understanding-additional-options"></a>Présentation des options supplémentaires
Lorsqu’une relation est créée, à détecter automatiquement ou manuellement, Power BI Desktop configure automatiquement les options supplémentaires en fonction des données dans vos tables. Vous pouvez configurer ces propriétés de relation supplémentaires situées tout en bas de la boîte de dialogue Créer/modifier une relation.

 ![](media/desktop-create-and-manage-relationships/candmrel_advancedoptions2.png)

Comme nous l’avons dit, ces propriétés sont généralement définies automatiquement et vous n’avez pas besoin d’y toucher ; toutefois, vous pouvez être amené à configurer ces options vous-même.

## <a name="automatic-relationship-updates"></a>Mises à jour automatique de relations

Vous pouvez gérer la façon dont Power BI traite et ajuste automatiquement les relations dans vos rapports et les modèles. Pour spécifier la façon dont Power BI gère les options de relations, sélectionnez **fichier > Options et paramètres > Options** à partir de Power BI Desktop, puis sélectionnez **chargement des données** dans le volet gauche. Vous voyez ensuite les options **relations**.

 ![Options de relations](media/desktop-create-and-manage-relationships/relationships-options-01.png)

Il existe trois options qui peuvent être sélectionnées et activées. 

La première option est *importer des relations à partir de sources de données*, et elle est sélectionnée par défaut. Lorsque sélectionné, Power BI vérifie pour les relations définies dans votre source de données, telle qu’une clé étrangère / principal dans votre entrepôt de données, les relations de clé. Si ces relations existent, elles sont mises en miroir dans le modèle de données Power BI, lorsque vous chargez initialement des données. Cette option vous permet rapidement commencer à travailler avec votre modèle, au lieu qu’il soit nécessaire de trouver ou de définir ces relations vous-même.

La deuxième option est *mise à jour ou supprimer des relations lors de l’actualisation des données*, et elle est désactivée par défaut. Si sélectionné (activé en cochant la case en regard de l’option), Power BI recherche des modifications dans les relations de source de données lorsque votre jeu de données est actualisé. Si ces relations modifiées ou sont supprimées, Power BI reflète ces modifications dans son propre modèle de données, la mise à jour ou les supprimer pour faire correspondre.

> [!WARNING]
> Si vous utilisez la sécurité au niveau des lignes qui s’appuie sur les relations définies, nous ne recommandons pas en sélectionnant la seconde option, *mise à jour ou supprimer des relations lors de l’actualisation des données*. Si une relation est supprimée que vos paramètres RLS s’appuient sur, votre modèle peut devenir moins sécurisé. 

La troisième option est *Autodetect nouvelles relations une fois les données sont chargées*, qui est décrite dans le [détection automatique pendant le chargement](#autodetect-during-load) section, située plus haut dans cet article. 


## <a name="future-updates-to-the-data-require-a-different-cardinality"></a>Les futures mises à jour des données nécessitent une cardinalité différente
Normalement, Power BI Desktop peut déterminer automatiquement la meilleure cardinalité pour la relation. Si vous avez besoin de remplacer le paramétrage automatique car vous savez que les données changeront ultérieurement, vous pouvez utiliser le contrôle Cardinalité. Examinons un exemple où nous devons sélectionner une cardinalité différente.

La table PrioritéProjetEntreprise ci-dessous répertorie tous les projets de l’entreprise et leur priorité. La table BudgetProjet regroupe les projets pour lesquels un budget a été approuvé.

**BudgetProjet**

| **ProjetsApprouvés** | **AllocationBudget** | **DateAllocation** |
|:--- | ---:| ---:|
| Bleu |40,000 |12/1/2012 |
| Rouge |100,000 |12/1/2012 |
| Vert |50,000 |12/1/2012 |

**PrioritéProjetEntreprise**

| **Projet** | **Priorité** |
| --- | --- |
| Bleu |A |
| Rouge |B |
| Vert |C |
| Jaune |C |
| Violet |B |
| Orange |C |

Si nous créons une relation entre la colonne Projet de la table PrioritéProjetEntreprise et la colonne ProjetsApprouvés de la table BudgetProjet, comme suit :

 ![](media/desktop-create-and-manage-relationships/candmrel_create_compproj_appproj2.png)

La cardinalité prend automatiquement la valeur Un à un (1:1) et la direction du filtrage croisé la valeur À double sens (comme indiqué). En effet, pour Power BI Desktop, la meilleure combinaison des deux tables ressemble à ceci :

| **Projet** | **Priorité** | **AllocationBudget** | **DateAllocation** |
|:--- | --- | ---:| ---:|
| Bleu |A |40,000 |12/1/2012 |
| Rouge |B |100,000 |12/1/2012 |
| Vert |C |50,000 |12/1/2012 |
| Jaune |C |<br /> |<br /> |
| Violet |B |<br /> |<br /> |
| Orange |C |<br /> |<br /> |

Il existe une relation un à un entre nos deux tables, car la colonne Projet de la table combinée ne contient pas de doublons. La colonne Projet est unique, car chaque valeur n’y apparaît qu’une seule fois. Ainsi, les lignes des deux tables peuvent être combinées directement sans aucune duplication.

Toutefois, supposons que les données sont censées changer à la prochaine actualisation. Une version actualisée de la table BudgetProjet fait apparaître des lignes supplémentaires pour les valeurs Bleu et Rouge :

**BudgetProjet**

| **ProjetsApprouvés** | **AllocationBudget** | **DateAllocation** |
| --- | ---:| ---:|
| Bleu |40,000 |12/1/2012 |
| Rouge |100,000 |12/1/2012 |
| Vert |50,000 |12/1/2012 |
| Bleu |80,000 |6/1/2013 |
| Rouge |90,000 |6/1/2013 |

 Cela signifie que la meilleure combinaison des deux tables ressemble maintenant à ceci : 

| **Projet** | **Priorité** | **AllocationBudget** | **DateAllocation** |
| --- | --- | ---:| ---:|
| Bleu |A |40,000 |12/1/2012 |
| Rouge |B |100,000 |12/1/2012 |
| Vert |C |50,000 |12/1/2012 |
| Jaune |C |<br /> |<br /> |
| Violet |B |<br /> |<br /> |
| Orange |C |<br /> |<br /> |
| Bleu |A |80000 |6/1/2013 |
| Rouge |B |90000 |6/1/2013 |

Dans cette nouvelle table combinée, la colonne Projet contient des doublons. Les deux tables d’origine n’auront pas de relation un à un une fois la table actualisée. Dans ce cas, comme nous savons que ces mises à jour ultérieures engendreront des doublons dans la colonne Projet, nous souhaitons définir la cardinalité sur Plusieurs à un (\*:1), avec la composante « plusieurs » côté BudgetProjet et la composante « un » côté PrioritéProjetEntreprise.

## <a name="adjusting-cross-filter-direction-for-a-complex-set-of-tables-and-relationships"></a>Ajustement de la direction du filtrage croisé pour un jeu complexe de tables et de relations
Pour la plupart des relations, la direction du filtrage croisé est définie sur « À double sens ». Toutefois, dans certaines circonstances plus rares, vous pouvez être amené à la définir différemment, comme dans le cas où vous importez un modèle à partir d’une ancienne version de Power Pivot, où chaque relation est définie sur une direction à sens unique. 

Le paramètre À double sens permet à Power BI Desktop de traiter tous les aspects des tables connectées comme s’il s’agissait d’une table unique. Dans certaines situations, toutefois, Power BI Desktop ne peut pas définir la direction du filtrage croisé d’une relation sur « À double sens » tout en conservant un ensemble non ambigu de valeurs par défaut pour la création de rapports. En règle générale, la direction du filtrage croisé d’une relation n’est pas définie sur À double sens si cela risque de créer une ambiguïté. Si la valeur par défaut de la direction du filtrage croisé ne fonctionne pas, essayez de la définir sur une table particulière ou sur À double sens.

Le filtrage croisé À sens unique fonctionne dans de nombreuses situations. En fait, si vous importez un modèle de données Power Pivot dans Excel 2013 ou version antérieure, toutes les relations sont définies sur À sens unique. Dans le cas d’une direction à sens unique, les choix de filtrage dans les tables connectées agissent sur la table où se produit l’agrégation. Parfois, le filtrage croisé peut être un peu difficile à comprendre. Nous allons donc étudier un exemple.

 ![](media/desktop-create-and-manage-relationships/candmrel_singledircrossfiltering.png)

Dans le cas du filtrage croisé à sens unique, si vous créez un rapport qui récapitule les heures de projet, vous pouvez choisir de récapituler (ou filtrer) par ProjetEntreprise, Priorité ou EmployéEntreprise, Ville. Si toutefois vous souhaitez obtenir le nombre d’employés par projet (ce qui est moins fréquent), cela ne fonctionne pas. Vous obtenez une colonne de valeurs identiques. Dans l’exemple ci-dessous, la direction du filtrage croisé des deux relations est définie sur une direction à sens unique, en l’occurrence vers la table HeuresProjet :

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfiltersingle.png)

Spécification de filtre de flux de Projetentreprise à Employéentreprise (comme indiqué dans l’image ci-dessous), mais il ne sera pas transmis jusqu'à Employéentreprise. Toutefois, si vous définissez la direction du filtrage croisé sur À double sens, l’opération fonctionne. Le paramètre À double sens permet d’étendre la spécification du filtrage à Employé.

 ![](media/desktop-create-and-manage-relationships/candmrel_bidircrossfiltering.png)

Avec la direction du filtrage croisé définie sur À double sens, notre rapport semble désormais correct :

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilterbi.png)

Le filtrage croisé à double sens convient pour un modèle de relations entre tables tel que le modèle ci-dessus. On parle généralement de schéma en étoile, comme illustré ci-dessous :

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterstarschema.png)

La direction du filtrage croisé ne fonctionne pas correctement avec un modèle plus général fréquent dans les bases de données, comme dans le diagramme ci-dessous :

 ![](media/desktop-create-and-manage-relationships/candmrel_crossfilterwithloops.png)

Si vous disposez d’un modèle de tables comme celui-ci, avec des boucles, le filtrage croisé peut créer un ensemble de relations ambigu. Par exemple, si vous additionnez les valeurs d’un champ de la table X et que vous choisissez de filtrer par un champ de la table Y, il est difficile de savoir si le filtrage doit passer par la table supérieure ou inférieure. Un exemple courant de ce genre de modèle est TableX (une table de ventes avec des données réelles) et TableY (une table contenant des données de budget). Les tables intermédiaires sont des tables de choix utilisées par les deux tables, par exemple Division ou Région. 

Comme dans le cas des relations actives/inactives, Power BI Desktop ne vous autorise pas à définir une relation À double sens si cela crée une ambiguïté dans les rapports. Vous avez plusieurs moyens de résoudre le problème. Voici les deux plus courants :

* Supprimez les relations ou marquez-les comme inactives pour réduire l’ambiguïté. Vous pourrez peut-être ensuite définir le filtrage croisé d’une relation sur À double sens.
* Importez une table deux fois (avec un nom différent la deuxième fois) pour éliminer les boucles. Ainsi, le modèle de relations s’apparente à un schéma en étoile. Avec un schéma en étoile, toutes les relations peuvent être À double sens.

## <a name="wrong-active-relationship"></a>Relation active incorrecte
Quand Power BI Desktop crée automatiquement des relations, il rencontre parfois plus d’une relation entre deux tables. Dans ces cas de figure, une seule des relations est définie comme relation active. La relation active fait office de relation par défaut. Ainsi, quand vous choisissez des champs dans deux tables différentes, Power BI Desktop peut créer automatiquement une visualisation pour vous. Toutefois, dans certains cas, la relation sélectionnée automatiquement peut être incorrecte. Vous pouvez utiliser la boîte de dialogue Gérer les relations pour définir une relation comme active ou inactive, ou vous pouvez définir la relation active dans la boîte de dialogue Modifier la relation. 

Pour s’assurer qu’il y a une relation par défaut, Power BI Desktop n’autorise qu’une seule relation active entre deux tables à tout moment donné. Ainsi, vous devez définir la relation actuelle comme inactive, puis définir la relation de votre choix comme relation active.

Examinons un exemple. Voici deux tables, TicketsProjet et RôleEmployé.

**TicketsProjet**

| **Ticket** | **OuvertPar** | **SoumisPar** | **Heures** | **Projet** | **DateSoumission** |
| ---:|:--- |:--- | ---:|:--- | ---:|
| 1001 |Perham, Tom |Brewer, Alan |22 |Bleu |1/1/2013 |
| 1002 |Roman, Daniel |Brewer, Alan |26 |Rouge |2/1/2013 |
| 1003 |Roth, Daniel |Ito, Shu |34 |Jaune |12/4/2012 |
| 1004 |Perham, Tom |Brewer, Alan |13 |Orange |1/2/2012 |
| 1005 |Roman, Daniel |Bowen, Eli |29 |Violet |10/1/2013 |
| 1006 |Roth, Daniel |Bento, Nuno |35 |Vert |2/1/2013 |
| 1007 |Roth, Daniel |Hamilton, David |10 |Jaune |10/1/2013 |
| 1008 |Perham, Tom |Han, Mu |28 |Orange |1/2/2012 |
| 1009 |Roman, Daniel |Ito, Shu |22 |Violet |2/1/2013 |
| 1010 |Roth, Daniel |Bowen, Eli |28 |Vert |10/1/2013 |
| 1011 |Perham, Tom |Bowen, Eli |9 |Bleu |10/15/2013 |

**RôleEmployé**

| **Employé** | **Rôle** |
| --- | --- |
| Bento, Nuno |Chef de projet |
| Bowen, Eli |Chargé de projet |
| Brewer, Alan |Chef de projet |
| Hamilton, David |Chargé de projet |
| Han, Mu |Chargé de projet |
| Ito, Shu |Chargé de projet |
| Perham, Tom |Parrain de projet |
| Roman, Daniel |Parrain de projet |
| Roth, Daniel |Parrain de projet |

Il existe en fait ici deux relations : une entre le champ SoumisPar de la table TicketsProjet et le champ Employé de la table RôleEmployé, l’autre entre le champ OuvertPar de la table TicketsProjet et le champ Employé de la table RôleEmployé.

 ![](media/desktop-create-and-manage-relationships/candmrel_activerelview.png)

Si nous ajoutons les deux relations au modèle (OuvertPar en premier), la boîte de dialogue Gérer les relations indique que la relation OuvertPar est active :

 ![](media/desktop-create-and-manage-relationships/candmrel_managerelactive.png)

Maintenant, si nous créons un rapport qui utilise des champs de rôle et des employés de Rôleemployé et le champ heures de Ticketsprojet dans une visualisation de table dans le canevas de rapport, nous verrons parrains de projet, car ils sont seuls ont ouvert un ticket de projet.

 ![](media/desktop-create-and-manage-relationships/candmrel_repcrossfilteractive.png)

Nous pouvons modifier la relation active pour remplacer OuvertPar par SoumisPar. Dans Gérer les relations, nous décochons la relation TicketsProjet(OuvertPar)/RôleEmployé(Employé) et nous cochons la relation TicketsProjet(SoumisPar)/RôleEmployé(Employé).

![](media/desktop-create-and-manage-relationships/candmrel_managerelactivesubmittedby.png)

## <a name="see-all-of-your-relationships-in-relationship-view"></a>Afficher toutes les relations dans la vue Relation
Parfois, votre modèle comporte plusieurs tables avec des relations complexes. La vue Relation dans Power BI Desktop montre toutes les relations dans votre modèle, leur direction et leur cardinalité dans un diagramme personnalisable et facile à comprendre. Pour plus d’informations, consultez [Vue Relation dans Power BI Desktop](desktop-relationship-view.md).

