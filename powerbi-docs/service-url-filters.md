---
title: Ajouter des paramètres de rapport Power BI à l’aide de l’URL
description: Filtrez un rapport à l’aide de paramètres de chaîne de requête URL et filtrez même sur plusieurs champs.
author: mihart
manager: kfile
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/18/2018
ms.author: mihart
LocalizationGroup: Reports
ms.openlocfilehash: aeaea6d14cf8f4fd62fbbf5098e68429fe40b96a
ms.sourcegitcommit: 2b9ef93bbff5c741ba55ea0502f642632683d593
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2018
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtrer un rapport à l’aide de paramètres de chaîne de requête dans l’URL
Lorsque vous ouvrez un rapport dans le service Power BI, chaque page du rapport possède sa propre URL unique. Pour filtrer cette page de rapport, vous pouvez utiliser le volet Filtres sur le canevas de rapport.  Vous pouvez également ajouter des paramètres de chaîne de requête à l’URL pour filtrer le rapport. Imaginons que vous avez un rapport que vous envisagez de présenter à des collègues après l’avoir filtré pour eux au préalable. Une solution consiste à ajouter les paramètres de filtre à l’URL par défaut du rapport, puis à envoyer par courriel à vos collègues l’URL entière ainsi obtenue.

![Rapport Power BI dans le service](media/service-url-filters/power-bi-report2.png)

<iframe width="640" height="360" src="https://www.youtube.com/embed/WQFtN8nvM4A?list=PLv2BtOtLblH3YE_Ycas5B1GtcoFfJXavO&amp;showinfo=0" frameborder="0" allowfullscreen></iframe>

## <a name="query-string-parameter-syntax-for-filtering"></a>Syntaxe du paramètre de chaîne de requête pour le filtrage
La syntaxe est assez simple. Il suffit d’accéder à l’URL du rapport, d’ajouter un point d’interrogation, puis d’ajouter la syntaxe du filtre.

URL?filter=***Tableau***/***Champ*** eq '***valeur***'

![URL avec filtre](media/service-url-filters/power-bi-filter-urls7b.png)

* Les noms de **Tableau** et de **Champ** respectent la casse, pas la **valeur**.
* Les champs masqués dans l’affichage Rapport peuvent également être filtrés.
* La **valeur** doivent être placée entre apostrophes.
* Le type de champ doit être un nombre ou une chaîne.
* Les noms de tableau et de champ ne peuvent pas contenir d’espaces.

Si cela ne vous semble pas clair, poursuivez votre lecture. Nous allons décomposer la syntaxe.  

## <a name="filter-on-a-field"></a>Filtrer sur un champ
Supposons que l’URL du rapport soit la suivante.

![URL de départ](media/service-url-filters/power-bi-filter-urls6.png)

Nous pouvons constater dans la visualisation de la carte (ci-dessus) que nous avons des magasins en Caroline du Nord (North Carolina).

>[!NOTE]
>Cet exemple est basé sur l’[Exemple Analyse de la vente au détail](sample-datasets.md).
> 

Pour filtrer le rapport afin d’afficher uniquement les données des magasins situés en « NC » (Caroline du Nord), ajoutez à l’URL le code suivant :

?filter=Store/Territory eq 'NC'

![URL avec filtre](media/service-url-filters/power-bi-filter-urls7.png)

>[!NOTE]
>*NC* est une valeur stockée dans le champ **Territory** (territoire) du tableau **Store** (magasin).
> 
> 

Notre rapport étant filtré sur la Caroline du Nord, les visualisations affichées sur la page du rapport présentent uniquement les données relatives à la Caroline du Nord.

![](media/service-url-filters/power-bi-report4.png)

## <a name="filter-on-multiple-fields"></a>Filtrer sur plusieurs champs
Vous pouvez également filtrer plusieurs champs en ajoutant des paramètres supplémentaires à votre URL. Revenons à notre paramètre de filtre d’origine.

```
?filter=Store/Territory eq 'NC'
```

Pour filtrer sur des champs supplémentaires, ajoutez un `and` et un autre champ au même format que ci-dessus. Voici un exemple.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

<iframe width="640" height="360" src="https://www.youtube.com/embed/0sDGKxOaC8w?showinfo=0" frameborder="0" allowfullscreen></iframe>


### <a name="using-dax-to-filter-on-multiple-values"></a>Utilisation de DAX pour filtrer plusieurs valeurs
Une autre façon de filtrer plusieurs champs consiste à créer une colonne calculée qui concatène deux champs pour former une seule valeur. Ensuite, vous pouvez utiliser cette valeur pour le filtrage.

Par exemple, nous avons deux champs : Territory (territoire) et Chain (chaîne). Dans Power BI Desktop, [créez une colonne calculée](desktop-tutorial-create-calculated-columns.md) (champ) nommée TerritoryChain (TerritoireChaîne). N’oubliez pas que le nom de **Champ** ne peut pas contenir d’espaces. Voici la formule DAX pour cette colonne.

TerritoryChain = [Territoire] & " - " & [Chaîne]

Publiez le rapport sur le service Power BI, puis utilisez la chaîne de requête d’URL pour filtrer les données affichées uniquement pour les magasins Lindseys en Caroline du Nord (NC).

    https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC–Lindseys'

## <a name="pin-a-tile-from-a-filtered-report"></a>Épingler une vignette d’un rapport filtré
Après avoir filtré le rapport à l’aide de paramètres de chaîne de requête, vous pouvez épingler des visualisations de ce rapport à votre tableau de bord. La vignette épinglée au tableau de bord affiche les données filtrées, et la sélection de cette vignette a pour effet d’ouvrir le rapport utilisé pour la créer.  Toutefois, le filtrage que vous avez effectué à l’aide de l’URL n’est pas enregistré avec le rapport et, en cas de sélection de la vignette épinglée au tableau de bord, le rapport qui s’ouvre n’est pas filtré.  Cela signifie que les données qu’affiche la vignette épinglée au tableau de bord ne correspondent pas à celles présentées dans la visualisation du rapport.

Cela peut cependant être utile lorsque vous souhaitez afficher différents résultats : filtrés sur le tableau de bord, non filtrés dans le rapport.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes
Lorsque vous utilisez les paramètres de chaîne de requête, vous devez garder certaines choses à l’esprit.

* Dans Power BI Report Server, vous pouvez [passer des paramètres de rapport](https://docs.microsoft.com/sql/reporting-services/pass-a-report-parameter-within-a-url?view=sql-server-2017.md) en les ajoutant dans une URL de rapport. Ces paramètres d’URL ne sont pas préfixés parce qu’ils sont passés directement dans le moteur de traitement de rapport. 
* Le filtrage de chaîne de requête ne fonctionne pas avec des URL de type [Publier sur le web](service-publish-to-web.md) ou Power BI Embedded.   
* Le type de champ doit être un nombre ou une chaîne.
* Les noms de tableau et de champ ne peuvent pas contenir d’espaces.

## <a name="next-steps"></a>Étapes suivantes
[Épingler une visualisation à un tableau de bord](service-dashboard-pin-tile-from-report.md)  
[Essayez-le gratuitement !](https://powerbi.com/)

D’autres questions ? [Essayez d’interroger la communauté Power BI](http://community.powerbi.com/)

