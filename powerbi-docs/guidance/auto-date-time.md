---
title: Conseils sur les dates/heures automatiques dans Power BI Desktop
description: Conseils sur l’utilisation de la fonctionnalité de date/heure automatique dans Power BI Desktop.
author: peter-myers
manager: asaxton
ms.reviewer: asaxton
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 10/23/2019
ms.author: v-pemyer
ms.openlocfilehash: 69084048b46c77452bf94f04fd79a97c4f09af5b
ms.sourcegitcommit: a72567f26c1653c25f7730fab6210cd011343707
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565991"
---
# <a name="auto-datetime-guidance-in-power-bi-desktop"></a>Conseils sur les dates/heures automatiques dans Power BI Desktop

Cet article s’adresse aux modélisateurs de données développant des modèles d’importation ou composites dans Power BI Desktop. Il fournit des conseils, des recommandations et des considérations concernant l'utilisation de la fonctionnalité de _date/heure automatique_ de Power BI Desktop dans des situations spécifiques. Pour une vue d’ensemble et une introduction générale à la fonctionnalité de _date/heure automatique_, voir [Date/heure automatique dans Power BI Desktop](../transform-model/desktop-auto-date-time.md).

L'option _Date/heure automatique_ fournit une intelligence temporelle pratique, rapide et conviviale. Les auteurs de rapports peuvent utiliser l'intelligence temporelle lorsqu'ils filtrent, regroupent et analysent des périodes de temps du calendrier.

## <a name="considerations"></a>Considérations

La liste à puces suivante décrit les considérations, et les éventuelles limites, liées à l'option _Date/heure automatique_.

- **S'applique à toutes ou à aucune :** Quand l’option _Date/heure automatique_ est activée, elle s'applique à toutes les colonnes de date (à l’exclusion des colonnes calculées) des tables d’importation qui ne figurent pas dans la partie &quot;plusieurs&quot; d’une relation. Elle ne peut pas être activée ou désactivée de manière sélective colonne par colonne.
- **Périodes calendaires uniquement :** Les colonnes de l'année et du trimestre se rapportent à des périodes civiles. Cela signifie que l'année commence le 1er janvier et se termine le 31 décembre. Il n'est pas possible de personnaliser la date de début (ou de fin) d'année.
- **Personnalisation :** Il n'est pas possible de personnaliser les valeurs utilisées pour décrire les périodes. De plus, il n'est pas possible d'ajouter des colonnes supplémentaires pour décrire d'autres périodes, par exemple, les semaines.
- **Filtrage par année :** Les valeurs des colonnes **Trimestre**, **Mois** et **Jour** n'incluent pas la valeur année. Par exemple, la colonne **Mois** contient uniquement les noms des mois (c'est-à-dire janvier, février, etc.). Les valeurs ne sont pas totalement auto-descriptives et, dans certains rapports, les conceptions de rapports peuvent ne pas communiquer le contexte du filtre d'année.

    C'est pourquoi il est important d’appliquer les filtres ou le regroupement à la colonne **Année**. En cas de descente dans la hiérarchie, les données seront filtrées par année, sauf si le niveau **Année** a été intentionnellement supprimé. S'il n'y a aucun filtre ou regroupement par année, un regroupement par mois, par exemple, peut résumer les valeurs de toutes les années pour ce mois.
- **Filtrage de la date dans une seule table :** Comme chaque colonne de date produit sa propre table de date/heure automatique (masquée), il n'est pas possible d'appliquer un filtre horaire à une table et de le propager à plusieurs tables de modèles. Le filtrage de cette façon est une exigence commune de modélisation lorsqu'il s'agit d'établir des rapports sur plusieurs sujets (tableaux de type fait) comme des ventes et un budget des ventes. Lors de l'utilisation de la fonctionnalité de date/heure automatique, l'auteur du rapport devra appliquer des filtres à chacune des différentes colonnes de date.
- **Taille du modèle :** Chaque colonne de date qui génère une table de date/heure automatique masquée entraîne une augmentation de la taille du modèle et un allongement du délai d’actualisation des données.
- **Autres outils de création de rapports :** Il n’est pas possible d’utiliser des tables de date/heure automatiques dans les cas suivants :
  - Utilisation de [Analyser dans Excel](../collaborate-share/service-analyze-in-excel.md).
  - Utilisation des concepteurs de requêtes Analysis Services pour des rapports paginés Power BI.
  - Connexion au modèle avec des concepteurs de rapports non-Power BI.

## <a name="recommendations"></a>Recommandations

Nous vous recommandons de garder l'option _Date/heure automatique_ activée uniquement lorsque vous utilisez des périodes calendaires et lorsque vous avez des exigences de modèle simplistes par rapport au temps. L'utilisation de cette option peut également être pratique lors de la création de modèles ad hoc ou de l'exploration ou du profilage de données.

Si votre source de données définit déjà une table de dimensions de date, cette table doit être utilisée pour définir de façon cohérente le temps au sein de votre organisation. Ce sera certainement le cas si votre source de données est un entrepôt de données. Sinon, vous pouvez générer des tables de dates dans votre modèle en utilisant les fonctions DAX [CALENDAR](/dax/calendar-function-dax) ou [CALENDARAUTO](/dax/calendarauto-function-dax). Vous pouvez ensuite ajouter des colonnes calculées pour prendre en charge les exigences connues en matière de filtrage et de regroupement du temps. Cette approche de conception vous permet de créer une table de dates unique qui se propage à toutes les tables de type fait, générant ainsi une seule table pour appliquer des filtres temporels. Pour plus d'informations sur la création de tables de date, lisez l'article [Définir et utiliser des tables de dates dans Power BI Desktop](../transform-model/desktop-date-tables.md).

Si l'option _Date/heure automatique_ n'est pas adaptée à vos projets, nous vous recommandons de désactiver l'option globale _Date/heure automatique_. Vous aurez ainsi la garantie que tous les nouveaux fichiers Power BI Desktop que vous créerez n'activeront pas l'option _Date/heure automatique_.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations en rapport avec cet article, consultez les ressources suivantes :

- [Date/heure automatique dans Power BI Desktop](../transform-model/desktop-auto-date-time.md)
- [Définir et utiliser des tables de dates dans Power BI Desktop](../transform-model/desktop-date-tables.md)
- Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)
- Vous avez des suggestions ? [Envoyez-nous vos idées pour améliorer Power BI](https://ideas.powerbi.com/)
