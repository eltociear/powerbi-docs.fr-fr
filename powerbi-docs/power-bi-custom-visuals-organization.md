---
title: Visuels personnalisés organisationnels dans Power BI
description: Utiliser, gérer et créer des visuels personnalisés d’une organisation dans Power BI
author: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-desktop
ms.topic: conceptual
ms.date: 12/11/2018
LocalizationGroup: Visualizations
ms.openlocfilehash: 6622625f27f62d9d8ffc35ecfddf4550f2a7e16e
ms.sourcegitcommit: c09241803664643e1b2ba0c150e525e1262ca466
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2019
ms.locfileid: "54072149"
---
# <a name="organizational-custom-visuals-in-power-bi"></a>Visuels personnalisés organisationnels dans Power BI

Vous pouvez utiliser des visuels personnalisés dans Power BI pour créer un type de visuel unique spécialement adapté à vos besoins. Les visuels personnalisés sont créés par des développeurs, en général lorsque la multitude de visuels inclus dans Power BI ne répond pas tout à fait à leurs attentes.

Dans certaines organisations, des visuels personnalisés sont encore plus importants : ils peuvent être nécessaires pour transmettre des données spécifiques ou des informations précises propres à l’organisation, présenter des contraintes liées à des données spéciales, ou mettre en évidence des méthodes privées de l’entreprise. Ces organisations doivent développer des visuels personnalisés, les partager dans toute l’entreprise, et s’assurer que ces visuels sont gérés correctement. Les visuels personnalisés Power BI permettent à ces organisations d’atteindre ces objectifs.

L’image suivante montre le processus dans lequel des visuels personnalisés d’une organisation dans Power BI passent de l’administrateur à l’analyste de données via le développement et la maintenance.

![Pic de visuel personnalisé](media/power-bi-custom-visuals-organizational/custom-visual-org-01.jpg)

Les visuels organisationnels sont déployés et gérés par l’administrateur Power BI sur le portail d’administration. Une fois ces visuels déployés dans le référentiel de l’organisation, les utilisateurs peuvent facilement les découvrir et les importer dans leurs rapports, directement depuis Power BI Desktop.

Pour savoir comment utiliser des visuels personnalisés organisationnels dans les rapports que vous avez créés, voir l’article suivant : [En savoir plus sur l’importation de visuels organisationnels dans des rapports](power-bi-custom-visuals.md).

## <a name="administer-organizational-custom-visuals"></a>Administrer les visuels personnalisés d’une organisation

Pour savoir comment déployer et gérer des visuels personnalisés organisationnels dans votre entreprise, voir l’article suivant : [En savoir plus sur le déploiement et la gestion de visuels personnalisés organisationnels](https://go.microsoft.com/fwlink/?linkid=866790).

> [!WARNING]
> Un visuel personnalisé peut contenir du code présentant des risques en matière de sécurité ou de confidentialité. Assurez-vous que vous faites confiance à l’auteur et à la source d’un visuel personnalisé avant de le déployer dans le référentiel de l’organisation.

## <a name="considerations-and-limitations"></a>Considérations et limitations

Il existe plusieurs considérations et limitations que vous devez connaître.

Admin :

* Les visuels personnalisés hérités (par exemple, ceux qui ne reposent pas sur les nouvelles API avec gestion de versions) ne sont pas pris en charge.

* Si un visuel personnalisé est supprimé du référentiel, tous les rapports existants qui utilisent le visuel supprimé ne s’afficheront plus. L’opération de suppression du référentiel n’est pas réversible. Pour désactiver temporairement un élément visuel personnalisé, utilisez la fonctionnalité « Désactiver ».

Utilisateur final :

* Les visuels personnalisés d’une organisation sont des visuels privés importés à partir du référentiel de l’organisation. Comme tous les visuels privés, ils ne peuvent pas être [exportés vers PowerPoint](https://docs.microsoft.com/power-bi/consumer/end-user-powerpoint) ou affichées dans des e-mails reçus quand un utilisateur [s’abonne aux pages de rapport](https://docs.microsoft.com/power-bi/consumer/end-user-subscribe). Seuls les [visuels personnalisés certifiés](https://docs.microsoft.com/power-bi/power-bi-custom-visuals-certified) importés directement à partir de la place de marché prennent en charge ces fonctionnalités.

* Les visuels Visio, PowerApps, Mapbox et GlobeMap provenant de la place de marché AppSource ne s’affichent pas s’ils sont déployés par le biais du référentiel de l’organisation.

## <a name="troubleshoot"></a>Résoudre des problèmes

Pour plus d’informations, visitez [Résolution des problèmes de vos visuels personnalisés Power BI](power-bi-custom-visuals-troubleshoot.md).

## <a name="faq"></a>FORUM AUX QUESTIONS

Pour plus d’informations et des réponses à vos questions, visitez [Questions fréquentes sur les visuels personnalisés Power BI](power-bi-custom-visuals-faq.md#organizational-custom-visuals).

D’autres questions ? [Posez vos questions à la Communauté Power BI](http://community.powerbi.com/).
