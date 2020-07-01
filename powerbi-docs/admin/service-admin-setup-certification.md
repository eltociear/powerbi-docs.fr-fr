---
title: Configurer la certification de jeux de données et de dataflows (préversion)
description: Découvrez comment configurer la certification de jeux de données et de dataflows dans votre organisation.
author: paulinbar
ms.service: powerbi
ms.subservice: powerbi-eim
ms.topic: how-to
ms.date: 05/15/2020
ms.author: painbar
LocalizationGroup: Share your work
ms.openlocfilehash: 41247a6dbee2ba6c4c5181a4646df735e43f8b18
ms.sourcegitcommit: eef4eee24695570ae3186b4d8d99660df16bf54c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85227529"
---
# <a name="set-up-dataset-and-dataflow-certification-preview"></a>Configurer la certification de jeux de données et de dataflows (préversion)

Votre organisation peut certifier des jeux de données et des dataflows qui sont les sources d’autorité d’informations importantes.

En tant qu’administrateur de locataire Power BI, vous êtes responsable de la configuration du processus de certification pour votre organisation. La procédure est la suivante :
* Activation de la certification sur votre locataire
* Définition d’une liste de groupes et d’utilisateurs autorisés à certifier des jeux de données et des dataflows
* Pour les jeux de données, spécification de l’URL de la stratégie de certification de jeu de données de l’organisation, si elle existe

La certification de jeu de données et de flux de données fait partie de l’*approbation* des jeux de données et des dataflows. Pour plus d’informations, consultez [Approbation de jeu de données](../connect-data/service-datasets-promote.md) et [Approbation de dataflow](../transform-model/service-dataflows-promote-certify.md).


## <a name="set-up-certification"></a>Configurer la certification

1. Dans le portail d’administration, accédez à Paramètres du locataire.
1. Dans la section Paramètres d’exportation et de partage, développez la section Certification.

   ![Configurer la certification de jeux de données et de dataflows](media/service-admin-setup-certification/service-admin-certification-setup-dialog.png)

1. Définissez le bouton bascule sur **Activé**.
1. Pour la certification de jeu de données, si votre organisation dispose d’une stratégie de certification publiée, vous pouvez spécifier son URL ici. Cela deviendra le lien **En savoir plus** dans la section Certification de la [boîte de dialogue de paramètres d’approbation de dataflow](../connect-data/service-datasets-promote.md#request-dataset-certification). 
1. Spécifiez les utilisateurs ou les groupes qui sont autorisés à certifier des jeux de données et des dataflows. Ces certificateurs autorisés pourront utiliser le bouton Certification de la section Certification de la boîte de dialogue de paramètres d’approbation de [jeu de données](../connect-data/service-datasets-promote.md#request-dataset-certification) ou de [dataflow](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow).
1. Cliquez sur **Appliquer**.

## <a name="next-steps"></a>Étapes suivantes
* [Promouvoir les jeux de données](../connect-data/service-datasets-promote.md)
* [Certifier des jeux de données](../connect-data/service-datasets-certify.md)
* [Promouvoir des dataflows](../transform-model/service-dataflows-promote-certify.md#promote-a-dataflow)
* [Certifier des dataflows](../transform-model/service-dataflows-promote-certify.md#certify-a-dataflow)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
