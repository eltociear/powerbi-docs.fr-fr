---
title: Résolution des erreurs de vignette
description: Erreurs courantes qui peuvent survenir quand une vignette tente de s’actualiser dans Power BI
author: maggiesMSFT
ms.reviewer: kayu
ms.custom: seodec18
ms.service: powerbi
ms.subservice: powerbi-service
ms.topic: troubleshooting
ms.date: 12/06/2018
ms.author: maggies
LocalizationGroup: Troubleshooting
ms.openlocfilehash: 463275d98c72441264e5bae699d983eb34bb1058
ms.sourcegitcommit: 0e9e211082eca7fd939803e0cd9c6b114af2f90a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83320489"
---
# <a name="troubleshooting-tile-errors"></a>Résolution des erreurs de vignette
Voici les erreurs courantes que vous pouvez rencontrer avec des vignettes, ainsi qu’une explication à ce sujet.

> [!NOTE]
> Si vous rencontrez une erreur qui ne figure pas dans la liste ci-dessous et que cela vous pose des problèmes, vous pouvez demander de l’aide sur le [site de la communauté](https://community.powerbi.com/) ou créer un [ticket de support](https://powerbi.microsoft.com/support/).
> 
> 

## <a name="errors"></a>Erreurs
**Power BI a rencontré une erreur inattendue lors du chargement du modèle. Veuillez réessayer plus tard.**
ou **Impossible d’extraire le modèle de données. Contactez le propriétaire du tableau de bord pour vous assurer que les sources et le modèle de données existent et sont accessibles.**

Nous n’avons pas pu accéder à vos données parce que la source de données était inaccessible. Ce problème peut se produire si la source de données a été supprimée, renommée, déplacée ou mise hors connexion, ou si des autorisations ont été changées. Vérifiez que la source est toujours à l’emplacement vers lequel nous pointons et que vous êtes toujours autorisé à y accéder. Si tel n’est pas le problème, il se peut que la source soit lente. Réessayez ultérieurement, quand la charge sur la source sera moindre. S’il s’agit d’une source locale, son propriétaire est peut-être en mesure de fournir des informations supplémentaires.

**Vous n’êtes pas autorisé à afficher cette vignette ou à ouvrir le classeur.**

Contactez le propriétaire du tableau de bord pour vous assurer que les sources et le modèle de données existent et sont accessibles par votre compte.

**Les visuels Power BI ont été désactivés par votre administrateur.**

Votre administrateur Power BI a désactivé l’utilisation des visuels Power BI pour votre organisation ou votre groupe de sécurité.
Vous ne pouvez pas utiliser les visuels Power BI de la [Place de marché Microsoft](https://appsource.microsoft.com/marketplace/apps?page=1&product=power-bi-visuals) ni importer de visuels privés à partir d’un fichier. Vous avez uniquement accès à l’ensemble des visuels initialement fournis dans le pack.


**Les formes de données doivent contenir au moins un groupe ou calcul qui génère des données. Contactez le propriétaire du tableau de bord.**

Nous n’avons aucune donnée à afficher parce que la requête est vide. Essayez d’ajouter des champs de la liste de champs à votre élément visuel et de l’épingler à nouveau.

**Impossible d’afficher les données, car Power BI ne parvient pas à déterminer la relation entre deux ou plusieurs champs.**

Vous essayez d’utiliser plusieurs champs à partir de tables qui sont sans relation. Vous devez supprimer de l’élément visuel les champs qui ne sont pas en relation, puis créer une relation entre les tables. Après cela, vous pouvez rajouter les champs au visuel. Vous le pouvez dans Power BI Desktop ou Power Pivot pour Excel. [En savoir plus](../transform-model/desktop-create-and-manage-relationships.md)

**Les groupes de l’axe principal et de l’axe secondaire se chevauchent. Les groupes de l’axe principal ne peuvent pas avoir les mêmes clés que les groupes de l’axe secondaire.**

C’est généralement un problème temporaire. Cela se produit généralement quand vous déplacez des groupes de lignes vers des colonnes. Dans ce cas, l’erreur doit disparaître lorsque vous achevez le déplacement de tous les groupes. Si le message s’affiche toujours, essayez de commuter des champs entre les lignes et les colonnes ou la légende de l’axe, ou de supprimer des champs de l’élément visuel.  

**Cette représentation visuelle a dépassé les ressources disponibles. Essayez de filtrer pour diminuer la quantité de données affichées.**

Votre élément visuel a tenté d’interroger un trop grand nombre de données pour que nous puissions générer le résultat avec les ressources disponibles. Essayez de filtrer l’élément visuel pour réduire la quantité de données dans le résultat.

**Nous ne parvenons pas à identifier les champs suivants : {0}. Veuillez mettre à jour l’élément visuel avec des champs existant dans le jeu de données.**

Le champ a probablement été supprimé ou renommé. Vous pouvez supprimer le champ incorrect de l’élément visuel, ajouter un autre champ, puis le réépingler.

**Impossible d’extraire les données de cet élément visuel. Veuillez réessayer plus tard.**

Il s’agit généralement d’un problème temporaire. Si vous réessayez plus tard et que ce message continue à s’afficher, contactez le support technique.

**Les vignettes continuent à afficher les données non filtrées après l’activation de l’authentification unique (SSO).**

Cela peut se produire si le jeu de données sous-jacent est configuré pour utiliser le mode DirectQuery ou une connexion active à Analysis Services par le biais d’une passerelle de données locale. Dans ce cas, les vignettes continuent d’afficher les données non filtrées après l’activation de l’authentification unique pour la source de données, jusqu’à l’actualisation de vignette suivante. À l’actualisation de vignette suivante, Power BI utilise l’authentification unique telle qu’elle est configurée, et les vignettes affichent les données filtrées en fonction de l’identité de l’utilisateur. 

Pour voir immédiatement les données filtrées, vous pouvez forcer une actualisation des vignettes en sélectionnant **Plus d’options** (...) dans l’angle supérieur droit d’un tableau de bord, puis l’option **Actualiser les vignettes du tableau de bord**.

En tant que propriétaire du jeu de données, vous pouvez également modifier la fréquence d’actualisation des vignettes et la définir sur 15 minutes pour accélérer l’actualisation des vignettes. Sélectionnez l’icône d’engrenage dans l’angle supérieur droit du Service Power BI, puis sélectionnez **Paramètres**. Dans la page **Paramètres**, sélectionnez l’onglet **Jeux de données**. Développez **Actualisation du cache planifiée** et modifiez la **Fréquence d'actualisation**. Veillez à réinitialiser la configuration à la fréquence d’actualisation d’origine une fois que Power BI effectué l’actualisation suivante de la vignette.

> [!NOTE]
> La section **Actualisation du cache planifiée** est disponible uniquement pour les jeux de données en mode DirectQuery/Connexion active. Les jeux de données en mode Importation ne nécessitent pas d’actualisation de vignette distincte, car les vignettes sont actualisées automatiquement lors de l’actualisation planifiée des données suivante.

## <a name="contact-support"></a>Contact support
Si vous rencontrez toujours le même problème, [contactez le support technique](https://support.powerbi.com) pour approfondir les recherches.

## <a name="next-steps"></a>Étapes suivantes
[Résolution des problèmes de passerelle de données locale](service-gateway-onprem-tshoot.md)  
[Résolution des problèmes liés à Power BI Personal Gateway](service-admin-troubleshooting-power-bi-personal-gateway.md)  
D’autres questions ? [Posez vos questions à la communauté Power BI](https://community.powerbi.com/)
