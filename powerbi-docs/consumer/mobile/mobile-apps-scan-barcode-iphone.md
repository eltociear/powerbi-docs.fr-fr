---
title: Scanner un code-barres à partir de l’application mobile Power BI
description: Scannez des codes-barres dans le monde réel pour accéder directement à des informations décisionnelles filtrées dans l’application mobile Power BI.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 12/02/2019
ms.author: painbar
ms.openlocfilehash: 043f27a2fb695811ac867689b4a63efdefded2e6
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "80802046"
---
# <a name="scan-a-barcode-with-your-device-from-the-power-bi-mobile-app"></a>Scanner un code-barres avec votre appareil à partir de l’application mobile Power BI
Scannez des codes-barres dans le monde réel pour accéder directement à des informations décisionnelles filtrées dans l’application mobile Power BI.


S’applique à :

| ![iPhone](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![iPad](./media/mobile-apps-qr-code/ios-logo-40-px.png) | ![Téléphone Android](././media/mobile-apps-qr-code/android-logo-40-px.png) | ![Tablette Android](././media/mobile-apps-qr-code/android-logo-40-px.png) |
|:--- |:--- |:--- |:--- |
|iPhone |iPad |Téléphones Android |Tablettes Android |

Supposons qu’un collègue ait [marqué un champ de code-barres dans un rapport Power BI Desktop](../../desktop-mobile-barcodes.md) et partagé le rapport avec vous. 

![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-scanner.png)

Quand vous scannez un code-barres de produit avec le scanner de l’application Power BI de votre appareil, vous voyez le rapport (ou une liste de rapports) avec ce code-barres. Vous pouvez ouvrir ce rapport filtré selon ce code-barres.

## <a name="scan-a-barcode-with-the-power-bi-scanner"></a>Scanner un code-barres avec le scanner de Power BI
1. Dans la barre de navigation, appuyez sur **Autres options** (...), puis sur **Scanneur**.

    ![](media/mobile-apps-scan-barcode-iphone/power-bi-scanner.png)

2. Si votre appareil photo n’est pas activé, vous devez autoriser l’application Power BI à l’utiliser. Il s’agit d’une autorisation à usage unique. 
4. Pointez le scanner sur un code-barres de produit. Une liste des rapports associés à ce code-barres s’affiche.
5. Appuyez sur le nom du rapport, automatiquement filtré selon ce code-barres, pour l’ouvrir sur votre appareil.

## <a name="filter-by-other-barcodes-while-in-a-report"></a>Filtrer selon d’autres codes-barres dans un rapport
Quand vous consultez un rapport filtré selon un code-barres sur votre appareil, vous pouvez filtrer ce rapport en fonction d’un autre code-barres.

* Si l’icône de code-barres contient un filtre ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-filtered-icon-black.png), cela signifie que le filtre est actif et que le rapport est déjà filtré selon un code-barres. 
* Si l’icône ne contient pas de filtre ![](media/mobile-apps-scan-barcode-iphone/power-bi-barcode-unfiltered-icon.png), cela signifie que le filtre est inactif et que le rapport n’a pas été filtré selon un code-barres. 

Dans ces deux cas, appuyez sur l’icône pour ouvrir un petit menu avec un scanner flottant.

* Dirigez le scanner sur le nouvel élément pour modifier la valeur de code-barres du filtre du rapport. 
* Sélectionnez **Effacer le filtre à code-barres** pour rétablir le rapport non filtré.
* Sélectionnez **Filtrer par codes-barres récents** pour remplacer le filtre du rapport par l’un des codes-barres que vous avez scannés durant la session active.

## <a name="issues-with-scanning-a-barcode"></a>Problèmes lors de la lecture d’un code-barres
Les messages suivants peuvent s’afficher quand vous scannez le code-barres d’un produit.

### <a name="couldnt-filter-report"></a>« Impossible de filtrer le rapport... »
Le rapport à filtrer est basé sur un modèle de données qui ne comprend pas cette valeur de code-barres. Par exemple, le produit « eau minérale » n’est pas inclus dans le rapport.  

### <a name="allsome-of-the-visuals-in-the-report-dont-contain-any-value"></a>Tous les visuels du rapport ou une partie d’entre eux ne contiennent aucune valeur
La valeur de code-barres que vous avez scannée existe dans votre modèle, mais tous les visuels de votre rapport ou une partie d’entre eux ne contiennent pas cette valeur et, par conséquent, le filtrage va renvoyer un état vide. Essayez de consulter d’autres pages du rapport ou modifiez vos rapports dans Power BI Desktop afin qu’ils contiennent cette valeur. 

### <a name="looks-like-you-dont-have-any-reports-that-can-be-filtered-by-barcodes"></a>« Apparemment, vous n’avez aucun rapport pouvant être filtré par code-barres. »
Cela signifie que vous n’avez aucun rapport prenant en charge les codes-barres. Le scanner de codes-barres peut filtrer uniquement les rapports qui possèdent une colonne marquée **Code-barres**.  

Vérifiez que vous ou le propriétaire du rapport avez marqué une colonne **Code-barres** dans Power BI Desktop. En savoir plus sur [le marquage d’un champ de code-barres dans Power BI Desktop](../../desktop-mobile-barcodes.md)

### <a name="couldnt-filter-report---looks-like-this-barcode-doesnt-exist-in-the-report-data"></a>« Impossible de filtrer le rapport - Il semble que ce code-barres n’existe pas dans les données du rapport. »
Le rapport que vous avez choisi de filtrer est basé sur un modèle de données qui ne comprend pas cette valeur de code-barres. Par exemple, le produit « eau minérale » n’est pas inclus dans le rapport. Vous pouvez scanner un autre produit, choisir un autre rapport (si plusieurs rapports sont disponibles) ou afficher le rapport sans filtrage. 

## <a name="next-steps"></a>Étapes suivantes
* [Marquer un champ de code-barres dans Power BI Desktop](../../desktop-mobile-barcodes.md)
* [Vignettes d’un tableau de bord dans Power BI](../end-user-tiles.md)
* [Tableaux de bord dans Power BI](../end-user-dashboards.md)

