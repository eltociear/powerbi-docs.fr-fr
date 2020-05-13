---
title: Filtrage croisé bidirectionnel dans Power BI Desktop
description: Activer le filtrage croisé bidirectionnel avec DirectQuery dans Power BI Desktop
author: davidiseminger
ms.reviewer: ''
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 01/15/2020
ms.author: davidi
LocalizationGroup: Connect to data
ms.openlocfilehash: 141dabdce7816d21c49d8c7f98d1438c2fc20e8d
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83339096"
---
# <a name="enable-bidirectional-cross-filtering-for-directquery-in-power-bi-desktop"></a>Activer le filtrage croisé bidirectionnel pour DirectQuery dans Power BI Desktop

Quand ils filtrent les tables pour voir les données dont ils ont besoin, les créateurs de rapports et les modélisateurs de données ont parfois du mal à savoir comment appliquer les filtres à un rapport. Avant, le contexte de filtre de la table était conservé d’un seul côté de la relation. Cette conception amenait souvent à créer une formule DAX complexe pour obtenir les résultats souhaités.

Avec le filtrage croisé bidirectionnel, les créateurs de rapports et les modélisateurs de données peuvent désormais mieux contrôler l’application des filtres avec les tables associées. Le filtrage croisé bidirectionnel leur permet d’appliquer des filtres des *deux* côtés d’une relation de table. Il est possible d’appliquer les filtres en propageant le contexte de filtre vers une deuxième table associée de l’autre côté de la relation de table.

## <a name="enable-bidirectional-cross-filtering-for-directquery"></a>Activer le filtrage croisé bidirectionnel pour DirectQuery

Vous pouvez activer le filtrage croisé dans la boîte de dialogue **Modifier la relation**. Pour activer le filtrage croisé dans une relation, vous devez configurer les options suivantes :

* Définissez l’option **Direction du filtrage croisé** sur **À double sens**.
* Sélectionnez **Appliquer le filtre de sécurité dans les deux directions**.

  ![Configurez le filtrage bidirectionnel dans Power BI Desktop.](media/desktop-bidirectional-filtering/bidirectional-filtering_2.png)

> [!NOTE]
> Quand vous créez des formules DAX de filtrage croisé dans Power BI Desktop, utilisez *UserPrincipalName*. Ce champ correspond souvent au nom de connexion d’un utilisateur, par exemple <em>joe@contoso.com</em>, au lieu de *UserName*. Par conséquent, vous devrez peut-être créer une table associée qui mappe *UserName* ou *EmployeeID* à *UserPrincipalName*.

Pour obtenir plus d’informations et des exemples d’utilisation du filtrage croisé bidirectionnel, consultez le [livre blanc sur le filtrage croisé bidirectionnel pour Power BI Desktop](https://download.microsoft.com/download/2/7/8/2782DF95-3E0D-40CD-BFC8-749A2882E109/Bidirectional%20cross-filtering%20in%20Analysis%20Services%202016%20and%20Power%20BI.docx).

