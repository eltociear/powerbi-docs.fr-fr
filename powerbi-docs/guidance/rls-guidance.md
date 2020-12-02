---
title: Aide sur la sécurité au niveau des lignes (RLS) dans Power BI Desktop
description: Conseils pour l’application de la sécurité au niveau des lignes (RLS) dans vos modèles de données avec Power BI Desktop.
author: paulinbar
ms.author: painbar
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/18/2020
ms.openlocfilehash: 3c8290391d549f4510b4f6ea6ee0fd596500045e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96410088"
---
# <a name="row-level-security-rls-guidance-in-power-bi-desktop"></a>Aide sur la sécurité au niveau des lignes (RLS) dans Power BI Desktop

Cet article s’adresse principalement aux modélisateurs de données qui utilisent Power BI Desktop. Il décrit les bonnes pratiques de conception pour l’application de la sécurité au niveau des lignes (RLS) dans vos modèles de données.

Il est important de comprendre les filtres RLS de _lignes de table_. Ils ne peuvent pas être configurés pour restreindre l’accès aux objets de modèle, y compris les tables, les colonnes et les mesures.

> [!NOTE]
> Cet article ne décrit pas ce qu’est la sécurité au niveau des lignes ou la façon de le configurer. Pour plus d’informations à ce sujet, consultez [Restreindre l’accès aux données avec la sécurité au niveau des lignes (RLS) pour Power BI Desktop](../create-reports/desktop-rls.md).
>
> En outre, il ne couvre pas l’application de la sécurité au niveau des lignes pour les connexions actives à des modèles hébergés en externe avec Azure Analysis Services ou SQL Server Analysis Services. Dans ces cas, la sécurité au niveau des lignes est appliquée par Analysis Services. Lorsque Power BI se connecte à l’aide de l’authentification unique (SSO), Analysis Services applique la sécurité au niveau des lignes (à moins que le compte dispose de privilèges d’administrateur).

## <a name="create-roles"></a>Créer les rôles

Il est possible de créer plusieurs rôles. Lorsque vous envisagez les besoins d’autorisation pour un utilisateur de rapport particulier, efforcez-vous de créer un rôle unique qui accorde toutes ces autorisations, au lieu d’avoir une structure dans laquelle un utilisateur de rapport sera membre de plusieurs rôles. En effet, un utilisateur de rapport peut correspondre à plusieurs rôles, soit directement à l’aide de son compte d’utilisateur, soit indirectement par l’appartenance à un groupe de sécurité. Les associations de rôles multiples peuvent entraîner des résultats inattendus.

Lorsqu’un utilisateur de rapport est affecté à plusieurs rôles, les filtres RLS deviennent additifs. Cela signifie que les utilisateurs de rapports peuvent voir les lignes de table qui représentent l’union de ces filtres. De plus, dans certains scénarios, il n’est pas possible de garantir qu’un utilisateur de rapport ne voit pas de lignes dans une table. Par conséquent, contrairement aux autorisations appliquées aux objets de base de données SQL Server (et aux autres modèles d’autorisation), le principe de « ce qui est refusé une fois est toujours refusé » ne s’applique pas.

Prenons l’exemple d’un modèle avec deux rôles : Le premier rôle, nommé **Workers**, limite l’accès à toutes les lignes de la table **Payroll** à l’aide de l’expression de règle suivante :

```dax
FALSE()
```

> [!NOTE]
> Une règle ne retourne pas de lignes de table lorsque son expression prend la valeur **false**.

Pourtant, un deuxième rôle, nommé **Managers**, autorise l’accès à toutes les lignes de la table **Payroll** à l’aide de l’expression de règle suivante :

```dax
TRUE()
```

Attention : Si un utilisateur de rapport est associé aux deux rôles, il voit toutes les lignes de la table **Payroll**.

## <a name="optimize-rls"></a>Optimiser la sécurité au niveau des lignes

La sécurité au niveau des lignes fonctionne en appliquant automatiquement des filtres à chaque requête DAX, et ces filtres peuvent avoir un impact négatif sur les performances des requêtes. Par conséquent, l’efficacité de la sécurité au niveau des lignes repose sur une bonne conception de modèle. Il est important de suivre les recommandations relatives à la conception du modèle, comme indiqué dans les articles suivants :

- [Comprendre le schéma en étoile et son importance pour Power BI](star-schema.md)
- Tous les articles sur les relations figurant dans la [Documentation d’assistance sur Power BI](./index.yml)

En général, il est souvent plus efficace d’appliquer des filtres RLS sur des tables de type de dimension que sur des tables de type fait. Il convient aussi de se reposer sur des relations bien conçues pour garantir la propagation des filtres RLS aux autres tables de modèle. Par conséquent, évitez d’utiliser la fonction DAX [LOOKUPVALUE](/dax/lookupvalue-function-dax) lorsque les relations de modèle peuvent atteindre le même résultat.

Chaque fois que des filtres RLS sont appliqués sur les tables DirectQuery et qu’il y a des relations avec d’autres tables DirectQuery, veillez à optimiser la base de données source. Cela peut impliquer la conception d’index appropriés ou l’utilisation de colonnes calculées persistantes. Pour plus d’informations, consultez l’[Aide sur le modèle DirectQuery dans Power BI Desktop](directquery-model-guidance.md).

### <a name="measure-rls-impact"></a>Mesurer l’impact de la RLS

Il est possible de mesurer l’impact sur les performances des filtres RLS dans Power BI Desktop à l’aide de l’[Analyseur de performances](../create-reports/desktop-performance-analyzer.md). Tout d’abord, déterminez les durées des requêtes visuelles du rapport lorsque la sécurité au niveau des lignes n’est pas appliquée. Ensuite, utilisez la commande **Afficher en tant que** sous l’onglet de ruban **Modélisation** pour appliquer la sécurité au niveau des lignes et déterminer et comparer les durées des requêtes.

## <a name="configure-role-mappings"></a>Configurer des mappages de rôles

Après publication sur Power BI, vous devez mapper les membres aux rôles du jeu de données. Seuls les propriétaires de jeux de données ou les administrateurs de l’espace de travail peuvent ajouter des membres aux rôles. Pour plus d’informations, consultez [Sécurité au niveau des lignes avec Power BI (Gérer la sécurité sur votre modèle)](../admin/service-admin-rls.md#manage-security-on-your-model).

Les membres peuvent être des comptes d’utilisateur ou des groupes de sécurité. Dans la mesure du possible, nous vous recommandons de mapper des groupes de sécurité aux rôles de jeu de données. Cela implique la gestion des appartenances aux groupes de sécurité dans Azure Active Directory. Cela peut éventuellement déléguer la tâche à vos administrateurs réseau.

## <a name="validate-roles"></a>Valider les rôles

Testez chaque rôle pour vérifier que le modèle est correctement filtré. Pour ce faire, il suffit d’utiliser la commande **Afficher en tant que** sous l’onglet de ruban **Modélisation**.

Lorsque le modèle a des règles dynamiques utilisant la fonction DAX [USERNAME](/dax/username-function-dax), veillez à tester les valeurs attendues _et inattendues_. Lors de l’incorporation de contenu Power BI, en particulier dans le scénario [L’application possède les données](../developer/embedded/embedding.md#embedding-for-your-customers), la logique de l’application peut passer n’importe quelle valeur comme nom d’utilisateur d’identité effectif. Dans la mesure du possible, vérifiez que des valeurs accidentelles ou malveillantes engendrent des filtres qui ne retournent aucune ligne.

Prenons un exemple de Power BI incorporé, où l’application transmet le rôle de travail de l’utilisateur en tant que nom d’utilisateur effectif : Il s’agit soit de « Manager » soit de « Worker ». Les Managers peuvent voir toutes les lignes, mais les Workers peuvent uniquement voir les lignes pour lesquelles la valeur de la colonne **Type** est « Internal ».

L’expression de règle suivante est définie :

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    TRUE()
)
```

Le problème avec cette expression de règle est que toutes les valeurs, à l’exception de « Worker », retournent _toutes les lignes de la table_. Ainsi, une valeur accidentelle, telle que « Wrker », retourne par inadvertance toutes les lignes de la table. Par conséquent, il est plus sûr d’écrire une expression qui teste chaque valeur attendue. Dans l’expression de règle améliorée suivante, une valeur inattendue n’entraîne le renvoi d’aucune ligne par la table.

```dax
IF(
    USERNAME() = "Worker",
    [Type] = "Internal",
    IF(
        USERNAME() = "Manager",
        TRUE(),
        FALSE()
    )
)
```

## <a name="design-partial-rls"></a>Créer une RLS partielle

Parfois, les calculs nécessitent des valeurs qui ne sont pas limitées par les filtres de la RLS. Par exemple, un rapport peut avoir besoin d’afficher la proportion du chiffre d’affaires réalisé pour la région de ventes de l’utilisateur du rapport au _chiffre d’affaires total_.

Bien qu’il ne soit pas possible pour une expression DAX de remplacer la RLS (en fait, elle ne peut même pas déterminer que la sécurité au niveau des lignes est appliquée), vous pouvez utiliser une table de modèle de synthèse. La table de modèle de synthèse est interrogée pour récupérer le chiffre d’affaires pour « toutes les régions » et n’est pas limitée par des filtres de la RLS.

Voyons comment vous pourriez implémenter cette exigence de conception. Tout d’abord, examinez la conception de modèle suivante :

:::image type="content" source="media/rls-guidance/mixed-rls-model.png" alt-text="Une image d’un diagramme de modèle est affichée. Elle est décrite dans les paragraphes suivants.":::

Le modèle comprend quatre tables :

- La table **Salesperson** stocke une ligne par vendeur. Elle comprend la colonne **EmailAddress**, qui stocke l’adresse e-mail de chaque commercial. Cette table est masquée.
- La table **Sales** stocke une ligne par commande. Elle comprend la mesure **Revenue % All Region**, qui est conçue pour renvoyer la proportion du chiffre d’affaires obtenu par la région de l’utilisateur du rapport par rapport au chiffre d’affaires réalisé par toutes les régions.
- La table **Date** stocke une ligne par date et permet de filtrer et de regrouper par année et par mois.
- **SalesRevenueSummary** est une table calculée. Elle stocke le chiffre d’affaires total pour chaque date de commande. Cette table est masquée.

L’expression suivante définit la table calculée **SalesRevenueSummary** :

```dax
SalesRevenueSummary =
SUMMARIZECOLUMNS(
    Sales[OrderDate],
    "RevenueAllRegion", SUM(Sales[Revenue])
)
```

> [!NOTE]
> Une [table d’agrégation](../transform-model/desktop-aggregations.md) peut répondre aux mêmes exigences de conception.

La règle RLS suivante est appliquée à la table **SalesPerson** :

```dax
[EmailAddress] = USERNAME()
```

Chacune des trois relations de modèle est décrite dans le tableau suivant :

|Relation|Description|
|---------|---------|
|![Indicateur de fin de l’organigramme 1.](media/common/icon-01-red-30x30.png)|Il existe une relation plusieurs-à-plusieurs entre les tables **Salesperson** et **Sales**. La règle RLS filtre la colonne **EmailAddress** de la table masquée **Salesperson** à l’aide de la fonction DAX [USERNAME](/dax/username-function-dax). La valeur de la colonne **Region** (pour l’utilisateur du rapport) est propagée vers la table **Sales**.|
|![Indicateur de fin de l’organigramme 2.](media/common/icon-02-red-30x30.png)|Il existe une relation un-à-plusieurs entre les tables **Date** et **Sales**.|
|![Indicateur de fin de l’organigramme 3.](media/common/icon-03-red-30x30.png)|Il existe une relation un-à-plusieurs entre les tables **Date** et **SalesRevenueSummary**.|

L’expression suivante définit la mesure **Revenue % All Region** :

```dax
Revenue % All Region =
DIVIDE(
    SUM(Sales[Revenue]),
    SUM(SalesRevenueSummary[RevenueAllRegion])
)
```

> [!NOTE]
> Veillez à éviter de divulguer des faits sensibles. S’il n’y a que deux régions dans cet exemple, il est possible pour un utilisateur de rapport de calculer le chiffre d’affaires de l’autre région.

## <a name="avoid-using-rls"></a>Éviter d’utiliser RLS

Évitez d’utiliser la sécurité au niveau des lignes aussi souvent qu’il est logique de le faire. Si vous n’avez qu’un petit nombre de règles RLS simples qui appliquent des filtres statiques, envisagez de publier plusieurs jeux de données à la place. Aucun des jeux de données ne définit de rôles, car chaque jeu de données contient des données pour une audience d’utilisateur de rapport spécifique, avec des autorisations de données communes. Créez ensuite un espace de travail par audience et attribuez des autorisations d’accès à l’espace de travail ou à l’application.

Par exemple, une société qui a seulement deux régions de vente décide de publier un jeu de données _pour chaque région de vente_ dans différents espaces de travail. Les jeux de données n’appliquent pas la sécurité au niveau des lignes. Toutefois, ils utilisent des [paramètres de requête](/power-query/power-query-query-parameters) pour filtrer les données sources. De cette façon, le même modèle est publié dans chaque espace de travail, mais avec des valeurs de paramètre de jeu de données différentes. Les commerciaux se voient attribuer l’accès à un seul des espaces de travail (ou une seule des applications publiées).

Éviter RLS présente plusieurs avantages :

- **Amélioration des performances des requêtes :** Cela peut entraîner une amélioration des performances en raison d’un nombre moins élevé de filtres.
- **Modèles plus petits :** Bien que cette façon de faire génère plus de modèles, la taille de ces derniers est plus petite. Les modèles plus petits peuvent améliorer la réactivité lors des requêtes et de l’actualisation des données, en particulier si la capacité d’hébergement subit une pression sur les ressources. En outre, il est plus facile de maintenir les tailles de modèle sous les limites de taille imposées par votre capacité. Enfin, il est plus facile d’équilibrer les charges de travail sur différentes capacités, car vous pouvez créer des espaces de travail sur (ou déplacer des espaces de travail vers) des capacités différentes.
- **Fonctionnalités supplémentaires :** Les fonctionnalités Power BI indisponibles avec la sécurité au niveau des lignes, comme [Publier sur le web](../collaborate-share/service-publish-to-web.md), peuvent être utilisées.

Toutefois, il existe des inconvénients associés à l’élimination de la sécurité au niveau des lignes :

- **Espaces de travail multiples :** Un espace de travail est requis pour chaque audience d’utilisateurs de rapport. Si des applications sont publiées, cela signifie également qu’il existe une application par audience d’utilisateurs de rapport.
- **Duplication de contenu :** Les rapports et les tableaux de bord doivent être créés dans chaque espace de travail. Cela nécessite un surplus d’efforts et de temps de configuration et de maintenance.
- **Utilisateurs avec des privilèges élevés :** Les utilisateurs dotés de privilèges élevés, qui appartiennent à plusieurs utilisateurs de rapports, ne peuvent pas voir une vue consolidée des données. Ils doivent ouvrir plusieurs rapports (à partir de différents espaces de travail ou applications).

## <a name="troubleshoot-rls"></a>Résolution des problèmes de RLS

Si la sécurité au niveau des lignes produit des résultats inattendus, vérifiez les problèmes suivants :

- Des relations incorrectes existent entre les tables de modèle, en termes de mappages de colonnes et de directions de filtre.
- La propriété de relation **Appliquer le filtre de sécurité dans les deux directions** n’est pas correctement définie. Pour plus d’informations, consultez [Guide des relations bidirectionnelles](relationships-bidirectional-filtering.md).
- Les tables ne contiennent pas de données.
- Des valeurs incorrectes sont chargées dans les tables.
- L’utilisateur est mappé à plusieurs rôles.
- Le modèle comprend des tables d’agrégation, et les règles RLS ne filtrent pas les agrégations et les détails de façon cohérente. Pour plus d’informations, consultez [Utiliser des agrégations dans Power BI Desktop (Sécurité au niveau des lignes pour les agrégations)](../transform-model/desktop-aggregations.md#rls-for-aggregations).

Lorsqu’un utilisateur spécifique ne peut pas voir de données, cela peut être dû au fait que son UPN n’est pas stocké ou qu’il n’est pas entré correctement. Cela peut se produire brusquement si leur compte d’utilisateur a changé suite à un changement de nom.

> [!TIP]
> À des fins de test, ajoutez une mesure qui retourne la fonction DAX [USERNAME](/dax/username-function-dax). Vous pouvez la nommer « Qui suis-je », par exemple. Ajoutez ensuite la mesure à un objet visuel de carte dans un rapport et publiez ce dernier sur Power BI.

Lorsqu’un utilisateur spécifique peut voir toutes les données, il est possible qu’il accède à des rapports directement dans l’espace de travail et qu’il s’agisse du propriétaire du jeu de données. La sécurité au niveau des lignes est appliquée uniquement lorsque :

- Le rapport est ouvert dans une application.
- Le rapport est ouvert dans un espace de travail, quand l’utilisateur est mappé au [rôle Observateur](../collaborate-share/service-new-workspaces.md#roles-in-the-new-workspaces).

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Sécurité au niveau des lignes (RLS) avec Power BI](../admin/service-admin-rls.md)
- [Restreindre l’accès aux données avec la sécurité au niveau des lignes (SNL) pour Power BI Desktop](../create-reports/desktop-rls.md)
- [Relations de modèle dans Power BI Desktop](../transform-model/desktop-relationships-understand.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
