---
title: Utilisation de tables calculées dans Power BI Desktop
description: Tables calculées dans Power BI Desktop
services: powerbi
documentationcenter: ''
author: davidiseminger
manager: kfile
backup: ''
editor: ''
tags: ''
qualityfocus: no
qualitydate: ''
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 04/24/2018
ms.author: davidi
LocalizationGroup: Model your data
ms.openlocfilehash: 3b7e3204d918c84acaff1b98bbab0fc09c6f0b87
ms.sourcegitcommit: 3f2f254f6e8d18137bae879ddea0784e56b66895
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2018
---
# <a name="using-calculated-tables-in-power-bi-desktop"></a>Utilisation de tables calculées dans Power BI Desktop
Avec les tables calculées, vous pouvez ajouter une nouvelle table au modèle. Toutefois, au lieu d’interroger et de charger les valeurs dans les colonnes de votre nouvelle table à partir d’une source de données, vous créez une formule DAX (Data Analysis Expressions) qui définit les valeurs de la table. Dans Power BI Desktop, vous pouvez créer des tables calculées à l’aide de la fonctionnalité Nouvelle table dans la vue Rapport ou Données.

La plupart du temps, vous importez des données dans votre modèle à partir d’une source de données externe. Toutefois, les tables calculées procurent certains avantages. Elles sont généralement plus adaptées aux calculs intermédiaires et aux données que vous souhaitez stocker dans le cadre du modèle plutôt que calculer à la volée ou dans le cadre d’une requête.

Contrairement aux tables créées dans le cadre d’une requête, les tables calculées créées dans la vue Rapport ou Données sont basées sur des données que vous avez déjà chargées dans le modèle. Par exemple, vous pouvez choisir d’effectuer l’union ou la jointure croisée de deux tables.

Tout comme les tables normales, les tables calculées peuvent avoir des relations avec d’autres tables. Les colonnes de votre table calculée ont des types de données et une mise en forme, et elles peuvent appartenir à une catégorie de données. Vous pouvez nommer vos colonnes comme vous le souhaitez et les ajouter à une visualisation de rapport comme d’autres champs. Les tables calculées sont recalculées si l’une des tables à partir desquelles elles extraient des données sont actualisées ou mises à jour.

Les tables calculées calculent les résultats en utilisant [DAX (Data Analysis Expressions)](https://msdn.microsoft.com/library/gg413422.aspx), langage de formule conçu pour fonctionner avec les données relationnelles comme dans Power BI Desktop. Le langage DAX inclut une bibliothèque de plus de 200 fonctions, opérateurs et constructions. Il offre ainsi une flexibilité considérable pour créer des formules afin d’effectuer les calculs nécessaires pour quasiment tout type d’analyse de données.

## <a name="lets-look-at-an-example"></a>Examinons un exemple.
Jeff, chef de projet chez Contoso, a une table avec les employés de la région Nord-ouest et une autre table avec les employés de la région Sud-ouest. Il souhaite rassembler ces deux tables dans une seule table.

**NorthwestEmployees**

 ![](media/desktop-calculated-tables/calctables_nwempl.png)

**SoutwestEmployees**

 ![](media/desktop-calculated-tables/calctables_swempl.png)

Il est très facile de rassembler ces deux tables avec une table calculée. Jeff peut créer une table calculée dans la vue Rapport ou Données, mais c’est un peu plus facile dans la vue Données car il peut tout de suite voir sa nouvelle table calculée.

Dans la **Vue de données**, sous l’onglet **Modélisation** , Jeff clique sur **Nouvelle table**. Une barre de formule apparaît.

 ![](media/desktop-calculated-tables/calctables_formulabarempty.png)

Jeff entre ensuite la formule suivante :

 ![](media/desktop-calculated-tables/calctables_formulabarformula.png)

Une nouvelle table nommée Western Region Employees est créée.

 ![](media/desktop-calculated-tables/calctables_westregionempl.png)

La nouvelle table « Western Region Employees » de Jeff apparaît comme toute autre table dans la liste Champs. Il peut créer des relations avec d’autres tables, ajouter des mesures et des colonnes calculées, et ajouter ses champs à des rapports comme avec toute autre table.

 ![](media/desktop-calculated-tables/calctables_fieldlist.png)

## <a name="functions-for-calculated-tables"></a>Fonctions pour les tables calculées
Les tables calculées peuvent être définies par toute expression DAX qui retourne une table, y compris une simple référence à une autre table. Par exemple :

 ![](media/desktop-calculated-tables/calctables_formulabarsimpleformula.png)

Vous pouvez utiliser des tables calculées avec DAX pour résoudre de nombreux problèmes analytiques. Nous vous avons fourni ici une brève introduction aux tables calculées. Voici quelques-unes des fonctions de table DAX les plus courantes qui pourront vous être utiles quand vous commencerez à travailler avec des tables calculées :

* DISTINCT
* VALUES
* CROSSJOIN
* UNION
* NATURALINNERJOIN
* NATURALLEFTOUTERJOIN
* INTERSECT
* CALENDAR
* CALENDARAUTO

Pour plus d’informations sur ces fonctions et sur d’autres fonctions DAX qui retournent des tables, consultez la [Référence des fonctions DAX](https://msdn.microsoft.com/ee634396.aspx).

