---
title: Désactiver l’actualisation en arrière-plan de Power Query
description: Aide pour savoir quand désactiver l’actualisation en arrière-plan de Power Query.
author: peter-myers
ms.author: v-pemyer
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi
ms.topic: conceptual
ms.date: 09/26/2019
ms.openlocfilehash: 54e8524d2997e086b218e7d5b569e58ace21c48e
ms.sourcegitcommit: 653e18d7041d3dd1cf7a38010372366975a98eae
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/01/2020
ms.locfileid: "96418644"
---
# <a name="disable-power-query-background-refresh"></a>Désactiver l’actualisation en arrière-plan de Power Query

Cet article s’adresse principalement aux modélisateurs de données d’importation qui utilisent Power BI Desktop.

Par défaut, quand Power Query importe des données, il met également en cache jusqu’à 1000 lignes de données d’aperçu pour chaque requête. Ce sont ces données d’aperçu qui vous permettent d’avoir un aperçu rapide des données sources et des résultats de transformation pour chaque étape de vos requêtes. Elles sont stockées séparément sur disque et non pas dans le fichier Power BI Desktop.

Toutefois, quand votre fichier Power BI Desktop contient trop de requêtes, la récupération et le stockage des données d’aperçu risquent de prolonger la durée d’actualisation.

## <a name="recommendation"></a>Recommandation

Pour une actualisation plus rapide, définissez le fichier Power BI Desktop pour mettre à jour le cache d’aperçu _en arrière-plan_. Pour ce faire, dans Power BI Desktop, sélectionnez _Fichier > Options et paramètres > Options_, puis sélectionnez la page _Chargement de données_. Vous pouvez alors activer l’option **Autoriser le téléchargement de l’aperçu des données en arrière-plan**. Notez que cette option peut uniquement être définie pour le fichier actuel.

![Capture d’écran de Power BI Desktop montrant des options de données en arrière-plan.](media/power-query-background-refresh/power-query-options-background-data.png)

L’actualisation en arrière-plan peut entraîner la péremption de certaines données d’aperçu. Si c’est le cas, l’éditeur Power Query vous avertit avec l’avertissement suivant :

![Capture d’écran de Power BI Desktop montrant l’avertissement de l’éditeur Power Query concernant les vieilles données d’aperçu.](media/power-query-background-refresh/power-query-preview-data-old.png)

Vous pouvez toujours mettre à jour le cache d’aperçu. Vous pouvez le mettre à jour pour une seule requête ou pour toutes les requêtes à l’aide de la commande **Actualiser l’aperçu**. Cette commande se trouve dans le ruban **Accueil** de la fenêtre de l’éditeur Power Query.

![Capture d’écran de Power BI Desktop montrant les commandes de l’éditeur Power Query permettant d’actualiser les données d’aperçu.](media/power-query-background-refresh/power-query-refresh-preview-data.png)

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Documentation Power Query](/power-query/)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
