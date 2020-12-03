---
title: Création de tables de dates dans Power BI Desktop
description: Techniques et conseils pour la création de tables de dates dans Power BI Desktop.
author: peter-myers
ms.author: v-pemyer
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 06/24/2020
ms.openlocfilehash: 9040fb54e51dfeecad853e5ba980f423ab48e908
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96417839"
---
# <a name="create-date-tables-in-power-bi-desktop"></a>Création de tables de dates dans Power BI Desktop

Cet article s’adresse principalement aux modélisateurs de données qui utilisent Power BI Desktop. Il décrit les bonnes pratiques de conception pour la création de tables de dates dans des modèles de données.

Pour utiliser les [fonctions Time Intelligence](/dax/time-intelligence-functions-dax) DAX (Data Analysis Expressions), vous devez respecter un prérequis : votre modèle doit comporter au moins une _table de dates_. Une table de dates est une table qui répond aux exigences suivantes :

> [!div class="checklist"]
> - Elle doit avoir une colonne dont le type de données est **date** (ou **date/heure**), appelée _colonne de dates_.
> - La colonne de dates doit contenir des valeurs uniques.
> - La colonne de dates ne doit pas contenir de valeurs vides.
> - Il ne doit pas y avoir de dates manquantes dans la colonne de dates.
> - La colonne de dates doit couvrir des années entières. Une année n’est pas nécessairement une année civile (janvier-décembre).
> - La table de dates doit être [marquée comme table de dates](../transform-model/desktop-date-tables.md#setting-your-own-date-table).

Vous pouvez utiliser l’une des techniques suivantes pour ajouter une table de dates à votre modèle :

- L’option date/heure automatique
- Power Query pour se connecter à une table de dimensions de dates
- Power Query pour générer une table de dates
- DAX pour générer une table de dates
- DAX pour cloner une table de dates existante

> [!TIP]
> La table de dates constitue peut-être la fonctionnalité la plus cohérente que l’on puisse ajouter à un modèle. De plus, elle doit être définie de manière cohérente au sein d’une organisation. Par conséquent, quelle que soit la technique utilisée, nous vous recommandons de créer un [modèle Power BI Desktop](../create-reports/desktop-templates.md) incluant une table de dates entièrement configurée. Partagez le modèle avec tous les concepteurs de votre organisation. Ainsi, chaque fois que l’un d’eux développera un nouveau modèle, il pourra partir d’une table de dates définie de manière cohérente.

## <a name="use-auto-datetime"></a>Date/heure automatique

L'option [Date/heure automatique](../transform-model/desktop-auto-date-time.md) fournit une intelligence temporelle pratique, rapide et conviviale. Les auteurs de rapports peuvent utiliser l'intelligence temporelle lorsqu'ils filtrent, regroupent et analysent des périodes de temps du calendrier.

Nous vous recommandons de ne maintenir activée l’option date/heure automatique que si vous travaillez sur des périodes civiles et avec des exigences de modèle simplistes par rapport au temps. L'utilisation de cette option peut également être pratique lors de la création de modèles ad hoc ou de l'exploration ou du profilage de données. Toutefois, cette approche ne permet pas de gérer le cas où une seule conception de table de dates peut propager des filtres à plusieurs tables. Pour plus d’informations, consultez [Aide sur l’option date/heure automatique dans Power BI Desktop](auto-date-time.md).

## <a name="connect-with-power-query"></a>Connexion avec Power Query

Si votre source de données contient déjà une table de dates, nous vous recommandons de l’utiliser comme source de votre modèle de table de dates. C’est généralement le cas en cas de connexion à un entrepôt de données, car ils comportent habituellement une table de dimensions de dates. Ainsi, votre modèle s’appuie sur une seule source de vérité pour le temps dans votre organisation.

Si vous développez un modèle DirectQuery et que votre source de données n’inclut pas de table de dates, nous vous recommandons vivement d’en ajouter une à la source de données. Elle doit remplir toutes les exigences de modélisation d’une table de dates. Vous pouvez ensuite utiliser Power Query pour vous y connecter. Vos calculs de modèle pourront ainsi tirer parti des capacités Time Intelligence de DAX.

## <a name="generate-with-power-query"></a>Génération avec Power Query

Il est possible de générer une table de dates à l’aide de Power Query. Voici deux entrées de blog qui expliquent comment faire :

- [Creating a Date Dimension with a Power Query Script](https://www.mattmasson.com/2014/02/creating-a-date-dimension-with-a-power-query-script/) de Matt Masson (en anglais)
- [Generating A Date Dimension Table In Power Query](https://blog.crossjoin.co.uk/2013/11/19/generating-a-date-dimension-table-in-power-query/) de Chris Webb (en anglais)

> [!TIP]
> Si vous ne disposez pas d’un entrepôt de données ou d’une autre définition cohérente du temps dans votre organisation, envisagez d’utiliser Power Query pour publier un [dataflow](../transform-model/dataflows/dataflows-introduction-self-service.md). Ensuite, demandez à tous les concepteurs de données de se connecter au dataflow pour ajouter des tables de dates à leurs modèles. Ainsi, votre modèle devient la seule source de vérité pour le temps dans votre organisation.

Si vous devez générer une table de dates, envisagez de le faire avec DAX. Vous trouverez peut-être cette solution plus facile. Elle se révèlera par ailleurs probablement plus pratique, car DAX comprend des fonctionnalités intelligentes intégrées qui simplifient la création et la gestion des tables de dates.

## <a name="generate-with-dax"></a>Génération avec DAX

Il est possible de générer une table de dates dans un modèle en créant une table calculée à l’aide des fonctions DAX [CALENDAR](/dax/calendar-function-dax) et [CALENDARAUTO](/dax/calendarauto-function-dax). Chacune d’elles retourne une table de dates à une seule colonne. Vous pouvez ensuite étendre la table calculée avec des colonnes calculées pour gérer vos exigences de filtrage et de regroupement d’intervalles de dates.

- Utilisez la fonction **CALENDAR** lorsque vous souhaitez définir une plage de dates. Vous lui transmettez deux valeurs : la date de début et la date de fin. Ces valeurs peuvent être définies par d’autres fonctions DAX, comme `MIN(Sales[OrderDate])` ou `MAX(Sales[OrderDate])`.
- Utilisez la fonction **CALENDARAUTO** si vous souhaitez que la plage de dates englobe automatiquement toutes les dates stockées dans le modèle. Vous pouvez transmettre un seul paramètre facultatif correspondant au dernier mois de l’année (ce n’est pas nécessaire si votre année est une année civile, qui se termine en décembre). Il s’agit d’une fonction utile, car elle garantit que des années entières de dates sont retournées, ce qui fait partie des exigences des table de dates marquées. De plus, vous n’avez pas besoin de gérer l’extension de la table pour les années à venir : à la fin de chaque actualisation des données, le recalcul de la table est déclenché, ce qui permet d’étendre automatiquement la plage de dates de la table lorsque les dates d’une nouvelle année sont chargées dans le modèle.

## <a name="clone-with-dax"></a>Clonage avec DAX

Si votre modèle comporte déjà une table de dates et qu’il vous en faut une autre, vous pouvez facilement cloner la première. C’est le cas quand la date est une [dimension de rôle actif](star-schema.md#role-playing-dimensions). Pour cloner une table, vous pouvez créer une table calculée. L’expression de table calculée correspond simplement au nom de la table de dates existante.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Date/heure automatique dans Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Conseils sur les dates/heures automatiques dans Power BI Desktop](auto-date-time.md)
- [Définir et utiliser des tables de dates dans Power BI Desktop](../transform-model/desktop-date-tables.md)
- [Préparation des données en libre-service dans Power BI](../transform-model/dataflows/dataflows-introduction-self-service.md)
- [Fonction CALENDAR (DAX)](/dax/calendar-function-dax)
- [Fonction CALENDARAUTO (DAX)](/dax/calendarauto-function-dax)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)