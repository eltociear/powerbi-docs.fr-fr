---
title: Application Power BI pour la réalité mixte (Preview)
description: Consultez vos tableaux de bord et vos rapports dans l’application Power BI pour la réalité mixte (préversion) pendant votre immersion dans le monde virtuel ou dans le contexte de votre environnement.
author: mshenhav
ms.reviewer: ''
ms.service: powerbi
ms.subservice: powerbi-mobile
ms.topic: conceptual
ms.date: 06/05/2018
ms.author: mshenhav
ms.openlocfilehash: 04a77aa9a5a464baf0ce1c9a88604d84ad0feb53
ms.sourcegitcommit: 64c860fcbf2969bf089cec358331a1fc1e0d39a8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2019
ms.locfileid: "73879120"
---
# <a name="power-bi-for-mixed-reality-app-preview"></a>Application Power BI pour la réalité mixte (Preview)
Consultez vos tableaux de bord et vos rapports dans l’application Power BI pour la réalité mixte (préversion) pendant votre immersion dans le monde virtuel ou placez-les dans des emplacements spécifiques du contexte de votre environnement. 

[Téléchargez l’application Power BI pour Mixed Reality](https://www.microsoft.com/p/power-bi-mobile/9nblgggzlxn1?activetab=pivot%3aoverviewtab) à partir du Windows Store : Dans le Windows Store, elle porte le nom « Power BI Mobile ». Interagissez avec vos tableaux de bord et rapports dans le monde virtuel, puis sélectionnez ceux que vous voulez placer. 

## <a name="two-views-windows-classic-and-holographic"></a>Deux vues : Windows classique et holographique

Power BI pour la réalité mixte est basé sur l’application mobile Windows Power BI avec des fonctionnalités supplémentaires spécifiques à la réalité mixte. Quand vous démarrez Power BI pour la réalité mixte, vous êtes dans cette vue Windows « classique » de Power BI. Dans cette vue, vous pouvez naviguer entre les tableaux de bord et les rapports auxquels vous avez accès. Quand vous trouvé celui que vous voulez, vous pouvez passer de la vue Windows classique à l’expérience holographique. 


## <a name="windows-classic-view-basics"></a>Concepts de base de la vue classique Windows

Si vous découvrez l’expérience de réalité mixte, cette section vous concerne. L’interaction avec une application en réalité mixte diffère de l’interaction avec un ordinateur, ou même avec une tablette ou un téléphone. Dans la vue classique Windows, les applications en réalité mixte répondent à un ensemble de mouvements et de commandes vocales qui remplacent la souris et le clavier traditionnels, ou l’appui avec le doigt sur les téléphones. 

**Appui**

L’appui en l’air est le mouvement le plus simple que vous devez connaître pour interagir avec la plupart des applications en réalité mixte. Vous appuyez avec le pouce et l’index à la fois avec votre main placée verticalement, d’une façon similaire à un clic avec la souris ou un appui sur les téléphones.  

![Geste d’appui en l’air pour la réalité mixte](./media/mobile-mixed-reality-app/power-bi-hololens-airtap.png)

Dans Power BI, vous utilisez un appui dans l’application classique Windows partout où vous utiliseriez un clic avec la souris. Vous pouvez effectuer un appui en l’air pour ouvrir un tableau de bord ou un rapport dans votre espace de travail, ou sur une partie d’un visuel pour filtrer ou mettre en évidence de façon croisée d’autres visuels, etc.

![Appui en l’air avec la main dans Power BI](./media/mobile-mixed-reality-app/power-bi-hololens-airtap-hand.png) 

Découvrez plus d’informations sur les [mouvements de main Microsoft en réalité mixte](https://developer.microsoft.com/windows/mixed-reality/gestures).

**Épingler un élément** 

Appuyez en l’air sur l’icône **Épingle** ![Icône Épingle](./media/mobile-mixed-reality-app/power-bi-hololens-pin.png) pour épingler un tableau de bord ou un rapport de la vue classique Windows dans la vue holographique. Vous pouvez épingler plusieurs éléments dans la vue holographique. 

**Passer à la vue holographique**

Une fois que vous avez épinglé des éléments dans la vue classique Windows, vous appuyez sur l’icône **Plein écran** ![Icône Plein écran](./media/mobile-mixed-reality-app/power-bi-hololens-fullscreen.png) pour passer à la vue holographique. 


## <a name="holographic-view-basics"></a>Concepts de base de la vue holographique

Maintenant que vous êtes dans la vue holographique, tous les artefacts que vous avez épinglés se trouvent dans votre ruban d’ancrage. Vous pouvez placer ces éléments épinglés à des emplacements spécifiques dans l’espace physique, par exemple à côté de l’élément d’équipement décrit par l’élément. Dans la vue holographique, les commandes vocales complètent les mouvements de la main. Voici quelques commandes vocales courantes.

**« Follow me »** (Me suivre) 

Sélectionnez un artefact Power BI : il reste alors dans votre champ de vision principal et suit votre regard jusqu’à ce que vous le placiez quelque part.

**« Dock »** (Ancrer) 

Utilisez la commande « dock » pour placer un artefact dans votre bande d’ancrage Power BI : il vous suit alors en dehors de votre champ de vision principal, ce qui vous facilite l’accès.

**« Place here »** (Placer ici)

Cette commande place un tableau de bord ou un rapport sur un mur ou un objet, ou le déplace dans l’espace.

![Placement d’un tableau de bord dans l’espace](./media/mobile-mixed-reality-app/power-bi-hololens-place-visuals.png)

**« Go home »** (Aller à l’accueil)

Dites « go home » pour revenir à la vue Windows classique de Power BI. 

**« Remove »** (Supprimer)

Utilisez cette commande pour supprimer un artefact de la vue holographique.

**« Remove all »** (Tout supprimer) 

Utilisez cette commande pour supprimer tous les artefacts de la vue holographique.


## <a name="scan-a-report-qr-code-in-holographic-view"></a>Scanner le code QR d’un rapport dans la vue holographique

Vous pouvez scanner le code QR pour un rapport dans la vue holographique, tout comme vous pouvez [scanner des codes QR avec les applications mobiles Power BI](mobile-apps-qr-code.md) pour iPhone et Android.

- Dans la vue holographique, fixez du regard un code QR. Power BI ouvre le rapport associé à ce code QR.

## <a name="limitations-and-considerations"></a>Considérations et limitations

Gardez à l’esprit les considérations et les limitations suivantes pour la vue holographique.

- Vous ne voyez pas le filtrage croisé ou la mise en surbrillance croisée que vous avez éventuellement définis dans la vue classique Windows.
- La vue de vos tableaux de bord et rapports épinglés est privée. Nous ne prenons actuellement pas en charge les expériences partagées.
- Les tableaux de bord et les rapports s’actualisent toutes les 45 secondes, au fil de la modification des données.


## <a name="next-steps"></a>Étapes suivantes

- [Obtenir des données du monde réel avec les applications mobiles Power BI](mobile-apps-data-in-real-world-context.md)

 



