---
title: 'Packs de contenu d’organisation : accès et copie'
description: Consultez les informations relatives à la création de copies de packs de contenu d’organisation et à la résolution des problèmes d’accès à ces derniers dans Power BI
author: maggiesMSFT
manager: kfile
ms.reviewer: ajayan
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 10/12/2017
ms.author: maggies
LocalizationGroup: Share your work
ms.openlocfilehash: a4c2eaed0e8d577359ad9b5ee191ad2894ada12b
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
---
# <a name="organizational-content-packs-copy-refresh-and-get-access"></a>Packs de contenu d’organisation : copie, actualisation et accès
> [!NOTE]
> Avez-vous déjà entendu parler des nouvelles *applications*? Les applications sont la nouvelle méthode pour distribuer du contenu à un large public dans Power BI. Vous créez des applications dans des *espaces de travail d’application* qui remplacent les groupes et les espaces de travail de groupe. Nous recommandons d’utiliser des applications plutôt que des packs de contenu d’organisation ou des espaces de travail en lecture seule. En savoir [plus sur les applications](service-install-use-apps.md).
> 
> 

Quand un pack de contenu d’organisation est publié, tous les destinataires voient les mêmes tableaux de bord, rapports, classeurs Excel, jeux de données et données (sauf s’il s’agit d’une source de données SQL Server Analysis Services (SSAS)).  [Seul l’auteur du pack de contenu peut modifier et republier](service-organizational-content-pack-manage-update-delete.md) celui-ci.  Toutefois, tous les destinataires peuvent enregistrer une copie du pack de contenu qui peut coexister avec l’original.

La création de packs de contenu est différente du partage de tableaux de bord ou de la collaboration sur ces derniers dans un groupe. Pour déterminer l’option la plus adaptée à votre situation, consultez [Comment partager des tableaux de bord, rapports et vignettes ?](service-how-to-collaborate-distribute-dashboards-reports.md).

## <a name="create-a-copy-of-an-organizational-content-pack"></a>Créer une copie d’un pack de contenu d’organisation
Créez votre propre copie du pack de contenu, non visible à d’autres personnes.

1. Sélectionnez les points de suspension (...) en regard du tableau de bord du pack de contenu > Faire une copie.
   
    ![](media/service-organizational-content-pack-copy-refresh-access/power-bi-create-copy-organizational-content-pack.png)
2. Sélectionnez **Enregistrer**.  

Vous disposez maintenant d’une copie que vous pouvez modifier. Personne d’autre ne peut voir les modifications que vous apportez.

## <a name="help--i-can-no-longer-access-the-content-pack"></a>Au secours !  Je ne peux plus accéder au pack de contenu
Cela peut se produire pour plusieurs raisons :

* **Modifications d’appartenance :** les packs de contenu sont publiés à l’adresse de groupes de distribution d’e-mails, de groupes de sécurité et de [groupes Power BI basés sur Office 365](https://support.office.com/article/Create-a-group-in-Office-365-7124dc4c-1de9-40d4-b096-e8add19209e9).  Si vous êtes supprimé d’un groupe, vous n’avez plus accès au pack de contenu.
* **Modifications de la distribution :** l’auteur du pack de contenu modifie la distribution. Par exemple, si le pack de contenu a été publié à l’origine pour l’organisation entière, puis que son créateur l’a republié à l’adresse d’un public plus restreint, il se peut que vous ne figuriez plus parmi ses destinataires.
* **Modification des paramètres de sécurité :** si le tableau de bord et les rapports sont connectés à des sources de données SSAS locales et si des modifications sont apportées aux paramètres de sécurité, vos autorisations concernant ce serveur peuvent être révoquées.

## <a name="how-are-organizational-content-packs-refreshed"></a>Comment les packs de contenu d’organisation sont-ils actualisés ?
Quand un pack de contenu est créé, les paramètres d’actualisation sont hérités avec le jeu de données.  Quand vous créez une copie du pack de contenu, la nouvelle version conserve son lien au jeu de données d’origine et à la planification de l’actualisation. 

Voir [Gérer, mettre à jour et supprimer des packs de contenu d’organisation](service-organizational-content-pack-manage-update-delete.md).

## <a name="next-steps"></a>Étapes suivantes
* [Introduction aux packs de contenu d’organisation](service-organizational-content-pack-introduction.md)
* [Créer un groupe dans Power BI](service-create-distribute-apps.md)
* D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

