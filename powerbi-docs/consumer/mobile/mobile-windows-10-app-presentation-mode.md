---
title: Afficher le mode Présentation dans Surface Hub et Windows 10 - Power BI
description: Découvrez comment afficher des rapports Power BI dans Surface Hub et comment afficher des vignettes, des rapports et des tableaux de bord Power BI en mode de présentation sur les appareils Windows 10.
author: paulinbar
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: how-to
ms.date: 08/12/2020
ms.author: painbar
ms.openlocfilehash: a982374bbf713d4e0c970da601fdca3249120cbe
ms.sourcegitcommit: 5fdb45736ca0c8070124279fed4dab1ced8b7b27
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "92683313"
---
# <a name="view-reports-and-dashboards-in-presentation-mode-on-surface-hub-and-windows-10-devices"></a>Afficher des rapports et des tableaux de bord dans le mode de présentation dans les appareils Surface Hub et Windows 10
Vous pouvez utiliser le mode de présentation pour afficher des rapports et des tableaux de bord en plein écran sur les appareils Windows 10 et Surface Hub. Le mode Présentation est utile pour afficher Power BI lors de réunions ou de conférences ou sur un projecteur dédié au bureau ou pour optimiser l’espace sur un petit écran.

![Capture d’écran d’un rapport en mode de présentation.](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-2.png)

En mode Présentation :
* Tous les éléments de type « chrome » (comme les barres de navigation et de menus) disparaissent, ce qui vous permet de mieux vous concentrer sur les données de votre rapport.
* Une barre d’outils d’action est disponible pour vous permettre d’interagir avec vos données et de contrôler la présentation.
* Vous pouvez lancer un diaporama qui navigue automatiquement entre les pages, les signets ou les pages et les signets.

>[!NOTE]
>La prise en charge des applications mobiles Power BI pour les **téléphones utilisant Windows 10 Mobile** ne sera plus disponible après le 16 mars 2021. [En savoir plus](/legal/powerbi/powerbi-mobile/power-bi-mobile-app-end-of-support-for-windows-phones)

## <a name="use-presentation-mode"></a>Utiliser le mode de présentation
Dans l’application mobile Power BI, appuyez sur l’icône **Basculer en mode de présentation**.
![Icône Plein écran](././media/mobile-windows-10-app-presentation-mode/power-bi-full-screen-icon.png) Tout ce qui est inutile dans l’application disparaît et la barre d’outils d’action s’affiche en bas de l’écran ou sur les côtés gauche et droit (selon la taille de votre écran).

[![Rapport en mode plein écran avec des barres d’outils sur le côté](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-presentation-mode-toolbar-expanded.png#lightbox)

Dans la barre d’outils, vous pouvez appuyer pour effectuer les actions suivantes :

| Icône | Action |
|------|--------|
|![Icône Précédent](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-back-icon.png)|**Revenir** à la page précédente. Un appui long sur l’icône fait apparaître les fenêtres Fil d’Ariane, ce qui vous permet d’accéder au dossier contenant votre rapport ou tableau de bord.|
|![Icône Pagination](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-pages-icon.png)|**Basculer** vers une autre page du rapport de votre présentation.|
|![Icône Signets](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-bookmarks-icon.png)|**Appliquer un signet** pour présenter la vue spécifique de vos données capturées par le signet. Vous pouvez appliquer des signets personnels et de rapport.|
|![Icône Encre](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-ink-icon.png)|**Choisir la couleur de l’encre** lors de l’utilisation du stylet Surface pour annoter et dessiner sur votre page de rapport.|
|![Icône Gomme](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-eraser-icon.png)|**Effacer les marques d’encre** que vous avez faites avec le stylet Surface pour dessiner et annoter sur la page de votre rapport.          |
|![Icône Réinitialiser](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-reset-icon.png)|**Rétablir l’affichage par défaut** et effacer tous les filtres, segments ou autres modifications apportées à l’affichage des données au cours de la présentation.|
|![Icône de partage](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-share-icon.png)|**Partager** une image de la vue Présentation avec vos collègues. L’image inclut les annotations que vous avez éventuellement créées avec le stylet Surface pendant la présentation.|
|![Icône d’actualisation](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-refresh-icon.png)|**Actualiser** le rapport.|
|![Icône de lecture](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-play-icon.png)|**Lire le diaporama** , en masquant la barre d’action et en démarrant le diaporama. Un sélecteur vous permet de choisir de naviguer automatiquement les pages, les signets ou entre les pages et les signets. Par défaut, le diaporama navigue automatiquement entre les pages toutes les 30 secondes. Vous pouvez modifier ces paramètres dans [**Paramètres > Options**](#slideshow-settings). Voir [plus de détails](#slideshows) sur les diaporamas|
|![Quitter le mode plein écran](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-exit-full-screen-icon.png)|**Quitter** le mode Présentation.|
|![Icône de recherche](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-search-icon.png)|**Rechercher** d’autres artefacts dans Power BI.|

Vous pouvez détacher la barre d’outils et la placer n’importe où sur l’écran. Cela est utile pour les grands écrans, lorsque vous souhaitez vous concentrer sur une zone spécifique de votre rapport et placer les outils en regard de celui-ci. Placez simplement votre doigt sur la barre d’outils et faites la défiler dans le canevas de rapport.

[![Rapports en mode Présentation et barre d’outils non ancrée](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2.png)](./media/mobile-windows-10-app-presentation-mode/power-bi-windows-10-presentation-drag-toolbar-2-expanded.png#lightbox)

## <a name="slideshows"></a>Diaporamas

Vous pouvez lire un diaporama pour parcourir automatiquement votre présentation. Vous pouvez définir le diaporama pour qu’il parcourt les pages, les signets ou les pages et les signets. Pendant le diaporama, les pages de rapport avec [actualisation automatique de la page](../../create-reports/desktop-automatic-page-refresh.md) continuent à s’actualiser automatiquement comme configuré, garantissant ainsi que les données les plus récentes sont toujours affichées.

Lorsque vous sélectionnez le bouton **Lecture** dans la barre d’outils action, le diaporama démarre. Un contrôleur s’affiche pour vous permettre de suspendre le diaporama ou de modifier le contenu en cours de lecture : pages, signets ou pages et signets.

![Capture d’écran du sélecteur de diaporama](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-selector.png)

 Le contrôleur affiche le nom de la vue actuellement affichée (page ou signet et page). Dans l’image ci-dessus, nous voyons que dans le rapport appelé **Sales** (Ventes), nous voyons actuellement le signet **Asia Pacific** (Asie-Pacifique) sur la page **Sales Performance** (Performances des ventes).

Par défaut, un diaporama parcourt les pages uniquement, à raison d’une toutes les 30 secondes. Vous pouvez modifier le comportement par défaut est dans les [Paramètres du diaporama](#slideshow-settings).


### <a name="auto-play-a-slideshow-on-startup"></a>Lire automatiquement un diaporama au démarrage

Vous pouvez configurer l’application mobile Power BI pour démarrer automatiquement la lecture d’un diaporama chaque fois que l’application est lancée. Cette option est utile pour créer une expérience de type kiosque qui exécute un rapport dans des affichages publics sans aucune intervention manuelle. Pour plus d’informations sur la configuration d’un rapport pour l’exécution automatique, consultez [Paramètres de diaporama](#slideshow-settings) .

### <a name="slideshow-settings"></a>Paramètres du diaporama

Par défaut, un diaporama parcourt les pages uniquement, à raison d’une toutes les 30 secondes. Vous pouvez modifier ce comportement par défaut en accédant à **Paramètres > Options** , comme illustré ci-dessous. Vous pouvez également activer l’exécution automatique et choisir un rapport à lire.

1. Sélectionnez l’icône Paramètres.

1. Ouvrez l’onglet Options.

1. Si vous le souhaitez, modifiez les paramètres par défaut pour le mode de basculement du diaporama (pages, signets ou les deux) et la fréquence de transition des diapositives.

1. Si vous souhaitez que votre rapport démarre automatiquement lorsque l’application est lancée, activez le bouton bascule et choisissez **Sélectionner un rapport**. Vous pouvez rechercher les rapports auxquels vous avez accès.

![Capture d’écran des paramètres de diaporama](././media/mobile-windows-10-app-presentation-mode//power-bi-windows-10-slideshow-settings.png)

## <a name="next-steps"></a>Étapes suivantes
* [Afficher les tableaux de bord et les rapports en mode Plein écran à partir du service Power BI](../end-user-focus.md)
* Vous avez des questions ? [Essayez d’interroger la communauté Power BI](https://community.powerbi.com/)