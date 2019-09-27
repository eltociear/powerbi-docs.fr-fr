---
title: Passer un paramètre de rapport dans une URL pour un rapport paginé - Générateur de rapports Power BI
description: Cette rubrique explique comment passer des paramètres de rapport à un rapport en les incluant dans l’URL d’un rapport paginé.
ms.service: powerbi
ms.subservice: report-builder
ms.custom: ''
ms.topic: conceptual
author: maggiesMSFT
ms.author: maggies
ms.reviewer: cfinlan
ms.date: 08/29/2019
ms.openlocfilehash: f7f1b777e7c4e54dbdcfb1757fe4df274624a580
ms.sourcegitcommit: a97c0c34f888e44abf4c9aa657ec9463a32be06f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71076000"
---
# <a name="pass-a-report-parameter-in-a-url-for-a-paginated-report-in-power-bi"></a>Passer un paramètre de rapport dans une URL pour un rapport paginé dans Power BI 

Vous pouvez passer des paramètres de rapport à un rapport en les incluant dans l’URL d’un rapport paginé. Tous les paramètres de requête peuvent avoir des paramètres de rapport correspondants. Ainsi, vous passez un paramètre de requête à un rapport en passant le paramètre de rapport correspondant. Vous devez préfixer le nom du paramètre avec `rp:` pour que Power BI le reconnaisse dans l’URL. 

Les paramètres de rapport sont sensibles à la casse et utilisent les caractères spéciaux suivants : 

- Un espace dans la partie des paramètres de l’URL est remplacé par un signe plus (+).  Par exemple : 

    ```rp:Holiday=Christmas+Day```

- Un point-virgule dans n’importe quelle partie de la chaîne est remplacé par les caractères `%3A`.

Les navigateurs doivent normalement effectuer automatiquement l’encodage approprié de l’URL. Vous n’avez pas besoin d’encoder les caractères manuellement. 

Pour définir un paramètre de rapport dans une URL, utilisez la syntaxe suivante : 

```
rp:parameter=value
```

Par exemple, pour spécifier deux paramètres, « Salesperson » et « State », définis dans un rapport de votre espace de travail Mon espace de travail, vous devez utiliser l’URL suivante : 

```
https://app.powerbi.com/groups/me/rdlreports/xxxxxxx-abc7-40f0-b456-febzf9cdda4d?rp:Salesperson=Tie+Bear&rp:State=Utah 
```

Pour spécifier les deux mêmes paramètres définis dans un rapport d’une application, vous devez utiliser l’URL suivante : 

```
https://app.powerbi.com/groups/me/apps/xxxxxxx-c4c4-4217-afd9-3920a0d1e2b0/rdlreports/b1d5e659-639e-41d0-b733-05d2bca9853c?rp:Salesperson=Tiggee&State=Utah 
```

Pour passer une valeur null pour un paramètre, utilisez la syntaxe suivante : 

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
