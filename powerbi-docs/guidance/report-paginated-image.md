---
title: Aide sur l’utilisation d’images pour les rapports paginés
description: Aide sur l’utilisation d’images dans les rapports paginés Power BI.
author: peter-myers
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: report-builder
ms.topic: conceptual
ms.date: 02/16/2020
ms.author: v-pemyer
ms.openlocfilehash: 09fd2197cca31e083c0242b187d7e242244235eb
ms.sourcegitcommit: b22a9a43f61ed7fc0ced1924eec71b2534ac63f3
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/21/2020
ms.locfileid: "77530369"
---
# <a name="image-use-guidance-for-paginated-reports"></a>Aide sur l’utilisation d’images pour les rapports paginés

Cet article s’adresse à vous en tant qu’auteur de [rapports paginés](../paginated-reports-report-builder-power-bi.md) Power BI. Il fournit des suggestions en rapport avec l’utilisation d’images. En général, les images dans les mises en page de rapport servent à afficher un graphique comme un logo d’entreprise ou des photos.

Les images peuvent être stockées à trois emplacements différents :

- Dans le rapport (stockage incorporé)
- Sur un serveur web
- Dans une base de données (qui peut être extraite par un jeu de données)

Vous pouvez les utiliser dans bon nombre de scénarios pour vos mises en page de rapport :

- Logo ou image autonome
- Images associées à des lignes de données
- Arrière-plan pour certains éléments de rapport :
  - Corps du rapport
  - Zone de texte
  - Rectangle
  - Région de données d’un tableau matriciel (table, matrice ou liste)

## <a name="suggestions"></a>Suggestions

Tenez compte des suggestions suivantes pour fournir des mises en page de rapport professionnelles, faciliter la maintenance et optimiser les performances des rapports :

- **Utiliser la plus petite taille possible** : nous vous recommandons de préparer des petites images, mais précises et nettes. Vous devez trouver le juste équilibre entre qualité et taille. Envisagez de recourir à un éditeur graphique (comme MS Paint) pour réduire la taille du fichier image.
- **Éviter les images incorporées** : premièrement, les images incorporées peuvent augmenter la taille du fichier de rapport, ce qui peut contribuer au ralentissement du rendu du rapport. Deuxièmement, les images incorporées peuvent rapidement devenir un cauchemar en matière de maintenance si vous devez mettre à jour de nombreuses images de rapport (par exemple en cas de changement du logo de votre entreprise).
- **Utiliser le stockage du serveur web** : le stockage d’images sur un serveur web est une bonne option, en particulier pour un logo d’entreprise qui peut provenir du site web de l’entreprise. Toutefois, faites attention si les utilisateurs accèdent à des rapports en dehors de votre réseau. Dans ce cas, vérifiez que les images sont disponibles sur Internet.

    Quand des images se rapportent à vos données (comme les images de vos commerciaux), nommez les fichiers d’image de manière à ce qu’une expression de rapport puisse produire dynamiquement le chemin à l’URL de l’image. Par exemple, vous pouvez nommer les images en utilisant le numéro d’employé de chaque commercial. Si le jeu de données de rapport extrait le numéro d’employé, vous pouvez écrire une expression pour produire le chemin complet à l’URL de l’image.
- **Utiliser le stockage de la base de données** : quand une base de données relationnelle stocke des données d’image, il est logique de fournir les données d’image directement à partir des tables de base de données, en particulier si les images ne sont pas trop grandes.
- **Images d’arrière-plan appropriées** : si vous décidez d’utiliser des images d’arrière-plan, veillez à ne pas détourner l’attention de l’utilisateur des données de votre rapport. 

    Veillez également à utiliser des _images en filigrane_. En général, les images en filigrane ont un arrière-plan transparent (ou ont la même couleur d’arrière-plan que le rapport). Elles utilisent également des couleurs pâles. Il est ainsi fréquent d’ajouter des images en filigrane pour inclure le logo de l’entreprise ou des étiquettes de sensibilité comme « Brouillon » ou « Confidentiel ».

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Présentation des rapports paginés dans Power BI Premium](../paginated-reports-report-builder-power-bi.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
