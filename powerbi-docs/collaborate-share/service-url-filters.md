---
title: Filtrer un rapport à l’aide de paramètres de chaîne de requête dans l’URL
description: Filtrez un rapport à l’aide de paramètres de chaîne de requête URL et filtrez même sur plusieurs champs.
author: maggiesMSFT
ms.author: maggies
ms.reviewer: ''
featuredvideoid: ''
ms.service: powerbi
ms.subservice: pbi-collaborate-share
ms.topic: how-to
ms.date: 07/16/2020
LocalizationGroup: Reports
ms.openlocfilehash: 7015eb1298649534a6e93cb9d6671250c6c77b94
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96406362"
---
# <a name="filter-a-report-using-query-string-parameters-in-the-url"></a>Filtrer un rapport à l’aide de paramètres de chaîne de requête dans l’URL

Lorsque vous ouvrez un rapport dans le service Power BI, chaque page du rapport possède sa propre URL unique. Pour filtrer cette page de rapport, vous pouvez utiliser le volet Filtres sur le canevas de rapport.  Vous pouvez aussi ajouter des paramètres de chaîne de requête à l’URL pour préfiltrer le rapport. Imaginons que vous avez un rapport que vous envisagez de présenter à des collègues après l’avoir filtré pour eux au préalable. Une façon de le filtrer est de commencer par l'URL par défaut du rapport, d'ajouter les paramètres du filtre à l'URL, puis de leur envoyer par e-mail la nouvelle URL complète.

Cet article utilise le rapport Retail Analysis Sample. Pour suivre cette procédure pas à pas, vous pouvez [télécharger l’exemple de rapport](../create-reports/sample-retail-analysis.md#get-the-sample).

![Capture d’écran du rapport Power BI dans le service.](media/service-url-filters/power-bi-retail-analysis-sample.png)

## <a name="uses-for-query-string-parameters"></a>Utilisations des paramètres de chaîne de requête

Supposons que vous travaillez dans Power BI Desktop. Vous voulez créer un rapport comportant des liens vers d’autres rapports Power BI, mais vous ne souhaitez montrer que certaines informations dans les autres rapports. Filtrez d’abord les rapports en utilisant des paramètres de chaîne de requête et enregistrez les URL. Ensuite, créez une table dans Desktop avec ces nouvelles URL de rapport.  Enfin, publiez et partagez le rapport.

Une autre utilisation des paramètres de chaîne de requête concerne la création d’une solution Power BI avancée.  Avec DAX, elle crée un rapport qui génère une URL de rapport filtré dynamiquement en fonction de la sélection effectuée par son client dans le rapport actuel. Quand des clients sélectionnent l’URL, ils voient seulement les informations prévues. 

## <a name="query-string-parameter-syntax-for-filtering"></a>Syntaxe du paramètre de chaîne de requête pour le filtrage

Avec des paramètres, vous pouvez filtrer le rapport pour une ou plusieurs valeurs, même si ces valeurs contiennent des espaces ou des caractères spéciaux. La syntaxe de base est assez simple. Il suffit d’accéder à l’URL du rapport, d’ajouter un point d’interrogation, puis d’ajouter la syntaxe du filtre.

*URL*?filter=*Tableau*/*Champ* eq '*valeur*'

![Capture d’écran de l’URL avec un filtre.](media/service-url-filters/power-bi-filter-urls7b.png)

* Les noms de **Table** et de **Champ** sont sensibles à la casse, mais pas la **valeur**.
* Les champs masqués dans l’affichage Rapport peuvent également être filtrés.

### <a name="field-types"></a>Types de champ

Le type du champ peut être un nombre, une date/heure ou une chaîne, et le type utilisé doit correspondre au type défini dans le jeu de données.  Par exemple, la spécification d’une colonne de table de type « chaîne » ne fonctionne pas si vous recherchez une valeur numérique ou de date/heure dans une colonne du jeu de données définie en tant que date, telle que Table/StringColumn eq 1.

* Les **chaînes** doivent être placées entre des guillemets simples, comme dans 'nom responsable'.
* Les **nombres** ne nécessitent par de mise en forme spéciale. Voir la section [Types de données numériques](#numeric-data-types) de cet article pour plus d’informations.
* **Dates et heures** Voir la section [Types de données date](#date-data-types) dans cet article. 

Si cela ne vous semble pas clair, poursuivez votre lecture. Nous allons décomposer la syntaxe.  

## <a name="filter-on-a-field"></a>Filtrer sur un champ

Supposons que l’URL du rapport soit la suivante.

![Capture d’écran du lancement de l’URL.](media/service-url-filters/power-bi-filter-urls6.png)

Nous pouvons constater dans la visualisation de la carte ci-dessus que nous avons des magasins en Caroline du Nord (North Carolina). *NC* est la valeur pour North Carolina (Caroline du Nord) qui est située dans le champ **Territoire** du tableau **Magasin**. Ainsi, pour filtrer le rapport afin d’afficher uniquement les magasins situés en Caroline du Nord (« NC »), ajoutez cette chaîne à l’URL :

```
?filter=Store/Territory eq 'NC'
```

![Capture d’écran de l’URL avec un filtre pour Caroline du Nord.](media/service-url-filters/power-bi-filter-urls7.png)

Notre rapport étant désormais filtré sur la Caroline du Nord, les visualisations du rapport présentent uniquement les données relatives à la Caroline du Nord.

![Capture d’écran du rapport filtré sur la Caroline du Nord.](media/service-url-filters/power-bi-url-filter-nc.png)

## <a name="filter-on-more-than-one-value-in-a-field"></a>Filtrer sur plusieurs valeurs d’un champ

Pour filtrer sur plusieurs valeurs dans un champ unique, on utilise l’opérateur **in** au lieu de l’opérateur **and**. La syntaxe est :

*URL*?filter=*Tableau*/*Champ* **in** ('*valeur1*', '*valeur2*')

Reprenons le même exemple : pour filtrer le rapport afin d’afficher uniquement les données des magasins situés en « NC » (Caroline du Nord) ou au « TN » (Tennessee), ajoutez ceci à l’URL :

```
?filter=Store/Territory in ('NC', 'TN')
```

Pour obtenir une liste d’autres opérateurs utiles, consultez le tableau [Opérateurs](#operators) plus loin dans cet article.

## <a name="filter-on-multiple-fields"></a>Filtrer sur plusieurs champs

Vous pouvez également filtrer plusieurs champs en ajoutant des paramètres supplémentaires à votre URL. Revenons à notre paramètre de filtre d’origine.

```
?filter=Store/Territory eq 'NC'
```

Pour filtrer sur des champs supplémentaires, ajoutez un '**and**' et un autre champ au même format que ci-dessus. Voici un exemple.

```
?filter=Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'
```

## <a name="operators"></a>Opérateurs

Power BI prend en charge de nombreux opérateurs en plus de '**and**'. Le tableau ci-dessous liste ces opérateurs, ainsi que le type de contenu qu’ils prennent en charge.

|Opérateur  | Définition | chaîne  | nombre | Date |  Exemple|
|---------|---------|---------|---------|---------|---------|
|**and**     | et |  Oui      | Oui |  oui|  product/price le 200 and price gt 3,5 |
|**eq**     | est égal à |  Oui      | Oui   |  oui       | Address/City eq 'Redmond' |
|**ne**     | différent de |   Oui      | Oui  | oui        |  Address/City ne 'London' |
|**ge**     |  supérieur ou égal à       | non | Oui |oui |  product/price ge 10
|**gt**     | supérieur à        |non | Oui | oui  | product/price gt 20
|**le**     |   inférieur ou égal à      | non | Oui | oui  | product/price le 100
|**lt**     |  inférieur à       | non | Oui | oui |  product/price lt 20
|**in\*\***     |  incluant       | Oui | Oui |  oui | Student/Age in (27, 29)


\*\* Quand vous utilisez **in**, les valeurs à droite de **in** peuvent être une liste séparée par des virgules et entourée de parenthèses, ou une expression qui retourne une collection.

### <a name="numeric-data-types"></a>Types de données numériques

Un filtre d’URL Power BI peut inclure des nombres dans les formats suivants.

|Type de nombre  |Exemple  |
|---------|---------|
|**integer**     |   5      |
|**long**     |   5 L ou 5 l      |
|**double**     |   5,5 ou 55e-1 ou 0,55e+1 ou 5D ou 5d ou 0,5e1D ou 0,5e1d ou 5,5D ou 5,5d ou 55e-1D ou 55e-1d     |
|**decimal**     |   5 M ou 5 m ou 5.5 M ou 5.5 m      |
|**float**     | 5 F ou 5 f ou 0.5e1 F ou 0.5e-1 d        |

### <a name="date-data-types"></a>Types de données date

Power BI prend en charge OData V3 et V4 pour les types de données **Date** et **DateTimeOffset**. Pour OData V3, les dates doivent être entourées de guillemets simples et précédées du mot datetime. Les guillemets simples et le mot datetime ne sont pas nécessaires dans OData V4. 
  
Les dates sont représentées selon le format de modèle EDM (2019-02-12T00:00:00) : Quand vous spécifiez une date en 'AAAA-MM-JJ', Power BI l’interprète en 'AAAA-MM-JJT00:00:00'. Assurez-vous que le mois et le jour comportent deux chiffres, MM et JJ.

Pourquoi cette distinction est-elle importante ? Supposons que vous créez un paramètre de chaîne de requête **Table/Date gt 2018-08-03**.  Les résultats vont-ils inclure le 3 août 2018 ou commencer le 4 août 2018 ? Power BI traduit votre requête en **Table/Date gt '2018-08-03T00:00:00'** . Ainsi, vos résultats incluent toutes les dates qui ont une partie de temps différente de zéro, car ces dates seraient supérieures à **'2018-08-03T00:00:00'** .

Il existe d'autres différences entre V3 et V4. OData V3 ne prend pas en charge Dates, seulement DateTime. Par conséquent, si vous utilisez le format V3, vous devez le qualifier avec la date et l'heure complètes. Les littéraux de date comme "datetime'2019-05-20'" ne sont pas pris en charge dans la notation V3. Mais vous pouvez simplement écrire "2019-05-20" en notation V4. Voici deux requêtes de filtre équivalentes dans V3 et V4 :

- Format OData V4 : filter=Table/Date gt 2019-05-20
- Format OData V3 : filter=Table/Date gt datetime'2019-05-20T00:00:00'


## <a name="special-characters-in-url-filters"></a>Caractères spéciaux dans les filtres d’URL

### <a name="special-characters-in-table-and-column-names"></a>Caractères spéciaux dans les noms de tables et de colonnes

Les caractères spéciaux et les espaces dans les noms de tables et de colonnes nécessitent une mise en forme supplémentaire. Quand votre requête contient des espaces, des tirets ou d’autres caractères non-ASCII, faites précéder ces caractères spéciaux d’un *code d’échappement* commençant par un trait de soulignement et X ( **_x**), suivi du code **Unicode** à quatre chiffres, puis par un autre trait de soulignement. Si le code Unicode a moins de quatre caractères, vous devez le compléter avec des zéros. Voici quelques exemples.

|Identificateur  |Unicode  | Codage pour Power BI  |
|---------|---------|---------|
|**Nom du tableau**     | Le code Unicode pour l’espace est 0x20        |  Table_x0020_Name       |
|**Column**@**Number**     |   Le code Unicode pour @ est 0x40     |  Column_x0040_Number       |
|**[Column]**     |  [ is 0x005B ] is 0x005D       |  _x005B_Column_x005D_       |
|**Column+Plus**     | Le code Unicode pour + est 0x2B        |  Column_x002B_Plus       |

Table_x0020_Name/Column_x002B_Plus eq 3 ![Capture d’écran du visuel de table affichant des caractères spéciaux pour Unicode.](media/service-url-filters/power-bi-special-characters1.png)


Table_x0020_Special/_x005B_Column_x0020_Brackets_x005D_ eq '[C]' ![Capture d’écran du visuel de table affichant des caractères spéciaux pour le codage pour Power BI.](media/service-url-filters/power-bi-special-characters2.png)

### <a name="special-characters-in-values"></a>Caractères spéciaux dans les valeurs

Les filtres d’URL prennent déjà en charge tous les caractères spéciaux dans les valeurs de champs, à l’exception des guillemets simples ('). C’est le seul caractère que vous devez échapper. Pour rechercher un caractère guillemet simple, utilisez deux guillemets simples (''). 

Par exemple :

- `?filter=Table/Name eq 'O''Brien'` devient : 

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-obrien.png" alt-text="Le nom est O’Brien":::

- `?filter=Table/Name eq 'Lee''s Summit'` devient :

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-lees.png" alt-text="Lee's Summit":::

- L’opérateur `in` prend également en charge cet échappement : `?filter=Table/Name in ('Lee''s Summit', 'O''Brien')` devient :

    :::image type="content" source="media/service-url-filters/power-bi-url-filter-in.png" alt-text="Lee's Summit ou O'Brien":::

## <a name="use-dax-to-filter-on-multiple-values"></a>Utiliser DAX pour filtrer sur plusieurs valeurs

Une autre façon de filtrer plusieurs champs consiste à créer une colonne calculée qui concatène deux champs pour former une seule valeur. Ensuite, vous pouvez utiliser cette valeur pour le filtrage.

Par exemple, nous avons deux champs : Territory (territoire) et Chain (chaîne). Dans Power BI Desktop, [créez une colonne calculée](../transform-model/desktop-tutorial-create-calculated-columns.md) (champ) nommée TerritoryChain (TerritoireChaîne). N’oubliez pas que le nom de **Champ** ne peut pas contenir d’espaces. Voici la formule DAX pour cette colonne.

TerritoryChain = [Territoire] & " - " & [Chaîne]

Publiez le rapport sur le service Power BI, puis utilisez la chaîne de requête d’URL pour filtrer les données affichées uniquement pour les magasins Lindseys en Caroline du Nord (NC).

```
https://app.powerbi.com/groups/me/reports/8d6e300b-696f-498e-b611-41ae03366851/ReportSection3?filter=Store/TerritoryChain eq 'NC – Lindseys'
```

## <a name="pin-a-tile-from-a-filtered-report"></a>Épingler une vignette d’un rapport filtré

Après avoir filtré le rapport à l’aide de paramètres de chaîne de requête, vous pouvez épingler des visualisations de ce rapport à votre tableau de bord.  La vignette épinglée au tableau de bord affiche les données filtrées. La sélection de cette vignette a pour effet d’ouvrir le rapport utilisé pour la créer.  Toutefois, le filtrage effectué à l’aide de l’URL n’est pas enregistré avec le rapport. Lorsque vous sélectionnez la mosaïque du tableau de bord, le rapport s’ouvre dans son état non filtré.  Les données affichées par la mosaïque épinglée au tableau de bord ne correspondent donc pas à celles présentées dans la visualisation du rapport.

Cette divergence est utile quand vous voulez afficher des résultats différents : filtrés sur le tableau de bord et non filtrés dans le rapport.

## <a name="considerations-and-troubleshooting"></a>Considérations et résolution des problèmes

Lorsque vous utilisez les paramètres de chaîne de requête, vous devez garder certaines choses à l’esprit.

* Quand vous utilisez l’opérateur *in*, les valeurs à droite de *in* doivent être sous forme de liste séparée par des virgules et placée entre des parenthèses.    
* Power BI Report Server offre également la possibilité de spécifier des filtres supplémentaires à l’aide du paramètre d’URL « filter ». Voici un exemple de ce à quoi peut ressembler l’URL dans Power BI Report Server : `https://reportserver/reports/powerbi/Store Sales?rs:Embed=true&filter= Store/Territory eq 'NC' and Store/Chain eq 'Fashions Direct'`
* Les filtres d’URL de rapport sont limités à 10 expressions (10 filtres connectés par AND).
* Le type de données long est (2^53 - 1) en raison des limitations de JavaScript.
* Power BI ne limite pas le nombre de caractères pouvant être utilisés dans les chaînes de requête d’URL. Cependant, chaque navigateur a ses propres restrictions de longueur.

Les filtres d’URL sont pris en charge dans certains scénarios d’incorporation et non dans d’autres.

- L’[incorporation d’un rapport dans un portail sécurisé ou un site web](service-embed-secure.md) est prise en charge.
- Les filtres d’URL sont pris en charge dans Power BI Embedded. Pour plus d’informations, consultez [Fonctionnalités avancées de filtrage d’URL Power BI Embedded](https://azure.microsoft.com/updates/power-bi-embedded-advanced-url-filtering-capabilities).
- Le filtrage de chaîne de requête ne fonctionne pas avec [Publier sur le web](service-publish-to-web.md) ou [Exporter au format PDF](../consumer/end-user-pdf.md).
- [Incorporer avec le composant du rapport dans SharePoint Online](service-embed-report-spo.md) ne prend pas en charge les filtres d’URL.
- Les équipes n’autorisent pas la spécification d’une URL.

## <a name="next-steps"></a>Étapes suivantes

[Épingler une visualisation à un tableau de bord](../create-reports/service-dashboard-pin-tile-from-report.md)  
[S’inscrire à un essai gratuit](https://powerbi.microsoft.com/get-started/)

D’autres questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)



