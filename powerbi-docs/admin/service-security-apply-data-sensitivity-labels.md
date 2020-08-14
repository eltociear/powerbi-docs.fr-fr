---
title: Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI
description: Découvrez comment appliquer des étiquettes de sensibilité dans Power BI
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 08/10/2020
ms.author: painbar
LocalizationGroup: Data from files
ms.openlocfilehash: be2f98341abd581cd2df717d19b3a9110548a2ec
ms.sourcegitcommit: 9e39232cbc28d8b39dfec5496db7ece9837b5e53
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/10/2020
ms.locfileid: "88049204"
---
# <a name="how-to-apply-sensitivity-labels-in-power-bi"></a>Guide pratique pour appliquer des étiquettes de sensibilité dans Power BI

Les étiquettes de sensibilité de Microsoft Information Protection sur vos rapports, tableaux de bord, jeux de données et dataflows peuvent protéger votre contenu sensible contre les accès non autorisés aux données et contre les fuites de données. L’étiquetage correct des données avec des étiquettes de sensibilité garantit que seules les personnes autorisées peuvent accéder à vos données. Cet article explique comment appliquer des étiquettes de sensibilité à votre contenu.

Pour pouvoir appliquer des étiquettes de sensibilité dans Power BI :
* Vous devez disposer d’une licence Power BI Pro et d’autorisations de modification sur le contenu que vous souhaitez étiqueter.
* Vous devez appartenir à un groupe de sécurité qui dispose des autorisations nécessaires pour appliquer des étiquettes de sensibilité, comme décrit dans l’article intitulé [Activer les étiquettes de sensibilité dans Power BI](./service-security-enable-data-sensitivity-labels.md).
* Toutes les [Licences et autres configurations requises](./service-security-enable-data-sensitivity-labels.md#licensing-and-requirements) doivent être respectées.

Pour plus d’informations sur les étiquettes de sensibilité dans Power BI, consultez [Étiquettes de sensibilité dans Power BI](service-security-sensitivity-label-overview.md).

## <a name="applying-sensitivity-labels"></a>Application d’étiquettes de sensibilité

Quand la protection des données est activée sur votre locataire, les étiquettes de sensibilité apparaissent dans la colonne de sensibilité dans la vue Liste des tableaux de bord, des rapports, des jeux de données et des dataflows.

![Activer les étiquettes de sensibilité](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-01.png)

**Pour appliquer ou modifier une étiquette de sensibilité sur un rapport ou un tableau de bord**
1. Cliquez sur **Plus d’options (...)** .
1. Sélectionnez **Paramètres**.
1. Dans le volet latéral des paramètres, choisissez l’étiquette de sensibilité appropriée.
1. Enregistrez les paramètres.

L’image suivante montre ces étapes sur un rapport

![Définir des étiquettes de sensibilité](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-02.png)

**Pour appliquer ou modifier une étiquette de sensibilité sur un jeu de données ou un dataflow**

1. Cliquez sur **Plus d’options (...)** .
1. Sélectionnez **Paramètres**.
1. Dans le volet latéral des paramètres, choisissez l’étiquette de sensibilité appropriée.
1. Appliquez les paramètres.

Les deux images suivantes montrent ces étapes sur un jeu de données.

Choisissez **Plus d’options (...)** , puis **Paramètres**.

![Ouvrir les paramètres du jeu de données](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-05.png)

Dans la page des paramètres, ouvrez la section Étiquette de sensibilité, choisissez l’étiquette de sensibilité souhaitée, puis cliquez sur **Appliquer**.

![Choisir une étiquette de sensibilité](media/service-security-apply-data-sensitivity-labels/apply-data-sensitivity-labels-06.png)

## <a name="removing-sensitivity-labels"></a>Suppression des étiquettes de sensibilité
Pour supprimer une étiquette de sensibilité d’un rapport, d’un tableau de bord, d’un jeu de données ou d’un flux de données, suivez la [même procédure que celle utilisée pour appliquer des étiquettes](#applying-sensitivity-labels), mais choisissez **(Aucune)** quand vous êtes invité à classifier la sensibilité des données. 

## <a name="considerations-and-limitations"></a>Considérations et limitations

Consultez [Étiquettes de sensibilité dans Power BI](service-security-sensitivity-label-overview.md#limitations) pour obtenir la liste des limitations relatives aux étiquettes de sensibilité dans Power BI.

## <a name="next-steps"></a>Étapes suivantes

L’objectif de cet article était d’expliquer comment appliquer des étiquettes de sensibilité dans Power BI. Les articles suivants fournissent plus de détails sur la protection des données dans Power BI. 

* [Vue d’ensemble des étiquettes de sensibilité dans Power BI](./service-security-sensitivity-label-overview.md)
* [Activer les étiquettes de sensibilité dans Power BI](./service-security-enable-data-sensitivity-labels.md)
* [Utilisation de contrôles Microsoft Cloud App Security dans Power BI](./service-security-using-microsoft-cloud-app-security-controls.md)