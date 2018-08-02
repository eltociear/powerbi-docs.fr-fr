---
title: DirectQuery et SAP Business Warehouse (BW) dans Power BI
description: Considérations importantes concernant l’utilisation de DirectQuery avec SAP Business Warehouse (BW)
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 07/26/2018
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 3f6373db938f92f86c0f438162de4454f5f12e00
ms.sourcegitcommit: fbb7924603f8915d07b5e6fc8f4d0c7f70c1a1e1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/02/2018
ms.locfileid: "39280084"
---
# <a name="directquery-and-sap-business-warehouse-bw"></a>DirectQuery et SAP Business Warehouse (BW)
Vous pouvez vous connecter aux sources de données **SAP Business Warehouse (BW)** directement à l’aide de **DirectQuery**. Étant donné la nature multidimensionnelle/OLAP de SAP BW, il existe plusieurs différences importantes entre DirectQuery sur SAP BW et DirectQuery sur des sources relationnelles telles que SQL Server. Ces différences sont résumées ci-après :

* Dans **DirectQuery** sur des sources relationnelles, un ensemble de requêtes (tel que défini dans la boîte de dialogue **Obtenir des données** ou **l’éditeur de requête**) définit de manière logique les données disponibles dans la liste de champs. Cela n’est *pas* le cas lors de la connexion à une source OLAP telle que SAP BW. Lors de la connexion au serveur SAP à l’aide de la boîte de dialogue **Obtenir des données**, seule la requête InfoCube ou BEx est sélectionnée. Tous les chiffres clés et les dimensions de la requête Infocube/BEx sélectionnée sont alors disponibles dans la liste de champs.   
* De même, il n’y pas d’**éditeur de requête** lors de la connexion à SAP BW. Les paramètres de source de données (par exemple, le nom du serveur) se modifient en sélectionnant **Modifier les requêtes > Paramètres de la source de données**. La configuration des paramètres peut être modifiée en sélectionnant **Modifier les requêtes > Gérer les paramètres**.
* Compte tenu de la nature unique des sources OLAP, des restrictions supplémentaires (pour la modélisation et les visualisations) s’appliquent en plus des restrictions normales imposées pour DirectQuery. Ces restrictions sont décrites plus loin dans cet article.

En outre, il est *extrêmement important* de comprendre que de nombreuses fonctionnalités de SAP BW ne sont pas prises en charge dans Power BI et qu’en raison de la nature de l’interface publique de SAP BW, les résultats affichés dans Power BI ne correspondent pas à ceux observés dans un outil SAP dans de nombreux cas importants. Ces limitations sont décrites plus loin dans cet article. Vous devez soigneusement examiner ces limitations et différences de comportement, afin que les résultats affichés dans Power BI, tels qu’ils sont retournés par l’interface publique SAP, soient interprétés correctement.  

> [!NOTE]
> DirectQuery sur SAP BW était disponible en préversion jusqu’à la mise à jour de mars 2018 de Power BI Desktop. Certains commentaires et suggestions d’amélioration reçus durant la préversion demandaient un changement qui impactait les rapports créés à l’aide de cette préversion. Maintenant que la version en disponibilité générale de DirectQuery sur SAP BW a été publiée, vous *devez* supprimer tous les rapports existants qui ont été créés avec une préversion de DirectQuery sur SAP BW antérieure à la version en disponibilité générale. Dans les rapports créés avec une version de DirectQuery sur SAP BW antérieure à la version en disponibilité générale, des erreurs se produisent lors de l’appel de la commande d’actualisation suite à la tentative d’actualisation des métadonnées avec les modifications effectuées dans le cube sous-jacent de SAP BW. Vous devez recréer ces rapports à partir d’un rapport vide, en utilisant la version en disponibilité générale de DirectQuery sur SAP BW. 

## <a name="additional-modeling-restrictions"></a>Autres restrictions de modélisation
Les autres principales restrictions de modélisation au moment de se connecter à SAP BW à l’aide de DirectQuery dans Power BI sont les suivantes :

* **Aucune prise en charge des colonnes calculées :** la possibilité de créer des colonnes calculées est désactivée. Cela signifie également que le regroupement et le clustering, qui permettent de créer des colonnes calculées, ne sont pas disponibles.
* **Autres limitations concernant les mesures :** des limitations supplémentaires sont imposées sur les expressions DAX pouvant être utilisées dans les mesures, afin de refléter le niveau de prise en charge offert par SAP BW.
* **Aucune prise en charge de la définition de relations :** les relations sont inhérentes à la source SAP externe, et il n’est pas possible de définir d’autres relations dans le modèle.
* **Aucune vue de données :** la **vue de données** affiche normalement les données détaillées dans les tables. Étant donné la nature des sources OLAP telles que SAP BW, cette vue n’est pas disponible via SAP BW.
* **Les détails des colonnes et des mesures sont fixes :** la liste de colonnes et de mesures de la liste de champs est fixée par la source sous-jacente et ne peut pas être modifiée. Par exemple, il n’est pas possible de supprimer une colonne, ni de modifier son type de données (elle peut toutefois être renommée).
* **Autres limitations dans DAX :** il existe des limitations supplémentaires pour les expressions DAX qui peuvent être utilisées dans les définitions de mesures, afin de refléter les limitations de la source. Par exemple, il n’est pas possible d’utiliser une fonction d’agrégation sur une table.

## <a name="additional-visualization-restrictions"></a>Autres restrictions de visualisation
Les principales restrictions supplémentaires applicables aux visualisations lors de la connexion à SAP BW à l’aide de DirectQuery dans Power BI sont les suivantes :

* **Aucune agrégation de colonnes :** il n’est pas possible de modifier l’agrégation d’une colonne sur un visuel ; elle est toujours définie sur *Ne pas résumer*.
* **Le filtrage des mesures est désactivé :** le filtrage des mesures est désactivé pour refléter la prise en charge offerte par SAP BW.
* **Sélection multiple et inclusion/exclusion :** la possibilité de sélectionner plusieurs points de données sur un visuel est désactivée si les points représentent des valeurs de plusieurs colonnes. Par exemple, dans le cas d’un graphique à barres affichant les ventes par pays, avec la catégorie en légende, il est impossible de sélectionner le point pour (États-Unis, bicyclettes) et (France, vêtements). De même, il n’est pas possible de sélectionner le point pour (États-Unis, bicyclettes) et de l’exclure du visuel. Ces deux limitations sont imposées afin de refléter la prise en charge offerte par SAP BW.

## <a name="support-for-sap-bw-features"></a>Prise en charge des fonctionnalités de SAP BW
Le tableau suivant répertorie toutes les fonctionnalités de SAP BW qui ne sont pas entièrement prises en charge ou se comportent différemment lorsque vous utilisez Power BI.   

| Fonctionnalité | Description |
| --- | --- |
| Calculs locaux |Les calculs locaux définis dans une requête BEx changent les nombres affichés via des outils tels que BEx Analyzer. Toutefois, ils ne sont pas reflétés dans les nombres retournés par SAP par le biais de l’interface publique MDX. <br/> <br/> **Par conséquent, les nombres affichés dans les visuels Power BI ne correspondent pas nécessairement à ceux d’un visuel correspondant d’un outil SAP.**<br/> <br/>  Par exemple, lors de la connexion à un cube de requête à partir d’une requête BEx qui définit l’agrégation sur Cumulé (par exemple cumul), Power BI reprend les nombres de base, en ignorant ce paramètre.  Certes, un analyste peut alors appliquer un calcul de cumul localement dans Power BI, mais il doit alors interpréter ces nombres avec prudence s’il ne le fait pas. |
| Agrégations |Dans certains cas (en particulier lors du traitement de plusieurs devises), les nombres agrégés retournés par l’interface publique SAP ne correspondent pas à ceux indiqués par les outils SAP. <br/> <br/> **Par conséquent, les nombres affichés dans les visuels Power BI ne correspondent pas nécessairement à ceux d’un visuel correspondant d’un outil SAP.** <br/> <br/> Par exemple, les totaux affichés dans différentes devises le sont sous la forme « * » dans BEx Analyzer, mais le total est retourné par l’interface publique SAP, sans indication du non-sens de ce nombre agrégé. Par conséquent, le nombre (agrégeant par exemple des $ US, des euros et des $ australiens) est affiché par Power BI. |
| Mise en forme de devise |Toute mise en forme de devise (par exemple, 2 300 $ ou 4 000 AUD) n’est pas reflétée dans Power BI. |
| Unités de mesure |Les unités de mesure (par exemple 230 KG) ne sont pas reflétées dans Power BI. |
| Clé versus texte (court, moyen, long) |Pour une caractéristique SAP BW telle que CostCenter, la liste de champs affiche une seule colonne de centre de coût.  Si vous utilisez cette colonne, le texte par défaut s’affiche.  En affichant les champs masqués, il est également possible d’afficher la colonne à nom unique (qui retourne le nom unique attribué par SAP BW et constitue la base de l’unicité).<br/> <br/>  La clé et les autres champs de texte ne sont pas disponibles. |
| Hiérarchies multiples d’une caractéristique |Dans **SAP**, une caractéristique peut avoir plusieurs hiérarchies. Ainsi, dans des outils tels que BEx Analyzer, quand une caractéristique est incluse dans une requête, l’utilisateur peut sélectionner la hiérarchie à utiliser. <br/> <br/> Dans **Power BI**, les diverses hiérarchies sont affichées dans la liste de champs en tant que hiérarchies différentes sur la même dimension.  Toutefois, si vous sélectionnez plusieurs niveaux de deux hiérarchies différentes sur la même dimension, des données vides sont renvoyées par SAP. |
| Traitement des hiérarchies déséquilibrées |![](media/desktop-directquery-sap-bw/directquery-sap-bw_01.png) |
| Facteur d’échelle/signe inversé |Dans SAP, un chiffre clé peut avoir un facteur d’échelle (par exemple, 1000) défini comme option de mise en forme, ce qui signifie que tout affichage est mis à l’échelle en fonction de ce facteur. <br/> <br/> De même, il peut avoir un jeu de propriétés inversant le signe. L’utilisation d’un chiffre clé de ce type dans Power BI (dans un visuel ou dans le cadre d’un calcul) entraîne l’utilisation du nombre non mis à l’échelle (et le signe n’est alors pas inversé). Le facteur d’échelle sous-jacent n’est pas disponible. Dans les visuels Power BI,vous pouvez contrôler les unités d’échelle de l’axe (K, M, B) dans le cadre de la mise en forme des visuels. |
| Hiérarchies dans lesquelles les niveaux apparaissent/disparaissent dynamiquement |Lors de la connexion initiale à SAP BW, les informations sur les niveaux d’une hiérarchie sont extraites, ce qui génère un ensemble de champs dans la liste de champs. Celui-ci est mis en cache et, si l’ensemble de niveaux change, l’ensemble de champs ne change pas jusqu’à l’appel de l’actualisation. <br/> <br/> Cela est possible uniquement dans **Power BI Desktop**. Dans le service Power BI , il n’est pas possible, après la publication, d’appeler une actualisation de ce type visant à refléter les modifications apportées aux niveaux. |
| Filtre par défaut |Une requête BEx peut inclure des filtres par défaut, qui sont appliqués automatiquement par SAP BEx Analyzer. Ces filtres ne sont pas exposés et, par conséquent, l’utilisation équivalente dans Power BI n’applique pas ces filtres par défaut. |
| Chiffres clés masqués |Une requête BEx peut contrôler la visibilité des chiffres clés, et ceux qui sont masqués n’apparaissent pas dans SAP BEx Analyzer. Cela n’est pas reflété dans l’API publique et, par conséquent, ces chiffres clés masqués figurent toujours dans la liste de champs. Toutefois, vous pouvez ensuite les masquer dans Power BI. |
| Mise en forme numérique |Toute mise en forme numérique (nombre de décimales, séparateur décimal, etc.) n’est pas automatiquement répercutée dans Power BI. Toutefois, il est possible de contrôler ensuite ce type de mise en forme dans Power BI. |
| Contrôle de version des hiérarchies |SAP BW autorise la gestion de différentes versions d’une hiérarchie, par exemple la hiérarchie de centre de coût pour 2007 et 2008. Seule la dernière version est disponible dans Power BI, car les informations de versions ne sont pas exposées par l’API publique. |
| Hiérarchies dépendant du temps |Dans Power BI, les hiérarchies dépendant du temps sont évaluées à la date du jour. |
| Conversion de devises |SAP BW prend en charge la conversion de devises, en fonction des taux définis dans le cube. Ces fonctionnalités ne sont pas exposées par l’API publique et ne sont donc pas disponibles dans Power BI. |
| Ordre de tri |L’ordre de tri (par texte ou par clé) d’une caractéristique peut être défini dans SAP. Cet ordre de tri n’est pas reflété dans Power BI. Par exemple, les mois peuvent apparaître dans l’ordre « Avril », « Août » et ainsi de suite. <br/> <br/> Il n’est pas possible de modifier cet ordre de tri dans Power BI. |
| Noms techniques |Dans la boîte de dialogue **Obtenir des données**, les noms de caractéristique/mesure (description) et les noms techniques sont visibles. La liste de champs, elle, contient uniquement les noms de caractéristique/mesure (description). |
| Attributs |Il n’est pas possible d’accéder aux attributs d’une caractéristique dans Power BI. |
| Paramètre de langue de l’utilisateur final |Les paramètres régionaux utilisés pour se connecter à SAP BW sont définis dans le cadre des détails de connexion et ne reflètent pas les paramètres régionaux du lecteur du rapport final. |
| Variables de texte |SAP BW autorise l’utilisation des espaces réservés pour les variables dans les noms de champ (par exemple, « Chiffres réels $YEAR$ »), ceux-ci étant ensuite remplacés par la valeur sélectionnée. Par exemple, le champ apparaît sous la forme « Chiffres réels 2016 » dans les outils BEx si l’année 2016 a été sélectionnée pour la variable. <br/> <br/> Le nom de colonne affiché dans Power BI ne change pas en fonction de la valeur de la variable et, par conséquent, est affiché sous la forme « $YEAR$ Chiffres réels ».  Toutefois, vous pouvez modifier le nom de colonne ensuite dans Power BI. |
| Variables de sortie client | Les variables de sortie client ne sont pas exposées par l’API publique et ne sont donc pas prises en charge par Power BI. |
| Structures caractéristiques | Les structures caractéristiques de la source SAP BW sous-jacente entraînent une « explosion » des mesures exposées dans Power BI. Par exemple, avec deux mesures Sales et Costs et une structure caractéristique contenant Budget et Actual, quatre mesures sont exposées : Sales.Budget, Sales.Actual, Costs.Budget et Costs.Actual. |


## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur DirectQuery, consultez les ressources suivantes :

* [DirectQuery dans Power BI](desktop-directquery-about.md)
* [Sources de données prises en charge par DirectQuery](desktop-directquery-data-sources.md)
* [DirectQuery et SAP HANA](desktop-directquery-sap-hana.md)

