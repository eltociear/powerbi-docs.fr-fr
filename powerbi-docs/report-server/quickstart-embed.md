---
title: "Intégrer un rapport à l’aide d’un iFrame"
description: "L’installation de Power BI Report Server est un processus très rapide. Du téléchargement à la configuration en passant par l’installation, vous devriez être opérationnel en quelques minutes."
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 11/09/2017
ms.author: maghan
ms.openlocfilehash: 56835bfb25c8c930099fadf710137f69fa89fc2e
ms.sourcegitcommit: 6e693f9caf98385a2c45890cd0fbf2403f0dbb8a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/30/2018
---
# <a name="quickstart-embed-a-power-bi-report-using-an-iframe-and-url-parameters"></a>Démarrage rapide : incorporer un rapport Power BI à l’aide d’un iFrame et de paramètres d’URL

Vous pouvez intégrer un rapport dans votre application à l’aide d’un iFrame. 

## <a name="url-parameter"></a>Paramètre d’URL

Pour toute URL d’un rapport, vous pouvez ajouter un paramètre querystring défini sur `?rs:Embed=true`.

Par exemple :

```
http://myserver/reports/powerbi/Sales?rs:embed=true
```

Cela fonctionne sur tous les types de rapports dans Power BI Report Server.

## <a name="iframe"></a>iFrame

Une fois que vous avez votre URL, vous pouvez créer un iFrame dans une page Web pour héberger le rapport.

Par exemple :

```
<iframe width="800" height="600" src="http://myserver/reports/powerbi/Sales?rs:embed=true" frameborder="0" allowFullScreen="true"></iframe>
```

## <a name="url-filter"></a>Filtre d’URL

Vous pouvez ajouter un paramètre de chaîne de requête à l’URL pour filtrer les données retournées dans le rapport Power BI.

La syntaxe est simple. Il suffit d’accéder à l’URL du rapport, d’ajouter un point d’interrogation, puis cette syntaxe de filtre.

URL?filter=***Tableau***/***Champ*** eq '***valeur***'

Gardez les considérations suivantes à l’esprit :

- Les noms de **Tableau** et de **Champ** respectent la casse, pas la **valeur**.
- Vous pouvez filtrer un rapport dont des champs sont masqués dans l’affichage Rapport.
- La **valeur** doivent être placée entre apostrophes.
- Le type de champ doit être une chaîne.
- Les noms de table et de champ ne peuvent pas contenir d’espace.

###  <a name="example-filter-on-a-field"></a>Exemple : filtrer sur un champ

Prenons l’[Exemple Analyse de la vente au détail](../sample-datasets.md). Supposons que ceci est l’URL du rapport sur le serveur de rapports dans un dossier nommé « power bi » :

```
https://report-server/reports/power-bi/Retail-Analysis-Sample
```

Vous voyez que la visualisation de la carte dans l’exemple Analyse de la vente au détail affiche des magasins en Caroline du Nord et dans d’autres États.

![Visualisation de la carte de l’exemple Analyse de la vente au détail](media/quickstart-embed/report-server-retail-analysis-sample-map.png)

*NC* est la valeur pour North Carolina (Caroline du Nord) stockée dans le champ **Territoire** du tableau **Magasin**. Ainsi, pour filtrer le rapport afin d’afficher uniquement les données des magasins situés en Caroline du Nord, ajoutez à l’URL le code suivant :

?filter=Store/Territory eq 'NC'

À présent, le rapport étant filtré sur la Caroline du Nord, les visualisations affichées sur la page du rapport présentent uniquement des données relatives à la Caroline du Nord.

![Visualisations filtrées de l’exemple Analyse de la vente au détail](media/quickstart-embed/report-server-retail-analysis-sample-filtered-map.png)

### <a name="create-a-dax-formula-to-filter-on-multiple-values"></a>Créer une formule DAX pour filtrer sur plusieurs valeurs

Une autre façon de filtrer sur plusieurs champs consiste à créer une colonne calculée dans Power BI Desktop, qui concatène deux champs pour former une seule valeur. Ensuite, vous pouvez utiliser cette valeur pour le filtrage.

Par exemple, l’exemple Analyse de la vente au détail comporte deux champs : Territoire et Chaîne. Dans Power BI Desktop, vous pouvez [créer une colonne calculée](../desktop-tutorial-create-calculated-columns.md) (champ) nommée TerritoryChain (TerritoireChaîne). N’oubliez pas que le nom de **Champ** ne peut pas contenir d’espaces. Voici la formule DAX pour cette colonne.

TerritoryChain = [Territoire] & "-" & [Chaîne]

Publiez le rapport sur le serveur Power BI Report Server, puis utilisez la chaîne de requête d’URL pour filtrer afin d’afficher des données uniquement pour les magasins Lindseys de Caroline du Nord.

```
https://report-server/reports/power-bi/Retail-Analysis-Sample?filter=Store/TerritoryChain eq 'NC-Lindseys'

```

## <a name="next-steps"></a>Étapes suivantes

[Démarrage rapide : créer un rapport Power BI pour Power BI Report Server](quickstart-create-powerbi-report.md)  
[Démarrage rapide : créer un rapport paginé pour Power BI Report Server](quickstart-create-paginated-report.md)  

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)