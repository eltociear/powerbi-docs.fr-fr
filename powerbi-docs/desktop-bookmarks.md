---
title: Utilisation de signets dans Power BI
description: Les signets dans Power BI Desktop vous permettent d’enregistrer les vues et les paramètres dans vos rapports, ainsi que de créer des présentations de type récit.
author: davidiseminger
manager: kfile
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-desktop
ms.topic: conceptual
ms.date: 11/01/2018
ms.author: davidi
LocalizationGroup: Create reports
ms.openlocfilehash: 509eebfdf2d96a2cc77d5c9413c664a10309ab9c
ms.sourcegitcommit: 5e83fa6c93a0bc6599f76cc070fb0e5c1fce0082
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/13/2019
ms.locfileid: "56216423"
---
# <a name="use-bookmarks-to-share-insights-and-build-stories-in-power-bi"></a>Utiliser des signets pour partager des insights et créer des récits dans Power BI 
Les **signets** de Power BI permettent de capturer la vue actuellement configurée d’une page de rapport, filtrage et état des visuels compris, puis de revenir à cet état en sélectionnant simplement le signet enregistré. 

Vous pouvez également créer une collection de signets, les réorganiser dans l’ordre de votre choix, puis parcourir chaque signet d’une présentation pour mettre en avant une série d’insights ou le récit que vous souhaitez raconter avec vos visuels et rapports. 

![Signets dans Power BI](media/desktop-bookmarks/bookmarks_01.png)

Les signets ont de nombreuses utilisations. Vous pouvez les utiliser pour suivre la progression de la création de rapports (les signets sont faciles à ajouter, à supprimer et à renommer). Il est également possible de créer des signets pour concevoir une présentation de type PowerPoint qui parcourt les signets dans l’ordre, de façon à accompagner votre rapport d’un récit. Il existe peut-être d’autres utilisations en fonction de votre usage.

### <a name="enable-the-bookmarks-preview-versions-prior-to-march-2018"></a>Activer la préversion des signets (versions antérieures à mars 2018)
Depuis la version de mars 2018 de Power BI Desktop, les signets sont en disponibilité générale. 

Nous vous conseillons de toujours effectuer la mise à niveau vers la version la plus récente. Si vous utilisez une version antérieure de Power BI Desktop, vous pouvez essayer la fonctionnalité **Signets** à partir de la version **d’octobre 2017** de **Power BI Desktop** et, pour les rapports compatibles avec les signets, dans le **service Power BI** également. Pour activer la fonctionnalité en préversion, sélectionnez **Fichier > Options et paramètres > Options > Fonctionnalités en préversion**, puis cochez la case à côté de **Signets**. 

![Activer les signets dans la fenêtre Options](media/desktop-bookmarks/bookmarks_02.png)

Vous devrez redémarrer **Power BI Desktop** après avoir activé la préversion des signets.

## <a name="using-bookmarks"></a>Utilisation des signets
Pour utiliser des signets, sélectionnez le ruban **Vue**, puis activez la case du **volet Signets**. 

![Pour afficher le volet Signets, activez-le dans le ruban Vue.](media/desktop-bookmarks/bookmarks_03.png)

Lorsque vous créez un signet, les éléments suivants sont enregistrés :

* Page actuelle
* Filtres
* Segments, y compris le type de segments (par exemple, liste déroulante ou liste) et l’état des segment
* État de sélection des visuels (par exemple, filtres de mise en surbrillance croisée)
* Ordre de tri
* Emplacement d’exploration
* Visibilité (d’un objet, à l’aide du volet **Sélection**)
* Le mode focus ou **À la une** des objets visibles

Configurez une page de rapport comme vous souhaitez qu’elle apparaisse dans le signet. Une fois que votre page de rapport et les visuels sont organisés comment vous le souhaitez, sélectionnez **Ajouter** dans le volet **Signets** pour ajouter un signet. 

![Ajouter un signet](media/desktop-bookmarks/bookmarks_04.png)

**Power BI Desktop** crée un signet et lui donne un nom générique. Vous pouvez facilement *renommer*, *supprimer* ou *mettre à jour* un signet en sélectionnant les points de suspension en regard de son nom, puis en sélectionnant une action dans le menu qui s’affiche.

![Sélectionnez le sous-menu d’un signet en utilisant les points de suspension](media/desktop-bookmarks/bookmarks_05.png)

Une fois que vous avez un signet, vous pouvez l’afficher en cliquant simplement dessus dans le volet **Signets**. 

Vous pouvez également choisir si chaque signet appliquera des propriétés de *données*, comme des filtres et des segments, des propriétés *d’affichage*, comme À la une et sa visibilité, et les modifications de la page représentant la page qui était visible lors de l’ajout du signet. Ces fonctionnalités sont utiles si vous utilisez les signets pour naviguer entre les types de visuels. Dans ce cas, vous devrez sans doute désactiver les propriétés de données, afin que les filtres ne soient pas réinitialisés lorsque les utilisateurs modifient les types de visuels. 

Pour effectuer ces modifications, sélectionnez les points de suspension en regard du nom du signet, comme illustré dans l’image précédente, puis sélectionnez ou désélectionnez les coches en regard de *Données*, *Affichage* et autres contrôles. 

## <a name="arranging-bookmarks"></a>Organisation des signets
Lorsque vous créez des signets, vous pouvez trouver que l’ordre dans lequel vous les créez n’est pas nécessairement l’ordre dans lequel vous voulez les présenter à votre audience. Cela ne constitue pas un problème, car vous pouvez facilement réorganiser l’ordre des signets.

Dans le volet **Signets**, effectuez simplement un glisser-déplacer des signets pour modifier leur ordre, comme dans l’image suivante. La barre jaune entre les signets désigne où le signet déplacé sera positionné.

![Modifier l’ordre des signets par glisser-déplacer](media/desktop-bookmarks/bookmarks_06.png)

L’ordre de vos signets peut devenir important lorsque vous utilisez la fonctionnalité **Vue** des signets, comme décrit dans la section suivante.

## <a name="bookmarks-as-a-slide-show"></a>Signets en mode diaporama
Lorsque vous avez une collection de signets que vous souhaitez présenter dans l’ordre, vous pouvez sélectionner **Vue** dans le volet **Signets** pour lancer un diaporama.

Le mode **Vue** offre quelques fonctionnalités utiles :

1. Le nom du signet apparaît dans la barre de titre de celui-ci, qui apparaît au bas du canevas.
2. La barre de titre des signets comporte des flèches permettant de passer au signet suivant ou précédent.
3. Vous pouvez quitter le mode **Vue** en sélectionnant **Quitter** dans le volet **Signets** ou la croix (**X**) dans la barre de titre des signets. 

![Fonctionnalités de la barre de titre des signets](media/desktop-bookmarks/bookmarks_07.png)

Lorsque vous êtes en mode **Vue**, vous pouvez fermer le volet **Signets** (en cliquant sur le signe X sur ce volet) pour fournir davantage d’espace pour votre présentation. De plus, en mode **Vue**, tous les visuels sont interactifs et compatibles avec la sélection croisée, comme dans toute autre interaction. 

## <a name="visibility---using-the-selection-pane"></a>Visibilité à l’aide du volet Sélection
Un nouveau volet **Sélection** est également mis à disposition avec les signets. Le volet **Sélection** donne la liste de tous les objets de la page active. Il permet de sélectionner l’objet et de spécifier si un objet en particulier est visible. 

![Activer le volet Sélection](media/desktop-bookmarks/bookmarks_08.png)

Vous pouvez sélectionner un objet à l’aide du volet **Sélection**. De plus, vous pouvez indiquer si l’objet est actuellement visible en cliquant sur l’icône en forme d’œil à droite du visuel. 

![Volet Sélection](media/desktop-bookmarks/bookmarks_09.png)

Lorsque vous ajoutez un signet, l’état visible de chaque objet est également enregistré en fonction de son paramètre dans le volet **Sélection**. 

Il est important de noter que **des segments** continuent de filtrer une page de rapport, qu’ils soient visibles ou non. Par conséquent, vous pouvez créer différents signets, avec différents paramètres de segment. Vous pouvez ainsi donner un aspect complètement différent à une page de rapport (et mettre en évidence différents insights) en créant différents signets.

## <a name="bookmarks-for-shapes-and-images"></a>Signets pour les formes et images
Vous pouvez également lier des formes et des images à des signets. Lorsque vous cliquez sur un objet, cette fonctionnalité affiche le signet associé à cet objet. Cela peut s’avérer particulièrement utile si vous travaillez avec des boutons. Pour en savoir plus, lisez l’article sur [l’utilisation des boutons dans Power BI](desktop-buttons.md). 

Pour affecter un signet à un objet, sélectionnez l’objet, puis développez la section **Action** dans le volet **Format de la forme**, comme indiqué dans l’image suivante.

![Ajouter un lien de signet à un objet](media/desktop-bookmarks/bookmarks_10.png)

Une fois que vous avez activé le curseur **Action** en le définissant sur **Activé**, vous pouvez indiquer si l’objet est un bouton de retour, un signet ou une commande Q&R. Si vous sélectionnez Signet, vous pouvez ensuite sélectionner les signets auxquels l’objet est lié.

Les signets liés à des objets vous permettent d’effectuer des tâches très diverses. Vous pouvez créer un tableau visuel de contenu sur la page de rapport. Vous pouvez également fournir différentes vues (telles que les types de visuels) de la même information, en cliquant simplement sur un objet.

Lorsque vous êtes en mode Modification, vous pouvez utiliser Ctrl + clic pour suivre le lien. Si vous êtes dans un autre mode, cliquez simplement sur l’objet pour suivre le lien. 

## <a name="bookmark-groups"></a>Groupes de signets

À compter de la version d’août 2018 de **Power BI Desktop**, vous pouvez créer et utiliser des groupes de signets. Un groupe de signets est une collection de signets que vous spécifiez et qui peuvent être affichés et organisés sous forme de groupe. 

Pour créer un groupe de signets, maintenez la touche Ctrl enfoncée et sélectionnez les signets que vous voulez inclure dans le groupe, puis cliquez sur les points de suspension à côté de l’un des signets sélectionnés, puis sélectionnez **Grouper** dans le menu qui s’affiche.

![Créer un groupe de signets](media/desktop-bookmarks/bookmarks_15.png)

**Power BI Desktop** nomme automatiquement le groupe *Groupe 1*. Heureusement, vous pouvez simplement double-cliquer sur le nom et le renommer comme vous le souhaitez.

![Renommer un groupe de signets](media/desktop-bookmarks/bookmarks_16.png)

Le fait de cliquer sur le nom du groupe de signets développe ou réduit seulement le groupe de signets ; le nom ne représente pas un signet par lui-même. 

Lors de l’utilisation de la fonctionnalité **Afficher** des signets, ceci s’applique :

* Si le signet sélectionné est dans un groupe quand vous sélectionnez **Afficher** à partir des signets, seuls les signets *de ce groupe* apparaissent dans la session de visualisation. 

* Si le signet sélectionné n’est pas dans un groupe ou est au plus haut niveau (comme le nom d’un groupe de signets), tous les signets de l’intégralité du rapport sont affichés, y compris les signets des groupes. 

Pour dissocier des signets, sélectionnez simplement un signet dans un groupe, cliquez sur les points de suspension et sélectionnez **Dissocier** dans le menu qui apparaît. 

![Dissocier un groupe de signets](media/desktop-bookmarks/bookmarks_17.png)

Notez que la sélection de **Dissocier** pour un signet d’un groupe retire tous les signets du groupe (cette action supprimer le groupe, mais pas les signets eux-mêmes). Ainsi, pour supprimer un seul signet d’un groupe, vous devez **Dissocier** n’importe quel membre de ce groupe, ce qui supprime le regroupement, sélectionner les membres que vous voulez dans le nouveau groupe (en utilisant Ctrl et en cliquant sur chaque signet), puis resélectionner **Grouper**. 


## <a name="using-spotlight"></a>Utilisation du mode À la une
La fonctionnalité **À la une** est également fournie avec les signets. Avec la fonction **À la une**, vous pouvez attirer l’attention sur un graphique spécifique, par exemple lors de la présentation de vos signets en mode **Vue**.

Comparons les modes **À la une** et **Focus** pour voir en quoi ils diffèrent.

1. En mode **focus**, vous pouvez avoir un visuel qui remplit l’intégralité du canevas en sélectionnant l’**icône Mode focus**.
2. En utilisant le mode **À la une**, vous pouvez mettre en évidence un visuel dans sa taille d’origine et atténuer tous les autres visuels en les rendant presque transparents. 

![Comparer les modes Focus et À la une](media/desktop-bookmarks/bookmarks_11.png)

Lorsque le visuel dans l’image précédente a l’icône **focus** activée, la page a l’aspect suivant :

![mode Focus](media/desktop-bookmarks/bookmarks_12.png)

En revanche, quand **À la une** est sélectionné dans le menu des points de suspension du visuel, la page ressemble à ce que vous voyez ici :

![mode À la une](media/desktop-bookmarks/bookmarks_13.png)

Si l’un des modes est sélectionné lors de l’ajout d’un signet, ce mode (Focus ou À la une) est conservé dans le signet.

## <a name="bookmarks-in-the-power-bi-service"></a>Signets dans le service Power BI
Lorsque vous publiez un rapport contenant au moins un signet dans le **service Power BI** , vous pouvez afficher et utiliser les signets dans le **service Power BI**. Lorsque les signets sont disponibles dans un rapport, vous pouvez sélectionner **Vue > volet Sélection** ou **Vue > volet Signets** pour afficher chacun de ces volets.

![Afficher les volets Signets et Sélection dans le service Power BI](media/desktop-bookmarks/bookmarks_14.png)

Dans le **service Power BI**, le **volet Signets** fonctionne comme dans **Power BI Desktop**, y compris la possibilité de sélectionner **Vue** pour afficher vos signets dans l’ordre, comme un diaporama.

Notez que vous devez utiliser la barre de titre de signets en gris pour naviguer entre les signets et pas les flèches noires (celles-ci vous permettent de passer d’une page de rapport à une autre, et pas d’un signet à un autre).

## <a name="limitations-and-considerations"></a>Considérations et limitations
Pour cette préversion des **signets**, vous devez garder à l’esprit les considérations et limitations suivantes.

* La plupart des visuels personnalisés doivent fonctionner correctement avec l’attribution de signets. Si vous rencontrez des problèmes avec l’attribution de signets et un visuel personnalisé, contactez le créateur de ce dernier et demandez-lui d’ajouter la prise en charge des signets pour son visuel. 
* Si vous ajoutez un visuel sur une page de rapport après la création d’un signet, le visuel s’affiche dans son état par défaut. Cela signifie également que si vous introduisez un segment dans une page où vous avez précédemment créé des signets, le segment se comporte avec son état par défaut.
* Le déplacement parmi les visuels après la création d’un signet est reflété dans le signet. 


## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur les fonctionnalités qui sont similaires ou pour interagir avec des signets, consultez les articles suivants :

* [Utiliser une extraction dans Power BI Desktop](desktop-drillthrough.md)
* [Afficher une vignette de tableau de bord ou un visuel de rapport en mode Focus](consumer/end-user-focus.md)

