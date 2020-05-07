---
title: Désactiver l’actualisation de l’arrière-plan de Power Query
description: Aide pour savoir quand désactiver l’actualisation en arrière-plan de Power Query.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 09/26/2019
ms.author: v-pemyer
ms.openlocfilehash: 59cb62a9186da03a265fc3a8711d7275c3772af3
ms.sourcegitcommit: 7aa0136f93f88516f97ddd8031ccac5d07863b92
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "75623058"
---
# <a name="disable-power-query-background-refresh"></a>Désactiver l’actualisation de l’arrière-plan de Power Query

Cet article s’adresse principalement aux modélisateurs de données d’importation qui utilisent Power BI Desktop.

Par défaut, quand Power Query importe des données, il met également en cache jusqu’à 1000 lignes de données d’aperçu pour chaque requête. Ce sont ces données d’aperçu qui vous permettent d’avoir un aperçu rapide des données sources et des résultats de transformation pour chaque étape de vos requêtes. Elles sont stockées séparément sur disque et non pas dans le fichier Power BI Desktop.

Toutefois, quand votre fichier Power BI Desktop contient trop de requêtes, la récupération et le stockage des données d’aperçu risquent de prolonger la durée d’actualisation.

## <a name="recommendation"></a>Recommandation

Pour une actualisation plus rapide, définissez le fichier Power BI Desktop pour mettre à jour le cache d’aperçu _en arrière-plan_. Pour ce faire, dans Power BI Desktop, sélectionnez _Fichier > Options et paramètres > Options_, puis sélectionnez la page _Chargement de données_. Vous pouvez alors activer l’option **Autoriser le téléchargement de l’aperçu des données en arrière-plan**. Notez que cette option peut uniquement être définie pour le fichier actuel.

![Options de données en arrière-plan dans Power BI Desktop](media/power-query-background-refresh/power-query-options-background-data.png)

L’actualisation en arrière-plan peut entraîner la péremption de certaines données d’aperçu. Si c’est le cas, l’éditeur Power Query vous avertit avec l’avertissement suivant :

![Avertissement de l’éditeur Power Query sur les vieilles données d’aperçu](media/power-query-background-refresh/power-query-preview-data-old.png)

Vous pouvez toujours mettre à jour le cache d’aperçu. Vous pouvez le mettre à jour pour une seule requête ou pour toutes les requêtes à l’aide de la commande **Actualiser l’aperçu**. Cette commande se trouve dans le ruban **Accueil** de la fenêtre de l’éditeur Power Query.

![Commandes de l’éditeur Power Query pour actualiser les données d’aperçu](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Documentation Power Query](/power-query/)
- Des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
