---
title: "Utilisation des visuels personnalisés d’une organisation dans Power BI"
description: "Utiliser, gérer et créer des visuels personnalisés d’une organisation dans Power BI"
services: powerbi
documentationcenter: 
author: markingmyname
manager: kfile
backup: 
editor: 
tags: 
qualityfocus: no
qualitydate: 
ms.service: powerbi
ms.devlang: NA
ms.topic: article
ms.tgt_pltfrm: NA
ms.workload: powerbi
ms.date: 02/06/2018
ms.author: maghan
ms.openlocfilehash: 2c90ea4a7e95c354b6dfaec04cff7e5e4009b55f
ms.sourcegitcommit: db37f5cef31808e7882bbb1e9157adb973c2cdbc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2018
---
# <a name="using-organization-custom-visuals-in-power-bi-preview"></a>Utilisation des visuels personnalisés d’une organisation dans Power BI (préversion)

Vous pouvez utiliser des visuels personnalisés dans Power BI pour créer un type de visuel unique, spécialement adapté à vos besoins ou aux informations précises que vous souhaitez transmettre. Souvent, ces visuels personnalisés sont créés par des développeurs et lorsque la multitude de visuels inclus dans Power BI ne répond pas tout à fait à leurs attentes. 

Dans certaines organisations, des visuels personnalisés sont encore plus importants : ils peuvent être nécessaires pour transmettre des données spécifiques ou des informations précises propres à l’organisation, présenter des contraintes liées à des données spéciales, ou mettre en évidence des méthodes privées de l’entreprise. Ces organisations doivent développer des visuels personnalisés, les partager dans toute l’entreprise, et s’assurer que ces visuels sont gérés correctement. Les visuels personnalisés Power BI (actuellement en préversion) permettent à ces organisations d’atteindre ces objectifs. 

L’image suivante montre le processus dans lequel des visuels personnalisés (préversion) d’une organisation dans Power BI passent de l’administrateur à l’analyste de données via le développement et la maintenance.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

## <a name="how-to-enable-organizational-custom-visuals-preview"></a>Guide pratique pour activer des visuels personnalisés d’une organisation (préversion)

Les visuels personnalisés d’une organisation sont actuellement en préversion et vous devez donc activer cette fonctionnalité dans Power BI Desktop. Pour activer cette fonctionnalité en préversion, dans le ruban, sélectionnez Fichier > Options et paramètres > Options, puis dans le volet gauche, sélectionnez Fonctionnalités en préversion, puis cochez la case en regard de Visuels personnalisés de mon organisation, comme indiqué dans l’image suivante.

![](media/power-bi-custom-visuals-organizational/custom-visual-org-02.jpg)

Les visuels d’une organisation sont déployés et gérés par l’administrateur Power BI à partir du portail d’administration. Une fois ces visuels déployés dans le référentiel de l’organisation, les utilisateurs peuvent facilement les découvrir et les importer dans leurs rapports, directement depuis Power BI Desktop.

## <a name="using-organizational-custom-visuals"></a>Utilisation des visuels personnalisés d’une organisation

Pour en savoir plus sur l’utilisation des visuels personnalisés d’une organisation dans les rapports que vous avez créés, consultez l’article suivant : [En savoir plus sur l’importation de visuels d’une organisation dans vos rapports](power-bi-custom-visuals.md).
 
## <a name="administering-organizational-custom-visuals"></a>Administration des visuels personnalisés d’une organisation

Pour en savoir plus sur la façon de gérer, déployer et gérer des visuels personnalisés d’organisation dans votre organisation, consultez l’article suivant : [En savoir plus sur déploiement et la gestion des visuels personnalisés d’une organisation](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Un visuel personnalisé peut contenir du code présentant des risques en matière de sécurité ou de confidentialité. Assurez-vous que vous faites confiance à l’auteur et à la source d’un visuel personnalisé avant de le déployer dans le référentiel de l’organisation. 
> 

## <a name="considerations-and-limitations"></a>Considérations et limitations
 
Étant donné que les visuels personnalisés d’une organisation sont en préversion, vous devez connaître et prendre en compte un certain nombre de considérations et de limitations.
 
Admin :

* les visuels personnalisés hérités (par exemple les visuels personnalisés qui ne reposent pas sur les nouvelles API avec version gérée) ne sont pas pris en charge

* La mise à jour sur place n’est pas encore prise en charge. Pour mettre à jour un visuel, vous devez télécharger une nouvelle version de ce visuel dans le référentiel de l’organisation (assurez-vous également qu’il comporte le même identifiant de visuel dans le fichier PBIVIZ). Les auteurs de rapports peuvent ensuite importer la nouvelle version dans leur rapport et effectuer un remplacement sur place de la version actuelle du visuel dans le rapport.

* Si un visuel personnalisé est supprimé du référentiel, tous les rapports existants qui utilisent le visuel supprimé ne s’afficheront plus. L’opération de suppression du référentiel n’est pas réversible.
 
Utilisateur final :

* L’utilisation du même visuel (et du même identifiant) de la Place de marché publique (AppSource) et du référentiel de l’organisation n’est pas prise en charge. Dans ce cas, le visuel le plus récent importé sera utilisé.

* Le partage externe de visuels d’une organisation dans des tableaux de bord et des rapports n’est pas pris en charge. Les utilisateurs externes à l’entreprise qui affichent un tableau de bord avec un visuel personnalisé d’une organisation verront un visuel vide. 

* La collection d’espaces de travail Power BI n’est pas prise en charge pour les visuels d’une organisation

* Les visuels personnalisés d’une organisation figurant dans des rapports publiés sur le web ne s’afficheront pas

* Les éléments Visio, PowerApps et GlobeMap provenant de la Place de marché AppSource ne s’affichent pas s’ils sont déployés via le référentiel de l’organisation

* Si l’administrateur supprime un visuel personnalisé du référentiel, et que ce visuel est utilisé dans un rapport, il ne s’affiche pas et doit être supprimé du rapport afin d’enregistrer ce dernier