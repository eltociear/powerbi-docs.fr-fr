---
title: Résolution des erreurs de vignette
description: Erreurs courantes qui peuvent survenir quand une vignette tente de s’actualiser
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.component: powerbi-service
ms.topic: conceptual
ms.date: 05/02/2018
ms.author: davidi
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 8b68ce7af749b7e7f292592f6debdc7e964d6c17
ms.sourcegitcommit: 998b79c0dd46d0e5439888b83999945ed1809c94
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/17/2018
ms.locfileid: "34242883"
---
# <a name="troubleshooting-tile-errors"></a>Résolution des erreurs de vignette
Voici les erreurs courantes que vous pouvez rencontrer avec des vignettes, ainsi qu’une explication à ce sujet.

> [!NOTE]
> Si vous rencontrez une erreur qui ne figure pas dans la liste ci-dessous et que cela vous pose des problèmes, vous pouvez demander de l’aide sur le [site de la communauté](http://community.powerbi.com/) ou créer un [ticket de support](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Erreurs
**Power BI a rencontré une erreur inattendue lors du chargement du modèle. Veuillez réessayer plus tard.**
ou **Impossible d’extraire le modèle de données. Contactez le propriétaire du tableau de bord pour vous assurer que les sources et le modèle de données existent et sont accessibles.**

Nous n’avons pas pu accéder à vos données parce que la source de données était inaccessible. Cela peut se produire si la source de données a été supprimée, renommée, déplacée, mise hors connexion, ou si des autorisations ont été modifiées. Vérifiez que la source est toujours à l’emplacement vers lequel nous pointons et que vous êtes toujours autorisé à y accéder. Si tel n’est pas le problème, il se peut que la source soit lente. Réessayez ultérieurement, quand la charge sur la source sera moindre. S’il s’agit d’une source locale, son propriétaire est peut-être en mesure de fournir des informations supplémentaires.

**Vous n’êtes pas autorisé à afficher cette vignette ou à ouvrir ce classeur.**

Contactez le propriétaire du tableau de bord pour vous assurer que les sources et le modèle de données existent et sont accessibles pour votre compte.

**Les formes de données doivent contenir au moins un groupe ou calcul qui génère des données. Contactez le propriétaire du tableau de bord.**

Nous n’avons aucune donnée à afficher parce que la requête est vide. Essayez d’ajouter des champs de la liste de champs à votre élément visuel et de l’épingler à nouveau.

**Impossible d’afficher les données, car Power BI ne parvient pas à déterminer la relation entre deux ou plusieurs champs.**

Vous essayez d’utiliser plusieurs champs à partir de tables qui sont sans relation. Vous devez supprimer de l’élément visuel les champs qui ne sont pas en relation, puis créer une relation entre les tables. Cela fait, vous pouvez ajouter les champs à l’élément visuel. Vous le pouvez dans Power BI Desktop ou Power Pivot pour Excel. [En savoir plus](desktop-create-and-manage-relationships.md)

**Les groupes de l’axe principal et de l’axe secondaire se chevauchent. Les groupes de l’axe principal ne peuvent pas avoir les mêmes clés que les groupes de l’axe secondaire.**

Il s’agit généralement d’un problème temporaire. Cela se produit généralement quand vous déplacez des groupes de lignes vers des colonnes. Dans ce cas, l’erreur doit disparaître lorsque vous achevez le déplacement de tous les groupes. Si le message s’affiche toujours, essayez de commuter des champs entre les lignes et les colonnes ou la légende de l’axe, ou de supprimer des champs de l’élément visuel.  

**Cette représentation visuelle a dépassé les ressources disponibles. Essayez de filtrer pour diminuer la quantité de données affichées.**

Votre élément visuel a tenté d’interroger un trop grand nombre de données pour que nous puissions générer le résultat avec les ressources disponibles. Essayez de filtrer l’élément visuel pour réduire la quantité de données dans le résultat.

**Nous ne parvenons pas à identifier les champs suivants : {0}. Veuillez mettre à jour l’élément visuel avec des champs existant dans le jeu de données.**

Le champ a probablement été supprimé ou renommé. Vous pouvez supprimer le champ incorrect de l’élément visuel, ajouter un autre champ, puis le réépingler.

**Impossible d’extraire les données de cet élément visuel. Veuillez réessayer plus tard.**

Il s’agit généralement d’un problème temporaire. Si vous réessayez plus tard et que ce message continue à s’afficher, veuillez contacter le support technique.

## <a name="contact-support"></a>Contact du support technique
Si vous rencontrez toujours un problème, veuillez [contacter le support technique](https://support.powerbi.com) pour approfondir les recherches.

## <a name="next-steps"></a>Étapes suivantes
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
[Résolution des problèmes liés à Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](http://community.powerbi.com/)

