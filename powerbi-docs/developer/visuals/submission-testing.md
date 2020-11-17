---
title: Test d’envoi d’un visuel Power BI
description: Cet article décrit les cas de test que votre visuel doit passer avant la publication sur AppSource. Il existe également des cas de test facultatifs.
author: KesemSharabi
ms.author: kesharab
ms.reviewer: sranins
ms.service: powerbi
ms.subservice: powerbi-custom-visuals
ms.topic: how-to
ms.date: 04/15/2020
ms.openlocfilehash: 515813aeb98010f838cfff75febbb1ef206bc2cf
ms.sourcegitcommit: 37bd34053557089c4fbf0e05f78e959609966561
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94397481"
---
# <a name="submission-testing-of-a-power-bi-visual"></a>Test d’envoi d’un visuel Power BI

Avant de publier votre visuel dans [AppSource](https://appsource.microsoft.com/marketplace/apps?product=power-bi-visuals), il doit réussir les tests listés dans cet article. Testez votre visuel avant de l’envoyer. Si votre visuel ne réussit pas les cas de test obligatoires, il est rejeté.

Pour plus d’informations sur le processus de publication, consultez [Publier des visuels Power BI sur l’Espace partenaires](./office-store.md).

## <a name="testing-a-new-version-of-a-published-visual"></a>Test d’une nouvelle version d’un visuel publié

Si vous testez ou déboguez une nouvelle version d’un visuel déjà publié, vous pouvez remplacer la version AppSource par une version de fichier local en activant le mode développeur dans Power BI Desktop.

Pour activer le mode développeur, suivez ces étapes :

1. Ouvrez Power BI Desktop.

2.  Sélectionnez **Fichier** > **Options et paramètres**.

3.  Sélectionnez **Options**.

4. Dans la fenêtre Options, dans la liste FICHIER ACTIF, sélectionnez **Paramètres de rapport**.

5. En mode développeur, sélectionnez l’option **Activer le mode développeur pour cette session**.

>[!NOTE]
>Dans Power BI Desktop, le mode développeur est valide pour une seule session uniquement. Si vous ouvrez une nouvelle instance Power BI Desktop à des fins de test, vous devrez réactiver le mode développeur.

## <a name="general-test-cases"></a>Cas de test généraux

Vérifiez que votre visuel réussit les cas de test généraux.

| Cas de test | Résultats attendus
| --------- | ----------------
| Créez un **Histogramme empilé** avec **Catégorie** et **Valeur**. Convertissez-le en visuel, puis revenez à l’histogramme. | Aucune erreur ne s’affiche après ces conversions. |
| Créez une **Jauge** avec trois mesures. Convertissez-la en visuel, puis revenez à la **Jauge**. | Aucune erreur ne s’affiche après ces conversions. |
| Effectuez des sélections dans votre visuel. | Les autres visuels reflètent les sélections. |
| Sélectionnez des éléments dans d’autres visuels. | Votre visuel affiche des données filtrées en fonction de la sélection dans d’autres visuels. |
| Vérifiez les conditions min/max de **dataViewMapping**. | Les compartiments de champs peuvent accepter plusieurs champs, un champ unique ou être déterminés par d’autres compartiments. Les conditions min/max de **dataViewMapping** doivent être correctement configurées dans les fonctionnalités de votre visuel. |
| Supprimez tous les champs dans des ordres différents. | Le visuel continue à s’afficher correctement lorsque les champs sont supprimés dans un ordre arbitraire. Il n’y a pas d’erreurs dans la console ou le navigateur. |
| Ouvrez le volet **Format** avec chaque configuration de compartiment possible. | Ce test ne déclenche pas d’exceptions de référence null. |
| Filtrez les données à l’aide du volet **Filtre** au niveau du visuel, de la page et du rapport. | Les info-bulles sont correctes après l’application de filtres. Les info-bulles affichent la valeur filtrée. |
| Filtrez des données à l'aide de **segments**. | Les info-bulles sont correctes après l’application de filtres. Les info-bulles affichent la valeur filtrée. |
| Filtrez les données à l’aide d’un visuel publié. Par exemple, sélectionnez un secteur ou une colonne. | Les info-bulles sont correctes après l’application de filtres. Les info-bulles affichent la valeur filtrée. |
| Si le filtrage croisé est pris en charge, vérifiez que les filtres fonctionnent correctement. | La sélection appliquée filtre les autres visuels de cette page du rapport. |
| Sélectionnez avec les touches Ctrl, Alt et Maj. | Aucun comportement inattendu ne se manifeste. |
| Modifiez le **Mode d’affichage** sur **Taille réelle**, **Ajuster à la page** et **Ajuster à la largeur**. | Les coordonnées de la souris sont exactes. |
| Redimensionnez votre visuel. | Le visuel réagit correctement au redimensionnement. |
| Définissez la taille du rapport sur la valeur minimale. | Il n’y a pas d’erreurs d’affichage. |
| Assurez-vous que les barres de défilement fonctionnent correctement. | Les barres de défilement doivent exister, si nécessaire. Vérifiez les tailles des barres de défilement. Les barres de défilement ne doivent pas être trop larges ou hautes. La position et la taille des barres de défilement doivent être conformes aux autres éléments de votre visuel. Vérifiez que les barres de défilement sont nécessaires pour les différentes tailles du visuel. |
| Épinglez votre visuel à un **Tableau de bord**. | Le visuel doit s’afficher correctement. |
| Ajoutez plusieurs versions de votre visuel à une page de rapport unique. | Toutes les versions du visuel s’affichent et fonctionnent correctement. |
| Ajoutez plusieurs versions de votre visuel à plusieurs pages de rapport. | Toutes les versions du visuel s’affichent et fonctionnent correctement. |
| Basculez entre les pages du rapport. | Le visuel s’affiche correctement. |
| Testez le mode lecture et le mode édition pour votre visuel. | Toutes les fonctions fonctionnent correctement. |
| Si votre visuel utilise des animations, ajoutez, modifiez et supprimez des éléments de votre visuel. | L’animation des éléments du visuel fonctionne correctement. |
| Ouvrez le volet **Propriétés**. Activez ou désactivez les propriétés, entrez du texte personnalisé, épuisez les options disponibles et entrez des données incorrectes. | Le visuel répond correctement. |
| Enregistrez le rapport et rouvrez-le. | Tous les paramètres de propriété sont conservés. |
| Basculez entre les pages dans le rapport, puis revenez en arrière. | Tous les paramètres de propriété sont conservés. |
| Testez toutes les fonctionnalités de votre visuel, y compris les différentes options que le visuel fournit. | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Testez tous les types de données numériques, de date et de caractère, comme dans les tests suivants. | Toutes les données sont mises en forme correctement. |
| Passez en revue la mise en forme des valeurs d’info-bulle, des étiquettes des axes, des étiquettes de données et d’autres éléments visuels avec mise en forme. | Tous les éléments sont mis en forme correctement. |
| Vérifiez que les étiquettes de données utilisent la chaîne de format. | Toutes les étiquettes de données sont mises en forme correctement. |
| Activez ou désactivez la mise en forme automatique des valeurs numériques dans les info-bulles. | Les info-bulles affichent les valeurs correctement. |
| Testez les entrées de données avec différents types de données, notamment des chaînes numériques, du texte, des dates et heures et des chaînes de formats différents du modèle. Testez différents volumes de données, par exemple des milliers de lignes, une ligne et deux lignes. | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Fournissez des données incorrectes à votre visuel, par exemple null, une valeur infinie, des valeurs négatives ou des types de valeur incorrects. | Tous les affichages et fonctionnalités fonctionnent correctement. |

## <a name="optional-browser-testing"></a>Test facultatif des navigateurs

L’équipe AppSource valide le visuel sur les versions Windows les plus récentes des navigateurs Google Chrome, Microsoft Edge et Mozilla Firefox.
Si vous le souhaitez, testez votre visuel dans les navigateurs suivants.

| Cas de test | Résultats attendus
| --------- | ----------------
| **Windows** |
| Google Chrome (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Mozilla Firefox (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Microsoft Edge (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Microsoft Internet Explorer 11 (facultatif) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| **macOS** |
| Chrome (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Firefox (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Safari (version précédente) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| **Linux** |
| Firefox (versions les plus récentes et précédentes) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| **Mobile iOS** |
| Apple Safari iPad (version précédente de Safari) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| iPad Chrome (dernière version de Safari) | Tous les affichages et fonctionnalités fonctionnent correctement. |
| **Mobile Android** |
| Chrome (versions les plus récentes et précédentes) | Tous les affichages et fonctionnalités fonctionnent correctement. |

## <a name="desktop-testing"></a>Test de Desktop

Testez votre visuel dans la version actuelle de [Power BI Desktop](https://powerbi.microsoft.com/en-us/desktop/).

| Cas de test | Résultats attendus
| --------- | ----------------
| Testez toutes les fonctionnalités de votre visuel. | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Importez, enregistrez, ouvrez un fichier et publiez-le sur le service web Power BI à l’aide du bouton **Publier** dans Power BI Desktop. | Tous les affichages et fonctionnalités fonctionnent correctement. |
| Modifiez la chaîne de format numérique pour qu’elle ne comporte aucune décimale ou en ait trois en augmentant ou en diminuant la précision. | Le visuel s’affiche correctement. |

## <a name="performance-testing"></a>Tests de performances

Votre visuel doit s’exécuter à un niveau acceptable. Utilisez les outils de développement pour valider les performances. Ne vous fiez pas aux signaux visuels et aux journaux de temps de la console.

| Cas de test | Résultats attendus
| --------- | ----------------
| Créez un visuel avec de nombreux éléments visuels. | Le visuel doit s’exécuter correctement et ne pas geler l’application. Il ne doit y avoir aucun problème de performances avec des éléments tels que la vitesse d’animation, le redimensionnement, le filtrage et la sélection.

## <a name="next-steps"></a>Étapes suivantes

Pour plus d’informations sur le processus de publication, consultez [Publier des visuels Power BI sur l’Espace partenaires](./office-store.md).

D’autres questions ? [Poser des questions à la communauté Power BI](https://community.powerbi.com/).
