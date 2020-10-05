---
title: Certifier des jeux de données - Power BI
description: Découvrez comment guider les utilisateurs en entreprise vers des jeux de données fiables et de qualité.
author: maggiesMSFT
ms.reviewer: kayu
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: how-to
ms.date: 09/24/2020
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: d8b59a7a34d4cc79901ca7238b77b0448cecb9ee
ms.sourcegitcommit: 02b5d031d92ea5d7ffa70d5098ed15e4ef764f2a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "91374105"
---
# <a name="certify-datasets---power-bi"></a>Certifier des jeux de données - Power BI

Votre organisation peut *certifier* des jeux de données qui sont la source d’autorité d’informations importantes. Ces jeux de données occupent une place importante quand les concepteurs de rapports commencent à créer un rapport et à rechercher des données fiables. La certification est un processus hautement sélectif, où seuls les jeux de données les plus importants sont certifiés. Les administrateurs Power BI disposent d’un nouveau paramètre leur permettant de contrôler de façon précise qui peut certifier des jeux de données. Avec le processus de certification, les administrateurs garantissent que les jeux de données sont véritablement fiables, qu’ils font autorité et qu’ils sont conçus pour être utilisés dans l’ensemble de l’organisation.

En tant que propriétaire de jeux de données, vous pouvez demander la certification d’un jeu de données promu. Un groupe sélectionné d’utilisateurs défini dans le paramètre de locataire **Certification** détermine quels jeux de données certifier. Le nom de la personne qui a certifié un jeu de données s’affiche dans une info-bulle pendant l’expérience de découverte du jeu de données. Placez le curseur sur l’étiquette **Certifié** pour le voir. Pour plus d’informations, consultez [Configurer la certification de jeux de données et de dataflows](../admin/service-admin-setup-certification.md).

Power BI offre deux moyens de *recommander* des jeux de données : En dehors de la certification, l’autre méthode est la *promotion*. En tant que propriétaire de jeux de données ou membre d’un espace de travail, vous pouvez promouvoir vos jeux de données quand ils sont prêts pour une utilisation étendue. Pour plus d’informations, consultez [Promouvoir votre jeu de données](service-datasets-promote.md). 

## <a name="certify-a-dataset"></a>Certifier un jeu de données

Votre administrateur Power BI peut fournir une URL pour le lien **En savoir plus** situé dans la page des paramètres **Approbation**.  Il peut fournir un lien vers une documentation relative à votre processus de certification. Si aucune destination n’est spécifiée pour le lien **En savoir plus**, il vous dirige par défaut vers cet article.

![En savoir plus sur la certification de jeux de données](media/service-datasets-certify-promote/power-bi-dataset-learn-more-certification.png)

Être désigné comme une personne pouvant certifier des jeux de données est clairement une grande responsabilité. Si un créateur de jeu de données vous contacte concernant la certification d’un jeu de données, c’est le début de votre processus de contrôle. Quand vous êtes convaincu qu’un jeu de données mérite d’être certifié, voici les dernières étapes à suivre.

1. Le propriétaire du jeu de données doit vous accorder des autorisations de membre pour l’espace de travail où se trouve le jeu de données.
1. Si votre administrateur vous a désigné comme personne pouvant certifier des jeux de données, l’option **Certifié** de la section **Approbation** des **Paramètres** du jeu de données est disponible. Sélectionnez **Certifié**.
1. Sélectionnez **Appliquer**.

Découvrez des informations supplémentaires sur la façon dont les administrateurs peuvent [contrôler l’utilisation de jeux de données dans les espaces de travail](service-datasets-admin-across-workspaces.md).

## <a name="next-steps"></a>Étapes suivantes

* [Configurer la certification de jeux de données et de dataflows](../admin/service-admin-setup-certification.md)
* [Utilisation des jeux de données dans les espaces de travail](service-datasets-across-workspaces.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
