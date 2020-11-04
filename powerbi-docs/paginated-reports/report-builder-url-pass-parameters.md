---
title: Passer un paramètre de rapport dans une URL pour un rapport paginé - Générateur de rapports Power BI
description: Cette rubrique explique comment passer des paramètres de rapport à un rapport en les incluant dans l’URL d’un rapport paginé.
ms.service: powerbi
ms.subservice: report-builder
ms.topic: how-to
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.custom: ''
ms.date: 05/01/2020
ms.openlocfilehash: f103f29c61d1a4e4a5340d97598d80a86c708701
ms.sourcegitcommit: ccf53e87ff7cba1fcd9d2cca761a561e62933f90
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2020
ms.locfileid: "93298034"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Passer un paramètre de rapport dans une URL pour un rapport paginé dans Power BI 

[!INCLUDE [applies-to](../includes/applies-to.md)] [!INCLUDE [yes-service](../includes/yes-service.md)] [!INCLUDE [yes-paginated](../includes/yes-paginated.md)] [!INCLUDE [yes-premium](../includes/yes-premium.md)] [!INCLUDE [no-desktop](../includes/no-desktop.md)] 

Vous pouvez passer des paramètres de rapport à un rapport en les incluant dans l’URL d’un rapport paginé. Tous les paramètres de requête peuvent avoir des paramètres de rapport correspondants. Ainsi, vous passez un paramètre de requête à un rapport en passant le paramètre de rapport correspondant. Vous devez préfixer le nom du paramètre avec `rp:` pour que Power BI le reconnaisse dans l’URL. 

Les paramètres de rapport sont sensibles à la casse et utilisent les caractères spéciaux suivants : 

- Un espace dans la partie des paramètres de l’URL est remplacé par un signe plus (+).  Par exemple : 

    ```rp:Holiday=Christmas+Day```

- Un point-virgule dans n’importe quelle partie de la chaîne est remplacé par les caractères `%3A`.

Les navigateurs doivent effectuer automatiquement l'encodage d'URL approprié. Vous n’avez pas besoin d’encoder les caractères manuellement. 

Pour définir un paramètre de rapport au sein d'une URL, utilisez la syntaxe suivante : 

```
rp:parameter=value
```

Par exemple, pour spécifier deux paramètres, « Salesperson » et « State », définis dans un rapport de votre espace de travail Mon espace de travail, vous devez utiliser l’URL suivante : 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Pour spécifier les deux mêmes paramètres définis dans un rapport d’une application, vous devez utiliser l’URL suivante : 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&rp:State=Utah 
```

Pour passer une valeur NULL pour un paramètre, utilisez la syntaxe suivante : 

```
parameter:isnull=true
```

Par exemple :

```
rp:SalesOrderNumber:isnull=true
```

Pour passer une valeur booléenne, utilisez 0 pour « false » et 1 pour « true ». Pour passer une valeur en virgule flottante, incluez le séparateur décimal des paramètres régionaux du serveur.

> [!NOTE]
> Si votre rapport contient un paramètre de rapport qui a une valeur par défaut et que la valeur de la propriété **Prompt** (Demander) est **false** (autrement dit, si la propriété **Demander à l’utilisateur** n’est pas sélectionnée dans le Gestionnaire de rapports), vous ne pouvez pas passer une valeur pour ce paramètre de rapport dans une URL. Ceci permet aux administrateurs d’empêcher les utilisateurs finaux d’ajouter ou de modifier les valeurs de certains paramètres de rapport.
> 
> Power BI ne prend pas en charge les chaînes de requête de plus de 2,000 caractères.  Cette valeur peut être dépassée si vous utilisez des paramètres d’URL pour afficher votre rapport paginé.  Cela est particulièrement vrai si vous utilisez des paramètres multivaleurs.

## <a name="additional-examples"></a>Exemples supplémentaires 

L’exemple d’URL suivant comprend un paramètre à valeurs multiples, « Salesperson ». Le format d’un paramètre à valeurs multiples est de répéter le nom du paramètre pour chaque valeur. 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:Salesperson=Mickey 
```

L’exemple d’URL suivant passe un seul paramètre SellStartDate avec la valeur « 7/1/2005 » pour un serveur de rapports en mode natif.

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:SellStartDate=7/1/2005
```

## <a name="next-steps"></a>Étapes suivantes

- [Paramètres d’URL dans les rapports paginés de Power BI](report-builder-url-parameters.md)
- [Présentation des rapports paginés dans Power BI Premium](paginated-reports-report-builder-power-bi.md)
