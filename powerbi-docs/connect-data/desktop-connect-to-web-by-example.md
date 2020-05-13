---
title: Extraire les données d’une page web, par exemple dans Power BI Desktop
description: Extraire les données d’une page web en fournissant un exemple de ce que vous voulez extraire
author: davidiseminger
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/21/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 2a1fa08d01cfb05398e82cfc521d4a532ecd13ec
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83294200"
---
# <a name="get-webpage-data-by-providing-examples"></a>Obtenir des données de page web en fournissant des exemples

L’obtention des données d’une page web permet aux utilisateurs d’extraire facilement les données de pages web et d’importer ces données dans *Power BI Desktop*. Cependant, les données des pages web figurent souvent dans des tables mal organisées et donc difficiles à extraire. L’obtention de données à partir de ces pages peut être compliquée, même si les données sont structurées et cohérentes.

Mais il existe une solution. Avec la fonctionnalité *Obtenir les données du web par exemple*, vous pouvez indiquer à Power BI Desktop les données à extraire en fournissant un ou plusieurs exemples dans la boîte de dialogue du connecteur. Power BI Desktop collecte les autres données sur la page qui correspondent à vos exemples. Cette solution vous permet d’extraire toutes sortes de données de pages web, y compris les données de tables *et* d’autres données ne figurant pas dans des tables.

![Obtenir les données du web par exemple](media/desktop-connect-to-web-by-example/web-by-example_01.png)

Les prix dans les graphiques sont uniquement indiqués à titre d’exemple.

## <a name="using-get-data-from-web-by-example"></a>Utilisation de l’option Obtenir les données du web par exemple

Sélectionnez **Obtenir des données** dans le menu du ruban **Accueil**. Dans la boîte de dialogue qui s’affiche, sélectionnez **Autres** parmi les catégories dans le volet gauche, puis choisissez **Web**. Sélectionnez **Connexion** pour continuer.

![sélectionner Web dans Obtenir les données](media/desktop-connect-to-web-by-example/web-by-example_03.png)

Dans **À partir du web**, entrez l’URL de la page web de laquelle vous souhaitez extraire des données. Dans cet article, nous allons utiliser la page web du Microsoft Store pour montrer le fonctionnement de ce connecteur.

Si vous souhaitez suivre la procédure, vous pouvez utiliser l’[URL du Microsoft Store](https://www.microsoft.com/store/top-paid/games/xbox?category=classics) mentionnée dans cet article :

    https://www.microsoft.com/store/top-paid/games/xbox?category=classics

![Boîte de dialogue web](media/desktop-connect-to-web-by-example/web-by-example_04.png)

Quand vous sélectionnez **OK**, vous êtes dirigé vers la boîte de dialogue **Navigateur**, où sont présentées toutes les tables ayant été automatiquement détectées dans la page web. Dans le cas illustré dans l’image ci-dessous, aucune table n’a été trouvée. Sélectionnez **Ajouter une table à l’aide des exemples** pour fournir des exemples.

![Fenêtre du navigateur](media/desktop-connect-to-web-by-example/web-by-example_05.png)

**Ajouter une table à l’aide des exemples** présente une fenêtre interactive qui donne un aperçu du contenu de la page web. Entrez les exemples de valeurs des données que vous souhaitez extraire.

Dans cet exemple, nous allons extraire le *nom* et le *prix* de chacun des jeux dans la page. Pour cela, nous spécifions quelques exemples provenant de la page pour chaque colonne. Quand vous entrez les exemples, *Power Query* extrait les données qui correspondent au modèle des exemples d’entrées à l’aide d’algorithmes d’extraction de données intelligents.

![données par exemple](media/desktop-connect-to-web-by-example/web-by-example_06.png)

> [!NOTE]
> Les suggestions de valeurs incluent uniquement les valeurs inférieures ou égales à 128 caractères en longueur.

Une fois que vous avez extrait toutes les données souhaitées de la page web, sélectionnez **OK** pour accéder à l’éditeur Power Query. Vous pouvez appliquer d’autres transformations ou mettre en forme les données, notamment en combinant ces données avec d’autres données de nos sources.

![données par exemple](media/desktop-connect-to-web-by-example/web-by-example_07.png)

De là, vous pouvez créer des visuels ou bien utiliser les données de la page web pour créer des rapports dans Power BI Desktop.

## <a name="next-steps"></a>Étapes suivantes

Vous pouvez connecter toutes sortes de données à l’aide de Power BI Desktop. Pour plus d’informations sur les sources de données, consultez les ressources suivantes :

* [Ajouter une colonne à partir d’un exemple dans Power BI Desktop](../create-reports/desktop-add-column-from-example.md)
* [Se connecter à des pages web à partir de Power BI Desktop](desktop-connect-to-web.md)
* [Sources de données dans Power BI Desktop](desktop-data-sources.md)
* [Mettre en forme et combiner des données dans Power BI Desktop](desktop-shape-and-combine-data.md)
* [Se connecter à des classeurs Excel dans Power BI Desktop](desktop-connect-excel.md)
* [Se connecter à des fichiers CSV dans Power BI Desktop](desktop-connect-csv.md)
* [Entrer des données directement dans Power BI Desktop](desktop-enter-data-directly-into-desktop.md)
